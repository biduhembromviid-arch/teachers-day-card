<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Happy Teacher's Day</title>
  <style>
    :root {
      --night: #17233f;
      --ground: #203455;
      --ink: #496a69;
      --gold: #f7d488;
      --coral: #e07b71;
      --paper: #f7e6c2;
      --mint: #9fd8d2;
    }

    * { box-sizing: border-box; }

    body {
      margin: 0;
      min-height: 100vh;
      overflow: hidden;
      display: grid;
      place-items: center;
      color: white;
      background: #111a30;
      font-family: Georgia, "Times New Roman", serif;
    }

    body.is-loading { overflow: hidden; }

    .intro {
      position: fixed;
      z-index: 20;
      inset: 0;
      display: grid;
      place-items: center;
      background: #111a30;
      text-align: center;
      animation: introExit 1.2s ease 2.4s forwards;
    }

    .intro-content {
      padding: 30px;
      animation: introText 1.4s ease both;
    }

    .intro-kicker {
      margin: 0 0 14px;
      color: var(--mint);
      font-size: 13px;
      letter-spacing: .24em;
    }

    .intro h2 {
      margin: 0;
      color: var(--gold);
      font-size: clamp(32px, 7vw, 72px);
      font-weight: normal;
    }

    .intro-line {
      width: 0;
      height: 2px;
      margin: 20px auto 0;
      background: #e7a76b;
      animation: introLine 1s ease .5s forwards;
    }

    .view-present {
      margin-top: 28px;
      padding: 12px 22px;
      border: 1px solid #e7a76b;
      border-radius: 999px;
      color: #17233f;
      background: var(--gold);
      cursor: pointer;
      font: 700 14px Georgia, "Times New Roman", serif;
      box-shadow: 0 5px 0 #b77d61;
      transition: transform .2s ease, background .2s ease, box-shadow .2s ease;
    }

    .view-present:hover,
    .view-present:focus-visible {
      background: #ffe7a6;
      outline: 2px solid var(--mint);
      outline-offset: 4px;
      transform: translateY(-2px);
      box-shadow: 0 7px 0 #b77d61;
    }

    .view-present:active {
      transform: translateY(2px);
      box-shadow: 0 3px 0 #b77d61;
    }

    .intro.dismissed {
      animation: introExit .8s ease forwards;
      pointer-events: none;
    }

    .card { animation: cardArrival 1.3s ease .15s both; }

    .card {
      position: relative;
      width: min(100vw, 1100px);
      height: min(100vh, 720px);
      min-height: 620px;
      overflow: hidden;
      isolation: isolate;
      background:
        radial-gradient(circle at 15% 20%, rgba(89, 139, 160, .22), transparent 24%),
        radial-gradient(circle at 85% 18%, rgba(220, 167, 107, .14), transparent 25%),
        linear-gradient(180deg, var(--night) 0 66%, var(--ground) 66% 100%);
    }

    .card::before,
    .card::after {
      content: "";
      position: absolute;
      z-index: -1;
      width: 45%;
      height: 55%;
      bottom: -28%;
      border-radius: 50%;
      background: rgba(58, 92, 132, .42);
    }

    .card::before { left: -14%; transform: rotate(-12deg); }
    .card::after { right: -14%; transform: rotate(12deg); }

    .stars {
      position: absolute;
      inset: 0 0 34%;
      background-image:
        radial-gradient(circle, #f8e7a6 0 1px, transparent 1.5px),
        radial-gradient(circle, rgba(255,255,255,.85) 0 1px, transparent 1.5px);
      background-position: 20px 30px, 70px 90px;
      background-size: 115px 90px, 170px 140px;
      opacity: .72;
    }

    header { text-align: center; position: relative; z-index: 3; padding-top: 38px; }
    .eyebrow { margin: 0 0 8px; color: var(--mint); font-size: clamp(11px, 1.4vw, 15px); letter-spacing: .22em; }
    h1 { margin: 0; color: var(--gold); font-size: clamp(30px, 4vw, 48px); letter-spacing: .03em; }
    .rule { width: 230px; height: 2px; margin: 17px auto 0; background: #e7a76b; }

    .stage { position: relative; width: min(90%, 850px); height: 455px; margin: 18px auto 0; }
    .board {
      position: absolute; left: 4%; top: 38px; width: 39%; height: 245px;
      border: 5px solid #e1b76b; border-radius: 12px; background: #315c52;
      box-shadow: 0 14px 0 rgba(12, 22, 41, .2);
      text-align: center; padding-top: 34px;
    }
    .board b { display: block; font-size: clamp(25px, 3.5vw, 38px); line-height: 1.35; }
    .board b:nth-child(1) { color: #fff2bd; }
    .board b:nth-child(2) { color: #bce7d9; }
    .board b:nth-child(3) { color: #f5c7a9; }
    .board::after { content: ""; position: absolute; left: 12%; right: 12%; bottom: 17px; height: 2px; background: #d4e5d3; }

    .teacher { position: absolute; left: 17%; top: 250px; width: 130px; height: 185px; }
    .head { position: absolute; left: 25px; top: 0; width: 80px; height: 80px; border: 2px solid #fff3dc; border-radius: 50%; background: linear-gradient(145deg, #f7c9a5, #e8a985); box-shadow: inset -5px -6px 0 rgba(190, 108, 105, .12); z-index: 2; }
    .hair { position: absolute; z-index: 1; left: 11px; top: -14px; width: 108px; height: 126px; border-radius: 52% 52% 42% 42%; background: linear-gradient(115deg, #4d2d39, #2d2030); }
    .hair::before { content: ""; position: absolute; left: 44px; top: -7px; width: 24px; height: 11px; border-radius: 50%; background: #e07b71; transform: rotate(-12deg); box-shadow: 8px 3px 0 -2px #f7d488; }
    .hair::after { content: ""; position: absolute; left: 22px; top: 7px; width: 62px; height: 18px; border-bottom: 4px solid #81505a; border-radius: 50%; transform: rotate(-8deg); }
    .eye { position: absolute; top: 37px; width: 8px; height: 6px; border-radius: 50% 50% 45% 45%; background: #2a2631; box-shadow: 0 -2px 0 #70434b; }
    .eye.left { left: 22px; } .eye.right { right: 22px; }
    .head::before { content: ""; position: absolute; left: -4px; top: 53px; width: 6px; height: 9px; border-radius: 50%; background: var(--gold); box-shadow: 75px 0 0 var(--gold); }
    .head::after { content: ""; position: absolute; left: 14px; top: 53px; width: 10px; height: 5px; border-radius: 50%; background: rgba(215, 117, 120, .4); box-shadow: 42px 0 0 rgba(215, 117, 120, .4); }
    .smile { position: absolute; left: 35px; top: 48px; width: 20px; height: 9px; border-bottom: 3px solid #bd5f6e; border-radius: 50%; }
    .body { position: absolute; left: 2px; top: 85px; width: 125px; height: 100px; clip-path: polygon(12% 0, 88% 0, 100% 100%, 0 100%); border: 2px solid #fff3dc; background: linear-gradient(135deg, #ef9184, var(--coral)); }
    .tie { position: absolute; z-index: 2; left: 49px; top: 88px; width: 31px; height: 20px; border-radius: 50%; background: var(--gold); box-shadow: 15px 7px 0 -5px #e7a76b; }
    .arm { position: absolute; z-index: 3; left: 102px; top: 107px; width: 90px; height: 5px; background: var(--gold); transform: rotate(-38deg); transform-origin: left; }
    .hand { position: absolute; left: 178px; top: 71px; width: 14px; height: 14px; border-radius: 50%; background: #efbd99; }

    .bubble {
      position: absolute; top: 0; left: 35%; width: 190px; padding: 17px 12px;
      border: 2px solid #e7a76b; border-radius: 20px; color: #b95f61;
      background: #fff5d6; text-align: center; transform: rotate(2deg);
      animation: float 4s ease-in-out infinite;
    }
    .bubble::after { content: ""; position: absolute; left: 20px; bottom: -20px; border: 12px solid transparent; border-top-color: #e7a76b; transform: rotate(25deg); }
    .bubble strong { display: block; font-size: 21px; }
    .bubble span { color: var(--ink); font-size: 15px; font-style: italic; }

    .message {
      position: absolute; right: 0; top: 18px; width: 47%; min-height: 205px;
      padding: 42px 34px 25px; border: 3px solid #e7a76b; border-radius: 24px;
      background: var(--paper); text-align: center; box-shadow: 0 15px 0 rgba(13, 23, 43, .18);
      animation: reveal .8s ease both;
    }
    .message h2 { margin: 0; color: #a14e5c; font-size: clamp(20px, 2.5vw, 29px); line-height: 1.25; }
    .message p { margin: 25px auto 15px; max-width: 330px; color: var(--ink); font-size: clamp(14px, 1.6vw, 18px); font-style: italic; line-height: 1.45; }
    .message small { color: #b77d61; font-family: Arial, sans-serif; }

    .book { position: absolute; right: 12%; bottom: 35px; width: 225px; height: 100px; filter: drop-shadow(0 10px 0 rgba(14, 24, 43, .2)); }
    .page { position: absolute; bottom: 10px; width: 112px; height: 70px; background: #fff4ca; border: 2px solid #d08a69; }
    .page.left { left: 0; transform: skewY(11deg); } .page.right { right: 0; transform: skewY(-11deg); }
    .spine { position: absolute; z-index: 2; left: 110px; bottom: 8px; width: 5px; height: 74px; background: #c36c68; }
    .book-label { position: absolute; z-index: 3; left: 74px; bottom: 38px; color: #365b5b; font-size: 13px; font-weight: bold; }

    .flower { position: absolute; width: 50px; height: 50px; bottom: 78px; animation: float 5s ease-in-out infinite; }
    .flower.one { right: 1%; } .flower.two { left: 56%; bottom: 34px; animation-delay: -2s; }
    .petal { position: absolute; left: 16px; top: 3px; width: 20px; height: 32px; border-radius: 50%; background: #ed9a88; transform-origin: 10px 22px; }
    .petal:nth-child(2) { transform: rotate(72deg); } .petal:nth-child(3) { transform: rotate(144deg); }
    .petal:nth-child(4) { transform: rotate(216deg); } .petal:nth-child(5) { transform: rotate(288deg); }
    .flower.two .petal { background: var(--mint); }
    .center { position: absolute; left: 19px; top: 18px; width: 14px; height: 14px; border-radius: 50%; background: var(--gold); }

    .bubbles { position: absolute; inset: 0; z-index: 5; pointer-events: none; }
    .orb { position: absolute; border: 2px solid #76c9c2; border-radius: 50%; opacity: .78; animation: rise linear infinite; }
    .orb:nth-child(3n) { border-color: #d8a56c; } .orb:nth-child(4n) { border-color: #9bbbe0; }
    footer { position: absolute; z-index: 4; left: 0; right: 0; bottom: 18px; color: var(--gold); text-align: center; font-size: clamp(13px, 1.7vw, 18px); font-weight: bold; animation: shimmer 2.5s ease-in-out infinite; }
    .creator { display: block; margin-top: 5px; color: rgba(255, 255, 255, .62); font: 11px Arial, sans-serif; letter-spacing: .04em; }

    @keyframes rise { from { transform: translateY(40px); opacity: 0; } 15% { opacity: .75; } to { transform: translateY(-760px); opacity: 0; } }
    @keyframes float { 0%, 100% { transform: translateY(0) rotate(2deg); } 50% { transform: translateY(-13px) rotate(-2deg); } }
    @keyframes shimmer { 0%, 100% { opacity: .7; } 50% { opacity: 1; color: #ffe7a6; } }
    @keyframes reveal { from { opacity: 0; transform: translateY(15px) scale(.98); } to { opacity: 1; transform: translateY(0) scale(1); } }
    @keyframes introText { from { opacity: 0; transform: translateY(18px); } to { opacity: 1; transform: translateY(0); } }
    @keyframes introLine { to { width: 210px; } }
    @keyframes introExit { to { opacity: 0; visibility: hidden; } }
    @keyframes cardArrival { from { opacity: 0; transform: scale(.97) translateY(16px); } to { opacity: 1; transform: scale(1) translateY(0); } }

    @media (prefers-reduced-motion: reduce) {
      *, *::before, *::after { animation-duration: .01ms !important; animation-iteration-count: 1 !important; }
    }

    @media (max-width: 700px) {
      body { overflow: auto; display: block; }
      .card { width: 100%; min-height: 760px; height: 100vh; }
      header { padding-top: 28px; }
      .stage { height: 560px; margin-top: 8px; }
      .board { left: 3%; top: 70px; width: 42%; height: 185px; }
      .teacher { left: 10%; top: 280px; transform: scale(.78); transform-origin: top left; }
      .bubble { left: 39%; top: 14px; width: 150px; }
      .message { right: 3%; top: 285px; width: 52%; min-height: 210px; padding: 28px 15px 20px; }
      .book { right: 5%; bottom: 10px; transform: scale(.72); transform-origin: bottom right; }
      .flower.one { right: -4%; bottom: 72px; }
      footer { bottom: 14px; padding: 0 20px; }
    }
  </style>
</head>
<body>
  <div class="intro" id="intro" aria-label="Opening greeting">
    <div class="intro-content">
      <p class="intro-kicker">A SPECIAL MESSAGE FOR</p>
      <h2>Someone Wonderful</h2>
      <div class="intro-line"></div>
      <button class="view-present" id="viewPresent" type="button">Click here to view the present</button>
    </div>
  </div>
  <main class="card" aria-label="Animated Teacher's Day greeting card">
    <div class="stars"></div>
    <header>
      <p class="eyebrow">A LITTLE NOTE OF GRATITUDE</p>
      <h1>HAPPY TEACHER'S DAY</h1>
      <div class="rule"></div>
    </header>

    <section class="stage">
      <div class="board"><b>LEARN</b><b>GROW</b><b>SHINE</b></div>
      <div class="teacher" aria-label="Illustration of a female teacher">
        <div class="hair"></div><div class="head"><i class="eye left"></i><i class="eye right"></i><i class="smile"></i></div>
        <div class="body"></div><div class="tie"></div><div class="arm"></div><div class="hand"></div>
      </div>
      <div class="bubble"><strong>Believe</strong><span>in yourself!</span></div>
      <article class="message" id="message"></article>
      <div class="book"><div class="page left"></div><div class="page right"></div><div class="spine"></div><span class="book-label">DREAM</span></div>
      <div class="flower one"><i class="petal"></i><i class="petal"></i><i class="petal"></i><i class="petal"></i><i class="petal"></i><i class="center"></i></div>
      <div class="flower two"><i class="petal"></i><i class="petal"></i><i class="petal"></i><i class="petal"></i><i class="petal"></i><i class="center"></i></div>
    </section>

    <div class="bubbles" id="bubbles"></div>
    <footer>
      Every lesson becomes a beautiful part of who we are.
      <span class="creator">Created by Bidu Hembrom</span>
    </footer>
  </main>

  <script>
    document.body.classList.add("is-loading");
    const intro = document.getElementById("intro");
    const viewPresent = document.getElementById("viewPresent");

    function dismissIntro() {
      intro.classList.add("dismissed");
      document.body.classList.remove("is-loading");
      intro.setAttribute("aria-hidden", "true");
    }

    viewPresent.addEventListener("click", dismissIntro);
    window.setTimeout(dismissIntro, 3600);

    const teacherName = "Tanushree Mam"; // Change this line to personalise the card.
    const messages = [
      ["A teacher plants the seeds of tomorrow.", "With patience, kindness, and a little magic."],
      ["Thank you for helping every dream grow.", "Your lessons stay with us long after class ends."],
      [`Dear ${teacherName},`, "You make learning feel like an adventure."]
    ];
    const message = document.getElementById("message");
    let current = 0;

    function showMessage() {
      message.style.animation = "none";
      void message.offsetWidth;
      message.style.animation = "reveal .8s ease both";
      message.innerHTML = `<h2>${messages[current][0]}</h2><p>${messages[current][1]}</p><small>with love, from your student</small>`;
    }

    showMessage();
    setInterval(() => {
      current = (current + 1) % messages.length;
      showMessage();
    }, 5500);

    const bubbleLayer = document.getElementById("bubbles");
    for (let i = 0; i < 28; i += 1) {
      const bubble = document.createElement("i");
      const size = 7 + Math.random() * 24;
      bubble.className = "orb";
      bubble.style.width = `${size}px`;
      bubble.style.height = `${size}px`;
      bubble.style.left = `${Math.random() * 100}%`;
      bubble.style.top = `${85 + Math.random() * 20}%`;
      bubble.style.animationDuration = `${7 + Math.random() * 9}s`;
      bubble.style.animationDelay = `${-Math.random() * 12}s`;
      bubbleLayer.appendChild(bubble);
    }
  </script>
</body>
</html>
