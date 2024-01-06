---
title: "開放民間租屋資料"
tags: 土地,居住,hackpad
---

# 開放民間租屋資料

> [點此觀看原始內容](https://g0v.hackpad.tw/Ih7Jp4pUD5y)


本文以 CC0 拋棄一切著作權

## 想解決的問題

台灣租屋市場長期國防布，不只市場效能不彰、資訊不對等產生套利空間，就算政府或民間想要介入改變，也無法準確描述問題與定義有效的衡量指標，因果循環下，只能使用有限的資料進行實驗。儘管要讓租屋市場能夠被「看見」，需要透過外部制度改革與內部供需雙方意識的改變，無法透過單一方法就解決所有問題，但至少目前能作的，是整理已公開，但尚未結構化的租屋資料，長期追蹤，協助後續的問題分析。

目前可公開的租屋資訊，散落在各民間租屋網站，但各網站的資料格式不統一，成交後租屋資料就會消失，而且還有各種詐騙內容（隱匿頂加、詐騙照片），因此需要有一個能夠收集並清理資料的地方，存放民間的租屋資料。

## 使用情境

希望透過爬蟲，長期收集各租屋網站、品牌公寓的可公開資訊，清洗後整理成格式統一的資料，供後續有需要的人使用。

### 身為需要租屋資料來作研究的 NGO ...

1.  可以根據需求過濾出想要的物件
    1.  時間、房型、價位，諸如此類
2.  可以來這個網站下載資料，下載的資料可以拿去跑其他程式或統計軟體
3.  每個物件要有可辨識編號，方便長期追蹤
4.  資料最好是已經編碼過的資料，方便跑統計
> 話說  SPSS 現在能不能接受 utf8 當作編碼的字串阿 XD
> [name=ddio J]



### 身為需要租屋資料來作其他服務的宅宅...

TBD

### 身為想要來看某屋成交行情、房客更換頻率的租屋客...

TBD

### 身為想要調查租金行情的房東...

從目前的資料裡，看不出房客滿意度呦 XD

## 目前成果

1.  原始碼：[https://github.com/g0v/tw-rental-house-data](https://github.com/g0v/tw-rental-house-data)
2.  資料說明與下載網站：[https://rentalhouse.g0v.ddio.io](https://rentalhouse.g0v.ddio.io)
3.  聊天室： g0v-slack#tw-rental-house-data [https://g0v-tw.slack.com/messages/CBXKTAXHD/](https://g0v-tw.slack.com/messages/CBXKTAXHD/)
4.  Mockup: [https://app.moqups.com/ddio/eIKAZKBzp4/](https://app.moqups.com/ddio/eIKAZKBzp4/view/page/aa9df7b72)[v](https://app.moqups.com/ddio/eIKAZKBzp4/view/page/aa9df7b72)[i](https://app.moqups.com/ddio/eIKAZKBzp4/view/page/aa9df7b72)[e](https://app.moqups.com/ddio/eIKAZKBzp4/view/page/aa9df7b72)[w](https://app.moqups.com/ddio/eIKAZKBzp4/view/page/aa9df7b72)[/page/aa9df7b72](https://app.moqups.com/ddio/eIKAZKBzp4/view/page/aa9df7b72)
5.  即時資料視覺化與快速分析：因為 Metabase 較吃資源，未開放匿名使用，有興趣的人，請聯絡 ddio 開帳號～

## 功能規劃

### 爬資料

透過爬蟲，定期收錄台灣各租屋網站、品牌公寓的租屋資料
1.  目標網站
    1.  \`DONE\` 591
    2.  崔媽媽
    3.  好房網
    4.  ？？
2.  需要的資料內容
    1.  \`DONE\` 案號
    2.  \`DONE\` 縣市、鄉鎮市區
    3.  `版權資料，不散佈` 照片
    4.  \`DONE\` 頂加、地下室、隔間（如果查得出來）
    5.  \`DONE\` 刊登時間、更新時間、關閉時間
    6.  \`DONE\` 租金
    7.  \`DONE\` 坪數
    8.  \`DONE\` 身份限制（學生、上班族）
    9.  \`DONE\` 性別
    10.  \`DONE\` 提供的設備
    11.  `版權資料，不散佈` 特色說明
    12.  \`DONE\` 刊登者代碼（可用 md5 去識別化）
    13.  大概的地點 / gps + 半徑？
    14.  同一物件的歷史資料 / 變化
    15.  連結外部資料
        1.  土地與建物資料，例如坪數、樓層、屋齡
3.  資料處理方式
    1.  \`DONE\` 抓下來後保留原始檔，方便加入演算法時，可以重跑
    2.  \`DONE\` 清理資料，將可編碼的資料整理乾淨
    3.  判斷同一物件的狀況變化
    4.  清理資料，判斷房屋資料準確度
        1.  頂加
        2.  詐騙房屋
        3.  盜圖
    5.  合併跨平台、平台內的相同物件
        1.  同一物件，多平台投遞
        2.  同一物件，多仲介投遞
        3.  同一物件，多個網頁（隱藏過去開價）
    6.  尋找同戶內的物件
        1.  [2018.06](http://news.ltn.com.tw/news/focus/paper/1207731)  隔間六間或十床以上，列為公共使用建築，須列管與符合相關安全法規
    7.  \`DONE\` 儲存結果

### 界面

阿宅 mockup: [https://app.moqups.com/ddio/eIKAZKBzp4/view](https://app.moqups.com/ddio/eIKAZKBzp4/view)

1.  原型機零號
    1.  \`DONE\` 資料下載 +資料集說明
2.  原型機初號
    1.  更詳細的資料下載頁面，包含
        1.  每個 csv 最後更新時間、使用的欄位版本 + 資料集成熟度（x.x beta / x.x）
        2.  說明資料集版本的意含
        3.  提供原始資料外的延伸資料集，例如
            1.  重複物件列表
            2.  疑似頂加列表
            3.  應該是住宅 flag
3.  原型機二號
    1.  物件時光機，顯示單一物件的詳細資料
        1.  解決 CSV 不方便預覽，而且沒有照片、說明和標題的問題
        2.  包含因著作權而無法散佈的資料，限制只有人類可以讀取，加註警語
    2.  有趣的統計結果視覺化
4.  原型機三號
    1.  傳統資料庫模式，選定過濾條件，顯示結果表格，並提供下載，滿足研究者基本需求（因為本坑的源頭是[薪資與租屋居住品質關聯調查](https://g0v.hackpad.tw/hZwt2iPr78w) <3）
5.  原型機四號：
    1.  提供較友善的互動界面，協助研究者找出有趣/想要的資料

### 開放資料

1.  在 Google Drive 上定期上傳每月、每季、每年的資料
2.  API ?

## 實做順序


### Release 0.1

- 爬資料：
        - [x] 591，每日 1 次
        - [x] 基本編碼清理
        - [x] 增加**`爬資料** 2.l` 張貼者編碼
- 搜尋界面：原型機零號
        - [x] 資料下載 +資料集說明

### Release 0.1.2

- 爬資料：
    - [ ] 爬蟲 keep alive
    - [ ] 增加**`爬資料**2.m` 粗略 GPS
    - [ ] 增加  **`爬資料 3.e`**  重複物件偵測
> 有產業專家回報，可能會有屋主將同一物件交給多名仲介交易的情況，所以網站上應該會抓到很多重複，而且發文者不同的相同物件 orz..
> [name=ddio J]

> 而且實務上也常有假資料，像是給錯誤的地址、盜圖使用等等，因為有些案件一公開就會一堆仲介想辦法找到屋主資訊去爭取委託，導致仲介之間基於競爭關係會給很模糊的資料，在有實際買家接觸時才會帶到真正地點看屋，網路只是用來宣傳
> [name=kiang]

    - [ ] 找同網站的第二資料來源來驗證爬蟲正確度
- 搜尋界面：原型機初號
    - [ ] 更詳細的資料下載頁面
    - [ ] 物件時光機

### Release 1.0

TBD


## 歷次黑客松與支線任務

### 第參拾次佛系黑客松 \- 不住頂加有多難

[投影片、與頂樓資料表格](https://drive.google.com/drive/u/0/folders/1BduObGhc4d2aHEn6ZXpOTyWA5aBB0cJW)
> 此區開放聊天與筆記～～～
> [name=ddio J]

1.  30 次佛系黑客松成果：
    1.  from Lucien -法律問題都解決，爬蟲原始碼和資料都可以公開了～
    2.  from ronny - 可以用使用執照 / 建照查詢房屋樓層（如果地址有公佈的話）
    3.  from poga -可以用 Metabase 作大表格的查詢、視覺化，不需要寫程式或 sql
    4.  [挑了 6F/6F的房子，完成了 30/487](https://docs.google.com/spreadsheets/d/1Jp6N2VWybQ0hjmaTb-OeXfaTqNC1NwDuhZFF1n-S3JA/edit#gid=1305586301)
    5.  下一步：開放資料 \+ API + 讓頂加標注更方便

1.  可能的頂加辨認方向：
    - 拿已經標註頂加的資料當訓練資料？
    - 數字裡的資訊：
        - 價位 x 房型 x樓層？
    - 文字裡的資訊：
        - 大陽台
    - 圖片裡的資訊：
        - 輕鋼架
        - 大陽台

### 簡單的異常值條件


- 物件與建物類型：
    1.  建物類型建議只挑公寓、透天、電梯大樓，因為華廈的數量過少，每個縣市大概都 < 1%
    2.  物件類型建議只挑整層住家、獨立套房、分租套房、雅房較為保險，雖然「其他」裡也有些是住宅，但也可能是其他不是給人類住的（？！）的東西
- 樓層
    3.  看起來 < 90 樓是個合理指標，只剩一間高雄 85 大樓的物件沒有過濾掉，剩下都是 < 45 層的![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_f1a0e5d64fd3899e3619a0fdcbfa5d49)
- 坪數
    6.  < 500 坪是個合理指標，超過 500 的都是 10000 坪以上的物件
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ecc1619b0c8d4c6f547363e35b51f767)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_5a26330f9a470e51e1a4965613258fe6)
- 租金 \+ 每坪租金
    1.  每坪租金超過 10k 的共有 13 筆，其中大部份是數字填錯，或是刻意打錯，但也有一間是短租型旅館。以月租旅館單日 500 元來說，月租最高**不應該超過 15k**，以此當作每坪租金的界線，還算合適，雖然有機會抓到一些錯誤的資料
    2.  每坪租金 6k - 10k 的共 21 筆，大多是可短租的宿舍或旅館，但也有一些不是給人住的東西混入，像[廣告看板](https://rent.591.com.tw/rent-detail-6306810.html) 、[店面](https://rent.591.com.tw/rent-detail-6333654.html)
- 樓層 \> 建物高，而且不是整棟出租
    - 不過樓層寫 99 的，目前[還是整棟](https://github.com/g0v/tw-rental-house-data/issues/11) ，所以還是要算在裡面 XD
    - ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0a0418c00c27fea46291aedddec7cceb)


### 重複物件

1.  降價調降，砍掉重練，照片完全一致 XD
    1.  降價前：[https://rent.591.com.tw/rent-detail-6211452.html](https://rent.591.com.tw/rent-detail-6211452.html)
    2.  降價後：[https://rent.591.com.tw/rent-detail-6316624.html](https://rent.591.com.tw/rent-detail-6316624.html)
2.  工人洗版，同帳號同物件多次刊登 XD
    1.  忠誠路靜巷2+1房，近天母運動公園 [https://rent.591.com.tw/rent-detail-6518714.html](https://rent.591.com.tw/rent-detail-6518714.html)
    2.  天母運動公園對面靜巷三房，近高島屋 [https://rent.591.com.tw/rent-detail-6518754.html](https://rent.591.com.tw/rent-detail-6518754.html)


## 人力需求


- [x] 法務，到底什麼資料可以公開阿 XD
- [ ] 物業管理達人 \- 怎樣解釋資料才是對的？
- [ ] 後端 \- 爬蟲 (scrapy)
- [ ] 後端 \- RESTful API (django)
- [ ] UX + UI 設計師，救救工程師作的 mockup
> 有興趣跳坑~ 但需要一點時間多了解一下這個專案，也希望可以有更明確的UI/UX需求
> [name=Peggy L]

> 目前有的想法如上，稍微清楚的部份「使用情境」，剩下的就需要自己發揮啦～目前是碰到使用者（以需要資料的媒體與 NGO 為主），會聊聊使用上的經驗，網頁沒有裝任何的追蹤程式
> [name=ddio J]

- [ ] 前端 \- UI (nuxt)
- [ ] 統計、資料科學家、ML專家 - 重複物件、住宅物件偵測

## 相關專案

1.  此坑的源頭：薪資與租屋居住品質關聯調查  [https://g0v.hackpad.tw/hZwt2iPr78w](https://g0v.hackpad.tw/hZwt2iPr78w)
2.  租屋相關資料：[https://g0v.hackpad.tw/x1M9qr6Syqw](https://g0v.hackpad.tw/x1M9qr6Syqw)
3.  標籤「居住」： [https://g0v.hackpad.tw/ep/group/E4rnjHPORJO](https://g0v.hackpad.tw/ep/group/E4rnjHPORJO)

