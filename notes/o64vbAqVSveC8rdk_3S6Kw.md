---
title: "政商關係圖"
tags: hackpad
---

# 政商關係圖

> [點此觀看原始內容](https://g0v.hackpad.tw/hxJBK9v7frt)


### 網站：

[http://twcom.cryptogil.net/](http://twcom.cryptogil.net/)

### 計畫目標

提供台灣公司、社(財)團法人關係整合查詢界面，供各界查詢法人、自然人網絡連結。

### 短期目標

- open source
- 建立 Resfult API
- 整合台灣公司關係圖現有介面

### 中期目標

- 整合社團、財團法人董監事資料
- 美化網站、增加查詢功能
    - 查公司（加箭頭、區分核心與非核心企業）
    - 查人名
    - 查社團法人、財團法人董監事（如：XX基金會）
    - 查地址

### 目前進度

#### Open source:

    已放上 GitHub, 完成基本查詢範例  [https://github.com/WeiChengLiou/twcom](https://github.com/WeiChengLiou/twcom)
    資料庫 dump 放在 github 的  data 資料夾
#### 建立 Rest  API:

    已有 linode 主機, 資料庫也準備妥當. 預計用 Flask 作 Rest API. - Gilbert
#### 整合現有台灣公司關係圖界面:

    因皆使用 D3.js 的 Force  Layout, 只要略改 tag 名稱就可以接過去原界面 - Gilbert
> 我記得原本是用別人的library? 要視覺化的話重刻比較好？
> [name=sherry l]

> 我在想，要不要直接規劃ronny wang網站的介面？目前ronny wang會嘗試吧Gilbert的資料放到他的網站，已經在重新弄php了
> [name=雨蒼 林]

> [http://company.g0v.ronny.tw/](http://company.g0v.ronny.tw/)
> [name=雨蒼 林]


> 他應該不會重新弄 php 吧, 他給我看了他的 json 格式, 我只要把我的 json  格式修改一下就能接過去了
> [name=Liou G]

> 他的網站是死網頁, 只要改資料來源就好, 但我們可以把他作得更漂亮一點, 所以才要美化.
> [name=Liou G]

> 也不是漂亮的問題啦XD 只是因為那個lib不能改連結or節點顏色之類的 這樣比較難表示更多資訊
> [name=sherry l]

> 那我先隨便架個框 先研究一下D3?
> [name=sherry l]

> 可以拿我的 template 去改，那是我第一個 D3 作品 (掩面)
> [name=Liou G]


#### 網站美化:  (阿天)

    Github
    [https://github.com/solring/twcom_front](https://github.com/solring/twcom_front)
    Website on Heroku
    [http://twcom-analysis.herokuapp.com](http://twcom-analysis.herokuapp.com)
1.  基本功能
- [x] 統一編號 or 公司名稱查詢
- [x] 董監事人名查詢
- [x] Company network
- [x] Boss network
2.  視覺化項目
- [x] Link加箭頭 （還有bug XD
- [x] betweenness centrality
- [x] 董監事資訊放大顯示
- [ ] Link種類 - 子公司or共同董事
- [x] Boss network & Company network疊合
> 當然還有各種bug 歡迎回報XD
> [name=sherry l]

> 軟 Q 的網絡圖
> [name=che l]

3.  其他 Issues
- [ ] 目前無法用partial name搜尋董監事人名？(ex: 用“雪紅”搜不到王雪紅)
> API bug......剛修好了
> [name=Liou G]


#### 整合社團法人資料:

    已知Jimmy有爬過資料 =\> [https://github.com/g0v/foundationtw/blob/master/output/all_detail.csv](https://github.com/g0v/foundationtw/blob/master/output/all_detail.csv)
    [http://foundations.olc.tw/](http://foundations.olc.tw/) \- repo: [https://github.com/kiang/foundations](https://github.com/kiang/foundations) (cakephp)

    整理與整合社團法人資料的專案放在 [https://github.com/WeiChengLiou/twfund](https://github.com/WeiChengLiou/twfund)
    目前已初步處理一些錯別字的問題，並另外整理出一份各社團法人目前董監事名單。
    但有些資料缺失值還沒處理、法院公告也沒有機構改名的相關資訊（未提供原名與新名對照），
    所以有些改過名稱的社團法人可能會出現兩次以上（例如仁濟院），資料不算乾淨。
    另外正在改寫部份程式以整合公司董監事資料，董監事網路結構的儲存方式也會作調整，以配合未來新增不同來源資料需求。


### 建議

( 歡迎推坑, 不保證完成 XD)

    有幾個比較基本方向上的議題有機會想跟大家聊聊看 :
- 若是已知了政商關係網路，那我們是否可以從整體網路計算得到像是政商關係最複雜的公司排名、最腳踏N條船的人物排名、避債避稅兼洗錢用空頭公司排名等等之類的視覺化結果，讓使用者的目光比較能優先聚焦在一些顯著的政商關係結構上。
> 記得有一次Gilbert提到網路中觀察到有數間公司接連100%轉投資的詭異現象，後來問在金融公司上班的朋友，是說可能還要再看看公司設立的地址在哪裡，如果是在境外的話通常就是為了避稅，不過還是得看實際案例的狀況決定(像是轉投資了幾層之類的)。
> [name=Keith N]

> 這邊比較像是一個排行榜的概念，可以先從個人與公司的 degree 這種簡單的排行榜開始做做看。
> [name=Liou G]

- 目前的查詢好像有一個比較麻煩的地方，像是如果我不曉得公司的完整名稱的話，查詢出來部分符合的結果數量有時候相當多，但一直要到挑選了一個點進去了才會發現裡面的資訊量有多少... (比如搜尋"欣欣", 結果會出來一堆, 但很多都是小公司, 關聯資訊蘊含量很少)，如果可以依據節點與連結數量先將結果排序或顯示資訊含量的話或許會比較方便。
> 這邊我可以先作，好了再通知各位。
> [name=Liou G]

> Oh yeah~
> [name=Keith N]

> 排行榜寫到資料庫，也做成 API 了，待做出視覺化的部份
> [name=Liou G]

- 網路結構上的資訊探勘可用的SNA模型有好幾種，可以從數種中心性(centrality)及子網路群集探勘(clique)的現成方法中先行計算看看，再去解釋其中的實質意義是甚麼 (或是反過來)
> 這個部份先記錄一下構想, 歡迎討論~ 我會自行填坑... XD
> [name=Keith N]




## 圍標檢測


### 計劃目標


利用公司關係圖，建立圍標檢測系統：

#### 輸入公司關係


- 輸入：
    1.  txt file content
- 輸出：
    2.  圍標嫌疑標案清單
    3.  公司關係圖id
    4.  檔案的md5 checksum

#### 使用者查詢1\. 列出圍標嫌疑標案清單

- 輸入：
    1.  公司關係圖id
- 輸出：
    2.  圍標嫌疑標案清單

#### 使用者查詢2\. 查詢圍標可能性

- 輸入：
    1.  公司關係圖id
    2.  統編清單
- 輸出：
    3.  圍標嫌疑指數

