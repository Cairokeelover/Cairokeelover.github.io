
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Birthday Journey - Happy Birthday Jojo 🎉</title>
<style>
  html, body { margin:0; padding:0; height:100%; font-family: system-ui, sans-serif; overflow:hidden; background:#ffffff; }
  .page { display:none; width:100%; height:100%; position:absolute; top:0; left:0; justify-content:center; align-items:center; flex-direction:column; text-align:center; padding:20px; box-sizing:border-box; }
  .page.show { display:flex; }

  h1, h2 { margin:0; padding:0; }
  button { cursor:pointer; }

  /* Landing */
  #landing h1 { font-size: clamp(36px, 8vw, 80px); background:linear-gradient(90deg,#ffd6a5,#fdffb6,#caffbf); -webkit-background-clip:text; color:transparent; animation:float 2s ease infinite alternate; }
  #landing p { max-width:600px; font-size:18px; margin-top:20px; }

  /* Years */
  #years .year-grid { display:grid; grid-template-columns:repeat(auto-fit,minmax(120px,1fr)); gap:20px; max-width:600px; }
  .year { padding:20px; border-radius:12px; background:#fce4ec; font-size:18px; font-weight:bold; box-shadow:0 3px 8px rgba(0,0,0,0.1); }

  /* Year Detail */
  #yearDetail .box-grid { display:grid; grid-template-columns:repeat(auto-fit,minmax(200px,1fr)); gap:20px; max-width:700px; margin-top:25px; }
  .detail-box { padding:25px; border-radius:14px; background:#e3f2fd; box-shadow:0 3px 8px rgba(0,0,0,0.1); font-size:20px; font-weight:600; transition:0.3s; }
  .detail-box:hover { transform:scale(1.05); }

  /* Music/Album/Letters Pages */
  .sub-content { max-width:700px; font-size:18px; }

  /* Back button */
  .back-btn { margin-top:25px; padding:10px 22px; border:none; border-radius:10px; background:linear-gradient(90deg,#ffb347,#ffcc33); color:#fff; font-size:16px; }

  @keyframes float { from{transform:translateY(0);} to{transform:translateY(-10px);} }
</style>
</head>
<body>

<!-- Landing Page -->
<div id="landing" class="page show">
  <h1>Happy Birthday Jojo 🎉</h1>
  <div class="date">03/03/2008</div>
  <p>Happy Birthday Jihan, with all love I wish you all the best this year!</p>
  <button onclick="enterJourney()">Enter the Journey →</button>
</div>

<!-- Years Page -->
<div id="years" class="page">
  <h2>Select a Year</h2>
  <div id="yearGrid" class="year-grid"></div>
  <button class="back-btn" onclick="goBackLanding()">Back</button>
</div>

<!-- Year Detail Page -->
<div id="yearDetail" class="page">
  <h2 id="yearTitle">Year</h2>
  <div class="box-grid">
    <div class="detail-box" onclick="openMusic()">🎵 Music of the Year</div>
    <div class="detail-box" onclick="openAlbum()">📸 Album</div>
    <div class="detail-box" onclick="openLetters()">💌 Birthday Letters</div>
  </div>
  <button class="back-btn" onclick="goBackYears()">Back</button>
</div>

<!-- Music Page -->
<div id="musicPage" class="page">
  <h2>🎵 Music of the Year</h2>
  <div class="sub-content">Music list will be added here.</div>
  <button class="back-btn" onclick="goBackDetail()">Back</button>
</div>

<!-- Album Page -->
<div id="albumPage" class="page">
  <h2>📸 Album</h2>
  <div class="sub-content">Photos for this year will be shown here.</div>
  <button class="back-btn" onclick="goBackDetail()">Back</button>
</div>

<!-- Letters Page -->
<div id="lettersPage" class="page">
  <h2>💌 Birthday Letters</h2>
  <div class="sub-content">Names + messages will appear here.</div>
  <button class="back-btn" onclick="goBackDetail()">Back</button>
</div>

<canvas id="confettiCanvas" style="position:fixed;top:0;left:0;width:100%;height:100%;pointer-events:none;z-index:-1;"></canvas>

<script>
const landing=document.getElementById('landing');
const yearsPage=document.getElementById('years');
const yearDetailPage=document.getElementById('yearDetail');
const musicPage=document.getElementById('musicPage');
const albumPage=document.getElementById('albumPage');
const lettersPage=document.getElementById('lettersPage');

function show(page){ [landing,yearsPage,yearDetailPage,musicPage,albumPage,lettersPage].forEach(p=>p.classList.remove('show')); page.classList.add('show'); }
function enterJourney(){ show(yearsPage); }
function goBackLanding(){ show(landing); }
function goBackYears(){ show(yearsPage); }
function goBackDetail(){ show(yearDetailPage); }

const yearGrid=document.getElementById('yearGrid');
const currentYear=new Date().getFullYear();
for(let y=currentYear; y<=currentYear+5; y++){
  let div=document.createElement('div'); div.className='year'; div.textContent=y; div.onclick=()=>openYear(y); yearGrid.appendChild(div);
}

function openYear(y){ document.getElementById('yearTitle').textContent=y; show(yearDetailPage); }
function openMusic(){ show(musicPage); }
function openAlbum(){ show(albumPage); }
function openLetters(){ show(lettersPage); }

// Confetti
const confettiCanvas=document.getElementById('confettiCanvas');
const ctx=confettiCanvas.getContext('2d');
let confetti=[];
function resize(){ confettiCanvas.width=window.innerWidth; confettiCanvas.height=window.innerHeight; }
window.addEventListener('resize',resize); resize();
for(let i=0;i<150;i++){ confetti.push({x:Math.random()*innerWidth,y:Math.random()*innerHeight,r:Math.random()*4+1,dx:(Math.random()-0.5)*0.5,dy:Math.random()*1+0.5,color:['gold','#ffd700','#fff5cc','#ffecd1','#ffe7a0'][Math.floor(Math.random()*5)]});*innerWidth,y:Math.random()*innerHeight,r:Math.random()*6+2,dx:(Math.random()-0.5)*1,dy:Math.random()*2+1,color:`gold`}); }
function animate(){ ctx.clearRect(0,0,innerWidth,innerHeight); confetti.forEach(c=>{ c.x+=c.dx; c.y+=c.dy; if(c.y>innerHeight){ c.y=-10; c.x=Math.random()*innerWidth; } ctx.beginPath(); ctx.arc(c.x,c.y,c.r,0,Math.PI*2); ctx.fillStyle=c.color; ctx.fill(); }); requestAnimationFrame(animate); }
animate();
</script>

</body>
</html>
