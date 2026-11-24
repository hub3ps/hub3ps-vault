---
tipo: log
autor: claude
---
# Log

A entrada mais recente fica no topo, uma por sessão de trabalho.

### 2026-11-24 · Feriados bloqueados no Calendly
- **O que fiz:** com o OK do Guilherme, bloqueei pelo MCP do Calendly, no evento `Muay Thai Trial Classes – $29.99`, o Thanksgiving (26/11) e o recesso de 24/12 a 03/01, conforme o aviso do David de 24/11. Sexta e sábado já ficam fechados toda semana, então 27 e 28/11 não precisaram de bloqueio. Copiei as regras e os bloqueios antigos sem mudança.
- **O que achei:** conferido na API, não há horário em 26/11 nem de 24/12 a 03/01; 23/12 e 04/01 seguem abertos. Efeito colateral: o evento deixou de seguir a agenda "Working hours" e passou a ter agenda própria, com as mesmas regras. Mudança futura em "Working hours" não chega mais a ele; ajuste de horário passa a ser no evento.
- **Próximo passo:** o horário especial no Perfil da Empresa do Google é manual, por quem administra o perfil. Não temos acesso registrado.

### 2026-11-16 · IG-03 no ar na campanha de Tráfego
- **O que fiz:** conferi na API o conjunto e o anúncio que o Guilherme publicou pelo Gerenciador. Atualizei a ficha do Tráfego, a fila de Reels e o kanban.
- **Resultado em:** [[seguidores-frio-perfil-trafego]] e [[2026-11-11-reels-para-seguidores]]
- **O que achei:** conjunto `... | Visita ao perfil | IG-03` ativo, US$ 7/dia, visita ao perfil, MA, sem `Seguidores IG`. Anúncio `IG-03 | Reels | Holding pads parte 2` em análise, com o post certo (Dcgku5WBbIj) e botão de ver perfil. A campanha passou a US$ 14/dia. O conjunto novo saiu sem Advantage+ e com 18 a 55 fixos; o do IG-02 usa Advantage+.
- **Próximo passo:** conferir a aprovação do IG-03 em 17/11; o conjunto do IG-03 fica sem Advantage+, por decisão do Guilherme. Com o OK dele, renomeei o conjunto original para `... | Visita ao perfil | IG-02`, conferido na API.

### 2026-11-16 · Fim do teste de seguidores e IG-03 na fila do Tráfego
- **O que fiz:** conferi na API que o Guilherme pausou a campanha de Engajamento em 16/11 e li o resultado do teste. Preparei a subida do IG-03 (Holding pads parte 2) na campanha de Tráfego. O Guilherme decidiu que cada anúncio ganha conjunto próprio, duplicado do atual.
- **Resultado em:** [[seguidores-frio-perfil-engajamento]] e [[seguidores-frio-perfil-trafego]]
- **O que achei:** de 11 a 16/11, Engajamento a US$ 2,78 por seguidor (US$ 36,09, 13 seguidores) e Tráfego a US$ 0,90 (US$ 38,70, 43). O anúncio de visita ao perfil não se cria pela API nesta conta, então o IG-03 sobe pelo Gerenciador.
- **Próximo passo:** o Guilherme duplica o conjunto com o IG-03 no Gerenciador; eu confiro na API e marco a fila.

### 2026-11-16 · Revisão dos Reels dos últimos 3 meses para seguidores
- **O que fiz:** listei pelo MCP da Meta os posts do perfil de 16/08 a 16/11: 13 Reels. Propus 6 candidatos novos, além dos 5 da fila de 11/11 que caem na janela.
- **Resultado em:** [[2026-11-11-reels-para-seguidores]]
- **Decisão:** o Guilherme manteve a fila de 11/11 como está; os candidatos não entraram.
- **Próximo passo:** nenhum. Nada muda nas campanhas durante o teste, que vai até 25/11.

### 2026-11-12 · IG-02 do Engajamento aprovado e entregando
- **O que fiz:** conferi na API e no MCP, só leitura, as duas campanhas de seguidores. O `IG-02 | Reels | Holding pads` da campanha de Engajamento saiu da análise e está ativo. As duas campanhas e os dois conjuntos seguem ativos a US$ 7/dia.
- **Resultado em:** [[seguidores-frio-perfil-engajamento]]
- **O que achei:** parcial de 11 e 12/11, Engajamento com US$ 6,15 e 1 seguidor, Tráfego com US$ 8,43 e 6. Amostra pequena demais para ler. O campo de seguidores (`instagram_profile_follow_v2`) volta vazio pela Marketing API direta; só o MCP traz o número.
- **Próximo passo:** primeira leitura do teste em 14/11.

### 2026-11-11 · Teste de seguidores: Engajamento contra Tráfego
- **O que fiz:** abri a campanha `Seguidores | Frio | Perfil | Engajamento`, mesma verba (US$ 7/dia) e mesmo público frio de Massachusetts da de Tráfego, para comparar o custo por seguidor. A de Tráfego ganhou o quarto campo `| Tráfego`. Montei a fila de 7 Reels aprovada pelo Guilherme; nenhuma das duas gira criativo por ora. Conjunto e anúncio foram renomeados pelo MCP e conferidos na API.
- **Resultado em:** [[seguidores-frio-perfil-engajamento]], [[seguidores-frio-perfil-trafego]] e [[2026-11-11-reels-para-seguidores]]
- **O que achei:** a API não cria visita ao perfil nesta conta ("Ad account isn't eligible for Profile Visit ads"), mas o Gerenciador cria. Errei ao concluir que a conta não podia: o Guilherme montou conjunto e anúncio no Gerenciador, e a API só renomeia e lê. A primeira campanha que criei (`120260260783360386`) ficou arquivada; a que roda é a `120260262685740386`, recriada pelo Guilherme.

### 2026-11-11 · Campanhas renomeadas para o padrão novo de nomes
- **O que fiz:** renomeei as duas campanhas atuais no Ads Manager, pelo MCP da Meta, no [[03-processos/convencoes|padrão novo]] decidido pelo Guilherme hoje: `Agendamento | Quente | Aula experimental` e `Seguidores | Frio | Perfil`, com os conjuntos, os anúncios (`VID-01`, `IG-01`, `IG-02`) e os dois públicos do Instagram (`Engajou IG 365d`, `Seguidores IG`). A edição entrou direto, sem rascunho e sem pausar nada. Conferi na API: o IG-01 segue pausado, e o IG-02 e o VID-01 seguem ativos. As fichas ganharam os nomes novos de arquivo e a configuração de hoje.
- **Resultado em:** [[agendamento-quente-aula-experimental]] e [[seguidores-frio-perfil-trafego]]
- **O que achei:** o conjunto ativo do agendamento inclui, na API, quem engajou com o perfil em 365 dias e os seguidores, com local EUA. O Guilherme achava que era só de seguidores; ele decidiu manter a configuração e renomear o conjunto pelo que ela é, `Engajou IG 365d e seguidores | EUA | Escolheu o dia`, conferido na API. O hub troca o texto dos dois Reels impulsionados; a correção fica para o hub novo, por decisão do Guilherme. A ficha do agendamento dizia "pausada", mas a campanha voltou em 05/11.
- **Próximo passo:** corrigir o texto dos Reels no hub novo.

### 2026-11-04 · Migração do DS Muay Thai para o vault
- **O que fiz:** criei a nota do cliente, o kanban, este log e as fichas das duas campanhas recentes. As fontes foram a `origin/main` do `agencia_marketing` (nenhuma branch tem trabalho deste cliente fora dela), o plano do hub e a API da Meta. Conferi que as 4 páginas estão no ar. O repo ficou intocado.
- **Resultado em:** `04-clientes/dsmuaythai/`
- **O que achei:** a campanha de agendamento está pausada desde 27/10 (pausa do Gustavo, segundo o log de atividades), e só a de seguidores roda. A verba de seguidores está a US$ 7/dia, enquanto o plano diz US$ 9. O README do cliente no repo parou em 22/09. A pasta local "Reposicionamento IG" está fora do git.
- **Próximo passo:** o Guilherme decide a campanha de agendamento.

## Histórico anterior ao vault
Resumo do plano do hub, do README e dos commits no `agencia_marketing`.

- **30/10/2026:** e-mail da LP passa a ser o da recepção. A bio do Instagram deixa de citar o perfil pessoal do David.
- **27/10/2026:** campanha de agendamento pausada pelo Gustavo, às 15h58.
- **23/10/2026:** a página passa a enviar a aula paga ao pixel. O hub passa a contar agendamentos direto do Calendly, que registrou 9 aulas pagas desde 29/09.
- **21/10/2026:** grade de terça e quinta corrigida na LP e no destaque Adults, a partir de um áudio do David de 19/10.
- **13/10/2026:** campanha de seguidores no ar e hub publicado em `dsmuaythai.hub3ps.com`. A conta foi liberada no MCP da Meta.
- **09/10/2026:** página da bio no ar em `bio.dsmuaythaisquad.com`.
- **07/10/2026:** reposicionamento do Instagram: bio nova, destaques reduzidos de 11 para 3, fixados em vídeo e stories com a grade, tudo num simulador do perfil.
- **29/09/2026:** campanha de agendamento nova, otimizando para "Escolheu o dia". O público aberto parou em 02/10, e desde então a campanha fala com quem engajou no Instagram.
- **22/09/2026:** LP de trial aprovada. Ela foi ao ar em `trial.dsmuaythaisquad.com` antes da campanha de 29/09 (TODO: a data exata).
- **17/09/2026:** três conversões personalizadas do Calendly criadas.
- **16/09/2026:** primeira rodada de respostas do David: alunos, anos de academia, remarcação e grade.
- **01/09/2026:** diagnóstico: 43% dos cliques chegam ao Calendly, mas só 0,4% agendam. Daí a decisão de uma LP dedicada ao trial.
- **Agosto/2026:** a campanha passa a otimizar para agendamento e fecha 5 agendamentos, a US$ 72,08 cada.
- **Março/2026:** os anúncios passam a levar para o Calendly. Antes, iam para o Messenger.
- **26/08/2025:** início da parceria e primeiros anúncios.
