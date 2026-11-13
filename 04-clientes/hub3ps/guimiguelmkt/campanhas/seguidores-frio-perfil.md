---
tipo: campanha
cliente: hub3ps
nome-campanha: Seguidores | Frio | Perfil
plataforma: meta
conta: "1702680416845524"
id-campanha: "120249697942430578"
status: ativa
inicio: 2026-11-13
verba-diaria: 40
evento-otimizacao: Visita ao perfil
perfil: https://www.instagram.com/guimiguelmkt/
atualizado: 2026-11-13
autor: claude
---
# Seguidores | Frio | Perfil

Campanha de seguidores do Instagram pessoal do Guilherme (@guimiguelmkt), subida por ele em 13/11/2026 às 10h06. Nomes no [[03-processos/convencoes|padrão]] desde 13/11. Valores em BRL.

**Conta de anúncio:** `CONTA 03` (`act_1702680416845524`), fuso de São Paulo. O token da BM lê e escreve nela (conferido em 13/11). A conta também guarda a campanha antiga `[CADASTRO] [TESTE]`, de 2023 (Studio Energy), pausada e fora do escopo.

## Configuração
Conferida na API em 13/11/2026.

- **Objetivo da Meta:** engajamento, com destino no perfil do Instagram e otimização para visita ao perfil (`PROFILE_AND_PAGE_ENGAGEMENT`), lance de menor custo
- **Campanha:** antes `Nova campanha de Engajamento`

| Conjunto | ID | Status | Verba | Público na API |
|---|---|---|---|---|
| `Aberto 18-45 \| Brasil \| Visita ao perfil \| IG-06` (antes `Novo conjunto de anúncios de Engajamento`) | `120249697942440578` | ativo | R$ 20/dia | Brasil, 18 a 45, todos os gêneros, sem Advantage+ de público, sem exclusão. Posicionamentos manuais: Feed, Stories e Reels do Facebook; Feed, Stories, Reels, Explorar e Feed do perfil do Instagram |
| `Aberto 18-45 \| Brasil \| Visita ao perfil \| IG-04` (duplicado do primeiro) | `120249698525430578` | ativo | R$ 20/dia | igual ao do IG-06 |

Um conjunto por post, com verba própria em cada um (sem CBO), para garantir a entrega dos dois no teste. O ID do post entra como quarto campo no nome do conjunto.

| Anúncio | ID | Post | Chamada |
|---|---|---|---|
| `IG-06 \| Reels \| Claude no Meta Ads` (antes `Novo anúncio de Engajamento`) | `120249697942420578` | [Reels de 12/11](https://www.instagram.com/reel/Dfpya40vEsB/), o [[roteiros/2026-11-11-claude-meta-ads-contexto\|vídeo do IMG_2087]] | Ver perfil do Instagram |
| `IG-04 \| Reels \| Gestor ou anúncio` (veio como `IG-06 \| Reels \| Claude no Meta Ads`, nome herdado da duplicação) | `120249698525420578` | [Reels de 05/11](https://www.instagram.com/reel/DfX7yIchzJk/), "Anúncio ou gestor de tráfego: onde você gasta mais?" | Ver perfil do Instagram |

> Logo depois de renomear, o anúncio do IG-06 passou alguns minutos "em processamento" e voltou a ativo (conferido em 13/11).

> ⚠️ **Anúncio do IG-04 com erro (13/11):** depois de renomeado pela API, ficou "com problemas", com o erro `1885499`: *Sem permissão para o anunciante na Página*. O usuário do sistema da BM não tem a função de anunciante na Página do @guimiguelmkt (`1497157753475425`), e a edição dele reabriu a validação do anúncio. **Correção:** dar ao usuário do sistema (ou à BM da Hub3Ps) acesso de anunciante à Página e ao Instagram, ou o Guilherme abrir o anúncio no Ads Manager e publicar de novo. Até ter esse acesso, renomear anúncio desta conta é pelo Ads Manager, não pela API.

## Posts do perfil (IDs `IG-NN`)
A ordem de publicação dá o número, e o ID do anúncio segue esta lista.

| ID | Data | Post |
|---|---|---|
| IG-01 | 15/10 | Reels "Primeira vez em 8 anos que eu falo sobre isso" |
| IG-02 | 29/10 | Carrossel "8 anos resumidos em 8 slides" |
| IG-03 | 30/10 | Fotos "Abri minha galeria" |
| IG-04 | 05/11 | Reels "Se o seu gestor ganha mais que o seu anúncio" |
| IG-05 | 10/11 | Reels "Setup novo" |
| IG-06 | 12/11 | Reels "Não conecte o Claude no seu Meta Ads sem fazer isso antes" |

## Como ler o resultado
A Meta otimiza para visita ao perfil, não para quem segue. O que importa é o **custo por seguidor**: o investimento dividido pelos seguidores ganhos no período, que se vê nos insights do perfil. A visita ao perfil é só o caminho até ele.

## Histórico de otimizações
- 2026-11-13 · publicada pelo Guilherme, com um conjunto e o IG-06 · primeira campanha de seguidores do perfil
- 2026-11-13 · campanha, conjunto e anúncio renomeados para o padrão · só rótulo, sem efeito na entrega
- 2026-11-13 · novo conjunto com o IG-04, duplicado do primeiro, R$ 20/dia · testar um segundo post; a verba total passa a R$ 40/dia. Conjuntos ganham o ID do post no nome
