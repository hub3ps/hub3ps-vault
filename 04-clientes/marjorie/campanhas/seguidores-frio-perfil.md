---
tipo: campanha
cliente: marjorie
nome-campanha: Seguidores | Frio | Perfil
plataforma: meta
id-campanha: "120250854673620554"
status: ativa
inicio: 2026-11-06
verba-diaria: 10
evento-otimizacao: PROFILE_AND_PAGE_ENGAGEMENT
lp: https://instagram.com/marjoriedentalcad
atualizado: 2026-11-23
autor: claude
---
# Seguidores | Frio | Perfil

Nome no Meta desde 11/11/2026, no [[03-processos/convencoes|padrão novo]]. Antes: `marjorie-seguidores-frio-0611`. Os conjuntos, os anúncios e os públicos também foram renomeados, e a tabela abaixo traz os nomes novos.

Captação de seguidores no público frio dos EUA, a fase 1 da [[2026-11-04-estrategia-lancamento|estratégia de lançamento]]. Conta `2540479789760330`, valores em USD. Subida à mão pelo Guilherme em 06/11/2026.

## Configuração
Conferida na API em 09/11/2026.

- **Objetivo:** engajamento, com destino no perfil do Instagram, otimizando para visita ao perfil
- **Público:** `int_cad-dental_us`, público salvo de interesses, só EUA, excluindo o `Engajou IG 365d`. Detalhe em [[2026-11-05-publico-interesses]]
- **Estrutura:** um conjunto por post, com 1 anúncio cada e US$ 5 por dia, para garantir a entrega de cada post no teste (Guilherme, 06/11)
- **Posts:** a fila e a ordem de prioridade estão em [[2026-11-05-posts-para-captacao]]. O ID `IG-NN` é o número do post nessa lista
- **Critério do rodízio:** custo por seguidor (Guilherme, 09/11). A estratégia de 04/11 previa custo por visita ao perfil, mas a visita barata não virou seguidor no IG-03 (ver o histórico)

| Conjunto | ID do conjunto | Anúncio | ID do anúncio | Estado |
|---|---|---|---|---|
| `Interesse CAD dental \| EUA \| Visita ao perfil \| IG-03` | `120250854673630554` | `IG-03 \| Reels \| Dois lados` | `120250874413780554` | pausado em 09/11 |
| `Interesse CAD dental \| EUA \| Visita ao perfil \| IG-06` | `120250874693650554` | `IG-06 \| Reels \| Teclado ou caneta` | `120250874693660554` | pausado em 16/11 |
| `Interesse CAD dental \| EUA \| Visita ao perfil \| IG-07` | `120250920038790554` | `IG-07 \| Reels \| Face scan` | `120250920038780554` | pausado em 12/11 |
| `Interesse CAD dental \| EUA \| Visita ao perfil \| IG-12` | `120250969998310554` | `IG-12 \| Reels \| Setup em casa` | `120250969998320554` | ativo desde 12/11 |
| `Interesse CAD dental \| EUA \| Visita ao perfil \| IG-14` | `120251042926820554` | `IG-14 \| Reels \| Modo sobrevivência` | `120251042926830554` | pausado em 19/11 |
| `Interesse CAD dental \| EUA \| Visita ao perfil \| IG-24` | `120251098026000554` | `IG-24 \| Reels \| Candy Coating` | `120251098025990554` | em análise desde 19/11 |

## Criativos no ar
| ID | Anúncio | Desde |
|---|---|---|
| IG-12 | `IG-12 \| Reels \| Setup em casa` | 12/11/2026 |
| IG-24 | `IG-24 \| Reels \| Candy Coating` | 19/11/2026, em análise |

Regra (Guilherme, 25/11): na captação de seguidores não entra vídeo que explica o curso ou a comunidade. Por isso o #27 e o #31 ficam fora desta campanha.

Próximo da fila: o #20 (Calculadora, `DZ5ClM2uOvu`), o último dos 10 das clientes que ainda não foi testado. Depois dele vêm os posts que a Julia indicou, começando pelo #17 (Ferramentas escondidas do DentalCAD 3.3, `DV8sOBEjYHg`).

## Resultado por rodada
Rodada 1, de 06 a 09/11/2026. Seguidores pelo campo de seguidores do Instagram da API, valores de 09/11.

| ID | Gasto | Impressões | Frequência | Visitas ao perfil | Custo por visita | Seguidores | Custo por seguidor | Decisão |
|---|---|---|---|---|---|---|---|---|
| IG-03 | US$ 16,07 | 1.664 | 1,03 | 206 | US$ 0,08 | 11 | US$ 1,46 | sai |
| IG-06 | US$ 16,54 | 1.157 | 1,06 | 72 | US$ 0,23 | 30 | US$ 0,55 | fica |

Rodada 2, de 09 a 12/11/2026, com o dia 12 ainda aberto. Valores da API em 12/11. O custo por seguidor é gasto dividido por seguidores, conta nossa.

| ID | Gasto | Impressões | Frequência | Visitas ao perfil | Custo por visita | Seguidores | Custo por seguidor | Decisão |
|---|---|---|---|---|---|---|---|---|
| IG-06 | US$ 13,70 | 988 | 1,07 | 55 | US$ 0,25 | 20 | US$ 0,69 | fica |
| IG-07 | US$ 11,06 | 1.103 | 1,03 | 108 | US$ 0,10 | 8 | US$ 1,38 | sai |

Rodada 3, de 12 a 16/11/2026, com o dia 16 ainda aberto. Valores da API em 16/11. O IG-06 inclui o dia 12 inteiro (US$ 5,40 e nenhum seguidor), que já tinha entrado em parte na rodada 2. Custo por seguidor é conta nossa.

| ID | Gasto | Impressões | Frequência | Visitas ao perfil | Custo por visita | Seguidores | Custo por seguidor | Decisão |
|---|---|---|---|---|---|---|---|---|
| IG-06 | US$ 22,40 | 1.106 | 1,36 | 35 | US$ 0,64 | 5 | US$ 4,48 | sai |
| IG-12 | US$ 19,64 | 1.731 | 1,12 | 131 | US$ 0,15 | 43 | US$ 0,46 | fica |

Rodada 4, de 16 a 19/11/2026, com o dia 19 ainda aberto. Valores da API em 19/11, somados dia a dia. O IG-12 inclui o dia 16 inteiro, que já tinha entrado em parte na rodada 3. Custo por visita e por seguidor são conta nossa.

| ID | Gasto | Impressões | Visitas ao perfil | Custo por visita | Seguidores | Custo por seguidor | Decisão |
|---|---|---|---|---|---|---|---|
| IG-12 | US$ 17,20 | 1.504 | 91 | US$ 0,19 | 24 | US$ 0,72 | fica |
| IG-14 | US$ 14,30 | 1.310 | 125 | US$ 0,11 | 12 | US$ 1,19 | sai |

Rodada 5, de 19 a 23/11/2026, com o dia 23 ainda aberto. Valores da API em 23/11. O IG-24 entrou em análise no dia 19. Custo por seguidor é conta nossa.

| ID | Gasto | Impressões | Visitas ao perfil | Custo por visita | Seguidores | Custo por seguidor | Decisão |
|---|---|---|---|---|---|---|---|
| IG-12 | US$ 20,66 | 1.706 | 116 | US$ 0,18 | 24 | US$ 0,86 | empate, segue |
| IG-24 | US$ 20,91 | 939 | 46 | US$ 0,45 | 22 | US$ 0,95 | empate, segue |

## Histórico de otimizações
- 2026-11-06 · publicada com dois conjuntos de US$ 5 por dia, IG-03 e IG-06, os dois primeiros da lista da Julia · teste dos 2 primeiros posts, em rodízio a cada 3 dias
- 2026-11-09 · IG-03 pausado pelo Guilherme, IG-06 mantido · custo por seguidor de US$ 1,46 contra US$ 0,55. O IG-03 teve a visita ao perfil mais barata (US$ 0,08), mas só 5% das visitas viraram seguidor, contra 42% no IG-06. Com o conjunto pausado, a campanha roda a US$ 5 por dia até entrar o próximo post
- 2026-11-09 · IG-07 no ar, num conjunto novo de US$ 5 por dia, contra o IG-06 · rodada 2, o 3º da lista da Julia. A campanha volta a US$ 10 por dia
- 2026-11-11 · campanha, conjuntos, anúncios e públicos renomeados para o padrão novo · só rótulo, sem efeito na entrega. Os conjuntos rodam no Facebook e no Instagram, embora o nome antigo dissesse `ig`
- 2026-11-12 · IG-07 pausado, IG-06 mantido e IG-12 no ar num conjunto novo de US$ 5 por dia · rodada 2 fechada pelo custo por seguidor: US$ 0,69 no IG-06 contra US$ 1,38 no IG-07. O IG-07 repetiu o IG-03: a visita mais barata (US$ 0,10 contra US$ 0,25), mas só 7% das visitas viraram seguidor, contra 36% no IG-06. O IG-12 ("O setup novo em casa", DH1sAqTTxyY) é o 4º da lista da Julia. Pausa pelo MCP; o conjunto do IG-12 foi duplicado do IG-07 à mão pelo Guilherme, porque o MCP não cria conjunto com `PROFILE_AND_PAGE_ENGAGEMENT` nesta conta. Conferido na API: mesma configuração do IG-07, anúncio aprovado e entregando no mesmo dia. A campanha segue a US$ 10 por dia
- 2026-11-16 · IG-06 pausado pelo MCP, IG-12 mantido · rodada 3 fechada pelo custo por seguidor: US$ 0,46 no IG-12 contra US$ 4,48 no IG-06 (US$ 3,40 sem o dia 12). O IG-06 cansou: o custo por seguidor foi de US$ 0,55 na rodada 1 para US$ 0,69 na 2 e US$ 4,48 na 3, e só 14% das visitas viraram seguidor, contra 33% no IG-12. Na vida toda, o IG-06 trouxe 53 seguidores com US$ 50,12. A campanha roda a US$ 5 por dia até o IG-14 ("Sair do modo sobrevivência", DRnTUjXk0MW), o 5º da lista da Julia, entrar num conjunto duplicado do IG-12 à mão pelo Guilherme
- 2026-11-16 · IG-14 no ar num conjunto novo de US$ 5 por dia, contra o IG-12 · rodada 4, o 5º da lista da Julia. Conjunto duplicado do IG-12 à mão pelo Guilherme e conferido na API: mesma configuração. A duplicação levou junto o post do IG-12; o Guilherme trocou pelo DRnTUjXk0MW e conferi de novo. Anúncio em análise da Meta. A campanha volta a US$ 10 por dia
- 2026-11-19 · IG-14 pausado pelo MCP, com o ok do Guilherme, e IG-12 mantido · rodada 4 fechada pelo custo por seguidor: US$ 0,72 no IG-12 contra US$ 1,19 no IG-14. O IG-14 repetiu o IG-03 e o IG-07: a visita mais barata (US$ 0,11 contra US$ 0,19), mas só 10% das visitas viraram seguidor, contra 26% no IG-12, e nenhum seguidor desde 18/11. O IG-12 encareceu (US$ 0,46 na rodada 3), com frequência ainda perto de 1. Pausa conferida na API. A campanha roda a US$ 5 por dia até o próximo post entrar num conjunto duplicado do IG-12 à mão pelo Guilherme. O #18 e o #19, os próximos da lista das clientes, têm música e não aparecem como anunciáveis na API; se o Gerenciador também não deixar, entra o #24 (Candy Coating)
- 2026-11-19 · IG-24 no ar num conjunto novo de US$ 5 por dia, contra o IG-12 · rodada 5. O #18 também não pôde ser escolhido no Gerenciador, então entrou o #24 ("Tutorial do Candy Coating", DbTiRHGsOb4). Conjunto duplicado do IG-12 à mão pelo Guilherme e conferido na API: mesmo público, idade, posicionamentos, exclusão do `Engajou IG 365d`, otimização e verba; Advantage+ de público desligado (`advantage_audience: 0`) e nenhum aprimoramento Advantage+ de criativo no anúncio. Anúncio em análise. Os nomes no padrão foram feitos pelo MCP em rascunho e publicados pelo Guilherme no Gerenciador, conferidos na API. A campanha volta a US$ 10 por dia
- 2026-11-25 · conjunto e anúncio do IG-31 criados pelo MCP em rascunho, a pedido do Guilherme · rodada 6, o #31 (Df7Zrz-NOv6, anunciável na API). Conjunto `120251186839450554` copiado do IG-12 (`source_adset_id`), com a mesma configuração: US$ 5 por dia, `PROFILE_AND_PAGE_ENGAGEMENT` para o perfil do IG, Página no `promoted_object`, idade 22 a 55, EUA, posicionamentos, públicos de interesse, exclusão do `Engajou IG 365d`, Advantage+ de público desligado e atribuição de 1 dia no clique. Desta vez o MCP aceitou a otimização, que recusou em 12/11. Anúncio `120251186840330554`, `IG-31 | Reels | Comunidade nova`, com o post orgânico, botão "Ver perfil do Instagram", link do perfil e sem aprimoramentos. A Meta pediu o link, que entrou no rascunho. Os dois validados sem erro, falta publicar. Pela regra da rodada, sai o IG-24 (US$ 1,19 por seguidor contra US$ 1,03 do IG-12, de 19 a 25/11)
- 2026-11-25 · no rascunho, o #31 trocado pelo #20 (Calculadora, `DZ5ClM2uOvu`), a pedido do Guilherme · o #31 apresenta a comunidade, e vídeo do curso não entra na captação de seguidores. O #20 é o último dos 10 das clientes ainda não testado, e a automação de resposta ao "Calculator" funciona (Guilherme). Conjunto renomeado para `... | IG-20` e anúncio para `IG-20 | Reels | Calculadora`, com o mesmo botão, link e sem aprimoramentos. Sem erro no rascunho, com a validação do anúncio pendente na Meta. Falta publicar
