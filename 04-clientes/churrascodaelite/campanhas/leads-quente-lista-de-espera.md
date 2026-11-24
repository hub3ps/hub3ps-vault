---
tipo: campanha
cliente: churrascodaelite
nome-campanha: Leads | Quente | Lista de espera
plataforma: meta
id-campanha: "120250684802260559"
status: no ar desde 18/11, 4 conjuntos desde 24/11
inicio: 2026-11-18
fim: 2026-11-26
verba-diaria: 28
evento-otimizacao: Lead (Pixel 333549951080063)
lp: https://curso.churrascodaelite.pt
atualizado: 2026-11-24
autor: claude
---
# Leads | Quente | Lista de espera

Captação para a lista de espera da Black Friday do workshop "Faturando com Churrasco" (97 € por 67 €, de 27 a 30/11). A pessoa entra na lista pela [LP](https://curso.churrascodaelite.pt), cai na página de obrigado e entra no grupo VIP do WhatsApp, onde a oferta sai primeiro, a 27/11. Conta CA01 `1295259920836612`, Página `111836513679647`, Instagram @churrasco_da_elite `17841403077087483`. Pedida pelo Guilherme em 18/11, com os vídeos do Lucas ([[../entregas/2026-11-18-videos-do-lucas|análise]]).

Montada pelo Claude pelo MCP em rascunho, corrigida e publicada à mão pelo Guilherme no Ads Manager em 18/11, por volta das 15h01 UTC.

## IDs no ar (API, 18/11)
| Conjunto | ID do conjunto | Anúncio | ID do anúncio | Criativo | Botão |
|---|---|---|---|---|---|
| `Engajou IG 365d e seguidores \| Portugal \| Lead \| VL-07` | `120250684808600559` | `VL-07 \| Vídeo \| Cansado da obra` | `120250684833720559` | `1852552182752556` (era `2194781391249059` até a troca do botão) | Candidatar-se (`APPLY_NOW`) |
| `Engajou IG 365d e seguidores \| Portugal \| Lead \| VL-05` | `120250684809190559` | `VL-05 \| Vídeo \| Profissão lucrativa` | `120250684838900559` | `1004237632735235` | Candidatar-se (`APPLY_NOW`) |
| `Engajou IG 365d e seguidores \| Portugal \| Lead \| VL-08` | `120250788300100559` | `VL-08 \| Vídeo \| Apaixonado à noite` | `120250788300110559` | `1188137323556329` (vídeo `1161052599635665`) | Candidatar-se (`APPLY_NOW`) |
| `Engajou IG 365d e seguidores \| Portugal \| Lead \| VL-10` | `120250788325080559` | `VL-10 \| Vídeo \| Chuva em Lisboa` | `120250788325090559` | `4506124256304955` (vídeo `1831555067965915`) | Candidatar-se (`APPLY_NOW`) |

VL-08 e VL-10 entraram em 24/11, por volta das 19h28 UTC, montados à mão pelo Guilherme no Ads Manager. Cada um tem conjunto próprio, a 6 € por dia, com o mesmo público, o fim em 26/11 às 23h59 e as mesmas 5 variações de texto. A verba da campanha passou a 28 € por dia (VL-07 a 10 €; VL-05, VL-08 e VL-10 a 6 €).

Ads Manager: [campanha](https://adsmanager.facebook.com/adsmanager/manage/adsets?act=1295259920836612&selected_campaign_ids=120250684802260559)

## Conferência na API depois de publicar (18/11)
- **Certo:** campanha, conjuntos e anúncios nos nomes do padrão. Conjuntos `ACTIVE`, anúncios em análise (`IN_PROCESS`). Lead do Pixel `333549951080063`, atribuição 7 dias clique e 1 visualização, fim em 26/11 às 23h59. URL `https://curso.churrascodaelite.pt/` e link de exibição `churrascodaelite.pt`. Texto, título e descrição principais da versão 2. Sem catálogo. Público `Seguidores IG` (o `seguidores` renomeado pelo Guilherme) e `Engajou IG 365d`, Portugal, 18 a 65, Advantage+ público desligado
- **Mudou à mão:** verba de 5 € para 6 € por conjunto, 12 € por dia no total. Posicionamentos Advantage+, com Audience Network e Threads
- **A ver com o Guilherme:**
  - **Expansão do público:** estava ligada (`targeting_relaxation_types.custom_audience = 1`), entregando também para semelhantes de 1% dos dois públicos. **Desligada pelo Claude pelo MCP em 18/11, a pedido do Guilherme**, e conferida no ar: `custom_audience = 0`, sem semelhantes
  - **Botões:** estavam diferentes ("Ver detalhes" no VL-07). O Guilherme igualou em "Candidatar-se" nos dois em 18/11. O VL-07 ganhou criativo novo e voltou para análise
  - **"image_animation" ligado** nos dois criativos, além de Comentários relevantes. Não aparece no Ads Manager (o Guilherme procurou) porque é animação de imagem e o anúncio é vídeo: não tem efeito. O MCP não desliga em anúncio publicado com variações de texto. Fica como está
- **Não dá para ler pela API:** os outros 4 textos, títulos e descrições (a leitura traz só o principal), a UTM e a tela "Configuração do criativo"

## Configuração
- **Objetivo:** Leads (`OUTCOME_LEADS`), conversão no site, otimizando pelo `Lead` do Pixel `333549951080063`, que dispara na página de obrigado
- **Orçamento:** por conjunto (ABO), 6 € por dia em cada (5 € escolhidos em 18/11 e subidos para 6 € pelo Guilherme ao publicar), até 26/11 às 23h59 de Lisboa. Cerca de 100 € no total
- **Um conjunto por vídeo**, para os dois entregarem no teste (pedido do Guilherme)
- **Público (Guilherme, 18/11):** só quem segue o @churrasco_da_elite ou interagiu com ele em 365 dias, os dois somados. Públicos `seguidores` (`120250644113480559`, de 16/11, cerca de 18,8 a 22,1 mil) e `Engajou IG 365d` (`120250684886700559`, criado pelo Claude em 18/11, todas as interações com o perfil). Portugal (mora ou esteve há pouco). Sem filtro de idade nem de idioma: o público já é quente. Advantage+ público desligado, para não sair dos dois públicos
- **Primeira versão (descartada antes de publicar):** `Aberto 23-55`, frio, com Advantage+ público ligado. O Guilherme pediu a troca para os públicos quentes
- **Posicionamentos:** Advantage+
- **Atribuição:** 7 dias clique e 1 dia visualização
- **Botão:** "Candidatar-se" (`APPLY_NOW`) nos dois
- **UTM:** `utm_source=meta&utm_medium=paid&utm_campaign=leads-quente-lista-de-espera&utm_content=vl-07` (ou `vl-05`) `&utm_term=engajou-ig-365d-e-seguidores`. Os criativos da primeira versão (`1859768228774504` e `1134670792675021`, com a UTM do público aberto) ficaram sem uso na conta. A LP leva as UTMs para a planilha da lista
- **Declaração de IA:** não marcada. Os vídeos são gravações reais do Lucas

## Copy (as mesmas nos dois anúncios, a Meta combina)
Versão 2, de 18/11, subida à mão pelo Guilherme no Ads Manager. A versão 1 citava o preço (97 € por 67 €) e "renda extra", fora da regra de montagem ([[../../../03-processos/convencoes|convenções]], "Montagem do anúncio").

**Textos principais**
1. Gostas de fazer churrasco e já pensaste em transformar isso num negócio de eventos em Portugal? O workshop Faturando com Churrasco vai ter uma condição especial na Black Friday, de 27 a 30 de novembro. Entra na lista VIP e recebe a oferta primeiro, no grupo do WhatsApp.
2. Cansado da obra ou do restaurante? O Churrasco da Elite faz eventos de churrasco há mais de 10 anos e abre o passo a passo no workshop Faturando com Churrasco. Entra na lista VIP e sê dos primeiros a saber da oferta da Black Friday.
3. Sabes grelhar, mas não sabes cobrar? No workshop Faturando com Churrasco aprendes a montar o menu, a divulgar e a gerir os teus eventos. A oferta da Black Friday sai primeiro para quem está na lista VIP.
4. A oferta da Black Friday do workshop Faturando com Churrasco sai primeiro no grupo VIP do WhatsApp, a 27 de novembro. A inscrição na lista é grátis. Entra e recebe o link antes de todos.
5. Casamentos, batizados, aniversários: há sempre um evento a precisar de um bom churrasco. O workshop Faturando com Churrasco mostra como começar a trabalhar com eventos. Entra na lista VIP e recebe a oferta da Black Friday em primeira mão.

**Títulos:** Entra na lista VIP da Black Friday · A oferta sai primeiro no grupo VIP · Transforma a paixão em negócio · Workshop Faturando com Churrasco · Sabes grelhar? Aprende a cobrar

**Descrições:** Inscrição grátis na lista · Oferta de 27 a 30 de novembro · O link chega primeiro no WhatsApp · Workshop online do Churrasco da Elite · Mais de 10 anos de eventos

**Ajustes do Guilherme no Ads Manager (18/11):** URL do site e link de exibição `churrascodaelite.pt`, aprimoramentos desligados (só Comentários relevantes), Destaques do site, Links de site e Produtos e serviços desligados, catálogo do Shopify desvinculado

## Fila de vídeos
Para entrar aos poucos, no lugar do pior ou em conjunto novo: VL-02 (armazém), VL-03 (caixa preta) e VL-04 (sem o "2025"). Todos no Drive, em `12. Lucas - Churrasco da Elite/Criativos · Captação lista Black`.

**Como subir vídeo pela API:** a Meta só aceita link público. Em 18/11, os vídeos e as capas ficaram alguns minutos em `curso.churrascodaelite.pt/_midia/`, no deploy da LP, e saíram depois do upload.

**Na biblioteca da CA01 desde 24/11** (subidos pelo Claude, em 1080p, para o Guilherme testar num conjunto novo): VL-08 `1161052599635665` e VL-10 `1831555067965915`. Subiram pela Marketing API direto, depois que o Guilherme deu acesso de gravação ao token.

## Riscos
- VL-07 e VL-05 falam em ganhar 1.500 € por mês. A Meta pode reprovar. Se reprovar, há corte sem a promessa (tempos na análise dos vídeos)
- Vídeos em 576x1024, compressão do WhatsApp
- O Pixel só tinha o `Lead` do teste de 18/11 antes desta campanha

## Histórico de otimizações
- 2026-11-24 · VL-08 e VL-10 no ar, em conjuntos novos a 6 € (Guilherme), conferidos na API: ativos, com público, Pixel, fim, link e expansão iguais aos dos outros. A conferir: a UTM dos dois diz `utm_content=vl-05`, copiada do VL-05, então a planilha vai registrar as inscrições deles como VL-05; e o aprimoramento `pac_relaxation` está ligado, fora da regra, ao lado do `image_animation` e do `standard_enhancements`, que já estavam nos outros
- 2026-11-23 · verba invertida pelo MCP a pedido do Guilherme: VL-07 de 6 € para 10 € e VL-05 de 10 € para 6 €, conferido no ar. O VL-05 tinha subido em 20/11, quando era o mais barato
- 2026-11-23 · leitura de 18 a 22/11: 21 leads a 2,58 € (VL-07 12 a 1,97 €, VL-05 9 a 3,40 €). VL-05 está a 10 € por dia e VL-07 a 6 € (mudança de 20/11). Entrega parada de 22/11, 16h, até o pagamento do Lucas em 23/11, 10h25 UTC (cartão)
- 2026-11-18 · botão do VL-07 trocado para "Candidatar-se" pelo Guilherme; VL-05 aprovado e ativo, VL-07 de novo em análise
- 2026-11-18 · expansão do público desligada nos dois conjuntos pelo MCP (Guilherme pediu), conferida no ar
- 2026-11-18 · publicada pelo Guilherme, conferida na API: no ar, anúncios em análise, 6 € por conjunto. Expansão do público, botões diferentes e image_animation a ver
- 2026-11-18 · copy v2 sem preço e sem "renda extra", e link, aprimoramentos e configuração do criativo corrigidos à mão pelo Guilherme no Ads Manager
- 2026-11-18 · público trocado para `Engajou IG 365d e seguidores` (pedido do Guilherme), campanha renomeada para Quente, criativos refeitos com a UTM nova · rascunho sem erro, à espera do OK
- 2026-11-18 · montada em rascunho pelo Claude: campanha, 2 conjuntos a 5 € e 2 anúncios, sem erro de validação · à espera do OK para publicar
