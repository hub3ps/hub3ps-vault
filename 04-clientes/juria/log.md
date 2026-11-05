---
tipo: log
autor: claude
---
# Log

A entrada mais recente fica no topo, uma por sessão de trabalho.

### 2026-11-05 · Rótulo do evento Lead corrigido
- **O que fiz:** o hub, os geradores, as fichas e o `CLAUDE.md` chamavam o `Lead` de "cadastro concluído". Troquei para "conta criada" em tudo. "Cadastro concluído" ficou só para o último passo do funil (ligar as intimações).
- **Resultado em:** `juria.hub3ps.com` e `agencia_marketing`
- **O que achei:** o `Lead` dispara no `form_submit_trial`, quando a conta é criada, antes do onboarding. A `9estados-2810` otimiza pelo `CompleteRegistration`, que é o fim do onboarding. Correção apontada pelo Guilherme.

### 2026-11-05 · Hub e funil com as exportações de 04/11
- **O que fiz:** atualizei os números da Meta e do painel da Mobiletec até 04/11 no `gerar-funil.py`, reescrevi as conclusões e os resultados dos testes m12, m13 e m14 no `hub/mudancas.json`, e incluí o período dos e-mails pessoais da Isadora (desde 28/10). Publicado no commit `f7cbb69` do `agencia_marketing`.
- **Resultado em:** `juria.hub3ps.com` (conferido no ar em 05/11)
- **O que achei:** de 14/08 a 04/11, R$ 5.111 investidos, 104 escritórios criados e 20 importaram (19%), a R$ 365 por escritório que importou. Uso baixo depois do cadastro: 254 publicações lidas de 22.814. Os dois escritórios no plano `pro` não têm origem comprovada em campanha. Os erros do cadastro e as intimações revisadas seguem com o retrato de 20/10, porque a exportação nova não traz esses dados. As exportações ficaram em `~/Documents/juria-exportacoes/2026-11-04/`, fora do git.

### 2026-11-04 · Migração do JurIA para o vault
- **O que fiz:** criei a nota do cliente, o kanban, este log, as fichas das duas campanhas no ar e a reunião de 17/09. As fontes foram a `origin/main` e as branches do `agencia_marketing`, o `juria-lps`, a nota de contexto da reestruturação e a API da Meta. O `agencia_marketing` ficou intocado.
- **Resultado em:** `04-clientes/juria/`
- **O que achei:** na API (04/11), o conjunto de vídeos com música está pausado e só o da locução roda. A verba da campanha Lead está a R$ 42/dia. A `main` local do `agencia_marketing` está 127 commits atrás da `origin/main`.
- **Decisões:** JurIA e Mobiletec viram dois clientes, com uma pasta cada (Guilherme). A campanha de vídeos fica como está, e o Guilherme decide o teste e o evento direto no Ads Manager (Guilherme). O conhecimento fica no repo por enquanto, e a nota aponta onde está cada coisa.
- **Próximo passo:** o Guilherme revisa a estrutura e decide o teste de vídeos.

## Histórico anterior ao vault
Resumo tirado dos commits, das fichas e do registro do hub no `agencia_marketing`. Os detalhes estão lá.

- **30/10/2026:** hub novo no ar na raiz de `juria.hub3ps.com`, com Planejamento, Funil, Otimizações e Materiais.
- **05/11/2026:** hub atualizado com as exportações de 04/11: 104 escritórios criados, 20 importaram (19%), nenhuma assinatura confirmada.
- **29/10/2026:** leitura do funil de 14/08 a 29/10. Dos 93 escritórios criados, 18 importaram processos (19%), e não houve nenhuma assinatura. Entraram 10 propostas no registro.
- **28/10/2026:** campanha de vídeos publicada (`juria-leads-9estados-2810`): INST-VID-02 com música e INST-VID-03 com locução, um em cada conjunto.
- **26/10/2026:** revisão da Isadora aplicada nos posts do Instagram, no IG-VID-01 v7 e no INST-B-01.
- **22 e 23/10/2026:** site novo em Astro revisado pela Mobiletec, página a página, na branch `feat/site-astro`.
- **14/10/2026:** documento de funcionalidades da Mobiletec incorporado. O site novo foi publicado em `site.juria.hub3ps.com`, com `noindex`.
- **13/10/2026:** campanha Lead (`juria-leads-9estados-1310`) publicada em paralelo à View_Register, para testar o evento de otimização.
- **01/10/2026:** campanha View_Register (`juria-leads-9estados-3009`) no ar. Avaliada depois: não funcionou.
- **30/09/2026:** todas as campanhas antigas desligadas, porque anunciavam preço, plano e prazo de antes de 29/09.
- **29/09/2026:** planos reestruturados (Solo R$ 69, Plus R$ 159) e trial reduzido de 14 para 7 dias. A execução do site em Astro começou.
- **17/09/2026:** reunião com a Mobiletec sobre o ciclo de 27/08 a 15/09. Ver [[2026-09-17-mobiletec]].
- **14/09/2026:** campanha institucional reiniciada em 9 estados, só no Facebook e no Instagram.
- **31/08/2026:** campanha institucional Brasil no ar, com o primeiro vídeo da conta.
- **14/08/2026:** primeiras campanhas no ar, de nicho no Sul (trabalhista e previdenciário).
- **12/08/2026:** LP da oferta da OAB Brusque (`juria.app.br/oab`), com flyer e banner.
- **22/04/2026:** contrato assinado.
