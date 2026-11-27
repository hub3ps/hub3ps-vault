---
tipo: processo
atualizado: 2026-11-27
autor: claude
origem: agencia_marketing/docs/processos/video-juria.md (migrado em 27/11/2026)
---
# Vídeo para o JurIA

> Caminhos de arquivo e comandos são do repo `agencia_marketing` (`~/Desktop/agencia_marketing`), salvo quando outro repo é citado.

Do roteiro ao MP4 pronto para subir. Feito em Remotion (React renderizado em
MP4, sem custo por render) com locução do ElevenLabs.

Técnica de Remotion, áudio e armadilhas: skill `remotion-video`
(`.claude/skills/remotion-video/`). Este runbook é só o caminho do JurIA.

---

## 0. Antes de escrever uma linha

Confira os fatos que mudam. Vídeo com preço ou prazo velho já aconteceu.

- [ ] **Planos e trial:** `clients/juria/comercial/planos-e-creditos.md`.
      Não use o `brief.md` para número. Em 19/10/2026: trial de 7 dias, a
      partir de R$ 69 (Solo). "Todas as funcionalidades" só vale do Plus em diante.
- [ ] **Marca:** `clients/juria/brand.md`, paleta navy + ciano, Inter.
- [ ] **Eixo:** todo criativo declara um (Categoria, Consolidação ou
      Inteligência), ver `brief.md`.

## 1. Roteiro

Estrutura que já funcionou (INST-VID-02/03, cerca de 25s):

| Ato | Tempo | O que faz |
|---|---|---|
| Gancho | 0 a 4s | Fala com o público pelo nome ("Advogado, ...") e mostra a dor |
| Pergunta | 4 a 8s | Uma pergunta que incomoda |
| Produto | 8 a 15s | Interface respondendo com números |
| Marca | 15 a 19s | Logo e a promessa |
| Chamada | 19 a 25s | Trial grátis, botão com clique, cartão final com site e preço |

Escreva a locução como fala, não como folheto, e numa frase por cena. Aprove o
roteiro com o Guilherme **antes** de gerar voz: a voz gasta crédito.

## 2. Formato

Um 9:16 (1080×1920) serve Reels, Stories e o feed, que corta para 4:5. Para
isso o conteúdo importante fica:

- entre **y = 300 e y = 1500**, fora do topo (perfil) e do rodapé (legenda e botões);
- dentro da **faixa central 4:5** (1080×1350).

Confira na prévia de posicionamentos do Ads Manager antes de subir.

## 3. Projeto

```bash
cd clients/juria/creatives/_video
npm install
```

Cada vídeo é uma pasta em `src/` e uma `<Composition>` em `src/Root.tsx`. O
mais recente (`src/ju/`, IG-VID-01) é o melhor ponto de partida: cenas em
`Cenas.tsx`, celular com WhatsApp e teclado em `Whatsapp.tsx`, linha do tempo e
tabela de cortes em `tempo.ts`.

**Locução corrida, cenas no tempo da palavra.** Escreva o roteiro como texto
corrido, gere a voz numa tomada só e transcreva o MP3 com o ElevenLabs Scribe
(`creative_transcribe_audio`), que devolve início e fim de cada palavra. O
`tempo.ts` converte esses segundos em quadros com `q(s)`, e cada cena entra
na palavra que a anuncia. Aprovar texto e áudio com o Guilherme antes do vídeo.

**Imagem sempre com `<Img>`.** Foto como `background-image` em CSS não é
esperada pelo Remotion e sai vazia em alguns quadros do render. Ele usa `src/movimento.ts`, que implementa as regras de
`references/movimento.md` da skill (curva EO/EI, corte com velocidade casada,
desfoque derivado, digitação carimbada, mola do logo). Peças visuais e paleta
continuam em `src/categoria/ui.tsx`.

```bash
npx remotion still <Composicao> out/f300.png --frame=300   # um quadro
npx remotion render <Composicao> out/video.mp4             # vídeo inteiro
```

Confira os quadros-chave de cada cena antes de mostrar a alguém. Render sem
erro não quer dizer imagem certa.

## 4. Locução (ElevenLabs)

Pelo MCP do ElevenLabs, plano Starter da conta. Detalhes e armadilhas na
skill: `references/audio.md`.

| Item | Valor |
|---|---|
| Voz | Bianca (`9LwXyqQB0mUwtLRsS227`), feminina, pt-BR |
| Modelo | `eleven_v4` |
| Nome do produto no texto falado | **`Júri-á`** (ver `brand.md`). Na tela continua `JurIA` |

1. Gere **uma frase por vez**. Mais de uma ao mesmo tempo entra em fila.
2. Baixe logo (o link expira em 2 horas) para `public/<pasta-da-voz>/`.
3. Nivele cada arquivo (comando em `references/audio.md`).
4. Meça a duração com `ffprobe` e acerte entrada e duração de cada fala em `tempo.ts`.
   Se uma fala não couber na cena, `atempo=1.05` resolve.

## 5. Efeitos e trilha

- **Com música:** trilha em `public/audio/` com ducking sob a voz.
- **Sem música:** os efeitos dão o ritmo. Kit em `public/sfx-ref/`, gerado por
  `python3 .claude/skills/remotion-video/scripts/sfx.py <pasta>`.

Testar as duas versões da mesma imagem é barato: é a mesma composição com um
`modo` diferente (ver `JuriaCategoria.tsx`).

## 6. Fechar o arquivo

```bash
npx remotion render <Composicao> out/video.mp4
ffmpeg -i out/video.mp4 -c:v copy -af "loudnorm=I=-14:TP=-1.5:LRA=11" \
  -ar 48000 -c:a aac -b:a 192k ../meta-ads/institucional/<ID>_<utm_content>.mp4
```

Post orgânico vai para `../instagram/` com ID `IG-VID-NN` e registro no
README da pasta; não leva `utm_content`.

Confira com `ebur128` (comando na skill): **-14 LUFS, pico abaixo de -1 dB**.

- [ ] Nome no padrão `<ID>_<utm_content>.mp4` ([[convencoes|convenções]]), ID `INST-VID-NN`
- [ ] Linha nova na tabela de vídeo de `clients/juria/creatives/meta-ads/README.md`
- [ ] Preço, trial e nome conferidos de novo **no vídeo renderizado**
- [ ] Commit com fonte, áudio e MP4 juntos
