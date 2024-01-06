---
tags: cofacts, meeting note
GA: UA-98468513-3
---


# 20201230 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：bil, mrorz, hsiao, nonumpa, lucien, kalin
:::


## 開放授權變更

### Attribution 討論

> BY 署名的部分會彰顯在所有用到 Cofacts 資料的地方（參考網站、chatbot）
> 囊括 Cofacts 社群的下面的幾個概念，越多越好：
> - 是大家都可以參與的，不是封閉的
> - 是一群人，不是特定幾人
> - 參與者包含回報訊息的人、替回應評分的人、以及闢謠編輯
> - 做的事情：提供查核或不同意見
> - 查核對象：即時訊息
> - 使用到公民科技、自動化技術
> 
> [name=mrorz https://g0v-slack-archive.g0v.ronny.tw/index/channel/C2PPMRQGP#ts-1608736034.2102]
> 
> :elephant: 覺得光露出 Cofacts 專案名沒有辦法達成目的，想囊擴所有專案面向 :arrow_right:「Cofacts 真的假的」訊息回報機器人與查證協作社群
> :whale:  想用最簡單符合創用 CC 規定，也避免露出單一專案面向來框住專案實際做的事情 :arrow_right: Cofacts 真的假的社群
> :giraffe_face:從專案發展脈絡以及顧及收集資料需求出發，選擇強調聊天機器人:arrow_right: 真的假的聊天機器人協作社群
> [name=mrorz]
> 機器人跟查證社群並不是分開的工作呢，開發者很多設計都是在協助查核社群協作出查核機器人。2016年開始的提案也就是聊天機器人，給bot一個機會。
> [name=bil]

約束力 ＆ 導流需求？

- 長頸鹿重點比較像是機器人社群，但我們是事實查核社群 [name=lucien]
	- 但我們希望大家來參與社群，一起來查核 [name=lucien]
	- 長頸鹿會讓大家覺得是做聊天機器人
- 如果可以讓對方知道是機器人的話就可以 [name=bil]
	- 不希望讓人知道是專門做事實查核的組織或資料庫
	- 不希望「直接來問社群」、「盡量問，其他人會來回」
	- 希望大家服務自己
- 但大象也有一樣的功能 [name=johnson]
	- 同時呈現機器人、以及讓大家來參與機器人的感覺

:::success
「Cofacts 真的假的」訊息回報機器人與查證協作社群
:::


### 使用者條款
> by bil

- 本文
    - 網站[原使用規範](https://hackmd.io/mFSlWs4IQke_9RnFAOWlfQ?view)、[因應 CC BY-SA 修正後之規範](https://hackmd.io/UA0Mqo5ISyKH3yLPCC0YVA)
        - 對象為「登入之使用者」
        - 授權範圍為「回應」、「針對回應的評價」
    - Chatbot [原使用規範](https://hackmd.io/t2DSbtU9RsS8cNTi-uLtSQ)、[因應 CC BY-SA 修正後之規範](https://hackmd.io/xYCRvT6dQVi-k0ySgZYaLg)
        - 對象為「使用 Cofacts chatbot 的人」
        - 授權範圍為「回報之轉傳訊息」、「針對回應的評價」、以及 aggregated usage data
- 露出 Terms
    - 網站：https://github.com/cofacts/rumors-site/pull/364
        - 登入下方標示「登入網站即表示您同意使用者條款」
        - 展示內容之下加上 CC BY-SA 標示
    - Chatbot
        - Developer 設定可以設定 privacy policy URL 與 terms of use URL 但不知道會顯示在哪 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_921b40f9d9d4d0482f13586abc9f2520.png)
        - LINE Official account manager 可以設定 profile page ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_41cd7e7cef734977e9e4554e2077ee26.png)
            - 設定完：![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_81daa10f5eb4f781458ad52ecbd52774.png =x400)
			- 放主頁就好，不要放 profile [name=bil]

### 適用範圍

同意 Terms of use 的人，可能不是其所提供內容的著作權人。

- 案例甲：https://cofacts.g0v.tw/reply/IqhmUHYB9w1KR1Iki14S
    - 第一段是編輯寫的，第二段則是從第三個出處的聯合報導裡面複製貼上
    - 技術上要抓出與出處內容重複的部分然後標示，不是辦不到，但滿麻煩的，而且沒辦法做得很可靠。
- 案例乙：https://cofacts.g0v.tw/reply/Zh5MHGMBSH_MLFhISF78
	- 直接複製貼上其他查核報告
	- 實務上很難禁止協作編輯直接複製貼上，因為
		- 要求改寫太不近人情
		- 直接複製貼上確實能達成闢謠效果，不應全盤禁止
          該查核報告段落，其實本身就是複製貼上官方公告 lol
- 案例丙：https://cofacts.g0v.tw/article/2byo8zr3m9uwg
    - 編輯 A 使用 編輯 B 撰寫的回應來回應。
    - 但這個部分問題應該不大，因為
		- 編輯 A 與編輯 B 都會同意使用者條款
		- 使用者條款裡面會說是以「社群」的名義、用 CC BY-SA 釋出。

> 修改 attribution 文句讓使用者自行判斷，是否能有法律效力？如「以上內容之原創部分，由 CC BY-SA 4.0⋯⋯」


## Website Discussions

### Jumbotron

> 目前 dev.cofacts.org 的 landing page，在桌面環境下似乎少了讓人往下捲的示意或 call to action 按鈕
> @nonumpa 第一眼的注意力會被紅色 1、2 抓過去
> 這個部分有沒有什麼改善的空間呢
> [name=mrorz https://g0v-slack-archive.g0v.ronny.tw/index/channel/C2PPMRQGP#ts-1608735100.2083]
> 
> 我剛剛隨便看了其他網站，他們都沒有示意可以往下捲，但都會有一個按鈕 (start now/freetrial) 放在中間，我覺得讓「懷疑自己收到謠言嗎」的圖可以按可能比示意好一點（？）
> [name=nonumpa]
> 
> 可能第一張圖的區域用扁一點，讓「你可以這麼做」露出一半
> [name=nick]
> 
> 我之前有做過
> 1. 向下浮動箭頭
> 2. 向下掉落或是搖擺的導引動畫
> 3. 不全屏
> 4. 下面邊緣上 shadow
> [name=lucien]

:::success
MrOrz 在 https://github.com/cofacts/rumors-site/pull/371 處理
3. 95vh 之類的
:::

### URL slug limits

> 其實我們好像沒有討論過 URL slug 的限制
> 我想要不要
> - 強制都轉小寫
> - 如果 not url-safe (slug !== encodeURIComopnents(slug)) 的話就不給過
> - 前後端都實作檢查限制
>
> [name=mrorz https://g0v-slack-archive.g0v.ronny.tw/index/channel/C2PPMRQGP#ts-1608485232.200200]

:::success
開票紀錄上面的 limitation
https://github.com/cofacts/rumors-api/issues/242
:::

### Landing page SEO
- https://github.com/cofacts/rumors-site/pull/371
    - 標題使用 CC BY-SA attribution
- https://github.com/cofacts/rumors-site/issues/347#issuecomment-731930199

:::success
新版 landing page 上線後執行
:::

## Release

Blocked by CC BY-SA attribution


