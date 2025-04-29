# forila
<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Hujan Bunga Merah + Teks</title>
  <style>
    body {
      margin: 0;
      background: #fff0f0;
      overflow: hidden;
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      font-family: 'Segoe UI', sans-serif;
    }

    .text-overlay {
      position: absolute;
      z-index: 10;
      font-size: 48px;
      color: crimson;
      font-weight: bold;
      text-shadow: 2px 2px 4px rgba(0,0,0,0.2);
      animation: pulse 2s infinite;
    }

    @keyframes pulse {
      0%, 100% { transform: scale(1); }
      50% { transform: scale(1.05); }
    }

    .flower {
      position: absolute;
      width: 40px;
      height: 40px;
      top: -50px;
      animation: fall linear;
      pointer-events: none;
    }

    .petal {
      position: absolute;
      width: 24px;
      height: 24px;
      background: red;
      border-radius: 50% 50% 0 0;
      transform-origin: bottom center;
      opacity: 0.9;
    }

    .petal:nth-child(1) { transform: rotate(0deg) translateY(-15px); }
    .petal:nth-child(2) { transform: rotate(60deg) translateY(-15px); }
    .petal:nth-child(3) { transform: rotate(120deg) translateY(-15px); }
    .petal:nth-child(4) { transform: rotate(180deg) translateY(-15px); }
    .petal:nth-child(5) { transform: rotate(240deg) translateY(-15px); }
    .petal:nth-child(6) { transform: rotate(300deg) translateY(-15px); }

    .center {
      position: absolute;
      width: 12px;
      height: 12px;
      background: yellow;
      border-radius: 50%;
      top: 14px;
      left: 14px;
    }

    @keyframes fall {
      0% {
        transform: translateY(0) rotate(0deg);
        opacity: 1;
      }
      100% {
        transform: translateY(110vh) rotate(360deg);
        opacity: 0.2;
      }
    }
  </style>
</head>
<body>
  <div class="text-overlay">HAI ILA</div>

  <script>
    function createFallingFlower() {
      const flower = document.createElement("div");
      flower.className = "flower";
      flower.style.left = Math.random() * 100 + "vw";

      const duration = Math.random() * 5 + 5; // 5–10 detik
      flower.style.animationDuration = duration + "s";

      for (let i = 0; i < 6; i++) {
        const petal = document.createElement("div");
        petal.className = "petal";
        flower.appendChild(petal);
      }

      const center = document.createElement("div");
      center.className = "center";
      flower.appendChild(center);

      document.body.appendChild(flower);

      setTimeout(() => {
        flower.remove();
      }, duration * 1000);
    }

    setInterval(createFallingFlower, 300);
  </script>
</body>
</html>
