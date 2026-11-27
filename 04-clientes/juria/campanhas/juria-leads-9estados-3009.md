---
tipo: cliente-doc
cliente: juria
atualizado: 2026-11-27
autor: claude
origem: agencia_marketing, clients/juria/campanhas/9estados-institucional-3009.md (migrado em 27/11/2026)
---
# Campanha 9 Estados · Institucional · View_Register

Criada em 30/09/2026 e no ar desde 01/10. Substitui a
[[04-clientes/juria/campanhas/juria-leads-9estados-1409|9 Estados Institucional de setembro]], que foi
desativada junto com as demais.

**Dois motivos para ela existir**, e vale separar porque são independentes:

1. **Oferta corrigida.** Os planos foram reestruturados em 29/09 e o trial caiu
   de 14 para 7 dias. As campanhas antigas anunciavam preço, plano e prazo que
   não existem mais, inclusive dentro da arte.
2. **Experimento de otimização.** É a primeira campanha a otimizar para
   **ViewRegister** em vez de Lead.

## IDs

⚠️ **Preencher depois de montar no Ads Manager.** Esta ficha é o único lugar
onde os IDs numéricos do Meta ficam registrados, e o
`ferramentas/gerar-dados-campanha.py` depende deles para cruzar anúncio e
criativo no painel do hub.

| Nível | Nome | ID |
|---|---|---|
| Campanha | JurIA - Leads - 9 Estados - Institucional - View_Register | `{{ TODO }}` |
| Conjunto 1 | Ad Set-INST - Aberto - 9 Estados - 28-60 - Estáticos | `{{ TODO }}` |
| Conjunto 2 | ⚠️ nome não registrado | `{{ TODO }}` |
| Anúncio | INST-B-01-Estático-Cinco-Sistemas | `{{ TODO }}` |
| Anúncio | INST-B-02-Estático-Mudança | `{{ TODO }}` |
| Anúncio | INST-NAT-01-Estático-Notas-Escuro | `{{ TODO }}` |
| Anúncio | INST-NAT-02-Estático-Notas-Claro | `{{ TODO }}` |

## As quatro peças e suas UTMs

`utm_source=meta` · `utm_medium=paid` · `utm_campaign=juria-leads-9estados-3009`
· `utm_term=geral_aberto` em todas. Destino: `https://www.juria.app.br/`.

| Conjunto | Peça | `utm_content` | Copy |
|---|---|---|---|
| 1 | INST-B-01 | `inst_sistemas_v2` | [[04-clientes/juria/copies/juria-leads-9estados-3009/2026-09-30-INST-B-01\|doc]] |
| 1 | INST-B-02 | `inst_mudanca_v1` | [[04-clientes/juria/copies/juria-leads-9estados-3009/2026-09-30-INST-B-02\|doc]] |
| 2 | INST-NAT-01 escuro | `inst_nat_escuro_v1` | [[04-clientes/juria/copies/juria-leads-9estados-3009/2026-09-30-INST-NAT-01-e-02\|doc]] |
| 2 | INST-NAT-02 claro | `inst_nat_claro_v1` | mesmo doc |

⚠️ **O `utm_term` é igual nos dois conjuntos, e é de propósito.** Ele descreve
público, e o público não mudou. Quem separa as quatro peças é o `utm_content`.
Se o público do conjunto 2 for outro, é o único campo a trocar.

⚠️ **O `inst_sistemas_v2` não é erro de digitação.** A arte do INST-B-01 mudou
em 30/09 (selo de 7 dias, PJe e BCB fora), e a chave `v1` carrega o histórico
do anúncio de setembro em `gerar-dados-campanha.py`. Reusar `v1` somaria duas
artes diferentes na mesma linha do painel.

## O que muda na leitura, por causa do ViewRegister

O evento dispara na **abertura de `/register`**: depois do clique e antes do
cadastro. Três consequências:

- **Custo por ViewRegister não é custo por cadastro.** Comparar com o histórico
  de Lead das campanhas antigas mede coisas diferentes.
- O volume de ViewRegister será **maior** que o de Lead, porque nem todo mundo
  que abre a página de cadastro conclui.
- A conversão que importa para o negócio continua sendo o Lead. O ViewRegister
  é sinal para o algoritmo, não meta de negócio.

## O que ficou pendente

| O quê | De quem |
|---|---|
| IDs numéricos do Meta, acima | Guilherme, depois de montar |
| Nome do conjunto 2 | Guilherme |
| Nomes dos clientes da Mobiletec, para a página de autoridade | Mobiletec |

⚠️ **INST-A-01, INST-C-01 e INST-D-01 continuam com "14 dias" na arte** e não
podem subir sem correção. Arquivo e linha de cada um estão no
[[04-clientes/juria/copies/juria-leads-9estados-3009/2026-09-30-INST-B-01|doc do INST-B-01]].
