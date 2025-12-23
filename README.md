<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>For Jihan 💖</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
* { box-sizing: border-box; }

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
    flex-direction: column;
    justify-content: center;
    align-items: center;
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
    font-size: 45px;
    cursor: pointer;
    animation: pulse 1.5s infinite;
}

@keyframes pulse {
    0% { transform: scale(1); }
    50% { transform: scale(1.2); }
    100% { transform: scale(1); }
}

/* ---------- FLOATING HEARTS ---------- */
.floating-heart {
    position: absolute;
    bottom: -10px;
    font-size: 20px;
    animation: float 6s linear infinite;
    opacity: 0.7;
}

@keyframes float {
    0% { transform: translateY(0); opacity: 1; }
    100% { transform: translateY(-120vh); opacity: 0; }
}

/* ---------- FINAL PAGE ---------- */
.final {
    display: none;
    height: 100vh;
    background: #f4e3dc;
    display: flex;
    flex-direction: row;
    align-items: center;
    padding: 20px;
}

.message {
    width: 50%;
    font-size: 18px;
    color: #6b3f3f;
    line-height: 1.6;
    padding: 10px;
}

.rose-box {
    width: 50%;
    display: flex;
    justify-content: center;
}

/* ---------- ROSE DRAW ---------- */
svg path {
    fill: none;
    stroke: #f3a6b8;
    stroke-width: 4;
    stroke-dasharray: 1000;
    stroke-dashoffset: 1000;
    animation: draw 3s ease forwards;
}

@keyframes draw {
    to { stroke-dashoffset: 0; }
}

/* ---------- MOBILE ---------- */
@media (max-width: 768px) {
    .final {
        flex-direction: column;
    }
    .message, .rose-box {
        width: 100%;
        text-align: center;
    }
}
</style>
</head>

<body>

<!-- LOGIN -->
<div class="login" id="login">
    <h2>Welcome 💕</h2>
    <input type="password" id="password" placeholder="Password">
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

<!-- FINAL -->
<div class="final" id="finalPage">
    <div class="message" id="text"></div>

    <div class="rose-box">
        <svg id="roseSvg" width="180" height="220" viewBox="0 0 200 250">
            <path d="M100 230 C90 180 60 160 80 120 C60 80 100 60 120 80 C160 60 190 100 160 130 C180 170 140 190 120 220" />
        </svg>
    </div>
</div>

<script>
function goHeart() {
    const pass = document.getElementById("password").value;
    if (pass !== "jojo2008") {
        alert("Wrong password 💔");
        return;
    }
    document.getElementById("login").style.display = "none";
    document.getElementById("heartPage").style.display = "block";
    createHearts();
}

function openGift() {
    document.getElementById("heartPage").style.display = "none";
    document.getElementById("finalPage").style.display = "flex";
    typeText();
}

function createHearts() {
    setInterval(() => {
        const heart = document.createElement("div");
        heart.className = "floating-heart";
        heart.innerHTML = "💖";
        heart.style.left = Math.random() * 100 + "vw";
        heart.style.animationDuration = (4 + Math.random() * 3) + "s";
        document.body.appendChild(heart);
        setTimeout(() => heart.remove(), 6000);
    }, 400);
}

const message =
`Hey Jihan 💖
Happy Birthday 🎉✨
May God bless you 🙏
And give you happiness 🌷

Just want to say you’re sooo awesome 💕
Hope you have a great day 🌸
Today is your day 🎂💫`;

let i = 0;
function typeText() {
    if (i < message.length) {
        document.getElementById("text").innerHTML += message.charAt(i).replace("\n","<br>");
        i++;
        setTimeout(typeText, 50);
    }
}
</script>

</body>
</html>
