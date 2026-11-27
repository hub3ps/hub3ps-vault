---
tipo: cliente-doc
cliente: juria
atualizado: 2026-11-27
autor: claude
origem: agencia_marketing, clients/juria/helena/roteiro-INST-AVT-01.md (migrado em 27/11/2026)
---
# Roteiro · INST-AVT-01 · vídeo de teste com a avatar

> ⚠️ Roteiro de anúncio de setembro, nunca produzido. Fala em 14 dias de trial,
> que hoje é 7, e é anterior aos planos de 29/09. Revisar antes de usar.

Primeiro vídeo com a **Helena** ([[04-clientes/juria/helena/persona|persona]]). Peça de teste
para a campanha institucional Brasil (`juria-leads-br-2708`), que é a de melhor
CPL da conta.

| | |
|---|---|
| **ID** | INST-AVT-01 |
| **`utm_content`** | `inst_avatar_cinco_sistemas_v1` |
| **Duração alvo** | 30 segundos |
| **Cortes** | 9:16 · 4:5 · 1.91:1 |
| **Tom** | Linha A, Tech-modern (default de Meta Ads no `brand.md`) |
| **O que testa** | Se rosto falando bate o motion puro do INST-VID-01, que hoje está em R$ 28,41/cadastro |

---

## Roteiro principal

> Fala corrida, sem pausa dramática. Helena é direta, não apresenta, conversa.

| Tempo | Fala | Na tela |
|---|---|---|
| **0 a 5s** | "Seu escritório paga quatro, cinco sistemas diferentes. E nenhum deles conversa com o outro." | Helena, meio corpo. Nada além dela. O gancho é a frase |
| **5 a 10s** | "O prazo está num. O financeiro, em outro. O contrato, no WhatsApp de alguém." | Corte para tela dividida em blocos desconexos, cada um com um ícone diferente |
| **10 a 13s** | "O JurIA junta isso num sistema só." | Os blocos colapsam num painel único. Logo entra aqui, discreta |
| **13 a 19s** | "Você sobe o PDF do processo e a IA preenche o cadastro sozinha: partes, valores, tribunal." | Tela do sistema: PDF sendo solto, campos preenchendo |
| **19 a 25s** | "Ela monitora STF e STJ e te avisa quando um precedente muda o jogo." | Alerta de precedente aparecendo no painel |
| **25 a 30s** | "Quatorze dias grátis, todos os módulos, sem cartão." | Helena de volta. CTA e `juria.app.br` |

**Texto total:** 66 palavras. Em ritmo de fala natural em português, dá 28 a 31
segundos.

---

## Três ganchos alternativos

Mesmo corpo, primeiros 5 segundos trocados. **É isto que se testa primeiro**, não
o roteiro inteiro: o gancho decide 80% do resultado e é o mais barato de refazer.

**Gancho B, ângulo custo**
> "Some o que você paga de software por mês. Agora imagine isso numa conta só."

**Gancho C, ângulo tempo**
> "Quanto tempo seu time gasta cadastrando processo na mão? Esse é o número que importa."

**Gancho D, ângulo visibilidade**
> "Se o sócio quer saber como o escritório está hoje, ele pede relatório pra alguém. E espera."

Os três emendam direto em "O JurIA junta isso num sistema só" ou levam duas
frases de ponte antes.

---

## Versão curta, 15 segundos

Para Reels e Stories, onde a retenção cai mais rápido.

> "Seu escritório paga quatro, cinco sistemas diferentes, e nenhum conversa com o
> outro. O JurIA junta tudo num só: a IA lê o processo, preenche o cadastro e
> monitora STF e STJ pra você. Quatorze dias grátis, sem cartão."

**33 palavras.** Cerca de 15 segundos.

---

## Cada afirmação e de onde ela sai

Regra do `DIRETRIZES-COPY.md`: nada entra sem existir na LP.

| Fala | Fonte |
|---|---|
| "quatro, cinco sistemas diferentes" | `brief.md`, dor 1: 4 a 6 ferramentas separadas |
| "a IA preenche o cadastro: partes, valores, tribunal" | LP, "Extração inteligente de documentos" |
| "monitora STF e STJ e te avisa quando um precedente muda o jogo" | LP, "Inteligência de Precedentes STF e STJ" |
| "painel com pipeline, prazos e DRE" | LP, "Dashboard executivo para o sócio" |
| "14 dias grátis, todos os módulos, sem cartão" | `DIRETRIZES-COPY.md`, eixo trial |

---

## Notas de produção

**Legenda queimada, sempre.** A maior parte assiste sem som. Sem legenda, o
roteiro inteiro se perde. O `edge-tts` já exporta `.srt` junto da locução.

**Sem "oi pessoal" e sem logo antes da fala.** Os três primeiros segundos são o
único ativo real. Gastar com abertura é jogar fora.

**No 9:16, conteúdo nos dois terços superiores.** O rodapé é ocupado pela
interface do story.

**A Helena não vira advogada.** Nenhuma tela de tribunal, nenhuma toga, nenhum
comentário sobre tese ou estratégia processual. Ela mostra o sistema.

**Identificar como avatar.** Uma linha na descrição do anúncio resolve.

---

## O que falta

- ⬜ Ana aprovar a Helena antes de produzir
- ⬜ Copy de Ads Manager: rodar `/skill ad-creative`, 5 variações por campo
- ⬜ Definir se a locução sai do OpenArt ou do `edge-tts`, como no INST-VID-01
- ⬜ Gerar os três cortes
