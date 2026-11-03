---
tipo: comercial
---
# Pipeline

Uma nota por proposta em `propostas/`, criada a partir de [[_modelos/proposta]].
A tabela abaixo se monta sozinha.

```dataview
TABLE cliente, etapa, valor, enviada-em AS "Enviada", proximo-passo AS "Próximo passo"
FROM "05-comercial/propostas"
WHERE tipo = "proposta"
SORT enviada-em DESC
```
