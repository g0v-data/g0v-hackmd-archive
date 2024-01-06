---
title: "children-image 兒童圖像"
tags: hackpad
---

# children-image 兒童圖像

> [點此觀看原始內容](https://g0v.hackpad.tw/i70OmIWyjaY)


## 初始提案：教育提案──孩子在哪裡？台灣孩子的幸福國度

- 發起人/拋磚人：小天
- 狀態：  草稿
- 專案簡介：
    - 每年台灣人民都會選出代表國家的「字」，那代表著全體人民對台灣的認知與期待；當大家沸沸揚揚地關注著許多知名的社會事件時，大多的社會事件都跟「人」有關，但大家往往忽略了形塑這些人，他們的人格的黃金六年，也就是孩提時期是何光景。
    - 孩子在台灣街上比比皆是，但除了家長和幼教相關人士，有多少人認真的去看看這些孩子在做些什麼？許多的成人，對孩子是陌生的，即使是有孩子的成人亦如是。
    - 如果是現在，我們也許會說：「這麼小的孩子也在滑手機？」我們也許還會說：「這孩子好可愛！」或是「好吵喔，家長在做什麼？」若要我們用一張圖或一句話描述我們的孩子，心裡**首先浮現的圖像會是什麼呢？**
    - 成人對孩子的認知，成為「如何對待/期待他們」的根本，影響著家庭，還有教育；所以，成人對孩子的觀點、印象、解讀 很重要。
    - 若能有一個平台或小工具，能夠呈現即時的「孩子當下的_____(幸福/不幸/...)狀態」，累積的數據或曲線圖，會傳達一些聲音，以及台灣孩子的圖像。
    - 詳細提案草稿：[https://docs.google.com/document/d/1znrHAtJEdW3mMX3pN2n60nYjbPsDCIuldgDi8FoPWKI/edit](https://docs.google.com/document/d/1znrHAtJEdW3mMX3pN2n60nYjbPsDCIuldgDi8FoPWKI/edit)
- 工作目標：
    - TBD
- 授權方式：
    - 平台：CC-BY
    - 內容（文字及統計數據）：CC-BY
    - 內容（照片及肖像）：copyrighted by the uploader, all right reserved.
- 使用資料：
    - 無現行可用資料，需透過此專案蒐集資料
- 徵求夥伴（有興趣直接簽名）：
    - NeedsWriter (撰寫基本資訊)：
    - NeedsProcess (設計作業流程)：
    - NeedsTalkingToRealPerson (需要真人溝通協調)：

提案影片


[http://youtu.be/Ub2t3QJvPV4](http://youtu.be/Ub2t3QJvPV4)

## 核心概念:

孩子是獨立的個體，非未完成的成人半成品
資訊的功能：
1)  省思性 (改變觀感:重新省視孩子的存在)
2) 衝擊性 (ex資訊排列組合後的真相,打破認知死角--以原住民為例)
3) 知道(某類別)孩子在台灣/全球的"位置" (ex下午4:30的孩子,可看出地區差異)

## 任何想法請直接編輯



## 介面需求發想:

1)  無操作,首頁畫面: 開架式照片牆(隨機)
2) 觀看點選:
a.不選類別--單一照片點選(呈現三個關鍵字)
b.選單點選 舉例:
- ''時間軸''橫切面--ex:下午4:30各地台灣孩子的圖像;
- ''地區''橫切面--ex:北區孩子的圖像;
- ''社經''橫切面--ex:GDP在XX以下地區,孩子的圖像
- ''地點''橫切面--ex:遊樂場裡的孩子圖像
※ 橫切面類別 (可新增) 有選單
※ 選單類別: 參與類別.上傳者身分別.地區.孩子年齡.上傳者與幼兒的關係.描述短語.孩子行為類別
c.決定時間軸
看見--->不同時間 _____ (類別)孩子的圖像

## 資料處理呈現需求發想:

    量--統計各類別分布圖、曲線圖
    質--關鍵字分析、各類別圖像意象視覺呈現、選擇照片與其他照片關聯性由高而低排列(撲布流)

## 3.技術開發



### Web 開發

mockups: [https://moqups.com/#!/edit/youchenlee/pY1opSlu](https://moqups.com/#!/edit/youchenlee/pY1opSlu)

### App 開發

使用: Ushahidi-Android
Github: [https://github.com/jessy1092/Ushahidi_Android](https://github.com/jessy1092/Ushahidi_Android)
IDE: Eclipse
環境: Android 4.2.2( android-17 ), Android 2.3.3 ( android-10 ), Google Play Services SDK
官方安裝說明: [https://wiki.ushahidi.com/display/WIKI/Build+The+Android+App](https://wiki.ushahidi.com/display/WIKI/Build+The+Android+App)

- Build
    - git clone git@github.com:jessy1092/Ushahidi_Android.git
    - Eclipse import
        - ./Libraries/abs
        - ./Libraries/Core
            - Add Core/libs/ushahidi_sdk-1.1.jar to build path
> 選取 ushaidi_sdk-1.1.jar 按右鍵 Build Path -> Add to Build Path
> [name=Lee]

        - ./Libraries/google-play-services_lib
        - ./Themes/Ushahidi
- Set Google Map Api Key v2
    - 申請流程: [http://goo.gl/q6MTUn](http://goo.gl/q6MTUn)
        - Api Console: [https://cloud.google.com/console/project](https://cloud.google.com/console/project)
    - Open Ushahidi/res/values/theme.xml, and set:
        <string name="google\_map\_api_key"> Your key </string>
- Run App

### 後台

Ushahidi Admin

### API

APP to Backend API: Ushahidi
Backend to Frontend API: ?



