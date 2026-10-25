[secuencia2_decide_con_probabilidad.html](https://github.com/user-attachments/files/33930028/secuencia2_decide_con_probabilidad.html)
<!DOCTYPE html>
<html lang="es">
<head><meta charset="UTF-8"><meta name="viewport" content="width=device-width, initial-scale=1"><title>Decide con probabilidad | Secuencia 2</title>
<style>
:root{--ink:#19253a;--muted:#5d6b80;--blue:#3156a4;--teal:#16818a;--paper:#f5f7fb;--line:#dce4ef}
*{box-sizing:border-box}body{margin:0;background:var(--paper);color:var(--ink);font:16px/1.55 system-ui,Arial}
header{background:linear-gradient(120deg,#243d78,#16818a);color:#fff;padding:34px 20px}.wrap{max-width:1050px;margin:auto;padding:0 18px}
h1{font-size:clamp(2rem,5vw,3rem);line-height:1.1;margin:10px 0}header p{max-width:740px;color:#eafafa}
.tag{border:1px solid #ffffff80;border-radius:30px;padding:4px 12px;font-size:.85rem;display:inline-block}
nav{display:flex;gap:8px;flex-wrap:wrap;margin-top:18px}nav a{color:white;text-decoration:none;border:1px solid #ffffff80;padding:7px 12px;border-radius:20px}
main{padding:22px 0 48px}.card{background:#fff;border:1px solid var(--line);border-radius:16px;padding:22px;margin:16px 0;box-shadow:0 5px 18px #17345a0a}
h2{color:#254d8e;margin-top:0}h3{color:#3156a4}.grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(230px,1fr));gap:14px}
.note{background:#edf5ff;padding:12px 15px;border-left:4px solid var(--blue);border-radius:8px}
button,input,select{font:inherit;padding:9px 12px;border:1px solid #bac8da;border-radius:9px}button{background:var(--blue);color:#fff;border:0;font-weight:650;cursor:pointer}button.alt{background:#eaf0f8;color:var(--ink)}
.controls{display:flex;gap:10px;flex-wrap:wrap;align-items:center;margin:10px 0}
.result{font-size:1.1rem;font-weight:700;color:#176b69;margin-top:12px}
table{width:100%;border-collapse:collapse;margin:12px 0}td,th{border:1px solid var(--line);padding:8px;text-align:center}
.tree{display:flex;gap:8px;flex-wrap:wrap}.pill{background:#e9f4f4;padding:7px 11px;border-radius:20px}
.question{background:#f7f9fc;padding:14px;border-radius:10px;margin:12px 0}
small,.muted{color:var(--muted)}footer{text-align:center;color:var(--muted);padding:20px}
</style></head><body>
<header><div class="wrap"><span class="tag">Matemáticas · Grado 10.º · Secuencia 2</span><h1>Decide con probabilidad</h1>
<p>Resuelve retos de eventos simples y compuestos. Usa tablas, diagramas de árbol y simulaciones para comprender cómo se combinan los resultados.</p>
<nav><a href="#ideas">Conceptos</a><a href="#dados">Dos dados</a><a href="#ropa">Combinaciones</a><a href="#bolas">Extracción</a><a href="#quiz">Evaluación</a></nav></div></header>
<main class="wrap">
<section class="card" id="ideas"><h2>1. Caja de herramientas</h2><div class="grid">
<div class="note"><b>Eventos compuestos</b><br>Involucran dos o más condiciones o resultados.</div>
<div class="note"><b>Principio de conteo</b><br>Si una elección tiene m opciones y otra n, hay m × n combinaciones.</div>
<div class="note"><b>Eventos excluyentes</b><br>No pueden ocurrir al mismo tiempo. P(A ∪ B) = P(A) + P(B).</div>
<div class="note"><b>Eventos independientes</b><br>Uno no modifica al otro. P(A ∩ B) = P(A) × P(B).</div>
<div class="note"><b>Eventos dependientes</b><br>El primer resultado cambia las posibilidades del siguiente. P(A ∩ B) = P(A) × P(B|A).</div>
<div class="note"><b>Diagrama de árbol</b><br>Organiza las posibilidades de un experimento por etapas.</div></div>
<p><b>Atención:</b> la fórmula clásica P(A) = casos favorables / casos posibles se aplica cuando los resultados elementales son igualmente probables.</p></section>

<section class="card" id="dados"><h2>2. Reto 1: suma de dos dados</h2><p>Se lanzan dos dados equilibrados. Hay 36 parejas ordenadas posibles. Explora cuántas producen cada suma.</p>
<div class="controls"><button onclick="rollDice()">Simular 1 lanzamiento</button><button class="alt" onclick="manyDice()">Simular 1.000 lanzamientos</button><button class="alt" onclick="resetDice()">Reiniciar</button></div>
<div class="grid"><div class="note"><b>Resultado del último lanzamiento</b><div class="result" id="last">—</div></div><div class="note"><b>Frecuencia de suma 7</b><div class="result" id="freq7">0 de 0</div><small id="freqpct">0 %</small></div></div>
<table><thead><tr><th>Suma</th><th>Combinaciones favorables</th><th>Probabilidad teórica</th></tr></thead><tbody id="sumtable"></tbody></table>
<p class="note"><b>Piensa:</b> ¿por qué obtener 7 es más probable que obtener 12? Explica usando las parejas posibles.</p></section>

<section class="card" id="ropa"><h2>3. Reto 2: combinaciones de prendas</h2><p>Hay tres camisetas (roja, azul y blanca) y dos pantalones (negro y gris). Elige una prenda de cada tipo.</p>
<div class="controls"><button onclick="showCombos()">Mostrar todas las combinaciones</button></div><div id="combos" class="tree"><span class="muted">Pulsa el botón para explorar las 6 combinaciones.</span></div>
<p class="result" id="comboresult"></p><p>¿Cuál es la probabilidad de elegir una combinación con camiseta roja? <b>2/6 = 1/3</b>, porque hay dos combinaciones con camiseta roja entre seis posibles.</p></section>

<section class="card" id="bolas"><h2>4. Reto 3: extracción sin reemplazo</h2><p>Una bolsa contiene 4 bolas verdes y 3 amarillas. Se extraen dos bolas sin devolver la primera.</p>
<div class="grid"><div class="note"><b>Primera extracción verde</b><p>Hay 4 verdes de 7 bolas: P(V₁) = 4/7.</p></div><div class="note"><b>Segunda verde, sabiendo que la primera fue verde</b><p>Quedan 3 verdes entre 6 bolas: P(V₂|V₁) = 3/6.</p></div></div>
<p><b>Probabilidad de dos verdes:</b> (4/7) × (3/6) = 12/42 = 2/7 ≈ 28,6 %.</p>
<div class="controls"><button onclick="drawUrn()">Simular extracción</button><button class="alt" onclick="resetUrn()">Reiniciar contador</button></div>
<div class="result" id="urnlast">Realiza una extracción para ver el resultado.</div><p id="urncount" class="muted">Simulaciones: 0 · Dos verdes: 0</p>
<p class="note">En cada simulación se repone el contenido completo de la bolsa antes de comenzar una nueva pareja de extracciones; dentro de cada pareja no hay reemplazo.</p></section>

<section class="card" id="quiz"><h2>5. Comprueba lo aprendido</h2>
<div class="question"><b>1. Al lanzar dos monedas, ¿cuántos resultados ordenados hay?</b><br><label><input type="radio" name="q1" value="a"> 2</label><br><label><input type="radio" name="q1" value="b"> 4</label><br><label><input type="radio" name="q1" value="c"> 6</label></div>
<div class="question"><b>2. Si A y B son independientes, entonces:</b><br><label><input type="radio" name="q2" value="a"> P(A ∩ B) = P(A) × P(B)</label><br><label><input type="radio" name="q2" value="b"> P(A ∩ B) = P(A) + P(B)</label><br><label><input type="radio" name="q2" value="c"> P(A) = 0</label></div>
<div class="question"><b>3. En una bolsa se extraen dos bolas sin reemplazo. ¿Los eventos son necesariamente independientes?</b><br><label><input type="radio" name="q3" value="a"> Sí, siempre</label><br><label><input type="radio" name="q3" value="b"> No, la primera extracción modifica la composición</label><br><label><input type="radio" name="q3" value="c"> No se puede saber qué significa</label></div>
<button onclick="grade()">Calificar</button><p class="result" id="quizresult" aria-live="polite"></p>
</section>
<footer>Recurso didáctico interactivo · Probabilidad · Grado décimo</footer></main>
<script>
const sums={2:1,3:2,4:3,5:4,6:5,7:6,8:5,9:4,10:3,11:2,12:1};let total=0,sevens=0,urnN=0,urnVV=0;
function buildTable(){document.getElementById('sumtable').innerHTML=Object.entries(sums).map(([s,c])=>`<tr><td>${s}</td><td>${c}</td><td>${c}/36 = ${(c/36*100).toFixed(1)} %</td></tr>`).join('')}
function rollDice(){let a=1+Math.floor(Math.random()*6),b=1+Math.floor(Math.random()*6),s=a+b;total++;if(s===7)sevens++;document.getElementById('last').textContent=`${a} + ${b} = ${s}`;updateDice()}
function manyDice(){for(let i=0;i<1000;i++){let s=2+Math.floor(Math.random()*6)+Math.floor(Math.random()*6);total++;if(s===7)sevens++}document.getElementById('last').textContent='Se realizaron 1.000 lanzamientos adicionales';updateDice()}
function updateDice(){document.getElementById('freq7').textContent=`${sevens} de ${total}`;document.getElementById('freqpct').textContent=total?(sevens/total*100).toFixed(1)+' % (teórica: 16,7 %)':'0 %'}
function resetDice(){total=0;sevens=0;document.getElementById('last').textContent='—';updateDice()}
function showCombos(){let tops=['Roja','Azul','Blanca'],pants=['Negro','Gris'],arr=[];tops.forEach(t=>pants.forEach(p=>arr.push(`${t} + ${p}`)));document.getElementById('combos').innerHTML=arr.map(x=>`<span class="pill">${x}</span>`).join('');document.getElementById('comboresult').textContent=`${arr.length} combinaciones posibles. 2 de 6 incluyen camiseta roja.`}
function drawUrn(){let a=Math.random()<4/7?'V':'A';let greens=a==='V'?3:4;let b=Math.random()<greens/6?'V':'A';urnN++;if(a==='V'&&b==='V')urnVV++;document.getElementById('urnlast').textContent=`Primera: ${a==='V'?'verde':'amarilla'} · Segunda: ${b==='V'?'verde':'amarilla'}`;document.getElementById('urncount').textContent=`Simulaciones: ${urnN} · Dos verdes: ${urnVV} (${(urnVV/urnN*100).toFixed(1)} %; teórica: 28,6 %)` }
function resetUrn(){urnN=0;urnVV=0;document.getElementById('urnlast').textContent='Realiza una extracción para ver el resultado.';document.getElementById('urncount').textContent='Simulaciones: 0 · Dos verdes: 0'}
function grade(){let a={q1:'b',q2:'a',q3:'b'},s=0;for(let k in a){let x=document.querySelector(`input[name=${k}]:checked`);if(x&&x.value===a[k])s++}document.getElementById('quizresult').textContent=`Resultado: ${s} de 3 respuestas correctas. ${s===3?'¡Muy bien!':'Repasa los conceptos y vuelve a intentarlo.'}`}
buildTable();updateDice();
</script></body></html>
