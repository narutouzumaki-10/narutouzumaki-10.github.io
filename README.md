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
        }
        h1, h2 {
            color: #FFD700;
        }
        a {
            color: #1E90FF;
        }
        ul {
            list-style-type: none;
            padding: 0;
        }
        ul li {
            margin: 5px 0;
        }
        code {
            background-color: #333;
            color: #FFD700;
            padding: 2px 4px;
            border-radius: 4px;
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

<h1>Welcome to Titan Bot</h1>

<h2>Introduction</h2>

<p>Welcome to the home page of Titan Bot! Titan Bot is designed to assist you with a variety of tasks, offering seamless integration and powerful features to enhance your productivity.</p>

<h2>Table of Contents</h2>
<ul>
    <li><a href="#features">Features</a></li>
    <li><a href="#getting-started">Getting Started</a></li>
    <li><a href="#documentation">Documentation</a></li>
    <li><a href="#support">Support</a></li>
    <li><a href="#contact">Contact</a></li>
</ul>

<h2 id="features">Features</h2>
<ul>
    <li><strong>Automation</strong>: Automate repetitive tasks to save time.</li>
    <li><strong>Integration</strong>: Easily integrate with other tools and platforms.</li>
    <li><strong>Customizable</strong>: Tailor the bot to meet your specific needs.</li>
    <li><strong>User-Friendly</strong>: Simple and intuitive interface.</li>
</ul>

<h2 id="getting-started">Getting Started</h2>
<p>To get started with Titan Bot, follow these simple steps:</p>
<ol>
    <li><strong>Install the Bot</strong>: Download and install Titan Bot from the <a href="#">official website</a>.</li>
    <li><strong>Configure</strong>: Set up your preferences and integrations.</li>
    <li><strong>Use</strong>: Start using Titan Bot to automate tasks and improve productivity.</li>
</ol>

<h2 id="documentation">Documentation</h2>
<p>For detailed information on how to use Titan Bot, visit our <a href="#">Documentation</a>.</p>

<h2 id="support">Support</h2>
<p>If you need assistance, check out our <a href="#">Support Page</a> or contact our support team.</p>

<h2 id="contact">Contact</h2>
<p>Feel free to reach out to us at <a href="mailto:support@titanbot.com">support@titanbot.com</a> for any inquiries or feedback.</p>

<hr>

<p>Thank you for choosing Titan Bot! We hope it enhances your productivity and streamlines your workflow.</p>

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
