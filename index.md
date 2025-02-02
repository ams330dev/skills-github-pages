<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>RG6 Cable Loss Calculator</title>
  <style>
    body { font-family: Arial, sans-serif; margin: 40px; }
    label, input, button { font-size: 1.1em; }
    input { margin-right: 10px; }
  </style>
</head>
<body>
  <h1>RG6 Cable Loss Calculator</h1>
  <p>Enter the frequency in MHz:</p>
  <input type="number" id="frequency" placeholder="Frequency in MHz" step="any">
  <button onclick="calculateLoss()">Calculate Loss</button>
  <p id="result"></p>

  <script>
    function calculateLoss() {
      // Retrieve the entered frequency
      var frequency = parseFloat(document.getElementById("frequency").value);
      if (isNaN(frequency) || frequency <= 0) {
        document.getElementById("result").innerText = "Please enter a valid positive frequency.";
        return;
      }
      
      // Calculate loss using L(f) = 0.231 * f^0.484
      var loss = 0.231 * Math.pow(frequency, 0.484);
      
      // Display the result with two decimals
      document.getElementById("result").innerText =
        "Cable loss at " + frequency + " MHz is approximately " + loss.toFixed(2) + " dB per 100 ft.";
    }
  </script>
</body>
</html>
