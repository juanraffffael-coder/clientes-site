<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Guia Local — Comércios sem site (Jandira · Itapevi · Barueri · Cotia)</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Bricolage+Grotesque:opsz,wght@12..96,400..800&family=Space+Mono:wght@400;700&family=Inter:wght@400;500;600&display=swap" rel="stylesheet">
<style>
  :root{
    --paper:#F5EEDA;
    --paper-dark:#EBE0C4;
    --ink:#1C2B24;
    --ink-soft:#3E4A42;
    --brick:#C23B22;
    --mustard:#DE9F2E;
    --whats:#25D366;
    --whats-dark:#1DA851;
    --line: rgba(28,43,36,0.16);
  }
  *{box-sizing:border-box;}
  html,body{margin:0;padding:0;}
  body{
    background:
      radial-gradient(circle at 1px 1px, rgba(28,43,36,0.06) 1px, transparent 0) 0 0/22px 22px,
      var(--paper);
    color:var(--ink);
    font-family:'Inter', sans-serif;
    -webkit-font-smoothing:antialiased;
  }
  .wrap{max-width:1180px;margin:0 auto;padding:0 20px 80px;}

  /* HERO */
  header.hero{
    padding:56px 20px 40px;
    border-bottom:3px solid var(--ink);
    position:relative;
    overflow:hidden;
  }
  .hero-inner{max-width:1180px;margin:0 auto;position:relative;}
  .eyebrow{
    font-family:'Space Mono', monospace;
    font-size:12.5px;
    letter-spacing:.14em;
    text-transform:uppercase;
    color:var(--brick);
    font-weight:700;
    display:inline-flex;
    align-items:center;
    gap:8px;
  }
  .eyebrow::before{content:"●"; color:var(--whats-dark); font-size:10px;}
  h1{
    font-family:'Bricolage Grotesque', sans-serif;
    font-weight:800;
    font-size:clamp(38px, 6vw, 74px);
    line-height:0.98;
    margin:14px 0 18px;
    letter-spacing:-0.02em;
  }
  h1 .accent{color:var(--brick); font-style:italic; font-weight:800;}
  .hero-sub{
    max-width:620px;
    font-size:17px;
    line-height:1.55;
    color:var(--ink-soft);
    margin-bottom:26px;
  }
  .stamp{
    position:absolute;
    top:10px; right:10px;
    width:132px; height:132px;
    border:3px solid var(--brick);
    border-radius:50%;
    display:flex;align-items:center;justify-content:center;
    transform:rotate(-16deg);
    color:var(--brick);
    text-align:center;
    font-family:'Space Mono', monospace;
    font-weight:700;
    font-size:12.5px;
    line-height:1.35;
    letter-spacing:.03em;
    opacity:0.9;
    text-transform:uppercase;
  }
  .stamp::before{
    content:"";
    position:absolute; inset:8px;
    border:1px dashed var(--brick);
    border-radius:50%;
  }
  @media (max-width:700px){ .stamp{display:none;} }

  .stats{display:flex; gap:26px; flex-wrap:wrap; margin-top:8px;}
  .stat b{font-family:'Bricolage Grotesque', sans-serif; font-size:26px; display:block;}
  .stat span{font-family:'Space Mono', monospace; font-size:11px; text-transform:uppercase; letter-spacing:.08em; color:var(--ink-soft);}

  /* CONTROLS */
  .controls{
    position:sticky; top:0; z-index:10;
    background:var(--paper);
    border-bottom:2px solid var(--ink);
    padding:16px 20px;
  }
  .controls-inner{max-width:1180px;margin:0 auto; display:flex; flex-wrap:wrap; gap:10px; align-items:center;}
  .search-box{
    flex:1 1 220px;
    display:flex; align-items:center; gap:8px;
    background:#fff;
    border:2px solid var(--ink);
    padding:9px 14px;
    border-radius:3px;
  }
  .search-box input{
    border:none; outline:none; background:transparent;
    font-family:'Inter',sans-serif; font-size:14.5px; width:100%; color:var(--ink);
  }
  .chip-group{display:flex; gap:6px; flex-wrap:wrap;}
  .chip{
    font-family:'Space Mono', monospace;
    font-size:12px; text-transform:uppercase; letter-spacing:.04em;
    padding:8px 13px;
    border:2px solid var(--ink);
    background:transparent;
    color:var(--ink);
    border-radius:20px;
    cursor:pointer;
    white-space:nowrap;
    transition:.15s;
  }
  .chip:hover{background:rgba(28,43,36,0.06);}
  .chip.active{background:var(--ink); color:var(--paper);}
  .chip.active.brick{background:var(--brick); border-color:var(--brick);}

  /* GRID */
  .count-line{
    font-family:'Space Mono', monospace;
    font-size:12.5px;
    color:var(--ink-soft);
    margin:26px 0 16px;
    text-transform:uppercase;
    letter-spacing:.05em;
  }
  .grid{
    display:grid;
    grid-template-columns:repeat(auto-fill, minmax(280px,1fr));
    gap:20px;
  }
  .card{
    position:relative;
    background:#FDFAF1;
    border:2px solid var(--ink);
    border-radius:4px;
    padding:20px 20px 18px;
    display:flex; flex-direction:column; gap:10px;
    box-shadow:5px 5px 0 rgba(28,43,36,0.10);
  }
  .card::before, .card::after{
    content:"";
    position:absolute; top:50%; transform:translateY(-50%);
    width:16px; height:16px;
    background:var(--paper);
    border:2px solid var(--ink);
    border-radius:50%;
  }
  .card::before{left:-10px;}
  .card::after{right:-10px;}
  .cat-tag{
    align-self:flex-start;
    font-family:'Space Mono', monospace;
    font-size:10.5px;
    text-transform:uppercase;
    letter-spacing:.06em;
    padding:4px 9px;
    border-radius:12px;
    font-weight:700;
  }
  .cat-Alimentação{background:#F3D9A9; color:#6B3E00;}
  .cat-Beleza{background:#F2C9CE; color:#7A1F2B;}
  .cat-Serviços{background:#C9E4D6; color:#144A32;}
  .card h3{
    font-family:'Bricolage Grotesque', sans-serif;
    font-size:19px;
    font-weight:700;
    margin:0;
    line-height:1.2;
  }
  .card .city{
    font-family:'Space Mono', monospace;
    font-size:11px;
    color:var(--brick);
    font-weight:700;
    text-transform:uppercase;
    letter-spacing:.05em;
  }
  .card .addr{
    font-size:13.5px;
    color:var(--ink-soft);
    line-height:1.45;
  }
  .card .divider{border-top:1px dashed var(--line); margin:2px 0;}
  .whats-btn{
    margin-top:auto;
    display:flex; align-items:center; justify-content:center; gap:8px;
    background:var(--whats);
    color:#fff;
    text-decoration:none;
    font-family:'Inter', sans-serif;
    font-weight:600;
    font-size:14.5px;
    padding:11px 14px;
    border-radius:3px;
    border:2px solid var(--ink);
    transition:.15s;
  }
  .whats-btn:hover{background:var(--whats-dark);}
  .whats-btn svg{width:17px; height:17px; fill:#fff;}

  .no-results{
    text-align:center;
    padding:60px 20px;
    font-family:'Space Mono', monospace;
    color:var(--ink-soft);
  }

  footer{
    max-width:1180px; margin:0 auto; padding:40px 20px 0;
    font-family:'Space Mono', monospace;
    font-size:12px;
    color:var(--ink-soft);
    border-top:1px dashed var(--line);
    margin-top:50px;
    padding-top:20px;
  }
</style>
</head>
<body>

<header class="hero">
  <div class="hero-inner">
    <div class="stamp">100%<br>whatsapp<br>sem site</div>
    <span class="eyebrow">Jandira · Itapevi · Barueri · Cotia</span>
    <h1>Comércio de <span class="accent">bairro</span>,<br>direto no zap.</h1>
    <p class="hero-sub">Um mural com negócios locais que ainda não têm site — só telefone, endereço e o WhatsApp de quem atende. Toque no card pra chamar na hora.</p>
    <div class="stats" id="statsRow"></div>
  </div>
</header>

<div class="controls">
  <div class="controls-inner">
    <div class="search-box">
      <svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="#1C2B24" stroke-width="2.4"><circle cx="11" cy="11" r="7"/><line x1="21" y1="21" x2="16.65" y2="16.65"/></svg>
      <input id="searchInput" type="text" placeholder="Buscar por nome ou bairro...">
    </div>
    <div class="chip-group" id="cityChips"></div>
    <div class="chip-group" id="catChips"></div>
  </div>
</div>

<div class="wrap">
  <div class="count-line" id="countLine"></div>
  <div class="grid" id="grid"></div>
  <div class="no-results" id="noResults" style="display:none;">Nenhum comércio encontrado com esse filtro — tenta outra busca.</div>

  <footer>
    Dados coletados via busca de estabelecimentos locais (Google Places). Lista inicial — sem site cadastrado no momento da coleta. Se algum negócio já tiver site ou os dados estiverem desatualizados, me avise pra eu corrigir.
  </footer>
</div>

<script>
const DATA = [
{n:"BG Restaurante - Sabor Sergipano",cat:"Alimentação",city:"Jandira",addr:"Av. Conceição Sammartino, 298 - Centro",phone:"5511984523529"},
{n:"Restaurante Pepe Grill",cat:"Alimentação",city:"Jandira",addr:"Via de Acesso João de Góes, 1935 - Jardim Alvorada",phone:"551146196609"},
{n:"Restaurante e Churrascaria 34",cat:"Alimentação",city:"Jandira",addr:"Estr. Estadual Barueri-Itapevi, 650 - Parque Nova Jandira",phone:"5511950600550"},
{n:"Restaurante Vieiras",cat:"Alimentação",city:"Jandira",addr:"R. Benedito Pereira Leite, 73 - Centro",phone:"551147071754"},
{n:"Braseiro Nobre",cat:"Alimentação",city:"Jandira",addr:"R. São Fernando, 858 - Jardim do Golf I",phone:"551142060199"},
{n:"Restaurante Empório Sabor e Tentação",cat:"Alimentação",city:"Jandira",addr:"Estr. Velha de Itu, 15 - Jardim Alvorada",phone:"551146185461"},
{n:"Restaurante MV Marmitaria",cat:"Alimentação",city:"Jandira",addr:"Av. Pres. Costa e Silva, 428 - Jardim Sorocabano",phone:"5511949534211"},
{n:"Pedra Branca Jandira",cat:"Alimentação",city:"Jandira",addr:"R. Milton Alves, 205 - Jardim Alvorada",phone:"5511933803020"},
{n:"Square December 8 - Pães e Doces",cat:"Alimentação",city:"Jandira",addr:"R. Fernando Pessoa, 13 - Centro",phone:"551147896000"},
{n:"Hora do Café - Padaria Artesanal",cat:"Alimentação",city:"Jandira",addr:"R. Ver. Osmar de Oliveira, 14 - Vila Eugênia",phone:"5511939270658"},
{n:"Padaria Jê Pães",cat:"Alimentação",city:"Jandira",addr:"Rua Júpiter, 221 - Vila Eunice",phone:"5511985033553"},
{n:"Divino Doces BK",cat:"Alimentação",city:"Jandira",addr:"Av. Pres. Costa e Silva, 144 - Jardim Sorocabano",phone:"5511948493593"},
{n:"Padaria Mirante",cat:"Alimentação",city:"Jandira",addr:"Av. Pres. Costa e Silva, 445 - Jardim Novo Horizonte",phone:"5511959838374"},
{n:"Lena Paz Beauty e Care",cat:"Beleza",city:"Jandira",addr:"R. João Batista Pedrozo, 302 - Jardim Cristino",phone:"5511987751227"},
{n:"Studio Juliana Bueno",cat:"Beleza",city:"Jandira",addr:"Av. Conceição Sammartino, 302 - Centro",phone:"5511951016369"},
{n:"Studio Claudia Barbosa",cat:"Beleza",city:"Jandira",addr:"R. Jade, 352 - Vila Ercília",phone:"5511959548116"},
{n:"Studio Cássia Motollo",cat:"Beleza",city:"Jandira",addr:"Via Expressa Mauri S. Barufi, 08 - Jardim Jandira",phone:"5511939297184"},
{n:"Studio Elo Fernandes",cat:"Beleza",city:"Jandira",addr:"R. Eliezer Venuto dos Santos, 150 - Jardim das Margaridas",phone:"5511939297184"},
{n:"Instituto de Beleza The Family",cat:"Beleza",city:"Jandira",addr:"R. Sanazar Mardiros, 111 - Jardim Velho Sanazar",phone:"5511942718115"},
{n:"Sergio's Barber Shop",cat:"Beleza",city:"Jandira",addr:"R. Francisca Maria Bueno, 138 - Jardim Gabriela I",phone:"5511945208488"},
{n:"Barbearia Uillian Medina",cat:"Beleza",city:"Jandira",addr:"R. Antonio Domingues Fonseca, 54 - Jardim Rosa Emília",phone:"5511991456606"},
{n:"Mr Deivid Barbearia",cat:"Beleza",city:"Jandira",addr:"Av. Conceição Sammartino, 80 - Centro",phone:"5511989023828"},
{n:"Barbearia Ilha dos Barbados",cat:"Beleza",city:"Jandira",addr:"R. Borá, 70 - Vila Lucinda",phone:"5511978809650"},
{n:"Bola 8 Club Barbearia",cat:"Beleza",city:"Jandira",addr:"R. Francisca Maria Bueno, 187 - Jardim Gabriela I",phone:"5511971662761"},
{n:"Studio Bernasconi - Próteses Capilares",cat:"Beleza",city:"Jandira",addr:"R. Benedito Pereira Leite, 20 - Centro",phone:"5511948654626"},
{n:"Oficina Auto Center J.N.G",cat:"Serviços",city:"Jandira",addr:"R. Willian Waddel, 404 - Centro",phone:"551147897434"},
{n:"G2 Auto Mec",cat:"Serviços",city:"Jandira",addr:"R. Diadema, 189 - Jardim das Margaridas",phone:"5511945431509"},
{n:"Oficina Ferreiras Tecnologia Automotiva",cat:"Serviços",city:"Jandira",addr:"R. Maria José, 157 - Jardim Europa",phone:"5511963491159"},
{n:"Elite Serviços Automotivos",cat:"Serviços",city:"Jandira",addr:"R. Fernando Pessoa, 117 - Jardim Sorocabano",phone:"551147897213"},
{n:"Dois Irmãos Auto Mecânica",cat:"Serviços",city:"Jandira",addr:"R. Manoel Alves dos Santos, 136 - Vila São Nicolau",phone:"5511957757696"},
{n:"Nova Auto Mecânica",cat:"Serviços",city:"Jandira",addr:"Rua Sidney, 1998 - Jardim Sol Nascente",phone:"5511947189453"},
{n:"De Tudo Pet - Pet Shop e Clínica",cat:"Serviços",city:"Jandira",addr:"Av. Alberto Ruffolo, 284 - Jardim Sorocabano",phone:"551147892234"},
{n:"Pet Shop e Avicultura União",cat:"Serviços",city:"Jandira",addr:"R. Tupi, 33 - Vila Diogo Balhesteiro",phone:"5511987179710"},
{n:"Agropet Andrade Jandira",cat:"Serviços",city:"Jandira",addr:"Av. Conceição Sammartino, 151 - Centro",phone:"551146194378"},
{n:"Gatão Pet Shop",cat:"Serviços",city:"Jandira",addr:"R. Imirim, 790 - Jardim Nossa Sra. de Fátima",phone:"551146181798"},
{n:"Dan Pet Banho e Tosa",cat:"Serviços",city:"Jandira",addr:"Av. Pres. Costa e Silva, 398 - Jardim Sorocabano",phone:"5511984489604"},
{n:"Toco da Coruja",cat:"Serviços",city:"Jandira",addr:"R. Benedito Pereira Leite, 14 - Centro",phone:"551147895341"},

{n:"Forquetta Restaurante",cat:"Alimentação",city:"Itapevi",addr:"R. Leopoldina de Camargo, 101 - Centro",phone:"5511982060502"},
{n:"Restaurante Recanto da Eva",cat:"Alimentação",city:"Itapevi",addr:"R. Leopoldina de Camargo, 91 - Centro",phone:"551141411774"},
{n:"Bar Restaurante Casa do Norte",cat:"Alimentação",city:"Itapevi",addr:"R. Professor Irineu Chaluppe, 31 - Jardim Itapevi",phone:"551141410887"},
{n:"Boca Boca Restaurante",cat:"Alimentação",city:"Itapevi",addr:"R. Angelina Barreto Fernandes, 40 - Vila Aurora",phone:"5511947394309"},
{n:"Milk Burguer Itapevi",cat:"Alimentação",city:"Itapevi",addr:"R. João de Abreu, 47 - Parque Itamarati",phone:"551147743030"},
{n:"Ponto Certo Restaurante Central",cat:"Alimentação",city:"Itapevi",addr:"R. Agostinho Ferreira Campos, 674 - Cidade da Saúde",phone:"551147738357"},
{n:"Restaurante Cambará o Caipira",cat:"Alimentação",city:"Itapevi",addr:"R. Santa Rita, 14 - Vila Esperança",phone:"5511956517827"},
{n:"Matilde Restaurante",cat:"Alimentação",city:"Itapevi",addr:"R. José Michelotti, 88 - Cidade da Saúde",phone:"5511987742065"},
{n:"Bread and Life",cat:"Alimentação",city:"Itapevi",addr:"Av. Cesário de Abreu, 1020 - Centro",phone:"551142052760"},
{n:"Padaria Michelli",cat:"Alimentação",city:"Itapevi",addr:"Av. Cesário de Abreu, 177 - Centro",phone:"551141413619"},
{n:"Líder de Itapevi",cat:"Alimentação",city:"Itapevi",addr:"Av. Pres. Vargas, 381 - Jardim Nova Itapevi",phone:"551141412413"},
{n:"Padaria Mulatinha",cat:"Alimentação",city:"Itapevi",addr:"Av. Pres. Vargas, 775 - Jardim Nova Itapevi",phone:"5511933453702"},
{n:"Rainha de Itapevi",cat:"Alimentação",city:"Itapevi",addr:"R. Catharina Durante de Camargo, 223 - Jardim da Rainha",phone:"551141412475"},
{n:"Parque Pães",cat:"Alimentação",city:"Itapevi",addr:"R. Prof. Dimarães Antônio Sandei, 500 - Cidade da Saúde",phone:"5511941838872"},
{n:"Studio Jéssica Andrade - Especialista em Cachos",cat:"Beleza",city:"Itapevi",addr:"Ladeira Nacif Chaluppe, 12 - Centro",phone:"5511914711983"},
{n:"Espaço Vila Beauty",cat:"Beleza",city:"Itapevi",addr:"R. Isola Beli Leonardi, 18 - Centro",phone:"5511951555395"},
{n:"Salão Nayane Rocha",cat:"Beleza",city:"Itapevi",addr:"R. dos Maranhenses, 144 - Parque Suburbano",phone:"5511951131347"},
{n:"Spaço Alice Feliciano",cat:"Beleza",city:"Itapevi",addr:"R. Ester, 71 - Vila São Francisco",phone:"5511982623124"},
{n:"Studio Vanessa Matias",cat:"Beleza",city:"Itapevi",addr:"R. Doze de Setembro, 620 - Jardim Bela Vista",phone:"5511981834375"},
{n:"Beleza Inusitada - Nail Designer",cat:"Beleza",city:"Itapevi",addr:"Av. Rubens Caramez, 793 - Vila Aurora",phone:"5511950777228"},
{n:"Barbearia Victor Cortes",cat:"Beleza",city:"Itapevi",addr:"Av. dos Brasileiros, 241 - Parque Suburbano",phone:"5511957126292"},
{n:"Don Araújo Barbearia",cat:"Beleza",city:"Itapevi",addr:"Av. Pres. Vargas, 359 - Jardim Nova Itapevi",phone:"5511971248816"},
{n:"Barbearia Don Tchôca",cat:"Beleza",city:"Itapevi",addr:"Itashopping Vila Nova - Jardim Nova Itapevi",phone:"5511949684483"},
{n:"Barbearia do Rafa",cat:"Beleza",city:"Itapevi",addr:"Av. Leda Pantalena, 651 - Jardim Portela",phone:"5511930060123"},
{n:"Barbearia Nel Style",cat:"Beleza",city:"Itapevi",addr:"R. Prof. Dimarães Antônio Sandei, 29 - Cidade da Saúde",phone:"5511959883313"},
{n:"Nobre's Barbearia",cat:"Beleza",city:"Itapevi",addr:"R. dos Sergipanos, 41 - Parque Suburbano",phone:"5511984445296"},

{n:"Quinta do Conde",cat:"Alimentação",city:"Barueri",addr:"Av. Sagitário, 555 - Alphaville",phone:"551120780030"},
{n:"Lucky Gastrobar",cat:"Alimentação",city:"Barueri",addr:"Av. Srg. José Siqueira, 190 - Jardim Paraíso",phone:"5511993165979"},
{n:"El Uruguayo Restaurante",cat:"Alimentação",city:"Barueri",addr:"Av. Copacabana, 166 - Empresarial 18 do Forte",phone:"551141956784"},
{n:"Maria João",cat:"Alimentação",city:"Barueri",addr:"Av. Copacabana, 148 - Empresarial 18 do Forte",phone:"551146881950"},
{n:"Lellis Trattoria Alphaville",cat:"Alimentação",city:"Barueri",addr:"Alameda Araguaia, 860 - Alphaville",phone:"551141911100"},
{n:"Central Bakery and Confectionery",cat:"Alimentação",city:"Barueri",addr:"R. Duque de Caxias, 825 - Centro",phone:"551141983263"},
{n:"La Ville",cat:"Alimentação",city:"Barueri",addr:"Al. Rio Negro, 1286 - Alphaville",phone:"551141331200"},
{n:"Padaria Empório Bethaville (Jd. dos Camargos)",cat:"Alimentação",city:"Barueri",addr:"R. da Prata, 816 - Jardim dos Camargos",phone:"551141986888"},
{n:"Padaria Empório Bethaville (Bethaville I)",cat:"Alimentação",city:"Barueri",addr:"R. Caldas Novas, 206 - Bethaville I",phone:"551141986888"},
{n:"Nova SS Panificadora",cat:"Alimentação",city:"Barueri",addr:"Av. Vinte e Seis de Março, 1485 - Centro",phone:"551141981783"},
{n:"Junior Silver Studio",cat:"Beleza",city:"Barueri",addr:"R. Canal da Mancha, 262 - Centro",phone:"5511942008855"},
{n:"Studio ADL Hair",cat:"Beleza",city:"Barueri",addr:"Rua Campos Sales, 359 - Centro",phone:"5511956993768"},
{n:"Victoria Beauty",cat:"Beleza",city:"Barueri",addr:"Av. Presidente Washington Luís, 583 - Jardim Silveira",phone:"5511986796414"},
{n:"Sala D'Oro",cat:"Beleza",city:"Barueri",addr:"Alameda Amazonas, 832 - Alphaville",phone:"5511945075146"},
{n:"Studio ST",cat:"Beleza",city:"Barueri",addr:"R. Pres. Artur da Costa e Silva, 117 - Vila Silveira",phone:"5511955519230"},
{n:"Conexão Barbearia",cat:"Beleza",city:"Barueri",addr:"Av. Henriqueta Mendes Guerra, 1330 - Vila São João",phone:"551141632192"},
{n:"Barbearia Lima",cat:"Beleza",city:"Barueri",addr:"R. Prof. Elvira Lefevre de Salles Nemer, 434 - Jardim São Pedro",phone:"5511933527101"},
{n:"Trezentos Barueri",cat:"Beleza",city:"Barueri",addr:"R. Gen. de Divisão Pedro Rodrigues da Silva, 400 - Aldeia",phone:"5511993274726"},
{n:"Barbearia Café Racer",cat:"Beleza",city:"Barueri",addr:"Calçada das Violetas, 89 - Alphaville Comercial",phone:"551141957373"},
{n:"Barbearia dos Empresários",cat:"Beleza",city:"Barueri",addr:"Av. Trindade, 344 - Bethaville I",phone:"5511934847110"},
{n:"Mec7 Oficina Mecânica",cat:"Serviços",city:"Barueri",addr:"R. José Roberto Berti Biziko, 66 - Jardim Santa Mônica",phone:"5511987516112"},
{n:"Royalle Auto Mecânica",cat:"Serviços",city:"Barueri",addr:"R. São Paulo Apóstolo, 101 - Vila Boa Vista",phone:"5511947248987"},
{n:"Oficina Maranelo",cat:"Serviços",city:"Barueri",addr:"R. Almeida, 108 - Vila São Silvestre",phone:"551141612500"},
{n:"Master Repair Oficina Mecânica",cat:"Serviços",city:"Barueri",addr:"R. Penedo, 50 - Vila Engenho Novo",phone:"551126800338"},
{n:"Oficina MFast",cat:"Serviços",city:"Barueri",addr:"Estr. dos Romeiros, 2101 - Vila São Silvestre",phone:"551153044104"},
{n:"Duubpets Petshop",cat:"Serviços",city:"Barueri",addr:"Av. Henriqueta Mendes Guerra, 946 - Centro",phone:"551147772566"},
{n:"Bella Pet Banho e Tosa",cat:"Serviços",city:"Barueri",addr:"Rua Topázio, 14 - Jardim dos Camargos",phone:"5511963770506"},
{n:"My Pet Boutique",cat:"Serviços",city:"Barueri",addr:"R. da Prata, 816 - Jardim dos Camargos",phone:"551141980857"},
{n:"Nasa Pet Store",cat:"Serviços",city:"Barueri",addr:"R. Santo Antônio, 235 - Vila São João",phone:"551126801105"},
{n:"Pet Barueri",cat:"Serviços",city:"Barueri",addr:"R. Ver. José Viêira, 59 - Jardim Regina Alice",phone:"5511950166872"},
{n:"Conserta Phone",cat:"Serviços",city:"Barueri",addr:"R. da Prata, 331 - Jardim dos Camargos",phone:"5511961688219"},
{n:"Clickcel Assistência Técnica",cat:"Serviços",city:"Barueri",addr:"Av. Marginal Direita, 398 - Jardim Paulista",phone:"5511941572279"},
{n:"Lcell Assistência Técnica",cat:"Serviços",city:"Barueri",addr:"Estrada das Rosas, 343 - Jardim Flórida",phone:"5511951795573"},
{n:"MTScell Assistência Técnica",cat:"Serviços",city:"Barueri",addr:"R. Canal do Panamá, 296 - Jd. Regina",phone:"5511967527577"},
{n:"Utech Assistência Técnica",cat:"Serviços",city:"Barueri",addr:"Rua Campos Sales, 370 - Centro",phone:"5511982502242"},

{n:"A Quinta do Bacalhau",cat:"Alimentação",city:"Cotia",addr:"Av. Ivo Mário Isaac Pires, 1597 - Jardim Santa Paula",phone:"5511993904033"},
{n:"Espaço Casa do Lago",cat:"Alimentação",city:"Cotia",addr:"Rua Santos Dumont, 923 - Paisagem Casa Grande",phone:"5511969067630"},
{n:"Emilia Romagna",cat:"Alimentação",city:"Cotia",addr:"R. José Félix de Oliveira, 854 - Vila Santo Antônio",phone:"551147028974"},
{n:"Boteco da Granja",cat:"Alimentação",city:"Cotia",addr:"R. Adib Auada, 212 - Granja Viana",phone:"5511966113908"},
{n:"Padaria Trilha do Pão Km39",cat:"Alimentação",city:"Cotia",addr:"Av. Ivo Mário Isaac Pires, 10 - Pedras",phone:"551147036149"},
{n:"Dona Deóla",cat:"Alimentação",city:"Cotia",addr:"SP-270, km 22 - Granja Viana",phone:"551146122288"},
{n:"Nova Glória Padaria e Confeitaria",cat:"Alimentação",city:"Cotia",addr:"Av. João Paulo Ablas, 38 - Jardim da Glória",phone:"551147025417"},
{n:"Padaria Michelli (Parque São George)",cat:"Alimentação",city:"Cotia",addr:"Av. Eid Mansur, 835 - Parque São George",phone:"551147024660"},
{n:"Padaria Michelli (Sabiá)",cat:"Alimentação",city:"Cotia",addr:"Estr. do Capuava, 130 - Jardim Sabiá",phone:"551147032497"},
{n:"Espaço Chiquetáh Cotia",cat:"Beleza",city:"Cotia",addr:"Av. Prof. Manoel José Pedroso, 1606 - Parque Bahia",phone:"5511976049229"},
{n:"Salão de Beleza Espaço Belíssima",cat:"Beleza",city:"Cotia",addr:"Travessa Felício Savioli, 16 - Centro",phone:"5511957835035"},
{n:"Studio Angélica Ferreira",cat:"Beleza",city:"Cotia",addr:"R. José Augusto Pedroso, 149 - Vila São Francisco de Assis",phone:"5511914153743"},
{n:"Zenith Espaço Beleza",cat:"Beleza",city:"Cotia",addr:"Av. Prof. Manoel José Pedroso, 273 - Parque Bahia",phone:"5511944659898"},
];

const cities = ["Todos","Jandira","Itapevi","Barueri","Cotia"];
const cats = ["Todos","Alimentação","Beleza","Serviços"];
let activeCity = "Todos", activeCat = "Todos", query = "";

function whatsIcon(){
  return '<svg viewBox="0 0 24 24"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.472-.148-.67.15-.198.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.149-1.255-.462-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.148-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347z"/><path d="M12.01 2C6.486 2 2 6.486 2 12.01c0 1.986.579 3.837 1.579 5.396L2 22l4.708-1.549A9.96 9.96 0 0012.01 22C17.534 22 22 17.534 22 12.01 22 6.486 17.534 2 12.01 2zm0 18.14a8.11 8.11 0 01-4.393-1.288l-.315-.198-3.06 1.007 1.02-2.981-.204-.32a8.106 8.106 0 01-1.267-4.35c0-4.48 3.646-8.126 8.219-8.126 4.48 0 8.126 3.646 8.126 8.126 0 4.573-3.646 8.13-8.126 8.13z"/></svg>';
}

function render(){
  const grid = document.getElementById('grid');
  const filtered = DATA.filter(d=>{
    const cOk = activeCity==="Todos" || d.city===activeCity;
    const catOk = activeCat==="Todos" || d.cat===activeCat;
    const qOk = !query || d.n.toLowerCase().includes(query) || d.addr.toLowerCase().includes(query);
    return cOk && catOk && qOk;
  });
  document.getElementById('countLine').textContent = `${filtered.length} comércio${filtered.length===1?'':'s'} encontrado${filtered.length===1?'':'s'}`;
  document.getElementById('noResults').style.display = filtered.length ? 'none' : 'block';
  grid.innerHTML = filtered.map(d=>`
    <div class="card">
      <span class="cat-tag cat-${d.cat}">${d.cat}</span>
      <div>
        <div class="city">${d.city}</div>
        <h3>${d.n}</h3>
      </div>
      <div class="addr">${d.addr}</div>
      <div class="divider"></div>
      <a class="whats-btn" href="https://wa.me/${d.phone}" target="_blank" rel="noopener">
        ${whatsIcon()} Chamar no WhatsApp
      </a>
    </div>
  `).join('');
}

function buildChips(){
  const cityWrap = document.getElementById('cityChips');
  cityWrap.innerHTML = cities.map(c=>`<button class="chip ${c===activeCity?'active':''}" data-city="${c}">${c}</button>`).join('');
  const catWrap = document.getElementById('catChips');
  catWrap.innerHTML = cats.map(c=>`<button class="chip ${c===activeCat?'active brick':''}" data-cat="${c}">${c}</button>`).join('');

  cityWrap.querySelectorAll('.chip').forEach(btn=>{
    btn.addEventListener('click', ()=>{
      activeCity = btn.dataset.city;
      buildChips(); render();
    });
  });
  catWrap.querySelectorAll('.chip').forEach(btn=>{
    btn.addEventListener('click', ()=>{
      activeCat = btn.dataset.cat;
      buildChips(); render();
    });
  });
}

function buildStats(){
  const total = DATA.length;
  const byCity = cities.slice(1).map(c=>DATA.filter(d=>d.city===c).length);
  const rows = [
    {n: total, l:"Comércios listados"},
    {n: cities.length-1, l:"Cidades cobertas"},
    {n: cats.length-1, l:"Categorias"},
  ];
  document.getElementById('statsRow').innerHTML = rows.map(r=>`<div class="stat"><b>${r.n}</b><span>${r.l}</span></div>`).join('');
}

document.getElementById('searchInput').addEventListener('input', e=>{
  query = e.target.value.toLowerCase().trim();
  render();
});

buildChips();
buildStats();
render();
</script>
</body>
</html>
