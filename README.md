<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Birthday Journey</title>
<style>
    body { margin:0; padding:0; font-family:"Poppins", sans-serif; background:#ffffff; transition:0.4s; }
    .page { display:none; text-align:center; padding:40px; animation:fadeIn 0.7s ease; }
    .active { display:block; }
    @keyframes fadeIn { from { opacity:0; transform:translateY(20px); } to { opacity:1; transform:translateY(0); } }
    h1 { font-size:48px; margin-bottom:10px; color:#333; }
    h2 { font-size:24px; color:#666; margin-bottom:20px; }
    p { max-width:500px; margin:0 auto; font-size:18px; color:#444; }
    button { margin-top:30px; padding:14px 25px; border:none; background:black; color:white; font-size:17px; border-radius:12px; cursor:pointer; transition:0.3s; }
    button:hover { transform:scale(1.07); }
    .back { position:absolute; top:20px; left:20px; background:white; color:black; border:2px solid black; font-weight:bold; }
    .year-grid { display:grid; grid-template-columns:repeat(auto-fit, minmax(120px, 1fr)); gap:20px; margin-top:40px; }
    .year-box { background:white; border-radius:12px; border:2px solid #ddd; cursor:pointer; transition:0.3s; display:flex; flex-direction:column; justify-content:flex-start; align-items:center; padding:10px; box-shadow:0 4px 8px rgba(0,0,0,0.1); }
    .year-box:hover { transform:scale(1.05); background:#fef9f0; }
    .year-box .calendar-header { width:100%; background:#f5d76e; color:black; text-align:center; font-weight:bold; padding:5px 0; border-top-left-radius:10px; border-top-right-radius:10px; margin-bottom:8px; }
    .year-box .calendar-year { font-size:22px; font-weight:bold; color:#333; flex-grow:1; display:flex; align-items:center; justify-content:center; }
    .section-grid { display:grid; grid-template-columns:repeat(auto-fit, minmax(220px, 1fr)); gap:25px; margin-top:40px; }
    .section-box { background:white; padding:35px; border-radius:16px; border:2px solid #ddd; font-size:20px; cursor:pointer; transition:0.3s; }
    .section-box:hover { background:#f2f2f2; transform:scale(1.05); }
    .confetti-bg { position:fixed; top:0; left:0; width:100%; height:100%; pointer-events:none; z-index:-1; overflow:hidden; }
    .confetti-piece { position:absolute; width:8px; height:14px; background:gold; opacity:0.7; transform:rotate(15deg); border-radius:2px; animation:fall linear infinite; }
    @keyframes fall { 0% { transform: translateY(-50px) rotate(0deg); } 100% { transform: translateY(110vh) rotate(360deg); } }
    /* LOGIN PAGE */
    #loginPage { display:flex; justify-content:center; align-items:center; height:100vh; flex-direction:column; }
    .login-box { text-align:center; }
    input[type=password] { padding:10px; font-size:16px; border-radius:8px; border:2px solid #ccc; margin-top:10px; }
    .error { color:red; display:none; margin-top:10px; }
    img { border-radius:10px; box-shadow:0 4px 10px rgba(0,0,0,0.1); object-fit:cover; }
</style>
</head>
<body>

<!-- CONFETTI -->
<div class="confetti-bg" id="confetti"></div>

<!-- LOGIN PAGE -->
<div id="loginPage">
    <div class="login-box">
        <h2>🔒 Enter Password</h2>
        <input type="password" id="passwordInput" placeholder="Password">
        <button onclick="checkPassword()">Enter</button>
        <p id="errorMsg" class="error">Incorrect password.</p>
    </div>
</div>

<!-- PAGE 1 — FIRST INTERFACE -->
<div id="page1" class="page">
    <h1>🎉 Happy Birthday Jojo 🎉</h1>
    <h2>03 / 03 / 2008</h2>
    <p>
        Happy birthday Jihan, with all love.<br>
        I wish for you all the best in this year and all the years coming.<br>
        May your journey be full of happiness, success, and beautiful memories.
    </p>
</div>

<!-- PAGE 2 — YEARS -->
<div id="page2" class="page">
    <button class="back" onclick="showPage('page1')">← Back</button>
    <h1>Select a Year</h1>
    <div class="year-grid"></div>
</div>

<!-- PAGE 3 — THREE BOXES -->
<div id="page3" class="page">
    <button class="back" onclick="showPage('page2')">← Back</button>
    <h1 id="yearTitle">Year Memories</h1>
    <div class="section-grid">
        <div class="section-box" onclick="showPage('pageMusic')">🎵 Music of the Year</div>
        <div class="section-box" onclick="showPage('pageAlbum')">📸 Album of the Year</div>
        <div class="section-box" onclick="showPage('pageLetters')">💌 Birthday Letters</div>
    </div>
</div>

<!-- PAGE — MUSIC -->
<div id="pageMusic" class="page">
    <button class="back" onclick="showPage('page3')">← Back</button>
    <h1>Music of the Year</h1>
    <p>(Place your songs here later)</p>
</div>

<!-- PAGE — ALBUM -->
<div id="pageAlbum" class="page">
    <button class="back" onclick="showPage('page3')">← Back</button>
    <h1>Album of the Year</h1>
    <input type="file" id="photoInput" accept="image/*" multiple>
    <button onclick="uploadPhotos()">Add Photos</button>
    <div id="photoGallery" style="margin-top:30px; display:flex; flex-wrap:wrap; gap:15px; justify-content:center;"></div>
</div>

<!-- PAGE — LETTERS -->
<div id="pageLetters" class="page">
    <button class="back" onclick="showPage('page3')">← Back</button>
    <h1>Birthday Letters</h1>
    <p>(Letters + names go here)</p>
</div>

<script>
/* ====== PASSWORD LOGIN ====== */
function checkPassword() {
    const input = document.getElementById("passwordInput").value;
    const errorMsg = document.getElementById("errorMsg");
    if(input === "jojo2008") {
        localStorage.setItem("birthday_access","ok");
        document.getElementById("loginPage").style.display="none";
        document.getElementById("page1").classList.add("active");
    } else { errorMsg.style.display="block"; }
}
window.onload = () => {
    if(localStorage.getItem("birthday_access")==="ok") {
        document.getElementById("loginPage").style.display="none";
        document.getElementById("page1").classList.add("active");
    }
    generateYears();
};

/* ====== PAGE NAVIGATION ====== */
function showPage(id) {
    document.querySelectorAll(".page").forEach(p=>p.classList.remove("active"));
    document.getElementById(id).classList.add("active");
}

/* ====== CONFETTI ====== */
function createConfetti() {
    const confettiContainer = document.getElementById("confetti");
    const colors = ["gold","#f5d76e","#e6c24c","#ffeb99"];
    for(let i=0;i<60;i++){
        let piece=document.createElement("div");
        piece.classList.add("confetti-piece");
        piece.style.left=Math.random()*100+"vw";
        piece.style.animationDuration=3+Math.random()*4+"s";
        piece.style.background=colors[Math.floor(Math.random()*colors.length)];
        confettiContainer.appendChild(piece);
    }
}
createConfetti();

/* ====== YEARS DYNAMIC ====== */
function generateYears() {
    const grid = document.querySelector(".year-grid");
    for(let year=2025; year<=2040; year++){
        let div=document.createElement("div");
        div.className="year-box";
        div.innerHTML=`<div class="calendar-header">Year</div><div class="calendar-year">${year}</div>`;
        div.onclick = () => {
            document.getElementById("yearTitle").innerText=year+" Memories";
            currentYear = year;
            displayPhotos();
            showPage('page3');
        };
        grid.appendChild(div);
    }
    let more = document.createElement("div");
    more.className="year-box";
    more.innerHTML=`<div class="calendar-header">Year</div><div class="calendar-year">more...</div>`;
    more.onclick = ()=>{ alert("More years coming soon!"); };
    grid.appendChild(more);
}

/* ====== ALBUM PHOTO LOGIC ====== */
let currentYear = 2025;
function uploadPhotos() {
    const input = document.getElementById("photoInput");
    const files = input.files;
    if(!files.length) return;

    let storedPhotos = JSON.parse(localStorage.getItem("album"+currentYear) || "[]");

    for(let file of files){
        const reader = new FileReader();
        reader.onload = () => {
            storedPhotos.push(reader.result);
            localStorage.setItem("album"+currentYear, JSON.stringify(storedPhotos));
            displayPhotos();
        };
        reader.readAsDataURL(file);
    }
}

function displayPhotos() {
    const container = document.getElementById("photoGallery");
    container.innerHTML="";
    let storedPhotos = JSON.parse(localStorage.getItem("album"+currentYear) || "[]");
    storedPhotos.forEach(imgData=>{
        const img=document.createElement("img");
        img.src=imgData;
        img.style.width="150px";
        img.style.height="150px";
        container.appendChild(img);
    });
}



</body>
</html>
