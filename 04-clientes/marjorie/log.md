---
tipo: log
autor: claude
---
# Log

A entrada mais recente fica no topo, uma por sessão de trabalho.

### 2026-11-12 · Resumo da rodada 2 enviado ao grupo
- **O que fiz:** com o ok do Guilherme, enviei no grupo "CURSO EXOCAD 🚀🇧🇷", pelo número da agência no whatsapp-mcp, o resumo da rodada 2 no mesmo formato do de 09/11: IG-06 continua (US$ 0,69 por seguidor), IG-07 pausado (US$ 1,38), com os links, e o IG-12 já no ar para teste.
- **Próximo passo:** leitura da rodada 3 em 15/11.

### 2026-11-12 · Rodada 2 de seguidores e IG-12 no ar
- **O que fiz:** li na API o custo por seguidor de 09 a 12/11 em [[seguidores-frio-perfil]]. Com o ok do Guilherme, pausei pelo MCP o conjunto do IG-07. O conjunto do IG-12 o Guilherme duplicou do IG-07 à mão, e conferi na API: mesma otimização, público, exclusão, posicionamentos e US$ 5 por dia, com o anúncio apontando para o post DH1sAqTTxyY. O anúncio passou pela análise da Meta e já entrega no mesmo dia.
- **O que achei:** IG-06 com US$ 13,70 e 20 seguidores (US$ 0,69 cada), IG-07 com US$ 11,06 e 8 (US$ 1,38). O IG-07 teve a visita mais barata, US$ 0,10 contra US$ 0,25, e de novo a visita barata não virou seguidor. O MCP recusou criar o conjunto com `PROFILE_AND_PAGE_ENGAGEMENT` nesta conta, e o token da BM Hub3Ps não alcança a conta da Marjorie.
- **Decisões:** o IG-06 fica, o IG-07 sai e entra o IG-12, o 4º da lista da Julia (Guilherme). A campanha segue a US$ 10 por dia.
- **Próximo passo:** ler a rodada 3, IG-06 contra IG-12, em 15/11. O próximo da fila é o IG-14.

### 2026-11-11 · Campanhas renomeadas para o padrão novo de nomes
- **O que fiz:** renomeei pelo MCP da Meta as duas campanhas, os quatro conjuntos, os quatro anúncios e os cinco públicos personalizados para o [[03-processos/convencoes|padrão novo]], pelo que está configurado na conta: [[seguidores-frio-perfil]] e [[distribuicao-quente-zero-to-hero]]. Nesta conta a edição fica em rascunho; publiquei só os 10 renomes, que eram os únicos rascunhos, sem mudar status. Conferi na API: o IG-03 e o conjunto dele seguem pausados, e o resto segue ativo.
- **O que achei:** os conjuntos de seguidores rodam no Facebook e no Instagram, embora o nome antigo dissesse `ig`. O público salvo `int_cad-dental_us` ficou com o nome antigo, porque o MCP não renomeia público salvo.
- **Próximo passo:** renomear o público salvo no Gerenciador, quando alguém estiver lá.

### 2026-11-09 · Grupo de 06 a 09/11, primeira leitura pela rotina
- **O que fiz:** primeira leitura do grupo pela rotina WhatsApp diário. Registrei as 64 mensagens de 06 a 09/11.
- **Resultado em:** `fontes/2026-11-09-whatsapp-grupo.md`
- **O que achei:** em 06/11, a Marjorie passou o código para verificar o WhatsApp na conta de anúncios e disse que vai trocar o número dela no grupo. Ficou combinado o Pixel direto no site, sem GTM por ora, com o Lead da lista de espera como prioridade. Em 08/11, a Julia mandou um vídeo novo de dica de exocad (DffdDhwhldx), que entrou como #28 na lista de posts. Em 09/11: 14.035 seguidores em 02/11 e 15.764 em 09/11, com uns 900 de 08 para 09/11 vindos desse vídeo, no orgânico.
- **Decisões:** o #28 não entra no tráfego agora, para não matar a entrega orgânica. Entra quando o orgânico esgotar, e a Julia avisa (Guilherme, 09/11).
- **Próximo passo:** acompanhar o aviso da Julia sobre o #28.

### 2026-11-09 · Resumo da rodada 1 enviado ao grupo
- **O que fiz:** com o ok do Guilherme, enviei no grupo "CURSO EXOCAD 🚀🇧🇷" o resumo da rodada 1 de seguidores, pelo número da agência no whatsapp-mcp: resultado do IG-06 e do IG-03, com links, e o IG-07 já no ar para teste.
- **Próximo passo:** leitura da rodada 2 em 3 dias.

### 2026-11-09 · Rodada 1 de seguidores e fichas das campanhas
- **O que fiz:** abri as fichas das duas campanhas em `campanhas/`, no modelo do vault, com os IDs da Meta conferidos na API. Registrei a rodada 1 da campanha de seguidores.
- **Resultado em:** `campanhas/marjorie-seguidores-frio-0611.md` e `campanhas/marjorie-distribuicao-quente-0611.md`
- **O que achei:** de 06 a 09/11, o IG-03 gastou US$ 16,07 e trouxe 11 seguidores (US$ 1,46 cada). O IG-06 gastou US$ 16,54 e trouxe 30 (US$ 0,55). O IG-03 teve a visita ao perfil mais barata, US$ 0,08 contra US$ 0,23, mas só 5% das visitas viraram seguidor, contra 42%. A campanha da base foi criada em 09/11 e está em análise.
- **Decisões:** o Guilherme pausou o IG-03 e manteve o IG-06. O critério do rodízio passa a ser o custo por seguidor, e não o custo por visita. O próximo da fila da Julia é o IG-07.
- **Próximo passo:** subir o IG-07 num conjunto novo e ler a rodada 2 em 3 dias.

### 2026-11-09 · Lead pelo clique no botão
- **O que fiz:** conferi que o site não tem página de obrigado (10 endereços comuns dão 404, e o sitemap não tem nenhuma). Com o ok do Guilherme, criei e ativei pelo MCP uma regra de clique no Pixel `1775314010396135`: `Lead` no botão "Join the list", com `content_name: zth_waitlist`. ID da regra: `4511374259101290`. A regra já aparece na config pública do Pixel.
- **Decisões:** ficam de fora o "Join the waiting list" do topo, que só leva ao formulário, e o "ME AVISE" de `/pt/course`, que é a lista do curso em português. O evento conta tentativa de envio: o botão só libera depois do aceite dos termos, mas um erro no envio ainda conta.
- **Próximo passo:** testar com uma inscrição real no "Testar eventos". Quando a Julia puser o Lead no código, desativar esta regra.

### 2026-11-09 · Evento de Lead da lista de espera
- **O que fiz:** li o código do site para ver como disparar o Lead da lista de espera, sem enviar o formulário.
- **O que achei:** o Pixel `1775314010396135` está no site e só manda PageView. O formulário envia para `/api/zth-waitlist` e mostra o sucesso na mesma página, sem trocar de endereço. Por isso não dá para medir por página de obrigado nem por conversão personalizada de URL: o Lead precisa entrar no código, no retorno de sucesso do envio. O site também tem formulários da calculadora e de contato, então o evento leva `content_name: zth_waitlist` para separar.
- **Decisões:** evento padrão `Lead`, como manda o `docs/convencoes.md`. A CAPI pelo `/api/zth-waitlist`, com o mesmo `event_id`, fica como segundo passo.
- **Próximo passo:** a Julia aplica o código. Com o Lead chegando, a campanha 2 pode otimizar para ele ou seguir no ThruPlay.

### 2026-11-06 · Revisão das clientes: posts e interesses
- **O que fiz:** registrei a conversa do grupo de 05/11 e transcrevi os 5 áudios localmente. Atualizei a lista de posts e a de interesses. Conferi pela API que os 6 posts sugeridos pela Julia podem virar anúncio, então nenhum é colab.
- **Resultado em:** `fontes/2026-11-05-whatsapp-grupo.md`, `entregas/2026-11-05-posts-para-captacao.md` e `entregas/2026-11-05-publico-interesses.md`
- **O que achei:** um dos 6 é o vídeo do curso, que fala da lista de espera e já é o criativo da campanha da base. Outro é uma imagem única, formato que o Guilherme tinha tirado da lista em 05/11. A Julia não mandou os 10 preferidos em ordem: mandou o que tirar e o que pôr.
- **Decisões:** saem 5 posts em português ou da rotina na Nova Zelândia, e um deles fica de reserva. Entram 6 que trouxeram seguidores, e a lista fecha em 27. Colabs ficam para um segundo nível de teste, depois do lançamento. O público frio é só em inglês. Depois do lançamento, a Julia vai refazer em inglês alguns vídeos em português e repostar.
- **Correção (06/11):** a "lista pra postar inicial" da Julia, com os 10 primeiros, não estava no primeiro envio da conversa. Montei uma ordem de prioridade sem ela, e o Guilherme percebeu. Registrei a mensagem e troquei a ordem pela da Julia.
- **Estrutura final (06/11):** o Guilherme sobe as campanhas à mão. Na de seguidores, Engajamento com destino no perfil, são dois conjuntos de US$ 5 por dia com 1 post cada, para garantir a entrega de cada um. A da base roda só o vídeo de trajetória, a US$ 5 por dia. Total de US$ 15 por dia. Nomes em `docs/convencoes.md`, com o ID `IG-NN` e o ID do criativo no fim do nome do conjunto.
- **Status no fim do dia (06/11):** a campanha 1, de seguidores, está no ar. A campanha 2 ficou em espera até a Julia responder se dá para pôr o Pixel na página da lista de espera, que é o link da bio.
- **Próximo passo:** primeira leitura de custo por seguidor e frequência da campanha 1 em 3 dias, para o rodízio.

### 2026-11-05 · Públicos e nomes
- **O que fiz:** defini os públicos da campanha com o padrão novo de nomes do `docs/convencoes.md`. Pesquisei na base da Meta os interesses que existem para o público frio e comparei interesses com semelhante dos compradores.
- **Resultado em:** `entregas/2026-11-05-publico-interesses.md` e a seção de públicos da estratégia
- **O que achei:** a Meta não tem interesse de exocad nem de marcas do setor. O que segmenta de verdade são os cargos e os campos de estudo. O curso antigo era vendido pela iDD, então a lista de compradores talvez não seja da Marjorie. A Meta trocou a porcentagem de vídeo assistido por três níveis.
- **Decisões:** começar com interesses, num conjunto só, de 22 a 55 anos. O semelhante fica para quando houver lista com o tamanho mínimo. O Guilherme criou os públicos personalizados e pediu às clientes os 10 melhores vídeos, em ordem de preferência, e a revisão dos interesses.
- **Próximo passo:** com a resposta das clientes, criar o `int_cad-dental_us` e subir as campanhas de seguidores e do vídeo do curso.

### 2026-11-05 · Posts do perfil para a captação de seguidores
- **O que fiz:** li os 110 posts do @marjoriedentalcad pela API, do mais antigo ao mais recente, e separei 37 que servem para captar seguidor no público frio dos EUA. Na revisão, o Guilherme tirou 23: as imagens únicas e os posts em colab, que não dá para impulsionar. Ficaram 14. Depois entraram mais 3 vídeos, o DWy_NIqDQIC (a música se troca no anúncio), o CqJK4R2BIqp e o CzmSyFXhm5x, e 23 foram para uma lista de dúvidas do Guilherme. A API não devolve colabs nem alguns posts com música, então o Guilherme fez login no navegador do app e conferi os 150 posts do perfil. Entraram mais 12 vídeos com música licenciada (a música se troca no anúncio), e a lista principal fechou em 29. Na revisão final, o Guilherme tirou mais 3 e os 3 em dúvida: ficaram 26, enviados ao grupo do projeto. Os 23 da lista de dúvidas foram recusados pelo Guilherme.
- **Resultado em:** `entregas/2026-11-05-posts-para-captacao.md`
- **O que achei:** ficaram de fora os posts só em português, os datados (eventos, venda de curso antigo), os pessoais e os do lançamento atual. Quatro posts não tiveram o arquivo devolvido pela API, o que costuma ser música com direito autoral. Li só as legendas: o idioma do áudio dos vídeos precisa ser confirmado.
- **Decisões:** o rodízio de seguidores roda com 2 posts por vez, a cada 3 dias, começando pelos mais antigos (Guilherme). A estratégia de 04/11 previa 3. O vídeo novo do curso vai para a base.
- **Próximo passo:** o Guilherme manda a lista para a Marjorie e a Julia. Com a resposta, subir as duas campanhas.

### 2026-11-04 · Estratégia de lançamento e verba
- **O que fiz:** li os 25 posts mais recentes do @marjoriedentalcad pela API e montei a estratégia de novembro em 4 fases, com 3 opções de verba.
- **Resultado em:** `entregas/2026-11-04-estrategia-lancamento.md`
- **O que achei:** o lançamento já tem data (27/11) e lista de espera. Isso muda o alvo da captação: de seguidor para lista de espera. Parte da base é brasileira, então a distribuição também filtra por país.
- **Decisões:** verba enxuta, US$ 600 em novembro (Guilherme). O Guilherme refez o desenho: público frio vai para o perfil, e não para a lista de espera. O vídeo do curso vai para a base, a lista de espera só entra no lembrete de 25 e 26/11, e a LP só no carrinho de 27 a 30/11. A estratégia cobre só novembro. A verba começa em US$ 15 por dia, o mínimo para testar, e escala ou se mantém pelo resultado. Quando a Julia falou em "deixar dinheiro", era saldo no cartão, não na conta de anúncios. Os criativos de seguidores entram em rodízio a cada 3 dias. Captação fria só nos EUA, e a base recebe os anúncios sem filtro de país, Brasil incluído.
- **Próximo passo:** com o ok da Julia na verba, criar os públicos e subir as duas campanhas da fase 1.

### 2026-11-04 · Entrada da Marjorie no vault
- **O que fiz:** criei a nota do cliente, o briefing, o kanban e este log. As fontes foram o export do WhatsApp com a Julia, os 19 áudios (transcritos localmente com o Whisper) e o PDF da LP. Na conta de anúncios, pela API, li só a lista de campanhas.
- **Resultado em:** `04-clientes/marjorie/`
- **O que achei:** o acordo mudou no caminho. Em 19 e 20/10 era fazer a LP e o site pelo valor do fee, e a Julia fez os dois sozinha. Fechou em 02/11 como tráfego, a R$ 1.500, com o valor em dólar ainda a definir. A estratégia que o Guilherme propôs leva tráfego à LP só em dezembro, e o preço de lançamento acaba em 30/11.
- **Decisões:** slug `marjorie`. Escopo: tráfego pago, tracking, revisão de LP e site, e criativos. Sem contrato, e a meta será o marco de datas do lançamento.
- **Próximo passo:** mandar a estratégia e a verba para a Julia e subir os primeiros anúncios.

## Histórico anterior ao vault
- **19/10/2026:** a Julia propõe pagar o fee de ads para o Guilherme fazer a LP do curso e refazer o site da Marjorie, migrando do Wix para a Hostinger.
- **20/10/2026:** o Guilherme aceita. No mesmo dia, a Julia avisa que vai fazer o site com um amigo, usando o Claude.
- **25/10/2026:** a Julia mostra o site novo, feito com um design system no Claude.
- **26/10/2026:** o Guilherme promete um checklist de publicação de site.
- **01/11/2026:** site e LP prontos. A Julia pede tráfego para o perfil do Instagram e o valor mensal.
- **02/11/2026:** fechado a R$ 1.500, a pagar em dólar. A Julia manda os preços e o PDF da LP.
- **03/11/2026:** BM liberada para o Guilherme. Ele remove um parceiro desconhecido e cria a conta de anúncios em USD, e a Julia adiciona o cartão.
- **04/11/2026:** chega a lista de compradores. Postado o vídeo de trajetória, e criado o grupo com a Marjorie.
