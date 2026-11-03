---
tipo: processo
migrado-de: docs/convencoes.md
---
# Convenções

O que precisa ter nome igual sempre, para que arquivo, anúncio e relatório
falem a mesma língua.

---

## Campanha

```
<cliente>-<objetivo>-<recorte>-<DDMM>
```

Exemplos reais: `juria-leads-sul-2606`, `juria-leads-br-2708`.

- `recorte` é geografia ou nicho, o que definir a campanha
- `DDMM` é a data de criação, não a de veiculação
- O mesmo string vai no `utm_campaign` **e** no nome da campanha no Ads Manager

A **ficha** da campanha (`clients/<slug>/campanhas/`) usa um slug curto
derivado do recorte: `br-institucional-2708.md`. É o único lugar onde os IDs
numéricos do Meta ficam registrados.

## Criativo

```
<ID>_<utm_content>.<ext>
```

Exemplo: `TRAB-C-01_trab_sistemas_v1_4x5.jpg`

O nome do arquivo **casa com o `utm_content`** do anúncio. É isso que permite
cruzar peça e resultado no painel sem planilha de-para.

- `ID` = `<NICHO>-<LINHA>-<NN>`. Linha: `A` tech, `B` sóbrio, `C`
  funcionalidades, `NAT` native/stealth, `VID` vídeo.
- Sufixo de corte só quando há mais de um: `_4x5`, `_9x16`, `_191x1`.

## Anúncio no Ads Manager

```
<ID>-<Formato>-<Descritor>
```

Exemplos: `INST-C-01-Estático-Um-Sistema` · `INST-VID-01-Vídeo-Consolidação-Motion`
· `TRAB-A-01-Estático-Tech-modern`

- **`ID`**: o mesmo do arquivo do criativo. É o que amarra arte, anúncio e relatório
- **`Formato`**: `Estático` · `Vídeo` · `Carrossel`
- **`Descritor`**: uma a três palavras sobre o eixo, com inicial maiúscula e hífen

**A proporção não entra no nome.** O Ads Manager aceita um asset por *grupo* de
posicionamento, então os três cortes (4:5, 9:16, 1.91:1) vivem dentro do **mesmo
anúncio**. Um anúncio por criativo, não um por corte.

**O mesmo criativo em dois conjuntos usa o mesmo nome.** É proposital: o que
distingue é a coluna de conjunto no relatório, e o nome repetido é o que permite
comparar a mesma peça entre públicos.

> ⚠️ Há legado fora do padrão na conta do JurIA: `TRAB-C-01` e `TRAB-NAT-C`
> entraram só com o ID, sem formato nem descritor. Renomear reinicia nada, é só
> rótulo, mas fica para quando alguém estiver no Ads Manager de qualquer jeito.

## UTM

```
utm_source=meta · utm_medium=paid
utm_campaign=<slug da campanha>
utm_content=<peça>          ← casa com o nome do arquivo
utm_term=<público>          ← ex.: trabalhista_aberto, trabalhista_interesses
```

Gerador pronto: `juria.hub3ps.com/utm-generator.html`.

Ao duplicar um conjunto para testar outro público, troque **só** o `utm_term`.

## Referência da biblioteca

```
[nicho]_[ratio]_[tipovisual]_[angulo]_[hook]_[id].json
```

Tags compostas sem hífen (`dashboardui`, `medoperda`, `provasocial`). Vocabulário
completo e `id` sequencial por nicho: `references/creatives/json/README.md`.

## Cliente

Slug em minúsculo, sem acento, sem espaço: `juria`, `apex`, `usivic`. É o mesmo
que vai em `cliente=<slug>` ao chamar as skills.

## Data em nome de arquivo

`YYYY-MM-DD`. Ordena sozinho. Vale para as saídas de copy e criativo
(`copies/<campanha>/2026-09-01.md`).

## Commit

```
<tipo>(<escopo>): <o que mudou, em minúsculo, sem ponto final>
```

Tipos em uso: `feat` · `fix` · `docs` · `chore` · `refactor` · `style`.
Escopo: o slug do cliente (`juria`), `skills`, `references`, `hub`, `clients`.

- Assunto no imperativo ou no presente, descrevendo o efeito, não o arquivo:
  `atualiza o hub ate 30/08`, não `mexe no dados-campanha.json`.
- Corpo explica **por quê**, quando não for óbvio.
- **Sem travessão** em nenhum texto do repositório: commit, doc, copy ou
  criativo. Use vírgula, dois-pontos ou ponto.
- Sem acento nos assuntos de commit (o histórico já é assim).

## Credenciais

Nunca versionadas. Cofre da agência em `credenciais.local.md` na raiz, cofre por
cliente em `clients/<slug>/credenciais.local.md`. Sistema completo, regras de
higiene e o que fazer se vazar: [`credenciais.md`](credenciais.md).

## Escrita

- Sem travessão, em lugar nenhum.
- Número com unidade: `R$ 27,00/dia`, `1080×1350`, `14 dias`.
- Data por extenso curto no corpo do texto: `31/08/2026`.
