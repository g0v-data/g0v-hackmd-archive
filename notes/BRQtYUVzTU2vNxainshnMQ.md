---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20210505 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：bil, mrorz, lucien
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :robot_face: rumors-line-bot

[2021/05/05 Release](https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20210505)
- #248 Cofacts GraphQL
- #250 Article LIFF Proof of concept
- #251 Japanese translation

### :rocket: Staging

#### :globe_with_meridians: Site

- Tico integration https://github.com/cofacts/rumors-site/pull/431
- Japanese version https://github.com/cofacts/rumors-site/pull/432
    - ja.cofacts.tw

## 防詐顯名

趨勢 4/29 停止接取 Cofacts --> verified.

## [LIFF article page](https://g0v.hackmd.io/0RX4MsjRRJmBqJSKVilWMA#article-amp-reply-LIFF)

3. [ ] Article LIFF 設計 https://www.figma.com/file/DvmAQjMJCncuPORWKnljM1/?node-id=3004%3A224
4. [ ] 實作 article & reply
5. [ ] 實作 feedback form
6. [ ] 實作 reply request list & form
7. [ ] 實作 related article

## Syndavant 貼圖
會用較粗的線繪製

## Japanese version Cofacts

好像其實是想做 AI（QA 系統與情緒分析），日本版 Cofacts 只是順便？

https://g0v-slack-archive.g0v.ronny.tw/index/channel/C2PPMRQGP/2021-05#ts-1619953182.0885

> Thanks! I’ll check the article out really interested to take a look into this research.
> Wondering if there are models that could be used to detect strongly emotional messages that would be typically associated with fake information
> [name=John Cronin-McCartney]
 
> As far as I know Cofacts never tried to detect emotion in rumor text.
> Institute for Information Industry do develop such feature in Rumor Catcher ( https://tfc-taiwan.org.tw/articles/4477 ). However, they are not a fan of open-source and want to hold their findings proprietary.
> Another direction may be
Squash https://www.niemanlab.org/2020/07/a-lesson-in-automated-journalism-bring-back-the-humans/ and Full Fact https://fullfact.org/blog/2020/jul/afc-global/ 
> [name=mrorz]

## 使用者變多

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fd36525e5075c584f018fb9f8cb3b409.jpeg)

- 因為有疫情所以人就變多了 [name=bil]
- 可以在使用者查不到的時候，跟使用者說先不要相信 [name=bil]
    - 有點像過去「真訊息」「不要相信」二分法的時候
- 可以加「先保持懷疑」的 hint [name=mrorz]
- 指出哪些情緒用語可能會影響你的判斷（但就要另外做）[name=mrorz] 
- 有國外的 fact checking chatbot (Aos fatos?) 會在找不到的時候，教使用者檢查來源之類的

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d9284068f8654129e7ba85bd9df204f9.png)
- 希望可以告訴那 3,149 個沒回應的、或 8,405 個沒找到訊息的人說，先不要相信 [name=bil]
- 但沒回應的人會不知道，要想想怎麼放在現有的 prompt 才不會太長 [name=mrorz]
- 「找不到關於⋯⋯的訊息，建議您先不要輕信它。」[name=mrorz]
- 「建議您先不要相信它。如果要請闢謠編輯查證，請點下面的按鈕，提供您找到的資訊。」[name=bil]
    - 確實是可以要求使用者給更多資訊，因為在顯示這個句子的時候，就已經先送出了無 reason 的 reply request 了。[name=mrorz]

## NFT

- 可能可以放在 lootex [name=lucien]
    - https://lootex.io/zh-TW/stores/casimir
    - gas fee 較低
    - 上去了就拿不下來，所以要好好設計 [name=lucien]
        - 做爛了就自己買下來ㄚ [name=mrorz]
- 用途
    - 競價（稀有 or 較有共鳴）
    - 捐款者小禮物
    - 捐款管道


TFC - https://opensea.io/assets/0x495f947276749ce646f68ac8c248420045cb7b5e/69251980811113132305123917530239240041013450196849453076546217202331278114817

- Etherum, Gas fee 較高

## Oslo Freedom forum 

Booth - 桌子 & 大背板
- 7/18 (日) Grant Hyatt 君悅
- 印摺頁 & 1-page english flyer
