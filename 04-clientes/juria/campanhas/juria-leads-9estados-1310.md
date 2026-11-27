---
tipo: campanha
cliente: juria
nome-campanha: juria-leads-9estados-1310
plataforma: meta
id-campanha: "120249475110530208"
status: ativa
inicio: 2026-10-13
verba-diaria: 42
evento-otimizacao: LEAD
lp: https://www.juria.app.br
atualizado: 2026-11-27
autor: claude
origem: agencia_marketing, clients/juria/campanhas/9estados-lead-1310.md (anexado em 27/11/2026)
---
# juria-leads-9estados-1310

Nome no Meta: **JurIA - Leads - 9 Estados - Institucional - Lead**. A ficha completa, migrada do repo em 27/11/2026, está abaixo.

## Configuração
Conferida na API em 04/11/2026.

- **Objetivo:** Leads, otimizando conversão no site com o evento `LEAD` (conta criada, `form_submit_trial`, antes do onboarding) do Pixel `1009120801605718`
- **Conjunto:** `120249475110560208`, Ad Set-INST - Aberto - 9 Estados - 28-60 - Estáticos - Lead, ativo, R$ 42/dia (ABO)
- **Público:** de 28 a 60 anos, aberto, sem Advantage+ Audience, em BA, DF, GO, MG, PR, RJ, RS, SC e SP
- **Posicionamento:** manual, só Facebook e Instagram, só no celular

**O teste:** mesma praça, público, peça e copy da View_Register (3009). A única diferença é o evento otimizado. Abriu em 13/10, a pedido do Guilherme.

## Criativos no ar
| ID | Anúncio | Desde |
|---|---|---|
| `120249475110570208` | INST-B-01_inst_sistemas_v2 | 13/10/2026 |
| `120249475110540208` | INST-B-02_inst_mudanca_v1 | 13/10/2026 |

## Histórico de otimizações
- 2026-10-13 · publicada a R$ 37/dia · teste do evento `LEAD` contra o `ViewRegister`
- TODO · verba alterada para R$ 57/dia, segundo a ficha do repo em 28/10
- TODO · verba alterada para R$ 42/dia, conforme a API em 04/11. Registrar quando e por quê
- 2026-11-13 · avaliar, conforme o registro do hub

## Ficha completa

Aberta em 13/10/2026 a pedido do Guilherme. Pega os dois criativos que vêm
rendendo na campanha do ar (`INST-B-01_inst_sistemas_v2` e
`INST-B-02_inst_mudanca_v1`) e sobe os dois **num conjunto só**, com o mesmo
público, a mesma copy e uma diferença única: **otimiza pela conta criada
(`LEAD`), não pela chegada na tela de cadastro (`ViewRegister`)**.

**As duas campanhas ficam no ar em paralelo**, decisão do Guilherme em 13/10. É
um teste de evento de otimização com praça, público, peça e copy idênticos.

| | Campanha do ar | Esta campanha |
|---|---|---|
| Slug | `juria-leads-9estados-3009` | `juria-leads-9estados-1310` |
| Evento otimizado | `ViewRegister` (conversão personalizada) | `LEAD` |
| Verba | R$ 47,00/dia | R$ 37,00/dia |
| Resto | igual | igual |

### IDs

Montada por duplicação da View_Register (`click_campaign_group_duplicate`) e
**publicada pelo Guilherme em 13/10/2026 às 10:26**. Conferida na API depois de
publicar: os IDs do rascunho **se mantiveram**.

| Nível | Nome | ID | Status | Origem |
|---|---|---|---|---|
| Campanha | JurIA - Leads - 9 Estados - Institucional - Lead | `120249475110530208` | ACTIVE | `120249306206250208` |
| Conjunto | Ad Set-INST - Aberto - 9 Estados - 28-60 - Estáticos - Lead | `120249475110560208` | ACTIVE | `120249306206280208` |
| Anúncio | INST-B-01_inst_sistemas_v2 | `120249475110570208` | ACTIVE | `120249306206260208` |
| Anúncio | INST-B-02_inst_mudanca_v1 | `120249475110540208` | ACTIVE | `120249306374650208` |

Criativos: `3187709894752491` (INST-B-01) e `2455671671509518` (INST-B-02).

- [Abrir a campanha no Ads Manager](https://www.facebook.com/adsmanager/manage/campaigns/edit?act=1465935581974017&selected_campaign_ids=120249475110530208)
- [Abrir o conjunto](https://www.facebook.com/adsmanager/manage/adsets/edit?act=1465935581974017&selected_adset_ids=120249475110560208)

Os dois anúncios entraram em análise da Meta e **saíram no mesmo dia**: às
13h20 de 13/10 já estavam `ACTIVE`.

### ✅ Conferência do publicado · 13/10/2026

Lido na API depois da publicação. **Cinco das seis correções entraram.** As
URLs foram conferidas no destino real do anúncio, não no que a ficha dizia: a
API não devolve `link_url` destes criativos (são `SHARE`, com
`effective_object_story_id`), então o valor veio da URL de clique do preview de
cada anúncio.

| O que | Antes, no rascunho | Agora, no ar |
|---|---|---|
| `utm_campaign` dos dois anúncios | `juria-leads-9estados-3009` | **`juria-leads-9estados-1310`** ✅ |
| Nome do conjunto | igual ao do ar | sufixo **` - Lead`** ✅ |
| Evento | `LEAD`, já estava certo | `LEAD`, `pixel_rule: null` ✅ |
| CTA | `SEE_DETAILS` | **`LEARN_MORE`**, igual ao do ar ✅ |
| INST-B-01 | `PAUSED` | **entra junto com o B-02** ✅ |
| Nome dos anúncios | igual ao do ar | igual ao do ar, **não renomeado** |

URLs de destino, lidas no anúncio publicado:

```
INST-B-01 → ...utm_campaign=juria-leads-9estados-1310&utm_content=inst_sistemas_v2&utm_term=geral_aberto
INST-B-02 → ...utm_campaign=juria-leads-9estados-1310&utm_content=inst_mudanca_v1&utm_term=geral_aberto
```

#### Como separar esta campanha da View_Register

| Onde | O que separa |
|---|---|
| GA4 e destino | `utm_campaign`: `...-1310` aqui, `...-3009` lá. `utm_content` e `utm_term` são iguais nas duas, de propósito: a peça e o público são os mesmos |
| Ads Manager | nome da campanha (`... - Lead` contra `... - View_Register`) e do conjunto (sufixo ` - Lead`) |
| Painel do hub | `ad_id`, que é único. Os quatro anúncios têm IDs diferentes mesmo com dois nomes repetidos |

**Os nomes dos anúncios ficam repetidos nas duas campanhas, por decisão do
Guilherme em 13/10.** Renomear chegou a ser proposto
(`INST-B-01-Estático-Acervo-Importado`, `INST-B-02-Estático-Rotina-Mudou`) e foi
recusado: a mesma peça mantém o mesmo nome, como manda
`agencia_marketing/docs/convencoes.md` para o mesmo criativo em
lugares diferentes. Não quebra a medição: o painel cruza por `ad_id`, a página
de anúncios do hub agrupa por campanha e o Ads Manager tem a coluna de campanha.
Na exportação crua do Ads Manager, sem essa coluna, as duas linhas ficam
idênticas: é o preço, e é conhecido.

#### ⚠️ A verba ficou em R$ 37,00/dia

| Campanha | Verba |
|---|---|
| `...-3009` (View_Register) | R$ 47,00/dia |
| `...-1310` (Lead) | **R$ 37,00/dia** |

Combinado em 13/10 era R$ 27,00/dia; subiu para R$ 37,00. Está em ABO, no
conjunto, como manda a origem. **Com verbas diferentes o teste não compara
volume:** olhar custo por resultado, nunca número de cadastros.

### Configuração no ar

Herdada do conjunto `120249306206280208` (`Ad Set-INST - Aberto - 9 Estados -
28-60 - Estáticos`) e conferida no conjunto publicado em 13/10/2026.

| Campo | Valor |
|---|---|
| Objetivo | `OUTCOME_LEADS` · leilão (`AUCTION`) |
| Meta de performance | `OFFSITE_CONVERSIONS` |
| **Evento** | **Pixel `1009120801605718`, `LEAD`** (é o único campo que muda) |
| Cobrança | Impressões |
| Lance | Highest volume (`LOWEST_COST_WITHOUT_CAP`) |
| Orçamento | R$ 37,00/dia, no conjunto (ABO) |
| Atribuição | 7 dias clique + 1 dia visualização |
| Idade | 28 a 60 |
| Advantage+ Audience | **desligado** (`targeting_automation.advantage_audience: 0`) |
| Expansão de geo | ligada (`individual_setting.geo: 1`), igual à origem |
| Destino | Website |
| Dispositivo | **só mobile** (`device_platforms: ["mobile"]`) |

#### O evento, com cuidado

A origem **não** usa `custom_event_type: LEAD`. Ela usa `OTHER` com uma
`pixel_rule`:

```
custom_event_type: OTHER
pixel_rule: {"and":[{"event":{"eq":"ViewRegister"}},
                    {"or":[{"URL":{"i_contains":"/register"}}]}]}
```

Aqui a `pixel_rule` **não foi copiada**: o `promoted_object` publicado tem o
pixel e `custom_event_type: LEAD`, que é a conta criada (`form_submit_trial`, antes do onboarding), com
`pixel_rule: null`. Conferido na API depois de publicar. Duplicar o conjunto e
esquecer de trocar este campo é o jeito mais fácil de subir duas campanhas
idênticas e achar que são um teste.

#### Localização: os 9 estados, com os keys

A trava registrada em [[04-clientes/juria/campanhas/juria-leads-9estados-1409|9estados-institucional-1409.md]]
(a API exige `region key` numérico e não havia como resolver) **está
resolvida**: os keys saíram da própria API ao ler o conjunto do ar.

| Estado | `key` | Estado | `key` |
|---|---|---|---|
| Bahia | 442 | Rio de Janeiro | 454 |
| Distrito Federal | 444 | Rio Grande do Sul | 456 |
| Minas Gerais | 449 | Santa Catarina | 459 |
| Paraná | 452 | São Paulo | 460 |
| Goiás | 462 | | |

`location_types`: `frequently_in`, `home`, `recent`.

#### Posicionamento: manual, Facebook e Instagram

| Plataforma | Posições |
|---|---|
| Facebook | `feed`, `instream_video`, `story`, `facebook_reels`, `facebook_reels_overlay`, `profile_feed` |
| Instagram | `stream`, `story`, `reels`, `profile_feed` |

Sem Audience Network, sem Messenger, sem coluna direita nem Marketplace.
Filtro de conteúdo: `FACEBOOK_STRICT`.

### UTMs

Padrão de `agencia_marketing/docs/convencoes.md`. Muda **só** o
`utm_campaign` em relação à campanha do ar: o `utm_term` é o mesmo público e o
`utm_content` casa com o nome do arquivo do criativo, que é o mesmo.

```
utm_source=meta
utm_medium=paid
utm_campaign=juria-leads-9estados-1310
utm_term=geral_aberto
utm_content=inst_sistemas_v2   ← INST-B-01
utm_content=inst_mudanca_v1    ← INST-B-02
```

**URL de destino (usar com `www`):**

`INST-B-01_inst_sistemas_v2`

```
https://www.juria.app.br/?utm_source=meta&utm_medium=paid&utm_campaign=juria-leads-9estados-1310&utm_content=inst_sistemas_v2&utm_term=geral_aberto
```

`INST-B-02_inst_mudanca_v1`

```
https://www.juria.app.br/?utm_source=meta&utm_medium=paid&utm_campaign=juria-leads-9estados-1310&utm_content=inst_mudanca_v1&utm_term=geral_aberto
```

> Com as duas campanhas no ar, a **mesma peça** passa a existir em dois lugares
> com o mesmo `utm_content` e o mesmo `utm_term`. Quem separa é o
> `utm_campaign`. No GA4, comparar sempre por campanha; no painel do hub, pelo
> `ad_id`.

### Copy publicada

A mesma dos dois anúncios do ar, sem alteração. Registrada em
`ferramentas/gerar-anuncios.py`.

| Campo | INST-B-01 | INST-B-02 |
|---|---|---|
| Texto principal | Trocar de sistema não quer dizer redigitar o acervo inteiro. Ele entra por planilha ou direto pela sua OAB. | Em dois anos a rotina mudou mais que na década anterior. O escritório que não acompanhou sente no prazo. |
| Título | JurIA · Sistema Jurídico com IA | JurIA · Sistema Jurídico com IA |
| Descrição | Mobiletec, desde 2000 | Mobiletec, desde 2000 |
| CTA | Saiba mais (`LEARN_MORE`) | Saiba mais (`LEARN_MORE`) |

> ⚠️ **A descrição "Mobiletec, desde 2000" está errada.** O ano é 1999
> (Mobiletec, 21/10/2026; Guilherme, 04/11). Os dois anúncios seguem no ar com
> ela em 05/11. Trocar no Ads Manager depende do OK do Guilherme, e troca de
> descrição reinicia o aprendizado do anúncio.
| Imagem | `inst-b-01-sistemas.jpg` | `inst-b-02-mudanca.jpg` |

### ⚠️ O que o ciclo de métricas de 13/10 mostrou na campanha vizinha

Puxando os dados até 12/10 para o painel, apareceu o seguinte na
`juria-leads-9estados-3009`, que é a campanha de comparação deste teste:

- **Desde 09/10, dois dos quatro anúncios de lá pararam de entregar sozinhos.**
  INST-B-01 e INST-NAT-02 zeraram sem terem sido pausados: o leilão concentrou a
  verba na outra peça de cada conjunto. É exatamente o risco descrito abaixo, e
  agora com registro.
- **Em 13/10 o conjunto Notas foi pausado inteiro**, e o INST-B-01 foi pausado
  dentro do conjunto Estáticos. Da View_Register só sobrou o INST-B-02 no ar.

Para este teste isso importa: a campanha de comparação mudou de desenho no mesmo
dia em que esta subiu. Comparar as duas daqui para a frente é comparar uma peça
lá contra duas aqui, com verbas diferentes. **O que ainda compara é o custo por
resultado da mesma peça**, o INST-B-02, que roda nas duas.

### Os dois num conjunto só: risco conhecido

⚠️ Foi exatamente assim que o INST-D-01 ficou sem entrega em setembro: o leilão
concentra a verba em quem responde melhor nos primeiros dias, e com R$ 37,00/dia
dividido entre duas peças a segunda pode não aparecer. Decisão do Guilherme é um
conjunto só. **Se em alguns dias um dos dois estiver parado, separar cada um no
seu conjunto.** Registrado também em
[[04-clientes/juria/campanhas/juria-leads-9estados-1409|9estados-institucional-1409.md]].

### O que falta agora

- ⬜ Sair de `IN_PROCESS`: enquanto estiver em análise não há entrega
- ✅ Cadastrada em `ferramentas/gerar-dados-campanha.py` (`ADS`, `AD_STATUS`,
      `AD_SET`, `SETS`) e em `ferramentas/gerar-anuncios.py` (`CAMPANHAS` e
      `ANUNCIOS`), em 13/10. A página de anúncios do hub já mostra a campanha;
      o painel de Performance só mostra no próximo ciclo, quando houver gasto
- ✅ Nomes dos anúncios: ficam iguais aos da View_Register (decisão de 13/10)
- ✅ Saíram da análise no mesmo dia 13/10, já `ACTIVE` nos dois geradores
- ⬜ Conferir o primeiro clique real chegando com
      `utm_campaign=juria-leads-9estados-1310`
- ⬜ Vigiar a entrega dos dois criativos no mesmo conjunto (abaixo)

### Armadilhas da conta (não mudaram)

- **Upload de mídia por API bloqueado** ("gradually rolled out"): as duas
  imagens já estão na biblioteca da conta desde 30/09, então dá para reaproveitar
  o asset em vez de subir de novo.
- **App Meta em modo de desenvolvimento** faz a API recusar a criação do
  *anúncio* em alguns conjuntos. Campanha e conjunto costumam passar; o anúncio
  pode ter que ser montado à mão, como em 14/09 e 30/09.
- Campanha e conjunto criados por API **nascem `PAUSED`**. Anúncio novo entra
  como `PENDING_REVIEW`.

### Depois de publicar

- ⬜ Anúncios fora da análise e entregando
- ⬜ Cadastrar nos dicionários de `ferramentas/gerar-dados-campanha.py`:
      `ADS`, `AD_STATUS`, `AD_SET` e `SETS` (conjunto novo, `utm_term`
      `geral_aberto`), senão o painel não mostra a campanha
- ⬜ Cadastrar em `ferramentas/gerar-anuncios.py`: a campanha nova em
      `CAMPANHAS` (no topo, é a mais recente no ar) e os dois anúncios em
      `ANUNCIOS`
- ⬜ Primeiro clique real chegando com `utm_campaign=juria-leads-9estados-1310`

### Histórico

- **13/10/2026:** ficha aberta, antes da montagem.
- **13/10/2026, 10:13:** campanha duplicada da View_Register pelo Guilherme e
  deixada em rascunho. Conferida na API: UTMs ainda apontando para a campanha de
  30/09, nomes de conjunto e anúncios repetidos, verba e CTA divergentes. Evento
  `LEAD` correto.
- **13/10/2026:** ciclo de métricas do hub rodado até 12/10, com esta campanha
  já cadastrada. Os dois anúncios saíram da análise e estão `ACTIVE`.
- **13/10/2026:** cadastrada nos dois geradores do hub. O status entrou como
  "em análise", não como no ar: `PENDING_REVIEW` no gerador do painel e
  `IN_PROCESS` no da página de anúncios, que ganhou esse estado.
- **13/10/2026, 10:26:** publicada, com as correções aplicadas. UTMs conferidas
  no destino real dos dois anúncios. Ficou de fora: os nomes dos anúncios, que
  seguem iguais aos da View_Register. Verba definida em R$ 37,00/dia.
