# Happy-Birthday-Huzaif
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Happy Birthday Genius!</title>
  <style>
    body {
      margin: 0;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: linear-gradient(to right, #fceabb, #f8b500);
      color: #333;
      text-align: center;
      padding: 2rem;
    }

    h1 {
      font-size: 3rem;
      margin-bottom: 0.5rem;
    }

    #message {
      font-size: 1.2rem;
      max-width: 700px;
      margin: 1rem auto;
      background: #fff8e1;
      padding: 1.5rem;
      border-radius: 20px;
      box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
    }

    #cake {
      width: 80%;
      max-width: 500px;
      border-radius: 20px;
      margin: 2rem auto;
      box-shadow: 0 8px 20px rgba(0,0,0,0.2);
    }

    #countdown {
      font-size: 1.5rem;
      margin-top: 2rem;
      background: #ffffffcc;
      display: inline-block;
      padding: 1rem 2rem;
      border-radius: 10px;
      font-weight: bold;
    }

    canvas {
      position: fixed;
      top: 0;
      left: 0;
      pointer-events: none;
      z-index: 999;
    }
  </style>
</head>
<body>
  <h1>Happy Birthday, Genius!</h1>
  <div id="message">
    happy birthday huzaif, i hope you achieve all that you dream of and aim of. I hope you make all your loved ones feel proud of you and most importantly, I hope you feel satisfied with yourself. even though you hate your birthdays, doesn't change the fact that a wonderful human was born 22 years ago today. enjoy your day tesoro, mwah!
  </div>
  <img id="cake" src="cake.jpg" alt="Birthday Cake" />
  <div id="countdown"></div>

  <audio autoplay loop>
    <source src="https://youtu.be/6cucosmPj-A?si=84NjRvJODTNzrya2" type="audio/ogg">
  
  </audio>

  <canvas id="confetti-canvas"></canvas>

  <script>
    // Countdown Logic
    const countdownElement = document.getElementById("countdown");
    const birthday = new Date("May 8, 2025 00:00:00").getTime();
    const x = setInterval(() => {
      const now = new Date().getTime();
      const distance = birthday - now;

      const days = Math.floor(distance / (1000 * 60 * 60 * 24));
      const hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
      const minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
      const seconds = Math.floor((distance % (1000 * 60)) / 1000);

      countdownElement.innerHTML = `Countdown: ${days}d ${hours}h ${minutes}m ${seconds}s`;

      if (distance < 0) {
        clearInterval(x);
        countdownElement.innerHTML = "Happy Birthday!!!";
      }
    }, 1000);

    // Confetti Animation
    const canvas = document.getElementById("confetti-canvas");
    const ctx = canvas.getContext("2d");
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;

    let confetti = Array.from({length: 200}, () => {
      return {
        x: Math.random() * canvas.width,
        y: Math.random() * canvas.height,
        r: Math.random() * 6 + 4,
        d: Math.random() * 20 + 10,
        color: `hsl(${Math.random() * 360}, 100%, 70%)`,
        tilt: Math.floor(Math.random() * 10) - 10
      };
    });

    function drawConfetti() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      confetti.forEach(c => {
        ctx.beginPath();
        ctx.lineWidth = c.r / 2;
        ctx.strokeStyle = c.color;
        ctx.moveTo(c.x + c.tilt + c.r / 4, c.y);
        ctx.lineTo(c.x + c.tilt, c.y + c.tilt + c.d / 4);
        ctx.stroke();
      });
      updateConfetti();
    }

    function updateConfetti() {
      confetti.forEach(c => {
        c.y += Math.cos(c.d) + 1;
        c.x += Math.sin(c.d);
        if (c.y > canvas.height) {
          c.x = Math.random() * canvas.width;
          c.y = -20;
        }
      });
    }

    (function animate() {
      drawConfetti();
      requestAnimationFrame(animate);
    })();
  </script>
</body>
</html>
![image](https://github.com/user-attachments/assets/b15537bb-f9a4-4867-a32d-5a34da8df158)
