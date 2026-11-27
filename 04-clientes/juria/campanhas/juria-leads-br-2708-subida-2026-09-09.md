---
tipo: cliente-doc
cliente: juria
atualizado: 2026-11-27
autor: claude
origem: agencia_marketing, clients/juria/campanhas/subida-inst-c-d-2026-09-09.md (migrado em 27/11/2026)
---
# Subida dos criativos INST-C-01 e INST-D-01 · 09/09/2026

Duplicar o conjunto ativo da campanha Brasil Institucional e subir os dois
criativos estáticos novos, cada um com sua UTM, deixando tudo pausado para
revisão.

**Resultado: parcial.** O conjunto e as imagens subiram. Os anúncios não, e a
trava é a mesma que o repositório já registrava.

---

## ✅ O que ficou pronto na conta

### Conjunto duplicado, pausado

| | |
|---|---|
| **ID** | `120249009735710208` |
| Nome | `Ad Set-INST · Aberto · Brasil 28-60 · Estáticos` |
| Status | **PAUSED** |
| Campanha | `120248881937880208` · JurIA · Meta · Leads · Brasil · Institucional |

Conferido campo a campo contra o conjunto de origem (`120248881942670208`).
Idênticos: orçamento R$ 27,00/dia, cobrança por impressões, meta
`OFFSITE_CONVERSIONS`, lance `LOWEST_COST_WITHOUT_CAP`, destino `WEBSITE`,
pixel `1009120801605718` com evento `LEAD`, atribuição 7 dias clique + 1 dia
visualização, idade 28 a 60, Brasil, Advantage+ Audience desligado.

⚠️ **Uma diferença que não deu para eliminar:** o `location_types` do conjunto
novo saiu como `frequently_in, home, recent`, contra `home, recent` no original.
Enviei o valor certo duas vezes e a Meta reescreve sozinha, é normalização do
lado dela para segmentação por país. Na prática adiciona quem frequenta o Brasil
sem morar aqui, o que numa campanha nacional é ruído. Se incomodar, ajusta no
Ads Manager.

### Imagens na biblioteca da conta

| Criativo | Hash | Dimensão |
|---|---|---|
| `INST-C-01_inst_um_sistema_v1.jpg` | `55efce4b65fe0520b0c2d5825548eee0` | 1080×1080 |
| `INST-D-01_inst_precedentes_v1.jpg` | `cfdc17944ddf3dcb4d3aca93a9b991ff` | 1080×1350 |

Já aparecem na biblioteca de imagens do Ads Manager, é só selecionar.

---

## ❌ O que travou: criação do anúncio pela API

```
error_subcode: 1885183
"O post do criativo dos anúncios foi criado por um app que está em modo de
 desenvolvimento. Ele deve estar em modo público para criar este anúncio."
```

É exatamente o que o `creatives/meta-ads/README.md` já registrava na seção do
refresh trabalhista: *"a API recusa enquanto o app Meta da Hub3Ps estiver em modo
de desenvolvimento"*. Agora com o código do erro.

**Não é a mesma trava do MCP.** Aquela é rollout da Meta, conta a conta, sem ação
nossa. Esta tem solução: **publicar o app da Hub3Ps** no painel de
desenvolvedores, saindo do modo de desenvolvimento. Feito isso, subir anúncio por
API passa a funcionar em toda a carteira, não só aqui.

Enquanto não for feito, todo anúncio novo precisa ser montado à mão.

---

## ✅ Montado à mão em 09/09/2026

O Guilherme montou os dois anúncios no Ads Manager, contornando a trava do app.
Confirmado na API em 10/09:

| Anúncio | ID | Status |
|---|---|---|
| `INST-C-01-Estático-Um-Sistema` | `120249021905510208` | `PENDING_REVIEW` |
| `INST-D-01-Estático-Precedentes` | `120249022093790208` | `PENDING_REVIEW` |

O conjunto `120249009735710208` foi **ativado**. Assim que os anúncios saírem da
análise, começam a entregar e a consumir os R$ 27,00/dia.

Os três já estão cadastrados nos catálogos do `gerar-dados-campanha.py`, então a
próxima atualização do painel os inclui nas tabelas por criativo e por público.

### Copy usada

Cinco variações por campo, em
`hub3ps-vault/04-clientes/juria/copies/juria-leads-br-2708/`.

## Sobre as UTMs

`utm_term=geral_aberto`, igual ao anúncio que já roda. **Correção de registro:**
o `br-institucional-2708.md` afirmava que o anúncio tinha ficado com
`utm_term=geral_interesses` por não terem refeito a URL. Lendo o criativo ao
vivo, ele está com `geral_aberto`. A ressalva registrada lá estava errada e foi
removida.

`utm_content` é o que distingue os dois criativos no relatório, seguindo a
convenção do `DIRETRIZES-COPY.md`: o conjunto define o `utm_term`, o criativo
define o `utm_content`.

---

## Pendente antes de publicar

- ⬜ Montar os dois anúncios à mão, pelo passo a passo acima
- ✅ ~~5 variações de copy do INST-C-01~~ em
      [[04-clientes/juria/copies/juria-leads-br-2708/2026-09-09-INST-C-01|../copies/juria-leads-br-2708/2026-09-09-INST-C-01.md]]
- ✅ ~~5 variações de copy do INST-D-01~~ em
      [[04-clientes/juria/copies/juria-leads-br-2708/2026-09-09-INST-D-01|../copies/juria-leads-br-2708/2026-09-09-INST-D-01.md]]
- ⬜ Cortes que faltam: 4:5 e 1.91:1 do INST-C-01, 1:1 e 1.91:1 do INST-D-01
- ⬜ Publicar o app da Hub3Ps, para a próxima subida ser automática
