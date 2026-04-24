# Amo
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>🎂 Happy 20th Birthday, Grace!</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 25%, #ffd1b3 50%, #a18cd1 75%, #fbc2eb 100%);
            background-size: 400% 400%;
            animation: gradientShift 15s ease infinite;
            min-height: 100vh;
            overflow-x: hidden;
            position: relative;
        }

        @keyframes gradientShift {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        /* Floating Elements Background */
        .balloons-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 1;
        }

        .balloon {
            position: absolute;
            bottom: -150px;
            font-size: 40px;
            animation: floatUp linear infinite;
            opacity: 0.7;
        }

        @keyframes floatUp {
            0% {
                transform: translateY(0) rotate(0deg);
                opacity: 0.7;
            }
            50% {
                opacity: 1;
            }
            100% {
                transform: translateY(-110vh) rotate(360deg);
                opacity: 0;
            }
        }

        .floating-element {
            position: absolute;
            font-size: 30px;
            animation: gentleFloat 3s ease-in-out infinite;
            opacity: 0.6;
        }

        @keyframes gentleFloat {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-15px); }
        }

        /* Confetti */
        .confetti-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 2;
        }

        .confetti-piece {
            position: absolute;
            width: 12px;
            height: 12px;
            top: -10px;
            animation: confettiFall linear infinite;
        }

        @keyframes confettiFall {
            0% {
                transform: translateY(0) rotate(0deg) scale(1);
                opacity: 1;
            }
            100% {
                transform: translateY(100vh) rotate(720deg) scale(0.5);
                opacity: 0;
            }
        }

        /* Sparkles */
        .sparkle {
            position: fixed;
            pointer-events: none;
            z-index: 999;
            animation: sparklePop 0.8s ease-out forwards;
        }

        @keyframes sparklePop {
            0% {
                opacity: 1;
                transform: scale(1) rotate(0deg);
            }
            100% {
                opacity: 0;
                transform: scale(0) rotate(180deg);
            }
        }

        /* Main Content */
        .main-content {
            position: relative;
            z-index: 10;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
            padding: 20px;
        }

        .card {
            background: rgba(255, 255, 255, 0.92);
            border-radius: 30px;
            padding: 40px;
            max-width: 650px;
            width: 100%;
            box-shadow: 0 30px 60px rgba(0, 0, 0, 0.2), 0 0 80px rgba(245, 87, 108, 0.3);
            text-align: center;
            animation: slideIn 1.2s cubic-bezier(0.68, -0.55, 0.265, 1.55);
            backdrop-filter: blur(10px);
            border: 2px solid rgba(255, 255, 255, 0.5);
        }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateY(80px) scale(0.9);
            }
            to {
                opacity: 1;
                transform: translateY(0) scale(1);
            }
        }

        .crown-emoji {
            font-size: 70px;
            animation: royalBounce 1.2s infinite;
            display: inline-block;
        }

        @keyframes royalBounce {
            0%, 100% { transform: translateY(0) rotate(0deg); }
            25% { transform: translateY(-15px) rotate(-5deg); }
            75% { transform: translateY(-15px) rotate(5deg); }
        }

        .title {
            font-size: 3em;
            margin: 15px 0 5px 0;
            background: linear-gradient(135deg, #f5576c, #f093fb, #a18cd1);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            font-weight: 900;
            letter-spacing: 2px;
        }

        .friend-name {
            font-size: 2.8em;
            color: #f5576c;
            margin-bottom: 5px;
            font-weight: bold;
            font-style: italic;
            text-shadow: 2px 2px 0px rgba(245, 87, 108, 0.2);
        }

        .subtitle {
            font-size: 1.3em;
            color: #a18cd1;
            margin-bottom: 15px;
            font-weight: 500;
        }

        .message {
            font-size: 1.15em;
            color: #555;
            line-height: 1.8;
            margin: 20px 0;
            font-style: italic;
            background: rgba(161, 140, 209, 0.08);
            padding: 20px;
            border-radius: 20px;
            border-left: 4px solid #f093fb;
        }

        .age-badge {
            display: inline-block;
            background: linear-gradient(135deg, #f5576c, #f093fb);
            color: white;
            padding: 12px 35px;
            border-radius: 50px;
            font-size: 1.4em;
            font-weight: bold;
            margin: 15px 0;
            box-shadow: 0 8px 25px rgba(245, 87, 108, 0.4);
            animation: pulse 2s infinite;
            letter-spacing: 1px;
        }

        @keyframes pulse {
            0%, 100% { box-shadow: 0 8px 25px rgba(245, 87, 108, 0.4); }
            50% { box-shadow: 0 8px 35px rgba(245, 87, 108, 0.7); }
        }

        /* Photo Gallery */
        .photo-gallery {
            display: flex;
            gap: 15px;
            justify-content: center;
            flex-wrap: wrap;
            margin: 25px 0;
        }

        .photo-placeholder {
            width: 130px;
            height: 130px;
            border-radius: 20px;
            background: linear-gradient(135deg, #fbc2eb 0%, #a18cd1 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 55px;
            color: white;
            box-shadow: 0 8px 25px rgba(161, 140, 209, 0.3);
            transition: all 0.4s cubic-bezier(0.68, -0.55, 0.265, 1.55);
            cursor: pointer;
            position: relative;
            overflow: hidden;
        }

        .photo-placeholder:hover {
            transform: scale(1.15) rotate(-5deg);
            box-shadow: 0 15px 35px rgba(245, 87, 108, 0.4);
        }

        .photo-placeholder img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            border-radius: 20px;
        }

        .photo-caption {
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            background: rgba(0, 0, 0, 0.55);
            color: white;
            font-size: 0.75em;
            padding: 6px;
            border-radius: 0 0 20px 20px;
            font-weight: 500;
        }

        /* Buttons */
        .button-group {
            display: flex;
            gap: 12px;
            flex-wrap: wrap;
            justify-content: center;
            margin-top: 25px;
        }

        .btn {
            padding: 14px 28px;
            font-size: 1em;
            font-weight: bold;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s cubic-bezier(0.68, -0.55, 0.265, 1.55);
            text-transform: uppercase;
            letter-spacing: 1.5px;
            position: relative;
            overflow: hidden;
        }

        .btn:hover {
            transform: translateY(-4px);
            box-shadow: 0 12px 30px rgba(0, 0, 0, 0.25);
        }

        .btn:active {
            transform: translateY(-1px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }

        .btn-cake {
            background: linear-gradient(135deg, #f5576c 0%, #f093fb 100%);
            color: white;
            font-size: 1.1em;
        }

        .btn-music {
            background: linear-gradient(135deg, #a18cd1 0%, #fbc2eb 100%);
            color: white;
        }

        .btn-message {
            background: linear-gradient(135deg, #fbc2eb 0%, #f093fb 100%);
            color: white;
        }

        .btn-surprise {
            background: linear-gradient(135deg, #ffd1b3 0%, #f5576c 100%);
            color: white;
            animation: glowPulse 2s infinite;
        }

        @keyframes glowPulse {
            0%, 100% { box-shadow: 0 0 20px rgba(245, 87, 108, 0.4); }
            50% { box-shadow: 0 0 40px rgba(245, 87, 108, 0.8); }
        }

        /* Cake Animation */
        .cake-container {
            position: relative;
            margin: 25px auto;
            width: 200px;
            height: 200px;
            cursor: pointer;
            transition: transform 0.3s;
        }

        .cake-container:hover {
            transform: scale(1.05);
        }

        .cake {
            position: relative;
            width: 100%;
            height: 100%;
        }

        .cake-layer {
            position: absolute;
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
            border-radius: 12px;
        }

        .cake-layer-1 {
            width: 190px;
            height: 55px;
            background: linear-gradient(135deg, #f5576c, #f093fb);
            bottom: 0;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
        }

        .cake-layer-2 {
            width: 150px;
            height: 55px;
            background: linear-gradient(135deg, #fbc2eb, #a18cd1);
            bottom: 45px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
        }

        .cake-layer-3 {
            width: 110px;
            height: 55px;
            background: linear-gradient(135deg, #ffd1b3, #f5576c);
            bottom: 90px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
        }

        .cake-frosting {
            position: absolute;
            bottom: 5px;
            left: 50%;
            transform: translateX(-50%);
            font-size: 12px;
            color: white;
            letter-spacing: 3px;
            font-weight: bold;
            z-index: 5;
        }

        .candles-container {
            position: absolute;
            bottom: 140px;
            left: 50%;
            transform: translateX(-50%);
            display: flex;
            gap: 20px;
        }

        .candle {
            width: 8px;
            height: 45px;
            background: linear-gradient(to bottom, #ffd700, #ffaa00);
            border-radius: 5px;
            position: relative;
        }

        .candle-stripe {
            position: absolute;
            width: 100%;
            height: 3px;
            background: #ff6b6b;
            border-radius: 2px;
        }

        .flame {
            position: absolute;
            top: -22px;
            left: 50%;
            transform: translateX(-50%);
            width: 16px;
            height: 22px;
            background: radial-gradient(circle, #fff7ae, #ff6b35);
            border-radius: 50% 50% 20% 20%;
            animation: flicker 0.3s infinite alternate;
            box-shadow: 0 0 15px rgba(255, 107, 53, 0.6);
        }

        @keyframes flicker {
            from { 
                transform: translateX(-50%) scale(1);
                box-shadow: 0 0 15px rgba(255, 107, 53, 0.6);
            }
            to { 
                transform: translateX(-50%) scale(1.15, 0.9);
                box-shadow: 0 0 25px rgba(255, 107, 53, 0.8);
            }
        }

        .number-candle {
            position: absolute;
            top: -8px;
            left: 50%;
            transform: translateX(-50%);
            font-size: 14px;
            color: #ffd700;
            font-weight: bold;
            text-shadow: 0 0 10px rgba(255, 215, 0, 0.8);
            pointer-events: none;
        }

        /* Countdown */
        .countdown-section {
            background: rgba(161, 140, 209, 0.1);
            border-radius: 20px;
            padding: 20px;
            margin: 20px 0;
        }

        .countdown-title {
            font-size: 0.9em;
            color: #a18cd1;
            text-transform: uppercase;
            letter-spacing: 3px;
            margin-bottom: 10px;
        }

        .countdown {
            display: flex;
            gap: 12px;
            justify-content: center;
        }

        .countdown-item {
            background: rgba(255, 255, 255, 0.8);
            padding: 12px;
            border-radius: 15px;
            min-width: 65px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.08);
        }

        .countdown-number {
            font-size: 1.8em;
            font-weight: bold;
            color: #f5576c;
        }

        .countdown-label {
            font-size: 0.7em;
            color: #999;
            text-transform: uppercase;
            letter-spacing: 2px;
        }

        /* Modal */
        .modal {
            display: none;
            position: fixed;
            z-index: 1000;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.75);
            animation: fadeIn 0.3s;
            backdrop-filter: blur(5px);
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        .modal-content {
            background: white;
            margin: 8% auto;
            padding: 35px;
            border-radius: 25px;
            max-width: 500px;
            width: 90%;
            text-align: center;
            box-shadow: 0 25px 60px rgba(0,0,0,0.3);
            animation: modalSlideIn 0.4s cubic-bezier(0.68, -0.55, 0.265, 1.55);
        }

        @keyframes modalSlideIn {
            from {
                opacity: 0;
                transform: translateY(-60px) scale(0.9);
            }
            to {
                opacity: 1;
                transform: translateY(0) scale(1);
            }
        }

        .modal h2 {
            color: #f5576c;
            margin-bottom: 20px;
            font-size: 1.8em;
        }

        .modal textarea {
            width: 100%;
            height: 140px;
            padding: 18px;
            border: 2px solid #fbc2eb;
            border-radius: 18px;
            font-size: 1em;
            margin: 20px 0;
            resize: vertical;
            font-family: inherit;
            transition: border-color 0.3s;
        }

        .modal textarea:focus {
            outline: none;
            border-color: #f5576c;
        }

        .messages-wall {
            max-height: 300px;
            overflow-y: auto;
            text-align: left;
            margin: 20px 0;
        }

        .message-bubble {
            background: #fff5f7;
            padding: 12px 18px;
            border-radius: 18px;
            margin: 8px 0;
            color: #555;
            font-size: 0.95em;
            border-left: 3px solid #f093fb;
        }

        .message-bubble small {
            color: #aaa;
            font-size: 0.75em;
        }

        /* Responsive */
        @media (max-width: 600px) {
            .card {
                padding: 25px 20px;
                margin: 10px;
                border-radius: 25px;
            }
            .title {
                font-size: 2.2em;
            }
            .friend-name {
                font-size: 2em;
            }
            .photo-placeholder {
                width: 90px;
                height: 90px;
                font-size: 40px;
            }
            .btn {
                padding: 12px 20px;
                font-size: 0.85em;
            }
            .candles-container {
                gap: 15px;
            }
            .cake-layer-1 { width: 160px; height: 45px; }
            .cake-layer-2 { width: 125px; height: 45px; bottom: 38px; }
            .cake-layer-3 { width: 90px; height: 45px; bottom: 76px; }
            .candles-container { bottom: 118px; }
            .candle { height: 38px; }
        }
    </style>
</head>
<body>
    <!-- Animated Background -->
    <div class="balloons-container" id="balloonsContainer"></div>
    <div class="confetti-container" id="confettiContainer"></div>

    <!-- Floating decorative elements -->
    <div class="floating-element" style="top:10%;left:5%;animation-delay:0s;">💖</div>
    <div class="floating-element" style="top:20%;right:8%;animation-delay:0.5s;">✨</div>
    <div class="floating-element" style="top:60%;left:3%;animation-delay:1s;">🌸</div>
    <div class="floating-element" style="top:70%;right:5%;animation-delay:1.5s;">💫</div>
    <div class="floating-element" style="top:40%;left:90%;animation-delay:2s;">🦋</div>

    <!-- Main Content -->
    <div class="main-content">
        <div class="card" id="mainCard">
            <!-- Crown for the birthday queen -->
            <div class="crown-emoji">👑</div>
            
            <!-- Title -->
            <h1 class="title">Happy Birthday!</h1>
            
            <!-- Grace's Name -->
            <h2 class="friend-name">Grace</h2>
            <p class="subtitle">✨ The Big Two-Zero! ✨</p>
            
            <!-- Age Badge -->
            <div class="age-badge">🎀 Twenty & Fabulous! 🎀</div>
            
            <!-- Animated Cake with 20 candles -->
            <div class="cake-container" id="cakeContainer" onclick="blowCandles()" title="Click to blow out the candles!">
                <div class="cake">
                    <div class="cake-layer cake-layer-1">
                        <span class="cake-frosting">~ ~ ~ ~ ~ ~</span>
                    </div>
                    <div class="cake-layer cake-layer-2">
                        <span class="cake-frosting">~ ~ ~ ~ ~</span>
                    </div>
                    <div class="cake-layer cake-layer-3">
                        <span class="cake-frosting">~ ~ ~ ~</span>
                    </div>
                    <div class="candles-container" id="candlesContainer">
                        <!-- Candles generated by JS -->
                    </div>
                </div>
            </div>
            
            <!-- Personal Message for Grace -->
            <p class="message" id="personalMessage">
                Dear Grace,<br><br>
                Welcome to your twenties! 🎉 This is such an exciting milestone, 
                and I couldn't let it pass without celebrating the amazing person 
                you are. May this new decade bring you endless adventures, 
                unforgettable memories, and all the happiness you deserve. 
                Here's to you, the birthday queen! 💖👑
            </p>
            
            <!-- Photo Gallery -->
            <div class="photo-gallery" id="photoGallery">
                <div class="photo-placeholder" onclick="showPhotoMessage('Beautiful Grace! 📸')">
                    🌸
                    <div class="photo-caption">Forever Fabulous</div>
                </div>
                <div class="photo-placeholder" onclick="showPhotoMessage('Best moments together! 💖')">
                    ✨
                    <div class="photo-caption">Cherished Memories</div>
                </div>
                <div class="photo-placeholder" onclick="showPhotoMessage('Our adventures await! 🌟')">
                    🦋
                    <div class="photo-caption">Adventures Ahead</div>
                </div>
            </div>
            
            <!-- Countdown -->
            <div class="countdown-section">
                <div class="countdown-title">⏳ Countdown to Grace's 21st</div>
                <div class="countdown" id="countdown">
                    <div class="countdown-item">
                        <div class="countdown-number" id="days">--</div>
                        <div class="countdown-label">Days</div>
                    </div>
                    <div class="countdown-item">
                        <div class="countdown-number" id="hours">--</div>
                        <div class="countdown-label">Hours</div>
                    </div>
                    <div class="countdown-item">
                        <div class="countdown-number" id="minutes">--</div>
                        <div class="countdown-label">Mins</div>
                    </div>
                </div>
            </div>
            
            <!-- Action Buttons -->
            <div class="button-group">
                <button class="btn btn-cake" onclick="blowCandles()">
                    🎂 Blow Candles
                </button>
                <button class="btn btn-music" onclick="toggleMusic()">
                    🎵 Birthday Song
                </button>
                <button class="btn btn-message" onclick="openMessageModal()">
                    💌 Send Wishes
                </button>
                <button class="btn btn-surprise" onclick="triggerSurprise()">
                    🎁 Surprise!
                </button>
            </div>
            
            <p style="margin-top:20px;color:#ccc;font-size:0.8em;">
                💡 Press SPACE to blow out the candles
            </p>
        </div>
    </div>

    <!-- Message Modal -->
    <div id="messageModal" class="modal">
        <div class="modal-content">
            <h2>💌 Birthday Wishes for Grace</h2>
            <textarea id="messageInput" placeholder="Write your birthday message for Grace here..."></textarea>
            <button class="btn btn-cake" onclick="sendMessage()">Send Wishes 💖</button>
            <button class="btn" onclick="closeMessageModal()" style="margin-top:10px; background:#ccc; color:#555;">Close</button>
            
            <div class="messages-wall" id="messagesWall">
                <p style="color:#aaa;text-align:center;">Messages will appear here...</p>
            </div>
        </div>
    </div>

    <!-- Surprise Modal -->
    <div id="surpriseModal" class="modal">
        <div class="modal-content">
            <span style="font-size:60px;">🎁</span>
            <h2>Surprise, Grace!</h2>
            <p style="font-size:1.2em;color:#555;line-height:1.8;">
                You are an incredible person, and your twenties are going to be absolutely amazing! 
                This is your time to shine brighter than ever before. 
                Dream big, laugh often, and never forget how special you are! 💖
            </p>
            <p style="font-size:3em;">🥳🎉💕</p>
            <button class="btn btn-surprise" onclick="closeSurprise()">Thank You! ✨</button>
        </div>
    </div>

    <!-- Hidden Audio -->
    <audio id="birthdaySong" loop>
        <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
    </audio>

    <script>
        // ==================== CREATE CANDLES ====================
        
        function createCandles() {
            const container = document.getElementById('candlesContainer');
            container.innerHTML = '';
            
            // Create 20 candles for Grace's 20th birthday
            for (let i = 0; i < 20; i++) {
                const candle = document.createElement('div');
                candle.className = 'candle';
                candle.style.transform = `rotate(${(i - 9.5) * 2}deg)`;
                
                // Add decorative stripe
                const stripe = document.createElement('div');
                stripe.className = 'candle-stripe';
                stripe.style.top = `${30 + Math.random() * 30}%`;
                candle.appendChild(stripe);
                
                // Add flame
                const flame = document.createElement('div');
                flame.className = 'flame';
                flame.id = `flame-${i}`;
                flame.style.animationDelay = `${Math.random() * 0.3}s`;
                candle.appendChild(flame);
                
                // Add number on select candles
                if (i === 0 || i === 19) {
                    const num = document.createElement('div');
                    num.className = 'number-candle';
                    num.textContent = i === 0 ? '2' : '0';
                    candle.appendChild(num);
                }
                
                container.appendChild(candle);
            }
        }
        
        // ==================== BLOW CANDLES ====================
        
        function blowCandles() {
            const flames = document.querySelectorAll('.flame');
            let blownCount = 0;
            
            flames.forEach((flame, index) => {
                setTimeout(() => {
                    flame.style.opacity = '0';
                    flame.style.transition = 'opacity 0.3s';
                    blownCount++;
                    
                    // Sparkle effect near each candle
                    const rect = flame.getBoundingClientRect();
                    createSparkle(rect.left + rect.width/2, rect.top);
                }, index * 50);
            });
            
            // Celebration when all candles are out
            setTimeout(() => {
                if (blownCount >= flames.length) {
                    celebrateBlowOut();
                }
            }, flames.length * 50 + 300);
            
            // Relight after delay
            setTimeout(() => {
                flames.forEach(flame => {
                    flame.style.opacity = '1';
                });
            }, 4000);
            
            playSound('blow');
        }
        
        function celebrateBlowOut() {
            // Burst of confetti
            for (let i = 0; i < 30; i++) {
                setTimeout(() => {
                    const x = 30 + Math.random() * 40;
                    const y = 30 + Math.random() * 20;
                    createSparkle(window.innerWidth * x / 100, window.innerHeight * y / 100);
                }, i * 30);
            }
            
            // Show celebration message
            const msg = document.createElement('div');
            msg.style.cssText = `
                position: fixed;
                top: 50%;
                left: 50%;
                transform: translate(-50%, -50%) scale(0);
                font-size: 2em;
                color: #f5576c;
                font-weight: bold;
                z-index: 1000;
                pointer-events: none;
                text-align: center;
                animation: popIn 0.8s cubic-bezier(0.68, -0.55, 0.265, 1.55) forwards;
            `;
            msg.innerHTML = '🎉 Happy 20th, Grace! 🎉<br><span style="font-size:0.6em;">Make a wish!</span>';
            
            const style = document.createElement('style');
            style.textContent = `
                @keyframes popIn {
                    0% { transform: translate(-50%, -50%) scale(0); opacity: 0; }
                    70% { transform: translate(-50%, -50%) scale(1.2); opacity: 1; }
                    100% { transform: translate(-50%, -50%) scale(1); opacity: 1; }
                }
            `;
            document.head.appendChild(style);
            document.body.appendChild(msg);
            
            setTimeout(() => {
                msg.remove();
                style.remove();
            }, 3000);
        }
        
        function createSparkle(x, y) {
            const sparkle = document.createElement('div');
            sparkle.className = 'sparkle';
            sparkle.textContent = ['✨', '💫', '⭐', '🌟', '💖'][Math.floor(Math.random() * 5)];
            sparkle.style.cssText = `
                left: ${x}px;
                top: ${y}px;
                font-size: ${20 + Math.random() * 35}px;
            `;
            document.body.appendChild(sparkle);
            
            setTimeout(() => sparkle.remove(), 800);
        }
        
        // ==================== BALLOONS ====================
        
        function createBalloons() {
            const container = document.getElementById('balloonsContainer');
            const balloonEmojis = ['🎈', '🎀', '💝', '🌸', '🦋', '💖', '✨', '🎉', '👑', '💫'];
            
            for (let i = 0; i < 18; i++) {
                const balloon = document.createElement('div');
                balloon.className = 'balloon';
                balloon.textContent = balloonEmojis[Math.floor(Math.random() * balloonEmojis.length)];
                balloon.style.left = `${Math.random() * 95}%`;
                balloon.style.fontSize = `${30 + Math.random() * 55}px`;
                balloon.style.animationDuration = `${7 + Math.random() * 10}s`;
                balloon.style.animationDelay = `${Math.random() * 6}s`;
                container.appendChild(balloon);
                
                setTimeout(() => {
                    balloon.remove();
                    createSingleBalloon();
                }, (7 + Math.random() * 10) * 1000);
            }
        }
        
        function createSingleBalloon() {
            const container = document.getElementById('balloonsContainer');
            const balloon = document.createElement('div');
            balloon.className = 'balloon';
            balloon.textContent = ['🎈', '🎀', '💝', '🌸', '💖', '👑'][Math.floor(Math.random() * 6)];
            balloon.style.left = `${Math.random() * 95}%`;
            balloon.style.fontSize = `${30 + Math.random() * 55}px`;
            balloon.style.animationDuration = `${7 + Math.random() * 10}s`;
            container.appendChild(balloon);
            
            setTimeout(() => {
                balloon.remove();
                createSingleBalloon();
            }, (7 + Math.random() * 10) * 1000);
        }
        
        // ==================== CONFETTI ====================
        
        function createConfetti() {
            const container = document.getElementById('confettiContainer');
            const colors = ['#f5576c', '#f093fb', '#fbc2eb', '#a18cd1', '#ffd1b3', '#ffd700', '#ff6b6b', '#c084fc'];
            
            setInterval(() => {
                for (let i = 0; i < 4; i++) {
                    const confetti = document.createElement('div');
                    confetti.className = 'confetti-piece';
                    confetti.style.left = `${Math.random() * 100}%`;
                    confetti.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
                    confetti.style.width = `${6 + Math.random() * 12}px`;
                    confetti.style.height = `${6 + Math.random() * 12}px`;
                    confetti.style.borderRadius = Math.random() > 0.5 ? '50%' : '2px';
                    confetti.style.animationDuration = `${3 + Math.random() * 5}s`;
                    confetti.style.animationDelay = `${Math.random() * 3}s`;
                    container.appendChild(confetti);
                    
                    setTimeout(() => confetti.remove(), 6000);
                }
            }, 400);
        }
        
        // ==================== COUNTDOWN ====================
        
        function updateCountdown() {
            // Set Grace's next birthday (20th birthday in 2025)
            const birthdayDate = new Date(2025, 5, 15); // June 15, 2025 - EDIT THIS
            
            function calculateTimeLeft() {
                const now = new Date();
                let targetDate = new Date(birthdayDate);
                
                if (targetDate < now) {
                    targetDate.setFullYear(targetDate.getFullYear() + 1);
                }
                
                const difference = targetDate - now;
                
                if (difference <= 0) {
                    return { days: 0, hours: 0, minutes: 0 };
                }
                
                return {
                    days: Math.floor(difference / (1000 * 60 * 60 * 24)),
                    hours: Math.floor((difference / (1000 * 60 * 60)) % 24),
                    minutes: Math.floor((difference / 1000 / 60) % 60)
                };
            }
            
            function update() {
                const timeLeft = calculateTime
