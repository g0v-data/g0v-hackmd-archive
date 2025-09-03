---
tags: vtaiwan
---

# 「SenseMaker意見綜整器」使用說明(V2)

*這個版本主要是給Peter在2025/09/13~14高雄面海松使用*

## SenseMaker是什麼？

* [SenseMaker意見綜整器](https://github.com/Jigsaw-Code/sensemaking-tools) 透過Google 的 AI 服務，可以用來分析大數據，產生有意義的結果，包含主要共同點和主要意見分岐等。
* 例子：這是[一則報告實例(中文輸出版)](https://hackmd.io/N6h_hErOQBWjP1K8iyNxzg?view)，主題是'Share your views on generative AI'，包括：*356 條聲明和8,005 票*



## 如何上手使用SenseMaker？

方法不只一種，本文介紹的是透過Web UI，快速上傳資料並生成報告的方法：



## 前置準備1：取得open router AI模型的執行點數和API KEY

1. 先註冊一個[open router](https://openrouter.ai/)帳號，可以用Google Login。



2. 登入後，右上角滑鼠滑上去會有一個下拉選單，長這樣![](https://g0v.hackmd.io/_uploads/rkDpfgr5xe.png =200x)



3. 點入右上角下拉選單的"Credits"頁面，用VISA卡儲值(體驗的話，先存5美金就夠用30+次了。)



![](https://g0v.hackmd.io/_uploads/B1ZBQlH9ex.png)



4. 點入右上角下拉選單的"Keys"頁面，儲值後取得API KEY

![](https://g0v.hackmd.io/_uploads/B1uAZlr5ge.png)



## 前置準備2：導出Polis.tw的原始意見資料

*(建議使用Chrome瀏覽器)*

1. 進入[polis.tw](https://polis.tw)的報告頁report page

![](https://g0v.hackmd.io/_uploads/rkim4eS5gl.png)



2. 開啟[開發者模式](https://developer.chrome.com/docs/devtools/open?hl=zh-tw)，找到用 GET /api/v3/comments 回來的 JSON 。

    * 開發者模式選「網路」> 「全部」>「回應」
    * 過濾器打上「/api/v3/comments」
    * 重新載入頁面
    * 會找到唯一一個JSON格式的資料，就是它

![](https://g0v.hackmd.io/_uploads/S1rc6zjHeg.png)


3. 把它全選複製

4. 在電腦中開新檔案，命名為polis_report.json


5. 把剛才複製的全文貼上

6. 檢核: 您可以額外用[JSON Lint網路工具](https://jsonlint.com/)，把全文貼上，以檢查您的JSON有無漏掉的部分？(有漏掉的部分，格式不完整就無法生成報告)



## 重頭戲：上傳資料給Sensemaker


1. 前往[Sensemaker Web UI網站](https://sensemaker-frontend.pages.dev/)

2. 在介面上填上您的open router之API KEY

![](https://g0v.hackmd.io/_uploads/Sypr8lHcle.png)

3. 模型名稱不要動，就保留openai/gpt-oss-120b

4. 對話背景和環境一欄，可填可不填

5. 輸出語言，目前有六種語言可以選(繁中, 簡中, 英文, 法文, 西班牙文, 日文)。English是最穩定的。中文也經過多次測試。建議先跑預設的「繁體中文」。有興趣的話也可以跑別的語言，測一下不同語言的報告品質。


6. 會有一則警語提醒模型有不穩定性

![](https://g0v.hackmd.io/_uploads/BJ1nPeH5lg.png)

7. 重試模式可以自由選擇(建議是使用預設的「正常模式」)

8. 按「選擇檔案」把前置準備的polis_report.json上傳


9. 按「開始分析」鈕


10. 靜候5~25分鐘(視資料量大小而異)，就可以看到報告


![](https://g0v.hackmd.io/_uploads/ByaRtgH9ee.png)


11. 報告出來後，下方會多一個「下載Markdown」按鈕，按下去即可下載報告(markdown格式)到電腦中



## 支援

> 因為目前整個專案的核心工具, 後端, 前端都還在MVP實測階段， 可能會有沒測到bug，請大家多包涵，並協力debug，遇到問題請僅量提出，謝謝
> [name=Bestian]


### vTaiwan slack頻道
https://g0v-tw.slack.com/archives/C2Q1M4N1J

### Github議題區(障礙回報)
https://github.com/g0v/sensemaker-frontend/issues


### 支援聯絡電郵信箱
Email: bestian@gmail.com









