# gambar-hati
<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Nazwaa ❤️</title>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background: #08060d;
  overflow: hidden;
  font-family: Arial, sans-serif;
}

#heart {
  width: 100vw;
  height: 100vh;
  position: relative;
}

.name {
  position: absolute;
  color: #ff3978;
  font-size: 11px;
  font-weight: bold;
  white-space: nowrap;
  text-shadow: 0 0 8px #ff1744;
  animation: glow 1.5s infinite alternate;
}

@keyframes glow {
  from {
    opacity: 0.3;
    text-shadow: 0 0 3px #ff1744;
  }
  to {
    opacity: 1;
    text-shadow: 0 0 12px #ff1744,
                 0 0 20px #ff3978;
  }
}

#title {
  position: absolute;
  bottom: 7%;
  width: 100%;
  text-align: center;
  color: #ff8eaf;
  font-size: 20px;
  text-shadow: 0 0 15px red;
  letter-spacing: 3px;
}
</style>
</head>

<body>

<div id="heart"></div>
<div id="title">NAZWAA ❤️</div>

<script>
const nama = "Nazwaa";
const heart = document.getElementById("heart");

function tambahNama(x, y, ukuran = 11) {
  const teks = document.createElement("div");
  teks.className = "name";
  teks.textContent = nama;
  teks.style.left = x + "px";
  teks.style.top = y + "px";
  teks.style.fontSize = ukuran + "px";
  teks.style.transform = "translate(-50%, -50%)";
  teks.style.animationDelay = Math.random() * 2 + "s";

  heart.appendChild(teks);
}

function buatHati() {
  heart.innerHTML = "";

  const w = window.innerWidth;
  const h = window.innerHeight;
  const scale = Math.min(w / 36, h / 34);
  const cx = w / 2;
  const cy = h * 0.43;

  // Garis luar hati
  for (let t = 0; t < Math.PI * 2; t += 0.035) {
    const x = 16 * Math.pow(Math.sin(t), 3);
    const y = 13 * Math.cos(t)
      - 5 * Math.cos(2 * t)
      - 2 * Math.cos(3 * t)
      - Math.cos(4 * t);

    tambahNama(
      cx + x * scale,
      cy - y * scale
    );
  }

  // Mengisi bagian dalam hati
  let jumlah = 0;

  while (jumlah < 500) {
    const x = (Math.random() * 2 - 1) * 16;
    const y = (Math.random() * 2 - 1) * 14;

    const a = x / 16;
    const b = y / 13;

    const rumus =
      Math.pow(a * a + b * b - 1, 3)
      - a * a * Math.pow(b, 3);

    if (rumus <= 0) {
      tambahNama(
        cx + x * scale,
        cy - y * scale,
        8 + Math.random() * 4
      );
      jumlah++;
    }
  }
}

buatHati();

window.addEventListener("resize", buatHati);
</script>

</body>
</html>
