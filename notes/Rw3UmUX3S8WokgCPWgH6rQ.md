---
title: "真的假的 LINE bot"
tags: hackpad
---

# 真的假的 LINE bot

> [點此觀看原始內容](https://g0v.hackpad.tw/Zb4bFLB7pnv)


### ＊＊＊上層 Hackfoldr：[http://beta.hackfoldr.org/](http://beta.hackfoldr.org/cofacts)[c](http://beta.hackfoldr.org/cofacts)[ofacts](http://beta.hackfoldr.org/cofacts) / [謠言.大平台.tw](http://謠言.大平台.tw)＊＊＊



## 專案簡介

2016/12/17 提案影片：[https://www.youtube.com/watch?v=IX7Vp3DYOFk&index=11&list=PLdwQWxpS513CcFIWolRQQg-THPjiCnLgV](https://www.youtube.com/watch?v=IX7Vp3DYOFk&index=11&list=PLdwQWxpS513CcFIWolRQQg-THPjiCnLgV)

[2016/12/17 提案投影片](https://docs.google.com/presentation/d/1QTdEZFuaDaR-OA5BRL8svQLGTuAexyuzFtA2SsvuyaM/edit?usp=sharing)

2016/10/15 提案影片： [https://www.youtube.com/watch?v=uFQuyCvm5ng&t=20s](https://www.youtube.com/watch?v=uFQuyCvm5ng&t=20s)

### 緣由＆要解決的問題


Line 上面常常有人轉傳這樣的訊息：

```
「條形碼以＂ 8 ＂開頭的是基因改造食品！」
「醫大已經死17人，友情提醒:最近醫院急診的患者比較多，大都是蘑菇中毒， 今年蘑菇豐收，蘑菇可以和小白菜一起炒,但不能和茄子一起吃，會中毒」

```
雖然用關鍵字 google 一下就可以知道這並非事實，但對於甫接觸網路、鮮少使用搜尋的使用者，「擷取關鍵字、打開 google、放進搜尋框」並不是這麼的容易。

### Proposed Solution


雖然這些使用者**不會 google**，但既然能轉傳不實訊息給他人，那就一定會操作**轉傳**。

於是我們可以做一個 LINE bot 讓使用者加朋友，當他們對 LINE 上的訊息有疑問時，只要轉傳給這個 LINE bot，就可以得到答案，方便他們將結果轉傳回訊息的來源群組。

把「真的假的」加進 LINE 好友：

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_f3e7b9a73cdcbf6a4b136ac8f48a6823)
[http://qr-official.line.me/L/YqaICuIWP8.png](http://qr-official.line.me/L/YqaICuIWP8.png)


### 預定使用者


不熟黯用手機進行 google 搜尋，但會操作 LINE 轉傳的使用者（例如說家中長輩）。
謠言止於智者，這樣的 LINE bot 可以讓長輩輕鬆成為群組內最有智慧的人 (?)

### 預定功能


#### 基礎功能

- [x]  使用者轉傳訊息進來之後，回傳 google 或其他資料庫的相關闢謠文章摘錄與連結
- [ ] 找出「關鍵字」回傳，提供 [template 按鈕](https://devdocs.line.me/en/#template-messages)讓使用者一鍵 google。

#### 進階功能

把 bot 加到群組裡，當 bot 發現有訊息跟資料庫吻合，就主動推送闢謠文章。
> 超沒隱私的啊哈哈
> [name=Johnson L]

> 這應該永遠不會實作吧
> [name=Johnson L]


### 現有類似專案／相關專案


[新聞小幫手](https://newshelper.g0v.tw/)
> 主要是這個專案可以從新聞小幫手撈 data，但是這個專案的資料倒回去新聞小幫手資料庫好像起不了太大作用——畢竟新聞小幫手 extension 以 match shared URL 為主，但 LINE message 沒有 URL（流言訊息怎麼可能會付「來源網址」呢） Orz
> [name=Johnson L]


Google news fact check
[http://www.theverge.com/2016/10/14/13283200/google-news-fact-check-election](http://www.theverge.com/2016/10/14/13283200/google-news-fact-check-election)
> 不確定是人工標記的還是 AI。如果是 AI 的話，說不定 political fact check 跟 rumors check 其實是可以通用的？
> [name=Johnson L]


165反詐騙 App
- 「可疑訊息分析」功能供使用者傳訊息，經人查證之後會回傳「網路謠言」、「與詐騙無關訊息」等答復。
- 已於政府開放資料平台[提議](http://data.gov.tw/node/37640)開放答復資料，並且獲得回應，有[結構化的資料可以獲取](http://data.gov.tw/node/38262)。

Snopes.com
[http://www.snopes.com/](http://www.snopes.com/)


### 授權方式

程式碼：MIT
文案：CC  BY
轉傳訊息資料庫 (尚未實作)：取自網路，並不擁有著作權。
> 請問 [Chun-Kai Wang](https://g0v.hackpad.tw/ep/profile/n98pmxp0btS) 與 [Yu-chi Kuo](https://g0v.hackpad.tw/ep/profile/weYrp743dRU) 方便將當時的 crawler source code open 出來嗎～～
> [name=Johnson L]

> 目前希望可以把各個 cralwer 通通放在一個地方定時跑這樣
> [name=Johnson L]


### 使用資料

- Google custom search engine API (一天限 100 則 query)

#### 新聞小幫手

- ~希望可以與新聞小幫手介接 API，需要跟 Ronny wang 討論。~
- 如果使用者傳送的訊息含有網址，而資料庫裡面沒有闢謠資訊，就會去問新聞小幫手。

#### 科學相關

- [衛福部食藥署食藥闢謠專區](http://www.fda.gov.tw/TC/news.aspx?cid=5049&cchk=55abc933-3e57-48db-afff-a8a4cc1e4ae0) ([https://drive.google.com/file/d/0B3SdyPWxiw4DNFVlTkJLZ1pzRnc/view?usp=sharing](https://drive.google.com/file/d/0B3SdyPWxiw4DNFVlTkJLZ1pzRnc/view?usp=sharing)) \- 已經有 API : [http://data.gov.tw/node/17148](http://data.gov.tw/node/17148)
- [衛福部食藥署食藥好文網](http://fda-article.consumer.fda.gov.tw/rumor_list.aspx?subjectid=1)
- [衛福部國健署保健闢謠專區](http://www.hpa.gov.tw/Bhpnet/Web/HealthCare/HealthCareList.aspx) ([https://drive.google.com/file/d/0B6DgB9B7xvRhRy1rR3l0OEF5cFE/view?usp=sharing](https://drive.google.com/file/d/0B6DgB9B7xvRhRy1rR3l0OEF5cFE/view?usp=sharing))
- [衛福部疾管署闢謠專區](http://www.cdc.gov.tw/qa.aspx?treeid=9a414d734df9bb18&nowtreeid=9a414d734df9bb18) ([https://drive.google.com/file/d/0B6DgB9B7xvRhR1ZId0dMbDdMc0k/view?usp=sharing](https://drive.google.com/file/d/0B6DgB9B7xvRhR1ZId0dMbDdMc0k/view?usp=sharing))
- [衛福部真相說明](http://www.mohw.gov.tw/CHT/Ministry/DM2.aspx?f_list_no=334)
> 資訊含金量略低
> [name=Ying-Kai L]

- [農委會農產品食安專區](http://www.coa.gov.tw/faq/faq_list.php) ([https://drive.google.com/file/d/0B3SdyPWxiw4DLVFfY0V5MUFPZ00/view?usp=sharing](https://drive.google.com/file/d/0B3SdyPWxiw4DLVFfY0V5MUFPZ00/view?usp=sharing))
- [原能會輿情回應](http://www.aec.gov.tw/%E7%84%A6%E9%BB%9E%E5%B0%88%E5%8D%80/%E8%BC%BF%E6%83%85%E5%9B%9E%E6%87%89--218_2033.html) ([https://drive.google.com/file/d/0B6DgB9B7xvRhcldfUGdneGsyVlU/view?usp=sharing](https://drive.google.com/file/d/0B6DgB9B7xvRhcldfUGdneGsyVlU/view?usp=sharing))
> 有部分是PDF，需要列表網址，透過政府資料開放小組請原能會改。
> [name=Ying-Kai L]

> 已將PDF網址列表放入公用google drive
> [name=Chun-Kai W]

- [勞動部勞基法工時問答集](http://www.mol.gov.tw/service/19851/19852/19861/30927/)
- [科技大觀園](https://scitechvista.nat.gov.tw/zh-tw/Home.htm)
- [謠言粉碎機](http://www.guokr.com/group/40/) (中國果殼網)
- [Pansci 謠言tag](http://pansci.asia/?s=%E8%AC%A0%E8%A8%80)
- [Pansci 天天問社團](https://www.facebook.com/groups/pansci.ask/?fref=ts)
> 如果把科學相關流言能整理過來，這裡可以幫忙回應
> [name=Ying-Kai L]

- [公視流言追追追](http://www.pts.org.tw/program/Template1B_Customize_Menu.aspx?PNum=734&CMNum=1452)
> 有很多資料，但不確定要怎麼用
> [name=Ying-Kai L]


#### 非科學

- [內政部警政署詐騙闢謠專區](http://165.gov.tw/list_announcement.aspx) ([https://drive.google.com/file/d/0B3SdyPWxiw4DYWc5UTJORERabDg/view?usp=sharing](https://drive.google.com/file/d/0B3SdyPWxiw4DYWc5UTJORERabDg/view?usp=sharing))
- 網路追追追（已關站，需要爬 web archive，如： [https://web.archive.org/web/20150907025402/http://www.nownews.com/n/2014/10/03/1441001](https://web.archive.org/web/20150907025402/http://www.nownews.com/n/2014/10/03/1441001) ） \-\- 這個可以用寄信的先請求看看
- [MYGOPEN｜這是假消息](http://mygopen.blogspot.tw/)  \-\- 這個可以用寄信的先請求看看
> 會有用錯誤的資訊澄清謠言的狀況，要留意。
> [name=Ying-Kai L]

- [蘭姆酒吐司](http://www.rumtoast.com/)
> 這個是這兩年新成立的闢謠網站
> [name=Yi L]

- [臺北大巨蛋流言終結者*](https://taipeicity.github.io/tpe_dome/mythbusters_01.html)
> 有關政府闢謠的網站~~~
> [name=楊世鈺]

- [臺北市民常見問答*](http://data.taipei/opendata/datalist/datasetMeta?oid=203f1657-bb4a-45a7-b25f-279b63136645)
> 有關政府網站FAQ的開放資料
> [name=楊世鈺]

> 如果跟台北市政府有關的，我這邊都可以幫忙協調取得資料~~~
> [name=楊世鈺]

- [不實消息部落格](http://twbsss.blogspot.tw/)(不確定資料品質) ([https://drive.google.com/file/d/0B3SdyPWxiw4DbW5WVnMwVmd6M0U/view?usp=sharing](https://drive.google.com/file/d/0B3SdyPWxiw4DbW5WVnMwVmd6M0U/view?usp=sharing))
- [婚姻平權闢謠事務所](https://lawfirmagainstrumour.blogspot.tw/)
- [「同運不敢面對的真相」不敢面對的真相](http://whatswrongwithantigay.blogspot.tw/)

DB Schema 請見[開發工作區](http://beta.hackfoldr.org/rumors/https%253A%252F%252Fhackmd.io%252FEwTgrAhgzAphAsBaAbAEwMZUfAHPAZohAOz7CLEQzqr7Fggj4AMQA%253D%253D%253D%253Fview)

#### 謠言來源

1.  名稱：健康心得
    類型：部落格
    網址：[http://bsbshare.tumblr.com/](http://bsbshare.tumblr.com/)
    說明：部分內容是內容農場謠言，可以從裡面抓謠言範本，純蒐集無闢謠
2.


### 專案目前狀態

有了 Prototype 但不堪用。
詳細狀況請見 [https://www.facebook.com/groups/1847232902175197/permalink/1895293667369120/](https://www.facebook.com/groups/1847232902175197/permalink/1895293667369120/)

### 利益揭露

（牽涉到哪些組織團體、有哪些已知的或潛在的金錢或物質或無形利益報酬）

## 徵求協作者


發起人/拋磚人：
- [ ] NeedsWriter: 需要文案幫手（撰寫基本資訊、報導專案etc）
- [ ] NeedsDesigner: 需要介面設計
- [x] NeedsData: 需要資料（擷取、清理）
- [ ] NeedsTech: 需要技術支援（程式、架站 etc)
- [ ] NeedsProcess: 需要幫忙設計作業流程
- [ ] NeedsTalkingToRealPerson: 需要有人幫忙和其他機關聯絡
> HiHi，我這邊是台北市政府資訊局的小鈺，有任何協助我這邊可以提供聯繫喔~~~
> [name=楊世鈺]

> 希望可以跟我們合作，可以協調看看其他機關的資料，因為政府機關也頗多外界謠言需要闢謠orz
> [name=楊世鈺]

> Hello, 我是看看鄉民怎麼說的共同作者之一，如需要串接api的話可以跟我們說喔~~ [https://www.facebook.com/ptt.rocks/?fref=ts](https://www.facebook.com/ptt.rocks/?fref=ts)
> [name=如宏 羅]

## 實作細節（非技術背景可跳填）


### 協作工具

- github repo：[https://github.com/MrOrz/rumors-line-bot](https://github.com/MrOrz/rumors-line-bot)
- hackfoldr 工作資料夾網址：[http://beta.hackfoldr.org/rumors](http://beta.hackfoldr.org/rumors)
- google drive 共用資料夾網址：[https://drive.google.com/drive/u/0/folders/0B1tiWyU4jeioMWNKS2lOZnJaeHM](https://drive.google.com/drive/u/0/folders/0B1tiWyU4jeioMWNKS2lOZnJaeHM)
- 問題回報 FB 群組：[https://www.facebook.com/groups/1847232902175197/](https://www.facebook.com/groups/1847232902175197/)
> 開通權限請至 g0v slack 私訊給 mrorz
> [name=Johnson L]


### 進度與 to-do

#### First iteration : data collection

- [x] product planning（recommended procedure from justin lee / 李易修）
    - [ ] strategy
    - [ ] scope
    - [ ] structure
    - [ ] wireframe
    - [ ] visual
- [ ] web front-end
- [ ] web back-end
- [ ] ui / visual design

Google custom search
[https://cse.google.com/cse/publicurl?cx=006504535273787703401:-lrkd_snuyg](https://cse.google.com/cse/publicurl?cx=006504535273787703401:-lrkd_snuyg)
（使用網頁進行 custom search 不會佔 API quota）


10/15 需要
1.  更準確的搜尋 QQ
    1.  蓋一個自己的資料庫一直查一直查一直查
    2.  Text summarization mechanism
2.  一個老嫗能解的頭像 XD
3.  放在 LINE@ page 的介紹文案

> 「這是真的還是假的？」
> [name=雨蒼 林]


> 有這樣的疑問，就把問題丟給我吧！各種不知道真偽的健康食品、各種可怕的說法，通通歡迎！只要跟我說，我會丟更多資料給你參考喔！
> [name=雨蒼 林]

> 感謝雨蒼
> [name=Johnson L]

> 已經更新囉 :D
> [name=Johnson L]



#### 2nd iteration：完成所有基礎功能、回傳「建議您搜尋 OOO」之類的卡片 conversation、⋯⋯

> 先做 1st iteration 再說吧，我也不知道自己會不會棄坑⋯⋯
> [name=Johnson L]



## 成果展示（規劃文件、雛形/草稿、原型/初稿、正式發佈/完稿）


### 2016/10/15 黑客松後：可上線的 prove-of-concept


#### 今天做了什麼

- Amazon elastic search + PHP wrapper server
    - DB: parsed articles from 闢謠專區 list above
- LINE client
    - Avatars, informations added.
    - Searches from elastic search first
    - Goes to google only when elastic search returns nothing
- A list of rumors & not rumers
- Customer support FB group: [https://www.facebook.com/groups/1847232902175197/](https://www.facebook.com/groups/1847232902175197/)

#### 待解決問題

- 由於沒有做有效的 keyword extraction，目前 Elastic search 與 google search 撈到的東西滿有可能沒有意義的。例如說下面這個訊息傳進去會回傳完全無相關的結果（但如果傳「南海開戰啦」搜到的也一樣無關 Orz 但實際 google 是可以得到正確結果的。）
```
緊   急   通   知
各位朋友:
剛剛收到的緊急通知：
如果收到《南海開戰啦》的圖片，請不要打開，立即刪除，現在已經確認，這是比較極端的菲律賓網絡青年，攻擊中國人電腦和手機，會使電腦喪失一切信息，請發到各自群中，互相通知一下。
已經有人上當了??



```
### 2016/10/15 黑客松前


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_4ffb30a3a4b11811721741f0d73b0599)


### 把「真的假的」加進 LINE 好友

[https://line.me/R/ti/p/%40umn3820l](https://line.me/R/ti/p/%40umn3820l)



## 許願池

暫時利用這段落　許個願
資料庫累積大量的「糾正資訊」之後　也可以變成　www　網頁版　給人 Google 查詢
例如這個「[這是假消息](http://mygopen.blogspot.tw/)（[臉書](https://www.facebook.com/mygopen/)）」以及「科學新聞解剖（[官網](http://scienceanatomy.blogspot.tw/)）（[泛科學的發表](http://pansci.asia/archives/author/scinews)）」
PS.之前有自己想過　正確知識資料庫　不過還沒正式構思就是

- 如果之後用的人變多，可以考慮蒐集「年度10大謠言」？
- 蒐集一陣子後也可以針對最近熱門謠言，主動推送闢謠訊息給大家，有點像165反詐騙的LINE那樣~





