<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Birthday Jihan!</title>
    <style>
        body {
            font-family: 'Courier New', monospace; /* Letter-like font */
            margin: 0;
            padding: 0;
            height: 100vh;
            overflow: hidden;
            transition: background 0.5s ease;
        }

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

        #birthday-container {
            background: #f4e1d2; /* Rose beige */
            display: none;
            justify-content: center;
            align-items: center;
            height: 100vh;
            position: relative;
            animation: slideIn 1s ease-out;
        }

        @keyframes slideIn {
            from { transform: translateX(-100%); }
            to { transform: translateX(0); }
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

        #heart {
            font-size: 100px;
            color: red;
            cursor: pointer;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            transition: all 1s ease;
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0% { transform: translate(-50%, -50%) scale(1); }
            50% { transform: translate(-50%, -50%) scale(1.1); }
            100% { transform: translate(-50%, -50%) scale(1); }
        }

        #heart.clicked {
            opacity: 0;
            transform: translate(-50%, -50%) scale(0);
        }

        #rose {
            position: absolute;
            right: 10%;
            top: 50%;
            transform: translateY(-50%);
            opacity: 0;
            transition: opacity 1s ease;
            animation: bloom 2s ease-in-out forwards;
        }

        @keyframes bloom {
            0% { transform: translateY(-50%) scale(0.5) rotate(0deg); }
            50% { transform: translateY(-50%) scale(1.2) rotate(180deg); }
            100% { transform: translateY(-50%) scale(1) rotate(360deg); }
        }

        #rose.show {
            opacity: 1;
        }

        #text-container {
            position: absolute;
            left: 10%;
            top: 50%;
            transform: translateY(-50%);
            font-size: 18px; /* Smaller font */
            color: #333;
            max-width: 400px;
            text-align: left;
            background: rgba(255, 255, 255, 0.8);
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            border: 2px solid #d4a574; /* Letter-like border */
            animation: fadeInUp 1s ease-out;
        }

        @keyframes fadeInUp {
            from { opacity: 0; transform: translateY(-50%) translateY(20px); }
            to { opacity: 1; transform: translateY(-50%) translateY(0); }
        }

        #typing-text {
            border-right: 2px solid #333;
            animation: blink 1s infinite;
        }

        @keyframes blink {
            0%, 50% { border-color: transparent; }
            51%, 100% { border-color: #333; }
        }

        /* Falling Hearts Animation */
        .heart {
            position: absolute;
            font-size: 24px;
            color: red;
            animation: fall linear infinite;
            pointer-events: none;
        }

        @keyframes fall {
            0% { transform: translateY(-100vh) rotate(0deg); opacity: 1; }
            100% { transform: translateY(100vh) rotate(360deg); opacity: 0; }
        }
    </style>
</head>
<body>
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
    
    <div id="birthday-container">
        <div id="heart" title="Click here">❤️<br><small>Click here</small></div>
        <!-- Realistic Animated Rose (using SVG for simplicity) -->
        <svg id="rose" width="200" height="300" viewBox="0 0 200 300" xmlns="http://www.w3.org/2000/svg">
            <defs>
                <radialGradient id="petalGrad" cx="50%" cy="50%" r="50%">
                    <stop offset="0%" style="stop-color:#ff69b4;stop-opacity:1" />
                    <stop offset="100%" style="stop-color:#ffb6c1;stop-opacity:1" />
                </radialGradient>
            </defs>
            <!-- Stem -->
            <rect x="95" y="200" width="10" height="100" fill="#228B22" />
            <!-- Petals (animated) -->
            <ellipse cx="100" cy="150" rx="40" ry="60" fill="url(#petalGrad)" transform="rotate(-30 100 150)" class="petal" />
            <ellipse cx="100" cy="150" rx="40" ry="60" fill="url(#petalGrad)" transform="rotate(30 100 150)" class="petal" />
            <ellipse cx="100" cy="150" rx="40" ry="60" fill="url(#petalGrad)" transform="rotate(90 100 150)" class="petal" />
            <ellipse cx="100" cy="150" rx="40" ry="60" fill="url(#petalGrad)" transform="rotate(150 100 150)" class="petal" />
            <ellipse cx="100" cy="150" rx="40" ry="60" fill="url(#petalGrad)" transform="rotate(-90 100 150)" class="petal" />
            <!-- Center -->
            <circle cx="100" cy="150" r="15" fill="#FFD700" />
        </svg>
        <div id="text-container">
            <div id="typing-text"></div>
        </div>
    </div>

    <script>
        // Simple login logic (hardcoded password: "birthday2023" - change this!)
        document.getElementById('login-form').addEventListener('submit', function(e) {
            e.preventDefault();
            const password = document.getElementById('password').value;
            if (password === 'birthday2023') {
                document.getElementById('login-container').style.display = 'none';
                document.getElementById('birthday-container').style.display = 'flex';
                startFallingHearts(); // Start hearts falling
            } else {
                document.getElementById('error').style.display = 'block';
            }
        });

        // Heart click to transform to rose and start typing
        document.getElementById('heart').addEventListener('click', function() {
            this.classList.add('clicked');
            document.getElementById('rose').classList.add('show');
            typeText();
        });

        // Typing effect for the message (letter-style, smaller)
        const message = "Hey Jihan! 🎉 Happy Birthday! 🎂 May God bless you and give you happiness. 🌟 Just want to say you're sooo awesome! 😍 Hope you have a great day – today is YOUR day! 🥳 Etc... 💖";
        let index = 0;
        function typeText() {
            if (index < message.length) {
                document.getElementById('typing-text').innerHTML += message.charAt(index);
                index++;
                setTimeout(typeText, 100); // Adjust speed here
            } else {
                document.getElementById('typing-text').style.borderRight = 'none'; // Remove cursor after typing
            }
        }

        // Falling Hearts Animation
        function startFallingHearts() {
            setInterval(() => {
                const heart = document.createElement('div');
                heart.className = 'heart';
                heart.innerHTML = '❤️';
                heart.style.left = Math.random() * 100 + 'vw';
                heart.style.animationDuration = (Math.random() * 3 + 2) + 's'; // Random speed
                document.body.appendChild(heart);
                setTimeout(() => {
                    heart.remove();
                }, 5000); // Remove after falling
            }, 300); // New heart every 300ms
        }
    </script>
</body>
</html>
