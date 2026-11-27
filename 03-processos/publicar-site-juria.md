---
tipo: processo
atualizado: 2026-11-27
autor: claude
origem: agencia_marketing/docs/processos/publicar-site-juria.md (migrado em 27/11/2026)
---
# Publicar o site do JurIA

> Caminhos de arquivo e comandos são do repo `agencia_marketing` (`~/Desktop/agencia_marketing`), salvo quando outro repo é citado.

Desde 12/11/2026, o que está no ar em `www.juria.app.br` é o site novo em
Astro. A fonte fica neste repositório, em `juria-site-astro/`. O que vai ao ar é
só o build, copiado para o repo `juria-lps`.

> ⚠️ **O push neste repositório não publica o site.** Ele atualiza só a prévia
> (`site.juria.hub3ps.com`, projeto Vercel `site-novo-juria`, branch
> `feat/site-astro`). Quem publica em produção é o push no `juria-lps`.

| Repo | Projeto Vercel | Serve |
|---|---|---|
| `agencia_marketing`, pasta `juria-site-astro/` | `site-novo-juria` | Prévia, `site.juria.hub3ps.com`, com noindex |
| `juria-lps` (clone em `~/Desktop/juria-lps`) | `juria-lps` | **Produção**: `www.juria.app.br`, `juria.app.br` (308 para o `www`), `trabalhista.` e `previdenciario.` |

**Por que dois repositórios.** O `juria-lps` é separado de propósito: o projeto
da Vercel precisa poder ser transferido para outra pessoa sem levar o monorepo
da agência junto. Ele continua estático e sem build na Vercel, como era com as
LPs antigas.

---

## Passo a passo

**1. Edite a fonte**, em `juria-site-astro/src/`. Texto de produto, preço e
plano saem de `src/data/`, e o número só existe em
`clients/juria/comercial/planos-e-creditos.md`.

**2. Confira.**

```bash
cd juria-site-astro
npm run conferir
npm run build
npm run paginas:conferir
```

**3. Veja na prévia.** Commit e push na `feat/site-astro`, e confira em
`site.juria.hub3ps.com`. A prévia publica dessa branch.

**4. Copie o build para o `juria-lps`.**

```bash
cd ~/Desktop/juria-lps && git pull
cd -
npm run publicar
```

O script para se o `juria-lps` estiver sujo, fora da `main` ou atrás do origin.
Ele troca o conteúdo pelo `dist/` e pelo `vercel.json` e mantém `.gitignore`,
`README.md`, `logos/` e `_shared/`. A `/v2` fica de fora. **Ele não commita
nem dá push.**

**5. Publique**, só com o OK do Guilherme.

```bash
cd ~/Desktop/juria-lps
git status
git add -A && git commit -m "feat: <o que mudou>" && git push
```

**6. Confira no ar** em `www.juria.app.br`: a página mudada, o cabeçalho
`X-Robots-Tag` ausente no `www` e o Pixel e o GA4 disparando. O GTM só libera as
tags nos endereços `juria.app.br`, então isso não dá para conferir na prévia.

**7. Traga para a `main`.** `git merge feat/site-astro` na `main` e push. A
`main` é o registro do que está no ar, e a branch volta a ficar igual a ela.

## Voltar atrás

Pelo painel da Vercel, projeto `juria-lps`, aba Deployments: **Instant
Rollback** para o deploy anterior. Ou `git revert` do último commit no
`juria-lps` e push.

## O que a troca de 12/11 mudou de endereço

| Endereço antigo | Agora |
|---|---|
| `/institucional`, `/geral`, `/trabalhista`, `/previdenciario` | 308 para a home, mantendo a UTM |
| `trabalhista.` e `previdenciario.juria.app.br` | Mostram a home nova, com noindex |
| `/eventos`, `/integracao` | Saíram em 24/09 e seguem fora |
| `/oab` | Mesma página de antes, copiada como está (ajuste pendente no quadro de tarefas do vault) |
| `/termos`, `/privacidade`, `/cookies` | No desenho novo, mesmo texto jurídico |
