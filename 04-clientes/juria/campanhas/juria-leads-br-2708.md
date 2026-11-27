---
tipo: cliente-doc
cliente: juria
atualizado: 2026-11-27
autor: claude
origem: agencia_marketing, clients/juria/campanhas/br-institucional-2708.md (migrado em 27/11/2026)
---
# Campanha Brasil · Institucional · montagem

Criada via MCP da Meta em 31/08/2026 e **publicada pelo Guilherme no mesmo dia**.
Conjunto ativo desde 16:07; o anúncio entrou em análise da Meta (`IN_PROCESS`).

## IDs

| Nível | Nome | ID |
|---|---|---|
| Campanha | JurIA · Meta · Leads · Brasil · Institucional | `120248881937880208` |
| Conjunto | Ad Set-INST · Aberto · Brasil 28-60 | `120248881942670208` |
| Anúncio | INST-VID-01-Vídeo-Consolidação-Motion | `120248882022190208` |

> Nome do conjunto ajustado de "Interesses" para "Aberto" em 31/08, junto com a troca de segmentação.

- [Abrir a campanha no Ads Manager](https://www.facebook.com/adsmanager/manage/campaigns/edit?act=1465935581974017&selected_campaign_ids=120248881937880208)
- [Abrir o conjunto](https://www.facebook.com/adsmanager/manage/adsets/edit?act=1465935581974017&selected_adset_ids=120248881942670208)

## Configuração replicada

Copiada do `Ad Set-TRAB · Interesses · Sul 28-60` (`120248812776100208`).

| Campo | Valor |
|---|---|
| Objetivo | `OUTCOME_LEADS` · leilão |
| Meta de performance | `OFFSITE_CONVERSIONS` |
| Cobrança | Impressões |
| Lance | Highest volume (`LOWEST_COST_WITHOUT_CAP`) |
| Orçamento | R$ 27,00/dia, no conjunto (ABO) |
| Evento | Pixel `1009120801605718`, `LEAD` |
| Atribuição | 7 dias clique + 1 dia visualização |
| Idade | 28 a 60 |
| Advantage+ Audience | desligado (igual ao original) |

**Segmentação: público aberto.** Sem `flexible_spec`, igual aos conjuntos
"Aberto" da campanha do Sul. Só idade, geografia e Advantage+ Audience
desligado. O resto é posicionamento automático.

### Histórico da segmentação

O conjunto nasceu em 31/08 com os interesses copiados do
`TRAB · Interesses · Sul 28-60` (Advogado, Legal Services, três Escritórios de
Advocacia, três cargos). **Ainda em 31/08 os interesses foram removidos** a
pedido do Guilherme, para o público ficar aberto como nos demais conjuntos.

Faz sentido: numa campanha institucional sem nicho, para o Brasil inteiro,
interesses estreitam justamente onde se quer amplitude. E resolve de brinde o
incômodo do cargo "Advogada Trabalhista", que era de nicho numa peça que não é.

**Geografia é Brasil, não Sul**, decisão registrada no `brief.md`.

## UTMs

```
utm_source=meta
utm_medium=paid
utm_campaign=juria-leads-br-2708
utm_content=inst_video_consolidacao_v1
utm_term=geral_interesses
```

**URL de destino (usar com `www`):**

```
https://www.juria.app.br/?utm_source=meta&utm_medium=paid&utm_campaign=juria-leads-br-2708&utm_content=inst_video_consolidacao_v1&utm_term=geral_interesses
```

> Testado em 31/08/2026: o redirect **preserva a query string**. O bug listado
> em `tracking/verificacao-tracking-mobiletec.md` ("redirect não-www quebra com
> parâmetros") **foi corrigido**: os dois domínios chegam com as UTMs intactas.

## ✅ O `utm_term` está correto

> **Correção de 09/09/2026.** Este documento afirmava que o anúncio tinha ficado
> com `utm_term=geral_interesses`, montado antes de os interesses serem
> removidos, e que a URL não teria sido refeita. **Lendo o criativo ao vivo pela
> API, ele está com `utm_term=geral_aberto`.** A URL foi corrigida na época; a
> ressalva registrada aqui estava errada.

Os criativos novos seguem o mesmo valor. Ver
[[04-clientes/juria/campanhas/juria-leads-br-2708-subida-2026-09-09|subida-inst-c-d-2026-09-09.md]].

## ⛔ Encerrada em 14/09/2026

A campanha foi **pausada inteira** pelo Guilherme, e com ela os dois conjuntos
(`120248881942670208` e `120249009735710208`) e os três anúncios
(INST-VID-01, INST-C-01, INST-D-01).

O que os números diziam na hora da decisão, na janela de 7 dias até 13/09:

| Peça | Gasto | Cadastros | Por cadastro |
|---|---|---|---|
| INST-VID-01 (vídeo) | R$ 145,64 | 1 | R$ 145,64 |
| INST-C-01 | R$ 118,10 | 1 | R$ 118,10 |
| INST-D-01 | R$ 5,18 | 0 | sem entrega |
| TRAB-NAT-C, para comparar | R$ 195,94 | 4 | R$ 48,99 |

O vídeo já vinha piorando desde o ciclo de 09/09. Os dois estáticos entraram
para dar alternativa e não viraram o jogo: o C-01 ficou caro e o D-01 mal
apareceu, porque dividia conjunto com o C-01.

**O institucional recomeça com outro desenho,** recorte de 9 estados e
posicionamento manual, em
[[04-clientes/juria/campanhas/juria-leads-9estados-1409|9estados-institucional-1409.md]].

## Estado em 02/09/2026

| Nível | Status |
|---|---|
| Campanha | ativa |
| Conjunto | **ACTIVE**, R$ 27,00/dia, desde 31/08 16:07 · público aberto |
| Anúncio | **ACTIVE**, saiu da análise e entrou em entrega em 31/08 |

### Primeiros números (31/08 e 01/09)

| Dia | Gasto | Impressões | Cliques | Cliques no link | LPV | Cadastros |
|---|---|---|---|---|---|---|
| 31/08 | R$ 16,03 | 140 | 5 | 3 | 3 | 0 |
| 01/09 | R$ 40,78 | 529 | 25 | 19 | 14 | **2** |
| **Total** | **R$ 56,81** | **669** | **30** | **22** | **17** | **2** |

**R$ 28,41 por cadastro em dois dias.** É cedo para concluir, mas é o melhor CPL
da conta até aqui: a média geral desde 14/08 é R$ 76,89. Vale acompanhar antes de
mexer em qualquer coisa.

### Estado anterior, para histórico

Em 31/08 o anúncio estava **IN_PROCESS**, em análise da Meta, sem entrega.

Enquanto o anúncio estiver em análise não há entrega. Costuma liberar em
algumas horas; se passar de 24h, conferir em `ads_get_errors`.

## ⚠️ Bloqueio contornado: upload de mídia

O anúncio não pôde ser criado porque **o upload de mídia está bloqueado nesta
conta**. Tanto `ads_creative_upload_video` quanto o unificado
`ads_creative_upload_media` respondem:

> "This tool is new and is being gradually rolled out across ad accounts.
> Please check back at a later date."

Não é permissão nem modo de desenvolvimento do app: criação de campanha,
conjunto e anúncio funcionam. É rollout gradual da Meta, só para upload.

**Contornado:** o anúncio foi montado à mão no Ads Manager. O vídeo segue
publicado em `https://juria.hub3ps.com/juria-institucional-9x16.mp4`, que é o
caminho para quando o upload por API destravar.

## Copy publicada

5 variações por campo, conforme `creatives/meta-ads/DIRETRIZES-COPY.md`.
Contagem conferida contra os limites do Meta.

### Texto principal (125)

1. Prazos numa planilha, processos noutro sistema, financeiro à parte. O JurIA junta tudo num só lugar. *(100)*
2. As intimações do DJe chegam capturadas, com o prazo já calculado e lançado na agenda. Sem abrir o tribunal. *(107)*
3. Todos os módulos liberados em todos os planos, a partir de R$ 199/mês. Sem upgrade para desbloquear função. *(107)*
4. Software house desde 1999. O JurIA é produto de quem mantém sistema crítico em produção há mais de duas décadas. *(112)*
5. Prazos, processos, financeiro e inteligência jurídica no mesmo sistema. Teste 14 dias com os seus dados reais. *(110)*

### Título (40)

1. JurIA · Sistema Jurídico com IA *(31)*
2. Sistema jurídico para advogados *(31)*
3. Plataforma jurídica completa *(28)*
4. Software para escritórios de advocacia *(38)*
5. O sistema do seu escritório *(27)*

### Descrição (30)

1. Teste 14 dias grátis *(20)* · trial
2. Mobiletec, desde 1999 *(21)* · autoridade
3. Todos os módulos incluídos *(26)* · trial
4. A partir de R$ 199/mês *(22)* · trial
5. Feito no Brasil, com LGPD *(25)* · autoridade

**CTA:** Saiba mais · **Página:** Juria - Sistema Jurídico (`1079690555235842`)

> "Sem cartão" foi deliberadamente evitado: no briefing isso aparece como
> recomendação (cobrar no dia 12 do trial), não como implementação confirmada.

## O que observar nos próximos dias

- Sair de `IN_PROCESS`, porque sem isso não há entrega
- Primeiro CPL contra a meta de R$ 100 (a campanha do Sul está em R$ 76,98)
- Frequência: o público nacional deve demorar muito mais a saturar que o de SC,
  que estourou o teto de 1,8 em duas semanas
- Se o `utm_content` novo aparece separado no relatório
