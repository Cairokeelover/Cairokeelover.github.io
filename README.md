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
    #loginPage { display:flex; justify-content:center; align-items:center; height:100vh; flex-direction:column; }
    .login-box { text-align:center; }
    input[type=password] { padding:10px; font-size:16px; border-radius:8px; border:2px solid #ccc; margin-top:10px; }
    .error { color:red; display:none; margin-top:10px; }
    img { border-radius:10px; box-shadow:0 4px 10px rgba(0,0,0,0.1); object-fit:cover; }

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
    transform-origin: center center;
}

/* ---------- ROSE DRAW & BLOOM ---------- */
svg path {
    fill: none;
    stroke: #f3a6b8;
    stroke-width: 4;
    transform-origin: center center;
}

.rose-box svg {
    transform: scale(0.8);
    transition: transform 0.5s ease;
}
.rose-box.bloom svg {
    transform: scale(1);
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
    .rose-box svg {
        width: 150px;
        height: 180px;
    }
}
</style>
</head>

<body>

<!-- LOGIN -->  
<div id="login-container">
    <div class="container">
            <h1>Login to Jihan's Birthday Surprise</h1>
            <form id="login-form">
                <input type="password" id="password" placeholder="Enter Password" required>
                <button type="submit">Login</button>
            </form>
            <p id="error">Wrong password! Try again.</p>
        </div>
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
    animateRose();
}

function createHearts() {
    setInterval(() => {
        const heart = document.createElement("div");
        heart.className = "floating-heart";
        heart.innerHTML = "💖";
        heart.style.left = Math.random() * 100 + "vw";
        heart.style.animationDuration = (4 + Math.random() * 3) + "s";
        document.body.appendChild(heart);
        heart.addEventListener('animationend', () => heart.remove());
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
    const textEl = document.getElementById("text");
    if (i < message.length) {
        textEl.innerHTML += message[i] === "\n" ? "<br>" : message[i];
        i++;
        setTimeout(typeText, 50);
    }
}

function animateRose() {
    const path = document.querySelector("#roseSvg path");
    const roseBox = document.querySelector(".rose-box");
    const length = path.getTotalLength();

    path.style.strokeDasharray = length;
    path.style.strokeDashoffset = length;

    setTimeout(() => {
        roseBox.classList.add("bloom");
    }, 100);

    path.animate([
        { strokeDashoffset: length },
        { strokeDashoffset: 0 }
    ], {
        duration: 3000,
        easing: "ease",
        fill: "forwards"
    });
}
</script>

</body>
</html>
