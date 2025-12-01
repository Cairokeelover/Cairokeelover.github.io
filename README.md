<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Birthday Journey (Secure)</title>

<style>
/* ========== GLOBAL STYLES ========== */
body {
    margin: 0;
    padding: 0;
    font-family: "Poppins", sans-serif;
    background: #ffffff;
}

/* Pages */
.page { display: none; text-align: center; padding: 40px; }
.active { display: block; }

/* Fade animation */
@keyframes fadeIn {
    from { opacity:0; transform: translateY(20px); }
    to   { opacity:1; transform: translateY(0); }
}

/* Headings */
h1 { font-size: 48px; color:#333; }
h2 { font-size: 24px; color:#666; }

/* Buttons */
button {
    margin-top: 30px;
    padding: 14px 25px;
    background: black;
    color: white;
    border: none;
    border-radius: 12px;
    font-size: 17px;
    cursor: pointer;
    transition: 0.3s;
}
button:hover { transform: scale(1.07); }

/* Back Button */
.back {
    position: absolute;
    top: 20px;
    left: 20px;
    background: white;
    color: black;
    border: 2px solid black;
}

/* Year Grid */
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
    padding: 10px;
    box-shadow: 0 4px 8px rgba(0,0,0,0.1);
    cursor: pointer;
    transition: 0.3s;
}
.year-box:hover {
    transform: scale(1.05);
    background: #fef9f0;
}

.calendar-header {
    background: #f5d76e;
    padding: 5px 0;
    color: black;
    border-radius: 10px 10px 0 0;
    font-weight: bold;
}

.calendar-year {
    font-size: 22px;
    font-weight: bold;
    padding: 10px;
}

/* Confetti */
.confetti-bg {
    position: fixed;
    top:0; left:0;
    width:100%; height:100%;
    pointer-events:none;
    z-index:-1;
}
.confetti-piece {
    position:absolute;
    width:8px; height:14px;
    opacity:0.7;
    border-radius:2px;
    animation: fall linear infinite;
}
@keyframes fall {
    0%   { transform: translateY(-50px); }
    100% { transform: translateY(110vh); }
}

/* LOGIN PAGE */
#loginPage {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
}
.login-box {
    text-align:center;
    border:2px solid #ddd;
    padding:40px;
    border-radius:15px;
    width:320px;
    background:white;
    box-shadow:0 4px 15px rgba(0,0,0,0.1);
}
input {
    width:85%;
    padding:12px;
    border:2px solid #ddd;
    border-radius:10px;
    margin-top:10px;
    outline:none;
}
.error { color:red; display:none; }
</style>
</head>

<body>

<!-- CONFETTI -->
<div class="confetti-bg" id="confetti"></div>

<!-- ========== LOGIN PAGE ========== -->
<div id="loginPage" class="active">
    <div class="login-box">
        <h2>🔒 Enter Password</h2>
        <input type="password" id="passwordInput" placeholder="Password">
        <button onclick="checkPassword()">Enter</button>
        <p id="errorMsg" class="error">Incorrect password.</p>
    </div>
</div>

<!-- ========== PAGE 1 ========== -->
<div id="page1" class="page">
    <h1>🎉 Happy Birthday Jojo 🎉</h1>
    <h2>03 / 03 / 2008</h2>

    <p>
        Happy birthday Jihan, with all love.<br>
        I wish for you all the best in this year and all the years coming.<br>
        May your journey be full of happiness, success, and beautiful memories.
    </p>

    <button onclick="showPage('page2')">Enter the Journey →</button>
</div>

<!-- ========== PAGE 2 (Years) ========== -->
<div id="page2" class="page">
    <button class="back" onclick="showPage('page1')">← Back</button>
    <h1>Select a Year</h1>

    <div class="year-grid">
        <div class="year-box" onclick="alert('2025 page coming soon!')">
            <div class="calendar-header">Year</div>
            <div class="calendar-year">2025</div>
        </div>

        <div class="year-box" onclick="alert('2026 page coming soon!')">
            <div class="calendar-header">Year</div>
            <div class="calendar-year">2026</div>
        </div>

        <div class="year-box" onclick="showPage('pageMore')">
            <div class="calendar-header">Year</div>
            <div class="calendar-year">more...</div>
        </div>
    </div>
</div>

<!-- ========== MORE YEARS PAGE ========== -->
<div id="pageMore" class="page">
    <button class="back" onclick="showPage('page2')">← Back</button>
    <h1>🎉 More Years Ahead 🎉</h1>
    <p>May each year bring you joy, love and success.</p>
</div>

<script>
/* ========== PASSWORD LOGIC ========== */
const correctPassword = "jojo2008";

function checkPassword() {
    const pass = document.getElementById("passwordInput").value;

    if (pass === correctPassword) {
        localStorage.setItem("birthday_access", "ok");
        document.getElementById("loginPage").style.display = "none";
        showPage("page1");
    } else {
        document.getElementById("errorMsg").style.display = "block";
    }
}

window.onload = () => {
    if (localStorage.getItem("birthday_access") === "ok") {
        document.getElementById("loginPage").style.display = "none";
        showPage("page1");
    }
};

/* ========== PAGE SWITCHING ========== */
function showPage(id) {
    document.querySelectorAll(".page").forEach(p => p.classList.remove("active"));
    document.getElementById(id).classList.add("active");
}

/* ========== CONFETTI ========== */
function createConfetti() {
    const container = document.getElementById("confetti");
    const colors = ["gold", "#f5d76e", "#e6c24c", "#fff4a3"];

    for (let i = 0; i < 60; i++) {
        let c = document.createElement("div");
        c.classList.add("confetti-piece");
        c.style.left = Math.random()*100 + "vw";
        c.style.animationDuration = (3 + Math.random()*4) + "s";
        c.style.background = colors[Math.floor(Math.random()*colors.length)];
        container.appendChild(c);
    }
}
createConfetti();
</script>

</body>
</html>
