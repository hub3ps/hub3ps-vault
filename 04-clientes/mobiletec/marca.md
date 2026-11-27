---
tipo: cliente-doc
cliente: mobiletec
atualizado: 2026-11-27
autor: claude
origem: agencia_marketing, branch claude/loving-archimedes-rp33cv, clients/mobiletec/brand.md (migrado em 27/11/2026)
---
# Mobiletec · direção visual e de movimento

> A **identidade** (logo, cores oficiais) ainda não chegou. O que está aqui é a
> **direção** aprovada pelo Guilherme em 19/10/2026, e a paleta é provisória.

## Direção: seriedade e autoridade

Escolhida da lista do UX Planet, "50 Design Styles Every Designer Should Know":

| Estilo | Papel no site |
|---|---|
| **38 · Utilitarian** | Base. Função antes da forma: grade rígida, quase monocromático, uma cor de sinal, mono nos rótulos, número em evidência, zero enfeite |
| **49 · Modular Typography** | Títulos grandes, apertados, alinhados à grade. A autoridade vem do tamanho e da ordem |
| **28 · Bento Box** | Números, clientes e serviços em células, separadas por linha de 1px |

**Evitar:** Glassmorphism, Aurora, Neo-Brutalism, Memphis, Y2K, Cybercore. Dizem
"startup jovem". Do Neoclassical, só a simetria e a contenção, sem ornamento.

O site da Mobiletec **não** imita o do JurIA (SaaS, brilho, pílulas). A Mobiletec
é a casa de engenharia por trás dele.

## Paleta da marca

Roxo e cinza **lidos da logo** enviada pelo Guilherme em 19/10/2026. Não veio
código de cor oficial: se vier, troca só em
`mobiletec-site-astro/src/styles/tokens.css`.

| Token | Hex | Uso |
|---|---|---|
| `marca` | `#433A6B` | Roxo da logo: botão principal, bloco de contato, destaque nas seções claras |
| `marca-claro` | `#8F86C9` | Destaque sobre fundo escuro (o roxo da marca some no escuro) |
| `cinza-marca` / `muted` | `#666666` | Cinza da logo: texto secundário no claro |
| `ink` | `#0D0C14` | Fundo escuro, puxado para o roxo |
| `paper` | `#F3F2EE` | Fundo claro |

`sinal` é um papel, não uma cor: vale `marca-claro` no escuro e `marca` dentro
de `.tema-claro`.

**Logo:** vetorizada dos PNGs originais (potrace), em `assets/logos/`: símbolo,
horizontal clara e negativa. Cores medidas nos originais: roxo `#423A69`, cinza
`#646466`. Aprovada pelo Guilherme em 20/10/2026. Detalhe em `assets/logos/README.md`.

Tipografia: **Inter Tight** (títulos e texto) e **IBM Plex Mono** (rótulos),
servidas pelo próprio site, sem Google Fonts.

## Movimento

| Biblioteca | Faz |
|---|---|
| [Lenis](https://github.com/darkroomengineering/lenis) | Rolagem suave |
| [GSAP](https://github.com/greensock/GSAP) + ScrollTrigger | Animação ligada à rolagem: títulos por linha, cascata nas células, contadores, bloco fixo do ano |
| [three.js](https://github.com/mrdoob/three.js) | Uma cena só, no hero: campo de pontos ondulando, carregado sob demanda |

**Animação da logo** (20/10/2026, segunda versão): o símbolo se desenha com o
próprio traço, sem seta nem marcador. O cinza nasce na ponta do arco de cima,
passa por baixo do anel e segue pelo arco grande, num gesto só; o anel corre no
sentido oposto; no fim, o traço menor se completa. Curva senoidal, 2,4 s de
desenho. Roda na **abertura** da home, a cada carga (tela clara), e
termina pousando no símbolo da logo do menu, enquanto o site abre. Uns 5 s no
total; clique ou tecla pulam. **Sem logo grande no hero** (pedido do Guilherme).

Regras: movimento contido (revelar, fixar, contar, nada saltitante); 3D só no
hero; `prefers-reduced-motion` recebe a página estática e completa.

## Voz

Frase curta, afirmativa, sem superlativo. Fato no lugar de adjetivo: "desde
2000", não "líder de mercado". Sem travessão.
