<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy New Year!</title>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Orbitron', sans-serif;
            background: linear-gradient(135deg, #0f0f23, #1a1a2e, #16213e);
            background-size: 400% 400%;
            animation: bgShift 10s ease-in-out infinite;
            color: #ffffff;
            text-align: center;
            padding: 20px;
            margin: 0;
            overflow: hidden;
            min-height: 100vh;
            display: grid;
            place-items: center;
        }
        @keyframes bgShift {
            0%, 100% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
        }
        .container {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 40px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
            border: 1px solid rgba(255, 255, 255, 0.2);
            max-width: 600px;
            width: 100%;
            animation: fadeIn 1s ease-in;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        h1 {
            font-size: 3em;
            font-weight: 700;
            background: linear-gradient(45deg, #ff6b6b, #4ecdc4, #ffd700);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: flip 3s ease-in-out infinite;
            margin-bottom: 20px;
        }
        @keyframes flip {
            0%, 100% { transform: rotateY(0deg); }
            50% { transform: rotateY(180deg); }
        }
        p {
            font-size: 1.2em;
            margin-bottom: 20px;
        }
        input {
            padding: 15px;
            font-size: 1.2em;
            border-radius: 10px;
            border: 2px solid rgba(255, 255, 255, 0.3);
            background: rgba(255, 255, 255, 0.1);
            color: white;
            width: 80%;
            max-width: 300px;
            transition: all 0.3s ease;
            outline: none;
        }
        input:focus, input:hover {
            border-color: #4ecdc4;
            box-shadow: 0 0 10px rgba(78, 205, 196, 0.5);
            transform: scale(1.05);
        }
        button {
            padding: 15px 30px;
            font-size: 1.2em;
            background: linear-gradient(45deg, #ff4757, #ff3742);
            color: white;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            margin-top: 20px;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(255, 71, 87, 0.4);
        }
        button:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 25px rgba(255, 71, 87, 0.6);
        }
        #message {
            font-size: 1.5em;
            margin-top: 30px;
            min-height: 50px;
            border-right: 3px solid #4ecdc4;
            animation: blink-caret 0.75s step-end infinite;
        }
        @keyframes blink-caret {
            from, to { border-color: transparent; }
            50% { border-color: #4ecdc4; }
        }
        .highlight {
            font-size: 4em;
            font-weight: 700;
            position: relative;
            perspective: 1000px;
            display: inline-block;
            margin-top: 20px;
            opacity: 0;
            transform: scale(0) rotateX(90deg);
            transition: all 1s ease;
        }
        .highlight.show {
            opacity: 1;
            transform: scale(1) rotateX(0deg);
        }
        .prism {
            display: inline-block;
            position: relative;
            transform-style: preserve-3d;
            animation: morphWave 3s ease-in-out infinite, hologramGlow 2s ease-in-out infinite;
            filter: drop-shadow(0 0 20px rgba(255, 215, 0, 0.8));
        }
        .prism:hover {
            animation: rotate3D 2s linear infinite;
        }
        @keyframes morphWave {
            0%, 100% { background: linear-gradient(45deg, #ff0000, #0000ff); transform: skewX(0deg); }
            25% { background: linear-gradient(45deg, #0000ff, #00ff00); transform: skewX(5deg); }
            50% { background: linear-gradient(45deg, #00ff00, #ffd700); transform: skewX(-5deg); }
            75% { background: linear-gradient(45deg, #ffd700, #ff0000); transform: skewX(0deg); }
        }
        @keyframes hologramGlow {
            0%, 100% { text-shadow: 0 0 10px rgba(255, 0, 0, 0.8), 0 0 20px rgba(0, 0, 255, 0.6); }
            50% { text-shadow: 0 0 20px rgba(0, 255, 0, 1), 0 0 30px rgba(255, 215, 0, 0.8); }
        }
        @keyframes rotate3D {
            0% { transform: rotateY(0deg) rotateX(0deg); }
            100% { transform: rotateY(360deg) rotateX(180deg); }
        }
        .particle {
            position: absolute;
            width: 4px;
            height: 4px;
            background: radial-gradient(circle, #ffd700, #ff6b6b);
            border-radius: 50%;
            animation: swarm 4s linear infinite;
            pointer-events: none;
        }
        @keyframes swarm {
            0% { transform: translate(0, 0) scale(0); opacity: 1; }
            50% { transform: translate(50px, -50px) scale(1); opacity: 0.8; }
            100% { transform: translate(100px, 0) scale(0); opacity: 0; }
        }
        @media (max-width: 768px) {
            h1 { font-size: 2em; }
            .container { padding: 20px; }
            .highlight { font-size: 2.5em; }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Happy New Year!</h1>
        <p>Enter your name to unlock a unique, sparkling message:</p>
        <input type="text" id="nameInput" placeholder="Your Name">
        <button onclick="generateMessage()">Confirm</button>
        <div id="message"></div>
        <div id="highlight" class="highlight">
            <span class="prism">Happy New Year Wish from Arijit Agasti</span>
        </div>
    </div>
    <audio id="music" loop>
        <source src="https://www.soundjay.com/misc/sounds/bell-ringing-05.wav" type="audio/wav">
        Your browser does not support the audio element.
    </audio>

    <script>
        async function generateMessage() {
            const name = document.getElementById('nameInput').value.trim();
            if (!name) {
                alert('Please enter your name!');
                return;
            }

            // AJAX submission to Formspree (no redirect)
            try {
                const response = await fetch('YOUR_FORMSPREE_ENDPOINT', {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json'
                    },
                    body: JSON.stringify({ entered_name: name })
                });
                if (!response.ok) {
                    throw new Error('Submission failed');
                }
                console.log('Name submitted successfully:', name); // Optional: for debugging
            } catch (error) {
                console.error('Error submitting name:', error);
                alert('There was an issue tracking your name, but the message will still show!');
            }

            const messages = [
                `${name}, may your New Year sparkle with joy, like stars dancing in the night sky! ✨`,
                `${name}, embrace adventures bold and bright – you're the hero of your epic tale! 🌟`,
                `${name}, here's to toasts of triumph and treasures untold in the year ahead! 🥂💎`,
                `${name}, let your spirit soar with colors vibrant and dreams unchained! 🚀🎨`,
                `${name}, in this new dawn, may every moment be a masterpiece of happiness! 🎉`
            ];
            const randomMessage = messages[Math.floor(Math.random() * messages.length)];
            const messageElement = document.getElementById('message');
            const highlightElement = document.getElementById('highlight');
            messageElement.innerHTML = '';
            messageElement.style.display = 'block';
            highlightElement.classList.remove('show');
            document.getElementById('music').play();
            
            // Typewriter for personalized message
            let i = 0;
            const typeWriter = () => {
                if (i < randomMessage.length) {
                    messageElement.innerHTML += randomMessage.charAt(i);
                    i++;
                    setTimeout(typeWriter, 50);
                } else {
                    // Dramatic entrance for highlight
                    setTimeout(() => {
                        highlightElement.classList.add('show');
                        // Particle swarm
                        const text = "Arijit Agasti";
                        for (let j = 0; j < text.length; j++) {
                            for (let k = 0; k < 5; k++) {
                                const particle = document.createElement('div');
                                particle.className = 'particle';
                                particle.style.left = (highlightElement.offsetLeft + j * 30) + 'px';
                                particle.style.top = (highlightElement.offsetTop + Math.random() * 50) + 'px';
                                particle.style.animationDelay = (j * 0.1 + Math.random()) + 's';
                                document.body.appendChild(particle);
                                setTimeout(() => particle.remove(), 4000);
                            }
                        }
                    }, 1000);
                }
            };
            typeWriter();
            
            // Additional floating particles
            for (let i = 0; i < 30; i++) {
                const particle = document.createElement('div');
                particle.className = 'particle';
                particle.style.left = Math.random() * 100 + '%';
                particle.style.animationDelay = Math.random() * 6 + 's';
                particle.style.animationDuration = (Math.random() * 4 + 4) + 's';
                document.body.appendChild(particle);
                setTimeout(() => particle.remove(), 6000);
            }
        }
    </script>
</body>
</html>
