<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Kushagra Soni</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;600&display=swap" rel="stylesheet">
  <style>
    :root {
      --bg: #fffaf3;
      --accent: #d9a65f;
      --text: #1e1e1e;
    }

    body {
      margin: 0;
      font-family: 'Poppins', sans-serif;
      background: var(--bg);
      overflow: hidden;
      color: var(--text);
    }

    .container {
      position: relative;
      height: 100vh;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      text-align: center;
      z-index: 2;
      padding: 20px;
    }

    h1 {
      font-size: 3rem;
      margin: 0.5em 0;
      color: var(--accent);
      animation: fadeIn 1s ease-out;
    }

    img {
      width: 150px;
      height: 150px;
      object-fit: cover;
      border-radius: 50%;
      border: 4px solid var(--accent);
      animation: fadeIn 1.5s ease-out;
    }

    .btn {
      margin-top: 1.5em;
      padding: 12px 30px;
      border: none;
      border-radius: 30px;
      background-color: var(--accent);
      color: white;
      font-size: 1rem;
      text-decoration: none;
      cursor: pointer;
      transition: 0.3s ease;
      animation: fadeIn 2s ease-out;
    }

    .btn:hover {
      background-color: #c19052;
    }

    #background-canvas {
      position: absolute;
      top: 0;
      left: 0;
      z-index: 0;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }

    @media (max-width: 600px) {
      h1 { font-size: 2rem; }
      .btn { padding: 10px 20px; font-size: 0.9rem; }
    }
  </style>
</head>
<body>
  <canvas id="background-canvas"></canvas>

  <div class="container">
    <img src="kushagra Cv photo.jpg" alt="Kushagra Soni" />
    <h1>Kushagra Soni</h1>
    <a href="about.html" class="btn">Go to My Info</a>
  </div>

  <script>
    const canvas = document.getElementById('background-canvas');
    const ctx = canvas.getContext('2d');
    let w, h;
    const particles = [];

    function resize() {
      w = canvas.width = window.innerWidth;
      h = canvas.height = window.innerHeight;
    }

    window.addEventListener('resize', resize);
    resize();

    for (let i = 0; i < 60; i++) {
      particles.push({
        x: Math.random() * w,
        y: Math.random() * h,
        r: Math.random() * 3 + 1,
        dx: Math.random() * 0.5,
        dy: Math.random() * 0.5,
      });
    }

    function draw() {
      ctx.clearRect(0, 0, w, h);
      ctx.fillStyle = '#f3e7cd';
      for (let p of particles) {
        ctx.beginPath();
        ctx.arc(p.x, p.y, p.r, 0, Math.PI * 2);
        ctx.fill();

        p.x += p.dx;
        p.y += p.dy;

        if (p.x > w) p.x = 0;
        if (p.y > h) p.y = 0;
      }
      requestAnimationFrame(draw);
    }

    draw();
  </script>
</body>
</html>
