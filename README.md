<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Titan Bot Home Page</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            font-family: Arial, sans-serif;
            color: white;
            background: black;
            overflow: hidden;
            text-align: center;
        }
        #titan {
            font-size: 60px;
            margin-top: 20px;
            margin-bottom: 20px;
            text-shadow: 2px 2px #333, 4px 4px #222, 6px 6px #111;
            animation: merge 4s infinite;
        }
        @keyframes merge {
            0%, 100% { letter-spacing: 1em; }
            50% { letter-spacing: normal; }
        }
        #logo {
            margin-top: 20px;
            font-size: 100px;
            color: #FFD700;
            text-shadow: 2px 2px #333, 4px 4px #222, 6px 6px #111;
        }
        #description {
            margin-top: 20px;
            font-size: 20px;
            padding: 0 20px;
        }
        #matrix {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
        }
    </style>
</head>
<body>

<canvas id="matrix"></canvas>

<div id="titan">T I T A N</div>
<div id="description">Titan is a multi-purpose Discord bot for all your Politics and War needs. From applications to tickets to general information, Titan is here to make your life easy!</div>

<script>
    const canvas = document.getElementById('matrix');
    const ctx = canvas.getContext('2d');
    
    function resizeCanvas() {
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;
    }

    window.addEventListener('resize', resizeCanvas);
    resizeCanvas();
    
    const letters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789";
    const fontSize = 16;
    const columns = Math.floor(canvas.width / fontSize);
    
    const drops = Array(columns).fill(1);
    
    function draw() {
        ctx.fillStyle = "rgba(0, 0, 0, 0.05)";
        ctx.fillRect(0, 0, canvas.width, canvas.height);
        
        ctx.fillStyle = "#0F0";
        ctx.font = `${fontSize}px monospace`;
        
        drops.forEach((y, index) => {
            const text = letters[Math.floor(Math.random() * letters.length)];
            const x = index * fontSize;
            ctx.fillText(text, x, y * fontSize);
            
            if (y * fontSize > canvas.height && Math.random() > 0.975) {
                drops[index] = 0;
            }
            drops[index]++;
        });
    }
    
    setInterval(draw, 33);
</script>

</body>
</html>
