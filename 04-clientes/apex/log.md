---
tipo: log
autor: claude
---
# Log

A entrada mais recente fica no topo, uma por sessão de trabalho.

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
