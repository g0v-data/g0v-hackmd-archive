---
title: "vTaiwan.tw @ hackath12n"
tags: vTaiwan.tw, hackpad
---

# vTaiwan.tw @ hackath12n

> [點此觀看原始內容](https://g0v.hackpad.tw/RLDmz3h7oJg)

上層：[vTaiwan.tw 行政院法規線上諮詢系統](https://g0v.hackpad.com/oWRxOF4ilfx)

## 提案簡報

![](https://g0v.hackpad.tw/static/img/pixel.gif)
[https://speakerdeck.com/audreyt/vtaiwan-dot-tw-di-er-jie-duan](https://speakerdeck.com/audreyt/vtaiwan-dot-tw-di-er-jie-duan)

## 坑群

### 圖解流程

- [x] ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d902748b3fea0df55601b1214fc31d16)
    
    把  [https://demo.vtaiwan.tw/design/phase2.jpg](https://demo.vtaiwan.tw/design/phase2.jpg) 改成像 [https://demo.vtaiwan.tw/mockup/images/phase1.jpg](https://demo.vtaiwan.tw/mockup/images/phase1.jpg) 這樣 (CT)
- [ ] 板主 SOP 和上稿 SOP 也可以做成流程圖

### 草案對照

- [ ] 把 [https://github.com/g0v/closelyheld-ref1.vtaiwan.tw](https://github.com/g0v/closelyheld-ref1.vtaiwan.tw) 裡的 .docx 轉成結構化資料 (LY)
- [ ] 讓 Billab 復活，用來顯示甲案乙案 etc (LY)
- [ ] 加上逐條討論功能 (LY)

### 視覺主題

- [ ] 目前「數位商務模式」視覺是草原，文字是「可以不要去開曼設公司嗎」，需要有一個總提示
    - a0kman 提議「虛擬公聽會」（跟公聽會直播太像了）
    - 「網路審議平台」（適合政院嗎？）
    - 「法規線上諮詢系統」（就像是資料庫？）
- [ ] 找出「數位生活」（遠距教育、電傳勞動、遠距健康照護）的主題、文字 (william)
    - 主視覺 \-\- 土豆
    - Slogan --（電腦可以幫我們煮土豆，）接了網路的電腦可以讓土豆變什麼？
    - Statement -- 有沒有想過各樣不同的土豆種類？透過雲端廚師告訴我們更美味的煮法？或想探尋土豆的神秘療效？當生活數位化之後，能否利用其無遠弗屆的特性，創造更多的想像空間？
- [ ] 找出「數位公民環境」（開放資料、網路消費者保護、個人資料利用與去識別化）的主題、文字 (william)
    - 主視覺 \-\- Black box
    - Slogan -- 當黑盒子拿掉之後？
    - Statement -- 公開、透明的資料呈現了更多的細節，用以做為更全面的策略制定之時，也增加個資的曝光風險。我們試著聚焦在開放資料管理的討論，同時營造自由且安全的數位環境。

### Discourse (Ruby) Hacking

- [ ] 將 內嵌臉書 \+ 批踢踢 功能從 [雨蒼的 prototype](https://github.com/billy3321/vtaiwan_web_parser)移植進 [discourse/onebox](https://github.com/discourse/onebox/tree/master/lib/onebox/engine) 裡 (billy)
- [ ] 中文 @tag 別人（LY 好像有 pull req）
- [ ] 參考簡體中文翻譯，把[正體中文化](https://www.transifex.com/projects/p/discourse-org/)做完

### AngularJS Hacking

- [ ] [修好 MetaProvider](https://github.com/g0v/vtaiwan.tw/issues/28)，讓分享時可以看到預覽

### CSS Hacking

- [ ] 讓 talk.vtaiwan.tw 的「回覆」/「登入」更直觀：[g0v/vtaiwan.tw#13](https://github.com/g0v/vtaiwan.tw/issues/13)

### 簡化系統建置

- [ ] 把 [g0v/vTaiwan.tw](https://github.com/g0v/vtaiwan.tw) 裡提到特定網域的地方抽出來，變成設定檔
- [ ] 把 hard-code 的提案名稱改成從設定檔讀取（或許 Dockerize）
- [ ] 加上自己 fork 一份 vTaiwan 的操作說明

### 廣宣、文案

- [ ] 找比 [http://unsplash.com/](http://unsplash.com/) 適合的圖庫，也許有影像庫？
- [ ] 製作教學動畫？(William 的強者朋友)
    - [ ] 這裡有[一些素材](https://www.youtube.com/watch?v=X0Qu2EX7xug&list=PLEqOx80MURMyP4g-8wdiXIX5CDCk6ZCey&index=3&t=39m03s)
- [ ] 協助 Twitter、Google Plus、Plurk 或其他 SNS 訊息

### 工作組審議規則

- [ ] 確立建議規格書的定位及用途
- [ ] 審議流程及手冊設計
- [ ] 帶領人基礎訓練

