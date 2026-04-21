# Amo
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
  <title>Mercy, will you be my girlfriend? 💖</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      user-select: none;
    }

    body {
      min-height: 100vh;
      background: linear-gradient(145deg, #ffb7c5 0%, #ffd9e6 40%, #ffe4f0 100%);
      font-family: 'Segoe UI', 'Poppins', 'Quicksand', system-ui, -apple-system, 'Helvetica Neue', sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 20px;
      position: relative;
      overflow-x: hidden;
    }

    /* Floating hearts background */
    .floating-bg {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      z-index: 1;
      overflow: hidden;
    }

    .floating-bg i {
      position: absolute;
      font-size: 1.5rem;
      color: rgba(220, 70, 110, 0.35);
      animation: floatUp 15s infinite linear;
      bottom: -10%;
    }

    @keyframes floatUp {
      0% {
        transform: translateY(0) rotate(0deg);
        opacity: 0;
      }
      15% {
        opacity: 0.7;
      }
      85% {
        opacity: 0.6;
      }
      100% {
        transform: translateY(-120vh) rotate(360deg);
        opacity: 0;
      }
    }

    /* main card */
    .proposal-card {
      position: relative;
      z-index: 20;
      max-width: 650px;
      width: 100%;
      background: rgba(255, 251, 253, 0.98);
      backdrop-filter: blur(1px);
      border-radius: 80px 60px 85px 60px;
      box-shadow: 0 35px 55px rgba(0, 0, 0, 0.2), 0 0 0 12px rgba(255, 190, 210, 0.7);
      padding: 2rem 2rem 2.5rem;
      text-align: center;
      animation: softAppear 0.7s cubic-bezier(0.2, 0.9, 0.4, 1.1);
    }

    @keyframes softAppear {
      0% {
        transform: scale(0.92) translateY(20px);
        opacity: 0;
      }
      100% {
        transform: scale(1) translateY(0);
        opacity: 1;
      }
    }

    .icon-bounce {
      font-size: 5.2rem;
      filter: drop-shadow(2px 8px 18px rgba(0, 0, 0, 0.15));
      margin-bottom: 0.2rem;
      display: inline-block;
      animation: gentleBounce 2.5s infinite ease;
    }

    @keyframes gentleBounce {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-8px); }
    }

    h1 {
      font-size: 2.7rem;
      background: linear-gradient(125deg, #c0395b, #e84393, #ff70a6);
      background-clip: text;
      -webkit-background-clip: text;
      color: transparent;
      margin: 0.5rem 0 0.2rem;
      font-weight: 800;
      font-family: 'Dancing Script', cursive;
    }

    .sweet-message {
      font-size: 1.2rem;
      color: #b84c6e;
      background: #fff0f6;
      display: inline-block;
      padding: 0.4rem 1.5rem;
      border-radius: 60px;
      margin: 0.8rem 0 1rem;
      font-weight: 500;
      box-shadow: inset 0 1px 2px #ffe0e8, 0 4px 8px rgba(0,0,0,0.02);
    }

    .question {
      font-size: 2rem;
      font-weight: bold;
      color: #c13b6b;
      margin: 1.3rem 0 1rem;
      font-family: 'Dancing Script', cursive;
      letter-spacing: 1px;
      background: rgba(255, 235, 240, 0.8);
      display: inline-block;
      padding: 0.2rem 1.5rem;
      border-radius: 80px;
    }

    .mercy-name {
      font-size: 2.2rem;
      background: linear-gradient(120deg, #e84393, #ff9fbc);
      background-clip: text;
      -webkit-background-clip: text;
      color: transparent;
      display: inline-block;
      margin: 0 5px;
    }

    /* buttons container */
    .buttons {
      display: flex;
      justify-content: center;
      gap: 40px;
      flex-wrap: wrap;
      margin: 2rem 0 1rem;
      position: relative;
      min-height: 95px;
    }

    .btn {
      font-size: 1.7rem;
      font-weight: bold;
      padding: 0.8rem 2rem;
      border: none;
      border-radius: 60px;
      cursor: pointer;
      transition: all 0.2s ease;
      font-family: inherit;
      box-shadow: 0 8px 18px rgba(0, 0, 0, 0.12);
      display: inline-flex;
      align-items: center;
      gap: 12px;
    }

    .btn-yes {
      background: #e84393;
      color: white;
      border: 2px solid #ffbfcf;
    }

    .btn-yes:hover {
      background: #c72a74;
      transform: scale(1.05);
      box-shadow: 0 14px 24px rgba(232, 67, 147, 0.4);
    }

    .btn-no {
      background: #c2a5ad;
      color: #311e26;
      position: relative;
      transition: all 0.08s linear;
      border: 2px solid #fad1db;
    }

    /* music & youtube controls */
    .music-control {
      margin-top: 1rem;
      display: flex;
      justify-content: center;
      align-items: center;
      gap: 12px;
      background: rgba(255, 235, 240, 0.8);
      backdrop-filter: blur(4px);
      padding: 8px 20px;
      border-radius: 100px;
      width: fit-content;
      margin-left: auto;
      margin-right: auto;
      border: 1px solid #ffbfcf;
      flex-wrap: wrap;
    }
    
    .music-btn, .youtube-btn {
      background: #e84393;
      border: none;
      color: white;
      font-size: 1rem;
      padding: 8px 18px;
      border-radius: 40px;
      cursor: pointer;
      font-weight: bold;
      display: inline-flex;
      align-items: center;
      gap: 8px;
      transition: 0.2s;
      font-family: inherit;
      text-decoration: none;
    }
    
    .youtube-btn {
      background: #ff0000;
    }
    
    .music-btn:hover {
      background: #c72a74;
      transform: scale(0.97);
    }
    
    .youtube-btn:hover {
      background: #cc0000;
      transform: scale(0.97);
    }
    
    .music-status {
      font-size: 0.8rem;
      color: #b84c6e;
      font-weight: 500;
    }

    /* footer note */
    .footer-note {
      margin-top: 1.8rem;
      font-size: 0.9rem;
      color: #cc7b99;
      border-top: 1px dashed #ffcddb;
      padding-top: 1.3rem;
      display: flex;
      justify-content: center;
      gap: 18px;
      flex-wrap: wrap;
    }

    /* YES celebration modal */
    .modal {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.75);
      backdrop-filter: blur(8px);
      z-index: 1000;
      display: flex;
      align-items: center;
      justify-content: center;
      opacity: 0;
      visibility: hidden;
      transition: all 0.3s ease;
    }

    .modal.active {
      opacity: 1;
      visibility: visible;
    }

    .modal-content {
      background: #fff7f9;
      max-width: 520px;
      width: 90%;
      border-radius: 55px;
      padding: 2rem 1.8rem;
      text-align: center;
      transform: scale(0.8);
      transition: transform 0.3s cubic-bezier(0.34, 1.2, 0.64, 1);
      border: 2px solid #ffb7cb;
    }

    .modal.active .modal-content {
      transform: scale(1);
    }

    .modal-content h2 {
      font-size: 2.5rem;
      color: #d43f7a;
      font-family: 'Dancing Script', cursive;
      margin-bottom: 0.5rem;
    }

    .celebration-zone {
      font-size: 3.2rem;
      letter-spacing: 12px;
      margin: 15px 0;
    }

    .close-modal {
      background: #e84393;
      border: none;
      color: white;
      font-size: 1.2rem;
      padding: 0.7rem 1.5rem;
      border-radius: 50px;
      margin-top: 20px;
      cursor: pointer;
      font-weight: bold;
    }

    @keyframes sparklePulse {
      0% { text-shadow: 0 0 0 #ffb7c5; }
      100% { text-shadow: 0 0 12px #ff80a5, 0 0 5px #ffb347; }
    }

    @media (max-width: 550px) {
      .proposal-card { padding: 1.5rem; }
      h1 { font-size: 2rem; }
      .question { font-size: 1.6rem; }
      .btn { font-size: 1.3rem; padding: 0.6rem 1.3rem; }
      .mercy-name { font-size: 1.8rem; }
    }
  </style>
</head>
<body>

<div class="floating-bg" id="floatingBg"></div>

<div class="proposal-card">
  <div class="icon-bounce">🌸💖👸🏽🌸</div>
  <h1>To my sweet <span class="mercy-name">Mercy</span> 🌹</h1>
  <div class="sweet-message">Every heartbeat whispers your name, Mercy 💗✨</div>
  <div class="question">💍 Mercy, will you be my girlfriend? 💍</div>
  
  <div class="buttons">
    <button class="btn btn-yes" id="yesBtn">💘 YES! ABSOLUTELY 💘</button>
    <button class="btn btn-no" id="noBtn">😅 No... 😅</button>
  </div>
  
  <!-- Music + YouTube controls -->
  <div class="music-control">
    <button class="music-btn" id="playMusicBtn">🎵 Our Romantic Song 🎵</button>
    <a href="https://www.youtube.com/watch?v=rLV5UyD5Ah0" target="_blank" class="youtube-btn" id="youtubeLinkBtn">📺 Open "BUD FLOWERS" on YouTube 📺</a>
    <span class="music-status" id="musicStatus">♫ click to add magic ♫</span>
  </div>
  
  <div class="footer-note">
    <span>💞 You make my world magical 💞</span>
    <span>⭐️ Mercy = My sunshine ⭐️</span>
    <span>🌹 I'm crazy about you 🌹</span>
  </div>
</div>

<!-- Acceptance modal -->
<div id="proposalModal" class="modal">
  <div class="modal-content">
    <div class="celebration-zone">🎉💖🥳💍✨🎊</div>
    <h2>MERCY SAID YES! 💕👸🏽</h2>
    <p>You've just made me the happiest person in the universe, Mercy! 🌟</p>
    <p>I promise to cherish you, make you smile, and love you more every single day. 💗</p>
    <p><strong>🌸 Officially my girlfriend — my Mercy 🌸</strong></p>
    <button class="close-modal" id="closeModalBtn">💋 To forever with you 💋</button>
  </div>
</div>

<script>
  (function() {
    // Floating hearts background
    const floatContainer = document.getElementById('floatingBg');
    const FLOATING_ITEMS = ['❤️', '💖', '💗', '🌸', '🌼', '💫', '✨', '💘', '💕', '🌺', '🦋', '🌹', '👸🏽', '💍', '🌟', '🎵', '🎶'];
    
    function createFloatingItem() {
      const el = document.createElement('i');
      el.innerHTML = FLOATING_ITEMS[Math.floor(Math.random() * FLOATING_ITEMS.length)];
      const size = Math.random() * 26 + 14;
      el.style.fontSize = size + 'px';
      el.style.left = Math.random() * 100 + '%';
      el.style.opacity = Math.random() * 0.55 + 0.2;
      el.style.animationDuration = Math.random() * 13 + 8 + 's';
      el.style.animationDelay = Math.random() * 12 + 's';
      floatContainer.appendChild(el);
      setTimeout(() => { if(el && el.remove) el.remove(); }, 17000);
    }
    
    for(let i = 0; i < 45; i++) setTimeout(() => createFloatingItem(), i * 170);
    setInterval(createFloatingItem, 1600);
    
    // ---------- ROMANTIC MUSIC (Royalty-free, plays in background) ----------
    const musicURL = 'https://cdn.pixabay.com/download/audio/2022/03/10/audio_c8c8f7b3c3.mp3?filename=romantic-piano-103263.mp3';
    let audio = null;
    let musicPlaying = false;
    
    function initAudio() {
      if (audio) return audio;
      audio = new Audio();
      audio.loop = true;
      audio.volume = 0.4;
      audio.src = musicURL;
      audio.preload = 'auto';
      return audio;
    }
    
    function startMusic() {
      if (!audio) initAudio();
      if (!audio) return;
      const playPromise = audio.play();
      if (playPromise !== undefined) {
        playPromise.then(() => {
          musicPlaying = true;
          const statusSpan = document.getElementById('musicStatus');
          if (statusSpan) statusSpan.innerHTML = '🎶 playing softly for you 🎶';
          const playBtn = document.getElementById('playMusicBtn');
          if (playBtn) playBtn.innerHTML = '🎵 Music Playing 🎵';
        }).catch(() => {
          musicPlaying = false;
          document.getElementById('musicStatus').innerHTML = '🔊 click play to hear our song 🔊';
        });
      }
    }
    
    function stopMusic() {
      if (audio && musicPlaying) {
        audio.pause();
        musicPlaying = false;
        document.getElementById('musicStatus').innerHTML = '🎵 music paused — click to resume 🎵';
        document.getElementById('playMusicBtn').innerHTML = '🎵 Play our song 🎵';
      }
    }
    
    function toggleMusic() {
      if (!audio) initAudio();
      if (musicPlaying) stopMusic();
      else startMusic();
    }
    
    document.getElementById('playMusicBtn').addEventListener('click', toggleMusic);
    
    // Preload audio on first interaction
    function preloadAudio() {
      if (!audio) initAudio();
      document.body.removeEventListener('click', preloadAudio);
      document.body.removeEventListener('touchstart', preloadAudio);
    }
    document.body.addEventListener('click', preloadAudio);
    document.body.addEventListener('touchstart', preloadAudio);
    
    // ----- No button playful run away -----
    const yesButton = document.getElementById('yesBtn');
    const noButton = document.getElementById('noBtn');
    const modal = document.getElementById('proposalModal');
    const closeModalBtn = document.getElementById('closeModalBtn');
    
    let dodgeAttempts = 0;
    
    function getRandomPositionInsideContainer(btn, container) {
      if (!container) return { x: 10, y: 10 };
      const containerRect = container.getBoundingClientRect();
      const btnRect = btn.getBoundingClientRect();
      const maxX = containerRect.width - btnRect.width - 15;
      const maxY = containerRect.height - btnRect.height - 15;
      let randX = Math.max(8, Math.random() * maxX);
      let randY = Math.max(8, Math.random() * maxY);
      const yesBtn = document.getElementById('yesBtn');
      if (yesBtn) {
        const yesRect = yesBtn.getBoundingClientRect();
        const relativeYesX = yesRect.left - containerRect.left;
        const relativeYesY = yesRect.top - containerRect.top;
        if (Math.hypot(randX - relativeYesX, randY - relativeYesY) < 70 && maxX > 100) {
          randX = (randX + 70) % maxX;
          randY = (randY + 50) % maxY;
        }
      }
      return { x: Math.min(maxX - 5, Math.max(5, randX)), y: Math.min(maxY - 5, Math.max(5, randY)) };
    }
    
    function moveNoButtonAway() {
      const container = document.querySelector('.buttons');
      if (!container) return;
      if (window.getComputedStyle(noButton).position !== 'absolute') {
        noButton.style.position = 'absolute';
        container.style.position = 'relative';
        container.style.minHeight = '95px';
        noButton.style.left = noButton.offsetLeft + 'px';
        noButton.style.top = noButton.offsetTop + 'px';
        noButton.style.margin = '0';
      }
      const { x, y } = getRandomPositionInsideContainer(noButton, container);
      noButton.style.left = x + 'px';
      noButton.style.top = y + 'px';
      dodgeAttempts++;
      if (dodgeAttempts === 2) {
        noButton.textContent = "🥺 Wait, Mercy? 🥺";
        noButton.style.background = "#e2b6c2";
      } else if (dodgeAttempts === 4) {
        noButton.textContent = "💞 I love you... maybe YES? 💞";
        noButton.style.background = "#ffb7c5";
        noButton.style.color = "#a1345a";
      } else if (dodgeAttempts === 6) {
        noButton.textContent = "💘 YES, MERCY LOVES YOU! 💘";
        noButton.style.background = "#e84393";
        noButton.style.color = "white";
        noButton.style.border = "2px solid gold";
        noButton.removeEventListener('click', noClickHandler);
        noButton.removeEventListener('mouseenter', moveNoButtonAway);
        noButton.removeEventListener('touchstart', touchNoHandler);
        noButton.addEventListener('click', () => celebrateYes());
        noButton.style.cursor = 'pointer';
      }
    }
    
    function noClickHandler(e) {
      e.preventDefault();
      if (dodgeAttempts >= 6) { celebrateYes(); return; }
      moveNoButtonAway();
      const msg = document.createElement('div');
      msg.innerText = "💗 Mercy, think again? 💗";
      msg.style.position = 'fixed';
      msg.style.left = e.clientX + 'px';
      msg.style.top = e.clientY - 40 + 'px';
      msg.style.backgroundColor = '#fff0f3';
      msg.style.padding = '6px 15px';
      msg.style.borderRadius = '50px';
      msg.style.fontSize = '0.95rem';
      msg.style.fontWeight = 'bold';
      msg.style.color = '#c72a74';
      msg.style.zIndex = '10001';
      msg.style.pointerEvents = 'none';
      document.body.appendChild(msg);
      setTimeout(() => msg.remove(), 850);
    }
    
    function touchNoHandler(e) {
      e.preventDefault();
      if (dodgeAttempts >= 6) celebrateYes();
      else moveNoButtonAway();
    }
    
    noButton.addEventListener('click', noClickHandler);
    noButton.addEventListener('mouseenter', () => { if (dodgeAttempts < 6) moveNoButtonAway(); });
    noButton.addEventListener('touchstart', touchNoHandler);
    
    // Celebration
    function celebrateYes() {
      if (!musicPlaying && audio) startMusic();
      modal.classList.add('active');
      if (typeof confetti === 'function') {
        confetti({ particleCount: 250, spread: 100, origin: { y: 0.6 }, colors: ['#e84393', '#ffb7c5'] });
        confetti({ particleCount: 180, spread: 130, origin: { y: 0.3, x: 0.2 } });
        confetti({ particleCount: 180, spread: 130, origin: { y: 0.4, x: 0.8 } });
        setTimeout(() => confetti({ particleCount: 500, spread: 80, origin: { y: 0.5 } }), 180);
      } else {
        for (let i=0; i<60; i++) setTimeout(() => createFloatingItem(), i*30);
      }
      for (let i=0; i<30; i++) {
        const burst = document.createElement('div');
        burst.style.position = 'fixed';
        burst.style.fontSize = (Math.random() * 45 + 28) + 'px';
        burst.style.left = Math.random() * 100 + '%';
        burst.style.top = Math.random() * 80 + 10 + '%';
        burst.style.pointerEvents = 'none';
        burst.style.zIndex = '999';
        burst.style.animation = 'floatUp 1.5s ease-out forwards';
        burst.innerHTML = ['💖', '💘', '🌸', '💍', '👸🏽', '🎵'][Math.floor(Math.random()*6)];
        document.body.appendChild(burst);
        setTimeout(() => burst.remove(), 1600);
      }
    }
    
    yesButton.addEventListener('click', celebrateYes);
    closeModalBtn.addEventListener('click', () => modal.classList.remove('active'));
    modal.addEventListener('click', (e) => { if (e.target === modal) modal.classList.remove('active'); });
    
    if (typeof confetti !== 'function') {
      const script = document.createElement('script');
      script.src = 'https://cdn.jsdelivr.net/npm/canvas-confetti@1';
      document.head.appendChild(script);
    }
    
    setTimeout(() => { if(yesButton) yesButton.style.animation = 'sparklePulse 1.2s infinite alternate'; }, 1000);
    console.log("%c💖 Mercy, you're my everything! 💖", "color: #e84393; font-size: 16px; font-weight: bold;");
  })();
</script>
</body>
</html>
