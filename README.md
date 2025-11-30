<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Happy Birthday Jojo 🎉</title>
<style>
  html,body{
    height:100%;margin:0;font-family:system-ui;background:#0a0a0f;color:white;overflow:hidden;
  }
  /* Animated gradient background */
  body{
    background: linear-gradient(120deg,#1a1a2e,#16213e,#0f3460,#533483);
    background-size:400% 400%;
    animation: gradientAnim 18s ease infinite;
  }
  @keyframes gradientAnim{
    0%{background-position:0% 50%;}
    50%{background-position:100% 50%;}
    100%{background-position:0% 50%;}
  }

  /* Floating lights */
  .orb{
    position:absolute;width:14px;height:14px;border-radius:50%;
    background: rgba(255,255,255,0.7);
    box-shadow:0 0 12px 4px rgba(255,255,255,0.9);
    animation: floatUp 10s linear infinite;
  }
  @keyframes floatUp{
    from{transform:translateY(120vh);opacity:0;}
    20%{opacity:1;}
    to{transform:translateY(-20vh);opacity:0;}
  }

  /* Center card */
  .center{
    position:absolute;top:50%;left:50%;transform:translate(-50%,-50%);
    text-align:center;padding:28px 32px;
    backdrop-filter: blur(14px);
    background: rgba(255,255,255,0.08);
    border-radius:20px;
    box-shadow:0 0 30px rgba(0,0,0,0.6);
    animation: fadeIn 1.4s ease;
  }
  @keyframes fadeIn{
    from{opacity:0;transform:translate(-50%,-40%) scale(0.9);} 
    to{opacity:1;transform:translate(-50%,-50%) scale(1);} 
  }

  h1{
    font-size: clamp(36px,7vw,84px);
    margin:0;
    font-weight:800;
    background: linear-gradient(90deg,#ff9a9e,#fad0c4,#fbc2eb,#a18cd1);
    -webkit-background-clip:text;
    color:transparent;
    text-shadow:0 0 20px rgba(255,255,255,0.5);
  }

  .msg{
    font-size:clamp(16px,2vw,22px);
    margin-top:12px;
    opacity:0.92;
    animation: fadeMsg 2s ease;
  }
  @keyframes fadeMsg{
    from{opacity:0;} to{opacity:0.92;}
  }

  /* Confetti canvas */
  canvas#confetti{
    position:absolute;inset:0;pointer-events:none;
  }
</style>
</head>
<body>
<canvas id="confetti"></canvas>

<!-- glowing floating orbs -->
<script>
for(let i=0;i<26;i++){
  let o=document.createElement('div');
  o.className='orb';
  o.style.left=Math.random()*100+'vw';
  o.style.animationDelay=(Math.random()*8)+'s';
  o.style.animationDuration=(10+Math.random()*10)+'s';
  document.body.appendChild(o);
}
</script>

<div class="center">
  <h1>Happy Birthday Jojo 🎉</h1>
  <div class="msg">Wishing you a magical day full of joy, energy, and unforgettable moments.</div>
</div>

<script>
// Lightweight confetti
(function(){
  const cvs=document.getElementById('confetti');
  const ctx=cvs.getContext('2d');
  let w,h,particles=[];
  function resize(){w=cvs.width=innerWidth;h=cvs.height=innerHeight;}
  addEventListener('resize',resize);resize();

  function rand(a,b){return Math.random()*(b-a)+a;}

  function init(num=150){
    particles=[];
    for(let i=0;i<num;i++){
      particles.push({
        x:rand(0,w),y:rand(0,h),r:rand(4,9),d:rand(1,3),
        color:["#ff6b6b","#feca57","#48dbfb","#9b59b6"][Math.floor(rand(0,4))],
        tilt:rand(-0.4,0.4),ang:rand(0,Math.PI*2)
      });
    }
  }

  function update(){
    for(let p of particles){
      p.ang+=0.02;
      p.y+=Math.cos(p.ang)+1+p.d;
      p.x+=Math.sin(p.ang)*1.2;
      if(p.y>h+10){p.y=-10;p.x=rand(0,w);}    }
  }

  function draw(){
    ctx.clearRect(0,0,w,h);
    for(let p of particles){
      ctx.save();ctx.translate(p.x,p.y);ctx.rotate(p.tilt);
      ctx.fillStyle=p.color;
      ctx.fillRect(-p.r/2,-p.r/2,p.r,p.r*0.6);
      ctx.restore();
    }
  }

  init(170);
  (function loop(){update();draw();requestAnimationFrame(loop);}());
})();
</script>
</body>
</html>

