---
tipo: processo
atualizado: 2026-11-27
autor: claude
origem: agencia_marketing/docs/processos/novo-criativo.md (migrado em 27/11/2026)
---
# Produzir um criativo

> Caminhos de arquivo e comandos são do repo `agencia_marketing` (`~/Desktop/agencia_marketing`), salvo quando outro repo é citado.

Três caminhos, conforme a peça. Todos terminam com o arquivo nomeado segundo
[[convencoes|convenções]] e salvo em
`clients/<slug>/creatives/meta-ads/<nicho>/`.

---

## Estático · fluxo v1 (estável)

```
/skill meta-creative-from-json   cliente=<slug> campanha=<slug> ratio=1x1
   ↓  6 conceitos: copy de Ads Manager + copy interna + JSON ajustado
   ↓  salva em clients/<slug>/copies/<campanha>/<YYYY-MM-DD>.md
/skill render-creative           cliente=<slug> campanha=<slug>
   ↓  2 arquivos por conceito (modo JSON + modo prompt)
   ↓  salva em clients/<slug>/creatives/<campanha>/<YYYY-MM-DD>/conceito-N/
[manual] cola em Gemini / Nanobanana / GPT-Image / Claude Design
```

## Estático · fluxo v2 (experimental)

Separa as responsabilidades e ataca a baixa variação visual: o pool de templates
é o ratio inteiro, não só o nicho do cliente, e há penalidade de reuso para
forçar 6 templates distintos.

```
/skill ad-creative                 ← só a copy de Ads Manager
/skill meta-creative-from-json-v2  ← copy interna + JSON + render embutido
   ↓  salva uma pasta com 1 .md por conceito + README
[manual] para cada conceito-N.md: anexa o PNG da logo indicado no header
         e cola o arquivo inteiro na ferramenta de imagem
```

**Qual usar?** O v2 ainda não foi comparado com o v1 num teste real. Enquanto
não for, o v1 é o caminho seguro e o v2 é o que vale testar quando os 6
conceitos do v1 saírem visualmente parecidos demais. As duas leem a **mesma**
biblioteca.

---

## Vídeo · Remotion

React renderizado quadro a quadro em MP4 via Chrome headless. Local, sem API de
IA, sem custo por render. O texto é DOM real, então nunca sai com acento
quebrado ou palavra cortada, que é o defeito das IAs de vídeo.

```
/skill remotion-video
```

Passo a passo do JurIA (roteiro, formato, locução no ElevenLabs, efeitos,
volume final): [[video-juria|video-juria.md]].

Não serve para vídeo com pessoa real, avatar falante ou filmagem.

⚠️ **Licença:** livre até 3 funcionários. Acima disso exige Company License
antes de uso comercial. Reavaliar se a agência contratar.

---

## Antes de dar por pronto

- [ ] **Resolução:** o Meta quer ≥ 1080px no lado maior (4:5 = 1080×1350).
      Peça abaixo disso sobe, mas fica menos nítida.
- [ ] **Nome do arquivo casa com o `utm_content`** do anúncio
- [ ] **Cortes:** o Meta usa 4:5, 9:16 e 1.91:1. Uma peça só num corte perde
      posicionamento.
- [ ] **Copy:** 5 variações de texto principal, título e descrição
      (`creatives/meta-ads/DIRETRIZES-COPY.md`)
- [ ] **Registrado** na tabela do `creatives/meta-ads/README.md` do cliente
