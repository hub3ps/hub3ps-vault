---
tipo: processo
atualizado: 2026-11-11
autor: claude
---
# Convenções

O que precisa ter nome igual sempre, para que arquivo, anúncio e relatório
falem a mesma língua. **Esta é a única versão.** O `docs/convencoes.md` do
`agencia_marketing` é só um ponteiro para cá.

---

## Nomes no Ads Manager

Padrão de 11/11/2026, decidido pelo Guilherme no lugar do anterior
(`marjorie-seguidores-frio-0611`, `int_cad-dental_us_ig_visita-perfil_IG-07`).
O anterior tinha uma gramática por nível e era escrito para máquina. Este tem
uma regra só para os três níveis:

- **Palavras legíveis**, com acento e inicial maiúscula, separadas por ` | `
  (espaço, barra vertical, espaço). Quem lê é você, no Ads Manager, todo dia
- **Do geral para o específico**, sempre três campos, na mesma ordem
- **Quebra em colunas** numa planilha pelo ` | `, sem ambiguidade
- **O cliente e a data não entram.** A conta já é do cliente, e o Ads Manager
  mostra quando cada item foi criado
- **Renomear não reinicia o aprendizado.** O nome é só rótulo. Os hubs e as
  rotinas leem campanha pelo id, nunca pelo nome

| Nível | Formato | Exemplo |
|---|---|---|
| Campanha | `Objetivo \| Temperatura \| Oferta ou frente` | `Agendamento \| Quente \| Aula experimental` |
| Conjunto | `Público \| Local \| Otimização` | `Engajou IG 365d e seguidores \| EUA \| Escolheu o dia` |
| Anúncio | `ID \| Formato \| Descritor` | `VID-01 \| Vídeo \| Chamada` |

### Campanha
- **Objetivo:** o que a campanha entrega para o negócio, e não o objetivo da
  Meta: `Agendamento` · `Cadastro` · `Leads` · `Vendas` · `Seguidores` ·
  `Distribuição` (conteúdo para a base) · `Reconhecimento`
- **Temperatura:** `Frio` (não conhece a marca) ou `Quente` (já conhece:
  engajou, segue, visitou, é lead ou cliente)
- **Oferta ou frente:** o que se oferece ou para onde leva: `Aula
  experimental`, `Perfil`, `Lista de espera`, `Teste grátis`
- Duas campanhas com o mesmo nome: a segunda ganha um quarto campo, `v2`

### Conjunto
- **Público:** o nome do público, como na seção abaixo
- **Local:** `EUA`, `MA`, `SC`, `9 estados`, `Cidades atendidas`
- **Otimização:** o resultado que a campanha otimiza, pelo que ele é:
  `Escolheu o dia`, `Visita ao perfil`, `ThruPlay`, `Conta criada`, `Lead`
- Posicionamento só entra quando não é automático, como quarto campo:
  `Só Instagram`, `Feed e Stories`
- Um conjunto por criativo, para garantir a entrega de cada um no teste: o ID
  do anúncio entra como quarto campo, `Interesse CAD dental | EUA | Visita ao perfil | IG-07`

### Anúncio
- **ID:** o mesmo do arquivo do criativo, que amarra arte, anúncio e relatório.
  Post impulsionado do Instagram é `IG-<NN>`, com o número do post na lista de
  posts do cliente no vault (a ficha da campanha diz qual post é cada número).
  Vídeo próprio é `VID-<NN>`. No JurIA, segue o ID da biblioteca
  (`INST-C-01`, `TRAB-A-01`)
- **Formato:** `Estático` · `Vídeo` · `Carrossel` · `Reels`
- **Descritor:** uma a três palavras sobre o eixo da peça
- **A proporção não entra no nome.** Os três cortes (4:5, 9:16, 1.91:1) vivem
  dentro do mesmo anúncio
- **O mesmo criativo em dois conjuntos usa o mesmo nome.** O que distingue é a
  coluna de conjunto no relatório

## Público

O público salvo e o personalizado, na conta, têm o mesmo nome que vai no
conjunto.

| Tipo | Como escrever | Exemplo |
|---|---|---|
| Personalizado | o que a pessoa fez, a fonte e a janela | `Engajou IG 365d` · `Seguidores IG` · `Visitou site 30d` · `Viu vídeo 75% 90d` · `Compradores curso antigo` |
| Semelhante | `Semelhante <N>%` e o público de origem | `Semelhante 1% compradores curso antigo` |
| Interesse | `Interesse` e o tema | `Interesse CAD dental` |
| Aberto | `Aberto` e a faixa de idade | `Aberto 18-55` |

- Dois públicos somados: com `e`, `Engajou IG 365d e seguidores`
- A exclusão só entra no nome quando é o que define o público:
  `Aberto 18-55 sem seguidores`. Nos outros casos, fica na ficha da campanha

## UTM

```
utm_source=meta · utm_medium=paid
utm_campaign=<nome da campanha em slug>   ← agendamento-quente-aula-experimental
utm_content=<ID do anúncio>               ← vid-01
utm_term=<público do conjunto em slug>    ← engajou-ig-365d-e-seguidores
```

- **Slug:** minúsculo, sem acento, `-` no lugar de espaço e de ` | `
- UTM já publicada não se troca: o histórico do relatório depende dela
- Gerador pronto: `juria.hub3ps.com/utm-generator.html`

## Ficha da campanha

Uma nota por campanha em `04-clientes/<slug>/campanhas/`, com o nome no Meta,
os IDs numéricos, a configuração e o histórico de otimizações. É o único lugar
onde os IDs ficam registrados. O arquivo leva o slug do nome:
`agendamento-quente-aula-experimental.md`.

## Evento e conversão personalizada

- **Evento padrão da Meta sempre que existir um que descreva a ação:** `Lead`,
  `CompleteRegistration`, `Schedule`, `Purchase`, `ViewContent`. Ele traz
  otimização e relatório prontos, e o personalizado não
- **Evento personalizado** (dataLayer, GA4, Pixel): em inglês, minúsculo, com
  `_`, descrevendo a ação: `form_submit_trial`, `onboarding_completed`. Os que
  já existem ficam com o nome que têm
- **Conversão personalizada:** `<evento>_<filtro>`, como `lead_lp-trial` ou
  `schedule_calendly`. As que já existem não se renomeiam: no DS Muay Thai, a
  regra da conversão nem se edita
- **Todo evento tem uma linha no dicionário de tracking do cliente**: o que
  dispara, em que passo do funil, e o nome na Meta, no GA4 e no hub
- **No relatório, o evento se chama pelo que ele é**, e nunca pelo rótulo
  genérico da Meta. No JurIA, o `Lead` é a conta criada, antes do onboarding,
  e chamá-lo de "cadastro concluído" fez o hub dizer outra coisa (corrigido em
  05/11/2026)

## Criativo (arquivo)

```
<ID>_<descritor>_v<N>.<ext>
```

Exemplo: `TRAB-C-01_trab_sistemas_v1_4x5.jpg`. O `ID` é o mesmo do anúncio.

- `ID` no JurIA = `<NICHO>-<LINHA>-<NN>`. Linha: `A` tech, `B` sóbrio, `C`
  funcionalidades, `NAT` native/stealth, `VID` vídeo
- Sufixo de corte só quando há mais de um: `_4x5`, `_9x16`, `_191x1`

## Referência da biblioteca

```
[nicho]_[ratio]_[tipovisual]_[angulo]_[hook]_[id].json
```

Tags compostas sem hífen (`dashboardui`, `medoperda`, `provasocial`).
Vocabulário completo e `id` sequencial por nicho: `references/creatives/json/README.md`
do `agencia_marketing`.

## Cliente

Slug em minúsculo, sem acento, sem espaço: `juria`, `apex`, `usivic`. É o mesmo
que vai em `cliente=<slug>` ao chamar as skills.

## Data em nome de arquivo

`AAAA-MM-DD`. Ordena sozinho.

## Commit

```
<tipo>(<escopo>): <o que mudou, em minúsculo, sem ponto final>
```

Tipos em uso: `feat` · `fix` · `docs` · `chore` · `refactor` · `style`.
Escopo: o slug do cliente (`juria`), `skills`, `references`, `hub`, `clients`.

- Assunto no presente, descrevendo o efeito, não o arquivo
- Corpo explica **por quê**, quando não for óbvio
- Sem acento nos assuntos de commit (o histórico já é assim)

## Credenciais

Nunca versionadas. Cofre da agência em `credenciais.local.md`, na raiz do
`agencia_marketing`, e cofre por cliente em `clients/<slug>/credenciais.local.md`.
Nada de lá sai do arquivo: não vai para chat, commit, print ou doc.

## Escrita

- Sem travessão, em lugar nenhum
- Número com unidade: `R$ 27,00/dia`, `1080×1350`, `14 dias`
- Data curta no corpo do texto: `31/08/2026`
