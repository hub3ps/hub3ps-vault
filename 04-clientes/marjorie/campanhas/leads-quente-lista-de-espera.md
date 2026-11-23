---
tipo: campanha
cliente: marjorie
nome-campanha: Leads | Quente | Lista de espera
plataforma: meta
id-campanha: "120251146900880554"
status: ativa
inicio: 2026-11-23
fim: 2026-11-26
verba-diaria: 5
evento-otimizacao: LEAD
lp: https://www.marjoriedentalcad.com/zero-to-hero
atualizado: 2026-11-23
autor: claude
---
# Leads | Quente | Lista de espera

Leva a base aquecida para a lista de espera, de 23 a 26/11/2026, no lugar da [[distribuicao-quente-zero-to-hero]]. Decisão do Guilherme em 23/11: objetivo de lead, otimizando pelo `Lead` do Pixel, com os dois vídeos do Ad 1. Na sexta, 27/11, dia do lançamento, ela já terminou, e entra a campanha do carrinho. Conta `2540479789760330`, valores em USD.

## Configuração
Montada pelo MCP em rascunho em 23/11 e publicada pelo Guilherme no Gerenciador no mesmo dia, com IDs novos (o rascunho do MCP era `120251146030670554`). Conferida na API em 23/11: veja os desvios no histórico.

- **Objetivo:** leads (`OUTCOME_LEADS`)
- **Conjunto:** `Engajou IG 365d, seguidores e compradores | Sem filtro de país | Lead` (`120251146900900554`)
  - US$ 5 por dia no conjunto, sem limite de lance
  - Otimiza pelo `Lead` do Pixel `1775314010396135`, destino site
  - Termina em 26/11, 23h59, no horário do Pacífico (fuso da conta)
  - Públicos: `Engajou IG 365d`, `Seguidores IG` e `Compradores curso antigo`. O `Visitou perfil IG 90d` já está dentro do `Engajou IG 365d`
  - Sem filtro de país, como a distribuição, e idade a partir de 18
  - Advantage+ de público e expansão do público desligados, porque o conjunto é só de público personalizado
  - Posicionamentos automáticos
  - **Sem exclusão de quem já se inscreveu.** O público é pequeno, então não compensa (Guilherme, 23/11)
- **Anúncios:** os dois vídeos do Ad 1 ([[2026-11-14-anuncios-gravados-julia]]), já estão na biblioteca da conta desde 23/11 (IDs em [[2026-11-14-anuncios-gravados-julia]]). O Guilherme monta os anúncios no Gerenciador
  - `VID-01 | Vídeo | Caso travado`: Ad 1, versão 1 ([Drive](https://drive.google.com/file/d/1rql2gOV2ymvmOmisEx9731wNpUc-3SGC/view))
  - `VID-02 | Vídeo | Especialista à mão`: Ad 1, versão 2 ([Drive](https://drive.google.com/file/d/1I5hqXyhjpi4sUFJtjux2lVJokTuZl6Mz/view))

## Montagem dos anúncios
- **URL do site:** `https://www.marjoriedentalcad.com/zero-to-hero`
- **Link de exibição:** `marjoriedentalcad.com`
- **Botão:** Inscreva-se (`SIGN_UP`)
- **Parâmetros de URL:**
  - VID-01: `utm_source=meta&utm_medium=paid&utm_campaign=leads-quente-lista-de-espera&utm_content=vid-01&utm_term=engajou-ig-365d-seguidores-e-compradores`
  - VID-02: o mesmo, com `utm_content=vid-02`
- **Aprimoramentos:** Advantage+ de criativo todo desligado, só "Comentários relevantes" ligado. Destaques do site, Links de site e Produtos e serviços desligados

### Textos (inglês, iguais nos dois anúncios)
Texto principal:
1. Stuck on an exocad case with no one to ask? On November 27, I'm opening exocad: Zero to Hero Circle, a community where you post your cases, ask your questions and get answers from me and from people who use exocad every day. The waitlist hears from me first. Join now and save your spot.
2. What if you had an exocad expert to ask every time you got stuck? exocad: Zero to Hero Circle opens on November 27, with real support, real cases and more than 20 hours of training inside. Join the waitlist and be the first to know.
3. Doors open on November 27. Save your spot on the waitlist for exocad: Zero to Hero Circle and hear from me before anyone else.
4. Learning exocad alone is slow. Inside exocad: Zero to Hero Circle, you bring your real cases and get feedback from me, a dental technician and CAD designer, plus more than 20 hours of training. It opens on November 27. Join the waitlist now.
5. Dentists, dental technicians and assistants: if you design in exocad, this is for you. exocad: Zero to Hero Circle opens on November 27. Join the waitlist and hear everything from me first.

Título:
1. Join the waitlist
2. Zero to Hero Circle opens Nov 27
3. Save your spot before Nov 27
4. Get exocad answers from an expert
5. Stop figuring out exocad alone

Descrição: Opens November 27. Join the waitlist.

## Criativos no ar
| ID | Anúncio | Desde |
|---|---|---|
| VID-01 | `VID-01 \| Vídeo \| Caso travado` (`120251146900890554`) | 23/11/2026, aprovado |
| VID-02 | `VID-02 \| Vídeo \| Especialista à mão` (`120251148658610554`, recriado na publicação; o antigo era `120251147030590554`) | 23/11/2026, aprovado |

## Histórico de otimizações
- 2026-11-23 · campanha e conjunto criados pelo MCP em rascunho, a pedido do Guilherme · substituem a distribuição, pausada no mesmo dia. Primeiro o conjunto saiu com uma lista de 11 países, por erro meu, e foi corrigido no rascunho para sem filtro de país, como a base sempre rodou. Faltam os dois anúncios e a publicação, pelo Guilherme no Gerenciador
- 2026-11-23 · textos sem a palavra "free", a pedido do Guilherme
- 2026-11-23 · publicada pelo Guilherme no Gerenciador, conferida na API · está certo: objetivo de lead, US$ 5 por dia, otimização pelo `Lead` do Pixel, os três públicos, Advantage+ de público e expansão desligados, link, link de exibição, título e descrição. Desvios achados:
  - o conjunto saiu só com EUA, e não sem filtro de país
  - o conjunto ficou sem data de término, e devia terminar em 26/11, 23h59 (Pacífico)
  - os dois anúncios parecem usar o mesmo vídeo, o Ad 1 versão 1: mesma duração (24,566 s, a do VID-01; o VID-02 tem 24,766 s) e a mesma miniatura
  - o botão é "Candidatar-se" (`APPLY_NOW`), e não "Inscreva-se" (`SIGN_UP`)
  - aprimoramentos ligados: `pac_relaxation` nos dois e `translate_voiceover` (dublagem automática) no VID-02
  - a API não mostra os parâmetros de URL nem as variações de texto, só a primeira, então isso não foi conferido
- 2026-11-23 · desvios corrigidos pelo MCP em rascunho, a pedido do Guilherme, e validados sem erro · fica pendente de publicação pelo Guilherme no Gerenciador
  - conjunto: mundo todo, menos Taiwan e Singapura, que exigem uma declaração regional que o MCP não preenche; término em 26/11, 23h59 (Pacífico); anunciante e pagador da UE como "Marjorie Dental CAD"
  - criativos novos: `1758538798575927` (VID-01, vídeo `5595817547309155`) e `1675093980747985` (VID-02, vídeo `1693163199139239`), com o botão Inscreva-se, os 5 textos, os 5 títulos, a descrição, os parâmetros de URL e todos os aprimoramentos desligados menos Comentários relevantes
  - a troca do vídeo do VID-02 está confirmada pela miniatura: o anúncio publicado usava a mesma do VID-01
  - depois de publicar, os dois anúncios voltam para análise
- 2026-11-23 · segunda publicação pelo Guilherme, conferida na API · o rascunho do MCP não ficou: os criativos no ar são outros (`2383021325798608` no VID-01 e `1611980256818426` no VID-02), e o VID-02 virou um anúncio novo, `120251148658610554`. Os dois estão em análise
  - certo agora: cada anúncio com o seu vídeo (VID-01 com 24,566 s e VID-02 com 24,766 s, mesmas miniaturas da biblioteca), US$ 5 por dia, `Lead` do Pixel, os três públicos, expansão desligada, link, link de exibição, título e descrição
  - ainda errado: o botão segue "Candidatar-se" (`APPLY_NOW`) nos dois; `image_animation` ligado nos dois e `pac_relaxation` no VID-02; o conjunto segue sem data de término
  - a API não devolve país nenhum no conjunto, nem EUA nem mundo todo. Conferir no Gerenciador
  - parâmetros de URL e as 5 variações de texto seguem sem conferência pela API, que só mostra a primeira
- 2026-11-23 · ajuste do Guilherme no Gerenciador, conferido na API · término em 27/11, 00h00 (Pacífico), ou seja, roda até o fim de 26/11; local "Todas as localizações", que a API mostra como conjunto sem país; os dois anúncios aprovados (`ACTIVE`, em preparação para entrega)
  - o `image_animation` aparece na configuração do criativo pela API, mas o Guilherme confirmou que está desligado no Gerenciador. Num anúncio de vídeo ele não tem efeito
  - ficaram como estão: o botão "Candidatar-se" (`APPLY_NOW`) nos dois e o `pac_relaxation` no VID-02

