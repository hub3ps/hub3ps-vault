---
tipo: cliente-doc
cliente: juria
atualizado: 2026-11-27
autor: claude
origem: agencia_marketing, clients/juria/helena/roteiro-INST-AVT-02-gemini.md (migrado em 27/11/2026)
---
# Roteiro · INST-AVT-02 · vídeo de 30s gerado no Gemini

> ⚠️ Roteiro de anúncio de setembro, nunca produzido. Fala em 14 dias de trial,
> que hoje é 7, e é anterior aos planos de 29/09. Revisar antes de usar.

Versão para gerar em **Gemini/Veo**, em blocos de 7 segundos. Personagem: a
**Helena** ([[04-clientes/juria/helena/persona|persona]]).

| | |
|---|---|
| **ID** | INST-AVT-02 |
| **`utm_content`** | `inst_avatar_cinco_sistemas_v2` |
| **Estrutura** | 4 blocos de 7s (28s) + 2s de cartela final estática |
| **Formato** | 9:16 vertical, 1080×1920 |
| **Tom** | Linha A, Tech-modern |

---

## Os 30 segundos

| Bloco | Tempo | Fala | O que acontece |
|---|---|---|---|
| **1** | 0 a 7s | "Seu escritório paga quatro, cinco sistemas diferentes. E nenhum deles conversa com o outro." | Helena falando, aproximação lenta |
| **2** | 7 a 14s | "O JurIA junta tudo num só. Você sobe o PDF do processo e a IA preenche o cadastro sozinha." | Helena gesticula para a tela; corte para o sistema |
| **3** | 14 a 21s | "Ela monitora STF e STJ e te avisa quando um precedente muda o jogo." | Alerta de precedente no painel |
| **4** | 21 a 28s | "Pipeline, prazos e DRE num painel só. Quatorze dias grátis, sem cartão." | Dashboard, volta para Helena |
| **cartela** | 28 a 30s | sem fala | Logo, `juria.app.br`, CTA. **Estática, não se gera no Veo** |

---

## ⚠️ O bloco de personagem é obrigatório em todos os prompts

Veo não guarda memória entre gerações. Se você não colar a **mesma descrição
literal** da Helena em cada um dos quatro prompts, sai uma mulher diferente em cada
bloco e o vídeo não emenda.

Copie o bloco `SUBJECT` e o `WARDROBE` palavra por palavra, sem reescrever.

---

## BLOCO 1 · 0 a 7 segundos

```
FORMAT: Vertical video, 9:16 aspect ratio, 1080x1920, 7 seconds, photorealistic.

SHOT: Medium shot, waist-up framing, camera at her eye level. Very slow, almost
imperceptible dolly push-in over the full 7 seconds. Locked horizon, no handheld
shake, no whip pans.

SUBJECT: A 33-year-old Brazilian woman named Helena. Light brown skin with visible
natural texture and pores, no heavy retouching or skin smoothing. Dark brown
straight hair, shoulder length, parted slightly off-center, with soft natural
movement. Warm brown eyes, natural defined eyebrows, minimal makeup with a
neutral lip. Calm and composed expression, a restrained closed-lip smile, direct
and steady eye contact with the lens. Average build, upright posture, relaxed
shoulders. She reads as a competent software professional in her early thirties,
not as a model and not as a social media influencer.

WARDROBE: A well-tailored deep navy blazer with notch lapels, worn open over a
plain off-white crew-neck top. No patterns, no prints, no visible logos or
branding anywhere on the clothing. One small gold stud earring. No necklace, no
rings, no watch.

PERFORMANCE: She speaks directly to the lens, calm and conversational, as if
talking to one person across a desk rather than presenting to an audience. Her
delivery is unhurried and matter-of-fact, with quiet confidence and no
enthusiasm or salesmanship. On the second sentence she makes one small,
economical open-hand gesture at chest height, then lets the hand settle. Natural
blinking, subtle micro-expressions, a slight head tilt on the final words.

DIALOGUE (Brazilian Portuguese, natural adult female voice, medium-low pitch,
clear diction, unhurried pace): "Seu escritório paga quatro, cinco sistemas
diferentes. E nenhum deles conversa com o outro."

SETTING: A bright, modern software company office. Helena stands in the mid-ground.
Behind her, thrown softly out of focus: a large monitor displaying a dark navy
analytics dashboard with small cyan data highlights, a low white shelf holding a
few books and a single green plant, and a frosted glass partition wall. The
space is clean, contemporary and uncluttered. No people in the background.

LIGHTING: Soft natural daylight entering from a large window to camera left,
acting as the key light and modelling her face gently. Soft bounce fill from
camera right keeps the shadow side open. No hard shadows, no dramatic contrast,
no coloured gels, no neon, no rim light.

COLOR PALETTE: Deep navy #0A2540 dominant in the wardrobe and the background
screen. Sparing cyan #14B4C8 accents appearing only on the monitor behind her.
Neutral off-white walls. Overall calm, corporate and slightly desaturated.

LENS AND DEPTH: 50mm equivalent, shallow depth of field around f/2.0. Helena is
tack sharp; the background falls into smooth, even blur with no busy or
distracting bokeh shapes.

AUDIO: Her voice recorded close and clear, as if on a lavalier microphone, dry
and present with almost no room reverb. Underneath it, very low quiet office
ambience. No music. No sound effects. No audience, no laughter, no applause.

STYLE: Photorealistic corporate editorial video. Natural film grain, true skin
tone and texture, restrained contrast. It should look like a well-shot brand
film, not like a stock video, not like a glamour shoot, and not like an
influencer selfie video.

AVOID: No courtroom, no judge's gavel, no scales of justice, no legal robes or
gowns, no shelves of law books, no marble, no gold. No studio ring light, no
coloured bokeh, no lens flares, no smoke or haze. No trendy or fashion styling.
No waving hello, no pointing at the camera, no exaggerated hand gestures, no
head bobbing. No on-screen text, no burned-in captions, no logos or watermarks
in frame. No cuts, no transitions, no zoom snaps: this is one continuous take.
```

---

## Antes de gerar o bloco 2

Gere o bloco 1 primeiro e olhe o resultado. Três coisas que costumam sair
erradas na primeira tentativa e que é melhor descobrir agora:

1. **Idade e expressão.** Veo tende a rejuvenescer e a sorrir demais. Se vier
   com cara de 24 anos ou sorriso aberto, reforce "early thirties" e "restrained
   closed-lip smile, no wide smiling".
2. **Sincronia da fala.** Se a boca não casar com o português, vale gerar sem
   diálogo e dublar depois com `edge-tts`, como foi feito no INST-VID-01.
3. **O fundo.** Se a tela ao fundo aparecer com texto legível e errado, troque
   por "an abstract dark dashboard with no readable text".

Só depois que a Helena estiver do jeito certo é que valem os blocos 2, 3 e 4. Se
ela mudar agora, todos teriam que ser refeitos.

---

## Blocos 2, 3 e 4

Ainda não escritos, por decisão: dependem do resultado do bloco 1. O `SUBJECT`,
o `WARDROBE`, o `SETTING`, o `LIGHTING` e o `AVOID` serão idênticos aos daqui.
Muda apenas `SHOT`, `PERFORMANCE`, `DIALOGUE` e o que aparece na tela.

## Rastreio das afirmações

| Fala | Fonte |
|---|---|
| "quatro, cinco sistemas diferentes" | `brief.md`, dor 1: 4 a 6 ferramentas |
| "a IA preenche o cadastro sozinha" | LP, "Extração inteligente de documentos" |
| "monitora STF e STJ e te avisa quando um precedente muda o jogo" | LP, "Inteligência de Precedentes STF e STJ" |
| "Pipeline, prazos e DRE num painel só" | LP, "Dashboard executivo para o sócio" |
| "14 dias grátis, sem cartão" | `DIRETRIZES-COPY.md`, eixo trial |
