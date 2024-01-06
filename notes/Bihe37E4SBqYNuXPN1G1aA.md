---
title: 萌典松 11/01 第二十四松 moed24ct
tags: moedict, hackathon
image: https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_80b6bdd981601604aa8a7bdb4a36f989.png

---
# 萌典松 11/01 第二十四松 moed24ct
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c699b2a0295286cc09822998c48fbb35.jpg)

## 活動資訊
- 時間：2020/11/01 11:00 ~ 18:00 — **歡迎遲到早退**！（請在 g0v slack #jothon 喊開門）
- 地點：NPO HUB Taipei 4F 廚房（台北市重慶南路二段３號４樓，近捷運中正紀念堂站）
- 報名：https://moe.kktix.cc/events/moed24ct
- 直播：https://youtu.be/QEpFIGzS8Zs
- 行為守則：https://g0v.hackmd.io/s/COC

## 活動流程

| 時間 | 議程 |
| -------- | -------- |
|11:00|開始進場：伸懶腰、打招呼、暖身|
|11:30| 專案、想法簡報介紹|
|12:00| 自介、午餐、交流|
|14:00| 十五分鐘短講 open mic<tr><td colspan="2"> hack, eat, hack</td></tr>|
|17:30| 成果報告|
|18:00| 收播，閒聊，散會|

:::warning
請注意，這不是研討會，如果你沒參加過黑客松，請參考「[形形色色參與者](https://hackmd.io/@VsQ_Erf8QDS3ndjx9qWsYQ/BJQfJgFz-)」或 [前期現場錄影](https://www.youtube.com/playlist?list=PLdwQWxpS513DcD-Opw0Fl370dCzTKyG20)。
:::

## 活動注意事項

【誠徵】萌工小幫手 2 位，協助打點松間小事，服務大家腦力全開、賓主盡歡
【飲食】活動場地有飲水機並可以飲食，請自備餐點，或在附近覓食。
【費用】採量力而捐、自由贊助。如有剩餘，捐給下次黑客松。

## 誠徵萌工小幫手
:::warning
歡迎有意願協助場佈與訂餐的朋友在此留言。
:::

## 萌典/字典/語文相關專案
:::warning
11:30 專案、想法簡報介紹
請在底下填寫你的稱呼與專案名稱
:::

#### 恩予
希望萌典的筆畫可以條快慢

#### 黃米奧
台語聽寫練習  https://miau715.github.io/POJTest/

#### Billion
語文相關的(?)闢謠寫作練習 https://cofacts.org/hack

#### 拆國教院專業名詞辭典 (RSChiang)

之前在 #general 問過的計畫

**參考資料**：

* 2014 有人提案但是棄坑的 [moedict-data-terms](https://github.com/g0v/moedict-data-terms)
* [moedict-process](https://github.com/g0v/moedict-process)
* [舊的3du hackpad](https://g0v.hackpad.tw/3du.tw-ZNwaun62BP4)
* [14次萌典松](https://g0v.hackpad.tw/-moed14ct-oeBceDBeNA2)有台語缺字表：<https://ethercalc.net/koktai-ids.html>
    * 萌典最後使用的對照表：<https://github.com/g0v/moedict-epub/blob/master/sym-fuzzy-big5.txt>

#### 劉君磊
- 用一個中英文件翻譯庫存做翻譯功能=> https://www.deepl/press.html
用台灣的正式雙語文件庫存去設計一個文件翻譯的功能=> 台灣雙語文件來源=政府或其他語言
功能可以為了將來變成
- 改善外語搜尋功能=英語-德語-法語-搜尋功能
- 加西語

原來的軟件設計的 code 的兩個例子
Google:
https://translate.google.com/translate/releases/twsfe_w_20201027_RC00/r/js/translate_m_fr.js
Deepl:
https://static.deepl.com/js/translator_late.min.$8478f9.js

> 萌典 data flow (From [Makefile](https://github.com/g0v/moedict-webkit/blob/83135fd1253e11f1e29f27ed8e64511bf685d3ce/Makefile))
>
> 以法文為例：
> 1. CFDict 原始檔為 https://www.moedict.tw/translation-data/cfdict.xml
> 2. 由 xml2txt 轉成這樣的 txt file https://www.moedict.tw/translation-data/cfdict.txt
> 3. 再由 txt2json 轉成 JSON
>
> cedict.txt 例子：
> > 民主 民主 [min2 zhu3] /democracy/
> > 民主主義 民主主义 [min2 zhu3 zhu3 yi4] /democracy/
> 
> cfdict.txt 例子：
> > 民族 民族 [min2zu2] /nationalité/
> > 氣勢磅礴 气势磅礴 [qi4shi4pang2bo2] /d'une impétuosité irrésistible/d'un style vigoureux/
> 
> (cfdict 裡面沒有民主也沒有獨裁 lol)
>
> [name=mrorz]

成果報到：
換外語database用萌典的來源
暫時在找個人可以幫忙extract 英法德缺翻譯的資料
已經更新按照Cfdict最新的版本的文件
拿到缺外語詞的三樣文件後會通過外語專家論壇活動去改善萌典獨特的外語文檔



## 自由短講
:::warning
14:00~17:00 open mic 歡迎開講
請在底下填寫你的稱呼與短講題目
:::

### 直播教學 by tmonk
- 這個月預計將設計一系列 jothon-online 直播教學的影片，提供已簡易器材、開源軟體、流程設計的整套直播教學。

## 成果報告

#### 萌典筆畫調快慢
已送 PR https://github.com/g0v/moedict-webkit/pull/275
謝謝小蟹 🦀


謝謝阿三第一線提供使用者回饋讓更多小朋友可以清楚的寫筆畫
你會寫烏龜的龜了嗎





唉唷好近喔
下去下去
下去下去
下去啦
啦啦啦


#### Cofacts 本日貢獻
（也有阿三）阿三很棒
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e5943e4d371bd517ad1bb27c3e8d2552.png)

#### 國教院辭典

* **問題**：data.gov.tw 和官網釋出的資料新舊和內容不一致
    * → 看起來官網比較新，先抓下來再說
* **進度**：已經可以批次把類別抓下來、解壓縮、轉換成 CSV 了！
    * Ronny 是教育部的開放資料諮詢委員，可以月底戳他們
    * 如果覺得外來用語是個問題，就該努力讓這種詞典便於大眾存取啊啊啊 — [name=RS]

Repo: https://github.com/rschiang/naer-terms

#### 識字測驗 (tmonk)

#### 辯論機器人 (Ronny)

## 場邊閒聊

## 今日帳目

### 收 
- NTD 1,000

### 支
- NTD 1,586 Pizza and 炸雞
- NTD 524 餅乾與飲料

