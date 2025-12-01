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

    .year-box .calendar-header {
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

    .year-box .calendar-year {
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

    /* GOLD DOODLES */
    .doodle {
        position: absolute;
        font-size: 60px;
        color: gold;
        font-weight: bold;
        opacity: 0.6;
        pointer-events: none;
        font-family: "Cursive", "Poppins", sans-serif;
    }

    /* MUSIC PLAYLIST */
    .playlist {
        display: flex;
        flex-direction: column;
        gap: 20px;
        margin-top: 30px;
    }

    .song {
        background: #fff9f0;
        border-radius: 12px;
        padding: 20px;
        box-shadow: 0 4px 12px rgba(0,0,0,0.1);
        transition: transform 0.3s, box-shadow 0.3s;
        position: relative;
    }

    .song:hover {
        transform: translateY(-5px);
        box-shadow: 0 6px 15px rgba(0,0,0,0.15);
    }

    .song-info {
        margin-bottom: 10px;
    }

    .song-title {
        font-weight: bold;
        font-size: 20px;
    }

    .song-artist {
        font-size: 16px;
        color: #666;
    }

    .song-controls {
        display: flex;
        align-items: center;
        gap: 10px;
        margin-top: 10px;
    }

    .song-controls button {
        padding: 8px 12px;
        border: none;
        border-radius: 6px;
        cursor: pointer;
        background: #f5d76e;
        font-size: 16px;
        transition: 0.2s;
    }

    .song-controls button:hover {
        background: #e6c24c;
        transform: scale(1.1);
    }

    .volume-slider {
        flex-grow: 1;
        cursor: pointer;
    }

    .progress-container {
        height: 5px;
        background: #e6d9c3;
        border-radius: 5px;
        overflow: hidden;
        margin-top: 10px;
    }

    .progress-bar {
        width: 0%;
        height: 100%;
        background: #f5d76e;
        transition: width 0.2s linear;
    }

    /* ALBUM */
    .album-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
        gap: 20px;
        margin-top: 30px;
    }

    .photo {
        position: relative;
        background: #fdf7f0;
        padding: 10px;
        border-radius: 16px;
        box-shadow: 0 4px 8px rgba(0,0,0,0.1);
        overflow: hidden;
        cursor: pointer;
        transition: transform 0.3s, box-shadow 0.3s;
    }

    .photo img {
        width: 100%;
        border-radius: 12px;
        display: block;
        transition: transform 0.3s;
    }

    .photo:hover {
        transform: scale(1.05);
        box-shadow: 0 6px 15px rgba(0,0,0,0.15);
    }

    .caption {
        position: absolute;
        bottom: 0;
        left: 0;
        width: 100%;
        padding: 10px;
        background: rgba(255, 245, 224, 0.85);
        color: #8b5e3c;
        font-weight: bold;
        font-size: 14px;
        text-align: center;
        opacity: 0;
        transition: opacity 0.3s;
        border-bottom-left-radius: 12px;
        border-bottom-right-radius: 12px;
    }

    .photo:hover .caption {
        opacity: 1;
    }

    .modal {
        display: none;
        position: fixed;
        z-index: 1000;
        padding-top: 60px;
        left: 0;
        top: 0;
        width: 100%;
        height: 100%;
        overflow: auto;
        background-color: rgba(0,0,0,0.8);
    }

    .modal-content {
        margin: auto;
        display: block;
        max-width: 80%;
        border-radius: 12px;
    }

    /* LETTERS */
    .letter {
        background: #fff9f0;
        border-radius: 12px;
        padding: 15px 20px;
        margin-bottom: 15px;
        box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    }

    .sender {
        font-weight: bold;
        margin-bottom: 8px;
        color: #8b5e3c;
    }

    .message {
        color: #333;
    }
</style>
</head>

<body>

<div class="confetti-bg" id="confetti"></div>

<!-- PAGE 1 -->
<div id="page1" class="page active">
    <div class="doodle" style="top: 20%; left: 10%; transform: rotate(-15deg);">J</div>
    <div class="doodle" style="top: 35%; left: 70%; transform: rotate(10deg);">I</div>
    <div class="doodle" style="top: 60%; left: 20%; transform: rotate(-25deg);">H</div>
    <div class="doodle" style="top: 55%; left: 60%; transform: rotate(5deg);">A</div>
    <div class="doodle" style="top: 80%; left: 40%; transform: rotate(-10deg);">N</div>

    <h1>🎉 Happy Birthday Jojo 🎉</h1>
    <h2>03 / 03 / 2008</h2>

    <p>
        Happy birthday Jihan, with all love.  
        I wish for you all the best in this year and all the years coming.  
        May your journey be full of happiness, success, and beautiful memories.
    </p>

    <button onclick="showPage('page2')">Enter the Journey →</button>
</div>

<!-- PAGE 2 -->
<div id="page2" class="page">
    <button class="back" onclick="showPage('page1')">← Back</button>
    <h1>Select a Year</h1>
    <div class="year-grid">
        <div class="year-box" onclick="showPage('page3')">
            <div class="calendar-header">Year</div>
            <div class="calendar-year">2025</div>
        </div>
        <div class="year-box" onclick="showPage('page3')">
            <div class="calendar-header">Year</div>
            <div class="calendar-year">2026</div>
        </div>
        <!-- Add other years similarly -->
        <div class="year-box" onclick="showPage('pageMore')">
            <div class="calendar-header">Year</div>
            <div class="calendar-year">more...</div>
        </div>
    </div>
</div>

<!-- PAGE 3 — SECTIONS -->
<div id="page3" class="page">
    <button class="back" onclick="showPage('page2')">← Back</button>
    <h1>2025 Memories</h1>
    <div class="section-grid">
        <div class="section-box" onclick="showPage('pageMusic')">🎵 Music of the Year</div>
        <div class="section-box" onclick="showPage('pageAlbum')">📸 Album 2025</div>
        <div class="section-box" onclick="showPage('pageLetters')">💌 Birthday Letters</div>
    </div>
</div>

<!-- PAGE MUSIC, ALBUM, LETTERS (integrated earlier) -->
<!-- Music, Album, Letters code from previous sections goes here -->

<!-- MODAL FOR ALBUM -->
<div id="photoModal" class="modal" onclick="this.style.display='none'">
    <img class="modal-content" id="modalImg">
</div>

<script>
function showPage(id) {
    document.querySelectorAll(".page").forEach(p => p.classList.remove("active"));
    document.getElementById(id).classList.add("active");
}

/* CONFETTI */
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

/* MUSIC FUNCTIONALITY */
let currentAudio = null;
let currentSongElement = null;
document.querySelectorAll(".song").forEach(song => {
    const playBtn = song.querySelector(".play-pause-btn");
    const nextBtn = song.querySelector(".next-btn");
    const prevBtn = song.querySelector(".prev-btn");
    const volumeSlider = song.querySelector(".volume-slider");
    const progressBar = song.querySelector(".progress-bar");
    let audio = new Audio(song.dataset.src);

    playBtn.addEventListener("click", () => {
        if(currentAudio && currentAudio !== audio){
            currentAudio.pause();
            if(currentSongElement){
                currentSongElement.querySelector(".play-pause-btn").textContent = "▶";
            }
        }
        currentAudio = audio;
        currentSongElement = song;
        if(audio.paused){
            audio.play();
            playBtn.textContent = "⏸";
        } else {
            audio.pause();
            playBtn.textContent = "▶";
        }
    });

    audio.addEventListener("timeupdate", () => {
        const percent = (audio.currentTime / audio.duration) * 100;
        progressBar.style.width = percent + "%";
    });

    volumeSlider.addEventListener("input", () => {
        audio.volume = volumeSlider.value / 100;
    });

    nextBtn.addEventListener("click", () => alert("Next song placeholder"));
    prevBtn.addEventListener("click", () => alert("Previous song placeholder"));
});

/* ALBUM MODAL */
document.querySelectorAll('.photo').forEach(photo => {
    photo.addEventListener('click', () => {
        const modal = document.getElementById('photoModal');
        const modalImg = document.getElementById('modalImg');
        modal.style.display = "block";
        modalImg.src = photo.querySelector('img').src;
    });
});
</script>

</body>
</html>
