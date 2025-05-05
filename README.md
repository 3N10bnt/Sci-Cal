# Sci-Cal

<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Scientific Calculator</title>
  <style>
    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      padding: 0;
      font-family: 'Poppins', sans-serif;
      background-color: #f7f6f2;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
    }

    .calculator {
      background-color: #ffffff;
      border: 3px solid #d9cab3;
      border-radius: 20px;
      padding: 25px;
      max-width: 380px;
      width: 100%;
      box-shadow: 0 8px 16px rgba(0, 0, 0, 0.15);
      text-align: center;
    }

    .calculator h2 {
      color: #4a7c59;
      margin-bottom: 15px;
    }

    .display {
      width: 100%;
      height: 60px;
      background-color: #e7f0d7;
      color: #2f4f4f;
      font-size: 24px;
      padding: 10px;
      border: none;
      border-radius: 10px;
      text-align: right;
      margin-bottom: 20px;
    }

    .buttons {
      display: grid;
      grid-template-columns: repeat(5, 1fr);
      gap: 10px;
    }

    button {
      padding: 12px;
      font-size: 16px;
      border: none;
      border-radius: 10px;
      background-color: #fdd9a0;
      color: #4a3f35;
      cursor: pointer;
      transition: background-color 0.2s ease;
    }

    button:hover {
      background-color: #fbc77c;
    }

    .leaf {
      position: absolute;
      bottom: 20px;
      right: 20px;
      width: 60px;
      opacity: 0.2;
    }

    @media (max-width: 420px) {
      .calculator {
        padding: 15px;
      }

      .display {
        font-size: 20px;
      }

      button {
        font-size: 14px;
        padding: 10px;
      }
    }
  </style>
</head>
<body>

<div class="calculator">
  <h2>Scientific Calculator</h2>
  <input type="text" class="display" id="display" disabled>
  <div class="buttons">
    <button onclick="clearDisplay()">C</button>
    <button onclick="append('(')">(</button>
    <button onclick="append(')')">)</button>
    <button onclick="append('^')">^</button>
    <button onclick="backspace()">←</button>

    <button onclick="append('sin(')">sin</button>
    <button onclick="append('cos(')">cos</button>
    <button onclick="append('tan(')">tan</button>
    <button onclick="append('Math.PI')">π</button>
    <button onclick="append('/')">÷</button>

    <button onclick="append('7')">7</button>
    <button onclick="append('8')">8</button>
    <button onclick="append('9')">9</button>
    <button onclick="append('*')">×</button>
    <button onclick="append('Math.E')">e</button>

    <button onclick="append('4')">4</button>
    <button onclick="append('5')">5</button>
    <button onclick="append('6')">6</button>
    <button onclick="append('-')">−</button>
    <button onclick="append('log(')">log</button>

    <button onclick="append('1')">1</button>
    <button onclick="append('2')">2</button>
    <button onclick="append('3')">3</button>
    <button onclick="append('+')">+</button>
    <button onclick="append('sqrt(')">√</button>

    <button onclick="append('0')">0</button>
    <button onclick="append('.')">.</button>
    <button onclick="calculateResult()" style="grid-column: span 3">=</button>
  </div>
</div>

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/f4/Leaf_icon.svg/1024px-Leaf_icon.svg.png" class="leaf" alt="Leaf">

<script>
  const display = document.getElementById('display');

  function append(val) {
    display.value += val;
  }

  function clearDisplay() {
    display.value = '';
  }

  function backspace() {
    display.value = display.value.slice(0, -1);
  }

  function calculateResult() {
    try {
      const expression = display.value
        .replace(/sqrt/g, 'Math.sqrt')
        .replace(/log/g, 'Math.log10')
        .replace(/sin/g, 'Math.sin')
        .replace(/cos/g, 'Math.cos')
        .replace(/tan/g, 'Math.tan')
        .replace(/\^/g, '**');

      display.value = eval(expression);
    } catch {
      display.value = 'Error';
    }
  }
</script>

</body>
</html>
