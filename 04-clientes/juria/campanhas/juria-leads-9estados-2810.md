---
tipo: campanha
cliente: juria
nome-campanha: juria-leads-9estados-2810
plataforma: meta
id-campanha: "120249694436600208"
status: pausada
pausada: 2026-11-23
inicio: 2026-10-29
verba-diaria: 27
evento-otimizacao: COMPLETE_REGISTRATION
lp: https://www.juria.app.br
atualizado: 2026-11-27
autor: claude
origem: agencia_marketing, clients/juria/campanhas/9estados-videos-2810.md (anexado em 27/11/2026)
---
# juria-leads-9estados-2810

Nome no Meta: **JurIA - Leads - 9 Estados - Institucional - Concluir inscrição**. A ficha completa, migrada do repo em 27/11/2026, está abaixo.

> **Pausada em 23/11/2026** (API, conferido em 27/11). Só a campanha de Lead (`1310`) segue no ar. Antes disso, desde 02/11, só o conjunto da locução rodava, porque o da música estava pausado.

## Configuração
Conferida na API em 04/11/2026.

- **Objetivo:** Leads, otimizando o evento `COMPLETE_REGISTRATION`. Nesta conta esse evento marca o onboarding completo, não o cadastro, e teve 5 ocorrências na semana de 21 a 28/10. Decisão do Guilherme em aberto: manter ou trocar para `LEAD`
- **Posicionamento:** automático, inclui Audience Network, WhatsApp, Threads e desktop. É a única campanha da conta assim desde 14/09. Decisão do Guilherme em aberto
- **Público:** de 28 a 60 anos, aberto, nos mesmos 9 estados da campanha 1310

| Conjunto | ID | Status | Verba |
|---|---|---|---|
| Vídeos - Concluir inscrição (música) | `120249694436590208` | **pausado** | R$ 27/dia |
| Vídeos - Concluir inscrição — Cópia (locução) | `120249694552070208` | ativo | R$ 27/dia |

## Criativos no ar
| ID | Anúncio | Desde |
|---|---|---|
| `120249694436620208` | INST-VID-02-Vídeo-Categoria-Música (conjunto pausado) | 28/10/2026 |
| `120249694552080208` | INST-VID-03-Vídeo-Categoria-Locução | 28/10/2026 |

UTMs: `utm_campaign=juria-leads-9estados-2810`, `utm_content=inst_video_categoria_musica_v1` ou `inst_video_categoria_locucao_v1`, `utm_term=geral_aberto`.

## Histórico de otimizações
- 2026-10-28 · publicada pelo Guilherme · teste de música contra locução, com a mesma imagem e a mesma copy
- TODO · conjunto da música pausado. Registrar quando e por quê
- 2026-11-04 · trava encontrada na API e registrada sem mexer na campanha · o Guilherme decide o teste, o evento e o posicionamento no Ads Manager
- 2026-11-25 · avaliar, conforme o registro do hub

## Ficha completa

Publicada pelo Guilherme em 28/10/2026, às 17:55. Sobe os dois vídeos do eixo
Categoria aprovados pela Mobiletec, **um por conjunto**, para testar música
contra locução com a mesma imagem e a mesma copy. Conferida na API no mesmo dia.

`utm_campaign`: **`juria-leads-9estados-2810`**

### IDs

| Nível | Nome no Meta | ID | Status em 28/10 |
|---|---|---|---|
| Campanha | JurIA - Leads - 9 Estados - Institucional - Concluir inscrição | `120249694436600208` | ACTIVE |
| Conjunto | Ad Set-INST - Aberto - 9 Estados - 28-60 - Vídeos - Concluir inscrição | `120249694436590208` | ACTIVE |
| Conjunto | Ad Set-INST - Aberto - 9 Estados - 28-60 - Vídeos - Concluir inscrição — Cópia | `120249694552070208` | ACTIVE |
| Anúncio | INST-VID-02-Vídeo-Categoria-Música (1º conjunto) | `120249694436620208` | IN_PROCESS |
| Anúncio | INST-VID-03-Vídeo-Categoria-Locução (2º conjunto) | `120249694552080208` | IN_PROCESS |

Criativos: `2035935813777206` (VID-02, vídeo `2174146979804678`) e
`1675796874073515` (VID-03, vídeo `2832503923798206`).

- [Abrir a campanha no Ads Manager](https://www.facebook.com/adsmanager/manage/campaigns/edit?act=1465935581974017&selected_campaign_ids=120249694436600208)

### UTMs, conferidas no destino real

A API não devolve `link_url` destes criativos; o valor saiu da URL de clique do
preview de cada anúncio.

```
INST-VID-02 → ...utm_campaign=juria-leads-9estados-2810&utm_content=inst_video_categoria_musica_v1&utm_term=geral_aberto
INST-VID-03 → ...utm_campaign=juria-leads-9estados-2810&utm_content=inst_video_categoria_locucao_v1&utm_term=geral_aberto
```

Copy: `hub3ps-vault/04-clientes/juria/copies/juria-leads-9estados-2810/`.
O texto principal 1, o título 1 e a descrição 1 batem com os dois criativos. As
outras variações a API não expõe.

### Configuração, comparada com a campanha no ar

Referência: conjunto `120249475110560208` da `juria-leads-9estados-1310`.

| Campo | `...-1310` (no ar) | `...-2810` (esta) | |
|---|---|---|---|
| Objetivo | `OUTCOME_LEADS` | `OUTCOME_LEADS` | igual |
| Meta | `OFFSITE_CONVERSIONS` | `OFFSITE_CONVERSIONS` | igual |
| **Evento** | **`LEAD`** | **`COMPLETE_REGISTRATION`** | ⚠️ diferente |
| Lance | Highest volume | Highest volume | igual |
| Orçamento | R$ 57,00/dia, ABO | R$ 27,00/dia **por conjunto**, ABO (R$ 54,00 no total) | |
| Atribuição | 7d clique + 1d visualização | igual | igual |
| Público | 9 estados, 28 a 60, aberto, Advantage+ Audience desligado | igual | igual |
| **Posicionamento** | **manual: Facebook e Instagram, só celular** | **automático (Advantage+): inclui Audience Network, WhatsApp, Threads, Marketplace, coluna da direita e desktop** | ⚠️ diferente |
| Filtro de conteúdo | `FACEBOOK_STRICT` | `FACEBOOK_RELAXED` | ⚠️ acompanha o posicionamento |

#### ⚠️ O evento: "Concluir inscrição" não é o evento da `...-1310`

O rótulo do Meta engana. Nesta conta:

| Evento | O que é | Volume na conta, 21 a 28/10 |
|---|---|---|
| `Lead` | **conta criada** (`form_submit_trial`), primeiro passo do cadastro, antes do onboarding, o que a `...-1310` otimiza e o que o hub conta como cadastro | 17 |
| `CompleteRegistration` | **onboarding completo**, a ativação, um passo depois do cadastro | 5 |

Fonte do significado: `tracking/gtm-tag-complete-registration.html` e
`brief-migracao-juria-astro.md`. Volume: `ads_get_dataset_stats`, 28/10.

Com 5 eventos por semana na conta inteira, cada conjunto teria perto de nada
para aprender, e a campanha não seria comparável com a `...-1310`. Se a
intenção era comparar com a `...-1310`, o evento certo é `LEAD`. ⬜ **Decisão do
Guilherme.**

#### ⚠️ O posicionamento

Desde 14/09 todas as campanhas do JurIA rodam manual, só Facebook e Instagram,
no celular. Esta saiu no automático, que espalha verba por Audience Network,
WhatsApp, Threads e desktop. ⬜ **Decisão do Guilherme.**

### O que falta

- ⬜ Evento: manter `COMPLETE_REGISTRATION` ou trocar para `LEAD`
- ⬜ Posicionamento: manter automático ou voltar ao manual da `...-1310`
- ⬜ Renomear o 2º conjunto: hoje termina em "— Cópia". Sugestão: trocar
      "Vídeos" por "Vídeos - Música" no 1º e "Vídeos - Locução" no 2º
- ⬜ Conferir no Ads Manager as 5 variações de texto dos dois anúncios: o
      preview devolveu, ligado aos vídeos, o texto principal do INST-B-01 ("...pela
      sua OAB"), sinal de que a duplicação pode ter trazido variações antigas
- ⬜ Saída de `IN_PROCESS`
- ⬜ Cadastrar nos geradores do hub, depois das decisões acima (trocar o evento
      pode mudar o conjunto)

### Histórico

- **28/10/2026, 17:55:** publicada. Conferida na API: UTMs corretas, evento e
  posicionamento diferentes da `...-1310`.
