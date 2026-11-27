---
tipo: cliente
slug: apex
nome: Apex
empresa: Apex Wellness Club
status: implantacao
servicos: [agentes-de-ia]
inicio: 2026-07-27
contrato: TODO
vigencia: TODO
valor-mensal: TODO
meta: TODO
contatos: Matheus Goulart (profissional único), Beatriz (equipe de atendimento)
drive: https://drive.google.com/drive/folders/1gnE_W07HullYGpF5WbIzEWPtbagEhJRj
painel: https://apex.hub3ps.com
repositorios: [guimiguell/whatsapp-langchain]
proxima-reuniao: TODO
atualizado: 2026-11-19
autor: claude
---
# Apex

> **Estado atual:** a Amanda está em produção no número de teste, agora pela API oficial da Meta (17/11/2026). O painel ganhou visual novo, atendimento humano, templates, lembretes e campanhas, todos construídos entre 17 e 18/11. Falta fazer os testes reais T1 a T9 e, para o go-live, conectar o número da clínica e receber do cliente o termo LGPD, as chaves da InfinitePay e a agenda compartilhada.

## Quem é
- **Negócio:** clínica de liberação miofascial em Itajaí/SC, com acupuntura, fisioterapia e recovery. Fica dentro do Studio Remo, na R. Jorge Tzachel, 200, Fazenda. Matheus Goulart é o profissional único.
- **Público:** pacientes de dor e recuperação que marcam pelo WhatsApp, cerca de 30 contatos por dia, hoje atendidos por uma secretária.
- **Região:** Itajaí/SC.
- **Idioma:** português do Brasil.

## Escopo
- [[agentes-de-ia]]: a Amanda agenda, qualifica, vende pacote e reduz faltas. Tem também um painel da clínica, com calendário, ficha do paciente e registro de atendimento

TODO: modelo comercial e prazo. O briefing de 27/07 deixou para depois, e não há proposta nem contrato registrados.

## Exceções ao padrão

| Serviço | Exceção | Motivo | Desde |
|---|---|---|---|
| agentes de IA | O código vive no repo `guimiguell/whatsapp-langchain`, numa conta pessoal do GitHub, fora da organização hub3ps | O projeto nasceu antes da Apex, em 01/2026 | 27/07/2026 |
| agentes de IA | Roda numa VPS com EasyPanel. Desde 17/11 usa a API oficial da Meta (Hub3Ps é Tech Provider), com o número de teste Operacional Hub3ps. O número do Evolution foi para outro projeto | Herança do projeto e aprovação da Meta | 17/11/2026 |
| agentes de IA | A agente usa o nome da atendente, Amanda. Não diz que é IA, mas confirma se perguntarem | Decisão da clínica (ADR 0010 e resposta de 13/10) | 13/10/2026 |
| agentes de IA | As mensagens padronizadas da equipe saem literais, em balão único | ADR 0011 | 07/10/2026 |
| agentes de IA | O cadastro dos 316 pacientes, com CPF e saúde, nunca entra em repositório. Vai para o banco por migração | LGPD | 21/08/2026 |
| agentes de IA | Nada de diagnóstico, indicação de tratamento ou promessa de resultado. Dúvida clínica vai para a avaliação com o Matheus | Saúde e conselho profissional | 27/07/2026 |

## Depende do cliente
Conforme o `ESTADO.md` do repo (17/11/2026):

- [ ] Texto do termo de consentimento LGPD, que está no Notion. Bloqueia o go-live e a anamnese
- [ ] Estrutura real do formulário de anamnese e as três perguntas do Matheus
- [ ] Explicar por que 39 das 44 colunas do export vieram vazias: ninguém preenche ou o CSV não trouxe?
- [ ] Onde vive hoje o saldo de pacote, e as regras do membership (o crédito acumula ou expira?)
- [ ] Se o Matheus para de usar o Notion
- [ ] Compartilhar com a service account a agenda dos compromissos pessoais
- [ ] Cartão antecipado ou no dia? (confirmar com a Beatriz)
- [ ] De quem é o telefone que Otávio e Patrícia Socha dividem
- [ ] Pergunta da Beatriz de 17/09, ainda sem resposta (ver `pendencias.md` no repo)
- [ ] Logo da Apex, versões clara e escura, para Ajustes › Marca
- [ ] Fluxos de atendimento por perfil de lead e a lista de qual anúncio leva a qual perfil (Beatriz)

## Acessos
Nunca guarde senha aqui. As variáveis ficam no EasyPanel.

- **Painel:** https://apex.hub3ps.com
- **Infra:** VPS com EasyPanel, com os serviços `db`, `api`, `worker`, `evolution`, `evolution-db` e `frontend`
- **WhatsApp:** API oficial da Meta, com o número de teste Operacional Hub3ps (+55 47 9969-4347). O número da clínica é (47) 99609-4508 e entra no go-live pelo botão Conectar WhatsApp
- **Google Calendar:** service account configurada. Hoje aponta para a agenda de teste, de propósito
- **InfinitePay:** testado com a conta de teste do Guilherme. Faltam a API Key e a InfiniteTag da conta da Apex. A nota de contexto da reestruturação diz que o checkout exige conta PJ. TODO: conferir
- **Modelo:** `anthropic/claude-sonnet-5.5`, desde 13/10

## Onde está cada coisa (repo `whatsapp-langchain`, clone em `~/Desktop/whatsapp-langchain`)

| Preciso de | Está em |
|---|---|
| Onde parou, o que trava e o que vem | `ESTADO.md` |
| O que mudou para quem conversa com a Amanda | `CHANGELOG.md` |
| Negócio, serviços, regras, persona e FAQ | `docs/cliente-apex/` |
| Pendências e riscos completos | `docs/cliente-apex/pendencias.md` |
| Roteiro de testes do go-live | `docs/cliente-apex/roteiro-de-testes.md` |
| Plano por fases | `docs/PLANO-IMPLEMENTACAO.md` |
| Decisões (ADRs) | `docs/decisions/` |
| Briefing original de julho | [[04-clientes/apex/fontes/2026-07-27-briefing\|fontes/2026-07-27-briefing]] (migrado do `agencia_marketing` em 27/11/2026) |
| FAQ de 47 itens (`base_conhecimento_studio_apex.xlsx`) | Drive, pasta 15. Apex Wellness Club (TODO: subir) |

## Links
- Tarefas: [[04-clientes/apex/tarefas.base|quadro de tarefas]]
- Log: [[04-clientes/apex/log|log]]
- Fontes: `fontes/`
- Drive: [15. Apex Wellness Club](https://drive.google.com/drive/folders/1gnE_W07HullYGpF5WbIzEWPtbagEhJRj)
- Painel: https://apex.hub3ps.com
