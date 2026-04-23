<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
    <title>ИИ в робототехнике | Проект Хаустова Ярослава</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(145deg, #f0f4fa 0%, #d9e1ec 100%);
            color: #1a2c3e;
            line-height: 1.5;
            padding: 0;
            margin: 0;
        }

        /* Контейнер для навигации и страниц */
        .app-container {
            max-width: 1300px;
            margin: 0 auto;
            background: rgba(255,255,255,0.92);
            box-shadow: 0 20px 40px rgba(0,0,0,0.1);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            border-radius: 0;
        }

        /* Шапка с навигацией */
        .nav-bar {
            background: #0b2b3b;
            backdrop-filter: blur(4px);
            padding: 0.8rem 1.5rem;
            position: sticky;
            top: 0;
            z-index: 100;
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 0.4rem;
            box-shadow: 0 4px 12px rgba(0,0,0,0.2);
            border-bottom: 2px solid #2aa5b0;
        }

        .nav-btn {
            background: #1f4e6e;
            border: none;
            color: white;
            font-size: 1rem;
            font-weight: 600;
            padding: 0.6rem 1.2rem;
            border-radius: 40px;
            cursor: pointer;
            transition: 0.2s;
            font-family: inherit;
            letter-spacing: 0.3px;
            box-shadow: 0 1px 3px rgba(0,0,0,0.2);
        }

        .nav-btn:hover {
            background: #2aa5b0;
            transform: translateY(-2px);
        }

        .nav-btn.active {
            background: #f4c542;
            color: #0b2b3b;
            box-shadow: 0 0 8px #f4c542;
        }

        /* Основная область — страницы */
        .pages-container {
            flex: 1;
            position: relative;
            background: #ffffff;
            margin: 1rem;
            border-radius: 2rem;
            box-shadow: 0 8px 20px rgba(0,0,0,0.05);
            overflow: hidden;
            min-height: 70vh;
        }

        .page {
            display: none;
            padding: 2rem 2rem 3rem 2rem;
            animation: fade 0.3s ease;
            background: white;
        }

        .page.active-page {
            display: block;
        }

        @keyframes fade {
            from { opacity: 0; transform: translateY(8px);}
            to { opacity: 1; transform: translateY(0);}
        }

        /* Типографика */
        h1 {
            font-size: 2.2rem;
            background: linear-gradient(135deg, #0b2b3b, #1d7a8c);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            margin-bottom: 1rem;
            border-left: 8px solid #f4c542;
            padding-left: 1rem;
        }

        h2 {
            font-size: 1.8rem;
            color: #1f4e6e;
            margin: 1.2rem 0 0.8rem 0;
            border-bottom: 2px solid #cbdbe2;
            display: inline-block;
        }

        h3 {
            font-size: 1.4rem;
            color: #2aa5b0;
            margin: 1rem 0 0.5rem;
        }

        .slide-title {
            font-size: 1.9rem;
            font-weight: 700;
            margin-bottom: 1rem;
            color: #0b2b3b;
        }

        .card-info {
            background: #f8fafc;
            border-radius: 1.5rem;
            padding: 1.5rem;
            margin: 1.2rem 0;
            border-left: 6px solid #f4c542;
            box-shadow: 0 5px 12px rgba(0,0,0,0.03);
        }

        .grid-2 {
            display: flex;
            flex-wrap: wrap;
            gap: 1.5rem;
            margin: 1.5rem 0;
        }

        .grid-item {
            flex: 1 1 250px;
            background: #fef9e6;
            padding: 1rem;
            border-radius: 1.2rem;
            border-bottom: 3px solid #f4c542;
        }

        ul, ol {
            margin: 0.8rem 0 0.8rem 1.5rem;
        }
        li {
            margin: 0.4rem 0;
        }
        .badge {
            background: #1f4e6e;
            color: white;
            padding: 0.2rem 0.8rem;
            border-radius: 50px;
            font-size: 0.8rem;
            display: inline-block;
            margin-bottom: 0.5rem;
        }
        footer {
            text-align: center;
            padding: 1rem;
            font-size: 0.8rem;
            color: #5a6e7c;
            border-top: 1px solid #dce5ec;
            background: #f9fbfd;
        }
        @media (max-width: 680px) {
            .nav-btn { padding: 0.4rem 0.8rem; font-size: 0.8rem; }
            .page { padding: 1.2rem; }
            h1 { font-size: 1.7rem; }
        }
        .code-block {
            background: #1e2a32;
            color: #e2f0fa;
            font-family: monospace;
            padding: 0.8rem;
            border-radius: 14px;
            overflow-x: auto;
            margin: 1rem 0;
            font-size: 0.85rem;
        }
        hr {
            margin: 1rem 0;
            border: 0;
            height: 2px;
            background: linear-gradient(to right, #c0d4e3, transparent);
        }
        .robot-icon {
            font-size: 2rem;
            text-align: center;
        }
    </style>
</head>
<body>
<div class="app-container">
    <div class="nav-bar" id="navBar">
        <!-- навигационные кнопки будут созданы js на основе структуры -->
    </div>
    <div class="pages-container" id="pagesContainer">
        <!-- страницы будут генерироваться из данных -->
    </div>
    <footer>
        📡 Проект ученика 10 класса «Б» Хаустова Ярослава | Руководитель: Бехтева Елена Владимировна<br>
        МОУ Раменская СОШ №5 • Искусственный интеллект в робототехнике • GitHub Pages
    </footer>
</div>

<script>
    // Определяем структуру слайдов согласно презентации (каждый слайд = страница)
    const slidesData = [
        {
            id: "title",
            title: "Титульный слайд",
            content: `
                <div style="text-align: center; padding: 2rem 0;">
                    <div class="robot-icon">🤖🧠</div>
                    <h1 style="font-size: 2.8rem; background: linear-gradient(135deg,#0b2b3b,#1f8a9c); -webkit-background-clip:text; background-clip:text; color:transparent;">Искусственный интеллект<br>в робототехнике</h1>
                    <div style="margin: 2rem 0; font-size: 1.3rem;">
                        <p><strong>Выполнил:</strong> ученик 10 класса «Б»<br> МОУ Раменской СОШ №5<br> <span style="font-size:1.5rem;">Хаустов Ярослав</span></p>
                        <p><strong>Руководитель проекта:</strong> Бехтева Елена Владимировна</p>
                    </div>
                    <div style="margin-top: 2rem; font-style: italic;">⚙️ ИИ как переводчик между человеком и машиной ⚙️</div>
                </div>
            `
        },
        {
            id: "contents",
            title: "Оглавление",
            content: `
                <div class="slide-title">📖 Содержание проекта</div>
                <div class="grid-2">
                    <div class="grid-item"><strong>1. Введение</strong><br>Актуальность, гипотезы, цели и задачи</div>
                    <div class="grid-item"><strong>2. Основная часть</strong><br>Вступление, цели, задачи, ESP32, Лидар, шаговые двигатели, драйвер, схема, интеграция ИИ</div>
                    <div class="grid-item"><strong>3. Заключение</strong><br>Выводы и итоги</div>
                    <div class="grid-item"><strong>4. Список литературы</strong><br>Источники</div>
                </div>
                <div class="card-info">📌 Навигация сверху — каждый раздел соответствует слайдам презентации.</div>
            `
        },
        {
            id: "intro_why",
            title: "Вступление",
            content: `
                <div class="slide-title">🤖 Вступление: почему я решил сделать робота с ИИ?</div>
                <div class="card-info">
                    <p style="font-size:1.2rem;">⭐ <strong>Моя цель — избавление человечества от рутинных задач</strong>, и с этим мне поможет мой робот с искусственным интеллектом.</p>
                    <p>Современные технологии способны взять на себя монотонную работу, освободив время для творчества и развития. ИИ в робототехнике — ключ к этому будущему.</p>
                </div>
                <div style="background: #eef2fa; border-radius: 1rem; padding: 1rem;">
                    <span class="badge">ВДОХНОВЕНИЕ</span>
                    <p>Создание робота, который понимает человека и анализирует окружение — вызов, который даёт мощный импульс к изучению программирования, электроники и машинного обучения.</p>
                </div>
            `
        },
        {
            id: "actuality_hypothesis",
            title: "Актуальность и гипотезы",
            content: `
                <div class="slide-title">📌 Актуальность</div>
                <div class="card-info">В настоящее время программировать робота достаточно трудно, поэтому я ставлю между человеком и машиной <strong>«переводчика» в виде ИИ</strong>. Искусственный интеллект упрощает разработку и взаимодействие.</div>
                <h3>🔍 Гипотезы:</h3>
                <ul>
                    <li>1. Искусственный интеллект поможет оптимизировать работу человека.</li>
                    <li>2. Он сделает взаимодействие человека и машины легче.</li>
                </ul>
                <div class="grid-2">
                    <div class="grid-item"><strong>🎯 Цель:</strong> Сделать робота с ИИ, способного к восприятию окружения.</div>
                    <div class="grid-item"><strong>📋 Задачи:</strong> ① Сделать схему ② Собрать по схеме ③ Написать код ④ Протестировать ⑤ Проверить в компиляторе.</div>
                </div>
            `
        },
        {
            id: "esp32",
            title: "Что такое ESP32?",
            content: `
                <div class="slide-title">📡 Микроконтроллер ESP32</div>
                <div class="card-info">
                    <p><strong>ESP32</strong> — серия недорогих микросхем с малым энергопотреблением китайской компании <strong>Espressif Systems</strong>. Представляют собой систему на кристалле с интегрированными контроллерами радиосвязи <strong>Wi-Fi, Bluetooth и Thread</strong>.</p>
                    <p>В сериях ESP32 и ESP32-S используются процессорные ядра с архитектурой компании Tensilica.</p>
                </div>
                <div class="code-block">
                    // ESP32 идеально подходит для роботов с ИИ:<br>
                    // Двухъядерный процессор, поддержка нейросетевых библиотек, GPIO, I2C, SPI.
                </div>
                <p>✅ Именно ESP32 станет «мозгом» нашего робота, обрабатывая данные с лидара и управляя моторами.</p>
            `
        },
        {
            id: "lidar",
            title: "Лидар: устройство и схема",
            content: `
                <div class="slide-title">💡 Лидар (LiDAR)</div>
                <div class="card-info">
                    <p><strong>Лидар</strong> — технология, которая использует импульсы (чаще всего лазерные) для измерения расстояния до объектов. Название от <em>Light Detection and Ranging</em> — «обнаружение и определение дальности с помощью света».</p>
                    <p>🔹 Устройство испускает лазерные лучи, которые отражаются от объектов и возвращаются к датчику. У света постоянная скорость — лидар фиксирует время возврата луча и рассчитывает точное расстояние.</p>
                    <p>🔹 Чтобы собрать максимум данных, лидар вращается или использует массив лазеров.</p>
                </div>
                <h3>📐 Схема подключения лидара к ESP32:</h3>
                <ul>
                    <li>Лидар → UART (TX/RX) ESP32 для передачи данных.</li>
                    <li>Питание 5В через стабилизатор.</li>
                    <li>Обработка облака точек для SLAM и навигации.</li>
                </ul>
                <div class="code-block">// Псевдокод получения данных с лидара: расстояние и угол</div>
            `
        },
        {
            id: "stepper_motors",
            title: "Шаговые двигатели",
            content: `
                <div class="slide-title">⚙️ Шаговые двигатели</div>
                <div class="card-info">
                    <p><strong>Шаговые двигатели</strong> — электромеханические устройства, которые преобразуют электрические импульсы в дискретные механические перемещения. Вал вращается на фиксированный угол (шаг) при каждом импульсе.</p>
                    <p>Применяются в робототехнике для точного управления положением колёс, манипуляторов и поворотных механизмов.</p>
                </div>
                <h3>📌 Преимущества:</h3>
                <ul>
                    <li>Высокая точность позиционирования</li>
                    <li>Удержание момента без обратной связи</li>
                    <li>Простота управления с помощью драйверов</li>
                </ul>
            `
        },
        {
            id: "driver",
            title: "Драйвер шагового двигателя",
            content: `
                <div class="slide-title">🔌 Драйвер шагового двигателя</div>
                <div class="card-info">
                    <p>Драйвер (например, A4988, DRV8825) преобразует управляющие сигналы от микроконтроллера в токовые импульсы для обмоток шагового двигателя. Это позволяет управлять скоростью, направлением и микрошагом.</p>
                    <p><strong>Роль в роботе:</strong> ESP32 отправляет STEP/DIR сигналы драйверу, который вращает двигатель точно и плавно. Интеграция с ИИ — автоматическое построение маршрута на основе данных с лидара.</p>
                </div>
                <div class="code-block">
                    // Пример: инициализация драйвера через библиотеку AccelStepper<br>
                    // enable pin, step pin , dir pin - управление от ИИ
                </div>
            `
        },
        {
            id: "robot_scheme",
            title: "Схема робота",
            content: `
                <div class="slide-title">🧩 Общая схема робота с ИИ</div>
                <div class="card-info">
                    <p><strong>Компоненты:</strong> ESP32 (главный контроллер), Лидар (датчик окружения), 2+ шаговых двигателя на колёсную базу, драйверы двигателей, источник питания (Li-ion аккумуляторы), возможно IMU для одометрии.</p>
                    <p>🔌 <strong>Структурная схема:</strong> Лидар → UART (ESP32) → алгоритмы SLAM и ИИ (принятие решений) → драйверы → шаговые двигатели → движение робота.</p>
                </div>
                <div style="background:#eef2f5; border-radius:1rem; padding:1rem;">
                    📋 Этапы сборки: монтаж шасси, установка ESP32 и драйверов, подключение лидара через уровень логики, написание кода для обработки данных с последующей интеграцией ИИ-модуля (TensorFlow Lite Micro).
                </div>
            `
        },
        {
            id: "ai_integration",
            title: "Интеграция ИИ",
            content: `
                <div class="slide-title">🧠 Интеграция искусственного интеллекта</div>
                <div class="card-info">
                    <p><strong>Как ИИ помогает роботу?</strong> Нейросетевые алгоритмы классификации препятствий, планирование маршрута, распознавание объектов и голосовые команды. ИИ выступает как «переводчик» между сложной логикой и аппаратурой.</p>
                    <p>🔹 Использование библиотек машинного обучения на ESP32 (например, TensorFlow Lite Micro) — позволяет запускать небольшие модели прямо на микроконтроллере.</p>
                    <p>🔹 Интеграция ИИ ускоряет разработку: вместо прописывания тысяч условий, модель обучается избегать препятствия и оптимизировать движение.</p>
                </div>
                <div class="grid-2">
                    <div class="grid-item"><strong>✨ Результат интеграции:</strong> Робот самостоятельно строит карту помещения, избегает препятствия, распознаёт маркеры и оптимизирует траекторию.</div>
                    <div class="grid-item"><strong>📡 Код на Python/С++:</strong> ИИ модуль на хосте либо на ESP32 для лёгких задач + связь с компьютером для сложной обработки.</div>
                </div>
            `
        },
        {
            id: "conclusion",
            title: "Заключение",
            content: `
                <div class="slide-title">🎯 Заключение</div>
                <div class="card-info">
                    <p>В ходе проекта была разработана концепция робота с искусственным интеллектом на базе ESP32, лидара и шаговых двигателей. ИИ упрощает программирование сложного поведения, снижает порог входа в робототехнику и открывает возможности для создания адаптивных автономных систем.</p>
                    <p>✅ <strong>Гипотезы подтверждены:</strong> ИИ помогает оптимизировать работу человека и делает взаимодействие с машиной легче.<br>
                    ✅ Цель «Сделать робота с ИИ» достигнута на уровне проектной проработки схемы и алгоритмов.</p>
                    <p>Дальнейшее развитие: создание полнофункционального прототипа, обучение модели на реальных данных, публикация open-source кода.</p>
                </div>
                <div class="robot-icon">🚀🤖</div>
            `
        },
        {
            id: "literature",
            title: "Список литературы",
            content: `
                <div class="slide-title">📚 Список литературы и источников</div>
                <ul style="font-size:1.05rem;">
                    <li>Espressif Systems. Документация по ESP32. — URL: https://www.espressif.com/</li>
                    <li>Лидарные технологии: принципы работы и применение / под ред. А.В. Соколова. — М.: Техносфера, 2022.</li>
                    <li>У. Сандберг. «Программирование шаговых двигателей для роботов». — СПб.: БХВ, 2021.</li>
                    <li>TensorFlow Lite Micro — официальная документация для микроконтроллеров.</li>
                    <li>Материалы open-source проектов: ROS, SLAM, и интеграция ИИ в робототехнику.</li>
                    <li>Хаустов Я. Собственные наработки схемы робота, 2025 г.</li>
                </ul>
                <div class="card-info" style="margin-top: 1rem;">* Все электронные ресурсы актуальны на момент написания проекта.</div>
            `
        }
    ];

    // Функция рендера навигации и страниц
    function buildSite() {
        const navBar = document.getElementById('navBar');
        const pagesContainer = document.getElementById('pagesContainer');

        // Очистка
        navBar.innerHTML = '';
        pagesContainer.innerHTML = '';

        // создаем кнопки и страницы
        slidesData.forEach((slide, index) => {
            // Кнопка навигации
            const btn = document.createElement('button');
            btn.className = 'nav-btn';
            // короткое название для навигации (обрезаем, но читаемо)
            let shortTitle = slide.title;
            if (shortTitle.length > 18) shortTitle = shortTitle.slice(0, 16) + '..';
            btn.textContent = shortTitle;
            btn.dataset.id = slide.id;
            btn.addEventListener('click', () => {
                setActivePage(slide.id);
            });
            navBar.appendChild(btn);

            // Страница
            const pageDiv = document.createElement('div');
            pageDiv.className = 'page';
            pageDiv.id = `page-${slide.id}`;
            pageDiv.innerHTML = `
                <div style="margin-bottom: 10px;">
                    <span class="badge">Слайд ${index+1} / ${slidesData.length}</span>
                </div>
                ${slide.content}
                <hr>
                <div style="display: flex; justify-content: space-between; margin-top: 1rem;">
                    <button class="nav-prev" style="background:#e2e8f0; border:none; padding:0.5rem 1rem; border-radius:2rem; cursor:pointer;">◀ Предыдущий</button>
                    <button class="nav-next" style="background:#e2e8f0; border:none; padding:0.5rem 1rem; border-radius:2rem; cursor:pointer;">Следующий ▶</button>
                </div>
            `;
            pagesContainer.appendChild(pageDiv);
        });

        // добавим обработчики для кнопок предыдущий/следующий после рендера страниц
        document.querySelectorAll('.page').forEach((page, idx) => {
            const prevBtn = page.querySelector('.nav-prev');
            const nextBtn = page.querySelector('.nav-next');
            if (prevBtn) {
                prevBtn.addEventListener('click', () => {
                    if (idx > 0) {
                        const prevId = slidesData[idx-1].id;
                        setActivePage(prevId);
                    }
                });
            }
            if (nextBtn) {
                nextBtn.addEventListener('click', () => {
                    if (idx < slidesData.length-1) {
                        const nextId = slidesData[idx+1].id;
                        setActivePage(nextId);
                    }
                });
            }
        });

        // установка активной страницы по умолчанию (первая)
        function setActivePage(id) {
            // скрываем все страницы
            document.querySelectorAll('.page').forEach(page => {
                page.classList.remove('active-page');
            });
            const activePageEl = document.getElementById(`page-${id}`);
            if (activePageEl) activePageEl.classList.add('active-page');

            // активируем кнопки стилем
            document.querySelectorAll('.nav-btn').forEach(btn => {
                if (btn.dataset.id === id) {
                    btn.classList.add('active');
                } else {
                    btn.classList.remove('active');
                }
            });
            // прокрутка вверх
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }

        // активируем титульный слайд
        setActivePage('title');
    }

    buildSite();
</script>
</body>
</html>
