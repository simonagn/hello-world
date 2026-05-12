<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Past Tense Challenge</title>
    <style>
        :root { --primary: #6366f1; --bg: #f8fafc; }
        body { font-family: 'Segoe UI', sans-serif; background: var(--bg); display: flex; flex-direction: column; align-items: center; padding: 20px; }
        h1 { color: #1e293b; font-size: 1.5rem; }
        #game-container { width: 100%; max-width: 400px; perspective: 1000px; margin-top: 20px; }
        .card { background: white; height: 250px; border-radius: 20px; display: flex; flex-direction: column; justify-content: center; align-items: center; padding: 30px; text-align: center; box-shadow: 0 10px 25px rgba(0,0,0,0.1); cursor: pointer; transition: transform 0.6s; transform-style: preserve-3d; position: relative; }
        .card.is-flipped { transform: rotateY(180deg); }
        .front, .back { position: absolute; width: 100%; height: 100%; backface-visibility: hidden; display: flex; align-items: center; justify-content: center; padding: 20px; box-sizing: border-box; border-radius: 20px; }
        .back { background: var(--primary); color: white; transform: rotateY(180deg); font-size: 1.2rem; font-weight: bold; }
        .sentence { font-size: 1.1rem; color: #334155; line-height: 1.5; }
        .controls { margin-top: 30px; display: flex; gap: 20px; }
        button { padding: 12px 25px; border: none; border-radius: 50px; background: white; box-shadow: 0 4px 6px rgba(0,0,0,0.05); font-weight: bold; cursor: pointer; transition: 0.2s; }
        button:active { transform: scale(0.95); }
        .next-btn { background: var(--primary); color: white; }
        .progress { margin-top: 15px; font-size: 0.9rem; color: #64748b; }
    </style>
</head>
<body>

    <h1>⚡️ Past Tense Game</h1>
    <p>Tap the card to see the answer!</p>

    <div id="game-container">
        <div class="card" id="card" onclick="this.classList.toggle('is-flipped')">
            <div class="front">
                <p class="sentence" id="sentence">Loading...</p>
            </div>
            <div class="back" id="answer">
                Answer goes here
            </div>
        </div>
    </div>

    <div class="progress" id="progress">Card 1 of 10</div>

    <div class="controls">
        <button onclick="prevCard()">Back</button>
        <button class="next-btn" onclick="nextCard()">Next Card →</button>
    </div>

    <script>
        const tasks = [
            { s: "I ____ (read) a book when suddenly the lights ____ (go) out.", a: "was reading / went" },
            { s: "While the students ____ (write) their essays, the fire alarm ____ (start) to ring.", a: "were writing / started" },
            { s: "My mother ____ (cook) dinner while my father ____ (wash) the car.", a: "was cooking / was washing" },
            { s: "When I ____ (arrive) at the party, everyone ____ (dance) and singing.", a: "arrived / was dancing" },
            { s: "He ____ (break) his leg while he ____ (ski) in the Alps last winter.", a: "broke / was skiing" },
            { s: "The phone ____ (ring) three times while I ____ (take) a shower.", a: "rang / was taking" },
            { s: "What ____ (you / do) when the accident ____ (happen)?", a: "were you doing / happened" },
            { s: "I ____ (not / see) the thief because I ____ (sleep) on the sofa.", a: "didn't see / was sleeping" },
            { s: "It ____ (begin) to rain just as we ____ (leave) the house.", a: "began / were leaving" },
            { s: "Yesterday at 7:00 PM, I ____ (eat) dinner with my family.", a: "was eating" }
        ];

        let current = 0;
        const card = document.getElementById('card');
        const sText = document.getElementById('sentence');
        const aText = document.getElementById('answer');
        const pText = document.getElementById('progress');

        function updateCard() {
            card.classList.remove('is-flipped');
            setTimeout(() => {
                sText.innerText = tasks[current].s;
                aText.innerText = tasks[current].a;
                pText.innerText = `Card ${current + 1} of ${tasks.length}`;
            }, 150);
        }

        function nextCard() {
            if (current < tasks.length - 1) {
                current++;
                updateCard();
            } else {
                alert("Game Finished! Ready for the test?");
                current = 0;
                updateCard();
            }
        }

        function prevCard() {
            if (current > 0) {
                current--;
                updateCard();
            }
        }

        updateCard();
    </script>
</body>
</html>
