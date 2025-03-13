<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Temperature Converter</title>
    <link rel="icon" href="https://static.vecteezy.com/system/resources/previews/015/350/206/non_2x/temperature-high-icon-design-free-vector.jpg">
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background: linear-gradient(135deg, #ff7eb3, #ff758c);
            color: #fff;
            text-align: center;
            transition: background 0.5s, color 0.5s;
        }
        .container {
            max-width: 500px;
            margin: 50px auto;
            padding: 20px;
            background: rgba(0, 0, 0, 0.7);
            border-radius: 10px;
            box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.5);
        }
        input, select, button {
            width: 90%;
            padding: 10px;
            margin: 10px 0;
            border: none;
            border-radius: 5px;
            font-size: 16px;
        }
        button {
            background: #ffcc00;
            color: #111;
            font-weight: bold;
            cursor: pointer;
            transition: 0.3s;
        }
        button:hover {
            background: #ff4500;
            transform: scale(1.05);
        }
        .mode-toggle, .color-toggle {
            background: #222;
            color: #fff;
            padding: 10px;
            border-radius: 5px;
            cursor: pointer;
            display: inline-block;
            margin: 10px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Temperature Converter</h1>
        <input type="number" id="tempInput" placeholder="Enter Temperature">
        <select id="unit">
            <option value="C">Celsius</option>
            <option value="F">Fahrenheit</option>
            <option value="K">Kelvin</option>
        </select>
        <button onclick="convertTemp()">Convert</button>
        <h2 id="result"></h2>
        <div>
            <span class="mode-toggle" onclick="toggleMode()">🌞 Day/Night Mode</span>
            <span class="color-toggle" onclick="changeTextColor()">🎨 Change Text Color</span>
        </div>
    </div>

    <script>
        function convertTemp() {
            let temp = parseFloat(document.getElementById('tempInput').value);
            let unit = document.getElementById('unit').value;
            let result = document.getElementById('result');
            
            if (isNaN(temp)) {
                result.innerText = "Please enter a valid number!";
                return;
            }
            
            let converted;
            if (unit === "C") {
                converted = `Fahrenheit: ${(temp * 9/5 + 32).toFixed(2)}°F | Kelvin: ${(temp + 273.15).toFixed(2)}K`;
            } else if (unit === "F") {
                converted = `Celsius: ${((temp - 32) * 5/9).toFixed(2)}°C | Kelvin: ${(((temp - 32) * 5/9) + 273.15).toFixed(2)}K`;
            } else {
                converted = `Celsius: ${(temp - 273.15).toFixed(2)}°C | Fahrenheit: ${((temp - 273.15) * 9/5 + 32).toFixed(2)}°F`;
            }
            
            result.innerText = converted;
        }
        
        function toggleMode() {
            document.body.classList.toggle("dark-mode");
            if (document.body.classList.contains("dark-mode")) {
                document.body.style.background = "#222";
                document.body.style.color = "#fff";
            } else {
                document.body.style.background = "linear-gradient(135deg, #ff7eb3, #ff758c)";
                document.body.style.color = "#111";
            }
        }
        
        function changeTextColor() {
            const colors = ["#ffcc00", "#00ffcc", "#ff4500", "#00ff00", "#ff00ff"];
            document.body.style.color = colors[Math.floor(Math.random() * colors.length)];
        }
    </script>
</body>
</html>
