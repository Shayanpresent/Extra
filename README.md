<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>👻 & 💀 Best Friends Forever</title>
  <style>
    :root {
      --primary-color: #6a11cb;
      --secondary-color: #2575fc;
      --accent: white;
    }

    body {
      margin: 0;
      padding: 0;
      background: linear-gradient(to right, var(--primary-color), var(--secondary-color));
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      overflow-x: hidden;
      animation: fadeIn 1.5s ease-in;
      color: var(--accent);
    }

    @keyframes fadeIn {
      from { opacity: 0; }
      to { opacity: 1; }
    }

    .container {
      text-align: center;
      padding: 20px;
      max-width: 100%;
      box-sizing: border-box;
    }

    h1 {
      font-size: 8vw;
      text-shadow: 2px 2px 4px #000;
      margin-bottom: 10px;
    }

    h2 {
      font-size: 5vw;
      text-shadow: 1px 1px 3px #000;
      margin-bottom: 20px;
    }

    .heart {
      position: fixed;
      width: 20px;
      height: 20px;
      background: red;
      transform: rotate(-45deg);
      animation: floatHeart 5s linear infinite;
      z-index: 0;
    }

    .heart::before, .heart::after {
      content: '';
      position: absolute;
      width: 20px;
      height: 20px;
      background: red;
      border-radius: 50%;
    }

    .heart::before {
      top: -10px;
      left: 0;
    }

    .heart::after {
      left: 10px;
      top: 0;
    }

    @keyframes floatHeart {
      0% {
        bottom: -50px;
        left: calc(100% * var(--random));
        opacity: 1;
      }
      100% {
        bottom: 100%;
        left: calc(100% * var(--random) + 50px);
        opacity: 0;
      }
    }

    button {
      background: #00e5ff;
      color: #000;
      border: none;
      padding: 12px 24px;
      font-size: 4vw;
      border-radius: 30px;
      margin: 10px;
      cursor: pointer;
      box-shadow: 2px 2px 10px #000;
      transition: transform 0.2s;
      max-width: 90%;
    }

    button:hover {
      transform: scale(1.05);
    }

    .round-section {
      background: rgba(255, 255, 255, 0.9);
      margin: 10px auto;
      border-radius: 20px;
      padding: 20px;
      width: 90%;
      max-width: 600px;
      color: #222;
    }

    .quote {
      font-style: italic;
      color: #6a11cb;
      font-size: 4vw;
    }

    @media (min-width: 768px) {
      h1 { font-size: 3em; }
      h2 { font-size: 2em; }
      button { font-size: 1.2em; }
      .quote { font-size: 1.1em; }
    }
  </style>
</head>
<body>
  <audio autoplay loop>
    <source src="https://dl.sndup.net/jr35/palpal.mp3" type="audio/mpeg">
  </audio>

  <div class="container">
    <h1>💀 (Churail) & 👻 (Bhoot)</h1>
    <h2>🌟 Best Friend Journey Begins 🌟</h2>
    <div id="game-area"></div>
    <button onclick="nextRound()">Start</button>
  </div>

  <script>
    const hearts = Array.from({length: 40}).map(() => {
      const h = document.createElement('div');
      h.className = 'heart';
      h.style.setProperty('--random', Math.random());
      document.body.appendChild(h);
      return h;
    });

    const rounds = [
      { question: "Who is my best Churail friend?", options: ["Churail 💀", "Someone else"], answer: "Churail 💀", message: "Correct! You're my ghost buddy forever! 👻" },
      { question: "What makes Bhoot happy?", options: ["Food", "Churail's pranks"], answer: "Food", message: "Haha yes! Pranks for life! 🤭" },
      { question: "Our best friend adventure spot?", options: ["Mars", "Haunted Mansion"], answer: "Both", message: "Let’s go scare aliens together! 🚀" },
      { question: "Nickname I gave you?", options: ["Moti", "Churail 💀", "Friendzilla"], answer: "Churail 💀", message: "Legendary nickname! Only for the OG!" },
      { question: "Final Round: How strong is our bond?", options: ["Forever 💜", "Just okay"], answer: "Forever 💜", message: "Best friends till ghosts do us part! 👻" },
      { question: "Who screams louder during a horror movie?", options: ["Bhoot 👻", "Churail 💀"], answer: "Churail 💀", message: "Haha caught ya! Churail screams first, Bhoot hides later 😂" },
      { question: "Midnight snack choice?", options: ["Ice cream 🍦", "Brains 🧠", "Churails' cookies 🍪"], answer: "Churails' cookies 🍪", message: "Delicious and spooky! Midnight snack sorted! 🌙" },
      { question: "What’s our secret handshake?", options: ["BOO-5", "Scare Shake", "Churail Clap"], answer: "Scare Shake", message: "👋👻 Perfect ghostly greeting!" },
      { question: "What do we do on full moons?", options: ["Dance like ghosts 💃", "Scare people 😱", "Sleep 💤"], answer: "Dance like ghosts 💃", message: "Spooky moves unlocked! 💀🕺" },
      { question: "Spooky team name?", options: ["Ghostbusters", "BhootnChurail", "The Haunters"], answer: "BhootnChurail", message: "Legendary name for a legendary duo! 🔥" },
      { question: "Best horror movie to watch?", options: ["Conjuring", "Bhoot Returns", "Our life 😅"], answer: "Our life 😅", message: "Real-life horror comedy – starring us! 😆" },
      { question: "Spooky slogan?", options: ["Stay weird 💀", "Forever spooky 👻", "Till death do us prank 😈"], answer: "Till death do us prank 😈", message: "Perfect ending to a ghostly friendship! 👻💜" }
    ];

    let current = 0;

    function nextRound() {
      const r = rounds[current];
      if (!r) {
        document.getElementById("game-area").innerHTML = `
          <div class='round-section'>
            <h2>🎉 Special Message 🎉</h2>
            <p class='quote'>Churail, you're not just a friend. You're my partner in weirdness, my mischief manager, and my forever ghost buddy. 👻</p>
            <p>Stay spooky forever — Bhoot 👻</p>
            <button onclick="alert('BOO! You got a ghost hug 🥺')">Ghost Hug 🤗</button>
          </div>
        `;
        return;
      }
      let html = `<div class='round-section'><h2>${r.question}</h2>`;
      r.options.forEach(opt => {
        html += `<button onclick='choose("${opt}")'>${opt}</button>`;
      });
      html += `</div>`;
      document.getElementById("game-area").innerHTML = html;
    }

    function choose(opt) {
      const r = rounds[current];
      if (opt === r.answer || r.answer === "Both") {
        alert(r.message);
        current++;
        nextRound();
      } else {
        alert("Try again ghosty! 😈");
      }
    }

    setInterval(() => {
      hearts.forEach(h => h.style.setProperty('--random', Math.random()));
    }, 5000);
  </script>
</body>
</html>
