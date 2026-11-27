# Processos

Um runbook por rotina, começando pelo comando. Os runbooks de `docs/processos/` do repo `agencia_marketing` vieram para cá em 27/11/2026, e lá ficou só um ponteiro. Faltam os dois de atualizar o hub, que a rotina da nuvem ainda lê no repo: eles vêm junto com o agente da manhã ([[00-sistema/plano-fechamento-migracao|plano]]).

| Rotina | Quando | Runbook |
|---|---|---|
| Entrada de cliente novo | Primeiro contato até a gestão contínua | [[novo-cliente]] |
| Criar o hub do cliente | Cliente novo com tráfego pago | [[novo-hub]] |
| Montar campanha no Meta | Verba aprovada, criativo pronto | [[nova-campanha]] |
| Produzir criativo | Campanha nova ou refresh | [[novo-criativo]] |
| Alimentar a biblioteca de refs | Achou uma referência boa | [[nova-referencia]] |
| Editar vídeo falado | Vídeo bruto do @guimiguelmkt gravado no iPhone | [[editar-video]] (v0, em lapidação) |
| Publicar no Instagram | Post, carrossel ou Reels programado | [[publicar-instagram]] |
| WhatsApp diário | Dias úteis às 8h, agendado | [[whatsapp-diario]] |

**Só do JurIA**
| Rotina | Quando | Runbook |
|---|---|---|
| Produzir vídeo | Criativo em vídeo, com ou sem locução | [[video-juria]] |
| Post do Instagram | Carrossel ou estático do perfil orgânico | [[post-instagram-juria]] |
| Configurar o GA4 | Funil novo para medir, evento parado no dataLayer | [[configurar-ga4-juria]] |
| Agrupar canais no GA4 | Canal novo na mídia, convenção de UTM mudou | [[canais-ga4-juria]] |
| Publicar o site | Mudança em página do site | [[publicar-site-juria]] |
| Publicar LP (histórico) | LPs antigas, antes de 12/11/2026 | [[publicar-lp-juria]] |
| Atualizar o hub | Ciclo de reporte | ainda em `agencia_marketing/docs/processos/atualizar-hub-juria.md` |

**Só do DS Muay Thai**
| Rotina | Quando | Runbook |
|---|---|---|
| Publicar LP e bio | Mudança na LP de anúncio ou na bio | [[publicar-lp-dsmuaythai]] |
| Atualizar o hub | Ciclo de reporte | ainda em `agencia_marketing/docs/processos/atualizar-hub-dsmuaythai.md` |

O `novo-cliente.md` do repo antigo foi substituído por [[novo-cliente]] e não foi migrado: ele criava a pasta do cliente no `agencia_marketing`, modelo que o vault aposentou.

## Como escrever um runbook
- Comece pelo comando, não pela explicação. Quem abre quer executar
- O porquê mora na nota do cliente. O runbook linka
- Se um passo pode dar errado em silêncio, escreva como conferir
- Processo mudou, runbook muda no mesmo dia. Runbook errado é pior que runbook ausente
