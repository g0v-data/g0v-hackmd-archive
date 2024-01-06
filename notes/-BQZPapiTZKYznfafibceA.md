---
title: "數位保存"
tags: hackpad
---

# 數位保存

> [點此觀看原始內容](https://g0v.hackpad.tw/zg2QPaKbWgP)


### 緣起


現在產生數位資料內容的方式，又快又便宜，但就史料的記錄來講，數位的東西好像放上網路雲端，隨時想看都看的到，這邊歷史事件的保存，著重在忠實的呈現事件完整性。雖然很多的網路連結頁面，但放眼100年、200年，不見得還會存在。更何況數位資料亦很容易"被消失"，而掩蓋事實，當代事件也因為沒有距離感，每個人的看法都不同，因此我們希望以不帶偏見的重現並保存當代事件發生的一些資訊。

博物館領域及人文社會學者，有一個共同的問題就是他們的資訊技術人力（能力）很缺，
所以我們來這邊提案，邀請一些志士，一同來腦力激盪，如何有效的協助當代數化資料的典藏。

### 方法

- 確認要每個歷史事件 archive 的範圍，進行
    - 包含背後的系統、網路上的評論、新聞媒體
    - 若為OpenSource 的系統，則保存系統環境背景，安裝重現並封印於當時的狀態
    - 若不是OpenSource 的系統，則用 archive  的方式靜態頁面保留，希望看起來是一模一樣，甚至內部網址連結也一樣不變動
> [ally wang](https://g0v.hackpad.tw/ep/profile/x3jNpoNFAHt) 有考慮過使用 [https://web.archive.org/](https://web.archive.org/) ，他們本來就會做 archive 保存的動作
> [name=小蟹 李]

> 但其實我們有查過有一些限制，當然有一些簡單的頁面可以透過web archive 去處理，但也是要餵給他們，他們才會處理，因此想寫一些機器人去爬資料後，餵給web archive 去備存，若存的不錯就很好，若很重要又存的不好，我們就會想要自已存一份。而且很多當代歷史事件，評論很容易被消失，當然台灣比較沒有，但對岸就滿多被消失的記錄。若能即時archive  也是很有趣的一個保存
> [name=ally w]

> btw 類似 archive.org 的 wayback machine 的還有 [http://archive.is/](http://archive.is/)
> [name=Johnson L]

> 他不會爬資料，有人給了他連結他才會去爬，不過他抓下來 archive 的東西似乎比 wayback machine 完整，印象中連 FB 貼文（公開）也能處理。
> [name=Johnson L]


> 對於 web archiving，目前全世界已經有這一些 initiatives 在進行:
> [name=Johnson L]

> [https://en.wikipedia.org/wiki/List\_of\_Web\_archiving\_initiatives](https://en.wikipedia.org/wiki/List_of_Web_archiving_initiatives)
> [name=Johnson L]

> 其中包含國家圖書館的「台灣網站典藏系統」唷[http://webarchive.ncl.edu.tw/nclwa98Front/](http://webarchive.ncl.edu.tw/nclwa98Front/)
> [name=Johnson L]


> 最後，這裡有一些現成的 archiving tool: [https://en.wikipedia.org/wiki/Web\_archiving#Aspects\_of\_web\_curation](https://en.wikipedia.org/wiki/Web_archiving#Aspects_of_web_curation)
> [name=Johnson L]

> 但感覺好像都很難架，說不定 caasi 自己寫比較快（然後順便讓這世界上多誕生一種 [archive format standard](https://en.wikipedia.org/wiki/Web_ARChive)... XD)
> [name=Johnson L]

> 不不，暫時沒力，只能提供做過的或記得的（縮）
> [name=caasi H]


### 需要確認

- 網路共筆下 隱私權的處理
    - 當代歷史共筆下隱私很難去處理，互信的部份也很重要，先從公開資料的爬網處理，較不具問題，也許可以加密處理或是一段時間封存後再公開。(?)
- 數位內容的授權



### 以 318 為案例做數位保存 範圍

先做的深再做的廣
####  318 hackpad

- [319 Event Data Collection](https://g0vbeta.hackpad.tw/ep/pad/static/GH2X4Pd7kis)
- 本來文播的資料在 [https://hackpad.com/324--FRzDUBto4Vj](https://hackpad.com/324--FRzDUBto4Vj) ，但看來沒備份到，可以問問 ronnywang 他有沒有存到 FRzDUBto4Vj 這個 id 的文件
- 文播頁面也被別的服務備份了，請見 [https://archive.is/gfpmM](https://archive.is/gfpmM)
- 這是卡西四年前備份的文播內容 [https://gist.github.com/caasi/9856058](https://gist.github.com/caasi/9856058)
- hackpad.g0v.link 也備份了 [http://hackpad.g0v.link/sgyfCRGiBZC.html](http://hackpad.g0v.link/sgyfCRGiBZC.html)
#### 318 hackfoldr

congressoccupied 那頁當初為了防惡意修改，特別被處理成靜態的，請直接下載連結列表再分析： [https://ethercalc.org/_/congressoccupied/csv](https://ethercalc.org/_/congressoccupied/csv) 。或點[這裡看好讀版](https://gist.github.com/caasi/470484c423c99408b295deae6d4a6b8c)。
> 感謝 caasi 
> [name=ally w]


### 有興趣的人 ( 留下slack ID，後續設slack 群組）

 ericx1023
 tokimasa
 spidyjames
 mimo
 macpaul
 Michael_LI　　//我有參加318直播影片備份後移轉到中研院，[變成了一個資料呈現網站](http://public.318.io/)，318文播組資料我備份到「[這邊](https://hackmd.io/BwQwDAjATFCcwFoDsAzeCAs0IOAVj1gQGMBTNJAIylKjADYog===#)」（請先不要改文字，頂多下載就好）
 caasi


### 可參考的資訊

- [Why Some Video Games Are In Danger of Disappearing Forever](http://kotaku.com/why-some-video-games-are-in-danger-of-disappearing-fore-1789609791) 此文介紹了典藏日本遊戲八、九零年代舊遊戲可能遇到的問題。這可能發生在十年、二十年後的我們身上。
- 影片聲音文字圖片整理系統（VT Systen）（草案）
[（提案說明）](https://grants.g0v.tw/projects/587388cb8798fb001e7324de)[https://grants.g0v.tw/projects/587388cb8798fb001e7324de](https://grants.g0v.tw/projects/587388cb8798fb001e7324de)
　　（[簡報](https://docs.google.com/presentation/d/1HXEqmsnby_9oeDx3qOIVha_MY-Xc4xROud3eFy1S4RA/edit#slide=id.p5) ）
[文字稿的交叉查詢　by 記錄片／網路世界的幻想　Lo and Behold, Reveries of the Connected World](https://www.youtube.com/watch?v=ifXS_evUwaI)



daybreak.newbloommang.net








