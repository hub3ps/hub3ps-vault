---
tipo: processo
atualizado: 2026-11-27
autor: claude
origem: agencia_marketing/docs/processos/canais-ga4-juria.md (migrado em 27/11/2026)
---
# Agrupar canais no GA4 do JurIA

> Caminhos de arquivo e comandos são do repo `agencia_marketing` (`~/Desktop/agencia_marketing`), salvo quando outro repo é citado.

> Propriedade `G-DRF9JD5S5F`. Rotina curta, para rodar **quando um canal novo
> entra na mídia ou quando a convenção de UTM muda**.
>
> O catálogo de eventos e as armadilhas de medição ficam em
> `clients/juria/ferramentas/gerar-eventos.py`.
> Configuração do funil: [[configurar-ga4-juria|configurar-ga4-juria.md]].

## O problema que isto resolve

As UTMs da conta usam `utm_source=meta` e `utm_medium=paid`. O GA4 só reconhece
`facebook` e `instagram` como rede social, não `meta`. Então a regra de "Paid
Social" não casa, e o tráfego pago do Meta cai em **"Outras mídias pagas"**.

Não está misturado com orgânico e não há perda de dado. O problema é de leitura:
quem abre o relatório padrão não sabe que "Outras mídias pagas" é o Meta, e
qualquer comparação entre canais fica ilegível.

**O conserto é no GA4, não nas UTMs.** `utm_source=meta` já está em dezenas de
anúncios no ar e alimenta o painel do hub. Trocar agora quebra a série histórica
e o de-para do painel, para resolver um problema de rótulo.

---

## 1. Criar o grupo

**Administrador > Exibição de dados > Grupos de canais > Criar grupo de canais.**

| Campo | Valor |
|---|---|
| Nome | `Canais JurIA` |
| Descrição | `Canais padrão com o Meta identificado. utm_source=meta não casa com Paid Social.` |

O botão já abre com os canais padrão carregados, então é só adicionar a regra do
Meta e reordenar. Não refaça busca orgânica, direto, referência e e-mail à mão:
é trabalho para introduzir erro.

## 2. Adicionar a regra do Meta

Nova regra, **no topo da lista**:

| Campo | Valor |
|---|---|
| Nome do canal | `Meta Ads` |
| Condição | `Origem da sessão` **corresponde exatamente a** `meta` |
| E | `Mídia da sessão` **corresponde exatamente a** `paid` |

⚠️ **A ordem das regras decide o resultado.** O GA4 avalia de cima para baixo e
para na primeira que casa. Se `Meta Ads` ficar abaixo de "Outras mídias pagas",
nunca vai casar nada, e a tela não avisa: aparece um canal legítimo com zero
sessões para sempre.

## 3. Conferir

Em **Relatórios > Aquisição > Aquisição de tráfego**, trocar a dimensão para o
grupo novo. O volume que estava em "Outras mídias pagas" precisa aparecer em
"Meta Ads", com o mesmo número.

Se "Meta Ads" vier zerado e "Outras mídias pagas" continuar com o volume, é a
ordem das regras, não a condição.

⚠️ **Dar algumas horas antes de concluir que não funcionou.** O grupo é
retroativo, diferente de quase tudo no GA4, mas o reprocessamento não é
instantâneo. O alcance para trás é limitado pela retenção de dados da
propriedade, que subiu para 14 meses só em 01/10/2026: antes disso eram 2 meses,
e o que passou dessa janela já se perdeu.

## 4. Decidir se vira o principal

Criar o grupo **não** troca o que os relatórios padrão mostram. Eles usam o
**Grupo de canais principal**, que continua sendo o padrão do Google até alguém
promover o novo, em Grupos de canais > Grupo de canais principal.

Sem promover, o grupo novo existe como dimensão nas análises detalhadas e dá
para escolher nos relatórios, mas "Outras mídias pagas" segue aparecendo por
toda parte.

⚠️ **A promoção tem data de início**, a coluna "Data definida como principal".
Ela vale dali para a frente e não reescreve o passado nos relatórios padrão.
Isso é diferente da dimensão em si, que é retroativa. Promover só depois de
conferir a etapa 3.

---

## Usar no funil

O grupo aparece como dimensão nas análises detalhadas. Na guia `Funil do
cadastro`, em DETALHAMENTO, ele substitui com vantagem a `Mídia atribuída ao
primeiro usuário`: em vez de `paid` e `organic`, as etapas se abrem em `Meta
Ads`, `Busca orgânica` e `Direto`.

⚠️ **Para ler o funil por canal, o escopo tem que ser de primeiro usuário.** O
funil atravessa sessões: a pessoa clica no anúncio hoje, se cadastra amanhã e
termina o onboarding depois. Com escopo de sessão, o fundo do funil aparece todo
como Direto, porque ela volta digitando a URL.

---

## Quando revisar

- **Canal novo na mídia.** Google Ads já vem certo por marcação automática, com
  `gclid`, e não precisa de regra. Qualquer canal que dependa de UTM precisa ser
  conferido aqui antes de considerar o relatório confiável.
- **Mudança na convenção de UTM.** Se `utm_source=meta` virar `facebook`, a
  regra do Meta Ads precisa aceitar **os dois**, senão o histórico anterior à
  troca sai do canal e vira "Outras mídias pagas" de novo.
- **Nunca pôr UTM manual em anúncio do Google Ads.** A marcação automática já
  resolve, e a UTM manual sobrescreve e piora.
