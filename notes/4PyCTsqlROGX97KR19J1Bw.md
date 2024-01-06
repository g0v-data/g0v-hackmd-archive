g0v 線上揪松功能待作計畫
=================
* 待作目標
    * 為下次小松做準備
    * 為下次大松做準備
    * 可以支援其他需要線上辦松的活動單位
* 待作項目：
    * Bug修正
        * [bug] 有時會聽不到一些人的聲音
        * 轉貼：
            * 摘：「我猜測他應該是用 Safari，Safari 要直接用 HackMD，沒辦法透過大會的網頁用 iframe 的 HackMD」
            * from https://g0v-tw.slack.com/archives/CBLASC4CF/p1590216405019500
    * 共通功能需求
        * [feature] API
            * 讓更多開發者可以自行開發界面
            * [API文件](https://g0v.hackmd.io/ZN1Fc6peTGiDVcICAGy1XQ) 開發中
       * [feature] 新手教學
            * 一步一步線上導覽怎麼加入。
        * [feature] 自行架設 Jitsi server 測試
            * 目前有些人實測超過 20 人影像就會有些不穩定，可能需要測試如果自架 jitsi server 能不能解決這問題。
        * [design] 界面設計
            * 現在界面太陽春。
        * [feature] 增加可偵測使用者收音品質提示功能
            * 減少人力測試的成本 (例如請使用者用麥克風念一段文字，然後用語音辨識 API 看看能不能成功辨識，確認使用者麥克風收音狀況)
            * 同時也可以測試當有播放音樂時，使用者再錄一次，會不會把音樂聲也錄進來，表示使用者收音狀況不佳
            * 也可以幫使用者測試他的攝影機或是螢幕分享功能是否順暢，這樣坑主可以隨時自行測試，不需要專人專門時間來測
        * [feature] 一個次頻道可能超過 20 人以上的解決方案
        * [feature] 自我介紹可以延用舊的活動的自介
        * [feature] 可以顯示使用者與 MeetJitsi 的網路品質，方便偵錯訊號不良
        * [feature] 整合提案、短講、成果報告流程方便 OBS 轉播
    * 支援其他活動需要功能
        * [feature] 不限於 slack 登入
            * 這功能是考慮假如不是只有 g0v 活動要用的話
        * [feature] 整合 Youtube or facebook 聊天室打字內容成為彈幕
        * [feature] 整合 slido 可以線上 QA