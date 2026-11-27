---
tipo: processo
atualizado: 2026-11-27
autor: claude
origem: agencia_marketing/docs/processos/post-instagram-juria.md (migrado em 27/11/2026)
---
# Post do Instagram do JurIA (carrossel e estático)

> Caminhos de arquivo e comandos são do repo `agencia_marketing` (`~/Desktop/agencia_marketing`), salvo quando outro repo é citado.

Layout e por que ele é assim:
`clients/juria/creatives/instagram/LAYOUT.md`.
Vídeo segue outro runbook: [[video-juria|video-juria.md]].

## 1. Fatos antes do texto

- [ ] Preço, plano e trial só de `clients/juria/comercial/planos-e-creditos.md`
- [ ] Função e o que cada plano libera, de `comercial/funcionalidades.md`.
      "Todas as funcionalidades" só vale do Plus em diante
- [ ] Tom: `clients/juria/brand.md`, sem travessão

## 2. Montar

```bash
cd clients/juria/creatives/instagram
mkdir IG-CAR-NN_<assunto>        # carrossel: slide-01.html, slide-02.html…
mkdir IG-IMG-NN_<assunto>        # estático: post.html
```

Copie um post existente como ponto de partida (`IG-CAR-01_sistemas`,
`IG-IMG-01_engenharia`). Cada HTML linka `../_layout/layout.css`; estilo que só
aquele post usa vai num `post.css` na pasta dele.

## 3. Gerar os PNGs

```bash
bash _layout/render.sh IG-CAR-NN_<assunto>
```

Sai `IG-CAR-NN_<assunto>_s01.png`… (ou `IG-IMG-NN_<assunto>.png`), 1080×1350.

**Conferir no PNG, não no HTML:** acento, palavra cortada, título encostando na
cabeça ou no pé, e se o ciano aparece uma vez só.

## 4. Legenda

`legenda-<ID>.md` na pasta `instagram/`. **Não repete o texto da peça**:
completa (como ativar, ressalva, pergunta para comentário). Primeira linha é o
gancho, que aparece antes do "mais". Aprovar com o Guilherme.

## 5. Registrar

Linha nova na tabela do `instagram/README.md` e commit com HTML, PNG e legenda
juntos.
