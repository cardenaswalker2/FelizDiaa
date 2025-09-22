<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Un Jardín de Flores para Ti</title>
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&display=swap" rel="stylesheet">
    <style>
        :root {
            --flower-yellow-light: #FFEB3B;
            --flower-yellow-dark: #FFC107;
            --flower-center: #FFA000;
            --stem-green-light: #64DD17;
            --stem-green-dark: #33691E;
            --foliage-green-light: #4CAF50;
            --foliage-green-dark: #2E7D32;
            --sky-dark: #0A192F;
            --sky-medium: #152A4A;
            --glow-color-yellow: #FFFF00;
            --glow-color-orange: #FFA500;
            --text-color: #FFFDE7;
            --petal-pink-light: #FFBCD9; /* Nuevo color para flores variadas */
            --petal-pink-dark: #FF85B2;
            --petal-purple-light: #E0BBE4;
            --petal-purple-dark: #957DAD;
            --petal-blue-light: #A7D9FD; /* Añadido color azul */
            --petal-blue-dark: #5FA8D3;
        }

        body {
            margin: 0;
            overflow: hidden;
            background: radial-gradient(circle at bottom center, var(--sky-medium) 0%, var(--sky-dark) 100%);
            display: flex;
            justify-content: center;
            align-items: flex-end;
            min-height: 100vh;
            font-family: 'Dancing Script', cursive;
            position: relative;
            perspective: 1500px; /* Mayor perspectiva para un 3D más pronunciado */
        }

        .night-sky-background {
            position: absolute;
            width: 100%;
            height: 100%;
            background: linear-gradient(to bottom, #000000 0%, #050A1C 50%, #0A192F 100%);
            z-index: 1;
        }

        .star {
            position: absolute;
            background-color: rgba(255, 255, 255, 0.9);
            border-radius: 50%;
            box-shadow: 0 0 5px rgba(255, 255, 255, 0.7);
            opacity: 0;
            animation: twinkle 4s infinite ease-in-out alternate;
            z-index: 2;
        }

        @keyframes twinkle {
            0% { opacity: 0.2; transform: scale(0.6); }
            50% { opacity: 1; transform: scale(1.1); }
            100% { opacity: 0.2; transform: scale(0.6); }
        }

        .flower-container {
            position: relative;
            z-index: 10;
            display: flex;
            align-items: flex-end;
            gap: 25px; /* Menos espacio para un jardín más denso */
            padding-bottom: 50px;
            transform-style: preserve-3d;
        }

        .flower {
            display: flex;
            flex-direction: column;
            align-items: center;
            position: relative;
            transform-style: preserve-3d;
            animation: sway 6s ease-in-out infinite alternate;
            margin-bottom: -30px; /* Para que las flores se solapen un poco en la base */
        }

        /* Variaciones para la animación de las flores */
        .flower:nth-child(even) { animation-delay: 0.3s; transform: translateZ(-20px) rotateY(3deg); }
        .flower:nth-child(odd) { animation-delay: 0s; transform: translateZ(0px) rotateY(-3deg); }
        .flower:nth-child(3n) { animation-delay: 0.6s; transform: translateZ(-10px) rotateY(1deg); }
        .flower:nth-child(4n) { animation-delay: 0.9s; transform: translateZ(-30px) rotateY(-2deg); }


        @keyframes sway {
            0% { transform: rotateY(0deg) translateY(0px) rotateX(5deg); }
            50% { transform: rotateY(5deg) translateY(-8px) rotateX(0deg); }
            100% { transform: rotateY(-5deg) translateY(0px) rotateX(5deg); }
        }

        .stem {
            width: 12px;
            height: 200px;
            background: linear-gradient(to top, var(--stem-green-dark), var(--stem-green-light));
            border-radius: 6px;
            position: relative;
            transform-origin: bottom center;
            box-shadow: inset 1px 0 5px rgba(0,0,0,0.3);
            transform: rotateX(10deg);
        }

        .leaf {
            position: absolute;
            background: linear-gradient(to right, var(--foliage-green-dark), var(--foliage-green-light));
            width: 60px;
            height: 100px;
            border-radius: 0 70% 50% 0;
            transform-origin: top left;
            opacity: 0.9;
            box-shadow: 2px 2px 8px rgba(0,0,0,0.4);
            transform: translateZ(5px); /* Para un efecto 3D sutil */
        }
        .leaf.left {
            transform: rotate(-55deg) translateZ(5px);
            left: -40px;
            top: 60px;
        }
        .leaf.right {
            transform: rotate(55deg) translateZ(5px);
            right: -40px;
            top: 100px;
            border-radius: 70% 0 0 50%;
        }

        .petal-group {
            position: absolute;
            bottom: 180px;
            width: 100px;
            height: 100px;
            display: flex;
            justify-content: center;
            align-items: center;
            transform-style: preserve-3d;
            animation: flower-glow 3s infinite alternate ease-in-out;
        }

        @keyframes flower-glow {
            0% { filter: drop-shadow(0 0 15px rgba(255, 255, 0, 0.8)) drop-shadow(0 0 25px rgba(255, 165, 0, 0.5)); }
            100% { filter: drop-shadow(0 0 25px rgba(255, 255, 0, 1)) drop-shadow(0 0 40px rgba(255, 165, 0, 0.7)); }
        }

        .petal {
            position: absolute;
            width: 50px;
            height: 80px;
            background: radial-gradient(circle at top, var(--flower-yellow-light) 0%, var(--flower-yellow-dark) 100%);
            border-radius: 50% 50% 25% 25%;
            box-shadow: 0 5px 10px rgba(0,0,0,0.3), inset 0 2px 5px rgba(255,255,200,0.5);
            transform-origin: bottom center;
        }
        /* Variaciones de color para los pétalos */
        .flower:nth-child(4n + 1) .petal { /* Amarillas */
            background: radial-gradient(circle at top, var(--flower-yellow-light) 0%, var(--flower-yellow-dark) 100%);
            box-shadow: 0 5px 10px rgba(0,0,0,0.3), inset 0 2px 5px rgba(255,255,200,0.5);
        }
        .flower:nth-child(4n + 2) .petal { /* Rosas */
            background: radial-gradient(circle at top, var(--petal-pink-light) 0%, var(--petal-pink-dark) 100%);
            box-shadow: 0 5px 10px rgba(0,0,0,0.3), inset 0 2px 5px rgba(255,200,220,0.5);
        }
        .flower:nth-child(4n + 3) .petal { /* Moradas */
            background: radial-gradient(circle at top, var(--petal-purple-light) 0%, var(--petal-purple-dark) 100%);
            box-shadow: 0 5px 10px rgba(0,0,0,0.3), inset 0 2px 5px rgba(220,200,255,0.5);
        }
        .flower:nth-child(4n + 4) .petal { /* Azules */
            background: radial-gradient(circle at top, var(--petal-blue-light) 0%, var(--petal-blue-dark) 100%);
            box-shadow: 0 5px 10px rgba(0,0,0,0.3), inset 0 2px 5px rgba(200,220,255,0.5);
        }


        /* Rotaciones para el efecto 3D de los pétalos */
        .petal:nth-child(1) { transform: rotateX(15deg) rotateY(0deg) translateZ(10px) translateY(-25px); }
        .petal:nth-child(2) { transform: rotateX(15deg) rotateY(60deg) translateZ(10px) translateY(-25px); }
        .petal:nth-child(3) { transform: rotateX(15deg) rotateY(120deg) translateZ(10px) translateY(-25px); }
        .petal:nth-child(4) { transform: rotateX(15deg) rotateY(180deg) translateZ(10px) translateY(-25px); }
        .petal:nth-child(5) { transform: rotateX(15deg) rotateY(240deg) translateZ(10px) translateY(-25px); }
        .petal:nth-child(6) { transform: rotateX(15deg) rotateY(300deg) translateZ(10px) translateY(-25px); }

        .center {
            position: absolute;
            width: 35px;
            height: 35px;
            background: radial-gradient(circle, var(--flower-center) 0%, var(--flower-yellow-dark) 100%);
            border-radius: 50%;
            z-index: 1;
            box-shadow: 0 0 15px var(--glow-color-yellow), inset 0 0 10px rgba(255, 255, 200, 0.7);
            transform: translateZ(20px);
            animation: center-pulse 2s infinite alternate;
        }
        /* Centros de flores variadas */
        .flower:nth-child(4n + 1) .center { /* Amarillo */
            background: radial-gradient(circle, var(--flower-center) 0%, var(--flower-yellow-dark) 100%);
            box-shadow: 0 0 15px var(--glow-color-yellow), inset 0 0 10px rgba(255, 255, 200, 0.7);
        }
        .flower:nth-child(4n + 2) .center { /* Rosa */
            background: radial-gradient(circle, #FF6F9C 0%, var(--petal-pink-dark) 100%);
            box-shadow: 0 0 15px #FF6F9C, inset 0 0 10px rgba(255, 180, 200, 0.7);
        }
        .flower:nth-child(4n + 3) .center { /* Morado */
            background: radial-gradient(circle, #A282B9 0%, var(--petal-purple-dark) 100%);
            box-shadow: 0 0 15px #A282B9, inset 0 0 10px rgba(200, 180, 255, 0.7);
        }
        .flower:nth-child(4n + 4) .center { /* Azul */
            background: radial-gradient(circle, #6EB5FF 0%, var(--petal-blue-dark) 100%);
            box-shadow: 0 0 15px #6EB5FF, inset 0 0 10px rgba(180, 200, 255, 0.7);
        }

        @keyframes center-pulse {
            0% { transform: translateZ(20px) scale(1); box-shadow: 0 0 15px var(--glow-color-yellow); }
            100% { transform: translateZ(20px) scale(1.05); box-shadow: 0 0 25px var(--glow-color-yellow), 0 0 35px var(--glow-color-orange); }
        }

        .ground-foliage-area {
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 350px; /* Más alto para una base más robusta */
            background: linear-gradient(to top, #0A2010 0%, #14331C 30%, #2E7D32 70%, #4CAF50 100%);
            border-radius: 60% 60% 0 0 / 20% 20% 0 0;
            z-index: 5;
            box-shadow: inset 0 10px 40px rgba(0,0,0,0.6);
            transform: translateZ(-80px) rotateX(15deg); /* Más profundidad y rotación */
        }

        .grass-blade {
            position: absolute;
            width: 15px;
            height: 100px;
            background: linear-gradient(to top, #2b8a3e, #4CAF50);
            border-radius: 8px 8px 0 0;
            transform-origin: bottom center;
            bottom: 0;
            z-index: 6;
            box-shadow: 0 0 8px rgba(0,0,0,0.3);
            animation: grass-sway 5s ease-in-out infinite alternate;
        }

        @keyframes grass-sway {
            0% { transform: rotateY(0deg) translateZ(0) rotateX(0deg); }
            50% { transform: rotateY(3deg) translateZ(5px) rotateX(3deg); }
            100% { transform: rotateY(-3deg) translateZ(-5px) rotateX(-3deg); }
        }

        .message {
            position: absolute;
            top: 60px; /* Más arriba para que no estorbe las flores */
            color: var(--text-color);
            font-size: 3.8em; /* Más grande aún */
            text-shadow: 0 0 20px var(--glow-color-yellow), 0 0 30px var(--glow-color-orange), 0 0 40px rgba(255, 255, 255, 0.5);
            z-index: 20;
            font-weight: bold;
            letter-spacing: 2px;
            animation: text-glow 2.5s infinite alternate;
            padding: 15px 30px; /* Más padding */
            background: rgba(0,0,0,0.4); /* Fondo más oscuro */
            border-radius: 20px; /* Más redondeado */
            text-align: center;
            line-height: 1.2;
            transform: translateZ(50px); /* Asegurar que esté en primer plano */
        }

        .heart {
            color: #FF4081;
            margin-left: 15px;
            animation: pulse 1.5s infinite alternate;
            display: inline-block;
            transform-origin: center;
        }

        @keyframes text-glow {
            0% { text-shadow: 0 0 20px var(--glow-color-yellow), 0 0 30px var(--glow-color-orange); }
            100% { text-shadow: 0 0 30px var(--glow-color-yellow), 0 0 50px var(--glow-color-orange), 0 0 60px rgba(255, 255, 255, 0.7); }
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.3); }
            100% { transform: scale(1); }
        }

        .flower-sparkle {
            position: absolute;
            background: radial-gradient(circle, rgba(255, 255, 200, 1) 0%, rgba(255, 255, 0, 0) 70%);
            border-radius: 50%;
            width: 8px;
            height: 8px;
            opacity: 0;
            animation: sparkle 2.5s infinite ease-out;
            box-shadow: 0 0 10px rgba(255, 255, 0, 0.7);
        }

        @keyframes sparkle {
            0% { opacity: 0; transform: scale(0.5) translate(0,0) rotate(0deg); }
            20% { opacity: 1; transform: scale(1) translate(0, -10px) rotate(45deg); }
            80% { opacity: 0; transform: scale(0.7) translate(20px, -40px) rotate(90deg); }
            100% { opacity: 0; }
        }

        .firefly {
            position: absolute;
            width: 6px;
            height: 6px;
            background-color: rgba(255, 255, 0, 0.8);
            border-radius: 50%;
            box-shadow: 0 0 10px rgba(255, 255, 0, 0.7);
            animation: firefly-move 10s infinite ease-in-out alternate, firefly-blink 1.5s infinite alternate;
            z-index: 15;
        }

        @keyframes firefly-move {
            0% { transform: translateX(0px) translateY(0px) scale(1); opacity: 0.8;}
            25% { transform: translateX(50px) translateY(-30px) scale(0.9); opacity: 0.6;}
            50% { transform: translateX(10px) translateY(-60px) scale(1.1); opacity: 0.9;}
            75% { transform: translateX(-40px) translateY(-20px) scale(0.8); opacity: 0.7;}
            100% { transform: translateX(0px) translateY(0px) scale(1); opacity: 0.8;}
        }

        @keyframes firefly-blink {
            0%, 40%, 100% { opacity: 0; box-shadow: 0 0 5px rgba(255, 255, 0, 0.3); }
            50% { opacity: 1; box-shadow: 0 0 15px rgba(255, 255, 0, 1); }
        }
    </style>
</head>
<body>
    <div class="night-sky-background" id="nightSky"></div>

    <div class="message">
        Toma tus flores, <br> no vas a ser espectadora<span class="heart">💗</span>
    </div>

    <div class="flower-container" id="flowerContainer">
        <!-- Las flores se generarán dinámicamente con JS para mayor control y variedad -->
    </div>

    <div class="ground-foliage-area"></div>
    <!-- Hojas de hierba en el primer plano -->
    <!-- Se generarán dinámicamente con JS para mayor variedad -->


    <script>
        const nightSky = document.getElementById('nightSky');
        const flowerContainer = document.getElementById('flowerContainer');
        const numFlowers = 9; // Incrementamos el número de flores
        const numGrassBlades = 30; // Más hojas de hierba
        const numStars = 250; // Más estrellas
        const numFireflies = 20; // Más luciérnagas

        // Generar estrellas aleatorias
        for (let i = 0; i < numStars; i++) {
            const star = document.createElement('div');
            star.classList.add('star');
            star.style.width = star.style.height = `${Math.random() * 4 + 1}px`;
            star.style.top = `${Math.random() * 90}%`;
            star.style.left = `${Math.random() * 100}%`;
            star.style.animationDelay = `${Math.random() * 4}s`;
            star.style.animationDuration = `${Math.random() * 3 + 3}s`;
            nightSky.appendChild(star);
        }

        // Función para crear una flor con variaciones
        function createFlower(index) {
            const flowerDiv = document.createElement('div');
            flowerDiv.classList.add('flower');
            flowerDiv.style.animationDelay = `${index * 0.4}s`; // Retraso para animaciones escalonadas

            // Variaciones de tamaño y posición
            const scale = 0.7 + Math.random() * 0.5; // Escala entre 0.7 y 1.2
            const zOffset = (Math.random() - 0.5) * 80; // Desplazamiento Z para profundidad (mayor rango)
            const rotationY = (Math.random() - 0.5) * 15; // Rotación Y sutil
            const rotationX = (Math.random() - 0.5) * 10; // Rotación X sutil
            flowerDiv.style.transform = `scale(${scale}) translateZ(${zOffset}px) rotateY(${rotationY}deg) rotateX(${rotationX}deg)`;

            const stemHeight = 150 + Math.random() * 120; // Altura del tallo entre 150px y 270px
            const stemWidth = 10 + Math.random() * 7; // Ancho del tallo
            const petalGroupBottom = stemHeight - 20; // Ajuste para la posición de los pétalos

            flowerDiv.innerHTML = `
                <div class="stem" style="height: ${stemHeight}px; width: ${stemWidth}px;">
                    <div class="leaf left" style="top: ${30 + Math.random() * 70}px; transform: rotate(${(-60 + Math.random() * 20)}deg) translateZ(5px);"></div>
                    <div class="leaf right" style="top: ${50 + Math.random() * 70}px; transform: rotate(${(40 + Math.random() * 20)}deg) translateZ(5px);"></div>
                </div>
                <div class="petal-group" style="bottom: ${petalGroupBottom}px;">
                    <div class="petal"></div>
                    <div class="petal"></div>
                    <div class="petal"></div>
                    <div class="petal"></div>
                    <div class="petal"></div>
                    <div class="petal"></div>
                    <div class="center"></div>
                </div>
            `;
            return flowerDiv;
        }

        // Añadir flores al contenedor
        for (let i = 0; i < numFlowers; i++) {
            const flower = createFlower(i);
            flowerContainer.appendChild(flower);

            // Generar brillos para cada flor
            const petalGroup = flower.querySelector('.petal-group');
            for (let j = 0; j < 7; j++) {
                const sparkle = document.createElement('div');
                sparkle.classList.add('flower-sparkle');
                sparkle.style.top = `${Math.random() * 80 - 40}px`;
                sparkle.style.left = `${Math.random() * 80 - 40}px`;
                sparkle.style.animationDelay = `${Math.random() * 2}s`;
                sparkle.style.animationDuration = `${Math.random() * 2 + 2}s`;
                petalGroup.appendChild(sparkle);
            }
        }

        // Generar hojas de hierba dinámicamente
        for (let i = 0; i < numGrassBlades; i++) {
            const grassBlade = document.createElement('div');
            grassBlade.classList.add('grass-blade');
            grassBlade.style.left = `${Math.random() * 100}%`;
            grassBlade.style.height = `${80 + Math.random() * 70}px`; // Altura entre 80px y 150px
            grassBlade.style.width = `${10 + Math.random() * 10}px`; // Ancho entre 10px y 20px
            grassBlade.style.animationDelay = `${Math.random() * 2}s`;
            // Asegurar que algunas estén más cerca/lejos
            const zTranslate = (Math.random() - 0.5) * 40; // Mayor rango de Z
            const rotateY = (Math.random() - 0.5) * 20; // Mayor rango de rotación Y
            const rotateX = (Math.random() - 0.5) * 10; // Rotación X sutil
            grassBlade.style.transform = `rotateY(${rotateY}deg) translateZ(${zTranslate}px) rotateX(${rotateX}deg)`;
            document.body.appendChild(grassBlade);
        }

        // Generar luciérnagas
        const body = document.body;
        for (let i = 0; i < numFireflies; i++) {
            const firefly = document.createElement('div');
            firefly.classList.add('firefly');
            firefly.style.top = `${Math.random() * 70 + 10}%`;
            firefly.style.left = `${Math.random() * 80 + 10}%`;
            firefly.style.animationDelay = `${Math.random() * 5}s`;
            firefly.style.animationDuration = `${Math.random() * 8 + 8}s`;
            body.appendChild(firefly);
        }
    </script>
</body>
</html>
