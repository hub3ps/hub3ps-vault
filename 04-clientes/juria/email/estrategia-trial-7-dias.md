---
tipo: cliente-doc
cliente: juria
atualizado: 2026-11-27
autor: claude
origem: agencia_marketing, clients/juria/email/estrategia-trial-7-dias.md (migrado em 27/11/2026)
---
# JurIA · E-mail marketing do trial de 7 dias

> **Estado:** proposta para a reunião com a Mobiletec de 07/10/2026. Nada aqui
> está no ar.
>
> **Escopo seguido:** briefing "Estratégia de Email Marketing para Trial de 7
> Dias", de 05/10/2026. A entrega segue a ordem da seção 10 do briefing.
>
> **Fontes do produto:** `../comercial/planos-e-creditos.md` (planos, trial,
> créditos), `../brief.md` (ICP, dores, objeções, vocabulário) e
> `../lps/eventos.json` (eventos já medidos). Preço ou limite novo se confere
> primeiro em `planos-e-creditos.md`.
>
> Substitui o rascunho de 7 e-mails em 14 dias que estava na aba Plano. O trial
> caiu para 7 dias em 29/09/2026.
>
> **Este arquivo é a versão completa, de trabalho.** A versão que vai para a
> Mobiletec é um resumo em cinco seções, escrito para quem não é da área:
> https://claude.ai/artifact/MVXYPqjQiwi4uHsvDxffZY. Mudou algo aqui, atualize
> lá também.

---

## Resumo

A sequência tem **11 e-mails possíveis**, mas cada pessoa recebe no máximo **7
durante o trial**, um por dia. Quem decide o caminho é o comportamento no
produto, não o calendário.

O evento que manda em tudo é o **onboarding completo** (`onboarding_completed`):
OAB cadastrada, captura de intimações ativada e processos importados. Os e-mails
dos dias 0 a 3 existem para levar a pessoa até ele. Os dias 4 a 7 cuidam da
decisão de compra.

**Três decisões travam a execução** e são pauta da reunião: a ferramenta de
e-mail, o caminho dos eventos do produto até ela e quem assina os e-mails. Lista
completa na seção 6.

| Dia | Não ativou | Ativou |
|---|---|---|
| 0 | E1 · Boas-vindas | E1 · Boas-vindas |
| 1 | E2A · Destravar o setup | E2B · Próximo passo: prazos |
| 2 | E2C · Sem login (só quem não voltou ao sistema) | · |
| 3 | E3X · Call de setup | E3 · IA na prática, ou E3B · Back-office se já usou a IA |
| 4 | E4 · Quem está por trás e segurança | E4 |
| 5 | E5 · Faltam 2 dias, com recap do uso | E5 |
| 7 | E6 · Último dia, três caminhos | E6 |
| 14 | E7 · Pós-trial, só se engajou e não assinou | E7 |

Assinou em qualquer ponto: sai da sequência na hora.

---

## 1. Levantamento do produto

Preenchido com o que o repositório prova. O que falta está marcado como
**lacuna** e numerado na seção 6.

| Item | O que o JurIA tem | Onde é usado |
|---|---|---|
| **Evento de ativação** | `onboarding_completed`: fim dos três passos do onboarding (`lawyer`, `intimations`, `portfolio`). Já medido desde 28/09/2026. É premissa, falta provar com dados que ele prevê conversão (lacuna 3) | E1 a E3X |
| **Quick win** | Informar a OAB e ver o próprio acervo importado. A primeira importação por OAB custa 21 créditos e sai do saldo grátis de 50. Por planilha não custa nada | E1, E2A, E3X |
| **ICP e cargos** | Sócio-administrador (35 a 55 anos, compra por custo e controle) e gestor de operações (28 a 40, pilota o trial). Escritórios de 1 a 15 advogados | Tom e exemplos |
| **Dores e resultados** | 1. Ferramentas separadas para processo, prazo e financeiro. 2. Medo de perder prazo. 3. Horas de pesquisa e redação manual | E2B, E3, E3B |
| **Provas reais** | **Nenhum case autorizado** (lacuna 8). Prova disponível: Mobiletec com 25 anos em SC, LGPD, autenticação em dois fatores, isolamento por escritório, auditoria e backup diário | E4 |
| **Planos e preço** | Solo R$ 69 · Plus R$ 159 · Max R$ 499 · Ilimitado R$ 1.299. Só mensal, sem fidelidade. Desconto ou extensão de trial: **não sabemos se existem** (lacuna 6) | E5, E6, E7 |
| **Eventos rastreáveis** | Cadastro, passos do onboarding e onboarding completo já existem. Login recorrente, uso de IA, alertas de prazo, convite e visita à tela de planos **não existem** (seção 3) | Todos os gatilhos |
| **Canal humano** | Link de agendamento, quem atende e em quanto tempo: **não definido** (lacuna 5) | E2A, E3X, E5, E6 |
| **Remetente** | `[NOME_REMETENTE]`, `[CARGO]`. **Não definido** (lacuna 4) | Todos |
| **Regras do trial** | 7 dias, **sem cartão**. Limites: 2 usuários, 20 clientes, 50 processos, 100 MB, 20 gerações de IA, todas as funcionalidades. O que acontece ao expirar: **não sabemos** (lacuna 7) | E5, E6, E7 |

---

## 2. Fluxo de gatilhos

Escrito em formato genérico, porque a ferramenta ainda não foi escolhida. Vale
para qualquer ferramenta que receba eventos por API ou webhook.

**Dia 0** é o momento do `form_submit_trial`. Os prazos contam a partir dele.

| # | Regra | Cancela se, antes do envio |
|---|---|---|
| R1 | SE `form_submit_trial` ENTÃO enviar **E1** na hora | Nunca |
| R2 | SE passaram 24h do cadastro E **não** houve `onboarding_completed` ENTÃO enviar **E2A** | Houve `onboarding_completed` |
| R3 | SE passaram 24h do cadastro E houve `onboarding_completed` ENTÃO enviar **E2B** | Houve `deadline_alerts_enabled` |
| R4 | SE passaram 48h do cadastro E **não** houve `login` depois da sessão do cadastro ENTÃO enviar **E2C** | Houve `login` |
| R5 | SE dia 3 E **não** houve `onboarding_completed` ENTÃO enviar **E3X** | Houve `onboarding_completed` |
| R6 | SE dia 3 E houve `onboarding_completed` E **não** houve `ai_generation_created` ENTÃO enviar **E3** | Houve `ai_generation_created` |
| R7 | SE dia 3 E houve `onboarding_completed` E houve `ai_generation_created` ENTÃO enviar **E3B** | Houve `fee_created` |
| R8 | SE dia 4 E **não** houve `subscription_started` ENTÃO enviar **E4** | Assinou |
| R9 | SE dia 5 E **não** houve `subscription_started` ENTÃO enviar **E5** | Assinou |
| R10 | SE dia 7 E **não** houve `subscription_started` ENTÃO enviar **E6** | Assinou |
| R11 | SE passaram 7 dias de `trial_expired` E **não** assinou E engajou (`onboarding_completed` OU `login` em 3 dias diferentes) ENTÃO enviar **E7** | Assinou ou descadastrou |
| R12 | SE `subscription_started` ENTÃO tirar da sequência na hora e passar para o onboarding de cliente | · |
| R13 | SE `user_invited` OU `pricing_page_viewed` OU `login` em 3 dias diferentes ENTÃO **avisar o comercial** uma vez por conta, sem mudar os e-mails | Assinou |

**Regras gerais**

- **Um e-mail por dia por pessoa.** R2 e R3 são excludentes, assim como R5, R6 e
  R7. O E2C cai no dia 2, que não tem outro envio.
- **Horário:** dias úteis, das 9h às 18h, horário de Brasília. O E1 sai na hora
  do cadastro, qualquer dia.
- **Fim de semana:** e-mail de ativação (E2A a E3B) cai no sábado ou domingo e
  passa para o próximo dia útil livre. Se não houver dia livre, é descartado. E4
  segue a mesma regra. **E5 e E6 saem na data certa mesmo no fim de semana**,
  porque o prazo do trial é real e o texto cita os dias que faltam.
- **Supressão:** quem assina sai da sequência no mesmo minuto.

---

## 3. Eventos a rastrear

Os eventos precisam chegar **à ferramenta de e-mail**, não só ao GTM. Os que
existem hoje vão para o Analytics pelo navegador, e a ferramenta de e-mail não
enxerga esse caminho. O jeito mais limpo é o backend da Mobiletec (Supabase)
enviar cada evento por webhook, direto ou passando pelo n8n (lacuna 2).

| Evento | Situação | O que precisa carregar | Usado em |
|---|---|---|---|
| `form_submit_trial` | **Existe** | e-mail, nome, nome do escritório, data de início e de fim do trial | R1 |
| `signup_office_created` | **Existe** | `porte`, `processos` (declarados) | Plano indicado no E5 |
| `onboarding_step_done` | **Existe** | `step` (`lawyer`, `intimations`, `portfolio`), `skipped` | Personaliza o E2A |
| `onboarding_completed` | **Existe** | data e hora | **Ativação.** R2, R3, R5 a R7, R11 |
| `subscription_started` | Existe como `Purchase`, no servidor | plano assinado | R8 a R12 |
| `login` | **Criar** | data e hora de cada sessão | R4, R11, R13 |
| `ai_generation_created` | **Criar** | tipo (`peticao`, `outro`) | R6, R7, recap do E5 |
| `deadline_alerts_enabled` | **Criar** | · | R3 |
| `fee_created` | **Criar** | · | R7 |
| `user_invited` | **Criar** | · | R13 |
| `pricing_page_viewed` | **Criar** | · | R13 |
| `trial_expired` | **Criar**, no servidor | data e hora | R11 |

**Atributos do contato**, atualizados pelo backend: `primeiro_nome`,
`nome_escritorio`, `porte`, `processos_declarados`, `data_fim_trial`,
`dias_restantes`, `passo_parado`, `processos_importados`,
`clientes_cadastrados`, `geracoes_ia_usadas`, `plano_indicado`, `preco_plano`,
`status` (`trial`, `pagante`, `expirado`).

**Plano indicado** (premissa, lacuna 13):

| Situação do escritório | Plano |
|---|---|
| 1 usuário e até 70 processos declarados | Solo · R$ 69 |
| Até 5 usuários e até 500 processos | Plus · R$ 159 |
| Até 20 usuários ou mais de 500 processos | Max · R$ 499 |
| Acima disso | Ilimitado · R$ 1.299, com contato do time em vez de botão de assinar |

Na dúvida, o padrão é o **Plus**: é o primeiro plano com todas as
funcionalidades, as mesmas que a pessoa usou no trial. O Solo traz só o
essencial, então só entra quando o perfil é claramente individual.

---

## 4. Os e-mails

**Notação.** `{{variavel|fallback}}` mostra o fallback quando o dado falta. Todo
texto foi escrito para funcionar com o fallback. Linhas marcadas "só se > 0"
somem quando o número é zero.

**Assinatura padrão de todos:**

```
{{remetente_nome|[NOME_REMETENTE]}}
{{remetente_cargo|[CARGO]}}, JurIA
```

**UTM em todo link:** `utm_source=email` · `utm_medium=email` ·
`utm_campaign=juria-trial-7d` · `utm_content=<id do e-mail>_<variação de assunto>`.
Exemplo: `utm_content=e1_a`. O `utm_medium=email` faz o GA4 classificar o
acesso no canal E-mail sem regra nova.

**Links:** os caminhos dentro do portal (`[LINK_...]`) dependem da Mobiletec
(lacuna 11). Base: `https://portal.juria.app.br`.

---

### E1 · Boas-vindas

| Campo | Valor |
|---|---|
| Gatilho | R1 · `form_submit_trial`, na hora |
| Segmento | Todos |
| Assunto A | Comece por aqui: traga seus processos pela OAB |
| Assunto B | Seu escritório no JurIA, primeiro passo |
| Preheader | Um passo só: informe sua OAB e o JurIA traz o seu acervo. |
| Botão | **Importar meus processos** → `[LINK_ONBOARDING]?utm_...&utm_content=e1_a` |
| Cancela se | Nunca |
| Sucesso | % que chega a `onboarding_completed` em até 24h |

```
{{primeiro_nome|Olá}},

Seu teste do JurIA começou e vai até {{data_fim_trial|o fim desta semana}}.

O jeito mais rápido de avaliar o sistema é com o seu próprio acervo. Informe o
número da sua OAB e o JurIA importa seus processos automaticamente. A primeira
importação usa créditos do saldo grátis que já está na sua conta.

Prefere planilha? Também funciona, e não consome nada.

[ Importar meus processos ]

Se travar em qualquer ponto, responda este e-mail. Sou eu quem lê.
```

---

### E2A · Destravar o setup

| Campo | Valor |
|---|---|
| Gatilho | R2 · 24h após o cadastro, sem `onboarding_completed` |
| Segmento | Não ativou |
| Assunto A | Travou em {{passo_parado\|algum passo}}? Resolvo com você |
| Assunto B | Seu escritório no JurIA ficou pela metade |
| Preheader | São três passos, e dá para terminar agora ou com a minha ajuda. |
| Botão | **Continuar de onde parei** → `[LINK_ONBOARDING]` |
| Link secundário | Agendar uma conversa curta → `[LINK_AGENDA]` |
| Cancela se | `onboarding_completed` antes do envio |
| Sucesso | % que ativa em até 48h · % que agenda |

`passo_parado` vem do último `onboarding_step_done`: `lawyer` vira "cadastro da
OAB", `intimations` vira "captura de intimações", `portfolio` vira "importação
dos processos".

```
{{primeiro_nome|Olá}},

Vi que a configuração do seu escritório parou em {{passo_parado|um dos passos
iniciais}}. Acontece: às vezes um passo pede uma informação que não está à mão.

O caminho completo é curto:

1. Informe o número da sua OAB.
2. Ative a captura de intimações.
3. Importe seus processos, pela OAB ou por planilha.

[ Continuar de onde parei ]

Prefere fazer junto? Agende uma conversa curta comigo e configuramos com a sua
tela aberta. Ou responda este e-mail com a dúvida.
```

---

### E2B · Próximo passo

| Campo | Valor |
|---|---|
| Gatilho | R3 · 24h após o cadastro, com `onboarding_completed` |
| Segmento | Ativou |
| Assunto A | Seus processos chegaram. Agora, os prazos |
| Assunto B | O próximo passo é não perder prazo |
| Preheader | Alertas antes do vencimento, pelo calendário forense. |
| Botão | **Ativar alertas de prazo** → `[LINK_PRAZOS]` |
| Cancela se | `deadline_alerts_enabled` antes do envio |
| Sucesso | % que ativa os alertas em até 48h |

```
{{primeiro_nome|Olá}},

Seus processos já estão no JurIA. Bom começo.

O próximo passo é o que mais pesa na rotina de um escritório: prazo. No JurIA,
os prazos ficam no calendário forense, com alerta antes do vencimento, no mesmo
lugar em que estão os processos.

Ative os alertas e veja a agenda da semana montada.

[ Ativar alertas de prazo ]

Qualquer dúvida, é só responder.
```

---

### E2C · Sem login

| Campo | Valor |
|---|---|
| Gatilho | R4 · 48h após o cadastro, sem `login` depois da sessão do cadastro |
| Segmento | Sem login |
| Assunto A | Posso ajudar com o seu teste? |
| Assunto B | Uma pergunta rápida sobre o JurIA |
| Preheader | Uma linha de resposta já me ajuda. |
| Botão | Nenhum. O CTA é responder o e-mail |
| Cancela se | `login` antes do envio |
| Sucesso | Taxa de resposta · % que volta a logar em até 48h |

Sem conteúdo de funcionalidade, de propósito. Formato de e-mail pessoal, sem
logo nem imagem.

```
{{primeiro_nome|Olá}},

Você criou a conta no JurIA há dois dias e ainda não voltou ao sistema.

Uma pergunta só: o que ficou no caminho? Falta de tempo, alguma dúvida, ou não
era bem o que você procurava?

Responda com uma linha. Leio todas as respostas, e se for algo que eu resolva,
resolvo.
```

---

### E3X · Call de setup

| Campo | Valor |
|---|---|
| Gatilho | R5 · dia 3, sem `onboarding_completed`. Ocupa o lugar do E3 |
| Segmento | Não ativou |
| Assunto A | Quer que eu configure com você? |
| Assunto B | Uma conversa curta e o JurIA fica pronto |
| Preheader | Fazemos juntos o cadastro da OAB e a importação. |
| Botão | **Agendar a configuração** → `[LINK_AGENDA]` |
| Cancela se | `onboarding_completed` antes do envio |
| Sucesso | % que agenda · % que ativa até o dia 5 |

```
{{primeiro_nome|Olá}},

Seu escritório no JurIA ainda não está configurado, e sem os seus processos lá
dentro fica difícil avaliar o sistema de verdade.

Proponho o seguinte: uma chamada curta, com a sua tela compartilhada, em que
fazemos juntos o cadastro da OAB e a importação. Você sai com o JurIA rodando
com o seu acervo.

[ Agendar a configuração ]

Se preferir resolver por aqui, responda contando o que travou.
```

---

### E3 · IA na prática

| Campo | Valor |
|---|---|
| Gatilho | R6 · dia 3, ativou e ainda não usou a IA |
| Segmento | Ativou, sem IA |
| Assunto A | Sua próxima petição, com a IA do JurIA |
| Assunto B | Um rascunho de petição a partir do seu processo |
| Preheader | A IA prepara o rascunho. A decisão continua sendo sua. |
| Botão | **Gerar meu primeiro rascunho** → `[LINK_IA]` |
| Cancela se | `ai_generation_created` antes do envio |
| Sucesso | % que gera o primeiro rascunho em até 48h |

```
{{primeiro_nome|Olá}},

Com seus processos no sistema, dá para testar a parte que mais economiza tempo
na rotina: a IA.

Experimente assim:

1. Abra um processo do seu acervo.
2. Peça à IA o rascunho de uma petição.
3. Revise e ajuste. A IA prepara o rascunho, a decisão continua sendo sua.

A IA está inclusa no plano, dentro do limite mensal de gerações. No teste, você
tem 20 gerações para usar.

[ Gerar meu primeiro rascunho ]
```

---

### E3B · Back-office

| Campo | Valor |
|---|---|
| Gatilho | R7 · dia 3, ativou e já usou a IA |
| Segmento | Ativou, com IA |
| Assunto A | Processo, prazo e financeiro na mesma tela |
| Assunto B | Quantos sistemas o seu escritório usa hoje? |
| Preheader | A outra metade do JurIA: o back-office do escritório. |
| Botão | **Lançar um honorário** → `[LINK_FINANCEIRO]` |
| Cancela se | `fee_created` antes do envio |
| Sucesso | % que lança o primeiro honorário em até 48h |

```
{{primeiro_nome|Olá}},

Você já testou a IA. Agora vale ver a outra metade do JurIA: o back-office.

No mesmo sistema em que estão seus processos, ficam também agenda, clientes,
honorários e o financeiro do escritório. É uma ferramenta no lugar de várias.

Teste com um caso real: abra um processo e lance o honorário dele. O valor
aparece no financeiro do escritório, sem planilha à parte.

[ Lançar um honorário ]
```

---

### E4 · Quem está por trás

| Campo | Valor |
|---|---|
| Gatilho | R8 · dia 4, sem assinatura |
| Segmento | Todos sem assinatura |
| Assunto A | 25 anos de engenharia por trás do JurIA |
| Assunto B | Daqui a dois anos o JurIA ainda vai estar aqui? |
| Preheader | Quem faz o JurIA e como os dados do seu escritório são protegidos. |
| Botão | **Continuar meu teste** → `[LINK_PAINEL]` |
| Cancela se | Assinou |
| Sucesso | % de cliques que voltam ao sistema · % que assina até o dia 7 |

**Por que não é um case:** o briefing pede case real e autorizado, e o JurIA não
tem nenhum (lacuna 8). A regra do briefing para esse caso é usar resultado
verificável do produto. Este e-mail usa as duas objeções de confiança do
briefing, com fatos que a Mobiletec já confirmou. Quando houver case, ele entra
como variação B do dia 4, no teste A/B número 4.

```
{{primeiro_nome|Olá}},

Antes de colocar o acervo do escritório num sistema novo, duas perguntas são
justas: quem está por trás, e o que acontece com os dados.

Quem está por trás: o JurIA é da Mobiletec, empresa de Santa Catarina que opera
há 25 anos. Não é uma startup criada ontem.

Os dados: conformidade com a LGPD, autenticação em dois fatores, dados de cada
escritório isolados dos demais, registro de auditoria e backup diário.

[ Continuar meu teste ]
```

---

### E5 · Faltam 2 dias

| Campo | Valor |
|---|---|
| Gatilho | R9 · dia 5, sem assinatura |
| Segmento | Todos sem assinatura. Quem ativou recebe o recap completo, quem não ativou recebe só o parágrafo do plano |
| Assunto A | Seu teste do JurIA termina em 2 dias |
| Assunto B | O que você montou no JurIA até aqui |
| Preheader | Seu escritório no sistema, e o plano que serve para ele. |
| Botão | **Assinar o {{plano_indicado\|Plus}}** → `[LINK_PLANOS]` |
| Link secundário | Comparar os planos com alguém do time → `[LINK_AGENDA]` |
| Cancela se | Assinou |
| Sucesso | % que assina até o dia 7 |

```
{{primeiro_nome|Olá}},

Seu teste do JurIA termina em {{dias_restantes|2}} dias, em {{data_fim_trial}}.

Até aqui, o seu escritório já tem no sistema:

· {{processos_importados}} processos            (só se > 0)
· {{clientes_cadastrados}} clientes             (só se > 0)
· {{geracoes_ia_usadas}} rascunhos feitos pela IA (só se > 0)

Para seguir depois do teste, o plano indicado para o seu escritório é o
{{plano_indicado|Plus}}, por {{preco_plano|R$ 159}} por mês. Sem fidelidade:
você troca de plano ou cancela quando quiser, e seus dados continuam intactos.

[ Assinar o {{plano_indicado|Plus}} ]

Quer comparar os planos com alguém do time antes? Agende uma conversa.
```

---

### E6 · Último dia

| Campo | Valor |
|---|---|
| Gatilho | R10 · dia 7, sem assinatura |
| Segmento | Todos sem assinatura |
| Assunto A | Último dia do seu teste do JurIA |
| Assunto B | Hoje acaba o seu teste. Três caminhos |
| Preheader | Assinar, conversar antes ou pedir mais tempo. |
| Botão | **Assinar o {{plano_indicado\|Plus}}** → `[LINK_PLANOS]` |
| Link secundário | Conversar antes de decidir → `[LINK_AGENDA]` |
| Cancela se | Assinou |
| Sucesso | % que assina no dia · % que agenda · respostas pedindo extensão |

O terceiro caminho só entra se a Mobiletec aceitar estender o trial (lacuna 6).
Sem isso, o e-mail fica com dois caminhos e o assunto B muda para "Hoje acaba o
seu teste do JurIA".

```
{{primeiro_nome|Olá}},

Seu teste do JurIA termina hoje. Três caminhos, e qualquer um deles está bom:

1. Assinar e seguir com o que já montou. O {{plano_indicado|Plus}} sai por
   {{preco_plano|R$ 159}} por mês, sem fidelidade.

[ Assinar o {{plano_indicado|Plus}} ]

2. Conversar antes de decidir. Agende um horário com o time.

3. Precisa de mais tempo para avaliar? Responda este e-mail e vejo o que
   consigo fazer.
```

---

### E7 · Pós-trial

| Campo | Valor |
|---|---|
| Gatilho | R11 · 7 dias após `trial_expired`, sem assinatura, com engajamento |
| Segmento | Engajou e não converteu |
| Assunto A | O JurIA ainda faz sentido para o seu escritório? |
| Assunto B | Uma pergunta sobre o seu teste do JurIA |
| Preheader | Quero entender o que faltou. Uma linha basta. |
| Botão | **Ver os planos** → `[LINK_PLANOS]` |
| Cancela se | Assinou ou descadastrou |
| Sucesso | Taxa de resposta · % que assina em até 14 dias |

```
{{primeiro_nome|Olá}},

Seu teste do JurIA terminou há uma semana. Você chegou a configurar o escritório
no sistema, então imagino que algo ali chamou a sua atenção.

Se não assinou, quero entender o que faltou. Foi preço, alguma funcionalidade,
ou tempo para avaliar? Responda com uma linha.

Se foi preço: para quem advoga sozinho existe o plano Solo, por R$ 69 por mês.

[ Ver os planos ]
```

---

## 5. Métricas e testes

Nenhum número do JurIA existe ainda: a linha de base nasce nos primeiros 30 dias
de envio. As referências são de blogs de fornecedores, citados no briefing, e
servem só de ponto de partida.

| Métrica | Referência de mercado | JurIA |
|---|---|---|
| Ativação (% que chega a `onboarding_completed`) | Mediana de 38% em SaaS | A medir. O evento existe desde 28/09 |
| Tempo até a ativação | Mediana de 1 dia e 2 horas | A medir |
| Trial para pago | Mediana de 8%, trial sem cartão | A medir. O `Purchase` já chega ao servidor |
| Taxa de resposta (E2C, E3X, E7) | 5% a 10% | A medir |
| Abertura e entregabilidade | Abertura acima de 25%, entregabilidade acima de 95% | A medir |

**Testes A/B, um por vez**, porque o volume de trials é baixo (24 cadastros entre
27/08 e 15/09, pela reunião de 17/09):

1. Assunto do E1.
2. Assunto do E5.
3. CTA do E2A: continuar sozinho contra agendar conversa.
4. Dia 4: o E4 atual contra um case, quando houver.
5. Momento do aviso de fim de trial: dia 4 contra dia 5.

Com esse volume, cada teste leva semanas para ter leitura. Só passa para o
próximo quando o atual tiver pelo menos 100 envios por variação.

---

## 6. Lacunas e premissas

**Decisões para a reunião (travam a execução)**

1. **Ferramenta de e-mail.** Requisito mínimo: receber eventos e atributos por
   API ou webhook, montar automação com condição e cancelamento, e testar
   assunto A/B. Os gatilhos da seção 2 são genéricos de propósito.
2. **Caminho dos eventos até a ferramenta.** Quem envia: o backend da Mobiletec
   direto, ou por um workflow no n8n. Ligado à pendência Q28 do briefing
   (destino do lead). Os 7 eventos marcados "Criar" na seção 3 são trabalho da
   Mobiletec.
3. **Evento de ativação.** Premissa: `onboarding_completed`. Validar em 30 dias,
   comparando a conversão para pago de quem completou e de quem não completou.
4. **Remetente.** Nome, cargo e uma caixa que recebe as respostas, com alguém
   respondendo em até um dia útil.
5. **Canal humano.** Link de agendamento, quem faz a call de setup e quem recebe
   o aviso de alta intenção (R13).
6. **Extensão de trial ou desconto.** Existe? Se não, o E6 perde o terceiro
   caminho e o E7 fica só com conversa.

**A confirmar com a Mobiletec**

7. **O que acontece quando o trial expira:** acesso bloqueado ou somente
   leitura? Por quanto tempo os dados ficam guardados? Isso muda o tom do E5 ao
   E7.
8. **Cases ou beta testers** que autorizem uso de nome e resultado (pendência Q8
   do briefing).
9. **Domínio de envio** com SPF, DKIM e DMARC configurados antes do primeiro
   disparo. Sugestão: um subdomínio só para isso, como `mail.juria.app.br`, para
   não arriscar a reputação do domínio principal.
10. **Fluxos do produto citados na copy:** alerta de prazo depois da importação
    (E2B), IA gerando rascunho de petição a partir de um processo (E3),
    honorário lançado no processo aparecendo no financeiro (E3B) e o nome do
    passo `intimations` na tela (E2A).
11. **Links diretos do portal** para cada botão: onboarding, prazos, IA,
    financeiro, painel e planos.
12. **Base legal da LGPD** para e-mail de marketing a quem se cadastrou: conferir
    se o cadastro ou os termos cobrem o envio. O opt-out vai em todo e-mail, e o
    transacional (código de verificação, senha) fica separado.

**Premissas assumidas aqui**

13. **Regra do plano indicado** (seção 3). Padrão Plus quando faltar dado.
14. **O trial termina no fim do dia 7**, contando o cadastro como dia 0.
15. **Os textos não usam número de tempo** ("em 5 minutos") porque não temos
    medição de quanto o setup leva. Entra quando houver dado.

---

## Checklist do briefing

- [x] Todo e-mail tem um objetivo e um único botão (E2C e E7 têm a resposta como
      ação principal)
- [x] Nenhum e-mail passa de 150 palavras
- [x] Todo gatilho tem condição de cancelamento
- [x] Não há número, case ou funcionalidade inventados. Os fluxos a confirmar
      estão na lacuna 10
- [x] Quem ativou e quem não ativou seguem caminhos diferentes (E2A/E2B,
      E3X/E3/E3B)
- [x] Assinar encerra a sequência (R12)
- [x] Descadastro, UTM e variáveis com fallback previstos
