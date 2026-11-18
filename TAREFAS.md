---
tipo: painel
atualizado: 2026-11-18
autor: claude
---
# Tarefas de todos os clientes

Uma tela só com os cartões abertos dos kanbans de `04-clientes/`. Ela não guarda
tarefa nenhuma: lê os kanbans. Marcar o checkbox aqui conclui o cartão no
kanban do cliente. Para criar, editar ou mudar de coluna, clique no nome do
cliente e use o quadro dele. O padrão de prazo (`@{AAAA-MM-DD}`) e de `#gui`
está em [[03-processos/convencoes#Tarefa no kanban|convenções]].

Requer o plugin Dataview.

## Atrasadas
```dataview
TASK
FROM "04-clientes"
WHERE !completed AND meta(section).subpath != "Aguardando cliente"
FLATTEN date(regexreplace(text, "^.*@[{]([0-9-]+)[}].*$", "$1")) AS prazo
WHERE prazo AND prazo < date(today)
SORT prazo ASC
GROUP BY link(file.path, regexreplace(file.folder, "^04-clientes/", "")) AS cliente
```

## Hoje
```dataview
TASK
FROM "04-clientes"
WHERE !completed AND meta(section).subpath != "Aguardando cliente"
FLATTEN date(regexreplace(text, "^.*@[{]([0-9-]+)[}].*$", "$1")) AS prazo
WHERE prazo AND prazo = date(today)
GROUP BY link(file.path, regexreplace(file.folder, "^04-clientes/", "")) AS cliente
```

## Até o fim da semana
```dataview
TASK
FROM "04-clientes"
WHERE !completed AND meta(section).subpath != "Aguardando cliente"
FLATTEN date(regexreplace(text, "^.*@[{]([0-9-]+)[}].*$", "$1")) AS prazo
WHERE prazo AND prazo > date(today) AND prazo <= date(eow)
SORT prazo ASC
GROUP BY link(file.path, regexreplace(file.folder, "^04-clientes/", "")) AS cliente
```

## Próximas semanas
```dataview
TASK
FROM "04-clientes"
WHERE !completed AND meta(section).subpath != "Aguardando cliente"
FLATTEN date(regexreplace(text, "^.*@[{]([0-9-]+)[}].*$", "$1")) AS prazo
WHERE prazo AND prazo > date(eow)
SORT prazo ASC
GROUP BY link(file.path, regexreplace(file.folder, "^04-clientes/", "")) AS cliente
```

## Minhas, sem prazo
Cartões com `#gui` sem data: decisões e tarefas que esperam um horário seu.
```dataview
TASK
FROM "04-clientes"
WHERE !completed AND meta(section).subpath != "Aguardando cliente" AND contains(text, "#gui") AND !regexmatch("^.*@[{][0-9-]+[}].*$", text)
GROUP BY link(file.path, regexreplace(file.folder, "^04-clientes/", "")) AS cliente
```

## Cobrar dos clientes
O que está em "Aguardando cliente". Com data, é o dia que o cliente prometeu.
```dataview
TASK
FROM "04-clientes"
WHERE !completed AND meta(section).subpath = "Aguardando cliente"
GROUP BY link(file.path, regexreplace(file.folder, "^04-clientes/", "")) AS cliente
```

## Do Claude, sem prazo
O resto do backlog, sem `#gui` e sem data.
```dataview
TASK
FROM "04-clientes"
WHERE !completed AND meta(section).subpath != "Aguardando cliente" AND !contains(text, "#gui") AND !regexmatch("^.*@[{][0-9-]+[}].*$", text)
GROUP BY link(file.path, regexreplace(file.folder, "^04-clientes/", "")) AS cliente
```
