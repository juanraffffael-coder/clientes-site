<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Nexo — Prospecção SP (celulares)</title>
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
  .controls{display:flex;gap:10px;flex-wrap:wrap;margin:20px 0 14px;}
  select,input{background:var(--bg-card);border:1px solid var(--line);color:var(--text);padding:9px 12px;border-radius:8px;font-size:14px;}
  input{flex:1;min-width:180px;}
  .count{color:var(--text-dim);font-size:13px;margin-bottom:12px;}
  .grid{display:flex;flex-direction:column;gap:9px;}
  .card{background:var(--bg-card);border:1px solid var(--line);border-radius:12px;padding:14px 16px;display:flex;justify-content:space-between;align-items:center;gap:14px;flex-wrap:wrap;}
  .card .info{flex:1;min-width:220px;}
  .name{font-weight:700;font-size:15px;}
  .meta{color:var(--text-dim);font-size:12.5px;margin-top:2px;}
  .tags{margin-top:6px;display:flex;gap:6px;flex-wrap:wrap;}
  .tag{font-size:10.5px;letter-spacing:.04em;text-transform:uppercase;padding:2px 8px;border-radius:20px;border:1px solid var(--accent);color:var(--accent);}
  .tag.cat{border-color:#6a8fae;color:#8fb4d1;}
  .actions{display:flex;gap:8px;flex-wrap:wrap;}
  .btn{display:inline-flex;align-items:center;gap:6px;background:var(--ok);color:#0f1a0d;font-weight:700;padding:8px 13px;border-radius:8px;text-decoration:none;font-size:13px;border:none;cursor:pointer;}
  .btn.copy{background:transparent;color:var(--text);border:1px solid var(--line);font-weight:600;}
  .btn.copy.done{border-color:var(--ok);color:var(--ok);}
  footer{margin-top:26px;color:var(--text-dim);font-size:12px;text-align:center;}
</style>
</head>
<body>
<div class="wrap">
  <header>
    <div class="brand">Nexo · Prospecção v2</div>
    <h1>82 estabelecimentos com celular — SP</h1>
    <p class="sub">Só entram aqui números no formato celular (9 dígitos, começando com 9) — maior chance real de WhatsApp. Sem repetir a lista anterior.</p>
    <div class="notice">
      <b>Sobre "ativo no WhatsApp":</b> não existe ferramenta que me permita checar isso automaticamente, nem para 1 nem para 82 números. O filtro por formato de celular é o melhor proxy que dá pra fazer sem acesso à API do WhatsApp Business. Pra confirmar de fato, o jeito é abrir o botão "Abrir no WhatsApp" de cada um — se o número não tiver conta, o próprio WhatsApp mostra erro na hora, sem gastar sua mensagem.
    </div>
  </header>

  <div class="controls">
    <select id="zoneFilter">
      <option value="">Todas as zonas</option>
      <option value="Zona Oeste">Zona Oeste</option>
      <option value="Zona Leste">Zona Leste</option>
      <option value="Zona Sul">Zona Sul</option>
      <option value="Zona Norte">Zona Norte</option>
    </select>
    <select id="catFilter">
      <option value="">Todas as categorias</option>
    </select>
    <input id="search" type="text" placeholder="Buscar por nome ou bairro...">
  </div>
  <div class="count" id="count"></div>
  <div class="grid" id="grid"></div>
  <footer>Gerado para a Nexo — números filtrados por formato celular, não confirmados individualmente como ativos no WhatsApp.</footer>
</div>

<script>
const businesses = [
  // ZONA OESTE
  {name:"Beleza Fidalga", addr:"Pinheiros", zone:"Zona Oeste", cat:"Salão", phone:"5511989813900"},
  {name:"R2 Motorsport", addr:"Pinheiros", zone:"Zona Oeste", cat:"Oficina", phone:"5511912803437"},
  {name:"TKGARAGE Funilaria e Mecânica", addr:"Pompeia", zone:"Zona Oeste", cat:"Oficina", phone:"5511953949770"},
  {name:"Driver Oficina Mecânica", addr:"Pompeia", zone:"Zona Oeste", cat:"Oficina", phone:"5511913212222"},
  {name:"St. Chico", addr:"Pinheiros", zone:"Zona Oeste", cat:"Padaria", phone:"5511917643677"},
  {name:"Tu és Pão", addr:"Vila Madalena", zone:"Zona Oeste", cat:"Padaria", phone:"5511971070041"},
  {name:"Barbearia Marconi", addr:"Jardins", zone:"Zona Oeste", cat:"Barbearia", phone:"5511945724738"},
  {name:"Máfia Capital Barbearia Kids", addr:"Itaim Bibi", zone:"Zona Oeste", cat:"Barbearia", phone:"5511954917060"},
  {name:"Bonfim Flores", addr:"Cerqueira César", zone:"Zona Oeste", cat:"Floricultura", phone:"5511949674766"},
  {name:"Flores do Mercado", addr:"Pinheiros", zone:"Zona Oeste", cat:"Floricultura", phone:"5511980837827"},
  {name:"Mercado das Flores", addr:"Vila Leopoldina", zone:"Zona Oeste", cat:"Floricultura", phone:"5511997865267"},
  {name:"Confeitaria Marilia Zylbersztajn", addr:"Pinheiros", zone:"Zona Oeste", cat:"Confeitaria", phone:"5511965700094"},
  {name:"Saint Christ Store", addr:"Lapa", zone:"Zona Oeste", cat:"Loja de Roupas", phone:"5511917744118"},
  {name:"CALMA SAO PAULO", addr:"Vila Madalena", zone:"Zona Oeste", cat:"Loja de Roupas", phone:"5511949449647"},
  {name:"VS Fashion Store", addr:"Lapa", zone:"Zona Oeste", cat:"Loja de Roupas", phone:"5511981094632"},
  {name:"Studio Nails Maria Fernanda", addr:"Pinheiros", zone:"Zona Oeste", cat:"Nail Designer", phone:"5511970866449"},
  {name:"Bebelle Nail Spa", addr:"Pinheiros", zone:"Zona Oeste", cat:"Nail Designer", phone:"5511918743169"},
  {name:"Studio Mani", addr:"Bom Retiro", zone:"Zona Oeste", cat:"Nail Designer", phone:"5511945445150"},
  {name:"Y'All Burguer & BBQ", addr:"Perdizes", zone:"Zona Oeste", cat:"Hamburgueria", phone:"5511949500004"},
  {name:"Bubble Box Butantã", addr:"Butantã", zone:"Zona Oeste", cat:"Lavanderia", phone:"5511985908787"},
  {name:"Lavou Secou Lavanderia", addr:"Vila Leopoldina", zone:"Zona Oeste", cat:"Lavanderia", phone:"5511991964980"},
  {name:"#1 Lavanderia Alto da Lapa", addr:"Alto da Lapa", zone:"Zona Oeste", cat:"Lavanderia", phone:"5511998617780"},
  // ZONA LESTE
  {name:"88 Hair Style", addr:"Vila Rê / Penha", zone:"Zona Leste", cat:"Salão", phone:"5511995490442"},
  {name:"Espaço Karolyn Alves", addr:"Itaquera", zone:"Zona Leste", cat:"Salão", phone:"5511977648704"},
  {name:"MaluMaison D'Coiffeur", addr:"Vila Matilde", zone:"Zona Leste", cat:"Salão", phone:"5511973273784"},
  {name:"JL Auto Mecânica", addr:"Jardim Machado", zone:"Zona Leste", cat:"Oficina", phone:"5511962104836"},
  {name:"M&M Motors Oficina", addr:"Vila Londrina", zone:"Zona Leste", cat:"Oficina", phone:"5511940107711"},
  {name:"Mecânica Dragatto", addr:"Vila Diva", zone:"Zona Leste", cat:"Oficina", phone:"5511971068132"},
  {name:"Auto Mecânica Motor Leste", addr:"Chácara Belenzinho", zone:"Zona Leste", cat:"Oficina", phone:"5511983182118"},
  {name:"Floricultura Praça das Flores", addr:"Vila Talarico", zone:"Zona Leste", cat:"Floricultura", phone:"5511947685107"},
  {name:"Floricultura Flor Extra", addr:"Vila Rê", zone:"Zona Leste", cat:"Floricultura", phone:"5511958748311"},
  {name:"Floricultura Rosi Flores", addr:"Itaquera", zone:"Zona Leste", cat:"Floricultura", phone:"5511947620223"},
  {name:"R&G Flores", addr:"Tatuapé", zone:"Zona Leste", cat:"Floricultura", phone:"5511980789104"},
  {name:"Cia Animal Farm", addr:"Vila Matilde", zone:"Zona Leste", cat:"Pet Shop", phone:"5511931477578"},
  {name:"Wholesale Feed of Pit Bull", addr:"Vila Formosa", zone:"Zona Leste", cat:"Pet Shop", phone:"5511995933068"},
  {name:"PetShop / Banho e Tosa Rio Branco", addr:"Vila Rio Branco", zone:"Zona Leste", cat:"Pet Shop", phone:"5511959572183"},
  {name:"Camila Savi Nails", addr:"Vila Heliópolis", zone:"Zona Leste", cat:"Nail Designer", phone:"5511950787575"},
  // ZONA SUL
  {name:"Societá Hair Jardim Sul", addr:"Vila Andrade", zone:"Zona Sul", cat:"Salão", phone:"5511947300999"},
  {name:"Beleza Natural", addr:"Santo Amaro", zone:"Zona Sul", cat:"Salão", phone:"5511939174365"},
  {name:"Paris Vegas Beauty", addr:"Moema", zone:"Zona Sul", cat:"Salão", phone:"5511933723705"},
  {name:"Fá Sant'ana Espaço de Beleza", addr:"Americanópolis", zone:"Zona Sul", cat:"Salão", phone:"5511965278677"},
  {name:"Rpm Reparação Automotiva", addr:"Vila Santa Catarina", zone:"Zona Sul", cat:"Oficina", phone:"5511985614211"},
  {name:"Auto Center Kimiko", addr:"Bosque da Saúde", zone:"Zona Sul", cat:"Oficina", phone:"5511955866874"},
  {name:"WM Auto Center", addr:"Pedreira", zone:"Zona Sul", cat:"Oficina", phone:"5511940306077"},
  {name:"TSX Barbearia", addr:"Vila Olímpia", zone:"Zona Sul", cat:"Barbearia", phone:"5511999434797"},
  {name:"Dom Ladino Barber Experience", addr:"Campo Belo", zone:"Zona Sul", cat:"Barbearia", phone:"5511914563700"},
  {name:"Drip & Cut Barber Co.", addr:"Vila Mariana", zone:"Zona Sul", cat:"Barbearia", phone:"5511997530289"},
  {name:"Dom Ladino", addr:"Chácara Sto Antônio", zone:"Zona Sul", cat:"Barbearia", phone:"5511994900079"},
  {name:"Confeitaria Urbana", addr:"Vila Guarani", zone:"Zona Sul", cat:"Confeitaria", phone:"5511973794876"},
  {name:"Delicité Confeitaria", addr:"Village Panamby / Vila Andrade", zone:"Zona Sul", cat:"Confeitaria", phone:"5511951440443"},
  {name:"Doces Zona Sul", addr:"Parque Maria Helena", zone:"Zona Sul", cat:"Confeitaria", phone:"5511977546024"},
  {name:"Love Boutique", addr:"Vila Santa Lucia", zone:"Zona Sul", cat:"Loja de Roupas", phone:"5511984618309"},
  {name:"MOB Shopping Plaza Sul", addr:"Bosque da Saúde", zone:"Zona Sul", cat:"Loja de Roupas", phone:"5511957729495"},
  {name:"Lofty Style", addr:"Vila Andrade", zone:"Zona Sul", cat:"Loja de Roupas", phone:"5511976560409"},
  {name:"Espaço 7 14 Nails", addr:"Moema", zone:"Zona Sul", cat:"Nail Designer", phone:"5511939555283"},
  {name:"Cosmopolish Nail Bar", addr:"Moema", zone:"Zona Sul", cat:"Nail Designer", phone:"5511932311441"},
  {name:"Lavanderia Alvorada", addr:"Jardim Celeste", zone:"Zona Sul", cat:"Lavanderia", phone:"5511992060328"},
  {name:"Lavô Secô Lavanderia Express", addr:"Jardim Maria Duarte", zone:"Zona Sul", cat:"Lavanderia", phone:"5511978866863"},
  {name:"Cris Laverie", addr:"Campo Belo", zone:"Zona Sul", cat:"Lavanderia", phone:"5511999745141"},
  {name:"5àsec Shopping Jardim Sul", addr:"Vila Andrade", zone:"Zona Sul", cat:"Lavanderia", phone:"5511985855455"},
  // ZONA NORTE
  {name:"Studio Lins", addr:"Vila Ester", zone:"Zona Norte", cat:"Salão", phone:"5511978292910"},
  {name:"Fernando Lima Salão", addr:"Vila Isolina Mazzei", zone:"Zona Norte", cat:"Salão", phone:"5511918420112"},
  {name:"Fast Escova Casa Verde", addr:"Vila Ester", zone:"Zona Norte", cat:"Salão", phone:"5511922333575"},
  {name:"Espaço Marise Lima", addr:"Vila Isolina Mazzei", zone:"Zona Norte", cat:"Salão", phone:"5511983026410"},
  {name:"Studio de Beleza Thais Uehara", addr:"Vila Ester", zone:"Zona Norte", cat:"Salão", phone:"5511947893539"},
  {name:"Império da Beleza 1700", addr:"Vila Guilherme", zone:"Zona Norte", cat:"Salão", phone:"5511963528983"},
  {name:"Mecânica Horto Center", addr:"Parque Mandaqui", zone:"Zona Norte", cat:"Oficina", phone:"5511982042342"},
  {name:"Guia Norte - Continental Pneus", addr:"Vila Guilherme", zone:"Zona Norte", cat:"Oficina", phone:"5511971297227"},
  {name:"Guia Norte - Sikkens", addr:"Vila Maria Baixa", zone:"Zona Norte", cat:"Oficina", phone:"5511991885939"},
  {name:"Bosch Car Service - Guia Norte", addr:"Vila Guilherme", zone:"Zona Norte", cat:"Oficina", phone:"5511973809525"},
  {name:"H-Norte Oficina Honda", addr:"Vila Guilherme", zone:"Zona Norte", cat:"Oficina", phone:"5511974929898"},
  {name:"Barber 347", addr:"Santana", zone:"Zona Norte", cat:"Barbearia", phone:"5511954308579"},
  {name:"Barbearia Studio Original", addr:"Center Norte", zone:"Zona Norte", cat:"Barbearia", phone:"5511916070011"},
  {name:"Barber North Coast", addr:"Imirim", zone:"Zona Norte", cat:"Barbearia", phone:"5511996487304"},
  {name:"Barbearia Premium Don Pablo", addr:"Santana", zone:"Zona Norte", cat:"Barbearia", phone:"5511941437128"},
  {name:"Barbearia Zona Norte", addr:"Santana", zone:"Zona Norte", cat:"Barbearia", phone:"5511953960159"},
  {name:"Villa das Artes Flores", addr:"Imirim", zone:"Zona Norte", cat:"Floricultura", phone:"5511965212237"},
  {name:"Floricultura Santana", addr:"Imirim", zone:"Zona Norte", cat:"Floricultura", phone:"5511999286696"},
  {name:"Vip Flowers", addr:"Imirim", zone:"Zona Norte", cat:"Floricultura", phone:"5511980201050"},
  {name:"Camélia Flores e Presentes", addr:"Mandaqui", zone:"Zona Norte", cat:"Floricultura", phone:"5511989859660"},
  {name:"Fernanda Rabelo Nails", addr:"Vila Primavera", zone:"Zona Norte", cat:"Nail Designer", phone:"5511986979803"},
  {name:"Studio Ana Moreira", addr:"Vila Penteado", zone:"Zona Norte", cat:"Nail Designer", phone:"5511994302015"},
];

function buildMessage(name){
  return `Olá! Aqui é o Juan, da Nexo 👋 Vi que o ${name} ainda não tem um site e a gente cria sites profissionais para negócios locais aqui em SP. Posso te mandar uma proposta rápida sem compromisso?`;
}

const grid = document.getElementById('grid');
const countEl = document.getElementById('count');
const zoneFilter = document.getElementById('zoneFilter');
const catFilter = document.getElementById('catFilter');
const search = document.getElementById('search');

const cats = [...new Set(businesses.map(b=>b.cat))].sort();
catFilter.innerHTML += cats.map(c=>`<option value="${c}">${c}</option>`).join('');

function render(){
  const z = zoneFilter.value, c = catFilter.value, q = search.value.trim().toLowerCase();
  const filtered = businesses.filter(b=>{
    const mz = !z || b.zone === z;
    const mc = !c || b.cat === c;
    const mq = !q || b.name.toLowerCase().includes(q) || b.addr.toLowerCase().includes(q);
    return mz && mc && mq;
  });
  countEl.textContent = filtered.length + ' de ' + businesses.length + ' estabelecimento(s)';
  grid.innerHTML = filtered.map(b=>{
    const msg = encodeURIComponent(buildMessage(b.name));
    const link = `https://wa.me/${b.phone}?text=${msg}`;
    return `
    <div class="card">
      <div class="info">
        <div class="name">${b.name}</div>
        <div class="meta">${b.addr}</div>
        <div class="tags"><span class="tag">${b.zone}</span><span class="tag cat">${b.cat}</span></div>
      </div>
      <div class="actions">
        <a class="btn" href="${link}" target="_blank" rel="noopener">Abrir no WhatsApp</a>
        <button class="btn copy" onclick="copyMsg(this, '${b.name.replace(/'/g,"\\'")}')">Copiar mensagem</button>
      </div>
    </div>`;
  }).join('');
}

function copyMsg(btn, name){
  const msg = buildMessage(name);
  navigator.clipboard.writeText(msg).then(()=>{
    const original = btn.textContent;
    btn.textContent = 'Copiado ✓';
    btn.classList.add('done');
    setTimeout(()=>{btn.textContent = original; btn.classList.remove('done');}, 1800);
  });
}

zoneFilter.addEventListener('change', render);
catFilter.addEventListener('change', render);
search.addEventListener('input', render);
render();
</script>
</body>
</html>
