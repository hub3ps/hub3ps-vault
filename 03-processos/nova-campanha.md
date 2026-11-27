---
tipo: processo
atualizado: 2026-11-27
autor: claude
origem: agencia_marketing/docs/processos/nova-campanha.md (migrado em 27/11/2026)
---
# Montar uma campanha no Meta

> Caminhos de arquivo e comandos são do repo `agencia_marketing` (`~/Desktop/agencia_marketing`), salvo quando outro repo é citado.

Vale para qualquer cliente. Exemplo real ao longo do texto: JurIA.

## Antes de abrir o Ads Manager

- [ ] Criativo pronto e nomeado ([[novo-criativo|novo-criativo.md]])
- [ ] Copy nas 5 variações por campo (`creatives/meta-ads/DIRETRIZES-COPY.md`)
- [ ] Slug da campanha definido ([[convencoes|convenções]])
- [ ] URL de destino com UTM montada
- [ ] Verba diária e período acordados com o cliente

## Montar

O jeito mais seguro é **replicar um conjunto que já roda** e trocar só o que
muda. Evita esquecer campo de atribuição, cobrança ou evento.

Pelo MCP da Meta: `ads_create_campaign` → `ads_create_ad_set` →
`ads_create_creative` → `ads_create_ad`.

Campos que precisam bater com o conjunto de origem:

| Campo | Onde erra |
|---|---|
| Objetivo e meta de performance | `OUTCOME_LEADS` + `OFFSITE_CONVERSIONS` |
| Evento e pixel | O pixel certo, o evento certo (`LEAD`) |
| Atribuição | 7 dias clique + 1 dia visualização |
| Orçamento | No conjunto (ABO) ou na campanha (CBO): não misture |
| Advantage+ Audience | Ligado por default; desligue se o original estava desligado |

## Registrar a ficha

**Antes de publicar**, crie a ficha em `clients/<slug>/campanhas/<slug>-<DDMM>.md`.
É o único lugar onde os IDs numéricos ficam registrados, e sem eles não dá para
puxar métrica depois.

A ficha tem que ter:

1. **IDs** dos três níveis (campanha, conjunto, anúncio) numa tabela
2. **Links diretos** para o Ads Manager
3. **Configuração replicada**: de qual conjunto veio e o que mudou
4. **Segmentação**, explícita (aberto? interesses? quais?)
5. **Histórico**: toda mudança posterior, com data e motivo

Modelo pronto: [[04-clientes/juria/campanhas/juria-leads-br-2708]].

## Depois de publicar

- [ ] Anúncio saiu de `IN_PROCESS` e entrou em entrega
- [ ] Cadastrar o anúncio/conjunto novo nos dicionários do gerador de métricas
      (no JurIA: [[atualizar-hub-juria|atualizar-hub-juria.md]], passo 2)
- [ ] Primeiro clique real chegou com a UTM certa? Confira no destino

## Armadilhas conhecidas (conta do JurIA)

- **Upload de vídeo por API bloqueado** ("gradually rolled out"): o anúncio
  precisa ser montado à mão no Ads Manager. O vídeo fica publicado numa URL
  deste repo para quando destravar.
- **App Meta em modo de desenvolvimento** faz a API recusar criação de anúncio
  em alguns conjuntos. Mesmo contorno: montar à mão.
