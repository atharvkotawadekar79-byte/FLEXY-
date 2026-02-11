# FLEXY-
If app will be good the shere with your friends
<!DOCTYPE html>
<html>
<head>
  <title>Chicken Runner</title>
  <style>
    body {
      text-align: center;
      font-family: Arial, sans-serif;
    }

    #game {
      width: 600px;
      height: 200px;
      border: 2px solid black;
      margin: 20px auto;
      position: relative;
      overflow: hidden;
      background: #f7f7f7;
    }

    #chicken {
      position: absolute;
      bottom: 0;
      left: 50px;
      font-size: 40px;
    }

    #obstacle {
      position: absolute;
      bottom: 0;
      right: -40px;
      font-size: 35px;
      animation: move 2s linear infinite;
    }

    @keyframes move {
      0% { right: -40px; }
      100% { right: 640px; }
    }

    .jump {
      animation: jump 0.5s linear;
    }

    @keyframes jump {
      0%   { bottom: 0; }
      50%  { bottom: 90px; }
      100% { bottom: 0; }
    }
  </style>
</head>
<body>

  <h2>🐔 Chicken Runner</h2>
  <p>Press Space to Jump</p>

  <div id="game">
    <div id="chicken">🐔</div>
    <div id="obstacle">🌵</div>
  </div>

  <script>
    const chicken = document.getElementById("chicken");
    const obstacle = document.getElementById("obstacle");

    document.addEventListener("keydown", function (event) {
      if (event.code === "Space") {
        if (!chicken.classList.contains("jump")) {
          chicken.classList.add("jump");
          setTimeout(() => {
            chicken.classList.remove("jump");
          }, 500);
        }
      }
    });

    setInterval(function () {
      const chickenBottom = parseInt(
        window.getComputedStyle(chicken).getPropertyValue("bottom")
      );
      const obstacleRight = parseInt(
        window.getComputedStyle(obstacle).getPropertyValue("right")
      );

      if (obstacleRight > 500 && obstacleRight < 550 && chickenBottom < 40) {
        alert("Game Over! 🐔💥");
        obstacle.style.animation = "none";
        obstacle.style.display = "none";
      }
    }, 10);
  </script>
</body>
</html>
