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
atualizado: 2026-11-12
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
| `Interesse CAD dental \| EUA \| Visita ao perfil \| IG-06` | `120250874693650554` | `IG-06 \| Reels \| Teclado ou caneta` | `120250874693660554` | ativo |
| `Interesse CAD dental \| EUA \| Visita ao perfil \| IG-07` | `120250920038790554` | `IG-07 \| Reels \| Face scan` | `120250920038780554` | pausado em 12/11 |
| `Interesse CAD dental \| EUA \| Visita ao perfil \| IG-12` | `120250969998310554` | `IG-12 \| Reels \| Setup em casa` | `120250969998320554` | ativo desde 12/11 |

## Criativos no ar
| ID | Anúncio | Desde |
|---|---|---|
| IG-06 | `IG-06 \| Reels \| Teclado ou caneta` | 06/11/2026 |
| IG-12 | `IG-12 \| Reels \| Setup em casa` | 12/11/2026 |

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

## Histórico de otimizações
- 2026-11-06 · publicada com dois conjuntos de US$ 5 por dia, IG-03 e IG-06, os dois primeiros da lista da Julia · teste dos 2 primeiros posts, em rodízio a cada 3 dias
- 2026-11-09 · IG-03 pausado pelo Guilherme, IG-06 mantido · custo por seguidor de US$ 1,46 contra US$ 0,55. O IG-03 teve a visita ao perfil mais barata (US$ 0,08), mas só 5% das visitas viraram seguidor, contra 42% no IG-06. Com o conjunto pausado, a campanha roda a US$ 5 por dia até entrar o próximo post
- 2026-11-09 · IG-07 no ar, num conjunto novo de US$ 5 por dia, contra o IG-06 · rodada 2, o 3º da lista da Julia. A campanha volta a US$ 10 por dia
- 2026-11-11 · campanha, conjuntos, anúncios e públicos renomeados para o padrão novo · só rótulo, sem efeito na entrega. Os conjuntos rodam no Facebook e no Instagram, embora o nome antigo dissesse `ig`
- 2026-11-12 · IG-07 pausado, IG-06 mantido e IG-12 no ar num conjunto novo de US$ 5 por dia · rodada 2 fechada pelo custo por seguidor: US$ 0,69 no IG-06 contra US$ 1,38 no IG-07. O IG-07 repetiu o IG-03: a visita mais barata (US$ 0,10 contra US$ 0,25), mas só 7% das visitas viraram seguidor, contra 36% no IG-06. O IG-12 ("O setup novo em casa", DH1sAqTTxyY) é o 4º da lista da Julia. Pausa pelo MCP; o conjunto do IG-12 foi duplicado do IG-07 à mão pelo Guilherme, porque o MCP não cria conjunto com `PROFILE_AND_PAGE_ENGAGEMENT` nesta conta. Conferido na API: mesma configuração do IG-07, anúncio em análise da Meta. A campanha segue a US$ 10 por dia
