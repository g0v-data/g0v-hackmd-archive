## 5/26筆記

第一次指令:

要取得台北市opendata資料來做即時雨量顯示 請採用台北市的opendata雨量顯示 採用API介接 該API網址為https://wic.gov.taipei/OpenData/API/Rain/Get?stationNo=&loginId=open_rain&dataKey=85452C1D API使用方式採用GET 請採用p5.js撰寫程式碼 程式碼寫到skrtch,js檔案內 採用全螢幕畫布 取得的資料顯示在畫布網頁上因為台北市opendata取得的資料 無法顯示在127.0.0.1網址上 所以要採用代理伺服器取得台北市opendata資料內容 請在程式碼內設定代理伺服器

程式碼:


let rainData = null;
let apiUrl = 'https://wic.gov.taipei/OpenData/API/Rain/Get?stationNo=&loginId=open_rain&dataKey=85452C1D';
// 使用 AllOrigins 免費代理伺服器來繞過 CORS 限制
let proxyUrl = 'https://api.allorigins.win/raw?url=' + encodeURIComponent(apiUrl);
let lastUpdateTime = 0;
let updateInterval = 10000; // 每 10,000 毫秒（10秒）更新一次資料

function setup() {
  // 建立全螢幕畫布
  createCanvas(windowWidth, windowHeight);
  
  // 初始讀取資料
  fetchRainData();
  lastUpdateTime = millis();
}

function draw() {
  // 使用具有 Y2K 氛圍的舒適深色調背景
  background(30, 32, 45);
  
  // 檢查是否超過更新間隔，若是則重新抓取即時資料
  if (millis() - lastUpdateTime > updateInterval) {
    fetchRainData();
    lastUpdateTime = millis();
  }
  
  // 顯示標題與 UI 狀態
  drawUI();
  
  // 顯示雨量資料
  if (rainData && rainData.Data) {
    displayData(rainData.Data);
  } else {
    // 資料載入中或失敗的提示
    fill(200);
    textAlign(CENTER, CENTER);
    textSize(20);
    text('即時雨量資料載入中或正在嘗試透過代理伺服器連線...', width / 2, height / 2);
  }
}

// 取得資料的函式
function fetchRainData() {
  // 使用 p5.js 的 loadJSON，並傳入 callback 函式
  loadJSON(proxyUrl, gotData, handleIncomingError);
}

// 成功取得資料的回呼函式
function gotData(data) {
  console.log("資料更新成功！", data);
  rainData = data;
}

// 失敗時的回呼函式
function handleIncomingError(err) {
  console.error("讀取 OpenData 發生錯誤 (可能是代理伺服器流量限制或 API 異常):", err);
}

// 繪製標題與狀態列
function drawUI() {
  push();
  // 標題列
  fill(205, 180, 219); // 浪漫的薰衣草紫 (#cdb4db)
  textSize(28);
  textFont('sans-serif');
  textStyle(BOLD);
  textAlign(LEFT, TOP);
  text('臺北市即時雨量監測 (Open Data API)', 40, 40);
  
  // 狀態提示
  fill(189, 224, 254); // 粉藍色 (#bde0fe)
  textSize(14);
  textStyle(NORMAL);
  let nextCheck = Math.max(0, Math.ceil((updateInterval - (millis() - lastUpdateTime)) / 1000));
  text(`[系統狀態] 自動更新中... 預計 ${nextCheck} 秒後重新整理資料`, 40, 80);
  pop();
}

// 渲染雨量資料清單
function displayData(stations) {
  let startX = 40;
  let startY = 130;
  let itemWidth = 280;
  let itemHeight = 90;
  let spacing = 15;
  
  // 計算畫布寬度內每行可以塞下幾個測站卡片
  let cols = Math.floor((width - startX * 2) / (itemWidth + spacing));
  if (cols < 1) cols = 1;

  for (let i = 0; i < stations.length; i++) {
    let s = stations[i];
    
    // 計算卡片的網格位置
    let col = i % cols;
    let row = Math.floor(i / cols);
    let x = startX + col * (itemWidth + spacing);
    let y = startY + row * (itemHeight + spacing);
    
    // 如果卡片超出視窗高度則停止繪製（防止無限下延）
    if (y + itemHeight > height) break;
    
    // 繪製卡片背景
    push();
    stroke(255, 255, 255, 30);
    strokeWeight(1);
    
    // 根據雨量大小微幅改變卡片底色（有雨時帶點夢幻藍）
    let rainValue = parseFloat(s.Rainfall1hr) || 0;
    if (rainValue > 0) {
      fill(40, 55, 80); 
    } else {
      fill(45, 48, 65);
    }
    rect(x, y, itemWidth, itemHeight, 8); // 帶圓角的卡片
    
    // 寫入測站名稱
    noStroke();
    fill(255);
    textSize(16);
    textStyle(BOLD);
    textAlign(LEFT, TOP);
    text(s.StationName, x + 15, y + 15);
    
    // 寫入行政區或所屬單位
    fill(180);
    textSize(12);
    textStyle(NORMAL);
    text(s.Location || "臺北市", x + 15, y + 40);
    
    // 顯示 1 小時累積雨量
    textAlign(RIGHT, BOTTOM);
    textSize(24);
    textStyle(BOLD);
    if (rainValue > 0) {
      fill(189, 224, 254); // 有雨顯示亮藍色
    } else {
      fill(120); // 無雨顯示灰色
    }
    text(rainValue.toFixed(1), x + itemWidth - 55, y + itemHeight - 15);
    
    // 單位
    textSize(12);
    textStyle(NORMAL);
    fill(150);
    text(" mm", x + itemWidth - 15, y + itemHeight - 18);
    pop();
  }
}

// 當視窗大小改變時，自動調整畫布大小保持全螢幕
function windowResized() {
  resizeCanvas(windowWidth, windowHeight);
}
