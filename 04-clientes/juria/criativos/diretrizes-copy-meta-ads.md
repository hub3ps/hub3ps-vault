---
tipo: cliente-doc
cliente: juria
atualizado: 2026-11-27
autor: claude
origem: agencia_marketing, clients/juria/creatives/meta-ads/DIRETRIZES-COPY.md (migrado em 27/11/2026)
---
# Diretrizes de copy — anúncios Meta (JurIA)

Regras fixas para todo anúncio novo. Valem para qualquer nicho.

## Sempre entregar 5 variações de cada campo

O Meta rotaciona e aprende qual combinação performa. Um campo com uma opção só
desperdiça isso.

| Campo | Limite | O que ele tem que fazer |
|-------|--------|-------------------------|
| **Texto principal** | 125 | **Complementar o criativo** — dizer o que a imagem não diz, sem repetir a headline da arte. |
| **Título** | 40 | **Converter o clique** dizendo o que o produto é. |
| **Descrição** | 30 | **Reforçar o argumento decisivo** — trial e autoridade. |

## Título: diga o que o sistema é

O título não é lugar de hook nem de dor — isso já está no criativo e no texto
principal. Aqui o leitor precisa entender **o que está sendo anunciado**, para
decidir se clica.

Padrão: `JurIA · Sistema Jurídico com IA`, `Sistema jurídico para advogados`,
`Software para escritórios`, `Plataforma jurídica completa`.

Evitar: título que repete o hook do criativo, ou que descreve só uma
funcionalidade solta ("Jurimetria por vara"). A funcionalidade cabe no texto
principal.

## Descrição: trial e autoridade

Dois eixos, alternando entre as 5 variações:

- **Trial** — 14 dias grátis, sem cartão, todos os módulos liberados.
- **Autoridade** — Mobiletec, software house desde 1999, LGPD nativa.

## Formatos: sempre os três cortes

Todo criativo sai em três arquivos, um por grupo de posicionamento:

| Corte | Tamanho | Cobre |
|-------|---------|-------|
| 4:5 | 1080×1350 | Feed (e 3:4, 2:3 por corte automático) |
| 9:16 | 1080×1920 | Stories e Reels |
| 1.91:1 | 1200×628 | Coluna da direita, busca, in-stream (e 16:9, 3:2, 5:4) |

O Ads Manager aceita um asset por **grupo** de posicionamento, não um por
proporção — por isso três, e não oito.

No 9:16, manter o conteúdo nos dois terços superiores: o rodapé é ocupado pela
interface do story. No 1.91:1, refluir o texto em vez de esticar o layout
vertical.

## Criativos stealth (formato post)

O texto principal fica em **primeira pessoa**, no mesmo tom da arte. Se o anúncio
falar como marca ("Conheça o JurIA…") e a imagem falar como pessoa, quebra a
ilusão de post orgânico — que é justamente o que faz o formato funcionar.

## UTM: o que vai em cada parâmetro

| Parâmetro | Carrega | Exemplo |
|-----------|---------|---------|
| `utm_source` | fixo | `meta` |
| `utm_medium` | fixo | `paid` |
| `utm_campaign` | a campanha no Meta | `juria-leads-sul-2606` |
| `utm_content` | **o criativo** | `trab_nat_c`, `trab_sistemas_v1` |
| `utm_term` | **o público / a segmentação do conjunto** | `trabalhista_aberto`, `trabalhista_interesses` |

O `utm_term` é do **conjunto**, não do criativo. Quem duplica um conjunto para
testar outra segmentação só troca o `utm_term` — e aí o relatório cruza
"qual criativo" (`utm_content`) com "qual público" (`utm_term`).

Erro a evitar: usar `utm_term` para descrever a linha do criativo. Isso duplica o
que já está no `utm_content` e deixa os conjuntos indistinguíveis quando um é
duplicado para teste de público.

Alternativa quando duplicar conjunto virar rotina: preencher o campo
"Parâmetros de URL" do Meta com `{{campaign.name}}`, `{{ad.name}}` e
`{{adset.name}}` — preenche sozinho, ao custo de valores menos limpos no
relatório.

## Antes de publicar

- Conferir a contagem de caracteres campo a campo; o Meta trunca sem avisar.
- Toda afirmação sobre o produto precisa existir de verdade — conferir na LP do
  nicho (`source/lp_<nicho>/sections/beneficios.jsx`) antes de escrever.

> **Ano da Mobiletec: sempre 1999** (decisão do Guilherme em 28/10/2026). Nas
> descrições use "Mobiletec, desde 1999", que não envelhece. Os anúncios que
> subiram em 30/09 dizem "desde 2000": é erro, não a regra. O material antigo
> também fala em "25 anos de engenharia BR"; não use.
