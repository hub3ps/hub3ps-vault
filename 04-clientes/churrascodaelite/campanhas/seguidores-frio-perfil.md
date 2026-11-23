---
tipo: campanha
cliente: churrascodaelite
nome-campanha: Seguidores | Frio | Perfil
plataforma: meta
id-campanha: "120250644049660559"
status: no ar, anúncios em análise (16/11)
inicio: 2026-11-16
verba-diaria: 10
evento-otimizacao: PROFILE_AND_PAGE_ENGAGEMENT
lp: https://instagram.com/churrasco_da_elite
atualizado: 2026-11-16
autor: claude
---
# Seguidores | Frio | Perfil

Captação de seguidores para o @churrasco_da_elite, com quem pode comprar o curso "Faturando com Churrasco" na Black Friday (27 a 30/11). Conta CA01 - Churrasco da Elite `1295259920836612` (BM `666930504135899`), valores em EUR, indicada pelo Guilherme em 16/11. Página `111836513679647`, Instagram @churrasco_da_elite `17841403077087483`. Pedida pelo Guilherme em 13/11, com dois conjuntos e um post em cada.

**Bloqueio resolvido em 16/11:** na conta nova, a Página e o @churrasco_da_elite estão ligados e os posts IG-01 (`18114206996323146`) e IG-02 (`18399703315206330`) aparecem disponíveis para anúncio (MCP, 16/11).

## Configuração proposta
Mesmo desenho da campanha de seguidores da Marjorie ([[04-clientes/marjorie/campanhas/seguidores-frio-perfil|ficha]]), que funcionou lá.

- **Objetivo:** engajamento, com destino no perfil do Instagram, otimizando para visita ao perfil
- **Público:** `Aberto 23-55`, Portugal, idioma português, excluindo quem já engajou com o @churrasco_da_elite em 365 dias (o público `Engajou IG 365d` só se cria com o perfil ligado). A conferir pelo Guilherme
- **Estrutura:** um conjunto por post, com 1 anúncio e 5 € por dia cada, para os dois entregarem no teste
- **Verba:** 10 € por dia até 26/11, cerca de 140 €. Sobram cerca de 310 € dos 450 € de novembro para a base, a LP e a Black
- **Critério de rodízio:** custo por seguidor, como na Marjorie. A cada 3 dias, o pior sai e entra o próximo da [[2026-11-13-posts-para-captacao|lista]]
- **IDs:** `IG-NN` é o número do post na lista de 13/11

| Conjunto | Anúncio | Post | Estado |
|---|---|---|---|
| `Aberto 23-55 \| Portugal \| Visita ao perfil \| IG-01` | `IG-01 \| Reels \| 3 eventos num dia` | [DdgfPAcqGmT](https://www.instagram.com/reel/DdgfPAcqGmT/), 20/09, 196 curtidas, áudio original | no ar desde 16/11 |
| `Aberto 23-55 \| Portugal \| Visita ao perfil \| IG-02` | `IG-02 \| Reels \| Lugares que nunca imaginei` | [Dd_WRoXKN5K](https://www.instagram.com/reel/Dd_WRoXKN5K/), 02/10, 101 curtidas, áudio original | no ar desde 16/11 |

## IDs no ar (API, 16/11)
| Conjunto | ID do conjunto | ID do anúncio | Criativo |
|---|---|---|---|
| IG-01 | `120250644068130559` | `120250644068120559` | `1810905983536126` |
| IG-02 | `120250644175230559` | `120250644175240559` | `1108843141782966` |

Publicados pelo Guilherme à mão, no ar desde 16/11, 18h46 UTC. Na leitura, os anúncios estavam em análise (`IN_PROCESS`).

O que ficou diferente da especificação abaixo, lido na API:
- **Data de fim:** os conjuntos subiram sem data de fim. Pus `end_time` em 26/11, 23h59 de Lisboa, pelo MCP, a pedido do Guilherme, e conferi na leitura (16/11)
- **Advantage+ público desligado:** a idade de 23 a 55 é limite fixo, e não sugestão
- **Com exclusão:** o Guilherme criou o público `seguidores` (`120250644113480559`, quem segue o @churrasco_da_elite) e excluiu dos dois conjuntos. Melhor que a especificação, que não tinha exclusão

## Como subir
Na Marjorie, o MCP não criou conjunto com `PROFILE_AND_PAGE_ENGAGEMENT` (12/11), e a subida foi à mão. **Aqui aconteceu o mesmo em 16/11:** o Claude criou a campanha em rascunho pelo MCP (`120250644049660559`, engajamento, sem orçamento de campanha), e o conjunto foi recusado com "optimization_goal PROFILE_AND_PAGE_ENGAGEMENT is not available for this ad account". A alternativa que a conta aceita pelo MCP era otimizar por clique no link; o Guilherme escolheu criar os conjuntos à mão, mantendo a visita ao perfil. Depois, o Claude confere na API e registra os IDs.

Especificação de cada conjunto, para a subida à mão:
- Orçamento do conjunto: 5 € por dia, menor custo, até 26/11 às 23h59
- Local da conversão: perfil do Instagram. Meta de desempenho: maximizar visitas ao perfil. Página `111836513679647`
- Público: Portugal; idade 23 a 55 (com Advantage+ público, a idade entra como sugestão); idiomas português (Portugal) e português (Brasil). Sem exclusão por enquanto: o público `Engajou IG 365d` ainda não existe nesta conta
- Posicionamentos: Advantage+
- Anúncio: publicação existente do Instagram @churrasco_da_elite, IG-01 `DdgfPAcqGmT` num conjunto e IG-02 `Dd_WRoXKN5K` no outro, com o botão de visitar o perfil

## Histórico de otimizações
- 2026-11-23 · IG-01 e IG-02 de 16/11 pausados. No ar só `Aberto 23-55 | Homem | Portugal | Visita ao perfil | IG-01` (`120250683957360559`, desde 18/11, 7 € por dia, sem data de fim): 27,36 €, 925 visitas e 111 seguidores pelo MCP. Entrega parada de 22/11, 16h, até 23/11, 10h25 UTC (cartão)
- 2026-11-16 · data de fim em 26/11, 23h59, nos dois conjuntos, pelo MCP (Guilherme pediu)
- 2026-11-16 · Guilherme publicou os dois conjuntos à mão, com exclusão de quem já segue; conferido na API, anúncios em análise
- 2026-11-16 · campanha criada em rascunho pelo MCP; conjuntos recusados pelo MCP, ficam com o Guilherme à mão
- 2026-11-16 · conta trocada para a CA01 `1295259920836612`, com Página e Instagram conferidos · pronta para subir
- 2026-11-13 · campanha desenhada com IG-01 e IG-02, os dois primeiros da lista · à espera do @churrasco_da_elite na CA02
