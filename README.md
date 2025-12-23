<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Birthday Jihan!</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: linear-gradient(45deg, #ff9a9e, #fecfef);
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            overflow: hidden;
        }

        .container {
            text-align: center;
            background: rgba(255, 255, 255, 0.9);
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.2);
            transform: rotateX(10deg) rotateY(10deg);
            transition: transform 0.5s ease;
        }

        .container:hover {
            transform: rotateX(0deg) rotateY(0deg);
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

        #3d-scene {
            width: 100%;
            height: 400px;
        }
    </style>
</head>
<body>
    <div id="login-container" class="container">
        <h1>Login to Jihan's Birthday Surprise</h1>
        <form id="login-form">
            <input type="password" id="password" placeholder="Enter Password" required>
            <button type="submit">Login</button>
        </form>
        <p id="error" style="color: red; display: none;">Wrong password! Try again.</p>
    </div>
    
    <div id="birthday-container" class="container" style="display: none;">
        <h1>Happy Birthday, Jihan! 🎉</h1>
        <p>Wishing you a day filled with joy, love, and all your favorite things!</p>
        <div id="3d-scene"></div>
    </div>

    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <script>
        // Simple login logic (hardcoded password: "birthday2023" - change this!)
        document.getElementById('login-form').addEventListener('submit', function(e) {
            e.preventDefault();
            const password = document.getElementById('password').value;
            if (password === 'birthday2023') {
                document.getElementById('login-container').style.display = 'none';
                document.getElementById('birthday-container').style.display = 'block';
                init3DScene();
            } else {
                document.getElementById('error').style.display = 'block';
            }
        });

        // 3D Animation using Three.js (floating balloons)
        function init3DScene() {
            const scene = new THREE.Scene();
            const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
            const renderer = new THREE.WebGLRenderer();
            renderer.setSize(window.innerWidth, window.innerHeight);
            document.getElementById('3d-scene').appendChild(renderer.domElement);

            // Add some balloons (spheres)
            const geometry = new THREE.SphereGeometry(1, 32, 32);
            const material = new THREE.MeshBasicMaterial({ color: 0xff0000 });
            for (let i = 0; i < 10; i++) {
                const balloon = new THREE.Mesh(geometry, material);
                balloon.position.set(Math.random() * 20 - 10, Math.random() * 20 - 10, Math.random() * 20 - 10);
                scene.add(balloon);
            }

            camera.position.z = 5;

            function animate() {
                requestAnimationFrame(animate);
                scene.rotation.y += 0.01; // Rotate the scene
                renderer.render(scene, camera);
            }
            animate();
        }
    </script>
</body>
</html>
