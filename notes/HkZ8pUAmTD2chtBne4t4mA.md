---
tags: g0v-anniversary
---

# 十週年生日趴-集點互動式闖關共筆

## 概念
利用QR code 結合互動式的網頁，讓參與者掃描QR code 後，參與專案的貢獻，例如協助推廣社群、進行特定專案的微小貢獻。完成每一關後都可以獲得小獎品，如果闖完全部的關卡可以獲得特定的紀念品！

## 目的
希望利用互動式的方式，讓參與者更加認識g0v的專案，同時也讓專案可以從這樣的活動獲得參與者的貢獻，讓參與者、專案都能從中獲利！

## 分工
架設共筆：peter
協助流程：ddio 

## 摸彩開講須知

1. 集點紀錄會持續留存，但 ddio 會在活動前一天清除所有紀錄
2. 參與者再過完六關後，會看到：
   > 通知頁面，並可選擇是否要抽獎
   >> ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_56b42a58c3d6385cd6543f6e0825012f.png)
   > 登記抽獎後，可以看到抽獎序號
   >> ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d0b37a27379d3868f10a6014a82cbd17.png)
4. 開獎時，請打開： https://g0v.github.io/10v-points/lottery/
   - 要等到生日趴當天下午 3:50 才會顯示得獎清單（為了測試方便，目前先暫時打開）
   - 屆時會長得像這樣：
     > ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_508300d07c88969704dfa9ebc793c328.png)
   - 預設顯示前 20 筆序號，若有更多完成登記者，則會出現「載入更多」的按鈕，功主持人遙控顯示更多，以防找不到得獎者的狀況
   - 主持人可請參與者掃描頁面上的 QRCode ，即可找到自己（有登記抽獎者）的抽獎序號。抽獎序號頁面會長這樣：
     > ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_902be2f270f23c8e1b0b11b76b521409.png)
5. 議程助理若要協助領獎：
   - 可使用相同的網頁：https://g0v.github.io/10v-points/lottery/
   - 若需要登記誰已領獎，可使用[此試算表](https://docs.google.com/spreadsheets/d/1FEUfR2YDML1-XP9EkHLZ36T_2-jZCITkWY5YSNDtBzQ/edit?resourcekey#gid=980683186)

## 專案連結方式

闖關遊戲網站，將提供「單程票」、「單程直播票」、「去回票」三種導引方式。

1. 單程票：闖關遊戲將網址開至新視窗，點擊網址後就算闖關完成。
   - 適合需要引導瀏覽者開啟其他 App ，例如 Line 的專案。
   - 範例：https://g0v.github.io/10v-points/partner/%E5%B0%88%E6%A1%88%E4%B8%80%E8%99%9F/
2. 單程直播票：闖關遊戲將網址開在內嵌視窗（iframe）中，網頁打開就算闖關完成。
   - 適合已有現成網頁的專案。
   - 範例：https://g0v.github.io/10v-points/partner/%E5%B0%88%E6%A1%88%E4%BA%8C%E8%99%9F/
3. 去回票：闖關遊戲將網址開至新視窗，專案活動完成後，須連同 token 將瀏覽者導回闖關遊戲網頁，才算過關。
   - 適合可客製化活動、在意完成度的專案。
   - 範例：https://g0v.github.io/10v-points/partner/%E5%B0%88%E6%A1%88%E4%B8%89%E8%99%9F/

## 網站與程式

- 網站
  - 給生日趴參與者：https://g0v.github.io/10v-points/
  - 給主持人：https://g0v.github.io/10v-points/lottery/
  - 給議程助理：
    - 可看網頁： https://g0v.github.io/10v-points/lottery/
    - 如須標記領獎名單，可來[此試算表](https://docs.google.com/spreadsheets/d/1FEUfR2YDML1-XP9EkHLZ36T_2-jZCITkWY5YSNDtBzQ/edit?resourcekey#gid=980683186)
- 程式碼： https://github.com/g0v/10v-points/
- 修改資料，請至[此 Google 試算表](https://docs.google.com/spreadsheets/d/1FEUfR2YDML1-XP9EkHLZ36T_2-jZCITkWY5YSNDtBzQ/edit#gid=507488693)（找 Peter / MG / ddio 取得權限）
- 手動同步 Google 表單（或是等到隔日的台灣早上五點，自動更新）：
  1. 找到，或是加入成為 [g0v/10v-points](https://github.com/g0v/10v-points/) 的管理員
  1. 打開 https://github.com/g0v/10v-points/actions/workflows/periodic-update.yml
  2. 按下右側的 `Run workflow` ，等 60 秒，更新完成！
     > ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f3e035afd5c0c786a557c4d97ad6b09f.png)
- 素材
  - [設計素材](https://drive.google.com/drive/folders/1iU5mJ0-tbwN5GIKMKtKE269O81osXD4o)


## 要準備物品
紀念品？
各關獎品？

設定獎勵機制



## call for project 
我們希望跟專案合作，結合專案的內容來一起完成，也讓專案可以一起

### 目前已經談好的專案：
1. cofact 
   - 加入 linebot
3. disfactory 
   - 可能是大家來找廠，或是到時候想搭配的活動
5. g0vpodcast 
   - 聽完試聽帶(團隊提供)後填寫問卷
7. jothon?
8. 語音資料庫
   - 可以點進 [Common Voice](https://commonvoice.mozilla.org/) 玩幾次（華、臺）

### 數量：
我們要做幾個？

## 使用流程

- [流程圖](https://www.figma.com/file/SzTCOPVMBHs6Hk2nX91BXa/%E7%94%9F%E6%97%A5%E8%B6%B4-QR-Code-%E8%B7%91%E9%97%9C%E6%B4%BB%E5%8B%95?node-id=0%3A1)
   > ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1a6a74cfd6ef73f1bfad0a24cdc63c5f.png)
- 要支援：
  - 導回固定網址：例如設 line bot 為好友、survey cake
  - iframe / 導流回生日趴網站
- 提案方式
  - 提供投影片範本，讓各專案直接編輯 - 分工
  - 預留至少一個月，讓大家製作、調整網站

## 要做的事情：

### google form - peter

1. 專案名稱
2. 介紹（200字以內）
3. 圖片（檔案上傳）
4. 想要導流的網址
5. 補充 / 說明資訊


[去除個資後的公開資訊](https://docs.google.com/spreadsheets/d/e/2PACX-1vRnwi4M1rK17sNjFWlwkiSozz401CMvZnxmto53ipL9fIPoq9GPUSWRZ1c4oDCSUZkWbLyhFfyUw7AK/pubhtml?gid=1059324241&single=true)

### 網站 & 範例 ddio

1. 功能與釋出規劃：
   1. 08/03 範例網站 Alpha
      - 有功能，沒設計，方便驗證與試用流程
      - 使用 google spreadsheet 當作設定檔來源
   2. 08/17 範例網站 Beta ，開放申請
      - 加上 UI 設計，但沒有主視覺
      - 整合 google form ，讓 call for project / 黑客松時，可以現場試玩
   4. 09/01 正式網站
      - 加上主視覺與設計規範
      - 加上首頁（而不是只有個別專案頁）
      - 加上網站倒站警告機器人
   5. 09/xx 徵選結果公告，鎖定表單


## 文案

### 對專案團隊：

【互動式闖關：歡迎專案坑主一起來拼拼圖！】

g0v十週年了！在慶祝十週年的生日趴，我們除了想要用展覽跟派對讓大家一起同樂，紀錄自己參與g0v的瞬間，我們也希望與各個專案合作，利用集點互動式闖關的方式，讓參與闖關的人可以更加認識各個不同的專案，同時在參與闖關的過程中，也能讓大家對於專案做出小小的貢獻！

本次互動式闖關希望以貼在十週年生日趴場地中的QR code 連結來讓參與者參加闖關活動，參與者利用行動裝置掃描後就可以藉由闖關活動的網址，連到各個專案指定的地方，參與者完成任務後會回傳資訊到闖關活動的網站，讓我們可以確認參與者完成本次任務。

如果你的專案具有以下的特質，那就非常適合來一起拼拼圖！
1. 有需要使用者做出小小貢獻的
2. 想要讓使用者更了解專案內容的

如果專案坑主想要加入，歡迎與我們進行聯繫！此外，我們也希望專案坑主提供：
1. 導流用的固定網址
2. 專案的簡單介紹與照片等資料（可以參考我們提供的表單～）

表單連結：

如果希望聯繫我們的話，歡迎來 #10th-anniversary 找我們，或私訊 @peter（照片很繽紛的那個） @ddio吧！

### 對外：

【十週年生日趴：ASSEMBLE!專案者聯盟！】

來派對除了吃吃喝喝，當然是要玩遊戲的吧！g0v十週年也不例外，在今年這個十週年的盛會，我們也跟g0v社群中不同專案的坑主合作，讓來參加派對的參與者除了吃喝玩樂，也可以參與集點互動式闖關遊戲，除了更加認識不同的專案，也能貢獻自己的小小力量，一起召喚十週年多重宇宙的專案者聯盟！

我們在十週年生日趴的場地中設置了跟不同專案有關的闖關QR code，參與者可以在會場中尋找這些QR code 進入各個闖關活動，完成任務後就可以獲得獎勵！（未定：集滿所有活動更可以兌換XXXX）

本次參與的專案有：
1. coafact 
2. disfactory 
3. g0vpodcast 
4. jothon?
5. 語音資料庫

--
活動相關資訊

### 闖關圖卡內容

每個闖關圖卡內都有
1) 大標題(ASSEMBLE！專案者聯盟！)與活動介紹
2) 該關卡標題(e.g. 星球α：Cofacts 真的假的-訊息回報機器人與查證協作社群)、一小段專案介紹文字
3) QR Code
4) 掃描說明

----
**圖卡1：**

【ASSEMBLE！專案者聯盟！】
在這個零宇宙裡，散落著 g0v 零時政府不同專案的 QR code，掃描後就能快速連結到專案星球，只要花一分鐘的時間，你就能認識不同的專案，並且貢獻自己的小小的力量，一起召喚十週年多重宇宙的專案者聯盟！

<<星球α：Cofacts 真的假的-訊息回報機器人與查證協作社群>>

「Cofacts 真的假的」是一套連結網路訊息與事實查核的協作型系統。任何人都可以透過聊天機器人，將網傳可疑訊息進來；任何人也都可以擔任查核協作者，一起在網站上面一同撰寫對網傳訊息的回覆。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_70446a97e01a8936e8063c20e8c7117a.png)


掃描 QR code 後，LINE 加 @cofacts 好友，完成歡迎訊息中的使用教學。 

**圖卡2：**
【ASSEMBLE！專案者聯盟！】
在這個零宇宙裡，散落著 g0v 零時政府不同專案的 QR code，掃描後就能快速連結到專案星球，只要花一分鐘的時間，你就能認識不同的專案，並且貢獻自己的小小的力量，一起召喚十週年多重宇宙的專案者聯盟！

<<星球β：disfactory>>

disfactory希望藉由全民協力，一起揪出農地上正在違法興建的工廠！民眾可以使用我們開發的「農地違章回報系統」，現地拍照回報哪裏有農地違章，也可以鍵盤參與「大家來找廠」，利用辨識衛星空拍影像，抓出農地上的新建廠房。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8157dbe934b5912c290352d607e8d93d.png)


我們需要你玩完一輪「大家來找廠」，幫我們辨認農地上有沒有新增建物！

**圖卡3：**

【ASSEMBLE！專案者聯盟！】
在這個零宇宙裡，散落著 g0v 零時政府不同專案的 QR code，掃描後就能快速連結到專案星球，只要花一分鐘的時間，你就能認識不同的專案，並且貢獻自己的小小的力量，一起召喚十週年多重宇宙的專案者聯盟！

<<星球γ：g0v Podcast>>

「g0v Underground 零時電台」Podcast 節目 是 g0v 成立十週年後，再次從原本「g0v 零時電台」重啟展開的社群專案。接下來我們將會在這個 podcast 節目中跟聽眾分享 g0v專案、g0v貢獻者，以及很多關於 g0v 公民科技社群的專案幕後故事。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e1fc34c817d7ff39ef6fe42b7a3c3f7c.png)


邀請使用者到 apple podcast 上留言評論，分享聽眾對於節目的心得或未來想聽到的內容。

**圖卡4：**

【ASSEMBLE！專案者聯盟！】
在這個零宇宙裡，散落著 g0v 零時政府不同專案的 QR code，掃描後就能快速連結到專案星球，只要花一分鐘的時間，你就能認識不同的專案，並且貢獻自己的小小的力量，一起召喚十週年多重宇宙的專案者聯盟！

<<星球δ：零時小學校>>
零時小學校（Sch001）是聚焦在教育的 g0v 專案，將代表數位原生世代的 0 與 1 放入「School」，從零重新思考學校的意涵，同時也代表教育與數位社群的連結與協作。目前透過設計數位公民課程、學校課程合作、舉辦營隊及專案孵化競賽等方式進行推廣。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b8ad1395dd0e81c5728e6f778a54dde0.png)

進入 2022 專案孵化競賽提案列表，選擇一個提案給予回饋吧！


**圖卡5：**

【ASSEMBLE！專案者聯盟！】
在這個零宇宙裡，散落著 g0v 零時政府不同專案的 QR code，掃描後就能快速連結到專案星球，只要花一分鐘的時間，你就能認識不同的專案，並且貢獻自己的小小的力量，一起召喚十週年多重宇宙的專案者聯盟！

<<星球ε：島島阿學>>
島島阿學是由親師生以集體智慧共創的民主學習社群。邀請學習者一同解決民主教育兩大元素「自主學習、民主社群」的困難，如找不到目標、資源、學伴等。目前提供可共編的學習資源平台，邀學習者共享資源。一起慢慢學不用急，在互助共好中成就彼此。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2ac3317c4053dacad9df786d0f2d235d.png)


點選島島阿學首頁右上角「新增資源」，分享一個你很推薦的學習資源吧！


**圖卡6：**

【ASSEMBLE！專案者聯盟！】
在這個零宇宙裡，散落著 g0v 零時政府不同專案的 QR code，掃描後就能快速連結到專案星球，只要花一分鐘的時間，你就能認識不同的專案，並且貢獻自己的小小的力量，一起召喚十週年多重宇宙的專案者聯盟！

<<星球ζ：CourseAPI 開放式課程資訊匯流學院>>
CourseAPI 開放式課程資訊匯流學院，將整合近一萬筆開放式課程線上資源，建立入口查詢平台，提供個人學習者、自主學習推動單位與教育新創，取用資料並深化學習，就像是在書本上安置插座，讓知識如同電流一樣自由、廣闊。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_487960830b05d99783413f94a2429111.png)


前往使用 CourseAPI ，試著用一個關鍵字查詢相關課程。