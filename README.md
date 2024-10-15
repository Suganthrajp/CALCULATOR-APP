# CALCULATOR-APP
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Animated Calculator</title>
    <style>
        body {
            background: #f0f0f0;
            font-family: 'Arial', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }

        .calculator {
            background: #333;
            border-radius: 20px;
            padding: 20px;
            box-shadow: 0px 10px 30px rgba(0, 0, 0, 0.2);
            animation: fadeIn 1.2s ease-in-out;
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: scale(0.8);
            }
            to {
                opacity: 1;
                transform: scale(1);
            }
        }

        .screen {
            text-align: right;
            margin-bottom: 20px;
        }

        .screen input {
            width: 100%;
            height: 60px;
            background: #222;
            border: none;
            border-radius: 10px;
            color: #fff;
            font-size: 2rem;
            padding: 10px;
            box-shadow: inset 0 0 10px rgba(0, 0, 0, 0.5);
            animation: slideIn 0.6s ease-out;
        }

        @keyframes slideIn {
            from {
                transform: translateY(-50px);
                opacity: 0;
            }
            to {
                transform: translateY(0);
                opacity: 1;
            }
        }

        .buttons {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 10px;
        }

        button {
            background-color: #444;
            color: white;
            font-size: 1.5rem;
            padding: 20px;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            transition: transform 0.2s, background-color 0.3s;
        }

        button:hover {
            background-color: #555;
            transform: scale(1.1);
        }

        button:active {
            transform: scale(0.95);
        }

        button.equal {
            background-color: #ff9800;
            color: white;
            grid-column: span 2;
        }

        button.equal:hover {
            background-color: #e68a00;
        }
    </style>
</head>
<body>

    <div class="calculator">
        <div class="screen">
            <input type="text" id="display" disabled>
        </div>
        <div class="buttons">
            <button onclick="clearScreen()">C</button>
            <button onclick="del()">DEL</button>
            <button onclick="insert('%')">%</button>
            <button onclick="insert('/')">/</button>

            <button onclick="insert('7')">7</button>
            <button onclick="insert('8')">8</button>
            <button onclick="insert('9')">9</button>
            <button onclick="insert('*')">*</button>

            <button onclick="insert('4')">4</button>
            <button onclick="insert('5')">5</button>
            <button onclick="insert('6')">6</button>
            <button onclick="insert('-')">-</button>

            <button onclick="insert('1')">1</button>
            <button onclick="insert('2')">2</button>
            <button onclick="insert('3')">3</button>
            <button onclick="insert('+')">+</button>

            <button onclick="insert('0')">0</button>
            <button onclick="insert('.')">.</button>
            <button onclick="calculate()" class="equal">=</button>
        </div>
    </div>

    <script>
        function clearScreen() {
            document.getElementById("display").value = "";
        }

        function insert(value) {
            document.getElementById("display").value += value;
        }

        function del() {
            let display = document.getElementById("display").value;
            document.getElementById("display").value = display.substring(0, display.length - 1);
        }

        function calculate() {
            try {
                let result = eval(document.getElementById("display").value);
                document.getElementById("display").value = result;
            } catch (error) {
                document.getElementById("display").value = "Error";
            }
        }
    </script>

</body>
</html>
