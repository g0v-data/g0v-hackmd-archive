---
tags: disinfo, disinfothon
---
# disinf0thon 第零次不實訊息松

- Time: 2020/1/4 10:30-17:30
- Place: Taipei City
- 報名由此去 → https://forms.gle/kqffyonCYWTdeUgk8

## 11:00 自我介紹
- chihao
    - 0archive coordinator
    - 希望能寫到 code
- wenyi
    - 0archive developer
    - fb crawler
- bruce
    - 0archive developer
    - fb crawler
- Richard
    - NLP
- Julia
    - 不會寫程式
    - Open Up Summit
    - 還不知道要做什麼
- Peace
    - 研究假消息對於公共議題討論的危害與防治
- ronny
    - 基礎建設
    - elasticsearch

## 目前的公開資料

https://g0v.hackmd.io/yOIdBw0yRd61dYza8mgS1w

https://tinyurl.com/0archive-dev
最新資料：
[publication.jsonl.gz](http://ronnywang-public.s3.amazonaws.com/opendata/disinfo/publication.jsonl.gz)
[producer.jsonl.gz](http://ronnywang-public.s3.amazonaws.com/opendata/disinfo/producer.jsonl.gz)

提供網站 https://airtable.com/shr2kjYg6RH0wgQEh
## 一些問題

哪些網站我們有興趣？
分析每個網站的行為模式，藉由模式定義內容農場？
po 文時間
文章是轉貼的比例
轉貼的內容和原文的 distance（？）
改標？

手動調查⋯
e.g. 用怒吼的文章當開頭，找連結
下特定關鍵字、搜尋
那些沒有報導的事？

metadata e.g. GA ID

自動斷詞

發現簡化字、簡繁轉換錯誤

elasticsearch

用文章裡的 hyperlink 串

word2vec: e.g.韓國瑜離哪一些詞比較近？

[新聞的「製作品質」](https://g0v-tw.slack.com/archives/CNYM62P6X/p1576320855001700):

gugod:
> 我在寫爬蟲 ( NewsExtractor / people-in-news ) 時一面也在想這個問題。但只想得一些隨意的評量標準。
> 比方說：
> 1. 要有「標題」「日期時間」「記者名」「內文」這四欄位。
> 2. 內文 與 標題 所闡述的主題應相符 （否則就是「名不符實」，偏向 disinfomation 那一側的寫作法） 
> 3. 內文所闡述事件的時間不應與目前時間相距太遠。（舊聞）
> 4.  內文與標題不應出現「網友」兩字粗略觀察起來，大致上用了「網友」兩字的新聞內文都是帶一點虛假成分。或是「網友表示〇〇〇」為文中主要論點的支持論點，但去搜尋又找不到網友是在哪裡表示〇〇〇。變成是一種「虛的參考來源」。

tkirby:
> 《大眾傳播理論與實務》

pm5:
> 限定在新聞的話，可能寫作格式？前 3 個段落的長度、句數、全文裡驚嘆號或某些特殊符號的數量
> 某些用詞像是 https://oops.udn.com/oops/story/6698/2616762
> 「引語」和「過渡語」的數量與分佈？ https://www.prlass.com/3737/%e7%b6%b2%e8%b7%af%e6%96%b0%e8%81%9e%e7%a8%bf%e5%af%ab%e4%bd%9c/
> 

gugod:
> https://medium.com/@tunaBR/%E5%88%A4%E5%AE%9A%E6%96%B0%E8%81%9E%E5%85%A7%E5%AE%B9%E5%93%81%E8%B3%AA%E7%9A%84%E5%8F%A6%E9%A1%9E%E6%96%B9%E6%B3%95-%E7%B6%B2%E9%A0%81%E7%B5%90%E6%A7%8B%E5%88%86%E6%9E%90-bfcf4e990df8
> 
> 我的想法跟這篇文章裡提到的「新聞品質評分計畫」跟好像很類似

hkazami:
> - 分析一則新聞裡的用詞的情緒，情緒分數（或特定情緒的分數）低的可能是比較沒有主觀意見的新聞？
> - [島民衛星](https://islander.ailabs.tw/2020-01-04/11/about/)做的事情：
    遺漏分析：把同一主題的新聞都拿來自動生成一個摘要，再回頭比對每篇新聞，得到每篇新聞的摘要資訊含量。這個值越高代表這篇新聞提到的資訊越完整。
    風格分析：偏自由還是偏中時
> - [中研院輿情分析系統](https://ckip.iis.sinica.edu.tw/project/opinion)：
    看起來是只爬中時自由聯合三家的網路新聞（蘋果在表內但新聞數是0）

yitzu:
> [封鎖內容農場Chrome插件](https://chrome.google.com/webstore/detail/content-farm-blocker/opjaibbmmpldcncnbbglondckfnokfpm)
> https://github.com/benlau/ihatecontentfarms
> 1. 在打開內容農場時進行攔截
> 2. 用戶可以選擇繼續，然後在10分鐘內不再對同一網址進行攔截
> 3. 用戶自定黑名單及白名單


Wikidata?

案例：關西機場

用 Machine Learning ：
* 風格分析：激進 vs. 理性
    * 不限於真假消息，偏頗或帶風向式的消息也適用
* 直接做 fake news classifier
    * End-to-end?
  
用 More Like This 找現在 17 萬篇文章內是否有相同或相似的文章 by Ronny
* 條件
    1. 字數需大於 1000 bytes
    2. More Like This 分數大於 2.0
    3. 需要來自不同來源
* [成果](https://gist.githubusercontent.com/ronnywang/7ae62eb2691e570bf7a56328ca77c4fb/raw/43561878a38140511725f4c5d4603938330f9a7e/text-result.txt)
* 下一步目標
    * 統一轉成正體中文，這樣更能找到有做簡轉正體輸出的關聯

## 公眾宣傳

## 14:00 自我介紹
- Johnson / MrOrz
    - Cofacts http://beta.hackfoldr.org/cofacts
- tumi
    - 去年研究成果 https://drive.google.com/file/d/1D82zDBo64PWSgvW1QrrYzEvXukBddWfk/view
    - 在某私立科大教行銷管理理、公共關係
    - 希望幫忙釐清新聞vs.不實資訊定義
- steven
    - 只會一點點 python C++

## 17:00 成果分享
- Peace
- 資料庫描述
內容農場/粉絲頁/社群媒體/媒體為核心的結構，目的性的消息，非自然轉傳，大部分會是良又不齊的訊息，很大部分比例會是的不實訊息，有固定的系統式的集團化傳播途徑
>>>解決問題：可揭露有特定目的，參雜不實訊息，又不容易辨識的媒體守門人

- 內容農場是：
「是指以取得網路流量為主要目標 ，圖謀網路廣告等商業利益的網站或網路公司。內容農場用各種合法、非法之手段大量、快速的生產品質不穩定的網路文章， 會針對熱門搜尋關鍵字用人工或機器製造大量網站內容的手法欺騙搜尋引擎 ，使他們製造的網頁能夠優先出現在搜尋結果的前段而提高點閱率、以及滿足客戶搜尋引擎最佳化需求。」
>>>內容農場不關心真假，只關心流量
>>>憑據的重要。不是直接指控，而是收集基礎資料。
>>>含有憤怒情緒，破壞信任，不利社會討論。
>>>促進公共議題討論意義，避免社會不信任。

可分析
* 在這個脈絡裡被轉傳的途徑--策略
* 指標與條件，歸納與分類
* 策略型態，傳播速度、規模、預算、關聯性、頻率
* 信任的傳播模式的特質 ＶＳ 假消息的特質
* 內容農場的架構圖
* 一個完整的事件傳播
* 檢視結構裡的小工具，被多少轉傳，轉傳幾次
* 弱連結與強連結，角色定義

傳播方式
* 國際交流
* 教育素材
* 媒體分流
* 假消息論壇
* 資料庫的整併
* 定時專案內容分析

合作對象
* 多粉對話
* 選前大補帖
* 第三部門
* 媒體
* 大學或學術研究單位

假消息市場觀察
* 跟現在的假消息制度哪裡有缺
* 選舉完，事實查核，政策波段
* 開源工作的制度，如何讓更多人參與

目的
* 分享軌跡
* 被動接受到的訊息
* 不定義假消息/假新聞
* 不做事實查核
 
對象描述
* 開放新的市場，新的不相信的人是大多數
* 政治立場很明確
* 世代溝通
* 新的價值觀與新的脈絡
* 開源產業促進產業創新

後續
* 閱讀報告：資料怎麼被分析，有哪些結構與目的
* 如果讓更多人可以了解假消息的操作
* 世代溝通可以怎麼被建立
* 如何分眾討論，討論的核心問題是什麼：每個人都要有媒體素養

Johnson:
- Pull requests: https://github.com/cofacts/rumors-site/pull/210
- Demo: https://cofacts.hacktabl.org/articles?q=&replyRequestCount=1&filter=solved

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ac74947c710e2a16b669f27ddd4cd224)


chihao
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_4fce39717d231eeb1136597776229eda)


pm5
- fix(ed?) undying news scraper processes on middle2
- made article parser streamline
    - 自己會倒地死亡
- parse published_at from a little more metadata

wenyi
- fix comment author
- retrieve post content directly from html (without clicking '更多')
- discuss new architecture with Bruce
- write post parser that takes into post url
- (still) fixing getting reaction info

Ronny
用 More Like This 找現在 17 萬篇文章內是否有相同或相似的文章
* 條件
    1. 字數需大於 1000 bytes
    2. More Like This 分數大於 2.0
    3. 需要來自不同來源
* [成果](https://gist.githubusercontent.com/ronnywang/7ae62eb2691e570bf7a56328ca77c4fb/raw/43561878a38140511725f4c5d4603938330f9a7e/text-result.txt)
    * 使用 2.0 這個數字
* 下一步目標
    * 統一轉成正體中文，這樣更能找到有做簡轉正體輸出的關聯

bruce
* fb crawler 改善中
* 早上抓了 3 pages 3k+ posts
    * 抓 reaction、留言、留言作者、回覆留言的留言
* 建議：用分身 + 易付卡

Richard
- EDA - exploratory data analysis

tumi
- 我只是 user
- 新增追蹤對象
- 許願：希望可以一次輸入多筆

julia
- 新增追蹤對象
- 跨領域分身之術
- g0v 社群初體驗

yitzu
- 新增追蹤對象
