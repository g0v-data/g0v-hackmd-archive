---
title: "斧頭幫入會挑戰 (Crawler War Game) 發想"
tags: hackpad
---

# 斧頭幫入會挑戰 (Crawler War Game) 發想

> [點此觀看原始內容](https://g0v.hackpad.tw/UG3PJ9SLf7A)


為了能訓練更多的斧頭幫成員能夠循序漸近砍下更有價值的木材，來規劃一個 Crawler War Game 遊戲，網站上提供一些常見的 HTML 或者搜尋功能的網站，挑戰方法就是你自行寫一個程式將網站爬下來，並且把他轉換成題目要求的 CSV 或 JSON 格式，只要內容吻合就可以挑戰下一關，後面的難度將會越來越高。

也歡迎學生把自己寫的程式傳到 GitHub 跟大家分享，無論是使用什麼程式語言，讓更多人能夠交流如何寫 Crawler。鼓勵學生寫 wiki or blog 發表心得

### 注意事項

- 要先讓學生知道不要打太兇，不要把 server 打掛 XD
- 關卡應該盡量以我們做的假網站為主，不要叫學生去打真網站

### 工作分配

- 主站設計，主站只要用 iframe 顯示各關卡 landing page，並讓人上傳處理完的 CSV, JSON 驗證答案是否正確，如果正確就讓使用者進到下一關，不正確就告訴使用者資料太多太少格式不對或是無法判斷不正確原因
    - 答案驗證部份，CSV 應該要可以接受每一行順序不一致，但是每一行應該要跟標準答案一樣
    - JSON 應該也要可以接受 object key 順序可以變換？
    - 應該要提供可以討論分享這關心得的方式，但不要讓人把答案丟上來
- 各關實作，各關可以放在不同的平台網域，只要提供各關 landing page 網址以及各關答案給主站可以驗證就夠了

### 關卡技術挑戰

- 標準 HTML 網站
- gov.tw 等級超混亂 HTML 網站
- ajax infinite-scroll 資料 HTML 網站
- 會認 User-Agent 的網站
- 會擋 Referer 的網站
- 會擋頻率太快的網站
- 需要輸入一次 captcha 的網站 (輸入一次之後該 session 之後都不用輸入)
- 需要從列表頁去抓單一頁面資訊的網站
- 只有條件搜尋界面沒有完整列表界面
    - 偏偏又沒有 unique id
- jsp 寫的, server 或 cookie 會存 view state 的網站
- ajax 回來是 js code, 或是 html 裡含 js code
- IE only 的網站 (不過這好像是出題比較難 XD)
- Flash 的網站 (也是出題比較難 XD)
- 看似 structure data, 但 1% 的資料會多欄位或少欄位
- 有搜尋功能，但是每次搜尋有筆數上限必需想辦法找出所有集合並且將結果切細的搜法
    - Ex: 搜尋條件有「鄉鎮市區」，去 data.gov.tw 找到台灣鄉鎮市區列表帶進去就可以一次一次搜尋搜完全部資料
- 複雜的資料問題
    - 正常的 big5-1984, 要求輸出 utf8
    - 不是 big5-1984 譬如有 PUA, 要求輸出 utf8
    - input 是已經從 big5 轉成 utf8, 但轉壞了 (?)
    - html 沒有好好 escape
    - 不同的 csv variant
    - big5 json

範例網站：
- 實價登錄
    - 有需要輸入一次的 captcha, 只有搜尋界面沒有 unique id，一秒鐘不能 query 超過三次
- 立委名單
    - 純粹 parsing HTML
- 商業司公司資料
    - 會認 referer

### 關卡規劃

1.  最簡單的標準 <table><tr><td> 只有一頁的網站
2.  上一關加上 pager
3.  第二關改成 pager 還要用 POST 的網站
4.  第二關加上會認 referer
5.  第二關加上會認 user-agent
6.  第二關加上會擋一秒鐘只能 GET 一次的網站
7.  第二關加上超不穩定，9.2% 機率會 500 的網站
8.  第二關的 pager 改成 infinite scroll
9.  大量 ajax 的網站
10.  table 中包一堆 table ，沒有 id 可以用的網站 (gov.tw 常見)
11.  HTML 格式一堆 syntax error 以及 id 重覆使用的 nested table
12.  JSP 產生的網站，會需要認 \_VIEW\_STATE 內容
13.  資料被放在 js code 中的網站
14.  ~第一關改成同一 ip 一天限抓 5 次, 要求抓 100 次~
15.  要求座標轉換, 也許是度分秒轉度, 還有 twd67,wgs84 轉換之類. 小於 x 公尺就算通過. 主要目的是讓大家知道有不止一種座標.
    1.  進階的還包括離島. 不過這我也還不知道怎麼做比較好 :P

### 討論區

> 中間有跳轉得算那種 ? 例如: [http://enterprise.lib.nccu.edu.tw/govpeople/](http://enterprise.lib.nccu.edu.tw/govpeople/)
> [name=Yuan C]

> Ronny: 這種用只有搜尋界面的網站當作挑戰重點好了
> [name=Ronny W]

> 除了關卡以外,中間規劃一些gov.tw的網站當作成就感?
> [name=Yuan C]

> Ronny: 直接叫大家攻入政府會不會有法律問題 XD 不過有些關卡我是想可以直接照抄政府 HTML 格式來用換成假資料，這樣同一個程式斧頭幫的就可以直接拿來攻政府了，不過不是我們要他做的 XD
> [name=Ronny W]

> 10關 還碰過nested table格式有錯, 可以變成第11關? XD
> [name=Yuan C]

> Ronny: 第 14 關假如限 IP 會不會增加學生挑戰的門檻太高 XD 要學生去找 PROXY 或是租機器找網咖
> [name=Ronny W]

> NAT底下的人們表示哭了 ...
> [name=Yuan C]

> 推薦 picloud (有 crawler 專用 instance)每月有免費 20 小時. 不過這解法就太受限了
> [name=Kuang-che W]

> 我想主要以gov.tw會有的類型作為基礎關卡, 14關如果有的話當然也要算, 若是沒有就當bonus的關卡
> [name=Yuan C]

> 要增加 parse 那部份的難度嗎? 還是先專注在抓的部份?
> [name=Kuang-che W]

> Ronny: parsing 應該也要做，因為希望學生可以上傳 csv or json ，可以線上即時驗證他的答案是否正確，這樣整個遊戲也可以自動化
> [name=Ronny W]

> ScraperWiki?
> [name=Whiski T]

> 要不要像 [http://www.codewars.com/](http://www.codewars.com/) 那樣，在學生破了一關之後，列出這關別人怎麼破這關的程式碼，然後讓破關過後的大家 vote up 覺得精采的 solution；如果覺得自己寫得比列表上面列出的程式都還要好，也有個「上傳我的程式碼」讓大家可以觀摩自己的程式。
> [name=Johnson L]



