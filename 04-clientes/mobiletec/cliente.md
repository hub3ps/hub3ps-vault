---
tipo: cliente
slug: mobiletec
nome: Mobiletec
empresa: Mobiletec Sistemas Ltda
status: ativo
servicos: [lp-e-site, criativos-e-audiovisual]
inicio: 2026-10-19
contrato: TODO
vigencia: TODO
valor-mensal: TODO
meta: TODO
contatos: Everton (respondeu o briefing do vídeo)
drive: TODO (Hub3Ps/Clientes/mobiletec/)
painel:
repositorios: [hub3ps/agencia_marketing]
proxima-reuniao: TODO
atualizado: 2026-11-04
autor: claude
---
# Mobiletec

> **Estado atual:** o site institucional novo está no ar em `site.mobiletec.hub3ps.com` desde 20/10/2026, com `noindex`, mas sem domínio definitivo e com vários blocos esperando dados da Mobiletec. A sexta versão do vídeo institucional foi entregue em 27/10, e não há registro de aprovação. Todo o trabalho está fora da main, na branch `claude/loving-archimedes-rp33cv`.

É a mesma empresa do [[04-clientes/juria/cliente|JurIA]], mas aqui o assunto é a marca Mobiletec, não o produto. A divisão em dois clientes foi decisão do Guilherme em 04/11/2026.

## Quem é
- **Negócio:** software house de Itajaí/SC que desenvolve aplicações móveis, web e desktop e mantém sistemas em produção. Tem o JurIA como produto próprio. Flowee, Hub de Certificação, VendeAI e RoterizAI parecem produtos da casa, mas ninguém da Mobiletec confirmou: a pergunta está no doc do site de 04/11. Só a Bello foi chamada de projeto de cliente (Everton, 22/10).
- **Público:** quem contrata software para operação crítica, como empresas de grande porte (com foco na indústria de alimentos) e órgãos públicos.
- **Região:** Itajaí/SC, com clientes pelo Brasil.
- **Idioma:** português do Brasil.
- **Clientes citáveis:** 13 empresas, sob o rótulo exato "Empresas que rodam sistemas da Mobiletec": JBS, Copacol, Grupo Pluma, Minerva Foods, Barra Mansa, Vibra Foods, Better Beef, Lar, MBRF, Seara, Grupo BTZ, Coopavel e Plena (liberadas pelo Guilherme em 06/10/2026; a Vibra Energia foi trocada por Vibra Foods em 27 e 30/10).

## Escopo
TODO: confirmar se há contrato ou proposta separada do JurIA e como estes trabalhos são cobrados.

- [[lp-e-site]]: site institucional em Astro, aberto em 19/10/2026
- [[criativos-e-audiovisual]]: vídeo institucional em motion, pedido em 21/10/2026, para passar em loop num evento

## Exceções ao padrão

| Serviço | Exceção | Motivo | Desde |
|---|---|---|---|
| LP e site | Fica em `noindex` (meta, `robots.txt` e cabeçalho) até o lançamento | O endereço é provisório | 19/10/2026 |
| LP e site | A direção visual é utilitária, de grade e quase monocromática, sem o brilho do JurIA | A Mobiletec é a casa de engenharia, não um SaaS. O objetivo é transmitir seriedade e autoridade | 19/10/2026 |
| LP e site | A paleta foi lida da logo, porque não existe código oficial de cor | A identidade oficial não chegou | 19/10/2026 |
| LP e site | O rótulo dos clientes nunca muda. A conferência do site derruba a rodada se ele sumir | Texto aprovado | 06/10/2026 |
| criativos | O vídeo é em Remotion, com locução masculina de IA, e a música é escolhida por nós | Pedido da Mobiletec e decisão do Guilherme | 21/10/2026 |
| criativos | Números, slogan e o JurIA não entram no vídeo | Respostas da Mobiletec | 22/10/2026 |

## Depende do cliente
O que travou o site e o vídeo, conforme o brief e o vídeo na branch (19 a 27/10/2026):

- [ ] Logo em SVG, nas versões clara e escura, e as cores oficiais
- [ ] Domínio definitivo do site
- [ ] Conteúdo das 4 páginas de projeto: JBS, Copacol, Grupo Pluma e Minerva Foods
- [ ] Números de operação: usuários, volume, disponibilidade e tamanho do time
- [ ] Órgãos públicos que podem ser citados, com logo
- [ ] WhatsApp comercial
- [ ] Fotos reais do time ou do escritório, se quiserem usar
- [ ] Páginas além da home: Sobre, Soluções, Carreiras e Contato
- [x] Ano de fundação: 1999 (Guilherme, 04/11/2026). Falta trocar no site, que ainda diz 2000
- [ ] Aprovação da sexta versão do vídeo (TODO: conferir se já veio)

## Acessos
Nunca guarde senha aqui.

- **Vercel:** projeto `site-mobiletec` (time hub3psmarketing), com Root Directory `mobiletec-site-astro`. A produção acompanha a branch `claude/loving-archimedes-rp33cv`
- **Domínio:** `site.mobiletec.hub3ps.com`, com CNAME na Cloudflare. O site antigo segue em `mobiletec.com.br`
- **Instagram:** `@mobiletec.sistemas`
- **Materiais da Mobiletec:** os zips "Design Kits - Mobiletec" e "AFV", com logos, telas e cores dos 5 produtos. Hoje estão no Downloads do Mac e vão para o Drive

## Onde está cada coisa
Tudo está na branch `claude/loving-archimedes-rp33cv` do `agencia_marketing`. Nada disso está na main.

| Preciso de | Está em |
|---|---|
| Brief e o que falta perguntar | `clients/mobiletec/brief.md` |
| Direção visual e paleta | `clients/mobiletec/brand.md` |
| Onde o site parou | `clients/mobiletec/ESTADO-site-astro.md` |
| Código do site | `mobiletec-site-astro/` |
| Vídeo: briefing, respostas e entregas | `clients/mobiletec/video/README.md` e `video/entregas/` |
| Projeto Remotion do vídeo | `clients/mobiletec/video/_video/` |
| Briefing do vídeo respondido | Google Docs no Drive do Guilherme: "Vídeo institucional Mobiletec - Briefing para confirmar" |

## Links
- Kanban: [[04-clientes/mobiletec/kanban|kanban]]
- Log: [[04-clientes/mobiletec/log|log]]
- Reuniões: `reunioes/`
- Fontes: `fontes/`
- Drive: TODO
- Site: https://site.mobiletec.hub3ps.com
