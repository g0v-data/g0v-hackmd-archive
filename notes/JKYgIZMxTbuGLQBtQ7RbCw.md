---
title: 2019/11/29 LINEBot 市容幫手｜4th 小聚會
tags: LINE, libot, 里長, 市容幫手
description: 用 LINE BOT 來幫助市民、里長與公務員。
---

2019/11/29
LINEBot 市容幫手｜4th 小聚會
===

#### 已完成

本次沒有已完成事項QQ

- Mars 寫了個去LINE對話記錄識別化的 Script 
- 吃了很多坑主班班的零食 XDD

#### 未完成

- [ ] UI (Maggie): Flex message、reach menu、card。
- [ ] 接 google sheet: Mars
- [ ] data science、structure: Foucault
- [ ] 多個檔案免費儲存問題: Mars、JAQQ


小聚當天討論的事項
---

班班找了兩位不太熟的主管談訪談事宜，結果被冷處理，因此本次小聚討論此專案未來走向及短期目標。

### 未來走向與短期目標
* 向政府提案，容易推行

### 如何建立公務員對Line Bot的信任感？
* 文字雲 對話內容視覺化
* Demo
* 問 Che Wei

#### 為什麼要分析對話內容？
* 視覺化之後可以拿去提案
* 發現問題，看群組內在討論什麼東西
* 分享分析結果，作為貢獻的一部分
* 建立分析自動對話內容分析工具，產生報表讓不了解群組狀況的人，可以快速瞭解群組狀況
* 自動對話內容分析工具又回頭強化讓人需要用line bot去處理問題的動力

### 分析對話內容工具
* 去識別化
    * https://gist.github.com/hmj1026/bf5b7f16b50341218e5abccb0f15460d
    * Mars 有土砲寫一份

* 分析內容：[文字雲](https://wordcloud.timdream.org/?fbclid=IwAR1QVIGRG5kFyLWJtNpTkz0qD1RaEtvfu2gm_kSW_tWZz5MWYXyLGOHdes8#wikipedia:Cloud)...
* 自動產生報表
* 參考資料：
    * https://medium.com/@rz12345/%E4%BB%A5-python-%E8%A7%80%E5%AF%9F-line-%E7%BE%A4%E7%B5%84%E6%88%90%E5%93%A1%E4%BA%92%E5%8B%95%E6%83%85%E5%BD%A2-1adb1bfcff53
    * 

### [分析對話](https://hackmd.io/@_rpCTKj0SNKpFaD89UGC_A/Hy3-dJVTr)
* 出現頻率
    * 里別
    * 被點名的機關
    * 案件
        * 類別
        * 地點
        * 特殊情況（如：颱風）
* 區別用途
    * 傳遞案件
    * 公告
    * 宣傳
    * 聯絡感情
* 使用習慣
    * 照片最大宗
* ？

### 公務員內部訓練文件



### Google Sheet 欄位討論

[Google Sheet 連結](https://docs.google.com/spreadsheets/d/15Ul8nJUa8ifThZcg4VyifqauP9nL7xHlzi94we3DDZs/edit#gid=422969468)

為了因應使用者講到一半就跑走了，決定分成三種類型儲存。其中，每次對話都會對 database 做一次 request。

1. user
存使用者屬性，及處理過的 case 。另外還有當下在對話中的 case。

2. case
放經由程式篩選過的資料，並由 dialogIDList 收集所有的對話記錄。如果使用 Google Sheet，尚未解決多張圖片、影片、聲音的儲存問題。

3. dialog
記錄使用者和Line Bot的雙向對話，包含文字、貼圖、圖片，userId為0代表機器人


### 下次聚會時間：線上討論


