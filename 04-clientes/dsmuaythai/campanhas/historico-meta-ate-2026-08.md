---
tipo: historico
cliente: dsmuaythai
atualizado: 2026-09-01
autor: claude
origem: agencia_marketing/clients/dsmuaythai/campanhas/historico-meta-ate-2026-08.md
migrado: 2026-11-27
---
# Histórico da conta Meta · até 31/08/2026

Puxado da Marketing API em 01/09/2026 com o token da BM da Hub3Ps, contornando o
bloqueio do MCP. Conta `800990442489726`, USD, fuso `America/New_York`, criada em
**26/08/2025**.

## O agregado

| | |
|---|---|
| Gasto total desde o início | **$2.276,45** |
| Agendamentos no site (Calendly) | **7** desde 03/2026 |
| Custo por agendamento, acumulado | **$239,02** |
| Custo por agendamento, agosto | **$72,08** |
| Conversas no Messenger (canal secundário) | 139 |
| Campanhas criadas | 7 (1 nunca entregou) |
| Ativa hoje | 1, com **$6,00/dia** |

## Mês a mês

| Mês | Gasto | Impressões | CTR | Conversas | Blocks | $/conversa |
|---|---|---|---|---|---|---|
| 2025-08 | $27,07 | 743 | 2,42% | 2 | 1 | $13,54 |
| 2025-09 | $190,70 | 5.380 | 2,43% | 18 | 5 | $10,59 |
| 2025-10 a 12 | **sem veiculação** | | | | | |
| 2026-01 | $173,57 | 18.421 | 7,50% | 2 | 0 | $86,78 |
| 2026-02 | $211,96 | 21.354 | 8,09% | 7 | 1 | $30,28 |
| 2026-03 | $273,01 | 42.905 | 4,17% | 20 | 0 | $13,65 |
| 2026-04 | $349,43 | 56.689 | 4,20% | 25 | 9 | $13,98 |
| 2026-05 | $267,46 | 36.730 | 4,00% | 18 | 7 | $14,86 |
| 2026-06 | $173,20 | 23.509 | 4,19% | 4 | 3 | $43,30 |
| 2026-07 | $248,07 | 35.352 | 4,33% | 22 | 15 | $11,28 |
| 2026-08 | $360,38 | 36.723 | 3,68% | 21 | 12 | $17,16 |

**Buraco de três meses:** outubro, novembro e dezembro de 2025 sem veiculação
nenhuma. Confirmar o motivo com o David.

## Campanhas

| Campanha | Status | Objetivo | Criada | Gasto |
|---|---|---|---|---|
| Leads - Teste | **ATIVA** | `OUTCOME_LEADS` | 19/03/2026 | $1.491,38 |
| Post do Instagram: 2026 is a New Era | pausada | `LINK_CLICKS` | 19/01/2026 | $320,02 |
| [Engajamento] [Messenger] | pausada | `OUTCOME_ENGAGEMENT` | 28/08/2025 | $217,77 |
| Tráfego - Teste | pausada | `OUTCOME_TRAFFIC` | 13/03/2026 | $92,11 |
| Leads - invitee_select_day | pausada | `OUTCOME_SALES` | 11/05/2026 | $89,66 |
| Post do Instagram: Free tip | pausada | `LINK_CLICKS` | 22/01/2026 | $65,51 |
| [Leads] [Formulário_FB] | pausada | `OUTCOME_LEADS` | 26/09/2025 | **nunca entregou** |

A `Leads - Teste` sozinha é **66% de todo o gasto histórico**.

## O funil real: agendamento no site, via Calendly

> **Correção de 01/09/2026.** A primeira leitura desta ficha concluiu que a
> conversão acontecia no Messenger. **Estava errado.** O erro foi metodológico:
> filtrei a lista de `actions` por palavra-chave e nunca pedi o campo
> `conversions`, que é exatamente onde moram as conversões customizadas
> nomeadas. O agregado de 12 meses também é dominado pelas campanhas antigas de
> Messenger, o que escondeu a estratégia atual, que tem 6 meses.

A conta rastreia o funil do **Calendly** por eventos customizados no pixel:

| Evento | O que é |
|---|---|
| `invitee_event_type_page` | Visitou a página de agendamento |
| `invitee_select_day` | Escolheu um dia |
| `invitee_meeting_scheduled` | **Agendou de fato** |

### Era Calendly, mês a mês

| Mês | Gasto | Cliques | Visitas ao Calendly | **Agendou** | $/agendamento |
|---|---|---|---|---|---|
| 03/2026 | $273,01 | 781 | 273 | 0 | - |
| 04/2026 | $349,43 | 1.167 | 512 | 0 | - |
| 05/2026 | $267,46 | 667 | 289 | 0 | - |
| 06/2026 | $173,20 | 502 | 210 | 1 | $173,20 |
| 07/2026 | $248,07 | 774 | 365 | 1 | $248,07 |
| 08/2026 | $360,38 | 698 | 315 | **5** | **$72,08** |
| **Total** | **$1.673,15** | **4.594** | **1.965** | **7** | **$239,02** |

## ✅ A virada de 28/07: trocar o evento de otimização

Os dois conjuntos da campanha ativa contam a história inteira:

| Conjunto | Otimiza para | Início | Status |
|---|---|---|---|
| `Regiões próximas` | `invitee_event_type_page` (**visita**) | 20/03/2026 | pausado |
| `Regiões próximas - teste` | `invitee_meeting_scheduled` (**agendamento**) | 28/07/2026 | **ativo** |

| Período | Otimização | Visitas | Agendamentos |
|---|---|---|---|
| mar a jul/2026 | visita à página | 1.649 | 2 |
| ago/2026 | agendamento | 315 | **5** |

Otimizando para visita, a Meta entregava exatamente isso: gente que abre a
página e vai embora. **Trocar o evento para `invitee_meeting_scheduled` em 28/07
multiplicou o resultado por cinco com menos tráfego.** Foi a melhor decisão da
história desta conta.

O conjunto ativo, de 28/07 a 01/09: **$285,13 · 4 agendamentos · $71,28 cada.**

## O gargalo verdadeiro: a página de agendamento

**1.965 visitas ao Calendly produziram 7 agendamentos: 0,4%.**

Mesmo em agosto, o melhor mês, foram 315 visitas para 5 agendamentos, 1,6%. Para
uma página de agendamento que recebe tráfego já qualificado por clique pago,
isso é muito baixo.

O dinheiro não se perde comprando o clique: **se perde entre abrir a página de
agendamento e escolher o horário.** É exatamente ali que o trabalho de LP que
combinamos deve atacar, e a decisão de construí-la se confirma bem mirada.

Referência a bater: **$72,08 por agendamento**, o número de agosto.

## O funil completo, com as taxas reais

| Mês | Cliques | Visitas Calendly | clique → Calendly | Agendou | Calendly → agenda |
|---|---|---|---|---|---|
| 03/2026 | 781 | 273 | 35% | 0 | 0,0% |
| 04/2026 | 1.167 | 512 | 44% | 0 | 0,0% |
| 05/2026 | 667 | 289 | 43% | 0 | 0,0% |
| 06/2026 | 502 | 210 | 42% | 1 | 0,5% |
| 07/2026 | 774 | 365 | 47% | 1 | 0,3% |
| 08/2026 | 698 | 315 | 45% | **5** | **1,6%** |
| **Total** | **4.594** | **1.965** | **43%** | **7** | **0,4%** |

**A primeira etapa é saudável.** 43% dos cliques pagos chegam à página de
agendamento, estável em todos os meses. Para social pago, é bom.

**A segunda etapa é onde tudo se perde.** 1.965 visitas viraram 7 agendamentos.

## ❌ Alarme falso: a "queda de cliques para visualização de página"

> A leitura anterior apontou que "de cada três cliques pagos, dois não viram
> visualização de página" a partir de junho, e sugeriu investigar velocidade do
> destino ou troca de URL. **Investiguei e o alarme era falso.**

A queda do `landing_page_view` é real no número, mas não representa perda:

| | mar a mai | jun a ago |
|---|---|---|
| `landing_page_view` | 2.756 | 734 |
| Visitas ao Calendly | 1.074 | 890 |
| **Cliques → Calendly** | **41%** | **44%** |

A queda foi **uniforme em todos os placements ao mesmo tempo** (de 79 a 119%
para 26 a 42%), o que já descartava mix de posicionamento. E a explicação
aparece ao comparar as duas séries: até maio o `landing_page_view` era **maior**
que as visitas ao Calendly (879 contra 273 em março), sinal de que havia uma
página intermediária sendo contada. De junho em diante os dois números se
aproximam (211 contra 210, 227 contra 315).

**O caminho foi encurtado, não quebrado.** Provavelmente o tráfego passou a ir
direto para a página de agendamento em vez de passar por uma página do site. O
`PageView` genérico caiu porque há uma página a menos no percurso, e não porque
alguém deixou de chegar. A taxa que importa, clique para Calendly, não se mexeu.

O pixel confirma que está saudável: dispara `PageView`, `TimeOnPage`,
`PageScroll`, `invitee_event_type_page` e `invitee_select_day` normalmente.

## Sinais secundários

**Só roda post impulsionado.** Os anúncios com entrega se chamam todos "Post do
Instagram". Não existe criativo construído para converter, com oferta, prova e
CTA. Agora com alvo claro: levar ao agendamento.

**Bloqueios no Messenger.** O canal de DM roda em paralelo e tem 12 bloqueios
para 20 conversas no conjunto ativo. Problema real, mas canal secundário.

## Conjunto ativo hoje

`Regiões próximas - teste` · **$6,00/dia** · idade 18-55 · meta de otimização
`OFFSITE_CONVERSIONS`.

⚠️ **Possível descasamento:** o conjunto otimiza para conversão no site enquanto
as conversões reais acontecem no Messenger. Verificar para qual evento ele está
otimizando de fato, porque otimizar para um evento que quase não dispara entrega
mal e encarece tudo.

## Rastreamento

**Existe pixel:** `DS Muay Thai`, ID `25913656948303012`, último evento em
**31/08/2026 21:20**. Está vivo e disparando.

Isso corrige a suposição anterior do briefing de que não havia rastreamento. O
que falta saber é **quais eventos** ele registra e se algum representa matrícula
ou agendamento de trial.
