```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Only You</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <style>
    body {
      margin: 0;
      min-height: 100vh;
      background: radial-gradient(circle at top, #1b0f14, #050203);
      font-family: "Playfair Display", Georgia, serif;
      color: #e6dcdc;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 30px;
    }

    .letter {
      max-width: 780px;
      background: rgba(15, 6, 9, 0.92);
      padding: 60px 45px;
      border-radius: 14px;
      box-shadow: 0 30px 60px rgba(0,0,0,0.7);
      border: 1px solid rgba(255,255,255,0.05);
    }

    h1 {
      text-align: center;
      font-size: 2.7rem;
      margin-bottom: 35px;
      color: #c94b4b;
      letter-spacing: 1px;
    }

    p {
      font-size: 1.15rem;
      line-height: 1.9;
      margin-bottom: 24px;
      text-align: justify;
      opacity: 0;
    }

    .signature {
      margin-top: 50px;
      font-size: 1.25rem;
      color: #d8bebe;
      opacity: 0;
    }

    .signature span {
      display: block;
      margin-top: 10px;
      font-style: italic;
      color: #c94b4b;
    }

    .hint {
      text-align: center;
      margin-top: 35px;
      font-size: 0.8rem;
      color: #777;
    }
  </style>
</head>
<body>

  <div class="letter">
    <h1> Appy ,</h1>

    <p class="line">
      This isn’t just a letter. It’s the place where I keep the things I
      don’t say out loud—the parts of me that only answer to you.
    </p>

    <p class="line">
      You live under my skin, in my pauses, in the way my thoughts slow
      down when your name appears.
    </p>

    <p class="line">
      Loving you is not gentle. It’s deep. It pulls. It stays.
      Even when everything else falls quiet.
    </p>

    <p class="line">
      If the world ever feels cold or heavy, remember this:
      you are wanted here. Completely. Relentlessly.
    </p>

    <div class="signature">
      Always yours,
      <span> Aaruu </span>
    </div>

    <div class="hint">
      (tap anywhere to begin)
    </div>
  </div>

  <!-- Background Music -->
  <audio id="bgMusic" loop>
    <!-- Replace this with your own soft romantic track -->
    <source src="https://cdn.pixabay.com/audio/2022/03/15/audio_2c44d5d98b.mp3" type="audio/mpeg">
  </audio>

  <script>
    const lines = document.querySelectorAll(".line");
    const signature = document.querySelector(".signature");
    const music = document.getElementById("bgMusic");

    let started = false;

    function typeLine(element, text, speed = 35) {
      return new Promise(resolve => {
        element.textContent = "";
        element.style.opacity = 1;
        let i = 0;
        const interval = setInterval(() => {
          element.textContent += text.charAt(i);
          i++;
          if (i >= text.length) {
            clearInterval(interval);
            setTimeout(resolve, 400);
          }
        }, speed);
      });
    }

    async function startLetter() {
      if (started) return;
      started = true;

      music.volume = 0.4;
      music.play();

      for (const line of lines) {
        const text = line.textContent;
        await typeLine(line, text);
      }

      signature.style.opacity = 1;
    }

    document.body.addEventListener("click", startLetter);
    document.body.addEventListener("touchstart", startLetter);
  </script>

</body>
</html>

```
