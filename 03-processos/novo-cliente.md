---
tipo: processo
atualizado: 2026-11-04
autor: claude
---
# Entrada de cliente novo

São cinco fases, da proposta à gestão contínua. Cada uma tem um gatilho e um critério de saída, e **só se avança com o critério cumprido**. Este runbook cobre as etapas 1 e 2 da [[jornada]] e o caminho até a etapa 6. Para saber como o escopo vira trabalho, veja o [[motor]].

Decisões que valem aqui (Guilherme, 04/11/2026):
- A meta acordada é obrigatória para sair do Fechamento
- O briefing é coletado na reunião de kickoff
- O valor do contrato fica no frontmatter da nota do cliente. O PDF fica no Drive
- O painel (hub) só é criado quando o escopo tem tráfego pago

---

## 1. Proposta
**Gatilho:** primeiro contato de um cliente em potencial.

1. Crie a proposta em `05-comercial/propostas/<slug>-AAAA-MM.md`, a partir de [[_modelos/proposta]], com `etapa: diagnostico`
2. Registre o diagnóstico: dor, objetivo e contexto
3. Monte o escopo com os serviços do [[catalogo]] e diga o que fica fora
4. Monte as opções de valor, com setup, mensal e prazo mínimo, e registre o piso
5. Envie o PDF, guarde o link do Drive, mude para `etapa: proposta-enviada` e preencha `enviada-em`

**Para sair:** a proposta é aceita (`etapa: fechada`) ou perdida (`etapa: perdida`, com o motivo no histórico).

## 2. Fechamento
**Gatilho:** a proposta foi aceita.

1. Contrato assinado e PDF salvo no Drive, em `Hub3Ps/Clientes/<slug>/contrato/`
2. Pasta do Drive `Hub3Ps/Clientes/<slug>/` criada. O slug é o mesmo em todo lugar: vault, Drive, repositório e campanha
3. Pasta do cliente criada no vault:
   ```
   04-clientes/<slug>/cliente.md   ← de _modelos/cliente
   04-clientes/<slug>/kanban.md    ← de _modelos/kanban
   04-clientes/<slug>/log.md       ← de _modelos/log
   ```
4. Frontmatter do `cliente.md` preenchido: `status: implantacao`, `servicos`, `inicio`, `contrato` (link do PDF), `vigencia`, `valor-mensal`, `meta` e `drive`
5. Seção "Escopo" preenchida com os playbooks dos serviços contratados
6. Cliente registrado no [[00-sistema/indice]] e no [[log-operacoes]]

**Para sair:** contrato assinado e **`meta` preenchida com número e prazo**, como "75 a 90 trials por trimestre" ou "CAC até R$ 500". Sem meta, o cliente não vai para o kickoff.

## 3. Kickoff e briefing
**Gatilho:** o contrato foi assinado.

**Antes da reunião (Claude):**
1. Copie [[_modelos/briefing]] para `04-clientes/<slug>/briefing.md`
2. Mantenha os blocos comuns e **só os blocos dos serviços do escopo**. Esse arquivo vira o roteiro da reunião
3. Marque o que já se sabe pela proposta e pelo contrato, para não perguntar de novo

**Na reunião (Guilherme):** conduza pelo roteiro, grave e transcreva.

**Depois da reunião (Claude):**
1. Salve a transcrição em `04-clientes/<slug>/fontes/AAAA-MM-DD-kickoff.md`. É fonte e nunca se edita
2. Consolide o `briefing.md`, com status por bloco: ✅ fechado, 🟡 parcial ou ⬜ vazio
3. Crie a nota da reunião em `reunioes/`, a partir de [[_modelos/reuniao]]
4. Leve cada lacuna para "Depende do cliente" na nota e para "Aguardando cliente" no kanban
5. Marque `proxima-reuniao`

**Para sair:** os blocos comuns estão fechados (✅), e cada lacuna dos blocos de serviço virou cartão no kanban.

## 4. Onboarding e implantação
**Gatilho:** o briefing foi consolidado.

1. **Checklist de onboarding.** Para cada serviço do escopo, abra o playbook e copie os itens de "Pré-requisitos" para o kanban:
   - o que depende do cliente (acessos, materiais, aprovações) vai para **Aguardando cliente**
   - o que é nosso vai para **A fazer**, com a tag do serviço
2. **Tarefas de implantação.** Copie os passos de "Implantação" de cada playbook para **A fazer**, na ordem do [[motor]]: estratégia, tracking, LP e site, criativos, tráfego pago, e-mail e agente. O que não está no escopo fica de fora
3. **Painel.** Só se `trafego-pago` estiver no escopo: crie o hub do cliente. TODO: falta o runbook de criação. Hoje a referência são os hubs do JurIA e do DS Muay Thai no `agencia_marketing`
4. **Exceções.** Todo ponto em que o cliente foge do playbook vai para a tabela "Exceções ao padrão", com motivo e data. O playbook nunca se edita para um cliente
5. **Acessos.** Registre onde está cada acesso na seção "Acessos", sem senha. Token e chave ficam fora do vault

**Para sair:** todos os pré-requisitos estão feitos, todas as tarefas de implantação estão em "Feito", e os entregáveis da implantação de cada playbook estão no ar.

## 5. Passagem para a gestão contínua
**Gatilho:** a implantação foi concluída.

1. As rotinas de cada playbook do escopo estão agendadas no ciclo da [[jornada]]: diária, semanal, quinzenal e mensal
2. As automações têm dono, runbook e alerta de falha, como pede o [[suporte]]
3. `status: ativo` e `proxima-reuniao` preenchida
4. Estado atual da nota reescrito, com entrada no log do cliente e no [[log-operacoes]]

**Para sair:** o cliente aparece como ativo no [[INICIO]], com meta e próxima reunião, e a primeira rotina diária rodou.

---

## Como conferir
O [[INICIO]] tem duas tabelas que denunciam quando um passo foi pulado:
- **Em implantação:** cliente parado na fase 2, 3 ou 4
- **Sem meta ou sem próxima reunião:** cliente que saiu do Fechamento sem cumprir o critério
