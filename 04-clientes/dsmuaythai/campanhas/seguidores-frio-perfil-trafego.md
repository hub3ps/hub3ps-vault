---
tipo: campanha
cliente: dsmuaythai
nome-campanha: Seguidores | Frio | Perfil | Tráfego
plataforma: meta
id-campanha: "120259703778120386"
status: ativa
inicio: 2026-10-13
verba-diaria: 7
evento-otimizacao: PROFILE_VISIT
lp: https://instagram.com/ds_muaythai_squad
atualizado: 2026-11-16
autor: claude
---
# Seguidores | Frio | Perfil | Tráfego

Nome no Meta desde 11/11/2026, no [[03-processos/convencoes|padrão novo]]. Antes: `[HUB] [Tráfego] [Seguidores]`. O quarto campo, `Tráfego`, entrou no mesmo dia, quando abriu o teste com a [[seguidores-frio-perfil-engajamento|campanha de Engajamento]]. Valores em USD. Os números ficam no hub, em `dsmuaythai.hub3ps.com`.

## Configuração
Conferida na API em 16/11/2026. Um conjunto por anúncio desde 16/11, decisão do
Guilherme; o ID do anúncio entra como quarto campo do conjunto.

- **Objetivo da Meta:** tráfego, otimizando para visita ao perfil do Instagram
- **Verba:** US$ 7/dia por conjunto, US$ 14/dia na campanha desde 16/11

| Conjunto | ID | Público | Anúncio |
|---|---|---|---|
| `Aberto 18-55 sem seguidores \| MA \| Visita ao perfil \| IG-02` | `120259703778130386` | 18 a 55 como sugestão, **com Advantage+** (a API mostra 18 a 65) | IG-02 (IG-01 pausado) |
| `Aberto 18-55 sem seguidores \| MA \| Visita ao perfil \| IG-03` | `120260348130470386` | 18 a 55 fixos, **sem Advantage+** | IG-03 |

Os dois: homens e mulheres, Massachusetts, excluindo `Seguidores IG`.

> O conjunto do IG-03 saiu do Gerenciador sem Advantage+, diferente do
> original. Um muda o público e o criativo ao mesmo tempo, então a comparação
> entre IG-02 e IG-03 não isola o criativo. O Guilherme decidiu manter assim
> (16/11).

## Criativos
Todos são Reels do perfil (conferido no Instagram em 11/11).

| ID | Anúncio | Post | Status |
|---|---|---|---|
| IG-01 | `IG-01 \| Reels \| Welcome` (`120259703778140386`) | [DRbQdZSjbEV](https://www.instagram.com/p/DRbQdZSjbEV/), "Welcome to DS Muay Thai Squad" | pausado |
| IG-02 | `IG-02 \| Reels \| Holding pads` (`120259703972970386`) | [DcbbH7FBdmZ](https://www.instagram.com/p/DcbbH7FBdmZ/), "The art of holding pads" | ativo |
| IG-03 | `IG-03 \| Reels \| Holding pads parte 2` (`120260348130490386`) | [Dcgku5WBbIj](https://www.instagram.com/reel/Dcgku5WBbIj/), "The art of holding pads, part 2" | em análise (16/11) |

> O hub (`montar-hub.py`) troca o texto dos dois posts: mostra "holding pads" no DRbQdZSjbEV e "Welcome" no DcbbH7FBdmZ. Corrigir junto com o hub novo, decidido pelo Guilherme em 11/11.

## Histórico de otimizações
- 2026-10-13 · publicada · a US$ 9/dia, segundo o plano do hub
- TODO · verba em US$ 7/dia na API (04/11 e 11/11). Conferir se mudou ou se o plano está errado
- 2026-11-11 · campanha, conjunto e anúncios renomeados para o padrão novo · só rótulo, sem efeito na entrega
- 2026-11-11 · ganha o quarto campo `Tráfego` e vira a base do teste contra o Engajamento · sem girar criativo enquanto o teste roda
- 2026-11-16 · o teste contra o Engajamento acabou (US$ 0,90 contra US$ 2,78 por seguidor, de 11 a 16/11) · volta a girar criativo pela fila; próximo: IG-03, a subir pelo Gerenciador num conjunto próprio. Decisão do Guilherme em 16/11: daqui em diante, um anúncio por conjunto
- 2026-11-16 · IG-03 publicado pelo Guilherme num conjunto próprio, duplicado do original · verba da campanha vai a US$ 14/dia; o conjunto novo ficou sem Advantage+
- 2026-11-16 · conjunto original renomeado para `... | Visita ao perfil | IG-02` pelo MCP, com OK do Guilherme · só rótulo, sem efeito na entrega
