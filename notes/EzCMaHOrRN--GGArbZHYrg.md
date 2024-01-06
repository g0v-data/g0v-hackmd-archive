---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20210519 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：orz,bil, Lucien
-https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :globe_with_meridians: Site

https://github.com/cofacts/rumors-site/releases/tag/release%2F20210516

#### :robot_face: LINE bot

https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20210513

- [Ask user not to trust the message just yet when no reply is available #252](https://github.com/cofacts/rumors-line-bot/pull/252)

### :rocket: Staging

#### :robot_face: rumors-line-bot

- Batch request https://github.com/cofacts/rumors-line-bot/pull/255

> ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5b9efd6146ab892910cf0c29dbae228d.png)
>
> Deploy 後，倒回 redis 內 timestamp 至 5/14
> ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_566d8e4881509aedc8726f6e55dfba02.png)


## 流量 ＆ error 紀錄

與上週對比。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_244908516048bfe8d3d7fbdfbd01109f.png)

### Chatbot error rate baseline

2021/5/15 - 2021/5/19 217 errors
mostly "Request timeout"
2 "Session protocol negotiation failure: https://rumors-line-bot.herokuapp.com/callback"
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ce85aacd3ce913b3fa84722c6ff5f299.png)

### Linode server load baseline

Peak: 5/13 300%
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e29b19da60da666cb3a355d575e669a4.png)

Sampled date: 2021/5/19 21:12
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8225281fa05c15b0280b68f7e16424de.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f78e6ff6930e45f89470c0bb3039b8c1.png)


記憶體的差別不大，重新開網站會掉下來，但是沒有空修。
10GB
整體LINE bot 在 memory consumption在 1GB以內，

### Heroku LINE bot load baseline
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_07d0135d6f87bac88868a9554bcd9e7f.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_da26c0bbad97b969ebb5b806e26d6b92.png)

合併的PR
LIFF很麻煩，build image 要把api url 放進去
這樣LIFF才是正確的環境


## PDIS
> https://g0v.hackmd.io/6ZwH7NANRqG6s-CCIy9IYw?view#Visit-PDIS
> 

問題與 solution：

1. 我們希望透過科技來做媒體識讀教育以及查核社群，因此我們期待生態系能有更多「社群經營」、「查核內容產生」的角色產生，但此預想的競爭沒有發生，取而代之的是單方面的資源取用，也就是整個生態系只有 Cofacts 輸入回應但沒有而沒有得到正向的反饋。
2. 因為沒有良性的生態系誕生，我們嘗試使用贊助資源來激勵更多人參與，像是物質獎勵優秀的查核組織與個人（例如：台灣事實查核中心），以及外包部分平台功能開發⋯⋯等等，實際上有看到其獎勵成效，但後續我們找不到一個適當切入點去跟企業與大眾募集資源，我們近期有積極與企業 CSR 洽談並同時開啟小額募捐的方式，但收效甚微，還找不到一個能引起大家願意資助專案永續的敘事方法。

---

- 生態系單向取用：
    - 問題：使用者不夠
        - 查詢＆回應的人不夠多
        - 因為流量被導走
    - 嘗試解法
        - 直接要求導流
            - 後來 downstream bot 又改回去
            - 下游 bot 拒絕
        - 用 CC BY-SA 要求
            - LINE bot 使用者消長：導流時 v.s. 沒有導流時
            - CC BY & Article LIFF 是試著把 Cofacts 貢獻的功能，嵌入到取用 Cofacts 的產品 [name=mrorz]
            - 後續效應：下游 bot 停止取用
        - 宣傳？
        - (Article LIFF 開發設計 - 還沒做完，而且沒解決比較嚴重的編輯短缺問題，而是解決 feedback 不夠問題，所以先跳過)
    - 問題：編輯不夠
        - 小聚
        - 零時小學校
        - （renumeration）
    - 其他想法？
- 激勵內容產生者
    - 例如志工時數？
    - 政策相關的澄清？
- 大眾對群眾協作的想像
    - 期待「全志工」的「高尚」？
    - ex: 76 行者 / Wikipedia?

## syndavant貼圖
> visual identification system?

VIS中的中英文字體是什麼字型的呢？
希望能在角色設計上盡可能的選用適合VIS的字體。

Logo --> 類似金萱那提但是是志超自己拉的字體
僅有橫劃豎劃有差異，筆畫末端沒有裝飾性「襯線」
金萱那提也另外要授權

> ㄎㄎ使用金萱，要提醒是否有與 justfont 洽購授權

上色後的貼圖，顏色的應用都是延續Cofacts新的VIS的。
有一個「LINE Creator Market 截圖」資料夾是在LINE裡面使用的示意圖，也供作參考。

> 讚讚