---
title: "實作反映精準民意的網站"
tags: hackpad
---

# 實作反映精準民意的網站

> [點此觀看原始內容](https://g0v.hackpad.tw/08w0u5xtWUg)


在 g0v slack [#general](https://g0v.hackpad.tw/ep/search/?q=%23general&via=08w0u5xtWUg) 的閒聊。

今天看到 g0v news 上寫到這個網站 [https://parkgeunhack.com](https://parkgeunhack.com) 「一個讓民眾對自己選區議員精準施壓或是鼓勵的網站」，有人知道精準施壓具體來說是怎樣的方法嗎？

## 整理

目前還沒任何整理資訊

## 討論

剛看到這個時，想說如果在台灣做一個需要身份證認證的網站來表達精確民意的會踩到什麼雷...

yurenju \[11:03 AM\]
今天看到 g0v news 上寫到這個網站 [https://parkgeunhack.com](https://parkgeunhack.com) 「一個讓民眾對自己選區議員精準施壓或是鼓勵的網站」，有人知道精準施壓具體來說是怎樣的方法嗎？
剛看到這個時，想說如果在台灣做一個需要身份證認證的網站來表達精確民意的會踩到什麼雷...
1) 個資問題

vic \[11:07 AM\]
個資應該沒問題，主要是用來驗証

chihao \[11:07 AM\]
0) 不夠多人用，代表性不夠 :stuck\_out\_tongue:

vic \[11:08 AM\]
「寫下你的選區」「你的身份証字號」。身份証字號用於認証不種複，可用md5的方式，不重複即可。

yurenju \[11:08 AM\]
我每次打給吳思瑤辦公室總覺得他都覺得我是少數人，對他的選舉一點都產生不了影響 Orz...

vic \[11:08 AM\]
然後給這些官看，他在他的選區有多少人對他的立場感到不滿
當然，只能參考，因為也可能有人故意，產生很多合法但假的身份証字號

yurenju \[11:09 AM\]
有身分證字號產生器誒

vic \[11:09 AM\]
所以只能用來參考
至少，有個人會用「身份証產生器」這麼無聊又麻煩的行為來表達他的不滿，那他應該真的很不滿
也可能記ip，多久不能重複
真的年底太忙，不然我想盡一點心力
這個如果作起來，還能讓人舉發議題

yurenju \[11:11 AM\]
我也很忙，但是我想說先思考思考 XDDD
如果可以釐清些盲點也不錯
所以 2) 會有假帳號 <=== 這可能要看認證的方式

chihao \[11:12 AM\]
@vic 不對喔，他也可能有其他的動機「要讓目標議員覺得有很多人不滿」

vic \[11:13 AM\]
我的意思是，我們把這種行為的難度拉高一點，那他真的要「很有心」
如果他有「那份心」，其實他很可能會在fb或其它管道直接「拉人」比較快
因為這是「被動的」，也就是說，要先有「議員或官表達了什麼政策或立場」，才有「我不爽他的xxx」

yurenju \[11:18 AM\]
先開個 hackpad 記錄一下… 把訊息先貼過去，之後有空再整理 [https://g0v.hackpad.com/08w0u5xtWUg](https://g0v.hackpad.com/08w0u5xtWUg)
我的疑問也一樣，因為有同溫層的關係，所以 fb 的消息或風向可能不準

vic \[11:19 AM\]
被小追殺中，我沒表達清楚，晚點再上來，不好意思

yurenju \[11:19 AM\]
話說，不管是勞工或同志議題都一樣，如果做了這個網站，上面的與論可能會跟我們想的完全不一樣…

aelcenganda \[11:21 AM\]
那也是我們必須接受的不是嗎

yurenju \[11:22 AM\]
沒錯 \\o/

aelcenganda \[11:23 AM\]
接受降低公民參與門檻但其他人跟我們想的不同XD 所以需要更多說服跟倡議
其實同婚議題一直有做這種點名議員/立委的網站名單
唔，我覺得如果現在有紅衫軍，同樣的網站也會跑的動，非常集中的怒氣

chihao \[11:25 AM\]
沃草在去年大選之前做過的婚姻平權立委表態整理，伴侶盟也有協助 `[http://wevote.tw/issues/marriage-equality/legislators](http://wevote.tw/issues/marriage-equality/legislators)`

yurenju \[11:27 AM\]
@chihao 這個網站表達的是立委支持什麼，我的想法是「選民支持什麼」，然後立委可以看自己區域的選民到底支持什麼

chihao \[12:10 PM\]
@yurenju 我知道我知道，我是想回應 @aelcenganda 說 `點名議員立委的網站` XD

yurenju \[12:10 PM\]
喔喔 XDDD

yurenju \[1:21 PM\]
那議題要如何設定呢？感覺應該要和 join 平台一樣，任何人都可以發起議題，不過要超過某個比例的人表達立場才會顯示在「熱門議題」裡面？
設定議題好像也很重要，不同問法會有不同結果

yutin \[1:54 PM\]
@yurenju @chihao 動機會不會跟台灣最近 都透過各種方式在網路上因為同志婚姻 表態連署  一樣？

yurenju \[1:58 PM\]
@yutin: 但對立委不痛不癢啊，因為他不知道在他選區的人怎麼想

yutin \[1:59 PM\]
之前同志婚姻 柯建銘某篇PO文被灌爆甚至於出現罷免的聲音 對於立委有沒有壓力 可能只有她本人才知道哩 >///<

yurenju \[1:59 PM\]
也是

yutin \[2:01 PM\]
也許有一天立法委員在質詢時 要求NCC or 某單位 質疑某連署網站是否違法時 大概就知道有明確的壓力了

yurenju \[2:02 PM\]
基本上我想做的是更直接的民意反應跟更直接的民主。

viktor \[2:10 PM\]
光是上網站表達意見我覺得就很同溫層了

yurenju \[2:18 PM\]
是這樣說沒錯，但怎麼表達意見其實可以有些巧思，比如說可以用 LINE chatbot 搜集意見，這樣應該也可以觸及許多長輩。
本體是 web API 但如何表現可以是多種介面。 (edited)

superbil \[2:42 PM\]
送長輩圖的次數來表達意見？

vic \[5:41 PM\]
如果被動式是議員發生了行為而民眾表達看法，主動式是議員尚未有行為而民眾表達希望；我個人認為是被動式的比較可以聚焦，主動式很可能造成焦點發散。畢竟主動式的我們不一定需要一定由哪個黨或議員提出，任何的都可以。不表態也是態度的一種，我可以針對議員的「不表達」表達不滿。甚至我認為「表態力道不足」，也可以是不滿的點。

yurenju \[6:30 PM\]
對議題要如何設定有什麼看法嗎？是大家都可以上去發表呢，或者是只有少數人可以設定議題，或者是只能針對議案投票結果發表看法？

pofeng \[7:16 PM\]
@yurenju 你覺得用 ivoting 的架構可以嗎 ? ivoting 之後很有可能會 open source [http://doit.gov.taipei/ct.asp?xItem=100357468&ctNode=5582&mp=121001](http://doit.gov.taipei/ct.asp?xItem=100357468&ctNode=5582&mp=121001)
( 確認身分 / 投票 / 給代議士壓力 )
不過非官方網站 具名投票我覺得有困難, 這似乎不是單純的技術問題

yiji \[12:02 AM\]
@yurenju 已有相同概念的網站。不過議題已經設死，而且是用Facebook帳號認證XD [https://lightup.pridewatch.tw/](https://lightup.pridewatch.tw/)
用 line 認證可能更準，因為line 是綁手機號碼。


yurenju \[10:23 AM\]
@pofeng 要看他們發起每一次投票成本是不是很低，我這幾天想想是覺得用 LINE chatbot 比較好，因為他們已經做過電話號碼認證，我只要請他們填居住的行政區即可，感覺比較容易。
@yiji 我也覺得 LINE 可能是個好方法
如果有作弊行為比例也不會太高
另外一個好處是可以觸及的長輩比例會比較高

pofeng \[10:27 AM\]
@yurenju  ivoting 如果可以用健保卡或自然人憑證應該還好,  LINE chatbot 似乎不錯, 同意長輩觸及率會高 XDDD , 但是好像要 $ , @singing 好像哪邊好像有窗口可以討論一下免費的 quota (不確定) (edited)

singing \[10:30 AM\]
@pofeng @yurenju 我只知道今年中 LINE chatbot 在公益上主要是災防，有需要我可以幫忙問問看就是了...

yurenju \[10:31 AM\]
(我們在討論這個主題 [https://g0v.hackpad.com/08w0u5xtWUg](https://g0v.hackpad.com/08w0u5xtWUg)
好，不過可能晚點，因為他免費的帳號也可以先試一下

mrorz \[2:44 PM\]
[https://business.line.me/zh-hant/services/bot](https://business.line.me/zh-hant/services/bot)
免費也有無上限好友人數了
只是不能主動推送，只能回訊息

yurenju \[11:28 AM\]
LINE 一定要用電話認證嗎？還是現在可以單純用 email 認證？在想用 LINE 的多個帳號或是假帳號的成本到底高不高...


pofeng \[11:58 AM\]
@t0mst0ne LINE 雙認證後, 盜用狀況有好一點 ...

pofeng \[12:05 PM\]
@yurenju 我記得以前沒電話也可以申請 LINE , 但比較麻煩,  然後官方鼓勵綁定電話號碼 (雙認證) 但是還是可以移除綁定, 現況可能請常用的人補充一下

g0vtelegrambot (irc) BOT \[12:27 PM\]
<asinki> 我一年多前辦，是要電話號碼耶！

new messages
pofeng \[12:29 PM\]
2016-08-05 \[教學\]註冊LINE帳號不用手機電話號碼，Facebook登入+信箱直接搞定！
[https://sofree.cc/line-register-facebook-email/](https://sofree.cc/line-register-facebook-email/) (edited)

g0vtelegrambot (irc) BOT \[5:35 PM\]
<gugod> 好像應該請 eff 評估一下 line
<gugod> [https://www.eff.org/node/82654](https://www.eff.org/node/82654) 加到此表

g0vtelegrambot (irc) BOT \[7:15 PM\]
<JediLin> 電話號碼/Facebook 必須擇一
<JediLin> 所以對我這種沒有 Facebook 帳號的人來說，選擇剩一種：找人頭去辦 7-11 電話預付卡，用來開通 Line

