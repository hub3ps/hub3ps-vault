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
