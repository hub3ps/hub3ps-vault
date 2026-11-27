---
tipo: historico
cliente: dsmuaythai
atualizado: 2026-10-13
autor: claude
origem: agencia_marketing/clients/dsmuaythai/README.md
migrado: 2026-11-27
---
# DS Muay Thai Squad

Academia de Muay Thai em **Saugus, Massachusetts** (North Shore, região de
Boston). Head coach **David Silva**, brasileiro, ex-bombeiro e ex-atleta
profissional. Cliente da Hub3Ps desde 2025.

**Escopo:** funil completo. LP e conversão primeiro, tráfego pago depois.
**Comunicação:** inglês, público americano local.
**Públicos:** adulto para si **e** responsável por filho, na mesma página, porque
a verba de $6,00/dia não sustenta duas campanhas simultâneas.

---

## 🟡 Onde paramos · 22/09/2026

**A LP está pronta, nas duas versões.** Todas as perguntas ao David foram
respondidas, em duas rodadas (16/09 e 22/09), a avaliação da Jasna substituiu a
de "Prime Clean", a PT foi aprovada e a EN foi gerada dela. Nenhuma das duas tem
pendência.

**Destino decidido: `trial.dsmuaythaisquad.com`, no Vercel da Hub3Ps.** Pixel e
`noindex` instalados, pasta de publicação montada. Falta criar o projeto no
painel do Vercel e o CNAME no DNS. Passo a passo em
`docs/processos/publicar-lp-dsmuaythai.md`.

O que a página responde hoje, e que o site atual não responde:

| Objeção | Resposta na LP |
|---|---|
| E se eu não puder ir? | Remarca até 1 hora antes, por telefone, Instagram ou e-mail |
| Tem turma à noite? | Grade completa da semana, bloco próprio |
| É só homem? | Todas as turmas são mistas |
| Quem são vocês? | 140+ alunos ativos, 4 anos em Saugus, premiada pela Northshore Magazine, 5,0 em 113 avaliações |

### Não bloqueia a LP, mas segue aberto com o David

| Pergunta | Para quê |
|---|---|
| **Política de devolução da taxa** | Guilherme decide com o David. Vira pergunta no FAQ quando fechar, é a objeção que sobrou de pagar antes |
| Resultados do Pro Team e cartel do David | Reforçar o bloco do professor |
| **Quantos dos agendamentos viraram matrícula** | Define se $72,08 é bom, e o valor a pôr na conversão personalizada |

⚠️ **Conferência de operação, antes de publicar.** Quinta às 19h é
`Competitors only` e sexta é sparring, mesmo que leve. Se o Calendly oferece
esses horários para a aula experimental, um iniciante cai na turma errada no
primeiro contato com a academia. Conferir os slots do Calendly contra a grade.

### Próximos passos, na ordem

1. Commit e push da LP e da pasta `publicado/` (o painel do Vercel só enxerga a
   pasta depois que ela está no GitHub)
2. Guilherme cria o projeto `dsmuaythai-lps` no painel do Vercel e adiciona o
   domínio. A conexão MCP não tem permissão para criar projeto
3. Designer cria o CNAME do `trial` no DNS da academia
4. Conferir os horários que o Calendly oferece contra a grade
5. Teste de medição sem pagar, e conferir pela API que os eventos chegam com a
   URL nova
6. Apontar a campanha ativa para a LP nova e medir contra **$72,08/agendamento**

---

## Mapa da pasta

| Onde | O que é |
|---|---|
| [[04-clientes/dsmuaythai/briefing|briefing]] | Briefing em 12 blocos, com status por bloco |
| [[04-clientes/dsmuaythai/marca/marca|marca]] | Identidade extraída do site, não de brandbook |
| `clients/dsmuaythai/campanhas/` | Histórico da conta Meta lido pela Marketing API |
| `clients/dsmuaythai/lps/` | Análise da LP atual, avaliações do Google e a **LP nova** |
| `clients/dsmuaythai/lps/trial-lp/` | A LP: `index-pt.html` (aprovação) e `index.html` (fonte da publicação) |
| `clients/dsmuaythai/lps/publicado/` | ⛔ Gerada, é o que vai ao ar: `trial/` e `bio/`, mais o `vercel.json` que escolhe pelo domínio |
| `clients/dsmuaythai/hub/` | Hub do cliente em `dsmuaythai.hub3ps.com`: Performance, Instagram e Plano. Projeto Vercel `dsmuaythai`. Runbook em `docs/processos/atualizar-hub-dsmuaythai.md` |
| `clients/dsmuaythai/lps/bio/` | Página do link da bio, `bio.dsmuaythaisquad.com`. Publicada em `lps/publicado/bio/`, no projeto `dsmuaythai-lps`. Links pendentes (`href="#"` com `data-link`) |
| `clients/dsmuaythai/assets/fotos/` | 32 fotos resgatadas do site, por tipo |
| `clients/dsmuaythai/creatives/` | Avaliação do vídeo de depoimentos |
| `clients/dsmuaythai/ferramentas/` | Servidor local para revisar a LP, e o script que monta a pasta publicada |
| `source/` | Extração bruta do site em 01/09/2026 |

## Ver a LP

```bash
python3 clients/dsmuaythai/ferramentas/servidor-local.py
```

- 🇧🇷 aprovação: http://127.0.0.1:8765/lps/trial-lp/index-pt.html
- 🇺🇸 publicação: http://127.0.0.1:8765/lps/trial-lp/

## Contas e acessos

| Canal | Conta | Estado |
|---|---|---|
| Meta Ads | `800990442489726` · USD | Liberada no MCP desde 13/10/2026. Antes disso, só pela Marketing API |
| Google Ads | `104-170-9245` | ⚠️ Windsor no plano gratuito, limite estourado. **Nunca foi lido** |
| Pixel | `25913656948303012` | Vivo. Os eventos `invitee_*` vêm da integração do próprio Calendly, não do site |
| Conversões personalizadas | `Escolheu o dia` (`962316889514579`) · `Escolheu o horário` (`1720514239024454`) · `Aula experimental paga` (`1081697741136388`) | Criadas em 17/09/2026. Regra: evento + URL contendo `dsmuaythaisquad.com` ou `calendly.com`. As duas primeiras já receberam evento. **Regra não se edita**: domínio novo exige conversão nova |
| Vercel (hub) | `dsmuaythai`, time `hub3psmarketing` | Serve `dsmuaythai.hub3ps.com` a partir de `hub/` |
| Vercel | `dsmuaythai-lps`, time `hub3psmarketing` | Serve `trial.dsmuaythaisquad.com` e `bio.dsmuaythaisquad.com` a partir de `lps/publicado/` |
| Página do Facebook | `102351215972726` | É a que roda os anúncios. `100085893254469` é perfil pessoal |
| Google Business | `/g/11tfq328_m` | 5,0 · 113 avaliações (22/09/2026) |

**O MCP da Meta recusa esta conta** (`is_ads_mcp_enabled: false`, rollout da
Meta, sem ação nossa). O contorno é a **Marketing API direto**, com o token da BM
guardado no cofre da agência. Detalhe em
[[04-clientes/dsmuaythai/campanhas/historico-meta-ate-2026-08|historico-meta-ate-2026-08]].

## O diagnóstico em uma tela

$2.276,45 gastos desde 26/08/2025. O funil é **agendamento no site via Calendly**,
não Messenger.

| Etapa | Volume | Taxa |
|---|---|---|
| Cliques pagos | 4.594 | |
| Visitas à página de agendamento | 1.965 | 43%, saudável |
| **Agendamentos** | **7** | **0,4%** |

A perda inteira está na segunda etapa. Em agosto, com o evento de otimização
corrigido para `invitee_meeting_scheduled`, a taxa subiu para 1,6% e o custo caiu
para **$72,08 por agendamento**, que é a referência a bater.

⚠️ Ao publicar a LP nova, essa taxa **deixa de ser comparável**: o Calendly passa
de iframe embutido para popup, e o evento de visita passa a disparar só no
clique. Medir por `landing_page_view → invitee_meeting_scheduled`.

## Backlog

- Testar reserva **sem pagamento no ato**, cobrando na recepção
- Gravar vídeo de depoimentos **com adultos**, no mesmo formato do que existe com
  adolescentes, para os dois entrarem juntos na bifurcação
- Desbloquear o Google Ads: limpar contas do Windsor ou subir de plano
- Fachada, recepção e turma adulta cheia faltam no acervo de fotos
- Frente em **português**: os nomes dos avaliadores são majoritariamente
  brasileiros e boa parte escreveu em português. É o teste mais barato se o CPL
  apertar
