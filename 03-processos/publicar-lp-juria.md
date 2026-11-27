---
tipo: processo
atualizado: 2026-11-27
autor: claude
origem: agencia_marketing/docs/processos/publicar-lp-juria.md (migrado em 27/11/2026)
---
# Publicar uma LP · JurIA

> Caminhos de arquivo e comandos são do repo `agencia_marketing` (`~/Desktop/agencia_marketing`), salvo quando outro repo é citado.

> ⚠️ **Desde 12/11/2026 este runbook é histórico.** O site no ar passou a ser o
> site novo em Astro, e as LPs antigas saíram do `juria-lps`. Para publicar,
> use [[publicar-site-juria|publicar-site-juria.md]].

> ⚠️ **O erro que mais custa tempo:** dar push só neste repositório **não**
> atualiza o site público. As LPs públicas vêm do repo `juria-lps`
> (clone local em `~/Desktop/juria-lps`).

| Repo | Projeto Vercel | Serve | Domínios |
|---|---|---|---|
| `agencia_marketing` (este) | `juria` | Hub interno | `juria.hub3ps.com` |
| `juria-lps` (separado) | `juria-lps` | **LPs públicas** | `juria.app.br` e subdomínios |

O Vercel só serve arquivos estáticos. **Não há build no Vercel:** o build roda
na sua máquina e a saída é commitada.

---

## Caso A · LP React (`geral`, `trabalhista`, `previdenciario`)

**1. Edite a FONTE.** Nunca o `index.html` buildado, que é sobrescrito.

```
clients/juria/source/lp_<slug>/
```

**2. Rebuilde.**

```bash
cd clients/juria/lps/_build
npm install
npm run build          # grava clients/juria/lps/<slug>/index.html + assets/
```

**3. Commite aqui** (histórico + espelho).

```bash
git add clients/juria/source clients/juria/lps
git commit -m "feat(juria): <o que mudou na LP>"
git push origin main
```

**4. Publique de verdade**, sincronizando o build para o repo público.

```bash
rsync -a --delete clients/juria/lps/<slug>/ ~/Desktop/juria-lps/<slug>/
cd ~/Desktop/juria-lps
git add -A && git commit -m "feat: <o que mudou>" && git push
```

O push no `juria-lps` é o que dispara o deploy de produção.

## Caso B · Página estática (`institucional`, `privacidade`, `termos`, `cookies`, `eventos`, `integracao`, `instagram`, `oab`)

Sem build. Edite o `index.html` **nos dois repos** e dê push em cada um:

```
clients/juria/lps/<pagina>/index.html      (espelho)
~/Desktop/juria-lps/<pagina>/index.html    (produção)
```

> Estas páginas existem em cópia nos dois repositórios e **podem divergir**. A
> de produção é a do `juria-lps`. Editar só uma é como o drift começa.

## Caso C · Hub interno (`clients/juria/lps/index.html`)

Mora só aqui. Push na `main` publica. Para as métricas do painel, use
[[atualizar-hub-juria|atualizar-hub-juria.md]]. Não edite o JSON na mão.

## Caso D · Painel do funil (`funil.juria.hub3ps.com`)

Mora só aqui, no mesmo projeto Vercel do hub, e não é linkado no hub. A página
`clients/juria/lps/funil/index.html` é **gerada**: edite o modelo
`clients/juria/funil/pagina.html` ou os dados, e rode
`python3 clients/juria/ferramentas/gerar-funil.py` (passos completos em
`clients/juria/funil/README.md`). Push na
`main` publica.

O domínio próprio funciona por **redirecionamento** no `lps/vercel.json`, não por
reescrita: no Vercel, arquivo existente vence a reescrita, e a raiz `/` cairia no
`index.html` do hub. O DNS do `hub3ps.com` está na Cloudflare: o registro é um
CNAME `funil.juria` com proxy desligado.

---

## Conferir o deploy

```bash
curl -s https://juria.app.br/ | grep portal.juria.app.br
```

Ou pelo MCP do Vercel: `list_deployments` no time `hub3psmarketing`, projeto
`juria-lps` (`prj_rhGkSkYLQby3Mr7shf4sqOPGVtQw`).

## Antes de mexer em botão ou link

Os CTAs seguem um padrão e repassam UTM (`data-forward-utm`). Leia a seção 4 do
`clients/juria/README.md` antes. Punch-list aberta em
`clients/juria/source/lps-botoes-pendencias.md`.
