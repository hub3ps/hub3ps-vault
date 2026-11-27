---
tipo: arquivo
cliente: juria
atualizado: 2026-11-27
autor: claude
origem: agencia_marketing, clients/juria/PLANO-execucao-site-astro.md (migrado em 27/11/2026)
---
# Plano de execução · site JurIA em Astro

> Derivado do [[04-clientes/juria/site/brief-migracao|brief]], já corrigido com a fase de
> descoberta. Escrito em 29/09/2026 para execução autônoma durante a noite, com
> entrega em 30/09 às 9h.
>
> **Regra que vale acima de tudo:** nada do que está em produção é tocado. O
> projeto nasce em `agencia_marketing`, o site atual vive em `juria-lps`, e os
> dois só se encontram no cutover, que não faz parte desta execução.

---

## Decisões já tomadas, para não travar no meio

| Assunto | Decisão | Origem |
|---|---|---|
| Repositório | `agencia_marketing`, pasta `juria-site-astro/` | Guilherme, 29/09 |
| Branch | `feat/site-astro` | brief §2 |
| Canonical | `https://www.juria.app.br` | produção já redireciona apex → www |
| Identidade | mantém a atual: navy `#0A2540` + ciano `#14B4C8` | Guilherme, 29/09 |
| **CSS** | **híbrido: home e mockup com o CSS atual intacto, páginas novas em Tailwind** | Guilherme, 29/09 |
| Referência de movimento | animações do site da ADVBox | Guilherme, 29/09 |
| Propostas visuais | duas, variando **só hero e seção de preços** | Guilherme, 29/09 |
| WhatsApp | botão criado, **sem número**, configurado depois | Guilherme, 29/09 |
| Conteúdo das páginas novas | esqueleto + SEO. Texto final depois | brief §4 |

### Por que o CSS é híbrido

O site atual tem 3.512 linhas de CSS artesanal, e o mockup navegável do
dashboard sozinho ocupa da linha 4247 à 7308, cerca de 3.000 linhas de markup
com prefixo `jm-`. Converter isso para classes utilitárias é o maior bloco de
trabalho da execução e coloca em risco o critério de "sem diferença visual
perceptível" justamente na página que recebe o tráfego pago.

Então: os tokens do brandbook são a fonte única, o Tailwind lê deles, a home
entra com o CSS que já está validado, e as dez páginas novas nascem em Tailwind.

---

## Fase 0 · Fundação ✅ concluída em 29/09, 20h40

1. Branch `feat/site-astro`
2. `juria-site-astro/` com Astro `7.3.5` e Tailwind `4.3.3`, output `static`,
   sem SSR. Mais `@astrojs/sitemap`
3. Tokens do brandbook em `src/styles/tokens.css`, extraídos das linhas 109 a
   143 do `institucional/index.html`
4. Base global em `src/styles/global.css`
5. `.gitignore` para `node_modules/`, `dist/` e `.astro/`

**Critério de pronto:** `npm run build` passa e `npm run preview` serve. ✔

### Três coisas da fase 0 que valem para todas as fases seguintes

**O tema vive em CSS, não em `tailwind.config.js`.** Tailwind 4. Cor, fonte e
sombra se declaram em `@theme static` dentro de `tokens.css`. Não criar
`tailwind.config.js`.

**O `static` do `@theme` não é decorativo.** Sem ele o Tailwind poda do `:root`
toda variável que nenhuma utility usou, e o CSS portado da home, que é CSS puro,
perde o valor sem erro nenhum aparecer. Foi o que aconteceu com as cinco
sombras no primeiro build.

**Toda classe portada de produção entra em `@layer site`.** Nunca em
`components`. A layer `site` é declarada depois de `utilities` de propósito,
para que classe de produção vença utility do Tailwind de mesmo nome. Já
aconteceu com `.container`: a do Tailwind, com `max-width` até 96rem, deixava a
home mais larga que em produção.

---

## Fase 1 · Dados antes de tudo

`src/data/` com o que hoje está espalhado pelo markup:

- `planos.ts`: quatro planos, direto do `comercial/planos-e-creditos.md`
- `funcionalidades.ts`: as 20+, com quais pertencem ao Solo
- `faq.ts`: perguntas e respostas, já corrigidas
- `site.ts`: domínio, CNPJ `03.211.032/0001-24`, fundação 1999 (era 2000, corrigido pela Mobiletec em 21/10/2026), IDs de tracking

**Por que primeiro:** preço hardcoded em três lugares foi exatamente o que deu
retrabalho em 29/09. Nenhum número pode existir fora daqui.

**Critério de pronto:** nenhum preço, limite ou nome de plano escrito em `.astro`.

---

## Fase 2 · Componentes

Extraídos do HTML atual **sem mudar aparência**: `Header`, `Footer`, `Hero`,
`SectionHeader`, `FeatureCard`, `PricingCard`, `FaqAccordion`, `CtaBlock`,
`TrustBadges`, `Mockup`.

O `Mockup` é o diferencial competitivo do site. JS vanilla, copiado como está,
sem virar ilha. Precisa funcionar no celular.

**Critério de pronto:** home renderiza só com componentes, zero HTML solto.

---

## Fase 3 · Home

Seis âncoras vivas: `#recursos`, `#inteligencia`, `#precos`, `#faq`, `#mockup`
e `#cta`. Copy preservada integralmente, incluindo as correções de 29/09.

**Critério de pronto:** diff visual contra a atual sem diferença perceptível, e
as seis âncoras rolando para o lugar certo.

---

## Fase 4 · Páginas

Onze indexáveis, cada uma com layout, headings semânticos, SEO completo e
blocos `{{ TODO }}` marcados: `/`, `/precos`, `/software-juridico`,
`/gestao-de-processos-e-prazos`, `/jurimetria`, `/due-diligence-juridica`,
`/ia-para-advogados`, `/alternativas-ao-advbox`, `/alternativas-ao-astrea`,
`/alternativas-ao-projuris`, `/sobre`.

`/lp/*` com `noindex, nofollow` e fora do sitemap.
`/blog` e `/blog/[slug]` como estrutura vazia, via content collections.

⚠️ **Comparativos:** só entra fato verificável na página pública do concorrente.
Afirmação sobre produto alheio sem fonte não entra, vira `{{ TODO }}` com a
pergunta anotada.

⚠️ **Nada de depoimento, logo de cliente, número de uso ou case inventado.**

---

## Fase 5 · SEO técnico e busca com IA

- `title`, `description`, canonical absoluto, OG e Twitter por página
- Um `H1` por página
- `sitemap.xml` via `@astrojs/sitemap`, sem `/lp/*`
- `robots.txt` e `llms.txt` na raiz
- JSON-LD: `Organization`, `SoftwareApplication` com `AggregateOffer` e um
  `Offer` por plano, `FAQPage`, `BreadcrumbList`
- Formato pergunta → resposta direta em 2-3 frases, que é o que modelo extrai
- Número concreto sempre no HTML, nunca só em imagem

---

## Fase 6 · Tracking

Risco baixo, porque só o GTM está no HTML (ver brief §8 corrigida).

1. Bloco de Consent Mode no `<head>`, **antes** do snippet do GTM. Ordem não é
   estilo: invertida, as tags de inicialização disparam mesmo para quem se opôs
2. Snippet `GTM-WHQGLTXC` na mesma posição
3. Presente em todas as páginas, inclusive `/lp/*`
4. UTMs sobrevivem à navegação interna

**Não criar evento novo.** `ClickTrial` foi removido em 23/09 e não volta.

---

## Fase 7 · As duas propostas visuais

Variação só de **hero** e **seção de preços**, sobre a mesma identidade.

- `/`: proposta A
- `/v2`: proposta B, `noindex`

Movimento inspirado na ADVBox, respeitando `prefers-reduced-motion`.

---

## Fase 8 · Validação e relatório

Checklist do brief §9, e mais: `RELATORIO-decisoes.md` com **toda escolha que
eu fiz sozinho e por quê**, para aprovar ou mandar refazer.

---

## O que NÃO entra nesta execução

- Tocar em qualquer arquivo do `juria-lps`
- Deploy em produção ou alteração de projeto Vercel
- Conteúdo final das páginas novas
- Posts de blog
- Número de WhatsApp
- Depoimento, logo, case ou número de uso
