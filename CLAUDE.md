# Vault Hub3Ps · Protocolo do Claude

Este vault é o cérebro da agência. Tudo que a operação sabe, decide e faz está
aqui, em notas ligadas entre si. Leia este arquivo inteiro antes de qualquer
tarefa.

## Protocolo de sessão

**Ao abrir, sempre, nesta ordem:**
1. [[00-sistema/regras]]: regras de escrita e de trabalho
2. [[00-sistema/licoes]]: correções que viraram regra. Valem acima de qualquer padrão
3. Se a tarefa é de um cliente: `04-clientes/<slug>/cliente.md` (escopo, exceções, estado)
4. O playbook de cada serviço envolvido: `02-playbooks/<servico>.md`
5. Se existir runbook para a tarefa: `03-processos/`

**Ao terminar, sempre:**
1. Kanban do cliente: mova ou crie os cartões da tarefa
2. Log do cliente: uma entrada com data, o que foi feito e onde está o resultado
3. Estado atual na nota do cliente: reescreva em até três linhas e atualize `atualizado`
4. Se o usuário corrigiu algo: registre em [[00-sistema/licoes]]
5. Se o processo mudou: atualize o playbook ou o runbook na mesma sessão
6. [[00-sistema/log-operacoes]]: uma linha com data, cliente e tarefa

Sessão que não fecha esses passos deixa o vault mentindo. Não pule.

## Como este vault funciona

Segue o padrão LLM Wiki (Andrej Karpathy), adaptado para a agência. Três camadas:

| Camada | Onde | Quem escreve |
|---|---|---|
| **Fontes** | `04-clientes/<slug>/fontes/` e `07-referencias/fontes/` | Ninguém edita. Transcrição de reunião, conversa exportada, documento do cliente, print. São a prova |
| **Notas** | todo o resto | O Claude mantém: resume, liga, atualiza. O Guilherme lê, decide e corrige |
| **Regras** | este arquivo e `00-sistema/` | Os dois, evoluindo juntos |

## As três operações

**Registrar** (algo novo chegou: reunião, material, decisão, resultado)
1. Salve o original em `fontes/` com data no nome: `2026-11-03-reuniao-mobiletec.md`
2. Atualize todas as notas que ele afeta: cliente, campanha, playbook. Uma fonte pode mexer em dez notas
3. Registre no log do cliente e no [[00-sistema/log-operacoes]]

**Consultar** (pergunta sobre a operação)
1. Comece pelo [[00-sistema/indice]], depois abra as notas
2. Responda citando a nota de onde veio
3. Resposta que vale guardar (análise, comparação, diagnóstico) vira nota, não fica perdida no chat

**Revisar** (toda segunda, antes da checagem semanal)
- Nota de cliente com `atualizado` há mais de 7 dias
- Contradição entre notas, ou nota que diz algo que uma fonte mais nova desmente
- Nota órfã, sem link de entrada
- Pendência do cliente aberta há mais de 14 dias
- Conceito citado em várias notas sem nota própria
Resultado: uma entrada no log de operações e as correções feitas.

## Onde buscar cada coisa

| Preciso de | Está em |
|---|---|
| Como a agência funciona | `01-agencia/` (jornada, catálogo, motor, suporte, stack) |
| Como entregar um serviço | `02-playbooks/` |
| Passo a passo de uma rotina | `03-processos/` |
| Tudo de um cliente | `04-clientes/<slug>/` |
| Propostas e pipeline | `05-comercial/` |
| Produto próprio (SaaS) | `06-produto/` |
| Referências e templates de criativo | `07-referencias/` |
| Modelos de nota | `_modelos/` |
| Mapa geral do vault | [[00-sistema/indice]] |

## O que não mora aqui

- **Código** (LPs, sites, hubs, vídeos): nos repositórios de código, listados em
  [[01-agencia/stack]]. A nota do cliente aponta o repositório.
- **Arquivos pesados** (fotos, vídeos, PDFs, originais do cliente): no Google
  Drive, em `Hub3Ps/Clientes/<slug>/`. A nota guarda só o link.
- **Senhas, tokens e chaves**: nunca. Nem em nota, nem em log, nem em commit.

## Regras do repositório

- Só a `main`. Nada de branch no vault.
- O plugin Obsidian Git sincroniza sozinho. Na nuvem, faça commit e push na
  `main` ao terminar.
- Commit: `<tipo>(<slug>): <o que mudou>`, em português, sem travessão.
