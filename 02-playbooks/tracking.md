---
tipo: playbook
servico: tracking
status: rascunho
atualizado: 2026-11-03
---
# Tracking

Faz parte do [[catalogo]]. Ativado pelo [[motor]] quando o serviço está no escopo do cliente.

**Depende de:** [[lp-e-site]]

## Pré-requisitos
Viram o checklist de onboarding do cliente.

- [ ] Acesso a GTM, GA4, BM e domínio
- [ ] LP ou site no ar
- [ ] Política de consentimento

## Implantação
Feita uma vez, na ordem.

1. GTM e tags
2. Pixel e CAPI
3. Eventos de conversão
4. GA4 e funil
5. UTMs e canais

## Entregáveis

- Documento de tracking
- Plano de eventos
- Teste ponta a ponta

## Rotina

| Cadência | O quê |
|---|---|
| Diária | eventos chegando, via dash |
| Mensal | auditoria de eventos e UTMs |

## Ferramentas e skills

- GTM, GA4, Events Manager
- Marketing API
- Runbooks de GA4

## Indicadores
Entram no relatório do cliente.

- Eventos recebidos x esperados
- Qualidade da correspondência
- Divergência Meta x GA4

## Lições do serviço
Correções que valem para este serviço em todos os clientes.

