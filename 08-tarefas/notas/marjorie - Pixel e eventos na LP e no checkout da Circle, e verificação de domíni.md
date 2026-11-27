---
title: "Pixel e eventos na LP e no checkout da Circle, e verificação de domínio na BM"
status: a-fazer
cliente: marjorie
tags:
  - task
  - tracking
dateCreated: 2026-11-18T00:00:00.000-03:00
id: f89fd891-4ff9-4b3a-a358-f0a7076408e9
---

- 26/11: a página tem o Pixel `1775314010396135` e só dispara `PageView`. O clique nos botões da Circle só gera o `SubscribedButtonClick` automático. Decisão do Guilherme: por agora, rastrear o clique no checkout. Falta a Julia pôr `InitiateCheckout` no clique dos dois botões (texto para ela aguarda o ok do Guilherme) e o teste no mesmo dia. Pixel dentro do checkout da Circle segue em aberto.
- 26/11: em vez do código, regras de clique `InitiateCheckout` criadas e ativas pelo MCP: `1445278821096545` (botão trimestral) e `1819486695987515` (botão anual), por texto do botão. Dependem do texto atual dos botões.
- 26/11: testado na página, os dois botões disparam `InitiateCheckout`. Falta o Pixel dentro do checkout da Circle e a verificação de domínio.
