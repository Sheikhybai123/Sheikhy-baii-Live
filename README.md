# Sheikhy-baii-Live

<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Sheikhy Baii Signal</title>
  <style>
    body {
      background-color: black;
      color: #00FF99;
      font-family: monospace;
      text-align: center;
      padding-top: 100px;
    }
    .signal-box {
      border: 2px solid #00FF99;
      display: inline-block;
      padding: 30px;
      border-radius: 10px;
    }
    .signal-value {
      font-size: 40px;
      font-weight: bold;
      margin-top: 20px;
    }
  </style>
</head>
<body>
  <div class="signal-box">
    <h1>Sheikhy Baii ka Signal</h1>
    <div class="signal-value" id="prediction">Loading...</div>
  </div>  <!-- Alert Sound --><audio id="alertSound" src="https://actions.google.com/sounds/v1/alarms/beep_short.ogg" preload="auto"></audio>

  <script>
    // Dummy crash values
    const data = [
      1.27, 68.43, 1.92, 9.77, 4.12, 3.54, 1.40, 6.52, 10.97, 1.40,
      1.95, 1.02, 1.33, 94.09, 1.37, 44.95, 4.67, 2.07, 1.21, 3.03,
      12.73, 1.24, 1.67, 9.87, 1.18, 4.09, 1.89, 12.15, 9.27, 2.61,
      1.81, 1.00, 10.91, 3.83, 1.15, 2.91, 2.37, 10.01, 1.96, 2.88,
      1.04, 1.27, 1.64, 2.82, 1.05, 1.31, 1.29, 1.11, 6.63, 8.65,
      1.20, 1.41, 3.44
    ];

    function predictNext(crashData) {
      const len = crashData.length;
      const last3 = crashData.slice(len - 3);
      const weights = [0.2, 0.3, 0.5];
      let prediction = 0;
      for (let i = 0; i < 3; i++) {
        prediction += last3[i] * weights[i];
      }
      return prediction.toFixed(2);
    }

    const nextPrediction = predictNext(data);
    document.getElementById("prediction").innerText = `${nextPrediction}x`;

    // Sound alert if prediction is high
    if (parseFloat(nextPrediction) >= 2.0) {
      const sound = document.getElementById("alertSound");
      sound.play();
    }
  </script></body>
</html><!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Sheikhy Baii Signal</title>
  <style>
    body {
      background-color: black;
      color: #00FF99;
      font-family: monospace;
      text-align: center;
      padding-top: 100px;
    }
    .signal-box {
      border: 2px solid #00FF99;
      display: inline-block;
      padding: 30px;
      border-radius: 10px;
    }
    .signal-value {
      font-size: 40px;
      font-weight: bold;
      margin-top: 20px;
    }
  </style>
</head>
<body>
  <div class="signal-box">
    <h1>Sheikhy Baii ka Signal</h1>
    <div class="signal-value" id="prediction">Loading...</div>
  </div>  <!-- Alert Sound --><audio id="alertSound" src="https://actions.google.com/sounds/v1/alarms/beep_short.ogg" preload="auto"></audio>

  <script>
    // Dummy crash values
    const data = [
      1.27, 68.43, 1.92, 9.77, 4.12, 3.54, 1.40, 6.52, 10.97, 1.40,
      1.95, 1.02, 1.33, 94.09, 1.37, 44.95, 4.67, 2.07, 1.21, 3.03,
      12.73, 1.24, 1.67, 9.87, 1.18, 4.09, 1.89, 12.15, 9.27, 2.61,
      1.81, 1.00, 10.91, 3.83, 1.15, 2.91, 2.37, 10.01, 1.96, 2.88,
      1.04, 1.27, 1.64, 2.82, 1.05, 1.31, 1.29, 1.11, 6.63, 8.65,
      1.20, 1.41, 3.44
    ];

    function predictNext(crashData) {
      const len = crashData.length;
      const last3 = crashData.slice(len - 3);
      const weights = [0.2, 0.3, 0.5];
      let prediction = 0;
      for (let i = 0; i < 3; i++) {
        prediction += last3[i] * weights[i];
      }
      return prediction.toFixed(2);
    }

    const nextPrediction = predictNext(data);
    document.getElementById("prediction").innerText = `${nextPrediction}x`;

    // Sound alert if prediction is high
    if (parseFloat(nextPrediction) >= 2.0) {
      const sound = document.getElementById("alertSound");
      sound.play();
    }
  </script></body>
</html>

const WebSocket = require('ws');

const wss = new WebSocket.Server({ port: 8080 });

wss.on('connection', function connection(ws) {
  console.log('Client connected');

  ws.on('message', function incoming(message) {
    console.log('received: %s', message);
    // Dummy prediction logic (replace with real)
    const prediction = Math.random() * 10;
    ws.send(JSON.stringify({ prediction: prediction.toFixed(2) }));
  });
});

