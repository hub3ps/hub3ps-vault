---
tipo: arquivo
cliente: juria
atualizado: 2026-11-27
autor: claude
origem: agencia_marketing, clients/juria/tracking/_arquivo/eventos-gtm-a-implementar.md (migrado em 27/11/2026)
---
# Eventos a implementar no GTM · tarefas da Hub3Ps

> Container `GTM-WHQGLTXC`. As quatro tarefas que **não dependem da Mobiletec**,
> levantadas na revisão de tracking de 15/09/2026.
> As duas que dependem deles (e-mail no `Lead` e `event_source_url` completo)
> estão em [[_arquivo/juria/tracking/_arquivo/verificacao-tracking-mobiletec|verificacao-tracking-mobiletec.md]].

Ordem de execução abaixo. A 1 protege todas as outras, então vai primeiro.

| # | Tarefa | Estado |
|---|---|---|
| 1 | Exceção por hostname | ✅ **Feita em 15/09/2026** |
| 2 | `first_login` | ⬜ Pendente |
| 3 | `ClickTrial` | ✅ **Feita em 16/09/2026** |
| 4 | Conversões personalizadas | ⬜ Pendente, depende da 2 e da 3 |

---

## 1. Exceção por hostname · ✅ concluída em 15/09/2026

### O que foi feito

Os dois acionadores existentes passaram de lista de bloqueio para lista de
permissão. Em ambos, `EX — Ambiente de desenvolvimento (inicialização)` e
`(todos os eventos)`:

| Campo | Antes | Depois |
|---|---|---|
| Operador | corresponde a RegEx | **não corresponde a RegEx** |
| Valor | `lovable\.dev\|lovableproject\.com\|lovable\.app\|127\.0\.0\.1\|localhost` | `^(www\.\|portal\.\|trabalhista\.\|previdenciario\.)?juria\.app\.br$` |

Nenhuma tag precisou ser reaberta: os dois acionadores já estavam aplicados como
exceção em `Ads_Lead`, `Ads_Linker`, `GA4_Config`, `GA4_Lead`, `Pixel_Lead` e
`Pixel_PageView`, então a troca se propagou sozinha.

**Testado no Preview antes de enviar**, nas três URLs que cobrem os riscos
distintos, e `Pixel_PageView` disparou nas três:

- `www.juria.app.br`, o caso comum
- `juria.app.br/trabalhista`, apex sem www e com caminho
- `portal.juria.app.br/register`, onde o cadastro acontece

⚠️ **Conferir que a versão foi enviada** no GTM. Salvar não publica.

> **Lembrete para quando criar as tags das etapas 2 e 3:** elas também precisam
> das duas exceções. Uma tag nova nasce sem nenhuma.

### O contexto, para quem ler isso depois

**Por quê:** em 14/09 o preview
`juria-lps-git-feat-cookies-opt-out-hub3psmarketing.vercel.app` mandou evento
para o dataset de produção. É a mesma classe do problema com `lovable.dev`
registrado na auditoria de agosto. Isso polui aprendizado do algoritmo,
audiências e semelhantes.

**Os acionadores já existem, e o problema é a regra deles.** O container tem
`EX — Ambiente de desenvolvimento (inicialização)` e
`EX — Ambiente de desenvolvimento (todos os eventos)`, criados em agosto e já
aplicados em 6 tags cada. Lendo o `gtm.js` publicado, a condição dos dois é:

```
Page Hostname · corresponde a RegEx · lovable\.dev|lovableproject\.com|lovable\.app|127\.0\.0\.1|localhost
```

**É lista de bloqueio, e foi por isso que o preview do Vercel passou:** o
hostname não contém "lovable". Remendar adicionando `vercel\.app` resolve hoje e
quebra de novo no próximo domínio novo.

**A correção é inverter para lista de permissão,** nos dois acionadores:

| Campo | De | Para |
|---|---|---|
| Operador | corresponde a RegEx | **não corresponde a RegEx** |
| Valor | `lovable\.dev\|lovableproject\.com\|...` | `^(www\.\|portal\.\|trabalhista\.\|previdenciario\.)?juria\.app\.br$` |

Como os dois já estão aplicados nas 6 tags, a mudança se propaga sozinha: não é
preciso reabrir tag nenhuma.

⚠️ **Inverter a lógica tem risco de silenciar produção.** Uma allowlist com erro
de digitação bloqueia tudo e não avisa. Testar os dois lados no Preview antes de
publicar: a LP real precisa disparar, o preview do Vercel não.

Domínio novo que entrar (LP em subdomínio novo) precisa ser adicionado à regex,
senão nasce sem medição. É o lado certo para errar.

---

## 2. `first_login` · a tag que falta

Pendência registrada desde 27/08: o produto empurra o evento para o dataLayer,
e não existe tag que o encaminhe.

**Acionador novo:** `Evento_first_login`, seguindo a convenção do container, que
já tem `Evento_form_submit_trial` e `Consent_Update`.

| Campo | Valor |
|---|---|
| Tipo | Evento personalizado |
| Nome do evento | `first_login` |
| Dispara em | Todos os eventos personalizados |

**Tags:** `Pixel_FirstLogin` e `GA4_FirstLogin`, na mesma família de
`Pixel_Lead`, `GA4_Lead` e `Ads_Lead`. As duas precisam das exceções
`EX — Ambiente de desenvolvimento (inicialização)` e `(todos os eventos)`.

⚠️ **Conferir o nome no GTM Preview antes de publicar.** Já divergiu uma vez
nesta conta: a integração dizia `form_submit` e o implementado era
`form_submit_trial`.

**Tags:** `agencia_marketing/clients/juria/tracking/_arquivo/gtm-tag-first-login.html` para a Meta, mais
uma tag de evento GA4 com o mesmo acionador, nome de evento `first_login`.

---

## 3. `ClickTrial` · ✅ concluída em 16/09/2026

Mede quanta gente sai da LP em direção ao cadastro.

**Acionador:** `Clique_CTA_Trial` · **Tag:** `Pixel_ClickTrial`
(`agencia_marketing/clients/juria/tracking/_arquivo/gtm-tag-click-trial.html`)

### O acionador, e os dois blocos de condição

Marcar "Aguardar tags" e "Verificar validação" faz o GTM abrir **dois** blocos de
condição, e **eles não são a mesma pergunta**. Foi aqui que a implementação
travou por duas rodadas.

| Bloco | Quando é avaliado | O que usar |
|---|---|---|
| "**Ative** o acionador quando..." (acima dos botões) | no **carregamento da página** | só variáveis de página |
| "**Disparar** esse acionador quando ocorrer um evento..." (abaixo) | no **momento do clique** | variáveis de clique |

Configuração que funciona:

| Campo | Valor |
|---|---|
| Tipo | Clique · **Apenas links** |
| Aguardar tags | **marcado**, 2000 ms |
| Verificar validação | **marcado** |
| Bloco "Ative o acionador" | `Page Hostname` · **corresponde a RegEx** · `juria\.app\.br` |
| Dispara em | **Alguns cliques em links** |
| Bloco "Disparar esse acionador" | `Click URL` · **contém** · `portal.juria.app.br/register` |

Exceções: as duas `EX — Ambiente de desenvolvimento`.

**Consentimento:** a tag exige `ad_storage` nas configurações de consentimento,
igual a `Pixel_PageView` e `Pixel_Lead`. A guarda `if (typeof fbq !== 'function')`
do script já barrava o disparo sem consentimento, porque sem `ad_storage` a
`Pixel_PageView` não carrega e o `fbq` nem existe, mas isso era proteção por
efeito colateral. Com o consentimento declarado, o comportamento é garantido e o
GTM passa a enfileirar a tag em vez de descartar, se o aceite vier depois.

**Aguardar tags não é opcional aqui.** O link leva para outro domínio na mesma
aba, então sem isso a navegação começa antes de o evento sair e o clique some.

A condição por `Click URL` pega os CTAs do hero, do pricing e do rodapé das três
LPs de uma vez, e ignora o login (`/login`) e o "Falar com vendas" do Enterprise,
que é `mailto`. Não depende do texto do botão, que varia entre "Testar 14 dias
grátis", "Testar grátis", "Começar agora" e "Assinar Pro".

### ⚠️ Os dois erros que custaram duas rodadas, para não repetir

**1. `{{Click URL}}` no bloco "Ative o acionador".** O bloco de cima roda no
carregamento da página, quando ainda não houve clique, então a variável é
`undefined`, a condição dá falso e **o acionador nunca é registrado**. O sintoma
engana: o evento `gtm.linkClick` aparece no Preview com a Click URL correta,
porque o listener genérico do GTM está ativo, mas o nosso acionador não está
pendurado nele e não aparece no `_triggers` do evento. Variável de clique só
funciona no bloco de baixo.

**2. Variável de GTM sem aspas dentro do JavaScript.** A primeira versão da tag
tinha `lp: {{Page Hostname}}`. O GTM substitui por texto puro, então o `https://`
da URL virava início de comentário JS e quebrava o parse do script inteiro. A tag
falhava antes de executar o `fbq(...)`, **sem erro visível no Console do
Preview**. Variável de GTM dentro de string sempre entre aspas.

### Testado e publicado em 16/09/2026

`Pixel_ClickTrial` dispara no clique do CTA em `www.juria.app.br`, com `lp` e
`destino` preenchidos, e não dispara no login nem no "Falar com vendas". Versão
enviada no GTM no mesmo dia.

**Próximo passo:** conferir pela API, depois de um dia de tráfego real, se o
evento `ClickTrial` está entrando no dataset (`ads_get_dataset_stats`,
`aggregation: event`). Só depois disso criar a conversão personalizada da
tarefa 4, senão a regra nasce sem sinal.

---

## 4. Conversões personalizadas · a conta tem zero hoje

Confirmado pela API em 15/09: `ads_get_customconversions` devolve lista vazia.
Sem isso os eventos novos existem no dataset mas não viram coluna no Ads Manager.

Gerenciador de Eventos → Conversões personalizadas → Criar:

| Nome | Fonte | Evento | Categoria |
|---|---|---|---|
| Clique no CTA de trial | JurIA (`1009120801605718`) | `ClickTrial` | Outro |
| Primeiro login | JurIA (`1009120801605718`) | `FirstLogin` | Outro |

Só criar depois que os eventos aparecerem no dataset, senão a regra nasce sem
sinal e fica difícil saber se o problema é a tag ou a conversão.

**Não criar conversão personalizada por URL.** A URL que chega ao Pixel não tem
caminho: todos os eventos registram host raiz (`portal.juria.app.br/`,
`www.juria.app.br/`), nunca `/register`. Uma regra por URL não teria em que se
apoiar. Isso só muda quando a Mobiletec corrigir o `event_source_url`.

---

## O que essas quatro tarefas entregam, e o que não entregam

**Entregam:** a taxa que motivou o trabalho. Com `ClickTrial` no numerador e
`Lead` no denominador, dá para ler quanto da intenção de trial vira cadastro, e
comparar isso entre criativos pelo `utm_content`.

**Não entregam:** o número absoluto correto. `ClickTrial` dispara no navegador e
carrega consent de `ad_storage`, então conta só quem aceitou cookies. A CAPI não
socorre: clique não existe fora do navegador. Enquanto a decisão de cookies
estiver parada, a taxa serve para **comparar criativos entre si**, não para dizer
ao cliente "X% dos visitantes clicam".

Contexto da decisão de cookies:
[[_arquivo/juria/tracking/_arquivo/consentimento-cookies-decisao|consentimento-cookies-decisao.md]].

---

## Verificação, depois de publicar

1. GTM Preview numa LP: clicar num CTA e ver `ClickTrial` disparar, com o
   acionador certo e sem a exceção bloqueando.
2. Repetir com o preview do Vercel aberto: a tag **não** pode disparar.
3. Events Manager → Eventos de teste: `ClickTrial` chega com `lp` e `destino`.
4. No dia seguinte, `ads_get_dataset_stats` com `aggregation: host`: nenhum
   host fora da regex de produção.
