# Amo
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Crypto Miner: Space Adventure - Earn Points!</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 20px;
        }

        .game-container {
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
            padding: 30px;
            max-width: 800px;
            width: 100%;
        }

        .game-header {
            text-align: center;
            margin-bottom: 20px;
        }

        .game-title {
            font-size: 2.5em;
            color: #333;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.1);
        }

        .stats-bar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 15px;
            border-radius: 10px;
            margin-bottom: 20px;
            flex-wrap: wrap;
        }

        .stat-item {
            display: flex;
            align-items: center;
            gap: 8px;
            font-size: 1.1em;
            font-weight: bold;
        }

        .stat-icon {
            font-size: 1.5em;
        }

        .game-canvas {
            border: 3px solid #667eea;
            border-radius: 10px;
            display: block;
            margin: 0 auto;
            background: linear-gradient(180deg, #1a1a2e 0%, #16213e 100%);
            max-width: 100%;
        }

        .game-controls {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 15px;
            margin-top: 20px;
        }

        .btn {
            padding: 12px 24px;
            font-size: 1em;
            font-weight: bold;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s ease;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(0,0,0,0.3);
        }

        .btn-start {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
        }

        .btn-shop {
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
            color: white;
        }

        .btn-upgrade {
            background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);
            color: white;
        }

        .btn-info {
            background: linear-gradient(135deg, #43e97b 0%, #38f9d7 100%);
            color: white;
        }

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
            margin: 5% auto;
            padding: 30px;
            border-radius: 20px;
            max-width: 500px;
            width: 90%;
            max-height: 80vh;
            overflow-y: auto;
        }

        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }

        .close {
            font-size: 2em;
            cursor: pointer;
            color: #999;
        }

        .close:hover {
            color: #333;
        }

        .shop-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px;
            margin: 10px 0;
            background: #f5f5f5;
            border-radius: 10px;
            transition: all 0.3s;
        }

        .shop-item:hover {
            background: #e0e0e0;
            transform: translateX(5px);
        }

        .item-info {
            flex: 1;
        }

        .item-name {
            font-weight: bold;
            font-size: 1.1em;
            color: #333;
        }

        .item-desc {
            color: #666;
            font-size: 0.9em;
            margin-top: 5px;
        }

        .item-price {
            font-weight: bold;
            color: #667eea;
            margin-right: 15px;
        }

        .earn-methods {
            background: #f9f9f9;
            padding: 20px;
            border-radius: 10px;
            margin-top: 20px;
        }

        .earn-method {
            display: flex;
            align-items: center;
            padding: 10px;
            margin: 5px 0;
            background: white;
            border-radius: 8px;
            border-left: 4px solid #667eea;
        }

        .game-over-screen {
            text-align: center;
            padding: 20px;
        }

        .game-over-score {
            font-size: 3em;
            color: #667eea;
            font-weight: bold;
            margin: 20px 0;
        }

        .combo-indicator {
            position: absolute;
            color: #ffd700;
            font-weight: bold;
            font-size: 1.5em;
            pointer-events: none;
            animation: floatUp 1s ease-out;
        }

        @keyframes floatUp {
            from {
                opacity: 1;
                transform: translateY(0);
            }
            to {
                opacity: 0;
                transform: translateY(-50px);
            }
        }

        @media (max-width: 600px) {
            .stats-bar {
                flex-direction: column;
                gap: 10px;
            }
            
            .game-title {
                font-size: 1.8em;
            }
        }
    </style>
</head>
<body>
    <div class="game-container">
        <div class="game-header">
            <h1 class="game-title">🚀 Crypto Miner: Space Adventure</h1>
            <p>Collect space gems and earn virtual coins!</p>
        </div>

        <div class="stats-bar">
            <div class="stat-item">
                <span class="stat-icon">💰</span>
                <span>Coins: <span id="coins">0</span></span>
            </div>
            <div class="stat-item">
                <span class="stat-icon">⭐</span>
                <span>Score: <span id="score">0</span></span>
            </div>
            <div class="stat-item">
                <span class="stat-icon">🎯</span>
                <span>Level: <span id="level">1</span></span>
            </div>
            <div class="stat-item">
                <span class="stat-icon">💎</span>
                <span>Gems: <span id="gems">0</span></span>
            </div>
        </div>

        <canvas id="gameCanvas" class="game-canvas" width="700" height="400"></canvas>

        <div class="game-controls">
            <button class="btn btn-start" onclick="startGame()">🎮 Start Game</button>
            <button class="btn btn-shop" onclick="openShop()">🛒 Shop</button>
            <button class="btn btn-upgrade" onclick="openUpgrades()">⚡ Upgrades</button>
            <button class="btn btn-info" onclick="openEarnInfo()">💡 How to Earn</button>
        </div>
    </div>

    <!-- Shop Modal -->
    <div id="shopModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h2>🛒 Shop</h2>
                <span class="close" onclick="closeShop()">&times;</span>
            </div>
            <div id="shopItems"></div>
        </div>
    </div>

    <!-- Upgrades Modal -->
    <div id="upgradesModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h2>⚡ Upgrades</h2>
                <span class="close" onclick="closeUpgrades()">&times;</span>
            </div>
            <div id="upgradeItems"></div>
        </div>
    </div>

    <!-- How to Earn Modal -->
    <div id="earnModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h2>💡 How to Earn Virtual Coins</h2>
                <span class="close" onclick="closeEarnInfo()">&times;</span>
            </div>
            <div class="earn-methods">
                <h3>🎮 In-Game Methods:</h3>
                <div class="earn-method">
                    <span>💎 Collect space gems during gameplay</span>
                </div>
                <div class="earn-method">
                    <span>⭐ Reach high scores for bonus coins</span>
                </div>
                <div class="earn-method">
                    <span>🎯 Complete daily challenges</span>
                </div>
                <div class="earn-method">
                    <span>🏆 Win tournaments and events</span>
                </div>
                
                <h3 style="margin-top: 20px;">💳 For Real Integration:</h3>
                <div class="earn-method" style="background: #fff3cd;">
                    <span>🔌 Integrate payment gateways (Stripe, PayPal)</span>
                </div>
                <div class="earn-method" style="background: #fff3cd;">
                    <span>📱 Add rewarded video ads</span>
                </div>
                <div class="earn-method" style="background: #fff3cd;">
                    <span>🏪 In-app purchases for virtual items</span>
                </div>
            </div>
        </div>
    </div>

    <!-- Game Over Modal -->
    <div id="gameOverModal" class="modal">
        <div class="modal-content">
            <div class="game-over-screen">
                <h2>🎮 Game Over!</h2>
                <div class="game-over-score">
                    <span id="finalScore">0</span> points
                </div>
                <p>Coins earned: <span id="coinsEarned">0</span> 💰</p>
                <p>Gems collected: <span id="gemsCollected">0</span> 💎</p>
                <button class="btn btn-start" onclick="restartGame()" style="margin-top: 20px;">
                    🔄 Play Again
                </button>
            </div>
        </div>
    </div>

    <script>
        // Game State
        const canvas = document.getElementById('gameCanvas');
        const ctx = canvas.getContext('2d');

        let gameRunning = false;
        let score = 0;
        let coins = 0;
        let gems = 0;
        let level = 1;
        let combo = 1;
        let lives = 3;

        // Player
        let player = {
            x: 350,
            y: 350,
            width: 40,
            height: 40,
            speed: 5,
            color: '#00ff00'
        };

        // Game objects
        let collectibles = [];
        let obstacles = [];
        let particles = [];

        // Upgrades
        let upgrades = {
            speed: { level: 1, cost: 100, name: 'Speed Boost' },
            magnet: { level: 1, cost: 150, name: 'Coin Magnet' },
            shield: { level: 0, cost: 200, name: 'Shield' },
            multiplier: { level: 1, cost: 250, name: 'Score Multiplier' }
        };

        // Shop items
        let shopItems = [
            { id: 1, name: 'Coin Pack', desc: '100 virtual coins', price: 1, coins: 100 },
            { id: 2, name: 'Gem Pack', desc: '50 gems', price: 2, coins: 0, gems: 50 },
            { id: 3, name: 'Lives Pack', desc: '+3 extra lives', price: 1, lives: 3 },
            { id: 4, name: 'Premium Pack', desc: '500 coins + 100 gems', price: 5, coins: 500, gems: 100 }
        ];

        // Controls
        let keys = {};

        document.addEventListener('keydown', (e) => {
            keys[e.key] = true;
            if (!gameRunning && e.key === ' ') {
                startGame();
            }
        });

        document.addEventListener('keyup', (e) => {
            keys[e.key] = false;
        });

        // Touch controls for mobile
        let touchX = null;
        canvas.addEventListener('touchmove', (e) => {
            e.preventDefault();
            const rect = canvas.getBoundingClientRect();
            touchX = e.touches[0].clientX - rect.left;
        });

        // Game Loop
        function gameLoop() {
            if (!gameRunning) return;

            ctx.clearRect(0, 0, canvas.width, canvas.height);

            // Draw background
            drawBackground();

            // Update player position
            updatePlayer();

            // Update and draw collectibles
            updateCollectibles();

            // Update and draw obstacles
            updateObstacles();

            // Update and draw particles
            updateParticles();

            // Update UI
            document.getElementById('score').textContent = score;
            document.getElementById('coins').textContent = coins;
            document.getElementById('level').textContent = level;
            document.getElementById('gems').textContent = gems;

            // Increase difficulty
            if (score > level * 100) {
                level++;
                player.speed += 0.5;
            }

            requestAnimationFrame(gameLoop);
        }

        function drawBackground() {
            // Starfield
            for (let i = 0; i < 50; i++) {
                const x = (i * 137 + Date.now() * 0.01) % canvas.width;
                const y = (i * 97) % canvas.height;
                ctx.fillStyle = '#ffffff';
                ctx.fillRect(x, y, 2, 2);
            }
        }

        function updatePlayer() {
            // Keyboard controls
            if (keys['ArrowLeft'] || keys['a']) player.x -= player.speed;
            if (keys['ArrowRight'] || keys['d']) player.x += player.speed;
            if (keys['ArrowUp'] || keys['w']) player.y -= player.speed;
            if (keys['ArrowDown'] || keys['s']) player.y += player.speed;

            // Touch controls
            if (touchX !== null) {
                player.x += (touchX - player.x) * 0.1;
            }

            // Boundaries
            player.x = Math.max(0, Math.min(canvas.width - player.width, player.x));
            player.y = Math.max(0, Math.min(canvas.height - player.height, player.y));

            // Draw player
            ctx.fillStyle = player.color;
            ctx.shadowBlur = 20;
            ctx.shadowColor = player.color;
            ctx.fillRect(player.x, player.y, player.width, player.height);
            ctx.shadowBlur = 0;

            // Draw player emoji
            ctx.font = '30px Arial';
            ctx.fillText('🚀', player.x + 5, player.y + 33);
        }

        function updateCollectibles() {
            // Spawn collectibles
            if (Math.random() < 0.02 + level * 0.005) {
                collectibles.push({
                    x: Math.random() * (canvas.width - 30),
                    y: -30,
                    width: 30,
                    height: 30,
                    speed: 2 + level * 0.5,
                    type: Math.random() < 0.3 ? 'gem' : 'coin',
                    wobble: Math.random() * Math.PI * 2
                });
            }

            // Update collectibles
            collectibles = collectibles.filter(item => {
                item.y += item.speed;
                item.x += Math.sin(item.wobble + Date.now() * 0.003) * 2;

                // Check collision with player
                if (checkCollision(player, item)) {
                    if (item.type === 'coin') {
                        coins += 10 * upgrades.multiplier.level;
                        score += 10 * upgrades.multiplier.level;
                    } else {
                        gems += 5;
                        score += 25 * upgrades.multiplier.level;
                    }
                    
                    // Create particle effect
                    createParticles(item.x, item.y, item.type === 'gem' ? '#ffd700' : '#ffa500');
                    
                    // Combo system
                    combo++;
                    if (combo % 10 === 0) {
                        coins += 50 * combo;
                        showCombo(item.x, item.y);
                    }

                    return false;
                }

                // Remove if off screen
                if (item.y > canvas.height) {
                    combo = 1;
                    return false;
                }

                // Draw collectible
                ctx.font = '25px Arial';
                ctx.fillText(item.type === 'gem' ? '💎' : '💰', item.x, item.y);

                return true;
            });
        }

        function updateObstacles() {
            // Spawn obstacles
            if (Math.random() < 0.01 + level * 0.003 && upgrades.shield.level === 0) {
                obstacles.push({
                    x: Math.random() * (canvas.width - 40),
                    y: -40,
                    width: 40,
                    height: 40,
                    speed: 1.5 + level * 0.3
                });
            }

            // Update obstacles
            obstacles = obstacles.filter(obstacle => {
                obstacle.y += obstacle.speed;

                // Check collision with player
                if (checkCollision(player, obstacle)) {
                    if (upgrades.shield.level > 0) {
                        upgrades.shield.level--;
                        createParticles(obstacle.x, obstacle.y, '#00ffff');
                    } else {
                        lives--;
                        createParticles(obstacle.x, obstacle.y, '#ff0000');
                        
                        if (lives <= 0) {
                            gameOver();
                        }
                    }
                    return false;
                }

                // Remove if off screen
                if (obstacle.y > canvas.height) return false;

                // Draw obstacle
                ctx.font = '35px Arial';
                ctx.fillText('☄️', obstacle.x, obstacle.y);

                return true;
            });
        }

        function createParticles(x, y, color) {
            for (let i = 0; i < 10; i++) {
                particles.push({
                    x: x,
                    y: y,
                    vx: (Math.random() - 0.5) * 5,
                    vy: (Math.random() - 0.5) * 5,
                    life: 1,
                    color: color
                });
            }
        }

        function updateParticles() {
            particles = particles.filter(p => {
                p.x += p.vx;
                p.y += p.vy;
                p.life -= 0.02;

                ctx.fillStyle = p.color;
                ctx.globalAlpha = p.life;
                ctx.fillRect(p.x, p.y, 5, 5);
                ctx.globalAlpha = 1;

                return p.life > 0;
            });
        }

        function showCombo(x, y) {
            const indicator = document.createElement('div');
            indicator.className = 'combo-indicator';
            indicator.style.left = x + 'px';
            indicator.style.top = y + 'px';
            indicator.textContent = `${combo}x COMBO!`;
            document.body.appendChild(indicator);
            
            setTimeout(() => indicator.remove(), 1000);
        }

        function checkCollision(rect1, rect2) {
            return rect1.x < rect2.x + rect2.width &&
                   rect1.x + rect1.width > rect2.x &&
                   rect1.y < rect2.y + rect2.height &&
                   rect1.y + rect1.height > rect2.y;
        }

        function startGame() {
            gameRunning = true;
            score = 0;
            coins = 0;
            gems = 0;
            level = 1;
            combo = 1;
            lives = 3;
            collectibles = [];
            obstacles = [];
            particles = [];
            player.x = 350;
            player.y = 350;
            
            document.getElementById('gameOverModal').style.display = 'none';
            gameLoop();
        }

        function gameOver() {
            gameRunning = false;
            
            // Calculate earnings
            const coinsEarned = Math.floor(score / 10);
            coins += coinsEarned;
            
            document.getElementById('finalScore').textContent = score;
            document.getElementById('coinsEarned').textContent = coinsEarned;
            document.getElementById('gemsCollected').textContent = gems;
            document.getElementById('gameOverModal').style.display = 'block';
            
            // Save to localStorage
            saveGameData();
        }

        function restartGame() {
            startGame();
        }

        function saveGameData() {
            const gameData = {
                coins: coins,
                gems: gems,
                highScore: Math.max(score, parseInt(localStorage.getItem('highScore') || 0)),
                upgrades: upgrades,
                lastSaved: new Date().toISOString()
            };
            localStorage.setItem('gameData', JSON.stringify(gameData));
        }

        function loadGameData() {
            const saved = localStorage.getItem('gameData');
            if (saved) {
                const data = JSON.parse(saved);
                coins = data.coins || 0;
                gems = data.gems || 0;
                upgrades = data.upgrades || upgrades;
            }
        }

        // Shop Functions
        function openShop() {
            const shopDiv = document.getElementById('shopItems');
            shopDiv.innerHTML = '';
            
            shopItems.forEach(item => {
                const itemDiv = document.createElement('div');
                itemDiv.className = 'shop-item';
                itemDiv.innerHTML = `
                    <div class="item-info">
                        <div class="item-name">${item.name}</div>
                        <div class="item-desc">${item.desc}</div>
                    </div>
                    <div class="item-price">$${item.price}</div>
                    <button class="btn btn-shop" onclick="purchaseItem(${item.id})">
                        Buy
                    </button>
                `;
                shopDiv.appendChild(itemDiv);
            });
            
            document.getElementById('shopModal').style.display = 'block';
        }

        function purchaseItem(itemId) {
            const item = shopItems.find(i => i.id === itemId);
            if (!item) return;

            // Simulate purchase (in real app, integrate payment here)
            if (confirm(`Simulate purchase of ${item.name} for $${item.price}?`)) {
                // Add virtual items
                if (item.coins) coins += item.coins;
                if (item.gems) gems += item.gems;
                if (item.lives) lives += item.lives;
                
                saveGameData();
                alert(`Purchased ${item.name}! Items added to your account.`);
            }
        }

        // Upgrade Functions
        function openUpgrades() {
            const upgradeDiv = document.getElementById('upgradeItems');
            upgradeDiv.innerHTML = '';
            
            Object.entries(upgrades).forEach(([key, upgrade]) => {
                const nextCost = upgrade.cost * (upgrade.level + 1);
                const itemDiv = document.createElement('div');
                itemDiv.className = 'shop-item';
                itemDiv.innerHTML = `
                    <div class="item-info">
                        <div class="item-name">${upgrade.name} (Level ${upgrade.level})</div>
                        <div class="item-desc">Next upgrade cost: ${nextCost} coins</div>
                    </div>
                    <button class="btn btn-upgrade" onclick="purchaseUpgrade('${key}')">
                        Upgrade (${nextCost} 💰)
                    </button>
                `;
                upgradeDiv.appendChild(itemDiv);
            });
            
            document.getElementById('upgradesModal').style.display = 'block';
        }

        function purchaseUpgrade(upgradeKey) {
            const upgrade = upgrades[upgradeKey];
            const cost = upgrade.cost * (upgrade.level + 1);
            
            if (coins >= cost) {
                coins -= cost;
                upgrade.level++;
                
                // Apply upgrade effects
                switch(upgradeKey) {
                    case 'speed':
                        player.speed += 1;
                        break;
                    case 'magnet':
                        // Implement magnet effect
                        break;
                    case 'multiplier':
                        // Multiplier already applied in collection
                        break;
                }
                
                saveGameData();
                openUpgrades(); // Refresh display
            } else {
                alert('Not enough coins! Keep playing to earn more.');
            }
        }

        function openEarnInfo() {
            document.getElementById('earnModal').style.display = 'block';
        }

        // Close modals
        function closeShop() { document.getElementById('shopModal').style.display = 'none'; }
        function closeUpgrades() { document.getElementById('upgradesModal').style.display = 'none'; }
        function closeEarnInfo() { document.getElementById('earnModal').style.display = 'none'; }

        // Close modals when clicking outside
        window.onclick = function(event) {
            const modals = document.getElementsByClassName('modal');
            for (let modal of modals) {
                if (event.target === modal) {
                    modal.style.display = 'none';
                }
            }
        }

        // Initialize
        loadGameData();
        document.getElementById('coins').textContent = coins;
    </script>
</body>
</html>
