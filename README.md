
<html lang="de">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Moderne Philosophische Weisheit - Existenz & Absurdität</title>
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
            <h1>Moderne Philosophie</h1>
            <p class="subtitle">Existenz, Absurdität & Tiefe der Seele</p>
        </header>

        <div class="content-wrapper">
            <div class="quote-container">
                <div class="quote-text" id="quoteText">
                    Der Mensch ist verdammt, frei zu sein.
                </div>
                <div class="quote-author" id="quoteAuthor">Jean-Paul Sartre</div>
                <div class="quote-era" id="quoteEra">Existentialismus, 1905-1980</div>
            </div>

            <div class="context-box" id="contextBox">
                <div class="context-title">Tiefe offenbaren</div>
                <div class="context-text" id="contextText">
                    Sartre argumentiert, dass Freiheit nicht immer befreiend ist. Wir sind verdammt zur Freiheit und müssen die volle Verantwortung für unsere Wahlen tragen. Es gibt keine vorgegebene Essenz - wir selbst erschaffen uns durch unsere Handlungen.
                </div>
            </div>

            <div class="button-container">
                <button class="btn-primary" id="nextQuoteBtn">✨ Nächste Erkenntnis</button>
                <button class="btn-secondary" id="contextBtn">🔮 Tiefe offenbaren</button>
            </div>
        </div>

        <footer>
            <p>~ Moderne Weisheit für die existenzielle Krise ~</p>
            <p>Gedanken zur Absurdität und Existenz</p>
        </footer>
    </div>

    <script>
        // Moderne Philosophische Zitate Datenbank
        const quotes = [
            {
                quote: "Der Mensch ist verdammt, frei zu sein.",
                author: "Jean-Paul Sartre",
                era: "Existentialismus, 1905-1980",
                context: "Sartre argumentiert, dass Freiheit nicht immer befreiend ist. Wir sind verdammt zur Freiheit und müssen die volle Verantwortung für unsere Wahlen tragen. Es gibt keine vorgegebene Essenz - wir selbst erschaffen uns durch unsere Handlungen."
            },
            {
                quote: "Das Absurde ist, wenn der menschliche Wille nach Bedeutung auf ein stilles Universum trifft.",
                author: "Albert Camus",
                era: "Absurdismus, 1913-1960",
                context: "Camus beschreibt die menschliche Bedingung als absurd - wir suchen nach Sinn in einem Universum, das keinen hat. Sein Ansatz ist nicht Verzweiflung, sondern Akzeptanz: Wir müssen den Felsen, wie Sisyphus, zum Rollen bringen und dabei glücklich sein."
            },
            {
                quote: "Es gibt keine größere Torheit als die Hoffnung.",
                author: "Friedrich Nietzsche",
                era: "Moderne, 1844-1900",
                context: "Nietzsche kritisiert die Hoffnung, die uns an Illusionen bindet. Sie ist oft eine Flucht vor der Realität. Stattdessen plädiert er für die Bejahung des Lebens, wie es ist - das ist die wahre Stärke: nicht hoffen, sondern handeln."
            },
            {
                quote: "Die unterdrückte Menge wird eines Tages erwachen und ihre Ketten zerbrechen.",
                author: "Fjodor Dostojewski",
                era: "Psychologische Philosophie, 1821-1881",
                context: "Dostojewski erforscht die tiefsten Seelenabgründe der Menschheit. Er sieht Leiden als zentrales Element der menschlichen Existenz. Seine Werke stellen Fragen über Schuld, Freiheit und das Geheimnis des menschlichen Herzens."
            },
            {
                quote: "Der Prozess ist die Quintessenz der modernen Existenz.",
                author: "Franz Kafka",
                era: "Absurdistische Modernität, 1883-1924",
                context: "Kafka zeigt, wie das Individuum in undurchschaubaren, bürokratischen Systemen verloren geht. Seine Charaktere kämpfen gegen unsichtbare Kräfte. Dies ist eine Metapher für die Ohnmacht des modernen Menschen in der Gesellschaft."
            },
            {
                quote: "Wenn man keine Angst vor dem Tod hat, hat man nichts mehr zu fürchten.",
                author: "Albert Camus",
                era: "Absurdismus, 1913-1960",
                context: "Camus sieht in der Überwindung der Angst vor dem Tod die Befreiung. Indem wir die Sterblichkeit akzeptieren, befreien wir uns von den Illusionen, die uns versklaven. Dies ist der erste Schritt zur echten Freiheit."
            },
            {
                quote: "Der Übermensch ist die Seele, die am meisten leidet.",
                author: "Friedrich Nietzsche",
                era: "Moderne, 1844-1900",
                context: "Nietzsches Übermensch ist nicht eine brutale Figur, sondern ein Wesen, das über konventionelle Moral hinauswächst. Er erschafft seine eigenen Werte und transformiert Leiden in Schöpfung. Dies erfordert Mut und Integrität."
            },
            {
                quote: "Das Leben ist das, was uns widerfährt, während wir andere Pläne machen.",
                author: "Existentialisierte Moderne",
                era: "20. Jahrhundert",
                context: "Die Moderne Philosophie erkennt an, dass wir nicht vollständig die Kontrolle haben. Die Wirklichkeit überrascht uns ständig. Der Mensch muss zwischen seinen Plänen und der Wirklichkeit improvisieren - das ist das Wesen des Lebens."
            },
            {
                quote: "Ich bin, daher denke ich vielleicht nicht.",
                author: "Inspiriert von Nietzsche & Camus",
                era: "Moderne Inversion, 20. Jahrhundert",
                context: "Ein moderner Umkehrung von Descartes. Der modernen Existentialisten ist die bloße Existenz radikaler als das Denken. Erst wenn wir existieren, handeln und leiden, beginnen wir zu sein. Denken folgt, es ist nicht das Primäre."
            },
            {
                quote: "Die Wahrheit ist einsam.",
                author: "Fjodor Dostojewski",
                era: "Psychologische Philosophie, 1821-1881",
                context: "Dostojewski zeigt, dass jeder Mensch eine einsame Wahrheit in sich trägt. Echte Kommunikation ist selten. Die Isolation ist ein fundamentales Merkmal menschlicher Existenz. Nur durch diese Einsamkeit können wir uns selbst entdecken."
            },
            {
                quote: "Lasst die Ungerechtigkeit nicht zur Gewohnheit werden.",
                author: "Albert Camus",
                era: "Politische Philosophie, 1913-1960",
                context: "Camus plädiert für Widerstand gegen Ungerechtigkeit, nicht aus idealistischen Gründen, sondern als sittliche Verpflichtung. Der Mensch muss sich gegen die Absurdität der Ungerechtigeit wehren, auch wenn der Kampf aussichtslos scheint."
            },
            {
                quote: "Die Anpassung ist der Tod der Seele.",
                author: "Friedrich Nietzsche",
                era: "Moderne Kritik, 1844-1900",
                context: "Nietzsche warnt vor der Gefahr der Anpassung an Massennormen. Die Herde duldet keine Unterschiedlichkeit. Wahre Individuen müssen ihre eigenen Werte erschaffen, auch wenn dies Einsamkeit und Kampf bedeutet."
            },
            {
                quote: "Im Traum dachte ich, ich lebte. Im Leben bemerkte ich, ich träume.",
                author: "Inspiriert von Kafka",
                era: "Moderne Verunsicherung, 20. Jahrhundert",
                context: "Kafkas Werke hinterfragen die Grenze zwischen Realität und Traum. Das Leben wirkt oft wie ein Albtraum, aus dem wir nicht aufwachen können. Diese Verunsicherung ist zentral für das moderne Bewusstsein."
            },
            {
                quote: "Jeder Mensch ist ein Fremder in dieser Welt.",
                author: "Albert Camus",
                era: "Absurdismus, 1913-1960",
                context: "Camus sagt uns, dass Entfremdung nicht eine Krankheit ist, sondern die normale Bedingung. Wir sind alle Fremde - in der Gesellschaft, im Universum, oft sogar für uns selbst. Dies zu akzeptieren ist der Anfang der Weisheit."
            },
            {
                quote: "Die Rebellion ohne Hoffnung ist die Größe des Menschen.",
                author: "Albert Camus",
                era: "Absurdismus, 1913-1960",
                context: "Camus' ultimativer Trost: Obwohl alles absurd ist und hoffnungslos scheint, der menschliche Geist sich aufzulehnen und zu schaffen - das ist unsere Größe. Wir schaffen Sinn nicht, weil es ihn gibt, sondern weil es unser Wesen ist."
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
