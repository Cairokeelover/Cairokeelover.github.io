<!DOCTYPE html>
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
        background: #f9f5ef; /* beige */
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
        font-size: 42px;
        margin-bottom: 10px;
        color: #333;
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

    /* Back button */
    .back {
        position: absolute;
        top: 20px;
        left: 20px;
        background: white;
        color: black;
        border: 2px solid black;
        font-weight: bold;
    }

    /* Years grid */
    .year-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
        gap: 20px;
        margin-top: 40px;
    }

    .year-box {
        padding: 25px;
        background: white;
        font-size: 22px;
        border-radius: 14px;
        border: 2px solid #ddd;
        cursor: pointer;
        transition: 0.3s;
    }

    .year-box:hover {
        background: #ececec;
        transform: scale(1.05);
    }

    /* Three sections (music / album / letters) */
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
</style>
</head>

<body>

<!-- PAGE 1 — FIRST INTERFACE -->
<div id="page1" class="page active">
    <h1>🎉 Happy Birthday Jojo 🎉</h1>
    <h2>03 / 03 / 2008</h2>

    <p>
        Happy birthday Jihan, with all love.  
        I wish for you all the best in this year and all the years coming.  
        May your journey be full of happiness, success, and beautiful memories.
    </p>

    <button onclick="showPage('page2')">Enter the Journey →</button>
</div>

<!-- PAGE 2 — YEARS -->
<div id="page2" class="page">
    <button class="back" onclick="showPage('page1')">← Back</button>

    <h1>Select a Year</h1>

    <div class="year-grid">
        <div class="year-box" onclick="showPage('page3')">2025</div>
        <div class="year-box" onclick="showPage('page3')">2026</div>
        <div class="year-box" onclick="showPage('page3')">2027</div>
        <div class="year-box" onclick="showPage('page3')">2028</div>
        <div class="year-box" onclick="showPage('page3')">2029</div>
        <div class="year-box" onclick="showPage('page3')">2030</div>
        <div class="year-box" onclick="showPage('page3')">2031</div>
        <div class="year-box" onclick="showPage('page3')">2032</div>
        <div class="year-box" onclick="showPage('page3')">2033</div>
        <div class="year-box" onclick="showPage('page3')">2034</div>
        <div class="year-box" onclick="showPage('page3')">2035</div>
        <div class="year-box" onclick="showPage('page3')">2036</div>
        <div class="year-box" onclick="showPage('page3')">2037</div>
        <div class="year-box" onclick="showPage('page3')">2038</div>
        <div class="year-box" onclick="showPage('page3')">2039</div>
        <div class="year-box" onclick="showPage('page3')">2040</div> 
        <div class="year-box" onclick="showPage('page3')">more...</div>
    </div>
</div>

<!-- PAGE 3 — THREE BOXES -->
<div id="page3" class="page">
    <button class="back" onclick="showPage('page2')">← Back</button>

    <h1>2025 Memories</h1>

    <div class="section-grid">
        <div class="section-box" onclick="showPage('pageMusic')">🎵 Music of the Year</div>
        <div class="section-box" onclick="showPage('pageAlbum')">📸 Album 2025</div>
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
    <h1>Album 2025</h1>
    <p>(Photos will go here)</p>
</div>

<!-- PAGE — LETTERS -->
<div id="pageLetters" class="page">
    <button class="back" onclick="showPage('page3')">← Back</button>
    <h1>Birthday Letters</h1>
    <p>(Letters + names go here)</p>
</div>

<script>
function showPage(id) {
    document.querySelectorAll(".page").forEach(p => p.classList.remove("active"));
    document.getElementById(id).classList.add("active");
}
</script>

</body>
</html>

