<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<title>Méchant Méchant Math</title>

<style>
body {
    margin: 0;
    font-family: Arial, sans-serif;
    background: linear-gradient(45deg, #ff6b6b, #5f27cd, #1dd1a1);
    text-align: center;
    color: white;
    overflow: hidden;
}

h1 {
    background: black;
    padding: 15px;
    color: #ffcc00;
    text-shadow: 0 0 10px red;
}

#enemy {
    font-size: 80px;
    animation: bounce 1s infinite alternate;
}

@keyframes bounce {
    from { transform: translateY(0px); }
    to { transform: translateY(20px); }
}

#question {
    font-size: 40px;
    margin: 20px;
    color: yellow;
}

#answer {
    font-size: 25px;
    padding: 10px;
    text-align: center;
    border-radius: 10px;
    border: none;
    width: 120px;
}

button {
    margin-top: 10px;
    font-size: 20px;
    padding: 10px 20px;
    background: #ffcc00;
    border: none;
    border-radius: 10px;
    cursor: pointer;
}

#score, #timer {
    font-size: 25px;
    margin-top: 15px;
}

#timer { color: #00ffcc; }

/* TEXTE QUI FAIT LE TOUR */
#signature {
    position: fixed;
    font-size: 35px;
    font-weight: bold;
    font-family: 'Brush Script MT', cursive;
    background: linear-gradient(90deg, #ff0000, #ffcc00, #00ffcc, #ff00ff);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    text-shadow: 0 0 15px white;
    animation: tour 12s linear infinite;
    z-index: 999;
}

@keyframes tour {
    0% { top: 10px; left: 10px; }
    25% { top: 10px; left: calc(100% - 300px); }
    50% { top: calc(100% - 60px); left: calc(100% - 300px); }
    75% { top: calc(100% - 60px); left: 10px; }
    100% { top: 10px; left: 10px; }
}

/* Écran de fin */
#endScreen {
    position: fixed;
    top:0; left:0;
    width:100%; height:100%;
    background: rgba(0,0,0,0.9);
    color: #ffcc00;
    display: none;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    font-size: 35px;
}
#endScreen button {
    margin: 10px;
}

</style>
</head>
<body>

<h1>Yo, aller joue "méchant, méchant"</h1>

<div id="enemy">😈</div>

<div id="question"></div>

<input type="number" id="answer" placeholder="Ta réponse">
<br>
<button onclick="checkAnswer()">Attaque !</button>

<div id="score">Score : 0</div>
<div id="timer">Temps : 15</div>

<!-- TEXTE QUI TOURNE -->
<div id="signature">Carlos, méchant méchant</div>

<!-- Écran de fin -->
<div id="endScreen">
    <div id="finalScore"></div>
    <button onclick="restartGame()">Rejouer</button>
    <button onclick="quitGame()">Quitter</button>
</div>

<script>
let score = 0;
let time = 15;
let currentAnswer;
let timerInterval;

// Nouvelle question
function newQuestion() {
    let a = Math.floor(Math.random() * 10) + 1;
    let b = Math.floor(Math.random() * 10) + 1;
    let operations = ["+", "-", "×"];
    let op = operations[Math.floor(Math.random() * 3)];

    if(op === "+") currentAnswer = a + b;
    if(op === "-") currentAnswer = a - b;
    if(op === "×") currentAnswer = a * b;

    document.getElementById("question").innerText = a + " " + op + " " + b;
}

// Vérifier la réponse
function checkAnswer() {
    let userAnswer = document.getElementById("answer").value;

    if(userAnswer == currentAnswer) {
        score++;
        document.body.style.background = "limegreen";
    } else {
        score--;
        document.body.style.background = "crimson";
    }

    document.getElementById("score").innerText = "Score : " + score;
    document.getElementById("answer").value = "";
    newQuestion();

    setTimeout(() => {
        document.body.style.background = "linear-gradient(45deg, #ff6b6b, #5f27cd, #1dd1a1)";
    }, 300);
}

// Compte à rebours
function countdown() {
    time--;
    document.getElementById("timer").innerText = "Temps : " + time;

    if(time <= 0) {
        endGame();
    }
}

// Fin du jeu
function endGame() {
    clearInterval(timerInterval);
    document.getElementById("finalScore").innerText = "Le Méchant Méchant a gagné 😈\nScore : " + score;
    document.getElementById("endScreen").style.display = "flex";
}

// Rejouer
function restartGame() {
    score = 0;
    time = 15;
    document.getElementById("score").innerText = "Score : " + score;
    document.getElementById("timer").innerText = "Temps : " + time;
    document.getElementById("endScreen").style.display = "none";
    newQuestion();
    timerInterval = setInterval(countdown, 1000);
}

// Quitter
function quitGame() {
    alert("Merci d'avoir joué 😈");
    window.close();
}

// Démarrage
newQuestion();
timerInterval = setInterval(countdown, 1000);

</script>
</body>
</html>
