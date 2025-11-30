<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Speech Page</title>

<style>
    body {
        margin: 0;
        padding: 0;
        background: white;
        overflow: hidden;
        font-family: Arial, sans-serif;
    }

    .content {
        position: relative;
        z-index: 10;
        text-align: center;
        margin-top: 180px;
        padding: 20px;
    }

    h1 {
        font-size: 28px;
        font-weight: bold;
    }

    /* Back button */
    .back-btn {
        position: fixed;
        top: 20px;
        left: 20px;
        background: #ffffff;
        padding: 12px 18px;
        border-radius: 12px;
        font-size: 16px;
        font-weight: bold;
        border: 2px solid black;
        cursor: pointer;
        transition: 0.3s;
        animation: floatBtn 2s ease-in-out infinite;
    }

    /* Hover animation */
    .back-btn:hover {
        transform: scale(1.1);
        box-shadow: 0px 0px 15px rgba(0,0,0,0.3);
    }

    /* Floating animation */
    @keyframes floatBtn {
        0% { transform: translateY(0); }
        50% { transform: translateY(-6px); }
        100% { transform: translateY(0); }
    }

    /* Confetti canvas */
    #confetti {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        z-index: 1; /* Behind content, visible */
        pointer-events: none;
    }
</style>
</head>

<body>

<canvas id="confetti"></canvas>

<button class="back-btn" onclick="window.location.href='index.html'">
    ⬅ Back
</button>

<div class="content">
    <h1>Your Speech Goes Here</h1>
</div>

<script>
/* Simple circle confetti */
const confettiCanvas = document.getElementById("confetti");
const ctx = confettiCanvas.getContext("2d");

function resizeCanvas() {
    confettiCanvas.width = window.innerWidth;
    confettiCanvas.height = window.innerHeight;
}
resizeCanvas();
window.addEventListener("resize", resizeCanvas);

let confetti = [];
for (let i = 0; i < 120; i++) {
    confetti.push({
        x: Math.random() * confettiCanvas.width,
        y: Math.random() * confettiCanvas.height,
        r: Math.random() * 6 + 2,
        speed: Math.random() * 2 + 1,
        color: `hsl(${Math.random()*360}, 70%, 60%)`
    });
}

function drawConfetti() {
    ctx.clearRect(0, 0, confettiCanvas.width, confettiCanvas.height);

    confetti.forEach(p => {
        ctx.beginPath();
        ctx.arc(p.x, p.y, p.r, 0, Math.PI * 2);
        ctx.fillStyle = p.color;
        ctx.fill();

        p.y += p.speed;
        if (p.y > confettiCanvas.height) {
            p.y = -10;
            p.x = Math.random() * confettiCanvas.width;
        }
    });

    requestAnimationFrame(drawConfetti);
}

drawConfetti();
</script>

</body>
</html>
