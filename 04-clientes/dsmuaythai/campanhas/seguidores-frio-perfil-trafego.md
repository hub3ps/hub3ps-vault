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
atualizado: 2026-11-11
autor: claude
---
# Seguidores | Frio | Perfil | Tráfego

Nome no Meta desde 11/11/2026, no [[03-processos/convencoes|padrão novo]]. Antes: `[HUB] [Tráfego] [Seguidores]`. O quarto campo, `Tráfego`, entrou no mesmo dia, quando abriu o teste com a [[seguidores-frio-perfil-engajamento|campanha de Engajamento]]. Valores em USD. Os números ficam no hub, em `dsmuaythai.hub3ps.com`.

## Configuração
Conferida na API em 11/11/2026.

- **Objetivo da Meta:** tráfego, otimizando para visita ao perfil do Instagram
- **Conjunto:** `Aberto 18-55 sem seguidores | MA | Visita ao perfil` (`120259703778130386`), antes "Massachusetts - H/M - 18/55 - Exclusão: Seguidores IG". Ativo, US$ 7/dia
- **Público:** de 18 a 55 anos, homens e mulheres, em Massachusetts, excluindo `Seguidores IG`, com Advantage+

## Criativos
Os dois são Reels do perfil (conferido no Instagram em 11/11).

| ID | Anúncio | Post | Status |
|---|---|---|---|
| IG-01 | `IG-01 \| Reels \| Welcome` (`120259703778140386`) | [DRbQdZSjbEV](https://www.instagram.com/p/DRbQdZSjbEV/), "Welcome to DS Muay Thai Squad" | pausado |
| IG-02 | `IG-02 \| Reels \| Holding pads` (`120259703972970386`) | [DcbbH7FBdmZ](https://www.instagram.com/p/DcbbH7FBdmZ/), "The art of holding pads" | ativo |

> O hub (`montar-hub.py`) troca o texto dos dois posts: mostra "holding pads" no DRbQdZSjbEV e "Welcome" no DcbbH7FBdmZ. Corrigir junto com o hub novo, decidido pelo Guilherme em 11/11.

## Histórico de otimizações
- 2026-10-13 · publicada · a US$ 9/dia, segundo o plano do hub
- TODO · verba em US$ 7/dia na API (04/11 e 11/11). Conferir se mudou ou se o plano está errado
- 2026-11-11 · campanha, conjunto e anúncios renomeados para o padrão novo · só rótulo, sem efeito na entrega
- 2026-11-11 · ganha o quarto campo `Tráfego` e vira a base do teste contra o Engajamento · sem girar criativo enquanto o teste roda
