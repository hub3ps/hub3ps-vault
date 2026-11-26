---
tipo: log
---
# Log

A entrada mais recente no topo. Uma por sessão de trabalho.

Formato:
### AAAA-MM-DD · <título curto>
- **O que:** 
- **Resultado em:** 
- **Decisões:** 
- **Próximo passo:** 

### 2026-11-26 · Preço da Black baixado para 49,90 €
- **O que:** o Guilherme baixou a oferta de 67 € para 49,90 €. Troquei o preço na lista, no obrigado e na página de vendas (12 menções, mais o valor do `InitiateCheckout`), com espaço fixo entre o número e o "€" para não quebrar no celular. Publicado e conferido no ar: nenhum 67 € sobrou nas três páginas
- **Resultado em:** https://curso.churrascodaelite.pt, `/black/` e `/obrigado/` (fonte `agencia_marketing/clients/churrascodaelite/lps/lista-black/`)
- **Decisões:** preço de 49,90 € + IVA (Guilherme, 26/11). Em Portugal, com 23% de IVA, a conta dá 61,38 €, a conferir no checkout. A meta de 12 vendas segue como foi definida, a 67 €, sem revisão registrada
- **Próximo passo:** o Guilherme ajusta a oferta na Hotmart e manda o link do checkout. Confiro se o link mudou e o valor no checkout

### 2026-11-26 · Oferta na Hotmart e página de vendas no ar
- **O que:** o Guilherme configurou a oferta de 67 € na Hotmart (checkout `pay.hotmart.com/E106463685V?off=2tl4n8g6`). Montei a página de vendas a partir da LP da lista aprovada pelo Lucas, com o formulário trocado pelo checkout, as UTMs repassadas (mais `src` e `sck` para o relatório da Hotmart) e o `InitiateCheckout` no clique. Também gerei o logo em 600x600 para a imagem do produto na Hotmart
- **Resultado em:** https://curso.churrascodaelite.pt/black/ (fonte `agencia_marketing/clients/churrascodaelite/lps/lista-black/black/`), conferida no ar. A lista segue na raiz até o fim da captação. Logo em `marca/logo-hotmart-600.png`
- **Decisões:** no checkout a Hotmart soma o IVA do país (Portugal: 67 € viram 82,41 €). O Guilherme decidiu manter a oferta e mostrar "67 € + IVA" na página
- **Português de Portugal:** "renda" (em Portugal, aluguel) virou "rendimento" nas duas páginas, a da lista e a de vendas, a pedido do Guilherme, e foi publicado e conferido no ar. Com isso a expressão "renda extra" saiu também da página de destino dos anúncios. O nome do curso, "Faturando com Churrasco", fica como está na Hotmart
- **Próximo passo:** campanha de vendas apontando para `/black/` e Pixel da Hotmart no checkout para medir a compra

### 2026-11-25 · Grupo de 24 e 25/11, pela rotina
- **O que:** a rotina WhatsApp diário registrou as 10 mensagens de 24/11, 09h05, a 25/11, 08h23, com um áudio do Lucas transcrito
- **Resultado em:** `fontes/2026-11-25-whatsapp-grupo.md`
- **Reunião:** o Guilherme perguntou se o Lucas tinha tempo em 24/11 (09h06). O Lucas disse que sim às 11h55, e o Guilherme perguntou o horário às 12h30, sem resposta no grupo em 24/11. Não há registro de que a conversa aconteceu. Em 25/11, 08h22, o Lucas disse em áudio que está online hoje e que é só ligar a hora que o Guilherme quiser. O Guilherme respondeu "Beleza!!!" às 08h23
- **Decisões:** nenhuma nova no grupo
- **Próximo passo:** o Guilherme liga para o Lucas hoje, 25/11. Pauta em aberto: os próximos passos do Lucas no grupo (pedido de 23/11) e a Black, que começa em 27/11

### 2026-11-24 · Grupo de 23/11 à noite, pela rotina
- **O que:** a rotina WhatsApp diário registrou as 4 mensagens de 23/11, 18h24 a 20h17
- **Resultado em:** `fontes/2026-11-24-whatsapp-grupo.md`
- **Do Lucas:** "Depois me explica os próximos passo que tenho de fazer no grupo" (23/11, 18h24). Não diz se é o grupo da Black Week ou este
- **Reunião:** o Guilherme propôs "amanhã no período da tarde", ou seja, 24/11 à tarde (23/11, 20h17). Até a coleta o Lucas não confirmou
- **Decisões:** nenhuma nova no grupo
- **Próximo passo:** o Lucas confirmar a reunião de 24/11 à tarde; o Guilherme explicar a ele os próximos passos no grupo, de preferência na reunião

### 2026-11-24 · VL-08 e VL-10 na biblioteca e no ar
- **O que:** o Claude subiu VL-08 e VL-10 em 1080p na biblioteca da CA01, pela Marketing API, depois que o Guilherme deu ao token acesso de gravação na conta. O Guilherme montou à mão um conjunto e um anúncio para cada vídeo, na campanha da lista, e o Claude conferiu tudo pela API
- **Resultado em:** [[campanhas/leads-quente-lista-de-espera]], na tabela de IDs e no histórico
- **Decisões:** 6 € por dia em cada conjunto novo, e a campanha passa a 28 € por dia até 26/11 (Guilherme)
- **Correção:** a UTM dos dois anúncios novos vinha com `utm_content=vl-05`. O Claude trocou os criativos pelo MCP (VL-08 `1710054940638041`, VL-10 `1475215714703215`), e os dois seguem ativos no ar com `vl-08` e `vl-10`. O `pac_relaxation` ficou ligado, por decisão do Guilherme
- **Próximo passo:** leitura diária até o fim da captação, em 26/11

### 2026-11-23 · Vídeos e carrossel do Lucas, de 20 a 22/11
- **O que:** baixados os 3 vídeos (20 e 21/11) e o carrossel de 7 imagens (22/11) do grupo. A ponte do WhatsApp devolvia 403 em toda mídia, porque cortava a autorização do link. Corrigida a função `extractDirectPathFromURL` em `~/ferramentas/whatsapp-mcp/whatsapp-bridge/main.go`, com o binário antigo em `whatsapp-bridge.bak-20261123`. Vídeos transcritos, convertidos de 4K HDR para 1080p e comprimidos abaixo de 10 MB
- **Resultado em:** [[entregas/2026-11-23-videos-do-lucas]] e na pasta do Drive `Criativos · Captação lista Black`, com os tamanhos conferidos byte a byte
- **Decisões:** nenhuma do Guilherme ainda. A proposta: VL-10 e VL-08 na fila da lista até 26/11; VL-09 para seguidores e venda; carrossel CR-01 só como anúncio depois de tirar "renda extra" dos cards 1 e 5 e corrigir o card 7
- **Próximo passo:** o Guilherme decide se sobe VL-10 e VL-08 na lista e se pede ao Lucas o ajuste do carrossel

### 2026-11-23 · Leitura das campanhas e plano da semana da Black
- **O que:** leitura pela API (MCP e Marketing API) de 16 a 23/11, a pedido do Guilherme, para otimizar e organizar a semana
- **Entrega parada:** o cartão da CA01 falhou. Período de carência em 21/11 (13h54 UTC) e 22/11 (10h08 UTC), depois "Pagamento necessário": nenhuma impressão de 22/11, 16h, até a leitura de 23/11, 12h53 UTC. O Lucas pagou 20,03 € em 23/11, 10h25 UTC, e a conta voltou a Ativa. Era o "travou o pagamento" dele. Às 12h53 UTC a entrega ainda não tinha voltado a aparecer nos números
- **Lista de espera (18 a 22/11):** 54,22 €, 21 `Lead` (2,58 € cada) e 20 `CompleteRegistration` (clique no grupo VIP). VL-07: 23,60 €, 12 leads a 1,97 €, CTR 5,13%. VL-05: 30,62 €, 9 leads a 3,40 €, CTR 3,86%. O custo subiu depois do primeiro dia (20 a 22/11: VL-07 a 3,36 €, VL-05 a 5,33 €). Frequência 1,5, sem saturação. **Verba:** em 20/11 o Guilherme subiu o VL-05 para 10 € por dia quando ele tinha o lead mais barato (19/11: 3,06 € contra 3,37 €), e o custo dele subiu depois. Em 23/11, a pedido dele, inverti pelo MCP: VL-07 para 10 € e VL-05 para 6 €, conferido no ar
- **Seguidores:** os conjuntos IG-01 e IG-02 de 16/11 estão pausados. Roda só `Aberto 23-55 | Homem | Portugal | Visita ao perfil | IG-01` (`120250683957360559`, de 18/11, 7 € por dia, **sem data de fim**): 27,36 €, 925 visitas ao perfil e 111 seguidores pelo campo `instagram_profile_follow_v2` do MCP (cerca de 0,25 € cada), a conferir no Ads Manager
- **Verba:** cerca de 98 € gastos desde 16/11 (110,40 € na vida da conta, menos 12,38 € antigos). No ritmo de 23 € por dia até 26/11, chega a uns 190 €, e sobram uns 260 € dos 450 € de novembro para a Black (cerca de 65 € por dia)
- **Falta para a Black:** campanha de vendas (não existe), página de vendas com o checkout a 67 € (só existe a LP da lista), oferta de 67 € na Hotmart (com o Lucas) e Pixel no checkout da Hotmart para medir a compra
- **Plano da semana:** 23/11 rebalancear a verba da lista, data de fim no Homem IG-01, conferir a volta da entrega e avaliar os vídeos de 22/11. 24/11 reunião com o Lucas (oferta na Hotmart, cartão e roteiro do grupo), contagem da planilha e do grupo. 25/11 página de vendas e campanha de vendas em rascunho, cartão garantido. 26/11 publicar a campanha de vendas e fechar a captação às 23h59. 27 a 30/11 leitura diária. 01/12 fechamento e relatório
- **Tarefas:** 3 fechadas (as duas leituras e o pagamento) e 8 novas em `08-tarefas/notas/`
- **Ajustes do Guilherme em 23/11:** o pagamento da conta foi ajustado, e a entrega voltou (impressões no conjunto às 13h UTC). A página de vendas e a oferta de 67 € na Hotmart, com o Lucas, foram para 24/11
- **Planilha (23/11):** 27 linhas, 26 pessoas (uma inscrição repetida, linha 22), todas da campanha: VL-07 16 (1,48 € cada), VL-05 10 (3,06 €). O Pixel contou 21, por causa de quem recusa os cookies. O Guilherme conta 24 pessoas no grupo
- **WhatsApp da planilha:** 19 das 27 linhas davam `#ERROR!`, porque a LP manda "+351 9..." e a planilha lia como fórmula. Os 27 números foram recuperados da fórmula de cada célula e regravados como texto pelo Chrome, conferidos célula a célula. Na fonte, a LP passou a mandar o WhatsApp com apóstrofo e o `lista-black.gs` ganhou o `comoTexto`, sem commit. LP corrigida publicada na Vercel com o OK do Guilherme (23/11) e conferida no ar. O `.gs` novo só vale depois de reimplantado no Apps Script
- **Resumo no grupo:** aprovado pelo Guilherme e enviado em 23/11, por volta das 10h27 (Brasília), direto pela API da ponte. A ponte estava travada: reiniciada pelo serviço `com.hub3ps.whatsapp-bridge` do launchd, sem QR (a sessão seguia válida). O MCP do WhatsApp desta sessão continua sem alcançar a ponte (connection reset) e precisa ser reconectado no app
- **Próximo passo:** página de vendas e oferta na Hotmart em 24/11. A data de fim do Homem IG-01 segue sem decisão

### 2026-11-23 · Grupo de 20 a 23/11, pela rotina
- **O que:** a rotina WhatsApp diário registrou as 32 mensagens de 20/11 10:08 a 23/11 09:16. Três áudios e dez documentos não baixaram, então o conteúdo deles não está registrado
- **Resultado em:** `fontes/2026-11-23-whatsapp-grupo.md`
- **Do Lucas:** "tá entrando gente" (20/11, 10h08), e o Guilherme respondeu que "compensa chamar esse pessoal" (10h17); o resto do contexto estava no áudio. Em 21/11, 06h54, disse que ia tentar gravar mais dois vídeos. Em 21/11, 08h53, pediu 5 minutos sobre "um outro assunto aqui de urgencia pra 2027", e os dois combinaram de falar às 11h11; o que foi conversado não está no grupo. Em 22/11, 17h23, mandou vídeos e um carrossel para avaliar como criativos e pediu uma reunião nesta semana. Em 23/11, 05h44: "Travou o pagamento não consegui colocar pra pagar"
- **Pagamento:** a mensagem não diz de quê. Na leitura pela API em 23/11, a CA01 `1295259920836612` estava `ACTIVE` e com forma de pagamento, então não é bloqueio da conta de anúncios por dívida. O Guilherme disse "Já vou olhar aqui" (23/11, 09h16)
- **Decisões:** nenhuma nova no grupo
- **Próximo passo:** o Lucas dizer o dia da reunião (o Guilherme perguntou em 23/11, 09h16); baixar e avaliar os vídeos e o carrossel de 22/11; o Guilherme registrar o assunto de 2027 da conversa de 21/11

### 2026-11-19 · Grupo de 18 e 19/11, pela rotina
- **O que:** a rotina WhatsApp diário registrou as 32 mensagens de 18/11 10:57 a 19/11 05:36. Quatro áudios não baixaram e ficaram sem transcrição
- **Resultado em:** `fontes/2026-11-19-whatsapp-grupo.md`
- **Do Lucas (18/11):** chegaram muitos pedidos de orçamento de churrasco (10h57) e "muita mulher seguindo" (10h57). Em Portugal a promoção se chama "Black Week" (15h04). O grupo da Black está enchendo (17h06). Em 19/11, 05h36, acha que o lead pode sair mais barato que no Brasil, com o imposto
- **Decisões:**
  - Público feminino cortado 100% na campanha de seguidores (Guilherme, 18/11, 10h58). Não conferido pela API nesta rotina
  - O Lucas pode gravar vídeos novos no estilo dos que mandou (Guilherme, 18/11, 14h48)
  - Imagem e nome do grupo da promoção passam a "Black Week" (Guilherme, 18/11, 15h08). O Lucas respondeu "Eu vi aqui, perfeito" às 15h26
- **Números ditos no grupo, sem valor:** "Lead tá bem barato" (Guilherme, 18/11, 17h10). Não substitui a leitura pela API
- **Próximo passo:** leitura da lista de espera até sexta, 21/11, como o Guilherme disse no grupo (18/11, 14h47)

### 2026-11-18 · Logo e fotos dos grupos
- **O que:** ajustei a arte do grupo da promoção: "BLACK FRYDER" virou "BLACK WEEK" (nome que o Lucas usa), saíram os 4 cards e a arte foi enquadrada no círculo do WhatsApp. Para a logo, vetorizei primeiro a do site (duas vezes), e o Guilherme reprovou: além de ruim, era outra logo. A que vale é a das artes do Lucas. Recortei essa da arte da Black e ampliei em PNG, sem vetor, para a foto do grupo por enquanto
- **Resultado em:** [[marca/marca]]
- **Pendente:** o arquivo original da logo, com o Lucas ou o designer
- **Próximo passo:** o Guilherme põe `perfil-grupo-operacional.png` no grupo "Churrasco da Elite - Tráfego" e a arte Black Week no grupo da promoção

### 2026-11-18 · Lista de espera no ar
- **O que:** o Guilherme corrigiu à mão no Ads Manager (link, link de exibição, aprimoramentos, configuração do criativo, copy v2 sem preço e sem "renda extra") e publicou `Leads | Quente | Lista de espera`. Conferi pela API
- **Resultado em:** [[campanhas/leads-quente-lista-de-espera]]
- **No ar:** 2 conjuntos `ACTIVE` a 6 € por dia até 26/11, anúncios em análise. Link e textos principais certos, sem catálogo
- **Expansão do público:** estava ligada; desliguei pelo MCP a pedido do Guilherme e conferi no ar
- **Botões:** o Guilherme igualou em "Candidatar-se". O "image_animation" fica: não aparece no Ads Manager e não age em vídeo
- **Regras novas de montagem de anúncio:** registradas em `03-processos/convencoes.md`, seção "Montagem do anúncio"
- **Próximo passo:** primeira leitura de custo por lead em 20/11

### 2026-11-18 · Lista de espera: público quente
- **O que:** a pedido do Guilherme, a campanha da lista passou a rodar só para `seguidores` e `Engajou IG 365d` (criado agora, `120250684886700559`). Renomeada para `Leads | Quente | Lista de espera`, conjuntos renomeados, criativos refeitos com a UTM nova. Segue em rascunho
- **Resultado em:** [[campanhas/leads-quente-lista-de-espera]]
- **Próximo passo:** OK do Guilherme para publicar

### 2026-11-18 · Campanha da lista de espera em rascunho
- **O que:** `Leads | Frio | Lista de espera` montada pelo MCP na CA01, em rascunho: 2 conjuntos a 5 € por dia até 26/11, um com o VL-07 e outro com o VL-05, otimizando pelo `Lead`. 5 textos, 5 títulos e 5 descrições, em português de Portugal, sem promessa de ganho
- **Resultado em:** [[campanhas/leads-quente-lista-de-espera]] (o arquivo trocou de nome com a campanha)
- **Decisões:** verba de 5 € por conjunto (Guilherme, 18/11). Advantage+ público ligado e sem exclusão de seguidores, diferente da de seguidores
- **Achado:** o conjunto IG-01 da `Seguidores | Frio | Perfil` estava pausado na leitura de 18/11. Não fui eu
- **Próximo passo:** OK do Guilherme para publicar

### 2026-11-18 · Vídeos do Lucas analisados para a captação
- **O que:** os 7 vídeos que o Lucas mandou em 09/11, vistos por quadros e transcritos
- **Resultado em:** [[entregas/2026-11-18-videos-do-lucas]]
- **O que achei:** 5 aproveitáveis (VL-01, 02, 03, 06 e 07), 3 deles só com corte, porque prometem de 1.500 € a 5.000 € por mês. VL-04 (fala de 2025) e VL-05 (a promessa é o vídeo inteiro) ficam de fora. Todos chegaram em 576x1024 pelo WhatsApp
- **Cortes (18/11):** feitos a pedido do Guilherme, os 5 em `~/Downloads/churrascodaelite-captacao/`, conferidos por retranscrição. VL-06 com cartela final da lista VIP
- **Decisão do Guilherme (18/11):** VL-07 e VL-05 inteiros, um em cada conjunto. VL-02, VL-03 inteiros e VL-04 sem o "2025" ficam na fila. VL-01 e VL-06 descartados, assim como os cortes da primeira rodada
- **Drive (18/11):** os 5 subidos em `12. Lucas - Churrasco da Elite/Criativos · Captação lista Black`, pelo Chrome, e conferidos pelo tamanho
- **Próximo passo:** montar a campanha de captação da lista com dois conjuntos, otimizando por `Lead`

### 2026-11-18 · Cookies da LP no esquema do JurIA
- **O que:** o aviso de cookies da LP e da página de obrigado passou para o esquema do site do JurIA: o Pixel liga sozinho, e o aviso tem só "Recusar" e "Dispensar". Uma primeira versão com "Preferências" e "Gerir cookies" no rodapé foi feita e desfeita no mesmo dia: o Guilherme não gostou das opções de seleção
- **Resultado em:** `agencia_marketing/clients/churrascodaelite/lps/lista-black/` (comum.js, index.html, obrigado/index.html, README.md), publicado em curso.churrascodaelite.pt, sem commit. O aviso saiu do HTML das páginas e ficou só no `comum.js`
- **Teste no ar:** o PageView sai sem clique nenhum. Depois do "Recusar", um evento de teste não saiu, o cookie `_fbp` foi apagado e a página seguinte nem carrega o Pixel. Só o `SubscribedButtonClick` automático da Meta sai no próprio clique do "Recusar"
- **Decisões:** ligar o Pixel sem esperar o aceite foi pedido do Guilherme (18/11). O RGPD pede consentimento antes, e o risco é do Lucas, como dono da página. Quem recusa não tem como religar
- **Próximo passo:** subir a campanha de captação da lista otimizando por `Lead`

### 2026-11-18 · Pixel na LP da lista
- **O que:** Pixel `333549951080063` (escolhido e ajustado pelo Guilherme) posto em `comum.js`, `noindex` tirado da LP e publicado em curso.churrascodaelite.pt. O clique no botão do grupo VIP passou de `GrupoVIP` (personalizado) para `CompleteRegistration`, com `content_name: grupo_vip`
- **Resultado em:** `agencia_marketing/clients/churrascodaelite/lps/lista-black/` (comum.js, obrigado/index.html, README.md), sem commit
- **Teste no ar:** com o cookie aceito, saíram PageView, `Lead` e `CompleteRegistration` para o `333549951080063`, e a Meta registrou o disparo (18/11, 13h30 UTC). O teste deixou 1 `Lead` e 1 `CompleteRegistration` de mentira no Pixel, sem linha na planilha. A Meta também manda sozinha o `SubscribedButtonClick` no clique
- **Decisões:**
  - O `Lead` continua só para quem chega à página de obrigado pelo formulário, uma vez por inscrição: quem abre o link direto ou recarrega não conta
  - A entrada no grupo não se mede de fora do WhatsApp, então o cadastro concluído é o clique no botão
  - Pelo RGPD, quem recusa os cookies não gera evento nenhum: a planilha segue sendo a contagem verdadeira
- **Próximo passo:** subir a campanha de captação da lista otimizando por `Lead`

### 2026-11-17 · Grupo de 16 e 17/11, pela rotina
- **O que:** a rotina WhatsApp diário registrou as 62 mensagens de 16 e 17/11 do grupo
- **Resultado em:** `fontes/2026-11-17-whatsapp-grupo.md`
- **O que achei:**
  - **LP aprovada pelo Lucas:** "TA PERFEITA" (16/11, 13h39), sobre o link `churrascodaelite.vercel.app` mandado pelo Guilherme às 10h47. O preço de 67 € não foi comentado à parte
  - **WhatsApp em Portugal:** o Lucas disse que o pessoal usa "BASTANTE" (16/11, 13h36)
  - **Cartão na CA01:** o Guilherme passou a conta `1295259920836612` (13h49) e pediu o cadastro em euro, para não pagar os 12% de imposto do Brasil. O Lucas avisou "cartao ja cadastrado" às 15h00. Nenhum dado de cartão foi colado no grupo
  - **Grupo da Black:** o Lucas tem o grupo do primeiro workshop, com 23 pessoas, das quais só 6 foram presencialmente (13h50). O Lucas criou um grupo novo e mandou o link às 14h05. É o mesmo link que já está em `comum.js` da LP
  - **Seguidores:** em 17/11, 06h23, o Lucas disse que estão chegando muitos seguidores (sem número). O áudio dele das 09h05 não baixou. O Guilherme respondeu que vai ver a qualidade desses seguidores, que acha interessante segmentar só para homens e que vai otimizar as campanhas (17/11, 09h06 e 09h07)
  - **Hotmart:** o Lucas pensou em, no futuro, sair da Hotmart para uma página própria com Stripe. O Guilherme disse que compensa quando houver um fluxo bom de vendas (16/11, 15h48)
- **Decisões:**
  - A lista de espera vai para um grupo no WhatsApp, que libera as vagas na Black. Teste nesta semana: se der bom, mantém; se não, ajusta e roda direto para vender na LP (Guilherme, 16/11, 13h48)
  - Grupo novo, só para a Black, em vez do grupo do workshop. Quem foi ao workshop e não comprou se pega pelo Instagram (Guilherme, 16/11, 13h50 a 13h52)
- **Próximo passo:** com a LP aprovada, tirar o `noindex` e pôr o Pixel novo. O Guilherme olha a qualidade dos seguidores e decide a segmentação só para homens

### 2026-11-16 · Campanha de seguidores no ar
- **O que:** o Guilherme publicou à mão os dois conjuntos da `Seguidores | Frio | Perfil`. Conferi na API e registrei os IDs
- **Resultado em:** `campanhas/seguidores-frio-perfil.md` (seção "IDs no ar")
- **Decisões:** o Guilherme excluiu quem já segue o perfil (público `seguidores`) e deixou o Advantage+ público desligado. Os conjuntos subiram sem data de fim. A pedido dele, pus 26/11 às 23h59 pelo MCP e conferi na leitura
- **Próximo passo:** primeira leitura de custo por seguidor em 19/11

### 2026-11-16 · Planilha da lista ligada à LP
- **O que:** o Guilherme criou a planilha com o Apps Script, na conta guitrafegopago@gmail.com, e mandou a URL. Coloquei em `CONFIG.endpoint` (`comum.js`) e publiquei em curso.churrascodaelite.pt
- **Resultado em:** a planilha do Guilherme. O script respondeu `{"ok":true}` a um envio direto, e uma inscrição pelo formulário no ar chegou à página de obrigado. Ficaram linhas "TESTE Claude" a apagar
- **Decisões:** nenhuma. O primeiro teste deu "Você precisa ter acesso" por erro meu no `curl` (mantive POST ao seguir o redirecionamento), e não por falta de acesso
- **Conferido:** o Guilherme viu as linhas de teste na planilha (16/11)
- **Próximo passo:** Lucas aprova a LP; depois, Pixel novo e tirar o `noindex`

### 2026-11-16 · Domínio da LP e página de obrigado
- **O que:** o Guilherme pôs o domínio `curso.churrascodaelite.pt` no projeto Vercel, com o CNAME no dominios.pt. A raiz `churrascodaelite.pt` é a loja Shopify do Lucas, por isso a LP não pode ficar em `/curso`. A pedido dele, criei a página de obrigado com o botão do grupo VIP e passei a configuração do Pixel para `comum.js`, partilhado pelas duas páginas
- **Resultado em:** https://curso.churrascodaelite.pt e https://curso.churrascodaelite.pt/obrigado/, fonte em `agencia_marketing/clients/churrascodaelite/lps/lista-black/`, sem commit
- **Decisões:** o formulário leva à página de obrigado, e não mais direto ao WhatsApp. O `Lead` sai na página de obrigado, só para quem veio do formulário e uma vez só. O clique no botão dispara o `GrupoVIP`. Link do grupo sem os parâmetros de partilha. O endereço provisório `project-6x255.vercel.app` saiu do projeto, e o domínio novo serve a mesma cópia, sem Pixel e com `noindex`
- **Próximo passo:** Lucas aprova a LP. Depois, Pixel novo, Apps Script e tirar o `noindex`

### 2026-11-16 · Campanha de seguidores em rascunho, conjuntos à mão
- **O que:** o Guilherme confirmou a troca para a BM `666930504135899` e mandou subir a campanha de seguidores. Os registros passaram para a BM nova. Criei a campanha `Seguidores | Frio | Perfil` (`120250644049660559`) em rascunho pelo MCP. O conjunto foi recusado: a otimização por visita ao perfil não está disponível pelo MCP nesta conta, como na Marjorie
- **Resultado em:** `campanhas/seguidores-frio-perfil.md`, com a especificação para a subida à mão
- **Decisões:** Guilherme cria os conjuntos à mão, mantendo a visita ao perfil, em vez de otimizar por clique no link. Pixel novo fica para depois, criado pelo Guilherme (16/11)
- **Próximo passo:** Guilherme sobe os conjuntos; Claude confere na API e registra os IDs

### 2026-11-16 · Acessos na conta de anúncios nova
- **O que:** o Guilherme indicou a conta `1295259920836612` para os anúncios. Conferi pelo MCP a conta, a Página e o Instagram
- **Resultado em:** `cliente.md` (Acessos), `campanhas/seguidores-frio-perfil.md` e kanban
- **Decisões:** a conta dos anúncios passa a ser a CA01 - Churrasco da Elite (EUR, ativa, com pagamento), da BM `666930504135899`, e não a CA02. Página `111836513679647` e @churrasco_da_elite `17841403077087483` acessíveis, com os posts IG-01 e IG-02 disponíveis
- **Próximo passo:** subir a campanha de seguidores. Para a campanha da LP falta Pixel nesta conta, e a BM nova ainda não foi auditada

### 2026-11-16 · LP da lista no ar em domínio provisório, para o Lucas aprovar
- **O que:** publiquei a LP no projeto Vercel `churrasco-da-elite` (time hub3psmarketing, criado pelo Guilherme em 16/11), pela CLI, a partir de uma cópia no scratchpad
- **Resultado em:** https://project-6x255.vercel.app/ (público). O outro alias, `churrasco-da-elite-hub3psmarketing.vercel.app`, pede login da Vercel e não serve para mandar ao Lucas
- **Decisões:** a cópia de aprovação vai sem Pixel (`CONFIG.pixel` vazio) e com `noindex`, para os testes do Lucas não sujarem o Pixel `597919442616239`. O formulário ainda não grava (sem `CONFIG.endpoint`) e não leva ao grupo (sem `CONFIG.grupo`). A fonte ganhou uma guarda para carregar o Pixel só se houver ID
- **Próximo passo:** Guilherme manda o link ao Lucas. Depois da aprovação: Apps Script, grupo VIP, Pixel de volta e domínio próprio sob churracodaelitept.com

### 2026-11-16 · LP da lista com preço, cronómetro e seções de volta
- **O que:** a pedido do Guilherme, voltaram à LP as dores, o "o que ganhas" e o caminho da mentoria com eventos pagos (com a FAQ do bónus), com o texto da página do Framer passado para "tu". Entrou o card de preço, de 97 € por 67 €, e uma barra fixa com cronómetro até 27/11, 0h de Lisboa, no modelo da LP da Marjorie. De 27 a 30/11 a barra conta até o fim da Black e depois some
- **Resultado em:** `agencia_marketing/clients/churrascodaelite/lps/lista-black/index.html`, conferido no desktop e no celular, sem commit
- **Decisões:** preço da Black em 67 €, não 67,90 € (Guilherme, 16/11). Com 12 vendas dá 804 €, ainda o empate com os 800 € de fee e mídia, antes da taxa da Hotmart
- **Próximo passo:** Guilherme manda a LP ao Lucas para aprovar

### 2026-11-16 · Revisão da LP da lista antes de ir ao Lucas
- **O que:** comparei a copy da LP nova com a publicada no Framer (churracodaelitept.com, lida em 16/11) e corrigi o selo da garantia, que aparecia esticado (faltava `height: auto`)
- **Resultado em:** `agencia_marketing/clients/churrascodaelite/lps/lista-black/index.html`, sem commit
- **Decisões:** a copy da página de 97 € foi mantida onde serve à lista (módulos, para quem é, equipa, FAQ). Saíram mercado, dores, "o que ganhas", caminho da mentoria, preço, depoimentos sem nome e as FAQs do bónus e da garantia. A experiência do Lucas voltou a "em Portugal e no mundo", como na página dele
- **Próximo passo:** Guilherme decide se o bónus da mentoria volta, e manda a LP ao Lucas para aprovar

### 2026-11-16 · Grupo de 13 e 14/11, pela rotina
- **O que:** a rotina WhatsApp diário registrou as 16 mensagens de 13 e 14/11 do grupo
- **Resultado em:** `fontes/2026-11-16-whatsapp-grupo.md`
- **O que achei:** o Lucas se pôs à disposição para gravar no fim de semana (13/11, 12h38). O Guilherme disse que ia ver se precisava de vídeo e passar para ele gravar no fim de semana (13/11, 13h04). Não há no grupo o envio dos roteiros. Às 18h26, o Guilherme pediu ao Lucas para ser adicionado como ADM da Página do Churrasco da Elite no Facebook. O Lucas respondeu "feito" em 14/11, 11h25, depois de uma imagem que não baixou
- **Decisões:** nenhuma
- **Próximo passo:** conferir na BM se o Guilherme virou ADM da Página e ligar o @churrasco_da_elite à CA02, o bloqueio da campanha de seguidores. Ver com o Guilherme se os roteiros foram ao Lucas, já que o fim de semana de 14 e 15/11 passou

### 2026-11-13 · Campanha de seguidores desenhada e roteiros do fim de semana
- **O que:** ficha da `Seguidores | Frio | Perfil` com dois conjuntos (IG-01 e IG-02, 5 € por dia cada) e quatro roteiros para o Lucas gravar em 14 e 15/11
- **Resultado em:** [[04-clientes/churrascodaelite/campanhas/seguidores-frio-perfil|ficha da campanha]] e [[2026-11-13-roteiros-fim-de-semana|roteiros]]
- **Decisões:** começar pela lista dos 14, com dois conjuntos e um post em cada (Guilherme, 13/11). IG-01 e IG-02 são os dois primeiros, os dois com áudio original. Público e verba são proposta do Claude, a conferir pelo Guilherme
- **Bloqueio:** a campanha não sobe sem o @churrasco_da_elite na CA02 (conferido de novo na API em 13/11)
- **Próximo passo:** ligar o perfil à BM e à CA02, subir a campanha, revisar os roteiros e mandar ao Lucas

### 2026-11-13 · Posts para a captação de seguidores
- **O que:** os 82 posts do @churrasco_da_elite de 13/08 a 12/11 lidos no perfil, com 14 indicados para impulsionar e 7 bons em colab
- **Resultado em:** [[04-clientes/churrascodaelite/entregas/2026-11-13-posts-para-captacao|posts para a captação]]
- **Decisões:** critério é atrair quem quer viver de churrasco, e não quem contrata catering. Sem colab, pela lição de 05/11. Não assisti aos vídeos
- **Bloqueio:** o @churrasco_da_elite não está ligado à CA02 nem à BM; só o @omestredochurraspt está (API, 13/11)
- **Próximo passo:** Guilherme escolhe os posts, e o Lucas liga o @churrasco_da_elite à BM

### 2026-11-13 · LP da lista de espera da Black
- **O que:** LP nova da lista de espera, em HTML, com a copy e as fotos da página atual do Framer (churracodaelitept.com), formulário de nome, e-mail e WhatsApp, Apps Script para a planilha e grupo VIP depois da inscrição
- **Resultado em:** `agencia_marketing/clients/churrascodaelite/lps/lista-black/` (com README) e `ferramentas/lista-black.gs`
- **Decisões:** destino da lista é formulário mais grupo VIP (Guilherme, 13/11). O Pixel `597919442616239` só carrega com o aceite de cookies, por causa do RGPD. Preço da Black não aparece na página: só "preço especial de 27 a 30/11", enquanto os 67,90 € não estão confirmados com o Lucas. Depoimentos da página antiga ficaram de fora, por não terem nome
- **Próximo passo:** Guilherme cria o projeto na Vercel e a planilha, Lucas cria o grupo VIP. Com a URL e o link, a LP vai ao ar

### 2026-11-13 · Fechamento cumprido, escopo ampliado e auditoria da BM
- **O que:** meta, contrato e pagamento definidos pelo Guilherme; tracking e criativos entram no escopo; segunda auditoria da BM pela API
- **Resultado em:** [[04-clientes/churrascodaelite/cliente|cliente]] (frontmatter, escopo e acessos), [[2026-11-13-acordo-guilherme]] e kanban
- **Decisões (Guilherme, 13/11):** conta CA02 em EUR. Meta de 12 vendas na Black Friday a 67,90 €, com cerca de 450 € de anúncio em novembro. Sem contrato. Novembro pago. Briefing assíncrono. LP refeita do zero na Vercel, no domínio que já existe. Tracking e criativos dos anúncios no escopo. Painel na semana de 16/11. Calendário da proposta mantido
- **Auditoria (Claude):** pessoas são o Guilherme e dois perfis "Lucas Oliveira", todos com controle total. Usuário do sistema da CAPI. Um parceiro, "Peach" (`148826077524843`), a confirmar com o Lucas. Na CA02, um administrador sem nome entrou em 09/11 e saiu em 10/11, pelas mãos do Lucas
- **Próximo passo:** plano da Black, verificação de domínio e Pixel, LP na Vercel, criativos e as duas campanhas, ainda em 13/11

### 2026-11-13 · Acesso à BM conferido
- **O que:** a BM do Lucas (`1996641120812552`) já aparece no MCP da Meta, com a CA02 em EUR e a CA01 em BRL, as duas ativas e com forma de pagamento
- **Resultado em:** seção Acessos do [[04-clientes/churrascodaelite/cliente|cliente]] e kanban
- **Decisões:** nenhuma. A conta a usar fica com o Guilherme
- **Próximo passo:** auditoria de pessoas e parceiros da BM e escolha da conta

### 2026-11-13 · Grupo de 10 a 12/11, primeira leitura pela rotina
- **O que:** a rotina WhatsApp diário registrou as 23 mensagens do grupo, desde a criação em 10/11. O link de pagamento da Wise e os dados bancários foram omitidos da fonte
- **Resultado em:** `fontes/2026-11-13-whatsapp-grupo.md`
- **Decisões:** nenhuma nova. Os fatos do período já estavam na nota e no kanban desde 12/11: identidade visual (Lucas, 11/11), IBAN pedido e enviado (12/11), imagem do Lucas às 10h58 que não baixou, e a LP com lista de espera mais os primeiros anúncios prometidos pelo Guilherme para 13/11. O "Valeuu Lucas" das 16h45 não diz se a imagem era o comprovante, então o pagamento segue sem confirmação
- **Próximo passo:** LP com lista de espera e anúncios de seguidores e da base para a LP em 13/11, o que depende do acesso à BM e à conta de anúncios, ainda não registrado

### 2026-11-12 · Fechamento e entrada no vault
- **O que:** proposta marcada como fechada, pasta do cliente criada (nota, kanban e log), grupo do WhatsApp incluído na rotina diária e lembrete dos 3 meses agendado
- **Resultado em:** [[04-clientes/churrascodaelite/cliente|cliente]], [[05-comercial/propostas/churrascodaelite-2026-11|proposta]], [[00-sistema/whatsapp-grupos]] e a tarefa agendada `churrascodaelite-rediscutir-setup` (12/02/2027, 9h)
- **Decisões:** escopo em tráfego pago, estratégia como apoio pontual e ajustes na LP do curso. 350 € por mês, sem setup e sem os 10% nos 3 primeiros meses (Guilherme, 12/11/2026). O grupo entra na rotina desde 10/11, data em que foi criado, para a primeira leitura pegar a conversa inteira
- **Próximo passo:** o Guilherme define a meta, o contrato e a data de início do mês 1, e pede os acessos da BM e da conta de anúncios
