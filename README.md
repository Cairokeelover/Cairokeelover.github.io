<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Happy Birthday 🎉</title>
<style>
  :root{
    --bg1:#0f172a;
    --bg2:#1e293b;
    --accent:#ff6b6b;
    --accent2:#ffd166;
    --glass: rgba(255,255,255,0.06);
    --glass-2: rgba(255,255,255,0.04);
    --card-radius:20px;
    --sans: system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
  }
  html,body{height:100%;margin:0;font-family:var(--sans);color:white;background: linear-gradient(135deg,var(--bg1),var(--bg2));}
  .wrap{
    min-height:100vh;display:flex;align-items:center;justify-content:center;padding:24px;box-sizing:border-box;
    position:relative;overflow:hidden;
  }

  /* center card */
  .card{
    width:100%;max-width:960px;background:linear-gradient(180deg,var(--glass),var(--glass-2));
    border-radius:var(--card-radius);padding:28px;backdrop-filter: blur(6px);box-shadow: 0 10px 30px rgba(2,6,23,0.6);
    text-align:center;position:relative;z-index:3;
  }

  h1{
    font-size:clamp(34px,6vw,72px);letter-spacing:2px;margin:8px 0 10px;color:transparent;
    background:linear-gradient(90deg,var(--accent),#ffa69e,var(--accent2));-webkit-background-clip:text;background-clip:text;
    text-transform:uppercase;
  }
  .subtitle{font-size:clamp(14px,2.2vw,20px);opacity:0.95;margin-bottom:18px}

  .typewriter{
    min-height:36px;font-weight:600;font-size:clamp(16px,2.2vw,20px);margin-bottom:18px;
  }

  .enter-btn{
    display:inline-block;padding:12px 20px;border-radius:12px;background:linear-gradient(90deg,var(--accent),var(--accent2));
    color:#071233;font-weight:700;text-decoration:none;cursor:pointer;border:none;font-size:16px;
    box-shadow: 0 6px 18px rgba(0,0,0,0.35);
  }

  .reveal{
    margin-top:22px;display:none;align-items:center;gap:18px;flex-wrap:wrap;justify-content:center;
  }
  .reveal.show{display:flex}

  .photo{
    width:220px;height:220px;border-radius:16px;object-fit:cover;flex:0 0 220px;box-shadow: 0 8px 30px rgba(2,6,23,0.6);
    border:4px solid rgba(255,255,255,0.06);
  }
  .message-box{text-align:left;max-width:520px}
  .message-box p{margin:0 0 10px;font-size:16px;line-height:1.45;color:rgba(255,255,255,0.92)}

  /* tiny footer */
  .footer{margin-top:18px;font-size:13px;opacity:0.7}

  /* confetti canvas */
  canvas#confetti{position:absolute;inset:0;pointer-events:none;z-index:2}

  /* small note for mobile */
  @media (max-width:520px){
    .photo{width:140px;height:140px;flex:0 0 140px}
    .card{padding:18px}
  }
</style>
</head>
<body>
<div class="wrap">
  <canvas id="confetti"></canvas>

  <div class="card" role="main" aria-labelledby="title">
    <h1 id="title">Happy Birthday 🎉</h1>

    <div class="subtitle">A special surprise page just for you</div>

    <div class="typewriter" id="typewriter">Wishing you a day full of smiles, love and cake…</div>

    <button id="enter" class="enter-btn">Tap to enter ✨</button>

    <div class="reveal" id="reveal">
      <!-- Replace the sample image src with your photo (or remove the img if you don't want a photo) -->
      <img class="photo" id="photo" src="https://images.unsplash.com/photo-1544005313-94ddf0286df2?w=1200&q=80&auto=format&fit=crop" alt="Birthday photo">

      <div class="message-box">
        <p id="personal">Hey — happy birthday! I made this little page for you. I hope your day is as amazing as you are. 🎂💫</p>
        <p id="extra">Open your gift, make a wish, and enjoy every moment. Big hug!</p>
      </div>
    </div>

    <div class="footer">Tip: Tap the button once to start music (required on most phones).</div>
  </div>
</div>

<!-- audio (replace with your own short MP3 hosted somewhere) -->
<audio id="bgm" loop preload="auto">
  <source src="https://cdn.pixabay.com/download/audio/2022/03/15/audio_1a2b6f5d32.mp3?filename=happy-ukulele-111999.mp3" type="audio/mpeg">
  Your browser does not support the audio element.
</audio>

<script>
/* ===== Typewriter: simple */
const typeEl = document.getElementById('typewriter');
const messages = [
  "Wishing you a day full of smiles, love and cake…",
  "You make the world brighter — happy birthday!",
  "Hope every wish you make today comes true ✨"
];
let mi = 0;
function typeLoop(){
  const txt = messages[mi % messages.length];
  let i = 0;
  typeEl.textContent = '';
  const t = setInterval(()=> {
    typeEl.textContent += txt[i++] || '';
    if(i > txt.length){
      clearInterval(t);
      setTimeout(()=>{ mi++; typeLoop(); }, 2200);
    }
  }, 38);
}
typeLoop();

/* ===== Confetti - lightweight canvas confetti */
(function(){
  const cvs = document.getElementById('confetti');
  const ctx = cvs.getContext('2d');
  let w=0,h=0,particles=[];
  function resize(){ w = cvs.width = innerWidth; h = cvs.height = innerHeight; }
  addEventListener('resize', resize); resize();

  function rand(a,b){return Math.random()*(b-a)+a}
  function createParticles(n=90){
    particles = [];
    for(let i=0;i<n;i++){
      particles.push({
        x: rand(0,w), y: rand(-h,0),
        r: rand(6,12), d: rand(1,3),
        color: ['#ff6b6b','#ffd166','#6be4ff','#c7f9cc'][Math.floor(rand(0,4))],
        tilt: rand(-0.2,0.2), ang: rand(0,Math.PI*2)
      });
    }
  }
  function update(){
    for(let p of particles){
      p.ang += 0.03;
      p.y += Math.cos(p.ang) + 1 + p.d*0.5;
      p.x += Math.sin(p.ang)*2;
      p.tilt += 0.02;
      if(p.y > h+20) { p.y = -10; p.x = rand(0,w); }
    }
  }
  function draw(){
    ctx.clearRect(0,0,w,h);
    for(let p of particles){
      ctx.save();
      ctx.translate(p.x,p.y);
      ctx.rotate(p.tilt);
      ctx.fillStyle = p.color;
      ctx.fillRect(-p.r/2, -p.r/2, p.r, p.r*0.6);
      ctx.restore();
    }
  }
  createParticles(90);
  function loop(){ update(); draw(); requestAnimationFrame(loop); }
  loop();
})();

/* ===== Enter button: plays music and shows reveal */
const enterBtn = document.getElementById('enter');
const bgm = document.getElementById('bgm');
const reveal = document.getElementById('reveal');

enterBtn.addEventListener('click', async () => {
  try {
    // play audio (must be user gesture)
    await bgm.play();
  } catch(e){
    // ignore - if autoplay is blocked user can click play on controls (not shown)
  }
  reveal.classList.toggle('show');
  // change button text
  enterBtn.textContent = reveal.classList.contains('show') ? 'Close ✨' : 'Tap to enter ✨';
});

/* ===== Small accessibility niceties: focus to button on load for keyboard users */
window.addEventListener('load', ()=> enterBtn.focus());

</script>
</body>
</html>
