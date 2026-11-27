---
tipo: campanha
cliente: marjorie
nome-campanha: Vendas | Quente | Carrinho aberto
plataforma: meta
id-campanha: "120251198620610554"
status: publicada
inicio: 2026-11-27
fim: 2026-11-30
verba-diaria: 10
evento-otimizacao: LANDING_PAGE_VIEWS
lp: https://www.marjoriedentalcad.com/zero-to-hero
atualizado: 2026-11-26
autor: claude
---
# Vendas | Quente | Carrinho aberto

Carrinho aberto do exocad: Zero to Hero Circle, de 27 a 30/11/2026, depois da [[leads-quente-lista-de-espera]]. O destino é a mesma página da lista de espera, `/zero-to-hero` (Guilherme, 25/11). Conta `2540479789760330`, valores em USD.

## Configuração
Montada pelo MCP em 26/11 e publicada no mesmo dia com o ok do Guilherme. Conferido na API: conjunto ativo, programado para 27/11, e os 3 anúncios em análise.

- **Objetivo:** vendas (`OUTCOME_SALES`)
  - Sem catálogo. A Meta prendeu sozinha o catálogo `597402544929215` na campanha, e eu tirei no rascunho
- **Conjunto:** `Seguidores | Sem filtro de país | Visualização da página` (`120251198627320554`)
  - US$ 10 por dia no conjunto, sem limite de lance. Montei a US$ 5, e o Guilherme mudou para US$ 10 no Gerenciador antes de publicar
  - Otimiza por visualização da página de destino. O Pixel `1775314010396135` entra como sinal, com o evento `Purchase`
  - De 27/11, 00h00, até 01/12, 00h00, no horário do Pacífico (fuso da conta). Ou seja, roda até o fim de 30/11
  - Público: só `Seguidores IG`. A lista de espera vai num conjunto próprio, quando a Julia mandar o arquivo e o Guilherme criar o público (decisão de 26/11)
  - Sem filtro de país, idade de 18 a 65, Advantage+ de público e expansão desligados, posicionamentos automáticos
- **Rastreamento:** o clique nos botões da Circle dispara `InitiateCheckout` por regra do configurador de eventos (`1445278821096545` e `1819486695987515`), testado em 26/11. A venda se mede na Circle
- **Anúncios:** os 3 vídeos do Ad 2 ([[2026-11-14-anuncios-gravados-julia]]), um por cargo, no mesmo conjunto

## Montagem dos anúncios
- **URL do site:** `https://www.marjoriedentalcad.com/zero-to-hero`
- **Link de exibição:** `marjoriedentalcad.com`
- **Botão:** Inscreva-se (`SIGN_UP`)
- **Parâmetros de URL:** `utm_source=meta&utm_medium=paid&utm_campaign=vendas-quente-carrinho-aberto&utm_content=vid-0X&utm_term=seguidores-e-lista-de-espera`, com o `utm_content` de cada anúncio. O `utm_term` ficou com o nome antigo: a troca para `seguidores` no rascunho não pegou na publicação, e corrigir agora geraria criativo novo e nova análise. O conjunto da lista usa `utm_term=lista-de-espera`, então os dois se separam
- **Aprimoramentos:** tudo desligado, menos "Comentários relevantes". Sem catálogo e sem extensões de produto

### Textos (inglês)
Nenhum diz o preço. O "Launch pricing ends November 30" vem da fala dos vídeos.

**VID-03, dentista:**
1. Dentists: designing your own cases in exocad and getting stuck? exocad: Zero to Hero Circle is open. Bring your cases, ask your questions and get support from me, a dental technician and CAD designer, plus more than 20 hours of training. Launch pricing ends November 30. Join now.
2. You don't have to figure out exocad alone. Inside exocad: Zero to Hero Circle, dentists post real cases and get answers from me and from people who use exocad every day. Launch pricing ends November 30.
3. exocad: Zero to Hero Circle is open. Real cases, real feedback and more than 20 hours of training to learn at your own pace. Launch pricing ends November 30.

**VID-04, técnico:**
1. The only technician in the lab who knows exocad? Then who do you ask when you get stuck? exocad: Zero to Hero Circle is open. Share your cases and get real feedback from me and from techs who work in exocad every day. Launch pricing ends November 30.
2. Stop figuring out exocad by yourself. Inside exocad: Zero to Hero Circle you get feedback on your real cases, plus more than 20 hours of training. Launch pricing ends November 30.
3. O mesmo texto 3 do VID-03.

**VID-05, assistente:**
1. Your practice wants to bring design in-house, and now you're the CAD person? exocad: Zero to Hero Circle is open. Bring your cases, ask anything and get real feedback from me and from people who work in exocad every day. Launch pricing ends November 30.
2. Learn exocad step by step, without guessing. exocad: Zero to Hero Circle gives you more than 20 hours of training and a place to ask about your real cases. Launch pricing ends November 30.
3. O mesmo texto 3 do VID-03.

Títulos (iguais nos 3 anúncios):
1. exocad: Zero to Hero Circle is open
2. Join before November 30
3. Get exocad answers from an expert
4. Stop figuring out exocad alone

Descrição: Launch pricing ends November 30.

## Criativos
| ID | Anúncio | Criativo | Vídeo |
|---|---|---|---|
| VID-03 | `VID-03 \| Vídeo \| Vagas dentista` (`120251198646620554`) | `985651254220225` | `1160731756456315` |
| VID-04 | `VID-04 \| Vídeo \| Vagas técnico` (`120251198646850554`) | `1516785950357831` | `1142569055023775` |
| VID-05 | `VID-05 \| Vídeo \| Vagas assistente` (`120251198647120554`) | `1173173141886872` | `29290951537192198` |

## Histórico de otimizações
- 2026-11-26 · campanha, conjunto e os 3 anúncios criados pelo MCP em rascunho, a pedido do Guilherme, e validados sem erro · falta o público da lista de espera no conjunto, e depois a publicação
- 2026-11-26 · conjunto renomeado para só seguidores e campanha publicada pelo MCP, com o ok do Guilherme · verba de US$ 10 por dia, vinda do Gerenciador · conferido na API: conjunto ativo de 27/11 a 30/11, anúncios em análise, rascunho vazio
