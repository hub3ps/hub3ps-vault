---
tipo: cliente-doc
cliente: mobiletec
atualizado: 2026-11-27
autor: claude
origem: agencia_marketing, branch claude/loving-archimedes-rp33cv, clients/mobiletec/video/README.md (migrado em 27/11/2026)
---
# Vídeo institucional Mobiletec

Pedido de 21/10/2026: vídeo em motion, de 45 s a 1 min 30 s, em loop num
evento, só com música de fundo. **Fase: primeira versão entregue em 27/10/2026.**

- **Perguntas para a Mobiletec:** doc em
  [claude.ai/artifact/PLyiXYFRrqbp1Zbq4B8NWw](https://claude.ai/artifact/PLyiXYFRrqbp1Zbq4B8NWw).
  A versão respondida é o Google Docs no Drive do Guilherme,
  "Vídeo institucional Mobiletec - Briefing para confirmar"
- **Referência enviada por eles:** `../source/referencia-video-flowee.mp4`

## A referência

30 s, 1920 x 1080, sem áudio. É do **Flowee**, assinado "Flowee · Mobiletec",
não da Mobiletec. Estrutura: frase de impacto, logo, visão geral com tela real,
"Sem papel. Sem planilha.", cinco funcionalidades numeradas (checklists do dia,
formulários sob medida, processos BPMN, gere com IA, PDF do seu jeito), cada uma
com tela real, e fechamento com logo, slogan "Sua operação, em fluxo." e três
selos (multiempresa, IA integrada, auditoria completa).

O Flowee é um produto da Mobiletec. A referência vale pelo formato e pelo
ritmo, não pelo tema.

## Definido pelo Guilherme (21/10/2026)

- **Institucional da Mobiletec**, não de produto. Passa em loop ao fundo da
  apresentação de um produto num evento. Sem estande, sem QR code, sem chamada
  final
- **Formato igual ao do Flowee:** horizontal 16:9, 1920 x 1080, MP4
- **Só em português.** Prazo: o mais rápido possível
- **Proposta enviada para confirmar:** 60 s, só música (ou narração por voz de
  IA, eles escolhem), seis cenas: logo se desenhando, "Sistemas que sustentam
  operações críticas há mais de 25 anos", o que fazemos, como trabalhamos,
  produtos próprios (Flowee e JurIA), clientes e fechamento
- **A música é nossa escolha** (trilha livre de direitos). Não se pede à Mobiletec
- **Telas: só dos produtos que aparecerem no vídeo**, e só se forem mostrados.
  As do JurIA nós tiramos, da conta com dados fictícios do Guilherme

## Respostas da Mobiletec (Everton, 22/10/2026)

- **Duração:** até 1 min 30 s, se houver material
- **Formato, idioma, uso e visual:** confirmados como propostos
- **Áudio:** testar as duas versões, só música e com narração. Voz masculina.
  Eles têm API da ElevenLabs
- **Foco: produtos para a indústria de alimentos.** Destaque para Plataforma de
  certificação da Bello (projeto do cliente), CertiHub, Flowee, VendAI e
  RoterizAI. Os apresentados no evento, com mais peso: Bello, CertiHub e Flowee.
  **O JurIA fica fora**
- **Logos dos 13 clientes:** liberados
- **Números e slogan:** não entram
- **Restrições:** nenhuma no material que eles vão enviar

## Materiais da Mobiletec (27/10/2026)

Dois zips, "Design Kits - Mobiletec" e "AFV": para cada um dos 5 produtos,
`descricao.txt`, logos (SVG e PNG), telas em 4K e cores. Os originais não
foram para o repo; o que o vídeo usa está em `_video/public/produtos/`.

- Nomes como nos logos: **"Hub de Certificação"** (não "CertiHub") e
  **"VendeAI"** (não "VendAI")
- Bello: só um PNG de 260 x 146 px. Vai numa placa clara, pequeno. Pedir SVG se
  houver segunda versão
- Telas de login ficaram de fora

## Como foi feito

Projeto Remotion em `_video/` (código em `agencia_marketing/clients/mobiletec/video/_video/`, na mesma branch): 90 s, 12 cenas, duas
versões (só música e com locução). A abertura é a animação da logo do site.

## Entregas

Em `entregas/`, normalizada a -14 LUFS:

- `mobiletec-institucional-v6-locucao.mp4`: 68 s, sexta versão (27/10/2026), com os
  ajustes da Mobiletec (Flowee, logo, Vibra Foods, RoterizAI, Bello).
  Motion contínuo, locução corrida, trilha baixinha e fechamento "Mobiletec
  Sistemas que sustentam a sua operação."

## Pendências

- **Ano de fundação:** o vídeo diz 1999 (doc respondido pela Mobiletec); o
  site novo ainda diz 2000 (`mobiletec-site-astro/src/data/site.ts`). Alinhar
- **Pronúncia de "Mobiletec"**: só aparece sozinho, no começo e no fim, com os
  áudios aprovados pelo Guilherme
