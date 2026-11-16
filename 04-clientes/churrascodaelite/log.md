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
