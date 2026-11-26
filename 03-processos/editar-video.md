---
tipo: processo
status: rascunho
versao: v0
atualizado: 2026-11-26
autor: claude
---
# Editar vídeo falado (Reels do @guimiguelmkt)

O Claude edita o vídeo bruto gravado no iPhone: corta enrolação, repetição e respiros, põe legenda e as logos das ferramentas citadas. Tudo roda no Mac, sem serviço externo e sem custo.

**Estado:** v0, a primeira edição (IMG_2087, 11/11/2026). O Guilherme vai editar o mesmo vídeo à mão, e a diferença entre as duas edições vira as regras da v1. Meta: o Claude editar do jeito que o Guilherme gosta, e este runbook virar skill.

**Ferramenta:** `ferramentas/editar-video/` no repo `agencia_marketing`. O estilo fica em `estilo.json`, e cada vídeo tem uma pasta em `projetos/<AAAA-MM-DD>-<id>/`.

## Passo a passo
1. **Vídeo no Mac:** o Guilherme salva o bruto em `~/Downloads`. O Fotos do iCloud pode demorar a sincronizar. O caminho mais rápido é arrastar o arquivo da janela do espelhamento do iPhone ou mandar por AirDrop
2. **Projeto:** criar `projetos/<data>-<id>/projeto.json`, com `fonte` e `saida` (mesmo nome, com `_editado.mp4`, em `~/Downloads`)
3. **Transcrever:** `.venv/bin/python -I editar.py transcrever projetos/<id>`. Gera o tempo de cada palavra e lista os silêncios
4. **Escolher o que fica (Claude):** ler a transcrição e preencher `manter` com os trechos, no tempo do original
5. **Conferir o plano:** `editar.py plano projetos/<id>` mostra a duração e a legenda inteira. Revisar o texto da legenda
6. **Teste:** `editar.py render projetos/<id> --teste 8`. Olhar os quadros: legenda e selos no lugar, sem cobrir o rosto
7. **Render:** `editar.py render projetos/<id>`. Leva uns 4 min para 1 min 40 s de vídeo
8. **Conferir o áudio:** `editar.py conferir projetos/<id>` retranscreve o vídeo pronto. Palavra cortada ou estranha ("mectores", "se defaça") é emenda suja: ajustar o trecho e renderizar de novo

## Legenda no formato do Edits (26/11/2026)
O formato dos Reels já postados (IG-04, IG-06, IG-07). No `projeto.json`: `"legenda": "progressiva"`; estilo em `legenda_progressiva` do `estilo.json`.
- Minúscula, sem pontuação e sem borda, com sombra leve. Avenir Next Bold 44, centro em y 1560 de 1920, no peito, longe da boca
- A frase se monta palavra a palavra, e cada palavra entra direto, branca. O Guilherme recusou a versão em que a palavra entrava apagada e acendia (parecia borrada) e a de letra 52 em y 1450 (grande e perto da boca)
- **Título no começo** (`"titulo": {"linhas": [...], "ate": 6}`): caixa branca arredondada **no alto** (y 200), texto preto em Avenir Next Bold 46, por 6 s, igual ao do IG-06. A legenda segue no peito ao mesmo tempo. Título no peito foi recusado em 26/11
- **Sem corte:** `"corte": {"respiro": 99, "folga_antes": 0.3, "folga_depois": 0.8}` mantém o vídeo inteiro e só tira o silêncio das pontas
- Vídeo 4K do iPhone é reduzido para 1080 de largura no render
- Publicar e agendar: [[03-processos/publicar-instagram]]

## Regras de corte (v0)
- **Sai:** falso início, frase recomeçada (fica a última versão), repetição da mesma ideia, lista que se alonga sem informação nova, "tá?" no fim de frase, CTA repetido (fica o mais completo)
- **Respiro:** pausa maior que 0,30 s entre palavras sai. Cada emenda leva 0,07 s de folga antes e depois, e nunca passa da borda escolhida
- **Emenda suja:** se a palavra seguinte nasce de uma hesitação arrastada ("vocêêê faça"), a emenda pega a sílaba. Melhor trocar o trecho por outra versão da frase que comece depois de um silêncio
- **O Whisper erra o tempo** de palavra curta depois de pausa (ex.: "como" 0,2 s atrasado). Conferir com os silêncios e corrigir em `substituir`
- **Só tirar respiro, sem legenda** (criativo de anúncio, 26/11/2026): `cortar_respiros.py projetos/<id>`, depois do `transcrever`. Ele corta pelo volume do áudio, só dentro do silêncio de verdade, com 0,06 s de folga. O corte pelo tempo do Whisper comeu a primeira sílaba em 5 de 5 vídeos ("preenche" virou "enche", "clica" virou "fica"). Conferir retranscrevendo a saída: diferença longe de emenda é variação do Whisper ("sua" e "tua"), não corte

## Regras visuais (v0)
- **Cor:** a do original. O iPhone grava em HDR (HLG, 10 bits), e o vídeo sai em HLG, 10 bits
- **Legenda:** Arial Bold 66, branca com borda preta, até 4 palavras por bloco, na altura do peito (y 1330 de 1920). Branco em ~83%: no HDR, 100% estoura o brilho na tela do celular
- **Correções de legenda:** "cloud" vira Claude, "Vercell" vira Vercel
- **Logos:** selo claro com ícone e nome, no alto, na palavra que cita a ferramenta. Lista de ferramentas empilha os selos. Ícones do simple-icons. O Claude Code usa o ícone do Claude

## O que comparar na edição manual do Guilherme
TODO: preencher quando ele mandar a edição dele do IMG_2087.
- Duração final e quais trechos ele manteve que eu cortei, e o contrário
- Ritmo: ele corta respiro mais curto ou mais longo
- Legenda: tamanho, posição, quantas palavras, destaque de palavra
- Logos: tamanho, posição, tempo na tela, animação
- Algo que ele pôs e eu não: zoom, corte de câmera, música, efeito sonoro, B-roll
