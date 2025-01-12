<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <title>Интерактивная страница</title>
    <link href="https://fonts.googleapis.com/css?family=Poppins:100,200,300,400,500,600,700,800,900" rel="stylesheet">
      <style>
        @font-face {
            font-family: 'Intro';
            src: url('intro.otf') format('opentype');
        }

        body {
            background-image: url('fon.png');
            background-size: cover;
            background-position: center;
            background-repeat: no-repeat;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }

        .main-container {
            display: flex;
            flex-direction: column;
            align-items: center;
            width: 85%; /* Slightly smaller than before */
        }

        .container {
            display: flex;
            flex-direction: column;
            align-items: center;
            background-color: #0a101e;
            border-radius: 12px; /* Smaller radius */
            padding: 8px; /* Smaller padding */
            box-shadow: 0 3px 6px rgba(0,0,0,0.05), 0 0 8px 4px #ffa500; /* Subtler shadow */
        }

        .grid {
            display: grid;
            grid-template-columns: repeat(5, 45px); /* Smaller cells */
            grid-template-rows: repeat(5, 45px);
            gap: 7px; /* Smaller gaps */
        }

        .square {
            background-color: #238fa9;
            border-radius: 4px; /* Smaller border radius */
            transition: background-color 0.5s ease;
        }

        button {
            margin-top: 10px;
            padding: 10px 18px; /* Reduced padding */
            border: none;
            border-radius: 6px; /* Smaller radius */
            background-color: #000000;
            color: white;
            font-size: 14px; /* Reduced font size */
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 2px 3.5px rgba(0, 0, 0, 0.15); /* Subtler shadow */
            font-family: 'Intro', sans-serif;
            text-align: center;
            line-height: 1.1; /* Closer line height */
        }

        button:hover, button:focus {
            background-color: #0056b3;
            box-shadow: 0 2.5px 5px rgba(0, 0, 0, 0.25); /* Subtle change on hover */
            transform: translateY(-1px);
        }

        button:active {
            background-color: #004885;
            box-shadow: 0 1px 2px rgba(0, 0, 0, 0.1); /* Less shadow on active */
            transform: translateY(0.5px);
        }

        #trap-count-label {
            margin-top: 20px;
            font-size: 28px; /* Smaller font size */
            color: white;
            font-family: 'Intro', sans-serif;
            font-weight: bold;
        }
        .return-button {
            margin-top: 10px;
            padding: 10px 18px; /* Reduced padding */
            border: none;
            border-radius: 6px; /* Smaller radius */
            background-color: #000000;
            color: white;
            font-size: 14px; /* Reduced font size */
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 2px 3.5px rgba(0, 0, 0, 0.15); /* Subtler shadow */
            font-family: 'Intro', sans-serif;
            text-align: center;
            line-height: 1.1; /* Closer line height */
        }
        
        #counter-container {
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 4px 0; /* Smaller margin */
        }

        .count-display {
            width: 35px; /* Smaller width */
            text-align: center;
            font-size: 35px; /* Smaller font size */
            font-family: 'Intro', sans-serif;
            color: white;
            margin: 0 12px; /* Smaller margins */
        }

        .icon {
            cursor: pointer;
            width: 50px; /* Smaller icons */
            height: 50px;
        }

        #loading-text {
            cursor: default;
            text-align: center;
            margin-bottom: 8px; /* Smaller bottom margin */
            font-family: 'Intro', sans-serif;
        }

        #loading-text span {
            display: inline-block;
            animation: bounce 0.3s ease infinite alternate;
            font-size: 50px; /* Smaller font size */
            color: rgb(209, 178, 5);
            text-shadow: 0 0.25px 0 #ccc, 0 0.5px 0 #ccc, 0 0.75px 0 #ccc, 0 1px 0 #ccc,
                        0 1.25px 0 #ccc, 0 1.5px 0 transparent, 0 1.75px 0 transparent, 0 2px 0 transparent,
                        0 2.25px 0 transparent, 0 2.5px 2.5px rgba(0, 0, 0, 0.2);
        }
        
        #loading-text span:nth-child(1) { animation-delay: 0s; }
        #loading-text span:nth-child(2) { animation-delay: 0.1s; }
        #loading-text span:nth-child(3) { animation-delay: 0.2s; }
        #loading-text span:nth-child(4) { animation-delay: 0.3s; }
        #loading-text span:nth-child(5) { animation-delay: 0.4s; }
        #loading-text span:nth-child(6) { animation-delay: 0.5s; }
        #loading-text span:nth-child(7) { animation-delay: 0.6s; }

        @keyframes bounce {
            0% {
                transform: translateY(0px);
                text-shadow: 0 0.25px 0 #ccc, 0 0.5px 0 #ccc, 0 0.75px 0 #ccc, 0 1px 0 #ccc,
                             0 1.25px 0 #ccc, 0 1.5px 0 transparent, 0 1.75px 0 transparent, 0 2px 0 transparent,
                             0 2.25px 0 transparent, 0 2.5px 2.5px rgba(0, 0, 0, 0.2);
            }
            100% {
                transform: translateY(-5px);
                text-shadow: 0 0.25px 0 #ccc, 0 0.5px 0 #ccc, 0 0.75px 0 #ccc, 0 1px 0 #ccc,
                             0 1.25px 0 #ccc, 0 1.5px 0 transparent, 0 1.75px 0 transparent, 0 2px 0 transparent,
                             0 2.25px 0 transparent, 0 12.5px 6.25px rgba(0, 0, 0, 0.1);
            }
        }
    </style>
</head>
<body>
    <div class="main-container">
        <h1 id="loading-text">
            <span>B</span><span>E</span><span>S</span><span>T</span><span>_</span><span>S</span><span>I</span><span>G</span><span>N</span><span>A</span><span>L</span><span>S</span>
        </h1>
        <div class="container">
            <div class="grid" id="grid">
                <!-- Квадраты будут добавлены здесь с помощью JavaScript -->
            </div>
        </div>
        <div id="trap-count-label">КОЛ-ВО ЛОВУШЕК</div>
        <div id="counter-container">
            <img class="control-button icon" src="minus.png" onclick="decrement()" alt="Minus">
            <span id="count" class="count-display">3</span>
            <img class="control-button icon" src="plus.png" onclick="increment()" alt="Plus">
        </div>
        <button onclick="getSignal()">Получить<br>сигнал</button>
    </div>
    <audio id="sound-effect" src="1.mp3"></audio> <!-- Звуковой эффект для воспроизведения -->
    <script>
        let count = 3; // Начальное количество ловушек
        const countElement = document.getElementById('count');
        const soundEffect = document.getElementById('sound-effect');

    // Функция увеличения количества ловушек
    function increment() {
        const validTraps = [1, 3, 5, 7]; // Допустимые значения количества ловушек
        let currentIndex = validTraps.indexOf(count);
        if (currentIndex < validTraps.length - 1) {
            count = validTraps[currentIndex + 1];
            countElement.textContent = count;
        }
    }

    // Функция уменьшения количества ловушек
    function decrement() {
        const validTraps = [1, 3, 5, 7]; // Допустимые значения количества ловушек
        let currentIndex = validTraps.indexOf(count);
        if (currentIndex > 0) {
            count = validTraps[currentIndex - 1];
            countElement.textContent = count;
        }
    }

    // Создание ячеек на сетке
    function createSquares() {
        const grid = document.getElementById('grid');
        for (let i = 0; i < 25; i++) {
            const square = document.createElement('div');
            square.className = 'square';
            grid.appendChild(square);
        }
    }

    // Определение количества ячеек для открытия в зависимости от количества ловушек
    function squaresToOpen() {
        switch (count) {
            case 1:
                return 10; // Если выбрана 1 ловушка, открываем 10 ячеек
            case 3:
                return 5;  // Если выбрано 3 ловушки, открываем 5 ячеек
            case 5:
                return 4;  // Если выбрано 5 ловушек, открываем 4 ячейки
            case 7:
                return 3;  // Если выбрано 7 ловушек, открываем 3 ячейки
            default:
                return 3;  // Значение по умолчанию
        }
    }

    // Функция, запускающая процесс открытия ячеек и воспроизведение звука
    function getSignal() {
        const squares = document.querySelectorAll('.square');
        squares.forEach(square => {
            square.style.backgroundColor = '#238fa9';
            square.innerHTML = '';
        });

        let indices = new Set();
        const cellsToOpen = squaresToOpen(); // Получаем количество ячеек для открытия

        while (indices.size < cellsToOpen) {
            indices.add(Math.floor(Math.random() * squares.length));
        }

        let delay = 0;
        indices.forEach(index => {
            setTimeout(() => {
                const audio = new Audio('1.mp3');
                audio.play();
                const square = squares[index];
                square.style.backgroundColor = '#0a101e';
                square.innerHTML = '<div style="width: 100%; height: 100%; background: url(\'star.svg\') center/contain no-repeat;"></div>';
            }, delay);
            delay += 1000; // Задержка 1 секунда
        });
    }

    window.onload = function() {
        createSquares();
    }
</script>
</body>
</html>
