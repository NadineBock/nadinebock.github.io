<!DOCTYPE html>
<html lang="de">
<head>
<meta charset="UTF-8" />
<title>Mein Snake</title>
<style>
  body {
    margin: 0;
    background: #3c6e47; /* Wald-Grün */
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    user-select: none;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    color: white;
    overflow: hidden;
  }
  #gameCanvas {
    background: #a3d9a5; /* heller Waldboden */
    border: 3px solid #2b5033;
    border-radius: 10px;
    box-shadow: 0 0 15px #2b5033;
    display: block;
  }
  #scoreboard {
    position: absolute;
    top: 15px;
    left: 15px;
    font-size: 18px;
    font-weight: bold;
    text-shadow: 1px 1px 2px black;
  }
  #highscoreboard {
    position: absolute;
    top: 15px;
    right: 15px;
    font-size: 16px;
    font-weight: normal;
    color: #f0f0b0;
    text-shadow: 1px 1px 2px black;
    max-width: 150px;
  }
  button {
    position: absolute;
    bottom: 20px;
    left: 50%;
    transform: translateX(-50%);
    font-size: 16px;
    padding: 10px 20px;
    border-radius: 8px;
    border: none;
    background-color: #547d4c;
    color: white;
    cursor: pointer;
    box-shadow: 0 0 5px #2b5033;
  }
  button:hover {
    background-color: #466b3c;
  }
</style>
</head>
<body>

<div id="scoreboard">Punkte: 0</div>
<div id="highscoreboard">
  <div><strong>Beste Werte:</strong></div>
  <ol id="highscores"></ol>
</div>
<canvas id="gameCanvas" width="600" height="400"></canvas>
<button id="restartBtn" style="display:none;">Neu starten</button>

<script>
  const canvas = document.getElementById('gameCanvas');
  const ctx = canvas.getContext('2d');
  const scoreboard = document.getElementById('scoreboard');
  const highscoresElem = document.getElementById('highscores');
  const restartBtn = document.getElementById('restartBtn');

  const gridSize = 20;
  const cols = canvas.width / gridSize;
  const rows = canvas.height / gridSize;

  // Schlange als Array von Segmenten (jeder mit x,y im Grid)
  let snake = [{x: 10, y: 10}];
  let direction = {x: 1, y: 0}; // Start: nach rechts
  let nextDirection = direction;

  // Pilzposition
  let mushroom = spawnMushroom();

  // Punkte
  let score = 0;
  let gameOver = false;

  // Bestenliste aus localStorage laden
  let highscores = JSON.parse(localStorage.getItem('mushroomSnakeHighscores')) || [];

  function spawnMushroom() {
    let x, y;
    do {
      x = Math.floor(Math.random() * cols);
      y = Math.floor(Math.random() * rows);
      // Vermeide Pilz auf der Schlange
    } while (snake.some(seg => seg.x === x && seg.y === y));
    return {x, y};
  }

  // Zeichnet die Schlange
  function drawSnake() {
    ctx.fillStyle = '#ff69b4'; // Pink
    snake.forEach((seg, index) => {
      ctx.fillRect(seg.x * gridSize, seg.y * gridSize, gridSize, gridSize);
      // Kopf als hellere Farbe (optional)
      if(index === 0) {
        ctx.fillStyle = '#ff85c1';
        ctx.fillRect(seg.x * gridSize, seg.y * gridSize, gridSize, gridSize);
        ctx.fillStyle = '#ff69b4'; 
      }
    });
  }

  // Zeichnet Pilz
  function drawMushroom() {
    const centerX = mushroom.x * gridSize + gridSize/2;
    const centerY = mushroom.y * gridSize + gridSize/2;
    ctx.fillStyle = 'maroon';
    ctx.beginPath();
    ctx.arc(centerX, centerY, gridSize / 2.5, 0, Math.PI * 2);
    ctx.fill();
    // weißes Hütchen
    ctx.fillStyle = 'white';
    ctx.beginPath();
    ctx.arc(centerX, centerY - gridSize/6, gridSize / 3, 0, Math.PI * 2);
    ctx.fill();
  }

  // Aktualisiert Position und Status
  function update() {
    // Verhindere Rückwärtsbewegung
    if ((nextDirection.x !== -direction.x || nextDirection.y !== -direction.y) 
        && (nextDirection.x !== direction.x || nextDirection.y !== direction.y)) {
      direction = nextDirection;
    }

    // Neue Kopfposition berechnen
    let newHead = {x: snake[0].x + direction.x, y: snake[0].y + direction.y};

    // Kollision mit Wand = Game Over
    if(newHead.x < 0 || newHead.x >= cols || newHead.y < 0 || newHead.y >= rows) {
      endGame();
      return;
    }

    // Kollision mit eigenem Körper = Game Over
    if(snake.some(seg => seg.x === newHead.x && seg.y === newHead.y)) {
      endGame();
      return;
    }

    // Kopf hinzufügen
    snake.unshift(newHead);

    // Pilz essen prüfen
    if(newHead.x === mushroom.x && newHead.y === mushroom.y) {
      score++;
      scoreboard.textContent = 'Punkte: ' + score;
      mushroom = spawnMushroom();
    } else {
      // Schwanz entfernen (bewege Schlange)
      snake.pop();
    }
  }

  function draw() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    drawMushroom();
    drawSnake();
  }

  function gameLoop() {
    if(gameOver) return;
    update();
    draw();
  }

  // Steuerung mit Pfeiltasten/WASD
  window.addEventListener('keydown', e => {
    switch(e.key) {
      case 'ArrowUp': case 'w': nextDirection = {x: 0, y: -1}; break;
      case 'ArrowDown': case 's': nextDirection = {x: 0, y: 1}; break;
      case 'ArrowLeft': case 'a': nextDirection = {x: -1, y: 0}; break;
      case 'ArrowRight': case 'd': nextDirection = {x: 1, y: 0}; break;
    }
  });

  // Spiel beenden und Bestenliste aktualisieren
  function endGame() {
    gameOver = true;
    updateHighscores();
    alert('Spiel vorbei! Punkte: ' + score);
    restartBtn.style.display = 'block';
  }

  function updateHighscores() {
    highscores.push(score);
    highscores.sort((a,b)=>b-a);
    if(highscores.length > 5) highscores.length = 5; // max 5 Einträge
    localStorage.setItem('mushroomSnakeHighscores', JSON.stringify(highscores));
    renderHighscores();
  }

  function renderHighscores() {
    highscoresElem.innerHTML = '';
    highscores.forEach((sc, i) => {
      const li = document.createElement('li');
      li.textContent = (i+1) + '.  ' + sc + ' Punkte';
      highscoresElem.appendChild(li);
    });
  }

  restartBtn.addEventListener('click', () => {
    score = 0;
    scoreboard.textContent = 'Punkte: 0';
    snake = [{x: 10, y: 10}];
    direction = {x: 1, y: 0};
    nextDirection = direction;
    mushroom = spawnMushroom();
    gameOver = false;
    restartBtn.style.display = 'none';
  });

  // Zeichne initiale Bestenliste
  renderHighscores();

  // Starte das Spiel mit fester Framerate (z.B. 8 mal pro Sekunde)
  setInterval(() => {
    if(!gameOver) gameLoop();
  }, 125);

</script>

</body>
</html>

