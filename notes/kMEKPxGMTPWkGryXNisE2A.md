---
title: "7 月萌典松: moed11ct"
tags: event,moedict,hackpad
---

# 7 月萌典松: moed11ct

> [點此觀看原始內容](https://g0v.hackpad.tw/7-moed11ct)


時間：7/18 11am-8pm（歡迎遲到早退）
地點：[Bookshow.tw](http://bookshow.tw/traffic/) 基隆路一段 141 號 6 樓之 7（捷運市政府站步行三分鐘）
名額：35 人（[報名頁面](http://moe.kktix.cc/events/moedict-7-18)）
內容：比照之前[萌典松（ex.第五次）](https://g0v.hackpad.com/8-moed5ct#8-moed5ct-)，採「併松」模式舉行，歡迎 g0v 各大小專案加**萌**參加。
費用：採量力而捐、自由贊助方式。如有剩餘，捐給下次黑客松。
活動守則：[https://g0v.io/coc](https://g0v.io/coc)

流程：
- 11:30 專案、想法簡報介紹
- 12:00 自介、午餐、分組意見交流
- 13:30 十五分鐘短講
- 14:30 hack, eat, hack
- 17:00 第一次成果報告
- 17:30 hack, eat, hack
- 19:30 第二次成果報告
- 20:00 收播、閒聊

**萌典相關開發項目**
- iTaigi.tw
    - hackpad [https://g0v.hackpad.com/moed7ct-taigi-neologism?r=0#](https://g0v.hackpad.com/moed7ct-taigi-neologism?r=0#)
    - moqups [https://moqups.com/liz462/IMYHBVi5](https://moqups.com/liz462/IMYHBVi5)
    - 目前進度：已有基礎資料庫，後端大致完成、前端即將完成
    - [Taihoa楊允言老師提供資料庫-推薦用字表外字](https://github.com/sih4sing5hong5/tai5-uan5_gian5-gi2_phing5-thai5/blob/master/Taihoa%E6%A5%8A%E5%85%81%E8%A8%80%E8%80%81%E5%B8%AB%E6%8F%90%E4%BE%9B%E8%B3%87%E6%96%99%E5%BA%AB-%E6%8E%A8%E8%96%A6%E7%94%A8%E5%AD%97%E8%A1%A8%E5%A4%96%E5%AD%97.csv)
    - 未來人力需求：
        - 語言創意大隊：幫各台語詞想適合台語翻譯
        - 影音創意大隊：製作各種吸引人的台語短句、短片（格式設計）
        - 漢字正規化大隊：幫各種神奇的書寫方式轉寫成符合目前教育部規範的台語漢字及臺羅音標
    - 台語講談會？其他台語需求？
    - 與萌典的連結？（除了萌典專頁文章之外）
- 藏文萌典~
    - 語料：
        - [https://github.com/karmapa/tibetanchinesedict](https://github.com/karmapa/tibetanchinesedict) (CC0) 藏漢辭典 (已轉成moedict 格式)
        - [https://github.com/karmapa/monlamdict](https://github.com/karmapa/monlamdict) (CC0) 藏英雙向，以及藏藏辭典。(已轉成moedict 格式)
        - [藏文字典大全](http://blog.xuite.net/mkhadro/twblog1/124663040-%E9%98%BF%E8%98%AD%E2%80%A7%E8%8D%8F%E8%8A%8A%E5%A0%AA%E5%8D%93~+%E8%97%8F%E6%96%87%E8%BE%AD%E5%85%B8%E4%B8%8B%E8%BC%89%E5%9C%B0%E5%9D%80%E5%A4%A7%E5%85%A8)
    - 拼音檢索： [https://github.com/ksanaforge/tibetan](https://github.com/ksanaforge/tibetan)  (Wylie(藏文羅馬化方案)/Tibetan Unicode 雙向轉換)
```javascript
     var wylie=require("tibetan/wylie");
     wylie.toWylie("ཀརྨཔ")===wylie.fromWylie("karmapa")
```
    -  輸入藏文的方法
        - wikipedia 的多國語言線上輸入模組 [http://thottingal.in/projects/js/jquery.ime/examples/](http://thottingal.in/projects/js/jquery.ime/examples/)
            - 先選藏文(第11個 བོད་ཡིག། )，然後選 Tibetan EWTS，輸入 k 可得 ཀ
        - Windows 系統內建藏文 language code BO
    - ==Demo:== [https://karmapa.github.io/monlamdict/#](https://karmapa.github.io/monlamdict/#)[|data](https://karmapa.github.io/monlamdict/#|data)
    - 操作概說：
        - 比照 [http://amis.moedict.tw/](http://amis.moedict.tw/)
            - （資料結構請見 [https://amis.moedict.tw/dict-amis.json](https://amis.moedict.tw/dict-amis.json) ）
        - 檢索框可輸入 Wylie 字母、中文，或藏文字
        - 左側列表顯示 Wylie 字母 (?)
        - 右側主詞條顯示藏文字母 (?)
        - 右側敘述顯示中文、英文釋義
- 漢字源流資料集
    - [https://drive.google.com](https://drive.google.comf/folderview?id=0B1XMOr6Gyu3YbHBBSkZ1M2lmREE&usp=drive_web)[f](https://drive.google.comf/folderview?id=0B1XMOr6Gyu3YbHBBSkZ1M2lmREE&usp=drive_web)[/folderview?id=0B1XMOr6Gyu3YbHBBSkZ1M2lmREE&usp=drive_web](https://drive.google.comf/folderview?id=0B1XMOr6Gyu3YbHBBSkZ1M2lmREE&usp=drive_web)
    - 文總新釋出的資料集，歡迎把想到的應用寫在這裡
- 變調規則
    - [https://github.com/audreyt/moedict-webkit/blob/master/view.ls#L380](https://github.com/audreyt/moedict-webkit/blob/master/view.ls#L380)
- 加時app/kasi app
    - [https://github.com/sotronx/kasi](https://github.com/sotronx/kasi)
    - demo: [http://sotronx.github.io/kasi/](http://sotronx.github.io/kasi/)

## 併松

> 歡迎把想做的專案/計畫列在這裡！
> [name=Audrey T]


**超農域**
超農域本體\+ 診斷鑑定新坑

**政治承諾追蹤網 ppt (political promise tracker)**
專案 Hackfoldr: [http://beta.hackfoldr.org/ppt/](http://beta.hackfoldr.org/ppt/)

#### 松前進度

- 決定用程式將六都施政報告的內容爬出來！
    - 作為初始承諾資料
    - 「修改」比「新建」有效率
    - 政府若將某政策放進施政報告，那**_就得要做出來_**。
- 寫了把公文標號 PDF 轉成 CSV 的工具 [ppt-commitment-parser](https://github.com/g0v/ppt-commitment-parser)
- 將六都最近一次的施政報告（台南的是去年的）整理進 [Google spreadsheet](http://beta.hackfoldr.org/ppt/https%253A%252F%252Fdocs.google.com%252Fspreadsheets%252Fd%252F1EefGM7p3xlSMOcTFo5i8WkWbiZhwoBFv0rezFLIwUDo%252Fedit%2523gid%253D627721169)

#### 小松 TODO

- 將 [104 年市長施政報告](http://beta.hackfoldr.org/ppt/https%253A%252F%252Fdocs.google.com%252Fspreadsheets%252Fd%252F1EefGM7p3xlSMOcTFo5i8WkWbiZhwoBFv0rezFLIwUDo%252Fedit%2523gid%253D627721169)整理成適合放進資料庫的格式
> 因為項目很多，可以從格式比較整齊的桃園開始
> [name=Johnson L]

> 臺北與高雄各自有上千的施政進度要處理⋯⋯
> [name=Johnson L]

    - [x] 檢查 ppt-promise-parser 輸出的警告訊息
    - [x] 替施政進度挑選合適的標題
> 通常拿該項的小標即可。
> [name=Johnson L]

    - [x] 將之前[手動整理的承諾跟工作區的資料](https://goo.gl/UN0lcj)做匯整
    - [x] 將「承諾相關內容」（要做什麼）與「最新進展」（做到哪裡、預計怎麼做）分開
    - [x] 替每個進度填進度（「還沒做」「正在做」「已完成」三選一）
- 網站前端
    - [ ] commitment page 承諾頁面
    - [ ] index 首頁
- 網站資料後端
    - [ ] google spreadsheet --> mock data 的 script
> working on this
> [name=Johnson L]

    - [ ] 實作評分 API

**Data + Design 資料＋設計 正體中文版翻譯**
[http://bit.ly/data-design-zh](http://bit.ly/data-design-zh)
- 繼續翻譯，預計於下次大松釋出全文供校對。
今日進度：項目名稱第一版

**零時字引**
[簡報](https://docs.google.com/presentation/d/16MzEnhGiWYH2e5WMudW6Sc49BTWDf1_aicbFMU9nSrU/edit?usp=sharing) 用部件+筆劃搜尋罕用字 (up to Extension E)


**萌典粉絲團 / 出國比賽（a0kman）**
- a0kman 專案報告
    - 粉絲團突破 500 人, 歡迎投稿
    - 萌典介紹短片，毛片（？）釋出，怡君 ++

**人類學田野調查訪問（mglee）**
- 抽樣訪問了許多參與者，其中 au 的段落已採 [CC BY 4.0 公開放在 SoundCloud 上](https://soundcloud.com/audrey-tang/mglee-interview-20150718)。
    - 感謝 mglee [打成逐字稿](https://hackpad.com/20150718-Sxi1fRmfrYx)。

** 短講**
- [台灣司法結構的問題](https://docs.google.com/presentation/d/1ACvKWvs-x5g8nCW0_UkD9YNXT4r7bQ-x6lTWSr8phrk/pub?start=false&loop=false&delayms=3000)
- [關於課綱微調立委們、教育部長說了什麼？](http://event.cic.tw/course/)

**成果報告**
- [https://rawgit.com/g0v/z0y/master/](https://rawgit.com/g0v/z0y/master/)
- [https://karmapa.github.io/monlamdict](https://karmapa.github.io/monlamdict)
- [https://vtaiwan.tw/uberx](https://vtaiwan.tw/uberx)
- [http://event.cic.tw/course/](http://event.cic.tw/course/)
- [http://itaigi.tw/](http://itaigi.tw/)
- [https://github.com/g0v/ppt](https://github.com/g0v/ppt)


## 飲食庶務

 晚餐 15+2 人請點餐
> 綜合生魚片
> [name=雨蒼 林]

> 卡位 no16?(剛才沒舉手唷sorry +1) 
> [name=Huitse H]

> 涼拌茭白筍
> [name=Audrey T]

> 泰式椒麻雞
> [name=Zhemin L]

> 麻辣臭豆腐  地瓜葉 
> [name=Yap S]

> 月亮蝦餅
> [name=Johnson L]

> 蟹黃豆腐褒
> [name=宏圖 陳]

> 空心菜
> [name=余帛燦]

> 水蓮菜
> [name=nchild]

> 脆皮肥腸(剛才沒舉手唷sorry)
> [name=Mg L]

> 三杯皮蛋
> [name=Joy h]

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_fa9007ad1c2a7754fe2fb8a9b1ba980c)

- 綜合生魚片
- 月亮蝦餅
- 泰式椒麻雞 x 2
- 糖醋蝦球
- 蒜泥白肉 x 2
- 脆皮肥腸
- 芥藍牛肉
- 三杯皮蛋
- 大灣蚵仔煎 x 2
- 麻辣臭豆腐
- 蟹黃豆腐褒
- 空心菜 x 2
- 水蓮菜 x 2
- 地瓜葉 x 2
- 涼拌筊白筍 x 1
- 醉蝦（招待）

收支結算及明細掃描檔
- google spreadsheet [http://bit.ly/moedicthon2015](http://bit.ly/moedicthon2015)



