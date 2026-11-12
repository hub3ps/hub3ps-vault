---
tipo: sistema
atualizado: 2026-11-12
autor: claude
---
# Grupos de WhatsApp por cliente

A rotina [[03-processos/whatsapp-diario|WhatsApp diário]] só lê os grupos desta tabela. Qualquer outra conversa do número da agência fica de fora.

Para incluir um cliente: o Guilherme adiciona o número da agência ao grupo, e uma linha nova entra aqui com o slug, o nome do grupo e o ID. O ID aparece em `~/ferramentas/whatsapp-mcp/whatsapp-bridge/store/messages.db`, na tabela `chats`, e termina em `@g.us`.

| slug | grupo | jid | desde |
|---|---|---|---|
| marjorie | CURSO EXOCAD 🚀🇧🇷 | 120363265429433143@g.us | 2026-11-06 |
| churrascodaelite | Churrasco da Elite - Tráfego | 120363432140543418@g.us | 2026-11-10 |

A coluna `desde` é de onde a primeira leitura começa. Depois disso, a rotina guarda sozinha até onde já leu.
