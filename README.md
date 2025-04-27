# Happy-2months-game
I love u sm my love u r my world
<!DOCTYPE html><html>
<head>
  <title>Happy 2 Months, My Love!</title>
  <style>
    body {
      background-color: #d0f0f6;
      overflow: hidden;
      margin: 0;
      padding: 0;
    }
    #gameArea {
      width: 100vw;
      height: 100vh;
      position: relative;
      background: #aee1f9 url('https://i.imgur.com/6wsewVo.png') repeat;
    }
    #player {
      width: 48px;
      height: 48px;
      background: url('https://i.imgur.com/AX42MI3.png') no-repeat center/cover;
      position: absolute;
      bottom: 20px;
      left: 50%;
      transform: translateX(-50%);
    }
    .heart {
      width: 32px;
      height: 32px;
      background: url('https://i.imgur.com/ceMGRX5.png') no-repeat center/cover;
      position: absolute;
    }
    #message {
      position: absolute;
      top: 40%;
      left: 50%;
      transform: translate(-50%, -50%);
      background: #fff0f6;
      padding: 30px;
      border: 4px solid #ff7eb9;
      border-radius: 15px;
      box-shadow: 0 0 20px #ff91c1;
      display: none;
      font-family: 'Press Start 2P', cursive;
      text-align: center;
      font-size: 16px;
      color: #cc0066;
    }
  </style>
  <link href="https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap" rel="stylesheet">
</head>
<body><div id="gameArea">
  <div id="player"></div>
  <div id="message">Happy 2 Months! You picked all my pixel love! Love you so so much!</div>
</div><script>
  const player = document.getElementById('player');
  const gameArea = document.getElementById('gameArea');
  const message = document.getElementById('message');

  let playerX = window.innerWidth / 2 - 24;
  player.style.left = playerX + 'px';

  document.addEventListener('keydown', (e) => {
    if (e.key === 'ArrowLeft') {
      playerX -= 20;
      if (playerX < 0) playerX = 0;
    }
    if (e.key === 'ArrowRight') {
      playerX += 20;
      if (playerX > window.innerWidth - 48) playerX = window.innerWidth - 48;
    }
    player.style.left = playerX + 'px';
  });

  function createHeart() {
    const heart = document.createElement('div');
    heart.classList.add('heart');
    heart.style.left = Math.random() * (window.innerWidth - 32) + 'px';
    heart.style.top = '0px';
    gameArea.appendChild(heart);

    let fall = setInterval(() => {
      heart.style.top = (parseInt(heart.style.top) + 5) + 'px';
      if (parseInt(heart.style.top) > window.innerHeight - 70) {
        // check collision
        if (Math.abs(parseInt(heart.style.left) - playerX) < 40) {
          heart.remove();
          collected++;
          if (collected >= totalHearts) {
            message.style.display = 'block';
          }
        } else {
          heart.remove();
        }
        clearInterval(fall);
      }
    }, 20);
  }

  let collected = 0;
  let totalHearts = 5;
  for (let i = 0; i < totalHearts; i++) {
    setTimeout(createHeart, i * 1500);
  }
</script></body>
</html>
