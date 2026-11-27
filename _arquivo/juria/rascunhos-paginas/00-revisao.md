---
tipo: arquivo
cliente: juria
atualizado: 2026-11-27
autor: claude
origem: agencia_marketing, clients/juria/rascunhos-paginas/00-revisao.md (migrado em 27/11/2026)
---
# Revisão de fatos · páginas de área do JurIA

Revisão em 14/10/2026 contra `comercial/funcionalidades.md`,
`comercial/planos-e-creditos.md`, `juria-site-astro/src/data/paginas.ts`,
`home.ts` e `faq.ts`. Uma linha por mudança. Os três JSON validam e não têm
travessão.

---

## Lote 1

### whatsapp-para-advogados.json

**Mudanças**
- `descricao`: "lembretes e cobranças no mesmo número" virou "Caixa compartilhada e lembretes no número do escritório". "Mesmo número" sugeria que a secretária atende pelo número do escritório, o que não está confirmado. A cobrança saiu porque não está confirmado que vale no Solo. A descrição também passava de 155 caracteres.
- Destaque 3: o título "Sem cobrança por mensagem" virou "A JurIA não cobra por mensagem", e o texto agora diz que a Meta cobra o que o escritório envia primeiro na conexão oficial. O título antigo dava a entender custo zero, e a seção 3.2 mostra que a Meta cobra.
- Seção "lembrete e cobrança": tirei `"plano": null`. O próprio rascunho tinha a dúvida sobre a cobrança por WhatsApp valer no Solo, e `null` afirma que vale nos quatro planos.
- Seção da Jú: o item "Memória do escritório" virou "Memória da Jú, que você vê e edita", que é o nome que a tela usa (3.1).
- Seção do funil: "Quando o contrato fecha, a oportunidade vira cliente" virou "Na conversão, a oportunidade vira cliente aproveitando os dados já colhidos". A fonte (8.3) não diz em que momento a conversão acontece. No `todo` da seção, anotei que o selo vale para o funil (⛔) e que o plano da conversão foi deduzido dele.
- Seção do portal: mantive o selo "Do Plus em diante", que vale para o portal (⛔ na seção 3). Acrescentei um `todo` explicando que o plano do envio de documentos foi deduzido do portal, e não lido na fonte.
- FAQ "A Jú conversa com os meus clientes?": "Quem atende cliente é a secretária virtual e a sua equipe, pela caixa de entrada do número do escritório" virou "a secretária virtual atende, e a sua equipe responde pela caixa de entrada". O texto antigo dizia por qual número a secretária atende, e isso não está confirmado.
- Mantidos com lastro: `plano: null` na caixa compartilhada (a seção 3.2 liga a tela à linha "WhatsApp direto na plataforma", ✅ no Solo), a Jú "do Solo ao Ilimitado" (✅ na seção 3, confirmada nos quatro planos em `funcionalidades.ts`), a cota da Jú (80/300/1.000/3.000), 1 crédito por 5 respostas, o código de 6 números válido por 10 minutos e a ativação em 1 minuto.

**Dúvidas para a Mobiletec** (já na lista `duvidas` do JSON)
- Plano da secretária virtual, e se ela é uma função separada ou a Jú num modo que a tela não mostra.
- O que dispara a transferência para humano, e por qual número a secretária atende.
- Se respostas rápidas e modelos da caixa compartilhada valem no Solo, porque a 8.8 lista a caixa como função nova sem plano.
- Se a cobrança enviada pelo WhatsApp funciona no Solo.
- Se existe lembrete de audiência para o cliente, e com que antecedência os avisos saem.
- Se a conversa do WhatsApp cria oportunidade no funil sozinha.
- Plano do envio de documentos pelo portal, que foi deduzido do plano do portal.
- Revisão jurídica da seção sobre ética da OAB. O texto não cita número de norma.

### financeiro-para-escritorio-de-advocacia.json

**Mudanças**
- Seção "honorários contratuais e divisão": agora diz que os contratos de honorários são do plano Plus em diante. Eles fazem parte do financeiro avançado (⛔ na tabela da seção 4), e a seção sem selo deixava os contratos parecerem disponíveis no Solo. A divisão de honorários e as parcerias continuam sem plano.
- Seção de inadimplência: "A régua de cobrança organiza os próximos contatos, sem depender de alguém lembrar" virou "a régua de cobrança, com as etapas de contato para quem está em atraso". O texto antigo sugeria envio automático, e a fonte (8.6) não fala em envio nem em canal.
- FAQ "Em quais cidades o JurIA emite NFS-e?": removi "confira durante o teste de 7 dias". Ninguém confirmou que dá para emitir nota durante o teste, e isso já estava nas dúvidas.
- FAQ "O dinheiro da cobrança cai em qual conta?": "Na conta do escritório" virou "Na conta de pagamentos do próprio escritório", que é o texto da fonte (8.6). Acrescentei que a cobrança é do Plus em diante, porque a resposta não citava plano.
- `duvidas`: tirei a data de obrigatoriedade do emissor nacional do texto. A data é proibida, e assim ela não vaza para a página se o JSON for integrado inteiro.
- Mantidos com lastro: NFS-e automática no Solo (seção 6, tabela da seção 4 e decisão do Guilherme), a cobrança por PIX, boleto e cartão e o financeiro avançado do Plus em diante, e o FAQ que diz que o JurIA não substitui o contador.

**Dúvidas para a Mobiletec** (já na lista `duvidas` do JSON)
- Lista dos municípios com integração própria. O que dispara a emissão e o que o escritório precisa configurar antes.
- Se dá para emitir NFS-e durante o teste.
- Plano da divisão de honorários, da recuperação de crédito e das parcerias. Por quais canais a régua de cobrança envia.
- Se existe honorário de êxito. Qual é a conta de pagamentos e se há taxa por transação.
- Se plano de contas, contas bancárias e recibos entram no Solo.
- Revisão por contador das respostas sobre obrigação de emitir nota e sobre sucumbência.

### gestao-de-processos-e-prazos.json

**Mudanças**
- `descricao`: tirei "todo dia". Frequência não entra como promessa (8.9), e o próprio rascunho tinha a dúvida sobre o Solo.
- Seção "Como saber quando um processo teve movimentação nova?": reescrita, com o selo "Por créditos". O texto antigo prometia atualização automática grátis e deixava o monitoramento como extra pago. O `planos-e-creditos.md` 5.2 diz o contrário: "o acompanhamento automático é pago" (💳 na seção 2). Agora a atualização automática aparece pelo monitoramento.
- Seção do cálculo de prazo: "O JurIA faz essa contagem", logo depois de explicar as regras de publicação do art. 224, virou "O JurIA conta o prazo em dias úteis, com os feriados forenses nacionais e estaduais". A fonte (8.2) não diz que o sistema aplica a regra da disponibilização. Também tirei "conferir dia a dia", porque a fonte diz só "memória de cálculo".
- FAQ de feriado: a pergunta "Feriado municipal ou estadual conta no prazo?" virou "Feriado conta no prazo processual?", e a resposta deixou de citar feriado municipal, que é proibido. Tirei também o "dia a dia" da memória de cálculo.
- Atualizei o `todo` da seção de movimentações e uma dúvida, que ainda falavam do texto antigo.
- Mantidos com lastro: DJe, PJe e DJEN no Solo (seção 2), 1 OAB no Solo e ilimitadas do Plus em diante, os limites de processos (70/500/2.000/ilimitado), a importação por OAB por créditos e os 50 créditos grátis, o FAQ de monitoramento (cópia literal de `paginas.ts`) e o aviso CNJ 615/2025.

**Dúvidas para a Mobiletec** (já na lista `duvidas` do JSON)
- Se a atualização automática da 8.1 é o monitoramento por créditos da seção 2, ou outra função. Frequência no Solo.
- Se a leitura diária de publicações vale no Solo.
- Plano e créditos do resumo da intimação por IA.
- Plano das funções que só estão na seção 8: prazo fatal e interno, confirmação por link, Teams, importação em lote, vínculos e restauração.
- O conflito sobre importação: se a planilha é grátis e se a primeira importação por OAB é gratuita ou custa 21 créditos.
- Se o cálculo cobre suspensão local de expediente e ritos em dias corridos. Sincronização com o Outlook. A antecedência dos alertas.
- Revisão jurídica dos arts. 219 e 224 do CPC e da explicação do DJEN.

---

## Lote 2

### ia-para-advogados.json

**Mudanças**
- Seção "O advogado pode usar IA para fazer petição?": tirei a "Recomendação 001/2024 do Conselho Federal da OAB" e o que ela diria. É número de norma da OAB não confirmado, e isso é proibido. O título perdeu "O que diz a OAB?", porque a resposta deixou de responder isso. Deixei um `todo` pedindo revisão jurídica.
- Destaque "Petições por seção": "modelo do escritório preenchido sozinho. Entra no teto de gerações" virou "modelo preenchido com os dados do caso. A geração por IA entra no teto mensal". Nenhuma fonte diz que preencher um modelo consome geração. Só a geração por IA consome (seção 4).
- Seção do resumo da intimação: separei a sugestão da IA do cálculo automático de prazos. O texto antigo dizia que o prazo sugerido pela IA segue a contagem em dias úteis, ligação que a fonte (8.2) não faz.
- FAQ "Qual a melhor IA para advogados?": "O JurIA foi feito nessa lógica" virou "No JurIA, a IA fica dentro do sistema". A frase antiga dizia que o JurIA cumpre os três critérios, inclusive "mostra de onde tirou a informação", e o link para a fonte ainda é dúvida.
- Mantidos com lastro: os tetos de 20/150/400/1.000, 1 crédito por geração e 2 por petição, chave própria do Plus em diante, análise de risco e jurimetria do Plus em diante, transcrição por créditos e o assistente nos quatro planos sem citar "sem limite". As proteções iguais nos quatro planos estão no bloco de segurança de `home.ts`, e o aviso CNJ está presente.
- O "melhor" ficou só na pergunta do FAQ, que é termo de busca. A resposta não diz que o JurIA é o melhor.

**Dúvidas para a Mobiletec** (já na lista `duvidas` do JSON)
- Plano e créditos do resumo da intimação, e se ele é o "Resumo curto/completo" do catálogo, que custa 3 ou 8 créditos sempre.
- Plano da leitura de documentos. Preço da transcrição em créditos.
- Se os dados do escritório treinam a IA, inclusive com chave própria.
- Se cada precedente traz link para a fonte. A escala de 0 a 100 da análise de risco.
- Novo: a orientação do CFOAB sobre IA, conferida na fonte, antes de a página citar.

### jurimetria.json

**Mudanças**
- Seção "Em que planos a jurimetria está disponível?": a lista do que o Solo cobre ganhou "a Jú no WhatsApp". Com a Jú, o Solo tem cinco recursos desde 05/10 (`planos-e-creditos.md` 4.1, e `faq.ts` já corrigido). ⚠️ **A mesma frase desatualizada, com quatro recursos, continua em `juria-site-astro/src/data/paginas.ts`** (slug `jurimetria`). Não editei: fica para o orquestrador.
- FAQ "jurimetria e pesquisa de jurisprudência": acrescentei o limite de 100 buscas por mês no Solo (seção 5). "Nos quatro planos" sem o limite dava a entender uso livre no Solo.
- Créditos conferidos: 8 a jurimetria rápida e 29 a completa, 50 créditos grátis, cache. Batem com `planos-e-creditos.md` 3.3 e com `paginas.ts`. "Fatores explicáveis e recomendações de ação" tem lastro em `home.ts` e `faq.ts`. Nada de "por juiz" ou "por vara". Aviso CNJ presente.

**Dúvidas para a Mobiletec** (já na lista `duvidas` do JSON)
- A fonte exata dos dados. O que a completa traz a mais que a rápida.
- Se a análise de risco consome créditos ou gerações. A escala de 0 a 100.
- Se os créditos do teste são os 50 do cadastro.

### due-diligence-juridica.json

**Mudanças**
- Destaque "Custo antes de consultar": acrescentei que a prévia custa 4 créditos. Com selo "Por créditos" e "é abatida", o cartão dava a entender que a prévia era grátis.
- Créditos conferidos: dossiê rápido 21, completo 35, mais 3 por bloco de 200 acima dos 200 primeiros, prévia 4 abatida. Batem com `planos-e-creditos.md` 3.3 e com `paginas.ts`. Os selos "Do Plus em diante" têm lastro (⛔ na seção 5 e na tabela da seção 4).
- Sem aviso CNJ, de propósito: a página não chama a due diligence de IA. O FAQ da home chama, e isso está nas dúvidas.

**Dúvidas para a Mobiletec** (já na lista `duvidas` do JSON)
- Como as quatro frentes de análise se relacionam com os dossiês rápido, completo e de crédito. Se o custo é igual para CPF e CNPJ.
- Se a due diligence usa IA (define o aviso CNJ). O prazo de entrega. Se inclui a Justiça do Trabalho. A fonte da análise reputacional.

### pesquisa-juridica.json

**Mudanças**
- Destaque "Jurisprudência ligada ao caso": acrescentei o limite de 100 buscas por mês no Solo. Com `plano: null`, o cartão prometia uso livre nos quatro planos.
- Seção de consultas patrimoniais: o título "Como fazer consulta patrimonial por CPF ou CNPJ?" virou "Que consultas patrimoniais dá para fazer no JurIA?". A chave de busca não está confirmada, e o próprio rascunho já tinha essa dúvida. O termo de SEO volta quando a Mobiletec confirmar. Acrescentei ao `todo` a revisão jurídica da frase sobre SISBAJUD, RENAJUD, SNIPER e CNIB.
- FAQ dos créditos: "Créditos entram só onde há consulta a fonte externa paga" virou "Fora a IA acima do teto mensal, créditos entram só onde…". A IA acima do teto e os resumos também consomem crédito (3.3).
- Mantidos com lastro: precedentes, calculadora e CNPJ nos quatro planos (✅ na seção 5), veículos a 23 créditos, pesquisa de jurisprudência e de precedentes sem crédito (3.4). Aviso CNJ presente.

**Dúvidas para a Mobiletec** (já na lista `duvidas` do JSON)
- Plano de imóveis e da lista de devedores da União. Chave de busca da consulta patrimonial. O que são "consulta assistida" e "roteiro manual".
- Plano e créditos do previdenciário. Se as decisões trazem link para a fonte. O limite de buscas do Plus para cima.

### software-juridico.json

**Mudanças**
- `lede`: "com o plano em que ela está" virou "com o plano em que ela está quando ele já é confirmado". Metade da lista é da seção 8, sem plano.
- Processos, resposta e item: "as movimentações são atualizadas automaticamente" virou o monitoramento de processos, por créditos. O texto antigo prometia atualização automática sem custo, e `planos-e-creditos.md` 5.2 diz que "o acompanhamento automático é pago". Fica coerente com a página de gestão.
- Processos, item da importação em lote, e seção de migração: tirei "por planilha, não consome créditos". Há conflito de fonte: `planos-e-creditos.md` 3.4 diz que é grátis, e `funcionalidades.md` seção 2 diz que no Solo só o cadastro manual é livre. A fonte de mais autoridade contradiz.
- Prazos: "Captura diária de publicações" virou "Captura de publicações". Frequência não entra como promessa (8.9).
- Atendimento: o item "Caixa de entrada compartilhada, com respostas rápidas e modelos. Nos quatro planos" virou dois. "WhatsApp do escritório dentro do sistema. Nos quatro planos" tem lastro na seção 3 e na 3.2. "Caixa compartilhada, com respostas rápidas, modelos e histórico" fica sem selo, porque a 8.8 lista a caixa como função nova sem plano.
- Atendimento: tirei o selo "Do Plus em diante" do envio de documentos pelo cliente. Separei a conversão de oportunidade do funil e deixei a conversão sem selo. Nos dois casos o plano era dedução, não leitura, conforme a nota do orquestrador. O portal e o funil mantêm o selo (⛔).
- `duvidas`: tirei a dúvida do ✓ da Jú, confirmado em `funcionalidades.ts` (true nos quatro planos). Reescrevi a dúvida do envio e da conversão, e acrescentei o conflito da importação por planilha.
- Mantidos com lastro: os preços e limites dos quatro planos, os nove recursos do Solo para o Plus, a migração assistida grátis no Max, "sem taxa de ativação" e "não há cobrança automática" (`home.ts` e `faq.ts`), "9 integrações", com o Domicílio sempre "em ativação", e a NFS-e no Solo. Aviso CNJ presente. As 10 seções foram aceitas pelo orquestrador.
- O "melhor" ficou só na pergunta do FAQ, que é termo de busca. A resposta não faz autoelogio.

**Dúvidas para a Mobiletec** (já na lista `duvidas` do JSON)
- Plano de todas as funções que só aparecem na seção 8 (lista no JSON). Envio de documentos, conversão e caixa compartilhada entram nela.
- Se a atualização automática é o monitoramento por créditos. A frequência no Solo.
- O conflito da importação por planilha. Se "Desempenho e relatórios" é a função ⛔ "Relatórios, contabilidade e auditoria".
- A migração assistida na prática. Convênio com a OAB. O plano do SEEU e do eproc.
