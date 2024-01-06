---
title: "g0v pre-hackath3n"
tags: event,hackpad
---

# g0v pre-hackath3n

> [點此觀看原始內容](https://g0v.hackpad.tw/Y9xV1sIIuTt)


6/8 的客廳工廠黑客松之前，先來做點什麼吧！

主題：讓黑客松效果更好

希望偏重在協作工具、共用資料等等。不過也歡迎實作特定專案。

可能的專案：（請自由增加）

**以下複製至** [http://hack.g0v.tw/](http://hack.g0v.tw/meta)[meta](http://hack.g0v.tw/meta)

- [hackfoldr](https://github.com/hackfoldr/hackfoldr) \- the code behind hack.g0v.tw
    - 整合 @c9s 的 [wireroom](https://github.com/c9s/WireRoom)?
    - issues: [https://github.com/hackfoldr/hackfoldr/issues](https://github.com/hackfoldr/hackfoldr/issues)

- people.g0v.tw - 簡易 people registry (取代原來鄉民列表 spreadsheet), 讓人自己加 tag (如：環保、醫療、前端、後端), 也許每個 tag 可以成為一個 disq.us 討論區?
    - 開發: [http://github.com/g0v/hack.g0v.tw](http://github.com/g0v/hack.g0v.tw) branch: hub
        - (gem install sass compass)
        - npm i
        - ./node_modules/.bin/brunch w -s
    - people 的 tag 可以包含幾種不同的類型
        1.  熟悉哪些 domain knowledge（環保、醫療、社福、經濟、食品安全、都市規劃）
        2.  擁有哪些實做技術（介面、視覺、web 前端、web 後端、手機 app、資料分析）
        3.  熟悉哪些政府或民間單位（公督盟、司改會、苦勞網、泛科學、醫勞盟、醫改會）
> 以上感覺不大會彼此重複，所以應該不用特別分類，就直接標上就好？
> [name=Chia-liang K]

> 的確耶XD
> [name=ET B]

        4.  參與過哪些 g0v 專案
> 人跟人之間、人跟專案之間、專案跟專案之間需要使用統一的 tag 以方便媒合
> [name=ET B]

    - 除了 tag 跟 email、sns 以外，可以有個欄位附上個人 github 帳號... XD
> about.me 好像有 api, 如果 user 已經有用也許可以直接 pull 所有資料過來？不過基本上就是 github/twitter/email 為必要吧，其他就... 都好 :p
> [name=Chia-liang K]


- 定義 g0v project meta data & display
        - project 和 component 好像應該分開來
        - 例如 立院專案 有自己的說明，supporting components 又各有不同產出。又如萌典，有 data source、各類 app 等。
    - sample: [https://github.com/g0v/hack.g0v.tw/blob/master/g0v.json](https://github.com/g0v/hack.g0v.tw/blob/master/g0v.json)
    1.  專案名稱name, name.zh
    2.  簡短說明 description, description.zh
    3.  狀態: status: idea, alpha, beta
    4.  預定產出的格式是什麼（json  / csv / api / website / mobileapp / browserext） product
> 知道產出格式是什麼，就可以知道需要哪些人幫忙，比方說產出 json 檔的專案就不需要 ui designer 的加入了，這樣 designers 進來的話可以直接找 web / app 類型的專案參與
> [name=ET B]

    5.  東西可以給誰用（programmer / 一般民眾）audience:
    6.  要怎麼用（去哪裡取用資料 / 去哪裡下載安裝什麼東西）
    7.  專案牽涉到的專業領域 tags（同 people XD）
> 不會寫程式的朋友，可以根據自己擅長的領域挑選想加入的專案
> [name=ET B]

    8.  專案採用的語言/工具 tags（d3.js, the noun project, iconmoon, sass/compass...）
> 攻城屍還沒有特定偏好的主題的話，可以根據實做技術來挑選可參與的專案
> [name=ET B]

> 發現工具好像不用下 tags = =" 不然沒完沒了 orz
> [name=ET B]

    9.  專案牽涉到的政府或民間單位 tags
> 有特別聯繫管道的朋友，可以根據自己熟悉的人脈挑選想參與的專案
> [name=ET B]

> c,e,d 為 keywords
> [name=Chia-liang K]

> 理解，就跟 people 的 tags 一樣不用分類直接標就好對嗎 -\> right, 然後就可以和 people match 了 :p -\> hooray XD
> [name=Chia-liang K]

> 如果這麼多種 tag 全標, 分類可能比較好看/好search? either tag 有 namespace, 或是另外弄 tag category. 不過可能等 tag 太多時再考慮
> [name=Kuang-che W]

> 的確，今天上完阿修的課以後發覺某些有特別用途的tags也許需要分類，不過要等g0v首頁的策略定完再來深究 @@"
> [name=ET B]

    10.  專案分工與認領清單
> _可以提供一組常見的分工方式讓大家改，很像是之前的那些 neadxxxx tags，想認領的人自己寫上去。_
> [name=ET B]

        - parser
        - web back-end
        - web front-end
        - ui design
        - visual design
        - writer
    11.  聯絡窗口
    12.  專案的 github 網址
> 是否要建議每個專案開一個 group 設定 members，還是在自己帳號也行？（用自己的可能會比較亂）
> [name=ET B]

> 要是看到有人認領了某工作但很久沒 commit 了其他人可以考慮接手XD
> [name=ET B]


**以上複製至** [http://hack.g0v.tw/meta](http://hack.g0v.tw/meta)


- twhgis - 任一時點行政區 render

- liquid feedback single sign on with github id
    - setup area members according to github groups

- 立院相關
    - clkao 的 tts raw data
    - etblue 的 design
> 我已經完全忘記這是什麼了... @@" 
> [name=ET B]


- 鄉民關心你 \- 事件追蹤系統
    - [https://github.com/g0v/kuansim](https://github.com/g0v/kuansim)

- ~idea pool with tags~
> ~同 people，ideas 也可以加 tag，讓相關的 idea 更容易找到彼此 XD~
> [name=ET B]

> merged
> [name=ET B]


