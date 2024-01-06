---
tags: cofacts, meeting note
---

20190220 會議記錄
=====
 orz/文武/bil
 
> 前次會議記錄：https://g0v.hackmd.io/s/HyzBe31r4
> 

## Cofacts

See Cofacts TODO: https://g0v.hackmd.io/s/BJ2XBWAX4#Cofacts-TODO


### 使用量

上次發現新年期間使用量很少，2/14 前後有個高峰回到新年前的狀況。

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_45bac130142450ae1f6c9a714a1e594b)

燒燙傷假消息、柑桔園幫摘、蘑菇假消息回來了。

或許是因為假新聞清潔劑活動日？

bil
2/15 是 BBC 報導美玉姨呢。

文武
說不定是新年期間大家都在關注罷工
所以比較少轉


### Level tooltip bug
https://github.com/cofacts/rumors-site/issues/152

文武：
tooltips 有看一下，但不知道怎麼改

orz:
感覺改用這個就好
https://kazzkiq.github.io/balloon.css/

未來如果有複雜 tooltip 再改成
https://github.com/FezVrasta/react-popper

:::info
改用 [balloon.css](https://kazzkiq.github.io/balloon.css/)
:::

### 清潔劑提案

https://www.facebook.com/groups/cofacts/permalink/2311788659052950/?comment_id=2326041180961031&comment_tracking=%7B%22tn%22%3A%22R0%22%7D

#### 長輩需要ＯＸ清楚標記
    
bil
覺得留著滿好的，像是在分段，表情符號

orz
可是我們已經有類似 :raising_hand: 的符號做分段了

文武
長輩需要 OX 感覺需要更多研究
一樣是之前的疑問
他們不看那麼長的文章只看OX
那為什麼會看很長的不實資訊

既然會看長文章
那應該也可以看回應分辨

而且他也可以直接拉下去看也可以
也只是防君子不防小人

orz
其實我們目前放在最下面，使用者不用拉就可以看到

bil
另外編輯會看到 OX，為什麼編輯看到的跟使用者看到的不依樣

orz
因為編輯要表達主觀意見，ＯＸ比較方便
但使用者不一定要被影響，拿掉 OX 影響比較小

orz
那先把 15 字限制的 UX 做好好了

#### 傳文章介面清楚標示 15 字限制
https://github.com/cofacts/rumors-line-bot/issues/127

orz
這個可以先做做，這樣比較能讓人知道如何教老人

## 我愛家我解惑
> 網站架構見：https://g0v.hackmd.io/s/BJ2XBWAX4#%E7%B6%B2%E7%AB%99%E6%9E%B6%E6%A7%8B
>

https://answerfamily.org

### What's new
- article & reply page UI
- article submission UI

可以開始補資料了！

### What's missing
- bugs
    - https://github.com/answerfamily/answerfamily-api/issues/3
    - Cannot submit reply via UI
- DB backup
- analytics
- Landing page 要放什麼

## 小聚檢討

小聚討論紀錄：https://hackmd.io/X2nhTNROQ3unB5tzDvGrdg

bil:
有人願意分享滿感恩的
以後可以變成邀請個別編輯來用 10~15min 分享過去的想法
這件事情可以做

例如說芮菁

orz
我們是不是忘記給演講費了

bil
是

（討論中）

orz
流程方面有什麼要改進的嗎

bil
還算準時
但讓假新聞清潔劑等比較久不太好意思
買食物的時間有進步

orz:
開始闢謠之後就去買

bil
只要有準時開始就能準時結束
應該要尊重準時到的人
因此都是 2pm 準時開始，晚來記得貼名字
早到不貼可以隨意，晚來 miss 自我介紹的有責任讓別人認得

orz
大腸花只排 10min 有點少
但應該是這次比較熱烈，之前也沒有很長

bil
之前上官跟英凱有給
那就比照

:::info
大松要給書懷講師費 500
:::

### 下一次小聚

2019/4/13？20?27?

:::info
下次可以討論是否要邀請事實查核中心來分享
:::

bil:
還有龜珍 or 嘉琳

## Communications

### 美國商會
比鄰 until 4pm

### 2019 媒體素養培力計畫（教育部）
bil
感覺教育部就是要來叫大家做志工
不過沒辦法先承諾我們可以給志工什麼回饋（獎狀或志工時數什麼的）

:::info
bil 本週寫寫計畫
:::

### 資訊媒體素養講座巡迴

時間已經記在 calendar

### LINE & 願景工程
比鄰、GGM 會去週四

週五有比鄰，另外還有誰會去？

orz:
針對「合作上攜手針對假訊息可以做些什麼事情」
希望 LINE 可以起頭做
https://crosscheck.firstdraftnews.org/france-en/

我們可以幫忙 connect first draft

orz 會在晚上回信給 LINE 說明這個想法

### SPH Open Innovation Platform

orz
看起來像是創業比賽
又要寫計畫

bil
但又要排進度

orz
另一個是這種平台可以提供媒合的機會

但這個領域我們已經認識 first draft, google news lab, LINE 所以好像還好

### GEC
3/5 9am

比鄰會去
added to calendar

### clkao April 16 program

回信解釋 cofacts 沒有 AI components
