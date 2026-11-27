---
tipo: agencia
atualizado: 2026-11-09
---
# Stack

| Ferramenta | Papel |
|---|---|
| Obsidian | Cérebro: clientes, escopo, playbooks, processos, tarefas e histórico |
| Claude Code | Execução local, na nuvem e em rotinas. Lê o vault antes de agir |
| GitHub | Cópia online do vault e do código, com histórico. O vault sincroniza pelo Obsidian Git |
| Vercel | Publicação de LPs, sites e hubs |
| MCPs da Meta e do GA4 | Dados direto da fonte |
| n8n e Evolution | Automações e WhatsApp |
| Google Drive | Arquivos pesados: fotos, vídeos e PDFs, em `Hub3Ps/2. AGÊNCIA DE TRÁFEGO/1. CLIENTES ATIVOS/<N>. <Nome>/`. Cliente inativo vai para `2 CLIENTES INATIVOS/`. Projetos internos de IA e automação ficam em `3. AGÊNCIA DE IA/Projetos de IA e automação/` |
| Miro | Só para desenhar estrutura |
| Supabase | Só dentro dos agentes de IA de clientes |
| whatsapp-mcp | Claude lê e envia mensagens no WhatsApp por um número só da agência, conectado como aparelho (não oficial, risco de bloqueio do número). Instalado em 09/11/2026 em `~/ferramentas/whatsapp-mcp`: a ponte em Go roda como serviço do macOS (`com.hub3ps.whatsapp-bridge`), que liga com o Mac e se reinicia se cair. A rotina diária está em [[03-processos/whatsapp-diario]], e o QR se refaz a cada 20 dias, mais ou menos. A API local da ponte só aceita o próprio Mac. Toda mensagem enviada passa pelo ok do Guilherme |
| Composio | Publica no Instagram (feed, carrossel, Reels e Stories) por conta conectada. Em 04/11/2026 só a @guimiguelmkt está conectada; cada cliente precisa conectar a própria conta, que deve ser profissional. Toda publicação passa pelo ok do Guilherme |

## Onde cada coisa vive (Guilherme, 27/11/2026)
| Lugar | O que guarda |
|---|---|
| Obsidian (vault) | Toda a organização e todo documento em texto, de todos os clientes e projetos: cliente, escopo, playbooks, processos, tarefas, histórico, propostas, briefs |
| GitHub | Código, um repositório por projeto. Também guarda a cópia online do vault, que o Obsidian Git envia sozinho a cada 5 minutos |
| Google Drive | Arquivos de cliente e da agência: vídeos, imagens, logos, PDFs |
| Vercel | Só publica sites, LPs e hubs, a partir do GitHub |

**Nada importante fica só no Mac.** O Mac é a cópia de trabalho: o Obsidian edita ali, e os scripts e a ponte do WhatsApp rodam ali. Toda coisa de valor tem cópia no GitHub ou no Drive. As exceções são as credenciais, que vão para um gerenciador de senhas e nunca para o GitHub, e os documentos pessoais em `~/Documents/Pessoal/`.

- No celular: Obsidian Sync, opcional
- O Claude na nuvem e as rotinas leem o vault pelo GitHub

## Plugins do Obsidian
- **Obsidian Git**: commit, pull e push automáticos
- **Dataview**: tabelas a partir dos campos das notas (usado em [[INICIO]])
- **TaskNotes** (desde 18/11/2026): cada tarefa é uma nota em `08-tarefas/notas/`, com quadro central em `08-tarefas/Quadro.base` e um por cliente. Substituiu os kanbans por cliente, que estão em `_arquivo/kanbans-antigos/`
- **Kanban**: plugin mantido para abrir os kanbans antigos do arquivo

## Repositórios de código
| Repositório | O que publica |
|---|---|
| `hub3ps/agencia_marketing` | Hubs internos dos clientes (a reorganizar como repositório só de código) |
| `hub3ps/juria-lps` | LPs públicas do JurIA |
| `hub3ps/agente-whatsapp-hub3ps` | Agente de WhatsApp e painel do Apex, em `apex.hub3ps.com`. Clone local em `~/Desktop/whatsapp-langchain` (antes ficava em `guimiguell/whatsapp-langchain`, conta pessoal) |
| `hub3ps/radar-criadores` | Radar de criadores, clone em `~/Desktop/radar-criadores` |
