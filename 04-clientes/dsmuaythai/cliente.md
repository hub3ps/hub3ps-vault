---
tipo: cliente
slug: dsmuaythai
nome: DS Muay Thai Squad
empresa: DS Muay Thai Squad inc
status: ativo
servicos: [trafego-pago, tracking, lp-e-site, social]
inicio: 2025-08-26
contrato: TODO
vigencia: TODO
valor-mensal: TODO
meta: TODO
contatos: David Silva (head coach), designer do site WordPress (DNS), TODO nome do designer
drive: TODO (Hub3Ps/Clientes/dsmuaythai/)
painel: https://dsmuaythai.hub3ps.com
repositorios: [hub3ps/agencia_marketing]
proxima-reuniao: TODO
atualizado: 2026-11-04
autor: claude
---
# DS Muay Thai Squad

> **Estado atual:** só a campanha de seguidores roda, a US$ 7/dia (API, 04/11/2026). A de agendamento da aula experimental foi pausada pelo Gustavo em 27/10, sem motivo registrado. A LP de trial e a página da bio estão no ar em `dsmuaythaisquad.com`. Os stories dos destaques esperam a conferência do David.

## Quem é
- **Negócio:** academia de Muay Thai em Saugus, Massachusetts, na North Shore de Boston. O head coach, David Silva, é brasileiro, ex-bombeiro e ex-atleta profissional. Tem mais de 140 alunos ativos e cerca de 4 anos em Saugus (David, 16/09/2026).
- **Público:** adultos que treinam para si e pais que matriculam os filhos (kids a partir de 5 anos e teens), atendidos numa campanha só.
- **Região:** Saugus e North Shore. A campanha de seguidores atinge todo o estado de Massachusetts.
- **Idioma:** inglês, para o público americano local. A copy é escrita e aprovada em português e traduzida no fim.
- **Oferta:** 3 aulas experimentais por US$ 29,99, pagas no ato pelo Calendly. Planos Silver (US$ 179 a 209/mês) e Gold (US$ 199 a 249/mês).

## Escopo
Funil completo, definido em 01/09/2026: o destino vem antes da mídia.

- [[lp-e-site]]: LP de trial (`trial.dsmuaythaisquad.com`) e página da bio (`bio.dsmuaythaisquad.com`). O site institucional continua no WordPress, com o designer da academia
- [[tracking]]: Pixel, as conversões personalizadas do Calendly e o hub com Performance, Instagram e Plano
- [[trafego-pago]]: Meta Ads. O Google Ads (`104-170-9245`) nunca foi lido
- [[social]]: reposicionamento do Instagram (bio, destaques, fixados e stories)

TODO: meta numérica de matrículas, verba mensal acordada e prazo do contrato. Nada disso está registrado.

## Exceções ao padrão

| Serviço | Exceção | Motivo | Desde |
|---|---|---|---|
| tráfego pago | A conta é em USD, no fuso de Nova York | Cliente nos EUA | 2025 |
| tráfego pago | Uma campanha atende os dois públicos | A verba é pequena e não sustenta duas campanhas | 01/09/2026 |
| tráfego pago | O número a bater é US$ 72,08 por agendamento pago, não CPL | Foi o melhor mês (agosto/2026), depois de otimizar para agendamento | 01/09/2026 |
| tráfego pago | Na API, pedir o campo `conversions` e não só `actions` | As conversões personalizadas ficam ali. Ler só `actions` já gerou um diagnóstico errado | 01/09/2026 |
| LP e site | A LP só pode ser publicada sob `dsmuaythaisquad.com` | As conversões personalizadas filtram por esse domínio, e regra de conversão não se edita | 17/09/2026 |
| LP e site | `lps/publicado/` é gerada por `publicar-lp.py` e nunca se edita à mão | Apontar a Vercel para a pasta do cliente vazaria brief e histórico | 22/09/2026 |
| tracking | Os eventos `invitee_*` vêm da integração do próprio Calendly. O pixel da LP dá só `PageView` | Comprovado em 01 e 02/09 | 02/09/2026 |
| tracking | O teste de medição escolhe dia e horário, mas nunca paga | Pagar cobra US$ 29,99 e gera o evento que a campanha otimiza | 22/09/2026 |
| tracking | O hub conta agendamento pelo Calendly, não pelo pixel | A Meta só via as aulas pagas do site antigo | 23/10/2026 |
| social | Avaliações entram sem rótulo de objeção ao lado | Decisão do Guilherme | 09/2026 |

## Depende do cliente
Pendências com o David, conforme o plano do hub (13/10/2026) e o README do cliente:

- [ ] Conferir os stories dos destaques, incluindo a idade da turma de Teens (os stories dizem a partir de 9 anos)
- [ ] Conferir se o Calendly oferece só horários de iniciante. Quinta às 19h é só para competidores, e sexta é sparring
- [ ] Informar quantos agendamentos viraram matrícula, para saber se US$ 72 é bom
- [ ] Definir a política de devolução da taxa, junto com o Guilherme
- [ ] Mandar os resultados do Pro Team e o cartel do David
- [ ] Gravar depoimentos com alunos adultos
- [ ] Pedir aos alunos avaliações no Facebook, que hoje não tem nenhuma (o Google tem 113)
- [ ] Fechar o que falta do briefing: matrícula, adesão, contrato, aula avulsa e desconto de família

## Acessos
Nunca guarde senha aqui. O token da BM fica em `credenciais.local.md`, na raiz do `agencia_marketing`.

- **Meta:** conta de anúncios `800990442489726` (USD), business `562592887773309`, Página `102351215972726` (a `100085893254469` é perfil pessoal) e Pixel `25913656948303012`. A conta está liberada no MCP desde 13/10/2026, e antes era lida pela Marketing API
- **Conversões personalizadas:** Escolheu o dia (`962316889514579`), Escolheu o horário (`1720514239024454`) e Aula experimental paga (`1081697741136388`)
- **Google Ads:** `104-170-9245`, via Windsor.ai, que está bloqueado porque o plano gratuito estourou
- **Google Business:** `/g/11tfq328_m`, 5,0 com 113 avaliações (22/09/2026)
- **Vercel** (time hub3psmarketing): `dsmuaythai` (hub) e `dsmuaythai-lps` (trial e bio, a partir de `lps/publicado/`)
- **Instagram:** `@ds_muaythai_squad`

## Onde está cada coisa (repo `agencia_marketing`, pasta `clients/dsmuaythai/`)

| Preciso de | Está em |
|---|---|
| Briefing em 12 blocos | `brief.md` |
| Identidade visual | `brand.md` |
| Histórico da conta Meta até agosto | `campanhas/historico-meta-ate-2026-08.md` |
| LP: fonte e versão PT de aprovação | `lps/trial-lp/` |
| Página da bio | `lps/bio/` |
| Artes do Instagram e simulador do perfil | `comercial/instagram/` e `hub/simulador/` |
| Números do hub (campanhas e diário) | `ferramentas/montar-hub.py` |
| Runbooks | `docs/processos/publicar-lp-dsmuaythai.md` e `atualizar-hub-dsmuaythai.md` |

## Links
- Kanban: [[04-clientes/dsmuaythai/kanban|kanban]]
- Log: [[04-clientes/dsmuaythai/log|log]]
- Campanhas: `campanhas/`
- Fontes: `fontes/`
- Drive: TODO
- Painel: https://dsmuaythai.hub3ps.com
