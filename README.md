<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Nexo — Prospecção SP v8</title>
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
  .notice li{margin-bottom:5px;}
  .notice code{background:#241f1b;padding:1px 6px;border-radius:4px;font-size:12px;}
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
    <div class="brand">Nexo · Prospecção v8</div>
    <h1>102 estabelecimentos novos — SP</h1>
    <p class="sub">Leva 7, com os seus 3 sites de referência dentro de cada mensagem. Nada repete as levas anteriores (30 + 82 + 63 + 78 + 104 + 107 = 464 na sua base).</p>
    <div class="notice">
      <b>Sobre o carrossel na mensagem — não dá, e o motivo importa:</b>
      <ul>
        <li>Mensagem de WhatsApp aberta por link <code>wa.me</code> é <b>texto puro</b>. Carrossel só existe em template aprovado da API oficial do WhatsApp Business (precisa de conta Meta Business, template homologado e um disparador — não sai por link). Então fiz o mais próximo disso:</li>
        <li><b>Modo padrão (<code>linkes</code>):</b> os 3 sites vão escritos na mensagem. Funciona hoje, sem depender de nada. Só o primeiro link ganha miniatura no WhatsApp.</li>
        <li><b>Modo carrossel (<code>portfolio</code>):</b> subi junto o arquivo <code>portfolio.html</code> — uma página com os 3 sites em carrossel de verdade, com setas e swipe no celular. Suba no seu GitHub Pages, cole o endereço em <code>PORTFOLIO_URL</code> no topo do script e troque <code>MODO</code> para <code>'portfolio'</code>. Aí a mensagem vai com <b>um link só</b>, limpo, com miniatura — e o carrossel abre ao tocar.</li>
        <li><b>Recomendo o modo carrossel.</b> Três links numa primeira mensagem fria aumenta chance de bloqueio e polui a leitura. Um link com preview converte melhor.</li>
        <li>Coloque os prints dos 3 sites em <code>img/agro.png</code>, <code>img/viva.png</code> e <code>img/kolor.png</code> — sem eles a página mostra um placeholder no lugar da imagem.</li>
        <li>Ainda vale o de sempre: o Maps não devolve o campo de site, então "sem site" é hipótese. Confere o perfil antes de mandar.</li>
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
    Gerado para a Nexo — leva 7, agosto/2026.<br>
    Contatos coletados de perfis públicos do Google Maps. Se alguém pedir pra não receber mais mensagens, retire da lista e não insista (LGPD, art. 18).
  </footer>
</div>

<script>
/* ============================================================
   CONFIGURAÇÃO — mexa só aqui
   MODO = 'links'      → os 3 sites escritos na mensagem (padrão)
   MODO = 'portfolio'  → um link só, abrindo o carrossel
   ============================================================ */
const MODO = 'links';
const PORTFOLIO_URL = 'https://juanraffffael-coder.github.io/clientes-site/portfolio.html';

const SITES = [
  'https://agronegociosferreira.com.br',
  'https://www.vivamercato.com.br',
  'https://kolorflakes.com.br'
];

function blocoPortfolio(){
  if (MODO === 'portfolio'){
    return `Dá uma olhada em alguns sites que já entreguei:\n${PORTFOLIO_URL}`;
  }
  return `Dá uma olhada em alguns sites que já entreguei:\n${SITES.join('\n')}`;
}

const businesses = [
  {name:"Pizzaria Donna Adelaide", addr:"Imirim", zone:"Zona Norte", cat:"Pizzaria", phone:"5511917886050"},
  {name:"Oli Pizzas e Pães Artesanais", addr:"Itaim Bibi", zone:"Zona Oeste", cat:"Pizzaria", phone:"5511939333906"},
  {name:"Casa de Carnes Natal", addr:"Consolação", zone:"Centro", cat:"Açougue", phone:"5511978217995"},
  {name:"Belari Gelato", addr:"Vila Mariana", zone:"Zona Sul", cat:"Sorveteria", phone:"5511932435365"},
  {name:"Coffee Lab", addr:"Vila Madalena", zone:"Zona Oeste", cat:"Cafeteria", phone:"5511991488052"},
  {name:"London Coffee Station", addr:"Vila Mariana", zone:"Zona Sul", cat:"Cafeteria", phone:"5511930991094"},
  {name:"Shodai Sushi Delivery", addr:"Bela Vista", zone:"Centro", cat:"Sushi e Japonesa", phone:"5511988281805"},
  {name:"Katamaru Delivery Oriental", addr:"Liberdade", zone:"Centro", cat:"Sushi e Japonesa", phone:"5511960817616"},
  {name:"Requinte Espetos", addr:"Mooca", zone:"Zona Leste", cat:"Espetinho e Churrasco", phone:"5511994148854"},
  {name:"Espeteco", addr:"Limão", zone:"Zona Norte", cat:"Espetinho e Churrasco", phone:"5511996496868"},
  {name:"Fit House Itaim Bibi", addr:"Itaim Bibi", zone:"Zona Oeste", cat:"Produtos Naturais", phone:"5511945345745"},
  {name:"Empório Áurea", addr:"República", zone:"Centro", cat:"Produtos Naturais", phone:"5511945322838"},
  {name:"Empório Santa Inês", addr:"Brás", zone:"Centro", cat:"Produtos Naturais", phone:"5511985221524"},
  {name:"Empório Magna Vita", addr:"Jardim Paulistano", zone:"Zona Oeste", cat:"Produtos Naturais", phone:"5511951640258"},
  {name:"Ki Fish Mercadão", addr:"Centro Histórico", zone:"Centro", cat:"Peixaria", phone:"5511940067607"},
  {name:"Hedama Pescados", addr:"Vila da Saúde", zone:"Zona Sul", cat:"Peixaria", phone:"5511946294377"},

  {name:"AJF Construções e Reformas", addr:"Caxingui", zone:"Zona Oeste", cat:"Reforma e Construção", phone:"5511955592905"},
  {name:"M&G Construções e Reformas", addr:"Sacomã", zone:"Zona Sul", cat:"Reforma e Construção", phone:"5511946540609"},
  {name:"Nova Construção e Reformas", addr:"Ipiranga", zone:"Zona Sul", cat:"Reforma e Construção", phone:"5511993031997"},
  {name:"Reforma de Apartamento SP", addr:"Higienópolis", zone:"Centro", cat:"Reforma e Construção", phone:"5511961699182"},
  {name:"SPS Reformas", addr:"Brás", zone:"Centro", cat:"Reforma e Construção", phone:"5511978406750"},
  {name:"Ferreira Costa Construções", addr:"Jardim Ernestina", zone:"Zona Sul", cat:"Reforma e Construção", phone:"5511959612047"},
  {name:"S.A Impermeabilização", addr:"Cerqueira César", zone:"Centro", cat:"Impermeabilização", phone:"5511984480213"},
  {name:"Jesilva Construção", addr:"Jardim Boa Vista", zone:"Zona Oeste", cat:"Impermeabilização", phone:"5511985705605"},
  {name:"Imperex Impermeabilização", addr:"Vila Moinho Velho", zone:"Zona Sul", cat:"Impermeabilização", phone:"5511984681816"},
  {name:"MeJ Impermeabilizações", addr:"Jardim das Imbuias", zone:"Zona Sul", cat:"Impermeabilização", phone:"5511953278113"},
  {name:"LF Clean SP", addr:"Paraíso", zone:"Centro", cat:"Higienização de Estofados", phone:"5511996765181"},
  {name:"Land Clean", addr:"Jardim Nosso Lar", zone:"Zona Sul", cat:"Higienização de Estofados", phone:"5511975544883"},
  {name:"Clean São Paulo", addr:"Parque Nações Unidas", zone:"Zona Norte", cat:"Higienização de Estofados", phone:"5511957723322"},
  {name:"Limpeza Em Dobro", addr:"Vila Sônia", zone:"Zona Oeste", cat:"Higienização de Estofados", phone:"5511987828631"},
  {name:"Higienização de Colchão e Sofá", addr:"Americanópolis", zone:"Zona Sul", cat:"Higienização de Estofados", phone:"5511932276924"},
  {name:"WHigienização", addr:"Vila Morse", zone:"Zona Oeste", cat:"Higienização de Estofados", phone:"5511958331491"},
  {name:"MS Limpeza e Higienização", addr:"Santana", zone:"Zona Norte", cat:"Higienização de Estofados", phone:"5511998220908"},
  {name:"RJ Assentamento de Pisos", addr:"Jardim São Luís", zone:"Zona Sul", cat:"Pisos e Revestimentos", phone:"5511976730900"},
  {name:"Outlet dos Pisos", addr:"Parque Paineiras", zone:"Zona Leste", cat:"Pisos e Revestimentos", phone:"5511988055345"},
  {name:"Revesti Life", addr:"Moema", zone:"Zona Sul", cat:"Pisos e Revestimentos", phone:"5511940243067"},
  {name:"Paixão Solar", addr:"Tatuapé", zone:"Zona Leste", cat:"Energia Solar", phone:"5511980250255"},
  {name:"Marsol Energia Solar", addr:"Vila Fernandes", zone:"Zona Leste", cat:"Energia Solar", phone:"5511970680305"},
  {name:"ON-GRID Painel Solar", addr:"Casa Verde", zone:"Zona Norte", cat:"Energia Solar", phone:"5511976929292"},
  {name:"Alpha Solar", addr:"Vila Regina Feijó", zone:"Zona Leste", cat:"Energia Solar", phone:"5511963633605"},
  {name:"Brilho da Art Comunicação Visual", addr:"Vila Nhocuné", zone:"Zona Leste", cat:"Comunicação Visual", phone:"5511953403795"},
  {name:"Arcasign Comunicação Visual", addr:"Jardim Brasil", zone:"Zona Norte", cat:"Comunicação Visual", phone:"5511995825971"},
  {name:"North Visual", addr:"Cidade Líder", zone:"Zona Leste", cat:"Comunicação Visual", phone:"5511987094467"},
  {name:"SP Letras", addr:"Vila Marieta", zone:"Zona Leste", cat:"Comunicação Visual", phone:"5511948225365"},
  {name:"BM Lírios Personalizados", addr:"Parque Primavera", zone:"Zona Sul", cat:"Brindes Personalizados", phone:"5511939479657"},
  {name:"Estamparia Camisetas e Brindes", addr:"Vila Guilherme", zone:"Zona Norte", cat:"Brindes Personalizados", phone:"5511951320051"},
  {name:"SP Brindes Personalizados", addr:"Vila Amélia", zone:"Zona Norte", cat:"Brindes Personalizados", phone:"5511940110737"},
  {name:"AdriArtes e Personalizados", addr:"Campos Elíseos", zone:"Centro", cat:"Brindes Personalizados", phone:"5511947647012"},
  {name:"Estampa da Hora", addr:"Pinheiros", zone:"Zona Oeste", cat:"Brindes Personalizados", phone:"5511983675170"},
  {name:"4Youpersonalize", addr:"Parada Inglesa", zone:"Zona Norte", cat:"Brindes Personalizados", phone:"5511956103100"},
  {name:"Serigrart Produtos Personalizados", addr:"República", zone:"Centro", cat:"Brindes Personalizados", phone:"5511976693765"},
  {name:"Loca Norte Caçambas", addr:"Vila Constança", zone:"Zona Norte", cat:"Caçambas e Entulho", phone:"5511939415467"},
  {name:"JB Caçambas", addr:"Vila Formosa", zone:"Zona Leste", cat:"Caçambas e Entulho", phone:"5511937054532"},
  {name:"SOS Mini Entulhos", addr:"Jardim Paulistano", zone:"Zona Oeste", cat:"Caçambas e Entulho", phone:"5511923730011"},
  {name:"Aluguel de Caçamba de Entulho", addr:"Vila Brasílio Machado", zone:"Zona Sul", cat:"Caçambas e Entulho", phone:"5511917705962"},
  {name:"Dica Caçambas", addr:"Vila Mascote", zone:"Zona Sul", cat:"Caçambas e Entulho", phone:"5511940829093"},
  {name:"Trash Coleta", addr:"Moema", zone:"Zona Sul", cat:"Caçambas e Entulho", phone:"5511947124118"},
  {name:"Montador de Móveis Pirituba", addr:"Pirituba", zone:"Zona Oeste", cat:"Montador de Móveis", phone:"5511986959339"},
  {name:"Montador Rubens Sousa", addr:"Bosque da Saúde", zone:"Zona Sul", cat:"Montador de Móveis", phone:"5511960171294"},
  {name:"Montador Eder Vinicius", addr:"Bosque da Saúde", zone:"Zona Sul", cat:"Montador de Móveis", phone:"5511933056418"},
  {name:"Montador de Móveis e Carretos", addr:"Campos Elíseos", zone:"Centro", cat:"Montador de Móveis", phone:"5511986246927"},
  {name:"Bru Montador de Móveis", addr:"Jardim Mimar", zone:"Zona Leste", cat:"Montador de Móveis", phone:"5511951420186"},
  {name:"Montador de Móveis Paulo", addr:"Jardim Monte Kemel", zone:"Zona Oeste", cat:"Montador de Móveis", phone:"5511991258064"},
  {name:"Montador de Móveis Zona Sul", addr:"Jardim Aeroporto", zone:"Zona Sul", cat:"Montador de Móveis", phone:"5511966432401"},
  {name:"Depilfiber", addr:"Vila Gomes Cardim", zone:"Zona Leste", cat:"Depilação a Laser", phone:"5511948799094"},
  {name:"Maislaser Jardins", addr:"Jardim Paulista", zone:"Centro", cat:"Depilação a Laser", phone:"5511942261864"},
  {name:"Bella Laser", addr:"Paraíso", zone:"Centro", cat:"Depilação a Laser", phone:"5511975381206"},
  {name:"Julia Laser Mooca", addr:"Mooca", zone:"Zona Leste", cat:"Depilação a Laser", phone:"5511993807544"},

  {name:"Mori Swimming Morumbi", addr:"Vila Andrade", zone:"Zona Sul", cat:"Escola de Natação", phone:"5511930180068"},
  {name:"Escola de Futebol SPFC Piloto", addr:"Vila Água Funda", zone:"Zona Sul", cat:"Escola de Futebol", phone:"5511954791000"},
  {name:"Escola de Futebol SPFC Santana", addr:"Mandaqui", zone:"Zona Norte", cat:"Escola de Futebol", phone:"5511960811311"},
  {name:"Soccer School Primeira Camisa", addr:"Tatuapé", zone:"Zona Leste", cat:"Escola de Futebol", phone:"5511947289379"},
  {name:"Home Seniors Center", addr:"Vila São Francisco", zone:"Zona Sul", cat:"Cuidador de Idosos", phone:"5511911054928"},
  {name:"Cuidar com Amor", addr:"Pinheiros", zone:"Zona Oeste", cat:"Cuidador de Idosos", phone:"5511973274889"},
  {name:"Seven Home Care", addr:"Bela Vista", zone:"Centro", cat:"Cuidador de Idosos", phone:"5511980482186"},
  {name:"Re9 Care", addr:"Jardim Paulistano", zone:"Zona Oeste", cat:"Cuidador de Idosos", phone:"5511965968172"},
  {name:"Fonoaudióloga Talita Roveri", addr:"Pinheiros", zone:"Zona Oeste", cat:"Fonoaudiologia", phone:"5511981746515"},
  {name:"Espaço Garcia", addr:"Tucuruvi", zone:"Zona Norte", cat:"Fonoaudiologia", phone:"5511973421640"},
  {name:"Clinical Speech", addr:"Vila Mariana", zone:"Zona Sul", cat:"Fonoaudiologia", phone:"5511998194063"},
  {name:"Dra. Daniela Galli", addr:"Cerqueira César", zone:"Centro", cat:"Fonoaudiologia", phone:"5511974689607"},
  {name:"Fonoaudióloga Renata Santos", addr:"Vila Mariana", zone:"Zona Sul", cat:"Fonoaudiologia", phone:"5511916673643"},
  {name:"Bruna Montesserratti", addr:"Cidade São Francisco", zone:"Zona Oeste", cat:"Maquiagem e Noivas", phone:"5511973612128"},
  {name:"Studio Erika Okada", addr:"Parada Inglesa", zone:"Zona Norte", cat:"Maquiagem e Noivas", phone:"5511982886883"},
  {name:"Beatriz Rocha Maquiadora", addr:"Jardim Umuarama", zone:"Zona Sul", cat:"Maquiagem e Noivas", phone:"5511966718137"},
  {name:"Melina Giacomini", addr:"Vila Madalena", zone:"Zona Oeste", cat:"Maquiagem e Noivas", phone:"5511998335487"},
  {name:"Kethryn Silva", addr:"Casa Verde", zone:"Zona Norte", cat:"Maquiagem e Noivas", phone:"5511941942177"},
  {name:"Laiza Roma Maquiadora", addr:"Bela Vista", zone:"Centro", cat:"Maquiagem e Noivas", phone:"5511971452271"},
  {name:"Brazzan Semijoias", addr:"25 de Março", zone:"Centro", cat:"Semijoias", phone:"5511990189745"},
  {name:"Lillyth Semijoias", addr:"Bela Vista", zone:"Centro", cat:"Semijoias", phone:"5511941164536"},
  {name:"Master Semijoias", addr:"Consolação", zone:"Centro", cat:"Semijoias", phone:"5511945080042"},
  {name:"Rizzo Embalagens e Festas", addr:"Centro Histórico", zone:"Centro", cat:"Embalagens e Festas", phone:"5511995917054"},
  {name:"Baratão Descartáveis", addr:"Brás", zone:"Centro", cat:"Embalagens e Festas", phone:"5511941500963"},
  {name:"Camargo Corretora de Seguros", addr:"Cerqueira César", zone:"Centro", cat:"Corretora de Seguros", phone:"5511985761229"},
  {name:"Store Brasil Corretora", addr:"Bela Vista", zone:"Centro", cat:"Corretora de Seguros", phone:"5511947739843"},
  {name:"Space Blues Studio", addr:"Sumaré", zone:"Zona Oeste", cat:"Estúdio de Gravação", phone:"5511981521417"},
  {name:"Studio Music Brazil", addr:"Cidade Líder", zone:"Zona Leste", cat:"Estúdio de Gravação", phone:"5511970399683"},
  {name:"Greenhouse Studios", addr:"Vila Alexandria", zone:"Zona Sul", cat:"Estúdio de Gravação", phone:"5511951353543"},
  {name:"K9 Estúdio", addr:"Parque Jabaquara", zone:"Zona Sul", cat:"Estúdio de Gravação", phone:"5511941567423"},
  {name:"Anonimato Estúdios", addr:"Santa Cecília", zone:"Centro", cat:"Estúdio de Gravação", phone:"5511967125051"},
  {name:"Estúdio 2112", addr:"Santana", zone:"Zona Norte", cat:"Estúdio de Gravação", phone:"5511996134488"},
  {name:"Luxo das Marias", addr:"Brás", zone:"Centro", cat:"Moda Feminina", phone:"5511955990393"},
  {name:"Hstar Moda Feminina", addr:"República", zone:"Centro", cat:"Moda Feminina", phone:"5511966538731"},
];

const abertura = "Oi! Aqui é o Juan, da Nexo — eu faço sites para negócios daqui de São Paulo.";
const fechamento = "Em agosto estou com um desconto pra fechar os primeiros clientes do mês. Posso te passar como funciona e o valor?";

const ganchos = {
  "Pizzaria": (b) => `Vi a ${b.name} e as avaliações da massa de vocês. Pizzaria vive de pedido recorrente, e hoje boa parte dele passa por app cobrando comissão. Um site com o cardápio e pedido direto no WhatsApp faz o cliente pedir de você, sem intermediário.`,
  "Açougue": (b) => `Vi a ${b.name} e o cuidado com os cortes que os clientes descrevem. Açougue bom hoje vende por encomenda: o cliente quer ver os cortes, pedir pelo WhatsApp e receber em casa. Um site com isso organizado vira pedido fixo toda semana.`,
  "Sorveteria": (b) => `Vi a ${b.name} e o quanto elogiam os sabores. Sorvete é compra por impulso e por foto: quem procura sorveteria em ${b.addr} decide pelo que vê. Um site com os sabores, o espaço e onde vocês ficam traz gente nova do Google direto na porta.`,
  "Cafeteria": (b) => `Vi a ${b.name} e o ambiente que os clientes descrevem. Cafeteria se escolhe pela vibe: quem procura café em ${b.addr} quer ver as fotos do espaço, o menu e se dá pra trabalhar ali. Um site responde isso melhor que um feed que some.`,
  "Sushi e Japonesa": (b) => `Vi a ${b.name} e a qualidade que os clientes citam. Delivery japonês vive preso a app, com comissão pesada em cada pedido. Um site com o cardápio, os combinados e pedido direto no WhatsApp devolve essa margem pra você.`,
  "Espetinho e Churrasco": (b) => `Vi a ${b.name} e os elogios aos eventos de vocês. Churrasco em domicílio se fecha com antecedência: o cliente quer ver os pacotes, o que está incluso e a data livre antes de mandar mensagem. Um site com isso corta metade da conversa e traz cliente já decidido.`,
  "Produtos Naturais": (b) => `Vi a ${b.name}. Quem procura suplemento e produto natural pesquisa muito preço e marca antes de ir na loja. Um site com o mix, as marcas que vocês trabalham e pedido no WhatsApp traz cliente já sabendo o que quer — inclusive de fora do bairro.`,
  "Peixaria": (b) => `Vi a ${b.name} e a qualidade dos pescados que os clientes elogiam. Peixe é compra planejada: o cliente quer saber o que tem fresco hoje e se entrega em casa. Um site com isso e pedido no WhatsApp fideliza cliente semanal, não só o de sexta-feira.`,
  "Reforma e Construção": (b) => `Vi a ${b.name} e os relatos de obra entregue no prazo — isso é raro no ramo e vale ouro. Quem vai reformar pesquisa muito e desconfia de tudo. Um site com obras prontas, antes e depois e como funciona o orçamento fecha cliente que hoje some no meio da pesquisa.`,
  "Impermeabilização": (b) => `Vi a ${b.name} e os comentários sobre garantia e serviço bem feito. Impermeabilização o cliente contrata com medo, porque já foi mal atendido antes. Um site com o processo, os materiais, a garantia e obras entregues resolve essa desconfiança antes da primeira conversa.`,
  "Higienização de Estofados": (b) => `Vi a ${b.name} e as fotos de antes e depois nas avaliações — é exatamente isso que vende esse serviço. Um site com essa galeria, os valores por tipo de sofá e agendamento no WhatsApp faz o cliente decidir sozinho e já chegar marcando.`,
  "Pisos e Revestimentos": (b) => `Vi o trabalho da ${b.name}. Assentamento de porcelanato o cliente escolhe por acabamento: quer ver obra pronta, rodapé, recorte, nivelamento. Um site com esse portfólio e orçamento por foto no WhatsApp traz cliente mais qualificado e menos curioso.`,
  "Energia Solar": (b) => `Vi a ${b.name}. Energia solar é investimento alto: o cliente pede três orçamentos, pesquisa a empresa e some se não achar nada. Um site com instalações prontas, simulação de economia e o processo de homologação segura esse cliente com você.`,
  "Comunicação Visual": (b) => `Vi o trabalho da ${b.name}. Fachada e letreiro se vendem por foto — e quem contrata é dono de comércio abrindo ou reformando loja, que pesquisa no Google. Um site com as fachadas que vocês fizeram e orçamento no WhatsApp pega esse cliente na hora certa.`,
  "Brindes Personalizados": (b) => `Vi a ${b.name} e a agilidade que os clientes elogiam. Brinde e camiseta personalizada é pedido de empresa e de evento, quase sempre com pressa. Um site com os produtos, prazos e pedido de orçamento faz o comprador te achar antes do concorrente.`,
  "Caçambas e Entulho": (b) => `Vi a ${b.name} e a pontualidade que os clientes citam. Caçamba é decisão de 5 minutos: a obra parou e a pessoa liga pro primeiro que aparece no Google e passa confiança. Um site com tamanhos, valores, região atendida e pedido rápido ganha essa corrida.`,
  "Montador de Móveis": (b) => `Vi o trabalho da ${b.name} e as avaliações sobre capricho e serviço limpo. Montagem é urgência: o móvel chegou e a pessoa quer resolver hoje. Um site com serviços, região e agendamento no WhatsApp faz ela te achar antes do app de serviços — que ainda leva sua comissão.`,
  "Depilação a Laser": (b) => `Vi a ${b.name} e os resultados que as clientes descrevem. Depilação a laser é pacote caro: a cliente compara clínica, aparelho e preço por semanas antes de fechar. Um site com o equipamento, as áreas, os pacotes e agendamento tira você da disputa só por preço.`,
  "Escola de Natação": (b) => `Vi a ${b.name}. Mãe procurando natação pro filho quer ver a piscina, os horários por idade e a estrutura antes de visitar. Um site com fotos, grade de turmas e agendamento de aula experimental traz matrícula que hoje para na primeira mensagem.`,
  "Escola de Futebol": (b) => `Vi a ${b.name} e o quanto os pais elogiam os professores. Escolinha se escolhe por confiança e proximidade: o pai quer ver o campo, os horários por idade e o valor. Um site com isso e matrícula pelo WhatsApp enche turma no começo do semestre.`,
  "Cuidador de Idosos": (b) => `Vi a ${b.name} e os relatos das famílias — nesse ramo, isso é o que vende. Contratar cuidador é decisão feita em momento delicado, pesquisando muito e com medo de errar. Um site com como funciona, a formação da equipe e depoimentos passa a segurança que fecha o contrato.`,
  "Fonoaudiologia": (b) => `Vi o consultório da ${b.name}. Pai procurando fono pro filho pesquisa bastante: quer entender a abordagem, se atende a queixa específica e como agendar. Um site com isso claro traz paciente certo e evita consulta que não é o seu perfil.`,
  "Maquiagem e Noivas": (b) => `Vi o trabalho da ${b.name} e ele merece mais do que um feed. Noiva escolhe maquiadora por portfólio e disponibilidade de data — e pesquisa com meses de antecedência. Um site com as noivas que você já atendeu, os pacotes e um formulário de data trabalha por você enquanto você atende.`,
  "Semijoias": (b) => `Vi a ${b.name} e a qualidade das peças. Semijoia hoje se vende no atacado pra revendedora, e ela quer ver catálogo, pedido mínimo e condições antes de mandar mensagem. Um site com isso te traz revendedora nova do Brasil inteiro, não só de quem passa na loja.`,
  "Embalagens e Festas": (b) => `Vi a ${b.name}. Seu cliente é confeiteira, lanchonete, buffet — gente que compra sempre e pesquisa fornecedor no Google. Um site com as linhas de produto, condições de atacado e pedido no WhatsApp te coloca na frente de comprador que hoje nem sabe que você existe.`,
  "Corretora de Seguros": (b) => `Vi a ${b.name} e as avaliações sobre atendimento. Seguro e plano de saúde o cliente pesquisa corretor antes de passar dados pessoais — e não achar nada online derruba a confiança na hora. Um site com quem é você, o que trabalha e um formulário de cotação resolve isso.`,
  "Estúdio de Gravação": (b) => `Vi o ${b.name} e a estrutura de vocês. Artista escolhe estúdio pelo que vê e ouve: fotos das salas, lista de equipamentos, quem já gravou aí, valor da hora. Um site com isso e reserva no WhatsApp preenche horário vago que hoje fica parado.`,
  "Moda Feminina": (b) => `Vi a ${b.name} e as peças de vocês. Lojista que compra no atacado pesquisa fornecedor no Google e quer ver a grade, o pedido mínimo e as condições antes de ir até a loja. Um site com o catálogo e contato direto traz sacoleira e revendedora nova toda semana.`,
};

function buildMessage(b){
  const fn = ganchos[b.cat];
  const gancho = fn ? fn(b) : `Vi o ${b.name} em ${b.addr} e as avaliações de vocês. Um site simples, com os serviços, fotos e contato direto no WhatsApp, faz quem procura no Google chegar até você em vez de cair na concorrência.`;
  return `${abertura}\n\n${gancho}\n\n${blocoPortfolio()}\n\n${fechamento}`;
}

/* marcação de contatado — salva no navegador quando possível, senão vale só nesta sessão */
let contacted = {};
try {
  contacted = JSON.parse(window.localStorage.getItem('nexo_v8_contacted') || '{}');
} catch (e) {
  contacted = {};
}
function saveContacted(){
  try { window.localStorage.setItem('nexo_v8_contacted', JSON.stringify(contacted)); } catch (e) {}
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
