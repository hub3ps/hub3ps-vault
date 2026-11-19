---
tipo: log
autor: claude
---
# Log

A entrada mais recente fica no topo, uma por sessão de trabalho.

### 2026-11-19 · Revisão do quadro de tarefas
- **O que fiz:** comparei o quadro com o `ESTADO.md` do repo (17/11). A Fase 6 foi para Feito (virou WA-4b). Quatro tarefas que dependem do Guilherme ganharam `gui`. Criei as tarefas dos testes reais T1 a T9, do go-live com o número real pela API oficial, do logo da Apex e dos fluxos por perfil de lead da Beatriz, e registrei como feito o que entrou em 17 e 18/11. Atualizei o estado e os acessos na nota do cliente.
- **Resultado em:** `08-tarefas/notas/apex - *.md`, `04-clientes/apex/cliente.md`
- **Próximo passo:** testes reais T1 a T9; pedir à Beatriz os fluxos por perfil.

### 2026-11-17 e 18 · Canal oficial, painel novo, templates, lembretes e campanhas
- **O que fiz:** app da Hub3Ps aprovado como Tech Provider; canal oficial e botão Conectar WhatsApp (WA-1 e WA-2), com a instalação da Apex trocada para a API oficial no número Operacional Hub3ps; atendimento pelo painel (WA-3); visual estilo Apple, logo do cliente, menu por tarefa e tela Hoje; templates (WA-4a), lembretes com horário ajustável (WA-4b) e campanhas com opt-in (WA-5).
- **Resultado em:** repo `whatsapp-langchain`, ADRs 0014 a 0022, `ESTADO.md`
- **Próximo passo:** testes reais T1 a T9 listados no `ESTADO.md`.

### 2026-11-04 · Migração do Apex para o vault
- **O que fiz:** criei a nota do cliente, o kanban e este log. As fontes foram o `ESTADO.md` e os docs do repo `whatsapp-langchain` (atualizados em 21/10, sem nada fora da `main`) e o briefing de julho no `agencia_marketing`. Nenhum repositório foi alterado.
- **Resultado em:** `04-clientes/apex/`
- **O que achei:** o `agencia_marketing` parou em 28/07 e ainda fala em "Laura" e em "coleta avançada". O projeto real está no `whatsapp-langchain`, em produção no número de teste, e a agente agora se chama Amanda. O próprio `ESTADO.md` se contradiz sobre a cobrança: numa linha diz que foi ligada em 21/10 com a conta de teste, e em outra que está desligada até chegarem as chaves. Registrei como "testada e à espera das chaves da Apex".
- **Próximo passo:** o Guilherme revisa e define o modelo comercial.

## Histórico anterior ao vault
Resumo do `ESTADO.md`, dos commits do `whatsapp-langchain` e do `agencia_marketing`.

- **21/10/2026:** pagamento antecipado pela InfinitePay (ADR 0012) e depois um link só, com desconto no PIX (ADR 0013): PIX a R$ 220 e cartão a R$ 230, conferidos na página real. Corrigido o nome do paciente no Calendar.
- **13/10/2026:** ajustes de conversa pedidos em 17/09 e 07/10. A atendente vira Amanda, as mensagens da equipe saem literais, o cadastro deixa de pedir endereço e o modelo passa a ser o Claude Sonnet 5.5.
- **07/10/2026:** a Beatriz envia as mensagens padronizadas do atendimento e dois áudios.
- **17/09/2026:** reunião com a clínica, em que a Beatriz pede mensagens mais explicativas. O número tinha sido suspenso e voltou, e a versão do WhatsApp Web foi corrigida.
- **26/08/2026:** agente e painel em produção no número de teste, e os 299 cadastros do Notion migrados para o banco.
- **21/08/2026:** chegam o export de 316 pacientes e a tabela de preços 2026.
- **14 a 27/08/2026:** construção das fases 0 a 5: base, segurança, áudio e imagem, cadastro, agenda, Google Calendar e encaminhamento ao Matheus.
- **28/07/2026:** onboarding do cliente registrado no `agencia_marketing`.
- **27/07/2026:** briefing de 14 blocos e FAQ de 47 itens enviados pelo cliente.
