---
tipo: arquivo
cliente: juria
atualizado: 2026-11-27
autor: claude
origem: agencia_marketing, clients/juria/source/lps-botoes-pendencias.md (migrado em 27/11/2026)
---
# JurIA — Pendências de botões nas LPs

> Punch-list de correções de botões/links levantadas na revisão manual das LPs.
> Cada item vira uma correção depois (fonte em `source/lp_*` ou página estática,
> + rebuild/sync pro repo `juria-lps` quando for LP pública). Ver `README.md`.

**Legenda de status:** ⬜ pendente · 🔧 em correção · ✅ corrigido & publicado

## ✅ Definições (resolvidas)
- **E-mail de contato:** `contato@juria.app.br` — usar nos botões
  "Falar com especialista" (institucional) e "Falar com vendas"
  (pricing Enterprise) das 3 LPs React.
- **Escopo:** todas as alterações valem também para a LP geral.
- **CNPJ:** `03.211.032/0001-24` · "Mobiletec Sistemas Ltda".

> ✅ **Lote aplicado e publicado em 2026-07-14** — commits `90ce145` (agencia_marketing)
> e `9ff214c` (juria-lps). Verificado ao vivo em `juria.app.br`,
> `trabalhista.juria.app.br` e `previdenciario.juria.app.br`.

---

## Institucional (`juria.app.br` — homepage estática)

- ✅ **Botão "Falar com um especialista"** (CTA final, `index.html:5820`) — hoje
  é `https://wa.me/5547999999999` (número fake). Trocar por `mailto:` com o
  e-mail de contato correto.

## LP Geral (`www.juria.app.br/geral` — React, `source/lp_geral/`)

- ✅ **Rodapé:** remover itens "Mudanças (changelog)" (`cta-footer.jsx:43`),
  "Carreiras" (`:50`), "Imprensa" (`:52`) e "Status" (`:63`).
- ✅ **Rodapé — CNPJ:** trocar `CNPJ 03.xxx.xxx/0001-xx` por
  `CNPJ 03.211.032/0001-24` (`cta-footer.jsx:68`). Nome correto:
  "Mobiletec Sistemas Ltda".
- ✅ **Remover botão "Agendar demonstração"** — 2 lugares: hero (`hero.jsx:46`)
  e CTA final (`cta-footer.jsx:15`).
- ✅ **Botão "Falar com vendas"** (Enterprise, `pricing.jsx:22`) — hoje o CTA
  aponta pro `/register`; trocar por `mailto:` com o e-mail correto.
 

## LP Trabalhista (`trabalhista.juria.app.br` — React, `source/lp_trabalhista/`)

- ✅ **Remover botão "Agendar demonstração"** — 2 lugares: hero (`hero.jsx:46`)
  e CTA final (`cta-footer.jsx:15`).
- ✅ **Botão "Falar com vendas"** (Enterprise, `pricing.jsx:22`) — hoje o CTA
  aponta pro `/register`; trocar por `mailto:` com o e-mail correto.
 
- ✅ **Rodapé:** remover "Mudanças (changelog)" (`:43`), "Carreiras" (`:50`),
  "Imprensa" (`:52`) e "Status" (`:63`).
- ✅ **Rodapé — CNPJ:** `03.xxx.xxx/0001-xx` → `03.211.032/0001-24`
  (`cta-footer.jsx:68`), nome "Mobiletec Sistemas Ltda".

## LP Previdenciário (`previdenciario.juria.app.br` — React, `source/lp_previdenciario/`)

- ✅ **Remover botão "Agendar demonstração"** — 2 lugares: hero (`hero.jsx:62`)
  e CTA final (`cta-footer.jsx:15`).
- ✅ **Botão "Falar com vendas"** (Enterprise, `pricing.jsx:22`) — hoje o CTA
  aponta pro `/register`; trocar por `mailto:` com o e-mail correto.
 
- ✅ **Rodapé:** remover "Mudanças (changelog)" (`:43`), "Carreiras" (`:50`),
  "Imprensa" (`:52`) e "Status" (`:63`).
- ✅ **Rodapé — CNPJ:** `03.xxx.xxx/0001-xx` → `03.211.032/0001-24`
  (`cta-footer.jsx:68`), nome "Mobiletec Sistemas Ltda".

## Páginas legais / outras (privacidade, termos, cookies, eventos, integracao)

_(sem itens ainda)_

---

### Lembretes de execução (quando formos aplicar)
- LPs React: editar `source/lp_*` → `npm run build` no `_build/` → `rsync` pro
  `~/Desktop/juria-lps/<slug>/` → push nos 2 repos.
- Institucional: editar nos 2 repos (`clients/juria/lps/institucional/` e
  `~/Desktop/juria-lps/institucional/`) → push.
- Rodapé da institucional **não** tem os itens Carreiras/Imprensa/changelog/
  Status (remoção vale só pras 3 React).
