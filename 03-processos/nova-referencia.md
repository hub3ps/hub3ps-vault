---
tipo: processo
atualizado: 2026-11-27
autor: claude
origem: agencia_marketing/docs/processos/nova-referencia.md (migrado em 27/11/2026)
---
# Adicionar referência à biblioteca

> Caminhos de arquivo e comandos são do repo `agencia_marketing` (`~/Desktop/agencia_marketing`), salvo quando outro repo é citado.

A biblioteca é compartilhada entre todos os clientes:
`references/creatives/json/<ratio>/`. Uma árvore só, organizada por ratio.

> ⚠️ A biblioteca vai ser **refeita do zero**. Até lá, adicione o que for
> claramente bom e não invista em curadoria do acervo herdado.

## Caminho normal

Anexe a imagem (ou várias) no chat e chame:

```
/skill ref-ingest
```

A skill analisa layout, paleta, tipografia, mockups e gatilhos, infere as 5 tags
do nome, mostra um resumo com a justificativa de cada uma e **espera sua
confirmação** antes de salvar. Aceita uma imagem ou um lote na mesma mensagem.

Confira no resumo, antes de aprovar:

- **nicho**: a 1ª tag. É por ela que a busca filtra; errar aqui esconde a ref
- **ratio**: define a pasta de destino
- **ângulo** e **hook**: é o que casa a ref com o conceito na hora de escolher

## Caminho manual (fallback)

1. Salve o JSON em `references/creatives/json/<ratio>/`
2. Nomeie como `[nicho]_[ratio]_[tipovisual]_[angulo]_[hook]_[id].json`,
   com as tags compostas sem hífen (`dashboardui`, `medoperda`, `provasocial`)
3. O `id` é sequencial **por nicho**, não por pasta:
   ```bash
   ls references/creatives/json/*/<nicho>_*.json | wc -l   # + 1, com 3 dígitos
   ```
4. Commite. A próxima execução das skills já encontra.

## Onde o acervo está fraco

`ls references/creatives/json/9x16/` mostra o buraco: 2 refs. Pool raso demais
para pedir 6 conceitos distintos. `odonto`, `food`, `varejo` e `servico-local`
estão zerados. Vocabulário completo de tags:
`references/creatives/json/README.md`.
