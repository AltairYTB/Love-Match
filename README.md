<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Love Match</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #ffdde1;
            text-align: center;
            padding: 50px;
        }
        .container {
            background: #ff9a9e;
            padding: 20px;
            border-radius: 15px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            display: inline-block;
        }
        input, button {
            margin: 10px;
            padding: 10px;
            border: none;
            border-radius: 5px;
        }
        button {
            background-color: #ff758c;
            color: white;
            cursor: pointer;
        }
        button:hover {
            background-color: #ff5a7a;
        }
        .result {
            font-size: 24px;
            margin-top: 20px;
            color: #d6336c;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>💖 Love Match 💖</h1>
        <input type="text" id="name1" placeholder="Prénom 1">
        <input type="text" id="name2" placeholder="Prénom 2">
        <button onclick="calculateLove()">Tester l'amour ❤️</button>
        <div class="result" id="result"></div>
    </div>

    <script>
        function calculateLove() {
            let name1 = document.getElementById("name1").value.trim().toLowerCase();
            let name2 = document.getElementById("name2").value.trim().toLowerCase();
            let percentage;
            
            if ((name1 === "ines" && name2 === "natael") || (name1 === "natael" && name2 === "ines")) {
                percentage = 100;
            } else {
                percentage = matchNames(name1, name2);
            }
            
            document.getElementById("result").innerHTML = `💞 Compatibilité : ${percentage}% 💞`;
        }

        function matchNames(name1, name2) {
            let lengthScore = 100 - Math.abs(name1.length - name2.length) * 10;
            let commonLetters = [...new Set(name1)].filter(letter => name2.includes(letter)).length;
            let letterScore = (commonLetters / Math.max(name1.length, name2.length)) * 100;
            let finalScore = Math.min(Math.max((lengthScore + letterScore) / 2, 0), 100);
            return Math.floor(finalScore);
        }
    </script>
</body>
</html>
