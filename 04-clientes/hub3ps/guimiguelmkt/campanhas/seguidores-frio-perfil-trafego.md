---
tipo: campanha
cliente: hub3ps
nome-campanha: Seguidores | Frio | Perfil | Tráfego
plataforma: meta
conta: "1702680416845524"
id-campanha: "120249768983420578"
status: ativa
inicio: 2026-11-18
verba-diaria: 60
evento-otimizacao: Visita ao perfil
perfil: https://www.instagram.com/guimiguelmkt/
atualizado: 2026-11-18
autor: claude
---
# Seguidores | Frio | Perfil | Tráfego

Segunda campanha de seguidores do @guimiguelmkt, subida pelo Guilherme em 18/11/2026 às 10h07. Ela substitui a [[campanhas/seguidores-frio-perfil-engajamento|Seguidores | Frio | Perfil | Engajamento]], pausada no mesmo dia, e roda com os mesmos três posts. Valores em BRL. A lista de posts `IG-NN` está na ficha da campanha anterior.

**O que mudou em relação à anterior:** o objetivo da Meta passou de engajamento para tráfego, otimizando para visita ao perfil (`PROFILE_VISIT`). A idade passou para 22 a 45 em todos os conjuntos, e a entrega ficou só no Instagram e só no celular. Por isso as duas campanhas ganharam o objetivo como quarto campo do nome, como no DS Muay Thai.

## Configuração
Conferida na API em 18/11/2026.

- **Objetivo da Meta:** tráfego, com destino no perfil do Instagram e otimização para visita ao perfil, lance de menor custo
- **Público:** Brasil, 22 a 45, todos os gêneros, sem Advantage+ de público, sem exclusão. Só celular
- **Verba:** R$ 20/dia por conjunto (sem CBO), R$ 60/dia no total

| Conjunto | ID | Posicionamentos na API | Anúncio | ID do anúncio |
|---|---|---|---|---|
| `Aberto 22-45 \| Brasil \| Visita ao perfil \| Só Instagram \| IG-06` | `120249768983450578` | Instagram: Feed, Stories, Reels, Explorar e Feed do perfil | `IG-06 \| Reels \| Claude no Meta Ads` | `120249768983400578` |
| `Aberto 22-45 \| Brasil \| Visita ao perfil \| Só Instagram \| IG-04` | `120249768983460578` | Instagram: Feed, Stories, Reels, Explorar e Feed do perfil | `IG-04 \| Reels \| Gestor ou anúncio` | `120249768983410578` |
| `Aberto 22-45 \| Brasil \| Visita ao perfil \| Só Instagram \| IG-07` | `120249768983430578` | Instagram: Feed, Stories, Reels, Explorar e Feed do perfil | `IG-07 \| Reels \| Agente no WhatsApp` | `120249769141900578` |
| `Interesse IA e marketing digital \| Brasil \| Visita ao perfil \| Só Instagram \| IG-07` (cópia do aberto do IG-07, 18/11) | `120249773881260578` | igual | `IG-07 \| Reels \| Agente no WhatsApp` | `120249773881280578` |
| `Donos e empresários \| Brasil \| Visita ao perfil \| Só Instagram \| IG-07` (cópia do aberto do IG-07, 18/11; idade de 22 a 55) | `120249773881250578` | igual | `IG-07 \| Reels \| Agente no WhatsApp` | `120249773881270578` |

> **Conferência de 18/11:** o conjunto do IG-07 subiu entregando também no Facebook, e o do IG-04 sem a Busca do Instagram. O Guilherme tirou o Facebook do IG-07 e a Busca dos três. Agora os três estão iguais, conferidos na API.

Os nomes dos anúncios vieram certos, dados pelo Guilherme. Campanha e conjuntos foram renomeados pela API, e anúncio desta conta se renomeia no Ads Manager (erro de permissão na Página, de 13/11).

## Como ler o resultado
Igual à anterior: o que importa é o **custo por seguidor**, que é o investimento dividido pelos seguidores ganhos nos insights do perfil. A comparação justa com a campanha de engajamento é o custo por visita ao perfil: R$ 0,24 na média de 13 a 18/11.

## Diagnóstico de qualidade (18/11)
O Guilherme achou fraca a qualidade de quem está seguindo. O público que ele quer: quem trabalha com IA e marketing, empresários e autônomos.

**O que os dados mostram** (API, 13 a 18/11, as duas campanhas):
- **Seguidores:** 41 em 11/11 e 81 em 18/11, com cerca de R$ 139 investidos. Dá uns R$ 3,50 por seguidor, contando também os orgânicos
- **Conversão:** 511 visitas ao perfil na campanha de engajamento e uns 40 seguidores novos. Só 8% de quem visita segue
- **Quem chega:** homem de 25 a 34 é o maior grupo, espalhado por todos os estados, sem nenhum filtro além da idade. O público é `Aberto`
- **Onde:** os Reels concentram mais da metade da verba. O Facebook custou de 2 a 3 vezes mais por visita, e já saiu

**Por quê:** público aberto com otimização para visita entrega a quem clica barato, não a quem é do nicho. A Meta não tem otimização para seguir, só para visita ao perfil (fontes abaixo), então o filtro tem que vir do público e do criativo. E o IG-07 (produtividade) fala com qualquer um.

**O que fazer, em ordem:**
1. **Trocar `Aberto` por público de interesse**, em dois conjuntos de teste: `Interesse IA e marketing digital` (inteligência artificial, ChatGPT, marketing digital, Facebook Ads, tráfego pago) e `Interesse empreendedorismo e pequenas empresas` (empreendedorismo, pequenas empresas, comportamento de administrador de página de negócio). Advantage+ de público continua desligado
2. **Criativo que filtra:** o primeiro segundo e o texto na tela dizem com quem o vídeo fala ("se você é gestor de tráfego", "se você atende cliente sozinho"). O IG-06 é o mais de nicho; o IG-07 pode sair do teste de qualidade
3. **Perfil que converte o público certo:** bio, destaques e fixados falando com quem trabalha com IA e marketing, no padrão das [[referencias]]
4. **Medir toda semana:** custo por seguidor (insights do perfil) e uma amostra dos seguidores novos, conferindo se são do nicho
5. **Depois, com base:** semelhante de quem engajou com o perfil (`Engajou IG 365d`), quando o público tiver tamanho

### Públicos propostos (18/11, IDs e alcance na API)
Alcance estimado pela Meta para Brasil, 22 a 45, só Instagram, só celular. O aberto de hoje alcança de 83 a 98 milhões.

| Público | Regra | Alcance | IDs |
|---|---|---|---|
| `Interesse IA e marketing digital` (**proposto**) | curte IA **e** curte marketing (as duas coisas) | 10,2 a 12 mi | IA: `6002898176962` Inteligência artificial (computação), `6002968393168` A.I. Inteligência Artificial. Marketing: `6003127206524` Marketing digital, `6003389760112` Marketing de redes sociais, `6853952393067` Serviços e organizações de marketing |
| `Donos e admins de negócio` (rodou só algumas horas em 18/11) | comportamento, qualquer um dos três | 7,7 a 9,1 mi | `6002714898572` Proprietários de pequenas empresas, `6297846662583` Administradores do perfil comercial do Instagram, `6020530281783` Administradores de página comercial |
| IA ou marketing (descartado) | qualquer interesse da lista | 30 a 36 mi | largo demais, perto do aberto |
| Donos e admins mais PME e empreendedorismo (descartado) | comportamento e interesse | 30 a 35 mi | o interesse em empreendedorismo é amplo demais |

| `Donos e empresários` (**no ar desde 18/11**, montado pelo Guilherme) | qualquer um: comportamento Proprietários de pequenas empresas (`6002714898572`); cargos Proprietário (`110722838955052`), Founder, Director, CEO (`133337610036491`), Empresária - sócia (`135379189860515`), Dono e Gerente (`143530962334045`); empregadores Empresario (`108043745885308`), Proprietário (`110722838955052`), Empresária (`135088686641282`), Empresária/proprietária (`420836674693676`). Idade de 22 a **55** | 770 a 910 mil | troca pedida pelo Guilherme: cargo declarado é mais preciso que comportamento |

Não existe interesse de ChatGPT, OpenAI nem tráfego pago na busca da Meta em pt_BR.

Fontes: [Jon Loomer, tráfego com destino no perfil](https://www.jonloomer.com/create-a-traffic-campaign-with-instagram-profile-conversion-location/), [Creatorflow, como medir follower ads](https://creatorflow.so/blog/instagram-follower-ads/), [Felipe Vergara, seguidores com Meta Ads](https://felipevergara.co/blogs/meta-ads/aumentar-seguidores-instagram-meta-ads/), [Stackmatix, interesse em 2026](https://www.stackmatix.com/blog/meta-ads-interest-targeting). São blogs de quem opera, não documentação da Meta.

### Medição por conjunto
O Ads Manager mostra "Seguidores no Instagram" e "Custo por seguidor" por conjunto (colunas "Seguidores"). A API não devolve, então essa leitura é por print ou pelo navegador. Primeiro dia (18/11, print do Guilherme): IG-04 com 11 seguidores a R$ 0,82, IG-07 com 6 a R$ 0,89 e IG-06 com 3 a R$ 1,23.

### Sequência de testes proposta (18/11)
- **Fase 1, de 19 a 22/11: público.** O conjunto aberto do **IG-07** fica como controle, com duas cópias dele nos públicos de interesse, a R$ 20/dia cada. Os abertos do IG-04 e do IG-06 pausam. O IG-07 foi escolhido no lugar do IG-04 porque fala igual com os dois públicos (IA aplicada a quem atende cliente). O IG-04 puxaria para os donos e o IG-06 para IA e marketing. A diferença de custo entre eles no 1º dia era ruído. Decide o custo por seguidor de cada conjunto, mais uma amostra da qualidade dos seguidores novos
- **Fase 2, de 23 a 26/11: conteúdo.** No público vencedor, um conjunto por post (IG-04, IG-06, IG-07 e o que tiver de novo)

## Histórico de otimizações
- 2026-11-18 · publicada pelo Guilherme, com IG-04, IG-06 e IG-07, R$ 20/dia cada · testar o objetivo de tráfego, com idade de 22 a 45, só Instagram e só celular
- 2026-11-18 · campanha e conjuntos do IG-04 e do IG-06 renomeados para o padrão · só rótulo, sem efeito na entrega
- 2026-11-18 · Facebook tirado do IG-07 e Busca do Instagram tirada dos três, pelo Guilherme; conjunto do IG-07 renomeado com `Só Instagram` · deixar os três conjuntos iguais, só Instagram
- 2026-11-18 · abertos do IG-04 e do IG-06 pausados pelo Guilherme; duas cópias do IG-07 publicadas por ele e configuradas pela API com os públicos `Interesse IA e marketing digital` e `Donos e admins de negócio`, pausadas até o ok · fase 1 do teste de público, com o aberto do IG-07 como controle
- 2026-11-18 · os dois conjuntos de interesse ligados pela API, com o ok do Guilherme · começa a fase 1; leitura em 22/11
- 2026-11-18 · público do conjunto de donos trocado pelo Guilherme: sai admin de página e de perfil comercial, entram cargos e empregadores de dono e empresário, e a idade vai até 55; renomeado para `Donos e empresários` · comportamento era solto demais (pega social media e criador). A idade diferente do controle (22 a 45) entra na leitura do teste
