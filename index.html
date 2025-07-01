<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>XOBEPONG v1.1</title>
  <style>
    body {
      background: #181c24;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }
    canvas {
      border: 4px solid #fff;
      background: #23283b;
      box-shadow: 0 0 40px #00eaff44;
      border-radius: 18px;
      margin-bottom: 10px;
      touch-action: none;
    }
    .controls {
      display: flex;
      gap: 30px;
      margin-top: 10px;
      user-select: none;
    }
    .btn {
      width: 60px;
      height: 60px;
      border-radius: 50%;
      background: linear-gradient(145deg, #00eaff 60%, #23283b 100%);
      color: #fff;
      font-size: 2.2em;
      border: none;
      box-shadow: 0 2px 10px #00eaff55;
      display: flex;
      align-items: center;
      justify-content: center;
      font-family: inherit;
      outline: none;
      transition: background 0.2s;
      touch-action: manipulation;
    }
    .btn:active {
      background: #00eaff;
      color: #23283b;
    }
    @media (max-width: 900px) {
      canvas { width: 98vw !important; height: 60vw !important; max-width: 100vw; max-height: 70vw; }
    }
    @media (max-width: 600px) {
      canvas { width: 98vw !important; height: 60vw !important; }
      .btn { width: 50px; height: 50px; font-size: 1.5em; }
    }
  </style>
</head>
<body>
  <canvas id="gameCanvas" width="800" height="500"></canvas>
  <div class="controls">
    <button class="btn" id="upBtn">▲</button>
    <button class="btn" id="downBtn">▼</button>
  </div>
  <script>
    const canvas = document.getElementById('gameCanvas');
    const ctx = canvas.getContext('2d');

    // Responsive canvas
    function resizeCanvas() {
      if (window.innerWidth < 900) {
        canvas.width = window.innerWidth * 0.98;
        canvas.height = window.innerWidth * 0.6;
      } else {
        canvas.width = 800;
        canvas.height = 500;
      }
    }
    resizeCanvas();
    window.addEventListener('resize', resizeCanvas);

    // Game variables
    const paddleHeight = canvas.height * 0.2, paddleWidth = 18;
    let leftY = canvas.height / 2 - paddleHeight / 2, rightY = canvas.height / 2 - paddleHeight / 2;
    let leftSpeed = 0;
    let ballX = canvas.width / 2, ballY = canvas.height / 2, ballSize = 18;
    let ballSpeedX = 6, ballSpeedY = 4;
    let leftScore = 0, rightScore = 0;
    let aiSpeed = 4.2; // AI paddle speed

    // Draw functions
    function drawRect(x, y, w, h, color, shadow = false) {
      if (shadow) {
        ctx.save();
        ctx.shadowColor = "#00eaff";
        ctx.shadowBlur = 18;
      }
      ctx.fillStyle = color;
      ctx.fillRect(x, y, w, h);
      if (shadow) ctx.restore();
    }

    function drawBall(x, y, size, color) {
      ctx.save();
      ctx.shadowColor = "#fff";
      ctx.shadowBlur = 10;
      ctx.fillStyle = color;
      ctx.beginPath();
      ctx.arc(x + size/2, y + size/2, size/2, 0, Math.PI * 2);
      ctx.fill();
      ctx.restore();
    }

    function drawScore() {
      ctx.save();
      ctx.font = `bold ${Math.floor(canvas.height/7)}px 'Segoe UI', Arial, sans-serif`;
      ctx.textAlign = "center";
      ctx.textBaseline = "top";
      ctx.shadowColor = "#00eaff";
      ctx.shadowBlur = 18;
      ctx.fillStyle = "#fff";
      ctx.fillText(leftScore, canvas.width/4, 18);
      ctx.fillText(rightScore, canvas.width*3/4, 18);
      ctx.restore();
    }

    function drawNet() {
      ctx.save();
      ctx.strokeStyle = "#00eaff99";
      ctx.setLineDash([10, 18]);
      ctx.lineWidth = 4;
      ctx.beginPath();
      ctx.moveTo(canvas.width/2, 0);
      ctx.lineTo(canvas.width/2, canvas.height);
      ctx.stroke();
      ctx.setLineDash([]);
      ctx.restore();
    }

    // Main draw loop
    function draw() {
      // Clear
      ctx.clearRect(0, 0, canvas.width, canvas.height);

      // Net
      drawNet();

      // Paddles
      drawRect(10, leftY, paddleWidth, paddleHeight, '#fff', true);
      drawRect(canvas.width - paddleWidth - 10, rightY, paddleWidth, paddleHeight, '#00eaff', true);

      // Ball
      drawBall(ballX, ballY, ballSize, '#fff');

      // Score
      drawScore();

      // Move paddles
      leftY += leftSpeed;
      leftY = Math.max(0, Math.min(canvas.height - paddleHeight, leftY));

      // AI for right paddle
      let aiTarget = ballY - paddleHeight/2 + ballSize/2;
      if (ballSpeedX > 0) {
        // AI follows ball, but not perfect
        if (rightY + paddleHeight/2 < aiTarget - 10) rightY += aiSpeed;
        else if (rightY + paddleHeight/2 > aiTarget + 10) rightY -= aiSpeed;
      } else {
        // AI returns to center
        if (rightY + paddleHeight/2 < canvas.height/2 - 10) rightY += aiSpeed * 0.7;
        else if (rightY + paddleHeight/2 > canvas.height/2 + 10) rightY -= aiSpeed * 0.7;
      }
      rightY = Math.max(0, Math.min(canvas.height - paddleHeight, rightY));

      // Move ball
      ballX += ballSpeedX;
      ballY += ballSpeedY;

      // Bounce top/bottom
      if (ballY <= 0 || ballY + ballSize >= canvas.height) {
        ballSpeedY *= -1;
        ballY = Math.max(0, Math.min(canvas.height - ballSize, ballY));
      }

      // Paddle collision (left)
      if (
        ballX <= 10 + paddleWidth &&
        ballY + ballSize >= leftY &&
        ballY <= leftY + paddleHeight
      ) {
        ballSpeedX = Math.abs(ballSpeedX);
        // Sedikit random biar ga monoton
        ballSpeedY += (Math.random() - 0.5) * 2;
      }
      // Paddle collision (right/AI)
      if (
        ballX + ballSize >= canvas.width - paddleWidth - 10 &&
        ballY + ballSize >= rightY &&
        ballY <= rightY + paddleHeight
      ) {
        ballSpeedX = -Math.abs(ballSpeedX);
        ballSpeedY += (Math.random() - 0.5) * 2;
      }

      // Score
      if (ballX < 0) {
        rightScore++;
        resetBall(-1);
      }
      if (ballX > canvas.width) {
        leftScore++;
        resetBall(1);
      }

      requestAnimationFrame(draw);
    }

    function resetBall(dir = 1) {
      ballX = canvas.width / 2 - ballSize / 2;
      ballY = canvas.height / 2 - ballSize / 2;
      ballSpeedX = 6 * dir;
      ballSpeedY = (Math.random() - 0.5) * 8;
    }

    // Keyboard controls
    document.addEventListener('keydown', e => {
      if (e.key === 'w') leftSpeed = -8;
      if (e.key === 's') leftSpeed = 8;
    });
    document.addEventListener('keyup', e => {
      if (['w', 's'].includes(e.key)) leftSpeed = 0;
    });

    // Touch controls for mobile
    const upBtn = document.getElementById('upBtn');
    const downBtn = document.getElementById('downBtn');
    let touchInterval = null;

    function startMove(dir) {
      leftSpeed = dir;
      if (touchInterval) clearInterval(touchInterval);
      touchInterval = setInterval(() => { leftSpeed = dir; }, 50);
    }
    function stopMove() {
      leftSpeed = 0;
      if (touchInterval) clearInterval(touchInterval);
    }
    upBtn.addEventListener('touchstart', e => { e.preventDefault(); startMove(-8); });
    upBtn.addEventListener('touchend', e => { e.preventDefault(); stopMove(); });
    downBtn.addEventListener('touchstart', e => { e.preventDefault(); startMove(8); });
    downBtn.addEventListener('touchend', e => { e.preventDefault(); stopMove(); });

    // Also support mouse for buttons (for desktop)
    upBtn.addEventListener('mousedown', () => startMove(-8));
    upBtn.addEventListener('mouseup', stopMove);
    upBtn.addEventListener('mouseleave', stopMove);
    downBtn.addEventListener('mousedown', () => startMove(8));
    downBtn.addEventListener('mouseup', stopMove);
    downBtn.addEventListener('mouseleave', stopMove);

    draw();
  </script>
</body>
</html>
