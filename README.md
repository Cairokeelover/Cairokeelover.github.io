
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Birthday Journey - Happy Birthday Jojo 🎉</title>
<style>
  html, body { margin:0; padding:0; height:100%; font-family: system-ui, sans-serif; overflow: hidden; background: #ffffff; color: #333; }

  /* Common page style */
  .page { display:none; width:100%; height:100%; position:absolute; top:0; left:0; justify-content:center; align-items:center; flex-direction:column; text-align:center; padding:20px; box-sizing:border-box; transition: opacity 0.8s ease; }
  .page.show { display:flex; opacity:1; }

  /* Landing Page */
  #landing h1 { font-size: clamp(36px, 8vw, 80px); background: linear-gradient(90deg, #ffd6a5, #fdffb6, #caffbf); -webkit-background-clip: text; color: transparent; margin:0; animation: floatText 2s ease infinite alternate; }
  #landing .date { margin-top: 10px; font-size: 20px; color:#555; }
  #landing p { max-width:600px; margin-top: 20px; font-size: 18px; line-height:1.4; animation: fadeInText 2s ease; }
  #landing button { margin-top: 30px; padding:12px 25px; font-size:18px; border:none; border-radius:12px; background: linear-gradient(90deg, #a0c4ff, #bdb2ff); color:#fff; cursor:pointer; box-shadow:0 4px 12px rgba(0,0,0,0.2); transition: transform 0.2s; }
  #landing button:hover { transform: scale(1.05); }

  /* Year Page */
  #years h2 { font-size: clamp(28px, 6vw, 50px); margin-bottom:20px; animation: fadeInText 1s ease; }
  #years .year-grid { display:grid; grid-template-columns: repeat(auto-fit, minmax(120px, 1fr)); gap:20px; max-width:600px; }
  #years .year { padding:20px; border-radius:12px; background: #fce4ec; cursor:pointer; font-weight:bold; font-size:18px; box-shadow:0 3px 8px rgba(0,0,0,0.1); transition: transform 0.3s, background 0.3s; }
  #years .year:hover { transform: scale(1.05); background: #f8bbd0; }

  /* Year Detail Page */
  #yearDetail h2 { font-size: clamp(28px,6vw,50px); margin-bottom:15px; animation: floatText 1.5s ease infinite alternate; }
  #yearDetail .photos { display:flex; gap:15px; flex-wrap:wrap; justify-content:center; margin-top:15px; }
  #yearDetail .photos img { width:160px; height:160px; object-fit:cover; border-radius:12px; box-shadow:0 3px 10px rgba(0,0,0,0.15); animation: floatImg 3s ease infinite alternate; }
  #yearDetail p { max-width:600px; margin-top:20px; font-size:16px; line-height:1.4; animation: fadeInText 2s ease; }

  /* Back button */
  .back-btn { margin-top:25px; padding:10px 20px; border:none; border-radius:10px; background: linear-gradient(90deg, #ffb347, #ffcc33); color:#fff; cursor:pointer; box-shadow:0 3px 10px rgba(0,0,0,0.2); transition: transform 0.2s; }
  .back-btn:hover { transform: scale(1.05); }

  /* Animations */
  @keyframes floatText { transform: translateY(0px); }  /* subtle float effect */
  @keyframes floatImg { transform: translateY(0px); }
  @keyframes fadeInText { from{opacity:0;} to{opacity:1;} }
</style>
</head>
<body>

<!-- Landing Page -->
<div id="landing" class="page show">
  <h1>Happy Birthday Jojo 🎉</h1>
  <div class="date">03/03/2008</div>
  <p>Happy Birthday Jihan, with all love I wish you all the best this year! May your days be filled with joy, laughter, and unforgettable moments.</p>
  <button onclick="enterJourney()">Enter the Journey →</button>
</div>

<!-- Years Page -->
<div id="years" class="page">
  <h2>Choose a Year</h2>
  <div class="year-grid" id="yearGrid"></div>
  <button class="back-btn" onclick="goBackLanding()">Back to Start</button>
</div>

<!-- Year Detail Page -->
<div id="yearDetail" class="page">
  <h2 id="yearTitle">Year</h2>
  <div class="photos" id="photos"></div>
  <p id="letters">Letters and messages from friends will appear here.</p>
  <button class="back-btn" onclick="goBackYears()">Back to Years</button>
</div>

<script>
// Pages handling
const landing = document.getElementById('landing');
const yearsPage = document.getElementById('years');
const yearDetailPage = document.getElementById('yearDetail');

function showPage(page) {
  [landing, yearsPage, yearDetailPage].forEach(p=>p.classList.remove('show'));
  page.classList.add('show');
}

function enterJourney(){ showPage(yearsPage); }
function goBackLanding(){ showPage(landing); }
function goBackYears(){ showPage(yearsPage); }

// Generate years starting from current year
const yearGrid = document.getElementById('yearGrid');
const currentYear = new Date().getFullYear();
for(let y=currentYear; y<=currentYear+5; y++){
  let div = document.createElement('div');
  div.className = 'year';
  div.textContent = y;
  div.onclick = ()=>openYear(y);
  yearGrid.appendChild(div);
}

// Open Year Detail
function openYear(year){
  document.getElementById('yearTitle').textContent = year;
  // Placeholder photos
  const photosDiv = document.getElementById('photos');
  photosDiv.innerHTML = '';
  for(let i=1;i<=3;i++){
    let img = document.createElement('img');
    img.src = 'https://via.placeholder.com/160?text='+year+'+'+i;
    photosDiv.appendChild(img);
  }
  document.getElementById('letters').textContent = 'Letters and messages from friends for year '+year+'.';
  showPage(yearDetailPage);
}
</script>

</body>
</html>
