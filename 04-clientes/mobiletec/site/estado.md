---
tipo: cliente-doc
cliente: mobiletec
atualizado: 2026-11-27
autor: claude
origem: agencia_marketing, branch claude/loving-archimedes-rp33cv, clients/mobiletec/ESTADO-site-astro.md (migrado em 27/11/2026)
---
# Estado da execução · site Mobiletec em Astro

> **LEIA ISTO PRIMEIRO** se o pedido foi continuar o site da Mobiletec.
> Se o log não bate com o disco, confie no disco.

## Como retomar

1. Ler [[04-clientes/mobiletec/brief|brief.md]] e [[04-clientes/mobiletec/marca|brand.md]]
2. Ler [[04-clientes/mobiletec/site/plano-execucao|PLANO-execucao-site-astro.md]]
3. `cd mobiletec-site-astro && npm ci`
4. Continuar da primeira fase não concluída no log
5. **Atualizar este arquivo ao fim de cada rodada**, no mesmo commit

## Regras que não mudam

- **Sem inventar:** depoimento, case, cliente, número de uso, telefone, e-mail.
  Faltou dado, `{{ TODO }}` visível e seguir
- **O rótulo dos clientes é o aprovado:** "Empresas que rodam sistemas da
  Mobiletec". São clientes da Mobiletec, não do JurIA
- Sem travessão em nenhum texto
- Deploy só no projeto Vercel `site-mobiletec`, liberado pelo Guilherme em
  19/10/2026. Nenhum outro projeto Vercel é tocado. O `vercel.json` existe só
  para o `noindex` do endereço de demonstração, e sai no lançamento
- O site do JurIA (`juria-site-astro/`, `juria-lps`) não é tocado por este trabalho

## Como o código está montado

| Onde | O quê |
|---|---|
| `src/data/site.ts` | Fatos da empresa. Campo nulo = dado pendente |
| `src/data/home.ts` | Copy da home, bloco a bloco, com a fonte de cada afirmação |
| `src/components/sections/` | Um arquivo por bloco: Hero, Numeros, LinhaDoTempo, Clientes, Servicos, Juria, Contato |
| `src/styles/tokens.css` | Paleta e fontes. **Provisória**, troca aqui quando a identidade chegar |
| `src/scripts/movimento.ts` | Lenis + GSAP. Tudo é opcional para o conteúdo |
| `src/scripts/cena-hero.ts` | three.js do hero, carregado sob demanda |
| `scripts/conferir-paginas.mjs` | Conferência do `dist/` |

### Quatro coisas que quebram em silêncio

**O estado escondido só existe sob `.mov`.** O script inline do `<head>` põe
`mov` no `<html>` só sem `prefers-reduced-motion`. Esconder conteúdo fora de
`.mov` deixa a página em branco para quem pede menos movimento ou está sem JS.

**GSAP lê o transform do CSS.** O CSS inicial das linhas é
`translateY(105%)`; animar só `yPercent` soma com esse `y` lido e a linha nunca
aparece. Por isso o `fromTo` leva `y: 0` dos dois lados. Achado na primeira
captura, com o H1 invisível.

**Máscara de SVG com região explícita.** A região padrão de `<mask>` em
`userSpaceOnUse` vai de -10% a 120% medida da origem do sistema, não do
`viewBox`. O símbolo começa em y=196 e passava do fim: a parte de baixo sumia
durante o desenho. `LogoSimbolo.astro` passa `x`, `y`, `width` e `height`.

**Um relógio só.** O Lenis roda no `gsap.ticker`, não no próprio
`requestAnimationFrame`. Dois relógios fazem a animação tremer contra a rolagem.

## Antes de fechar uma rodada

```
npm run conferir        # astro check + build + paginas:conferir
```

E capturas a 390 e 1440px, com movimento normal e reduzido. Nenhuma conferência
automática pega defeito visual: o H1 invisível passou no build e no
`paginas:conferir`, e só a captura mostrou.

---

## Log

| Fase | Estado | Quando | Observação |
|---|---|---|---|
| 0 · Fundação | ✅ | 19/10 | Astro 7.4, Tailwind 4.3, Lenis 1.3, GSAP 3.15, three 0.186. Fontes locais (Inter Tight, IBM Plex Mono). `astro check` 0 erros |
| 1 · Home | ✅ | 19/10 | 7 blocos. 7 conferências passando, 4 `{{ TODO }}`. Capturas desktop, celular e reduzido: console limpo, nada oculto ao fim da rolagem, sem rolagem lateral. Defeito achado e corrigido: H1 invisível (ver "GSAP lê o transform") |
| 3 · Conteúdo | ⬜ | | Esperando as pendências do brief |
| 4 · Páginas | ⬜ | | |
| 5 · SEO e tracking | ⬜ | | Depende do domínio |
| 6 · Publicação (demonstração) | ✅ | 19/10 | Demonstração no projeto `site-mobiletec`, por API a partir do commit `57f6196`, em `site-mobiletec-hub3psmarketing.vercel.app`. Projeto **não está ligado ao Git**: push não publica sozinho. Domínio próprio e lançamento pendentes |
| (sem fase) · Git **não** ligado | ⚠️ | 20/10 | **Correção de uma linha anterior, que dizia que o push publicava sozinho: estava errado.** Os dois únicos deploys do projeto (`57f6196` e `70fcb2c`) foram feitos por API nesta sessão. O segundo pareceu recusado porque a sessão reiniciou e a chamada foi repetida: a primeira tinha passado. Os pushes seguintes não publicaram nada, e a API segue no limite de 100 deploys por dia da conta. **O ar está em `70fcb2c`**, sem a logo e sem a animação. Saída: o Guilherme liga o Git em Settings → Git |
| (sem fase) · Sede | ✅ | 19/10 | Itajaí/SC no hero, no número da sede, no rodapé e no JSON-LD |
| 2 · Identidade | 🟡 | 19/10 | Paleta da logo aplicada (roxo `#433A6B`, cinza `#666666`), lida da imagem. **Falta o arquivo da logo**: chegou só como imagem no chat |
| 2 · Identidade · logo em SVG | ✅ | 20/10 | Vetorizada com potrace dos PNGs originais (99,8% dos pixels iguais), **aprovada pelo Guilherme**. No site: cabeçalho e rodapé com a horizontal negativa, favicon com o símbolo |
| (sem fase) · Animação da logo | ✅ | 20/10 | Duas "›" desenham o símbolo e o traço menor fecha. Abertura em tela clara na primeira página da visita (`sessionStorage`), com a logo voando para o hero; nas outras, a logo se desenha no hero. Movimento reduzido e sem JS: logo pronta, sem abertura. Conferido em quadros com relógio controlado a 1440, 1024 e 390 px. Defeito achado e corrigido: a região padrão da máscara do SVG cortava a parte de baixo do símbolo |
| (sem fase) · Animação da logo, segunda versão | ✅ | 20/10 | Pedidos do Guilherme: **sem as "›"**, o desenho é o próprio traço da logo; **sem logo grande no hero**; mais lenta e suave (2,4 s de desenho em `sine.inOut`, contra 1,35 s em `power2`). A abertura agora termina pousando no símbolo da logo do menu (`simboloNaHorizontal` em `logo.gerado.ts`), com troca invisível. A cena 3D só carrega depois da abertura, para não disputar o quadro. Medido em tempo real: abertura de 5,3 s, gravada a ~49 quadros por segundo sem engasgo. **Atenção:** quadros com o relógio falso do Playwright comprimem o tempo; para julgar ritmo, use o screencast em tempo real |
| (sem fase) · Abertura sem piscar | ✅ | 20/10 | O Guilherme viu a logo inteira aparecer e travar no primeiro segundo. Confirmado no screencast: o markup é a logo pronta e aparecia antes de o script zerar o desenho, e montar os gatilhos de rolagem da página inteira travava a thread por ~310 ms. Agora a logo da abertura fica com `visibility: hidden` até a classe `desenhando`, e o `montarPagina()` só roda depois que a abertura acaba. Trava de segurança no BaseLayout: se o script não assumir em 3,5 s, a abertura sai sozinha. Lacunas que sobraram no screencast são momentos de tela parada (a pausa com a logo pronta), não travada |
| (sem fase) · Git ligado, produção não | ⚠️ | 20/10 | O Guilherme ligou o Git: o push de `b037a5a` gerou deploy sozinho, pronto e conferido (abertura nova no HTML). Mas saiu como **prévia**: a branch de produção do projeto não é esta. Promover por API deu 422, e criar deploy por API segue no limite diário. Falta trocar em Settings → Environments → Production → Branch Tracking para `claude/loving-archimedes-rp33cv` |
| (sem fase) · Domínio próprio | 🟡 | 20/10 | `site.mobiletec.hub3ps.com` ligado pelo Guilherme, DNS certo, responde 200 e público. Serve a **produção antiga** (`70fcb2c`, sem logo nem animação). Apontar o domínio para o deploy novo por API deu 403 (sem permissão de alias). Falta o Guilherme promover o deploy de `b037a5a` no painel e trocar a branch de produção |
| (sem fase) · Site antigo aproveitado | ✅ | 20/10 | Lido `mobiletec.com.br`. Entrou: endereço, telefone, e-mail, horário e Instagram (contato, rodapé e JSON-LD); os três serviços (móveis, web e desktop, manutenção) no bloco "O que fazemos", agora com quatro células; os quatro diferenciais num bloco novo, "Como trabalhamos". Reescrito na voz do site, sem os superlativos de lá. Ficou de fora: as fotos (banco de imagem) e a política de privacidade (vale revisar quando houver formulário ou tracking) |
| (sem fase) · Abertura a cada carga | ✅ | 20/10 | Pedido do Guilherme: a animação roda sempre que a home carrega, não só na primeira visita. Saiu o `sessionStorage`. Páginas internas não têm abertura |
| (sem fase) · Páginas de projeto | ✅ | 20/10 | O pedido falava em 3 páginas e link nas 4 primeiras logos: **fiz 4**, para nenhuma logo levar a página repetida ou vazia (JBS, Copacol, Grupo Pluma, Minerva Foods), em `/projetos/<slug>`. Modelo único, `src/pages/projetos/[slug].astro`, conteúdo em `src/data/projetos.ts`: topo com logo, ficha (setor, desde, plataformas), desafio e solução, três frentes, números, telas, tecnologia, depoimento, próximo projeto e contato. Tudo que não tem fonte é `{{ TODO }}` com o nome do campo, e acende sozinho quando o dado entra. As 4 logos ganharam "Ver projeto". 27 conferências passando |
| 6 · Publicação | ✅ | 20/10 | O Guilherme pôs a produção na branch `claude/loving-archimedes-rp33cv`. O push de `047f79a` publicou sozinho em produção, e **`site.mobiletec.hub3ps.com` serve o site novo**: home e `/projetos/jbs` em 200, abertura, bloco "Como trabalhamos", contato do site antigo e links das logos conferidos no HTML do domínio. Push que só mexe fora de `mobiletec-site-astro/` não gera deploy |
| 3 · Conteúdo, respostas da Mobiletec | ✅ | 24/11 | Doc "Site Mobiletec, informações para finalizar" (Drive do Guilherme) respondido. Aplicado: **fundação 1999** e uma menção só, no topo (saíram os blocos de números e de linha do tempo, que repetiam a fundação); **Vibra Foods** no lugar da Vibra Energia; **sem órgãos públicos** (não atendem: saiu do hero, da grade de clientes e da descrição); texto dos serviços escrito por eles; **WhatsApp** 47 3349-4088; **produtos** Flowee, VendeAI e RoterizAI ao lado do JurIA, num bloco novo e com página cada um em `/produtos/<slug>` (dados em `produtos.ts`, do kit do vídeo); **cases são de produto**: as 4 páginas de projeto por cliente e o "Ver projeto" nas logos saíram; **política de privacidade** do site antigo em `/privacidade`, com link no rodapé. 27 conferências passando, capturas a 1440 e 390 px sem erro de console nem rolagem lateral |
| (sem fase) · Contato e rodapé | ✅ | 24/11 | Pedido do Guilherme: o bloco de contato leva só os botões WhatsApp, e-mail e Instagram (saíram o botão do telefone e o endereço). Rodapé refeito em colunas (marca, navegação, contato, endereço), endereço e horário discretos, e barra final com razão social, CNPJ e privacidade |
| (sem fase) · Produtos sem TODO | ✅ | 24/11 | Pedido do Guilherme: as páginas de produto saem sem o `{{ TODO }}` do fim (números, tecnologias, depoimento). Ficam sem esses blocos por enquanto; os campos seguem nulos em `produtos.ts` |

**Última atualização:** 24/11/2026, respostas do doc do site aplicadas.

## O que falta

| O quê | Onde | Trava em |
|---|---|---|
| Números, tecnologias e depoimento dos produtos | `src/data/produtos.ts`. As páginas saem sem eles, sem `{{ TODO }}` (decisão do Guilherme, 24/11) | Mobiletec, se quiserem |
| Números de operação na home | Saíram com o bloco de números. A Mobiletec perguntou se ajudam: responder e, se vierem, voltar como bloco próprio | Mobiletec |
| Fotos do time ou do escritório | A Mobiletec perguntou se ajudam | Mobiletec |
| Hub de Certificação | Está no vídeo, mas não foi listado no doc do site. Confirmar se entra | Mobiletec |
| Domínio definitivo | `src/data/site.ts`, `site.url`, e `astro.config.mjs`; sai o `noindex` | Mobiletec |
| Menu no celular | `Header.astro`: hoje só o botão Contato aparece abaixo de 768px | Decisão |

## Decisões tomadas sem o Guilherme

1. **Paleta lida da logo**, sem código oficial. O roxo da marca vira roxo
   claro (`#8F86C9`) como destaque sobre o escuro, porque o original some ali
2. **Sem sitemap e com `noindex`** enquanto não há domínio, para não indexar um
   endereço provisório
3. **A copy do hero e dos títulos é nova**, escrita sobre os fatos do brief.
   Nenhum número ou cliente novo: "mais de 25 anos", "desde 2000", "empresas e
   órgãos públicos de porte" e os 13 logos são todos de fonte registrada
4. **Os três serviços** (desenvolvimento, sustentação em produção, produto
   próprio) são as únicas frentes que as fontes sustentam. O resto é `{{ TODO }}`
5. **A cena 3D pesa 526 KB sem compressão** (three.js inteiro). Carrega depois
   do primeiro paint, só com WebGL e movimento liberado, e para de desenhar fora
   da tela. Se pesar no celular, a primeira troca é importar só os módulos usados

## Travou em quê

_(nada travado: o que falta é dado da Mobiletec, não técnica)_
