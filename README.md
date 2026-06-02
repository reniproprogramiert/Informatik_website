# Github-website
Website für Informatik
<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Philosophische Weisheit - Tiefe Gedanken</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Playfair Display', 'Georgia', serif;
            background: linear-gradient(135deg, #0a0e27 0%, #1a1a3e 50%, #0f0a2e 100%);
            color: #e0e0e0;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
            overflow-x: hidden;
        }

        /* Nebel-Effekt Hintergrund */
        body::before {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(ellipse at 50% 50%, rgba(139, 69, 255, 0.15) 0%, transparent 70%);
            pointer-events: none;
            z-index: 1;
        }

        .container {
            position: relative;
            z-index: 2;
            max-width: 800px;
            width: 100%;
        }

        header {
            text-align: center;
            margin-bottom: 80px;
            animation: fadeIn 1.5s ease-in-out;
        }

        h1 {
            font-size: 3.5em;
            color: #b8a4ff;
            text-shadow: 0 0 30px rgba(184, 164, 255, 0.4), 0 0 60px rgba(139, 69, 255, 0.2);
            margin-bottom: 10px;
            letter-spacing: 2px;
            font-weight: 400;
        }

        .subtitle {
            font-size: 1.1em;
            color: #8b7cb8;
            font-style: italic;
            letter-spacing: 1px;
        }

        /* Hauptinhaltsbereich */
        .content-wrapper {
            background: rgba(15, 10, 46, 0.6);
            border: 1px solid rgba(184, 164, 255, 0.2);
            border-radius: 20px;
            padding: 60px 40px;
            backdrop-filter: blur(10px);
            box-shadow: 
                0 0 40px rgba(139, 69, 255, 0.15),
                inset 0 0 40px rgba(139, 69, 255, 0.05);
            animation: slideUp 1s ease-out;
        }

        /* Zitat-Display */
        .quote-container {
            min-height: 280px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            margin-bottom: 50px;
        }

        .quote-text {
            font-size: 1.8em;
            line-height: 1.8;
            color: #d4c5f9;
            margin-bottom: 30px;
            font-style: italic;
            text-shadow: 0 0 20px rgba(184, 164, 255, 0.3);
            animation: fadeInText 1s ease-in-out;
            letter-spacing: 0.5px;
        }

        .quote-text::before,
        .quote-text::after {
            content: '"';
            color: #8b7cb8;
            font-size: 2em;
            opacity: 0.5;
        }

        .quote-author {
            font-size: 1.2em;
            color: #b8a4ff;
            margin-bottom: 15px;
            font-weight: 600;
            letter-spacing: 1px;
        }

        .quote-author::before {
            content: '— ';
            color: #8b7cb8;
        }

        .quote-era {
            font-size: 0.95em;
            color: #7b6fa0;
            font-style: italic;
            letter-spacing: 1px;
        }

        /* Kontext-Box */
        .context-box {
            background: rgba(139, 69, 255, 0.1);
            border-left: 3px solid #8b45ff;
            padding: 25px;
            margin-bottom: 30px;
            border-radius: 10px;
            animation: slideDown 0.8s ease-out;
            max-height: 0;
            overflow: hidden;
            opacity: 0;
            transition: all 0.5s ease-in-out;
        }

        .context-box.active {
            max-height: 500px;
            opacity: 1;
        }

        .context-title {
            color: #b8a4ff;
            font-size: 1.1em;
            font-weight: 600;
            margin-bottom: 12px;
            letter-spacing: 1px;
        }

        .context-text {
            color: #d4c5f9;
            line-height: 1.8;
            font-size: 0.95em;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        /* Button-Bereich */
        .button-container {
            display: flex;
            gap: 20px;
            justify-content: center;
            flex-wrap: wrap;
        }

        button {
            padding: 15px 40px;
            font-size: 1.05em;
            border: 2px solid #b8a4ff;
            background: rgba(184, 164, 255, 0.1);
            color: #b8a4ff;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.4s ease;
            font-family: 'Playfair Display', serif;
            letter-spacing: 1px;
            text-transform: uppercase;
            font-weight: 600;
            box-shadow: 0 0 20px rgba(184, 164, 255, 0.2);
        }

        button:hover {
            background: rgba(184, 164, 255, 0.25);
            box-shadow: 0 0 40px rgba(184, 164, 255, 0.4);
            transform: translateY(-2px);
            border-color: #d4c5f9;
        }

        button:active {
            transform: translateY(0);
        }

        .btn-primary {
            background: linear-gradient(135deg, rgba(139, 69, 255, 0.3), rgba(184, 164, 255, 0.1));
            border-color: #8b45ff;
            color: #b8a4ff;
        }

        .btn-primary:hover {
            background: linear-gradient(135deg, rgba(139, 69, 255, 0.5), rgba(184, 164, 255, 0.3));
            box-shadow: 0 0 50px rgba(139, 69, 255, 0.5);
        }

        .btn-secondary {
            background: rgba(123, 111, 160, 0.2);
            border-color: #7b6fa0;
            color: #a89bbb;
        }

        .btn-secondary:hover {
            background: rgba(123, 111, 160, 0.4);
            border-color: #b8a4ff;
            color: #b8a4ff;
            box-shadow: 0 0 40px rgba(184, 164, 255, 0.3);
        }

        /* Footer */
        footer {
            text-align: center;
            margin-top: 60px;
            color: #7b6fa0;
            font-size: 0.9em;
            letter-spacing: 1px;
        }

        footer p {
            margin-bottom: 5px;
        }

        /* Animationen */
        @keyframes fadeIn {
            from {
                opacity: 0;
            }
            to {
                opacity: 1;
            }
        }

        @keyframes fadeInText {
            from {
                opacity: 0;
                transform: translateY(10px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes slideUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes slideDown {
            from {
                opacity: 0;
                transform: translateY(-10px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            h1 {
                font-size: 2.5em;
            }

            .content-wrapper {
                padding: 40px 25px;
            }

            .quote-text {
                font-size: 1.4em;
            }

            .quote-author {
                font-size: 1.05em;
            }

            .button-container {
                flex-direction: column;
            }

            button {
                width: 100%;
            }

            header {
                margin-bottom: 50px;
            }
        }

        @media (max-width: 480px) {
            h1 {
                font-size: 2em;
                letter-spacing: 1px;
            }

            .subtitle {
                font-size: 0.95em;
            }

            .content-wrapper {
                padding: 30px 20px;
                border-radius: 15px;
            }

            .quote-text {
                font-size: 1.2em;
                line-height: 1.6;
            }

            .quote-container {
                min-height: 200px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>Philosophische Weisheit</h1>
            <p class="subtitle">Zitate zur Introspektion und Tiefe</p>
        </header>

        <div class="content-wrapper">
            <div class="quote-container">
                <div class="quote-text" id="quoteText">
                    Erkenne dich selbst.
                </div>
                <div class="quote-author" id="quoteAuthor">Sokrates</div>
                <div class="quote-era" id="quoteEra">Antike, ~470-399 v.Chr.</div>
            </div>

            <div class="context-box" id="contextBox">
                <div class="context-title">Tiefe offenbaren</div>
                <div class="context-text" id="contextText">
                    Dieses berühmte Zitat war im Apollon-Tempel in Delphi eingraviert und war Sokrates' Leitprinzip. 
                    Es fordert zur Selbstreflexion auf und legt nahe, dass die Erkenntnis der eigenen Natur der Anfang aller Weisheit ist.
                </div>
            </div>

            <div class="button-container">
                <button class="btn-primary" id="nextQuoteBtn">✨ Erkenntnis</button>
                <button class="btn-secondary" id="contextBtn">🔮 Tiefe offenbaren</button>
            </div>
        </div>

        <footer>
            <p>~ Ein Raum für tiefe Gedanken ~</p>
            <p>Philosophische Zitate zum Nachdenken</p>
        </footer>
    </div>

    <script>
        // Philosophische Zitate Datenbank
        const quotes = [
            {
                quote: "Erkenne dich selbst.",
                author: "Sokrates",
                era: "Antike, ~470-399 v.Chr.",
                context: "Dieses berühmte Zitat war im Apollon-Tempel in Delphi eingraviert und war Sokrates' Leitprinzip. Es fordert zur Selbstreflexion auf und legt nahe, dass die Erkenntnis der eigenen Natur der Anfang aller Weisheit ist."
            },
            {
                quote: "Die Welt entsteht aus einem Traum, und wenn der Traum vergeht, vergeht die Welt.",
                author: "Platon",
                era: "Antike, ~428-348 v.Chr.",
                context: "In Platons Höhlengleichnis wird die Realität mit Schatten verglichen. Dies reflektiert seine Theorie der Ideen und wie unsere Wahrnehmung unsere Wirklichkeit prägt. Die Wirklichkeit ist möglicherweise nicht das, was wir sehen."
            },
            {
                quote: "Das Glück ist nicht etwas Fertiges. Es kommt aus deinen eigenen Handlungen.",
                author: "Aristoteles",
                era: "Antike, ~384-322 v.Chr.",
                context: "Aristoteles lehrte, dass Glück (Eudämonie) durch Tugend und gute Handlungen erreicht wird, nicht durch Glück oder Zufall. Es ist ein aktiver Prozess der Selbstvervollkommnung, nicht ein passiver Zustand."
            },
            {
                quote: "Gott ist tot. Und wir haben ihn getötet.",
                author: "Friedrich Nietzsche",
                era: "Moderne, 1844-1900",
                context: "Nietzsche proklamiert das Ende traditioneller Werte und Wahrheiten. Dies ist nicht Atheismus, sondern ein Aufruf zur Neugestaltung von Werten und der Selbstverwirklichung jenseits konventioneller Moral und Religion."
            },
            {
                quote: "Ich denke, also bin ich.",
                author: "René Descartes",
                era: "Aufklärung, 1596-1650",
                context: "Dies ist Descartes' methodischer Skeptizismus - der einzige unbestreitbare Beweis seiner Existenz ist die Tatsache, dass er denkt. Es markiert den Beginn der modernen Philosophie und der Zentralität des Bewusstseins."
            },
            {
                quote: "Der Mensch ist frei, und daher verdammt, die Last seiner Freiheit zu tragen.",
                author: "Jean-Paul Sartre",
                era: "Existentialismus, 1905-1980",
                context: "Sartre argumentiert, dass Freiheit nicht immer befreiend ist - wir sind zu Freiheit verurteilt und müssen die Verantwortung für unsere Wahlen und Handlungen tragen. Dies ist die Grundlage der existenzialistischen Ethik."
            },
            {
                quote: "Das Untersuchte Leben ist das Leben wert, gelebt zu werden.",
                author: "Sokrates",
                era: "Antike, ~470-399 v.Chr.",
                context: "Sokrates argumentierte, dass wir kontinuierlich unsere Überzeugungen und Handlungen hinterfragen müssen. Ein Leben ohne Selbstreflexion und kritisches Denken ist bedeutungslos und unwürdig."
            },
            {
                quote: "Die Wahrheit lässt sich nicht sprechen, sie muss erfahren werden.",
                author: "Blaise Pascal",
                era: "Aufklärung, 1623-1662",
                context: "Pascal unterschied zwischen dem Verstand und dem Herzen als Wege zur Wahrheit. Manche tiefste Wahrheiten können nicht rein logisch verstanden werden, sondern müssen gelebt und erfahren werden."
            },
            {
                quote: "Der Mensch ist das Maß aller Dinge.",
                author: "Protagoras",
                era: "Antike, ~490-420 v.Chr.",
                context: "Dies ist ein früher Ansatz zum Subjektivismus und Relativismus. Protagoras lehrte, dass die Wahrheit subjektiv ist und von der individuellen Wahrnehmung abhängt - eine radikale Idee für die antike Philosophie."
            },
            {
                quote: "Alles fließt, nichts bleibt.",
                author: "Heraklit",
                era: "Antike, ~540-480 v.Chr.",
                context: "Heraklits Philosophie betont die ständige Veränderung und das Werden. Er argumentierte, dass die Realität nicht statisch ist, sondern ein ewiger Fluss von Werden und Vergehen. Wir können nicht zweimal in denselben Fluss treten."
            },
            {
                quote: "Das Leben ohne Liebe ist kein Leben.",
                author: "Søren Kierkegaard",
                era: "19. Jahrhundert, 1813-1855",
                context: "Kierkegaard betonte die zentrale Rolle der Liebe und des Glaubens im menschlichen Dasein. Für ihn war Liebe nicht nur ein Gefühl, sondern ein ethisches und existenzielles Engagement für den anderen."
            },
            {
                quote: "Der Traum ist das kleine verborgene Tor in den tiefsten und intimsten Heiligtum der Seele.",
                author: "Carl Jung",
                era: "20. Jahrhundert, 1875-1961",
                context: "Jung sah Träume als Fenster zum Unbewussten. Sie sind nicht bloße Zufallsprodukte, sondern bedeutungsvolle Botschaften unserer tieferen Selbst, die Wege zur Selbstentdeckung und Heilung bietet."
            },
            {
                quote: "Wir sind nicht an Land; wir sind auf dem Meer.",
                author: "Martin Heidegger",
                era: "Moderne Philosophie, 1889-1976",
                context: "Heidegger beschreibt die menschliche Existenz als fundamental unsicher und unbegrenzt. Wir befinden uns nicht in einem festen, sicheren Zustand, sondern in einem ständigen Prozess des Werdens und der Möglichkeit."
            },
            {
                quote: "Das größte Glück ist, nicht begehrt zu werden.",
                author: "Konfuzius",
                era: "Antike China, ~551-479 v.Chr.",
                context: "Konfuzius lehrte, dass echtes Glück nicht aus Leidenschaft kommt, sondern aus innerer Harmonie und ethischem Verhalten. Die Begierde bindet uns an materielle Dinge und verstärkt Leid."
            },
            {
                quote: "Die Einheit ist die Vielheit betrachtet vom Standpunkt des Unendlichen.",
                author: "Giordano Bruno",
                era: "Renaissance, 1548-1600",
                context: "Bruno, ein früher Pantheist, sah das Universum als eine unendliche Einheit. Dies war eine radikale Idee, die ihn zur Verfolgung durch die Inquisition führte - er fragte nach der wahren Natur der Realität."
            }
        ];

        // DOM-Elemente
        const quoteText = document.getElementById('quoteText');
        const quoteAuthor = document.getElementById('quoteAuthor');
        const quoteEra = document.getElementById('quoteEra');
        const contextBox = document.getElementById('contextBox');
        const contextText = document.getElementById('contextText');
        const nextQuoteBtn = document.getElementById('nextQuoteBtn');
        const contextBtn = document.getElementById('contextBtn');

        let currentQuoteIndex = 0;

        // Zufälliges Zitat laden
        function getRandomQuote() {
            currentQuoteIndex = Math.floor(Math.random() * quotes.length);
            return quotes[currentQuoteIndex];
        }

        // Zitat anzeigen mit Fade-Effekt
        function displayQuote(quote) {
            // Fade out
            quoteText.style.animation = 'none';
            quoteAuthor.style.animation = 'none';
            quoteEra.style.animation = 'none';
            
            setTimeout(() => {
                quoteText.textContent = quote.quote;
                quoteAuthor.textContent = quote.author;
                quoteEra.textContent = quote.era;
                contextText.textContent = quote.context;

                // Fade in
                quoteText.style.animation = 'fadeInText 1s ease-in-out';
                quoteAuthor.style.animation = 'fadeInText 1s ease-in-out';
                quoteEra.style.animation = 'fadeInText 1s ease-in-out';
            }, 300);

            // Kontext-Box zurücksetzen
            contextBox.classList.remove('active');
        }

        // Button-Funktionen
        nextQuoteBtn.addEventListener('click', () => {
            const randomQuote = getRandomQuote();
            displayQuote(randomQuote);
        });

        contextBtn.addEventListener('click', () => {
            contextBox.classList.toggle('active');
        });

        // Initial Quote laden
        displayQuote(quotes[0]);

        // Tastenkürzel
        document.addEventListener('keydown', (e) => {
            if (e.code === 'Space') {
                e.preventDefault();
                const randomQuote = getRandomQuote();
                displayQuote(randomQuote);
            }
            if (e.code === 'Enter') {
                e.preventDefault();
                contextBox.classList.toggle('active');
            }
        });
    </script>
</body>
</html>
