---
tipo: cliente-doc
cliente: juria
atualizado: 2026-11-27
autor: claude
origem: agencia_marketing, clients/juria/RELATORIO-decisoes.md (migrado em 27/11/2026)
---
# Relatório de decisões · site JurIA em Astro

> **Para o Guilherme, 30/09/2026.** Oito fases executadas, da fundação à
> validação. Este documento é a lista do que eu decidi sozinho, o que eu **não**
> decidi de propósito, e o que ficou faltando.
>
> O log fase a fase e as decisões em detalhe estão em
> [[04-clientes/juria/site/estado|ESTADO-site-astro.md]]. Aqui é o resumo para aprovar ou
> mandar refazer.

---

## O que existe agora

Branch `feat/site-astro`, pasta `juria-site-astro/`. Nada em produção foi tocado.
Nenhum deploy, nenhuma alteração na Vercel.

| | |
|---|---|
| Páginas | 14: home, 10 indexáveis, `/blog`, modelo de `/lp`, e `/v2` |
| Componentes | 16, mais 2 layouts |
| CSS portado de produção | 5.349 linhas, conferidas byte a byte |
| JS portado | 748 linhas |
| Conferências automáticas | 28 de dados, 21 de página, 44 no navegador, 11 de porte |
| Peso do build | 760 KB |

**Para ver rodando:** `cd juria-site-astro && npm ci && npm run build && npm run preview`.

---

## As três coisas que eu mais preciso que você olhe

### 1. Duas frases de copy caíram, e estão marcadas na página

As duas prometiam "todas as funcionalidades" fora do contexto "do Plus em
diante", que é o erro corrigido em 29/09. A versão certa existe no `juria-lps`,
commit `edd7c77`, que não está clonado aqui. **Não inventei substituta.** As duas
aparecem na home como `{{ TODO }}` visível:

- 2ª frase do lede do hero
- lede da seção `#precos`

**É o item mais rápido de resolver e o único que impede a home de estar pronta.**

### 2. Inventei um tratamento visual, e é o único

O plano Ilimitado tem selo na tela do produto e não é o card destacado. Produção
não tinha esse caso, porque o selo era efeito colateral da classe `.featured`.
Fiz o selo do card não destacado com a mesma geometria e cor invertida. A
alternativa era não mostrar o selo do Ilimitado. Está em `styles/ajustes.css`,
item 3, e é apagar um bloco se você preferir.

### 3. A proposta B é uma aposta minha, em dois pontos

- **Hero:** título primeiro e maior, autoridade em pílula abaixo. A aposta é que
  em tráfego pago a promessa tem que ser lida antes de quem fez.
- **Preços:** Solo, Plus e Max em três colunas, Ilimitado numa faixa embaixo. A
  aposta é que o plano que não se compra pelo site não deve ocupar um quarto da
  largura disputando atenção com o "Mais escolhido".

`/v2`, com tarja na tela, `noindex` e fora do sitemap.

---

## O que eu descobri e que você provavelmente não sabia

**O espelho do site neste repositório está defasado.**
`clients/juria/lps/institucional/index.html` é anterior a 29/09: mostra R$ 199,
"14 dias" e Basic/Pro/Enterprise. Descobri comparando o FAQ dele com o `faq.ts`
que a fase 1 já tinha escrito corrigido. Isso mudou o método da migração inteira:
o espelho virou fonte só de CSS, JS, markup e estrutura, e todo número de plano
passou a sair de `src/data/`.

**Produção levanta um erro de JavaScript a cada carregamento de página.** O bloco
`<script id="mockups-novos-v2-scripts">` procura `#mg-gestao`, `#mg-pipeline` e
`#mg-precedentes` sem testar o resultado, e nenhum dos três existe no HTML. É
sobra de uma versão anterior do mockup. No site novo ele fica portado, para o
registro, e fora da página.

**O JSON-LD de produção anuncia os preços velhos.** Basic 199, Pro 499,
Enterprise 1299, em dado estruturado. Isso vira preço errado no resultado de
busca e na resposta de IA, sem ninguém ver. **Vale corrigir no site atual antes
do cutover**, é uma edição pequena e o tráfego pago está rodando agora.

**A coluna "Operação" do tour diz 11 funcionalidades e lista 12.** No site novo o
número é derivado da lista, então mostra 12.

**A UTM morreria na navegação interna.** Problema que a própria migração cria: o
site atual é um one-pager, então a query nunca se perde. Com onze páginas, quem
cai em `/?utm_source=meta` e clica em "Preços" perde a atribuição no
`ViewRegister`. Resolvido guardando a UTM em `sessionStorage`.

---

## O que eu não decidi, de propósito

Nada disso entrou no site, e nada disso eu chutei:

| O que falta | Onde está marcado |
|---|---|
| As duas frases de copy do item 1 | `{{ TODO }}` visível na home |
| Número de WhatsApp e mensagem padrão | `src/data/site.ts`, botão já montado |
| Todo fato sobre ADVBox, Astrea e Projuris | as 3 páginas de comparativo |
| Conteúdo final das 10 páginas novas | `{{ TODO }}` em cada seção |
| "Os dados do escritório treinam a IA?" | `/ia-para-advogados`, marcado como sensível |
| Sistemas e clientes que a Mobiletec pode citar | `/sobre` |
| Posts de blog | estrutura pronta, zero post |
| Imagem OG 1200x630 | não existe, nem em produção |

---

## Perguntas em aberto

Estão em [[04-clientes/juria/site/estado|ESTADO-site-astro.md]], seção "Perguntas para o
Guilherme". Resumo:

1. As duas frases de copy que caíram
2. "25 anos de software house" vira 26 em 2026. Atualizo, troco por "mais de 25",
   ou deixo?
3. "5 usuários simultâneos" no card: a tabela oficial chama de "usuários do
   escritório", que é assento, não acesso concorrente
4. O tour passou a mostrar 12 em vez de 11. Confirma que 12 é o certo?
5. Seis travessões dentro do mockup, nos dados de exemplo. Troco?
6. O link "Entrar" não repassa UTM, e produção também não. Coloco?
7. `Inter Tight` continua sendo baixada e não usada, igual a produção

---

## Checklist do brief §9

Marcado com o que dá para verificar sem deploy, que é a restrição desta
execução. Tudo que depende de preview na Vercel está identificado.

### Não quebrou nada

| Item | Estado |
|---|---|
| `/` carrega e é visualmente equivalente à atual | ✅ 6 das 11 seções idênticas pixel a pixel, as 5 restantes diferindo só pelas correções de 29/09 |
| Âncoras `#recursos`, `#inteligencia`, `#precos`, `#faq`, `#mockup`, `#cta` | ✅ as 6 caem em y=0, em desktop e celular, igual à produção |
| Mockup do dashboard funciona, incluindo mobile | ✅ sidebar monta, palco escala, abas trocam a tela, em 1440px e em 390px |
| Links pro `portal.juria.app.br` intactos | ✅ 7 de `/register` e 1 de `/login`, os mesmos de produção |
| GTM disparando com o ID correto | ✅ `GTM-WHQGLTXC` presente nas 14 páginas. Disparo real depende de deploy |
| Meta Pixel disparando, validado no Pixel Helper | ⏳ **depende de preview.** O Pixel vive dentro do container, não no HTML |
| GA4 registrando pageview, validado no DebugView | ⏳ **depende de preview.** Mesma situação |
| Eventos existentes com nome e parâmetros idênticos | ✅ nenhum evento foi criado, renomeado ou removido. `ClickTrial` não voltou |
| Tracking também nas páginas novas e em `/lp/*` | ✅ conferido página por página, com o Consent Mode antes do GTM |
| UTM sobrevive à navegação interna e chega ao GA4 | ✅ sobrevivência conferida no navegador. Chegada ao GA4 depende de preview |

### Novo funcionando

| Item | Estado |
|---|---|
| Todas as páginas da §4 respondem 200 | ✅ as 11 indexáveis geram HTML |
| `/lp/*` com `noindex` confirmado no HTML servido | ✅ `noindex, nofollow` |
| `sitemap.xml` gerado, sem `/lp/*` | ✅ 12 URLs, sem `/lp/` e sem `/v2` |
| `robots.txt` e `llms.txt` acessíveis | ✅ os dois na raiz. O `llms.txt` é gerado de `src/data/` |
| JSON-LD validado no Rich Results Test | ⏳ **depende de URL pública.** Estrutura conferida localmente: 4 tipos, um `Offer` por plano com o preço de hoje, trilha sem URL repetida |
| Canonical consistente em todas as páginas | ✅ absoluto, com www, apontando para a própria página |
| Um H1 por página | ✅ nas 14. Produção tem 3 na home |

### Qualidade

| Item | Estado |
|---|---|
| Lighthouse mobile: Performance ≥ 90, SEO = 100 | ✅ **roda local, e passou.** Performance 97 na home e 98 em `/precos`, `/blog` e `/lp`. SEO 100 nas indexáveis. Ver a ressalva abaixo |
| Sem erro no console | ✅ zero erro de JS, em desktop e celular. Produção levanta um por carregamento |
| Testado em mobile real | ⏳ **depende de preview.** Conferido em viewport de 390px com emulação de toque |

**A ressalva do Lighthouse, e por que ela não invalida o número.** A execução
anterior deu este item como dependente de preview, e isso estava errado: o
Lighthouse roda contra o `npm run preview` local, sem deploy nenhum. Rodei nas
quatro rotas, em emulação mobile, com o Chromium do próprio ambiente.

O que o número local **não** mede é a entrega: compressão, cache e CDN da
Vercel, que só o preview mostra. Como esses três só melhoram o resultado, 97
local é piso, não teto. O `/lp/exemplo` marca SEO 66 em vez de 100, e está
certo: a única falha é `is-crawlable`, que é o `noindex` que ele tem de
propósito.

**Acessibilidade, que o brief não pediu e o Lighthouse mediu junto:** 92 na home,
93 em `/precos`, 88 em `/blog`. Três achados, nenhum consertado por conta
própria, todos na seção de perguntas do ESTADO:

- **Contraste do CTA primário.** Branco sobre o ciano `#14B4C8` dá 2,5:1, e o
  mínimo da WCAG AA é 4,5:1. O ciano sobre fundo claro dá 2,41:1. Isso é a
  identidade da marca, e vale igual para o site que está no ar: não é regressão
  da migração, e não é decisão de quem porta
- **Quatro botões sem nome acessível**, todos dentro do mockup (`jm-switch`,
  `jm-icobtn`). É markup portado byte a byte, e produção tem os mesmos quatro
- **Hierarquia de heading pula para `<h4>`** no rodapé, em toda página. Estrutura
  de produção, mantida

**Sobre "sem erro no console":** o item segue ✅. O Lighthouse acusa três erros
de rede nas quatro páginas, e os três são `ERR_CERT_AUTHORITY_INVALID` em
`fonts.googleapis.com` e `googletagmanager.com`, que é o proxy TLS do ambiente
onde a conferência rodou, não o site. Zero erro vindo de código nosso.

---

## Como conferir tudo de novo

Rodado assim de novo em 30/09 às 11h15, em ambiente sem `node_modules`: o
`npm ci` montou o projeto do zero pelo lockfile e **as 105 conferências passaram,
nenhuma falha**. É a prova de que o cutover não depende de nada que só exista na
máquina onde o código foi escrito.

```bash
cd juria-site-astro
npm ci
npm run conferir                          # astro check + dados + porte + llms.txt
npm run build
npm run paginas:conferir                  # SEO e tracking no HTML servido

npm i --no-save playwright pixelmatch pngjs
node scripts/conferir-navegador.mjs       # o site funciona, desktop e celular
node scripts/diff-producao.mjs            # o site continua parecido com o que está no ar

npm i --no-save lighthouse                # qualidade, sem precisar de deploy
npm run preview -- --port 4400 &
CHROME_PATH=$(ls -d /opt/pw-browsers/chromium-*/chrome-linux/chrome | head -1) \
  npx lighthouse http://127.0.0.1:4400/ --only-categories=seo,accessibility,best-practices,performance
```

---

## O que vem depois, e não fez parte desta execução

1. Responder as perguntas acima e preencher os `{{ TODO }}`
2. Escrever o conteúdo das 10 páginas novas
3. Preview na Vercel, e aí fechar os 5 itens ⏳ do checklist
4. Cutover, que é problema à parte: o site em produção vive no `juria-lps`, com
   `vercel.json` compartilhado com `trabalhista` e `previdenciario`
