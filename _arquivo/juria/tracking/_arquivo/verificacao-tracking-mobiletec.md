---
tipo: arquivo
cliente: juria
atualizado: 2026-11-27
autor: claude
origem: agencia_marketing, clients/juria/tracking/_arquivo/verificacao-tracking-mobiletec.md (migrado em 27/11/2026)
---
# Verificação do Tracking · Entregas da Mobiletec (JurIA)

> **Objetivo:** confirmar se a Mobiletec executou corretamente as entregas do lado do produto, descritas em `lps/integracao/` e `lps/eventos/`. Eles informaram que concluíram.
> **Domínio:** juria.app.br · **Container GTM:** `GTM-WHQGLTXC` · **Stack:** React/TS + Supabase (Edge Functions) + Stripe.
> **Data da verificação:** ___/___/2026 · **Responsável:** Guilherme (Hub3Ps)

---

## Método: smoke test ponta-a-ponta

Um único fluxo de teste percorrendo toda a jornada, seguindo o **mesmo `event_id` e as mesmas UTMs** em todos os painéis.

**URL de teste (entrar por ela no /register):**
> ⚠️ **Atualização 28/07:** o `/register` migrou para **`portal.juria.app.br/register`**. A URL abaixo (`juria.app.br`) é histórica e hoje retorna **404**. Ver "Teste 04" no log de execução.
```
https://juria.app.br/register?gclid=TEST_GUI_0623&fbclid=TESTFB_0623&utm_source=verif&utm_medium=qa&utm_campaign=teste_tracking&utm_content=ctrl&utm_term=smoke
```

Sequência: **cadastro** → **primeiro login** → **virar pagante (Stripe)** → **upgrade**.

---

## Entregas e divisão (recap)

| # | Entrega da Mobiletec | Eu (Guilherme) consigo auditar? |
|---|---|---|
| Pré | Container `GTM-WHQGLTXC` no `/register` | ✅ Sim (DevTools / Tag Assistant) |
| Ponto 1a | Disparo `form_submit_trial` no cadastro | ✅ Sim (GTM Preview + GA4 + Meta) |
| Ponto 1b | Persistir `event_id` + `gclid`/`fbclid`/`utm_*` no registro do escritório | ❌ Não (precisa Supabase → **pedir evidência**) |
| Ponto 2 | `first_login` | ✅ Parcial (GA4) |
| Ponto 3a | Webhook Stripe → edge function monta payload | ❌ Não (precisa Supabase/Stripe → **pedir evidência**) |
| Ponto 3b | Envio server-side (Meta CAPI + Google Ads Offline) | ✅ Sim (Meta Events Manager + Google Ads) |

---

## ✅ Checklist: o que EU consigo verificar

### 0. Pré-requisito: GTM no /register
- [ ] Abrir `/register` com **Tag Assistant** (ou GTM Preview) conectado.
- [ ] No console: `window.google_tag_manager` existe e contém `GTM-WHQGLTXC`.
- [ ] No Network: requisição a `googletagmanager.com/gtm.js?id=GTM-WHQGLTXC` com status 200.
- **APROVADO se:** o container carrega na página de cadastro.

### 1a. Ponto 1: disparo `form_submit_trial`
- [ ] Entrar pela URL de teste acima e concluir um cadastro de trial.
- [ ] No console (antes/depois do submit): inspecionar `window.dataLayer`.
- [ ] Confirmar o push com **nome do evento**, `event_id` (UUID), `value`, `currency: 'BRL'`, `plan` (+ `porte`/`area` se o form coleta).
- [ ] **GTM Preview:** o evento aciona as tags **GA4**, **Meta Pixel** e **Google Ads (lead)**.
- [ ] **GA4 DebugView:** o evento chega com os parâmetros.
- [ ] **Meta Events Manager → Test Events:** Pixel registra o evento.
- **APROVADO se:** push dispara no sucesso do cadastro, com todos os campos, e as 3 tags acionam.
- ⚠️ **Conferir nome do evento:** a integração diz `form_submit_trial`; o mapa de eventos diz `form_submit`. O nome implementado **tem que bater com o gatilho do GTM**. Anotar qual foi usado: `________________`

### 1c. Deduplicação (Pixel × CAPI)
- [ ] **Meta Events Manager:** o evento de cadastro chega por **navegador (Pixel) e servidor (CAPI)** com o **mesmo `event_id`**.
- [ ] Events Manager mostra os eventos como **deduplicados** (não contados em dobro).
- **APROVADO se:** mesmo `event_id` nas duas fontes e dedup reconhecida pela Meta.

### 2. Ponto 2: `first_login`
- [ ] Logar pela **primeira vez** com a conta de teste recém-criada.
- [ ] **GA4 Realtime/DebugView:** `first_login` aparece.
- [ ] Logar de novo (2ª vez) → `first_login` **NÃO** deve disparar.
- **APROVADO se:** dispara exatamente uma vez, no primeiro acesso.

### 3b. Ponto 3: venda chega na Meta e no Google
- [ ] Após o pagamento de teste (ver seção Stripe abaixo): **Meta Events Manager** mostra `trial_to_paid` via **CAPI** (servidor), **sem** tag concorrente no navegador, com dedup.
- [ ] Repetir para `upgrade_plan` após um upgrade.
- [ ] **Google Ads → Ferramentas → Conversões → Uploads:** o Offline Conversion Import aceitou a conversão (pode levar de horas até ~24-48h para aparecer).
- [ ] **Atribuição:** a conversão carrega o `gclid` (`TEST_GUI_0623`) / UTMs do cadastro, loop fechado.
- **APROVADO se:** CAPI recebe a venda com dedup, Offline Import aceita, e a venda fica ligada à campanha de origem.

---

## ❌ Evidências a SOLICITAR à Mobiletec (não tenho acesso)

Mandar para o contato técnico da Mobiletec e pedir print/export:

1. **Persistência (Ponto 1b):** consulta/print do registro do escritório de teste no Supabase mostrando `event_id`, `gclid`, `fbclid` e `utm_*` gravados.
2. **Edge function (Ponto 3a):** log da edge function recebendo o webhook do Stripe e montando o payload (`event_id` estável tipo `sub_...`, `value`, `currency`, `plan`, `email_sha256`, UTMs lidas do Ponto 1).
3. **Webhook Stripe:** confirmação de que o endpoint do webhook está configurado e ativo (eventos `checkout.session.completed` / assinatura paga / upgrade).
4. **Deploy do código Hub3Ps:** confirmar que o código + credenciais de CAPI/Offline que a Hub3Ps entregou foram publicados e estão rodando no Supabase deles.

---

## Como fazer o teste de pagamento (Stripe)

O fluxo `trial_to_paid`/`upgrade_plan` só dispara com uma transação real. Opções:
- **(Preferível)** Pedir à Mobiletec para rodar em **Stripe test mode** (cartão `4242 4242 4242 4242`) e compartilhar o log da edge function, assim valida sem cobrança real.
- **(Alternativa)** Fazer uma transação real de baixo valor e estornar depois.

---

## Veredito

| Entrega | Status | Observação |
|---|---|---|
| GTM no /register | ⬜ |  |
| Ponto 1 · disparo | ⬜ |  |
| Ponto 1 · persistência | ⬜ | (evidência Mobiletec) |
| Dedup Pixel × CAPI | ⬜ |  |
| Ponto 2 · first_login | ⬜ |  |
| Ponto 3 · webhook/edge | ⬜ | (evidência Mobiletec) |
| Ponto 3 · CAPI + Offline | ⬜ |  |

**Conclusão geral:** _____________________________________________

---

## Log de verificação (execução)

### Achados de infraestrutura
- ~~**Redirect não-www quebra com parâmetros**~~ → **CORRIGIDO.** Verificado em 31/08/2026: `juria.app.br` e `www.juria.app.br` respondem 200 e **preservam a query string**: as UTMs chegam intactas nos dois. O redirect passou a manter caminho e parâmetros.
- **Propagação home → /register:** não passa os parâmetros, esperado, pois a LP real não está publicada (a propagação Hub3Ps vive nas LPs).
- **Nome do evento confirmado:** `form_submit_trial` (não `form_submit`). Gatilho + tags Lead (GA4_Lead, Ads_Lead, Pixel_Lead) ok.

### Resultados por item
- **Pré (GTM no /register):** ✅ container `GTM-WHQGLTXC` presente.
- **1a (form_submit_trial no cadastro real):** ✅ dispara sozinho no submit.

### Testes de cadastro (event_id pra cruzar com o banco, pedir à Mobiletec)
- **Teste 01** (sem UTM, e-mail `+tracking01`): `event_id = 7682f275-5a8f-4569-84a2-8bb3d23c1479` · value 199 · currency BRL · porte pequeno · area trabalhista · plan trial.
- **Teste 02** (com UTM completa, e-mail `+tracking02`): `event_id = da900115-7d7d-492d-8e4e-347af2211a1b` · plan trial · **value/currency/porte/area AUSENTES** (verificar).
  - UTMs usadas: `gclid=TEST_GUI_0623`, `fbclid=TESTFB_0623`, `utm_source=verif`, `utm_medium=qa`, `utm_campaign=teste_tracking`, `utm_content=ctrl`, `utm_term=smoke`.

### Achado em aberto
- **Inconsistência no payload do form_submit_trial:** Teste 01 trouxe value/currency/porte/area; Teste 02 não. Confirmar se é bug de implementação.

### Pedir à Mobiletec (1b)
- Registro do escritório do Teste 02: confirmar `event_id` salvo (= `da900115-...`?) + `gclid`/`fbclid`/`utm_*`.

### Meta · Events Manager (Teste 03, e-mail `+tracking03`)
- **Lead** recebido e **Processado** (Pixel `1009120801605718`), event ID `f7d17a3…`.
- ⚠️ **Todos os eventos só por Navegador: nenhum por Servidor (CAPI).** CAPI não está ativa (bate com tarefa 11 pendente). Dedup Pixel × CAPI não verificável até a CAPI subir.

### Item 2 · first_login: ❌ NÃO verificado
- No login (`+tracking03`): **nada no GA4 DebugView**.
- No Tag Assistant apareceu só `gtm.historyChange-v2` (troca de rota `/login`→`/dashboard`, automático do GTM), **não é** o `first_login`.
- Conclusão: nenhum `first_login` disparou (navegador). Era previsto server-side (backend JurIA), confirmar com a Mobiletec se foi implementado; sem evidência hoje.

### Teste 04 · 28/07/2026 · cadastro com todos os parâmetros (Hub3Ps)

⚠️ **Domínio atualizado:** o `/register` agora vive em **`portal.juria.app.br/register`**
(HTTP 200, container `GTM-WHQGLTXC` presente, preserva a query string). O antigo
`juria.app.br/register` (e `www`) retorna **404**: aquele domínio é só das LPs.

**URL usada no teste:**
```
https://portal.juria.app.br/register?gclid=QAGCLID0728&fbclid=QAFBCLID0728&utm_source=qa-source-0728&utm_medium=qa-medium-0728&utm_campaign=qa-campaign-0728&utm_content=qa-content-0728&utm_term=qa-term-0728&area=previdenciario
```
Cada valor é auto-rotulado (ex.: `utm_content=qa-content-0728`) para facilitar a
conferência coluna a coluna no banco.

**Valores esperados no registro do escritório (Supabase):**

| Parâmetro | Origem | Valor esperado |
|---|---|---|
| `gclid` | URL | `QAGCLID0728` |
| `fbclid` | URL | `QAFBCLID0728` |
| `utm_source` | URL | `qa-source-0728` |
| `utm_medium` | URL | `qa-medium-0728` |
| `utm_campaign` | URL | `qa-campaign-0728` |
| `utm_content` | URL | `qa-content-0728` |
| `utm_term` | URL | `qa-term-0728` |
| `area` | URL | `previdenciario` |
| `event_id` | gerado na página | UUID · anotar do dataLayer: `________________` |
| `value` | página | `199` |
| `currency` | página | `BRL` |
| `plan` | página | `trial` |

**Passos:** (1) abrir a URL e concluir o cadastro (e-mail com alias `+qa0728`);
(2) no console, achar o push `form_submit_trial` em `window.dataLayer` e anotar o
`event_id`; (3) pedir à Mobiletec o registro no Supabase e conferir a tabela acima.

**Foco do teste:** reconfirmar se `value`/`currency`/`area` vêm **sempre completos**
(o bug de inconsistência entre Teste 01 e Teste 02). Resultado: `________________`

### Teste 05 · 27/08/2026 · auditoria do conjunto de dados pelo MCP da Meta (Hub3Ps)

Verificação feita **direto na API da Meta** (`ads_get_dataset_stats` e
`ads_get_dataset_quality`, dataset `1009120801605718`), sem depender de
Test Events nem de evidência da Mobiletec.

**🟢 A CAPI subiu.** O quadro de "só navegador" descrito nos Testes 01–04 não vale mais:

| Data | Navegador | Servidor | Leitura |
|---|---|---|---|
| até 14/08 | sim | **não** | só Pixel · situação dos testes anteriores |
| 16–17/08 | sim | **sim** (1/h) | primeiros eventos server-side |
| 18/08 em diante | sim | **sim** | pareamento ~1:1 constante, hora a hora |

O pareamento 1:1 sustentado por nove dias é a assinatura de dedup funcionando:
o mesmo evento chega pelas duas vias e a Meta conta uma vez. Isso destrava o
item 1c e fecha o "Bloqueio de raiz" abaixo, o token da CAPI **foi** entregue.

**Eventos ativos no dataset:** `PageView`, `Lead`, `SubscribedButtonClick`.

**Qualidade de correspondência (EMQ), escala 0–10:**

| Evento | EMQ | Cobertura de e-mail | Observação |
|---|---|---|---|
| `SubscribedButtonClick` | 7,9 | 100% | melhor sinal da conta |
| `Lead` | 6,8 | **33,3%** | ⚠️ maior alavanca de melhoria |
| `PageView` | 6,5 | 25,7% | `fbc` em 52,6% |

`ip_address`, `user_agent` e `fbp` estão em 100% nos três. O gargalo é o e-mail:
elevar a cobertura no `Lead` puxa as três notas junto e melhora o custo por resultado.

**Leitura dos dois eventos que não aparecem no dataset** (corrigida em 27/08 com o Guilherme):
- `first_login`: o evento **já chega ao dataLayer/GTM**. O que falta é a tag de evento
  personalizado no container que o encaminha para GA4/Meta. **Ação Hub3Ps**, não Mobiletec.
- `Purchase`: o caminho **já foi testado e está funcionando** (os 2 eventos de 28–29/07 são
  justamente essa validação, e chegaram por navegador *e* servidor). A ausência de eventos
  recentes é só reflexo de não ter havido venda no período, não de falha na medição.

### Teste 06 · 15/09/2026 · revisão completa pela API (Hub3Ps)

Varredura do dataset `1009120801605718` por `ads_get_dataset_details`,
`ads_get_dataset_quality`, `ads_get_dataset_stats` (agregações `event`, `url`,
`host`, `event_source`), `ads_get_customconversions` e `ads_pixel_event_read`.

**🔴 Regressão: o `Lead` perdeu o e-mail.**

| | 27/08 (Teste 05) | 15/09 |
|---|---|---|
| EMQ do `Lead` | 6,8 | **6,1** |
| Cobertura de e-mail | 33,3% | **0%** |

O evento chega só com `ip_address`, `user_agent` e `fbp`, os três em 100%. Sem
e-mail, sem telefone e **sem `fbc`**. Pedido enviado ao Saulo (dev da Mobiletec)
por WhatsApp em 15/09, junto com o `event_source_url`.

**🟢 A CAPI segue saudável.** Comparando `SERVER_ONLY` contra `WEB_ONLY` na
janela de 28 dias: 28 leads pelo servidor e 26 pelo navegador, com 26 pareados.
Os 2 que só o servidor viu são exatamente o ganho da CAPI, casos em que o
navegador não mandou. Dataset ativo, disparando por navegador e servidor no
momento da consulta.

**A URL não chega só sem query string: chega sem caminho.** Em 11 dias de
`aggregation: url`, nenhum evento registra path. Só host raiz
(`www.juria.app.br/`, `portal.juria.app.br/`, `previdenciario.juria.app.br/`).
Isso amplia o achado do Teste 05: além de não dar para atribuir cadastro a
criativo, **não dá para criar conversão personalizada por URL**, porque não há
caminho em que a regra se apoie.

**O `PageView` do portal está afogado por uso do produto.** Picos de 308, 178 e
173 eventos numa hora, contra as ~45 visitas diárias vindas de anúncio. É o SPA
disparando a cada troca de tela para quem já é cliente. Consequência prática:
"chegou no `/register`" não é separável de "usou o sistema" pelo `PageView`.

**A conta não tem nenhuma conversão personalizada.** `ads_get_customconversions`
devolve lista vazia. Os eventos existem no dataset e não viram coluna no Ads
Manager.

**Poluição de ambiente, capítulo 2.** O preview
`juria-lps-git-feat-cookies-opt-out-hub3psmarketing.vercel.app` mandou 2 eventos
em 14/09. A exceção de hostname do container cobria só o Lovable. **Corrigido no
mesmo dia**, ver [[_arquivo/juria/tracking/_arquivo/eventos-gtm-a-implementar|eventos-gtm-a-implementar.md]].

**`SubscribedButtonClick` não é configuração nossa.** `ads_pixel_event_read` não
lista nenhuma regra de evento no pixel, então o evento vem do rastreamento
automático do próprio Pixel. EMQ 6,9, e-mail em 12,1%.

### Teste 07 · 18 a 22/09/2026 · a duplicação do `Lead` e o espelho da Meta

**O sintoma.** Em 18/09 um único cadastro virou 3 eventos de `Lead`: 1 pelo
navegador e 2 pelo servidor. Até 17/09 vinham 2 por cadastro, 1 e 1, com dedup
funcionando. A Meta parou de reportar deduplicação e passou a exibir "Melhorar
desduplicação deste evento".

**A causa, localizada pelo dev da Mobiletec em 22/09.** No Gerenciador de
Negócios, em Conversions API, existe uma conexão **"Supported by Meta"** com
**"Automatically connect only your datasets"** ligada. O dataset foi conectado
automaticamente pela Meta em **16/08 às 08:40**. O recurso pega o que o Pixel
manda pelo navegador e **reenvia como evento de servidor**, espelhando
`PageView`, `ViewRegister`, `ClickTrial` e `Lead`.

Evidências que fecham o diagnóstico: servidor sempre maior ou igual ao
navegador, e a conexão recebe evento a cada poucos minutos mesmo sem cadastro
nenhum.

Em 18/09 passaram a existir três remetentes ao mesmo tempo: Pixel, espelho da
Meta e a CAPI que a Mobiletec subiu naquele dia.

**A resolução.** O espelho foi desligado em 22/09. Ficaram Pixel + CAPI da
Mobiletec, que deduplicam pelo mesmo `event_id`. Os eventos voltaram ao correto.
A alternativa seria manter o espelho e desligar a CAPI da Mobiletec, o que
custaria e-mail, nome e telefone em hash e o IP real do cliente.

**O que este teste corrige nos anteriores:**

| Registro | O que dizia | O que era |
|---|---|---|
| Teste 05 · 27/08 | "A CAPI subiu", token confirmado pelos eventos server-side de 16/08 | 16/08 é a data da conexão automática da Meta. Os eventos de servidor eram o espelho, não CAPI da Mobiletec |
| Teste 06 · 15/09 | "A CAPI segue saudável"; os 2 leads que só o servidor viu eram "o ganho da CAPI" | Espelho não acrescenta sinal, reenvia o que o navegador mandou. Não havia ganho a creditar |
| Teste 06 · 15/09 | E-mail no `Lead` caiu de 33,3% para 0%, tratado como regressão da Mobiletec | Os 33,3% eram o Advanced Matching automático da Meta lendo o formulário antigo. A Mobiletec nunca enviou e-mail no `Lead`. Não foi regressão de código deles |

**Achado paralelo, mesmo dia.** Os cookies de primeira parte do dataset estavam
desligados (`first_party_cookie_status: first_party_cookie_disabled`), o que
zerou `fbp` e `fbc` em **todos** os eventos de navegador de uma vez: `fbp` do
`PageView` caiu de 98,5% para 1,8%, e o `Lead` ficou sem `fbp` nenhum. Religados
em 18/09.

**Lição de método.** Evento por servidor **não** prova CAPI própria. Antes de
creditar envio server-side a um integrador, conferir em Gerenciador de Negócios
→ Conversions API se existe conexão automática da Meta ligada. O Gerenciador de
Eventos não separa dois remetentes de CAPI: os dois aparecem como "API de
conversões", "Amostras de atividades" mascara custom data como `_removed_` e o
export sai vazio. Quem responde é o histórico da conexão, não a tela de eventos.

---

# RESUMO EXECUTIVO · Status da verificação

> Atualizado em **15/09/2026** após o Teste 06. O **teste de ponta a ponta das conversões
> segue concluído**: cadastro e venda percorrem o caminho até a Meta pelo navegador e pelo
> servidor, com deduplicação.
>
> 🔴 **O que mudou para pior:** o `Lead` perdeu a cobertura de e-mail, que saiu de 33,3%
> para 0%, e o EMQ caiu de 6,8 para 6,1. É a pendência mais cara em aberto.

## ✅ Funcionando (verificado de fora)
- **GTM no /register**: container `GTM-WHQGLTXC` ativo.
- **1a: `form_submit_trial`** dispara no cadastro real, acionando GA4_Lead, Ads_Lead e Pixel_Lead.
- **Meta recebe o Lead** pelo **navegador (Pixel) e pelo servidor (CAPI)**.
- **1c: dedup Pixel × CAPI**: o pareamento ~1:1 registrado a partir de 18/08 era Pixel contra
  **espelho da Meta**, não contra CAPI própria (Teste 07). A dedup real entre Pixel e a CAPI
  da Mobiletec, pelo mesmo `event_id`, vale a partir de **22/09**, quando o espelho saiu.
- **3: venda (trial → pagante)**: caminho validado em 28–29/07, por navegador e servidor.
  Sem eventos recentes apenas por não ter havido venda no período.

## 🔧 Pendente do nosso lado (Hub3Ps)

Passo a passo dos quatro, com as tags prontas:
[[_arquivo/juria/tracking/_arquivo/eventos-gtm-a-implementar|eventos-gtm-a-implementar.md]].

- ✅ **Exceção por hostname:** feita em 15/09. Virou lista de permissão, então preview
  novo já nasce bloqueado.
- ⬜ **`first_login`:** o evento chega ao GTM; falta criar a tag que o encaminha. Sem isso
  o passo "ativou a conta" não entra em nenhum relatório.
- ⬜ **`ClickTrial`:** medir o clique nos CTAs de trial das LPs, para ler a taxa de
  intenção contra cadastro. Nasce subcontado enquanto o consentimento for prévio, porque
  clique não existe fora do navegador e a CAPI não recupera.
- ⬜ **Conversões personalizadas:** a conta tem zero. Sem elas os eventos existem no
  dataset e não viram coluna no Ads Manager.

## ⏳ Aguardando evidência/ação da Mobiletec
- **1b: persistência:** confirmar `event_id` + `gclid`/`fbclid`/`utm_*` gravados no registro do
  escritório (Teste 02 = `da900115-...`). É o único item que ainda depende deles.

## ⚠️ Achados a resolver
- **`event_source_url` chega sem query string:** os 7 eventos de `Lead` do período registram
  `https://portal.juria.app.br/` puro, sem `utm_*` nem `fbclid`. Por isso o Gerenciador de Eventos
  não consegue atribuir cadastro a criativo, e um cadastro de 26/08 ficou sem conjunto de origem.
  A Mobiletec informou em 18/09 que a CAPI deles passou a enviar a URL completa, com `/register`,
  UTMs e `fbclid`. **Não verificado:** a medição de 18/09 ainda trouxe a raiz nua, mas o cadastro
  daquele dia foi teste do próprio dev, que entrou direto no portal, sem parâmetro de campanha.
  Remedir no próximo cadastro vindo de anúncio.
- ~~🔴 **Cobertura de e-mail no `Lead` em 0%**, regressão da Mobiletec~~ → **diagnóstico
  corrigido no Teste 07**. Não era regressão de código deles: os 33,3% de 27/08 vinham do
  Advanced Matching automático da Meta lendo o formulário antigo, e pararam quando o
  formulário mudou. Desde 18/09 a CAPI da Mobiletec envia e-mail com hash SHA-256,
  `external_id`, `fbp`, `fbc`, IP e user agent. **Remedir a cobertura agora que o espelho
  da Meta saiu do caminho**, porque enquanto ele existia metade dos eventos de servidor
  era reenvio de navegador, sem e-mail nenhum.
- **Inconsistência no push:** `value`/`currency`/`porte`/`area` presentes no Teste 01, ausentes no Teste 02. Investigar.
- ~~**Redirect não-www quebra com parâmetros**~~ → **CORRIGIDO** (verificado em 31/08/2026; as UTMs sobrevivem nos dois domínios).
- **Taxonomia de `plan`:** `form_submit_trial` manda `plan: "trial"`; garantir Basic/Pro/Enterprise no `trial_to_paid`.
- **Colisão de `utm_term`:** os conjuntos `TRAB · Aberto · Sul 28-55` e `TRAB · Aberto · Sul 28-60` carregam o mesmo `trabalhista_aberto`, então aparecem somados no Analytics. Diferenciar na próxima edição dos anúncios.

## ✅ Bloqueio de raiz: RESOLVIDO
- **Token da CAPI (System User do BM Meta):** **entregue**. ⚠️ A confirmação registrada no
  Teste 05 estava errada: os eventos server-side de 16/08 **não** eram prova de uso do token,
  eram o espelho automático da Meta (Teste 07). A CAPI própria da Mobiletec só começou a
  enviar `Lead` em **18/09**.
- **Código da edge function (CAPI + Google Ads Offline):** o trecho de venda foi validado em
  julho, por navegador e servidor. Google Ads Offline reconfere na próxima venda real.
- **Tag GA4 no GTM para `first_login`:** segue em aberto, ver "Pendente do nosso lado" acima.

