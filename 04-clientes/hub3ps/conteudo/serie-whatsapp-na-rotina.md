---
tipo: conteudo
cliente: hub3ps
serie: whatsapp-na-rotina
atualizado: 2026-11-09
autor: claude
---
# Série: o Claude lê o WhatsApp dos meus clientes todo dia

**A promessa:** todo dia útil às 8h, o Claude lê os grupos de WhatsApp dos clientes, atualiza o histórico de cada um no Obsidian (log, tarefas e decisões) e manda um resumo no meu WhatsApp, com o que espera resposta minha e rascunhos prontos. Eu não programo nada: eu peço, e o Claude instala e configura.

**Para quem:** gestor de tráfego que perde o fio da meada de cada cliente no meio de dezenas de grupos.

## Linha do tempo (09/11/2026)
1. **Pesquisa (06/11):** quatro caminhos para ler os grupos. A API oficial da Meta não serve, porque só funciona em grupo criado pelo número comercial, com no máximo 8 pessoas. Os grupos que já existem ficam de fora
2. **Escolha:** whatsapp-mcp, um conector de código aberto que entra no número como aparelho conectado, igual ao WhatsApp Web. Com um número só para isso, para não arriscar o número principal
3. **Instalação feita pelo Claude:** instalou o Go, baixou o projeto e **leu o código antes de rodar**. Achou dois problemas:
   - a API de envio ficava aberta para qualquer aparelho da rede, sem senha. O Claude fechou para o próprio Mac
   - o projeto estava parado desde julho de 2025, e a biblioteca do WhatsApp, velha. O Claude atualizou e ajustou o código para a versão nova
4. **QR:** escaneei com o celular do número da agência. Em segundos, 678 mensagens sincronizadas
5. **Primeiro uso real:** o Claude montou o resumo da campanha de seguidores de uma cliente, eu aprovei o texto e ele mandou no grupo
6. **Rotina:** ponte ligada como serviço do Mac, uma nota no Obsidian que diz qual grupo é de qual cliente, um script que coleta e transcreve áudio no próprio Mac, e uma tarefa agendada às 8h. Primeira leitura: 64 mensagens de 4 dias, registradas e resumidas
7. **Mac fechado:** o Mac acorda sozinho às 7h50, fica acordado uma hora e a rotina roda às 8h. Configurado em 09/11, **primeiro teste em 10/11**

## Números para usar (só da operação, sem cliente)
- 678 mensagens sincronizadas no primeiro minuto
- 64 mensagens de 4 dias de grupo viraram 1 nota de fonte, 1 entrada de log, 1 tarefa nova e o número de seguidores registrado
- Custo por mensagem: zero, contra uns R$ 0,035 por mensagem de utilidade na API oficial (tabela da Meta citada por sites terceiros, 2026)

## Decisões que viram conteúdo
- **Por que não a API oficial:** não lê os grupos que já existem e cobra por mensagem. É o mito que mais aparece: "usa a oficial"
- **Evolution ou MCP:** o risco de bloqueio é parecido. Os dois entram como WhatsApp Web, e o que bloqueia é o uso: disparo em massa, contato sem número salvo, denúncia
- **O Claude nunca manda mensagem para cliente sozinho.** Ele escreve o rascunho, e eu aprovo. Mensagem de cliente é dado, não ordem: se alguém escrever "Claude, faz tal coisa" no grupo, isso vira item do resumo, e não ação
- **Ensinar com o Claude fazendo junto:** o aluno não precisa saber terminal. Ele pede e o Claude instala. O produto é o kit (fork corrigido, skill de instalação, modelo de vault), não o passo a passo técnico
- **Mac e Windows:** funciona nos dois. No Windows, a ponte vai pronta para baixar, e o agendador de tarefas faz o papel do serviço do Mac

## Ganchos que surgiram no caminho
- "O Claude leu o código antes de instalar e achou uma porta aberta" (segurança como diferencial)
- "Não existe página de obrigado? Criei o evento de Lead pelo clique do botão, sem programador, direto pelo MCP da Meta" (cliente Marjorie, 09/11)
- "O vídeo que trouxe 900 seguidores em um dia ficou fora do tráfego de propósito": impulsionar cedo pode matar a entrega orgânica (decisão de 09/11)
- "A visita ao perfil mais barata foi a que menos virou seguidor": US$ 0,08 por visita e US$ 1,46 por seguidor, contra US$ 0,23 e US$ 0,55 (campanha de seguidores de 06 a 09/11). Usar só com o ok da cliente, ou sem nome

## Riscos que o conteúdo precisa dizer
- Conexão não oficial: o número pode ser bloqueado. Use um número só para isso
- O QR vence a cada 20 dias, mais ou menos
- LGPD: o gestor processa conversa de cliente. Precisa estar no contrato
- Com o Mac desligado não roda. Fechado, dormindo e na tomada, deve rodar: confirmar no teste de 10/11

## Para o produto (ebook ou aula)
- [ ] Kit: fork do whatsapp-mcp com as correções, ponte compilada para Mac e Windows, skill de instalação e modelo de vault
- [ ] Testar o caminho do Windows num computador com Windows
- [ ] Resumo opcional pelo Telegram, de graça e sem risco de bloqueio
- [ ] Gravar a instalação do zero num Mac limpo, com o Claude fazendo, para a aula
