<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>عيد ميلاد سعيد يا سارة! 🎂</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@300;400;500;700;800;900&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary: #e91e63;
            --primary-light: #f8bbd0;
            --primary-dark: #ad1457;
            --bg-1: #ffe5ec;
            --bg-2: #ffc2d1;
            --bg-3: #ffb3c6;
            --glass: rgba(255,255,255,0.15);
            --glass-border: rgba(255,255,255,0.25);
            --shadow: rgba(233,30,99,0.2);
        }

        * { margin:0; padding:0; box-sizing:border-box; }
        html { scroll-behavior: smooth; }

        body {
            font-family: 'Tajawal', sans-serif;
            background: linear-gradient(135deg, var(--bg-1) 0%, var(--bg-2) 50%, var(--bg-3) 100%);
            min-height: 100vh;
            overflow-x: hidden;
            cursor: none;
            position: relative;
        }

        /* ========== LOADING SCREEN ========== */
        .loader {
            position: fixed;
            inset: 0;
            background: linear-gradient(135deg, #fff0f5, #fce4ec);
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            z-index: 10000;
            transition: opacity 0.8s ease, visibility 0.8s ease;
        }
        .loader.hidden {
            opacity: 0;
            visibility: hidden;
            pointer-events: none;
        }
        .loader-cake {
            font-size: 5rem;
            animation: loaderBounce 1s ease infinite;
        }
        @keyframes loaderBounce {
            0%,100% { transform: translateY(0) scale(1); }
            50% { transform: translateY(-20px) scale(1.1); }
        }
        .loader-text {
            margin-top: 1.5rem;
            color: var(--primary-dark);
            font-size: 1.3rem;
            font-weight: 700;
        }
        .loader-bar {
            width: 200px; height: 4px;
            background: rgba(233,30,99,0.1);
            border-radius: 2px;
            margin-top: 1rem;
            overflow: hidden;
        }
        .loader-fill {
            height: 100%;
            background: linear-gradient(90deg, var(--primary), var(--primary-light));
            border-radius: 2px;
            animation: loadFill 2s ease forwards;
        }
        @keyframes loadFill { 0% { width:0; } 100% { width:100%; } }

        /* ========== CUSTOM CURSOR ========== */
        .cursor {
            position: fixed;
            width: 20px; height: 20px;
            border: 2px solid var(--primary);
            border-radius: 50%;
            pointer-events: none;
            z-index: 9999;
            transition: transform 0.1s ease, background 0.2s ease;
            transform: translate(-50%, -50%);
            mix-blend-mode: difference;
        }
        .cursor-dot {
            position: fixed;
            width: 6px; height: 6px;
            background: var(--primary);
            border-radius: 50%;
            pointer-events: none;
            z-index: 9999;
            transform: translate(-50%, -50%);
        }
        .cursor.hover { transform: translate(-50%,-50%) scale(2.5); background: rgba(233,30,99,0.15); }

        /* ========== CANVAS PARTICLES ========== */
        #particles-canvas {
            position: fixed;
            inset: 0;
            pointer-events: none;
            z-index: 1;
        }

        /* ========== PARALLAX BACKGROUND ========== */
        .parallax-layer {
            position: fixed;
            inset: 0;
            pointer-events: none;
            z-index: 0;
        }
        .parallax-circle {
            position: absolute;
            border-radius: 50%;
            opacity: 0.08;
            background: var(--primary);
        }
        .c1 { width: 600px; height: 600px; top: -200px; right: -200px; }
        .c2 { width: 400px; height: 400px; bottom: -100px; left: -100px; }
        .c3 { width: 300px; height: 300px; top: 50%; left: 50%; transform: translate(-50%,-50%); }

        /* ========== MAIN CONTAINER ========== */
        .main {
            position: relative;
            z-index: 10;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 2rem 1rem;
        }

        /* ========== GLASS CARD ========== */
        .glass-card {
            background: rgba(255,255,255,0.72);
            backdrop-filter: blur(20px) saturate(180%);
            -webkit-backdrop-filter: blur(20px) saturate(180%);
            border-radius: 2.5rem;
            border: 1px solid var(--glass-border);
            box-shadow:
                0 25px 50px var(--shadow),
                inset 0 1px 0 rgba(255,255,255,0.6);
            padding: 3rem 2.5rem;
            max-width: 480px;
            width: 100%;
            text-align: center;
            position: relative;
            overflow: hidden;
            transform-style: preserve-3d;
            perspective: 1000px;
            transition: transform 0.1s ease;
        }
        .glass-card::before {
            content: '';
            position: absolute;
            top: -50%; left: -50%;
            width: 200%; height: 200%;
            background: radial-gradient(circle, rgba(255,255,255,0.4) 0%, transparent 60%);
            pointer-events: none;
        }

        /* ========== SHINE EFFECT ========== */
        .shine {
            position: absolute;
            top: 0; left: -100%;
            width: 50%; height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.4), transparent);
            transform: skewX(-25deg);
            animation: shineMove 4s ease-in-out infinite;
            pointer-events: none;
        }
        @keyframes shineMove {
            0%,100% { left: -100%; }
            50% { left: 150%; }
        }

        /* ========== CAKE 3D ========== */
        .cake-container {
            position: relative;
            width: 100px; height: 100px;
            margin: 0 auto 1.5rem;
            perspective: 600px;
        }
        .cake-3d {
            font-size: 4rem;
            display: inline-block;
            animation: cakeFloat 3s ease-in-out infinite;
            filter: drop-shadow(0 10px 20px rgba(233,30,99,0.3));
        }
        @keyframes cakeFloat {
            0%,100% { transform: translateY(0) rotateY(0deg); }
            25% { transform: translateY(-12px) rotateY(5deg); }
            50% { transform: translateY(-5px) rotateY(0deg); }
            75% { transform: translateY(-12px) rotateY(-5deg); }
        }

        /* ========== TITLE ========== */
        .title {
            font-size: 2.2rem;
            font-weight: 900;
            color: var(--primary-dark);
            margin-bottom: 0.3rem;
            position: relative;
            display: inline-block;
        }
        .title::after {
            content: '';
            position: absolute;
            bottom: -5px; left: 50%;
            transform: translateX(-50%);
            width: 0; height: 4px;
            background: linear-gradient(90deg, var(--primary), var(--primary-light));
            border-radius: 2px;
            animation: lineExpand 1s ease forwards 0.5s;
        }
        @keyframes lineExpand { to { width: 60px; } }

        /* ========== DATE BADGE ========== */
        .date-badge {
            display: inline-flex;
            align-items: center;
            gap: 0.4rem;
            background: linear-gradient(135deg, #fce4ec, #f8bbd0);
            color: var(--primary-dark);
            padding: 0.5rem 1.5rem;
            border-radius: 2rem;
            font-weight: 800;
            font-size: 1rem;
            margin: 1rem 0 1.5rem;
            box-shadow: 0 4px 15px rgba(233,30,99,0.15);
            position: relative;
            overflow: hidden;
        }
        .date-badge::before {
            content: '';
            position: absolute;
            inset: 0;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.4), transparent);
            animation: badgeShine 3s ease-in-out infinite;
        }
        @keyframes badgeShine {
            0%,100% { transform: translateX(-100%); }
            50% { transform: translateX(100%); }
        }

        /* ========== TYPEWRITER ========== */
        .typewriter-container {
            min-height: 120px;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 1.5rem;
        }
        .typewriter {
            color: #555;
            font-size: 1.2rem;
            line-height: 2;
            font-weight: 500;
        }
        .typewriter .highlight {
            color: var(--primary);
            font-weight: 800;
            position: relative;
        }
        .cursor-blink {
            display: inline-block;
            width: 3px; height: 1.2em;
            background: var(--primary);
            margin-right: 2px;
            animation: blink 0.8s step-end infinite;
            vertical-align: middle;
        }
        @keyframes blink { 50% { opacity: 0; } }

        /* ========== COUNTDOWN ========== */
        .countdown-section {
            margin: 1.5rem 0;
            padding: 1.2rem;
            background: linear-gradient(135deg, rgba(233,30,99,0.05), rgba(248,187,208,0.1));
            border-radius: 1.5rem;
            border: 1px solid rgba(233,30,99,0.1);
        }
        .countdown-title {
            font-size: 0.85rem;
            color: var(--primary-dark);
            font-weight: 700;
            margin-bottom: 0.8rem;
            opacity: 0.8;
        }
        .countdown-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 0.5rem;
        }
        .countdown-item {
            background: rgba(255,255,255,0.8);
            border-radius: 1rem;
            padding: 0.6rem 0.3rem;
            box-shadow: 0 2px 10px rgba(0,0,0,0.05);
        }
        .countdown-num {
            font-size: 1.6rem;
            font-weight: 900;
            color: var(--primary);
            display: block;
            line-height: 1;
        }
        .countdown-label {
            font-size: 0.65rem;
            color: #888;
            font-weight: 600;
            margin-top: 0.2rem;
        }

        /* ========== BUTTON ========== */
        .btn-container { position: relative; display: inline-block; }
        .btn {
            background: linear-gradient(135deg, #ec407a, #d81b60, #c2185b);
            background-size: 200% 200%;
            color: #fff;
            border: none;
            padding: 1rem 3rem;
            font-size: 1.15rem;
            font-weight: 800;
            font-family: 'Tajawal', sans-serif;
            border-radius: 3rem;
            cursor: none;
            box-shadow:
                0 10px 30px rgba(233,30,99,0.35),
                0 0 0 0 rgba(233,30,99,0.4);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
            animation: gradientShift 3s ease infinite, pulseGlow 2s ease infinite;
        }
        @keyframes gradientShift {
            0%,100% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
        }
        @keyframes pulseGlow {
            0%,100% { box-shadow: 0 10px 30px rgba(233,30,99,0.35), 0 0 0 0 rgba(233,30,99,0.4); }
            50% { box-shadow: 0 10px 30px rgba(233,30,99,0.45), 0 0 0 15px rgba(233,30,99,0); }
        }
        .btn:hover { transform: translateY(-4px) scale(1.03); }
        .btn:active { transform: translateY(0) scale(0.97); }
        .btn::before {
            content: '';
            position: absolute;
            top: 0; left: -100%;
            width: 100%; height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3), transparent);
            transition: left 0.5s ease;
        }
        .btn:hover::before { left: 100%; }

        /* ========== SURPRISE ========== */
        .surprise {
            margin-top: 1.5rem;
            padding: 1.5rem;
            background: linear-gradient(135deg, #fff0f5, #fce4ec);
            border-radius: 1.8rem;
            border: 2px solid rgba(248,187,208,0.5);
            display: none;
            position: relative;
            overflow: hidden;
        }
        .surprise.show {
            display: block;
            animation: surpriseIn 0.8s cubic-bezier(0.34, 1.56, 0.64, 1);
        }
        @keyframes surpriseIn {
            0% { transform: scale(0.3) rotate(-5deg); opacity: 0; }
            100% { transform: scale(1) rotate(0deg); opacity: 1; }
        }
        .surprise-hearts {
            font-size: 2.5rem;
            margin-bottom: 0.5rem;
            animation: heartbeat 1.2s ease infinite;
        }
        @keyframes heartbeat {
            0%,100% { transform: scale(1); }
            15% { transform: scale(1.3); }
            30% { transform: scale(1); }
            45% { transform: scale(1.15); }
        }
        .surprise-text {
            color: var(--primary-dark);
            font-weight: 800;
            font-size: 1.15rem;
            line-height: 1.8;
        }
        .surprise-from {
            color: var(--primary);
            font-size: 0.9rem;
            margin-top: 0.5rem;
            font-weight: 600;
        }

        /* ========== FOOTER ========== */
        .footer {
            margin-top: 2rem;
            text-align: center;
            color: var(--primary-dark);
            font-size: 0.8rem;
            opacity: 0.6;
        }
        .footer-hearts {
            font-size: 1.3rem;
            margin-bottom: 0.5rem;
            animation: footerPulse 2s ease infinite;
        }
        @keyframes footerPulse {
            0%,100% { opacity: 0.5; transform: scale(1); }
            50% { opacity: 1; transform: scale(1.15); }
        }

        /* ========== REVEAL ANIMATIONS ========== */
        .reveal {
            opacity: 0;
            transform: translateY(30px);
            transition: all 0.8s cubic-bezier(0.34, 1.56, 0.64, 1);
        }
        .reveal.visible {
            opacity: 1;
            transform: translateY(0);
        }
        .reveal-delay-1 { transition-delay: 0.1s; }
        .reveal-delay-2 { transition-delay: 0.2s; }
        .reveal-delay-3 { transition-delay: 0.3s; }
        .reveal-delay-4 { transition-delay: 0.4s; }
        .reveal-delay-5 { transition-delay: 0.5s; }

        /* ========== CONFETTI ========== */
        .confetti {
            position: fixed;
            pointer-events: none;
            z-index: 200;
            animation: confettiFall 3s ease-out forwards;
        }
        @keyframes confettiFall {
            0% { transform: translate(0,0) rotate(0deg) scale(1); opacity: 1; }
            100% { transform: translate(var(--tx), var(--ty)) rotate(var(--rot)) scale(0); opacity: 0; }
        }

        /* ========== FLYING HEARTS ========== */
        .fly-heart {
            position: fixed;
            pointer-events: none;
            z-index: 199;
            animation: flyUp 2s ease-out forwards;
            font-size: 1.5rem;
        }
        @keyframes flyUp {
            0% { transform: translate(0,0) scale(1) rotate(0deg); opacity: 1; }
            100% { transform: translate(var(--hx), var(--hy)) scale(0) rotate(var(--hr)); opacity: 0; }
        }

        /* ========== SPARKLES ========== */
        .sparkle {
            position: fixed;
            width: 8px; height: 8px;
            background: #ffd700;
            border-radius: 50%;
            pointer-events: none;
            z-index: 198;
            box-shadow: 0 0 12px #ffd700, 0 0 24px #ffd700;
            animation: sparkleAnim 1.2s ease-out forwards;
        }
        @keyframes sparkleAnim {
            0% { transform: scale(0); opacity: 1; }
            100% { transform: scale(3); opacity: 0; }
        }

        /* ========== RIPPLE ========== */
        .ripple {
            position: fixed;
            border-radius: 50%;
            border: 2px solid var(--primary-light);
            pointer-events: none;
            z-index: 197;
            animation: rippleAnim 1s ease-out forwards;
        }
        @keyframes rippleAnim {
            0% { width: 0; height: 0; opacity: 0.8; }
            100% { width: 200px; height: 200px; opacity: 0; }
        }

        /* ========== MUSIC BUTTON ========== */
        .music-btn {
            position: fixed;
            bottom: 1.5rem; left: 1.5rem;
            width: 50px; height: 50px;
            border-radius: 50%;
            background: rgba(255,255,255,0.8);
            backdrop-filter: blur(10px);
            border: 1px solid var(--glass-border);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.3rem;
            cursor: none;
            box-shadow: 0 4px 15px rgba(0,0,0,0.1);
            transition: all 0.3s ease;
            z-index: 50;
        }
        .music-btn:hover { transform: scale(1.1); background: rgba(255,255,255,0.95); }
        .music-btn.playing { animation: musicPulse 1s ease infinite; }
        @keyframes musicPulse {
            0%,100% { box-shadow: 0 0 0 0 rgba(233,30,99,0.3); }
            50% { box-shadow: 0 0 0 12px rgba(233,30,99,0); }
        }

        /* ========== RESPONSIVE ========== */
        @media (max-width: 480px) {
            .glass-card { padding: 2rem 1.5rem; border-radius: 2rem; }
            .title { font-size: 1.7rem; }
            .typewriter { font-size: 1.05rem; }
            .countdown-num { font-size: 1.3rem; }
            .btn { padding: 0.9rem 2rem; font-size: 1rem; }
            .cursor, .cursor-dot { display: none; }
            body { cursor: auto; }
        }

        /* ========== SCROLLBAR ========== */
        ::-webkit-scrollbar { width: 6px; }
        ::-webkit-scrollbar-track { background: transparent; }
        ::-webkit-scrollbar-thumb { background: var(--primary-light); border-radius: 3px; }
        ::-webkit-scrollbar-thumb:hover { background: var(--primary); }
    </style>
<base target="_blank">
</head>
<body>

    <!-- Loading Screen -->
    <div class="loader" id="loader">
        <div class="loader-cake">🎂</div>
        <div class="loader-text">نحضر مفاجأة لسارة...</div>
        <div class="loader-bar"><div class="loader-fill"></div></div>
    </div>

    <!-- Custom Cursor -->
    <div class="cursor" id="cursor"></div>
    <div class="cursor-dot" id="cursor-dot"></div>

    <!-- Canvas Particles -->
    <canvas id="particles-canvas"></canvas>

    <!-- Parallax Background -->
    <div class="parallax-layer" id="parallax">
        <div class="parallax-circle c1" data-speed="0.02"></div>
        <div class="parallax-circle c2" data-speed="0.03"></div>
        <div class="parallax-circle c3" data-speed="0.015"></div>
    </div>

    <!-- Main Content -->
    <div class="main">
        <div class="glass-card" id="card">
            <div class="shine"></div>

            <div class="cake-container reveal reveal-delay-1">
                <div class="cake-3d">🎂</div>
            </div>

            <h1 class="title reveal reveal-delay-2">عيد ميلاد سعيد يا سارة!</h1>

            <div class="date-badge reveal reveal-delay-3">
                <span>🎈</span>
                <span>24 يوليو</span>
            </div>

            <div class="typewriter-container reveal reveal-delay-4">
                <div class="typewriter" id="typewriter"></div>
            </div>

            <div class="countdown-section reveal reveal-delay-4" id="countdown">
                <div class="countdown-title">⏰ الوقت المتبقي لعيد ميلادك</div>
                <div class="countdown-grid">
                    <div class="countdown-item">
                        <span class="countdown-num" id="cd-days">00</span>
                        <span class="countdown-label">يوم</span>
                    </div>
                    <div class="countdown-item">
                        <span class="countdown-num" id="cd-hours">00</span>
                        <span class="countdown-label">ساعة</span>
                    </div>
                    <div class="countdown-item">
                        <span class="countdown-num" id="cd-minutes">00</span>
                        <span class="countdown-label">دقيقة</span>
                    </div>
                    <div class="countdown-item">
                        <span class="countdown-num" id="cd-seconds">00</span>
                        <span class="countdown-label">ثانية</span>
                    </div>
                </div>
            </div>

            <div class="btn-container reveal reveal-delay-5">
                <button class="btn" id="celebrate-btn">اضغطي هنا يا حلوة 💝</button>
            </div>

            <div class="surprise" id="surprise">
                <div class="surprise-hearts">💖🌹💖</div>
                <div class="surprise-text">
                    أحبك أكثر مما أستطيع أن أقول!<br>
                    كل يوم معك هو عيد بالنسبة لي 💕
                </div>
                <div class="surprise-from">— من حبيبك ❤️</div>
            </div>
        </div>

        <div class="footer reveal reveal-delay-5">
            <div class="footer-hearts">💕 💕 💕</div>
            <div>صُنع بحب خصيصاً لسارة</div>
        </div>
    </div>

    <!-- Music Button -->
    <button class="music-btn" id="music-btn" title="تشغيل موسيقى">🎵</button>

    <script>
        // ========== LOADER - Fixed ==========
        function hideLoader() {
            const loader = document.getElementById('loader');
            if (loader) {
                loader.classList.add('hidden');
                setTimeout(() => {
                    loader.style.display = 'none';
                }, 800);
            }
            initTypewriter();
            revealElements();
        }

        // Try DOMContentLoaded first (fires when HTML is parsed)
        if (document.readyState === 'loading') {
            document.addEventListener('DOMContentLoaded', function() {
                setTimeout(hideLoader, 2200);
            });
        } else {
            // DOM already loaded
            setTimeout(hideLoader, 2200);
        }

        // Fallback: force hide after 5 seconds no matter what
        setTimeout(function() {
            const loader = document.getElementById('loader');
            if (loader && !loader.classList.contains('hidden')) {
                hideLoader();
            }
        }, 5000);

        // ========== CUSTOM CURSOR ==========
        const cursor = document.getElementById('cursor');
        const cursorDot = document.getElementById('cursor-dot');
        let mouseX = 0, mouseY = 0, cursorX = 0, cursorY = 0;

        document.addEventListener('mousemove', function(e) {
            mouseX = e.clientX;
            mouseY = e.clientY;
            if (cursorDot) {
                cursorDot.style.left = mouseX + 'px';
                cursorDot.style.top = mouseY + 'px';
            }
        });

        function animateCursor() {
            if (cursor) {
                cursorX += (mouseX - cursorX) * 0.15;
                cursorY += (mouseY - cursorY) * 0.15;
                cursor.style.left = cursorX + 'px';
                cursor.style.top = cursorY + 'px';
            }
            requestAnimationFrame(animateCursor);
        }
        animateCursor();

        document.querySelectorAll('button, .glass-card').forEach(function(el) {
            el.addEventListener('mouseenter', function() { if(cursor) cursor.classList.add('hover'); });
            el.addEventListener('mouseleave', function() { if(cursor) cursor.classList.remove('hover'); });
        });

        // ========== 3D TILT CARD ==========
        const card = document.getElementById('card');
        if (card) {
            card.addEventListener('mousemove', function(e) {
                const rect = card.getBoundingClientRect();
                const x = e.clientX - rect.left;
                const y = e.clientY - rect.top;
                const centerX = rect.width / 2;
                const centerY = rect.height / 2;
                const rotateX = (y - centerY) / 20;
                const rotateY = (centerX - x) / 20;
                card.style.transform = 'perspective(1000px) rotateX(' + rotateX + 'deg) rotateY(' + rotateY + 'deg)';
            });
            card.addEventListener('mouseleave', function() {
                card.style.transform = 'perspective(1000px) rotateX(0) rotateY(0)';
            });
        }

        // ========== TYPEWRITER ==========
        const typeText = "كل عام وأنتِ <span class=\"highlight\">أجمل هدية</span> في حياتي 💕\nيا نور عيوني وفرحتي الكبيرة\nربنا يخليكي لي ويديم ضحكتك";
        const typewriterEl = document.getElementById('typewriter');
        let typeIndex = 0;
        let typeHTML = '';
        let inTag = false;

        function initTypewriter() {
            if (!typewriterEl) return;
            typeIndex = 0;
            typeHTML = '';
            inTag = false;
            typeNextChar();
        }

        function typeNextChar() {
            if (typeIndex < typeText.length) {
                const char = typeText[typeIndex];
                if (char === '<') inTag = true;
                if (char === '>') inTag = false;
                if (char === '\\' && typeText[typeIndex + 1] === 'n') {
                    typeHTML += '<br>';
                    typeIndex += 2;
                } else {
                    typeHTML += char;
                    typeIndex++;
                }
                typewriterEl.innerHTML = typeHTML + '<span class="cursor-blink"></span>';
                setTimeout(typeNextChar, inTag ? 0 : 45);
            } else {
                typewriterEl.innerHTML = typeHTML;
            }
        }

        // ========== COUNTDOWN ==========
        function updateCountdown() {
            const now = new Date();
            const currentYear = now.getFullYear();
            let target = new Date(currentYear, 6, 24, 0, 0, 0);
            if (now > target) target = new Date(currentYear + 1, 6, 24, 0, 0, 0);

            const diff = target - now;
            const days = Math.floor(diff / (1000 * 60 * 60 * 24));
            const hours = Math.floor((diff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
            const minutes = Math.floor((diff % (1000 * 60 * 60)) / (1000 * 60));
            const seconds = Math.floor((diff % (1000 * 60)) / 1000);

            const d = document.getElementById('cd-days');
            const h = document.getElementById('cd-hours');
            const m = document.getElementById('cd-minutes');
            const s = document.getElementById('cd-seconds');
            if (d) d.textContent = String(days).padStart(2, '0');
            if (h) h.textContent = String(hours).padStart(2, '0');
            if (m) m.textContent = String(minutes).padStart(2, '0');
            if (s) s.textContent = String(seconds).padStart(2, '0');
        }
        updateCountdown();
        setInterval(updateCountdown, 1000);

        // ========== REVEAL ON SCROLL ==========
        function revealElements() {
            document.querySelectorAll('.reveal').forEach(function(el, i) {
                setTimeout(function() { el.classList.add('visible'); }, 300 + i * 150);
            });
        }

        // ========== PARALLAX ==========
        document.addEventListener('mousemove', function(e) {
            const x = (e.clientX / window.innerWidth - 0.5) * 2;
            const y = (e.clientY / window.innerHeight - 0.5) * 2;
            document.querySelectorAll('.parallax-circle').forEach(function(circle) {
                const speed = parseFloat(circle.dataset.speed);
                circle.style.transform = 'translate(' + (x * 50 * speed) + 'px, ' + (y * 50 * speed) + 'px)';
            });
        });

        // ========== CANVAS PARTICLES ==========
        const canvas = document.getElementById('particles-canvas');
        const ctx = canvas ? canvas.getContext('2d') : null;
        let particles = [];
        const particleColors = ['#ff6b9d', '#ff8fab', '#fb6f92', '#ffc2d1', '#ffd700', '#ff69b4'];

        function resizeCanvas() {
            if (canvas) {
                canvas.width = window.innerWidth;
                canvas.height = window.innerHeight;
            }
        }
        resizeCanvas();
        window.addEventListener('resize', resizeCanvas);

        function Particle(x, y, type) {
            this.x = x || Math.random() * (canvas ? canvas.width : 800);
            this.y = y || Math.random() * (canvas ? canvas.height : 600);
            this.size = Math.random() * 4 + 2;
            this.speedX = (Math.random() - 0.5) * 1;
            this.speedY = (Math.random() - 0.5) * 1;
            this.color = particleColors[Math.floor(Math.random() * particleColors.length)];
            this.opacity = Math.random() * 0.5 + 0.3;
            this.type = type || 'ambient';
            this.life = type === 'burst' ? 100 : Infinity;
            this.update = function() {
                this.x += this.speedX;
                this.y += this.speedY;
                if (this.type === 'burst') {
                    this.life--;
                    this.opacity = this.life / 100;
                    this.speedX *= 0.98;
                    this.speedY *= 0.98;
                }
                if (this.x < 0 || this.x > (canvas ? canvas.width : 800)) this.speedX *= -1;
                if (this.y < 0 || this.y > (canvas ? canvas.height : 600)) this.speedY *= -1;
            };
            this.draw = function() {
                if (!ctx) return;
                ctx.save();
                ctx.globalAlpha = this.opacity;
                ctx.fillStyle = this.color;
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                ctx.fill();
                ctx.restore();
            };
        }

        for (let i = 0; i < 40; i++) particles.push(new Particle());

        function animateParticles() {
            if (!ctx) return;
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            particles = particles.filter(function(p) { return p.life > 0; });
            particles.forEach(function(p) { p.update(); p.draw(); });
            requestAnimationFrame(animateParticles);
        }
        animateParticles();

        document.addEventListener('mousemove', function(e) {
            if (Math.random() > 0.85) {
                particles.push(new Particle(e.clientX, e.clientY, 'burst'));
            }
        });

        // ========== CELEBRATE ==========
        const heartEmojis = ['💕','💖','💗','💝','🌹','💘','💓','💞'];
        const confettiShapes = ['circle', 'square', 'triangle'];
        const celebrateBtn = document.getElementById('celebrate-btn');

        if (celebrateBtn) {
            celebrateBtn.addEventListener('click', celebrate);
        }

        function celebrate() {
            const surprise = document.getElementById('surprise');
            if (surprise) surprise.classList.add('show');

            for (let i = 0; i < 30; i++) {
                setTimeout(createFlyHeart, i * 60);
            }

            const colors = ['#ff6b9d','#ff8fab','#fb6f92','#ffc2d1','#ff4081','#ffd700','#ff69b4','#e91e63'];
            for (let i = 0; i < 60; i++) {
                setTimeout(function() { createConfetti(colors[Math.floor(Math.random()*colors.length)]); }, i * 40);
            }

            for (let i = 0; i < 20; i++) {
                setTimeout(createSparkle, i * 80);
            }

            for (let i = 0; i < 5; i++) {
                setTimeout(createRipple, i * 200);
            }

            if (celebrateBtn) {
                const rect = celebrateBtn.getBoundingClientRect();
                for (let i = 0; i < 30; i++) {
                    var p = new Particle(rect.left + rect.width/2, rect.top + rect.height/2, 'burst');
                    p.speedX = (Math.random() - 0.5) * 8;
                    p.speedY = (Math.random() - 0.5) * 8;
                    p.size = Math.random() * 6 + 3;
                    particles.push(p);
                }
            }
        }

        function createFlyHeart() {
            const heart = document.createElement('div');
            heart.className = 'fly-heart';
            heart.innerHTML = heartEmojis[Math.floor(Math.random() * heartEmojis.length)];
            if (celebrateBtn) {
                const rect = celebrateBtn.getBoundingClientRect();
                heart.style.left = (rect.left + rect.width/2 + (Math.random()*80-40)) + 'px';
                heart.style.top = (rect.top + (Math.random()*20-10)) + 'px';
            } else {
                heart.style.left = '50%';
                heart.style.top = '50%';
            }
            heart.style.setProperty('--hx', (Math.random()*300-150) + 'px');
            heart.style.setProperty('--hy', '-' + (Math.random()*400+200) + 'px');
            heart.style.setProperty('--hr', (Math.random()*360) + 'deg');
            document.body.appendChild(heart);
            setTimeout(function() { heart.remove(); }, 2000);
        }

        function createConfetti(color) {
            const conf = document.createElement('div');
            conf.className = 'confetti';
            const shape = confettiShapes[Math.floor(Math.random() * confettiShapes.length)];
            conf.style.backgroundColor = color;
            if (shape === 'circle') conf.style.borderRadius = '50%';
            if (shape === 'triangle') {
                conf.style.backgroundColor = 'transparent';
                conf.style.width = '0'; conf.style.height = '0';
                conf.style.borderLeft = '6px solid transparent';
                conf.style.borderRight = '6px solid transparent';
                conf.style.borderBottom = '10px solid ' + color;
            }
            if (celebrateBtn) {
                const rect = celebrateBtn.getBoundingClientRect();
                conf.style.left = (rect.left + rect.width/2) + 'px';
                conf.style.top = rect.top + 'px';
            } else {
                conf.style.left = '50%';
                conf.style.top = '50%';
            }
            conf.style.setProperty('--tx', (Math.random()*500-250) + 'px');
            conf.style.setProperty('--ty', (Math.random()*400+100) + 'px');
            conf.style.setProperty('--rot', (Math.random()*720) + 'deg');
            document.body.appendChild(conf);
            setTimeout(function() { conf.remove(); }, 3000);
        }

        function createSparkle() {
            const sparkle = document.createElement('div');
            sparkle.className = 'sparkle';
            const surprise = document.getElementById('surprise');
            if (surprise) {
                const rect = surprise.getBoundingClientRect();
                sparkle.style.left = (rect.left + Math.random()*rect.width) + 'px';
                sparkle.style.top = (rect.top + Math.random()*rect.height) + 'px';
            }
            document.body.appendChild(sparkle);
            setTimeout(function() { sparkle.remove(); }, 1200);
        }

        function createRipple() {
            const ripple = document.createElement('div');
            ripple.className = 'ripple';
            const surprise = document.getElementById('surprise');
            if (surprise) {
                const rect = surprise.getBoundingClientRect();
                ripple.style.left = (rect.left + rect.width/2 - 100) + 'px';
                ripple.style.top = (rect.top + rect.height/2 - 100) + 'px';
            }
            document.body.appendChild(ripple);
            setTimeout(function() { ripple.remove(); }, 1000);
        }

        // ========== MUSIC BUTTON ==========
        const musicBtn = document.getElementById('music-btn');
        let musicPlaying = false;
        if (musicBtn) {
            musicBtn.addEventListener('click', function() {
                musicPlaying = !musicPlaying;
                musicBtn.classList.toggle('playing', musicPlaying);
                musicBtn.innerHTML = musicPlaying ? '🔊' : '🎵';
                musicBtn.title = musicPlaying ? 'إيقاف' : 'تشغيل موسيقى';
                if (musicPlaying) {
                    particles.forEach(function(p) { p.speedY = -Math.abs(p.speedY) - 0.5; });
                }
            });
        }

        // ========== CLICK RIPPLE EFFECT ==========
        document.addEventListener('click', function(e) {
            const ripple = document.createElement('div');
            ripple.style.position = 'fixed';
            ripple.style.left = e.clientX + 'px';
            ripple.style.top = e.clientY + 'px';
            ripple.style.width = '0';
            ripple.style.height = '0';
            ripple.style.borderRadius = '50%';
            ripple.style.background = 'rgba(233,30,99,0.2)';
            ripple.style.transform = 'translate(-50%,-50%)';
            ripple.style.pointerEvents = 'none';
            ripple.style.zIndex = '150';
            ripple.style.animation = 'rippleClick 0.6s ease-out forwards';
            document.body.appendChild(ripple);
            setTimeout(function() { ripple.remove(); }, 600);
        });
    </script>
    <style>
        @keyframes rippleClick {
            0% { width:0; height:0; opacity:0.6; }
            100% { width:100px; height:100px; opacity:0; }
        }
    </style>
</body>
</html>
