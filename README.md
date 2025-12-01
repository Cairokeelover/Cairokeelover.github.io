<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Birthday Journey</title>

<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">

<style>
    body {
        margin: 0;
        padding: 0;
        font-family: "Poppins", sans-serif;
        background: linear-gradient(135deg, #fff6da, #ffe8b5);
        overflow-x: hidden;
        transition: background 0.4s;
    }

    /* Fade transition for pages */
    .page {
        display: none;
        text-align: center;
        padding: 40px;
        animation: fadeSlide 0.7s ease;
    }

    .active {
        display: block;
    }

    @keyframes fadeSlide {
        from { opacity: 0; transform: translateY(25px); }
        to { opacity: 1; transform: translateY(0); }
    }

    h1 {
        font-size: 48px;
        margin-bottom: 10px;
        color: #333;
        font-weight: 700;
    }

    h2 {
        font-size: 24px;
        color: #666;
        margin-bottom: 20px;
    }

    p {
        max-width: 550px;
        margin: 0 auto;
        font-size: 18px;
        color: #444;
        line-height: 1.6;
    }

    button {
        margin-top: 30px;
        padding: 14px 25px;
        border: none;
        background: black;
        color: white;
        font-size: 17px;
        border-radius: 12px;
        cursor: pointer;
        transition: 0.25s;
        position: relative;
        overflow: hidden;
    }

    button:hover {
        transform: scale(1.08);
        box-shadow: 0 5px 15px rgba(0,0,0,0.25);
    }

    /* Back button */
    .back {
        position: absolute;
        top: 20px;
        left: 20px;
        background: #fff;
        color: black;
        border: 2px solid black;
        font-weight: bold;
    }

    /* Grid for years */
    .year-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
        gap: 25px;
        margin-top: 40px;
        padding: 20px;
    }

    /* Modern glass year card */
    .year-box {
        background: rgba(255, 255, 255, 0.65);
        backdrop-filter: blur(10px);
        border-radius: 18px;
        padding: 18px;
        cursor: pointer;
        transition: 0.25s;
        border: 2px solid rgba(255, 199, 64, 0.55);
        box-shadow: 0 6px 15px rgba(0,0,0,0.1);
        animation: popIn 0.6s ease;
    }

    @keyframes popIn {
        from { opacity: 0; transform: scale(0.85); }
        to { opacity: 1; transform: scale(1); }
    }

    .year-box:hover {
        transform: translateY(-5px) scale(1.05);
        background: rgba(255, 251, 232, 0.85);
        box-shadow: 0 8px 20px rgba(255, 180, 0, 0.35);
    }

    .calendar-header {
        background: gold;
        color: black;
        font-weight: bold;
        padding: 5px;
        border-radius: 12px;
        margin-bottom: 10px;
    }

    .calendar-year {
        font-size: 22px;
        font-weight: 700;
        color: #333;
    }

    /* Three main sections */
    .section-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
        gap: 30px;
        margin-top: 40px;
    }

    .section-box {
        background: white;
        padding: 40px;
        border-radius: 20px;
        font-size: 20px;
        border: 2px solid #eee;
        cursor: pointer;
        transition: 0.3s;
        box-shadow: 0 4px 12px rgba(0,0,0,0.1);
    }

    .section-box:hover {
        transform: scale(1.05);
        background: #fff5d4;
        box-shadow: 0 8px 20px rgba(255,200,0,0.4);
    }

    /* Confetti improved */
    .confetti-bg {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        pointer-events: none;
        z-index: -1;
    }

    .confetti-piece {
        position: absolute;
        width: 10px;
        height: 16px;
        background: gold;
        border-radius: 3px;
        opacity: 0.7;
        animation: fall linear infinite;
    }

    @keyframes fall {
        0% { transform: translateY(-5vh) rotate(0deg); opacity: 0.9; }
        100% { transform: translateY(110vh) rotate(360deg); opacity: 0.2; }
    }
</style>
</head>

<body>

<div class="confetti-bg" id="confetti"></div>

<!-- PAGE 1 -->
<div id="page1" class="page active">
    <h1>🎉 Happy Birthday Jojo 🎉</h1>
    <h2>03 / 03 / 2008</h2>
    <p>
        Happy birthday Jihan, with all love.  
        May every year bring you joy, success, and beautiful memories.
    </p>
    <button onclick="showPage('page2')">Enter the Journey →</button>
</div>

<!-- PAGE 2 (Dynamic Years) -->
<div id="page2" class="page">
    <button class="back" onclick="showPage('page1')">← Back</button>
    <h1>Select a Year</h1>
    <div class="year-grid" id="yearGrid"></div>
</div>

<!-- PAGE 3 (Sections) -->
<div id="page3" class="page">
    <button class="back" onclick="showPage('page2')">← Back</button>
    <h1 id="selectedYearTitle">Year Memories</h1>

    <div class="section-grid">
        <div class="section-box" onclick="showPage('pageMusic')">🎵 Music of the Year</div>
        <div class="section-box" onclick="showPage('pageAlbum')">📸 Album</div>
        <div class="section-box" onclick="showPage('pageLetters')">💌 Birthday Letters</div>
    </div>
</div>

<!-- MUSIC -->
<div id="pageMusic" class="page">
    <button class="back" onclick="showPage('page3')">← Back</button>
    <h1>Music of the Year</h1>
</div>

<!-- ALBUM -->
<div id="pageAlbum" class="page">
    <button class="back" onclick="showPage('page3')">← Back</button>
    <h1>Album</h1>
</div>

<!-- LETTERS -->
<div id="pageLetters" class="page">
    <button class="back" onclick="showPage('page3')">← Back</button>
    <h1>Birthday Letters</h1>
</div>

<script>
/* PAGE SWITCH */
function showPage(id) {
    document.querySelectorAll(".page").forEach(p => p.classList.remove("active"));
    document.getElementById(id).classList.add("active");
}

/* ---------- DYNAMIC YEARS ---------- */
const startYear = 2025;
const endYear = 2040;
const yearGrid = document.getElementById("yearGrid");

for (let y = startYear; y <= endYear; y++) {
    let box = document.createElement("div");
    box.className = "year-box";
    box.innerHTML = `
        <div class="calendar-header">Year</div>
        <div class="calendar-year">${y}</div>
    `;

    box.onclick = function () {
        document.getElementById("selectedYearTitle").innerText = y + " Memories";
        showPage("page3");
    };

    yearGrid.appendChild(box);
}

/* ---------- CONFETTI ---------- */
function createConfetti() {
    const confettiContainer = document.getElementById("confetti");
    const colors = ["gold", "#ffde73", "#ffe9ac", "#fff3d1"];

    for (let i = 0; i < 80; i++) {
        let piece = document.createElement("div");
        piece.classList.add("confetti-piece");

        piece.style.left = Math.random() * 100 + "vw";
        piece.style.animationDuration = 4 + Math.random() * 3 + "s";
        piece.style.background = colors[Math.floor(Math.random() * colors.length)];

        confettiContainer.appendChild(piece);
    }
}
createConfetti();
</script>

</body>
</html>
