---
tipo: arquivo
cliente: juria
atualizado: 2026-11-27
autor: claude
origem: agencia_marketing, clients/juria/rascunhos-paginas/00-briefing-redacao.md (migrado em 27/11/2026)
---
# Briefing de redação · páginas de área do JurIA

Rascunhos das páginas do site novo (`juria-site-astro/`). O orquestrador integra
no código; os redatores **só escrevem o JSON da própria página nesta pasta**.

## Fontes, nesta ordem de autoridade
1. `clients/juria/comercial/funcionalidades.md` (inventário; seção 8 é o documento
   da Mobiletec; seções 1 a 7 dizem o plano de cada função; 3.1 e 3.2 detalham Jú
   e WhatsApp do escritório; 8.9 lista dúvidas abertas)
2. `clients/juria/comercial/planos-e-creditos.md` (preço, limite, créditos)
3. `juria-site-astro/src/data/paginas.ts` (respostas já aprovadas: créditos de
   jurimetria e due diligence, monitoramento, IA, chave própria)
4. `juria-site-astro/src/data/home.ts` e `faq.ts` (tom e copy aprovada da home)
5. `clients/juria/rascunhos-paginas/00-seo.md` (termo, URL, title, H1, perguntas)

## Regras que derrubam o texto
- **Nunca travessão** (— ou –). Vírgula, dois-pontos ou ponto.
- **Sem inventar**: número, cliente, depoimento, prazo, percentual de economia.
  Faltou dado: escreva o campo `todo` explicando o que falta e siga.
- **Plano sempre certo.** Função bloqueada no Solo (⛔ no inventário) diz "Do
  Plus em diante". Função por crédito diz "Por créditos". Função cujo plano é
  desconhecido (só aparece na seção 8) **não ganha promessa de plano** e entra
  na lista `duvidas` do JSON.
- **"Todas as funcionalidades"** só junto de "do Plus em diante".
- Secretária virtual: IA que atende os **clientes** do escritório pelo WhatsApp e
  transfere para humano (decisão do Guilherme). Jú: atende **a equipe**. Plano da
  secretária: desconhecido.
- NFS-e: emissão **automática** (confirmado pelo Guilherme), no Solo.
- Domicílio Judicial Eletrônico: **em ativação**, nunca como ativo.
- Valores da Meta para WhatsApp: **não citar**. Pode: "a JurIA não cobra nada
  por mensagem".
- Página com IA: incluir o aviso da Resolução CNJ 615/2025 (texto na seção 8.4).
- Trial: 7 dias, sem cartão. Preço só de `planos-e-creditos.md`.

## Tom
Direto, fato antes de adjetivo, segunda pessoa ("você", "seu escritório").
Frase curta. Nada de "revolucionário", "o melhor", "líder". Cada resposta começa
respondendo a pergunta nas duas primeiras frases (é o que Google e IAs extraem).

## Formato: um arquivo `<slug>.json` por página
```json
{
  "slug": "whatsapp-para-advogados",
  "titulo": "até 60 caracteres, termina em | JurIA",
  "descricao": "meta description, 120 a 155 caracteres",
  "eyebrow": "rótulo curto da página",
  "h1": "H1 da pesquisa SEO",
  "lede": "2 frases que dizem o que é e para quem",
  "destaques": [
    { "titulo": "curto", "texto": "1 a 2 frases", "plano": null }
  ],
  "secoes": [
    {
      "titulo": "Pergunta em linguagem de quem busca?",
      "resposta": "Resposta direta em 2 a 3 frases.",
      "itens": ["opcional, 3 a 6 itens curtos"],
      "plano": "opcional: 'Do Plus em diante' ou 'Por créditos'"
    }
  ],
  "faq": [
    { "pergunta": "…?", "resposta": ["parágrafo 1", "parágrafo 2 opcional"] }
  ],
  "relacionadas": [ { "texto": "Nome da página", "href": "/url" } ],
  "duvidas": ["o que precisa de confirmação da Mobiletec"]
}
```
Tamanhos: 3 a 4 destaques, 4 a 7 seções, 4 a 6 perguntas no FAQ (sem repetir as
seções), 2 a 4 relacionadas. `plano: null` quando vale nos quatro planos.

## URLs do site para links internos
`/whatsapp-para-advogados`, `/ia-para-advogados`, URL de financeiro e do hub de
pesquisa conforme `00-seo.md`, `/gestao-de-processos-e-prazos`, `/jurimetria`,
`/due-diligence-juridica`, `/software-juridico`, `/precos`.
