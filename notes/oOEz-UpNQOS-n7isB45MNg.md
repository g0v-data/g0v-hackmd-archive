---
tags: cofacts, meeting note
---

20190925 會議記錄
=====
orz,lucien, bil,文武
> 上次開會紀錄：https://g0v.hackmd.io/2j_zXsDTTr-koQ6fzSHf_g?view
> 

## 10/6 (日) 小聚

- [x] 主題：國慶
    - slogan：
        - 小心！匪謠就在你身邊
        - 回應謠言人人有責
        - chatbot 有愛時，便給出回應。回應擴散，阻止謠言。埋首案前的編輯使 chatbot 產生回應，卻並不要求什麼報酬。
        - 
- [x] 時間：10/6 14:00-17:00 
- [x] KKTIX
- [ ] 攜帶貼紙 - bil
- [x] 場地：時間已經跟青平台訂下
    - [x] 茶水
    - [x] 麥克風+插座
    - [x] 投影機
    - [x] 延長線
    - [ ] 食物 (2:10 訂，之後來的沒有)
    - [x] 垃圾
    - [ ] Talk -> slido
    - [x] wifi 不夠力 -> 已經買了 [Netgear Nighthawk M1](https://shopee.tw/%E6%BE%B3%E6%B4%B2%E7%89%88-Netgear-M1-4CA-4G-%E8%A1%8C%E5%8B%95Wifi-%E7%B6%B2%E5%8D%A1%E8%B7%AF%E7%94%B1%E5%99%A8-790s-810s-e5788-%E8%8F%AF%E7%82%BA-b525-i.5320736.314685253) 會帶
- [ ] 誰會來呢？ bil, mrorz, 文武, 
- [ ] 開場使用材料更新：https://docs.google.com/presentation/d/1QCAPtwkxreQ4EUtIWsOgR4c8h4tkRs22Qvv7jBFNrfI/edit#slide=id.g1ffc87ef17_0_23
- [ ] 加slido
    - 連結寫白板上
- [ ] 改[instant文案](https://github.com/cofacts/rumors-site/blob/master/pages/instant.js#L9-L87) - https://github.com/cofacts/rumors-site/issues/167

推播文案 - 9/28, 29

## Dev Items

### 分析新版 reply requests

近期 reply requests 列表：
https://docs.google.com/spreadsheets/d/1vCHmDz3Vc3kVfp2hqhyvV69yWTAdv5msgmdH2rxEtG8/edit#gid=702378399

- 上線時間：2019/9/18
- Reply request count / New article count:
  - 9/14: 15 / 15
  - 9/15: 26 / 23
  - 9/16: 23 / 21
  - 9/17: 21 / 20
  - ---上線---
  - 9/19: 35 / 26
  - 9/20: 56 / 34
  - 9/21: 45 / 25

orz
文章列表兩人以上回報會變多：精準呈現哪些訊息會被轉傳
理由的 quality 其實差不多

bil
覺得工作量增加
就算不點開「只有一人回報」的也是工作量增加

但使用者增加本來就會這樣

orz
但至少我們可以確定說處理的都是真的有在轉傳的

有需要做「只有一人回報但理由寫很好」的嗎

bil
不用，現在就很好

文武
那 new article count 呢

（補上 new article count）

orz
看起來上線前 new reply request 絕大多數都是由 new article 貢獻
在上線之後 new reply request 才顯著大於 new article
看起來是有成功加速回報 1 -> 2 的部分

另外，開放後新文章量也確實有上升，看起來理由字數拿掉確實對新送文章進來也有差

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_816cfb16179aad9f959ed3e163493679)

:::success
No TODO for now
:::

### Cofacts Logo 英文字體

bil:
漂亮

lucien:
同意志超說的，
如果用 futura 的話中文也會一起改

現在的版本覺得可以

:::success
以志超 20190819 的提案結案
:::

### Rumors-site 升級 next9

https://github.com/cofacts/rumors-site/compare/next9

#### Progress

1. [x] Article list --> PR to dev
2. [ ] Article page （見 API 更新）
3. [ ] Reply list
4. [ ] reply page


### 主機轉移

ES 對外

:::success
下一次來做
:::

## 臨時動議

From FB group 的志工與期待

**[likecoin](https://like.co/)**

https://matters.news/@az/%E7%B5%A6%E7%A4%BE%E5%8D%80%E7%9A%84%E4%B8%80%E5%B0%81%E4%BF%A1-matters-%E8%88%87-like-coin%E5%AE%A3%E4%BD%88%E5%90%88%E4%BD%9C-zdpuB3JTzZ8Ch2J9NbPsJ79NKuAJB3ehie3KWf78rimdCefo4

mrorz
「LINE 使用者覺得有用」要怎麼對應到這裡？
likecoin 要做內容有價，不過 liker 的 incentive 是什麼
跟媒體小農差在哪裡

lucien
小農現今有自己的生態圈
token 就是大家自己一個聯盟

bil
心理學來說，token 花起來比較沒有錢的感覺

lucien
對付錢的人來說確實比較麻煩
LINE 端整合也不容易
一種做法是我們註冊 100 liker 帳號，有「覺得有用」的時候就是由我們的 liker 帳號幫他 like

覺得可以跟 likecoin 官方談

服務整合他們的東西，討論技術細節
likecoin 他們的創作可能是大文章，但我們的創作是很短的闢謠
這兩個的 base 不知道是不是一樣

orz
主要是「回應是否有用」

確實如果是 likecoin 而不是直接對應到錢，會讓人覺得有得到東西但又不會直接覺得很廉價

lucien 
恩這相當於他的 like 數

對 likecoin 來說我們幫他們免費增加用戶 + 平台

orz
網站的部分可以幫他們開錢包
line bot 這端怎麼整合確實可以再談

:::success
Lucien 在有空的時候可以跟 likecoin 聊聊
- 具體來說如何把「回應是否有用」轉化為 liker like
:::
