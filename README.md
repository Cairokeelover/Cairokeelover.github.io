<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Birthday Jihan!</title>
    <style>
        body {
            font-family: 'Poppins', sans-serif;
            margin: 0;
            padding: 0;
            height: 100vh;
            overflow: hidden;
            transition: background 0.5s ease;
        }

        /* Login Page Styles (from previous version) */
        #login-container {
            background: white;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            animation: fadeIn 2s ease-in-out;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(-20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .container {
            text-align: center;
            background: rgba(255, 255, 255, 0.9);
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.2);
            animation: bounceIn 1s ease-out;
        }

        @keyframes bounceIn {
            0% { transform: scale(0.3); opacity: 0; }
            50% { transform: scale(1.05); }
            70% { transform: scale(0.9); }
            100% { transform: scale(1); opacity: 1; }
        }

        #login-form input, #login-form button {
            margin: 10px;
            padding: 10px;
            border: none;
            border-radius: 5px;
            transition: all 0.3s ease;
        }

        #login-form input:focus {
            box-shadow: 0 0 10px rgba(255, 107, 107, 0.5);
        }

        #login-form button {
            background: #ff6b6b;
            color: white;
            cursor: pointer;
        }

        #login-form button:hover {
            background: #ff5252;
            transform: scale(1.1);
        }

        #error {
            color: red;
            display: none;
            animation: shake 0.5s ease-in-out;
        }

        @keyframes shake {
            0%, 100% { transform: translateX(0); }
            25% { transform: translateX(-5px); }
            75% { transform: translateX(5px); }
        }

        /* Heart Page Styles */
        .heart-page {
            display: none;
            height: 100vh;
            background: #f4e3dc;
            position: relative;
            animation: slideIn 1s ease-out;
        }

        @keyframes slideIn {
            from { transform: translateX(-100%); }
            to { transform: translateX(0); }
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
            animation: pulse 1.5s infinite, glow 2s infinite alternate;
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.2); }
            100% { transform: scale(1); }
        }

        @keyframes glow {
            from { text-shadow: 0 0 5px #ff69b4; }
            to { text-shadow: 0 0 20px #ff69b4, 0 0 30px #ff69b4; }
        }

        /* Floating Hearts */
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

        /* Final Page Styles */
        .final {
            display: none;
            height: 100vh;
            background: #f4e3dc;
            display: flex;
            flex-direction: row;
            align-items: center;
            padding: 20px;
            position: relative;
        }

        .message {
            width: 50%;
            font-size: 18px;
            color: #6b3f3f;
            line-height: 1.6;
            padding: 10px;
            animation: sparkle 2s infinite alternate;
        }

        @keyframes sparkle {
            from { text-shadow: 0 0 5px #ffd700; }
            to { text-shadow: 0 0 15px #ffd700, 0 0 25px #ffd700; }
        }

        .rose-box {
            width: 50%;
            display: flex;
            justify-content: center;
            perspective: 1000px; /* For 3D effect */
        }

        /* 3D Rose */
        .rose-3d {
            position: relative;
            width: 200px;
            height: 250px;
            transform-style: preserve-3d;
            animation: bloom3d 3s ease-in-out forwards;
        }

        @keyframes bloom3d {
            0% { transform: scale(0.5) rotateX(0deg) rotateY(0deg); }
            50% { transform: scale(1.2) rotateX(180deg) rotateY(180deg); }
            100% { transform: scale(1) rotateX(360deg) rotateY(360deg); }
        }

        .petal {
            position: absolute;
            width: 80px;
            height: 120px;
            background: linear-gradient(45deg, #ff69b4, #ffb6c1);
            border-radius: 50% 50% 50% 50% / 60% 60% 40% 40%;
            box-shadow: 0 0 10px rgba(255, 105, 180, 0.5);
            transform-origin: bottom center;
        }

        .petal:nth-child(1) { transform: rotateY(0deg) translateZ(20px); }
        .petal:nth-child(2) { transform: rotateY(72deg) translateZ(20px); }
        .petal:nth-child(3) { transform: rotateY(144deg) translateZ(20px); }
        .petal:nth-child(4) { transform: rotateY(216deg) translateZ(20px); }
        .petal:nth-child(5) { transform: rotateY(288deg) translateZ(20px); }

        .stem {
            position: absolute;
            bottom: 0;
            width: 10px;
            height: 150px;
            background: #228B22;
            left: 50%;
            transform: translateX(-50%);
            border-radius: 5px;
        }

        .center {
            position: absolute;
            top: 50%;
            left: 50%;
            width: 20px;
            height: 20px;
            background: #FFD700;
            border-radius: 50%;
            transform: translate(-50%, -50%) translateZ(30px);
        }

        /* Confetti Rain */
        .confetti {
            position: absolute;
            width: 10px;
            height: 10px;
            background: gold;
            animation: confettiFall 5s linear infinite;
            opacity: 0.8;
        }

        @keyframes confettiFall {
            0% { transform: translateY(-100vh) rotate(0deg); }
            100% { transform: translateY(100vh) rotate(360deg); }
        }

        /* Music Toggle */
        #music-toggle {
            position: absolute;
            top: 20px;
            right: 20px;
            background: #ff6b6b;
            color: white;
            border: none;
            padding: 10px;
            border-radius: 50%;
            cursor: pointer;
            font-size: 16px;
        }

        /* Mobile */
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
    <!-- Login Page -->
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

    <!-- Heart Page -->
    <div class="heart-page" id="heartPage">
        <div class="guide">
            <div class="line"></div>
            <div>Click here</div>
            <div class="heart" onclick="openGift()">❤️</div>
        </div>
    </div>

    <!-- Final Page -->
    <div class="final" id="finalPage">
        <button id="music-toggle" onclick="toggleMusic()">🎵</button>
        <div class="message" id="text"></div>
        <div class="rose-box">
            <div class="rose-3d">
                <div class="petal"></div>
                <div class="petal"></div>
                <div class="petal"></div>
                <div class="petal"></div>
                <div class="petal"></div>
                <div class="stem"></div>
                <div class="center"></div>
            </div>
        </div>
    </div>

    <!-- Background Music (Optional) -->
    <audio id="bg-music" loop>
        <source src="https://www.soundjay.com/misc/sounds/bell-ringing-05.wav" type="audio/wav"> <!-- Replace with a birthday tune URL if available -->
    </audio>

    <script>
        // Login Logic
        document.getElementById('login-form').addEventListener('submit', function(e) {
            e.preventDefault();
            const password = document.getElementById('password').value;
            if (password === 'jojo2008') {
                document.getElementById('login-container').style.display = 'none';
                document.getElementById('heartPage').style.display = 'block';
                createHearts();
            } else {
                document.getElementById('error').style.display = 'block';
            }
        });

        // Heart Click to Open Gift
        function openGift() {
            document.getElementById('heartPage').style.display = 'none';
            document.getElementById('finalPage').style.display = 'flex';
            typeText();
            startConfetti();
        }

        // Floating Hearts
        function createHearts() {
            setInterval(() => {
                const heart = document.createElement('div');
                heart.className = 'floating-heart';
                heart.innerHTML = '💖';
                heart.style.left = Math.random() * 100 + 'vw';
                heart.style.animationDuration = (4 + Math.random() * 3) + 's';
                document.body.appendChild(heart);
                heart.addEventListener('animationend', () => heart.remove());
            }, 400);
        }

        // Typing Text
        const message = `Hey Jihan 💖\nHappy Birthday 🎉✨\nMay God bless you 🙏\nAnd give you happiness 🌷\n\nJust want to say you’re sooo awesome 💕\nHope you have a great day 🌸\nToday is your day 🎂💫`;
        let i = 0;
        function typeText() {
            const textEl = document.getElementById('text');
            if (i < message.length) {
                textEl.innerHTML += message[i] === '\n' ? '<br>' : message[i];
                i++;
                setTimeout(typeText, 50);
            }
        }

        // Confetti Rain
        function startConfetti() {
            setInterval(() => {
                const confetti = document.createElement('div');
                confetti.className = 'confetti';
                confetti.style.left = Math.random() * 100 + 'vw';
                confetti.style.animationDuration = (3 + Math.random() * 2) + 's';
                document.body.appendChild(confetti);
                setTimeout(() => confetti.remove(), 5000);
            }, 200);
        }

        // Music Toggle
        let musicPlaying = false;
        function toggleMusic() {
            const audio = document.getElementById('bg-music');
            if (musicPlaying) {
                audio.pause();
                musicPlaying = false;
            } else {
                audio.play();
                musicPlaying = true;
            }
        }
    </script>
</body>
</html>
