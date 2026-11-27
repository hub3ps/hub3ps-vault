---
tipo: cliente-doc
cliente: juria
atualizado: 2026-11-27
autor: claude
origem: agencia_marketing, clients/juria/campanhas/9estados-institucional-1409.md (migrado em 27/11/2026)
---
# Campanha 9 Estados · Institucional · montagem

> ⚠️ **DESATIVADA EM 30/09/2026**, junto com as demais. Os planos foram
> reestruturados em 29/09 e o trial caiu de 14 para 7 dias, então ela anunciava
> preço, plano e prazo que não existem mais, inclusive dentro da arte.
> Substituída pela [[04-clientes/juria/campanhas/juria-leads-9estados-3009|9 Estados Institucional · View_Register]].

Criada via MCP da Meta em 14/09/2026, réplica da campanha Brasil Institucional
com dois ajustes pedidos pelo Guilherme: posicionamento manual (só Facebook e
Instagram) e localização restrita a 9 estados.

## IDs

| Nível | Nome | ID |
|---|---|---|
| Campanha | JurIA · Meta · Leads · 9 Estados · Institucional | `120249074673920208` |
| Conjunto | Ad Set-INST · Aberto · 9 Estados 28-60 · Estáticos | `120249074781200208` |
| Anúncio | INST-A-01-Estático-Rende-Mais | `120249074811260208` |
| Anúncio | INST-B-01-Estático-Cinco-Sistemas | `120249075126420208` |

> ⚠️ **O conjunto trocou de ID.** O que a API criou (`120249074683700208`) saiu
> de cena e o que está no ar é o `120249074781200208`, remontado à mão pelo
> Guilherme em 14/09 junto com os dois anúncios. O ID antigo não vale mais para
> nada, nem para relatório.

**Estado em 14/09:** conjunto ativo a R$ 27,00/dia, os dois anúncios já fora da
análise e entregando. Os dois estão cadastrados no `gerar-dados-campanha.py`,
então aparecem nas tabelas do painel no próximo ciclo, quando tiverem gasto.

Esta campanha substitui a Brasil Institucional, pausada inteira em 14/09.
Ver [[04-clientes/juria/campanhas/juria-leads-br-2708|br-institucional-2708.md]].

⚠️ **Os dois criativos dividem o mesmo conjunto.** Foi assim que o INST-D-01
ficou sem entrega na campanha anterior: o leilão concentra a verba em quem
responde melhor nos primeiros dias. Se em alguns dias um dos dois estiver
parado, separar cada um no seu conjunto.

Copiados com `source_campaign_id` (`120248881937880208`, campanha Brasil
Institucional) e `source_adset_id` (`120249009735710208`, Ad Set-INST ·
Aberto · Brasil 28-60 · Estáticos, o conjunto que já hospeda INST-C-01 e
INST-D-01).

- [Abrir a campanha no Ads Manager](https://www.facebook.com/adsmanager/manage/campaigns/edit?act=1465935581974017&selected_campaign_ids=120249074673920208)
- [Abrir o conjunto](https://www.facebook.com/adsmanager/manage/adsets/edit?act=1465935581974017&selected_adset_ids=120249074683700208)

Ambos nasceram **PAUSED**, como toda campanha e conjunto criados por API.

## Configuração replicada

| Campo | Valor |
|---|---|
| Objetivo | `OUTCOME_LEADS` · leilão |
| Meta de performance | `OFFSITE_CONVERSIONS` (igual ao conjunto de origem, não a recomendação padrão `LEAD_GENERATION` que a ferramenta sugere) |
| Cobrança | Impressões |
| Lance | Highest volume (`LOWEST_COST_WITHOUT_CAP`) |
| Orçamento | R$ 27,00/dia, no conjunto (ABO) |
| Evento | Pixel `1009120801605718`, `LEAD` |
| Atribuição | 7 dias clique + 1 dia visualização (default) |
| Idade | 28 a 60, hard cap (`targeting_automation.advantage_audience` desligado) |
| Destino | Website |

## ⚠️ Localização: nasceu Brasil, não os 9 estados

A API de targeting do Meta exige um `region key` numérico por estado, não
aceita só o nome, e não havia ferramenta disponível nesta sessão para resolver
esses keys com segurança. Decisão do Guilherme em 14/09: o conjunto nasce
com Brasil inteiro e ele mesmo troca pelos 9 estados no Ads Manager.

**Estados pretendidos:** São Paulo, Rio de Janeiro, Minas Gerais, Rio Grande
do Sul, Paraná, Bahia, Goiás, Santa Catarina e Distrito Federal.

⬜ **Pendente:** trocar a localização do conjunto `120249074683700208` pelos
9 estados acima, direto no Ads Manager.

## Posicionamento: manual, só Facebook e Instagram

Diferente do institucional original (posicionamento automático), este
conjunto restringe a:

| Plataforma | Posições |
|---|---|
| Facebook | Feed, Stories, Reels |
| Instagram | Feed, Stories, Reels |

Sem Audience Network, sem Messenger, sem coluna direita nem Marketplace.

## ❌ Upload de imagem: mesma trava de sempre

Tentei subir `INST-A-01_inst_ia_v1.jpg` e `INST-B-01_inst_sistemas_v1.jpg`
pela API (`ads_creative_upload_local_image`) e caiu na mesma mensagem já
registrada em `subida-inst-c-d-2026-09-09.md`:

> "This tool is new and is being gradually rolled out across ad accounts.
> Please check back at a later date."

Não é a trava do app em modo de desenvolvimento (essa é a de criar o
*anúncio*, mais adiante). Esta é upload de mídia, rollout gradual da Meta,
mesma raiz do bloqueio do vídeo institucional.

⬜ **Pendente:** subir as duas imagens à mão na biblioteca de imagens da
conta (Ads Manager, biblioteca de anúncios), mesmo caminho usado para
INST-C-01 e INST-D-01.

## O que falta antes de publicar

- ⬜ Ajustar a localização para os 9 estados (acima)
- ⬜ Subir as duas imagens à mão na biblioteca
- ⬜ UTMs dos dois criativos: a pedido do Guilherme, fica para depois
- ⬜ Copy dos dois anúncios (5 variações por campo): a pedido do Guilherme, fica para depois
- ⬜ Montar os dois anúncios à mão no Ads Manager, mesma trava de app em modo
  de desenvolvimento que travou INST-C-01 e INST-D-01
