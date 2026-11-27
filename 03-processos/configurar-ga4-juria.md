---
tipo: processo
atualizado: 2026-11-27
autor: claude
origem: agencia_marketing/docs/processos/configurar-ga4-juria.md (migrado em 27/11/2026)
---
# Configurar o GA4 do JurIA para ler o funil

> Caminhos de arquivo e comandos são do repo `agencia_marketing` (`~/Desktop/agencia_marketing`), salvo quando outro repo é citado.

> Propriedade `G-DRF9JD5S5F` · container `GTM-WHQGLTXC` · conta de anúncios
> `1465935581974017`.
>
> **Leia antes:** o catálogo do funil e as armadilhas estão em
> `clients/juria/ferramentas/gerar-eventos.py`,
> que é o documento único de tracking. Este runbook executa o que as pendências
> de GA4 de lá descrevem.

**Rodado em 01/10/2026, etapas 1 a 5.** Falta a 6. O runbook fica porque o
processo se repete: evento novo do produto nasce empurrado ao dataLayer e não
encaminhado, e aí é só somar o nome na RegEx da etapa 3 e registrar a dimensão
da etapa 2.

O ponto de partida, para quem ler isto depois: o produto empurrava **9 eventos**
ao dataLayer e o container encaminhava **1** ao GA4. Os seis passos do meio do
funil não chegavam a lugar nenhum.

Ordem abaixo é a ordem de execução, e ela importa. A etapa 1 é a única que perde
dado de forma irreversível enquanto espera. A etapa 2 vem antes da 3 porque
parâmetro que chega sem dimensão registrada é análise perdida.

| # | Etapa | Onde |
|---|---|---|
| 1 | Retenção de dados para 14 meses | GA4 |
| 2 | Registrar as 8 dimensões personalizadas | GA4 |
| 3 | Encaminhar os 7 eventos do funil | GTM |
| 4 | Trocar os parâmetros mortos da tag do cadastro | GTM |
| 5 | Marcar os 2 eventos principais | GA4 |
| 6 | Montar as duas análises | GA4 |

---

## 1. Retenção de dados para 14 meses

**Administrador > Coleta e modificação de dados > Retenção de dados.**

Trocar "Retenção de dados de eventos" de 2 meses para **14 meses** e salvar.

Por que primeiro: exploração de funil só enxerga o que está retido, e a mudança
**não é retroativa**. Todo dia esperando é mais um dia de janela que encolhe.
14 meses é o teto da versão gratuita.

**Como conferir:** reabrir a tela. Se o seletor voltou para 2 meses, o salvar não
pegou, o que acontece quando a conta não tem permissão de Editor.

---

## 2. Registrar as dimensões personalizadas

**Administrador > Exibição de dados > Definições personalizadas > Criar dimensão
personalizada.** Escopo **Evento** nas oito.

A coluna da direita vai no campo **Descrição**, como está escrita. Descrição de
dimensão é lida meses depois, sem este runbook aberto do lado, então ela diz o
que é o valor, de qual evento vem e quais valores existem. O campo aceita 150
caracteres.

| Nome da dimensão | Parâmetro | Descrição |
|---|---|---|
| Passo do onboarding | `step` | Qual passo do onboarding foi concluído: lawyer, intimations ou portfolio. Vem do onboarding_step_done, que dispara uma vez por passo. |
| Passo pulado | `skipped` | true quando a pessoa clicou em pular, false quando concluiu. Vem do onboarding_step_done. Sem ela, pular conta como concluir. |
| Método de cadastro | `method` | Se a conta nasceu por e-mail ou pelo Google. Vem do signup_account_created e do form_submit_trial. |
| Porte do escritório | `porte` | Porte do escritório informado no cadastro. Vem do signup_office_created. Permite ler o funil por tamanho de escritório. |
| Faixa de processos | `processos` | Volume de processos informado no cadastro. Vem do signup_office_created. Permite ler o funil por tamanho de operação. |
| Plano | `plan` | Plano escolhido no cadastro. Vem do form_submit_trial. Hoje é sempre trial, e muda quando houver mais planos. |
| Caminho do cadastro | `flow` | Qual fluxo gerou o cadastro. Vem do form_submit_trial. Hoje só existe create_office. |
| Página de origem | `landing_page` | Landing page que originou o cadastro. Vem do form_submit_trial, do objeto de atribuição que o produto guarda no navegador. |

O campo do parâmetro aceita um nome que o GA4 ainda não recebeu. É de propósito:
registrar antes de publicar a tag é o certo.

⚠️ **Não descrever uma dimensão por comparação com a de cima** ("mesma leitura,
por volume"). Na tela do GA4 elas ficam em ordem alfabética, não nesta ordem, e
a frase perde o referente.

⚠️ **Parâmetro sem dimensão registrada não aparece em relatório.** Ele chega na
coleta, aparece no DebugView e em Tempo real, e depois desaparece. Relatório e
exploração só leem dimensão registrada, e não há aviso de que falta uma.

**Como conferir:** as oito aparecem na lista com escopo "Evento". O limite da
versão gratuita é 50 dimensões de evento, então sobra folga.

---

## 3. Encaminhar os 7 eventos do funil

Uma tag só, com nome de evento `{{Event}}`. O genérico é a encanação: como o
nome do evento vem da variável, **cada evento chega ao GA4 com o nome próprio** e
aparece separado no relatório, igual se fossem sete tags.

### 3.1 Cinco variáveis de camada de dados

**Variáveis > Definidas pelo usuário > Nova > Variável da camada de dados.**
Versão 2 em todas, sem valor padrão.

```
dl_step        →  step
dl_skipped     →  skipped
dl_method      →  method
dl_porte       →  porte
dl_processos   →  processos
```

### 3.2 Um acionador

**Acionadores > Novo > Evento personalizado.**

| Campo | Valor |
|---|---|
| Nome | `Funil_Cadastro` |
| Nome do evento | a RegEx abaixo |
| Usar correspondência de expressão regular | **marcado** |
| Dispara em | Todos os eventos personalizados |

```
^(signup_started|signup_method_selected|signup_account_created|signup_email_verified|signup_office_created|onboarding_step_done|onboarding_completed)$
```

⚠️ **Manter o `^` e o `$`.** Sem as âncoras, a RegEx casa por pedaço e qualquer
evento futuro que contenha um desses nomes entra sem ninguém pedir.

Evento novo do produto entra somando um nome aqui, sem tag nova.

### 3.3 Uma tag

**Tags > Nova > Google Analytics: evento do GA4.**

| Campo | Valor |
|---|---|
| Nome da tag | `GA4_Funil_Cadastro` |
| ID de medição | a mesma variável constante que a tag do cadastro já usa, não digitar o `G-` na mão |
| Nome do evento | `{{Event}}` |
| Acionador | `Funil_Cadastro` |
| Exceções | `EX - Ambiente de desenvolvimento (inicialização)` **e** `(todos os eventos)` |

Parâmetros do evento:

```
step        {{dl_step}}
skipped     {{dl_skipped}}
method      {{dl_method}}
porte       {{dl_porte}}
processos   {{dl_processos}}
```

Parâmetro cujo evento não traz valor simplesmente não é enviado, então a mesma
tag serve os sete eventos sem sujar nenhum.

⚠️ **As duas exceções de ambiente não vêm de graça.** Tag nova nasce sem elas, e
foi assim que um preview do Vercel mandou evento para produção em 14/09/2026.

Consentimento não precisa de ajuste à mão: a tag de evento do GA4 já verifica
`analytics_storage` por conta própria. Quem precisa declarar é tag de HTML
personalizado, como as do Pixel.

### 3.4 Conferir antes de publicar

No **Visualizar** do GTM, abrir `portal.juria.app.br/register` e percorrer o
cadastro de verdade, até o fim do onboarding. Em cada evento da coluna da
esquerda, confirmar que `GA4_Funil_Cadastro` aparece em **Tags acionadas**, e não
só que o evento apareceu.

⚠️ **Ver o evento no Visualizar não é ver o evento medido.** O evento aparece na
coluna porque chegou ao dataLayer, e é exatamente esse sintoma que esconde a
falta de tag. O que responde é a lista de tags acionadas.

No **DebugView** do GA4, ao mesmo tempo, conferir:

- os sete nomes de evento chegando
- o `onboarding_step_done` chegando **três vezes**, com `step` diferente
- `skipped` aparecendo também quando é `false`, não só quando é `true`

Se `skipped=false` não aparecer, é o GTM descartando o valor booleano falso. O
contorno é pôr `false` como valor padrão da variável.

**Conferência final, sem login, depois de publicar:**

```bash
curl -s "https://www.googletagmanager.com/gtm.js?id=GTM-WHQGLTXC" \
  | grep -c onboarding_step_done
```

Zero significa que a versão foi salva e não enviada. **Salvar não publica.**

---

## 4. Trocar os parâmetros mortos da tag do cadastro

A tag de evento GA4 do cadastro manda `value` e `currency`, e o produto não
empurra nenhum dos dois nesse push: chegam vazios desde sempre. Enquanto isso
`plan`, `flow`, `method` e `landing_page` vêm no evento e são descartados.

Abrir a tag (nome do evento `form_submit_trial`), remover os dois parâmetros e
pôr no lugar:

```
plan          {{dl_plan}}
flow          {{dl_flow}}
method        {{dl_method}}
landing_page  {{dl_landing_page}}
```

As três variáveis novas, `dl_plan`, `dl_flow` e `dl_landing_page`, se criam
como as da etapa 3.1.

**Não renomear o evento para `sign_up`.** Decidido em 01/10/2026: o nome fica
igual no dataLayer, no GTM e no GA4, e a série histórica não quebra. O catálogo
é que estava errado ao dizer `sign_up`.

⚠️ **Esta etapa não se testa com push manual.** O `form_submit_trial` também
aciona a `Pixel_Lead` e a `Ads_Lead`, então um push no console manda um **Lead
falso para a Meta e para o Google Ads**. Lead é o evento que guia a otimização,
entra na contagem que o cliente lê no hub, e um evento sem dado real de pessoa
arranha a nota de correspondência. Como aqui só se troca parâmetro numa tag que
já funciona, publique e confira no próximo cadastro real, em Tempo real no GA4.

Vale para qualquer teste manual: antes de disparar um evento no console, olhe
quais outras tags aquele mesmo evento aciona. Em 01/10/2026 o teste do
`onboarding_completed` mandou uma ativação falsa para a Meta por esse descuido.

---

## 5. Marcar os eventos principais

**Administrador > Exibição de dados > Eventos > Criar evento.** Dois, e só dois:

```
form_submit_trial
onboarding_completed
```

Na caixa que abre, escolher **"Criar com código"**, informar o nome e ligar
"Marcar como evento principal". Esse modo serve para evento que você mesmo
envia, que é o caso: o GTM já publica os dois.

⚠️ **Não usar "Criar sem código".** Ela fabrica um evento NOVO a partir de outro
que já chega, tipicamente por regra de URL. Usar ali criaria uma segunda fonte
para o mesmo nome, convivendo com a que o GTM publica, e cada ativação contaria
duas vezes. O seletor dela só lista eventos já processados, o que também engana:
evento recém-criado não aparece por causa do atraso de processamento, não porque
esteja faltando.

Duas escolhas dentro da caixa:

- **"Não definir um valor de evento principal padrão".** Valor monetário
  inventado não ensina nada ao algoritmo e ainda entraria em dólar, que é o
  padrão do seletor. Valor de verdade só existe no `Purchase`.
- **"Uma vez por evento"**, o recomendado. Cada ativação é uma.

Marcar micro-passo como evento principal faz todo número da propriedade parecer
conversão, e aí nenhum parece. O `purchase` aparece marcado sem ninguém ter
marcado: é padrão do GA4 em propriedade nova, e não prova que o evento chega.

---

## 6. Montar as duas análises

**Analisar.** A seção chamava Explorar, e dentro dela cada peça chamava
exploração. Agora chama **análise detalhada**. É a mesma coisa, só o nome mudou.

A tela tem três painéis: **Variáveis** à esquerda, **Configurações** no meio, o
resultado à direita.

**É UMA análise detalhada com DUAS guias, não duas análises.** O `+` ao lado do
nome da aba cria a guia, e o painel Variáveis é compartilhado entre elas: as
dimensões e métricas se importam uma vez só. O período também é comum, e aqui
isso é vantagem, não limitação: comparar cadastro e onboarding em janelas
diferentes esconde mais do que mostra.

| O quê | Nome |
|---|---|
| Análise detalhada | `Funil de cadastro e onboarding` |
| Guia 1 (seção 6.1) | `Funil do cadastro` |
| Guia 2 (seção 6.2) | `Onde a pessoa trava no onboarding` |

A guia se renomeia na setinha ao lado do nome da aba, que nasce como "Formato
livre 1" ou parecido. Cada guia tem técnica e configurações próprias.

⚠️ **Antes de montar qualquer coisa, importe dimensões e métricas em
Variáveis.** Sem importar ali, elas não existem para arrastar em Configurações,
e a ausência parece erro de medição quando é só isto.

No `+` de **DIMENSÕES**, a aba **Personalizado** do seletor traz as 8 que
registramos na etapa 2. Selecione as 8 de uma vez, e some pela busca:

```
Nome do evento     (grupo Evento)   OBRIGATÓRIA: é o filtro da guia 2
```

O `+` de DIMENSÕES aceita o que mais você quiser, e não custa nada. "Origem
atribuída ao primeiro usuário", "Mídia" e "Campanha" valem a pena: permitem
segmentar o funil por origem, e responder se quem vem do anúncio converte
diferente de quem vem do orgânico.

**Não precisa importar "Local da página" por causa do funil.** O editor de
etapas tem catálogo próprio de parâmetros, independente do painel Variáveis, e
o `page_location` aparece lá sem estar importado aqui.

No `+` de **MÉTRICAS**:

```
Contagem de eventos
Usuários ativos
```

⚠️ **O período padrão exclui hoje.** "Últimos 28 dias" termina ontem. Para
conferir medição que acabou de subir, troque para um período que inclua hoje,
senão o painel diz "não há dados" com a medição funcionando perfeitamente.

### 6.1 Funil do cadastro

Guia **`Funil do cadastro`**. Em Configurações:

| Campo | Valor |
|---|---|
| TÉCNICA | `Análise detalhada de funil` |
| VISUALIZAÇÃO | `Funil padrão` |
| ABRIR O FUNIL | **ligado** |
| ETAPAS | o lápis abre o editor dos passos |
| DETALHAMENTO | `Método de cadastro` |

Os passos, nesta ordem, no editor do lápis. As etapas 2 a 7 são o evento e nada
mais, só escolher e nomear:

| # | Nome da etapa | Condição |
|---|---|---|
| 1 | Abre a página de cadastro | evento `page_view` **com parâmetro** `page_location` contém `/register` |
| 2 | Começa a preencher | evento `signup_started` |
| 3 | Criou a conta | evento `signup_account_created` |
| 4 | Confirmou o e-mail | evento `signup_email_verified` |
| 5 | Conta criada | evento `form_submit_trial` |
| 6 | Escritório criado | evento `signup_office_created` |
| 7 | Onboarding completo | evento `onboarding_completed` |

⚠️ **Na etapa 1, o `page_location` entra pelo botão "+ Adicionar parâmetro" da
linha do `page_view`, nunca como uma segunda condição ligada por "E".** São
coisas diferentes: parâmetro quer dizer "um page_view CUJA url contém
/register", e segunda condição quer dizer "houve um page_view E existe um
page_location", que não filtra nada e deixa a etapa 1 valendo para o site
inteiro. O sintoma é um funil que parece montado e entrega zero.

Operador **contém**, não "igual a": o `page_location` é a URL inteira, com
domínio e query string, então igualdade nunca casa.

Os botões "Ou" de cada linha e o "E" do rodapé não são usados em nenhuma etapa
deste funil. Cada etapa aqui é um evento só.

⚠️ **Entre uma etapa e a seguinte, escolher "é seguida indiretamente por".** É o
padrão, e a outra opção arruína o funil. "Diretamente" exige que a próxima etapa
seja o evento IMEDIATAMENTE seguinte, sem nada no meio, e o GA4 coleta sozinho
`user_engagement`, `scroll`, `page_view` e `session_start` o tempo todo. Entre
dois passos do cadastro quase sempre haverá algum deles, então o funil cairia a
zero depois da etapa 1 com cara de medição quebrada.

Isso é um eixo diferente do "Abrir o funil", e os dois são independentes:

- **Abrir o funil** responde "a pessoa precisa ter entrado pela etapa 1?"
- **Diretamente / indiretamente** responde "pode acontecer outra coisa entre uma
  etapa e a seguinte?"

"Abrir o funil" ligado deixa a pessoa entrar em qualquer etapa, em vez de exigir
que ela tenha passado pela primeira. Aqui isso importa: quem volta depois por
`/login` e termina o onboarding noutro dia não começou a sessão no passo 1.

O detalhamento por `Método de cadastro` mostra se o caminho do Google ou o do
e-mail perde mais gente.

Não usar `signup_method_selected` como passo: ele só dispara em quem escolhe o
Google, então quebraria o funil para todo mundo que segue por e-mail. Ele serve
para comparar os dois caminhos, não para medir queda.

### 6.2 Onde a pessoa trava no onboarding

Guia **`Onde a pessoa trava no onboarding`**. O nome é a pergunta que ela
responde, de propósito: "Formato livre 2" não diz nada daqui a três meses, e
ainda faz alguém criar uma terceira igual.

É esta que responde a pergunta do onboarding, e ela não assume ordem de passo,
diferente do funil. Em Configurações:

| Campo | Valor |
|---|---|
| TÉCNICA | `Formato livre` |
| VISUALIZAÇÃO | tabela, o primeiro ícone |
| LINHAS | `Passo do onboarding` |
| COLUNAS | `Passo pulado` |
| VALORES | `Contagem de eventos` e `Usuários ativos` |
| FILTROS | `Nome do evento` **igual a** `onboarding_step_done` |
| EXIBIR LINHAS | 10 basta, são três passos |

⚠️ **Sem o filtro a tabela fica ilegível.** Todo evento da propriedade que não
carrega `step` entra como `(not set)`, e isso é mais de 99% das linhas. O sinal
fica afogado no ruído e parece que a medição não pegou.

⚠️ **O dropdown de FILTROS só oferece o que está em Variáveis.** Se o "Nome do
evento" não aparece ali, é porque não foi importado, não porque não exista.

As duas métricas respondem coisas diferentes e vale ter as duas: contagem de
eventos conta disparos, e `onboarding_step_done` dispara uma vez por passo;
usuários ativos conta pessoas. Passo que alguém refaz aparece inflado na
primeira e não na segunda.

Lê-se direto: cada linha é um dos três passos (`lawyer`, `intimations`,
`portfolio`), e a coluna separa quem concluiu de quem clicou em pular. Passo com
muito `skipped=true` é passo que incomoda. Passo que simplesmente não aparece é
passo que ninguém alcança.

Fechar a taxa de ativação exige o `onboarding_completed` no GA4, que a etapa 3
resolve.

⚠️ **Análise detalhada nasce privada.** Só quem criou enxerga. Para a Mobiletec
ou qualquer outra pessoa da propriedade abrir, compartilhar no ícone de pessoa
com `+` na barra de cima. Sem isso o link entregue responde "sem acesso".

⚠️ **Análise nova só enxerga dado a partir de hoje.** Nada no GA4 é
retroativo: os seis eventos nunca foram coletados, então não existe histórico
para olhar. A leitura começa a valer alguns dias depois de publicar a tag.

---

## Depois de rodar tudo

Conferir o que subiu, sem login, direto do container publicado:

```bash
curl -s "https://www.googletagmanager.com/gtm.js?id=GTM-WHQGLTXC" \
  | grep -c onboarding_step_done
```

Zero significa que a versão foi salva e não enviada. **Salvar não publica**, e
este container já falhou assim.

Atualizar o catálogo, que é a fonte da verdade da página de Rastreamento do hub:

```bash
# em clients/juria/ferramentas/gerar-eventos.py, nos eventos migrados:
#   estado="a_ligar"  ->  estado="ga4"
#   existe=False      ->  existe=True
#   ga4_ligado=False  ->  ga4_ligado=True
#   gatilho=None      ->  gatilho="Funil_Cadastro"
#   tag=None          ->  tag="GA4_Funil_Cadastro"
#   fontes=[]         ->  fontes=["navegador"]
python3 clients/juria/ferramentas/gerar-eventos.py
```

O script recusa evento com `existe=True` sem destino, então catálogo e realidade
não voltam a divergir em silêncio.

Publicar o hub: [[publicar-lp-juria|publicar-lp-juria.md]].
