---
tipo: cliente-doc
cliente: mobiletec
atualizado: 2026-11-27
autor: claude
origem: agencia_marketing, branch claude/loving-archimedes-rp33cv, clients/mobiletec/README.md (migrado em 27/11/2026)
---
# Mobiletec · site institucional

> **Leia isto antes de mexer em qualquer coisa da Mobiletec.**
> Cliente: **Mobiletec Sistemas Ltda** · CNPJ 03.211.032/0001-24 · software
> house de Santa Catarina, desde 2000. É a mesma empresa do JurIA
> (`clients/juria/`), mas aqui o assunto é a **marca Mobiletec**, não o produto.

## O projeto

Site institucional da Mobiletec, aberto em 19/10/2026. Objetivo: transmitir
**seriedade e autoridade** de uma software house com mais de 25 anos e clientes
de grande porte.

O código vive em `mobiletec-site-astro/` (código no repo `agencia_marketing`, branch `claude/loving-archimedes-rp33cv`), na raiz
do repositório, no mesmo modelo do `juria-site-astro/` (branch
`feat/site-astro`): Astro estático, Tailwind 4, dados separados da forma, e
`{{ TODO }}` visível onde falta dado.

**Comece por [[04-clientes/mobiletec/site/estado|ESTADO-site-astro.md]].** Ele diz onde a
execução parou.

## Mapa da pasta

| Arquivo | O que guarda |
|---|---|
| [[04-clientes/mobiletec/site/estado|ESTADO-site-astro.md]] | Onde parou, regras, log por rodada, o que falta |
| [[04-clientes/mobiletec/site/plano-execucao|PLANO-execucao-site-astro.md]] | As fases, cada uma com critério de pronto |
| [[04-clientes/mobiletec/brief|brief.md]] | O que sabemos da Mobiletec, com a fonte de cada fato, e o que falta perguntar |
| [[04-clientes/mobiletec/marca|brand.md]] | Direção visual e de movimento aprovada. Identidade da marca: pendente |
| `assets/logos/` | Vazia. A logo da Mobiletec ainda não chegou |
| `credenciais.local.md` | Cofre, fora do git, se um dia existir |

## Onde está o quê

- **Site:** `mobiletec-site-astro/`. Rodar: `npm ci && npm run dev`.
- **Logos de cliente:** `mobiletec-site-astro/public/logos/clientes/`, os 13 já
  normalizados para o JurIA. Os originais e o script que normaliza
  (`clients/juria/assets/logos-clientes/` e
  `clients/juria/ferramentas/preparar-logos.py`) estão **na branch
  `feat/site-astro`**, não na `main`.
- **Deploy:** projeto Vercel `site-mobiletec`, criado pelo Guilherme em 19/10/2026,
  com Root Directory `mobiletec-site-astro` e framework Astro. Endereço:
  `site-mobiletec-hub3psmarketing.vercel.app`. Sem domínio próprio ainda, e com
  `noindex` (meta, `robots.txt` e o cabeçalho do `vercel.json`) até o lançamento.
  **Domínio: `site.mobiletec.hub3ps.com`** (20/10/2026, CNAME na Cloudflare, verificado).
  É público: a proteção por login da Vercel não vale em domínio próprio. Segue
  com `noindex`.
  **Ligado ao Git, com produção na branch `claude/loving-archimedes-rp33cv`**
  (ajustado pelo Guilherme em 20/10/2026): push nesta branch, com mudança dentro
  de `mobiletec-site-astro/`, publica sozinho no domínio.
