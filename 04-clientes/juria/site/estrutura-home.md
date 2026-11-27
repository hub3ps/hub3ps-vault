---
tipo: cliente-doc
cliente: juria
atualizado: 2026-11-27
autor: claude
origem: agencia_marketing, clients/juria/ESTRUTURA-home.md (migrado em 27/11/2026)
---
# Estrutura da home do JurIA

> **Para quem:** Guilherme, e quem for escrever a copy depois.
> **Decidida em:** 30/09/2026, a partir da
> [[04-clientes/juria/analises/2026-09-30-analise-advbox-copy|análise da ADVBox]].
>
> **Ordem do trabalho, combinada:** estrutura → copy → design. Este documento
> fecha a primeira etapa. Nenhuma copy nova é escrita aqui: só o que cada bloco
> precisa fazer.

---

## A sequência

| # | Bloco | O trabalho que ele faz | Estado |
|---|---|---|---|
| 1 | Hero | Promessa e primeiro CTA | existe, revisar |
| 2 | Autoridade Mobiletec | Responde "quem são vocês?" antes de pedir leitura | **sobe da 6** |
| 3 | Problemas | Dor que o leitor reconhece como dele | existe, **reescrever** |
| 4 | O que muda | Traduz a dor em consequência, antes e depois | **novo** |
| 5 | **Tour da plataforma** (o mockup) | Prova que o produto existe e é bom | existe, **ganhou o nome** |
| 6 | Inteligência | O que nos separa do concorrente | **sobe da 5, e cresce** |
| 7 | **Funcionalidades** | Amplitude: dá para largar as outras ferramentas | existe, **renomeado, 2 colunas** |
| 8 | Prova social | Alguém como eu já usa | ⏸️ **em standby** |
| 9 | Preços | A oferta | existe |
| 10 | Segurança e confiança | Responde "é seguro?" e "qual a pegadinha?" | **novo, com peça existente** |
| 11 | FAQ | Tira o último freio antes de assinar | existe, **trocar perguntas** |
| 12 | CTA final | Fecho | existe |

---

## Por que cada mudança

### O nome "Tour" foi para o bloco 5, que é o tour de verdade

Até 30/09 o bloco 7 se chamava "Tour da plataforma" e era uma lista de 27
itens. O mockup navegável, que é literalmente um tour, não tinha nome nenhum.

O nome trocou de dono. O bloco 5 virou **Tour da plataforma** e o 7 virou
**Funcionalidades**, que é o que ele é.

⚠️ A classe CSS do bloco 7 continua `.tour` e a âncora continua `#recursos`. A
classe vem do CSS portado byte a byte de produção, e a âncora é destino de link
em anúncio rodando agora. Nenhuma das duas pode mudar de nome junto.

### O bloco 2 deixou de ser número de tração

A ADVBox abre com "+5.000 escritórios" e "+1 Bilhão em honorários cobrados".
Não temos equivalente, porque o JurIA acabou de entrar no mercado, e número de
tração não se inventa.

**A autoridade da Mobiletec ocupa esse lugar.** É a única prova social real que
temos hoje: uma software house operando desde 1999, com sistemas críticos em
produção para empresas e órgãos públicos. Não é o mesmo argumento, mas responde
a mesma pergunta, que é "por que eu deveria continuar lendo".

⚠️ **Falta o que torna esse bloco forte: nome.** "Sistemas críticos para
empresas e órgãos públicos" é genérico. Uma lista de clientes ou sistemas que a
Mobiletec pode citar transforma o bloco.

**A esteira de logos já está construída** e fecha o bloco 2. São empresas
grandes e conhecidas, então a logo faz o trabalho sozinha, sem precisar de
texto. Ela roda automática, pausa quando o mouse encosta, e fica parada para
quem pede menos movimento.

Enquanto `autoridade.logos.itens` estiver vazio, **a esteira não renderiza** e
no lugar dela aparece o `{{ TODO }}`, visível de propósito. Subir os arquivos em
`public/logos/` e preencher a lista é tudo que falta. ⚠️ Não preencher com logo
de mentira, nem para ver como fica.

### Autoridade e segurança se separaram

Os dois vieram juntos na mesma decisão, mas fazem trabalhos diferentes e por
isso ficam em pontas opostas da página:

- **Autoridade vai para o topo, bloco 2.** A pergunta "quem está por trás
  disso?" nasce antes da leitura. Respondida cedo, ela destrava o resto.
- **Segurança vai depois do preço, bloco 10.** A pergunta "é seguro guardar
  processo de cliente aqui?" nasce quando a pessoa já se imagina usando. E
  junto dela nasce a outra, que só existe porque somos baratos: **"por que R$ 69
  se a ADVBox cobra R$ 220 mais taxa de ativação?"**

O bloco 10 responde as duas de uma vez, com fato verificável: LGPD, MFA TOTP,
RLS multi-tenant, auditoria em 14 tabelas, backup diário, cloud certificada. E
mais duas frases que são vantagem nossa e a copy atual não usa: **sem taxa de
ativação** e **sem fidelidade**.

### O bloco 3 vira dor de verdade

Hoje os três títulos do bloco Problemas são capacidades, não problemas:

| Título de hoje | O que ele é |
|---|---|
| "De 5 ferramentas para uma" | solução |
| "Risco e precedentes na velocidade da IA" | solução |
| "Dashboard executivo do escritório" | solução |

A dor existe, mas está enterrada no corpo do texto. O bloco se chama Problemas
e não mostra problema nenhum no lugar que as pessoas leem, que é o título.

### O bloco 4 é o único realmente novo

**Formato: antes e depois, lado a lado.** A coluna da esquerda é a rotina de
hoje, a da direita é a mesma rotina com o JurIA.

É o equivalente ao molde "Isso significa" da ADVBox, que eles repetem três
vezes, mas mais concreto: em vez de prometer "mais tempo para estratégia", que
é abstrato, mostra a cena. E aproveita a dor que o bloco 3 acabou de nomear, em
vez de repeti-la.

É **o bloco que mais muda a página**, e não depende de ninguém para ser escrito.

### A duplicata entre Tour e Inteligência acabou

Quatro coisas apareciam duas vezes na mesma página: análise de risco,
precedentes STF/STJ, due diligence e geração de petições estavam na coluna
"Inteligência" do Tour **e** no bloco Inteligência.

- A coluna sai do Tour, que fica com **Operação (12) e Financeiro (8)**.
- Os 7 itens de IA passam a viver só no bloco 6, que sobe e ganha espaço para
  explicar cada um.

A página continua com 27 itens. Nenhum repetido.

### A Inteligência sobe

É o que mais nos separa da ADVBox. Eles vendem IA como duas assistentes com nome
próprio, Donna e Justine, e dedicam um bloco inteiro a isso. Nossa IA estava
espremida entre o Tour e o bloco da Mobiletec.

### O FAQ troca de assunto

Hoje são 5 perguntas, quatro conceituais: o que é, como funciona a IA, para quem
serve, é seguro. O FAQ da ADVBox tem 11, e quase todas comerciais: fidelidade,
taxa de ativação, forma de pagamento, e se eu crescer, e se eu passar do limite.

As perguntas conceituais já são respondidas pelo resto da página. **As
comerciais não são respondidas em lugar nenhum**, e são as que travam a
assinatura.

---

## O que está bloqueado, e por quê

| # | Onde | O que falta | De quem |
|---|---|---|---|
| 2 | Esteira de logos | Os arquivos e a lista. A esteira já roda | Mobiletec |
| 8 | Prova social | Escritórios que aceitem depoimento com nome, e um caso com antes e depois | Mobiletec |

**Fechados em 30/09/2026, pelo Guilherme:**

- **Não existe taxa de ativação.** Era leitura de ausência e virou fato
  confirmado. A frase fica no hero, na nota de preços, no bloco 10 e no FAQ.
- **O que acontece ao atingir o limite**, que era o buraco do FAQ: volume
  (usuários, clientes, processos, armazenamento) resolve subindo de plano, e o
  teto de IA resolve comprando crédito, sem trocar de plano. Do Plus em diante
  ainda dá para conectar a própria chave e usar sem teto.
- **`JURIA` em caixa alta está liberado**, desde que a logo continue `JurIA`.
  Ela já é `Jur<span class="ai">IA</span>` e não tem `text-transform`, então
  nada a fazer.

**O bloco 8 está em standby**, por decisão do Guilherme em 30/09: não temos
nenhum depoimento e a coleta dos primeiros vai levar um tempo. Ele não existe na
página, e não existe versão provisória de depoimento. Quando houver, o lugar é
entre o bloco 7 e os preços. Seis bons bastam.

Tudo o que não está nesta tabela pode ser feito agora.

---

## O que não muda, e por que vale registrar

**O preço continua na home.** A ADVBox esconde e manda para `/planos`, o que faz
sentido para quem começa em R$ 220 mais taxa de ativação. Começando em R$ 69 sem
taxa, o preço é argumento. Mostrar é vantagem.

**O mockup navegável continua.** Eles têm print estático. É a única parte da
nossa home que já ganha da deles hoje.

**A tabela comparativa continua com 23 linhas.** A deles tem mais de 90, em 9
seções, e é ilegível.

---

## Estado

**Estrutura: fechada.** **Copy: escrita, blocos 1 a 12.** **Design: em
lapidação**, duas rodadas em 30/09/2026.

### Design, rodada 2: o site para de ficar amarrado bloco a bloco

Pedido do Guilherme: o site "tem que fluir e não ficar tão amarrado bloco por
bloco", sem eyebrow nomeando o óbvio, e com animações mais simples que as da
Phenomenon Studio, mas que deixem a página mais atraente.

**O que deixava a página amarrada tinha medida:** cada bloco com fundo próprio,
e toda troca de fundo desenhava uma linha reta de ponta a ponta. Doze blocos,
onze cortes. Agora:

- **Um canvas claro contínuo.** Os blocos claros ficaram transparentes sobre
  ele, e duas manchas de cor muito fracas, presas à janela, atravessam todos
  eles enquanto a pessoa rola.
- **As zonas escuras viraram cápsulas**, com margem e canto arredondado,
  flutuando sobre o canvas. Duas escuras seguidas se fundem numa cápsula só:
  hero com autoridade, tour com inteligência, e o CTA. O ritmo aprovado de
  claro e escuro continua igual; só a fronteira mudou.
- **Nenhum eyebrow.** O título de cada bloco fala sozinho.
- **Cabeçalhos que não são sempre centralizados.** Título à esquerda com lede à
  direita em Funcionalidades e Segurança; título preso à esquerda com conteúdo
  rolando ao lado em Problemas e FAQ.
- **Cabeçalho em pílula flutuante**, que escurece sozinho sobre as cápsulas.

**Animações**, todas sem biblioteca nova, todas desligadas para quem pede menos
movimento, e a página inteira funciona sem JavaScript:

| O quê | Onde |
|---|---|
| Título subindo palavra por palavra | todo H1 e H2 |
| Quatro avisos de produto flutuando | hero, só no desktop |
| Marca-texto que se desenha sob "num só sistema" | hero |
| Cards que empilham ao rolar | bloco 3, CSS puro |
| Mockup que chega deitado e endireita | bloco 5, preso ao scroll |
| Percurso que se desenha parada por parada | bloco 7 |
| Número que sobe | "25+" do bloco 2 |
| Fio de progresso no topo | página inteira |

**Os avisos do hero são ilustração, com dado que já existe no mockup**: ACME,
contestação, Estrela Logística e R$ 3.800,00 estão todos no markup portado de
produção. Uma conferência automática trava cliente ou valor que não esteja lá.

### Três coisas que quebraram em silêncio no build, e foram consertadas

Todas estavam escritas certo no CSS e saíam erradas, sem erro nenhum. Só
apareceram medindo o estilo calculado no navegador, e cada uma ganhou
conferência para não voltar.

1. **O minificador fundia `animation-timeline` no atalho `animation`**, que o
   Chrome rejeita inteiro. O mockup chegava reto.
2. **`overflow: hidden` na cápsula criava um contêiner de rolagem**, e a
   timeline do mockup ficava presa nele, parada em zero. Virou `overflow: clip`.
3. **O minificador guardava só `-webkit-backdrop-filter`** quando via o par, e
   o Chrome ignora o prefixado. ⚠️ **Isso afetava o cabeçalho das onze páginas
   novas desde a fase 2**, porque o CSS portado de produção escreve o par nessa
   ordem. O site no ar não tem o problema, porque não passa por este build.
   Consertado no item 8 do `ajustes.css`.

O que existe hoje de CSS nos blocos novos, em `src/styles/blocos-novos.css`, é
o mínimo para eles ficarem legíveis e funcionarem no celular. Não é o design.

### Anotado para a fase de design

**`JurIA` vira `JURIA` em toda caixa alta.** Todo eyebrow do site é
`text-transform: uppercase`, e a marca perde o `IA`, que é a única coisa que o
nome tem de próprio. Vale para o site em produção também, não é regressão
daqui. O rótulo das colunas do bloco 4 já saiu do padrão por causa disso, e é a
única exceção até a decisão valer para todos.

---

## Revisão de 14/10/2026, com o documento da Mobiletec

Aprovada pelo Guilherme. Sete mudanças:

1. **Bloco 6B** deixou de ser só da Jú e virou o bloco de **WhatsApp** (`#whatsapp`,
   era `#ju`): secretária virtual para os clientes, caixa da equipe, lembretes e
   cobranças, a Jú para a equipe, "a JurIA não cobra nada por mensagem"
2. **Bloco 4** deixou de repetir o bloco 3 e virou o destaque da **nota fiscal
   automática** ("A nota fiscal sai sozinha."), mantendo o quadro Hoje / Com o
   JurIA. O alerta de mudança de tese foi para o destaque do card 2 dos Problemas
3. **Card 1 dos Problemas:** "Cinco sistemas" virou "Seis", que é o que a lista tem
4. **Bloco 6 (IA):** entraram resumo da intimação, leitura de documentos e
   transcrição; saíram due diligence e busca de jurisprudência. São 8 pontos
5. **Bloco 7B, novo:** integrações oficiais, 9 do Judiciário e 6 de órgãos
   oficiais. O Domicílio Judicial aparece como "em ativação"
6. **FAQ:** duas perguntas novas, WhatsApp e nota fiscal
7. **Hero:** o subtítulo cita atendimento no WhatsApp e nota fiscal, e um selo
   virou "Integrado ao CNJ, ao DJEN e à Receita Federal". Não ficou "15
   integrações" porque uma das 15, o Domicílio, ainda não está ativa

Os blocos 4, 6, 6B e 7B ganharam link para a página da área.


## Desenho novo, 15/10/2026

Referências aprovadas pelo Guilherme: os templates Webild `saas-platform` e
`ai-email-platform`. A estrutura dos blocos não mudou; mudou a pele.

- **Etiqueta em pílula voltou** em todas as seções (a decisão de 30/09 de tirar
  os eyebrows foi revista por ele). Texto em `home.ts`, campo `etiqueta`
- **Botões em pílula** com círculo e seta no hero e no CTA final
- **IA e WhatsApp** em cartões escuros com ícone com brilho. No celular, os da
  IA deitam (ícone ao lado do texto)
- **Segurança** com órbita animada em volta do escudo
- **Preços** com nome, preço e descrição num painel interno e check redondo.
  A linha de Max e Ilimitado passou a ter a mesma largura da de Solo e Plus
- **Integrações** em cartão com painel e ícone; **FAQ** em pílulas de duas
  colunas; **CTA final** dentro de cartão grande com raios de luz
- **Pendente:** a tela do produto que o Guilherme vai mandar entra na moldura
  do bloco do sistema, provisória até o print final
- Tudo para com `prefers-reduced-motion`
