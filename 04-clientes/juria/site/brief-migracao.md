---
tipo: cliente-doc
cliente: juria
atualizado: 2026-11-27
autor: claude
origem: agencia_marketing, clients/juria/brief-migracao-juria-astro.md (migrado em 27/11/2026)
---
# Brief de execução — Migração do site JurIA para Astro

> **Para o Claude Code.** Este documento é a especificação completa da tarefa. Leia inteiro antes de escrever qualquer código.
>
> **Revisado em 29/09/2026** com o resultado da fase de descoberta. As correções estão marcadas com `✅ APURADO`. Onde a descoberta contradisse a premissa original, vale o apurado.

---

## 0. Contexto e regra de ouro

O site institucional do **JurIA** (`juria.app.br`) hoje é um **one-pager em HTML puro**, hospedado na **Vercel**. Ele está **recebendo tráfego pago do Meta Ads neste momento**.

**REGRA DE OURO: nada do que está em produção pode quebrar ou sair do ar em nenhum momento desta tarefa.**

Isso significa, na prática:

- Todo o trabalho acontece em **branch separada** e **pasta separada**.
- Os arquivos do site atual **não são movidos, renomeados nem deletados** até o cutover final aprovado.
- O deploy de produção da Vercel continua apontando para o site atual até que eu (Guilherme) dê o OK explícito.
- Validação acontece via **preview deploy da Vercel** na branch, nunca em produção.

O objetivo da migração é triplo:

1. **SEO orgânico** — sair de 1 URL indexável para uma arquitetura multi-página que compete por termos de cabeça.
2. **Busca com IA** (ChatGPT, Perplexity, Google AI Overviews) — estruturar o conteúdo pra ser extraível e citável.
3. **Tráfego pago** — permitir landing pages dedicadas por campanha, isoladas do SEO.

---

## 0.0 ✅ APURADO — onde o site vive, e onde o novo vai nascer

O site **não vive neste repositório**. Ele está em `hub3ps/juria-lps`, clone
local em `~/Desktop/juria-lps`. Este repositório (`agencia_marketing`) guarda a
operação da agência, e é onde este brief mora.

**Decisão de 29/09:** o projeto Astro nasce **neste repositório**
(`agencia_marketing`), isolado do `juria-lps`. A ligação entre os dois, na hora
de publicar, é problema do cutover e será resolvida depois. Até lá, nada do
`juria-lps` é tocado.

---

## 0.1 Escopo — o que está e o que não está incluído

**No escopo:** o domínio principal `juria.app.br`.

**FORA do escopo:** existe uma landing page de segmento no subdomínio **`trabalhista.juria.app.br`**, que também recebe tráfego pago ativo.

Esse subdomínio **não é tocado nesta tarefa**. Não migre, não mova, não altere, não inclua no projeto Astro. Ele continua rodando exatamente como está.

### ✅ APURADO — ele compartilha tudo

**Sim, compartilha.** Mesmo repositório (`juria-lps`), mesmo projeto Vercel e,
o que mais importa, **o mesmo `vercel.json`**. Não é projeto à parte: é a pasta
`trabalhista/`, servida por um rewrite por host:

```json
{ "source": "/", "has": [{"type":"host","value":"trabalhista.juria.app.br"}],
  "destination": "/trabalhista" },
{ "source": "/", "has": [{"type":"host","value":"previdenciario.juria.app.br"}],
  "destination": "/previdenciario" },
{ "source": "/", "destination": "/institucional" }
```

O institucional é servido pela **última regra**, o fallback do `/`.

**Consequência:** "não tocar no trabalhista" e "migrar o site principal" não são
separáveis por pasta. A separação tem que acontecer dentro do `vercel.json`, que
é arquivo único. O `previdenciario` está na mesma situação.

Como o projeto Astro nasce em outro repositório (ver §0.0), isso deixa de ser
risco durante a construção e vira decisão de cutover.

---

## 1. Fase de descoberta (faça isso ANTES de codar)

Não presuma nada sobre o estado atual. Investigue e me reporte:

1. **Onde o site do JurIA vive neste repositório?** Localize a pasta e liste os arquivos.
2. **Como o CSS está feito?** Tailwind via CDN, Tailwind buildado, CSS custom, ou mistura? Isso muda completamente a estratégia de migração.
3. **Há JavaScript?** O mockup navegável do dashboard (seção `#mockup`) tem interatividade — mapeie o que ele faz e de que depende.
4. **Como está o deploy na Vercel?** Existe `vercel.json`? Qual o build command atual? O projeto é o repositório inteiro ou uma subpasta?
5. **Já existe JSON-LD (`application/ld+json`) no HTML?** Se sim, qual schema?
6. **Inventário completo de tracking.** O site já tem GTM, Meta Pixel e GA4 rodando com campanhas ativas. Extraia todos os IDs, identifique se Pixel e GA4 disparam via GTM ou por script direto, e liste eventos customizados existentes. Detalhe na §8 — **é a parte mais frágil da migração.**
7. **O subdomínio `trabalhista.juria.app.br` vive neste repositório?** Compartilha projeto Vercel, build ou config com o site principal? **Responda isso explicitamente** — ver §0.1.
8. **Tracking do subdomínio:** ele usa os mesmos IDs de GTM, Pixel e GA4? Se sim, verifique se há medição entre subdomínios configurada, pra não quebrar atribuição no cutover.

### ✅ APURADO — respostas da descoberta, 29/09/2026

| # | Achado |
|---|---|
| 1 | `hub3ps/juria-lps`, não este repo. Ver §0.0 |
| 2 | **CSS custom, 3.512 linhas num `<style>` inline.** Zero Tailwind, zero arquivo externo |
| 3 | **JS vanilla puro**, 9 blocos, sem framework. O mockup é o `<script id="mockups-novos-v2-scripts">` |
| 4 | `vercel.json` na raiz, **sem build**. Site estático servido direto, projeto = repositório inteiro |
| 5 | **Existe**: `SoftwareApplication` e `Organization` |
| 6 | **Só o GTM está no HTML.** Ver §8 |
| 7 | Compartilha repo, projeto Vercel e `vercel.json`. Ver §0.1 |
| 8 | Mesmo `GTM-WHQGLTXC` em todas as páginas |

**Três achados extras, que o brief não previu:**

**Nenhum anúncio no ar usa âncora.** Os quatro criativos ativos apontam para
`https://www.juria.app.br/` puro. A §3 trata âncora como risco alto; o risco
real é menor, mas as âncoras continuam valendo porque a navegação interna usa.

**Existe uma âncora a mais que a §3 não lista:** `#cta`, no bloco final.

**Links para o portal, sete destinos distintos:** `/register` (7 ocorrências),
`/login`, `/dashboard` e `/meu` (2). Todos precisam sobreviver.

---

**Fase de descoberta CONCLUÍDA.**

---

## 2. Setup do projeto paralelo

- Branch nova: `feat/site-astro` ✅ APURADO: **no repositório `agencia_marketing`**,
  não no `juria-lps`. Ver §0.0.
- O projeto Astro vive em **pasta nova**, ao lado do site atual (não dentro dele). Sugestão: `juria-site-astro/`. Se a estrutura do repositório pedir outro caminho, proponha.
- Stack: **Astro + Tailwind**. Sem React/Vue — o site é conteúdo estático, ilha nenhuma é necessária salvo no mockup navegável (avalie; se for JS vanilla, mantenha vanilla).
- Output: `static`. Nada de SSR.
- Configure o preview deploy da Vercel pra essa branch, apontando pra pasta nova. Preview não pode ter domínio de produção nem ser indexável (ver §7).

---

## 3. Migração da home — o ponto mais sensível

A home nova substitui a atual **na mesma URL (`/`)**, e é aqui que mora o risco com o Meta Ads.

### Âncoras que NÃO podem quebrar

Os anúncios ativos podem apontar para URLs com âncora. Todas estas precisam continuar existindo e funcionando na home nova:

- `#recursos`
- `#inteligencia`
- `#precos`
- `#faq`
- `#mockup`
- `#cta` ✅ APURADO, existe e não estava listada

**Se a seção de preços virar página própria (`/precos`), a home ainda precisa manter uma seção `#precos` funcional.** Não remova a âncora — no máximo, resuma a seção e linke pra página completa.

### Conteúdo

O conteúdo atual é bom e **deve ser preservado integralmente**. Não reescreva copy por conta própria. Migração é de estrutura, não de texto. Se identificar algo que julga que deveria mudar, **liste pra mim como sugestão** em vez de alterar.

O **mockup navegável do dashboard** é o principal diferencial competitivo do site e precisa continuar funcionando exatamente igual, inclusive no mobile.

---

## 4. Arquitetura de páginas

### Indexáveis

| URL | Propósito |
|---|---|
| `/` | Home |
| `/precos` | Planos completos |
| `/software-juridico` | Termo de cabeça principal |
| `/gestao-de-processos-e-prazos` | Termo de cabeça |
| `/jurimetria` | Termo de cabeça |
| `/due-diligence-juridica` | Termo de cabeça |
| `/ia-para-advogados` | Termo de cabeça |
| `/alternativas-ao-advbox` | Comparativo — alta intenção |
| `/alternativas-ao-astrea` | Comparativo — alta intenção |
| `/alternativas-ao-projuris` | Comparativo — alta intenção |
| `/sobre` | Autoridade Mobiletec |

### Não indexáveis

| URL | Propósito |
|---|---|
| `/lp/*` | Landings de campanha paga — `noindex, nofollow`, fora do sitemap |

### Blog (esqueleto, sem conteúdo ainda)

Monte a estrutura pronta e vazia: `/blog` (índice) e `/blog/[slug]` via content collections do Astro, com layout de post, breadcrumb e JSON-LD de `Article`. **Não invente posts.** Só a estrutura, pronta pra receber markdown depois.

### Sobre as páginas de conteúdo

**Não escreva o conteúdo final delas agora.** Crie cada uma com:

- Layout e componentes montados
- Estrutura de headings semântica definida
- Blocos com placeholder claramente marcado (`{{ TODO: ... }}`)
- SEO técnico já completo (title, description, canonical, JSON-LD)

O texto vem depois, comigo. O que preciso agora é o esqueleto navegável e tecnicamente correto.

---

## 5. Componentes

Extraia do HTML atual, sem alterar aparência:

`Header`, `Footer`, `Hero`, `SectionHeader`, `FeatureCard`, `PricingCard`, `FaqAccordion`, `CtaBlock`, `TrustBadges`, `Mockup` (o dashboard navegável).

Tudo que é dado (planos, features, FAQ) sai do markup e vai pra arquivo de dados em `src/data/`. Preço e limite de plano não podem estar hardcoded em três lugares diferentes.

---

## 6. SEO técnico

### Por página
- `<title>` e `meta description` únicos
- **`canonical` absoluto e correto** — ver alerta abaixo
- Open Graph e Twitter Card completos
- Hierarquia de headings correta: **um H1 por página**

### ⚠️ Problema de canonical detectado — resolver

O site atual tem uma inconsistência: o `canonical` declara `https://juria.app.br/` (sem www), mas a URL final resolve para `https://www.juria.app.br` (com www). **Isso divide sinal de SEO e precisa ser decidido antes do cutover.**

Ação: escolha **uma** versão como oficial, faça 301 permanente da outra pra ela na Vercel, e use a escolhida em todos os canonicals, no sitemap e no JSON-LD. Me pergunte qual eu prefiro se não for óbvio pela configuração de domínio da Vercel.

### Arquivos
- `sitemap.xml` gerado automaticamente (`@astrojs/sitemap`), **excluindo `/lp/*`**
- `robots.txt` apontando pro sitemap
- **`llms.txt` na raiz** — resumo factual do produto pra crawlers de IA: o que é, quem fez, funcionalidades, planos e preços, links principais. Fato puro, sem copy de venda.

### JSON-LD (obrigatório em todas as páginas relevantes)
- `Organization`: Mobiletec Sistemas, CNPJ, fundação em 1999 (corrigido pela Mobiletec em 21/10/2026; antes constava 2000)
- `SoftwareApplication` — com `AggregateOffer` e um `Offer` por plano, com preços em BRL
- `FAQPage` — nas páginas com FAQ
- `BreadcrumbList` — nas páginas internas

---

## 7. Otimização para busca com IA

Isso é diferente de SEO clássico e não é opcional — é um dos três objetivos da migração.

1. **Formato pergunta → resposta direta.** H2 com a pergunta em linguagem natural, resposta objetiva em 2-3 frases **imediatamente abaixo**, detalhamento depois. É o formato que os modelos extraem.
2. **Números explícitos no HTML.** "R$ 159/mês, 5 usuários, 500 processos" é
   citável. "Planos flexíveis" não é. Nunca deixe um dado concreto existir só
   dentro de imagem. ✅ APURADO: os preços mudaram em 29/09, ver §11.
3. **Nada de conteúdo crítico renderizado por JS.** Crawler de IA frequentemente não executa JavaScript. Tudo que importa precisa estar no HTML servido.
4. **Bloco de fatos verificáveis** em `/sobre`: ano de fundação, CNPJ, tempo de mercado, o que a Mobiletec construiu.

### Preview deploys não podem indexar
Todo preview da Vercel precisa servir `X-Robots-Tag: noindex` via `vercel.json`. Se um preview vazar pro índice, gera conteúdo duplicado contra o domínio principal.

---

## 8. Tracking e conversão

### ✅ APURADO — a premissa desta seção estava errada, e isso é boa notícia

**Só o GTM está no HTML.** Não há `fbq(`, não há `connect.facebook`, não há
`gtag()` de GA4. Zero ocorrências.

O Pixel e o GA4 **disparam por dentro do GTM**, e os IDs vivem lá, não no site:

| Ferramenta | ID | Onde vive |
|---|---|---|
| GTM | `GTM-WHQGLTXC` | snippet no HTML |
| Meta Pixel | `1009120801605718` | dentro do GTM |
| GA4 | `G-DRF9JD5S5F` | dentro do GTM |
| Google Ads | `AW-17799194021` | dentro do GTM |

**O que isso muda:** não há script de Pixel nem de GA4 para replicar. Migrar o
snippet do GTM, na mesma posição, preserva tudo. O inventário de eventos também
não sai do HTML, sai do container, e está documentado em
`clients/juria/ferramentas/gerar-eventos.py`, o documento único de tracking.

**O único `dataLayer.push` do HTML é o Consent Mode**, entre as linhas 68 e 90,
no `<head>`, ANTES do snippet do GTM. Essa ordem não é estilo: se o bloco for
para depois, as tags de inicialização já foram avaliadas e disparam mesmo para
quem se opôs. Já aconteceu nesta conta e foi corrigido em agosto.

O risco real desta seção, portanto, é **um só**: manter o Consent Mode antes do
GTM e o GTM na mesma posição.

### Inventário obrigatório (faça primeiro)

Antes de migrar qualquer script, extraia do HTML atual e me reporte:

~~Antes de migrar qualquer script, extraia do HTML atual e me reporte~~
**Feito.** Ver o quadro acima.

### Preservar exatamente

- Todos os IDs acima, **idênticos**. Não gere, não troque, não "atualize" nenhum.
- Mesma posição e ordem de carregamento.
- Presentes em **todas** as páginas novas, inclusive `/lp/*`.
- Se algum evento já é disparado hoje, ele continua disparando com o mesmo nome e os mesmos parâmetros. Renomear evento quebra otimização de campanha em andamento.

### Adicionar (apenas o que não existe)

✅ APURADO. O container já tem, e **nenhum deles precisa ser criado no site**,
porque todos disparam por gatilho de clique ou de página dentro do GTM:

| Já existe | Observação |
|---|---|
| `PageView` | desde 28/09 só nas LPs, não nas telas internas do portal |
| `ViewRegister` | chegada no `/register`, com conversão personalizada |
| `Lead` | conta criada (`form_submit_trial`), dedup por `event_id`, EMQ 8,0 |
| `CompleteRegistration` | onboarding completo, subiu em 28/09 |
| `Purchase` | venda, via servidor |

⚠️ **`ClickTrial` foi REMOVIDO em 23/09** e não deve ser recriado. O evento
disparava no clique do CTA, mas o redirecionamento para `/register` cortava o
envio antes de chegar à Meta. O `ViewRegister` mede a mesma intenção do outro
lado do redirecionamento, com confiança maior.

Se ainda assim quiser `click_whatsapp` e `view_pricing`, são eventos novos e
legítimos. Confirmar antes de criar.

### Corrigir
- **Substituir os `mailto:` por WhatsApp com link rastreado.** ✅ APURADO: são
  **dois**, ambos para `contato@juria.app.br`, um deles no CTA do plano
  Ilimitado. Já está registrado na página de Plano do hub como tópico a decidir:
  "Rever o botão Falar com especialista". **Pedir o número e a mensagem padrão
  antes de implementar. Não inventar.**

---

## 9. Checklist de validação (antes de falar em produção)

Rode tudo no preview deploy e me entregue o resultado item a item:

**Não quebrou nada**
- [ ] `/` carrega e é visualmente equivalente à atual
- [ ] Âncoras `#recursos`, `#inteligencia`, `#precos`, `#faq`, `#mockup` funcionam na home
- [ ] Mockup do dashboard funciona, incluindo mobile
- [ ] Todos os links pro `portal.juria.app.br` (login e register) intactos
- [ ] GTM disparando com o ID correto
- [ ] **Meta Pixel disparando** — validado no Meta Pixel Helper, PageView confirmado
- [ ] **GA4 registrando pageview** — validado no DebugView em tempo real
- [ ] Eventos que já existiam continuam disparando com nome e parâmetros idênticos
- [ ] Tracking presente também nas páginas novas e em `/lp/*`
- [ ] Parâmetros UTM sobrevivem à navegação interna e chegam ao GA4

**Novo funcionando**
- [ ] Todas as páginas da §4 respondem 200
- [ ] `/lp/*` com `noindex` confirmado no HTML servido
- [ ] `sitemap.xml` gerado, sem `/lp/*`
- [ ] `robots.txt` e `llms.txt` acessíveis
- [ ] JSON-LD validado no Rich Results Test do Google, sem erro
- [ ] Canonical consistente (www vs não-www resolvido) em todas as páginas
- [ ] Um H1 por página

**Qualidade**
- [ ] Lighthouse mobile: Performance ≥ 90, SEO = 100
- [ ] Sem erro no console
- [ ] Testado em mobile real, não só no devtools

---

## 10. Cutover — só depois do meu OK explícito

**Antes de qualquer coisa:** os anúncios ativos do Meta Ads apontam hoje para **dois destinos**:

| Destino | Situação |
|---|---|
| `juria.app.br` | **No escopo** desta migração |
| `trabalhista.juria.app.br` | **FORA do escopo** — não tocar (ver §0.1) |

Valide no preview que `juria.app.br` responde 200 em todas as variações usadas nos anúncios: com e sem âncora, com e sem UTM. Se surgir qualquer outra URL de destino além dessas duas, me avise antes de prosseguir.

Sequência:

1. Lista de URLs dos anúncios validada uma a uma ✓2. Checklist da §9 100% verde ✓
3. Meu OK explícito ✓
4. Merge da branch
5. Deploy de produção
6. **Verificação imediata pós-deploy:** home, âncoras, portal, GTM, uma URL de anúncio real
7. Submeter o novo sitemap no Google Search Console

**Rollback:** se qualquer coisa quebrar, use o *instant rollback* da Vercel pro deployment anterior. Não tente consertar em produção. Volta primeiro, investiga depois.

---

## 11. O que NÃO fazer

- ❌ Tocar em qualquer arquivo do site atual antes do cutover
- ❌ Tocar em qualquer coisa do `trabalhista.juria.app.br`
- ❌ Fazer deploy em produção sem meu OK explícito
- ❌ Mudar, "melhorar" ou reescrever a copy existente por conta própria
- ❌ Remover ou renomear as âncoras da home
- ❌ Inventar depoimentos, logos de clientes, números de uso ou cases
- ❌ Trocar, gerar ou "atualizar" qualquer ID de tracking já instalado (GTM, Pixel, GA4)
- ❌ Renomear eventos de conversão que já existem
- ❌ Inventar número de WhatsApp ou qualquer dado que você não tem
- ❌ Escrever o conteúdo final das páginas novas — só o esqueleto
- ❌ Criar posts de blog
- ❌ Alterar preços ou limites de plano por conta própria.
  ✅ APURADO: **os planos foram reestruturados em 29/09/2026**, antes desta
  migração. A fonte da verdade é
  `clients/juria/comercial/planos-e-creditos.md`, e o site atual já foi
  corrigido (commit `edd7c77` no `juria-lps`). O Astro parte dos números novos:

  | Plano | Preço | Usuários | Processos | IA/mês |
  |---|---|---|---|---|
  | Solo | R$ 69 | 1 | 70 | 20 |
  | Plus | R$ 159 | 5 | 500 | 150 |
  | Max | R$ 499 | 20 | 2.000 | 400 |
  | Ilimitado | R$ 1.299 | ∞ | ∞ | 1.000 |

  Trial: **7 dias**, sem cartão. O Solo **não** tem todas as funcionalidades:
  são quatro recursos. Nenhuma promessa global de "todas as funcionalidades"
  pode existir fora do contexto "do Plus em diante".

---

## 12. Ordem de execução

1. Descoberta (§1) → **pare e me reporte**
2. Setup do projeto e preview deploy (§2)
3. Migração da home com âncoras preservadas (§3) → **pare e me mostre o preview**
4. Componentes e dados (§5)
5. Esqueleto das páginas novas (§4)
6. SEO técnico, JSON-LD, llms.txt (§6, §7)
7. Tracking preservado e WhatsApp (§8) — inventário primeiro, migração depois
8. Checklist de validação (§9) → **pare e me entregue o resultado**
9. Cutover (§10) — só com OK

**Pare nos três pontos marcados.** Não emende a tarefa inteira sem checkpoint.
