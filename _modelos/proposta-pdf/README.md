---
tipo: modelo
atualizado: 2026-11-04
autor: claude
---
# Modelo de proposta em PDF

O padrão de proposta da Hub3Ps desde 04/11/2026, aprovado pelo Guilherme na proposta do [[churrascodaelite-2026-11|Churrasco da Elite]]. Substitui o visual antigo das propostas da Usivic e da Liliane (laranja, serifa e ícones), que não se usa mais.

## O que tem aqui
- `proposta.html`: o modelo, com `{{...}}` em tudo o que muda e um comentário em cada seção
- `assets/`: logo preta da Hub3Ps, foto do Guilherme e a fonte Inter Tight, todos do site do Guilherme (`~/Desktop/site-guimiguelmkt/assets/`). Se o site mudar, atualize aqui

## Regras do padrão
- **Visual:** preto e branco, na linha do guimiguel.site. Sem ícones, sem cor de destaque e sem caixa colorida. O destaque é peso de fonte, linha fina e o bloco preto da coluna principal do investimento
- **Valor percebido:** a proposta mostra o que o cliente recebe, com cada entrega explicada, para o preço parecer pequeno perto do valor. **Nunca entregue diagnóstico ou melhoria de graça** (lição de 04/11/2026)
- **"Não incluso":** só o que não é óbvio
- **Seções, em ordem fixa:** capa, 01 cenário, 02 estratégia, 03 cronograma, 04 o que você recebe, 05 investimento, 06 para onde pode crescer (opcional) e 07 quem sou
- **Capa:** o nome do contato em destaque e a empresa abaixo, em fonte leve. O produto ou serviço vai no subtítulo
- **Quem sou:** fala do Guilherme, não da agência. O terceiro número ("7 dígitos com infoprodutos") pode trocar conforme o nicho do cliente
- **Moeda:** a do cliente
- **Texto:** sem travessão, frases curtas, sem jargão

## Como usar
1. Copie `proposta.html` para `05-comercial/propostas/<slug>-AAAA-MM.html`, ao lado da nota da proposta (criada a partir de [[_modelos/proposta]]). Os caminhos dos assets já funcionam de lá, porque as duas pastas ficam a dois níveis da raiz do vault
2. Troque os `{{...}}`, apague as linhas que sobrarem e repita as que faltarem. Remova a seção 06 se não houver próximos passos
3. Gere o PDF:
   ```bash
   "/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless=new --disable-gpu --no-pdf-header-footer --allow-file-access-from-files --print-to-pdf="Proposta-Hub3Ps-<Cliente>.pdf" "file://<caminho absoluto do html>"
   ```
4. Confira as páginas: nenhuma seção pode começar com um bloco solto no topo, nem sobrar página quase vazia. Para ajustar, troque `class="break"` (força página nova) ou `class="avoid"` (não quebra a seção) nas `<section>`
5. O PDF vai para o Drive, e o link vai na nota da proposta

Exemplo pronto: `05-comercial/propostas/churrascodaelite-2026-11.html`.
