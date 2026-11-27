---
tipo: sistema
autor: claude
atualizado: 2026-11-27
---
# Fechamento da migração e agente da manhã (27/11/2026)

Levantamento feito comparando o vault, o `agencia_marketing`, as rotinas na nuvem, a tarefa local do WhatsApp e o organograma. Continua a seção 8 de [[contexto-reestruturacao]].

## Como as rotinas funcionam de verdade
**Rotina na nuvem** (as 3 de hoje): no horário marcado, um Claude liga num computador da Anthropic, baixa do GitHub os repositórios da lista dela, recebe os conectores anexados (hoje: Meta Ads, n8n, Supabase, Vercel), executa o texto da rotina e desliga. Roda com o Mac desligado. **Não vê nada do Mac:** nem a pasta local do vault, nem a ponte do WhatsApp, nem o Chrome. Só vê o vault se o repositório `hub3ps-vault` estiver na lista dela, e hoje não está. Avisa por notificação no app do Claude ou pelo webhook do n8n.

**Tarefa agendada local** (o WhatsApp diário): roda no app do Claude neste Mac, às 8h dos dias úteis. Vê tudo do Mac, mas só roda com o Mac ligado e acordado.

## Diagnóstico
| Rotina | Onde roda | Problema |
|---|---|---|
| Resumo diário no WhatsApp (`trig_01Fmw2SWUC3xcfpbDofaSs91`), 7h52 | Nuvem | Só JurIA e DS: Marjorie e Churrasco ficam fora. Contas fixas no texto. Token do webhook escrito no texto. Lê o repo antigo. **Hoje (27/11) o envio falhou:** o n8n respondeu "Error in workflow" duas vezes e a mensagem não chegou, só uma notificação no app |
| Hub interno (`trig_01NkctTDaZ26baqsL6H3x9f3`), 7h47 | Nuvem | Roda a cada 48h, e a decisão era diária. Só JurIA e DS |
| Site Astro, execução noturna (`trig_01RrXZGiQYEH1FysBKDA4bHm`) | Nuvem | Desligada desde 01/10. O site está no ar desde 12/11: sobra |
| WhatsApp diário dos grupos, 8h, dias úteis | Mac | Depende do Mac acordado e na tomada. Grava no vault e funciona |

**O que nenhuma rotina faz hoje:** olhar as tarefas do vault (vencendo, atrasadas, esperando cliente) e guardar o que viu. O resumo das contas se perde no WhatsApp.

## Proposta: o agente da manhã
Uma rotina na nuvem, todo dia às 7h30, que trabalha como um funcionário que chega antes de você:
1. **Lê o vault pelo GitHub.** A lista de clientes ativos e as contas de anúncio saem do `cliente.md` de cada um (campo `meta_conta`), e não do texto da rotina. Cliente novo entra sozinho
2. **Contas de anúncio:** pagamento e números de ontem e dos últimos 7 dias, em todas as contas ativas. Alerta para conta parada, pagamento pendente, campanha ativa sem gasto e custo por resultado muito acima da média da semana
3. **Tarefas:** o que vence hoje, o que está atrasado e o que espera o cliente há mais de 3 dias
4. **Grava o briefing no vault**, em `00-sistema/diario/AAAA-MM-DD.md`, e sobe no GitHub. Arquivo próprio, para não brigar com o Obsidian Git
5. **Avisa:** WhatsApp pelo n8n, com o token numa variável da rotina e fora do texto, e a notificação do app como reserva quando o WhatsApp falhar

O que o agente faz fica num runbook do vault, `03-processos/agente-da-manha.md`, e a rotina só diz "leia e siga". **Mudar o agente é editar uma nota no Obsidian**, sem mexer na rotina. Delegar uma coisa nova para ele é acrescentar um passo nessa nota.

## Etapas
**Ordem decidida em 27/11 (Guilherme):** primeiro fechar a estrutura (etapas 2 a 5), depois o agente da manhã (etapa 1). A regra de onde cada coisa vive está em [[01-agencia/stack|stack]].

### Etapa 1 · Rotinas (primeiro, hoje)
- [ ] 1.1 Campo `meta_conta` no `cliente.md` dos 4 clientes com anúncio: JurIA, DS Muay Thai, Marjorie e Churrasco da Elite
- [ ] 1.2 Runbook `03-processos/agente-da-manha.md`, aproveitando o da branch `claude/focused-brahmagupta-fhfuqd`
- [ ] 1.3 Consertar o fluxo do n8n que falhou hoje (provável: instância da Evolution desconectada, o que pede o QR no seu celular)
- [ ] 1.4 Rotina do agente lendo o vault, com o token em variável. Teste rodando na hora
- [ ] 1.5 Hub interno diário
- [ ] 1.6 Apagar a rotina do site Astro
- [ ] 1.7 Trocar o token do webhook no n8n: ele está escrito no texto da rotina desde 13/10

### Etapa 2 · Conhecimento do repo para o vault
- [x] 2.1 Os 12 runbooks que ainda estão só em `docs/processos/`: atualizar-hub-juria, atualizar-hub-dsmuaythai, canais-ga4-juria, configurar-ga4-juria, nova-campanha, nova-referencia, novo-criativo, post-instagram-juria, publicar-lp-dsmuaythai, publicar-lp-juria, publicar-site-juria e video-juria. Migrar é mover e deixar ponteiro ([[fonte-unica-vault]])
- [x] 2.2 JurIA: brief, brand, comercial, funil, e-mail e Helena, que só existem em `clients/juria/`
- [x] 2.3 Usivic e Liliane: nota no vault (hoje só aparecem citadas)
- [ ] 2.4 Skills e biblioteca de referências: ficam no repo, porque o Claude Code as carrega de lá. Entra um índice delas no vault

### Etapa 3 · Branches fora da main
- [ ] 3.1 `claude/loving-archimedes-rp33cv` (39 commits): site institucional e vídeo da Mobiletec
- [x] 3.2 `claude/admiring-allen-xbjdup` (3): proposta da Liliane
- [ ] 3.3 `claude/focused-brahmagupta-fhfuqd` (3): runbook das rotinas, que entra na 1.2

### Etapa 4 · O repo vira só código
- [x] 4.1 `CLAUDE.md` do `agencia_marketing` passa a apontar para o vault como cérebro
- [ ] 4.2 A `main` local está 10 commits à frente e 23 atrás da remota: sincronizar
- [ ] 4.3 Commit do que está pendente (`cortar_respiros.py`, `hubs/`, ajustes do editar-video), com o seu ok
- [ ] 4.4 Dar cópia na nuvem ao que só existe no Mac: os 8 ajustes do `~/ferramentas/whatsapp-mcp`, `Desktop/projetos_python`, `Desktop/site-guimiguelmkt` e `credenciais.local.md` (num gerenciador de senhas). `Documents/juria-exportacoes` já tem cópia no Drive desde 26/11

### Etapa 5 · Arquivos
- [ ] 5.1 O que sobrou no Downloads vai para o Drive ou para a lixeira, com o seu ok em cada grupo
- [ ] 5.2 Pastas velhas para a lixeira: `fastapp-main`, `hub3ps-site` (cópia no GitHub) e as duas pastas ocultas de edição

### Etapa 6 · Fechamento
- [ ] 6.1 Organograma no Miro, versão 6, com o agente da manhã
- [ ] 6.2 Nota de conteúdo para o Instagram em `04-clientes/hub3ps/conteudo/`, contando o antes e o depois

**Fica para depois, porque precisa de você coluna a coluna:** validar os 8 playbooks, que seguem em rascunho.

## Progresso (27/11, fim da tarde)
- 2.1: 10 runbooks no vault, ponteiros no repo. Faltam os 2 de atualizar o hub, que vão com o agente da manhã
- 2.2: pedido às sessões do JurIA, do DS e do Churrasco. Conferir o que cada uma entregou
- 2.3: Apex (briefing em `fontes/`), Usivic e Liliane (em `05-comercial/propostas/`) migrados
- 3.1: textos da Mobiletec copiados da branch para `04-clientes/mobiletec/`. Falta o ponteiro na branch, que exige push (a branch é a produção do site)
- 3.2: Liliane feita. 3.3 entra na 1.2
- Nada commitado no `agencia_marketing`
- 2.2 (fim): JurIA com 33 notas novas, 3 juntadas e 11 em `_arquivo/juria/`, e 47 ponteiros no repo. DS com 10 notas e ponteiros. Churrasco com o README virado ponteiro. Ficam no repo só o que código lê, os README de pasta de código e `credenciais.local.md`. Todos os ponteiros abrem notas que existem (conferido)
- 4.1: `CLAUDE.md` e `clients/README.md` do repo dizem que ele é só de código e mandam ler o vault
- Binários do JurIA (cerca de 170 MB): quase todos são lidos por código (LPs, vídeo, peças em HTML) e ficam no repo. Ao Drive vão só as peças finais, com o ok do Guilherme
