---
title: "動民主 @ g0v 自由時代 hackath7n"
tags: 動民主,hackpad
---

# 動民主 @ g0v 自由時代 hackath7n

> [點此觀看原始內容](https://g0v.hackpad.tw/g6Ka3ms2rp3)


### 過去進度

- 上次的 [hackath6n 當天進度](https://plus.google.com/u/0/+ETBlue/posts/YVTZ7nhsgww)
- 2013/12/25 hackad0n 後決定進行 [動民主 2.0 的 MVP 版](https://g0v.hackpad.com/-2.0--A8UlpEbKfK2)
- tkirby 率先將表決功能做成 [動民主 0.5 精簡版](http://g0v.github.io/don-republic/framework/simple.html)
- 2013/12/30 跟著 au 做了一些[網路工具 x 新民主制度的研究](https://docs.google.com/drawings/d/1_AYWazW9FMLgNwfNj_och4r5nIMbhFyi2IhZpXyMxh8/edit)
- 2.0 MVP 版最關鍵的提案部分由於企畫困難，仍然卡在[做一半的 mockup](http://g0v.github.io/don-republic/public/index.html)
- 開發 2.0 MVP 版的期間陸續聽到公民團體的需求
- 2014/2/10 小松[針對 2.0 MVP 版在今年底選舉前的上線時程與可行性做討論](https://docs.google.com/file/d/0B0NsS2a-Qx8ZR2IzaWotSjR0dms/edit)，發現 2.0 主要的政策規劃功能目標族群小且開發門檻高，決定先做目標大眾且較易開發的 [全民記者會](http://g0v.github.io/don-press/public/index.html)
- 2014/2/10 當天晚上發現全民記者會跟沃草公司開發中的[市長給問嗎](http://visly.net/sixcities/pages/petition-list.html)專案重疊，原本想一起開發，但該專案當時不開源，且範圍只鎖定台北市長選舉，於是兩邊各自發展
- 勾勒出包括全民記者會在內的[動民主 app 家族可能的產品組合](https://g0v.hackpad.com/-2.0-app-a.k.a.-1.337-iBRhXaRlfZh)，目前將這組功能拆分、app 化的版本稱之為動民主 1.337

### 全民記者會預定的功能

- [全民記者會 mockup](http://g0v.github.io/don-press/public/index.html)
- 首頁：自動偵測目前位置，秀出目前縣市的政務官、候選人、質詢問題。可以手動選擇地方、中央、或全國。可以在質詢問題上連署，讓回答的人知道哪幾題應該優先作答。
- 問題頁：可以群眾收集政治人物在媒體上對該問題的回應，政治人物也可以自己上來作答，除了政治人物，公民團體或任何公開組織也可以加入搶答（皆以臉書專頁帳號認證）。一題可回答多次，長期累積後可以觀察到政治人物的政策轉變。
- 給分頁：可以看政治人物對各題的回答並給分，作為政見評分統計的根據，也可以用來篩選出優秀的政見，作為日後撰寫政策共筆的 idea pool。
- 政治人物頁：針對單一政治人物列出基本資料、被問的問題、回答的內容，需人工編輯整理回答的內容，濃縮成政見總覽（政見懶人苞）
- 競選擂臺頁：配合選舉活動，將各區候選人的政見以比較表格的方式呈現，按照分類並列，並顯示每個候選人在每個類別的政見的平均得分、平均支持度。
- 上線初期可能需要先開放公民團體帳號針對各自專長的領域提新問題，其他人僅可以連署和評分。一方面測試系統，一方面建立基本的發問品質。等社群風氣較固定後，再逐步開放所有使用者提新問題。

### 本日需要

- 把全民記者會的 mockup 補完
- 前端工程師：把已經完成的 mockup 套上 angular js
    - 簽名：t____y
- 後端工程師：弄資料、接 angularfire 之類的
    - 簽名：t\_\_\_\_y, j\_\_\_\_y, j________g
- 將工作切小（人形坑）
- [github repo 在此](https://github.com/g0v/don-press)

### 未來計畫

- 收集中央與地方各縣市官員名單、基本資料柴（膝部狗仔）
- 接觸各公民團體，尋找人力處理需要人工編輯的內容（製作政見懶人苞、處理每次選舉時競選擂臺的設定和候選人名單整理等）
- 解決企畫卡關的問題：成立動民主企畫組
    - 要填的坑包括…
        - 整理[動民主家族從古到今的文件](http://hack.g0v.tw/don-democracy)，補齊缺漏的部分，讓任何有興趣開發類似專案的人可以快速瞭解動民主的發展過程、走過哪些路、沒走過哪些路，節省重複摸索的時間。
        - 研究審議式民主，想像選舉罷免創制複決四大公民權怎麼實踐、未來的新民主制度可能怎麼運作、運作過程中需要哪些資訊工具協助、而動民主家族在整個新民主生態系中可能負責哪幾個環節、可能需要和哪些其他工具彼此串連。
        - 收集國內外類似專案、整理成功與失敗範例、分析背後的商業邏輯，收集使用者需求、收集大量靈感、天馬行空地發想[動民主 app 家族可能的成員](https://g0v.hackpad.com/-2.0-app-a.k.a.-1.337-iBRhXaRlfZh)，腦力激盪、畫大量的、多種版本的 mockup 草圖，作為產品規劃與介面設計的依據。
    - 跳企畫坑請簽名
        - ETBlue
        - simonpai
        - ipa
        -
- 解決資訊零散、開發者間交流不足的問題：召開定期黑客松
    - 進行的方式
        - 人數約 5-10 人，頻率約每週一次或隔週一次，時間由 ipa 視情況揪團，地點可能在 kktix / 沃草 或其他場地贊助單位
        - 程式組寫前後端串資料，企畫組補完還沒規劃好的頁面、支援程式組的需求，同時整理文件、收集資料、腦力激盪、畫草圖、討論未來的方向，簡單的說就是寫 code 兼喇賽大亂鬥
    - 要參加定期松的人…
        - [到這個hackpad簽名](https://g0v.hackpad.com/ur06eAVZRGo)
        - [報名即將到來的小松](http://g0v-mini.kktix.cc/events/don140226)
        - [加入這個g+社團](https://plus.google.com/u/0/communities/114108909405606736641)
        - [到hackfoldr逛逛之前的文件](http://hack.g0v.tw/don-democracy)


收集各縣市的候選人名單
政見總覽可以放 firepad 共筆整理


[#動民主](https://g0v.hackpad.tw/ep/search/?q=%23%E5%8B%95%E6%B0%91%E4%B8%BB&via=g6Ka3ms2rp3)

