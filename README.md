<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>For Jihan 💖</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
body {
    margin: 0;
    font-family: "Poppins", sans-serif;
    overflow: hidden;
}

/* ---------- LOGIN ---------- */
.login {
    height: 100vh;
    background: white;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
}

.login input {
    padding: 12px;
    width: 220px;
    border-radius: 20px;
    border: 1px solid #ccc;
    text-align: center;
    margin-bottom: 15px;
}

.login button {
    padding: 10px 30px;
    border-radius: 20px;
    border: none;
    background: #f3a6b8;
    color: white;
    font-size: 16px;
    cursor: pointer;
}

/* ---------- HEART PAGE ---------- */
.heart-page {
    display: none;
    height: 100vh;
    background: #f4e3dc;
    position: relative;
}

.guide {
    position: absolute;
    top: 45%;
    left: 50%;
    transform: translate(-50%, -50%);
    text-align: center;
    color: #a56a6a;
}

.line {
    width: 2px;
    height: 60px;
    background: #a56a6a;
    margin: 10px auto;
}

.heart {
    font-size: 42px;
    cursor: pointer;
    animation: pulse 1.5s infinite;
}

@keyframes pulse {
    0% { transform: scale(1); }
    50% { transform: scale(1.3); }
    100% { transform: scale(1); }
}

/* ---------- FLOATING HEARTS ---------- */
.floating-heart {
    position: absolute;
    bottom: -10%;
    font-size: 18px;
    animation: floatUp 6s linear infinite;
    opacity: 0.8;
}

@keyframes floatUp {
    from { transform: translateY(0); opacity: 1; }
    to { transform: translateY(-120vh); opacity: 0; }
}

/* ---------- FINAL PAGE ---------- */
.final {
    display: none;
    height: 100vh;
    background: #f4e3dc;
    padding: 40px;
}

/* CONTENT */
.content {
    display: flex;
    align-items: center;
    justify-content: space-between;
    height: 100%;
}

/* TEXT LEFT */
.message {
    width: 45%;
    font-size: 20px;
    color: #6b3f3f;
    line-height: 1.6;
    white-space: pre-line;
}

/* ROSE RIGHT */
.rose {
    width: 45%;
    display: flex;
    justify-content: center;
}

svg {
    width: 260px;
}

/* DRAW ROSE */
path {
    fill: none;
    stroke: #e8a1b0;
    stroke-width: 3;
    stroke-dasharray: 1000;
    stroke-dashoffset: 1000;
    animation: draw 4s ease forwards;
}

@keyframes draw {
    to { stroke-dashoffset: 0; }
}

/* ---------- MOBILE ---------- */
@media (max-width: 768px) {
    .content {
        flex-direction: column;
        text-align: center;
    }

    .message, .rose {
        width: 100%;
    }

    svg {
        width: 220px;
        margin-bottom: 20px;
    }
}
</style>
</head>

<body>

<!-- LOGIN -->
<div class="login" id="login">
    <h2>Welcome 💕</h2>
    <input type="password" id="password" placeholder="Enter password"
           onkeydown="if(event.key==='Enter') goHeart()">
    <button onclick="goHeart()">Enter</button>
</div>

<!-- HEART PAGE -->
<div class="heart-page" id="heartPage">
    <div class="guide">
        <div class="line"></div>
        <div>Click here</div>
        <div class="heart" onclick="openGift()">❤️</div>
    </div>
</div>

<!-- FINAL PAGE -->
<div class="final" id="finalPage">
    <div class="content">

        <!-- TEXT LEFT -->
        <div class="message" id="typing"></div>

        <!-- ROSE RIGHT -->
        <div class="rose">
            <svg id="roseSvg" viewBox="0 0 200 300">
                <path d="M100 280 C90 220 70 180 100 150 C130 180 110 220 100 280"/>
                <path d="M100 150 C60 120 60 80 100 60 C140 80 140 120 100 150"/>
                <path d="M100 140 C80 110 90 90 100 80 C110 90 120 110 100 140"/>
            </svg>
        </div>

    </div>
</div>

<script>
function goHeart() {
    const password = document.getElementById("password").value;

    if (password === "jojo2008") {
        document.getElementById("login").style.display = "none";
        document.getElementById("heartPage").style.display = "block";
        startFloatingHearts();
    } else {
        alert("Wrong password 💔");
    }
}

function openGift() {
    document.getElementById("heartPage").style.display = "none";

    const final = document.getElementById("finalPage");
    final.style.display = "block";

    // reset rose animation
    const svg = document.getElementById("roseSvg");
    svg.style.display = "none";
    svg.offsetHeight;
    svg.style.display = "block";

    typeText();
}

/* FLOATING HEARTS */
function startFloatingHearts() {
    setInterval(() => {
        const heart = document.createElement("div");
        heart.className = "floating-heart";
        heart.innerHTML = "💗";
        heart.style.left = Math.random() * 100 + "vw";
        heart.style.fontSize = Math.random() * 20 + 15 + "px";
        document.body.appendChild(heart);
        setTimeout(() => heart.remove(), 6000);
    }, 400);
}

/* TYPING TEXT */
const text = `Hey Jihan 💖

Happy Birthday 🎉✨
May God bless you 🙏
And give you happiness 🌷

Just want to say you’re sooo awesome 💕
Hope you have a great day 🌸
Today is your day 🎂💫

💖🌷🎉`;

let i = 0;
function typeText() {
    if (i < text.length) {
        document.getElementById("typing").innerHTML += text.charAt(i);
        i++;
        setTimeout(typeText, 40);
    }
}
</script>

</body>
</html>
