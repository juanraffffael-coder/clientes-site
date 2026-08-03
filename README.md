<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Nexo — Prospecção SP v5</title>
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
    <div class="brand">Nexo · Prospecção v5</div>
    <h1>78 estabelecimentos novos — SP</h1>
    <p class="sub">Sem repetir nenhuma leva anterior (30 + 82 + 63 = 175 já contatados). Todas as 4 zonas, número celular.</p>
    <div class="notice">
      <b>Nota honesta:</b> pediu 100, cheguei em 78 de qualidade (celular, sem duplicar, com endereço real). Passei por dentista, contador, salão de festas, colchoaria, marcenaria, serralheria, auto elétrica, funilaria, estética, idiomas, música, eletrônicos, assistência técnica, gráfica, açaiteria e costureira pra cobrir isso — nichos óbvios (salão, oficina, pilates etc.) já foram usados nas levas 2 e 3. Posso abrir mais nichos se quiser fechar os 22 que faltam.
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
  <footer>Gerado para a Nexo — leva 4, números filtrados por formato celular.</footer>
</div>

<script>
const businesses = [
  {name:"JP Bike Shop", addr:"Butantã", zone:"Zona Oeste", cat:"Bicicletaria", phone:"5511973503630"},
  {name:"Pastelaria Brasileira", addr:"Pompeia", zone:"Zona Oeste", cat:"Pastelaria", phone:"5511988318737"},
  {name:"Buzina Burgers", addr:"Pinheiros", zone:"Zona Oeste", cat:"Hamburgueria", phone:"5511988457550"},
  {name:"Cavalcanti Hortifruti", addr:"Jardim Boa Vista", zone:"Zona Oeste", cat:"Hortifruti", phone:"5511971746595"},
  {name:"Studio Yoga Iyengar", addr:"Pinheiros", zone:"Zona Oeste", cat:"Yoga", phone:"5511957981766"},
  {name:"Hot Yoga São Paulo", addr:"Pinheiros", zone:"Zona Oeste", cat:"Yoga", phone:"5511998306465"},
  {name:"Studio Goa Sol HotYoga", addr:"Água Branca", zone:"Zona Oeste", cat:"Yoga", phone:"5511959087822"},
  {name:"Portal do Sorriso", addr:"Pinheiros", zone:"Zona Oeste", cat:"Dentista", phone:"5511957168474"},
  {name:"Nazello Kovacs Odontologia", addr:"Vila Leopoldina", zone:"Zona Oeste", cat:"Dentista", phone:"5511943304995"},
  {name:"Viu Odontologia", addr:"Jardim Bonfiglioli", zone:"Zona Oeste", cat:"Dentista", phone:"5511951941032"},
  {name:"Candeloro Dental Studio", addr:"Água Branca", zone:"Zona Oeste", cat:"Dentista", phone:"5511972877480"},
  {name:"Espaço Moní", addr:"Alto de Pinheiros", zone:"Zona Oeste", cat:"Salão de Festas", phone:"5511953088881"},
  {name:"Casa Bartira", addr:"Perdizes", zone:"Zona Oeste", cat:"Salão de Festas", phone:"5511973828305"},
  {name:"Auto Electrical Jaguaré", addr:"Vila Lageado", zone:"Zona Oeste", cat:"Auto Elétrica", phone:"5511993203630"},
  {name:"Wizard Pinheiros", addr:"Pinheiros", zone:"Zona Oeste", cat:"Escola de Idiomas", phone:"5511945215664"},
  {name:"Native English Academy", addr:"Vila Indiana", zone:"Zona Oeste", cat:"Escola de Idiomas", phone:"5511985072103"},
  {name:"Gráfica Pinheiros Visual Pro", addr:"Pinheiros", zone:"Zona Oeste", cat:"Gráfica", phone:"5511961881742"},
  {name:"Borracharia Benoni 24 horas", addr:"Cidade Centenário", zone:"Zona Leste", cat:"Borracharia", phone:"5511970375226"},
  {name:"Tire 24 Hours", addr:"Vila Jacuí", zone:"Zona Leste", cat:"Borracharia", phone:"5511916635235"},
  {name:"Borracharia Lion Pneus e Rodas", addr:"Itaquera", zone:"Zona Leste", cat:"Borracharia", phone:"5511943410531"},
  {name:"Borracharia Brasil", addr:"São Miguel Paulista", zone:"Zona Leste", cat:"Borracharia", phone:"5511977511819"},
  {name:"Borracharia Reobote", addr:"Colônia", zone:"Zona Leste", cat:"Borracharia", phone:"5511974995292"},
  {name:"Line Duarte Loja de Fábrica", addr:"Jardim São Francisco", zone:"Zona Leste", cat:"Calçados", phone:"5511969421576"},
  {name:"Esperança Calçados Show", addr:"Artur Alvim", zone:"Zona Leste", cat:"Calçados", phone:"5511915417785"},
  {name:"Junior Calçados", addr:"Jardim Sta Terezinha", zone:"Zona Leste", cat:"Calçados", phone:"5511977445809"},
  {name:"Imobiliária Leste", addr:"São Miguel Paulista", zone:"Zona Leste", cat:"Imobiliária", phone:"5511977477000"},
  {name:"YOKOTA & XAVIER Odontologia", addr:"Zona Leste", zone:"Zona Leste", cat:"Dentista", phone:"5511948007313"},
  {name:"Geraldo Auto Elétrico", addr:"Parque Sta Madalena", zone:"Zona Leste", cat:"Auto Elétrica", phone:"5511948056513"},
  {name:"Auto Elétrico MM Romeiro Car", addr:"Artur Alvim", zone:"Zona Leste", cat:"Auto Elétrica", phone:"5511950001273"},
  {name:"Oficina Funilaria Marcone", addr:"Jardim da Conquista", zone:"Zona Leste", cat:"Funilaria e Pintura", phone:"5511985881363"},
  {name:"Laav Tatuapé Funilaria", addr:"Tatuapé", zone:"Zona Leste", cat:"Funilaria e Pintura", phone:"5511910671376"},
  {name:"Sander Car", addr:"Itaquera", zone:"Zona Leste", cat:"Funilaria e Pintura", phone:"5511914056867"},
  {name:"L.M.Car Funilaria", addr:"Limoeiro", zone:"Zona Leste", cat:"Funilaria e Pintura", phone:"5511985807624"},
  {name:"Instituto Maxwell", addr:"Jardim Sta Adelia", zone:"Zona Leste", cat:"Escola de Música", phone:"5511947495159"},
  {name:"Escola de Música Blues Club", addr:"Vila Diva", zone:"Zona Leste", cat:"Escola de Música", phone:"5511985120049"},
  {name:"Hamburgueria Zona Leste", addr:"Itaquera", zone:"Zona Leste", cat:"Hamburgueria", phone:"5511988797063"},
  {name:"Vidraçaria Casa & Vidro", addr:"Campo Grande", zone:"Zona Sul", cat:"Vidraçaria", phone:"5511972826409"},
  {name:"Vidraçaria Zona Sul", addr:"Jardim Zaira", zone:"Zona Sul", cat:"Vidraçaria", phone:"5511981699228"},
  {name:"GSV Vidraçaria & Molduras", addr:"Chácara Sto Antônio", zone:"Zona Sul", cat:"Vidraçaria", phone:"5511996152748"},
  {name:"Vidraçaria Sabará", addr:"Jardim Palmares", zone:"Zona Sul", cat:"Vidraçaria", phone:"5511940242004"},
  {name:"Urban Yoga", addr:"Vila Nova Conceição", zone:"Zona Sul", cat:"Yoga", phone:"5511942112872"},
  {name:"Nogal Escritório de Contabilidade", addr:"Chácara Sto Antônio", zone:"Zona Sul", cat:"Contador", phone:"5511992484644"},
  {name:"CESANTO Assessoria Empresarial", addr:"Campo Grande", zone:"Zona Sul", cat:"Contador", phone:"5511999342946"},
  {name:"Impacto Assessoria Contábil", addr:"Rio Bonito", zone:"Zona Sul", cat:"Contador", phone:"5511943232634"},
  {name:"Marcenaria Zona Sul", addr:"Capão Redondo", zone:"Zona Sul", cat:"Marcenaria", phone:"5511995187323"},
  {name:"Marcenaria Ishida", addr:"Morumbi", zone:"Zona Sul", cat:"Marcenaria", phone:"5511967970197"},
  {name:"Marcenaria Takal", addr:"Jardim Primavera", zone:"Zona Sul", cat:"Marcenaria", phone:"5511985665011"},
  {name:"E.M. Marcenaria", addr:"Jardim São Januário", zone:"Zona Sul", cat:"Marcenaria", phone:"5511952905959"},
  {name:"Refine Clínica de Estética", addr:"Chácara Sto Antônio", zone:"Zona Sul", cat:"Clínica de Estética", phone:"5511964274151"},
  {name:"Analaser", addr:"Chácara Sto Antônio", zone:"Zona Sul", cat:"Clínica de Estética", phone:"5511932011785"},
  {name:"Clínica Priscila Soares", addr:"Vila Moraes", zone:"Zona Sul", cat:"Clínica de Estética", phone:"5511998702883"},
  {name:"Karina Dall'oca Estética", addr:"Chucri Zaidan", zone:"Zona Sul", cat:"Clínica de Estética", phone:"5511914810559"},
  {name:"Soul Musa Clínica de Estética", addr:"Vila Andrade", zone:"Zona Sul", cat:"Clínica de Estética", phone:"5511988699014"},
  {name:"Eletronic Land", addr:"Vila Andrade", zone:"Zona Sul", cat:"Eletrônicos", phone:"5511940028835"},
  {name:"The Best Açaí", addr:"Vila Mascote", zone:"Zona Sul", cat:"Açaiteria", phone:"5511920905461"},
  {name:"Açaí Island Distribuidora", addr:"Santo Amaro", zone:"Zona Sul", cat:"Açaiteria", phone:"5511982120904"},
  {name:"Açaí Roots", addr:"Jardim São Francisco", zone:"Zona Sul", cat:"Açaiteria", phone:"5511981250706"},
  {name:"Serralheria na Zona Norte", addr:"Vila Nova Cachoeirinha", zone:"Zona Norte", cat:"Serralheria", phone:"5511948236457"},
  {name:"Henrimetal Serralheria", addr:"Casa Verde Alta", zone:"Zona Norte", cat:"Serralheria", phone:"5511954092563"},
  {name:"LNG Serralheria", addr:"Jardim Santa Cruz", zone:"Zona Norte", cat:"Serralheria", phone:"5511957181375"},
  {name:"Serralheria Art da Vila", addr:"Vila Maria Alta", zone:"Zona Norte", cat:"Serralheria", phone:"5511958536435"},
  {name:"SP Serralheria", addr:"Tucuruvi", zone:"Zona Norte", cat:"Serralheria", phone:"5511973833143"},
  {name:"Serralheria JMB", addr:"Vila Medeiros", zone:"Zona Norte", cat:"Serralheria", phone:"5511968098321"},
  {name:"Pastellicia ZN", addr:"Brasilândia", zone:"Zona Norte", cat:"Pastelaria", phone:"5511948626326"},
  {name:"Pastel da Sueli", addr:"Vila Medeiros", zone:"Zona Norte", cat:"Pastelaria", phone:"5511976441802"},
  {name:"Horti-Fruti Era Vegetal", addr:"Água Fria", zone:"Zona Norte", cat:"Hortifruti", phone:"5511996823011"},
  {name:"Contábil Norte", addr:"Santana", zone:"Zona Norte", cat:"Contador", phone:"5511988829158"},
  {name:"Dra. Thalita Araujo Estética", addr:"Vila Ester", zone:"Zona Norte", cat:"Clínica de Estética", phone:"5511919991260"},
  {name:"Sublimebio Tratamento de Vasinhos", addr:"Santana", zone:"Zona Norte", cat:"Clínica de Estética", phone:"5511914816718"},
  {name:"Clínica Márcia Cebelle", addr:"Carandiru", zone:"Zona Norte", cat:"Clínica de Estética", phone:"5511990206503"},
  {name:"M.Lan Estética Integrada", addr:"Limão", zone:"Zona Norte", cat:"Clínica de Estética", phone:"5511932348286"},
  {name:"A Norte Assistência Técnica", addr:"Casa Verde", zone:"Zona Norte", cat:"Assistência Técnica", phone:"5511958647376"},
  {name:"Conserta Smart Lauzane", addr:"Lauzane Paulista", zone:"Zona Norte", cat:"Assistência Técnica", phone:"5511943186758"},
  {name:"Tablet Hospital", addr:"Tucuruvi", zone:"Zona Norte", cat:"Assistência Técnica", phone:"5511944518305"},
  {name:"Atelier Acostureira", addr:"Santana", zone:"Zona Norte", cat:"Costureira", phone:"5511993873129"},
  {name:"Ateliê de Costura Elyzeth", addr:"Tremembé", zone:"Zona Norte", cat:"Costureira", phone:"5511989416179"},
];

function buildMessage(name){
  return `Olá! Aqui é o Juan, da Nexo. Vi que o ${name} não tem um site — isso significa clientes te procurando no Google e caindo direto na concorrência. Esse mês estamos com um desconto especial pra criação de sites. Posso te passar os detalhes?`;
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
