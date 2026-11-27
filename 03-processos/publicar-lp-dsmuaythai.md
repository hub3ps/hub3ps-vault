---
tipo: processo
atualizado: 2026-11-27
autor: claude
origem: agencia_marketing/docs/processos/publicar-lp-dsmuaythai.md (migrado em 27/11/2026)
---
# Publicar a LP · DS Muay Thai

> Caminhos de arquivo e comandos são do repo `agencia_marketing` (`~/Desktop/agencia_marketing`), salvo quando outro repo é citado.

> ⚠️ **O erro que mais custa:** editar dentro de `lps/publicado/trial/` ou
> `lps/publicado/bio/`. Essas pastas são apagadas e refeitas pelo script a cada
> rodada. Edite a fonte e rode o script.

**Um projeto Vercel, dois domínios**, no mesmo desenho do JurIA. O projeto
`dsmuaythai-lps` tem raiz em `clients/dsmuaythai/lps/publicado/`, e o
`vercel.json` dessa pasta escolhe a página pelo domínio.

| Fonte, é aqui que se edita | Gerado, não se edita | Domínio |
|---|---|---|
| `clients/dsmuaythai/lps/trial-lp/index.html` e `styles.css` | `lps/publicado/trial/` | `trial.dsmuaythaisquad.com`, e qualquer outro que não seja o da bio |
| `clients/dsmuaythai/lps/bio/index.html` | `lps/publicado/bio/` | `bio.dsmuaythaisquad.com` |

O `lps/publicado/vercel.json` é **fonte**: o script não toca nele. Domínio novo
no projeto exige regra nova ali, ou ele cai na trial.

Sem build no Vercel: o build roda na sua máquina e a saída é commitada, no mesmo
padrão do hub do JurIA. Arquitetura da LP e do Calendly em
`clients/dsmuaythai/lps/trial-lp/README.md`.

---

## Publicar uma mudança

**1. Edite a fonte.** Copy nova passa antes pela PT (`index-pt.html`), que é onde
se aprova, e depois vai para a EN (`index.html`). A PT nunca vai ao ar.

**2. Confira local.**

```bash
python3 clients/dsmuaythai/ferramentas/servidor-local.py
```

EN em http://127.0.0.1:8765/lps/trial-lp/

**3. Monte a pasta publicada.**

```bash
python3 clients/dsmuaythai/ferramentas/publicar-lp.py
```

Ele diz quantas fotos entraram e o peso antes e depois. Se uma foto referenciada
não existir, ele para com erro em vez de publicar página quebrada.

**4. Confira a versão publicada**, ainda local: http://127.0.0.1:8765/lps/publicado/trial/

É exatamente o que vai ao ar, com as fotos já em WebP.

**5. Commite e dê push.** O push na `main` dispara o deploy.

```bash
git add clients/dsmuaythai/lps/trial-lp
git commit -m "feat(dsmuaythai): <o que mudou na LP>"
git push origin main
```

## Conferir o deploy

```bash
curl -s https://trial.dsmuaythaisquad.com/ | grep -c "<um texto que você mudou>"
```

`1` é publicado. `0` é deploy que não subiu ou ainda está rodando. Pelo MCP do
Vercel: `list_deployments` no time `hub3psmarketing`, projeto `dsmuaythai-lps`.

O endereço `.vercel.app` pede login no Vercel, de propósito. Só o domínio da
academia é público.

---

## Medição: o que não pode quebrar

**Nunca publicar fora de `dsmuaythaisquad.com`.** As 3 conversões personalizadas
da conta filtram por URL contendo `dsmuaythaisquad.com` ou `calendly.com`, e regra
de conversão não se edita depois de criada. Outro domínio faz as três pararem de
contar sem aviso nenhum.

**Quem dispara o quê:**

| Evento | Quem dispara | Onde |
|---|---|---|
| `PageView` | Pixel na própria LP, no `<head>` da `index.html` | Só em `*.dsmuaythaisquad.com`. No local e no `.vercel.app` não dispara |
| `invitee_*` (agendamento) | **O próprio Calendly**, pela integração dele | Em qualquer página que abra o popup |
| `invitee_meeting_scheduled` (pagou) | **A LP**, ao receber `calendly.event_scheduled` do popup, desde 23/10/2026. A integração do Calendly não envia esse de dentro do popup | Só em `*.dsmuaythaisquad.com` |

**Como testar a medição sem estragar a campanha:** abra a LP no domínio real,
clique em agendar e escolha **dia e horário, sem pagar**. Isso gera
`invitee_event_type_page`, `invitee_select_day` e `invitee_select_time`.

**Não conclua o pagamento.** Pagar cobra $29,99 e gera um
`invitee_meeting_scheduled` verdadeiro, que é o evento que a campanha otimiza.

Depois confira pela Marketing API que os disparos vieram do domínio novo:

```bash
curl -sG "https://graph.facebook.com/v21.0/25913656948303012/stats" \
  --data-urlencode "access_token=<TOKEN>" \
  --data-urlencode "aggregation=url" \
  --data-urlencode "start_time=<data do teste>"
```

Tem que aparecer `https://trial.dsmuaythaisquad.com/`. Token em
`credenciais.local.md`, na raiz.

---

## Configuração do projeto, feita uma vez só

Referência, caso precise recriar. A conexão MCP do Vercel **não tem permissão
para criar projeto** no time (403, em 22/09/2026): isso é feito no painel.

| Campo | Valor |
|---|---|
| Time | Hub3Ps Marketing (`hub3psmarketing`) |
| Repositório | `hub3ps/agencia_marketing` |
| Nome | `dsmuaythai-lps` |
| Framework Preset | Other |
| Root Directory | `clients/dsmuaythai/lps/publicado` (era `lps/trial-lp/publicado` até 09/10/2026) |
| Build, Output e Install | vazios, sem build |
| Domínios | `trial.dsmuaythaisquad.com` e `bio.dsmuaythaisquad.com`, um CNAME cada no DNS da academia |
| Proteção | Vercel Authentication em tudo menos domínio próprio, o padrão |

O DNS do `dsmuaythaisquad.com` é do designer que cuida do WordPress. Os únicos
registros que ele precisa criar são os CNAME do `trial` e do `bio`, com o valor
que o Vercel mostra em Settings → Domains.

---

## Página da bio · `bio.dsmuaythaisquad.com`

Mesmo fluxo e mesmo projeto. Fonte em `clients/dsmuaythai/lps/bio/index.html`,
CSS dentro do próprio HTML, e a pasta gerada sai com o argumento `bio`:

```bash
python3 clients/dsmuaythai/ferramentas/publicar-lp.py bio
```

Até 09/10/2026 a bio rodava num projeto próprio, `dsmuaythai`. Foi centralizada
no `dsmuaythai-lps`, e o projeto `dsmuaythai` ficou sem uso: pode ser apagado no
painel.
