<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
    <title>ИИ в робототехнике | Презентация</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', 'Roboto', system-ui, -apple-system, sans-serif;
            background: linear-gradient(145deg, #e0e5ec 0%, #f0f4fa 100%);
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 24px 20px;
        }

        /* Основной контейнер презентации */
        .presentation-container {
            max-width: 1300px;
            width: 100%;
            background: #ffffff;
            border-radius: 48px;
            box-shadow: 0 25px 45px -12px rgba(0,0,0,0.3);
            overflow: hidden;
            transition: all 0.2s ease;
        }

        /* Область слайда */
        .slide-area {
            position: relative;
            min-height: 70vh;
            background: #fff;
        }

        .slide {
            display: none;
            padding: 40px 48px;
            animation: fadeSlide 0.4s ease-out;
        }

        .slide.active {
            display: block;
        }

        @keyframes fadeSlide {
            from { opacity: 0; transform: translateY(8px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* === СТИЛИ ДЛЯ СОДЕРЖИМОГО (полная аналогия исходной презентации) === */
        .slide h1 {
            font-size: 3.2rem;
            font-weight: 700;
            background: linear-gradient(135deg, #1a2a6c, #b21f1f, #fdbb4d);
            background-clip: text;
            -webkit-background-clip: text;
            color: transparent;
            margin-bottom: 24px;
            letter-spacing: -0.01em;
        }

        .slide h2 {
            font-size: 2rem;
            margin: 24px 0 16px 0;
            color: #0a2540;
            border-left: 6px solid #2c7da0;
            padding-left: 20px;
        }

        .slide h3 {
            font-size: 1.5rem;
            margin: 20px 0 12px 0;
            color: #1f6392;
        }

        .slide p {
            font-size: 1.1rem;
            line-height: 1.5;
            margin-bottom: 16px;
            color: #2c3e4e;
        }

        .slide ul, .slide ol {
            margin: 16px 0 16px 28px;
            font-size: 1.05rem;
            line-height: 1.5;
            color: #2c3e4e;
        }

        .slide li {
            margin: 8px 0;
        }

        .slide blockquote {
            background: #f0f7fb;
            border-left: 5px solid #2c7da0;
            padding: 14px 24px;
            margin: 20px 0;
            border-radius: 20px;
            font-style: italic;
            color: #1e4663;
        }

        .slide table {
            width: 100%;
            border-collapse: collapse;
            margin: 20px 0;
            background: #f9fbfd;
            border-radius: 24px;
            overflow: hidden;
            box-shadow: 0 1px 3px rgba(0,0,0,0.05);
        }

        .slide th, .slide td {
            border: 1px solid #dce5ec;
            padding: 12px 16px;
            text-align: left;
            vertical-align: top;
        }

        .slide th {
            background: #eef3f9;
            font-weight: 600;
            color: #0f3b5c;
        }

        .slide code {
            background: #eef2f6;
            padding: 3px 8px;
            border-radius: 12px;
            font-family: 'JetBrains Mono', monospace;
            font-size: 0.9rem;
        }

        /* навигация */
        .nav-buttons {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 48px 30px 48px;
            background: #ffffff;
            border-top: 1px solid #e9edf2;
        }

        .nav-btn {
            background: #2c7da0;
            border: none;
            color: white;
            font-size: 1.1rem;
            font-weight: 600;
            padding: 12px 28px;
            border-radius: 60px;
            cursor: pointer;
            transition: all 0.2s ease;
            display: inline-flex;
            align-items: center;
            gap: 8px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }

        .nav-btn:hover:not(:disabled) {
            background: #1f5e7e;
            transform: scale(1.02);
            box-shadow: 0 6px 12px rgba(0,0,0,0.1);
        }

        .nav-btn:disabled {
            background: #bdc4cc;
            cursor: not-allowed;
            opacity: 0.6;
            transform: none;
        }

        .slide-counter {
            font-size: 1rem;
            background: #eef2f7;
            padding: 8px 18px;
            border-radius: 40px;
            color: #1f5e7e;
            font-weight: 500;
        }

        /* адаптив */
        @media (max-width: 780px) {
            .slide {
                padding: 28px 20px;
            }
            .slide h1 {
                font-size: 2.2rem;
            }
            .slide h2 {
                font-size: 1.6rem;
            }
            .nav-buttons {
                padding: 16px 20px;
                flex-wrap: wrap;
                gap: 12px;
            }
            .nav-btn {
                padding: 8px 20px;
                font-size: 0.9rem;
            }
        }

        /* расцветка для акцентов */
        .highlight {
            background: linear-gradient(120deg, #f9f3e6 0%, #fff1db 100%);
            padding: 6px 12px;
            border-radius: 24px;
            font-weight: 500;
        }

        footer {
            font-size: 0.75rem;
            text-align: center;
            padding: 12px;
            background: #f8fafc;
            color: #6c86a3;
            border-top: 1px solid #e2e8f0;
        }
    </style>
</head>
<body>
<div class="presentation-container">
    <div class="slide-area">
        <!-- Слайд 1: Титульный (переработанный, читаемый и стильный) -->
        <div class="slide active" id="slide1">
            <div style="text-align: center; margin-top: 20px; margin-bottom: 30px;">
                <span style="background: #eef2ff; padding: 6px 18px; border-radius: 100px; font-weight: 500; color:#2c7da0;">🤖✨ Интеллектуальные системы</span>
            </div>
            <h1 style="text-align: center; font-size: 3.4rem; margin-bottom: 20px;">Искусственный интеллект <br>в робототехнике</h1>
            <p style="text-align: center; font-size: 1.2rem; color: #2c5a74; max-width: 85%; margin: 0 auto 30px auto;">Как нейросети, обучение с подкреплением и компьютерное зрение<br>меняют облик автономных машин</p>
            <div style="background: #eef2fa; padding: 20px; border-radius: 32px; margin-top: 20px; text-align: center;">
                <p style="margin-bottom: 0;"><strong>📌 Ключевые направления:</strong> Computer Vision, Reinforcement Learning, SLAM, планирование траекторий</p>
                <p style="margin-top: 12px; font-size: 0.9rem;">Современная робототехника немыслима без методов ИИ — от беспилотных автомобилей до медицинских ассистентов</p>
            </div>
        </div>

        <!-- Слайд 2: Основные сферы ИИ в робототехнике -->
        <div class="slide" id="slide2">
            <h2>🧠 Роль ИИ в управлении роботами</h2>
            <p>Искусственный интеллект превращает роботов из жёстко запрограммированных машин в адаптивные системы, способные воспринимать окружение и принимать решения в реальном времени.</p>
            <ul>
                <li><strong>🔍 Компьютерное зрение</strong> – распознавание объектов, навигация, избегание препятствий.</li>
                <li><strong>🎓 Обучение с подкреплением (RL)</strong> – роботы самостоятельно обучаются сложным движениям и тактикам.</li>
                <li><strong>🗺️ SLAM (Simultaneous Localization and Mapping)</strong> – построение карты неизвестной среды.</li>
                <li><strong>🤖 Планирование движений и манипуляции</strong> – точный захват, сборка, взаимодействие.</li>
            </ul>
            <blockquote>«ИИ — это ключ к созданию по-настоящему автономных роботов, способных действовать в условиях неопределённости»</blockquote>
        </div>

        <!-- Слайд 3: Компьютерное зрение и深度学习 -->
        <div class="slide" id="slide3">
            <h2>👁️ Компьютерное зрение и глубокое обучение</h2>
            <p>Сверточные нейронные сети (CNN) и архитектуры вроде YOLO, EfficientNet обеспечивают высокую точность детекции и сегментации, что критически важно для мобильных роботов.</p>
            <ul>
                <li>Распознавание пешеходов, дорожных знаков, разметки — основа автономного вождения.</li>
                <li>3D-зрение (LiDAR + RGB-D) + нейросетевые методы позволяют роботам "понимать" сцену.</li>
                <li>Пример: роботы-доставщики (Starship, Amazon Scout) используют камеры и семантическую сегментацию.</li>
            </ul>
            <p><strong>🔥 Тренд:</strong> объединение классических алгоритмов и нейросетей для повышения робастности.</p>
        </div>

        <!-- Слайд 4: Обучение с подкреплением и симуляции -->
        <div class="slide" id="slide4">
            <h2>🎮 Обучение с подкреплением и симуляторы</h2>
            <p>Deep Reinforcement Learning (DRL) позволяет роботам обучаться сложным последовательным действиям путём проб и ошибок в виртуальных средах (Gazebo, Isaac Sim, PyBullet).</p>
            <ul>
                <li><strong>Пример:</strong> обучение ходьбы двуногих роботов (ANYmal, Atlas от Boston Dynamics).</li>
                <li><strong>Sim‑to‑real transfer:</strong> перенос политик из симуляции на реальное оборудование с доменами случайности.</li>
                <li>Использование алгоритмов PPO, SAC для управления манипуляторами в логистике и сборке.</li>
            </ul>
        </div>

        <!-- Слайд 5: Применение в промышленности и сервисе -->
        <div class="slide" id="slide5">
            <h2>🏭 Применение: от заводов до здравоохранения</h2>
            <table>
                <thead>
                    <tr><th>Область</th><th>Решения на базе ИИ</th></tr>
                </thead>
                <tbody>
                    <tr><td>Промышленные роботы</td><td>Адаптивная сборка, контроль качества на основе машинного зрения, прогнозирование отказов.</td></tr>
                    <tr><td>Сервисная робототехника</td><td>Роботы-уборщики, помощники в аэропортах, социальные роботы с распознаванием эмоций.</td></tr>
                    <tr><td>Медицина</td><td>Роботизированные хирургические системы (Da Vinci), реабилитационные экзоскелеты.</td></tr>
                    <tr><td>Экстремальная среда</td><td>Роботы-спасатели, подводные дроны с автономной навигацией на основе ИИ.</td></tr>
                </tbody>
            </table>
            <p>ИИ также активно используется в роевой робототехнике (координация группы роботов без центрального управления).</p>
        </div>

        <!-- Слайд 6: Вызовы и будущее -->
        <div class="slide" id="slide6">
            <h2>⚠️ Текущие вызовы и будущие направления</h2>
            <ul>
                <li><strong>Недостаток данных и сложность сбора:</strong> обучение требует больших размеченных наборов или симуляций.</li>
                <li><strong>Обобщение на новые среды:</strong> перенос обученных политик в реальный мир остаётся проблемой.</li>
                <li><strong>Безопасность и интерпретируемость:</strong> необходимость объяснимого ИИ для критических систем.</li>
                <li><strong>Энергоэффективность:</strong> Edge AI и нейроморфные вычисления для бортовых контроллеров.</li>
            </ul>
            <blockquote>🎯 Будущее: фундаментальные модели (Foundation models) + робототехника, мультимодальные агенты и полноценный общей интеллект в машинах.</blockquote>
        </div>

        <!-- Слайд 7: Итоги и заключение -->
        <div class="slide" id="slide7">
            <h2>📌 Заключение</h2>
            <p>Искусственный интеллект — это не просто модное дополнение, а критическая составляющая современной робототехники. От автономного вождения до тонких хирургических операций – везде нейросетевые методы повышают автономность и эффективность.</p>
            <p>Перспективы связаны с усилением симбиоза классических алгоритмов управления и глубокого обучения, развитием робототехнических фундаментальных моделей и массовым внедрением роботов с ИИ в повседневную жизнь.</p>
            <div style="background: #eef3fc; border-radius: 24px; padding: 16px; margin: 20px 0; text-align: center;">
                <strong>💡 Ключевая идея:</strong> «ИИ даёт роботам способность учиться и адаптироваться, открывая возможности, недоступные традиционному программированию».
            </div>
            <p style="margin-top: 20px;">Спасибо за внимание! 🚀</p>
        </div>
    </div>

    <!-- Навигация между слайдами -->
    <div class="nav-buttons">
        <button class="nav-btn" id="prevBtn" aria-label="Предыдущий">◀ Назад</button>
        <span class="slide-counter" id="slideCounter">Слайд 1 из 7</span>
        <button class="nav-btn" id="nextBtn" aria-label="Следующий">Далее ▶</button>
    </div>
    <footer>ИИ в робототехнике — обзор современных технологий | Материал структурирован и адаптирован</footer>
</div>

<script>
    // Управление слайдами
    const slides = document.querySelectorAll('.slide');
    const prevButton = document.getElementById('prevBtn');
    const nextButton = document.getElementById('nextBtn');
    const counterSpan = document.getElementById('slideCounter');
    let currentSlide = 0;
    const totalSlides = slides.length;

    function updateSlides() {
        slides.forEach((slide, idx) => {
            slide.classList.toggle('active', idx === currentSlide);
        });
        counterSpan.innerText = `Слайд ${currentSlide+1} из ${totalSlides}`;
        prevButton.disabled = currentSlide === 0;
        nextButton.disabled = currentSlide === totalSlides - 1;
    }

    function nextSlide() {
        if (currentSlide < totalSlides - 1) {
            currentSlide++;
            updateSlides();
        }
    }

    function prevSlide() {
        if (currentSlide > 0) {
            currentSlide--;
            updateSlides();
        }
    }

    prevButton.addEventListener('click', prevSlide);
    nextButton.addEventListener('click', nextSlide);
    document.addEventListener('keydown', (e) => {
        if (e.key === 'ArrowLeft') prevSlide();
        if (e.key === 'ArrowRight') nextSlide();
    });
    updateSlides();
</script>
</body>
</html>
