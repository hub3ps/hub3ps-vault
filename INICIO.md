---
tipo: painel
---
# Hub3Ps · Início

Requer o plugin Dataview.

## Clientes
```dataview
TABLE status, servicos AS "Serviços", proxima-reuniao AS "Próxima reunião", atualizado
FROM "04-clientes"
WHERE tipo = "cliente"
SORT status ASC
```

## Em implantação
Clientes nas fases 2 a 4 da [[03-processos/novo-cliente|entrada de cliente]].
```dataview
TABLE servicos AS "Serviços", inicio AS "Início", row["proxima-reuniao"] AS "Próxima reunião", atualizado
FROM "04-clientes"
WHERE tipo = "cliente" AND status = "implantacao"
SORT inicio ASC
```

## Sem meta ou sem próxima reunião
Cliente que pulou o critério de saída do Fechamento ou da passagem para a gestão.
```dataview
TABLE status, meta, row["proxima-reuniao"] AS "Próxima reunião"
FROM "04-clientes"
WHERE tipo = "cliente" AND status != "encerrado" AND (!meta OR contains(string(meta), "TODO") OR !row["proxima-reuniao"] OR contains(string(row["proxima-reuniao"]), "TODO"))
SORT file.folder ASC
```

## Pendências abertas em todos os clientes
```dataview
TASK
FROM "04-clientes"
WHERE !completed
GROUP BY file.folder
```

## Pipeline comercial
```dataview
TABLE etapa, valor, proximo-passo AS "Próximo passo"
FROM "05-comercial/propostas"
WHERE tipo = "proposta"
```
