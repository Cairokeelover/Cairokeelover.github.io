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

    /* ---------- LOGIN PAGE ---------- */
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
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 30px;
    }

    .rose {
        font-size: 120px;
        animation: bloom 1.5s ease;
    }

    @keyframes bloom {
        from { transform: scale(0); opacity: 0; }
        to { transform: scale(1); opacity: 1; }
    }

    .message {
        max-width: 420px;
        font-size: 20px;
        color: #6b3f3f;
        line-height: 1.6;
        white-space: pre-line;
    }

    /* ---------- MOBILE ---------- */
    @media (max-width: 768px) {
        .final {
            flex-direction: column;
            text-align: center;
        }

        .rose {
            font-size: 100px;
            margin-bottom: 20px;
        }

        .message {
            font-size: 18px;
        }
    }
</style>
</head>

<body>

<!-- LOGIN PAGE -->
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
    <div class="rose">🌸</div>
    <div class="message" id="typing"></div>
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
        document.getElementById("finalPage").style.display = "flex";
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
