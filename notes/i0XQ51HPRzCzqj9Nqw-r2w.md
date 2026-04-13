20260413實作
製作一個可以展出各週作業作品，主題以「水底世界」為主，要產生點選第一週就會在 iframe 顯示該週的作品內容，並顯示在 iframe 上面。利用 p5.js 製作展覽區內容，程式碼寫在 sketch.js 內。作品有兩週作品顯示，這個主題直接延續「海草」與「水底世界」的邏輯，將每一項平時作業視為水底的一個「生態聚落」。
AI回答:<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>水底世界：作業展覽館</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.4.0/p5.js"></script>
    <style>
        body {
            margin: 0;
            padding: 0;
            overflow: hidden;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            color: white;
        }
        #ui-layer {
            position: relative;
            z-index: 10;
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 20px;
            height: 100vh;
            box-sizing: border-box;
        }
        header {
            text-align: center;
            margin-bottom: 20px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
        }
        nav {
            margin-bottom: 20px;
        }
        .week-btn {
            background: rgba(255, 255, 255, 0.2);
            border: 1px solid rgba(255, 255, 255, 0.5);
            color: white;
            padding: 10px 20px;
            margin: 0 10px;
            cursor: pointer;
            border-radius: 20px;
            transition: all 0.3s;
            backdrop-filter: blur(5px);
        }
        .week-btn:hover {
            background: rgba(255, 255, 255, 0.4);
            transform: translateY(-2px);
        }
        #exhibition-container {
            width: 80%;
            height: 60%;
            background: rgba(0, 0, 0, 0.3);
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
            border: 2px solid rgba(255, 255, 255, 0.1);
        }
        iframe {
            width: 100%;
            height: 100%;
            border: none;
        }
    </style>
</head>
<body>
    <div id="ui-layer">
        <header>
            <h1>Underwater Portfolio</h1>
            <p>探索每一週的生態聚落</p>
        </header>
        <nav>
            <button class="week-btn" onclick="document.getElementById('display-frame').src='week1.html'">第一週：海草起源</button>
            <button class="week-btn" onclick="document.getElementById('display-frame').src='week2.html'">第二週：聚落繁衍</button>
        </nav>
        <div id="exhibition-container">
            <iframe id="display-frame" src="about:blank"></iframe>
        </div>
    </div>
    <script src="sketch.js"></script>
</body>
</html>
2. 背景視覺邏輯：/sketch.js
使用 p5.js 繪製動態海草與氣泡聚落。

New file: sketch.js
+99
let seaweeds = [];
let bubbles = [];

function setup() {
  let canvas = createCanvas(windowWidth, windowHeight);
  canvas.style('position', 'fixed');
  canvas.style('top', '0');
  canvas.style('left', '0');
  canvas.style('z-index', '1');

  // 初始化海草
  for (let i = 0; i < 15; i++) {
    seaweeds.push(new Seaweed(random(width), height));
  }

  // 初始化生態氣泡
  for (let i = 0; i < 20; i++) {
    bubbles.push(new Bubble());
  }
}

function draw() {
  // 水底深藍漸層
  background(10, 30, 60);
  noStroke();
  for (let i = 0; i < height; i++) {
    let inter = map(i, 0, height, 0, 1);
    let c = lerpColor(color(20, 50, 100), color(5, 15, 30), inter);
    stroke(c);
    line(0, i, width, i);
  }

  // 繪製與更新氣泡 (聚落感)
  bubbles.forEach(b => {
    b.move();
    b.display();
  });

  // 繪製與更新海草
  seaweeds.forEach(s => {
    s.display();
  });
}

function windowResized() {
  resizeCanvas(windowWidth, windowHeight);
}

// 海草類別
class Seaweed {
  constructor(x, y) {
    this.x = x;
    this.y = y;
    this.segments = random(10, 20);
    this.len = random(15, 25);
    this.offset = random(100);
  }

  display() {
    push();
    translate(this.x, this.y);
    stroke(50, 150, 100, 200);
    strokeWeight(8);
    noFill();
    beginShape();
    let nx = 0;
    for (let i = 0; i <= this.segments; i++) {
      let angle = map(noise(this.offset + i * 0.1, frameCount * 0.01), 0, 1, -0.2, 0.2);
      nx += sin(angle) * this.len;
      let ny = -i * this.len;
      vertex(nx, ny);
    }
    endShape();
    pop();
  }
}

// 氣泡類別 (象徵生態聚落中的生命氣息)
class Bubble {
  constructor() {
    this.reset();
  }
  reset() {
    this.x = random(width);
    this.y = height + random(100);
    this.r = random(2, 10);
    this.speed = random(1, 3);
  }
  move() {
    this.y -= this.speed;
    this.x += sin(frameCount * 0.05) * 0.5;
    if (this.y < -10) this.reset();
  }
  display() {
    noStroke();
    fill(255, 255, 255, 100);
    ellipse(this.x, this.y, this.r);
  }
}
. 週次內容範例 (供測試用)
您可以建立 week1.html 與 week2.html 來測試 iframe 的顯示。

/week1.html

New file: week1.html
+10
<!DOCTYPE html>
<html>
<body style="background: rgba(255,255,255,0.1); color: white; display: flex; justify-content: center; align-items: center; height: 100vh; margin: 0;">
    <div style="text-align: center;">
        <h2>第一週：海草的基本邏輯</h2>
        <p>這是利用貝茲曲線與 Noise 函數模擬的海草動態。</p>
        <div style="width: 100px; height: 100px; background: #2ecc71; margin: auto;"></div>
    </div>
</body>
</html>
/week2.html

New file: week2.html
+10
<!DOCTYPE html>
<html>
<body style="background: rgba(255,255,255,0.1); color: white; display: flex; justify-content: center; align-items: center; height: 100vh; margin: 0;">
    <div style="text-align: center;">
        <h2>第二週：水底聚落產生器</h2>
        <p>這週我們加入了物件導向的概念，讓多個生物個體能獨立運作。</p>
        <div style="width: 100px; height: 100px; background: #3498db; border-radius: 50%; margin: auto;"></div>
    </div>
</body>
     如何美化 index.html 的 CSS 讓它更有深海實驗室的科技感？
    AI回答:index.html
-13
+62
    <style>
        body {
            margin: 0;
            padding: 0;
            overflow: hidden;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            color: white;
            font-family: 'Courier New', Courier, monospace;
            color: #00f2ff;
            background-color: #000;
        }
        /* 掃描線特效 */
        body::before {
            content: " ";
            display: block;
            position: fixed;
            top: 0; left: 0; bottom: 0; right: 0;
            background: linear-gradient(rgba(18, 16, 16, 0) 50%, rgba(0, 0, 0, 0.25) 50%), linear-gradient(90deg, rgba(255, 0, 0, 0.06), rgba(0, 255, 0, 0.02), rgba(0, 0, 255, 0.06));
            z-index: 100;
            background-size: 100% 4px, 3px 100%;
            pointer-events: none;
        }
        #ui-layer {
            position: relative;
            z-index: 10;
            display: flex;
            box-sizing: border-box;
        }
        header {
            text-align: center;
            margin-bottom: 20px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
            text-shadow: 0 0 10px #00f2ff;
            letter-spacing: 4px;
        }
        header h1 {
            margin: 0;
            font-size: 2.5em;
            text-transform: uppercase;
        }
        nav {
            margin-bottom: 20px;
        }
        .week-btn {
            background: rgba(255, 255, 255, 0.2);
            border: 1px solid rgba(255, 255, 255, 0.5);
            color: white;
            background: rgba(0, 242, 255, 0.05);
            border: 1px solid #00f2ff;
            color: #00f2ff;
            padding: 10px 20px;
            margin: 0 10px;
            cursor: pointer;
            border-radius: 20px;
            border-radius: 0;
            clip-path: polygon(10% 0, 100% 0, 90% 100%, 0 100%);
            transition: all 0.3s;
            backdrop-filter: blur(5px);
            text-transform: uppercase;
            font-weight: bold;
        }
        .week-btn:hover {
            background: rgba(255, 255, 255, 0.4);
            background: rgba(0, 242, 255, 0.3);
            box-shadow: 0 0 15px #00f2ff;
            transform: translateY(-2px);
        }
        #exhibition-container {
            width: 80%;
            height: 60%;
            background: rgba(0, 0, 0, 0.3);
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
            border: 2px solid rgba(255, 255, 255, 0.1);
            background: rgba(0, 20, 40, 0.6);
            position: relative;
            border: 1px solid rgba(0, 242, 255, 0.3);
            box-shadow: inset 0 0 20px rgba(0, 242, 255, 0.2);
        }
        /* 裝飾角落 */
        #exhibition-container::after, #exhibition-container::before {
            content: "";
            position: absolute;
            width: 20px;
            height: 20px;
            border: 2px solid #00f2ff;
        }
        #exhibition-container::before {
            top: -2px; left: -2px;
            border-right: none; border-bottom: none;
        }
        #exhibition-container::after {
            bottom: -2px; right: -2px;
            border-left: none; border-top: none;
        }
        iframe {
            width: 100%;
            height: 100%;
            border: none;
            filter: cyan(0.5);
        }
        /* 動態數據裝飾感 */
        .status-bar {
            position: absolute;
            bottom: 10px;
            right: 20px;
            font-size: 0.8em;
            opacity: 0.7;
            animation: blink 1s infinite;
        }
        @keyframes blink { 50% { opacity: 0.2; } }
    </style>
</head>
<body>
        <nav>
            <button class="week-btn" onclick="document.getElementById('display-frame').src='week1.html'">第一週：海草起源</button>
            <button class="week-btn" onclick="document.getElementById('display-frame').src='week2.html'">第二週：聚落繁衍</button>
        </nav>
        <div id="exhibition-container">
            <iframe id="display-frame" src="about:blank"></iframe>
            <div class="status-bar">SYSTEM: ONLINE | SECTOR: DEEP_SEA_B3</div>
        </div>
    </div>
    
    body {
    margin: 0;
    padding: 0;
    overflow: hidden;
    font-family: 'Courier New', Courier, monospace;
    color: #00f2ff;
    background-color: #000;
}
/* 掃描線特效 */
body::before {
    content: " ";
    display: block;
    position: fixed;
    top: 0; left: 0; bottom: 0; right: 0;
    background: linear-gradient(rgba(18, 16, 16, 0) 50%, rgba(0, 0, 0, 0.25) 50%), linear-gradient(90deg, rgba(255, 0, 0, 0.06), rgba(0, 255, 0, 0.02), rgba(0, 0, 255, 0.06));
    z-index: 100;
    background-size: 100% 4px, 3px 100%;
    pointer-events: none;
}
#ui-layer {
    position: relative;
    z-index: 10;
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 20px;
    height: 100vh;
    box-sizing: border-box;
}
header {
    text-align: center;
    margin-bottom: 20px;
    text-shadow: 0 0 10px #00f2ff;
    letter-spacing: 4px;
}
header h1 {
    margin: 0;
    font-size: 2.5em;
    text-transform: uppercase;
}
nav {
    margin-bottom: 20px;
}
.week-btn {
    background: rgba(0, 242, 255, 0.05);
    border: 1px solid #00f2ff;
    color: #00f2ff;
    padding: 10px 20px;
    margin: 0 10px;
    cursor: pointer;
    border-radius: 0;
    clip-path: polygon(10% 0, 100% 0, 90% 100%, 0 100%);
    transition: all 0.3s;
    backdrop-filter: blur(5px);
    text-transform: uppercase;
    font-weight: bold;
}
.week-btn:hover {
    background: rgba(0, 242, 255, 0.3);
    box-shadow: 0 0 15px #00f2ff;
    transform: translateY(-2px);
}
#exhibition-container {
    width: 80%;
    height: 60%;
    background: rgba(0, 20, 40, 0.6);
    position: relative;
    border: 1px solid rgba(0, 242, 255, 0.3);
    box-shadow: inset 0 0 20px rgba(0, 242, 255, 0.2);
}
/* 裝飾角落 */
#exhibition-container::after, #exhibition-container::before {
    content: "";
    position: absolute;
    width: 20px;
    height: 20px;
    border: 2px solid #00f2ff;
}
#exhibition-container::before {
    top: -2px; left: -2px;
    border-right: none; border-bottom: none;
}
#exhibition-container::after {
    bottom: -2px; right: -2px;
    border-left: none; border-top: none;
}
iframe {
    width: 100%;
    height: 100%;
    border: none;
}
/* 動態數據裝飾感 */
.status-bar {
    position: absolute;
    bottom: 10px;
    right: 20px;
    font-size: 0.8em;
    opacity: 0.7;
    animation: blink 1s infinite;
}
@keyframes blink { 
    0% { opacity: 0.7; }
    50% { opacity: 0.2; }
    100% { opacity: 0.7; }
}
index.html
-104
+1
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>水底世界：作業展覽館</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.4.0/p5.js"></script>
    <style>
        body {
            margin: 0;
            padding: 0;
            overflow: hidden;
            font-family: 'Courier New', Courier, monospace;
            color: #00f2ff;
            background-color: #000;
        }
        /* 掃描線特效 */
        body::before {
            content: " ";
            display: block;
            position: fixed;
            top: 0; left: 0; bottom: 0; right: 0;
            background: linear-gradient(rgba(18, 16, 16, 0) 50%, rgba(0, 0, 0, 0.25) 50%), linear-gradient(90deg, rgba(255, 0, 0, 0.06), rgba(0, 255, 0, 0.02), rgba(0, 0, 255, 0.06));
            z-index: 100;
            background-size: 100% 4px, 3px 100%;
            pointer-events: none;
        }
        #ui-layer {
            position: relative;
            z-index: 10;
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 20px;
            height: 100vh;
            box-sizing: border-box;
        }
        header {
            text-align: center;
            margin-bottom: 20px;
            text-shadow: 0 0 10px #00f2ff;
            letter-spacing: 4px;
        }
        header h1 {
            margin: 0;
            font-size: 2.5em;
            text-transform: uppercase;
        }
        nav {
            margin-bottom: 20px;
        }
        .week-btn {
            background: rgba(0, 242, 255, 0.05);
            border: 1px solid #00f2ff;
            color: #00f2ff;
            padding: 10px 20px;
            margin: 0 10px;
            cursor: pointer;
            border-radius: 0;
            clip-path: polygon(10% 0, 100% 0, 90% 100%, 0 100%);
            transition: all 0.3s;
            backdrop-filter: blur(5px);
            text-transform: uppercase;
            font-weight: bold;
        }
        .week-btn:hover {
            background: rgba(0, 242, 255, 0.3);
            box-shadow: 0 0 15px #00f2ff;
            transform: translateY(-2px);
        }
        #exhibition-container {
            width: 80%;
            height: 60%;
            background: rgba(0, 20, 40, 0.6);
            position: relative;
            border: 1px solid rgba(0, 242, 255, 0.3);
            box-shadow: inset 0 0 20px rgba(0, 242, 255, 0.2);
        }
        /* 裝飾角落 */
        #exhibition-container::after, #exhibition-container::before {
            content: "";
            position: absolute;
            width: 20px;
            height: 20px;
            border: 2px solid #00f2ff;
        }
        #exhibition-container::before {
            top: -2px; left: -2px;
            border-right: none; border-bottom: none;
        }
        #exhibition-container::after {
            bottom: -2px; right: -2px;
            border-left: none; border-top: none;
        }
        iframe {
            width: 100%;
            height: 100%;
            border: none;
            filter: cyan(0.5);
        }
        /* 動態數據裝飾感 */
        .status-bar {
            position: absolute;
            bottom: 10px;
            right: 20px;
            font-size: 0.8em;
            opacity: 0.7;
            animation: blink 1s infinite;
        }
        @keyframes blink { 50% { opacity: 0.2; } }
    </style>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div id="ui-layer">