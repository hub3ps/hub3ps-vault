---
tipo: agencia
atualizado: 2026-11-03
---
# Motor operacional

Como o cliente puxa a estrutura: o escopo ativa os playbooks, e os playbooks
geram todo o trabalho.

1. **Escopo do cliente** (nota do cliente): serviços contratados e exceções ao padrão
2. **Playbooks ativados**: um por serviço do escopo, todos no mesmo formato
3. **O que sai daí:**
   - **Checklist de onboarding**: soma dos pré-requisitos dos playbooks ativos
   - **Tarefas de implantação**: soma das implantações, na ordem de dependência
   - **Rotinas recorrentes**: soma das rotinas, encaixadas no ciclo da [[jornada]]
   - **Relatório**: soma dos indicadores

## Regra
O padrão nunca é editado para um cliente. O que um cliente faz diferente fica
registrado como exceção no escopo dele. Se a exceção se repete em vários
clientes, vira padrão.

## Ordem de dependência na implantação
Estratégia → Tracking → LP e site → Criativos → Tráfego pago → E-mail e Agente.
O que não está no escopo, pula.
