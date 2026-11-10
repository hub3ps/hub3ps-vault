---
tipo: processo
atualizado: 2026-11-10
autor: claude
---
# Criar o hub de um cliente novo

Só com tráfego pago no escopo. O hub é o painel que o cliente lê, em
`<slug>.hub3ps.com`. A base é o hub do DS Muay Thai, o mais simples: HTML
estático, sem build, com os números gerados por um script local. Faz parte da
fase 4 da [[novo-cliente|entrada de cliente novo]].

O código do hub vive no repo `agencia_marketing`. Todos os comandos abaixo rodam
da raiz dele, `~/Desktop/agencia_marketing`.

| Onde, no `agencia_marketing` | O quê | Edita à mão? |
|---|---|---|
| `clients/<slug>/hub/*.html` e `_shared/` | Páginas e estilo | Sim, é fonte |
| `clients/<slug>/ferramentas/montar-hub.py` | Números, leitura do período | Sim, é fonte |
| `hub/dados.json` e o que o script gerar | Saída do script | **Nunca** |

## 1. Copiar a base

```bash
mkdir -p clients/<slug>/hub clients/<slug>/ferramentas
cp -r clients/dsmuaythai/hub/{_shared,index.html,plano.html,vercel.json} clients/<slug>/hub/
cp clients/dsmuaythai/ferramentas/montar-hub.py clients/<slug>/ferramentas/
```

No script, tire o que é do DS Muay Thai: `AGENDAMENTOS` (Calendly), `IMAGENS` e
o simulador (página Instagram). Esvazie `CAMPANHAS`, `DIARIO`, `ALCANCE` e
`LEITURA`, troque a conta da Meta no cabeçalho e ajuste as colunas de `DIARIO`
aos eventos do funil do cliente. Nas páginas, troque nome, logo e cores pelos da
marca do cliente, e tire o link da página Instagram se ela não existir.

**Confira:** as páginas têm `<meta name="robots" content="noindex, nofollow">`.
O hub mostra número do cliente e não pode cair no Google.

## 2. Primeiros números

Puxe a conta pelo MCP da Meta, rode o script e confira local, como nos passos 1
a 5 do runbook de atualização do DS Muay Thai
(`docs/processos/atualizar-hub-dsmuaythai.md` do `agencia_marketing`, ainda não
migrado). Sem campanha no ar ainda, o hub sobe com o Plano preenchido e a
Performance vazia.

## 3. Commit e push antes do Vercel

```bash
git add clients/<slug>/hub clients/<slug>/ferramentas/montar-hub.py
git commit -m "feat(<slug>): hub do cliente"
git push origin main
```

A pasta precisa estar no GitHub antes do passo 4: sem isso, o painel do Vercel
não mostra a pasta como raiz.

## 4. Projeto no Vercel (Guilherme, pelo painel)

O MCP do Vercel lê o time, mas não cria projeto (403). No painel, time
`hub3psmarketing`:

- **Repositório:** `hub3ps/agencia_marketing`
- **Nome do projeto:** `<slug>`
- **Root Directory:** `clients/<slug>/hub`
- **Framework:** Other, sem comando de build

Ligado ao Git, todo push na `main` publica o hub. (O do DS Muay Thai não está
ligado e pede deploy manual: não repita.)

## 5. Domínio (Guilherme, pelo painel)

1. No projeto do Vercel, em Domains, adicione `<slug>.hub3ps.com`
2. Na Cloudflare, zona `hub3ps.com`: CNAME `<slug>` com o valor que o Vercel
   mostrar, **proxy desligado** (nuvem cinza)

**Confira:**

```bash
curl -sI https://<slug>.hub3ps.com/ | head -1
```

Tem que voltar `200`.

## 6. Registrar

- Runbook de atualização do cliente: copie o do DS Muay Thai para
  `03-processos/atualizar-hub-<slug>.md`, com a conta, os eventos e o endereço do
  cliente, e ponha a linha no [[03-processos/README|índice dos processos]]
- No `cliente.md` do cliente, o campo `painel` com o endereço e o projeto Vercel
- Linha no log do cliente e no `00-sistema/log-operacoes.md`
