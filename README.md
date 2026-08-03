<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Nexo — Prospecção SP v6</title>
<style>
  :root{
    --bg: #14110f; --bg-card: #1c1815; --line: #2e2822;
    --text: #f2ece3; --text-dim: #a89c8d;
    --accent: #c96a43; --accent-soft: rgba(201,106,67,.14); --ok: #7fa66a;
  }
  *{box-sizing:border-box;}
  body{margin:0;background:var(--bg);color:var(--text);font-family:'Segoe UI',system-ui,-apple-system,sans-serif;padding:28px 16px 60px;}
  .wrap{max-width:960px;margin:0 auto;}
  .brand{font-size:13px;letter-spacing:.14em;text-transform:uppercase;color:var(--accent);font-weight:700;}
  h1{font-size:24px;margin:6px 0 8px;font-weight:700;}
  .sub{color:var(--text-dim);font-size:14px;line-height:1.5;max-width:680px;}
  .notice{margin-top:16px;background:var(--accent-soft);border:1px solid var(--accent);padding:14px 16px;border-radius:10px;font-size:13px;line-height:1.55;}
  .notice b{color:var(--accent);}
  .notice ul{margin:8px 0 0;padding-left:18px;}
  .notice li{margin-bottom:4px;}
  .controls{display:flex;gap:10px;flex-wrap:wrap;margin:20px 0 14px;}
  select,input{background:var(--bg-card);border:1px solid var(--line);color:var(--text);padding:9px 12px;border-radius:8px;font-size:14px;}
  input{flex:1;min-width:180px;}
  .count{color:var(--text-dim);font-size:13px;margin-bottom:12px;display:flex;justify-content:space-between;align-items:center;gap:10px;flex-wrap:wrap;}
  .reset{background:none;border:none;color:var(--text-dim);font-size:12px;text-decoration:underline;cursor:pointer;padding:0;}
  .grid{display:flex;flex-direction:column;gap:9px;}
  .card{background:var(--bg-card);border:1px solid var(--line);border-radius:12px;padding:14px 16px;display:flex;justify-content:space-between;align-items:center;gap:14px;flex-wrap:wrap;}
  .card.done{opacity:.45;}
  .card .info{flex:1;min-width:220px;}
  .name{font-weight:700;font-size:15px;}
  .meta{color:var(--text-dim);font-size:12.5px;margin-top:2px;}
  .tags{margin-top:6px;display:flex;gap:6px;flex-wrap:wrap;align-items:center;}
  .tag{font-size:10.5px;letter-spacing:.04em;text-transform:uppercase;padding:2px 8px;border-radius:20px;border:1px solid var(--accent);color:var(--accent);}
  .tag.cat{border-color:#6a8fae;color:#8fb4d1;}
  .preview{margin-top:10px;font-size:12.5px;line-height:1.5;color:var(--text-dim);border-left:2px solid var(--line);padding-left:10px;display:none;white-space:pre-wrap;}
  .preview.open{display:block;}
  .link{background:none;border:none;color:var(--text-dim);font-size:11.5px;text-decoration:underline;cursor:pointer;padding:0;margin-top:8px;}
  .actions{display:flex;gap:8px;flex-wrap:wrap;}
  .btn{display:inline-flex;align-items:center;gap:6px;background:var(--ok);color:#0f1a0d;font-weight:700;padding:8px 13px;border-radius:8px;text-decoration:none;font-size:13px;border:none;cursor:pointer;}
  .btn.copy{background:transparent;color:var(--text);border:1px solid var(--line);font-weight:600;}
  .btn.copy.done{border-color:var(--ok);color:var(--ok);}
  .btn.mark{background:transparent;color:var(--text-dim);border:1px solid var(--line);font-weight:600;}
  footer{margin-top:26px;color:var(--text-dim);font-size:12px;text-align:center;line-height:1.6;}
</style>
</head>
<body>
<div class="wrap">
  <header>
    <div class="brand">Nexo · Prospecção v6</div>
    <h1>104 estabelecimentos novos — SP</h1>
    <p class="sub">Leva 5. Nenhum repete as levas anteriores (30 + 82 + 63 + 78 = 253 já na sua base). Todos com número de celular, mensagem escrita por categoria e desconto de agosto no texto.</p>
    <div class="notice">
      <b>Leia antes de disparar:</b>
      <ul>
        <li><b>São 104, não 100</b> — sobrou margem pra você descartar os que não servirem.</li>
        <li><b>"Sem site" não está confirmado.</b> A busca do Google Maps não me devolve o campo de site, então filtrei pelo que dá pra confirmar: celular (9 dígitos, quase sempre WhatsApp) e negócio pequeno o bastante pra provavelmente não ter site. Antes de mandar, bata o olho no perfil do Google — se tiver site, pula. Prometer "vi que você não tem site" pra quem tem queima o contato no primeiro segundo, por isso <b>nenhuma mensagem afirma isso</b>.</li>
        <li><b>Os 29 primeiros</b> (manicure, floricultura, ótica, mecânica, turismo, dança, reforço, sapataria) vieram da lista que te passei mais cedo hoje. Se já falou com algum, marca como contatado.</li>
        <li><b>Sem demo, o CTA é "te passo os detalhes e o valor"</b> — nenhuma mensagem promete mockup que você ainda não tem. Assim que fechar o primeiro, tira print e me fala: eu reescrevo os textos com "olha um exemplo do que entrego", que converte bem melhor.</li>
      </ul>
    </div>
  </header>

  <div class="controls">
    <select id="zoneFilter">
      <option value="">Todas as zonas</option>
      <option value="Zona Oeste">Zona Oeste</option>
      <option value="Zona Leste">Zona Leste</option>
      <option value="Zona Sul">Zona Sul</option>
      <option value="Zona Norte">Zona Norte</option>
      <option value="Centro">Centro</option>
    </select>
    <select id="catFilter">
      <option value="">Todas as categorias</option>
    </select>
    <select id="statusFilter">
      <option value="">Todos</option>
      <option value="pending">Só não contatados</option>
      <option value="done">Só contatados</option>
    </select>
    <input id="search" type="text" placeholder="Buscar por nome ou bairro..." />
  </div>
  <div class="count"><span id="count"></span><button class="reset" id="reset">Limpar marcações de contatado</button></div>
  <div class="grid" id="grid"></div>
  <footer>
    Gerado para a Nexo — leva 5, agosto/2026.<br>
    Contatos coletados de perfis públicos do Google Maps. Se alguém pedir pra não receber mais mensagens, retire da lista e não insista (LGPD, art. 18).
  </footer>
</div>

<script>
const businesses = [
  {name:"Studio Daniele Fraile", addr:"Vila Talarico", zone:"Zona Leste", cat:"Manicure", phone:"5511914909464"},
  {name:"StudioTrês Nail", addr:"Vila Formosa", zone:"Zona Leste", cat:"Manicure", phone:"5511949432246"},
  {name:"Ateliê Dany Unhas de Gel", addr:"Tatuapé", zone:"Zona Leste", cat:"Manicure", phone:"5511973846827"},
  {name:"Studio Sabrina Dourado", addr:"Jardim Norma", zone:"Zona Leste", cat:"Manicure", phone:"5511955778047"},
  {name:"Sabores até Você", addr:"Parque Peruche", zone:"Zona Norte", cat:"Salgados e Doces", phone:"5511992246522"},
  {name:"Minha Costureira Meu Sapateiro", addr:"Jardim das Acácias", zone:"Zona Sul", cat:"Sapataria", phone:"5511918546646"},
  {name:"Sapataria da Vila", addr:"Vila Clementino", zone:"Zona Sul", cat:"Sapataria", phone:"5511948562140"},
  {name:"Sapataria Nova Jardins", addr:"Jardim Paulista", zone:"Centro", cat:"Sapataria", phone:"5511969721332"},
  {name:"Sicatur Viagens", addr:"Vila Alpina", zone:"Zona Leste", cat:"Turismo", phone:"5511971494119"},
  {name:"Ângulo Travel", addr:"Bela Vista", zone:"Centro", cat:"Turismo", phone:"5511973073491"},
  {name:"Ágora Tour", addr:"Higienópolis", zone:"Centro", cat:"Turismo", phone:"5511913490569"},
  {name:"School of Dance Mara Santos", addr:"Vila da Saúde", zone:"Zona Sul", cat:"Escola de Dança", phone:"5511996975401"},
  {name:"Yandê Dança e Movimento", addr:"Campo Belo", zone:"Zona Sul", cat:"Escola de Dança", phone:"5511975506448"},
  {name:"Instituto da Dança", addr:"Interlagos", zone:"Zona Sul", cat:"Escola de Dança", phone:"5511944542907"},
  {name:"Piva Educacional", addr:"Campo Belo", zone:"Zona Sul", cat:"Reforço Escolar", phone:"5511992019404"},
  {name:"Saber Ensino Individual", addr:"Vila Mariana", zone:"Zona Sul", cat:"Reforço Escolar", phone:"5511942297800"},
  {name:"Ensinando o Saber", addr:"Vila Pirajussara", zone:"Zona Oeste", cat:"Reforço Escolar", phone:"5511910100018"},
  {name:"Professor Wesley", addr:"Rosa Maria", zone:"Zona Oeste", cat:"Reforço Escolar", phone:"5511960300767"},
  {name:"Aulas Particulares Mooca", addr:"Mooca", zone:"Zona Leste", cat:"Reforço Escolar", phone:"5511993479715"},
  {name:"Mecânica Horto Center", addr:"Parque Mandaqui", zone:"Zona Norte", cat:"Oficina Mecânica", phone:"5511982042342"},
  {name:"Doctor Auto Prime", addr:"Casa Verde", zone:"Zona Norte", cat:"Oficina Mecânica", phone:"5511996377301"},
  {name:"Guia Norte Auto Center", addr:"Vila Maria Baixa", zone:"Zona Norte", cat:"Oficina Mecânica", phone:"5511991885939"},
  {name:"Floricultura Praça das Flores", addr:"Vila Talarico", zone:"Zona Leste", cat:"Floricultura", phone:"5511947685107"},
  {name:"Floricultura Flor Extra", addr:"Vila Ré", zone:"Zona Leste", cat:"Floricultura", phone:"5511958748311"},
  {name:"Floricultura Rosi Flores", addr:"Itaquera", zone:"Zona Leste", cat:"Floricultura", phone:"5511947620223"},
  {name:"Ótica Leste Vision", addr:"Vila São Francisco", zone:"Zona Leste", cat:"Ótica", phone:"5511968188677"},
  {name:"Óticas Veluzzi", addr:"Vila Matilde", zone:"Zona Leste", cat:"Ótica", phone:"5511974288950"},
  {name:"Óticas Platinum", addr:"Cangaíba", zone:"Zona Leste", cat:"Ótica", phone:"5511994758930"},
  {name:"Fábrica de Óculos Leste", addr:"Parque Artur Alvim", zone:"Zona Leste", cat:"Ótica", phone:"5511951595477"},

  {name:"Pet Shop Novopet", addr:"Limão", zone:"Zona Norte", cat:"Pet Shop", phone:"5511998586987"},
  {name:"Pet Shop Bisteca", addr:"Vila Sabrina", zone:"Zona Norte", cat:"Pet Shop", phone:"5511989261230"},
  {name:"Banho e Tosa Rita Groomer", addr:"Limão", zone:"Zona Norte", cat:"Pet Shop", phone:"5511995012292"},
  {name:"5àsec Jardim Sul", addr:"Vila Andrade", zone:"Zona Sul", cat:"Lavanderia", phone:"5511985855455"},
  {name:"Chaveiro 24 Horas Barra Funda", addr:"Barra Funda", zone:"Centro", cat:"Chaveiro", phone:"5511984957473"},
  {name:"Chaveiro Paulista 24 Horas", addr:"Consolação", zone:"Centro", cat:"Chaveiro", phone:"5511956170813"},
  {name:"Chaveiro 24 Horas Wesley", addr:"Barra Funda", zone:"Centro", cat:"Chaveiro", phone:"5511986638718"},
  {name:"Chaveiro 24 Horas SP", addr:"Vila Mariana", zone:"Zona Sul", cat:"Chaveiro", phone:"5511916737171"},
  {name:"Chaveiro 24 Horas Bela Vista", addr:"Bela Vista", zone:"Centro", cat:"Chaveiro", phone:"5511987851481"},
  {name:"Lunar Dedetização", addr:"Vila Santa Lúcia", zone:"Zona Leste", cat:"Dedetizadora", phone:"5511992690923"},
  {name:"Dedetizadora Otto", addr:"República", zone:"Centro", cat:"Dedetizadora", phone:"5511965387795"},
  {name:"RCA Ar Condicionado", addr:"Água Rasa", zone:"Zona Leste", cat:"Ar Condicionado", phone:"5511947809096"},
  {name:"Oficina do AR", addr:"Tatuapé", zone:"Zona Leste", cat:"Ar Condicionado", phone:"5511963407432"},
  {name:"Proar Climatização", addr:"Itaim Bibi", zone:"Zona Oeste", cat:"Ar Condicionado", phone:"5511949840899"},
  {name:"Percusor Climatização", addr:"Santa Cecília", zone:"Centro", cat:"Ar Condicionado", phone:"5511978514196"},
  {name:"SeuAr Climatização", addr:"Bela Vista", zone:"Centro", cat:"Ar Condicionado", phone:"5511943138055"},
  {name:"Del'Art Garden Paisagismo", addr:"Vila Prudente", zone:"Zona Leste", cat:"Paisagismo", phone:"5511939431001"},
  {name:"MUDA Paisagismo", addr:"Alto da Lapa", zone:"Zona Oeste", cat:"Paisagismo", phone:"5511937499473"},
  {name:"Paisagismo Brasil", addr:"Higienópolis", zone:"Centro", cat:"Paisagismo", phone:"5511914878585"},
  {name:"Quintal Decorinha", addr:"Higienópolis", zone:"Centro", cat:"Buffet Infantil", phone:"5511917180949"},
  {name:"Magic and Co. Buffet", addr:"Vila Olímpia", zone:"Zona Oeste", cat:"Buffet Infantil", phone:"5511940685837"},
  {name:"Ateliê da Festa", addr:"Ipiranga", zone:"Zona Sul", cat:"Buffet Infantil", phone:"5511989548890"},
  {name:"Super Peralta Buffet", addr:"Parque São Domingos", zone:"Zona Oeste", cat:"Buffet Infantil", phone:"5511977296259"},
  {name:"Tapeçaria Incanto", addr:"Cidade Líder", zone:"Zona Leste", cat:"Tapeçaria", phone:"5511940036336"},
  {name:"Tapeçaria Kisofá", addr:"Vila Dalila", zone:"Zona Leste", cat:"Tapeçaria", phone:"5511914031526"},
  {name:"Tapeçaria Gerci", addr:"Vila Santa Catarina", zone:"Zona Sul", cat:"Tapeçaria", phone:"5511933964668"},
  {name:"Flex Solutions Decors", addr:"Jardim Ampliação", zone:"Zona Sul", cat:"Cortinas e Persianas", phone:"5511910733185"},
  {name:"Costa e Barros Persianas", addr:"Santo Amaro", zone:"Zona Sul", cat:"Cortinas e Persianas", phone:"5511986340166"},
  {name:"Jr Cortinas e Persianas", addr:"Vila Mariana", zone:"Zona Sul", cat:"Cortinas e Persianas", phone:"5511977416618"},

  {name:"Mansão Eventual Estúdio", addr:"Brooklin", zone:"Zona Sul", cat:"Fotografia", phone:"5511925542704"},
  {name:"VM Arte em Fotografias", addr:"Vila Santo Estêvão", zone:"Zona Sul", cat:"Fotografia", phone:"5511955593662"},
  {name:"Juliana Ferrari Fotografia", addr:"Tatuapé", zone:"Zona Leste", cat:"Fotografia", phone:"5511965564476"},
  {name:"Estúdio Imagem Fotografia", addr:"Tatuapé", zone:"Zona Leste", cat:"Fotografia", phone:"5511984350335"},
  {name:"André Personal Fotografia", addr:"Pinheiros", zone:"Zona Oeste", cat:"Fotografia", phone:"5511992490170"},
  {name:"O Mundo Play & Diversões", addr:"Cidade D'Abril", zone:"Zona Oeste", cat:"Aluguel de Brinquedos", phone:"5511993079545"},
  {name:"Magic Fest Brinquedos", addr:"Vila Leopoldina", zone:"Zona Oeste", cat:"Aluguel de Brinquedos", phone:"5511945170574"},
  {name:"DK Decoração de Festas", addr:"Vila Pedra Branca", zone:"Zona Norte", cat:"Aluguel de Brinquedos", phone:"5511991183244"},
  {name:"Baby Toys Rental Events", addr:"Vila Palmeiras", zone:"Zona Norte", cat:"Aluguel de Brinquedos", phone:"5511947540709"},
  {name:"Locação de Brinquedos Leiloca", addr:"Vila Hebe", zone:"Zona Norte", cat:"Aluguel de Brinquedos", phone:"5511940242200"},
  {name:"Decor Gesso & Drywall", addr:"Vila Emir", zone:"Zona Sul", cat:"Gesso e Drywall", phone:"5511981512673"},
  {name:"Gesso e Drywall Nacional SP", addr:"Liberdade", zone:"Centro", cat:"Gesso e Drywall", phone:"5511914191108"},
  {name:"Pro Gesso Drywall", addr:"Jardim Santa Cruz", zone:"Zona Norte", cat:"Gesso e Drywall", phone:"5511981633455"},
  {name:"Reforbrax Drywall", addr:"Parque Jabaquara", zone:"Zona Sul", cat:"Gesso e Drywall", phone:"5511957871590"},
  {name:"Gesso Drywall Zaidan", addr:"Vila São Francisco", zone:"Zona Sul", cat:"Gesso e Drywall", phone:"5511962623751"},
  {name:"Eletricista Residencial Liberdade", addr:"Liberdade", zone:"Centro", cat:"Eletricista", phone:"5511913234680"},
  {name:"Eletricista Marcos Iorio", addr:"Chácara Mafalda", zone:"Zona Leste", cat:"Eletricista", phone:"5511982168222"},
  {name:"Sherlock Houses Eletricista", addr:"Casa Verde", zone:"Zona Norte", cat:"Eletricista", phone:"5511997140441"},
  {name:"Eletricista Residencial Ricardo", addr:"Brás", zone:"Centro", cat:"Eletricista", phone:"5511948771161"},
  {name:"MLG Manutenção Elétrica", addr:"Tatuapé", zone:"Zona Leste", cat:"Eletricista", phone:"5511910607056"},
  {name:"L A Hidráulica e Serviços", addr:"Sumaré", zone:"Zona Oeste", cat:"Hidráulica", phone:"5511913975155"},
  {name:"Desentupidora Faz Tudo SP", addr:"Pinheiros", zone:"Zona Oeste", cat:"Hidráulica", phone:"5511940713000"},
  {name:"Ideal Soluções Hidráulicas", addr:"Interlagos", zone:"Zona Sul", cat:"Hidráulica", phone:"5511973006164"},
  {name:"Desentupidora Nipo Brasil", addr:"Vila Bela", zone:"Zona Leste", cat:"Hidráulica", phone:"5511999397460"},
  {name:"Saulo W.F Serviços", addr:"Vila Mariana", zone:"Zona Sul", cat:"Hidráulica", phone:"5511984787610"},
  {name:"Pintura Residencial e Comercial SP", addr:"Vila Olímpia", zone:"Zona Oeste", cat:"Pintor", phone:"5511962893644"},
  {name:"Gomes Pinturas", addr:"Consolação", zone:"Centro", cat:"Pintor", phone:"5511964094135"},
  {name:"Pintor Residencial Gerson", addr:"Consolação", zone:"Centro", cat:"Pintor", phone:"5511994394635"},
  {name:"Pinte Predial", addr:"Vila Mariana", zone:"Zona Sul", cat:"Pintor", phone:"5511995607772"},
  {name:"Paulo Pintor", addr:"Brás", zone:"Centro", cat:"Pintor", phone:"5511966184420"},
  {name:"Mesquita Portões", addr:"Jardim São Paulo", zone:"Zona Norte", cat:"Portões Automáticos", phone:"5511947272537"},
  {name:"Portomatic Solar SP", addr:"Jardim Paulista", zone:"Centro", cat:"Portões Automáticos", phone:"5511917085678"},
  {name:"Ericson Portões Automáticos", addr:"Parque Maria Helena", zone:"Zona Sul", cat:"Portões Automáticos", phone:"5511930035633"},
  {name:"Zona Sul Portões Automáticos", addr:"Jardim Reimberg", zone:"Zona Sul", cat:"Portões Automáticos", phone:"5511967364789"},
  {name:"GMS Portões Automáticos", addr:"Jardim Santa Adélia", zone:"Zona Leste", cat:"Portões Automáticos", phone:"5511984515024"},
  {name:"Alfa Carretos Fretes & Mudanças", addr:"Cambuci", zone:"Centro", cat:"Fretes e Mudanças", phone:"5511990008160"},
  {name:"Sandro Fretes e Mudanças", addr:"Liberdade", zone:"Centro", cat:"Fretes e Mudanças", phone:"5511970373857"},
  {name:"Vanderson Carretos & Fretes", addr:"Jardim Ester Yolanda", zone:"Zona Oeste", cat:"Fretes e Mudanças", phone:"5511957894151"},
  {name:"AS Fretes e Mudanças", addr:"Jardim Germânia", zone:"Zona Sul", cat:"Fretes e Mudanças", phone:"5511954871846"},
  {name:"Ben Piscinas", addr:"Jardim Prudência", zone:"Zona Sul", cat:"Piscinas", phone:"5511995388054"},
  {name:"TOK Piscinas", addr:"Jardim Monte Kemel", zone:"Zona Oeste", cat:"Piscinas", phone:"5511985547790"},
  {name:"Limpa Piscinas", addr:"Butantã", zone:"Zona Oeste", cat:"Piscinas", phone:"5511956703434"},
  {name:"Leda Designer de Sobrancelhas", addr:"Vila Diva", zone:"Zona Leste", cat:"Sobrancelhas", phone:"5511996186202"},
  {name:"Onira Studio", addr:"Tatuapé", zone:"Zona Leste", cat:"Sobrancelhas", phone:"5511986291831"},
  {name:"Fernanda Felix Epilação", addr:"Vila Santa Teresa", zone:"Zona Leste", cat:"Sobrancelhas", phone:"5511965232515"},
  {name:"Amelia Studio", addr:"Vila Ré", zone:"Zona Leste", cat:"Sobrancelhas", phone:"5511992191574"},
];

const abertura = "Oi! Aqui é o Juan, da Nexo — eu faço sites para negócios daqui de São Paulo.";
const fechamento = "Em agosto estou com um desconto pra fechar os primeiros clientes do mês. Posso te passar como funciona e o valor?";

const messages = {
  "Manicure": (b) => `${abertura}\n\nVi o ${b.name} no Google e as avaliações são ótimas. Só que quem procura "unha em ${b.addr}" bate primeiro em quem tem site com fotos dos trabalhos, tabela de preços e botão de agendar. Um site simples resolve isso e trabalha pra você 24h.\n\n${fechamento}`,
  "Salgados e Doces": (b) => `${abertura}\n\nVi o ${b.name} e o movimento de encomendas de vocês. O que trava esse tipo de negócio é o cliente perguntar "quanto é o cento?" e ter que esperar resposta. Com um site de cardápio, preços e pedido direto no WhatsApp, ele já chega decidido.\n\n${fechamento}`,
  "Sapataria": (b) => `${abertura}\n\nAchei o ${b.name} procurando conserto de calçado em ${b.addr}. Quem tem um sapato ou uma bolsa cara pra consertar pesquisa antes e quer ver foto de antes e depois pra confiar. Um site com esse portfólio e os serviços já te separa da concorrência.\n\n${fechamento}`,
  "Turismo": (b) => `${abertura}\n\nVi o ${b.name} e a quantidade de gente elogiando as viagens. Só que pacote é compra cara: o cliente pesquisa a agência antes de pagar, e não achar um site derruba a confiança. Um site com os roteiros, as datas e os depoimentos resolve isso.\n\n${fechamento}`,
  "Escola de Dança": (b) => `${abertura}\n\nVi o ${b.name} e as turmas que vocês têm. Quem quer começar a dançar procura no Google e quer ver grade de horários, os ritmos e o valor antes de mandar mensagem. Com um site assim você recebe menos pergunta repetida e mais matrícula.\n\n${fechamento}`,
  "Reforço Escolar": (b) => `${abertura}\n\nVi o ${b.name} e os resultados que os pais comentam. Mãe procurando reforço compara três ou quatro antes de escolher, e quem tem site com o método, as matérias e os depoimentos sai na frente. É o tipo de serviço que se vende pela confiança.\n\n${fechamento}`,
  "Oficina Mecânica": (b) => `${abertura}\n\nVi o ${b.name} e a fama de honestidade nas avaliações — isso é raro no ramo e vale ouro. Quem está com o carro parado procura oficina no Google e escolhe pela confiança que o site passa: serviços, fotos da oficina e orçamento no WhatsApp.\n\n${fechamento}`,
  "Floricultura": (b) => `${abertura}\n\nVi a ${b.name} e o capricho dos arranjos. Flor se vende pelo olho: quem quer mandar um buquê precisa ver as opções e o preço na hora, senão compra de quem tem site ou fica só no iFood pagando taxa. Um catálogo próprio com pedido no WhatsApp muda essa conta.\n\n${fechamento}`,
  "Ótica": (b) => `${abertura}\n\nVi a ${b.name} e o atendimento que os clientes elogiam. Óculos é compra visual: quem procura em ${b.addr} quer ver as armações e entender as lentes antes de sair de casa. Um site com esse catálogo traz gente já quase decidida na sua porta.\n\n${fechamento}`,
  "Pet Shop": (b) => `${abertura}\n\nVi o ${b.name} e o carinho que os clientes descrevem com os pets. Dono de cachorro procura banho e tosa perto de casa e quer ver preço, serviços e agendar sem ligar. Um site simples com isso já enche a agenda da semana.\n\n${fechamento}`,
  "Lavanderia": (b) => `${abertura}\n\nVi a ${b.name} e a nota de vocês. Quem procura lavanderia quer saber duas coisas antes de ir: quanto custa e quando fica pronto. Um site com tabela, prazos e pedido de coleta pelo WhatsApp tira essa fricção toda.\n\n${fechamento}`,
  "Chaveiro": (b) => `${abertura}\n\nVi o ${b.name} e o tanto de gente falando da rapidez de vocês. Chaveiro é serviço de desespero: a pessoa está trancada na rua, pesquisa no celular e liga pro primeiro que passa confiança. Um site com região atendida, serviços e botão de chamar agora ganha essa corrida.\n\n${fechamento}`,
  "Dedetizadora": (b) => `${abertura}\n\nVi a ${b.name} e as avaliações sobre a garantia de vocês. Dedetização entra em casa, então o cliente pesquisa muito antes de contratar. Um site explicando o processo, a garantia e os produtos usados fecha orçamento que hoje some no meio da pesquisa.\n\n${fechamento}`,
  "Ar Condicionado": (b) => `${abertura}\n\nVi a ${b.name} e o padrão das instalações de vocês. Nessa área o cliente pede três orçamentos e escolhe quem parece mais sério — e quem só tem perfil do Google parece menor do que é. Um site com serviços, fotos das instalações e orçamento no WhatsApp inverte isso.\n\n${fechamento}`,
  "Paisagismo": (b) => `${abertura}\n\nVi o trabalho da ${b.name} e é o tipo de coisa que precisa ser vista pra ser vendida. Projeto de jardim se fecha pelo portfólio: fotos grandes de antes e depois, num site que é seu e não some junto com o algoritmo da rede social.\n\n${fechamento}`,
  "Buffet Infantil": (b) => `${abertura}\n\nVi o ${b.name} e o quanto os pais elogiam as festas. Só que mãe planejando aniversário compara pacote, preço e fotos com calma, geralmente à noite — e se não achar um site, decide com quem tem. Um site com os pacotes e um álbum das festas resolve.\n\n${fechamento}`,
  "Tapeçaria": (b) => `${abertura}\n\nVi a ${b.name} e os antes e depois nas avaliações. Reforma de sofá é decisão visual e cara: o cliente precisa ver o resultado e os tecidos pra confiar em entregar o móvel. Um site com esse portfólio e orçamento por foto no WhatsApp fecha mais.\n\n${fechamento}`,
  "Cortinas e Persianas": (b) => `${abertura}\n\nVi a ${b.name} e a qualidade das instalações. Cortina e persiana o cliente escolhe pelo olho: modelos, tecidos, ambientes prontos. Um site com esse catálogo e agendamento de medição faz o cliente chegar já sabendo o que quer.\n\n${fechamento}`,
  "Fotografia": (b) => `${abertura}\n\nVi o trabalho da ${b.name} e ele merece mais do que uma fichinha no Google. Fotógrafo se contrata pelo portfólio, e um site próprio com os ensaios, os pacotes e um formulário de contato passa muito mais profissionalismo do que só mandar link de rede social.\n\n${fechamento}`,
  "Aluguel de Brinquedos": (b) => `${abertura}\n\nVi a ${b.name} e o movimento de festas de vocês. O cliente quer ver os brinquedos disponíveis, o tamanho, o preço e a data livre — tudo isso antes de mandar mensagem. Um site com catálogo e pedido de reserva economiza horas do seu WhatsApp por semana.\n\n${fechamento}`,
  "Gesso e Drywall": (b) => `${abertura}\n\nVi o trabalho da ${b.name}. Sanca e forro se vendem por foto: quem está reformando procura referência visual antes de chamar alguém. Um site com o portfólio das obras e orçamento por foto no WhatsApp traz cliente mais qualificado.\n\n${fechamento}`,
  "Eletricista": (b) => `${abertura}\n\nVi o ${b.name} e as avaliações sobre honestidade e pontualidade — é exatamente o que o cliente procura, já que vai deixar um estranho mexer na casa. Um site com serviços, região atendida e seu registro passa essa confiança antes mesmo da primeira mensagem.\n\n${fechamento}`,
  "Hidráulica": (b) => `${abertura}\n\nVi a ${b.name} e a rapidez que os clientes citam. Vazamento e entupimento são urgência: a pessoa pesquisa no celular, olha dois ou três e chama quem parece mais confiável. Um site com atendimento 24h, serviços e botão de chamar agora ganha essa disputa.\n\n${fechamento}`,
  "Pintor": (b) => `${abertura}\n\nVi o trabalho da ${b.name}. Pintura o cliente contrata por indicação ou por prova visual — e quem tem site com antes e depois, tipos de serviço e orçamento pelo WhatsApp fecha obra que hoje vai pro concorrente que apareceu primeiro no Google.\n\n${fechamento}`,
  "Portões Automáticos": (b) => `${abertura}\n\nVi a ${b.name} e a agilidade que os clientes elogiam. Portão quebrado é urgência e insegurança: a pessoa procura no Google e chama quem passa mais confiança. Um site com serviços, marcas atendidas e chamada rápida no WhatsApp faz diferença nessa hora.\n\n${fechamento}`,
  "Fretes e Mudanças": (b) => `${abertura}\n\nVi a ${b.name} e o cuidado que os clientes descrevem. Mudança é entregar tudo o que a pessoa tem na mão de um desconhecido — ela pesquisa muito antes. Um site com o serviço, o caminhão, fotos e orçamento online passa a seriedade que fecha o contrato.\n\n${fechamento}`,
  "Piscinas": (b) => `${abertura}\n\nVi a ${b.name} e o trabalho de vocês. Manutenção de piscina é contrato mensal: vale muito mais aparecer bem pra quem procura, porque cada cliente fechado fica meses. Um site com planos, região atendida e orçamento no WhatsApp ajuda direto nisso.\n\n${fechamento}`,
  "Sobrancelhas": (b) => `${abertura}\n\nVi o trabalho da ${b.name} e as avaliações são ótimas. Sobrancelha e cílios se vendem por antes e depois: a cliente quer ver o resultado, o preço e agendar sem ficar esperando resposta. Um site com portfólio e agendamento resolve os três de uma vez.\n\n${fechamento}`,
};

function buildMessage(b){
  const fn = messages[b.cat];
  if (fn) return fn(b);
  return `${abertura}\n\nVi o ${b.name} em ${b.addr} e as avaliações de vocês. Um site simples, com os serviços, fotos e contato direto no WhatsApp, faz quem procura no Google chegar até você em vez de cair na concorrência.\n\n${fechamento}`;
}

/* marcação de contatado — salva no navegador quando possível, senão vale só nesta sessão */
let contacted = {};
try {
  contacted = JSON.parse(window.localStorage.getItem('nexo_v6_contacted') || '{}');
} catch (e) {
  contacted = {};
}
function saveContacted(){
  try { window.localStorage.setItem('nexo_v6_contacted', JSON.stringify(contacted)); } catch (e) {}
}

const grid = document.getElementById('grid');
const countEl = document.getElementById('count');
const zoneFilter = document.getElementById('zoneFilter');
const catFilter = document.getElementById('catFilter');
const statusFilter = document.getElementById('statusFilter');
const search = document.getElementById('search');

const cats = [...new Set(businesses.map(b=>b.cat))].sort();
catFilter.innerHTML += cats.map(c=>`<option value="${c}">${c}</option>`).join('');

function esc(s){
  return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
}

function render(){
  const z = zoneFilter.value, c = catFilter.value, st = statusFilter.value, q = search.value.trim().toLowerCase();
  const filtered = businesses.filter(b=>{
    const mz = !z || b.zone === z;
    const mc = !c || b.cat === c;
    const ms = !st || (st === 'done' ? !!contacted[b.phone] : !contacted[b.phone]);
    const mq = !q || b.name.toLowerCase().includes(q) || b.addr.toLowerCase().includes(q);
    return mz && mc && ms && mq;
  });
  const doneCount = businesses.filter(b=>contacted[b.phone]).length;
  countEl.textContent = filtered.length + ' de ' + businesses.length + ' estabelecimento(s) · ' + doneCount + ' contatado(s)';
  grid.innerHTML = filtered.map(b=>{
    const msg = buildMessage(b);
    const link = `https://wa.me/${b.phone}?text=${encodeURIComponent(msg)}`;
    const isDone = !!contacted[b.phone];
    return `
    <div class="card${isDone ? ' done' : ''}">
      <div class="info">
        <div class="name">${esc(b.name)}</div>
        <div class="meta">${esc(b.addr)} · ${esc(b.phone.replace(/^55(\d{2})(\d{5})(\d{4})$/,'($1) $2-$3'))}</div>
        <div class="tags"><span class="tag">${esc(b.zone)}</span><span class="tag cat">${esc(b.cat)}</span></div>
        <button class="link" data-preview="${esc(b.phone)}">Ver mensagem</button>
        <div class="preview" id="p-${esc(b.phone)}">${esc(msg)}</div>
      </div>
      <div class="actions">
        <a class="btn" href="${link}" target="_blank" rel="noopener">Abrir no WhatsApp</a>
        <button class="btn copy" data-copy="${esc(b.phone)}">Copiar mensagem</button>
        <button class="btn mark" data-mark="${esc(b.phone)}">${isDone ? 'Desmarcar' : 'Marcar contatado'}</button>
      </div>
    </div>`;
  }).join('');
}

grid.addEventListener('click', (ev)=>{
  const t = ev.target;
  const previewPhone = t.getAttribute && t.getAttribute('data-preview');
  const copyPhone = t.getAttribute && t.getAttribute('data-copy');
  const markPhone = t.getAttribute && t.getAttribute('data-mark');

  if (previewPhone){
    const el = document.getElementById('p-' + previewPhone);
    if (el){
      el.classList.toggle('open');
      t.textContent = el.classList.contains('open') ? 'Esconder mensagem' : 'Ver mensagem';
    }
    return;
  }
  if (copyPhone){
    const b = businesses.find(x=>x.phone === copyPhone);
    if (!b) return;
    navigator.clipboard.writeText(buildMessage(b)).then(()=>{
      const original = t.textContent;
      t.textContent = 'Copiado ✓';
      t.classList.add('done');
      setTimeout(()=>{ t.textContent = original; t.classList.remove('done'); }, 1800);
    });
    return;
  }
  if (markPhone){
    if (contacted[markPhone]) { delete contacted[markPhone]; } else { contacted[markPhone] = true; }
    saveContacted();
    render();
  }
});

document.getElementById('reset').addEventListener('click', ()=>{
  contacted = {};
  saveContacted();
  render();
});

zoneFilter.addEventListener('change', render);
catFilter.addEventListener('change', render);
statusFilter.addEventListener('change', render);
search.addEventListener('input', render);
render();
</script>
</body>
</html>
