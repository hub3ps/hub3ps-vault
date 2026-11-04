---
tipo: sistema
autor: claude
atualizado: 2026-11-04
fonte: sessão "Reorganizar estrutura operacional e clientes" (claude.ai, 08/10 a 04/11/2026)
---
# Contexto da reestruturação da Hub3Ps

Resumo da conversa que desenhou a nova estrutura. Leia inteiro antes de
continuar o projeto.

## 1. Objetivo
O repositório `hub3ps/agencia_marketing` virou o lugar de tudo (código,
conhecimento, estado de cliente, arquivos) e a operação ficou desorganizada. O
Guilherme quer uma estrutura interna padronizada, em que cada cliente puxa os
serviços que contratou e todo o processo se alinha. Primeiro a estrutura
interna completa, depois cada cliente se encaixa nela.

**Regras do projeto:**
- Não mexer no repositório `agencia_marketing`. Ele continua rodando a
  operação atual até a migração terminar
- Migrar tudo, sem deixar nada para trás: repo, todas as branches e o histórico
  das sessões do Claude
- Validar cada estrutura com o Guilherme antes de construir
- Respostas curtas, diretas e profissionais. Sem travessão em nenhum texto

## 2. Board no Miro (fonte visual da estrutura)
**Organograma HUB3Ps v1:** https://miro.com/app/board/uXjVEc61zJI=/

O board original do Guilherme ("Mapa mental") ficou intacto. O conteúdo dos
blocos já foi transcrito em `01-agencia/` e `02-playbooks/`.

| Bloco | Conteúdo | Nota no vault |
|---|---|---|
| A. Jornada do cliente | 7 etapas: Comercial, Onboarding, Estratégia, Produção, Lançamento, Gestão contínua, Renovação | [[jornada]] |
| B. Catálogo de serviços | 8 serviços, cada um com rotina padrão | [[catalogo]] |
| C. Braço de produto | Hub3Ps SaaS (gestão de clube de futebol), separado da agência | [[hub3ps-saas]] |
| D. Motor operacional | Escopo do cliente ativa playbooks, que geram checklist de onboarding, tarefas de implantação, rotinas e relatório | [[motor]] |
| E. Playbooks | Grade 8 serviços x 6 campos, rascunho completo a validar | `02-playbooks/` |
| F. Estrutura de suporte | Playbook comercial, painel do cliente, automações internas, Hub3Ps como cliente 0 | [[suporte]] |
| G. Stack e vault | Ferramentas, onde os arquivos vivem, padrões do vault | [[stack]] |

## 3. Decisões tomadas
**Serviços (8):** Tráfego pago (Meta e Google), LP e site, Criativos e
audiovisual (anúncio estático e vídeo, vídeo institucional e de evento,
impressos, influencer virtual), Tracking, E-mail marketing, Social (Instagram),
Agentes de IA (atendimento no WhatsApp e no Instagram), Busca orgânica (Google
Meu Negócio, SEO, AEO e GEO).

**Cadência padrão da gestão contínua:** dashboard diário e automático,
otimização semanal, relatório quinzenal, relatório mensal com reunião. Cada
serviço tem rotina própria no playbook. O cliente executa só as rotinas dos
serviços do escopo.

**Regra do motor:** o padrão nunca é editado para um cliente. Diferença vira
exceção na nota do cliente. Exceção que se repete em vários clientes vira
padrão.

**Ordem de implantação:** Estratégia, Tracking, LP e site, Criativos, Tráfego
pago, E-mail e Agente.

**Operação solo:** o organograma mostra processos e serviços, não pessoas.

**Stack:**
| Ferramenta | Papel |
|---|---|
| Obsidian | Cérebro: clientes, escopo, playbooks, processos, Kanban, histórico |
| Claude Code | Execução local (dia a dia), na nuvem e em rotinas |
| GitHub | Cópia online do vault e do código. Vault sincroniza pelo Obsidian Git |
| Vercel | Publicação de LPs, sites e hubs |
| MCPs da Meta e do GA4 | Dados direto da fonte |
| n8n e Evolution | Automações e WhatsApp |
| Google Drive | Arquivos pesados, em `Hub3Ps/Clientes/<slug>/` |
| Miro | Só para desenhar estrutura |
| Supabase | Só dentro dos agentes de IA de clientes. Futuro: dados estruturados em volume |

**Por que o vault está no GitHub e não só no Obsidian Sync:** o Sync guarda os
arquivos só nos aparelhos do Guilherme. O Claude na nuvem e as rotinas
agendadas rodam em servidor e precisam ler o vault com o Mac desligado. O MCP
do Obsidian não resolve, porque só funciona com o Mac ligado. O Sync pode ser
usado só para o celular.

**Uso:** sessão local (app Claude, "Este computador", pasta `hub3ps-vault`,
Worktree desligado) no dia a dia. Nuvem e rotinas leem e escrevem pelo GitHub.
O vault usa só a `main`.

## 4. O vault
**Repositório:** `hub3ps/hub3ps-vault` (privado). Clone local em
`~/Documents/hub3ps-vault`. Plugins Obsidian Git, Dataview e Kanban instalados
em 04/11/2026, com backup automático a cada 5 minutos.

**Padrão LLM Wiki (Andrej Karpathy, gist de abril de 2026)**, adaptado:
- Três camadas: fontes (originais, nunca editados), notas (o Claude mantém),
  regras (`CLAUDE.md` e `00-sistema/`)
- Três operações: registrar, consultar, revisar (toda segunda)

**Outros padrões incorporados** (de repos pesquisados): protocolo de sessão no
`CLAUDE.md` (brain-template), nota viva por cliente lida antes de toda tarefa
(digital-marketing-pro), arquivo de lições (marketing-os-starter), índice, log
de operações e verificação de notas quebradas (obsidian-vault-template).

**Pendência conhecida:** `03-processos/convencoes.md` tem um link para
`credenciais` que não existe no vault. Corrigir na migração.

## 5. Revisão do histórico (03/11/2026)
Lidos: repo e as 14 branches, as 3 rotinas agendadas, títulos e resumos das 58
sessões do Claude. As conversas completas não foram lidas, só a parte mais
recente de 5 delas.

**Clientes e frentes reais:**
| Cliente | O que existe | Onde está hoje |
|---|---|---|
| Mobiletec · JurIA | Tráfego Meta (conta `1465935581974017`), LPs (repo `juria-lps`), site novo em Astro (branch `feat/site-astro`, 60 commits fora da main), criativos estáticos e vídeo (Remotion), Instagram orgânico, influencer virtual Helena, tracking (GTM, GA4, consentimento), e-mail do trial, hub `juria.hub3ps.com`, painel de funil, impressos (flyer OAB, banner) | `clients/juria/` |
| Mobiletec · institucional | Vídeo de abertura para evento (sexta versão) | Branch `claude/loving-archimedes-rp33cv` (36 commits fora da main) |
| DS Muay Thai Squad | Tráfego Meta (conta `800990442489726`, USD), LP de trial e página da bio no ar, hub `dsmuaythai.hub3ps.com`, reposicionamento e simulador do Instagram | `clients/dsmuaythai/` |
| Apex | Agente de IA "Laura" no WhatsApp; checkout de pagamento exige conta PJ | `clients/apex/` |
| Liliane Fontenele (vereadora, Itajaí) | Proposta de automação do gabinete enviada em 21/10 (contato: Diego). A Meta proíbe políticos de usar a API do WhatsApp Business | Branch `claude/admiring-allen-xbjdup`, fora da main |
| Usivic | Proposta de agente de IA, sem retorno desde 19/06 | `clients/usivic/` |
| Hub3Ps (cliente 0) | Site pessoal para a bio do Instagram, parado aguardando LinkedIn, cidade ou atendimento online, e planilha de leads | Sessão de 29/10 |
| Hub3Ps SaaS | Estrutura do sistema de clube desenhada, nada construído | `hub3ps-saas/` e board no Miro |

**Automações existentes:**
- Rotina "Hub interno" (`trig_01NkctTDaZ26baqsL6H3x9f3`): atualiza a
  Performance dos dois hubs. Hoje roda a cada 48h; a decisão é diária. **O
  Guilherme ajusta a frequência na interface depois**
- Rotina "Resumo diário no WhatsApp" (`trig_01Fmw2SWUC3xcfpbDofaSs91`), via n8n
  e Evolution. **Parada:** a instância Hub3Ps da Evolution precisa ser
  reconectada pelo QR code
- Runbook das rotinas fora da main, na branch `claude/focused-brahmagupta-fhfuqd`

**Sessões aguardando decisão do Guilherme:** Meta Ads JurIA (evento Lead ou
CompleteRegistration, e posicionamento), Hub JurIA, site pessoal, rotinas
(QR da Evolution), estratégia de e-mail do JurIA.

**Desatualizado no repo antigo:** `CLAUDE.md` e `clients/README.md` não citam
Liliane nem Mobiletec institucional.

## 6. Próximos passos
1. **Migrar cliente por cliente**, começando pela Mobiletec (JurIA e
   institucional), que concentra cerca de 70% do histórico. Para cada um:
   nota viva com escopo real, exceções, Kanban com as pendências atuais, log
   com o histórico e fontes originais. Ler a `main` e as branches do
   `agencia_marketing` sem alterar nada nele
2. Depois: DS Muay Thai, Apex, Liliane, Usivic, Hub3Ps
3. Migrar runbooks (`docs/processos/`), referências e skills
4. Validar com o Guilherme os playbooks de cada serviço, coluna por coluna
5. Definir o destino do repo `agencia_marketing`: virar repositório só de código
   (hubs, LPs, vídeos) depois da migração

## 7. Inventário fora da main (04/11/2026)
Levantado na sessão local que migrou o JurIA. As branches foram comparadas com a
`origin/main` do `agencia_marketing`, e não com a `main` local, que está 127
commits atrás.

**Branches com trabalho fora da `origin/main`:**
| Branch | Commits fora | Cliente | Destino na migração |
|---|---|---|---|
| `feat/site-astro` | 113 (último em 30/10) | juria | Site novo. A local está 50 commits atrás da remota |
| `claude/loving-archimedes-rp33cv` | 36 (último em 27/10) | mobiletec | Site institucional e vídeo, sexta versão |
| `claude/admiring-allen-xbjdup` | 3 (21/10) | liliane | Proposta de automação do gabinete |
| `claude/focused-brahmagupta-fhfuqd` | 3 (13/10) | agencia | Runbook das rotinas agendadas, que vai para `03-processos/` |

**Já contidas na `origin/main`, sem nada a migrar:** `clever-wozniak`,
`trusting-bell`, `zealous-newton`, `intelligent-shannon`, `gallant-mayer`,
`zen-planck`, `beautiful-cerf`, `docs/juria-comercial-campanhas` e `dc8968a`.

**`juria-lps`:** nada fora da `main`. A local está 1 commit atrás.

**Sessões do Claude:** no app local só existem 2 sessões, nenhuma do JurIA. As
da nuvem não são legíveis daqui, e o trabalho delas está nas branches acima.

**Arquivos soltos que vão para o Drive** (`~/Downloads`): pasta `JurIA/`
(proposta, planos de mídia do mês 1, minibrandbook, LPs antigas, posts),
`CRIATIVOS/criativos juria`, `JurIA_Funcionalidades.pdf`,
`Revisao_Site_JurIA_Isadora.pdf`, `avatar_juria.png`, pasta `clientes mobiletec`,
`Design Kits - Mobiletec.zip`, `mobiletec-institucional-locucao.mp4`,
`NF_Mobiletec_Outubro.pdf` e o contrato Hub3Ps e Mobiletec (Clicksign). Na
Área de Trabalho: `JurIA - Apresentacao Institucional.pdf`.
