---
tipo: cliente-doc
cliente: juria
atualizado: 2026-11-27
autor: claude
origem: agencia_marketing, clients/juria/ESTADO-site-astro.md (migrado em 27/11/2026)
---
# Estado da execução · site JurIA em Astro

> **LEIA ISTO PRIMEIRO** se você é uma sessão nova e o pedido foi continuar o
> site em Astro. Este arquivo diz onde a execução parou e o que você precisa
> saber que **não está no brief**.
>
> Se a última linha do log não bate com o que existe em disco, confie no disco.

## Como retomar, em ordem

1. O site está na `main` desde 12/11/2026. A prévia publica da `feat/site-astro`, e a produção, do repo `juria-lps` (ver `docs/processos/publicar-site-juria.md`)
2. Ler [[04-clientes/juria/site/brief-migracao|brief-migracao-juria-astro.md]]. Ele já foi
   corrigido com a fase de descoberta: onde houver `✅ APURADO`, vale o apurado,
   não a premissa original
3. Ler [[_arquivo/juria/PLANO-execucao-site-astro|PLANO-execucao-site-astro.md]]. Oito fases,
   cada uma com critério de pronto
4. Continuar da primeira fase não concluída no log abaixo
5. **Atualizar este arquivo ao fim de cada fase, antes de começar a seguinte.**
   Commitar junto. É o que permite a próxima sessão continuar

## Regras que não mudam, em nenhuma hipótese

- **Nada do repositório `juria-lps` é tocado.** É o site em produção, recebendo
  tráfego pago agora. Ele nem precisa estar clonado para este trabalho
- Trabalho só em `agencia_marketing`, branch `feat/site-astro`, pasta
  `juria-site-astro/`
- ~~Sem deploy, sem criar ou alterar projeto na Vercel~~ **MUDOU EM 06/10/2026.**
  O Guilherme precisava mostrar o site na reunião com a Mobiletec e abriu a
  exceção. O site publica num projeto Vercel **próprio e novo**, `site-novo-juria`,
  que ele criou vazio, com root `juria-site-astro/` e branch de produção
  `feat/site-astro`. Os projetos `juria` (o hub) e `juria-lps` (produção)
  continuam intocados, e essa parte da regra não mudou.
  O `juria-site-astro/vercel.json` existe **só por causa desse deploy de
  demonstração**: ele carrega `X-Robots-Tag: noindex, nofollow` para o site novo
  não competir no Google com o `juria.app.br`, que está recebendo tráfego pago.
  **Esse arquivo sai no dia do cutover**, junto com a decisão de domínio.
- **Sem inventar:** depoimento, logo de cliente, case, número de uso, número de
  WhatsApp. Se faltar dado, marcar `{{ TODO }}` e seguir
- Preço, limite e nome de plano saem **sempre** de
  `agencia_marketing/clients/juria/comercial/planos-e-creditos.md`. Mudaram em
  29/09/2026: qualquer número que você lembre de antes disso está errado

## Contexto que não está no brief e custa caro redescobrir

**Tracking.** O Pixel e o GA4 **não** estão no HTML do site atual, só o GTM
(`GTM-WHQGLTXC`). Os IDs vivem dentro do container. Não há script de Pixel nem
de GA4 para replicar.

**Ordem do Consent Mode.** O bloco vai no `<head>`, **antes** do snippet do GTM.
Não é estilo: invertido, as tags de inicialização já foram avaliadas e disparam
mesmo para quem se opôs. Já aconteceu nesta conta e foi corrigido em agosto.

**O Solo não é "o plano completo mais barato".** Tem quatro recursos:
publicações e prazos automáticos, importação de acervo por OAB, contas a pagar
e receber com NFS-e, e Inteligência de Precedentes. Mais 1 advogado e 1 OAB.
**Nenhuma promessa de "todas as funcionalidades" pode aparecer fora do contexto
"do Plus em diante".** Foi exatamente o erro que a LP atual tinha em cinco
lugares, corrigido em 29/09.

**`ClickTrial` foi removido em 23/09 e não volta.** O evento disparava no clique
do CTA, mas o redirecionamento para `/register` cortava o envio antes de chegar
à Meta. O `ViewRegister` mede a mesma intenção do outro lado do redirecionamento.

**Trial: 7 dias, sem cartão.** Era 14 até 29/09.

**Canonical: `https://www.juria.app.br`**, com www. A produção já redireciona o
apex com 308.

**Identidade visual:** navy `#0A2540`, navy-deep `#061A30`, ciano `#14B4C8`,
ciano-bright `#1DCBE0`, ciano-soft `#7FDBE5`, texto `#0F1B2D`, texto-muted
`#5B6B7D`, borda `#E5EBF0`, fundo `#F7F9FA`. Tokens completos no
`<style>` do `institucional/index.html` do outro repositório.

**Referência de movimento:** animações do site da ADVBox
(`advbox.com.br/software-juridico`), aprovadas pelo Guilherme. Respeitar
`prefers-reduced-motion`.

**⚠️ O ESPELHO DE PRODUÇÃO NESTE REPOSITÓRIO ESTÁ DEFASADO NA COPY.**
`clients/juria/lps/institucional/index.html` é anterior à reestruturação de
29/09: mostra R$ 199, "14 dias" e Basic/Pro/Enterprise, e promete "todas as
funcionalidades em qualquer plano" em cinco lugares. A versão corrigida subiu no
commit `edd7c77` do `juria-lps`, **que não está clonado aqui e não precisa
estar**. Descoberto na fase 2, conferindo o FAQ do espelho contra o `faq.ts` da
fase 1: o `faq.ts` traz a versão nova, o espelho traz a velha.

Consequência, e ela vale para todas as fases seguintes: o espelho é fonte de
**CSS, JS, markup e estrutura**, nunca de número de plano nem de promessa sobre
plano. Isso sai de `src/data/`.

**O porte é scriptado, não copiado à mão.** `npm run portar` regera os onze
blocos (5 de CSS, 5 de JS, 1 de markup) do espelho, e `npm run portar:conferir`
compara byte a byte. Quem precisa divergir de produção escreve em
`src/styles/ajustes.css`, o único CSS da home que se edita. Isso existe porque
"sem diferença visual perceptível" não é verificável por leitura de 5.349 linhas.

---

## Log

| Fase | Estado | Quando | Observação |
|---|---|---|---|
| 0 · Fundação | ✅ | 29/09, 20h40 | Astro 7.3.5 + Tailwind 4.3.3. Build e preview verificados |
| 1 · Dados | ✅ | 29/09, 21h | 4 arquivos em src/data. 20 conferências automáticas passando |
| 2 · Componentes | ✅ | 30/09, 07h30 | 13 componentes + layout. Porte scriptado e conferido byte a byte. 28 conferências de dados e 38 no navegador passando |
| 3 · Home | ✅ | 30/09, 08h00 | 6 das 11 seções pixel a pixel idênticas à produção, as 5 restantes diferindo só pelas correções de 29/09. As 6 âncoras caem em y=0, igual à produção. 2 blocos de copy seguem como TODO |
| 4 · Páginas | ✅ | 30/09, 08h05 | 11 indexáveis + /blog + modelo de /lp, todas com SEO por página e blocos {{ TODO }}. 13 conferências de página passando |
| 5 · SEO e IA | ✅ | 30/09, 08h15 | JSON-LD dos 4 tipos, robots.txt, llms.txt gerado de src/data, e a home passou a ter 1 H1. 21 conferências de página passando |
| 6 · Tracking | ✅ | 30/09, 08h30 | Consent Mode antes do GTM em todas as 13 páginas, nenhum evento novo, e a UTM passou a sobreviver à navegação interna. 44 conferências no navegador |
| 7 · Duas propostas | ✅ | 30/09, 08h45 | /v2 com hero e preços diferentes, noindex e fora do sitemap. Conferida com movimento normal e reduzido |
| 8 · Validação | ✅ | 30/09, 08h55 | RELATORIO-decisoes.md escrito. Checklist da §9 com 17 itens verdes e 6 dependendo de preview |
| (sem fase) · Reconferência | ✅ | 30/09, 09h20 | Nenhuma fase nova. As 104 conferências rodadas de novo em checkout limpo, todas passando, e 1 dos 6 itens ⏳ fechado: o Lighthouse não precisava de preview |
| (sem fase) · Reprodutibilidade | ✅ | 30/09, 11h15 | Nenhuma fase nova, nada pendente para abrir. Ambiente sem `node_modules`, então `npm ci` instalou do zero pelo lockfile e as 105 conferências passaram assim: 28 de dados, 11 de porte, 1 de llms.txt, 21 de página, 44 no navegador, mais `astro check` e build limpos. Os 5 itens ⏳ restantes seguem travados em preview, que o brief proíbe |
| (sem fase) · Correções do Guilherme | ✅ | 30/09, 11h05 | Espelho de produção sincronizado, que era a raiz. Grade de preços em duas linhas, copy da home batendo com o ar, contraste do CTA resolvido. 111 conferências passando |
| (sem fase) · Lapidação da home | ✅ | 30/09, 15h05 | Estrutura, copy e duas rodadas de design. Canvas contínuo com cápsulas escuras, sem eyebrow, oito animações. Detalhe em `ESTRUTURA-home.md`. 146 conferências passando |
| (sem fase) · Reconferência em ambiente limpo | ✅ | 01/10, 07h20 | Nenhuma fase nova para abrir: as oito seguem concluídas. `npm ci` do zero pelo lockfile e as 156 conferências rodadas de novo. Achou **1 conferência quebrada no celular**, consertada nesta rodada: era defeito do medidor, não do site. 156/156 passando, três rodadas seguidas |

| (sem fase) · Conferência de produção consertada | ✅ | 01/10, 09h35 | Nenhuma fase nova. Achou que **o `diff-producao.mjs` estava quebrado e não rodava desde a fase 3**: a lapidação de 30/09 reestruturou a home e ninguém atualizou a lista `ESPERADO`, então ele acusava 25 divergências e foi ignorado em três rodadas que se declararam verdes. Consertado, e no caminho ele achou **1 defeito real no site**, a âncora caindo 1px atrás do cabeçalho no celular. 156/156 mais o `diff-producao` passando |

| (sem fase) · A conferência de dados passou a ler a fonte da verdade | ✅ | 01/10, 11h30 | Nenhuma fase nova: as oito seguem concluídas e nenhuma foi refeita. As 156 conferências rodaram de novo em ambiente limpo, com `npm ci`, e passaram. Achou que **o `conferir-dados.mjs` nunca abria o `planos-e-creditos.md`**, apesar de o cabeçalho dele dizer que conferia contra a fonte: preço, limite e trial estavam digitados dentro das asserções. Era o mesmo defeito do espelho defasado e do `ESPERADO` defasado, na terceira forma. Agora um parser lê o markdown e as asserções não sabem número nenhum. 163/163 mais o `diff-producao`. **Nenhuma linha do site mudou** |

| (sem fase) · As dez perguntas respondidas | ✅ | 05/10, 10h50 | Nenhuma fase nova. O Guilherme decidiu as dez em aberto e todas foram aplicadas. Oito mudam o site, duas nao mudaram nada (o selo no Max e o ciano do H1 ja' estavam como ele queria). Criado o mecanismo de `ajuste` no porte, para travessao e `aria-label` sem edicao a mao. **Achou que o `diff-producao` NAO passava em arvore limpa**, contra o que a linha de 01/10 afirma: 4 ancoras divergem, e sao anteriores a esta sessao. 39 + 21 + 92 conferencias passando, mais `astro check`, build e porte |

| (sem fase) · Home finalizada, 6 ajustes do Guilherme | ✅ | 05/10, 14h30 | Nenhuma fase nova. Cinco commits: ancoras, mockup trocado por print emoldurado, esteira em previa, menu com submenus e gaveta, barra flutuante. **Achou e corrigiu 1 defeito real que afetava trafego pago** (a ancora da URL parava 139px fora no desktop e 255px no celular depois da troca de fonte) e 6 defeitos introduzidos no proprio trabalho, todos pegos por conferencia e nao por leitura. Peso da home caiu 59% no HTML e 41% no CSS. 41 + 21 + 133 + 12 conferencias passando |

| (sem fase) · Ajustes e revisão de copy da home | ✅ | 05/10, 18h40 | Nenhuma fase nova. Seis commits: barra de menu, avisos do hero, Jú em moldura de WhatsApp, e a revisão de copy em três partes. **A auditoria achou que a home repetia o defeito que a LP tinha em cinco lugares e foi corrigido em 29/09**: prometia recurso que o plano de entrada não tem. Voltou porque a copy foi escrita em cima daquela LP. Criadas 3 travas que leem o `funcionalidades.md` e derrubam a rodada se isso voltar. O bloco de funcionalidades passou de 20 itens tirados da LP para 36 do inventário de produto. 43 + 21 + 137 + 12 conferências passando |

| (sem fase) · Mapa do sistema em grafo | ✅ | 05/10, 19h34 | Nenhuma fase nova. Dois commits, `67fa49e` e `5d53bd5`: o bloco 7 virou o mapa do sistema em grafo, com as 28 telas da navegação real, painel escuro, zoom na entrada e pulso nas conexões. No celular vira espinha vertical. 43 + 21 + 137 + 12 + 20 âncoras passando. Esta linha foi escrita depois, na rodada seguinte |

| (sem fase) · /v2 vira a home com o grafo | ✅ | 05/10 | Nenhuma fase nova. Pedido do Guilherme: a home vai ganhar outro desenho para o bloco 7, e o grafo atual fica em `/v2` como segunda opção. A `/v2` perdeu o hero e os preços próprios de 29/09 e passou a ser a home inteira, menos o bloco 7, que é `v2/FuncionalidadesV2.astro`: cópia congelada do grafo, com classes e keyframes `v2-mapa-*` em `v2.css`. **Mexer no mapa da home não muda a `/v2`.** Conferido por pixel, seção a seção, home contra `/v2`, em desktop e celular: todas iguais, incluindo o mapa. A tarja da `/v2` continua. 43 + 21 + 137 + 12 + `diff-producao` passando |

| (sem fase) · Bloco 7 vira pasta com abas | ✅ | 06/10 | Nenhuma fase nova. Decisão do Guilherme depois de três esboços (metrô, dossiê, um dia no escritório): o bloco 7 da home virou uma **pasta com abas**, uma por área do menu mais a dos atalhos, com as telas em grade e entrada em cascata a cada troca. Recorte de pasta como aceno jurídico, painel escuro do grafo como identidade. O grafo segue em `/v2`. **Sem JavaScript as 8 áreas aparecem empilhadas**, e as abas só surgem com `scripts/novos/pasta.js`, que não depende da classe `.js` (ela some com movimento reduzido). A frase descritiva de cada área ficou de fora: não existe na fonte, e não foi inventada. 43 + 21 + 139 + 12 + `diff-producao` passando |

| (sem fase) · Menu vira Recursos, IA, Planos e Sobre | ✅ | 05/10, 22h08 | Nenhuma fase nova. Commit `6b71f69`, estrutura ditada pelo Guilherme. "Produto" vira "Recursos", com grupos espelhando as áreas do menu do sistema. A IA vira entrada própria, com a Jú primeiro; as demais funções de IA entram depois da reunião com a Mobiletec. Jurimetria e due diligence ficam em "Recursos", sob "Pesquisas". Itens sem página própria apontam para `/#ancora`, não `#ancora`, porque o menu sai nas 12 páginas. Linha registrada em 14/10 |

| (sem fase) · Os treze logos de cliente entram na home | ✅ | 06/10, 07h37 | Nenhuma fase nova. Commit `659c68b`. A lista veio da Mobiletec e o Guilherme liberou citar os treze sob o rótulo "Empresas que rodam sistemas da Mobiletec". Originais versionados em `clients/juria/assets/logos-clientes/originais/`, normalizados por `clients/juria/ferramentas/preparar-logos.py`. A esteira ganhou painel claro dentro da seção escura, porque os logos reais somem sobre o navy. Logos viraram `eager` (com `lazy`, metade nunca aparecia para quem pede menos movimento). 147 no navegador, 45 de dados, 21 de página, 12 portados. Linha registrada em 14/10 |

| (sem fase) · Copy conferida contra o documento da Mobiletec | ✅ | 14/10 | Nenhuma fase nova. O Guilherme mandou o PDF de funcionalidades da Mobiletec, registrado na seção 8 do `comercial/funcionalidades.md` e versionado ao lado dele. Corrigido: precedentes de **todos os tribunais**, não só STF e STJ; jurimetria **por tipo de ação e tribunal**, sem "juiz" nem "vara"; análise de risco **do caso**, não "em oportunidades"; due diligence **de pessoas e empresas**, não "por número de processo". Entrou o aviso da Resolução CNJ 615/2025 no fim do bloco de IA. Mantidos por decisão do Guilherme: "em tempo real" no card 3, o alerta de mudança de tese, e o assistente respondendo sobre financeiro. `conferir`, build e 21 de página passando |

| (sem fase) · WhatsApp entra no mapa do sistema | ✅ | 14/10 | Nenhuma fase nova. Dois prints do sistema confirmaram a tela "WhatsApp" no grupo Carteira, e ela entrou no mapa: 29 telas. Como a `/v2` lê os mesmos dados, o grafo dela também ganhou o nó, sem sobrepor rótulo (conferido em captura). O `funcionalidades.md` ganhou a seção 3.2 (WhatsApp do escritório, que fala com cliente) e o detalhe da Jú na 3.1 (que só fala com a equipe), e fechou a dúvida da "secretária virtual": é a Jú, e o PDF da Mobiletec erra ao dizer que ela transfere para humano. `conferir`, build e 21 de página passando |

| (sem fase) · Deploy na Vercel | ✅ | 14/10 | Nenhuma fase nova. O projeto `site-novo-juria` (que estava como `project-hbmde` até o Guilherme renomear em 14/10) **não está ligado ao Git**: tinha um deploy só, de 06/10, e os pushes de 14/10 não publicavam. Publicado por API a partir do commit `04a9f3f`. O primeiro deploy saiu sem build, porque o projeto **não tinha Root Directory salvo**, e o domínio `site.juria.hub3ps.com` deu 404 por cerca de 1 minuto; o segundo saiu com Root Directory `juria-site-astro` e framework Astro, que ficaram salvos no projeto. Conferido no domínio: home, `/v2` e páginas em 200, mudanças de 14/10 presentes, `noindex` ativo. **Para o push voltar a publicar sozinho:** ligar o Git em Settings → Git e, em Environments → Production, trocar a branch para `feat/site-astro`. ✅ **Feito pelo Guilherme no mesmo dia**: o projeto está ligado ao repo, e o push publica sozinho |

| (sem fase) · Estrutura do site aprovada | ✅ | 14/10 | Nenhuma fase nova. Páginas por área de trabalho, não por funcionalidade, com três destaques: Atendimento e WhatsApp, Inteligência artificial, Financeiro e nota fiscal. Detalhe em [[04-clientes/juria/site/estrutura-site\|ESTRUTURA-site.md]]. **Próximo passo: a página de Atendimento e WhatsApp**, começando pela pesquisa de palavra-chave |

| (sem fase) · Estrutura aplicada no site | ✅ | 14/10 | Menu novo (Recursos com 4 áreas e "Tudo o que o JurIA faz", IA como link direto, Planos, Sobre). Três páginas novas em esqueleto, com URL provisória: `/atendimento-e-whatsapp`, `/pesquisa-e-jurimetria`, `/financeiro-e-nota-fiscal`. Cada aba da pasta da home ganhou link para a página da área. `/jurimetria` e `/due-diligence-juridica` saíram do menu e ficaram linkadas do hub de pesquisa. O rótulo "Todas as funcionalidades" foi barrado pela trava de 29/09 e virou "Tudo o que o JurIA faz". 45 de dados, 21 de página, build com 17 páginas |

| (sem fase) · Root Directory perdido ao ligar o Git | ✅ | 14/10 | Ao ligar o repo, o projeto `site-novo-juria` ficou **sem Root Directory**: os dois pushes seguintes construíram a raiz do repositório e o domínio deu 404 por cerca de 10 minutos. Restaurado por deploy via API com `rootDirectory` na requisição (a sessão não tem permissão para alterar o projeto). O Guilherme fixou no painel **Root Directory `juria-site-astro` e framework Astro**. **Se o domínio voltar a dar 404 depois de um push, conferir isso primeiro** |

| (sem fase) · Home revisada com o documento da Mobiletec | ✅ | 14/10 | Sete mudanças aprovadas pelo Guilherme, detalhe no fim de [[04-clientes/juria/site/estrutura-home\|ESTRUTURA-home.md]]: bloco de WhatsApp no lugar do da Jú, nota fiscal no lugar do "O que muda" repetido, IA com as ações do dia a dia, faixa de integrações nova, FAQ com WhatsApp e nota fiscal, hero ajustado. A âncora `#ju` virou `#whatsapp` e entrou `#integracoes`. A `/v2` recebeu as mesmas mudanças, porque usa os mesmos blocos. 45 de dados, 21 de página, build e capturas em desktop e celular. **`conferir-navegador` e `diff-producao` não rodaram**, por decisão do Guilherme nesta sessão |

| (sem fase) · Dois defeitos do celular | ✅ | 14/10 | Achados pelo Guilherme e numa revisão visual da home inteira a 390px. (1) O marca-texto ciano de "num só sistema" virava um toco solto sobre "sistema" quando a frase quebra em duas linhas: era `::after` absoluto dentro de inline quebrado. Virou fundo do próprio `.accent` com `box-decoration-break: clone`, uma faixa por linha (`tema.css`, `movimento.css`). (2) O quadro da nota fiscal abria com faixa vazia e borda solta, porque o cabeçalho some no celular. `conferir-navegador` 149/149, rodado a pedido do Guilherme, mais 45 de dados. **Nenhuma das 149 conferências pegava o primeiro defeito**: é visual, e só captura de tela mostra |

| (sem fase) · Oito páginas de área escritas | ✅ | 14/10 | Plano aprovado pelo Guilherme, executado com 4 agentes: pesquisa SEO, dois redatores e um revisor de fatos (só rascunho); integração por mim. Template novo de página de área (hero com CTA, faixa de destaques, perguntas, aviso CNJ, FAQ com `FAQPage`, "Veja também"). Texto em `src/data/paginas-area/*.json`; `termosDeCabeca` e os esqueletos saíram do `paginas.ts`. URLs definitivas: `/whatsapp-para-advogados`, `/financeiro-para-escritorio-de-advocacia`, `/pesquisa-juridica`; as provisórias redirecionam (301). 24 `{{ TODO }}` visíveis, cada um ligado a uma dúvida de [[_arquivo/juria/rascunhos-paginas/00-duvidas-mobiletec\|rascunhos-paginas/00-duvidas-mobiletec.md]]. 45 de dados, 21 de página, 149 no navegador, capturas a 390 e 1440px |

| (sem fase) · Cinco dúvidas respondidas pelo Guilherme | ✅ | 14/10 | Secretária virtual atende clientes, nos quatro planos; funções novas do documento da Mobiletec nos quatro planos (envio de documentos e conversão de oportunidade seguem o portal e o funil, Plus em diante); atualização = monitoramento por créditos; planilha sem crédito; primeira importação por OAB a 21 créditos; resumo da intimação sem custo citado. Registrado como premissa na seção 9 do `funcionalidades.md`. `{{ TODO }}` visíveis caíram de 24 para 8, só onde falta conteúdo ou revisão jurídica |

| (sem fase) · Desenho novo, referências Webild | ✅ | 15/10 | Plano de 3 fases aprovado pelo Guilherme. (1) `sistema.css`, comum à home e às páginas: etiqueta em pílula, título bicolor, botão em pílula com seta, cartão em camadas, ícone com brilho, check redondo, FAQ em pílulas, cartão de CTA, raios de luz; `Icone.astro` e `BotaoPilula.astro`. (2) As 8 páginas de área num template só, `AreaPagina.astro`, com cápsula navy no topo. (3) Home: etiqueta em todas as seções, botões em pílula, IA e WhatsApp em cartões com ícone, órbita no escudo da Segurança, preços com painel interno e check redondo (vale também em /precos), Integrações em cartão com ícone, FAQ em pílulas, CTA final em cartão (vale em todas as páginas que usam `CtaBlock`). **Falta:** o print do produto que o Guilherme vai mandar, para a moldura do bloco do sistema (`tourPlataforma.print.arquivo`). O porte voltou a passar com `npm run portar`: o espelho mudou de linha com o "Sob consulta" e só os cabeçalhos dos portados mudaram. 45 de dados, 21 de página, 149 no navegador, capturas a 390 e 1440px |

| (sem fase) · Cabeçalho igual ao da home, e Ilimitado sob consulta | ✅ | 15/10 | Pedidos do Guilherme. (1) As páginas carregavam só parte do CSS da home, então o cabeçalho era a faixa branca de produção, o menu do celular ficava sem estilo e a barra flutuante caía solta abaixo do rodapé. `pagina.css` passou a importar também `responsive`, `blocos-novos`, `tema` e `movimento`; o topo das páginas de área virou cápsula com o cabeçalho flutuando por cima, igual ao hero. (2) Ilimitado "Sob consulta", igual à LP Institucional no ar: campo `sobConsulta` em `planos.ts`. O preço continua no dado (é o da fonte), mas sai do card, da tabela, do JSON-LD, do `llms.txt` e dos textos. Conferência nova: nenhuma página publica o valor |

| (sem fase) · Botões do cabeçalho e da barra em pílula | ✅ | 15/10 | Pedido do Guilherme: o "Começar teste grátis" do cabeçalho, do menu do celular e da barra flutuante passou a ser o `BotaoPilula`, o mesmo do resto do site. No cabeçalho, compacto para caber na pílula do menu; na barra e no menu, largura total com a altura de antes |

| (sem fase) · Celular, Max em destaque e página de planos | ✅ | 15/10 | Pedidos do Guilherme. (1) Celular: as três frases sob o botão do hero viraram coluna com check redondo alinhado; o marca-texto de "num só sistema" afinou e desceu para baixo das palavras; a barra flutuante virou pílula do tamanho do texto e some enquanto o botão do hero está na tela (`barra-flutuante.js` vigia o botão do topo e o `#cta`). (2) O card escuro passou do Plus para o Max (`enfase` em `planos.ts`), e os quatro planos ficam numa linha só, na home e em /precos. (3) /precos no desenho das outras páginas: cápsula no topo (`CapsulaTopo.astro`, extraído da página de área), cards, tabela "Compare" nova no modelo da ADVBox (`ComparaPlanos.astro`: planos com nome, preço e botão presos no alto ao rolar, recursos por grupo, coluna do Max marcada; no celular rola de lado com a coluna do recurso parada), FAQ com as quatro perguntas de plano da home (`FaqArea.astro`) e CTA em cartão (`CtaArea.astro`). De quebra: com o `tema.css` nas páginas, os respiros entre blocos das páginas internas estavam maiores que o desenhado; voltaram com `main.area` na frente dos seletores |

| (sem fase) · Página /sobre no desenho novo | ✅ | 15/10 | `SobrePagina.astro` + `data/sobre.ts`: cápsula com quatro fatos (2000, 25+, SC, CNPJ) fundida com a história (parágrafos e logos aprovados da home), selos de segurança, cartão de contato e CTA. **Pendente com a Mobiletec, marcado como {{ TODO }}:** cidade da sede, 3 a 5 sistemas ou projetos citáveis, e-mail comercial (e telefone, se quiserem) e o número de WhatsApp. O "Contato" do rodapé ainda aponta para `#` |

| (sem fase) · Favicon | ⏳ | 20/10 | O site fica **sem favicon** por decisão do Guilherme: saiu o padrão do Astro (o foguete), e o "IA" que eu gerei da logo foi recusado. Pendente: arquivo aprovado por ele. Quando chegar, entram `favicon.svg`, `favicon.ico` e `apple-touch-icon.png` em `public/` e os `<link rel="icon">` no `BaseLayout.astro` |
| (sem fase) · Favicon | ✅ | 12/11 | O J da logo em branco sobre navy, opção 1 de três, escolhida pelo Guilherme. Gerado do glifo da Inter 800: `favicon.svg`, `favicon.ico` (16, 32 e 48 px) e `apple-touch-icon.png` (180 px, sem canto) em `public/`, e os `<link rel="icon">` mais a `theme-color` navy no `BaseLayout.astro` |
| (sem fase) · Imagem de compartilhamento | ✅ | 12/11 | `public/og-image.png`, 1200x630, aprovada pelo Guilherme: título da home, tela Meu Dia e a linha da Mobiletec, todo texto tirado do site. Antes a metatag apontava para um arquivo que não existia (404). O `og:image:alt` deixou de dizer "all-in-one" e passou a ser o título da home |
| (sem fase) · Revisão da Mobiletec, Home bloco 1 (topo) | ✅ | 22/10 | A Mobiletec mandou a revisão do site (PDF da Isadora, 21/10), reorganizada por página em [[04-clientes/juria/fontes/2026-10-21-revisao-mobiletec\|revisao-mobiletec-2110.md]]. **A revisão passou a ser a referência de copy**, acima do "palavra por palavra de produção" (decisão do Guilherme, 22/10). Execução bloco a bloco, cada um aprovado antes. Feito: selo sem "do Solo ao Ilimitado"; texto de apoio novo; linha do teste embaixo do botão, saindo de `linhaTeste` em `planos.ts`, que vale para o site inteiro (opção B do relatório); faixa de confiança com LGPD, "Integração oficial com o CNJ" e Mobiletec desde 1999. **Fundação corrigida para 1999** em `site.ts` e nos docs internos; os números e descrições do site já saem do dado. `conferir-dados` tinha bug com duas ocorrências da mesma frase, corrigido. Próximo: Home bloco 2, Quem constrói |
| (sem fase) · Revisão da Mobiletec, Home bloco 2 (Quem constrói) | ✅ | 22/10 | Texto da Mobiletec palavra por palavra, em dois parágrafos, no lugar dos três de 05/10. "25+ anos desenvolvendo sistemas" na Home e no /sobre (o pedido era só do /sobre; o Guilherme alinhou os dois). Legenda dos logos: "Empresas atendidas pela Mobiletec". O /sobre reusa `autoridade`, então o item 5.2 da revisão (mesmo texto e legenda) já fica atendido. Próximo: Home bloco 3, Por que trocar |
| (sem fase) · Revisão da Mobiletec, Home bloco 3 (Por que o JurIA) | ✅ | 22/10 | Rótulo, apoio e os três cards com o texto da Mobiletec. O card 3 virou atendimento ao cliente (Portal do Cliente). Etiquetas escolhidas pelo Guilherme: Fragmentação, Trabalho manual, Atendimento. Título mantido, não foi citado. Próximo: Home bloco 4, Financeiro e nota fiscal |
| (sem fase) · Revisão da Mobiletec, Home bloco 4 (Financeiro e nota fiscal) | ✅ | 22/10 | Título, apoio e as linhas de NFS-e e cobrança com o texto da Mobiletec ("A nota fiscal sai sozinha" era falso: a nota é emitida pelo sistema). O plano saiu de cada linha e virou `oQueMuda.nota`, embaixo do quadro. Coluna "Hoje" mantida. Próximo: Home bloco 5, O sistema por dentro |
| (sem fase) · Revisão da Mobiletec, Home bloco 5 (O sistema por dentro) | ✅ | 22/10 | Apoio novo e legenda "Imagem ilustrativa, com dados de exemplo." (`tourPlataforma.legenda`). **O print chegou**: `public/imagens/meu-dia.webp`, 2000x1129, feito pelo Guilherme com dados de exemplo, menus recolhidos e zoom reduzido para caber "Próximos dias". O `{{ TODO }}` da moldura saiu. Pendente opcional: o contador "Publicações a revisar" está em 0 no print. **Ritmo novo, decisão do Guilherme em 22/10:** a cada bloco só `conferir`, build e `paginas:conferir`; navegador e `diff-producao` ao fechar cada página. Próximo: Home bloco 6, Inteligência artificial |
| (sem fase) · Print do celular no "O sistema por dentro" | ✅ | 22/10 | No celular o print do desktop virava miniatura. Abaixo de 600px a moldura de navegador some e entra uma moldura de telefone com `public/imagens/meu-dia-celular.webp` (720x1494, print do Guilherme do topo do Meu Dia no celular). Um print só, sem carrossel, decisão do Guilherme. `conferir-navegador` mede a moldura de cada perfil e passou a rolar até o print antes de conferir se a imagem carregou: com imagem lazy, o `naturalWidth` era 0 sem nada quebrado. 149 conferências no navegador. Próximo: Home bloco 6 |
| (sem fase) · Revisão da Mobiletec, Home bloco 6 (Inteligência artificial) | ✅ | 22/10 | Título novo; 11 pontos em três grupos (No dia a dia, Na produção, Na estratégia), sem selo no cartão. Entraram pesquisa de jurisprudência, modelos do escritório e due diligence; precedentes viraram "qualificados" (BNP do CNJ). O plano saiu dos cartões para `notaPlanos`, e `conferir-dados` agora exige que todo ponto bloqueado no Solo esteja nela. Análise de risco: "pode ser reavaliada". Aviso cita o Conselho Federal da OAB no lugar da Resolução CNJ 615/2025. Próximo: redesenho do bloco 6 |
| (sem fase) · Redesenho do bloco 6 (IA) | ✅ | 22/10 | O Guilherme recusou três desenhos: cartões em grade com o nome do grupo em cima, faixas horizontais por grupo e cartões com vitrine ilustrada. Aprovado: **o bloco sai da cápsula escura** (fundo claro, título navy) e os cartões ficam navy, com ícone só em traço ciano, sem o quadrado com brilho e sem número. Efeito na Home: a sequência passa a alternar, cápsula do mockup, IA clara, cápsula da Jú. Nota de planos centralizada. Próximo: Home bloco 7, Atendimento e WhatsApp |
| (sem fase) · Revisão da Mobiletec, Home bloco 7 (Atendimento e WhatsApp) | ✅ | 22/10 | A Jú deixou de atender cliente: subtítulo novo, "Secretária virtual" virou "Portal do Cliente", "Lembretes e cobranças" virou "Avisos para o cliente" (envio pela equipe), caixa de entrada com texto novo. Conversa de exemplo com a resposta sugerida pela Mobiletec. Custo de mensagens corrigido (QR Code sem custo da Meta). "Do Solo ao Ilimitado" virou "Em todos os planos". Título mantido, decisão do Guilherme. Próximo: Home bloco 8, Áreas do sistema |
| (sem fase) · Revisão da Mobiletec, Home bloco 8 (Áreas do sistema) | ✅ | 22/10 | Só o título: "Ferramentas para cada etapa, desde o primeiro contato com o cliente." As pastas só têm nome de tela do sistema, nada que as regras gerais da revisão alcancem. Próximo: Home bloco 9, Integrações |
| (sem fase) · Revisão da Mobiletec, Home bloco 9 (Integrações) | ✅ | 22/10 | Nomes oficiais e ordem da Mobiletec nos dois grupos, e o terceiro grupo "Ferramentas do escritório" (5). Grade em três colunas. Apoio cita as ferramentas; nota do Domicílio diz "em homologação" em vez de "está pronto". Título mantido. Próximo: Home bloco 10, Planos |
| (sem fase) · Revisão da Mobiletec, Home bloco 10 (Planos) + ajuste do 9 | ✅ | 22/10 | **"Ilimitado" virou "Sob consulta"** (id interno segue `ilimitado`), selo "Proposta sob medida", limites "Sob medida", bullets e descrição da revisão. Solo, Plus e Max alinhados à tela do sistema: franquia da Jú, conta própria de IA, "Cobrança mensal, sem fidelidade" (`textoCobranca`) e "Suporte prioritário" no Max; descrição nova do Max. **`planos-e-creditos.md` atualizado** (seções 1, 1.2 e 4), porque é a fonte que as conferências leem; `fonte-da-verdade.mjs` mapeia "Sob consulta" para `ilimitado`. Tabela comparativa (`funcionalidades.ts`) já com "Sob medida"/"Sob consulta" nas linhas de limite. Nota de planos com o texto da Mobiletec (item 4.3). **WhatsApp oficial (47) 93386-3850 no site todo**: os botões acendem sozinhos. Bloco 9: sem as contagens 9, 6 e 5 e com ícone só no traço. Próximo: Home bloco 11, Segurança |
| (sem fase) · Revisão da Mobiletec, Home bloco 11 (Segurança) | ✅ | 22/10 | Título e apoio da revisão; 2FA "que você pode ativar"; LGPD com controlador e operador; backup sem promessa absoluta; saíram "Sem taxa" e "Sem fidelidade"; entraram criptografia e trilha de auditoria. O /sobre reusa `seguranca.selos`, então os cartões do item 5.3 já ficam corrigidos lá. **Ritmo novo, 22/10:** páginas internas vão para aprovação inteiras, numa mensagem só. Próximo: Home blocos 12 e 13 (FAQ e chamada final) |
| (sem fase) · Revisão da Mobiletec, Home blocos 12 e 13 + ícones da Jú | ✅ | 22/10 | FAQ com os textos da revisão: IA (extração, precedentes do BNP, fechamento sem quantificar crédito, "pode ser reavaliada"), WhatsApp virou "Como meus clientes acompanham os processos?", nota fiscal virou "Como o JurIA emite nota fiscal?", autônomos com o texto dela, teste "disponíveis", fidelidade e limite com o texto do item 4.6 (que o FAQ de /precos reusa). Chamada final com título e texto novos e a `linhaTeste`. Cards da Jú com ícone só no traço. **A Home terminou**: bateria completa verde (45 dados, 12 porte, llms, 22 páginas, 149 navegador, `diff-producao` 0). Próximo: Recursos, página a página |
| (sem fase) · Revisão da Mobiletec, Processos e prazos (2.1) | ✅ | 22/10 | Página inteira: título, apoio, cards, como funciona (01, 02, 03, 04 nova, 06, 07), FAQ (DJEN, monitoramento **gratuito**, excluir com contato), "vínculos entre processos" saiu, aviso da OAB. Regras gerais aplicadas: prazo "sugerido", primeira importação pela OAB gratuita, "Sob consulta". **A linha do teste do topo de todas as páginas de Recursos e IA** (`CapsulaTopo`) passou a ser a `linhaTeste`; no celular ela fica centrada, sem o check. Próximo: Atendimento e WhatsApp (2.2) |
| (sem fase) · Revisão da Mobiletec, Atendimento e WhatsApp (2.2) | ✅ | 22/10 | **Página reestruturada:** a "secretária virtual que atende clientes" não existe e saiu de tudo, inclusive do h1 (agora "WhatsApp para advogados, integrado ao sistema"). Cards novos (caixa da equipe, Portal do Cliente, custo da Meta, Jú). "Como funciona" em dois blocos com subtítulo (`Secao.bloco`, novo em `paginas.ts` e `AreaPagina.astro`): Atendimento ao cliente e Jú, assistente do advogado e da equipe. Saíram a pergunta do chatbot e a da OAB sobre IA atendendo cliente (decisão do Guilherme). FAQ: custo de mensagem da revisão, Jú não fala com cliente, cota sem quantificar crédito, "Sob consulta". Próximo: Pesquisa e jurimetria (2.3) |
| (sem fase) · Revisão da Mobiletec, Pesquisa e jurimetria (2.3) | ✅ | 22/10 | Título "As ferramentas que o caso pede, num só lugar", sem "com IA". Precedentes qualificados do BNP em card, item 02 e FAQ. Imóveis saíram das consultas patrimoniais (não conectados). Itens 01, 04 e 05 com o texto da revisão (previdenciário pela extensão do Chrome). Jurimetria sem custo em créditos; selos de plano viraram frase. Veículos "usa créditos", sem número. **Pendente fora da revisão:** conferir `/jurimetria`, que pode falar em custo de créditos. Próximo: Financeiro e nota fiscal (2.4) |
| (sem fase) · Revisão da Mobiletec, Financeiro e nota fiscal (2.4) | ✅ | 22/10 | Título "com emissão de nota fiscal integrada"; NFS-e "pelo sistema" em todo lugar; PIX e boleto com cartão "sob configuração"; selos dos destaques viraram `notaDestaques` (campo novo em `paginas.ts`, renderizado em `AreaPagina.astro`). Item 01 virou "Como o JurIA emite nota fiscal?" e o `{{ TODO }}` da lista de municípios saiu. Saíram "Advogado precisa emitir nota?", "cobrar inadimplente" e a pergunta da sucumbência. FAQ com a lista de cidades no sistema e o Asaas. Próximo: Tudo o que o JurIA faz (2.5) |
| (sem fase) · Revisão da Mobiletec, Tudo o que o JurIA faz (2.5) | ✅ | 23/10 | IA de 20 a 400; NFS-e pelo sistema; teste "disponíveis". Processos com primeira importação gratuita, monitoramento sem custo e sem vínculos; prazo sugerido; secretária e Jú fora do atendimento; patrimoniais só veículos; previdenciário pela extensão; gestão com o texto da revisão e sem recuperação de crédito; integrações com os nomes oficiais; preços alinhados ao sistema. **Migração:** saíram os nomes de concorrentes do título e o `{{ TODO }}`. FAQ: plano gratuito e LGPD com o texto da revisão. Rodapé: "Trial grátis" virou "Teste grátis" (regra G9). Recursos concluído; bateria completa verde. Ainda com termos proibidos: `/ia-para-advogados`, `/precos`, `/sobre` (próximas da revisão) e `/jurimetria`, `/due-diligence-juridica` e as três `/alternativas-ao-*` (fora da revisão). Próximo: Inteligência artificial (3) |
| (sem fase) · Revisão da Mobiletec, Inteligência artificial (3) | ✅ | 23/10 | Cards sem teto e sem selo (nota "Análise de risco do caso a partir do Plus."), "pode ser reavaliada" em card, item 04 e FAQ. Itens 01, 05, 06 e 07 com o texto da revisão; o `{{ TODO }}` de "os dados treinam a IA?" saiu. Sem "1 crédito por geração", sem "Ilimitado", sem CNJ 615. FAQ de segurança com a resposta de LGPD do 2.5. Próximo: Planos (4) |
| (sem fase) · Revisão da Mobiletec, Planos (4) | ✅ | 23/10 | Subtítulo novo (troca proporcional só no FAQ); descrição sem "Ilimitado". Tabela: saiu "Advogados do escritório" (e o limite `advogados` deixou de ser conferido e de ir ao llms.txt), quatro linhas renomeadas, Jú "Ajustada à operação" no Sob consulta, suporte igual aos cards. Notas de limite de IA com o texto da revisão (DataJud não custa). `planos-e-creditos.md` seção 4 atualizada junto. Chamada final das páginas internas (`CtaArea`) com a `linhaTeste`, o que também resolve o 5.5. SEEU não ganhou linha na tabela (decisão do Guilherme). Bateria completa verde. Próximo: Sobre (5) |
| (sem fase) · Revisão da Mobiletec, Sobre (5) | ✅ | 23/10 | Os três `{{ TODO }}` saíram: sede "Itajaí, SC", os três projetos genéricos em "O que a Mobiletec construiu" e os canais de contato. Contato oficial em `site.contato` e sede em `site.empresa` (JSON-LD de Organization com endereço, e-mail e telefone). Segurança com o subtítulo da revisão e a nota de LGPD (termo e encarregado). **O e-mail sai como texto, sem `mailto:`**: o brief manda contato por WhatsApp rastreado e `conferir-paginas` trava mailto; o telefone abre o WhatsApp. **A revisão da Mobiletec está aplicada inteira.** Bateria completa verde. Pendente fora da revisão: `/jurimetria`, `/due-diligence-juridica` e as três `/alternativas-ao-*` |
| (sem fase) · Fora da revisão: limpeza | ✅ | 23/10 | `/jurimetria` e `/due-diligence-juridica`: "tudo liberado" virou "todas as funcionalidades disponíveis" e o aviso de IA cita a OAB. **As três `/alternativas-ao-*` saíram do site** (fora de `paginas`, do sitemap e do llms.txt; o conteúdo segue em `paginas.ts`), por citarem concorrentes e estarem com TODO. **`/lp/exemplo` foi apagada**; `conferir-paginas` deixou de esperar por ela. Bateria completa verde. ⚠️ **Aberto, com a Isadora:** a consulta de jurimetria (rápida 8 e completa 29 créditos, como diz `/jurimetria` e o `planos-e-creditos.md`) consome créditos ou não? A revisão diz que "o acompanhamento de jurimetria não consome", e `/pesquisa-juridica` já segue a revisão. Decisões do Guilherme em 23/10: contador de publicações do print pode ficar em 0; anúncios com "desde 2000" ficam por enquanto. |
| (sem fase) · Logo da Vibra corrigida | ✅ | 30/10 | O cliente da Mobiletec é a **Vibra Foods**, não a Vibra Energia. Original trocado por `vibra-foods.png` (enviado pelo Guilherme), MAPA do `preparar-logos.py` e rótulo em `home.ts` atualizados; a saída virou `vibra.png`. Rodado na nuvem com ImageMagick 6 via shim (`alpha` vira `matte` no `-draw`); os outros PNGs saíram com bytes diferentes e foram restaurados, só a Vibra mudou. 45 de dados e build verdes |
| (sem fase) · Últimos ajustes da Isadora | ✅ | 12/11 | Pedidos no grupo do JurIA, com a publicação liberada depois que a Mobiletec aprovou as logos dos clientes. Título do financeiro na home no plural, "Dos honorários à nota fiscal, tudo no mesmo sistema."; link "Preços" do rodapé virou "Planos", igual ao menu (o destino segue `#precos`); no FAQ "O que é o DJEN?" da `/gestao-de-processos-e-prazos` saiu "como intimações e editais". `npm run conferir`, build e as 22 conferências de página passando |
| (sem fase) · WhatsApp e telefone novos | ✅ | 12/11 | O Guilherme trocou o (47) 93386-3850 da revisão de 21/10 pelo (47) 98817-5142, no WhatsApp e no telefone de contato. Mudou só `site.ts` (`whatsapp.numero` e `contato`) e a asserção do número em `conferir-dados.mjs`. Os botões `wa.me`, o `/sobre` e o JSON-LD de Organization saem do dado. 45 conferências de dados, 22 de página, build e llms.txt passando |
| (sem fase) · Preparação para o domínio principal | ✅ | 12/11 | `/privacidade`, `/termos`, `/cookies` e `/oab` copiadas byte a byte do `juria-lps` para `public/` (o rodapé já apontava para as três primeiras, e `/oab` é o QR do flyer impresso). `vercel.json`: noindex em todo host que não seja `www.juria.app.br` (a prévia segue fora do Google sem mexer na troca) e sempre em `/oab`, como em produção; `/institucional`, `/geral`, `/trabalhista` e `/previdenciario` redirecionam para `/` com 308; `/v2` redireciona para `/` só no `www`, e segue na prévia. "Contato" do rodapé foi de `#` para `/sobre#contato`. `/blog` sem post: noindex, fora do sitemap e do llms.txt. Sitemap sem barra no fim, que fazia cada URL responder 308. ⚠️ Os termos copiados ainda trazem Basic R$ 199, Pro R$ 499 e teste de 14 dias, e o `/oab` diz "todos os módulos liberados, em todos os planos": é o texto que está no ar hoje, e corrigir texto jurídico depende da Mobiletec. Conferências de dados, de página, llms.txt e build passando. A conferência do navegador (Playwright) não rodou |
| (sem fase) · Páginas do rodapé no desenho novo | ✅ | 12/11 | `/termos`, `/privacidade` e `/cookies` deixaram de ser cópia estática do `juria-lps` e viraram páginas do site: `components/LegalPagina.astro` (cápsula navy sem botões, sumário fixo ao lado e o texto num cartão), `styles/legal.css`, `data/legal.ts` e o corpo em `data/legal/<slug>.html`. Pedido do Guilherme: corrigir só o que é produto, nada jurídico. Mudou só nos termos: seção 3 (Solo, Plus, Max e Sob consulta, com preço e nome saindo de `data/planos.ts`; "todas as funcionalidades" só do Plus em diante) e seção 4 (teste de 7 dias, de `trial.dias`). Privacidade e cookies sem nenhuma palavra mudada, conferido por diff do texto contra o que está no ar. Data e versão dos termos mantidas, por serem da versão jurídica. As três entram no sitemap. `/oab` segue a cópia estática, e o ajuste dela ficou para depois. Conferências, build e capturas no desktop conferidos |
| (sem fase) · Rodapé com links que funcionam fora da home | ✅ | 12/11 | "Recursos", "Inteligência (IA)" e "Central de ajuda" eram âncoras que só existiam na home. Viraram `/#recursos`, `/#inteligencia` e `/#faq`, e "Planos" foi para `/precos`. "Central de ajuda" virou "Perguntas frequentes", que é o que o link abre (Guilherme) |
| (sem fase) · No ar em www.juria.app.br | ✅ | 12/11 | Merge na `main` (b6f7306, 12 conflitos de documento resolvidos um a um) e publicação no `juria-lps` (1f8cc9f), que segue repo separado e estático para o projeto da Vercel poder ser transferido. `npm run publicar` copia o build, sem commit nem push; runbook em `docs/processos/publicar-site-juria.md`. Conferido no ar: páginas 200, sem noindex no `www`, noindex no `/oab` e nos subdomínios, rotas antigas com 308 para a home levando a UTM, apex com 308 para o `www`, canonical com `www`, Pixel `PageView`, GA4 `page_view` e Google Ads disparando, e o botão de teste levando a UTM ao cadastro. O favicon entrou no mesmo dia, ver a linha abaixo |

**Última atualização:** 15/10/2026, desenho novo com as referências Webild. Antes disso, 14/10, quando a copy foi conferida contra o
documento de funcionalidades da Mobiletec. Pendências dele, para a Mobiletec,
na seção 8.9 do `comercial/funcionalidades.md`.
**As oito fases seguem concluídas.**

✅ **AS 4 ÂNCORAS DIVERGENTES FORAM RESOLVIDAS**, e a linha anterior deste
rodapé está superada. Eram 1 bug real e 3 defeitos do medidor:

- **O bug real:** a folha do Google Fonts vem com `display=swap`, o Chrome
  aplica a rolagem do fragmento contra o layout da fonte de fallback, a Inter
  chega, o documento cresce e a âncora nunca é reaplicada. `/#recursos` parava
  139px fora no desktop e 255px no celular, e isso afetava anúncio rodando.
  Corrigido por `src/scripts/novos/ancora-estavel.js`.
- **Os 3 do medidor:** o `diff-producao.mjs` reusava uma aba só para as seis
  âncoras e trocava o hash, o que o navegador trata como navegação no mesmo
  documento, e o `scroll-behavior: smooth` animava até 8.900px enquanto um
  `setTimeout` de 1400ms media no meio do voo.

Hoje são 18 âncoras medidas em aba nova, com `fonts.ready` e pesquisa até o
scroll parar, todas passando.

⚠️ **O QUE AINDA FALTA NA HOME, e é tudo dependência externa:**

Revisada em 14/10/2026.

| O quê | Onde | Trava em |
|---|---|---|
| Print do sistema por dentro | `src/data/home.ts`, `tourPlataforma.print.arquivo` | Guilherme, salvar em `public/imagens/` |
| Número do WhatsApp | `src/data/site.ts`, `whatsapp.numero` | Mobiletec |
| Bloco de prova social | sem lugar ainda | Standby, decisão do Guilherme |
| Imagem OG 1200x630 | `src/layouts/BaseLayout.astro`, aponta para `/og-image.png`, que não existe (o site no ar tem o mesmo defeito) | Gerar a arte ou tirar as metatags |

~~Logos de clientes da Mobiletec~~: **fechado em 06/10**, commit `659c68b`.

Nenhum deles é bloqueio técnico. Print e WhatsApp têm o lugar pronto, com
`{{ TODO }}` visível ou botão já montado, e acendem sozinhos quando o dado
entrar.

⚠️ **ACHADO DESTA RODADA, E ELE CONTRADIZ A LINHA ANTERIOR.** A linha de 01/10
diz "163/163 mais o `diff-producao`". O `diff-producao` **não passa**, e não
passava antes desta sessão: conferido com `git stash`, em árvore limpa, no
commit `7f40d45`. São 4 divergências de âncora, nenhuma causada por este
trabalho:

| Âncora | Onde | O que acontece |
|---|---|---|
| `#recursos` | desktop | para em y=259px, esperado 120px |
| `#recursos` | celular | para em y=359px, esperado 104px |
| `#mockup` | celular | para em y=85px, fica **atrás** do cabeçalho de 87px |
| `#cta` | celular | para em y=9889px, ou seja, não rola para lá |

É o quinto caso do mesmo padrão desta branch: alguém declarou verde o que não
tinha rodado até o fim. Está aberto, não corrigido, e é a primeira coisa a pegar
na próxima sessão.

⚠️ **Entrada em `PENDENTE` esconde mais do que o assunto dela.** A `navbar`
estava lá pelo texto do botão. Quando a pergunta 12 foi respondida e ela saiu da
lista, apareceu uma diferença de **altura** que sempre existiu, 79px em produção
contra 104px aqui. É legítima, a cápsula flutuante da lapidação de 30/09, e foi
para `ESPERADO` com esse motivo. Mas ficou três rodadas invisível, encoberta por
uma pendência que falava de outra coisa.

⚠️ **Esta linha estava defasada e foi corrigida.** Ela dizia "30/09, 11h05",
mas havia duas rodadas registradas no log depois disso, a de 11h15 e a
lapidação de 15h05. Quem lesse só o rodapé do log concluiria que a lapidação
não tinha acontecido.

⚠️ **Esta rodada achou um problema de raiz que invalidava parte da conferência
das fases 2 e 3.** O espelho de produção deste repositório,
`clients/juria/lps/institucional/index.html`, estava **anterior à
reestruturação de planos de 29/09**. A sessão da madrugada só tinha este
repositório, portou e transcreveu dele, e conferiu contra ele. Então "idêntico
à produção" queria dizer idêntico a um retrato velho do site.

O espelho foi sincronizado, o porte refeito, e o que divergia foi corrigido.
Detalhe nas decisões 66 a 71.

⚠️ **A rodada de 01/10, 09h35, achou que o número "156 conferências" estava
incompleto desde 30/09.** A rotina do `AGENTS.md` tem **seis** comandos, e o
sexto, `node scripts/diff-producao.mjs`, **não entrava na contagem e não era
rodado**. Ele quebrou na lapidação de 30/09 e ficou quebrado: a home foi
reestruturada em doze blocos de propósito, e a lista `ESPERADO` dele, escrita na
fase 3, continuou descrevendo a home antiga. Resultado: 25 divergências, todas
legítimas, num script que ninguém abria.

Isso significa que as três rodadas que se declararam "tudo passando", incluindo
as duas de reconferência em ambiente limpo, **estavam verdes num subconjunto**.
Detalhe nas decisões 73 a 76.

---

## Decisões tomadas sem o Guilherme

Registrar aqui **toda** escolha feita sozinho, com o porquê. Vira o
`RELATORIO-decisoes.md` da fase 8, que ele usa para aprovar ou mandar refazer.

### Fase 0

**1. Tema do Tailwind em CSS, não em `tailwind.config.js`.** O plano dizia
config em JS, mas a versão instalada é a 4.3.3, e no Tailwind 4 o tema se
declara em CSS com `@theme`. Ganho inesperado: cada entrada gera a utility e
emite a custom property de uma vez, então o hex existe uma vez só e serve tanto
as páginas novas em utility quanto as 3.512 linhas de CSS da home, que pedem
`var(--navy)`. Arquivo: `src/styles/tokens.css`.

**2. Preflight do Tailwind desligado.** O import é fatiado, `theme.css` mais
`utilities.css`, em vez do `tailwindcss` inteiro. O preflight zera `font-size`
e `font-weight` de heading e tira `list-style` de lista, e a home é um porte de
CSS que está em produção com o critério de "sem diferença visual perceptível".
No lugar dele vale o reset do próprio site, que já faz box-sizing, zera margem
e padding e normaliza `img`, `a` e `button`. Consequência para página nova:
heading herda o estilo de marca e lista nasce com bullet, então quem quiser
outra coisa usa utility explícita.

**3. `@theme static` em vez de `@theme`.** Sem `static` o Tailwind poda do
`:root` toda variável que nenhuma utility usou. As cores escapariam pelos
apelidos, que as referenciam com `var()`, mas as cinco sombras não têm apelido,
porque o nome do token e o nome que a home pede são o mesmo. Elas saíram do
primeiro build: `var(--shadow-md)` no CSS portado resolveria para nada e a home
perderia profundidade sem erro nenhum aparecer. Pego conferindo o `:root` do
CSS buildado, não no log do build, que passou limpo.

**4. Layer `site` declarada depois de `utilities`.** Colisão de nome entre
classe de produção e utility do Tailwind. Aconteceu com `.container` no
primeiro build: o Tailwind gera a dele com `max-width` por breakpoint até
96rem, e a nossa, de 1240px, perdia em tela larga. A home ficaria mais larga
que em produção sem erro aparecer. Com `site` por último, o CSS que está no ar
sempre vence. **Toda classe portada de produção entra em `site`, não em
`components`.**

**5. `Inter Tight` fica carregada e sem uso, como está hoje.** O site atual
declara `--font-display: 'Inter'` mas carrega `Inter Tight` no `<link>` e não
usa em lugar nenhum. Mantido igual, porque é o comportamento validado em
produção, e mexer nisso mudaria a aparência de todo heading do site. É um
requisito de "não quebrar", não um bug para consertar por conta própria.
**Pendente de decisão do Guilherme:** ou tira o `<link>`, que economiza
download, ou passa a usar a fonte nos headings, que muda o visual.

**6. `/v2` também fora do sitemap.** O plano só pedia `/lp/*` fora. Mas `/v2` é
a segunda proposta visual, existe só para comparação, e indexar duas versões da
mesma home cria conteúdo duplicado contra o próprio domínio.

**7. `AGENTS.md` dentro de `juria-site-astro/`, e o `CLAUDE.md` symlink fora.**
O scaffold do Astro cria os dois, sendo o segundo um symlink para o primeiro. O
`CLAUDE.md` da raiz já avisa que symlink não commita direito, então tirei. No
`AGENTS.md` ficaram as regras que valem dentro daquela pasta, porque é o que
uma sessão nova lê ao trabalhar ali.

### Fase 1

**8. Conferência automática dos dados, em `npm run dados:conferir`.** Não estava
no plano. Preço errado no site não quebra build, não aparece no console e não
falha teste: aparece no cliente lendo a página, que foi o que aconteceu com a LP
em R$ 199 e "14 dias". São 20 asserções sobre preço, limite, nome de plano
aposentado, trial, o escopo do Solo e os IDs de tracking. `npm run conferir`
roda ela junto com o `astro check`. **Rodar antes de cada commit das fases
seguintes.**

**9. A conferência achou um erro na fonte da verdade, e ele foi corrigido.** A
seção 4.2 do `planos-e-creditos.md` dizia que o degrau Solo para Plus abre
**dez** recursos. São **nove**: dos dez itens que o Solo não tem, migração
assistida também não vem no Plus, só chega no Max. A 4.1 estava certa, a 4.2
não. Corrigido nos dois lugares, com nota explicando. O erro apareceu porque o
código deriva as duas listas da tabela em vez de repetir o número escrito.

**10. `Migração assistida` continua classificada como funcionalidade**, igual à
tabela oficial, mas o texto do degrau Plus para Max passou de "nenhuma
funcionalidade nova" para "nenhum recurso novo do produto". É serviço de
entrada, não função do sistema, e é o único item da tabela que separa os dois
planos. A frase antiga se contradizia com a própria tabela.

**11. Data impossível corrigida na fonte da verdade.** O `planos-e-creditos.md`
dizia que a Mobiletec confirmou os limites do trial em 30/09/2026, que é
amanhã. A confirmação foi em 29/09. Trocado.

### Fase 2

**12. O espelho de produção deste repositório está defasado, e isso mudou o
método da fase.** `clients/juria/lps/institucional/index.html` é anterior a
29/09: R$ 199, "14 dias", Basic/Pro/Enterprise. Descoberto comparando o FAQ dele
com o `faq.ts` da fase 1, que já traz o texto corrigido. Como a versão certa vive
no `juria-lps`, que não está clonado, a transcrição da copy passou a seguir três
regras, escritas no cabeçalho de `src/data/home.ts`: número errado sai de
`src/data/`; afirmação errada vira `{{ TODO }}`; número que o próprio markup
contradiz passa a ser derivado.

**13. O porte virou script, `npm run portar`.** Eram 5.349 linhas de CSS, 748 de
JS e 1.315 de markup. Copiadas à mão, elas divergem da fonte no primeiro ajuste
que alguém fizer, e ninguém descobre, porque CSS errado não quebra build.
`npm run portar:conferir` compara byte a byte e responde "isto ainda é o que está
no ar?" com sim ou não. Entrou no `npm run conferir`.

**14. Divergência de produção só em `src/styles/ajustes.css`.** Consequência do
item anterior: se os arquivos portados são intocáveis, precisa existir um lugar
para o que muda. É esse, e cada regra lá diz o que mudou e por quê. Ganho: a
lista completa de diferenças contra o site no ar cabe num arquivo de 120 linhas,
em vez de estar espalhada por 5.349.

**15. A grade de preços passou de três para quatro colunas.** Produção tem
`repeat(3, 1fr)` porque eram três planos. Não é escolha de layout: a seção 5.3 do
`planos-e-creditos.md` diz que a tabela precisa de quatro colunas. Escada nova:
4 colunas, 2x2 entre 881 e 1080px, 1 no celular.

**16. O selo do card passou a vir do dado.** Produção escrevia
`content: 'Mais escolhido'` dentro do CSS. Com o texto do selo morando no CSS ele
podia divergir da tela do produto, que é o erro que a fase 1 existe para impedir.
Agora é `attr(data-selo)`, lendo o mesmo valor de `planos.ts`.

**17. ⚠️ INVENTEI UM TRATAMENTO VISUAL, E É O ÚNICO.** O Ilimitado tem selo na
tela do produto, "Ilimitado", e não é o card destacado. Produção não tinha esse
caso, porque o selo era efeito colateral do `.featured`. Fiz o selo do card não
destacado com a mesma geometria e cor invertida: contorno ciano sobre branco, em
vez de ciano cheio, para não disputar atenção com o "Mais escolhido". **A
alternativa era não mostrar o selo do Ilimitado**, que perde informação que está
no produto. Se preferir assim, é apagar um bloco do `ajustes.css`.

**18. `mockup-nav.js` ficou fora da página.** É o `<script
id="mockups-novos-v2-scripts">`, 239 linhas. Os três IIFE dele buscam
`#mg-gestao`, `#mg-pipeline` e `#mg-precedentes` sem testar o resultado, e
**nenhum desses ids existe no HTML**, nem os elementos que eles animam. É sobra
de uma versão anterior do mockup. **Hoje, no site que está no ar, ele levanta um
TypeError a cada carregamento de página.** Fica portado, para o registro, e fora
da página, porque "sem erro no console" é item do checklist. A conferência falha
se alguém importar de volta.

**19. O contador do tour passou a ser derivado.** A coluna "Operação" anuncia
"11 funcionalidades" em produção e lista 12. O componente conta `itens.length`,
então o número não pode mais divergir. Mesma disciplina que achou o "dez
recursos" da fase 1. **O site novo mostra 12, e produção mostra 11.**

**20. Os dois `mailto:` viraram botão de WhatsApp sem link.** O brief manda
trocar e manda pedir o número antes. Enquanto `site.whatsapp.numero` for nulo, o
botão é um `<span>` apagado, não um link morto. Sai sozinho quando o número
chegar.

**21. O logo da navbar aponta para `/`, não para `#`.** Em produção é `#` porque
o site é um one-pager. Com onze páginas, o logo precisa levar para a home. Na
própria home o comportamento é o mesmo de antes.

**22. O ano do rodapé é calculado.** Produção tem "© 2026" fixo, que envelhece
sozinho em 1º de janeiro.

**23. Guardei uma conferência de navegador, `scripts/conferir-navegador.mjs`.**
Roda em desktop e celular contra o `dist/` e confere o que o build não vê: o
mockup montou, a aba troca a tela, o FAQ abre, a UTM sobrevive, as seis âncoras
existem, a grade muda de colunas e o console fica limpo. Foi ela que pegou os
itens 18 e 24. Não virou dependência do projeto: roda a mão, com
`npm i --no-save playwright`.

**24. Um bug que eu mesmo introduzi e corrigi antes de commitar.** A primeira
versão do `ajustes.css` declarou as quatro colunas sem media query, contando que
o `@media (max-width: 880px)` de produção continuasse ganhando. Não continua:
`ajustes.css` entra depois na mesma layer, então o celular ficou com quatro cards
espremidos. O build passou limpo. Agora cada regra vive dentro da sua faixa, com
`min-width`, e a ordem dos arquivos parou de decidir o resultado.

### Fase 3

**25. A fase 3 já estava quase pronta ao fim da fase 2, e isso é do plano, não
atalho.** O critério da fase 2 é "home renderiza só com componentes", o que
obriga a home a existir. Sobrou para a fase 3 o que é dela: provar que não tem
diferença visual perceptível, e que as seis âncoras rolam para o lugar certo.

**26. O diff visual mede cada seção ISOLADA no topo do body.** A primeira
medição comparou as seções onde elas caem na página, e acusou de 0,3% a 1,5% de
pixels diferentes em seções cujo texto é idêntico, inclusive o rodapé. A imagem
do diff mostrou o padrão: linha sim, linha não. É deslocamento de sub-pixel. A
home nova é legitimamente mais alta (o bloco `{{ TODO }}`, quatro cards de preço
em vez de três), e a altura acumulada empurra tudo abaixo para outro offset, o
que faz o texto anti-aliasar diferente. Escondendo os irmãos de primeiro nível,
os dois lados renderizam em Y=0 e o número vira **0,000%**.

Para não confundir de novo: o piso de ruído foi medido, comparando produção com
ela mesma, e é 0%. Então 0,3% não era ruído, era offset, e o método é que estava
errado. `scripts/diff-producao.mjs` já nasce com o método certo e com o porquê
escrito.

**27. Confirmei por geometria, não só por pixel.** 107 elementos de 5 seções,
comparando posição, tamanho, `font-size`, `line-height`, `font-weight`, `color` e
`letter-spacing` contra produção. Zero diferença acima de 1px ou de estilo. Um
número de pixel sozinho não distingue "mudou o layout" de "mudou o anti-aliasing",
e essa é exatamente a dúvida que o critério da fase precisa resolver.

**28. A lista de diferenças esperadas está dentro do script.** `hero`,
`recursos`, `precos`, `faq` e `cta` **têm** que divergir, porque o espelho é
anterior a 29/09. Cada uma está na constante `ESPERADO`, com o motivo. Divergência
fora dessa lista faz o script sair com erro. Sem isso, "5 seções diferentes" não
diz se o porte está certo ou quebrado.

### Fase 4

**29. As dez páginas saem de uma rota só, `[slug].astro`, e de um arquivo de
dados.** O esqueleto das dez é o mesmo e o que muda é conteúdo, que já mora em
`src/data/paginas.ts`. Dez arquivos quase iguais divergem no primeiro ajuste que
alguém faz em um deles. A de preços tem conteúdo próprio, os quatro cards e a
tabela comparativa, e entra pelo slot.

**30. Página nova carrega `styles/pagina.css`, não `home.css`.** Ela usa o
cabeçalho, o rodapé, o botão e a tipografia do site, que são classes de produção,
então carrega o `site.css` portado. Mas não carrega os três arquivos de mockup,
que são 3.168 das 5.349 linhas e servem a uma seção que só existe na home.

**31. As três páginas de comparativo não afirmam nada sobre o concorrente.**
Toda seção que falaria do ADVBox, do Astrea ou do Projuris é uma pergunta
marcada, com o que precisa ser apurado na página pública deles. As seções que
falam do JurIA já vêm respondidas, porque essas eu confiro na fonte da verdade.
Escrever "o ADVBox não tem X" sem fonte é risco jurídico e de reputação, e o
brief chama isso de atenção.

**32. Onde eu tinha fonte, a resposta já foi escrita.** Nove seções nasceram
respondidas, e todas saem de `planos-e-creditos.md`: o que o Solo não tem, o teto
de IA por plano, o custo em créditos de jurimetria, dossiê e monitoramento, os 50
créditos grátis, BYOK do Plus em diante. O resto é `{{ TODO }}`. Entregar
esqueleto não é motivo para deixar em branco o que dá para conferir.

**33. Uma das perguntas marcadas é sensível, e está sinalizada.** "Os dados do
escritório treinam a IA?" é das primeiras que um sócio faz, e eu não tenho a
resposta. Precisa de confirmação da Mobiletec, por escrito, antes de qualquer
frase entrar ali.

**34. `/lp/exemplo` nasce com `noindex, nofollow` E fora do sitemap.** Os dois,
porque um só não basta: sem o `noindex` o buscador indexa mesmo sem sitemap, e
sem o filtro a LP aparece na lista de URLs que o Search Console recebe. O
tracking está lá também, que é item do checklist: LP de campanha sem GTM é
campanha sem medição.

**35. O blog nasce vazio, e continua vazio.** Coleção de conteúdo configurada,
rota de post, índice, breadcrumb e schema de frontmatter prontos. Zero post, que
é o que o brief manda. O índice mostra estado vazio de verdade, não post
inventado para a página não ficar feia. O primeiro markdown em
`src/content/blog/` vira página sem mexer em código.

O build avisa que a coleção está vazia. É esperado, e o aviso some com o primeiro
post.

**36. Guardei `scripts/conferir-paginas.mjs`, 13 conferências sobre o HTML
servido.** Rota existe, um H1 por página, title e description únicos, canonical
absoluto apontando para a própria página, `/lp/*` fora do índice e do sitemap,
GTM em toda página com o Consent Mode antes, nenhum Pixel ou GA4 solto no HTML,
nenhum `mailto:` e nenhum preço aposentado. Erro de SEO técnico não quebra build
e não aparece na tela: aparece no Search Console, semanas depois.

**37. Essa conferência achou uma coisa, e eu não consertei de propósito.** O link
"Entrar" não repassa UTM. **Produção também não**: o atributo `data-forward-utm`
está nos seis links de `/register` e em nenhum de `/login`. Mantive igual, porque
mexer em tracking que está rodando é justamente o que o brief proíbe, e a
conferência passou a exigir o atributo só nos links de cadastro, que são os que
levam a UTM até o `ViewRegister`. A pergunta está abaixo.

**38. `zod` virou dependência declarada.** O `z` reexportado por `astro:content`
está deprecado no Astro 7, e usá-lo enchia o `astro check` de avisos. Importar de
`zod` direto resolve, e declarar a dependência evita depender de resolução
transitiva do próprio Astro.

### Fase 5

**39. A home passou a ter um H1, e produção continua com três.** Os dois extras
eram "Meu Dia" e "Painel Gerencial", títulos de tela **dentro** do mockup. A
troca de tag acontece em `components/Mockup.astro`, na hora de injetar o markup,
e não no arquivo portado, que segue byte a byte igual à fonte. São `div`, e não
`h2`: dentro da demonstração aquilo não é heading da página, e promover para h2
só trocaria um problema de hierarquia por outro.

**40. Essa troca quase passou com o mockup 12px mais alto.** O `line-height` dos
dois títulos não vinha de `.jm-block h1`, vinha da regra global `h1, h2, h3, h4`
do site, que um `div` não pega: ele herda o 1.6 do body. O diff contra produção
acusou 2% de pixels diferentes na seção do mockup, e comparar o estilo computado
mostrou que `line-height` era a única das onze propriedades que divergia. Com a
linha no `ajustes.css`, voltou a 0,000%. Sem o diff, isso entraria e ninguém
veria.

**41. O JSON-LD saiu inteiro de `src/data/`.** Produção ainda anuncia Basic 199,
Pro 499 e Enterprise 1299 em dado estruturado, que é a tabela de antes de 29/09.
Preço errado ali vira preço errado no resultado de busca e na resposta de IA, sem
ninguém ver. Agora são quatro `Offer`, um por plano, dentro de um
`AggregateOffer`, e cada um com `priceSpecification` mensal, porque o plano anual
saiu do catálogo e R$ 69 sem unidade pode ser lido como valor único.

**42. `FAQPage` só onde as perguntas aparecem na tela, e `BreadcrumbList` só em
página interna.** Declarar FAQPage sem FAQ visível contraria a diretriz do
Google. A home não recebe trilha porque é a raiz. A conferência exige as duas
coisas, nos dois sentidos.

**43. A trilha estruturada tem Início e a própria página, e pula o grupo.**
"Produto" e "Comparativos" aparecem na trilha visual, mas não são página: não têm
URL própria. Item de `BreadcrumbList` com a mesma URL do item seguinte é trilha
malformada, e foi o que a primeira versão fez.

**44. `llms.txt` é gerado, não escrito.** É o arquivo do site com maior densidade
de número de plano por linha. Escrito à mão, vira a terceira cópia dos preços, e
foi preço repetido em três lugares que deu o retrabalho de 29/09. `npm run llms`
gera de `src/data/` e `npm run llms:conferir` falha se o arquivo em disco estiver
velho. Entrou no `npm run conferir`.

**45. O `llms.txt` diz explicitamente o que o Solo NÃO tem.** O bloco está escrito
em forma de correção, e de propósito: "o Solo tem quatro recursos, e não todos"
é exatamente o que um modelo tende a assumir errado ao resumir um plano de
entrada, e é o erro que a LP teve em cinco lugares. Dito assim, quem extrai o
texto extrai a ressalva junto.

### Fase 6

**46. O risco que o brief apontava já estava coberto, e agora é conferido.** O
bloco de Consent Mode vem antes do snippet do GTM, em todas as 13 páginas,
inclusive em `/lp/`. Isso nasceu no `BaseLayout` na fase 2, mas ninguém tinha
provado: `conferir-paginas.mjs` agora verifica a ordem página por página,
comparando a posição dos dois no HTML servido. Invertido, as tags de
inicialização já foram avaliadas quando o default chega, e disparam mesmo para
quem se opôs.

**47. Nenhum evento novo, e `ClickTrial` não voltou.** O site instala só o GTM.
Uma das conferências falha se aparecer `fbq(` ou `gtag('config'` no HTML: seria
disparo duplicado com o que já roda dentro do container.

**48. ⚠️ A UTM morria na navegação interna, e isso é problema que a migração
criou.** O site atual é um one-pager: navegação interna é rolagem, e a query
string nunca se perde. `forward-utm.js`, que é o script de produção, lê
`window.location.search` e desiste se estiver vazio, o que basta numa página só.

Com onze páginas deixa de bastar. Quem cai em `/?utm_source=meta` e clica em
"Preços" chega em `/precos` sem query, e dali o link de cadastro sai limpo. A
campanha perde a atribuição no `ViewRegister`, que é a conversão que a Meta
otimiza. É item da seção 9 do brief, e não teria aparecido em teste nenhum da
home sozinha.

**49. A solução guarda a UTM em `sessionStorage`, e não propaga na URL.**
Propagar encheria o site de URLs com parâmetro, cada uma uma variação da mesma
página para o buscador. O canonical resolveria, mas é sujeira que não precisa
existir. Em `sessionStorage` a UTM viaja invisível e morre quando a aba fecha,
que é o tempo de vida certo para atribuição de sessão. `gclid`, `fbclid` e
`msclkid` viajam junto: valem tanto quanto a UTM.

**50. O script novo roda DEPOIS do de produção, e isso é a proteção.**
`forward-utm.js` continua fazendo o trabalho dele quando a query está na URL,
exatamente como hoje. `utm-persistente.js` só cobre o caso novo, a página sem
query. Se o novo quebrar, o comportamento que está no ar continua de pé. Ele mora
em `src/scripts/novos/`, separado dos portados, para ninguém confundir código
nosso com cópia de produção.

**51. Entrada nova vence UTM guardada.** Quem volta pelo segundo anúncio é
creditado ao segundo, não ao primeiro. Tem conferência para isso, porque o
contrário é o erro silencioso óbvio dessa abordagem.

### Fase 7

**52. ⚠️ AQUI EU DESENHEI, e é a fase em que mais decidi sozinho.** Você pediu
duas propostas variando só hero e seção de preços, sobre a mesma identidade. As
duas escolhas abaixo são minhas, e é o que você precisa julgar.

**53. Hero B inverte a ordem de leitura.** A proposta A abre com o selo de
autoridade ("Construído pela Mobiletec, 25 anos de software house") e desce até o
título. A B põe o título primeiro e maior, e a autoridade logo abaixo, em pílula.
**A aposta:** em tráfego pago, a primeira coisa lida tem que ser a promessa, não
quem fez. Quem chega pelo anúncio ainda não sabe que a Mobiletec importa.

O segundo caminho, "Ver tour rápido", virou link de texto em vez de botão. Na A
são dois botões com o mesmo peso, e o objetivo da página é um só.

O fundo é navy escuro com uma aurora ciano que respira em 14s. É o movimento da
ADVBox: longo, discreto, e nada piscando.

**54. Preços B separa por forma de compra, não por preço.** A A põe os quatro
planos em quatro colunas iguais. Em 1440px isso dá 290px por card, e o Ilimitado,
que não se compra pelo site, ocupa um quarto da largura disputando atenção com o
Max, que é o plano que o produto marca como "Mais escolhido". A B põe Solo, Plus
e Max em três colunas mais largas, e o Ilimitado numa faixa embaixo. **A aposta:**
cada card de autoatendimento respira, e o Ilimitado deixa de ser card de preço
para virar o que ele é, uma conversa.

A divisão sai de `contatoComercial`, que é campo do dado, e não de nome escrito.
Plano que mudar de forma de venda muda de lugar sozinho.

**55. Copy e dados idênticos nas duas.** As duas leem `src/data/home.ts` e
`planos.ts`. Comparar duas propostas com copy diferente não compara nada.

**56. O movimento não pode ser necessário para ler a página, e isso deu
trabalho.** `prefers-reduced-motion` corta a duração da animação para 0,01ms. Se
o estado inicial (`opacity: 0`) estivesse numa regra normal, quem pede menos
movimento veria o hero em branco, porque a animação que devolveria a opacidade
não roda. Por isso o `opacity: 0` vive **dentro** do keyframe, com
`animation-fill-mode: both`. Conferido nos dois modos: com movimento reduzido,
título, selo e garantias saem com `opacity: 1`.

**57. `/v2` tem tarja na tela dizendo que é proposta.** Mais o `noindex` e o
filtro do sitemap, que já estavam desde a fase 0. Uma aba esquecida aberta não
pode ser confundida com a home.

### Fase 8

**58. O relatório está em [[04-clientes/juria/relatorios/2026-09-30-relatorio-decisoes|RELATORIO-decisoes.md]].** Este
arquivo aqui é o log de execução, com o detalhe de cada decisão. O relatório é o
resumo para aprovar ou mandar refazer, e abre com as três coisas que mais
precisam do seu olho.

**59. Seis itens do checklist da §9 dependem de preview, e eu não marquei nenhum
deles como feito.** São Meta Pixel no Pixel Helper, GA4 no DebugView, Rich
Results Test, Lighthouse mobile, mobile real, e a chegada da UTM ao GA4. Todos
precisam de URL pública, e esta execução não faz deploy. Marcar como verde o que
não foi verificado seria o pior tipo de entrega: a que parece pronta.

Os outros 17 estão verdes, e cada um tem como foi verificado escrito ao lado.

**60. O que dava para verificar sem deploy, eu verifiquei com script, não com
leitura.** São 104 conferências automáticas no total: 28 de dados, 21 de página,
44 no navegador e 11 de porte. Todas rodam de novo com quatro comandos, que estão
no fim do relatório. Revisão por leitura não pega `line-height` errado em 5.349
linhas de CSS portado, e foi exatamente isso que quase passou na fase 5.

### Reconferência de 30/09, 09h20

**61. Não abri fase 9, e não refiz nenhuma fase.** O log dizia oito de oito, e o
disco confirmou. O pedido era continuar da primeira fase não concluída, e não
existia uma. Em vez de inventar escopo, gastei a janela provando que o que está
commitado funciona a partir de um clone limpo, que é a única coisa que nenhuma
execução anterior podia afirmar sobre si mesma.

Rodei `npm ci` num container novo e as quatro suítes: **104/104 passaram** (28 de
dados, 21 de página, 44 no navegador, 11 de porte), mais `astro check` com 0
erro, 0 aviso e 0 dica em 51 arquivos, e o build das 14 páginas. O
`diff-producao.mjs` fecha com as mesmas cinco divergências esperadas e as seis
âncoras em y=0. Nada do que está escrito neste arquivo se mostrou otimista.

**62. Fechei o item do Lighthouse, porque ele não dependia de preview.** A fase 8
marcou "Lighthouse mobile" como ⏳ com a justificativa "não roda com Google Fonts
e GTM bloqueados". Isso estava errado: o Lighthouse roda contra o `npm run
preview` local, e recurso externo bloqueado não impede a medição. Rodei nas
quatro rotas, em emulação mobile:

| Rota | Performance | SEO | Acessibilidade | Boas práticas |
|---|---|---|---|---|
| `/` | 97 | 100 | 92 | 96 |
| `/precos` | 98 | 100 | 93 | 96 |
| `/blog` | 98 | 100 | 88 | 96 |
| `/lp/exemplo` | 98 | 66 | 88 | 96 |

O critério do brief é Performance ≥ 90 e SEO = 100, e as indexáveis passam nos
dois. O 66 do `/lp/exemplo` é o `noindex` que ele tem de propósito: a única falha
é `is-crawlable`. **Restam 5 itens ⏳, não 6**, e os cinco precisam de coisa que
não existe sem deploy: Pixel Helper, DebugView do GA4, a chegada da UTM ao GA4,
o Rich Results Test e um aparelho de verdade.

**63. Três achados de acessibilidade, e não consertei nenhum de propósito.** O
brief não pede nota de acessibilidade, e o Lighthouse mediu junto. Os três são
pergunta para você, abaixo, e não bug da migração: os três existem igual no site
que está no ar, porque saem da identidade ou do markup portado byte a byte.
Consertar contraste de marca ou editar markup portado na manhã da entrega, sem
você, seria exatamente o chute que este arquivo manda não dar.

O que me fez parar no `<main>`, que é o único dos três que é nosso: a home e a
`/v2` não têm a tag e as páginas novas têm. Envolver as seções da home num
`<main>` muda a estrutura de filhos diretos do `body`, que é justo onde o
`diff-producao.mjs` se apoia para medir seção isolada, e onde o CSS de produção
pode ter seletor de filho direto. É mudança de 30 segundos com revalidação da
fase 3 inteira atrás. Não na manhã da entrega.

**64. Dois links quebrados por caixa, e esses eu consertei.** O ESTADO e o PLANO
apontavam para `BRIEF-migracao-juria-astro.md`, e o arquivo é
`brief-migracao-juria-astro.md`, minúsculo. Em Linux o link simplesmente não
abre, e ele é o passo 2 das instruções de retomada deste arquivo: toda sessão
nova tropeça nele antes de ler o brief. Corrigido nos dois. É erro de digitação
com consequência, não decisão de conteúdo.

### Reprodutibilidade (30/09, 11h15)

**65. Não abri fase nova, e reconferi do zero em vez disso.** O log já trazia as
oito fases concluídas e uma reconferência. Sobraram três tipos de coisa, e
nenhum é meu: os 5 itens ⏳ do checklist, que precisam de preview na Vercel, e o
brief proíbe deploy; as 10 perguntas desta seção, que são decisão sua; e o
`<main>` da home mais os quatro `aria-label` do mockup, que a decisão 63 deixou
esperando sua autorização porque mexem em markup portado byte a byte. Inventar
uma nona fase para ter o que mostrar seria o chute que este arquivo proíbe.

O que fiz então foi fechar a única lacuna de verificação que ainda existia. As
sessões anteriores rodaram as conferências com `node_modules` já instalado. Neste
ambiente a pasta não existia, então o `npm ci` montou tudo do lockfile, como faria
qualquer máquina nova ou a Vercel no primeiro build. Passaram: `astro check` sem
erro, build com as 14 páginas, 28 conferências de dados, 11 blocos de porte
idênticos a produção, o llms.txt em dia, 21 conferências de página e 44 no
navegador. **105 no total, nenhuma falha.** Vale como prova de que o cutover não
depende de nada que só exista na máquina que escreveu o código.

Um detalhe do ambiente, para a próxima sessão não se assustar: o Playwright não é
dependência do projeto, de propósito, e a conferência de navegador pede
`npm i --no-save playwright` antes de rodar. Está documentado no cabeçalho do
`conferir-navegador.mjs` e funcionou sem ajuste.

---

### Correções do Guilherme, 30/09

**66. Sincronizei o espelho de produção, e essa era a raiz.**
`clients/juria/lps/institucional/index.html` estava **anterior à
reestruturação de 29/09**: trazia "14 dias" nove vezes, Basic, Enterprise, e
nenhum Solo. É o arquivo que `portar-producao.mjs` usa como fonte e contra o
qual a conferência de porte compara, e foi dele que a copy da home foi
transcrita. A sessão da madrugada só tinha este repositório, então portou,
transcreveu e conferiu tudo contra um retrato velho do site. Passava limpo
porque a conferência media contra a mesma coisa errada. Copiado de
`~/Desktop/juria-lps/institucional/index.html`, e são 120 linhas de diferença,
todas produção sendo mais nova. Nenhuma era customização do espelho.

**67. As faixas de linha do porte viraram âncoras.** Com o espelho 32 linhas
mais longo, todas as faixas fixas do `portar-producao.mjs` escorregaram: o
porte passou a levar a tag `<style>` para dentro do CSS e a perder a última
linha de cada bloco. Agora cada bloco se identifica por `id` ou por uma marca,
um trecho que só existe dentro dele, e os limites são achados a cada rodada. Se
uma marca deixar de casar, ou casar em dois blocos, o script **para com erro**
em vez de portar coisa errada. Foi o que ele fez na primeira tentativa, quando
minha marca do `mockup-fit.js` usava aspas simples e a fonte usa duplas.

**68. A grade de preços passou a ter duas linhas, e o ajuste que forçava quatro
colunas saiu.** Produção já tinha a opção B que você aprovou em 29/09:
`.pricing-grid` com Solo e Plus, `.pricing-grid-sec` com Max e Ilimitado, menor
e mais apagada. O espelho velho não tinha esse CSS, então a sessão da madrugada
viu `repeat(3, 1fr)` com quatro cards e escreveu um ajuste levando a grade para
quatro colunas. Com o espelho em dia, o CSS certo entrou pelo porte e o ajuste
virou estorvo. O item 1 do `ajustes.css` foi removido, e ficou só o registro do
porquê.

**69. Separei `enfase` de `destaque` no dado dos planos.** Produção prende o
texto do selo à classe `featured` e, com isso, escreve "Mais escolhido" no
Plus, contrariando a tela do produto e a sua decisão de 29/09. Os dois viraram
campos distintos: `destaque` é o selo do produto, que está no Max, e `enfase` é
qual card a página empurra, que é o Plus. Segui você e o produto. É a única
diferença visível contra o site no ar na seção de preços, e está na pergunta 11.

**70. Texto navy no botão primário, em vez de escurecer o ciano.** As duas
saídas passam na WCAG. Navy sobre o ciano dá 6,21:1, e no hover 7,90:1, sem
mexer numa cor de marca sequer. Escurecer o ciano até o branco passar exigiria
tirar 28% da luminância, mudando o botão, o preenchimento e todo o resto.
Para o `eyebrow`, que é ciano sobre fundo claro, criei `--cyan-texto`
(`#0E7F8D`, 4,57:1), usado **só** onde ciano é texto sobre claro. Detalhe na
pergunta 9.

**71. O card Ilimitado deixou de repetir a si mesmo.** O componente derivava
quatro linhas de volume, "Usuários ilimitados / Clientes ilimitados /
Processos ilimitados / Armazenamento ilimitado", e logo abaixo vinha o bullet
do produto dizendo "Usuários, clientes, processos e storage ilimitados".
Produção colapsa as quatro numa linha só. Passei a colapsar também, com a
frase de produção palavra por palavra, e só quando os quatro limites são
ilimitados, que é o caso de um plano só.

### Reconferência em ambiente limpo, 01/10

**72. A conferência do cabeçalho media durante uma rolagem animada, e eu
troquei o jeito de medir, não o site.** Em ambiente limpo, com `npm ci` do zero,
a conferência `cabecalho escuro sobre o hero, claro sobre o canvas` **falhava no
celular em toda rodada**, e passava no desktop em toda rodada. O site está
certo: o cabeçalho escurece sobre o hero nos dois, e eu confirmei isso medindo
direto no navegador.

Quem estava errado era o medidor. A home declara `scroll-behavior: smooth`,
então o `scrollTo(0, 0)` do script é **animado**, e ele media 350ms depois do
salto, com a página ainda no meio do caminho:

| Perfil | Onde a página estava aos 350ms | O que havia sob a faixa | Resultado |
|---|---|---|---|
| desktop | scrollY 5.533 de 11.354 | cápsula escura | passava, pelo motivo errado |
| celular | scrollY 7.596 de 16.259 | canvas claro | falhava, pelo motivo errado |

A página do celular é cerca de 5.000px mais alta, então a mesma animação demora
mais e termina mais longe do topo. Não era instabilidade de máquina lenta: é
determinístico, e foi por isso que apareceu agora e não na lapidação.

A segunda metade da conferência passava igualmente pelo motivo errado. Ela
esperava a classe **desaparecer**, e em pleno voo sobre o canvas claro ela já
estava ausente: a asserção se satisfazia antes de a rolagem chegar ao destino.

**O conserto:** as duas rolagens passaram a usar `behavior: 'instant'`, e as
duas medições passaram a exigir, na mesma condição, que a rolagem **tenha
chegado** (`scrollY === 0`, e tolerância de 2px no destino do canvas) além do
estado da classe. Com isso a conferência volta a medir o
`IntersectionObserver`, que é o que ela existe para medir.

**Conferi que a asserção continua com dentes**, em vez de só ter ficado mais
fácil de passar: injetei uma mutação no `revelar.js` trocando o
`classList.toggle` por `false` fixo, rebuildei, e a conferência falhou **nos
dois perfis**. Revertida a mutação, voltou a 92/92. O arquivo mexido é só
`scripts/conferir-navegador.mjs`. **Nenhuma linha do site mudou nesta rodada.**

**Por que isso não é maquiagem de número verde:** a conferência antiga dava
`true` no desktop sem nunca ter olhado o cabeçalho no topo da página. O ganho
não é o 92/92, é que agora os dois perfis medem a coisa que o nome da
conferência promete.

### Conserto da conferência de produção, 01/10

**73. O `diff-producao.mjs` não rodava desde a fase 3, e eu consertei o script,
não o site.** A rotina do `AGENTS.md` manda rodar seis comandos antes de fechar
fase. O sexto compara a home nova com o espelho de produção em três eixos, texto,
pixel e âncora, e a lista `ESPERADO` dentro dele diz quais seções **têm** que
divergir. Essa lista foi escrita na fase 3, quando a home era porte de produção.

Em 30/09 a lapidação reestruturou a home em doze blocos, a seu pedido. A regra do
`AGENTS.md` é explícita: "Mexeu na home de propósito? Atualize a lista no mesmo
commit." Não foi atualizada. O script passou a acusar 25 divergências, e em vez
de alguém ler, ele saiu da rotina: as rodadas seguintes contaram 146 e depois 156
conferências, números que **não incluem este script**. Conferência que falha
sempre ensina a pular, e foi o que aconteceu.

O que eu mudei:

| Era | Virou |
|---|---|
| `section.mobiletec`, que a lapidação renomeou | `section.autoridade`, com o seletor de produção à parte em `selVelho` |
| `problemas` casando na primeira seção sem `id`, que agora é a de autoridade | `section.problemas` |
| `#muda` e `#seguranca` invisíveis para o script | seções `nova`, sem equivalente em produção para comparar |
| seletor que não casa lendo texto vazio, e vazio batendo com qualquer `ESPERADO` | seletor que não casa **derruba** a conferência, nos dois eixos |
| `ESPERADO` descrevendo a home da fase 3 | uma entrada por bloco, citando o bloco do `ESTRUTURA-home.md` que autoriza a divergência |

**74. Separei "divergência aprovada" de "divergência sem decisão", porque
misturar as duas é que faz conferência virar enfeite.** Agora há três
classificações, e não duas: `esperado` é divergência que você já aprovou,
`pend` é divergência conhecida que ainda espera resposta sua, e `X` é regressão.
A `pend` **não derruba** a rodada, mas sai num resumo no fim, com o número da
pergunta. Assim o item não bloqueia o trabalho e também não desaparece, que era
a escolha ruim entre deixar vermelho para sempre ou esconder dentro do
`ESPERADO`.

**75. Depois da lapidação, o eixo de texto e o de pixel sobraram com uma seção
só que ainda prova algo por comparação, e eu escrevi isso no cabeçalho do script
em vez de fingir o contrário.** A home é design novo: ela não deve mais parecer
com o site no ar. Das treze seções, onze divergem por decisão sua, duas são
novas, e só o `footer` ainda bate (0,000%). Quem garante a fidelidade do que
**continua** portado de produção, que é CSS, JS e o markup do mockup, é o
`npm run portar:conferir`, byte a byte, e não este script. O eixo de âncoras
continua valendo inteiro, e é ele que achou o defeito da decisão 76.

**76. O conserto do eixo de âncoras achou um defeito real no site, e esse eu
consertei no site.** No celular, entrar por `/#precos` deixava o topo da seção
**1px atrás do cabeçalho**. No desktop a folga era de 5px, onde o CSS prometia
16px.

A causa é um token que a lapidação deixou para trás. O recuo era
`calc(var(--nav-altura) + 16px)`, e `--nav-altura` (92px no desktop, 70px no
celular) **não é a altura da barra**: é a altura que o hero usa para passar por
baixo dela. A barra de verdade, depois que o cabeçalho virou pílula flutuante,
mede 103px e 87px, medidos no estilo calculado. Então o recuo dava 108px e 86px,
contra uma barra de 103px e 87px.

| Perfil | Barra real | Recuo antigo | Folga | Recuo novo | Folga |
|---|---|---|---|---|---|
| desktop | 103px | 108px | 5px | 120px | 17px |
| celular | 87px | 86px | **−1px** | 104px | 17px |

Criei `--ancora-recuo` em vez de corrigir o `--nav-altura`, porque o
`--nav-altura` também posiciona o hero e três elementos sticky: mexer nele
move layout que está certo. Nenhuma outra regra mudou.

**77. Conferi que a asserção nova tem dentes, em vez de só ter ficado mais fácil
de passar.** O eixo de âncoras exigia o topo da seção em `y=0`, o que nesta home
é justamente o defeito. Passou a exigir três coisas: que a página tenha rolado,
que a seção pare onde o CSS declara, e que ela pare **abaixo da barra medida no
navegador**. A terceira é a que não depende do valor do CSS, e foi testada com
três mutações:

| Mutação | Esperado | Resultado |
|---|---|---|
| recuo de volta para `--nav-altura + 16px` | falha só no celular | 6 falhas, exatamente o defeito original |
| `--ancora-recuo: 0` | falha nos dois perfis | 12 falhas, não passou "zero contra zero" |
| seletor de seção renomeado, como aconteceu com `.mobiletec` | falha nos dois eixos | 3 falhas, onde antes era um `?` silencioso |

Todas revertidas depois. **A pergunta 12 nasceu desta rodada, e eu não a
chutei:** é copy de CTA, e está abaixo.

### A conferência de dados passou a ler a fonte, 01/10

**78. O `conferir-dados.mjs` jurava conferir contra a fonte da verdade e nunca
abria o arquivo. Consertei o medidor, não o site.** O cabeçalho dele dizia, desde
a fase 1, "confere os dados de `src/data` contra a fonte da verdade,
`clients/juria/comercial/planos-e-creditos.md`". Ele nunca leu esse arquivo. O
que ele lia era o espelho de produção e o `mockup.html`, e as asserções de preço,
limite, selo, CTA e trial tinham os valores **digitados no próprio corpo**:

```js
assert.equal(planoPorId('plus').preco, 159);   // como estava
```

Isso é cópia da fonte, não derivação dela. A conferência comparava `src/data`
contra a memória de quem escreveu o script, e os dois concordarem não diz nada
sobre o markdown. **Conferi à mão, linha por linha, e hoje os dois concordam:**
os quatro preços, os sete limites de cada plano, os bullets, as descrições, os
selos, os CTAs e o trial batem com as seções 1, 1.2, 1.3 e 4. Não havia número
errado no site. O que havia era uma trava solta.

E ela é a mesma trava que já falhou duas vezes aqui, nesta terceira forma:

| Rodada | O que estava defasado | Efeito |
|---|---|---|
| fases 2 e 3 | o espelho de produção | "idêntico à produção" era idêntico a um retrato velho |
| 30/09 a 01/10 | o `ESPERADO` do `diff-producao` | 25 divergências legítimas num script que ninguém abria |
| fase 1 a 01/10 | a expectativa do `conferir-dados` | a fonte podia mudar sem ninguém descobrir |

O padrão é sempre o mesmo: **a conferência mede contra uma cópia do alvo, e a
cópia envelhece.** A regra do projeto já dizia o certo na decisão 9, derivar da
tabela em vez de repetir o número escrito. A conferência de preço era justamente
o lugar que não seguia a própria regra.

**O conserto:** `juria-site-astro/scripts/fonte-da-verdade.mjs`, que interpreta o
markdown, as tabelas das seções 1, 1.1, 1.2, 1.3 e 4. As asserções passaram a
derivar dele e **não sabem nenhum número**. Sete conferências novas entraram,
e as de preço, nome aposentado, selo e trial deixaram de ter valor escrito à mão:

- o preço de cada plano, contra a tabela da seção 1
- os sete limites de cada plano, contra a comparativa da seção 4
- a comparativa de `src/data` recurso por recurso, que é o que torna os números
  4, 10 e 9 do Solo consequência da fonte em vez de contagem digitada
- os bullets, as descrições e os CTAs, contra a transcrição literal da seção 1.2
- a duração e os limites do trial, contra a seção 1.3
- os nomes aposentados, lidos da seção 1.1 em vez da lista `['Basic', 'Pro',
  'Enterprise']`
- **a fonte contra si mesma**, porque as seções 1 e 4 repetem preço e limite. Se
  uma for atualizada e a outra não, o site herda a que `src/data` seguiu. Foi
  assim que a fonte chegou a dizer dez recursos na 4.2 e nove na 4.1

**79. O parser para com erro quando o markdown muda de formato, em vez de
conferir contra vazio.** É a lição da decisão 73, onde seletor que não casava lia
texto vazio e vazio batia com qualquer expectativa. Aqui, tabela que não casa,
que casa em dois lugares, que perde a linha separadora, que muda de número de
colunas ou que vem vazia **levanta erro**. Rótulo de linha que deixa de existir
também, e a mensagem lista os rótulos atuais, para quem for consertar não ter que
procurar.

**80. Conferi que as asserções novas têm dentes, mutando a fonte da verdade e
não o código.** O teste certo aqui não é mexer em `src/data`: é mudar o markdown
e ver se a conferência acorda, porque é esse o cenário que aconteceu em 29/09.
Sete mutações, todas revertidas depois, e a fonte voltou byte a byte:

| Mutação na fonte | Resultado |
|---|---|
| preço do Plus, R$ 159 para R$ 149 na seção 1 | 2 falhas: o preço, e a contradição entre as seções 1 e 4 |
| processos do Max, 2.000 para 3.000 na seção 4 | 3 falhas: limites, comparativa e a contradição |
| trial de volta para 14 dias na seção 1.3 | 1 falha, a duração |
| bullet do Max reescrito na seção 1.2 | 1 falha, a transcrição literal |
| linha "Advogados do escritório" renomeada na seção 4 | 2 falhas, e não um `undefined` silencioso |
| cabeçalho da tabela da seção 1 mudando de formato | erro: `tabela "secao 1, planos" nao foi achada` |
| uma quinta coluna de plano entrando na seção 1 | erro: `esperava 5 colunas, veio 6` |

A primeira mutação é a que importa: com o script de antes ela **passaria limpo**,
porque 159 estava escrito na asserção. Agora ela derruba a rodada e imprime os
dois valores, o de `src/data` e o da fonte.

**Nenhuma linha do site mudou nesta rodada.** Os arquivos tocados são
`scripts/fonte-da-verdade.mjs`, que é novo, `scripts/conferir-dados.mjs`,
`AGENTS.md` e este ESTADO. A fonte da verdade foi mutada sete vezes e restaurada,
e `git status` confirma que ela está intacta.

---

## Travou em quê

Se uma fase não puder ser concluída, escrever aqui o motivo, em vez de
improvisar uma solução. **É melhor entregar oito fases e uma pergunta do que
nove fases com um chute dentro.**

_(nada travado. As oito fases foram entregues. O que ficou de fora está na seção de perguntas abaixo e no RELATORIO, e é decisão sua, não bloqueio técnico.)_

**Situação em 01/10, 11h30.** Não há fase para continuar: as oito estão
concluídas e eu não refiz nenhuma. Confirmei isso rodando a rotina inteira em
ambiente limpo, com `npm ci` do zero, e as 156 conferências da rodada anterior
passaram, o `diff-producao` incluído.

Em vez de rodar a mesma rotina uma quarta vez, fui ver **contra o que ela
mede**, e achei o terceiro caso do mesmo defeito: o `conferir-dados.mjs` dizia
no cabeçalho que conferia `src/data` contra o `planos-e-creditos.md` e **nunca
abria esse arquivo**. Preço, limite, selo, CTA e trial estavam digitados dentro
das asserções. Conferi à mão que hoje os dois concordam, então **não havia número
errado no site**: havia uma trava solta, no lugar exato que a tarefa chama de
"nunca de memória". Detalhe nas decisões 78 a 80.

Agora um parser lê o markdown e as asserções não sabem número nenhum. São 163
conferências, 7 novas, e a prova de que elas funcionam é a mutação da própria
fonte, na decisão 80: trocar R$ 159 por R$ 149 passava limpo antes e derruba a
rodada agora.

O que mudou de arquivo nesta rodada, e só isso:
`juria-site-astro/scripts/fonte-da-verdade.mjs`, que é novo,
`juria-site-astro/scripts/conferir-dados.mjs`, `juria-site-astro/AGENTS.md` e
este ESTADO. **Nenhuma linha do site mudou, produção não foi tocada, e o
`juria-lps` nem está clonado aqui.** A fonte da verdade foi mutada para testar e
restaurada byte a byte.

**O que agora depende de você, e não de mais execução:**

⚠️ **ATUALIZADO EM 05/10: o item 1 saiu, as dez perguntas foram respondidas.**
Sobraram os itens 2 e 3, mais a correção das âncoras, que é técnica e não
depende de você. Ver o rodapé do log.

1. ~~**As doze perguntas da seção abaixo.**~~ A 1 e a 9 já estão resolvidas. As
   outras dez não são bloqueio técnico: são escolhas de marca, de produto ou
   de tracking, e eu deliberadamente não as chutei. A 11 ("Mais escolhido" no
   Max ou no Plus) e a 12 (o texto do CTA) são as duas diferenças de copy que
   sobram contra o site no ar. A 12 é nova de 01/10
2. **Os 5 itens ⏳ do checklist da §9.** Conferi se algum deles fechava sem
   deploy, agora que a conferência do navegador serve o `dist/` num servidor
   local, e **nenhum fecha.** Não é falta de servidor: dois pedem o container
   do GTM carregando de verdade, com Pixel Helper e GA4 DebugView, que o
   ambiente desta sessão nem alcança; um pede URL pública para o Rich Results
   Test ler; e um pede aparelho de verdade, não emulação de 390px. Só um
   preview na Vercel resolve, e o brief proíbe. **Não gaste sessão tentando
   `npm run preview` local: não é disso que eles dependem**
3. **Os 37 blocos `{{ TODO }}`** que ainda esperam texto final seu, espalhados
   por 12 das 14 páginas servidas. `/precos` e `/blog` são as duas sem nenhum, e
   a home tem 1. A concentração está nos três comparativos e na
   `/software-juridico`, com 5 cada. Eles são previstos pelo plano, não
   esquecimento: a fase 4 entregou esqueleto mais SEO, e o conteúdo final está
   na lista do "o que NÃO entra nesta execução"

**Para a próxima sessão:** se o pedido for só "continuar", não há o que
continuar sem uma destas três respostas. Vale mais perguntar do que abrir fase
nova por conta própria.

E se a sessão for de conferência, como esta e as três anteriores: **não basta
rodar a rotina de novo.** Quatro rodadas seguidas agora acharam defeito, e
nenhum deles estava no site. Estavam todos no medidor: o espelho defasado, o
`ESPERADO` defasado, o medidor do cabeçalho medindo durante rolagem animada, e
a expectativa de preço digitada à mão. A pergunta que rende é sempre a mesma,
**contra o que isto está medindo, e essa referência está em dia?**, e o teste é
mutar a referência para ver se a conferência acorda.

---

## Perguntas para o Guilherme

Nada aqui impediu a fase 2 de fechar. São pontos onde eu **podia** ter escrito
uma frase e escolhi não escrever, porque a resposta é sua.

### 1. ✅ RESOLVIDA em 30/09. As duas frases entraram

Elas nunca precisaram ser escritas: já estavam no ar. O que faltava era o
espelho deste repositório estar em dia. Com ele sincronizado, as duas vieram
palavra por palavra de produção, e os `{{ TODO }}` sumiram da home:

| Onde | O que entrou |
|---|---|
| 2ª frase do lede do hero | "A partir de R$ 69 por mês, sem cartão para testar." |
| lede da seção `#precos` | "Comece no Solo por R$ 69 e suba quando a equipe crescer. A troca é em um clique, sem migrar dado nem perder histórico." |

O preço nas duas sai de `planoMaisBarato`, não escrito à mão.

Junto veio uma terceira, que ninguém tinha percebido: o **título** da seção de
preços estava "Você só paga conforme cresce", que saiu do ar em 29/09. O que
está no ar é "Cada escritório tem um tamanho. O JurIA acompanha o seu."

A conferência de dados agora exige que as três apareçam no espelho, então copy
da home não pode mais divergir do site no ar sem alguém ser avisado.

### 2. ✅ RESOLVIDA em 05/10. Virou "mais de 25 anos"

O numero exato sobe todo ano e viraria manutencao esquecida. "mais de 25" continua
verdade em 2027 e e' a forma que o FAQ aprovado ja' usava. Trocado em dois lugares
da home: a assinatura do rodape e o paragrafo da autoridade.

**Pergunta original:**

O selo do hero diz "25 anos", e a Mobiletec foi fundada em 2000 (na época era o dado; a Mobiletec corrigiu para 1999 em 21/10/2026). O FAQ aprovado
diz "mais de 25 anos", que continua certo. Mantive o texto de produção palavra
por palavra: mexer em número de autoridade da marca não é decisão de quem porta.
**Atualiza para 26, troca por "mais de 25", ou deixa como está?**

### 3. ✅ RESOLVIDA em 05/10. Virou "do escritório"

"Simultaneos" promete acesso concorrente, e a tabela oficial chama a linha de
"Usuarios do escritorio", que e' assento. A diferenca aparece no suporte, nao na
pagina. E' a unica divergencia de qualificador contra producao, e e' deliberada.

**Pergunta original:**

A tabela oficial chama essa linha de "Usuários **do escritório**", que é assento,
não acesso concorrente. O card de produção diz "simultâneos", que promete uma
coisa um pouco diferente. Mantive o texto de produção. **Vale trocar o
qualificador pelo da tabela?**

### 4. ✅ RESOLVIDA em 05/10. Sao 12 mesmo

O Guilherme conferiu a lista item a item e confirmou que nenhum sobra. O "11" de
producao era numero escrito a mao que ficou para tras quando alguem acrescentou
uma funcionalidade. Aqui o total e' contado, entao nao tem como defasar de novo.

**Pergunta original:**

A coluna "Operação" anuncia "11 funcionalidades" em produção e lista 12 itens.
Passei a derivar do tamanho da lista, então o site novo diz 12. **Confirma que o
certo é 12, ou tem item nessa lista que não deveria estar?**

### 5. ✅ RESOLVIDA em 05/10. Os seis viraram dois-pontos e virgula

Autorizado. Cinco estavam em `<h3>` de dado de exemplo e viraram dois-pontos; o
sexto estava num comentario HTML de producao e virou virgula, porque a frase ja'
tinha dois-pontos antes. Nao foi edicao a mao: virou `ajuste` declarado no
`portar-producao.mjs`, que o porte reaplica sozinho a cada rodada. Ver a decisao
sobre o mecanismo, mais abaixo.

**Pergunta original:**

O CLAUDE.md proíbe travessão em qualquer texto. Existem seis, todos dentro do
markup do mockup, nos dados de exemplo do dashboard ("Contestação — ACME Ltda").
Não mexi: o mockup é porte byte a byte e o critério é não ter diferença visual.
**Se quiser, troco os seis por dois-pontos**, e aí o porte do markup ganha uma
exceção documentada, como já tem o `mockup-nav.js`.

### 6. Um ponto em que o site novo ficou melhor que o que está no ar

Não é pergunta, é aviso.

- **Um H1 por página.** Produção tem três na home, porque o mockup traz "Meu Dia"
  e "Painel Gerencial" em `<h1>`. No site novo os dois viram `div` na hora de
  injetar o markup, sem mudar um pixel.

⚠️ **Correção de 30/09: aqui havia um segundo item, e ele estava errado.** Dizia
que produção anuncia Basic 199, Pro 499 e Enterprise 1299 no JSON-LD. **Não
anuncia.** Produção declara os quatro planos certos, com um `Offer` cada, desde
o commit `edd7c77`. Quem tinha o dado velho era o espelho deste repositório, e
a sessão da madrugada chamou o espelho de "produção" porque era o único arquivo
que ela enxergava. O site no ar nunca teve esse problema, e não há nada a
corrigir lá.

### 7. ✅ RESOLVIDA em 05/10. O "Entrar" passou a repassar

Quem clica no anuncio, ja' tem conta e entra por ali estava sumindo da atribuicao.
Vale so' neste site: producao segue sem, e nao foi tocada. A conferencia de pagina
deixou de apenas "notar" o caso e passou a exigir o atributo nos dois links.

**Pergunta original:**

O atributo `data-forward-utm` está nos seis links de `/register` e em nenhum de
`/login`. Mantive igual. **Vale colocar no "Entrar" também?** Prós: quem clica em
anúncio, já tem conta e entra por ali mantém a atribuição. Contra: é mexer em
tracking que está rodando, e o brief proíbe fazer isso por conta própria.

### 8. ✅ RESOLVIDA em 05/10. Inter Tight saiu do <link>

Era download por pagina sem um pixel de efeito, porque `--font-display` sempre
resolveu para Inter. Para um dia usar de verdade e' preciso mexer em DOIS lugares,
o `<link>` do BaseLayout e o token em `tokens.css`, e os dois comentarios agora
dizem isso.

**Pergunta original:**

A fonte `Inter Tight` continua sendo baixada e não usada, igual a produção. Ou
tira o `<link>`, que economiza download, ou passa a usar nos headings, que muda o
visual de todo o site.

### 9. ✅ RESOLVIDA em 30/09. O CTA passou a ter texto navy

Branco sobre o ciano `#14B4C8` dava **2,50:1**, contra o mínimo de 4,5:1 da
WCAG AA, e no `:hover` piorava para 2,26:1, porque o fundo clareia.

**O texto do botão virou navy. Dá 6,21:1, e no hover 7,90:1.** A cor da marca
não mudou em nada: quem mudou foi a cor do texto em cima dela. A alternativa
era escurecer o ciano, e para o branco passar seria preciso tirar 28% da
luminância, chegando em `#0E8290`, o que mudaria o botão, o preenchimento e
todo o resto do ciano do site.

O `eyebrow` tinha o mesmo defeito, ciano sobre fundo claro a **2,42:1**. Ganhou
um token próprio, `--cyan-texto` (`#0E7F8D`), usado **só onde ciano é texto
sobre fundo claro**: dá 4,57:1. Preenchimento, borda, e todo o ciano de dentro
do mockup seguem no tom original, porque lá ele aparece sobre navy escuro e já
passava.

⚠️ **Fica um caso de fora, e é decisão sua.** O `.accent` do H1, o "num só
sistema" em ciano, dá 2,42:1. Por ser texto grande o mínimo cai para 3:1, então
ele reprova por pouco. Não troquei: mudar a cor de acento do H1 é decisão de
marca, e o `--cyan-texto` deixaria o título com dois tons de ciano brigando.

Tudo isso vale para o site que está no ar também, que tem exatamente os mesmos
contrastes.

### 10. ✅ RESOLVIDA em 05/10. As duas foram feitas

Os quatro botoes ganharam `aria-label` pelo mesmo mecanismo de `ajuste` da
pergunta 5. O `<main>` entrou na home E na /v2, para as duas propostas terem a
mesma estrutura. ⚠️ Foi o `<main>` que fez o `diff-producao` precisar de uma
rodada a mais, como este arquivo previa.

**Pergunta original:**

Os quatro são `jm-switch` e três `jm-icobtn`, dentro do markup do mockup. É porte
byte a byte, produção tem os mesmos quatro, e resolver é um `aria-label` em cada
um. **Se autorizar, o porte do markup ganha uma exceção documentada**, como já
tem o `mockup-nav.js` e os seis travessões da pergunta 5.

Junto: a home e a `/v2` não têm `<main>`, e as onze páginas novas têm. A
assimetria é nossa, não de produção, que é one-pager. O conserto é envolver as
seções da home, e isso mexe nos filhos diretos do `body`, que é onde o diff da
fase 3 se apoia. **Faço junto com a próxima mudança na home, se você mandar**,
com a fase 3 revalidada depois.

### 11. ✅ RESOLVIDA em 05/10. Fica no Max

O Guilherme manteve a decisao de 29/09: o selo e' verdade de produto, e o produto
poe no Max. O Plus segue como o card enfatizado da grade, que e' o outro campo.
Nenhuma linha mudou, porque o site ja' estava assim. Segue sendo a unica diferenca
visivel contra o ar na secao de precos, agora por escolha registrada.

**Pergunta original:**

Achado em 30/09, ao sincronizar o espelho. Produção prende o texto do selo à
classe `featured`, num `content: 'Mais escolhido'` dentro do CSS. Como o card
`featured` da linha principal é o **Plus**, produção escreve "Mais escolhido"
no Plus.

Mas a tela do produto põe esse selo no **Max**, e foi o que você confirmou em
29/09: "mantém o Max como o mais escolhido".

**Segui a sua decisão e o produto:** o selo sai de `src/data/planos.ts`, então
aparece no Max. Para isso os dois conceitos foram separados no dado:

| Campo | O que é | Quem tem |
|---|---|---|
| `destaque` | carrega o selo "Mais escolhido", verdade de produto | Max |
| `enfase` | card que a página empurra, a classe `featured` | Plus |

Produção junta os dois num campo só, e é por isso que lá eles se contradizem.

**A pergunta é qual dos dois vale.** Se o selo é argumento de venda e o Max é
mesmo o mais vendido, está certo como ficou. Se o selo virou só um recurso
visual para destacar o card que você quer empurrar, então ele pertence ao Plus,
e o Max fica sem selo. É a única diferença visível entre o site novo e o que
está no ar na seção de preços.

### 12. ✅ RESOLVIDA em 05/10. Um texto so', igual ao ar

Os seis botoes de conversao dizem "Começar teste grátis" e o do Ilimitado diz
"Falar com especialista", palavra por palavra como producao. O texto saiu de tres
lugares diferentes e passou a morar em `ctaTexto`, em `planos.ts`.

⚠️ **A pergunta cobria tres botoes e eram sete.** Os quatro cards de plano diziam
"Assinar Solo", "Assinar Plus", "Assinar Max" e "Falar com o time", e nao estavam
na pergunta. O Guilherme decidiu alinhar os quatro tambem, senao a correcao
deixaria o site com duas versoes do mesmo botao, que era o defeito original.

Duas conferencias novas travam isso: uma exige que todo CTA saia de `ctaTexto`, e
outra PROIBE numero dentro do texto do botao, que e' o motivo de producao ter
tirado o "7 dias" em 29/09.

**Pergunta original:**

Achado em 01/10, quando o `diff-producao.mjs` voltou a rodar. É a única
divergência de texto que o script classifica como `pend`, sem decisão.

| Onde | O que diz | De onde vem |
|---|---|---|
| site no ar | "Começar teste grátis", nos seis CTAs | produção, desde 29/09 |
| navbar daqui | "Começar grátis" | `Header.astro`, escrito à mão |
| hero, preços e CTA final daqui | "Começar 7 dias grátis" | derivado de `trial.dias` |

**Como cada um apareceu.** O "Começar grátis" da navbar é fóssil: a fase 2
portou do espelho velho, que dizia exatamente isso, e quando o espelho foi
sincronizado em 30/09 ninguém reconferiu, porque o script que compara estava
quebrado. Não foi escolha de ninguém. O "Começar 7 dias grátis" é escolha, e tem
lógica: sai de `trial.dias`, então o dia que o trial mudar de novo o site se
corrige sozinho, que é a regra de nunca ter número escrito à mão.

**Só que produção fez o contrário, e pode ter sido de propósito:** em 29/09 ela
tirou o número do CTA. Quem tira o número não precisa refazer a arte quando a
duração muda, e foi justamente a duração que mudou de 14 para 7.

**Não mexi em nenhum dos três.** Texto de CTA é copy, mexe em conversão, e o
critério de "palavra por palavra de produção" que resolveu a pergunta 1 brigaria
aqui com o de "nenhum número escrito à mão". Escolha sua:

1. **Os três viram "Começar teste grátis"**, igual ao ar. Perde o número, ganha
   não ter que lembrar de mudar.
2. **Os três viram "Começar 7 dias grátis"**, derivado do dado. Copy mais forte,
   e diverge do ar.
3. **Navbar curta, resto com o número**, que é quase o estado de hoje, mas aí a
   navbar precisa dizer o que você decidiu e não o que o espelho velho dizia.

Enquanto não houver resposta, a conferência passa e imprime o item no fim, com
este número. Ela não vai deixar o assunto sumir de novo.
