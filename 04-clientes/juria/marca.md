---
tipo: cliente-doc
cliente: juria
atualizado: 2026-11-27
autor: claude
origem: agencia_marketing, clients/juria/brand.md (migrado em 27/11/2026)
---
# JurIA — Identidade visual e verbal

Fonte oficial: `source/JurIA_Minibrandbook_v1.pdf` (v1.0, 18/05/2026, produzido por Hub3Ps).

Este arquivo é o **resumo navegável** para alimentar a skill de criativo e copywriters. Em caso de conflito, valer o PDF.

---

## Logo

Três versões fornecidas pelo cliente (3 PNGs colados no chat — **pendente salvar em `assets/logos/`**):

1. **Logo principal fundo escuro** — wordmark "JurIA" (Jur branco, IA ciano) + tagline "Inteligência Jurídica" branca, sobre fundo navy `#0A2540`.
2. **Logo principal fundo claro** — wordmark "JurIA" (Jur navy, IA ciano) + tagline navy, sobre branco.
3. **Logo institucional/com símbolo** — logo + balança da justiça com figura "inteligente" (ponto ciano na cabeça), usada na capa do brandbook.

### Regras de uso (do brandbook)

- **Zona de proteção:** margem mínima = altura da letra "J" ao redor da logo.
- **Tamanho mínimo:** 32 px de altura em telas, 12 mm em impressos. Abaixo disso, tagline "Inteligência Jurídica" deixa de ser legível.
- **Fundos permitidos:** Off-white `#F7F9FA`, Navy `#0A2540`, Ciano `#14B4C8`. Evitar fundos com textura ou imagens de baixo contraste.
- **Não fazer:** rotacionar, distorcer, recolorir wordmark, aplicar sombras decorativas ou contornos.

> **Pendência:** subir os PNGs/SVGs da logo em `clients/juria/assets/logos/`. Sem isso, a geração de criativos exige substituição manual de logo após o handoff do JSON.

---

## Paleta de cores

### Primárias

| Token | HEX | RGB | Uso |
|-------|-----|-----|-----|
| **Navy JurIA** | `#0A2540` | 10, 37, 64 | Principal institucional. Headers, navbar, tipografia institucional, fundo de slides corporativos. |
| **Ciano IA** | `#14B4C8` | 20, 180, 200 | Accent IA / CTA. Botões de ação, links, destaque do "IA", indicadores de IA. **Uso parcimonioso.** |

### Secundárias

| Token | HEX | Uso |
|-------|-----|-----|
| Navy Deep | `#061A30` | Profundidade |
| Navy Mid | `#1B3A5C` | Hover, camadas |
| Ciano Soft | `#7FDBE5` | Glow suave |
| Ciano Wash | `#F0FBFC` | Background soft |

### Neutros

| Token | HEX | Uso |
|-------|-----|-----|
| Texto | `#0F1B2D` | Texto principal |
| Cinza Texto | `#5B6B7D` | Texto secundário |
| Cinza Linha | `#E5EBF0` | Bordas, divisórias |
| Off-white | `#F7F9FA` | Background |

---

## Tipografia

| Família | Uso | Pesos |
|---------|-----|-------|
| **Inter** | Digital, web, LP, criativos | 400 Regular · 500 Medium · 600 Semibold · 700 Bold · 800 ExtraBold |
| **Arial** | Fallback impresso e e-mail | Regular · Bold |

### Quando a ferramenta não tem Inter

Acontece em Instagram, Canva e afins, que oferecem uma lista fechada.

| Ordem | Fonte | Por quê |
|---|---|---|
| 1ª | **Roboto** | A mais próxima no olho. Grotesca neutra, feita para tela, altura de x alta e contraformas abertas, igual à Inter |
| 2ª | **Arimo** | Metricamente idêntica à Arial, que o brandbook já aprova como fallback. Defensável pelo manual, mas mais distante da Inter: a Arial tem terminais inclinados no `t`, `s`, `e` e `C`, os da Inter são retos |
| 3ª | Source Sans 3 · Noto Sans · Libre Franklin | Servem se as duas acima faltarem. Mais humanistas e mais largas |

**Nunca substituir por Poppins nem Montserrat.** São o substituto automático mais
comum e mudam a personalidade inteira: geométricas, mais redondas, mais largas. A
peça deixa de parecer JurIA.

**Nunca por condensada de display** (Bebas, Oswald, Teko, League Spartan). Quebra
a marca de vez.

### Hierarquia (do brandbook)

| Nível | Especificação |
|-------|---------------|
| H1 | Inter Bold 800 · 32pt · letter-spacing -1.5 |
| H2 | Inter Bold 700 · 20pt · letter-spacing -0.5 |
| H3 | Inter Semibold 600 · 14pt |
| Body | Inter Regular 400 · 11pt · line-height 1.55 |
| Caption | Inter Medium 500 · 9pt · letter-spacing 1.5 (caixa alta) |

---

## Instagram orgânico: layout editorial

Desde 20/10/2026 os carrosséis e estáticos do perfil seguem o layout
"editorial jurídico": fundo papel, grade com linhas finas, Inter fina nos
títulos com destaque em seminegrito, ciano em um detalhe só por peça e nada de
neon, degradê ou vidro. Regras e componentes:
`agencia_marketing/clients/juria/creatives/instagram/LAYOUT.md`. Anúncio no
Meta segue as linhas A e B abaixo.

---

## Tom de voz — split de duas linhas

O briefing v6 fechou um split de tom desde o dia 1.

### Linha A — Tech-modern

- **Onde:** Meta Ads, criativos de IA em ação
- **Públicos:** Contencioso, Previdenciário
- **Estilo:** direto, com confiança técnica. Frases curtas. Verbos no presente. Foco em velocidade, automação e diferenciação competitiva.
- **Headline de exemplo:** "A IA do seu escritório lê o STF antes de você."
- **CTA de exemplo:** "Comece em 60 segundos. Sem cartão."

### Linha B — Tradicional-sóbrio

- **Onde:** Google Search, LP institucional
- **Públicos:** Trabalhista, Tributário
- **Estilo:** institucional, cuidadoso, ancorado em autoridade. Frases mais completas. Foco em segurança, controle, conformidade e durabilidade.
- **Headline de exemplo:** "Controle total do seu escritório, com 25 anos de engenharia por trás."
- **CTA de exemplo:** "Conheça o JurIA. LGPD, MFA e auditoria nativas."

> **Default para Meta Ads:** Linha A. Skill pode misturar Linha B em conceitos de ângulo `autoridade` ou `prova-social`.

---

## Pronúncia do nome

Fala-se **"Júri-á"**: "júri" + "á", com força no "á" final. Não é "Juría" nem
"Jur-I-A" soletrado.

**Em locução por IA (ElevenLabs), escreva `Júri-á`** no texto. Testado em
19/10/2026 com a voz Bianca no `eleven_v4`: "Júriá" e a transcrição fonética
`/ˌʒuɾiˈa/` ficaram piores. A grafia vale só para o texto falado; na tela, no
anúncio e em qualquer texto escrito o nome continua `JurIA`.

## Vocabulário

### Usar

inteligência · plataforma · sistema · jurimetria · precedentes · monitoramento · automação · controle · conformidade · due diligence · escritório · advogado · sócio · gestão · produtividade

### Evitar

- "Robôs", "mágica", "revolucionário", "disruptivo", "leva no automático"
- Expressões que sugiram que a IA **substitui** o advogado
- Jargão de startup ("growth hack", "killer feature")
- Exageros sem dado por trás
