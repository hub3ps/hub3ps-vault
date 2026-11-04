---
tipo: cliente
slug: juria
nome: JurIA
empresa: Mobiletec Sistemas Ltda
status: ativo
servicos: [trafego-pago, tracking, lp-e-site, criativos-e-audiovisual, social, email-marketing]
inicio: 2026-04-22
contatos: Saulo (time técnico da Mobiletec), Isadora (comercial e revisão de conteúdo, TODO confirmar papel)
drive: TODO (Hub3Ps/Clientes/juria/)
painel: https://juria.hub3ps.com
repositorios: [hub3ps/agencia_marketing, hub3ps/juria-lps]
proxima-reuniao: TODO
atualizado: 2026-11-04
autor: claude
---
# JurIA

> **Estado atual:** duas campanhas Meta no ar (API, 04/11/2026): a de Lead, a R$ 42/dia, avaliada em 13/11, e a de vídeos, em que só o conjunto da locução roda porque o da música está pausado. O gargalo é a ativação: só 19% dos escritórios importam processos e não houve nenhuma assinatura até 29/10. O site novo em Astro foi revisado pela Mobiletec em 23/10 e continua fora da main, sem data de troca.

Mesma empresa do cliente [[04-clientes/mobiletec/cliente|Mobiletec]], que tem pasta própria. Decisão do Guilherme em 04/11/2026.

## Quem é
- **Negócio:** a Mobiletec é uma software house de Itajaí/SC fundada em 1999. O JurIA é um produto dela: uma plataforma jurídica com IA (gestão de processos, prazos, financeiro, NFS-e, jurimetria) e com a Jú, uma secretária no WhatsApp.
- **Público:** sócios e gestores de escritórios com 2 a 15 advogados. O trial atrai também advogados solo.
- **Região:** os anúncios rodam em 9 estados: BA, DF, GO, MG, PR, RJ, RS, SC e SP (API, 04/11/2026).
- **Idioma:** português do Brasil.
- **Oferta:** trial de 7 dias sem cartão. Planos Solo R$ 69, Plus R$ 159, Max R$ 499 e Ilimitado sob consulta (desde 29/09/2026, com o Ilimitado alterado em 15/10). A fonte da verdade é `clients/juria/comercial/planos-e-creditos.md` no repo, nunca a LP.

## Escopo
Contrato assinado em 22/04/2026, com período de avaliação até 22/07/2026 (briefing consolidado, 15/05/2026). TODO: confirmar a vigência atual.

- [[trafego-pago]]: só Meta Ads. A campanha de Search do Google aparece no plano do mês 1, mas a situação atual dela está como TODO
- [[tracking]]: GTM, Pixel, CAPI, GA4, consentimento e o painel do funil
- [[lp-e-site]]: as LPs públicas em `juria.app.br` e o site novo em Astro
- [[criativos-e-audiovisual]]: anúncios estáticos, vídeos em Remotion, a influencer virtual Helena e os impressos do evento da OAB
- [[social]]: posts orgânicos do Instagram `@juria.app`
- [[email-marketing]]: a sequência do trial de 7 dias, enviada pela Isadora

**Metas combinadas com a Mobiletec** (briefing, 11/05/2026): CAC máximo de R$ 500 no plano de entrada e 75 a 90 trials por trimestre. Já o CPL de R$ 100 é projeção nossa, não foi acordado.

## Exceções ao padrão

| Serviço | Exceção | Motivo | Desde |
|---|---|---|---|
| tráfego pago | A métrica principal é o escritório que importou processos (R$ 378 por escritório na Meta), não o CPL | Um trial que não usa o sistema não vira assinatura | 30/10/2026 |
| tráfego pago | Concorrentes (Astrea, ADVBOX, Projuris, Tikal Tech) nunca aparecem em anúncio | Regra do briefing | 15/05/2026 |
| tráfego pago | Copy fala da rotina do escritório, não do software | Correção do Guilherme | 14/09/2026 |
| tráfego pago | Uma mudança por etapa do funil, sempre com hipótese, métrica e data de avaliação, registrada no hub | Antes, várias mudanças na mesma semana impediam ler o efeito de cada uma | 29/10/2026 |
| tráfego pago | Relatório e leitura do gestor escritos para leigo | Quem lê é a Mobiletec, não um gestor de tráfego | 14/09/2026 |
| LP e site | Dois repositórios: as LPs públicas vêm do `juria-lps`, e o push no `agencia_marketing` publica só o hub | Arquitetura herdada | 08/2026 |
| LP e site | O Solo não tem todas as funções. "Todas as funcionalidades" só vale do Plus em diante | A LP já errou isso em cinco lugares | 29/09/2026 |
| criativos | Vídeo é feito em Remotion, nunca com IA de vídeo | Texto exato e nenhum custo por render | 31/08/2026 |
| tracking | O `ClickTrial` saiu, e a intenção é medida pelo `ViewRegister` | O redirecionamento cortava o evento antes de chegar à Meta | 23/09/2026 |
| tracking | O Consent Mode vai no `<head>`, antes do GTM | Na ordem invertida, as tags disparavam para quem recusou | 08/2026 |

## Depende do cliente
Pedidos abertos com a Mobiletec, conforme o registro do hub (`clients/juria/hub/mudancas.json`, de 29 e 30/10/2026):

- [ ] Exportar, por cadastro, a OAB, a seccional, o nome informado e se a busca encontrou o advogado
- [ ] Separar por motivo o erro na tela de dados do escritório
- [ ] Informar se existe um endereço que abre direto a importação pela OAB e se esse e-mail pode sair pelo mesmo envio das réguas
- [ ] Informar o que acontece quando a importação passa de 50 processos no teste
- [ ] Implementar o `trial_to_paid` no servidor (README do cliente, sem data)
- [ ] Responder Q8, Q9, Q27 e Q28 do briefing: beta testers, lista de espera, quem ativa os trials e o destino final do lead (abertas desde 15/05/2026)

## Acessos
Nunca guarde senha aqui. O token fica em `credenciais.local.md`, na raiz do `agencia_marketing`, fora do git.

- **Meta:** conta de anúncios `1465935581974017` e Pixel `1009120801605718`. O MCP oficial da Meta está liberado
- **Google Ads:** lido pelo Windsor.ai
- **GTM:** `GTM-WHQGLTXC`
- **Domínios:** `juria.app.br` (LPs), `portal.juria.app.br` (o app, com cadastro e login), `juria.hub3ps.com` (hub), `funil.juria.hub3ps.com` (painel do funil), `site.juria.hub3ps.com` (prévia do site novo)
- **Vercel** (time hub3psmarketing): `juria` (hub), `juria-lps` (produção) e `site-novo-juria` (site novo, publicado da branch `feat/site-astro`)

## Onde está cada coisa (repo `agencia_marketing`, pasta `clients/juria/`)
Por enquanto o conhecimento fica no repo. A migração para o vault é o próximo passo, registrado no [[kanban]].

| Preciso de | Está em |
|---|---|
| Arquitetura, deploy e CTAs | `README.md` |
| Briefing, persona, dores e objeções | `brief.md` (o original `.docx` está em `source/`) |
| Preço, plano e funções | `comercial/planos-e-creditos.md` e `comercial/funcionalidades.md` |
| Registro de otimizações e propostas | `hub/mudancas.json` (aparece no hub) |
| Definições do funil | `funil/definicoes.md` |
| Fichas de campanha | `campanhas/`. As ativas também estão em `campanhas/` aqui no vault |
| Copy dos anúncios | `copies/<campanha>/` |
| Site novo em Astro | branch `feat/site-astro`, arquivo `clients/juria/ESTADO-site-astro.md` |
| Runbooks | `docs/processos/atualizar-hub-juria.md` e `publicar-lp-juria.md` |

## Links
- Kanban: [[04-clientes/juria/kanban|kanban]]
- Log: [[04-clientes/juria/log|log]]
- Reuniões: `reunioes/`
- Campanhas: `campanhas/`
- Fontes: `fontes/`
- Drive: TODO
- Painel: https://juria.hub3ps.com
