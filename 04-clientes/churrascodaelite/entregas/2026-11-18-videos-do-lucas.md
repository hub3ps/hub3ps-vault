---
tipo: entrega
cliente: churrascodaelite
atualizado: 2026-11-18
autor: claude
---
# Vídeos do Lucas para a captação da lista

Sete vídeos que o Lucas mandou ao Guilherme pelo WhatsApp em 09/11, baixados em `~/Downloads/WhatsApp Video 2026-11-09 at *.mp4`. Analisados em 18/11 para a campanha de captação da [[../log|lista de espera]], com quadros e transcrição (Whisper local).

**Técnico:** todos verticais 9:16, mas em 576x1024, compressão do WhatsApp. Serve para Reels e Stories, mas o ideal é pedir ao Lucas os originais do celular (enviar como documento ou por Drive).

**Risco de reprovação:** quatro vídeos prometem um valor de ganho (1.500 € a 5.000 € por mês). A Meta reprova ou limita anúncio com promessa de renda, e os valores nem batem entre si. A LP não promete valor nenhum. Por isso os cortes abaixo tiram esses trechos.

| ID | Arquivo | Duração | O que é | Veredito |
|---|---|---|---|---|
| VL-01 | `11.47.35` | 30 s | Pergunta "é possível ganhar dinheiro com churrasco em Portugal?", evento em Sintra para 40 pessoas, carne crua na bancada | **Usar com corte:** 0 a 14,6 s + 25,6 a 28,8 s (tira "2 mil a 5 mil euros por mês"), cerca de 18 s |
| VL-02 | `11.50.10` | 36 s | No armazém, três eventos separados, já com legenda queimada | **Usar inteiro.** Sem promessa de valor, é o mais seguro |
| VL-03 | `11.50.21` | 55 s | Fim de tarde na segunda estrutura do dia, "abrir a caixa preta" | **Usar com corte:** 0 a 40,9 s + 48,3 a 54,6 s (tira "de 1.500 a 2.500 euros"), cerca de 47 s. Diz "8 anos" de empresa, e a LP diz "mais de 10" |
| VL-04 | `11.54.07` | 39 s | À noite, "empreender em 2025", último churrasco do ano | **Descartar:** datado e escuro |
| VL-05 | `11.54.12` | 17 s | Tábua de carne, "ganhar até 1.500 euros por mês" | **Descartar:** a promessa é o vídeo inteiro |
| VL-06 | `11.54.18` | 28 s | "Cansado de trabalhar na obra, no restaurante, de ganhar ordenado mínimo?" | **Usar com fecho novo:** é o melhor gancho, mas termina sem chamada ("me acompanhe"). Precisa de cartela final com "Clica no link e entra na lista" |
| VL-07 | `11.57.52` | 33 s | Ao lado da piscina, "cansado da obra, do restaurante?" | **Usar com corte:** 0 a 6,6 s + 14,7 a 31,7 s (tira "1.500 euros" e a palavra solta do fim), cerca de 23 s |

**Ordem para testar:** VL-06, VL-07 e VL-02 (dor e prova, sem promessa), depois VL-01 e VL-03.

## Cortes prontos (18/11)
Em `~/Downloads/churrascodaelite-captacao/`, 576x1024, H.264, 30 fps. Cortados no ffmpeg direto: a ferramenta `editar-video` sai em HDR de iPhone e 1080 de largura, e estes vídeos do WhatsApp são SDR. Sem legenda nova. Conferidos por retranscrição: sem emenda suja e sem valor em euros.

| Arquivo | Duração | Trechos do original |
|---|---|---|
| `VL-01_sintra-40-pessoas.mp4` | 13,7 s | 1,40 a 13,70 + 25,32 a 26,70 |
| `VL-02_armazem-3-eventos.mp4` | 36 s | inteiro |
| `VL-03_caixa-preta.mp4` | 45,4 s | 1,55 a 40,62 + 48,30 a 54,60 |
| `VL-06_ordenado-minimo.mp4` | 28,8 s | 0 a 25,32 (sai o "me acompanhe") + 3,5 s de cartela sobre o último quadro: "Entra na lista VIP · A oferta da Black Friday sai primeiro no grupo VIP · Clica no link", nas cores da LP, acima da faixa que a interface do Reels cobre |
| `VL-07_cansado-da-obra.mp4` | 23,2 s | 0 a 6,85 + 15,25 a 31,62 |

Nenhum fala da Black nem da lista. A chamada é genérica ("clique no link"), o que serve, e o texto do anúncio completa com a lista e os 67 €.
