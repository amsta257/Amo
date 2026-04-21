# Amo
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
  <title>Will You Marry Me? ❤️</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      user-select: none; /* prevents accidental text selection on buttons */
    }

    body {
      min-height: 100vh;
      background: linear-gradient(145deg, #ff9a9e 0%, #fad0c4 50%, #fad0c4 100%);
      font-family: 'Segoe UI', 'Poppins', 'Dancing Script', 'Pacifico', cursive, system-ui, -apple-system, 'Helvetica Neue', sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 20px;
      position: relative;
      overflow-x: hidden;
    }

    /* Floating hearts animation background */
    .heart-bg {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      z-index: 1;
      overflow: hidden;
    }

    .heart-bg i {
      position: absolute;
      font-size: 1.5rem;
      color: rgba(255, 80, 120, 0.25);
      animation: floatHeart 12s infinite linear;
      bottom: -10%;
    }

    @keyframes floatHeart {
      0% {
        transform: translateY(0) rotate(0deg);
        opacity: 0;
      }
      10% {
        opacity: 0.6;
      }
      90% {
        opacity: 0.6;
      }
      100% {
        transform: translateY(-110vh) rotate(360deg);
        opacity: 0;
      }
    }

    /* main card */
    .proposal-card {
      position: relative;
      z-index: 20;
      max-width: 650px;
      width: 100%;
      background: rgba(255, 255, 255, 0.96);
      backdrop-filter: blur(2px);
      border-radius: 64px 48px 80px 48px;
      box-shadow: 0 30px 45px rgba(0, 0, 0, 0.2), 0 0 0 12px rgba(255, 215, 215, 0.5);
      padding: 2rem 2rem 2.5rem;
      text-align: center;
      transition: all 0.3s ease;
      animation: gentlePop 0.8s cubic-bezier(0.2, 0.9, 0.4, 1.1);
    }

    @keyframes gentlePop {
      0% {
        transform: scale(0.92);
        opacity: 0;
      }
      100% {
        transform: scale(1);
        opacity: 1;
      }
    }

    /* romantic header */
    .ring-icon {
      font-size: 5rem;
      filter: drop-shadow(2px 6px 12px rgba(0, 0, 0, 0.2));
      margin-bottom: 0.5rem;
      display: inline-block;
      animation: subtleRing 2s infinite ease;
    }

    @keyframes subtleRing {
      0%, 100% { transform: rotate(0deg); }
      25% { transform: rotate(8deg); }
      75% { transform: rotate(-4deg); }
    }

    h1 {
      font-size: 2.9rem;
      background: linear-gradient(135deg, #c2365c, #e84393, #fd79a8);
      background-clip: text;
      -webkit-background-clip: text;
      color: transparent;
      margin: 0.5rem 0 0.5rem;
      font-weight: 800;
      letter-spacing: -0.5px;
      font-family: 'Dancing Script', cursive;
    }

    .sub-message {
      font-size: 1.25rem;
      color: #6b3e4c;
      background: #fff0f3;
      display: inline-block;
      padding: 0.4rem 1.2rem;
      border-radius: 100px;
      margin-bottom: 1.5rem;
      font-weight: 500;
      box-shadow: inset 0 1px 2px #ffd9e4, 0 2px 5px rgba(0,0,0,0.05);
    }

    .question {
      font-size: 2rem;
      font-weight: bold;
      color: #b34167;
      margin: 1.2rem 0 1rem;
      font-family: 'Dancing Script', cursive;
    }

    /* buttons container */
    .buttons {
      display: flex;
      justify-content: center;
      gap: 35px;
      flex-wrap: wrap;
      margin: 2rem 0 1rem;
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
      box-shadow: 0 8px 18px rgba(0, 0, 0, 0.15);
      display: inline-flex;
      align-items: center;
      gap: 12px;
    }

    .btn-yes {
      background: #e84393;
      color: white;
      border: 2px solid #ffb7c5;
    }

    .btn-yes:hover {
      background: #c72a74;
      transform: scale(1.05);
      box-shadow: 0 12px 22px rgba(232, 67, 147, 0.4);
    }

    .btn-no {
      background: #b0a0a5;
      color: #2d1c22;
      position: relative;
      transition: all 0.1s ease;
    }

    /* romantic footer */
    .footer-note {
      margin-top: 2rem;
      font-size: 0.85rem;
      color: #b9708b;
      border-top: 1px dashed #fbc4d2;
      padding-top: 1.2rem;
      display: flex;
      justify-content: center;
      gap: 12px;
      flex-wrap: wrap;
    }

    .footer-note span {
      font-size: 1rem;
    }

    /* YES response modal */
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
      background: #fff5f8;
      max-width: 500px;
      width: 90%;
      border-radius: 48px;
      padding: 2rem 1.8rem;
      text-align: center;
      box-shadow: 0 30px 40px rgba(0, 0, 0, 0.3);
      transform: scale(0.8);
      transition: transform 0.3s cubic-bezier(0.34, 1.2, 0.64, 1);
      border: 2px solid #ffb7cb;
    }

    .modal.active .modal-content {
      transform: scale(1);
    }

    .modal-content h2 {
      font-size: 2.4rem;
      color: #d43f7a;
      font-family: 'Dancing Script', cursive;
      margin-bottom: 1rem;
    }

    .modal-content p {
      font-size: 1.25rem;
      margin: 0.8rem 0;
      color: #5a2e3e;
    }

    .fireworks-zone {
      font-size: 3rem;
      letter-spacing: 12px;
      margin: 20px 0;
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
      transition: all 0.2s;
    }

    .close-modal:hover {
      background: #b32c6b;
      transform: scale(0.96);
    }

    /* extra sparkle for the page */
    @keyframes sparkle {
      0% { text-shadow: 0 0 0 gold; }
      100% { text-shadow: 0 0 12px #ffd966; }
    }

    /* responsive adjustments */
    @media (max-width: 550px) {
      .proposal-card {
        padding: 1.6rem;
      }
      h1 {
        font-size: 2rem;
      }
      .question {
        font-size: 1.6rem;
      }
      .btn {
        font-size: 1.3rem;
        padding: 0.6rem 1.4rem;
      }
      .ring-icon {
        font-size: 3.8rem;
      }
    }

    /* for the no button "runaway" effect */
    .no-runaway {
      transition: all 0.08s linear;
    }
  </style>
</head>
<body>

<div class="heart-bg" id="heartBackground"></div>

<div class="proposal-card">
  <div class="ring-icon">💍💖</div>
  <h1>My Dearest Love,</h1>
  <div class="sub-message">Every heartbeat whispers your name</div>
  <div class="question">Will you marry me? ✨</div>
  
  <div class="buttons">
    <button class="btn btn-yes" id="yesBtn">💘 YES! 💘</button>
    <button class="btn btn-no" id="noBtn">😅 No... 😅</button>
  </div>
  
  <div class="footer-note">
    <span>❤️ You are my forever ❤️</span>
    <span>✨ my whole universe ✨</span>
  </div>
</div>

<!-- The proposal acceptance modal -->
<div id="proposalModal" class="modal">
  <div class="modal-content">
    <div class="fireworks-zone">🎉💍🥂✨🎊</div>
    <h2>YES! She said YES! 💕</h2>
    <p>My love, you've made me the happiest person alive.</p>
    <p>I promise to cherish you, make you laugh, and love you more every single day.</p>
    <p>❤️ <strong>Our forever starts now.</strong> ❤️</p>
    <button class="close-modal" id="closeModalBtn">💞 To infinity & beyond 💞</button>
  </div>
</div>

<script>
  (function() {
    // ---------- floating hearts background ----------
    const heartContainer = document.getElementById('heartBackground');
    const HEART_SYMBOLS = ['❤️', '💖', '💗', '💓', '💕', '💞', '🌸', '🌹', '✨', '💘'];
    
    function createFloatingHeart() {
      const heart = document.createElement('i');
      heart.innerHTML = HEART_SYMBOLS[Math.floor(Math.random() * HEART_SYMBOLS.length)];
      const size = Math.random() * 24 + 14; // 14px to 38px
      heart.style.fontSize = size + 'px';
      heart.style.left = Math.random() * 100 + '%';
      heart.style.opacity = Math.random() * 0.5 + 0.2;
      heart.style.animationDuration = Math.random() * 10 + 8 + 's'; // 8-18s
      heart.style.animationDelay = Math.random() * 10 + 's';
      heartContainer.appendChild(heart);
      
      // remove after animation ends to keep DOM clean
      setTimeout(() => {
        if(heart && heart.remove) heart.remove();
      }, 15000);
    }
    
    // generate multiple floating hearts initially, then keep interval moderate
    for(let i = 0; i < 35; i++) {
      setTimeout(() => createFloatingHeart(), i * 200);
    }
    setInterval(createFloatingHeart, 1800);
    
    // ---------- interactive elements ----------
    const yesButton = document.getElementById('yesBtn');
    const noButton = document.getElementById('noBtn');
    const modal = document.getElementById('proposalModal');
    const closeModalBtn = document.getElementById('closeModalBtn');
    
    // celebration on YES: modal + confetti effect
    function launchHeavyCelebration() {
      // Show modal
      modal.classList.add('active');
      
      // Burst of confetti from multiple positions
      if (typeof confetti === 'function') {
        // if canvas confetti is loaded (we'll add library via CDN in head, but we can implement simple fallback)
        confetti({ particleCount: 200, spread: 100, origin: { y: 0.6 }, colors: ['#e84393', '#ffb7c5', '#ff6b9d', '#c44569'] });
        confetti({ particleCount: 150, spread: 130, origin: { y: 0.3, x: 0.2 }, startVelocity: 15 });
        confetti({ particleCount: 150, spread: 130, origin: { y: 0.4, x: 0.8 }, startVelocity: 15 });
        setTimeout(() => {
          confetti({ particleCount: 400, spread: 80, origin: { y: 0.5 }, startVelocity: 20, colors: ['#ffd966', '#e84393', '#f8c291'] });
        }, 200);
        setTimeout(() => {
          confetti({ particleCount: 300, spread: 100, origin: { y: 0.7 }, startVelocity: 18 });
        }, 500);
      } else {
        // fallback: add dynamic style & extra hearts
        for (let i = 0; i < 40; i++) {
          setTimeout(() => createFloatingHeart(), i * 30);
        }
      }
      
      // also add some big floating hearts
      const bigHearts = ['💖', '💍', '💘', '💕', '👰', '🤵'];
      for (let i = 0; i < 12; i++) {
        const bigHeartDiv = document.createElement('div');
        bigHeartDiv.style.position = 'fixed';
        bigHeartDiv.style.fontSize = (Math.random() * 40 + 30) + 'px';
        bigHeartDiv.style.left = Math.random() * 100 + '%';
        bigHeartDiv.style.top = Math.random() * 80 + 10 + '%';
        bigHeartDiv.style.pointerEvents = 'none';
        bigHeartDiv.style.zIndex = '999';
        bigHeartDiv.style.opacity = '0.9';
        bigHeartDiv.style.animation = 'floatHeart 2s ease-out forwards';
        bigHeartDiv.innerHTML = bigHearts[Math.floor(Math.random() * bigHearts.length)];
        document.body.appendChild(bigHeartDiv);
        setTimeout(() => bigHeartDiv.remove(), 2000);
      }
      
      // audio optional but not mandatory due to autoplay policies, but we could try gentle beep? but no worries.
    }
    
    // ---- "No" button behaviour: move away randomly, but don't be mean: also change text eventually to "Yes I'm sure" but we keep romantic.
    // The No button will run away from cursor/tap on desktop/mobile, and after 4 dodges it changes to "Wait, I mean YES!"?
    let dodgeCount = 0;
    let noButtonOriginalText = "😅 No... 😅";
    
    function getRandomPosition(buttonElement) {
      const card = document.querySelector('.proposal-card');
      const cardRect = card.getBoundingClientRect();
      const btnRect = buttonElement.getBoundingClientRect();
      const margin = 20;
      // available area inside card boundaries
      const maxLeft = cardRect.width - btnRect.width - margin;
      const maxTop = cardRect.height - btnRect.height - margin;
      const randomX = Math.max(margin, Math.random() * maxLeft);
      const randomY = Math.max(margin, Math.random() * maxTop);
      return { x: randomX, y: randomY };
    }
    
    function moveNoButton() {
      if (!noButton) return;
      // relative positioning inside card (buttons container is relative? we set parent relative but better make button position relative with transform)
      // Buttons container has display flex, to move individually we set absolute? We'll change no button to position absolute relative to .buttons container
      const buttonsContainer = document.querySelector('.buttons');
      if (!buttonsContainer) return;
      // Ensure noButton has position absolute if not already
      const computedStyle = window.getComputedStyle(noButton);
      if (computedStyle.position !== 'absolute') {
        noButton.style.position = 'absolute';
        // store original inline styles to not break layout much, but also we set container relative
        buttonsContainer.style.position = 'relative';
        buttonsContainer.style.minHeight = '80px';
        // set initial left, top based on its original offset
        const originalLeft = noButton.offsetLeft;
        const originalTop = noButton.offsetTop;
        noButton.style.left = originalLeft + 'px';
        noButton.style.top = originalTop + 'px';
        noButton.style.margin = '0';
      }
      // get container bounds
      const containerRect = buttonsContainer.getBoundingClientRect();
      const btnRect = noButton.getBoundingClientRect();
      // relative to container
      const maxX = containerRect.width - btnRect.width - 15;
      const maxY = containerRect.height - btnRect.height - 15;
      let newX = Math.max(5, Math.random() * maxX);
      let newY = Math.max(5, Math.random() * maxY);
      // try to not overlap yes button too much (just cute)
      const yesRect = yesButton.getBoundingClientRect();
      const relativeYesX = yesRect.left - containerRect.left;
      const relativeYesY = yesRect.top - containerRect.top;
      // if distance too small, adjust
      let dx = newX - relativeYesX;
      let dy = newY - relativeYesY;
      const distance = Math.hypot(dx, dy);
      if (distance < 70 && maxX > 100) {
        newX = (newX + 80) % maxX;
        newY = (newY + 50) % maxY;
      }
      noButton.style.left = Math.min(maxX - 5, Math.max(5, newX)) + 'px';
      noButton.style.top = Math.min(maxY - 5, Math.max(5, newY)) + 'px';
      // also change text after few moves, more playful
      dodgeCount++;
      if (dodgeCount === 2) {
        noButton.textContent = "🤔 Hmm... maybe? 🤔";
      } else if (dodgeCount === 4) {
        noButton.textContent = "💕 Wait, I love you! 💕";
        noButton.style.background = "#ffb7c5";
        noButton.style.color = "#9b2f5e";
        // change event to trigger YES after next click?
      } else if (dodgeCount >= 6) {
        noButton.textContent = "💍 YES! Of course! 💍";
        noButton.style.background = "#e84393";
        noButton.style.color = "white";
        noButton.style.border = "2px solid gold";
        // remove runaway behavior and make it act as yes button
        noButton.removeEventListener('click', noButtonClickHandler);
        noButton.removeEventListener('mouseenter', moveNoButton);
        noButton.removeEventListener('touchstart', moveNoButton);
        noButton.addEventListener('click', () => {
          launchHeavyCelebration();
        });
        noButton.style.cursor = 'pointer';
        noButton.style.transform = 'scale(1.02)';
      }
    }
    
    // event handlers for dodge
    function handleNoClick(ev) {
      ev.preventDefault();
      if (dodgeCount >= 6) {
        // already became a yes button (in disguise)
        launchHeavyCelebration();
        return;
      }
      // otherwise move
      moveNoButton();
      // also playful: add a little heart popup
      const tempMsg = document.createElement('div');
      tempMsg.innerText = "💗 Think again? 💗";
      tempMsg.style.position = 'fixed';
      tempMsg.style.left = ev.clientX + 'px';
      tempMsg.style.top = ev.clientY - 30 + 'px';
      tempMsg.style.backgroundColor = '#ffeef2';
      tempMsg.style.padding = '6px 12px';
      tempMsg.style.borderRadius = '40px';
      tempMsg.style.fontSize = '0.9rem';
      tempMsg.style.fontWeight = 'bold';
      tempMsg.style.color = '#d43f7a';
      tempMsg.style.boxShadow = '0 4px 12px rgba(0,0,0,0.2)';
      tempMsg.style.zIndex = '10000';
      tempMsg.style.pointerEvents = 'none';
      document.body.appendChild(tempMsg);
      setTimeout(() => tempMsg.remove(), 800);
    }
    
    function handleNoMouseEnter() {
      if (dodgeCount < 6) {
        moveNoButton();
      }
    }
    
    // store references for cleanup
    let noButtonClickHandler = handleNoClick;
    let noButtonMouseEnterHandler = handleNoMouseEnter;
    let noButtonTouchHandler = function(e) {
      e.preventDefault();
      if (dodgeCount < 6) moveNoButton();
    };
    
    // attach dodge events
    noButton.addEventListener('click', noButtonClickHandler);
    noButton.addEventListener('mouseenter', noButtonMouseEnterHandler);
    noButton.addEventListener('touchstart', noButtonTouchHandler);
    
    // Yes button magic
    yesButton.addEventListener('click', () => {
      launchHeavyCelebration();
    });
    
    // Close modal button
    closeModalBtn.addEventListener('click', () => {
      modal.classList.remove('active');
      // extra sprinkle hearts after closing
      for(let i = 0; i < 20; i++) {
        setTimeout(() => createFloatingHeart(), i * 60);
      }
    });
    
    // also if user clicks outside modal (on overlay) we can close
    modal.addEventListener('click', (e) => {
      if (e.target === modal) {
        modal.classList.remove('active');
      }
    });
    
    // ensure confetti library loaded dynamically (cdn)
    if (typeof confetti !== 'function') {
      const script = document.createElement('script');
      script.src = 'https://cdn.jsdelivr.net/npm/canvas-confetti@1';
      script.onload = () => {
        console.log('confetti ready');
      };
      document.head.appendChild(script);
    }
    
    // little bonus: auto create a romantic message after 2 seconds
    setTimeout(() => {
      const btnYes = document.querySelector('.btn-yes');
      if(btnYes) {
        btnYes.style.animation = 'sparkle 1.2s infinite alternate';
      }
    }, 1000);
    
    // preload some big love text animation
    const questionDiv = document.querySelector('.question');
    if(questionDiv) {
      setInterval(() => {
        questionDiv.style.transform = 'scale(1.02)';
        setTimeout(() => { if(questionDiv) questionDiv.style.transform = 'scale(1)'; }, 400);
      }, 2800);
    }
    
    // mobile friendly touch adjustments - ensure no button doesn't trap
    // add instruction note? but it's fine, the button runs, still reachable eventually
  })();
</script>
</body>
</html>
