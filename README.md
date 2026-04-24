# Amo
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>🎂 Happy Birthday!</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            overflow-x: hidden;
            position: relative;
        }

        /* Floating Balloons Background */
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
            width: 10px;
            height: 10px;
            top: -10px;
            animation: confettiFall linear infinite;
        }

        @keyframes confettiFall {
            0% {
                transform: translateY(0) rotate(0deg);
                opacity: 1;
            }
            100% {
                transform: translateY(100vh) rotate(720deg);
                opacity: 0;
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
            background: rgba(255, 255, 255, 0.95);
            border-radius: 30px;
            padding: 40px;
            max-width: 600px;
            width: 100%;
            box-shadow: 0 30px 60px rgba(0, 0, 0, 0.3);
            text-align: center;
            animation: slideIn 1s ease-out;
            backdrop-filter: blur(10px);
        }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateY(50px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .birthday-emoji {
            font-size: 80px;
            animation: bounce 1s infinite;
        }

        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-20px); }
        }

        .title {
            font-size: 3em;
            color: #333;
            margin: 20px 0 10px 0;
            background: linear-gradient(135deg, #667eea, #764ba2, #f093fb);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .friend-name {
            font-size: 2em;
            color: #764ba2;
            margin-bottom: 10px;
            font-weight: bold;
        }

        .message {
            font-size: 1.2em;
            color: #666;
            line-height: 1.6;
            margin: 20px 0;
            font-style: italic;
        }

        .age-badge {
            display: inline-block;
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
            padding: 10px 30px;
            border-radius: 50px;
            font-size: 1.2em;
            font-weight: bold;
            margin: 15px 0;
            box-shadow: 0 5px 15px rgba(102, 126, 234, 0.4);
        }

        /* Photo Gallery */
        .photo-gallery {
            display: flex;
            gap: 10px;
            justify-content: center;
            flex-wrap: wrap;
            margin: 25px 0;
        }

        .photo-placeholder {
            width: 120px;
            height: 120px;
            border-radius: 15px;
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 50px;
            color: white;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
            transition: transform 0.3s;
            cursor: pointer;
            position: relative;
            overflow: hidden;
        }

        .photo-placeholder:hover {
            transform: scale(1.1) rotate(5deg);
        }

        .photo-placeholder img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            border-radius: 15px;
        }

        .photo-caption {
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            background: rgba(0, 0, 0, 0.6);
            color: white;
            font-size: 0.7em;
            padding: 5px;
            border-radius: 0 0 15px 15px;
        }

        /* Buttons */
        .button-group {
            display: flex;
            gap: 15px;
            flex-wrap: wrap;
            justify-content: center;
            margin-top: 25px;
        }

        .btn {
            padding: 15px 30px;
            font-size: 1.1em;
            font-weight: bold;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s;
            text-transform: uppercase;
            letter-spacing: 1px;
            position: relative;
            overflow: hidden;
        }

        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.3);
        }

        .btn:active {
            transform: translateY(-1px);
        }

        .btn-cake {
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
            color: white;
        }

        .btn-music {
            background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);
            color: white;
        }

        .btn-message {
            background: linear-gradient(135deg, #43e97b 0%, #38f9d7 100%);
            color: white;
        }

        /* Countdown */
        .countdown {
            display: flex;
            gap: 15px;
            justify-content: center;
            margin: 20px 0;
        }

        .countdown-item {
            background: rgba(102, 126, 234, 0.1);
            padding: 15px;
            border-radius: 15px;
            min-width: 70px;
        }

        .countdown-number {
            font-size: 2em;
            font-weight: bold;
            color: #667eea;
        }

        .countdown-label {
            font-size: 0.8em;
            color: #666;
            text-transform: uppercase;
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
            background: rgba(0, 0, 0, 0.8);
            animation: fadeIn 0.3s;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        .modal-content {
            background: white;
            margin: 10% auto;
            padding: 30px;
            border-radius: 20px;
            max-width: 500px;
            width: 90%;
            text-align: center;
        }

        .modal textarea {
            width: 100%;
            height: 150px;
            padding: 15px;
            border: 2px solid #667eea;
            border-radius: 15px;
            font-size: 1em;
            margin: 20px 0;
            resize: vertical;
            font-family: inherit;
        }

        /* Cake Animation */
        .cake-container {
            position: relative;
            margin: 30px auto;
            width: 200px;
            height: 200px;
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
            border-radius: 10px;
        }

        .cake-layer-1 {
            width: 180px;
            height: 50px;
            background: linear-gradient(135deg, #f5576c, #f093fb);
            bottom: 0;
        }

        .cake-layer-2 {
            width: 140px;
            height: 50px;
            background: linear-gradient(135deg, #f093fb, #667eea);
            bottom: 40px;
        }

        .cake-layer-3 {
            width: 100px;
            height: 50px;
            background: linear-gradient(135deg, #667eea, #764ba2);
            bottom: 80px;
        }

        .candle {
            position: absolute;
            bottom: 130px;
            left: 50%;
            transform: translateX(-50%);
            width: 8px;
            height: 40px;
            background: #ffd700;
            border-radius: 5px;
        }

        .flame {
            position: absolute;
            top: -20px;
            left: 50%;
            transform: translateX(-50%);
            width: 15px;
            height: 25px;
            background: #ff6b35;
            border-radius: 50% 50% 20% 20%;
            animation: flicker 0.5s infinite alternate;
        }

        @keyframes flicker {
            from { transform: translateX(-50%) scale(1); }
            to { transform: translateX(-50%) scale(1.1); }
        }

        /* Responsive */
        @media (max-width: 600px) {
            .card {
                padding: 25px;
                margin: 10px;
            }
            .title {
                font-size: 2em;
            }
            .friend-name {
                font-size: 1.5em;
            }
            .photo-placeholder {
                width: 80px;
                height: 80px;
                font-size: 35px;
            }
            .btn {
                padding: 12px 20px;
                font-size: 0.9em;
            }
        }
    </style>
</head>
<body>
    <!-- Animated Background Elements -->
    <div class="balloons-container" id="balloonsContainer"></div>
    <div class="confetti-container" id="confettiContainer"></div>

    <!-- Main Content -->
    <div class="main-content">
        <div class="card" id="mainCard">
            <!-- Birthday Emoji -->
            <div class="birthday-emoji">🎉</div>
            
            <!-- Title -->
            <h1 class="title">Happy Birthday!</h1>
            
            <!-- Friend's Name - EDIT THIS -->
            <h2 class="friend-name" id="friendName">[Your Friend's Name]</h2>
            
            <!-- Age Badge -->
            <div class="age-badge" id="ageBadge">🎂 Today's Your Day!</div>
            
            <!-- Animated Cake -->
            <div class="cake-container">
                <div class="cake">
                    <div class="cake-layer cake-layer-1"></div>
                    <div class="cake-layer cake-layer-2"></div>
                    <div class="cake-layer cake-layer-3"></div>
                    <div class="candle">
                        <div class="flame" id="flame"></div>
                    </div>
                </div>
            </div>
            
            <!-- Personal Message -->
            <p class="message" id="personalMessage">
                Wishing you the happiest of birthdays! May your day be filled with joy, 
                laughter, and all the things that make you smile. You deserve nothing 
                but the best! 🎈
            </p>
            
            <!-- Photo Gallery -->
            <div class="photo-gallery" id="photoGallery">
                <div class="photo-placeholder" onclick="showPhotoMessage('Best Memories! 📸')">
                    🖼️
                    <div class="photo-caption">Memory 1</div>
                </div>
                <div class="photo-placeholder" onclick="showPhotoMessage('Our Adventures! 🌟')">
                    🎨
                    <div class="photo-caption">Memory 2</div>
                </div>
                <div class="photo-placeholder" onclick="showPhotoMessage('Good Times! 🎊')">
                    📷
                    <div class="photo-caption">Memory 3</div>
                </div>
            </div>
            
            <!-- Countdown to Next Birthday -->
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
                    <div class="countdown-label">Minutes</div>
                </div>
            </div>
            
            <!-- Action Buttons -->
            <div class="button-group">
                <button class="btn btn-cake" onclick="blowCandles()">
                    🎂 Blow Candles
                </button>
                <button class="btn btn-music" onclick="toggleMusic()">
                    🎵 Play Song
                </button>
                <button class="btn btn-message" onclick="openMessageModal()">
                    💌 Leave Message
                </button>
            </div>
        </div>
    </div>

    <!-- Message Modal -->
    <div id="messageModal" class="modal">
        <div class="modal-content">
            <h2>💌 Leave a Birthday Message</h2>
            <textarea id="messageInput" placeholder="Write your birthday wishes here..."></textarea>
            <button class="btn btn-message" onclick="sendMessage()">Send Message 🎈</button>
            <button class="btn" onclick="closeMessageModal()" style="margin-top:10px; background:#999; color:white;">Close</button>
        </div>
    </div>

    <!-- Hidden Audio Element -->
    <audio id="birthdaySong" loop>
        <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
    </audio>

    <script>
        // ==================== CONFIGURATION - EDIT THESE VALUES ====================
        
        // Your friend's information
        const friendName = "Alex"; // Change to your friend's name
        const friendAge = 25; // Change to your friend's age (or set to null)
        const birthdayDate = new Date(2025, 5, 15); // Year, Month (0-11), Day - Set their next birthday
        
        // Personal message
        const personalMessage = "Wishing you the happiest of birthdays! May your day be filled with joy, laughter, and all the things that make you smile. You deserve nothing but the best! 🎈";
        
        // Photo URLs (replace with actual image URLs or leave as null for placeholders)
        const photoUrls = [
            null, // Replace with 'https://example.com/photo1.jpg'
            null, // Replace with 'https://example.com/photo2.jpg'
            null  // Replace with 'https://example.com/photo3.jpg'
        ];
        
        // Photo captions
        const photoCaptions = [
            "Best Memories! 📸",
            "Our Adventures! 🌟",
            "Good Times! 🎊"
        ];
        
        // ==================== INITIALIZATION ====================
        
        // Update friend's name
        document.getElementById('friendName').textContent = friendName;
        
        // Update age badge if provided
        if (friendAge) {
            document.getElementById('ageBadge').textContent = `🎂 Turning ${friendAge}!`;
        }
        
        // Update personal message
        document.getElementById('personalMessage').textContent = personalMessage;
        
        // Update photos if URLs provided
        const photoElements = document.querySelectorAll('.photo-placeholder');
        photoElements.forEach((element, index) => {
            if (photoUrls[index]) {
                const img = document.createElement('img');
                img.src = photoUrls[index];
                img.alt = `Memory ${index + 1}`;
                element.innerHTML = '';
                element.appendChild(img);
                
                const caption = document.createElement('div');
                caption.className = 'photo-caption';
                caption.textContent = photoCaptions[index];
                element.appendChild(caption);
            }
        });
        
        // ==================== BALLOONS ====================
        
        function createBalloons() {
            const container = document.getElementById('balloonsContainer');
            const balloonEmojis = ['🎈', '🎉', '🎊', '🎀', '💝', '🌟', '✨', '🎁'];
            
            for (let i = 0; i < 15; i++) {
                const balloon = document.createElement('div');
                balloon.className = 'balloon';
                balloon.textContent = balloonEmojis[Math.floor(Math.random() * balloonEmojis.length)];
                balloon.style.left = `${Math.random() * 100}%`;
                balloon.style.fontSize = `${30 + Math.random() * 50}px`;
                balloon.style.animationDuration = `${6 + Math.random() * 8}s`;
                balloon.style.animationDelay = `${Math.random() * 5}s`;
                container.appendChild(balloon);
                
                // Remove and recreate balloons
                setTimeout(() => {
                    balloon.remove();
                    createBalloons();
                }, (6 + Math.random() * 8) * 1000);
            }
        }
        
        // ==================== CONFETTI ====================
        
        function createConfetti() {
            const container = document.getElementById('confettiContainer');
            const colors = ['#ff6b6b', '#4ecdc4', '#45b7d1', '#96ceb4', '#ffeaa7', '#dfe6e9', '#fd79a8', '#a29bfe'];
            
            setInterval(() => {
                for (let i = 0; i < 5; i++) {
                    const confetti = document.createElement('div');
                    confetti.className = 'confetti-piece';
                    confetti.style.left = `${Math.random() * 100}%`;
                    confetti.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
                    confetti.style.width = `${5 + Math.random() * 10}px`;
                    confetti.style.height = `${5 + Math.random() * 10}px`;
                    confetti.style.animationDuration = `${3 + Math.random() * 4}s`;
                    confetti.style.animationDelay = `${Math.random() * 2}s`;
                    container.appendChild(confetti);
                    
                    // Remove confetti after animation
                    setTimeout(() => confetti.remove(), 5000);
                }
            }, 500);
        }
        
        // ==================== COUNTDOWN ====================
        
        function updateCountdown() {
            function calculateTimeLeft() {
                const now = new Date();
                let targetDate = new Date(birthdayDate);
                
                // If birthday has passed this year, set to next year
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
                const timeLeft = calculateTimeLeft();
                document.getElementById('days').textContent = timeLeft.days;
                document.getElementById('hours').textContent = timeLeft.hours;
                document.getElementById('minutes').textContent = timeLeft.minutes;
            }
            
            update();
            setInterval(update, 60000);
        }
        
        // ==================== INTERACTIVE FEATURES ====================
        
        function blowCandles() {
            const flame = document.getElementById('flame');
            flame.style.opacity = '0';
            flame.style.transition = 'opacity 0.5s';
            
            // Create sparkle effect
            for (let i = 0; i < 15; i++) {
                setTimeout(() => {
                    createSparkle();
                }, i * 100);
            }
            
            // Relight after 3 seconds
            setTimeout(() => {
                flame.style.opacity = '1';
            }, 3000);
            
            // Play sound effect
            playSound('blow');
        }
        
        function createSparkle() {
            const sparkle = document.createElement('div');
            sparkle.textContent = '✨';
            sparkle.style.cssText = `
                position: fixed;
                left: 50%;
                top: 40%;
                font-size: 30px;
                pointer-events: none;
                animation: sparkleAnimation 1s ease-out forwards;
                z-index: 1000;
            `;
            
            const style = document.createElement('style');
            style.textContent = `
                @keyframes sparkleAnimation {
                    0% {
                        opacity: 1;
                        transform: translate(0, 0) scale(1);
                    }
                    100% {
                        opacity: 0;
                        transform: translate(${(Math.random() - 0.5) * 200}px, ${-Math.random() * 200}px) scale(0);
                    }
                }
            `;
            document.head.appendChild(style);
            document.body.appendChild(sparkle);
            
            setTimeout(() => {
                sparkle.remove();
                style.remove();
            }, 1000);
        }
        
        let musicPlaying = false;
        function toggleMusic() {
            const audio = document.getElementById('birthdaySong');
            if (musicPlaying) {
                audio.pause();
                musicPlaying = false;
            } else {
                audio.play().catch(e => console.log('Audio play failed:', e));
                musicPlaying = true;
            }
        }
        
        function playSound(type) {
            // Simple sound using Web Audio API
            try {
                const audioContext = new (window.AudioContext || window.webkitAudioContext)();
                const oscillator = audioContext.createOscillator();
                const gainNode = audioContext.createGain();
                
                oscillator.connect(gainNode);
                gainNode.connect(audioContext.destination);
                
                if (type === 'blow') {
                    oscillator.frequency.setValueAtTime(800, audioContext.currentTime);
                    oscillator.frequency.exponentialRampToValueAtTime(200, audioContext.currentTime + 0.5);
                    gainNode.gain.setValueAtTime(0.3, audioContext.currentTime);
                    gainNode.gain.exponentialRampToValueAtTime(0.01, audioContext.currentTime + 0.5);
                }
                
                oscillator.start(audioContext.currentTime);
                oscillator.stop(audioContext.currentTime + 0.5);
            } catch (e) {
                console.log('Sound not supported');
            }
        }
        
        function showPhotoMessage(message) {
            alert(message);
        }
        
        // ==================== MESSAGE SYSTEM ====================
        
        function openMessageModal() {
            document.getElementById('messageModal').style.display = 'block';
        }
        
        function closeMessageModal() {
            document.getElementById('messageModal').style.display = 'none';
        }
        
        function sendMessage() {
            const message = document.getElementById('messageInput').value;
            if (message.trim()) {
                // Store message in localStorage
                const messages = JSON.parse(localStorage.getItem('birthdayMessages') || '[]');
                messages.push({
                    text: message,
                    timestamp: new Date().toISOString()
                });
                localStorage.setItem('birthdayMessages', JSON.stringify(messages));
                
                // Show confirmation
                alert('Your birthday message has been saved! 🎉');
                document.getElementById('messageInput').value = '';
                closeMessageModal();
            } else {
                alert('Please write a message first! 💌');
            }
        }
        
        // Close modal when clicking outside
        window.onclick = function(event) {
            const modal = document.getElementById('messageModal');
            if (event.target === modal) {
                closeMessageModal();
            }
        }
        
        // ==================== START EVERYTHING ====================
        
        createBalloons();
        createConfetti();
        updateCountdown();
        
        // Add keyboard shortcut for candles
        document.addEventListener('keydown', (e) => {
            if (e.key === ' ' || e.code === 'Space') {
                e.preventDefault();
                blowCandles();
            }
        });
        
        console.log('🎂 Happy Birthday App is Ready!');
        console.log('💡 Tips:');
        console.log('  - Press SPACE to blow out the candles');
        console.log('  - Edit the configuration at the top of the script');
        console.log('  - Replace photo URLs with real images');
        console.log('  - Share this page with your friend!');
    </script>
</body>
</html>
