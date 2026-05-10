<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Sketch Board</title>

  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: Verdana, sans-serif;
      background: linear-gradient(to right, #dfe9f3, #ffffff);
      text-align: center;
      padding: 20px;
      transition: 0.3s ease;
    }

    h1 {
      margin-bottom: 20px;
      color: #222;
    }

    .toolbar {
      background: white;
      padding: 15px;
      border-radius: 12px;
      width: 90%;
      margin: auto;
      margin-bottom: 15px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
    }

    button,
    input {
      margin: 6px;
      padding: 8px 12px;
      border-radius: 8px;
      border: 1px solid #ccc;
      cursor: pointer;
    }

    button:hover {
      background: #333;
      color: white;
    }

    canvas {
      background: white;
      border: 3px solid #444;
      border-radius: 10px;
      cursor: crosshair;
      width: 90%;
      max-width: 900px;
      height: 500px;
    }

    .dark-mode {
      background: #1f1f1f;
      color: white;
    }

    .dark-mode .toolbar {
      background: #333;
    }
  </style>
</head>
<body>

  <h1>Sketch Board</h1>

  <div class="toolbar">
    <label>Choose Color:</label>
    <input type="color" id="paintColor" value="#000000">

    <label>Brush Size:</label>
    <input type="range" id="brushRange" min="1" max="25" value="4">

    <button id="eraseBtn">Eraser</button>
    <button id="clearBtn">Clear Board</button>
    <button id="saveBtn">Save Image</button>
    <button id="themeBtn">Dark Mode</button>
  </div>

  <canvas id="drawingBoard"></canvas>

  <script>
    const board = document.getElementById("drawingBoard");
    const pen = board.getContext("2d");

    const colorInput = document.getElementById("paintColor");
    const sizeInput = document.getElementById("brushRange");

    let isPainting = false;
    let selectedColor = colorInput.value;
    let brushWidth = sizeInput.value;

    // Responsive canvas size
    board.width = 900;
    board.height = 500;

    colorInput.addEventListener("input", () => {
      selectedColor = colorInput.value;
    });

    sizeInput.addEventListener("input", () => {
      brushWidth = sizeInput.value;
    });

    board.addEventListener("mousedown", startPaint);
    board.addEventListener("mouseup", stopPaint);
    board.addEventListener("mousemove", paint);
    board.addEventListener("mouseleave", stopPaint);

    function startPaint(event) {
      isPainting = true;
      paint(event);
    }

    function stopPaint() {
      isPainting = false;
      pen.beginPath();
    }

    function paint(event) {
      if (!isPainting) return;

      const area = board.getBoundingClientRect();
      const pointX = event.clientX - area.left;
      const pointY = event.clientY - area.top;

      pen.lineWidth = brushWidth;
      pen.lineCap = "round";
      pen.strokeStyle = selectedColor;

      pen.lineTo(pointX, pointY);
      pen.stroke();

      pen.beginPath();
      pen.moveTo(pointX, pointY);
    }

    // Clear drawing
    document.getElementById("clearBtn").addEventListener("click", () => {
      pen.clearRect(0, 0, board.width, board.height);
    });

    // Eraser tool
    document.getElementById("eraseBtn").addEventListener("click", () => {
      selectedColor = "#ffffff";
    });

    // Save image
    document.getElementById("saveBtn").addEventListener("click", () => {
      const imageLink = document.createElement("a");
      imageLink.download = "my_drawing.png";
      imageLink.href = board.toDataURL();
      imageLink.click();
    });

    // Dark mode
    document.getElementById("themeBtn").addEventListener("click", () => {
      document.body.classList.toggle("dark-mode");
    });
  </script>

</body>
</html>
```


