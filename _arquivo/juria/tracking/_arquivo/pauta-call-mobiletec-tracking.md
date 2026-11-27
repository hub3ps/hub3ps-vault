---
tipo: arquivo
cliente: juria
atualizado: 2026-11-27
autor: claude
origem: agencia_marketing, clients/juria/tracking/_arquivo/pauta-call-mobiletec-tracking.md (migrado em 27/11/2026)
---
# Pauta da call — Tracking JurIA (Hub3Ps × Mobiletec)

> Objetivo da call: alinhar o que falta pra fechar o tracking de ponta a ponta e definir responsáveis/prazos.
> Detalhe técnico completo em `verificacao-tracking-mobiletec.md`.

---

## ✅ O que já está funcionando (abrir a call com isso)
- **GTM** instalado no `/register` (`GTM-WHQGLTXC`).
- **Cadastro dispara `form_submit_trial`** sozinho, acionando as tags de Lead (GA4, Google Ads, Meta Pixel).
- **Meta recebe o Lead** pelo navegador (Pixel), processado.

Ou seja: a camada de **navegador/lead está de pé**. O que falta é **servidor (vendas) + persistência + alguns ajustes**.

---

## 🔵 Pendências da MOBILETEC (deles)

1. **Persistência no banco (item 1b)**
   Confirmar que o cadastro grava no registro do escritório: `event_id` + `gclid`, `fbclid`, `utm_source/medium/campaign/content/term`.
   *Evidência a mandar:* print do registro do cadastro de teste (event_id `da900115-7d7d-492d-8e4e-347af2211a1b`).

2. **`first_login` (item 2)**
   Hoje **não dispara** (testamos, não chega nem no GTM nem no GA4). Definir: implementar via push no navegador **ou** server-side (Measurement Protocol do GA4) e ativar.

3. **Webhook do Stripe (item 3)**
   Expor o endpoint e **cadastrar no Stripe** os eventos de assinatura paga + upgrade, pra acionar a edge function (vira `trial_to_paid` / `upgrade_plan`).

4. **Deploy das edge functions no Supabase**
   Publicar e rodar o código de **Meta CAPI** e **Google Ads Offline** (que a Hub3Ps vai entregar).

5. **Redirect `juria.app.br → www` preservando query**
   Hoje o redirect quebra quando há parâmetros (`?gclid/utm`). Corrigir pra preservar caminho + parâmetros (hosting).

6. **Inconsistência no push `form_submit_trial`**
   Em um cadastro vieram `value/currency/porte/area`; em outro, não. Investigar por que o payload varia (precisa vir sempre completo).

7. **Taxonomia de `plan`**
   No cadastro o push manda `plan: "trial"`. Garantir que no `trial_to_paid` o `plan` venha como Basic/Pro/Enterprise.

---

## 🟠 Pendências da HUB3PS (nosso) — destravar antes de cobrar

1. **Token da CAPI (System User do BM Meta)** — gerar e enviar pra Mobiletec. **Bloqueio de raiz**: sem ele, a CAPI não sobe.
2. **Código das edge functions** (CAPI + Google Ads Offline) — entregar pra eles deployarem.
3. **Tag GA4 no GTM para `first_login`** — se a rota escolhida for navegador, criar a tag de encaminhamento (depende da decisão do item 2 deles).
4. **Final URLs dos anúncios sempre em `www`** — ao montar as campanhas.
5. **Propagação de parâmetros LP → /register** — nossa, quando as LPs forem publicadas (hoje são mockup).

---

## 🔗 Ordem que destrava (dependências)
1. **Hub3Ps envia token CAPI + código** → Mobiletec **deploya** edge functions.
2. Mobiletec garante **persistência (1b)** → habilita dedup do Lead (event_id no servidor).
3. Mobiletec **expõe webhook Stripe** → `trial_to_paid`/`upgrade_plan` passam a disparar.
4. Só então dá pra **verificar:** CAPI na Meta, Google Ads Offline, e a **dedup Pixel × CAPI**.

---

## ⏳ Fica pra verificar DEPOIS que ativarem
- `trial_to_paid` / `upgrade_plan` chegando na Meta (CAPI) e no Google Ads (Offline).
- Deduplicação Pixel × CAPI (mesmo `event_id`, navegador + servidor).
- `first_login` no GA4.
