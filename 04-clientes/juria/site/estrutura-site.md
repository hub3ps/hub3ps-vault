---
tipo: cliente-doc
cliente: juria
atualizado: 2026-11-27
autor: claude
origem: agencia_marketing, clients/juria/ESTRUTURA-site.md (migrado em 27/11/2026)
---
# Estrutura do site JurIA · páginas e menu

> **Aprovada pelo Guilherme em 14/10/2026.** Vale para o site em Astro
> (`juria-site-astro/`, branch `feat/site-astro`). A estrutura da home está em
> [[04-clientes/juria/site/estrutura-home|ESTRUTURA-home.md]]; este arquivo cuida do resto do site.

## O princípio

Página por **área de trabalho do cliente**, não por funcionalidade. Cada página
junta várias funções do sistema como seções. Quem quer ver tudo tem uma página
só com a lista completa.

Por que assim: é o que fazem os SaaS grandes e o concorrente mais próximo. O
Astrea (Aurum) tem 6 páginas por área: processos, tarefas, financeiro, equipe,
atendimento ao cliente e IA. O ADVBox só dá página própria para a IA. Uma
página por função, que foi a proposta anterior, dava 11 páginas no menu e
espalhava a autoridade de SEO.

## Menu principal

```
Recursos
├─ Processos e prazos
├─ Atendimento e WhatsApp     ★
├─ Pesquisa e jurimetria
├─ Financeiro e nota fiscal   ★
└─ Tudo o que o JurIA faz

Inteligência artificial       ★
Planos
Sobre
```

★ = os três destaques, feitos primeiro. São as funções com mais procura,
segundo o Guilherme: a IA no WhatsApp (equipe e clientes), as ações de IA, e a
nota fiscal automática.

⚠️ **O rótulo aprovado era "Todas as funcionalidades" e virou "Tudo o que o
JurIA faz"** no mesmo dia. A trava de `conferir-dados.mjs` barra "todas as
funcionalidades" sem "do Plus em diante" por perto, por causa do erro de
29/09: a frase lida sozinha promete o catálogo inteiro em qualquer plano.

## As páginas

| Página | URL | O que entra | Fonte |
|---|---|---|---|
| ★ Atendimento e WhatsApp | `/whatsapp-para-advogados` | Secretária virtual (IA que atende o cliente), WhatsApp do escritório (caixa compartilhada, lembretes, cobranças), Jú para a equipe, portal do cliente, funil de oportunidades. "A JurIA não cobra por mensagem" | `funcionalidades.md` 3.1, 3.2, 8.3 |
| ★ Inteligência artificial | `/ia-para-advogados` (existe) | Petição por seções, leitura de documentos, transcrição, resumo da intimação com prazo sugerido, assistente, análise de risco, precedentes, aviso CNJ 615/2025 | 5, 5.1, 8.4, 8.5 |
| ★ Financeiro e nota fiscal | `/financeiro-para-escritorio-de-advocacia` | **NFS-e automática** (confirmado pelo Guilherme em 14/10; NFS-e está no Solo), cobrança PIX, boleto e cartão com baixa automática, honorários, recuperação de crédito, rotinas, tarefas, desempenho | 6, 8.6 |
| Processos e prazos | `/gestao-de-processos-e-prazos` (existe) | Importação por OAB e em lote, ficha do processo, atualização automática, publicações, cálculo de prazo, prazo fatal e interno, alertas, agenda, Teams | 2, 8.1, 8.2 |
| Pesquisa e jurimetria | `/pesquisa-juridica` | Precedentes, jurisprudência, patrimonial, previdenciário, calculadora. Leva para as duas abaixo | 5, 8.5 |
| Tudo o que o JurIA faz | `/software-juridico` (existe) | A lista completa do documento da Mobiletec, mais as 15 integrações | 8 inteira |

**Fora do menu, mas no ar:** `/jurimetria` e `/due-diligence-juridica`, já
prontas, com link a partir de "Pesquisa e jurimetria". Também `/precos`,
`/sobre`, os 3 comparativos, o blog e as páginas legais, como hoje.

**Na home:** cada aba da pasta do bloco 7 ganha um link para a página da área.

## SEO, GEO e AEO

Pedido do Guilherme: atenção máxima nas três páginas de destaque.

- **Palavra-chave antes do texto.** A URL, o título e o H1 de cada página
  saem de uma pesquisa de termo, feita no início de cada página. Não chutar.
- **Uma pergunta por seção, resposta nas duas primeiras frases.** É o formato
  que buscador e modelo de IA extraem. O padrão já existe em `src/data/paginas.ts`.
- **FAQ com `FAQPage` em JSON-LD** em cada página, e a página entra no
  `llms.txt`.
- **Fato verificável, nunca adjetivo.** Número de integrações, plano em que a
  função está, o que custa. Sem "o melhor", sem "revolucionário".

## Dúvidas para o fim

Decisão do Guilherme em 14/10: o que ficar em dúvida é anotado e resolvido no
final, sem travar a copy. A lista viva está na seção 8.9 do
`agencia_marketing/clients/juria/comercial/funcionalidades.md`.

## Páginas escritas em 14/10/2026

As oito páginas de área estão no ar com texto completo. O texto mora em
`juria-site-astro/src/data/paginas-area/<slug>.json`; pesquisa SEO, briefing,
log de revisão e dúvidas em `agencia_marketing/clients/juria/rascunhos-paginas`. As URLs
provisórias (`/atendimento-e-whatsapp`, `/pesquisa-e-jurimetria`,
`/financeiro-e-nota-fiscal`) redirecionam com 301 pelo `vercel.json`.

