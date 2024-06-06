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
            animation: merge 2s forwards;
            text-shadow: 2px 2px 2px #333, 4px 4px 4px #222, 6px 6px 6px #111;
        }
        @keyframes merge {
            0% { letter-spacing: 1em; }
            100% { letter-spacing: normal; }
        }
        #logo {
            margin-top: 20px;
            font-size: 100px;
            color: #FFD700;
        }
        #description {
            margin-top: 20px;
            font-size: 20px;
            padding: 0 20px;
        }
        #matrix {
            position: absolute;
            width: 100%;
            height: 100%;
            z-index: -1;
        }
    </style>
</head>
<body>

<canvas id="matrix"></canvas>

<div id="titan">T I T A N</div>
<div id="logo">T</div>
<div id="description">Titan is a multi-purpose Discord bot for all your Politics and War needs. From applications to tickets to general information, Titan is here to make your life easy!</div>

<script>
    const canvas = document.getElementById('matrix');
    const ctx = canvas.getContext('2d');
    
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
    
    const letters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789";
    const fontSize = 16;
    const columns = canvas.width / fontSize;
    
    const drops = [];
    for(let x = 0; x < columns; x++) {
        drops[x] = 1;
    }
    
    function draw() {
        ctx.fillStyle = "rgba(0, 0, 0, 0.05)";
        ctx.fillRect(0, 0, canvas.width, canvas.height);
        
        ctx.fillStyle = "#0F0";
        ctx.font = fontSize + "px monospace";
        
        for(let i = 0; i < drops.length; i++) {
            const text = letters[Math.floor(Math.random() * letters.length)];
            ctx.fillText(text, i * fontSize, drops[i] * fontSize);
            
            if(drops[i] * fontSize > canvas.height && Math.random() > 0.975) {
                drops[i] = 0;
            }
            drops[i]++;
        }
    }
    
    setInterval(draw, 33);
</script>

</body>
</html>
