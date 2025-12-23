<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Birthday Jihan!</title>
    <style>
        body {
            font-family: Arial, sans-serif;
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
        }

        #birthday-container {
            background: #f4e1d2; /* Rose beige */
            display: none;
            justify-content: center;
            align-items: center;
            height: 100vh;
            position: relative;
        }

        .container {
            text-align: center;
            background: rgba(255, 255, 255, 0.9);
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.2);
        }

        #login-form input, #login-form button {
            margin: 10px;
            padding: 10px;
            border: none;
            border-radius: 5px;
        }

        #login-form button {
            background: #ff6b6b;
            color: white;
            cursor: pointer;
        }

        #login-form button:hover {
            background: #ff5252;
        }

        #error {
            color: red;
            display: none;
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
        }

        #heart.clicked {
            opacity: 0;
            transform: translate(-50%, -50%) scale(0);
        }

        #rose {
            font-size: 200px;
            color: #ffb6c1; /* Light pink */
            position: absolute;
            right: 10%;
            top: 50%;
            transform: translateY(-50%);
            opacity: 0;
            transition: opacity 1s ease;
        }

        #rose.show {
            opacity: 1;
        }

        #text-container {
            position: absolute;
            left: 10%;
            top: 50%;
            transform: translateY(-50%);
            font-size: 24px;
            color: #333;
            max-width: 400px;
            text-align: left;
        }

        #typing-text {
            border-right: 2px solid #333;
            animation: blink 1s infinite;
        }

        @keyframes blink {
            0%, 50% { border-color: transparent; }
            51%, 100% { border-color: #333; }
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
        <div id="rose">🌹</div>
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

        // Typing effect for the message
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
    </script>
</body>
</html>
