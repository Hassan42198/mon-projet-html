<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pour Imane, ma fleur</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background: linear-gradient(135deg, #FFD1DC 0%, #B0E0E6 100%); /* Couleurs douces et dégradées */
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            overflow: hidden; /* Cache les fleurs en dehors de l'écran initial */
            position: relative;
        }

        /* Effet Glassmorphism pour la carte */
        .card {
            background: rgba(255, 255, 255, 0.2); /* Fond semi-transparent */
            backdrop-filter: blur(10px); /* Effet flou derrière */
            -webkit-backdrop-filter: blur(10px); /* Compatibilité Safari */
            border-radius: 20px;
            border: 1px solid rgba(255, 255, 255, 0.3); /* Bordure légère */
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            padding: 2.5rem;
            text-align: center;
            max-width: 380px;
            z-index: 10;
            position: relative;
            overflow: hidden; /* Pour le cœur scintillant */
        }

        /* Texte */
        h1 {
            color: #4A4A4A; /* Couleur de texte sombre mais douce */
            font-size: 2.2rem;
            margin-bottom: 0.5rem;
            font-weight: 600;
        }

        p {
            color: #666;
            font-size: 1.3rem;
            font-weight: 400;
            margin-top: 0;
        }

        /* Cœur scintillant */
        .sparkle-heart {
            font-size: 6rem; /* Plus grand */
            color: transparent; /* Masque le cœur initial */
            position: relative;
            width: 1em; /* Pour centrer le pseudo-élément */
            height: 1em;
            display: inline-block;
            margin-bottom: 1rem;
        }

        .sparkle-heart::before {
            content: '❤️'; /* Le vrai cœur */
            position: absolute;
            top: 0;
            left: 0;
            color: #FF69B4; /* Rose vif */
            text-shadow: 0 0 15px #FF69B4, 0 0 30px #FFD1DC; /* Effet de brillance */
            animation: pulse-sparkle 1.5s infinite alternate;
        }

        @keyframes pulse-sparkle {
            0% { transform: scale(0.9); opacity: 0.8; }
            100% { transform: scale(1.1); opacity: 1; text-shadow: 0 0 20px #FF69B4, 0 0 40px #FFD1DC; }
        }

        /* Animation des pétales de fleurs */
        .flower-petal {
            position: absolute;
            font-size: 1.5rem; /* Taille des pétales */
            color: rgba(255, 255, 255, 0.8); /* Couleur des pétales, presque blanche */
            pointer-events: none;
            user-select: none;
            animation: fall 10s linear infinite;
        }

        .flower-petal:nth-child(2n) {
            animation-delay: -2s; /* Décalage pour un effet plus naturel */
            font-size: 1.2rem;
        }
        .flower-petal:nth-child(3n) {
            animation-delay: -5s;
            font-size: 1.8rem;
        }
        .flower-petal:nth-child(4n) {
            animation-delay: -8s;
            font-size: 1rem;
        }

        @keyframes fall {
            0% { transform: translateY(-10vh) translateX(0vw) rotate(0deg); opacity: 0; }
            10% { opacity: 1; }
            100% { transform: translateY(110vh) translateX(20vw) rotate(720deg); opacity: 0; }
        }
    </style>
</head>
<body>

    <div class="card">
        <div class="sparkle-heart"></div>
        <h1>Pour Imane</h1>
        <p>Tu es ma fleur.</p>
    </div>

    <script>
        const flowerTypes = ['🌸', '🌷', '🌼', '🌺', '✨']; // Différents types de fleurs/sparkles

        function createPetal() {
            const petal = document.createElement('div');
            petal.classList.add('flower-petal');
            petal.innerHTML = flowerTypes[Math.floor(Math.random() * flowerTypes.length)];
            petal.style.left = Math.random() * 100 + 'vw';
            petal.style.animationDuration = (Math.random() * 8 + 7) + 's'; // Durée de 7 à 15 secondes
            petal.style.animationDelay = (Math.random() * -10) + 's'; // Décalage pour qu'elles apparaissent à différents moments
            petal.style.fontSize = (Math.random() * 1.5 + 1) + 'rem'; // Taille variable
            petal.style.opacity = Math.random() * 0.7 + 0.3; // Opacité variable
            document.body.appendChild(petal);

            // Supprime le pétale après son animation pour éviter l'encombrement DOM
            petal.addEventListener('animationend', () => {
                petal.remove();
            });
        }

        // Génère des pétales en continu
        setInterval(createPetal, 500); // Toutes les 0.5 secondes
    </script>
</body>
</html>
