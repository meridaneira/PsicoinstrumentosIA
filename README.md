
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="description" content="PsicoInstrumenta AI: apoyo a la investigación psicométrica y organización de evidencia científica.">
<title>PsicoInstrumenta AI</title>
<style>
:root{--navy:#12345a;--blue:#1769aa;--light:#eef5fc;--border:#d8e4f0;--text:#20344d;--muted:#65788d;--green:#16835c}
*{box-sizing:border-box}
body{margin:0;font:15px Arial,sans-serif;color:var(--text);background:#f4f7fb}
button,input,textarea,select{font:inherit}
button{cursor:pointer;border:0;border-radius:7px;padding:10px 14px;background:var(--blue);color:white}
button.secondary{background:#e6eff9;color:var(--navy)}
button.danger{background:#a83242}
input,textarea,select{width:100%;padding:10px;border:1px solid var(--border);border-radius:7px;background:white;color:var(--text)}
textarea{min-height:90px;resize:vertical}
label{display:block;font-weight:600;margin:12px 0 6px}
header{background:var(--navy);color:white;padding:20px 24px;display:flex;justify-content:space-between;align-items:center;gap:15px;flex-wrap:wrap}
header h1{margin:0;font-size:24px}
header p{margin:7px 0 0;color:#d5e6f7}
.layout{display:grid;grid-template-columns:225px minmax(0,1fr);min-height:calc(100vh - 90px)}
aside{background:#173b61;padding:20px 12px}
aside button{display:block;width:100%;text-align:left;margin:5px 0;background:transparent;color:#eaf3ff}
aside button.active,aside button:hover{background:#2c6598}
main{padding:25px;min-width:0}
.panel{background:white;border:1px solid var(--border);border-radius:12px;padding:20px;margin-bottom:18px;box-shadow:0 2px 8px #183b6008}
h2{margin:0 0 12px;color:var(--navy)}
h3{color:var(--navy)}
.muted{color:var(--muted);line-height:1.6}
.cards{display:grid;grid-template-columns:repeat(auto-fit,minmax(180px,1fr));gap:14px}
.card{padding:18px;border:1px solid var(--border);border-radius:10px;background:#fbfdff}
.card strong{display:block;margin-bottom:8px;color:var(--navy)}
.grid2{display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:12px}
.actions{display:flex;flex-wrap:wrap;gap:8px;margin-top:14px}
.section{display:none}.section.active{display:block}
table{width:100%;border-collapse:collapse;font-size:13px}
th,td{text-align:left;padding:10px;border-bottom:1px solid var(--border);vertical-align:top;overflow-wrap:anywhere}
th{background:var(--light);color:var(--navy)}
.table-wrap{overflow-x:auto}
.badge{display:inline-block;background:#e3f5ed;color:#17694d;padding:4px 7px;border-radius:5px;font-size:12px}
.notice{padding:12px;background:#edf6ff;border-left:4px solid var(--blue);border-radius:5px;line-height:1.5}
footer{padding:16px;color:var(--muted);font-size:12px}
a{color:var(--blue)}
@media(max-width:720px){.layout{grid-template-columns:1fr}aside{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:4px}aside button{font-size:13px;padding:10px}main{padding:12px}header{padding:18px}}
</style>
</head>
<body>
<header>
 <div><h1>🧠 PsicoInstrumenta AI</h1><p>Ciencia · Evidencia · Instrumentos</p></div>
 <div id="saveStatus">Espacio de trabajo local</div>
</header>
<div class="layout">
<aside>
 <button class="active" data-page="home">⌂ Inicio</button>
 <button data-page="search">⌕ Buscar instrumentos</button>
 <button data-page="matrix">▦ Matriz de instrumentos</button>
 <button data-page="model">◇ Modelo conceptual</button>
 <button data-page="items">☷ Banco de ítems</button>
 <button data-page="quality">✓ Control de calidad</button>
</aside>
<main>
<section id="home" class="section active">
 <div class="panel">
  <h2>Bienvenido a PsicoInstrumenta AI</h2>
  <p class="muted">Organiza antecedentes, revisa instrumentos existentes y desarrolla propuestas de medición con rigor metodológico.</p>
  <div class="notice">Esta herramienta apoya la investigación. No sustituye la revisión de artículos originales, los permisos de uso ni la evaluación psicométrica profesional.</div>
 </div>
 <div class="cards">
  <div class="card"><strong>Buscar instrumentos</strong><p class="muted">Explora fuentes bibliográficas académicas.</p><button onclick="showPage('search')">Abrir búsqueda</button></div>
  <div class="card"><strong>Matriz de evidencia</strong><p class="muted">Registra y compara instrumentos.</p><button onclick="showPage('matrix')">Abrir matriz</button></div>
  <div class="card"><strong>Modelo conceptual</strong><p class="muted">Define constructos y dimensiones.</p><button onclick="showPage('model')">Definir modelo</button></div>
  <div class="card"><strong>Banco de ítems</strong><p class="muted">Organiza ítems candidatos por dimensión.</p><button onclick="showPage('items')">Crear ítems</button></div>
 </div>
 <div class="panel" style="margin-top:18px">
  <h3>Datos del proyecto</h3>
  <div class="grid2">
   <div><label for="projectTitle">Título</label><input id="projectTitle" placeholder="Nombre de la investigación"></div>
   <div><label for="construct">Constructo</label><input id="construct" placeholder="Ej. gratificación instantánea"></div>
   <div><label for="population">Población</label><input id="population" placeholder="Ej. estudiantes universitarios"></div>
   <div><label for="objective">Objetivo</label><input id="objective" placeholder="Objetivo principal"></div>
  </div>
  <div class="actions"><button onclick="saveProject()">Guardar proyecto</button></div>
 </div>
</section>

<section id="search" class="section">
 <div class="panel">
  <h2>Buscar instrumentos y publicaciones</h2>
  <p class="muted">Escribe el constructo o el nombre de un instrumento. Se abrirán búsquedas en fuentes externas; revisa los artículos originales y la calidad de la evidencia.</p>
  <label for="query">Términos de búsqueda</label><input id="query" placeholder="Ej. escala de regulación emocional, validación, Perú">
  <div class="actions">
   <button onclick="searchWeb('https://scholar.google.com/scholar?q=')">Google Scholar</button>
   <button onclick="searchWeb('https://pubmed.ncbi.nlm.nih.gov/?term=')">PubMed</button>
   <button onclick="searchWeb('https://api.openalex.org/works?search=')">OpenAlex</button>
   <button onclick="searchWeb('https://search.crossref.org/?q=')">Crossref</button>
  </div>
  <p class="muted">Consejo: combina constructo, nombre del instrumento, población, país y términos como validación, confiabilidad o validez.</p>
 </div>
 <div class="panel">
  <h3>Ejemplo de estrategia</h3>
  <p><code>"nombre del constructo" AND (escala OR cuestionario) AND (validación OR psychometric properties)</code></p>
  <p class="muted">Anota la base consultada, fecha de búsqueda y criterios de inclusión en tu protocolo de revisión.</p>
 </div>
</section>

<section id="matrix" class="section">
 <div class="panel">
  <h2>Matriz de instrumentos</h2>
  <form id="instrumentForm">
   <div class="grid2">
    <div><label for="iName">Nombre del instrumento *</label><input id="iName" required></div>
    <div><label for="iAuthors">Autores</label><input id="iAuthors"></div>
    <div><label for="iYear">Año</label><input id="iYear" type="number" min="1800" max="2200"></div>
    <div><label for="iCountry">País / población</label><input id="iCountry"></div>
    <div><label for="iDimensions">Dimensiones</label><input id="iDimensions"></div>
    <div><label for="iReliability">Confiabilidad (dato reportado)</label><input id="iReliability" placeholder="Ej. alfa, omega; valor y fuente"></div>
   </div>
   <label for="iValidity">Evidencias de validez y limitaciones</label><textarea id="iValidity"></textarea>
   <label for="iLink">DOI o enlace al artículo</label><input id="iLink" type="url" placeholder="https://doi.org/...">
   <div class="actions"><button type="submit">Añadir instrumento</button><button type="button" class="secondary" onclick="exportCSV()">Exportar CSV</button><button type="button" class="secondary" onclick="exportJSON()">Exportar proyecto JSON</button></div>
  </form>
 </div>
 <div class="panel">
  <h3>Instrumentos registrados</h3>
  <div class="table-wrap"><table><thead><tr><th>Instrumento</th><th>Autores / año</th><th>Población</th><th>Dimensiones</th><th>Evidencia</th><th>Enlace</th><th>Acción</th></tr></thead><tbody id="instrumentRows"></tbody></table></div>
  <p class="muted" id="instrumentCount">No hay registros.</p>
 </div>
</section>

<section id="model" class="section">
 <div class="panel">
  <h2>Modelo conceptual</h2>
  <label for="modelDefinition">Definición conceptual del constructo</label><textarea id="modelDefinition" placeholder="Define el constructo a partir de literatura científica y delimita lo que no incluye."></textarea>
  <label for="modelDimensions">Dimensiones propuestas</label><textarea id="modelDimensions" placeholder="Una dimensión por línea, acompañada de su definición teórica."></textarea>
  <label for="modelOperational">Definición operacional</label><textarea id="modelOperational" placeholder="Explica cómo se observará o medirá el constructo."></textarea>
  <div class="actions"><button onclick="saveModel()">Guardar modelo</button><button class="secondary" onclick="downloadModel()">Exportar modelo TXT</button></div>
 </div>
 <div class="notice">Las dimensiones son hipótesis de trabajo hasta que se justifiquen teóricamente y se sometan a evaluación empírica.</div>
</section>

<section id="items" class="section">
 <div class="panel">
  <h2>Banco de ítems</h2>
  <form id="itemForm">
   <label for="itemDimension">Dimensión *</label><input id="itemDimension" required>
   <label for="itemText">Ítem candidato *</label><textarea id="itemText" required placeholder="Escribe una afirmación o pregunta clara y de una sola idea."></textarea>
   <div class="grid2">
    <div><label for="itemScale">Formato de respuesta</label><select id="itemScale"><option>Likert 5 puntos</option><option>Likert 7 puntos</option><option>Sí / No</option><option>Frecuencia</option><option>Otro / por definir</option></select></div>
    <div><label for="itemStatus">Estado</label><select id="itemStatus"><option>Candidato</option><option>Revisar con expertos</option><option>Revisado</option><option>Descartado</option></select></div>
   </div>
   <label for="itemRationale">Justificación teórica / fuente</label><textarea id="itemRationale"></textarea>
   <div class="actions"><button type="submit">Añadir ítem</button><button type="button" class="secondary" onclick="exportItems()">Exportar ítems CSV</button></div>
  </form>
 </div>
 <div class="panel">
  <h3>Ítems registrados</h3>
  <div class="table-wrap"><table><thead><tr><th>Dimensión</th><th>Ítem</th><th>Respuesta</th><th>Estado</th><th>Justificación</th><th>Acción</th></tr></thead><tbody id="itemRows"></tbody></table></div>
  <p class="muted" id="itemCount">No hay ítems.</p>
 </div>
</section>

<section id="quality" class="section">
 <div class="panel">
  <h2>Control de calidad metodológica</h2>
  <p class="muted">Marca los pasos completados. Esta lista organiza el trabajo, pero no certifica la calidad ni la validez del instrumento.</p>
  <div id="checks">
   <label><input type="checkbox" style="width:auto"> Definición conceptual respaldada por bibliografía.</label>
   <label><input type="checkbox" style="width:auto"> Búsqueda de instrumentos existentes documentada.</label>
   <label><input type="checkbox" style="width:auto"> Permisos de uso y derechos de autor revisados.</label>
   <label><input type="checkbox" style="width:auto"> Evidencia pertinente para la población objetivo.</label>
   <label><input type="checkbox" style="width:auto"> Revisión de contenido por expertos planificada.</label>
   <label><input type="checkbox" style="width:auto"> Entrevistas cognitivas o prueba piloto planificadas.</label>
   <label><input type="checkbox" style="width:auto"> Plan de análisis de confiabilidad y validez establecido.</label>
   <label><input type="checkbox" style="width:auto"> Ética, consentimiento y protección de datos revisados.</label>
  </div>
  <p id="checkCount" class="badge">0 de 8 completados</p>
  <div class="actions"><button onclick="saveChecks()">Guardar checklist</button></div>
 </div>
</section>

<div class="panel">
 <h3>Copias de seguridad</h3>
 <p class="muted">Los datos se guardan en este navegador. Exporta el proyecto JSON periódicamente para evitar perder tus registros. El JSON puede importarse en este mismo artefacto.</p>
 <div class="actions"><button onclick="exportJSON()">Descargar copia JSON</button><button class="secondary" onclick="document.getElementById('importFile').click()">Importar JSON</button><input id="importFile" type="file" accept=".json,application/json" style="display:none" onchange="importJSON(event)"></div>
</div>
<footer>PsicoInstrumenta AI · Herramienta de apoyo a la investigación científica. La inclusión en la matriz no implica validación psicométrica.</footer>
</main>
</div>
<script>
const KEY='psicoinstrumentaAI_v1';
let data={project:{},model:{},instruments:[],items:[],checks:[]};
function load(){try{const x=JSON.parse(localStorage.getItem(KEY)||'null');if(x)data={...data,...x}}catch(e){};fillProject();fillModel();renderInstruments();renderItems();fillChecks()}
function persist(){try{localStorage.setItem(KEY,JSON.stringify(data));document.getElementById('saveStatus').textContent='Guardado en este navegador'}catch(e){alert('No se pudo guardar en el navegador. Exporta tus datos como JSON.')}} 
function showPage(id){document.querySelectorAll('.section').forEach(x=>x.classList.toggle('active',x.id===id));document.querySelectorAll('aside button').forEach(x=>x.classList.toggle('active',x.dataset.page===id));window.scrollTo({top:0,behavior:'smooth'})}
document.querySelectorAll('aside button[data-page]').forEach(b=>b.addEventListener('click',()=>showPage(b.dataset.page)));
function searchWeb(base){const q=document.getElementById('query').value.trim();if(!q){alert('Escribe los términos de búsqueda.');return}window.open(base+encodeURIComponent(q),'_blank','noopener')}
function saveProject(){data.project={title:val('projectTitle'),construct:val('construct'),population:val('population'),objective:val('objective')};persist();alert('Proyecto guardado.')}
function fillProject(){for(const k of ['title','construct','population','objective'])setVal({title:'projectTitle',construct:'construct',population:'population',objective:'objective'}[k],data.project[k]||'')}
function saveModel(){data.model={definition:val('modelDefinition'),dimensions:val('modelDimensions'),operational:val('modelOperational')};persist();alert('Modelo conceptual guardado.')}
function fillModel(){setVal('modelDefinition',data.model.definition||'');setVal('modelDimensions',data.model.dimensions||'');setVal('modelOperational',data.model.operational||'')}
document.getElementById('instrumentForm').addEventListener('submit',e=>{e.preventDefault();data.instruments.push({id:Date.now()+Math.random(),name:val('iName'),authors:val('iAuthors'),year:val('iYear'),country:val('iCountry'),dimensions:val('iDimensions'),reliability:val('iReliability'),validity:val('iValidity'),link:val('iLink')});e.target.reset();persist();renderInstruments()});
function renderInstruments(){const body=document.getElementById('instrumentRows');body.replaceChildren();data.instruments.forEach(x=>{const tr=document.createElement('tr');[x.name,(x.authors||'')+(x.year?' · '+x.year:''),x.country,x.dimensions,x.reliability+(x.validity?' · '+x.validity:'' )].forEach(t=>{const td=document.createElement('td');td.textContent=t||'—';tr.append(td)});const linktd=document.createElement('td');if(x.link){const a=document.createElement('a');a.href=x.link;a.target='_blank';a.rel='noopener';a.textContent='Abrir';linktd.append(a)}else linktd.textContent='—';tr.append(linktd);const action=document.createElement('td');const b=document.createElement('button');b.className='danger';b.textContent='Eliminar';b.onclick=()=>{if(confirm('¿Eliminar este registro?')){data.instruments=data.instruments.filter(y=>y.id!==x.id);persist();renderInstruments()}};action.append(b);tr.append(action);body.append(tr)});document.getElementById('instrumentCount').textContent=data.instruments.length+' instrumento(s) registrados.'}
document.getElementById('itemForm').addEventListener('submit',e=>{e.preventDefault();data.items.push({id:Date.now()+Math.random(),dimension:val('itemDimension'),text:val('itemText'),scale:val('itemScale'),status:val('itemStatus'),rationale:val('itemRationale')});e.target.reset();persist();renderItems()});
function renderItems(){const body=document.getElementById('itemRows');body.replaceChildren();data.items.forEach(x=>{const tr=document.createElement('tr');[x.dimension,x.text,x.scale,x.status,x.rationale].forEach(t=>{const td=document.createElement('td');td.textContent=t||'—';tr.append(td)});const td=document.createElement('td'),b=document.createElement('button');b.className='danger';b.textContent='Eliminar';b.onclick=()=>{if(confirm('¿Eliminar este ítem?')){data.items=data.items.filter(y=>y.id!==x.id);persist();renderItems()}};td.append(b);tr.append(td);body.append(tr)});document.getElementById('itemCount').textContent=data.items.length+' ítem(s) registrados.'}
function fillChecks(){document.querySelectorAll('#checks input').forEach((x,i)=>x.checked=!!data.checks[i]);updateCheckCount()}
function updateCheckCount(){const a=[...document.querySelectorAll('#checks input')];const n=a.filter(x=>x.checked).length;document.getElementById('checkCount').textContent=n+' de '+a.length+' completados'}
function saveChecks(){data.checks=[...document.querySelectorAll('#checks input')].map(x=>x.checked);persist();updateCheckCount();alert('Checklist guardado.')}
document.querySelectorAll('#checks input').forEach(x=>x.addEventListener('change',()=>{updateCheckCount();data.checks=[...document.querySelectorAll('#checks input')].map(y=>y.checked);persist()}));
function val(id){return document.getElementById(id).value.trim()}
function setVal(id,v){document.getElementById(id).value=v}
function download(name,content,type){const blob=new Blob([content],{type});const a=document.createElement('a');const url=URL.createObjectURL(blob);a.href=url;a.download=name;document.body.append(a);a.click();a.remove();setTimeout(()=>URL.revokeObjectURL(url),1000)}
function exportJSON(){saveProject();data.model={definition:val('modelDefinition'),dimensions:val('modelDimensions'),operational:val('modelOperational')};data.checks=[...document.querySelectorAll('#checks input')].map(x=>x.checked);download('psicoinstrumenta-proyecto.json',JSON.stringify(data,null,2),'application/json')}
function csv(rows){return rows.map(r=>r.map(v=>'"'+String(v??'').replace(/"/g,'""')+'"').join(',')).join('\r\n')}
function exportCSV(){const rows=[['Instrumento','Autores','Año','País/población','Dimensiones','Confiabilidad','Validez/limitaciones','Enlace'],...data.instruments.map(x=>[x.name,x.authors,x.year,x.country,x.dimensions,x.reliability,x.validity,x.link])];download('matriz-instrumentos.csv','\uFEFF'+csv(rows),'text/csv;charset=utf-8')}
function exportItems(){const rows=[['Dimensión','Ítem','Formato de respuesta','Estado','Justificación'],...data.items.map(x=>[x.dimension,x.text,x.scale,x.status,x.rationale])];download('banco-items.csv','\uFEFF'+csv(rows),'text/csv;charset=utf-8')}
function downloadModel(){const m=data.model;download('modelo-conceptual.txt','DEFINICIÓN CONCEPTUAL\n'+val('modelDefinition')+'\n\nDIMENSIONES\n'+val('modelDimensions')+'\n\nDEFINICIÓN OPERACIONAL\n'+val('modelOperational'),'text/plain;charset=utf-8')}
function importJSON(e){const f=e.target.files[0];if(!f)return;const reader=new FileReader();reader.onload=()=>{try{const incoming=JSON.parse(reader.result);if(!incoming||!Array.isArray(incoming.instruments)||!Array.isArray(incoming.items))throw Error();if(!confirm('Importar reemplazará los datos actuales de esta aplicación. ¿Continuar?'))return;data={project:{},model:{},instruments:[],items:[],checks:[],...incoming};persist();load();alert('Proyecto importado.')}catch(err){alert('El archivo no parece ser un proyecto JSON válido de PsicoInstrumenta AI.')}e.target.value=''};reader.readAsText(f)}
load();
</script>
</body>
</html>
