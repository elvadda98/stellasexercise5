<!DOCTYPE html>
<html lang="it">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Completa le Frasi</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #1a2a6c 0%, #b21f1f 50%, #fdbb2d 100%);
            min-height: 100vh;
            padding: 20px;
            color: #2c3e50;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .container {
            max-width: 1000px;
            width: 100%;
            background: white;
            border-radius: 20px;
            box-shadow: 0 15px 35px rgba(0,0,0,0.2);
            overflow: hidden;
        }

        .header {
            background: linear-gradient(135deg, #1a2a6c, #b21f1f);
            color: white;
            padding: 30px;
            text-align: center;
            position: relative;
        }

        .header h1 {
            font-size: 2.5em;
            margin-bottom: 10px;
            position: relative;
            z-index: 1;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.2);
        }

        .header p {
            font-size: 1.2em;
            opacity: 0.9;
            position: relative;
            z-index: 1;
        }

        .game-section {
            padding: 30px;
        }

        .word-bank {
            background: linear-gradient(135deg, #f5f7fa, #e8f4f8);
            padding: 25px;
            border-radius: 15px;
            margin-bottom: 25px;
            border: 2px solid #1a2a6c;
            box-shadow: 0 4px 15px rgba(26, 42, 108, 0.2);
        }

        .word-bank h3 {
            color: #1a2a6c;
            margin-bottom: 15px;
            text-align: center;
            font-size: 1.4em;
        }

        .word-options {
            display: flex;
            flex-wrap: wrap;
            gap: 12px;
            justify-content: center;
        }

        .word-option {
            background: linear-gradient(135deg, #1a2a6c, #b21f1f);
            color: white;
            padding: 10px 18px;
            border-radius: 20px;
            font-weight: bold;
            font-size: 16px;
            box-shadow: 0 3px 10px rgba(26, 42, 108, 0.3);
            transition: all 0.3s ease;
            cursor: default;
        }

        .word-option:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(26, 42, 108, 0.4);
        }

        .question {
            background: #f8f9fa;
            padding: 25px;
            border-radius: 15px;
            margin-bottom: 20px;
            border-left: 5px solid #1a2a6c;
            box-shadow: 0 4px 15px rgba(0,0,0,0.05);
        }

        .question h3 {
            color: #1a2a6c;
            margin-bottom: 15px;
            font-size: 1.3em;
        }

        .fill-blank {
            background: #fff;
            border: 2px solid #ddd;
            border-radius: 8px;
            padding: 8px 12px;
            font-size: 16px;
            margin: 0 5px;
            min-width: 120px;
            transition: border-color 0.3s ease;
        }

        .fill-blank.correct {
            border-color: #4CAF50;
            background: #e8f5e8;
        }

        .fill-blank.incorrect {
            border-color: #f44336;
            background: #ffeaea;
        }

        .check-btn {
            background: linear-gradient(135deg, #1a2a6c, #b21f1f);
            color: white;
            border: none;
            padding: 15px 30px;
            border-radius: 25px;
            cursor: pointer;
            font-size: 16px;
            font-weight: bold;
            margin: 20px auto;
            display: block;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(26, 42, 108, 0.3);
        }

        .check-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(26, 42, 108, 0.4);
        }

        .feedback {
            margin-top: 15px;
            padding: 15px;
            border-radius: 10px;
            font-weight: bold;
            text-align: center;
            animation: slideIn 0.3s ease;
        }

        @keyframes slideIn {
            from { transform: translateX(-20px); opacity: 0; }
            to { transform: translateX(0); opacity: 1; }
        }

        .feedback.correct {
            background: #d4edda;
            color: #155724;
            border: 1px solid #c3e6cb;
        }

        .feedback.incorrect {
            background: #f8d7da;
            color: #721c24;
            border: 1px solid #f5c6cb;
        }

        .score {
            position: fixed;
            top: 20px;
            right: 20px;
            background: linear-gradient(135deg, #1a2a6c, #b21f1f);
            color: white;
            padding: 15px 20px;
            border-radius: 25px;
            font-weight: bold;
            box-shadow: 0 4px 15px rgba(26, 42, 108, 0.3);
            z-index: 1000;
        }

        .icon {
            font-size: 24px;
            margin-right: 10px;
            vertical-align: middle;
        }

        .shuffle-btn {
            background: linear-gradient(135deg, #fdbb2d, #b21f1f);
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 25px;
            cursor: pointer;
            font-size: 14px;
            font-weight: bold;
            margin: 10px auto;
            display: block;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(253, 187, 45, 0.3);
        }

        .shuffle-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(253, 187, 45, 0.4);
        }

        @media (max-width: 768px) {
            .score {
                position: static;
                margin: 20px auto;
                display: block;
                width: fit-content;
            }
        }
    </style>
</head>
<body>
    <div class="score">Punteggio: <span id="score">0</span>/12</div>
    
    <div class="container">
        <div class="header">
            <h1><i class="fas fa-language icon"></i> Completa le Frasi</h1>
            <p>Inserisci le parole mancanti nelle frasi!</p>
        </div>

        <div class="game-section">
            <div class="word-bank">
                <h3><i class="fas fa-list-ul icon"></i> Parole da usare:</h3>
                <div class="word-options">
                    <span class="word-option">evening</span>
                    <span class="word-option">weather</span>
                    <span class="word-option">ill</span>
                    <span class="word-option">planning</span>
                    <span class="word-option">high season</span>
                    <span class="word-option">become</span>
                </div>
            </div>

            <button class="shuffle-btn" onclick="shuffleQuestions()">
                <i class="fas fa-random"></i> Mescola le Frasi
            </button>

            <div id="questions-container">
                <!-- Le domande verranno inserite dinamicamente qui -->
            </div>

            <button class="check-btn" onclick="checkFillBlanks()">Controlla Risposte</button>
        </div>
    </div>

    <script>
        let score = 0;
        let questions = [
            {
                id: 1,
                question: "We're having a barbecue this <input type='text' class='fill-blank' data-answer='evening' placeholder='risposta'>. (Stiamo facendo un barbecue questa sera.)",
                answer: "evening"
            },
            {
                id: 2,
                question: "The <input type='text' class='fill-blank' data-answer='weather' placeholder='risposta'> is perfect for a day at the beach. (Il tempo è perfetto per una giornata in spiaggia.)",
                answer: "weather"
            },
            {
                id: 3,
                question: "I can't come to work today because I'm feeling <input type='text' class='fill-blank' data-answer='ill' placeholder='risposta'>. (Non posso venire al lavoro oggi perché mi sento male.)",
                answer: "ill"
            },
            {
                id: 4,
                question: "We're <input type='text' class='fill-blank' data-answer='planning' placeholder='risposta'> a trip to Japan for next year. (Stiamo pianificando un viaggio in Giappone per l'anno prossimo.)",
                answer: "planning"
            },
            {
                id: 5,
                question: "July and August are considered <input type='text' class='fill-blank' data-answer='high season' placeholder='risposta'> for tourism in Europe. (Luglio e agosto sono considerati alta stagione per il turismo in Europa.)",
                answer: "high season"
            },
            {
                id: 6,
                question: "She wants to <input type='text' class='fill-blank' data-answer='become' placeholder='risposta'> a doctor when she grows up. (Lei vuole diventare un dottore quando crescerà.)",
                answer: "become"
            },
            {
                id: 7,
                question: "The <input type='text' class='fill-blank' data-answer='evening' placeholder='risposta'> sky was painted with beautiful colors. (Il cielo serale era dipinto con colori bellissimi.)",
                answer: "evening"
            },
            {
                id: 8,
                question: "The forecast says the <input type='text' class='fill-blank' data-answer='weather' placeholder='risposta'> will improve tomorrow. (Le previsioni dicono che il tempo migliorerà domani.)",
                answer: "weather"
            },
            {
                id: 9,
                question: "Several students were <input type='text' class='fill-blank' data-answer='ill' placeholder='risposta'> with the flu last week. (Diversi studenti erano malati con l'influenza la scorsa settimana.)",
                answer: "ill"
            },
            {
                id: 10,
                question: "They're <input type='text' class='fill-blank' data-answer='planning' placeholder='risposta'> to get married in the spring. (Stanno pianificando di sposarsi in primavera.)",
                answer: "planning"
            },
            {
                id: 11,
                question: "Prices are higher during the <input type='text' class='fill-blank' data-answer='high season' placeholder='risposta'>. (I prezzi sono più alti durante l'alta stagione.)",
                answer: "high season"
            },
            {
                id: 12,
                question: "He studied hard to <input type='text' class='fill-blank' data-answer='become' placeholder='risposta'> an engineer. (Ha studiato duramente per diventare un ingegnere.)",
                answer: "become"
            }
        ];

        // Funzione per mescolare le domande (algoritmo Fisher-Yates)
        function shuffleArray(array) {
            for (let i = array.length - 1; i > 0; i--) {
                const j = Math.floor(Math.random() * (i + 1));
                [array[i], array[j]] = [array[j], array[i]];
            }
            return array;
        }

        // Funzione per visualizzare le domande
        function renderQuestions() {
            const container = document.getElementById('questions-container');
            container.innerHTML = '';
            
            questions.forEach((q, index) => {
                const questionDiv = document.createElement('div');
                questionDiv.className = 'question';
                questionDiv.innerHTML = `
                    <h3>Domanda ${index + 1}:</h3>
                    <p>${q.question}</p>
                    <div class="feedback" id="feedback-${q.id}" style="display: none;"></div>
                `;
                container.appendChild(questionDiv);
            });
        }

        // Funzione per mescolare le domande
        function shuffleQuestions() {
            questions = shuffleArray([...questions]);
            renderQuestions();
            
            // Mostra un messaggio di conferma
            const feedback = document.createElement('div');
            feedback.className = 'feedback correct';
            feedback.textContent = 'Frasi mescolate!';
            feedback.style.marginTop = '10px';
            feedback.style.marginBottom = '20px';
            
            const container = document.getElementById('questions-container');
            container.parentNode.insertBefore(feedback, container);
            
            // Rimuovi il messaggio dopo 2 secondi
            setTimeout(() => {
                feedback.remove();
            }, 2000);
        }

        function checkFillBlanks() {
            const blanks = document.querySelectorAll('.fill-blank');
            let correctCount = 0;
            
            blanks.forEach((blank, index) => {
                const userAnswer = blank.value.toLowerCase().trim();
                const correctAnswer = blank.dataset.answer.toLowerCase();
                
                if (userAnswer === correctAnswer) {
                    blank.classList.remove('incorrect');
                    blank.classList.add('correct');
                    correctCount++;
                } else {
                    blank.classList.remove('correct');
                    blank.classList.add('incorrect');
                }
                
                // Trova l'ID della domanda dal campo di input
                const inputId = blank.closest('.question').querySelector('.feedback').id.split('-')[1];
                const feedback = document.getElementById(`feedback-${inputId}`);
                
                if (userAnswer === correctAnswer) {
                    feedback.textContent = '✅ Corretto!';
                    feedback.className = 'feedback correct';
                } else {
                    feedback.textContent = `❌ Sbagliato. La risposta corretta è: "${blank.dataset.answer}"`;
                    feedback.className = 'feedback incorrect';
                }
                feedback.style.display = 'block';
            });
            
            // Aggiorna il punteggio
            score = correctCount;
            document.getElementById('score').textContent = score;
            
            // Mostra il punteggio finale
            const finalFeedback = document.createElement('div');
            finalFeedback.className = 'feedback ' + (score === questions.length ? 'correct' : 'incorrect');
            finalFeedback.textContent = score === questions.length ? 
                '🎉 Complimenti! Hai risposto correttamente a tutte le domande!' : 
                `Hai totalizzato ${score} punti su ${questions.length}. Continua a esercitarti!`;
            finalFeedback.style.marginTop = '20px';
            
            const checkBtn = document.querySelector('.check-btn');
            checkBtn.parentNode.insertBefore(finalFeedback, checkBtn.nextSibling);
            
            // Rimuovi il messaggio dopo 5 secondi
            setTimeout(() => {
                finalFeedback.remove();
            }, 5000);
        }
        
        // Inizializza la pagina
        window.onload = function() {
            renderQuestions();
        }
    </script>
</body>
</html>
