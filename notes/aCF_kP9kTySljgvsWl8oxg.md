---
title: "台大新聞所「調查報導」課程分享"
tags: hackpad
---

# 台大新聞所「調查報導」課程分享

> [點此觀看原始內容](https://g0v.hackpad.tw/GWI2LM21Ld0)


台大新聞所林照真老師今年開了「調查報導」課程，其中安排了三天希望可以由業界的專業人士給新聞所學生一些資料取得、使用、分析相關的知識，因此開這份 Hackpad 是希望可以整理一下能夠在三天的時間跟學生分享些什麼，並且看看能不能有人跳坑，順便把這些課程內容錄影下來，也可以分享給更多非程式背景的人了解怎麼用電腦幫助資料分析處理。
> 林老師是直接與我連絡的，希望我分享爬資料的技術，但是我覺得我爬資料的技術太黑手了 XD 好像不太適合新聞所的學生，所以如果要我幫忙上三天課九個小時我覺得我搾不出那麼多東西可以說 XD因此我先答應了分享一天，也希望可以拉到其他人來跳坑
> [name=Ronny W]

> 再這樣列下去好像我們都快要可以自行開課了, 乾脆順便寫本書... 
> [name=Kirby W]

> 好像是一個給非資訊背景的 CCSP了 XD
> [name=Ronny W]

> 太強大了
> [name=Jimmy H]

> \+\+ 3du 真的開始擴展了
> [name=isacl]


### 課程時間

- 2014/3/24(一) 15:30 - 18:30   填坑人: Ronny Wang  (願意錄影公開)
- 2014/3/31(一) 15:30 - 18:30    填坑人: Kirby Wu (願意錄影公開)
- 2014/4/7(一) 15:30 - 18:30     填坑人: {   跳進來吧   }

### 參考書目

- [http://www.amazon.com/Scraping-Journalists-Paul-Bradshaw-ebook/dp/B00CQ6L4JW](http://www.amazon.com/Scraping-Journalists-Paul-Bradshaw-ebook/dp/B00CQ6L4JW)
- [http://datajournalismhandbook.org/1.0/en/](http://datajournalismhandbook.org/1.0/en/)

### 可分享內容

- 機器可讀資料(Machine-Readable Data)
    - CSV, JSON, XML, PX, SHP ...
    - 如何去開啟這些檔案
    - 了解五星級開放資料的意義
- 哪邊可以找到 data
    - 政府各 open data 網站
    - github 上 g0v 放出來的檔案
    - 怎麼使用 github
    - 除了開放資料, 還有各種可能用到資訊的表列. 例如:
        - whois, google trend, alexa ranking, stock info...
- 群眾協作實例
    - 由使用者提供, 建立的資料
    - 紀錄使用者活動產生的資料
- 地理資料
    - qgis 處理 shapefile
    - 將 shapefile 與含地名的 CSV 做結合
    - 與 WMS 做疊圖
    - Fusion Table, CartoDB,
- 抓資料
    - 不是 programmer 也可以爬資料的工具
    - 類似資料新聞手冊 p128 的python 例子, 簡易的程式教學? (至少理解一下概念, 也不錯~)
    - 來介紹一下斧頭幫讓學生可以直接對他們硬幹好了
- 資料處理
    - pdf2text, vim shortcut 之類的幫助快速處理資料
    - 常見的資料處理注意事項 (比方說經緯度)
    - google search api
- 資料分析
    - R, Matlab, PCA, LDA, 等統計分析
    - 文章斷句 \- by moedict, 字詞頻率 (?)
- 為什麼會想處理某種資料
> 這應該是新聞系的專長，搞不好可以事前事前問問他們有沒有特別想要做什麼主題的報導
> [name=Jimmy H]

    - Ex: Ronny Wang 在十二月去居酒屋吃到季節是四到六月的飛魚卵，因為好奇而去搜尋知道是南美洲進口的之後，引發了想要去了解關貿進出口資料
    - 日常生活中遇到什麼問題導致想要去爬資料來分析，從別人的想法中知道怎麼找出社會現象奇妙的部份並且去分析他

