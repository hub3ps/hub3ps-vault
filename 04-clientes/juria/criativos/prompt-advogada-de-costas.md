---
tipo: cliente-doc
cliente: juria
atualizado: 2026-11-27
autor: claude
origem: agencia_marketing, clients/juria/creatives/_fundos/prompt-advogada-de-costas.md (migrado em 27/11/2026)
---
# Fundo reutilizável · advogada de costas no notebook

Placa de fundo para criativos estáticos do JurIA. Gerada uma vez, reusada em
várias peças trocando só a tela do notebook ou sobrepondo camada de texto.

**Ferramenta:** Gemini · **Idioma do prompt:** português
**Onde salvar depois de gerar:** `clients/juria/assets/fundos/`

---

## As duas regras que fazem essa imagem servir de fundo

**1. Tela sem texto legível.** Modelo de imagem erra texto. Pedir "JurIA" escrito
na tela devolve `JURlA`, `Juria` ou rabisco. O prompt pede **painel abstrato, sem
nenhum caractere**, e a interface real entra depois em composição. É isso que
permite trocar a tela sem regerar a imagem.

**2. Área vazia desde o início.** A advogada fica no **terço direito**. Os dois
terços da esquerda ficam limpos, para receber headline, selo e CTA. Sem isso, a
imagem vira peça única e não fundo.

---

## Prompt · v2, para regerar

> **v1 gerou uma boa imagem em 08/09/2026**, mas com dois problemas: saiu em
> 825 px de largura, abaixo dos 1080 que o Meta pede, e a área limpa acabou no
> topo em vez da lateral esquerda, porque a janela apareceu no quadro.
>
> Esta v2 corrige os dois. **Antes de colar, confira a configuração de resolução
> da ferramenta**: o prompt sozinho não controla o tamanho de saída no Gemini.
> Se ele só oferecer ~1024, gere assim mesmo e resolva no upscale.

```
Fotografia editorial corporativa, fotorrealista, em altíssima resolução e com
riqueza de detalhe, em formato vertical 4:5.

Uma advogada por volta dos 35 anos aparece de costas, vista por cima do ombro
esquerdo, trabalhando concentrada em um notebook sobre a mesa de um escritório de
advocacia moderno. Vemos apenas as costas, os ombros e a lateral da cabeça dela; o
rosto fica fora de quadro. O cabelo escuro está preso num coque baixo e discreto.
Ela veste um blazer azul-marinho profundo, bem cortado, sobre uma blusa lisa
clara. A postura é ereta e atenta, uma das mãos repousa no teclado. Ela tem a
presença de uma profissional no meio do expediente, não de uma modelo posando.

Ela está sentada no terço direito do enquadramento. O TERÇO SUPERIOR da imagem,
em toda a sua largura, é apenas parede lisa e vazia: nenhum objeto, nenhum
quadro, nenhuma luminária, nenhum detalhe. Essa faixa de cima é intencional e
precisa permanecer completamente limpa, porque vai receber texto depois. A
lateral esquerda também fica livre, mostrando somente a parede e a profundidade
da sala em desfoque suave.

A janela que ilumina a cena está fora do enquadramento, à esquerda: a luz entra
por ali e contorna o ombro dela, mas nenhuma moldura, vidro ou brilho de janela
aparece na imagem.

O notebook à frente dela está inclinado de modo que a tela apareça parcialmente.
Na tela há um painel de dados abstrato, em azul-marinho escuro: cartões
retangulares de cantos arredondados, linhas finas de gráfico, um gráfico de barras
simples e pequenos pontos de destaque em ciano. A tela não contém nenhuma letra,
nenhum número, nenhuma palavra e nenhum logotipo, apenas formas e blocos de cor,
levemente fora do foco crítico.

O ambiente é um escritório contemporâneo e silencioso, de parede neutra e quente.
Ao longe, bem desfocada e sempre abaixo da faixa superior, aparece apenas uma
estante baixa. Sobre a mesa há somente o notebook, um caderno fechado e uma
caneta.

A luz é natural e suave, de contraste baixo e sombras abertas, sem nenhum ponto de
luz dura. A paleta é dominada pelo azul-marinho profundo, presente no blazer e na
tela, com toques contidos de ciano apenas no painel de dados. O ambiente traz
cinzas neutros e off-white. O conjunto é calmo, corporativo e levemente
dessaturado.

A câmera está na altura dos olhos, um pouco atrás e acima do ombro dela, com
aparência de lente 50mm e profundidade de campo rasa, em torno de f/2.2. O ombro e
a borda do notebook estão nítidos e o fundo se dissolve num desfoque liso, sem
formas chamativas.

O acabamento é de fotografia editorial de alto padrão: textura real de pele e
tecido, grão fino e natural, contraste contido. Nada de aparência de banco de
imagem, brilho excessivo ou estética artificial.

A imagem não traz texto, marca d'água nem logotipo em lugar nenhum. Não aparecem
balança da justiça, martelo de juiz, toga, estante de códigos, mármore nem
dourado. A mesa permanece limpa e o terço superior permanece vazio.
```

### O que mudou da v1

| | v1 | v2 |
|---|---|---|
| Área de texto | "dois terços da esquerda" | **"terço superior em toda a largura"**, que foi o que funcionou |
| Janela | aparecia no quadro e sujava a lateral | **fora do enquadramento**, mas a luz continua vindo dela |
| Resolução | não pedida | "altíssima resolução e com riqueza de detalhe" |
| Estante ao fundo | livre | **sempre abaixo da faixa superior** |
| Divisória de vidro | mencionada | removida, aparecia como moldura no meio do quadro |

## Os três cortes

A conta usa 4:5, 9:16 e 1.91:1. **Não corte um do outro:** a área vazia muda de
lugar em cada formato e o corte automático destrói a composição.

| Corte | Onde entra | O que trocar no prompt |
|---|---|---|
| **4:5** · 1080×1350 | Feed | Como está acima |
| **9:16** · 1080×1920 | Stories e Reels | "em formato vertical 9:16" e, no 2º parágrafo: "Ela está posicionada no terço inferior do enquadramento. Os dois terços de cima permanecem livres" |
| **1.91:1** · 1200×628 | Coluna da direita, busca | "em formato horizontal 1.91:1" e: "Ela ocupa o quarto direito do enquadramento. Os três quartos da esquerda permanecem livres" |

Gere na maior resolução que a ferramenta oferecer. Reduzir depois é de graça,
aumentar não.

---

## Depois de gerar

**1. Conferir a tela.** Se saiu qualquer letra ou número legível, regere. Um
caractere torto num criativo de software jurídico chama mais atenção do que a
peça inteira. É o erro mais comum, e costuma levar duas ou três tentativas.

**2. Compor a interface real por cima.** É aqui que a imagem vira ativo: a tela
gerada é só a base, e o print real do JurIA entra em cima, com a perspectiva
ajustada. Assim cada criativo novo troca só a tela.

**3. Testar a legibilidade do texto.** Coloque uma headline branca em Inter Bold
sobre a área vazia e veja se lê. Se o fundo estiver claro ou movimentado demais,
resolve com um degradê navy `#0A2540` de 40 a 60% de opacidade sobre a área de
texto, o que ainda aproxima a peça da identidade.

**4. Salvar a original sem tratamento.** Guarde o arquivo cru em
`assets/fundos/`, antes de qualquer camada. A versão editada vai para a pasta da
campanha.

## Pendências

- ⬜ Gerar e escolher a melhor entre 3 ou 4 saídas
- ⬜ Produzir os três cortes
- ⬜ Print em alta da tela real do JurIA para a composição
