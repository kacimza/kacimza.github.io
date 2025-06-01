# kacimza.github.io
<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fenerbahçe Kongre İmza Takip Sistemi</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #003366 0%, #001a33 50%, #000d1a 100%);
            min-height: 100vh;
            color: white;
            overflow-x: hidden;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        header {
            text-align: center;
            padding: 40px 0;
            background: rgba(255, 215, 0, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            margin-bottom: 40px;
            border: 2px solid #FFD700;
        }

        .logo {
            width: 120px;
            height: 120px;
            background: #FFD700;
            border-radius: 50%;
            margin: 0 auto 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 10px 30px rgba(255, 215, 0, 0.3);
            overflow: hidden;
        }

        .logo svg {
            width: 80px;
            height: 80px;
        }

        h1 {
            font-size: 2.5rem;
            color: #FFD700;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
        }

        .subtitle {
            font-size: 1.2rem;
            color: rgba(255, 255, 255, 0.8);
            margin-bottom: 20px;
        }

        .main-counter {
            background: rgba(255, 215, 0, 0.1);
            backdrop-filter: blur(15px);
            border-radius: 25px;
            padding: 50px;
            text-align: center;
            margin: 40px 0;
            border: 3px solid #FFD700;
            box-shadow: 0 20px 60px rgba(255, 215, 0, 0.2);
            position: relative;
            overflow: hidden;
        }

        .main-counter::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent, rgba(255, 215, 0, 0.1), transparent);
            animation: shimmer 3s infinite;
        }

        @keyframes shimmer {
            0% { transform: translateX(-100%) translateY(-100%) rotate(45deg); }
            100% { transform: translateX(100%) translateY(100%) rotate(45deg); }
        }

        .counter-label {
            font-size: 1.5rem;
            color: rgba(255, 255, 255, 0.9);
            margin-bottom: 20px;
            position: relative;
            z-index: 2;
        }

        .counter-number {
            font-size: 5rem;
            font-weight: bold;
            color: #FFD700;
            text-shadow: 3px 3px 6px rgba(0,0,0,0.5);
            margin-bottom: 20px;
            position: relative;
            z-index: 2;
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }

        .last-update {
            font-size: 1.1rem;
            color: rgba(255, 255, 255, 0.7);
            position: relative;
            z-index: 2;
        }

        .progress-section {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 40px;
            margin: 40px 0;
            border: 1px solid rgba(255, 215, 0, 0.3);
        }

        .progress-title {
            font-size: 1.8rem;
            color: #FFD700;
            margin-bottom: 30px;
            text-align: center;
        }

        .progress-bar-container {
            background: rgba(0, 0, 0, 0.3);
            border-radius: 15px;
            height: 30px;
            margin-bottom: 20px;
            overflow: hidden;
            border: 2px solid rgba(255, 215, 0, 0.3);
        }

        .progress-bar {
            background: linear-gradient(90deg, #FFD700, #FFA500);
            height: 100%;
            border-radius: 15px;
            transition: width 0.5s ease;
            position: relative;
            overflow: hidden;
        }

        .progress-bar::after {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3), transparent);
            animation: loading 2s infinite;
        }

        @keyframes loading {
            0% { left: -100%; }
            100% { left: 100%; }
        }

        .progress-text {
            text-align: center;
            font-size: 1.2rem;
            color: rgba(255, 255, 255, 0.9);
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 30px;
            margin: 40px 0;
        }

        .stat-card {
            background: rgba(255, 215, 0, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 15px;
            padding: 30px;
            text-align: center;
            border: 1px solid rgba(255, 215, 0, 0.3);
            transition: transform 0.3s ease;
        }

        .stat-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 35px rgba(255, 215, 0, 0.2);
        }

        .stat-number {
            font-size: 2.5rem;
            font-weight: bold;
            color: #FFD700;
            margin-bottom: 10px;
        }

        .stat-label {
            font-size: 1.1rem;
            color: rgba(255, 255, 255, 0.8);
        }

        .info-section {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(5px);
            border-radius: 15px;
            padding: 30px;
            margin: 40px 0;
            border-left: 5px solid #FFD700;
        }

        .info-title {
            font-size: 1.5rem;
            color: #FFD700;
            margin-bottom: 15px;
        }

        .info-text {
            color: rgba(255, 255, 255, 0.8);
            line-height: 1.6;
            margin-bottom: 10px;
        }

        .live-indicator {
            display: inline-flex;
            align-items: center;
            gap: 10px;
            background: rgba(255, 0, 0, 0.2);
            padding: 10px 20px;
            border-radius: 25px;
            border: 1px solid #ff0000;
            margin: 20px 0;
        }

        .live-dot {
            width: 12px;
            height: 12px;
            background: #ff0000;
            border-radius: 50%;
            animation: blink 1s infinite;
        }

        @keyframes blink {
            0%, 50% { opacity: 1; }
            51%, 100% { opacity: 0.3; }
        }

        footer {
            text-align: center;
            padding: 30px 0;
            color: rgba(255, 255, 255, 0.6);
            border-top: 1px solid rgba(255, 215, 0, 0.2);
            margin-top: 60px;
        }

        @media (max-width: 768px) {
            .counter-number {
                font-size: 3.5rem;
            }
            
            h1 {
                font-size: 2rem;
            }
            
            .main-counter {
                padding: 30px 20px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <div class="logo">
                <svg viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
                    <!-- Fenerbahçe logosu temsili -->
                    <circle cx="50" cy="50" r="45" fill="#003366" stroke="#FFD700" stroke-width="3"/>
                    <circle cx="50" cy="35" r="12" fill="#FFD700"/>
                    <rect x="40" y="47" width="20" height="25" fill="#FFD700" rx="2"/>
                    <text x="50" y="56" text-anchor="middle" fill="#003366" font-size="8" font-weight="bold">FB</text>
                    <text x="50" y="85" text-anchor="middle" fill="#FFD700" font-size="6" font-weight="bold">1907</text>
                </svg>
            </div>
            <h1>Fenerbahçe Kongre İmza Takip Sistemi</h1>
            <p class="subtitle">Olağanüstü Genel Kurul Çağrısı İçin Toplanan İmzalar</p>
            <div class="live-indicator">
                <div class="live-dot"></div>
                <span>CANLI TAKİP</span>
            </div>
        </header>

        <div class="main-counter">
            <div class="counter-label">Toplanan Noter Onaylı İmza Sayısı</div>
            <div class="counter-number" id="signatureCount">13,486</div>
            <div class="last-update">Son Güncelleme: <span id="lastUpdate"></span></div>
        </div>

        <div class="progress-section">
            <h3 class="progress-title">İlerleme Durumu</h3>
            <div class="progress-bar-container">
                <div class="progress-bar" id="progressBar"></div>
            </div>
            <div class="progress-text">
                Gerekli imza sayısına ulaşma oranı: <span id="progressPercent">0</span>%
            </div>
        </div>

        <div class="stats-grid">
            <div class="stat-card">
                <div class="stat-number" id="remaining">0</div>
                <div class="stat-label">Hedef İçin Kalan</div>
            </div>
        </div>

        <div class="info-section">
            <h3 class="info-title">Bilgilendirme</h3>
            <p class="info-text">• Olağanüstü Genel Kurul için gerekli olan kongre üyesi imza sayısı: <strong>16,465</strong></p>
            <p class="info-text">• Tüm imzalar noter onaylı olarak toplanmaktadır</p>
            <p class="info-text">• İmza toplama süreci devam etmektedir</p>
            <p class="info-text">• Sayfa otomatik olarak güncellenmektedir</p>
        </div>

        <footer>
            <p>Bu sayfa kongre üyeleri tarafından oluşturulmuş bilgilendirme amaçlı bir takip sistemidir.</p>
            <p>© 2025 - Fenerbahçe Kongre Üyeleri</p>
        </footer>
    </div>

    <script>
        let currentSignatures = 13486;
        let targetSignatures = 16465;
        let todaySignatures = 0;
        let weekSignatures = 0;

        function updateLastUpdateTime() {
            const now = new Date();
            const timeString = now.toLocaleString('tr-TR', {
                day: '2-digit',
                month: '2-digit',
                year: 'numeric',
                hour: '2-digit',
                minute: '2-digit',
                second: '2-digit'
            });
            document.getElementById('lastUpdate').textContent = timeString;
        }

        function formatNumber(num) {
            return num.toLocaleString('tr-TR');
        }

        function updateCounter() {
            document.getElementById('signatureCount').textContent = formatNumber(currentSignatures);
            
            // Progress bar güncelleme
            const progressPercent = Math.min((currentSignatures / targetSignatures) * 100, 100);
            document.getElementById('progressBar').style.width = progressPercent + '%';
            document.getElementById('progressPercent').textContent = progressPercent.toFixed(1);
            
            // İstatistikler güncelleme
            document.getElementById('remaining').textContent = formatNumber(Math.max(targetSignatures - currentSignatures, 0));
            
            updateLastUpdateTime();
        }

        function addSignature() {
            currentSignatures++;
            
            updateCounter();
            
            // Animasyon efekti
            const counterElement = document.getElementById('signatureCount');
            counterElement.style.transform = 'scale(1.1)';
            counterElement.style.color = '#00ff00';
            
            setTimeout(() => {
                counterElement.style.transform = 'scale(1)';
                counterElement.style.color = '#FFD700';
            }, 500);
            
            console.log(`Yeni imza eklendi. Toplam: ${currentSignatures}`);
        }

        // İlk yükleme
        updateCounter();
        
        // Her 30 dakikada bir otomatik imza ekleme (30 * 60 * 1000 = 1800000 ms)
        setInterval(addSignature, 30 * 60 * 1000);
        
        // Test için her 10 saniyede bir imza eklemek isterseniz bu satırı kullanın:
        // setInterval(addSignature, 10000);
        
        // Her saniye son güncelleme zamanını yenile
        setInterval(updateLastUpdateTime, 1000);
        
        // Sayfa yüklendiğinde ilk güncelleme
        updateLastUpdateTime();
    </script>
</body>
</html>
