教練已經瀏覽目前的使用者故事，
也有逛過致敬對象 巴克幫 ，
想要對齊一下彼此的認知、請協助確認與教練的理解有沒有出入：

## (1) 角色：訪客 / 未登入者
### 功能
**優先：**
- 介紹平台(組織使命、故事、工作人員)
- 最新消息(活動、部落格)

**候補：**
- 加入我們(招募活動)
- 常見問題
- 引導到登入註冊

## (2) 角色：捐贈者
### 功能
**優先：**
- 登入註冊
- 查看捐款紀錄
- 瀏覽線上認養列表
- 查看認養對象的專屬資料
- 選擇捐贈方案(物資/多元化支付款項/義賣商品)
- 更新個人資料、篩選條件
- 
**候補：**
- 通知(近況/獎勵)
- 留言
- 點讚

## (3) 角色：平台管理者
### 功能
**優先：**
- 登入(後台系統)
- 查看交易紀錄
- 更新公告(維護平台的最新消息，例如介紹、活動)
- 更新受認養貓狗的專屬資料

**候補：**
- 招募
- 回覆留言和問題
- 更新公告(部落格文章、捐贈需求/發信通知)

## (4) 角色：響應企業
### 功能
**候補：**
- 聯名商品
- 企業名單(曝光公司行號)

## (5) 角色：流浪動物收留者
### 功能
候補：
- 查看認養對象的專屬資料(未來照顧建議)
- 通知(公益活動)
- 收留的認養流程(例如評估、會面等等)

使用者故事延伸出來的問題，請各位協助釐清：
1️⃣ 各角色的功能，請協助區分主要和次要功能，會影響後續開發的優先順序
2️⃣ 請討論是否要同時製作線上認養(捐贈) 和 帶我回家(領養)兩種路線？以教練的觀點，建議專注在線上認養，因為目前角色 1~4 功能羅列比較齊全


以上內容和問題，請幫忙確認和回覆~以利於後續的開發嘿！！ 


# 1.使用者故事

## **主要使用者**

### **捐贈者**

- [O] - 我希望了解組織的使命和成功故事，以便對我的捐款感到放心。

- [O] - 我希望能夠註冊及登入帳號，以便捐款及查看過往的捐款紀錄。**（Morning）**（我不確定大家有沒有覺得一定要註冊登入後才能捐款贊助，也不確定之後六角會提供怎樣的API能不能做到）

- [O] - **關於我們**。我希望平台有一個關於組織的頁面（有地址電話等等），方便取得聯繫。**（Morning）**

- [O] - 我可以在”我要捐贈”選單中選擇以捐贈物資(例如:衣服、玩具)或捐贈款項的方式贊助這隻貓狗。**（Shiloh）**

    - 我希望除了捐贈以外，也能透過購買義賣商品的方式幫助浪浪，並且了解商品背後故事。**（Kevin）**

    - 希望我可以選擇直接捐款給特定貓狗或是一般捐贈（不指定）。**（Morning）**


- [ ] - 我希望有個頁面可以看到所有待認養的貓狗。**（Morning）**


- [ ] - 我可以在平台上的”線上認養”選單中看到每隻貓狗的專屬資料，例如:體重、健康狀況、個性。**（Shiloh）**

    - 我可以在待認養的貓狗的頁面，看到他們的基本資料，甚至是個性﹑健康狀況等等。**（Morning）**

- [ ] - 我可以在贊助貓狗的清單中為貓狗打氣加油或是觀看其他捐贈者的喊話。

    - 在每隻貓狗的資料中我可以為我有意願贊助的貓狗點讚。**（Shiloh）**

    - 我可以在捐贈後，在貓狗資料底下留言給貓狗或看到其他捐贈者的留言。**（Shiloh）**

- [ ] - 我希望能有多元的捐款方式，如電子支付、轉帳、超商繳費、電子發票愛心碼、飼料捐贈、醫療支持。**（Kevin）**

- [ ] - ~~我希望能追蹤受我捐贈的流浪貓狗的狀況，以確保他們得到良好的照顧。（已有具體方案）~~
    - 我可以在贊助這隻貓狗後，定期收到其近況照片與各項生活資訊。**（Shiloh）**

    - 我可以在捐贈後，獲得贊助的貓狗特定的獎勵或是獎品（xx的乾媽證書等），增加彼此的連結。**（Kevin）**


### **平台管理員**

- [ ] - 我必須擁有帳號並登入後，才可以使用後臺管理系統。**（Morning）**

- [ ] - 我可以在後台追蹤每一筆捐贈的交易紀錄。

- [ ] - 我可以建立官方公告，以通知平台更新或重要資訊。

    - 我可以於”近期活動”選項中定期發布最新活動內容並發信邀請捐贈者一起參與實體與貓狗見面活動與活動須知。**（Shiloh）**

- [ ] - 我可以更新和維護流浪動物資料，以便保持網站資訊的準確性和及時性。

    - 我可以在貓狗資料中顯示這隻貓狗已收到的捐贈款項&物資內容，並留下可以建議給捐贈者做的行動(例如:這隻貓或狗已經有很多糧食了，最近天冷了需要衣服~)，讓捐贈者更安心且不重複捐贈太類似的物資。**（Shiloh）**

- [ ] - 我可以管理並回覆捐贈者和訪客的留言以及問題，提高網站的互動度以及可信度。**（Kevin）**

## **次要使用者**

### **流浪動物收留者**

- [ ] - 我希望閱讀到收留流浪貓狗後的相關緊急措施及未來對寵物的照顧提示和建議。

- [ ] - 我希望得到一些公益活動的資訊（絕育、疫苗）。**（Kevin）**


### **一般訪客**

- [ ] - ~~我希望了解組織的歷史和使命甚至相關工作人員，以便了解其目的。（已有具體方案）~~
- [ ] - 我希望了解組織的歷史和使命。

    - 我希望可以閱讀園區負責人、工作人員的故事、簡介，讓我更加認識這些英雄。**（Kevin）**

- [ ] - 我希望瀏覽部落格，閱讀關於寵物照顧和成功故事的有趣文章。

- [ ] - 我希望可以用實際行動幫忙，想看到徵才、招募義工的資訊。**（Kevin）**

- [ ] - 我希望可以查看過去以及即將舉行的活動紀錄、照片，以便參與未來的活動。**（Kevin）**

- [ ] - 我希望可以看到情況特殊、緊急需要幫助、資源的浪狼資訊。**（Kevin）**


### 響應企業

- [ ] - 我是認同平台理念的企業，想要捐款、掛名於網站上並推出聯名商品或舉辦活動。**（Shiloh）**

- [ ] - 我是一般企業，我希望針對捐款可以曝光公司行號。**（Kevin）**