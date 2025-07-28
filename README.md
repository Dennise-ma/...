<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pregunta de Amor</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        /* Define colores personalizados */
        :root {
            --color-red-custom: #EF4444; /* Rojo fuerte */
            --color-white-bg: #FFFFFF; /* Fondo blanco */
            --color-black-text: #000000; /* Texto negro */
        }

        body {
            font-family: 'Inter', sans-serif;
            background-color: var(--color-white-bg);
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
            overflow: hidden; /* Para evitar barras de desplazamiento durante la animación */
        }

        .card-container {
            position: relative;
            perspective: 1000px; /* Para la animación 3D */
            width: 90%;
            max-width: 400px;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .love-card {
            background-color: var(--color-red-custom);
            color: white;
            padding: 2.5rem;
            border-radius: 1.5rem; /* Bordes más redondeados */
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
            text-align: center;
            transition: transform 1s ease-out, opacity 1s ease-out; /* Transición suave */
            position: absolute;
            width: 100%;
            display: flex;
            flex-direction: column;
            gap: 1.5rem;
            transform-origin: center center;
        }

        .love-card.fade-out {
            opacity: 0;
            transform: translateZ(-500px) scale(0.8); /* Mover hacia atrás y encoger */
        }

        .question-text {
            font-size: 1.75rem; /* Texto más grande para la pregunta */
            font-weight: bold;
            margin-bottom: 1rem;
        }

        .answer-button {
            background-color: rgba(255, 255, 255, 0.2); /* Fondo de botón semi-transparente */
            color: white;
            padding: 0.8rem 1.5rem;
            border-radius: 9999px; /* Botones pill-shaped */
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            transition: background-color 0.3s ease, transform 0.2s ease;
            border: 2px solid rgba(255, 255, 255, 0.5); /* Borde blanco semi-transparente */
        }

        .answer-button:hover {
            background-color: rgba(255, 255, 255, 0.3);
            transform: translateY(-2px);
        }

        .message-overlay {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            display: flex;
            justify-content: center;
            align-items: center;
            text-align: center;
            background-color: transparent; /* Fondo transparente */
            color: var(--color-black-text);
            font-size: 1.8rem; /* Tamaño de texto para el mensaje */
            font-weight: bold;
            opacity: 0; /* Inicialmente oculto */
            transition: opacity 1s ease-in; /* Transición para que aparezca suavemente */
            z-index: 10; /* Asegura que esté por encima de la tarjeta difuminada */
            line-height: 1.4;
            padding: 1rem; /* Espaciado interno */
        }

        .message-overlay.show {
            opacity: 1;
        }
    </style>
</head>
<body>
    <div class="card-container">
        <div id="loveCard" class="love-card">
            <p class="question-text">¿Será que hoy me baño?</p>
            <div class="flex flex-col space-y-4">
                <button class="answer-button" data-answer="no">1. no</button>
                <button class="answer-button" data-answer="no-princesa">2. no, mi princesa linda</button>
                <button class="answer-button" data-answer="no-apestosa">3. no, mi chiquita… así apestosa te amo</button>
            </div>
        </div>
        <div id="messageOverlay" class="message-overlay">
            TE AMO MI NEGRO, FUTURO ESPOSO, PAPÁ DE MIS BEBES, MI CHIQUITO. GRACIAS POR AMARME ASÍ
        </div>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const loveCard = document.getElementById('loveCard');
            const messageOverlay = document.getElementById('messageOverlay');
            const answerButtons = document.querySelectorAll('.answer-button');

            answerButtons.forEach(button => {
                button.addEventListener('click', () => {
                    // Añade la clase para la animación de difuminado y retroceso a la tarjeta
                    loveCard.classList.add('fade-out');

                    // Espera a que la animación de la tarjeta termine (1 segundo)
                    setTimeout(() => {
                        // Muestra el mensaje con una transición suave
                        messageOverlay.classList.add('show');
                    }, 1000); // Coincide con la duración de la transición CSS
                });
            });
        });
    </script>
</body>
</html>
