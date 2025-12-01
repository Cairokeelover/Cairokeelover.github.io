<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Birthday Journey</title>

<style>
    body {
        margin: 0;
        padding: 0;
        font-family: "Poppins", sans-serif;
        background: #ffffff;
        transition: 0.4s;
    }

    .page {
        display: none;
        text-align: center;
        padding: 40px;
        animation: fadeIn 0.7s ease;
    }

    .active {
        display: block;
    }

    @keyframes fadeIn {
        from { opacity: 0; transform: translateY(20px); }
        to { opacity: 1; transform: translateY(0); }
    }

    h1 {
        font-size: 48px;
        margin-bottom: 10px;
        color: #333;
    }

    h2 {
        font-size: 24px;
        color: #666;
        margin-bottom: 20px;
    }

    p {
        max-width: 500px;
        margin: 0 auto;
        font-size: 18px;
        color: #444;
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
        transition: 0.3s;
    }

    button:hover {
        transform: scale(1.07);
    }

    .back {
        position: absolute;
        top: 20px;
        left: 20px;
        background: white;
        color: black;
        border: 2px solid black;
        font-weight: bold;
    }

    .year-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
        gap: 20px;
        margin-top: 40px;
    }

    .year-box {
        background: white;
        border-radius: 12px;
        border: 2px solid #ddd;
        cursor: pointer;
        transition: 0.3s;
        display: flex;
        flex-direction: column;
        justify-content: flex-start;
        align-items: center;
        padding: 10px;
        box-shadow: 0 4px 8px rgba(0,0,0,0.1);
    }

    .year-box:hover {
        transform: scale(1.05);
        background: #fef9f0;
    }

    .calendar-header {
        width: 100%;
        background: #f5d76e;
        color: black;
        text-align: center;
        font-weight: bold;
        padding: 5px 0;
        border-top-left-radius: 10px;
        border-top-right-radius: 10px;
        margin-bottom: 8px;
    }

    .calendar-year {
        font-size: 22px;
        font-weight: bold;
        color: #333;
        flex-grow: 1;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .section-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
        gap: 25px;
        margin-top: 40px;
    }

    .section-box {
        background: white;
        padding: 35px;
        border-radius: 16px;
        border: 2px solid #ddd;
        font-size: 20px;
        cursor: pointer;
        transition: 0.3s;
    }

    .section-box:hover {
        background: #f2f2f2;
        transform: scale(1.05);
    }

    /* CONFETTI */
    .confetti-bg {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        pointer-events: none;
        z-index: -1;
        overflow: hidden;
    }

    .confetti-piece {
        position: absolute;
        width: 8px;
        height: 14px;
        background: gold;
        opacity: 0.7;
        transform: rotate(15deg);
        border-radius: 2px;
        animation: fall linear infinite;
    }

    @keyframes fall {
        0% { transform: translateY(-50px) rotate(0deg); }
        100% { transform: translateY(110vh) rotate(360deg); }
    }

    /* --- GOLD DOODLES ON FIRST PAGE --- */
    #page1 {
        position: relative;
        overflow: hidden;
    }

    .doodle {
        position: absolute;
        font-size: 32px;
        color: gold;
        opacity: 0.25;
        pointer-events: none;
        user-select: none;
        font-weight: bold;
        animation: floatDoodle 6s ease-in-out infinite;
    }

    @keyframes floatDoodle {
        0% { transform: translateY(0px); }
        50% { transform: translateY(-10px); }
        100% { transform: translateY(0px); }
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
        Happy birthday Jihan, with all love.<br>
        I wish for you the best in this year and all the years coming.<br>
        May your journey be full of happiness, success, and beautiful memories.
    </p>

    <button onclick="showPage('page2')">Enter the Journey →</button>
</div>

<!-- PAGE 2 -->
<div id="page2" class="page">
    <button class="back" onclick="showPage('page1')">← Back</button>

    <h1>Select a Year</h1>

    <div class="year-grid">
        <!-- DEFAULT YEARS (unchanged) -->
        <div class="year-box" onclick="showPage('page3')"><div class="calendar-header">Year</div><div class="calendar-year">2025</div></div>
        <div class="year-box" onclick="showPage('page3')"><div class="calendar-header">Year</div><div class="calendar-year">2026</div></div>
        <div class="year-box" onclick="showPage('page3')"><div class="calendar-header">Year</div><div class="calendar-year">2027</div></div>
        <div class="year-box" onclick="showPage('page3')"><div class="calendar-header">Year</div><div class="calendar-year">2028</div></div>
        <div class="year-box" onclick="showPage('page3')"><div class="calendar-header">Year</div><div class="calendar-year">2029</div></div>
        <div class="year-box" onclick="showPage('page3')"><div class="calendar-header">Year</div><div class="calendar-year">2030</div></div>
        <div class="year-box" onclick="showPage('page3')"><div class="calendar-header">Year</div><div class="calendar-year">2031</div></div>
        <div class="year-box" onclick="showPage('page3')"><div class="calendar-header">Year</div><div class="calendar-year">2032</div></div>
        <div class="year-box" onclick="showPage('page3')"><div class="calendar-header">Year</div><div class="calendar-year">2033</div></div>
        <div class="year-box" onclick="showPage('page3')"><div class="calendar-header">Year</div><div class="calendar-year">2034</div></div>
        <div class="year-box" onclick="showPage('page3')"><div class="calendar-header">Year</div><div class="calendar-year">2035</div></div>
        <div class="year-box" onclick="showPage('page3')"><div class="calendar-header">Year</div><div class="calendar-year">2036</div></div>
        <div class="year-box" onclick="showPage('page3')"><div class="calendar-header">Year</div><div class="calendar-year">2037</div></div>
        <div class="year-box" onclick="showPage('page3')"><div class="calendar-header">Year</div><div class="calendar-year">2038</div></div>
        <div class="year-box" onclick="showPage('page3')"><div class="calendar-header">Year</div><div class="calendar-year">2039</div></div>
        <div class="year-box" onclick="showPage('page3')"><div class="calendar-header">Year</div><div class="calendar-year">2040</div></div>

        <div class="year-box" onclick="showPage('pageMore')">
            <div class="calendar-header">Year</div>
            <div class="calendar-year">more...</div>
        </div>
    </div>
</div>

<!-- PAGE 3 -->
<div id="page3" class="page">
    <button class="back" onclick="showPage('page2')">← Back</button>
    <h1>2025 Memories</h1>

    <div class="section-grid">
        <div class="section-box" onclick="showPage('pageMusic')">🎵 Music of the Year</div>
        <div class="section-box" onclick="showPage('pageAlbum')">📸 Album 2025</div>
        <div class="section-box" onclick="showPage('pageLetters')">💌 Birthday Letters</div>
    </div>
</div>

<!-- MUSIC -->
<div id="pageMusic" class="page">
    <button class="back" onclick="showPage('page3')">← Back</button>
    <h1>Music of the Year</h1>
    <p>(Place your songs here later)</p>
</div>

<!-- ALBUM -->
<div id="pageAlbum" class="page">
    <button class="back" onclick="showPage('page3')">← Back</button>
    <h1>Album 2025</h1>
    <p>(Photos will go here)</p>
</div>

<!-- LETTERS -->
<div id="pageLetters" class="page">
    <button class="back" onclick="showPage('page3')">← Back</button>
    <h1>Birthday Letters</h1>
    <p>(Letters + names go here)</p>
</div>

<!-- MORE -->
<div id="pageMore" class="page">
    <button class="back" onclick="showPage('page2')">← Back</button>
    <h1>🎉 More Years Ahead 🎉</h1>
    <p>More wonderful years are waiting for you!</p>
</div>

<script>
function showPage(id) {
    document.querySelectorAll(".page").forEach(p => p.classList.remove("active"));
    document.getElementById(id).classList.add("active");
}

// CONFETTI
function createConfetti() {
    const confettiContainer = document.getElementById("confetti");
    const colors = ["gold", "#f5d76e", "#e6c24c", "#ffeb99"]; 

    for (let i = 0; i < 60; i++) {
        let piece = document.createElement("div");
        piece.classList.add("confetti-piece");

        piece.style.left = Math.random() * 100 + "vw";
        piece.style.animationDuration = 3 + Math.random() * 4 + "s";
        piece.style.background = colors[Math.floor(Math.random() * colors.length)];

        confettiContainer.appendChild(piece);
    }
}

createConfetti();

/* ------------------ GOLD DOODLES ------------------ */
function addDoodles() {
    const doodles = ["⭐", "✨", "🎈", "🎉", "💛", "✦", "𖤐", "JIHAN"];
    const page = document.getElementById("page1");

    for (let i = 0; i < 25; i++) {
        let d = document.createElement("div");
        d.classList.add("doodle");

        d.innerText = doodles[Math.floor(Math.random() * doodles.length)];

        // Random positions BUT avoid center text area
        let topPos = Math.random() * 100;
        let leftPos = Math.random() * 100;

        // Avoid middle area
        if (topPos > 25 && topPos < 75 && leftPos > 20 && leftPos < 80) {
            i--;
            continue;
        }

        d.style.top = topPos + "vh";
        d.style.left = leftPos + "vw";

        d.style.animationDelay = (Math.random() * 4) + "s";

        page.appendChild(d);
    }
}

addDoodles();
</script>

</body>
</html>
