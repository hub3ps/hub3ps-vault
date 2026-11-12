---
tipo: log
autor: claude
---
# Log

A entrada mais recente fica no topo, uma por sessão de trabalho.

### 2026-11-12 · Site novo: preparação da troca
- **Decisões (Guilherme, 12/11):** a troca é hoje, e o impacto nos testes em andamento (`Lead`, `m15` e vídeos) será analisado depois, já com o site novo. Os domínios ficam no projeto `juria-lps` da Vercel, que passa a publicar o site novo. A branch vai para a `main`. A Mobiletec não precisa revisar mais nada.
- **O que fiz:** enviei para aprovação o favicon de 20/10 ("IA" ciano sobre navy). No rodapé, "Recursos", "Inteligência (IA)", "Planos" e "Central de ajuda" eram âncoras que só funcionavam na home. Corrigi para `/#recursos`, `/#inteligencia`, `/precos` e `/#faq` (sem commit). "Central de ajuda" não é uma central: leva ao FAQ da home.
- **O que achei:** na prévia o GTM carrega e o consentimento segue a mesma regra do site no ar, mas Pixel e GA4 não disparam. O próprio container só libera as tags em `juria.app.br`, `www.`, `portal.`, `trabalhista.` e `previdenciario.`. É esperado, e a conferência real fica para logo depois da troca, no `www`. Neste navegador havia uma recusa de cookies no site atual, de 06/11. O projeto `juria-lps` publica estático do repo `juria-lps`, com `www`, apex (308 para o `www`), `trabalhista.` e `previdenciario.`. O merge da `feat/site-astro` na `main` tem 12 conflitos, e a `main` local tem 4 commits sem push.

### 2026-11-12 · Site novo: páginas do rodapé no desenho novo
- **O que fiz:** refiz `/termos`, `/privacidade` e `/cookies` no desenho do site novo: cápsula navy no topo, sumário fixo ao lado e o texto num cartão. Nos termos, corrigi só o que é produto: a seção 3 passou a listar Solo, Plus, Max e Sob consulta, com os preços de hoje e "todas as funcionalidades" só do Plus em diante, e a seção 4 passou a falar em teste de 7 dias.
- **Resultado em:** commit dc74164 na `feat/site-astro` do `agencia_marketing`, com push. Conferido no ar na prévia: as três páginas no desenho novo e com noindex, e no celular (375 px) sem rolagem lateral. O texto foi comparado palavra por palavra com o que está no ar: privacidade e cookies sem nenhuma mudança, e os termos só nas seções 3 e 4. Conferências e build passando, com capturas de tela conferidas no desktop.
- **Decisões:** corrigir nas páginas do rodapé só o que é produto, sem mexer em nada jurídico, e deixar o `/oab` para depois (Guilherme, 12/11).
- **O que achei:** a data e a versão dos termos ("Versão 1.0 · 02 de junho de 2026") não mudaram, porque são da versão jurídica. Atualizar fica com a Mobiletec. A privacidade fala de BYOK e de Google Calendar sem citar plano. É texto de tratamento de dados e ficou como está.
- **Próximo passo:** o favicon, a data da troca depois de 25/11, conferir GTM e Pixel na prévia, mover os domínios na Vercel e trazer a branch para a `main`.

### 2026-11-12 · Site novo: ajustes técnicos para o domínio principal
- **O que fiz:** na `feat/site-astro`, copiei `/privacidade`, `/termos`, `/cookies` e `/oab` do `juria-lps`, sem mudar uma letra. O noindex passou a valer em todo endereço que não seja `www.juria.app.br`, e sempre em `/oab`, como hoje. `/institucional`, `/geral`, `/trabalhista` e `/previdenciario` redirecionam para a home. `/v2` redireciona só no `www`. O "Contato" do rodapé leva a `/sobre#contato`. O `/blog`, sem post, ganhou noindex e saiu do sitemap. O sitemap ficou sem a barra no fim.
- **Resultado em:** commit cc6e64f na `feat/site-astro` do `agencia_marketing`, com push. Conferido na prévia: as quatro páginas respondem 200, tudo sai com noindex, as quatro rotas antigas redirecionam com 308 para a home levando a UTM, o sitemap está sem barra e o "Contato" aponta para `/sobre#contato`. Só dá para conferir o `www` sem noindex e a `/v2` redirecionando depois da troca. A conferência no navegador (Playwright) não rodou.
- **O que achei:** os termos de uso no ar ainda falam em Basic R$ 199, Pro R$ 499 e teste de 14 dias, e o `/oab` promete "todos os módulos liberados, em todos os planos". Copiei como está, porque texto jurídico é da Mobiletec. Precisa ir para ela antes da troca.
- **Próximo passo:** a Mobiletec atualizar os termos e o `/oab`; favicon; data da troca depois dos testes; conferir GTM e Pixel na prévia; mover os domínios na Vercel; trazer a branch para a `main`.

### 2026-11-12 · Site novo: o que falta para ir ao domínio principal
- **O que fiz:** comparei as rotas do site no ar (`juria-lps`, só leitura) com as páginas do site novo e conferi o build e a prévia.
- **O que achei:** bloqueiam a troca: (1) somem rotas que existem hoje: `/privacidade`, `/termos` e `/cookies`, para onde o rodapé novo aponta, `/oab`, que é o QR do flyer impresso, `/geral` e `/institucional`; e `trabalhista.` e `previdenciario.` dependem do projeto `juria-lps`; (2) o `vercel.json` do site novo manda noindex em todas as páginas; (3) os anúncios levam a `www.juria.app.br`, então trocar antes de 25/11 muda a página no meio dos testes `Lead` (13/11), `m15` (23/11) e vídeos (25/11); (4) GTM, Pixel e GA4 nunca foram conferidos carregando de verdade no site novo. Também faltam: o favicon, o "Contato" do rodapé, que aponta para `#`, a `/v2` pública, o `/blog` vazio e no sitemap, o sitemap com barra final que redireciona (308), mover os domínios na Vercel e trazer a branch para a `main`. O QR do folder leva à home, então segue valendo.
- **Próximo passo:** o Guilherme decide a data da troca e o que fazer com as rotas antigas.

### 2026-11-12 · Site novo: WhatsApp e telefone novos
- **O que fiz:** troquei o (47) 93386-3850, da revisão da Mobiletec de 21/10, pelo (47) 98817-5142 no WhatsApp e no telefone de contato do site novo.
- **Resultado em:** commit 54550fe na `feat/site-astro` do `agencia_marketing`, com push. Conferido no ar em `site.juria.hub3ps.com` (home, `/sobre` e `/precos`): só o número novo aparece.
- **Decisões:** número novo no WhatsApp e no telefone de contato (Guilherme, 12/11).
- **O que achei:** o número antigo segue em `clients/juria/revisao-mobiletec-2110.md`, que é registro da revisão e não muda. Não conferi se o site em produção (`juria-lps`) e outras peças usam o número antigo: o repo é outro e ficou intocado.

### 2026-11-12 · Site novo: últimos ajustes da Isadora
- **O que fiz:** apliquei os três pedidos da Isadora na `feat/site-astro`. O título do financeiro na home foi para o plural, "Dos honorários à nota fiscal, tudo no mesmo sistema.". O "Preços" do rodapé virou "Planos", igual ao menu. No FAQ "O que é o DJEN?", da `/gestao-de-processos-e-prazos`, saiu "como intimações e editais".
- **Resultado em:** commit be15b1f na `feat/site-astro` do `agencia_marketing`, com push a pedido do Guilherme. Conferido no ar em `site.juria.hub3ps.com`: os três ajustes aparecem, e a prévia segue com noindex. Conferências, build e as 22 conferências de página passando.
- **Próximo passo:** publicar em produção. Antes, o favicon, o domínio e a data da troca, e trazer a branch para a `main`.

### 2026-11-12 · Site novo: logos dos clientes liberadas
- **O que fiz:** registrei a liberação e conferi o estado da `feat/site-astro` para os últimos ajustes antes de publicar.
- **Decisões:** a Mobiletec aprovou o uso das logos dos clientes no site, o que travava a publicação (Guilherme, 12/11).
- **O que achei:** a `feat/site-astro` local está igual à `origin` (último commit d4817c1, 30/10) e 113 commits à frente da `main`. As 13 logos já estão no site desde 06/10: na home, em "Empresas que rodam sistemas da Mobiletec", e na `/sobre`. Nada a incluir. A prévia `site.juria.hub3ps.com` sai com `x-robots-tag: noindex` pela Vercel. Ainda pendentes: o favicon (sem arquivo aprovado desde 20/10), o domínio e a data da troca, os 5 itens do checklist que pediam preview (GTM e Pixel carregando, Rich Results e celular de verdade), e trazer a branch para a `main`. Não há runbook de publicação do site novo em `docs/processos/`.
- **Próximo passo:** aplicar os ajustes da Isadora, que o Guilherme vai mandar.

### 2026-11-12 · Folder institucional, arquivo da gráfica
- **O que fiz:** apliquei os dois pedidos da Isadora na opção B. No B2, o primeiro item da lista virou "Envia agenda do dia, prazos e intimações". No B1, o QR saiu e no lugar dele entrou "Conveniado com a" com a logo da CAASC, ao lado do "Comece agora seu teste grátis", que ficou. A logo foi vetorizada da versão de fundo transparente que ela mandou. Gerei o arquivo da gráfica e o Guilherme aprovou.
- **Resultado em:** `clients/juria/creatives/folder-institucional/folder-juria-b-grafica-PDFX1a.pdf` do `agencia_marketing` (sem commit). PDF/X-1a:2001, CMYK FOGRA39, 600 DPI, 2 páginas de 306x216 mm com sangria e corte de 300x210 mm. Gera de novo com `python3 ferramentas/grafica.py folder-b.html`. A gráfica pediu as marcas de vinco, e elas entraram tracejadas na margem de 10 mm fora da sangria, nas duas dobras (100 e 200 mm do corte), em cima e embaixo.
- **O que achei:** o site novo não fala do convênio com a CAASC, então "Conveniado com a" é texto do Guilherme, liberado no conferidor. O QR agora só está no B3, o verso da capa, e foi lido no PDF final. O perfil FOGRA39 saiu do PDF do flyer da OAB, para manter a mesma especificação. Os outros itens da lista da Jú não mudaram: "Alerta de prazos" soa como substantivo ao lado dos verbos, mas a Isadora só pediu o primeiro.
- **Decisões:** CAASC no lugar do QR do B1, com o texto "Conveniado com a" (Guilherme, 12/11). Folder aprovado para a gráfica (Guilherme, 12/11).
- **Próximo passo:** mandar à gráfica, confirmar que ela faz sanfona no papel escolhido e testar o QR na prova impressa. Entrega até 15/11.

### 2026-11-11 · Reels da Jú publicado no Instagram
- **O que fiz:** conferi o perfil @juria.app, que tinha só o IG-CAR-01 e o IG-IMG-01, e preparei o IG-VID-01 v7 (a Jú no WhatsApp) com a legenda aprovada em 19/10. Antes, conferi no site novo os fatos da legenda: Jú em todos os planos a partir do Solo, 7 dias grátis sem cartão e só o número vinculado com acesso. O Guilherme publicou como Reels.
- **Resultado em:** https://www.instagram.com/juria.app/reel/DfmvXquJQD6/ (o perfil passou a 3 posts)
- **O que achei:** o caminho de ativação da legenda, "Configurações > Integrações > Seu WhatsApp com a Jú", só existe dentro do sistema e não foi conferido. Pelo MCP da Meta, a consulta de contas do Instagram ligadas à conta de anúncios voltou vazia: ou o perfil não está ligado a ela, ou falta a permissão de leitura. Por isso a lista de posts foi conferida no perfil público.
- **Próximo passo:** publicar o IG-CAR-02 (NFS-e), o último aprovado na fila.

### 2026-11-10 · Folder institucional, opção B com a revisão da Isadora
- **O que fiz:** apliquei na opção B, a escolhida pela Mobiletec, os ajustes da Isadora. No A3, o texto pequeno ao lado de "sistema." virou o dela. No B1, entrou no topo "Menos planilha, mais advocacia." com o texto dela, e a Mobiletec desceu, com o texto novo e o 1999 menor. No B2, o rótulo virou "A Jú, assistente do seu escritório no WhatsApp, sempre disponível", e as duas perguntas viraram balões de mensagem enviada, com o visto duplo. Regerei prévias, PDF de aprovação e mockup.
- **Resultado em:** `clients/juria/creatives/folder-institucional/folder-juria-b-aprovacao.pdf` do `agencia_marketing` (commit 44353ba). Revisão original em [[2026-11-10-revisao-isadora-folder]]
- **O que achei:** cinco trechos da Isadora não estão no site novo, entre eles "notas fiscais", "checklists" e "Menos planilha, mais advocacia". Entraram como texto da própria Mobiletec, liberados no conferidor com o motivo. O A3 manteve o título "IA jurídica inclusa em todos os planos."; ela só trocou o texto de baixo. "Use a jurimetria" aparece sem o "A partir do Plus", que segue no B3.
- **Próximo passo:** mandar o PDF para a aprovação da Mobiletec. Depois, gráfica, CMYK e prova do QR. Entrega até 15/11.

### 2026-11-09 · Informativos de segurança no ar no cadastro
- **O que fiz:** registrei a 1ª frente da reunião de 06/11, publicada hoje pelo Saulo, e conferi no ar a tela de criar conta e a janela "Como cuidamos dos seus dados". Entrou no registro do hub como teste `m15`, na etapa Cadastro, a avaliar em 23/11.
- **Resultado em:** [[2026-11-09-whatsapp-saulo-seguranca]] (o que mudou, tela por tela, com os prints) e `juria.hub3ps.com` (commit d2cce38 do `agencia_marketing`)
- **O que achei:** são três pontos: o bloco "Seus dados, protegidos" na criação da conta, três itens na tela da OAB mais a linha "Consulta direta ao CNJ (DataJud)", e uma janela com oito garantias. O Saulo chama de primeira versão, discreta, e aceita opiniões. A tela da OAB vem depois de criar a conta, então ela foi conferida só pelos prints.
- **Próximo passo:** comparar em 23/11 a importação e a passagem da tela da OAB antes e depois de 09/11. Mandar ao Saulo as nossas opiniões sobre o texto, se houver.

### 2026-11-09 · Decisões da reunião de 06/11
- **O que fiz:** registrei a reunião com a Mobiletec e as três frentes combinadas, com o objetivo de aumentar os escritórios que importam processos e a qualidade dos leads.
- **Resultado em:** [[2026-11-06-mobiletec]]
- **Decisões (reunião de 06/11, Guilherme e Mobiletec):** mais informativos de segurança em páginas do onboarding e do cadastro; site novo em produção; uma pessoa para gravar conteúdo do Instagram e criativos dos anúncios, para humanizar a marca.
- **Próximo passo:** definir prazos e responsáveis das três frentes, que não foram registrados.

### 2026-11-06 · Hub revisado para a reunião e marcos do projeto
- **O que fiz:** conferi os números e as propostas do hub com as exportações de 04/11 e publiquei duas correções: a conversa com quem importou fala em 20 escritórios, e não 18, e a importação automática depende das propostas 1 e 3. Consolidei os marcos do projeto no `cliente.md`.
- **Resultado em:** `juria.hub3ps.com` (commit 93ebe35) e a seção "Marcos do projeto" do [[04-clientes/juria/cliente|cliente]]
- **O que achei:** os números do topo e das campanhas batem. "Metade desiste na tela do escritório" usa o registro desde 06/10, e o funil do hub soma desde 14/08, por isso as perdas diferem; a explicação está na proposta. As 254 publicações lidas não estão em nenhuma exportação que temos. Envio do briefing, kickoff e renovação do contrato não estão registrados.
- **Proposta nova (06/11):** "Vincular a Jú no cadastro", prioridade 2. A Jú, vinculada na tela dos prazos, manda prazos, intimações e o resumo do dia durante o teste, e o WhatsApp fica com a equipe comercial. Antes, conferi o cadastro ao vivo: segue igual ao mapeado, com 7 passos e o telefone só como opcional na tela da OAB. Publicado no commit 6695a8e.
- **Próximo passo:** reunião com a Mobiletec às 15h. Preencher os marcos que faltam.

### 2026-11-05 · Folder institucional, copy só do site novo
- **O que fiz:** troquei todo texto das duas opções pelo do site novo, `site.juria.hub3ps.com`, palavra por palavra, e criei `ferramentas/conferir-copy.py`, que aponta trecho fora do site. Corrigi o ano da Mobiletec para 1999 e o logo da Vibra para o da Vibra Foods. Refiz os mockups.
- **O que achei:** a cópia local da branch `feat/site-astro` estava 50 commits atrás, e era dela que vinham o "2000" e a frase do STF. Os dois anúncios no ar da `juria-leads-9estados-1310` dizem "Mobiletec, desde 2000" na descrição, e a arte do INST-B-02 diz "software house desde 2000". Não mexi: depende do OK do Guilherme.

### 2026-11-05 · Folder institucional, sem preço e com mockups
- **O que fiz:** tirei os planos e valores das duas opções, a pedido do Guilherme: o folder informa e leva ao QR, e o preço fica no site. Na A entrou "Já vem com o JurIA" no lugar dos planos. Na B, a resposta da Jú desceu e o verso da capa ganhou QR. Gerei um mockup de cada opção para mandar à Ana.
- **Resultado em:** `clients/juria/creatives/folder-institucional/mockup-opcao-a.jpg` e `mockup-opcao-b.jpg` (commit 30a9326; correção do ano em 386f16b)

### 2026-11-05 · Folder institucional, opção B
- **O que fiz:** a v2 foi commitada como opção A, editorial. Montei uma opção B, audaciosa, para a Ana escolher: dobra em sanfona, um lado inteiro em ciano com "Tudo num só sistema." em letras gigantes, uma palavra por painel. Na 2ª rodada, depois das recusas do Guilherme (selo branco da logo, lado B parecido com a A, "Jú" gigante), o lado A virou navy com a frase em ciano e a logo branca sem selo, e o lado B virou três blocos de cor: branco com o ano 2000, ciano com as perguntas à Jú, navy com a IA e o trial.
- **Resultado em:** `clients/juria/creatives/folder-institucional/folder-b.html` (opção A no commit 92a39e4, opção B no 3754f9e)
- **O que achei:** a B pede sanfona, com 3 painéis de 100 mm, e não carteira. Precisa confirmar com a gráfica. O lado A não pode ser ciano: o "IA" da logo é ciano e sumiria no fundo, e logo não se recolore.

### 2026-11-05 · Folder institucional, v2
- **O que fiz:** refiz o folder em linha editorial depois que o Guilherme achou a v1 poluída e com cara de IA. Tem mais branco, tipografia grande e uma faixa navy cruzando os painéis. A IA caiu de 7 pontos para 4. Na 2ª rodada, a capa ficou só tipográfica, sem foto, e a Jú virou citação com avatar pequeno.
- **Resultado em:** `clients/juria/creatives/folder-institucional/` (a v1 está em `_v1/`)

### 2026-11-05 · Folder institucional, 1ª versão
- **O que fiz:** primeira versão do folder pedido pela Ana, para aprovação. Tríptico de 2 dobras, 10x21 cm fechado e 30x21 cm aberto. A copy é toda do site novo. Seis painéis: capa, antes e depois, Mobiletec com logos e QR, inteligência, Jú no WhatsApp, e mapa do sistema com planos.
- **Resultado em:** `agencia_marketing/clients/juria/creatives/folder-institucional/` (ainda sem commit)
- **O que achei:** não havia registro do pedido nem do prazo de 15/11. O flyer da OAB promete "todos os módulos em todos os planos", o que deixou de ser verdade em 29/09. O folder não repete isso e marca "Do Plus em diante" onde o site marca.

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
