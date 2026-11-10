---
tipo: agencia
atualizado: 2026-11-10
---
# Estrutura de suporte

O que sustenta a operação para todos os clientes, fora dos serviços vendidos.

## Playbook comercial
Do primeiro contato ao contrato assinado.
1. Diagnóstico inicial
2. Proposta no modelo Hub3Ps (HTML exportado para PDF)
3. Negociação com opções e piso
4. Contrato e cláusulas
5. O escopo fechado vira a nota do cliente e entra no [[motor]]

O passo a passo, da proposta à gestão contínua: [[03-processos/novo-cliente]].

Pipeline: [[05-comercial/pipeline]].

## Painel do cliente
Um hub por cliente com tráfego pago no escopo, no mesmo formato para todos. Projetos sem tráfego, como agente ou site, usam o kanban e o relatório (Guilherme, 04/11/2026).
- Páginas: Performance, Plano, Anúncios, Funil. Ativadas conforme o escopo
- Números: atualização diária, automática
- Leitura do gestor: quinzenal e mensal

## Automações internas
A infraestrutura que roda a operação sozinha.
- Rotinas do Claude na nuvem: atualização dos hubs e resumo das contas no WhatsApp
- Rotina do Claude no Mac: leitura dos grupos dos clientes às 8h, dias úteis ([[03-processos/whatsapp-diario]])
- whatsapp-mcp, n8n, Evolution (WhatsApp), Vercel
- **Regra:** toda automação tem dono, runbook e alerta de falha

## Hub3Ps, cliente 0
A agência roda os próprios playbooks: site e LP pessoal, social, busca
orgânica, captação de leads e cases. Nota: [[04-clientes/hub3ps/cliente]].
