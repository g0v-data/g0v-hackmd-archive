---
title: "lí kám ū thiann-tio̍h in ê giân"
tags: CongressOccupied,hackpad
---

# lí kám ū thiann-tio̍h in ê giân

> [點此觀看原始內容](https://g0v.hackpad.tw/DcgMGDWw8WQ)


Github page:
[https://github.com/a-tsioh/kam-u-thiann-tioh](https://github.com/a-tsioh/kam-u-thiann-tioh)

## 目的

讓人瀏覽在立法院附近（包括PTT，IRC,網路）人人所說的言
Provide a webpage to search and browse public speeches made around the 立法院



## User story

使用者可能無法當時一直聽或看文博，或許想看global picture
加上幾個月後，想記起現在在發生什麼
從一個PO，可以看到上下一個跟類似的（同一個話題）

A typical user may not have followed the whole event or missed part of it. He wants to have a clearer picture of the though shared on the different stages around the legislative yuan.

## 需要什麼

- understand and select what source of data may be relevant and shall be indexed
- 選重要資料的來源，
- Structure the data so that the meta-data can be used (timestamps, location, kind of intervention/speaker)
- Create a semantic space to find similar messages
- Define a list of relevant keyword that should be spotted by the system to relate messages.
    - word cloud or sth like that for what people are saying now
- a timeline for quickly understanding what have been said
- a map for quickly identifying where the message is delivered
- analyze semantic to recognize stand point of specific message
    - is this possible? (can you explain more ?give an example)
> e.g., "KMT的奧步啊" "深藍是超想當中國人的" have similar stand pointa
> [name=Kirby W]

> sounds hard if we don't define the topics on which the standpoints are given beforehand
> [name=A-Tsioh]

> FYI, Gene Hong (黑貘) did a related project: [http://gene.speaking.tw/2014/03/tvbs-tvbs-10-1129.html](http://gene.speaking.tw/2014/03/tvbs-tvbs-10-1129.html)
> [name=Simon P]


## The Data

See [319 Event Data Collection](https://g0v.hackpad.tw/GH2X4Pd7kis)
(minimalist fetch and json from irc included in this project, will use 319 Event Data Collection when available)

Transcripts typically include:
- Timestamp
- Place
- person
- text
- may have an English translation
From the text, we may extract some keywords (like names of politic figures, event, places...)

## dealing with videos

Just a question, if we precise location and time of the beginning of each recording, does it make sense to link it to the text feeds ?


## 用的技術

- Django on the serverside ( I need some python libs)
- elasticsearch for the index
> a-tsioh: just curious, how do you plan to host the server? or do we have a hosted elaticsearch server ready? (cuz one server should be able to serve multiple projects, if the loading is not heavy)
> [name=Simon P]

> got a server in Europe, if the link is not fast enough, we can see how to host it in Taiwan, installing elasticsearch is extremely simple.
> [name=A-Tsioh]

- Livescript on the clientside, we may need some d3js (just because I like it)
- select a UI toolkit (no preference for now

\-\-\-\-
先把FB　的 messages 放在這

\_\_\_\_\_\_\_\_\_

大家好！
我身爲國語有限制的外國人。
在現在發生的事件，資料已經多得難以處理。
很多有意思的話，我注意不到。
text 和 video 的 livestream 事實上我大腦無法處理。（你們會有這個問題嗎？）
> 看非中文的 livestream 就有可能無法處理 XD
> [name=Bropheus H]

找到的資料大部分都是 chronological.
現在有沒有計劃作一個讓人look back at what have been said
just like a search engine over the transcript/videos
或許有而有只是沒發現。
沒有的話，我願意來負責
-
- [**Kirby Wu**](https://www.facebook.com/zbryikt) 我有 logbot 跟 bbs 的 crawler, 文字直播跟鄉民的消息都可以做.. (logbot 其實比較好的是拿 dump database or api endpoint )
- video 則需要有逐字稿或至少自動翻譯.. facebook 可以建立一個專頁, 請大家把相關訊息轉入, 再用程式自動備份...其他資料來源就得 case by case?
> PTT 八卦板上有很多其他資料的 link, 至少廣為流傳的都不會漏掉
> [name=Simon P]


- [**Pierre Magistry**](https://www.facebook.com/pierre.magistry) I was thinking about starting with the live transcription archive (and 文播記錄) that are already timestamped, this may help to align Mandarin and English and maybe even video if possible
[**Pierre Magistry**](https://www.facebook.com/pierre.magistry) one usecase would also be to allow people that were not following to catch up (including foreign press)
- [**Pierre Magistry**](https://www.facebook.com/pierre.magistry) 有些無關的事我得先處理。晚一點會回來。
- 有興趣的人請舉手。計劃會需要比我多瞭解情況和資料的人(算.txt租吧)還有UI-designer 我個人會看一下怎麼用elasticsearch 作　search and classification，也可以pre-process data。
- 如果你在臺大附近，今晚就可以見面，不然網路上也可以
-
- [**Ymow Wu**](https://www.facebook.com/ymow.wu) 我前天做好一個，有點像是包在kirby你說的架構底下，我原本是希望報名上台發表言論的人，能夠用這系統報名，直接接到文字轉播系統，但是目前可能會暫緩，先用新聞瀏覽器的模式擴大傳播效應，自動翻譯我原本要把文字轉播丟到google翻譯再接回來直接放在Androdi app，但是
- @Sunny Chien 說 ：
- google翻譯不可行, 那成品還不夠精準，都要中英日三語直播，我們可以幫忙的譯者會挺你們到底
- 所以我覺得能用logbot解決當然很好，現在可能先以HumanAPI為主，當然如果logbot翻譯水準很高，又另當別論
-

> FYI: [http://share.inside.com.tw/posts/4292](http://share.inside.com.tw/posts/4292)
> [name=Simon P]


