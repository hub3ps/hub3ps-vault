---
tipo: arquivo
cliente: juria
atualizado: 2026-11-27
autor: claude
origem: agencia_marketing, clients/juria/tracking/_arquivo/consentimento-cookies-decisao.md (migrado em 27/11/2026)
---
# Cookies e medição de campanhas — decisão necessária

> **Para:** Mobiletec Sistemas Ltda (controladora dos dados)
> **De:** Hub3Ps · gestão de tráfego
> **Data:** 20/08/2026
> **Decisão pedida:** qual modelo de cookies o JurIA adota — e quem assume a base legal.

---

## 1. O problema, em um parágrafo

Hoje as tags de medição (Meta Pixel, Google Analytics, Google Ads) só disparam
**depois** que o visitante clica em "Aceitar todos" no banner de cookies. Como a
maioria das pessoas ignora o banner, estamos medindo **8% do que realmente
acontece**: 61 cliques de anúncio geraram 5 visualizações de página registradas,
e os cadastros de trial chegam ao Meta pela mesma fração.

Isso não afeta o produto — o cadastro acontece, o lead entra no banco, o
comercial atende normalmente. **Afeta a capacidade de otimizar a campanha.**

---

## 2. Por que isso é grave para a mídia paga

O algoritmo do Meta aprende com os cadastros que recebe. Com 8% do sinal:

1. **A campanha não sai da fase de aprendizado.** São necessárias ~50 conversões
   para o sistema estabilizar. Com 2 registradas, a entrega segue cara e errática.
2. **O público aprendido fica enviesado.** O Meta monta o perfil de quem converte
   a partir dos exemplos que recebe — e só recebe quem aceita cookies. Isso não é
   uma amostra aleatória. Na prática, a campanha aprende o perfil de "quem clica
   em aceitar", não o de "quem assina o JurIA". O erro se acumula e contamina as
   audiências semelhantes previstas para os próximos meses.
3. **O custo por cadastro aparece inflado**, o que pode levar a pausar criativos
   que na verdade estão funcionando.

---

## 3. As duas opções

### Opção A — Manter como está (consentimento prévio)

Cookies de análise e marketing só ativam após aceite explícito.

- **Base legal:** consentimento (art. 7º, I, LGPD).
- **Postura:** a mais conservadora, alinhada à leitura predominante do Guia
  Orientativo da ANPD sobre cookies.
- **Custo:** a medição continua em ~8%. A campanha segue sem base estatística
  para otimizar, e a verba rende menos.

### Opção B — Aviso informativo + opção de desativar (opt-out)

Cookies ativos por padrão, com aviso claro e a possibilidade de desativar a
qualquer momento, em um clique.

- **Base legal:** legítimo interesse (art. 7º, IX, LGPD), com direito de oposição
  garantido (art. 18, § 2º).
- **Postura:** adotada por grande parte do e-commerce brasileiro — Magazine Luiza,
  entre outros, opera exatamente assim, inclusive com a categoria de publicidade
  ativa por padrão.
- **Ganho:** a medição vai de ~8% para perto de 100%.

---

## 4. O que precisa ser verdade na Opção B

Não basta desligar o banner. Para o modelo se sustentar:

- [x] **Aviso visível no primeiro acesso**, informando o uso de cookies — sem
      bloquear a navegação e sem pedir aceite.
- [x] **"Negar não essenciais" em um clique**, direto no aviso.
- [x] **Painel de preferências** por categoria, acessível pelo link "Gerenciar
      cookies" no rodapé de **todas** as páginas.
- [x] **Política de Cookies** declarando a base legal de cada categoria e
      nomeando os terceiros que recebem dados (Meta e Google).
- [x] **A escolha vale em todo o domínio** `juria.app.br`, inclusive na
      plataforma — quem se opõe na landing page continua oposto no cadastro.
- [ ] **A plataforma (`portal.juria.app.br`) precisa exibir o link "Gerenciar
      cookies"** no rodapé. → **ação da Mobiletec**
- [ ] **A plataforma precisa do bloco de Consent Mode no `<head>`**, antes do
      snippet do GTM. → **ação da Mobiletec** · *ver detalhe abaixo*
- [ ] **Avaliação de legítimo interesse (LIA)** registrada. → **ação da Mobiletec**

### Detalhe técnico do bloco no `<head>` (para o dev da Mobiletec)

O padrão de consentimento **precisa ser definido antes de o container do GTM
carregar**. Se ficar dentro de uma tag do próprio GTM, ele é processado tarde
demais: as tags de inicialização já foram avaliadas e disparam mesmo para quem
se opôs. Foi exatamente o que aconteceu nas landing pages, e a correção foi
mover o bloco para o `<head>`.

No `portal.juria.app.br` o problema é o mesmo — e mais sério, porque é ali que
o cadastro coleta os dados. Sem esse bloco, a oposição do titular não é
respeitada na página de cadastro.

O código está em `clients/juria/lps/cookies/index.html` (ou em qualquer
index.html das LPs), logo antes do comentário `<!-- Google Tag Manager -->`.
É um script curto, síncrono, sem dependência externa: ele lê o cookie
`cc_cookie_juria` e define o consentimento inicial de acordo com a escolha já
registrada pelo visitante.

Os itens marcados já estão implementados e prontos para publicação pela Hub3Ps.

---

## 5. Os riscos da Opção B, declarados

Não recomendamos esta opção como "sem risco". Ela é uma escolha consciente:

1. **Para publicidade, o legítimo interesse é a posição mais exposta.** Para
   análise de audiência própria, é confortável e usual. Para compartilhamento com
   Meta e Google com finalidade publicitária, o entendimento da ANPD tende a
   consentimento. É defensável, mas exige o LIA documentado.
2. **Os Termos das Ferramentas de Negócios da Meta** obrigam o anunciante a obter
   os consentimentos exigidos pela lei aplicável. Esse é um risco **contratual com
   a plataforma**, separado da LGPD, e não desaparece nesta configuração.
3. **O público do JurIA são advogados** — inclusive de contencioso e consumidor.
   É o público com maior probabilidade de examinar a configuração e questionar.
   Some-se que o produto vende conformidade (LGPD, MFA, auditoria) como argumento
   de venda, o que eleva a exigência de coerência.

---

## 6. O que a Hub3Ps recomenda

**Um meio-termo**, que captura a maior parte do ganho com bem menos exposição:

- **Análise** (Google Analytics, medição de audiência própria) → legítimo
  interesse, ativo por padrão, com opt-out. Resolve a leitura de tráfego.
- **Marketing** (Meta, Google Ads) → mantém consentimento.
- **Conversões de cadastro e venda** → enviadas ao Meta pelo servidor (API de
  Conversões), a partir do registro já existente no banco, com base legal própria
  de execução de contrato. É aqui que o sinal de cadastro é recuperado.

Esse desenho devolve a medição de tráfego e o sinal de conversão — que é o que
trava a campanha hoje — sem assumir a parte mais exposta.

---

## 7. Decisão pedida

Que a Mobiletec, como **controladora**, indique por escrito:

1. Qual modelo adotar: **A**, **B** ou o **meio-termo** da seção 6.
2. Quem responde pelo LIA, se a escolha envolver legítimo interesse para marketing.
3. Prazo para incluir o link "Gerenciar cookies" no rodapé da plataforma.

A Hub3Ps implementa e reverte qualquer um dos modelos em poucas horas. O que não
podemos é decidir a base legal do tratamento — essa é uma prerrogativa do
controlador.

---

## Registro

- **20/08/2026** — Hub3Ps apresentou as opções e os riscos acima. Por decisão
  comercial, a configuração da Opção B foi preparada e colocada em ambiente de
  pré-visualização para validação, com publicação condicionada a esta conversa.
  Nenhuma alteração foi publicada em produção até a data deste documento.
