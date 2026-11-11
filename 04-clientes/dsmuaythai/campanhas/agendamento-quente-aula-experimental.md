---
tipo: campanha
cliente: dsmuaythai
nome-campanha: Agendamento | Quente | Aula experimental
plataforma: meta
id-campanha: "120259487489600386"
status: ativa
inicio: 2026-09-29
verba-diaria: 7
evento-otimizacao: Escolheu o dia (conversão personalizada 962316889514579)
lp: https://trial.dsmuaythaisquad.com
atualizado: 2026-11-11
autor: claude
---
# Agendamento | Quente | Aula experimental

Nome no Meta desde 11/11/2026, no [[03-processos/convencoes|padrão novo]]. Antes: `[HUB] [Vendas] [Escolheu o dia]`. Valores em USD. Os números ficam no hub, em `dsmuaythai.hub3ps.com`.

## Configuração
Conferida na API em 11/11/2026.

- **Objetivo da Meta:** vendas, otimizando para quem escolhe o dia no Calendly
- **Anúncio:** `VID-01 | Vídeo | Chamada` (antes "Vídeo 01 de chamada"), o mesmo nos dois conjuntos

| Conjunto | ID | Status | Verba | Público na API |
|---|---|---|---|---|
| `IG [Engajamento] [365] / [Seguidores]` (nome antigo, ver abaixo) | `120259487489620386` | ativo | US$ 7/dia | inclui `Engajou IG 365d` e `Seguidores IG`, local EUA, 18 a 65, só celular, sem Advantage+ |
| `Aberto 18-50 \| Cidades atendidas \| Escolheu o dia` | `120259488077550386` | pausado desde 02/10 | US$ 13/dia | 27 cidades de MA, 18 a 50, excluindo `Engajou IG 365d` e `Seguidores IG` |

> **Em aberto (11/11):** o Guilherme diz que o público do conjunto ativo é só de seguidores do Instagram. A API mostra os dois públicos incluídos, quem engajou em 365 dias e os seguidores, com local EUA. Esse conjunto ficou sem renomear até isso se resolver.

## Públicos usados
- `Engajou IG 365d` (`120259482616410386`), antes `IG [Engajamento] [365]`
- `Seguidores IG` (`120259482686800386`), antes `IG [Seguidores]`

## Histórico de otimizações
- 2026-09-29 · publicada, com dois conjuntos · LP nova no ar, otimizando para o passo "escolheu o dia"
- 2026-10-02 · pausado o público aberto, "Todas as cidades atendidas" · TODO: o motivo
- 2026-10-23 · a página passa a enviar a aula paga ao pixel · a Meta só via as aulas do site antigo
- 2026-10-27 · campanha pausada pelo Gustavo, às 15h58 · TODO: o motivo
- 2026-11-05 · religada pelo Gustavo, às 12h17 (log de atividades da conta, em `montar-hub.py`)
- 2026-11-11 · campanha, conjunto pausado, anúncios e públicos renomeados para o padrão novo · só rótulo, sem efeito na entrega
