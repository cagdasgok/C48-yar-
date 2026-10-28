
<!doctype html>
<html lang="tr">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1,maximum-scale=1,user-scalable=no">
<title>C48 Street Rush v0.6.2</title>
<style>
*{box-sizing:border-box}body{margin:0;background:#090d14;color:#edf4ff;font:15px Arial,sans-serif}
header{padding:14px;background:#111a27;display:flex;justify-content:space-between;align-items:center;font-weight:bold}
header b{color:#ff4055}header strong{color:#ffc857}
main{max-width:850px;margin:auto;padding:12px}
.panel{background:#111a27;border:1px solid #293951;border-radius:16px;padding:12px;margin-bottom:12px}
#game{width:100%;height:auto;aspect-ratio:3/4;display:block;background:#17212d;border-radius:12px;touch-action:none}
.stats{display:flex;justify-content:space-between;gap:8px;flex-wrap:wrap;margin:10px 0;font-weight:bold}
.modes,.garage{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:8px}
button,select{background:#202e42;color:white;border:1px solid #3b4d67;border-radius:12px;padding:13px 8px;font-size:15px;font-weight:bold;cursor:pointer}
button:active{transform:scale(.97)}button.selected{border-color:#ff4055;background:#38202c}
small{display:block;color:#9fb0c5;margin-top:5px;font-weight:normal}
.start{width:100%;background:#f32e4c;font-size:18px;margin-top:12px}
.controls{display:grid;grid-template-columns:repeat(5,1fr);gap:6px;margin-top:10px}
.controls button{font-size:20px;padding:15px 0}
#msg{text-align:center;font-weight:bold;min-height:25px;margin-top:10px;color:#ffc857}
@media(min-width:700px){main{max-width:620px}}
</style>
</head>
<body>
<header><span><b>C48</b> STUDIOS / STREET RUSH v0.6.2</span><strong>₺<span id="money">15000</span></strong></header>
<main>
<div class="panel">
<div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:10px">
<b id="carName">Tofaş</b><button onclick="fullScreen()">⛶ Tam ekran</button>
</div>
<canvas id="game" width="480" height="640"></canvas>
<div class="stats"><span>HIZ <span id="speed">0</span> km/sa</span><span>CAN <span id="health">100</span>%</span><span>MESAFE <span id="distance">0</span> m</span></div>
<div class="stats"><span>NİTRO <span id="nitro">100</span>%</span><span id="status">GARJDA BEKLİYOR</span></div>
<div class="controls">
<button onclick="move(-1)">◀</button><button onclick="accelerate()">▲</button><button onclick="brake()">▼</button><button onclick="move(1)">▶</button><button onclick="boost()">⚡</button>
</div>
<div id="msg">Aracını seç ve yarışa başla!</div>
</div>
<div class="panel">
<h3>🏁 Yarış modu</h3>
<div class="modes">
<button class="selected" id="m0" onclick="setMode(0)">☀️ Sabah Yarışı<small>1.600 m · Ödül ₺3.500</small></button>
<button id="m1" onclick="setMode(1)">🌙 Gece Otobanı<small>2.500 m · Açılış ₺30.000</small></button>
<button id="m2" onclick="setMode(2)">🏙️ Sokak Yarışı<small>2.800 m · Açılış ₺55.000</small></button>
<button id="m3" onclick="setMode(3)">🚨 Paket Atma<small>3.000 m · Polis takibi</small></button>
</div>
</div>
<div class="panel">
<h3>🚘 Garaj</h3>
<div class="garage" id="cars"></div>
</div>
<div class="panel">
<h3>🔧 Modifiye</h3>
<div class="modes">
<button onclick="upgrade('engine')">Motor yükselt <small>₺3.000</small></button>
<button onclick="upgrade('turbo')">Turbo yükselt <small>₺2.500</small></button>
<button onclick="upgrade('spoiler')">Arka spoiler <small>₺4.500</small></button>
<button onclick="upgrade('neon')">Yan neon <small>₺3.500</small></button>
</div>
</div>
<button class="start" onclick="startRace()">🏁 YARIŞA BAŞLA</button>
</main>
<script>
const $=id=>document.getElementById(id);
const canvas=$('game'),ctx=canvas.getContext('2d');
const cars=[
{name:'Tofaş',price:0,max:120,color:'#e8e8e8'},
{name:'Renault Clio',price:5000,max:135,color:'#e23d4d'},
{name:'Fiat Doblo',price:9500,max:155,color:'#ddd8ca'},
{name:'Volkswagen Passat',price:14000,max:167,color:'#283f62'},
{name:'Seat Leon',price:19000,max:184,color:'#e9e9e9'},
{name:'Honda Civic',price:26000,max:196,color:'#b52c3a'},
{name:'Toyota Supra',price:47000,max:210,color:'#ff7b21'},
{name:'Mercedes C200',price:35000,max:209,color:'#b8c2ce'},
{name:'Audi RS3',price:39000,max:213,color:'#20242a'},
{name:'BMW M3',price:52000,max:221,color:'#3656a6'},
{name:'VW Golf',price:63000,max:226,color:'#eee'},
{name:'Audi RS6',price:86000,max:235,color:'#4b5260'},
{name:'BMW M6',price:94000,max:239,color:'#2e6a9d'},
{name:'Koenigsegg Regera',price:146000,max:245,color:'#a5b8c9'},
{name:'McLaren Speedtail',price:167000,max:249,color:'#e8e8e8'},
{name:'Czinger 21C V Max',price:235000,max:253,color:'#9da5b1'}
];
let money=15000,owned=[0],selected=0,mode=0,running=false,speed=0,health=100,dist=0,nitro=100;
let lane=1,traffic=[],last=0,elapsed=0,engine=0,turbo=0,spoiler=false,neon=false,policeGap=380;
let best={0:1600,1:2500,2:2800,3:3000};
try{const s=JSON.parse(localStorage.getItem('c48sr')||'null');if(s){money=s.money??15000;owned=s.owned||[0];selected=s.selected||0;engine=s.engine||0;turbo=s.turbo||0;spoiler=!!s.spoiler;neon=!!s.neon}}catch(e){}
function save(){try{localStorage.setItem('c48sr',JSON.stringify({money,owned,selected,engine,turbo,spoiler,neon}))}catch(e){}}
function ui(){ $('money').textContent=money.toLocaleString('tr-TR');$('carName').textContent=cars[selected].name;$('speed').textContent=Math.round(speed);$('health').textContent=health;$('distance').textContent=Math.floor(dist);$('nitro').textContent=Math.round(nitro);$('status').textContent=running?'YARIŞTA':'GARAJDA BEKLİYOR';renderCars()}
function renderCars(){$('cars').innerHTML='';cars.forEach((c,i)=>{let b=document.createElement('button');b.className=i===selected?'selected':'';b.innerHTML=(owned.includes(i)?'✅ ':'🔒 ')+c.name+'<small>'+c.max+' km/sa · '+(owned.includes(i)?'Sahip':'₺'+c.price.toLocaleString('tr-TR'))+'</small>';b.onclick=()=>{if(owned.includes(i)){selected=i;ui();save()}else if(money>=c.price){money-=c.price;owned.push(i);selected=i;ui();save();$('msg').textContent=c.name+' satın alındı!'}else $('msg').textContent='Yeterli paran yok!';};$('cars').appendChild(b)})}
function setMode(m){mode=m;[0,1,2,3].forEach(i=>$('m'+i).classList.toggle('selected',i===m));$('msg').textContent=['Sabah yarışı seçildi','Gece otobanı seçildi','Sokak yarışı seçildi','Paket atma seçildi'][m]}
function startRace(){if(running)return;let cost=mode===1?30000:mode===2?55000:0;if(cost&&!window.confirm('Bu modun açılış ücreti ₺'+cost.toLocaleString('tr-TR')+'. Ödemek istiyor musun?'))return;if(cost&&money<cost){$('msg').textContent='Bu mod için yeterli paran yok!';return}money-=cost;running=true;speed=0;health=100;dist=0;nitro=100;elapsed=0;traffic=[];policeGap=380;lane=1;for(let i=0;i<5;i++)spawn(-i*150-100);$('msg').textContent='3... 2... 1... BAŞLA!';ui();save();last=performance.now();requestAnimationFrame(loop)}
function spawn(y=-100){traffic.push({lane:Math.floor(Math.random()*3),y:y,speed:65+Math.random()*85,color:['#f5bd48','#42b8c7','#a4b1c4','#e45b64','#79b879'][Math.floor(Math.random()*5)],w:48,h:82})}
function move(d){lane=Math.max(0,Math.min(2,lane+d))}
function accelerate(){if(running)speed=Math.min(cars[selected].max+engine*10+turbo*8,speed+7)}
function brake(){if(running)speed=Math.max(0,speed-12)}
function boost(){if(running&&nitro>0){speed=Math.min(cars[selected].max+engine*10+turbo*8+35,speed+20);nitro=Math.max(0,nitro-14)}}
function upgrade(type){let cost=type==='engine'?3000:type==='turbo'?2500:type==='spoiler'?4500:3500;if((type==='engine'&&engine>=3)||(type==='turbo'&&turbo>=2)||((type==='spoiler'&&spoiler)||(type==='neon'&&neon))){$('msg').textContent='Bu yükseltme zaten maksimumda!';return}if(money<cost){$('msg').textContent='Yeterli paran yok!';return}money-=cost;if(type==='engine')engine++;if(type==='turbo')turbo++;if(type==='spoiler')spoiler=true;if(type==='neon')neon=true;save();ui();$('msg').textContent='Modifiye uygulandı!'}
function fullScreen(){let el=canvas.parentElement;if(!document.fullscreenElement&&el.requestFullscreen)el.requestFullscreen().catch(()=>{});else if(document.exitFullscreen)document.exitFullscreen()}
function drawCar(x,y,color,player=false){ctx.save();ctx.translate(x,y);ctx.fillStyle='rgba(0,0,0,.35)';ctx.fillRect(-27,8,54,78);ctx.fillStyle=color;ctx.beginPath();ctx.moveTo(-21,65);ctx.lineTo(-24,25);ctx.quadraticCurveTo(-23,5,-14,0);ctx.lineTo(14,0);ctx.quadraticCurveTo(23,5,24,25);ctx.lineTo(21,65);ctx.closePath();ctx.fill();ctx.fillStyle='#111b28';ctx.beginPath();ctx.moveTo(-16,20);ctx.lineTo(-11,7);ctx.lineTo(11,7);ctx.lineTo(16,20);ctx.closePath();ctx.fill();ctx.fillRect(-17,25,34,17);ctx.fillStyle='#fff0b5';ctx.fillRect(-19,59,9,4);ctx.fillRect(10,59,9,4);if(spoiler&&player){ctx.fillStyle='#161b23';ctx.fillRect(-25,0,50,5)}if(neon&&player){ctx.shadowBlur=22;ctx.shadowColor='#27d7ff';ctx.strokeStyle='#27d7ff';ctx.lineWidth=3;ctx.beginPath();ctx.moveTo(-24,20);ctx.lineTo(-23,60);ctx.moveTo(24,20);ctx.lineTo(23,60);ctx.stroke()}ctx.restore()}
function drawRoad(){let w=canvas.width,h=canvas.height;ctx.fillStyle=mode===1||mode===3?'#132b24':'#285c37';ctx.fillRect(0,0,w,h);ctx.fillStyle='#454c56';ctx.fillRect(65,0,w-130,h);ctx.fillStyle='#e5e5e5';ctx.fillRect(65,0,5,h);ctx.fillRect(w-70,0,5,h);let offset=(dist*2)%70;ctx.strokeStyle='#e8e2bf';ctx.lineWidth=4;ctx.setLineDash([34,36]);ctx.lineDashOffset=-offset;ctx.beginPath();ctx.moveTo(w/2-58,0);ctx.lineTo(w/2-58,h);ctx.moveTo(w/2+58,0);ctx.lineTo(w/2+58,h);ctx.stroke();ctx.setLineDash([]);for(let i=0;i<7;i++){let y=((i*110+offset*1.5)%h);drawTree(30,y);drawTree(w-30,y+45)}}
function drawTree(x,y){ctx.fillStyle='#66482e';ctx.fillRect(x-3,y,6,20);ctx.fillStyle=['#267446','#338e4b','#4b9a53'][Math.floor((x+y)/50)%3];ctx.beginPath();ctx.arc(x,y,15,0,Math.PI*2);ctx.fill();ctx.fillStyle='#f0a0c1';ctx.fillRect(x+9,y+15,3,3);ctx.fillStyle='#ffd85a';ctx.fillRect(x-12,y+19,3,3)}
function frame(){ctx.clearRect(0,0,canvas.width,canvas.height);drawRoad();let laneX=[canvas.width/2-58,canvas.width/2,canvas.width/2+58];traffic.forEach(t=>drawCar(laneX[t.lane],t.y,t.color));drawCar(laneX[lane],canvas.height-125,cars[selected].color,true);if(mode===3){ctx.fillStyle='#f33';ctx.fillRect(laneX[lane]-20,canvas.height-210,40,5);ctx.fillStyle='#fff';ctx.font='bold 18px Arial';ctx.fillText('POLİS',canvas.width/2-25,40)}}
function loop(now){if(!running)return;let dt=Math.min(.04,(now-last)/1000||.016);last=now;elapsed+=dt;let max=cars[selected].max+engine*10+turbo*8;speed=Math.min(max,speed+dt*8);dist+=speed/3.6*dt;nitro=Math.min(100,nitro+dt*2);let target=best[mode];if(mode===3){policeGap-=(speed<180?dt*16:-dt*3);if(policeGap<60){running=false;money=Math.max(0,money-3000);$('msg').textContent='🚨 YAKALANDIN! Ceza ₺3.000';ui();save();frame();return}}
let trafficRate=speed>250?1.1:speed>220?1.5:speed>200?2.1:3.2;
if(Math.random()<dt*trafficRate)spawn(-90);
let playerY=canvas.height-125;traffic.forEach(t=>{t.y+=(speed/3.6+12-t.speed/3.6)*dt*2.2;if(t.lane===lane&&Math.abs(t.y-playerY)<62){health-=dt*(speed>250?55:speed>220?45:speed>200?32:20);speed=Math.max(0,speed-100*dt);if(health<=0){health=0;running=false;money=Math.max(0,money-500);$('msg').textContent='💥 KAZA YAPTIN!';save()}}});traffic=traffic.filter(t=>t.y<canvas.height+120);if(dist>=target){running=false;let reward=mode===0?3500:mode===1?15000:mode===2?23000:30000;money+=reward;$('msg').textContent=mode===3?'📦 PAKET TESLİM EDİLDİ! +₺'+reward:'🏁 YARIŞ BİTTİ! +₺'+reward;save()}ui();frame();if(running)requestAnimationFrame(loop)}
let keys={};document.addEventListener('keydown',e=>{if(e.key==='ArrowLeft'||e.key==='a')move(-1);if(e.key==='ArrowRight'||e.key==='d')move(1);if(e.key==='ArrowUp'||e.key==='w')accelerate();if(e.key==='ArrowDown'||e.key==='s')brake();if(e.code==='Space')boost()});
let touchStart=null;canvas.addEventListener('touchstart',e=>{touchStart=e.touches[0].clientX},{passive:true});canvas.addEventListener('touchend',e=>{if(touchStart===null)return;let dx=e.changedTouches[0].clientX-touchStart;if(Math.abs(dx)>25)move(dx>0?1:-1);touchStart=null},{passive:true});
ui();frame();
</script>
</body>
</html>
