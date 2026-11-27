---
tipo: cliente-doc
cliente: mobiletec
atualizado: 2026-11-27
autor: claude
origem: agencia_marketing, branch claude/loving-archimedes-rp33cv, clients/mobiletec/PLANO-execucao-site-astro.md (migrado em 27/11/2026)
---
# Plano de execução · site Mobiletec em Astro

> Mesmo modelo do plano do JurIA (`agencia_marketing/clients/juria/PLANO-execucao-site-astro.md`), na
> branch `feat/site-astro`. Fases curtas, cada uma com critério de pronto.

## Decisões já tomadas

| Assunto | Decisão | Origem |
|---|---|---|
| Pasta | `mobiletec-site-astro/` na raiz, docs em `clients/mobiletec/` | Guilherme, 19/10 |
| Base | projeto limpo: só a arquitetura do JurIA, visual do zero | Guilherme, 19/10 |
| Direção | Utilitarian + Modular Typography + Bento | Guilherme, 19/10 |
| Movimento | Lenis + GSAP ScrollTrigger + three.js | Guilherme, 19/10 |
| Escopo da 1ª rodada | fundação + home completa | Guilherme, 19/10 |
| Deploy | projeto Vercel `site-mobiletec`, só ele | Guilherme, 19/10 |

## Fases

| Fase | Entrega | Critério de pronto |
|---|---|---|
| 0 · Fundação | Astro 7, Tailwind 4, tokens, fontes locais, motor de movimento | `astro check` e build limpos |
| 1 · Home | 7 blocos com copy de lastro e `{{ TODO }}` onde falta dado | `paginas:conferir` verde, capturas a 390 e 1440px, com movimento e reduzido |
| 2 · Identidade | Logo, paleta e domínio da Mobiletec | Troca só em `tokens.css`, `site.ts` e `Header`/`Footer` |
| 3 · Conteúdo | Serviços, números, órgãos públicos, contato | `{{ TODO }}` da home em zero |
| 4 · Páginas | As que a Mobiletec pedir (Sobre, Soluções, Contato) | Mesma conferência da fase 1 |
| 5 · SEO e tracking | Sitemap, canonical, robots liberado, GTM com Consent Mode antes | Só com domínio definido |
| 6 · Publicação | Projeto Vercel próprio | Só com pedido do Guilherme |
