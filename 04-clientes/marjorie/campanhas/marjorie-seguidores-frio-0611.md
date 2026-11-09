---
tipo: campanha
cliente: marjorie
nome-campanha: marjorie-seguidores-frio-0611
plataforma: meta
id-campanha: "120250854673620554"
status: ativa
inicio: 2026-11-06
verba-diaria: 10
evento-otimizacao: PROFILE_AND_PAGE_ENGAGEMENT
lp: https://instagram.com/marjoriedentalcad
atualizado: 2026-11-09
autor: claude
---
# marjorie-seguidores-frio-0611

Captação de seguidores no público frio dos EUA, a fase 1 da [[2026-11-04-estrategia-lancamento|estratégia de lançamento]]. Conta `2540479789760330`, valores em USD. Subida à mão pelo Guilherme em 06/11/2026.

## Configuração
Conferida na API em 09/11/2026.

- **Objetivo:** engajamento, com destino no perfil do Instagram, otimizando para visita ao perfil
- **Público:** `int_cad-dental_us`, público salvo de interesses, só EUA, excluindo o `cp_ig-engajou_365d`. Detalhe em [[2026-11-05-publico-interesses]]
- **Estrutura:** um conjunto por post, com 1 anúncio cada e US$ 5 por dia, para garantir a entrega de cada post no teste (Guilherme, 06/11)
- **Posts:** a fila e a ordem de prioridade estão em [[2026-11-05-posts-para-captacao]]. O ID `IG-NN` é o número do post nessa lista
- **Critério do rodízio:** custo por seguidor (Guilherme, 09/11). A estratégia de 04/11 previa custo por visita ao perfil, mas a visita barata não virou seguidor no IG-03 (ver o histórico)

| Conjunto | ID do conjunto | Anúncio | ID do anúncio | Estado |
|---|---|---|---|---|
| `int_cad-dental_us_ig_visita-perfil_IG-03` | `120250854673630554` | `IG-03-Vídeo-Dois-Lados` | `120250874413780554` | pausado em 09/11 |
| `int_cad-dental_us_ig_visita-perfil_IG-06` | `120250874693650554` | `IG-06-Vídeo-Teclado-ou-Caneta` | `120250874693660554` | ativo |
| `int_cad-dental_us_ig_visita-perfil_IG-07` | `120250920038790554` | `IG-07-Vídeo-Face-Scan` | `120250920038780554` | ativo desde 09/11 |

## Criativos no ar
| ID | Anúncio | Desde |
|---|---|---|
| IG-06 | `IG-06-Vídeo-Teclado-ou-Caneta` | 06/11/2026 |
| IG-07 | `IG-07-Vídeo-Face-Scan` | 09/11/2026 |

## Resultado por rodada
Rodada 1, de 06 a 09/11/2026. Seguidores pelo campo de seguidores do Instagram da API, valores de 09/11.

| ID | Gasto | Impressões | Frequência | Visitas ao perfil | Custo por visita | Seguidores | Custo por seguidor | Decisão |
|---|---|---|---|---|---|---|---|---|
| IG-03 | US$ 16,07 | 1.664 | 1,03 | 206 | US$ 0,08 | 11 | US$ 1,46 | sai |
| IG-06 | US$ 16,54 | 1.157 | 1,06 | 72 | US$ 0,23 | 30 | US$ 0,55 | fica |

## Histórico de otimizações
- 2026-11-06 · publicada com dois conjuntos de US$ 5 por dia, IG-03 e IG-06, os dois primeiros da lista da Julia · teste dos 2 primeiros posts, em rodízio a cada 3 dias
- 2026-11-09 · IG-03 pausado pelo Guilherme, IG-06 mantido · custo por seguidor de US$ 1,46 contra US$ 0,55. O IG-03 teve a visita ao perfil mais barata (US$ 0,08), mas só 5% das visitas viraram seguidor, contra 42% no IG-06. Com o conjunto pausado, a campanha roda a US$ 5 por dia até entrar o próximo post
- 2026-11-09 · IG-07 no ar, num conjunto novo de US$ 5 por dia, contra o IG-06 · rodada 2, o 3º da lista da Julia. A campanha volta a US$ 10 por dia
