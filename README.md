<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ERES EL AMORR DE MI VIDAMM</title>
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@700&display=swap" rel="stylesheet">
<style>
  html, body {
    margin: 0;
    height: 100%;
    background: black;
    overflow: hidden;
    font-family: 'Roboto', sans-serif;
  }

  .mensaje {
    position: absolute;
    color: #ff69b4;
    font-size: 1.5rem;
    text-align: center;
    line-height: 1.2;
    z-index: 10;
    text-shadow: 0 0 5px #ff69b4, 0 0 10px #ffd1dc;
  }

  .falling-heart {
    position: absolute;
    top: -5%;
    font-size: 40px;
    animation: fall linear infinite;
    opacity: 0.8;
  }

  .falling-adoro {
    position: absolute;
    top: -5%;
    font-size: 1rem;
    color: #ffd1dc;
    opacity: 0.6;
    animation: fallAdoro linear infinite;
  }

  @keyframes fall {
    to {
      transform: translateY(110vh) rotate(360deg);
      opacity: 0.3;
    }
  }

  @keyframes fallAdoro {
    to {
      transform: translateY(110vh) rotate(0deg);
      opacity: 0.1;
    }
  }

  .tap-heart {
    position: absolute;
    font-size: 40px;
    opacity: 1;
    animation: pop 1s ease-out forwards;
  }

  @keyframes pop {
    0% { transform: scale(1); opacity: 1; }
    100% { transform: scale(2); opacity: 0; }
  }
</style>
</head>
<body>

<div id="mensaje" class="mensaje">ERES EL AMORR<br>DE MI VIDAMM</div>

<script>
// Corazones cayendo: ❤️ 💖 🤍
const heartOptions = ["❤️", "💖", "🤍"];

function createFallingHeart() {
  const heart = document.createElement("div");
  heart.className = "falling-heart";
  heart.textContent = heartOptions[Math.floor(Math.random() * heartOptions.length)];
  heart.style.left = Math.random() * 100 + "vw";
  heart.style.color = heart.textContent === "🤍" ? "#fff" : "#ff69b4";
  heart.style.animationDuration = (4 + Math.random() * 4) + "s";
  document.body.appendChild(heart);
  setTimeout(() => heart.remove(), 8000);
}

setInterval(createFallingHeart, 300);

// TE ADORO cayendo como fondo
function createFallingAdoro() {
  const adoro = document.createElement("div");
  adoro.className = "falling-adoro";
  adoro.textContent = "TE ADORO";
  adoro.style.left = Math.random() * 100 + "vw";
  adoro.style.animationDuration = (5 + Math.random() * 5) + "s";
  adoro.style.fontSize = (0.8 + Math.random() * 0.5) + "rem";
  document.body.appendChild(adoro);
  setTimeout(() => adoro.remove(), 8000);
}

setInterval(createFallingAdoro, 500);

// Corazones al tocar
document.addEventListener("click", (e) => {
  const heart = document.createElement("div");
  heart.className = "tap-heart";
  heart.textContent = heartOptions[Math.floor(Math.random() * heartOptions.length)];
  heart.style.color = heart.textContent === "🤍" ? "#fff" : "#ff69b4";
  heart.style.left = e.clientX + "px";
  heart.style.top = e.clientY + "px";
  document.body.appendChild(heart);
  setTimeout(() => heart.remove(), 1000);
});

// Texto principal que rebota
const mensaje = document.getElementById("mensaje");
let x = (window.innerWidth - mensaje.offsetWidth) / 2;
let y = (window.innerHeight - mensaje.offsetHeight) / 2;
let dx = 2;
let dy = 2;

function animateMensaje() {
  const w = mensaje.offsetWidth;
  const h = mensaje.offsetHeight;

  x += dx;
  y += dy;

  if (x <= 0) { x = 0; dx = -dx; }
  else if (x + w >= window.innerWidth) { x = window.innerWidth - w; dx = -dx; }

  if (y <= 0) { y = 0; dy = -dy; }
  else if (y + h >= window.innerHeight) { y = window.innerHeight - h; dy = -dy; }

  mensaje.style.left = `${x}px`;
  mensaje.style.top = `${y}px`;

  requestAnimationFrame(animateMensaje);
}

animateMensaje();

</script>

</body>
</html>
