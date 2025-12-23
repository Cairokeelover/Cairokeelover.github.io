 /* === PHOTO ALBUM LAYOUT === */
    .photo-album { display: flex; flex-wrap: wrap; justify-content: center; gap: 25px; margin-top: 25px; }
    .photo-card { background: white; width: 260px; border-radius: 15px; padding: 10px; box-shadow: 0 4px 15px rgba(0,0,0,0.15); transition: transform 0.2s ease; }
    .photo-card:hover { transform: scale(1.03); }
    .photo-card img { width: 100%; border-radius: 12px; }
    .caption { text-align: center; margin-top: 8px; font-size: 15px; color: #666; }
</style>
</head>
<body>

<div class="confetti-bg" id="confetti"></div>

<div id="loginPage">
    <div class="login-box">
        <h2>🔒 Enter Password</h2>
        <input type="password" id="passwordInput" placeholder="Password">
        <button onclick="checkPassword()">Enter</button>
        <p id="errorMsg" class="error">Incorrect password.</p>
    </div>
</div>

<div id="page1" class="page">
    <h1>🎉 Happy Birthday Jojo 🎉</h1>
    <h2>03 / 03 / 2008</h2>
    <p>
        Happy birthday Jihan, with all love.<br>
        I wish for you all the best in this year and all the years coming.<br>
        May your journey be full of happiness, success, and beautiful memories.
    </p>

    <!-- Music Player -->

<audio id="birthdayMusic" autoplay></audio>
<button onclick="toggleMusic()">⏯ Play / Pause Music</button>

    <button onclick="showPage('page2')">Enter the Journey →</button>
</div>

<div id="page2" class="page">
    <button class="back" onclick="showPage('page1')">← Back</button>
    <h1>Select a Year</h1>
    <div class="year-grid"></div>
</div>

<div id="page3" class="page">
    <button class="back" onclick="showPage('page2')">← Back</button>
    <h1 id="yearTitle">Year Memories</h1>
    <div class="section-grid">
        <div class="section-box" onclick="showPage('pageMusic')">🎵 Music of the Year</div>
        <div class="section-box" onclick="showPage('pageAlbum')">📸 Album of the Year</div>
        <div class="section-box" onclick="showPage('pageLetters')">💌 Birthday Letters</div>
    </div>
</div>

<div id="pageMusic" class="page">
    <button class="back" onclick="showPage('page3')">← Back</button>
    <h1>Music of the Year</h1>
    <p>(Place your songs here later)</p>
</div>

<div id="pageAlbum" class="page">
    <button class="back" onclick="showPage('page3')">← Back</button>
    <h1>Album of the Year</h1>
    <div id="photoAlbumContainer" class="photo-album"></div>
</div>

<div id="pageLetters" class="page">
    <button class="back" onclick="showPage('page3')">← Back</button>
    <h1>Birthday Letters</h1>
    <p>(Letters + names go here)</p>
</div>

<script>
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
    initMusic();
};

function showPage(id) {
    document.querySelectorAll(".page").forEach(p=>p.classList.remove("active"));
    document.getElementById(id).classList.add("active");

    if(id === "pageAlbum") loadGithubPhotos();
}

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

function generateYears() {
    const grid = document.querySelector(".year-grid");
    for(let year=2025; year<=2040; year++){
        let div=document.createElement("div");
        div.className="year-box";
        div.innerHTML=`<div class="calendar-header">Year</div><div class="calendar-year">${year}</div>`;
        div.onclick = () => {
            document.getElementById("yearTitle").innerText=year+" Memories";
            currentYear = year;
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

let currentYear = 2025;

/* === PHOTO ALBUM SYSTEM === */
const albumPhotos = {
    "2025": [
        "https://raw.githubusercontent.com/Cairokeelover/Cairokeelover.github.io/8e1708720a0fbf8e96846d8dc8f17998b596c9c4/Screenshot%202025-09-04%20135123.png",
        "https://raw.githubusercontent.com/Cairokeelover/Cairokeelover.github.io/8e1708720a0fbf8e96846d8dc8f17998b596c9c4/Screenshot%202025-09-06%20171636.png",
        "https://raw.githubusercontent.com/Cairokeelover/Cairokeelover.github.io/8e1708720a0fbf8e96846d8dc8f17998b596c9c4/Screenshot%202025-10-22%20221310.png"
    ]
};

function loadGithubPhotos() {
    const yearText = currentYear.toString();
    const container = document.getElementById("photoAlbumContainer");

    container.innerHTML = "";

    const photos = albumPhotos[yearText];
    if (!photos || photos.length === 0) {
        container.innerHTML = "<p>No photos for this year yet.</p>";
        return;
    }

    photos.forEach((url, index) => {
        const card = document.createElement("div");
        card.className = "photo-card";
        card.innerHTML = `<img src="${url}" alt="Photo ${index}"><p class="caption">Memory ${index + 1} - ${yearText}</p>`;
        container.appendChild(card);
    });
}

/* === MUSIC SYSTEM === */

const songs = ["https://github.com/Cairokeelover/Cairokeelover.github.io/blob/main/Eva%20-%20Anniversaire%20(Audio%20Officiel).mp3"
 ];

let musicIndex = 0;
let musicPlayer;

function initMusic() {
    musicPlayer = document.getElementById("birthdayMusic");
    playNextSong();
    musicPlayer.addEventListener("ended", playNextSong);
}

function playNextSong() {
    musicPlayer.src = songs[musicIndex];
    musicPlayer.play();
    musicIndex = (musicIndex + 1) % songs.length;
}

function toggleMusic() {
    if(musicPlayer.paused) musicPlayer.play();
    else musicPlayer.pause();
}
</script>

</body>
</html>


