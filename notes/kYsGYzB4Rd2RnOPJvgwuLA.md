---
tags: cofacts, meeting note
---
20200101 會議紀錄
=====
JC, bil, mrorz, 文武,ggm

> 上次開會紀錄：https://g0v.hackmd.io/@mrorz/B1XErJZyL
> 

## Rumors-site 升級 next9
1. [x] Article list --> PR to dev
2. [x] Article page （見 API 更新）
3. [x] Reply list
4. [x] reply page
5. [x] docker build
6. [x] landing page
7. [x] 上 staging
8. [x] 上 production --> 新台幣升級
9. [x] google analytics (w/ gtag)
10. [ ] All i18n (including levels...)
11. [ ] RSS feed

### Stackimpact native extension
Done, deployed to production

### Rollbar bugs
- Set is not defined [Rollbar](https://rollbar.com/mrorz/rumors-site/items/61/) / [Github](https://github.com/cofacts/rumors-site/issues/209)
- User ID not set via query string [Rollvar](https://rollbar.com/mrorz/rumors-site/items/62/) / [Github](https://github.com/cofacts/rumors-site/issues/209)
- Share aborted [Rollbar1](https://rollbar.com/mrorz/rumors-site/items/19/) , [Rollbar2](https://rollbar.com/mrorz/rumors-site/items/60/) / [Github](https://github.com/cofacts/rumors-site/issues/205)
- Cannot read property 'name' of null [Rollbar](https://rollbar.com/mrorz/rumors-site/items/10) / [Github](https://github.com/cofacts/rumors-site/issues/196)

### TODOs
- 從其他頁面點進 `/replies` 會壞掉 - https://github.com/cofacts/rumors-site/issues/193
- ~~字太小~~

## Chatbot Token 過期

> 文武：自動更新
> 

ggm
那個 script 跑在新機器的 cron job 上
但那個機器我們關了

orz
有備份嗎

ggm
記得是個 curl


### JC分享
讓使用者一眼看出來
用強的視覺做
module要換一些視覺

最後想做一個，前面介紹
第一個問題難度高，drop off就會高
先用簡單的問題拉他進來
先用簡單的問題「有沒有謠言想要叫我們幫你查」
- 先分眾
如果沒有就再給他一個假訊息讓他試試看
他有一個way out去學習怎麼做
這樣可以結合兩種設計的好處
好處是一進來，第一題答得出來。

- 選定了方向，開發的人是開issue
沒辦法用LINE＠

- 先壓一個授權
JC會上傳檔案到slack

FINAL(互動多的版本)
感謝感謝


原則上on board會獨立做，所以可以先release
UX 設計師要做初步研究，關於bot的東西會先展開
做初步的使用者研究，會幫助做出來之後編輯小聚的feedback
用這個做初步的concept看可以優化後來的物件
然後陸陸續續一包一包做
其實我不是很在意是不是一次做出來然後全部刻進去
有些可以設計完就放在旁邊

## 外賓接待

### BBC interview
bil
1/8，電視
沒有想要寫共筆，
要有電視畫面

orz
有給他共筆嗎

bil
沒有，想現場訪問

### NDI Victoria

https://g0v-slack-archive.g0v.ronny.tw/index/channel/C2PPMRQGP/2019-12#ts-1577180787.021800

> Hi everyone! My name is Victoria and I am working on a short documentary-like video on civic tech/g0v/and democracy. My organization (NDI) has been a friend of g0v and Code for All for many years (I have met at few of you at various times in Taipei, including a few years ago at the g0v summit/Code for All Summit :)) and I am really excited for this opportunity. You can read more about the film and our hopeful(!) schedule for filming here: <https://g0v.hackmd.io/HaIQVQpLQ8i-ixUDyXtBCQ> Please find the link to my interview questions below which will be used for the video regarding g0v and your work (I will be interviewing three people from the community - someone representing 0archive, someone representing cofacts, and someone from g0v who is also in government), I look forward to your input! <https://g0v.hackmd.io/@kVqWpZq8R12VCa4i1N68UA/SJiTyGyJ8/edit> Please edit and reach out directly if your have any questions!
> 

Bil
一樣想要拍 1/8
但已經建議其他時間
對方還沒回應

### 1/13至1/17

作為參與者參與座談會
邀請與會

> bil 聯絡


### 1月7日（二）下午5時 1月10日（五）下午4時

bil:
1月7日（二）可能要上午，或是換另一個時段。
1月10日（五）下午4時 拜會 是可以的。

> bil 聯絡

## 二月小聚(第18次編輯小聚)

maybe 2/8
NPO hub - (問 jothon了)
主題：元宵

平平安安慶元宵，看著滿月，年節也終於到尾聲了。
2020，Cofacts 第一次的編輯小聚，就在02月08日星期六下午。
這次換了一個新的場地，NPO HUB！！

