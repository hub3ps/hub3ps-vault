---
tipo: arquivo
cliente: juria
atualizado: 2026-11-27
autor: claude
origem: agencia_marketing, clients/juria/rascunhos-paginas/00-seo.md (migrado em 27/11/2026)
---
# SEO das páginas de produto do JurIA

> Pesquisa feita em 14/10/2026 para o site em Astro (`juria-site-astro/`).
> Método: autocomplete do Google (pt-BR, gl=br) consultado via
> `suggestqueries.google.com`, mais leitura das SERPs e dos concorrentes diretos
> (Astrea/Aurum, ADVBox, Projuris, EasyJur) e de quem ranqueia no tema.
>
> **Volume de busca:** nenhum termo abaixo tem número. Sem dado de volume; sinal =
> autocomplete/SERP. "Forte" quer dizer que o Google completa o termo com várias
> variações comerciais (sistema, software, melhor, para advogados). "Fraco" quer
> dizer que o autocomplete devolve só o próprio termo ou nada.
>
> Regras aplicadas: title até 60 caracteres terminando em " | JurIA"; meta
> description entre 120 e 155 caracteres, sem preço nem plano; H1 sem marca.
> As contagens estão ao lado de cada item.

## Resumo das decisões

| Página | URL | Mudou? |
|---|---|---|
| Atendimento e WhatsApp | `/whatsapp-para-advogados` | Confirmada. Title e H1 novos |
| Inteligência artificial | `/ia-para-advogados` | Mantida. Title atual tem 72 caracteres e precisa encurtar |
| Financeiro e nota fiscal | `/financeiro-para-escritorio-de-advocacia` | **Nova** (substitui a provisória `/financeiro-e-nota-fiscal`) |
| Processos e prazos | `/gestao-de-processos-e-prazos` | Mantida. Termo principal passa a ser "controle de prazos processuais" |
| Pesquisa (hub) | `/pesquisa-juridica` | **Nova** (substitui a provisória `/pesquisa-e-jurimetria`) |
| Jurimetria | `/jurimetria` | Mantida |
| Due diligence | `/due-diligence-juridica` | Mantida |
| Tudo o que o JurIA faz | `/software-juridico` | Mantida. Meta atual cita preço e precisa trocar |

Se as URLs provisórias já estiverem linkadas no site, vale redirecionar 301
para as novas.

---

## 1. Atendimento e WhatsApp

**Termo principal:** whatsapp para advogados

**Termos secundários:**
- chatbot whatsapp para advogados
- ia whatsapp para advogados / ia para whatsapp escritório de advocacia
- atendimento whatsapp para advogados / ia para atendimento escritório de advocacia
- sistema de atendimento whatsapp para escritório de advocacia
- crm whatsapp para advogados
- secretária virtual para advogados

**Sinal:** forte. "whatsapp para advogados" completa com chatbot, crm,
whatsapp business, automação, ia, atendimento e sistema. "ia para escritório de
advocacia" completa com "ia para atendimento" e "ia para whatsapp". "secretária
virtual para advogados" e "assistente virtual para advogados" aparecem, mas sem
variações (fraco). A SERP é ocupada por blogs de plataformas de mensageria
(Digisac, SleekFlow) e pelo Projuris ADV; nenhum software jurídico domina.

**URL:** `/whatsapp-para-advogados`

**Title (53):** `WhatsApp para advogados com IA no atendimento | JurIA`

**H1:** WhatsApp para advogados, com secretária virtual de IA

**Meta description (152):** Secretária virtual com IA atende seus clientes no WhatsApp e passa a conversa para a equipe. Caixa compartilhada, lembretes e cobranças no mesmo número.

**Perguntas que a página deve responder:**
1. Como usar o WhatsApp no escritório de advocacia sem perder mensagem de cliente?
2. Chatbot de WhatsApp para advogados funciona? O que ele responde e quando passa para um humano?
3. A OAB permite usar IA ou chatbot para atender clientes no WhatsApp? (Provimento 205/2021 e Recomendação 001/2024 do CFOAB: atender quem já procurou o escritório, sem captação ativa, e sem a IA dar orientação jurídica sem supervisão)
4. Dá para várias pessoas da equipe atenderem o mesmo número de WhatsApp do escritório?
5. Precisa de WhatsApp Business ou da API oficial? Paga por mensagem? (a página tem a resposta: "a JurIA não cobra por mensagem")
6. Como mandar lembrete de audiência e cobrança de honorários pelo WhatsApp automaticamente?
7. O cliente consegue ver o andamento do processo sem ligar para o escritório? (portal do cliente)
8. Como acompanhar os contatos que chegam pelo WhatsApp até virarem contrato? (funil de oportunidades, a dor por trás de "crm whatsapp para advogados")

---

## 2. Inteligência artificial

**Termo principal:** ia para advogados

**Termos secundários:**
- inteligência artificial para advogados
- ia jurídica
- ia para petição inicial / inteligência artificial para advogados petições
- ia para escritório de advocacia
- ia para resumir processos judiciais / ia para análise de processos judiciais
- ia para transcrição de audiência

**Sinal:** forte. "ia para advogados" completa com grátis, curso, "qual a
melhor", teste grátis, oab, claude, criminalistas, previdenciários. "ia
jurídica" completa com gratuita, "qual a melhor", brasileira. "ia para petição"
tem 10 variações. A SERP de "qual a melhor" é dominada por listas de
fornecedores: Jurídico AI (várias URLs), EasyJur ("11 opções") e ADVBox. A
pesquisa não indica URL melhor que a atual, que é exatamente o termo de cabeça.

**URL:** `/ia-para-advogados` (mantida)

**Title (56):** `IA para advogados: petições, intimações e prazos | JurIA`

**H1:** IA para advogados, dentro do sistema do escritório

**Meta description (151):** IA jurídica que resume intimações com prazo sugerido, redige petições por seção, lê documentos e transcreve áudios, ligada aos processos do escritório.

**Perguntas que a página deve responder:**
1. Qual a melhor IA para advogados? (responder com critério verificável: dados ligados ao processo, fontes conferíveis, sigilo; sem "a melhor")
2. O advogado pode usar inteligência artificial para fazer petição? O que diz a OAB? (Recomendação 001/2024 do CFOAB: supervisão humana, sigilo, informar o cliente)
3. A IA consegue ler e resumir um processo ou uma intimação e dizer qual é o prazo?
4. ChatGPT ou Claude servem para advogado, ou é melhor uma IA jurídica? Qual a diferença?
5. A IA jurídica inventa jurisprudência? Como conferir as citações antes de protocolar?
6. Os dados dos meus clientes ficam seguros? A IA usa meus documentos para treinar?
7. Dá para transcrever audiência ou áudio de cliente com IA?
8. Tem IA para advogados grátis ou com teste grátis?

---

## 3. Financeiro e nota fiscal

**Termo principal:** financeiro para escritório de advocacia

**Termos secundários:**
- sistema financeiro para escritório de advocacia / sistema financeiro para advogados
- controle financeiro escritório de advocacia
- software financeiro para advogados
- nota fiscal para advogados / emissão de nota fiscal para advogados
- sistema de cobrança para escritório de advocacia
- controle de honorários advocatícios

**Sinal e escolha da URL:** as duas candidatas têm autocomplete, mas com
intenção diferente.
- "financeiro escritório de advocacia" completa com controle, sistema,
  software, planilha e BPO: **intenção de ferramenta**, que é o que a página
  vende. "software financeiro para advogados" e "sistema financeiro para
  escritório de advocacia" aparecem também a partir de "software para
  advogados" e "sistema para escritório de advocacia".
- "nota fiscal advogado" completa com autônomo, pessoa física, imposto de
  renda, avulsa, "como emitir", "precisa emitir": **intenção informativa**,
  de quem quer saber a regra. A SERP é de contabilidades (Contabilizei,
  Contmatic) e de artigos sobre NFS-e de honorários de sucumbência.

Decisão: URL pelo termo comercial, e "nota fiscal" no H1, no title (como NFS-e)
e numa seção própria com as perguntas informativas, que é como a página pega as
duas buscas. O Astrea usa `/astrea/gestao-financeira/` e cobre boleto, PIX e
baixa automática, mas a pesquisa não achou emissão de nota fiscal na página
dele: a NFS-e automática é o ângulo que diferencia.

**URL:** `/financeiro-para-escritorio-de-advocacia`

**Title (57):** `Financeiro para escritório de advocacia com NFS-e | JurIA`

**H1:** Financeiro para escritório de advocacia, com nota fiscal automática

**Meta description (150):** Emita NFS-e automaticamente, cobre por PIX, boleto ou cartão com baixa automática e controle honorários e fluxo de caixa do escritório em um só lugar.

**Perguntas que a página deve responder:**
1. Advogado precisa emitir nota fiscal? E a sociedade de advogados? (depende do município para o autônomo; a página explica e manda confirmar com o contador)
2. Como emitir nota fiscal de serviço sendo advogado? (o sistema emite pelo padrão nacional de NFS-e e em municípios com integração própria)
3. Precisa emitir nota fiscal de honorários de sucumbência?
4. Como fazer o controle financeiro de um escritório de advocacia sem planilha?
5. Como cobrar honorários por PIX ou boleto e saber quem já pagou?
6. Como controlar honorários contratuais, de êxito e a divisão entre advogados?
7. Como cobrar um cliente inadimplente do escritório? (recuperação de crédito: carteira de devedores, acordos, régua de cobrança)
8. Como montar o fluxo de caixa de um escritório de advocacia?

Atenção para a copy: o emissor nacional de NFS-e passa a ser obrigatório para
optantes do Simples em 01/11/2026, segundo a Contmatic (fonte comercial, não
conferida na Receita). Se for usar como gancho, conferir antes na fonte oficial.

---

## 4. Processos e prazos

**Termo principal:** controle de prazos processuais

**Termos secundários:**
- gestão de processos jurídicos / software de gestão de processos judiciais
- sistema de controle de prazos processuais
- captura de publicações judiciais / publicações e intimações
- monitoramento de processos judiciais
- calculadora de prazos processuais
- consultar processos pela OAB

**Sinal:** "controle de prazos processuais" é o termo jurídico com autocomplete
mais rico do tema (sistema, programa, app, planilha, grátis). "gestão de
processos" sozinho é genérico e puxa gestão industrial e administrativa, por
isso não serve de termo principal. "calculadora de prazos" completa com
dezenas de tribunais (TJSP, TJRJ, TJBA). "processos pela oab" completa com
"consultar processos pela oab do advogado". "intimações" completa com DJEN,
AASP, OAB. SERP dominada por Projuris, EasyJur e Aurum.

**URL:** `/gestao-de-processos-e-prazos` (mantida: já contém "processos" e
"prazos" e não há motivo forte para trocar)

**Title (48):** `Gestão de processos e controle de prazos | JurIA`

**H1:** Gestão de processos e controle de prazos processuais

**Meta description (149):** Importe processos pela OAB, receba publicações e intimações todo dia e tenha o prazo calculado em dias úteis com feriados forenses, direto na agenda.

**Perguntas que a página deve responder:**
1. Como fazer o controle de prazos processuais sem planilha e sem perder prazo?
2. Como receber publicações e intimações automaticamente pelo número da OAB?
3. O que é o DJEN e como acompanhar as intimações por ele?
4. Como calcular prazo processual em dias úteis, com feriados? (CPC, arts. 219 e 224; a página explica a regra e diz que o sistema mostra a memória de cálculo)
5. Feriado municipal ou estadual conta no prazo? O sistema considera?
6. Como importar todos os meus processos pela OAB de uma vez?
7. Como saber quando um processo teve movimentação nova?
8. Dá para ver os prazos e audiências na agenda do Google ou do Outlook?

Atenção para a copy: o inventário diz "feriados forenses nacionais e
estaduais". Não prometer feriado municipal sem confirmar com a Mobiletec.

---

## 5. Pesquisa (página hub)

**Termo principal:** pesquisa jurídica com IA

**Termos secundários:**
- busca de jurisprudência com IA / jurisprudência com IA
- precedentes judiciais
- consulta patrimonial por CPF / busca de bens do devedor
- calculadora jurídica
- jurimetria (só link para `/jurimetria`)
- due diligence jurídica (só link para `/due-diligence-juridica`)

**Sinal e escolha da URL:** nenhum termo cobre o hub inteiro, então a escolha
é por eliminação.
- "pesquisa e jurimetria" não tem busca, e usar "jurimetria" no hub canibaliza
  a página `/jurimetria`, que já existe para esse termo.
- "pesquisa de jurisprudência" tem autocomplete forte, mas navegacional: as
  sugestões são STJ, TJSP, STF, TST. Quem busca quer o site do tribunal.
- "pesquisa jurídica" tem autocomplete, mas acadêmico (aplicada, dogmática,
  mestrado) e Jusbrasil. "jurisprudência com ia" e "busca de jurisprudência
  com ia" existem e são comerciais.
- "consulta patrimonial por cpf", "busca de bens do devedor" e "calculadora
  jurídica" (online, grátis, trabalhista, por tribunal) têm sinal forte, mas
  cada um é uma função, não o hub.

Decisão: `/pesquisa-juridica`. É curta, descreve o hub, não briga com
`/jurimetria`, e o title e o H1 qualificam com "IA" e "advogados" para fugir do
sentido acadêmico. Sinal fraco para o termo exato; a página vale mais como
distribuidora de autoridade para as duas filhas do que como ranqueadora própria.

**URL:** `/pesquisa-juridica`

**Title (47):** `Pesquisa jurídica com IA para advogados | JurIA`

**H1:** Pesquisa jurídica com IA: jurisprudência, precedentes e patrimônio

**Meta description (153):** Jurisprudência e precedentes de todos os tribunais, jurimetria, due diligence, consultas patrimoniais e calculadora jurídica, ligados aos seus processos.

**Perguntas que a página deve responder:**
1. Como pesquisar jurisprudência com IA de forma confiável? Dá para conferir a fonte no tribunal?
2. Onde encontrar precedentes vinculantes e qualificados dos tribunais sobre o meu tema?
3. Como fazer consulta patrimonial por CPF ou CNPJ? (o JurIA pesquisa bases públicas de imóveis rurais e urbanos, veículos e lista de devedores da União)
4. Como encontrar bens do devedor antes de entrar com a execução?
5. Existe calculadora jurídica online com índices oficiais e cálculo trabalhista?
6. O que é jurimetria e quando vale usar? (resposta curta e link para `/jurimetria`)
7. O que é due diligence jurídica? (resposta curta e link para `/due-diligence-juridica`)

Atenção para a copy: SISBAJUD, RENAJUD, SNIPER e CNIB aparecem muito nas
buscas sobre bens do devedor, mas dependem de ordem judicial. O JurIA consulta
bases públicas; não sugerir que ele substitui essas ferramentas.

### 5a. `/jurimetria` (URL mantida)

**Termo principal:** jurimetria

**Termos secundários:** jurimetria o que é, o que é jurimetria no direito,
jurimetria software, jurimetria ia, jurimetria preditiva, análise de risco
processual

**Sinal:** forte para o termo, com mistura de intenção. "jurimetria" completa
com "o que é", CNJ, curso, FGV, software, "software gratuito" e IA. SERP com
Thomson Reuters, Projuris, Turivius e EasyJur, todos com guia "o que é" e
"como escolher software".

**Title (46):** `Jurimetria por tipo de ação e tribunal | JurIA`

**H1:** Jurimetria por tipo de ação e tribunal (mantido)

**Meta description (146):** Dados estatísticos de decisões por tipo de ação e tribunal para avaliar o risco do caso, definir estratégia e conversar com o cliente com números.

**Perguntas:**
1. O que é jurimetria no direito?
2. Para que serve a jurimetria na advocacia?
3. Como usar jurimetria para avaliar o risco de um caso antes de aceitar?
4. Jurimetria preditiva consegue prever o resultado de um processo?
5. De onde vêm os dados de um software de jurimetria?
6. Qual a diferença entre jurimetria e pesquisa de jurisprudência?

Atenção: o recorte do JurIA é **por tipo de ação e tribunal**. As SERPs falam
em "histórico do juiz" e "por julgador"; não usar.

### 5b. `/due-diligence-juridica` (URL mantida)

**Termo principal:** due diligence jurídica

**Termos secundários:** due diligence jurídica o que significa, parecer de due
diligence jurídica, due diligence de empresas, diligência prévia, análise de
risco de contraparte

**Sinal:** médio. O autocomplete devolve só "o que significa" e "parecer de
due diligence jurídica". SERP com Turivius, Thomson Reuters, Jurídico AI e
Judit, em formato guia com etapas.

**Title (46):** `Due diligence jurídica por CPF ou CNPJ | JurIA`

**H1:** Due diligence jurídica por CPF ou CNPJ (mantido)

**Meta description (150):** Diligência prévia de pessoas e empresas com análise societária, fiscal, patrimonial e reputacional, em um dossiê para decidir antes de fechar negócio.

**Perguntas:**
1. O que é due diligence jurídica e o que significa?
2. Quando fazer due diligence: compra de empresa, contrato, imóvel, novo cliente?
3. Quais são as etapas de uma due diligence jurídica?
4. O que é analisado: societário, fiscal, trabalhista, processos, patrimônio?
5. O que deve ter num parecer de due diligence jurídica?
6. Quanto tempo leva uma due diligence?
7. Dá para fazer due diligence de pessoa física, pelo CPF?

---

## 6. Tudo o que o JurIA faz

**Termo principal:** software jurídico

**Termos secundários:**
- software para advogados / sistema para advogados
- sistema para escritório de advocacia
- software jurídico com IA
- melhor software jurídico
- software jurídico para advogado autônomo
- software jurídico gratuito OAB

**Sinal:** o mais forte de todos. "software jurídico" completa com gratuito
OAB (e por seccional: PR, SP, MG, RJ, RS), de gestão, para advogado autônomo,
mais usados, exemplos. "software para advogados" traz "astrea software para
advogados" já na sugestão. "melhor software jurídico" completa com 2025 e
2026. SERP de comparativos de fornecedor (EasyJur "Melhores softwares jurídicos
2026", ADVBox "7 melhores") e B2B Stack.

**URL:** `/software-juridico` (mantida)

**Title (49):** `Software jurídico com IA para escritórios | JurIA`

**H1:** Software jurídico com IA, função por função

**Meta description (150):** Processos, prazos, publicações, WhatsApp, financeiro com NFS-e, pesquisa e IA jurídica: veja cada função do JurIA e com quais sistemas ele se integra.

**Perguntas que a página deve responder:**
1. O que é um software jurídico e o que ele faz?
2. Qual o melhor software jurídico para escritório de advocacia? (critérios, sem superlativo)
3. Qual software jurídico para advogado autônomo?
4. Existe software jurídico gratuito? Tem convênio com a OAB? (responder com fato: o que o JurIA oferece de teste, sem prometer gratuidade)
5. Quais as funcionalidades de um software jurídico completo?
6. Quanto custa um software jurídico? (a resposta pode estar no corpo; a meta não cita preço)
7. Como migrar de outro sistema, como Astrea, ADVBox ou Projuris?
8. Software jurídico na nuvem é seguro? Atende a LGPD?

Atenção para a copy: a meta atual da página cita preço e dias de teste. Pela
regra deste trabalho, troca pela de cima. O H1 evita "todas as
funcionalidades", que a trava do `conferir-dados.mjs` barra.

---

## Fontes

Autocomplete (consultado em 14/10/2026, `hl=pt-BR`, `gl=br`):
`https://suggestqueries.google.com/complete/search?client=firefox&q=<termo>`

SERP e concorrentes:
- [Digisac: chatbot WhatsApp para advogados](https://digisac.com.br/blog/chatbot-whatsapp-para-advogados)
- [SleekFlow: solução de atendimento para advogados](https://sleekflow.io/pt-br/blog/solucao-de-atendimento-para-advogados-e-escritorios-de-advocacia)
- [Projuris: autoatendimento via WhatsApp](https://www.projuris.com.br/blog/autoatendimento-via-whatsapp/)
- [Estado de Minas: IA no WhatsApp muda o atendimento na advocacia](https://www.em.com.br/mundo-corporativo/2026/07/7469453-ia-no-whatsapp-muda-o-atendimento-na-advocacia.html)
- [MacMagazine: Meta libera chatbots de IA no WhatsApp no Brasil](https://macmagazine.com.br/post/2026/01/15/meta-abre-excecao-e-libera-chatbots-de-ia-para-o-whatsapp-no-brasil/)
- [ADVBox: melhor inteligência artificial para advogados](https://advbox.com.br/blog/melhor-inteligencia-artificial-para-advogados/)
- [EasyJur: melhores IA para advogados](https://easyjur.com/blog/melhores-ia-para-advogados/)
- [Jurídico AI: qual a melhor IA para advogados](https://juridico.ai/direito-digital/qual-melhor-ia-para-advogados/)
- [Cálculo Jurídico: gerador de petições com IA e normas da OAB](https://calculojuridico.com.br/gerador-peticoes-ia-oab/)
- [Modelo Inicial: recomendações da OAB no uso da IA](https://modeloinicial.com.br/artigos/oab-recomendacoes-uso-ia)
- [IAB: uso ético da IA na prática jurídica (PDF)](https://iabnacional.org.br/wp-content/uploads/2025/10/Uso-etico-da-IA-na-pratica-juridica-Ana-Amelia-Menna-Barreto.pdf)
- [Aurum: Astrea gestão financeira](https://www.aurum.com.br/astrea/gestao-financeira/)
- [Asaas: gestão financeira em escritório de advocacia](https://blog.asaas.com/gestao-financeira-em-escritorio-de-advocacia/amp/)
- [Contabilizei: nota fiscal para advogados](https://www.contabilizei.com.br/contabilidade-online/nota-fiscal-para-advogados/)
- [Contmatic: advogado emite nota fiscal?](https://simplifique.contmatic.com.br/blogs/advogado-emite-nota-fiscal)
- [Contmatic: contabilidade para advogados e NFS-e 2026](https://simplifique.contmatic.com.br/blogs/contabilidade-para-advogados-guia-completo-tributacao-nfse-2026)
- [Ozai: honorários de sucumbência, nota fiscal e tributos](https://www.ozai.com.br/honorarios-de-sucumbencia-nota-fiscal-e-tributos-retidos-na-fonte)
- [Projuris: software jurídico e prazos processuais](https://www.projuris.com.br/blog/software-juridico-prazos-processuais/)
- [EasyJur: controle de prazos processuais](https://easyjur.com/blog/controle-prazos-processuais/)
- [Projuris: contagem de prazos processuais no CPC](https://www.projuris.com.br/blog/contagem-prazos-processuais/)
- [Projuris: DJEN, o que é e como contar prazos](https://www.projuris.com.br/blog/djen/)
- [OAB-PI: cartilha das novas intimações pelo DJEN (PDF)](https://www.oabpi.org.br/wp-content/uploads/2025/06/CARTILHA-NOVAS-INTIMACOES-DJEN-1.pdf)
- [Thomson Reuters: como escolher software de jurimetria](https://www.thomsonreuters.com.br/pt/juridico/blog/como-escolher-software-jurimetria-escritorio.html)
- [Projuris: software de jurimetria](https://www.projuris.com.br/blog/software-de-jurimetria/)
- [EasyJur: jurimetria](https://easyjur.com/blog/jurimetria/)
- [Turivius: due diligence na advocacia](https://turivius.com/portal/due-diligence-na-advocacia/)
- [Thomson Reuters: o que é due diligence](https://www.thomsonreuters.com.br/pt/juridico/blog/o-que-e-due-diligence.html)
- [Jurídico AI: como buscar jurisprudência com IA](https://juridico.ai/direito-civil/como-buscar-jurisprudencia-ia/)
- [Migalhas: busca de bens do devedor](https://www.migalhas.com.br/depeso/372090/busca-de-bens-do-devedor)
- [EasyJur: melhores softwares jurídicos 2026](https://easyjur.com/blog/melhores-softwares-juridicos-comparativo/)
- [ADVBox: 7 melhores softwares jurídicos](https://advbox.com.br/blog/o-melhor-software-juridico/)
- [B2B Stack: gestão de casos jurídicos](https://www.b2bstack.com.br/categoria/gestao-casos-juridicos)

Fatos de produto conferidos em `clients/juria/comercial/funcionalidades.md`
(seção 8) e estrutura em `clients/juria/ESTRUTURA-site.md`.
