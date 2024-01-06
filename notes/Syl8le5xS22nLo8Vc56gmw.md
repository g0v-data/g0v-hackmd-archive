---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20211229 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis 出席：bil, mrorz
- 線上出席：4000, cai
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## 小聚籌備

- [x] 1/9 (日)
- [ ] 主題：2022 新年新希望
    - 中正萬華區罷免投票當日 :P
- [ ] 場地：
    - NPO Hub 13:30 ~ 17:30
    - ~~[小樹屋](https://thehapp.com/space/267)~~
        - 捷運行天宮站 1 號出口，步行約 4 分鐘
        - 民生東路二段90巷4號1樓-101房
        - 1:30 開始借就好，很好佈置；~ 5:30
        - 缺少延長線
- [ ] 食物 
    - 熱的燒仙草之類
    - Ubereats
    - https://www.ubereats.com/tw/store/%E5%85%AB%E6%99%82%E7%A5%9E%E4%BB%99%E8%8D%89-%E6%9D%BE%E8%8F%B8%E5%BA%97/S1gfxwEaQBmQNMnSJba1ow
- [ ] 時間：
	- 活動時間：14:00 - 17:00
	- 時間分配
        - 2:00 - 2:20 開場
            - 影片
            - Keyholder 介紹場地
        - 2:20 - 2:40 介紹 mission 1 - 按讚 
        - 2:40 - 3:00 進行評價 (20則)
        - 3:00 - 3:30 休息、自我介紹、交流 
        - 3:30 - 3:50 介紹 mission 2 - 寫回應
        - 3:50 - 4:30 進行回應（1則）
        - 4:30 - 5:00 介紹分類、RSS、合照
- [ ] 投放目標：北北基桃
- [ ] 事前產生 spreadsheet 25 人分工
- [x] KKTIX：[name=bil]https://cofacts.kktix.cc/events/cofacteditor28
- [ ] 誰會來呢：mrorz, bil, (nonumpa?)
- [ ] 無法來：lucien
- [ ] 做圖：用 Figma 做 [name=mrorz]
    - https://unsplash.com/photos/PXl_S152jNM
    - 字壓在色塊上
- [ ] LINE 文案

查核機器人所回應的查證資訊，都是善良的志工一筆一筆新增的。
在這裡邀請您，即使只是對查證資訊好奇，不限年齡、無論經驗，都能參與本次的查核工作坊。只需要攜帶筆記型電腦，花一個下午的時間，就能習得查核技巧幫助其他的朋友喔！

2022年的第一次真的假的編輯志工教學聚會，就在2022年01月09日下午2:00-5:00
在NPO Hub Taipei（台北市中正區重慶南路三段2號 4樓廚房），活動完全免費。
最近的捷運站是中正紀念堂站2號出口

:::success
From 檢討：
- 行前通知信要提醒說不能來的話要取消
:::

## 廣告處理

- Reply spam - 阮明明 --> https://github.com/cofacts/takedowns/pull/33
    - 比照 yegogo
- Reply request spam - 各種廣告 --> https://github.com/cofacts/takedowns/pull/34/files
    - 標記為 blocked

## Block user 延伸事項

Slack discussion: https://g0v-slack-archive.g0v.ronny.tw/index/channel/C2PPMRQGP#ts-1640669726.234100

> 做個檢舉機制，比較容易實作的方式如下：
> 1. 在「我想補充」與「回應」右邊多個「舉報」按鈕
> 2. 按下「舉報」時會帶使用者到 google form，裡面已經預填好一些欄位，如 user ID
> 3. 在 Google form 設定說有新舉報的時候寄信通知 cofacts googlegroups
> 4. 在該 form 的 response spreadsheet 開一個手動填寫的新 column 放我們是否有執行刪除。
>     1. 執行刪除就是之前寫的 block user script
>     2. 我可以在 Google sheet 自動用前面預填的欄位做出 block 指令，所以要執行就直接複製指令執行即可
> 5. 在 google spreadsheet 開一個新 sheet 把我們有執行刪除的人列出來，然後 publish 這個單一 sheet to HTML。這個 published URL 會被放進 cofacts/takedowns repo，我們就不針對廣告檢舉另外發 PR 與公告了。
>
> 以上 1, 2 是唯一會動到程式碼的部分；回報、執行與公告一氣呵成，不針對個案另行公告。
唯一有瑕疵的是在執行前大家看不到違規者的 spam 長什麼樣子，但之後可以用 script 撈出所有 BLOCKED content 供大家檢視說目沒 block 錯人。
> [name=mrorz]
>
> 希望像是youtube留言那樣，每則補充右邊多個 「 ⋮ 」，點下去有個「回報濫用」→ 跳出表單 →  單選廣告後送出
> [name=cai]

表單內容
- 項目種類（reply request, reply 等）- prefilled, 必填
- reply request ID / article ID : reply ID - prefilled, 必填
- spammer user id - prefilled, 必填
- [違規樣態](https://github.com/cofacts/rumors-site/blob/master/LEGAL.md) - 必填
    - 廣告投放
    - 惡意的文章散布 
    - （僅「項目種類」為 reply 時：）侮辱、毀謗、散布不實資訊
    - （僅「項目種類」為 reply 時：）侵害著作權
    - 其他有違反相關法令或侵害他人權利之情事
- 舉報人暱稱（選填）
- 附註欄位（選填、自由填寫）

後續處理
- Google form / sheet 設定
    - apps script submit hook: 拿項目種類、ID 去查違規內文，驗證 spammer user id 是否正確
    - 有新回應時寄信到 cofacts google groups
- 手動填入處理結果欄位，可能有幾種處理方式
    - 封鎖使用者所有內容（不另發新 takedown 公告）
    - 移除單一內容（不另發新 takedown 公告）
    - 判定不處理
- 建立 filtered view of processed records 並 publish to web、把網址一次性的公告在 cofacts/takedown（濫用回報處理結果）
    - 會跟 blocked user 未來貼了什麼分開 spreadsheet

細節討論
- 只有已登入 Cofacts 的使用者才看得到檢舉按鈕？
    - 雖然表單收不到是誰舉報、表單連結流出的話還是可以任意舉報，但應該可以減少任意舉報 [name=mrorz]
    - 合理 [name=bil]


## 整理詐騙使用話術，寫篇貼文

- medium 貼文
- 內文放詐騙文字，讓 Google 搜得到 (?)
- 分為養套殺
    - 養：Cofacts 內的各種攬客訊息、徵各種試吃員試住員、您好請問是本人調理身體嗎、二次詐騙
        - [我本身有在做](https://cofacts.tw/search?type=messages&q=%E6%88%91%E6%9C%AC%E8%BA%AB%E6%9C%89%E5%9C%A8%E5%81%9A)
        - [試住員](https://cofacts.tw/article/2vflekpevr9e2)
    - 套：
        - 投錢（有訊息嗎？）
            - 關鍵字： 1000元開通
              https://cofacts.tw/article/1soe18ahetf16
        - 租借 FB 帳號
            - https://cofacts.tw/article/238fyagsgmywq
    - 殺：Cofacts 內的各種「裁決書」
    - 延伸閱讀
        - [報導者 引流仲介](https://www.twreporter.org/a/online-scams-fraud-tool-insiders)
        - [防詐達人 二次詐騙](https://getdr.com/%E4%BD%A0%E6%9C%89%E8%81%BD%E9%81%8E%E3%80%8C%E4%BA%8C%E6%AC%A1%E8%A9%90%E9%A8%99%E3%80%8D%E5%97%8E%EF%BC%9F%E6%83%B3%E8%A6%81%E8%BF%BD%E5%9B%9E%E8%A2%AB%E9%A8%99%E7%9A%84%E9%8C%A2%E4%B9%9F%E5%88%A5/)
- 另一種分法：整理同一 LINE 使用者舉報的 article (可能是同一個對話串！)
- 另一種分法：要使用者付錢的（騙錢）＆不要使用者付錢的（車手 or 帳號出租）
- 後果
    - 當車手的判決書
      [臺灣高等法院 臺南分院 109 年度上訴字第 1481 號刑事判決](https://law.judicial.gov.tw/FJUD/data.aspx?ro=2&q=148c6069bca8c2c9b13e11e2bd29001c&sort=DS&ot=in)
    - 貸款變人頭帳戶(關鍵字：詐欺、洗錢防制法)
      臺灣高等法院 108 年度上易字第 105 號刑事判決

:::success
存參，歡迎有興趣寫的人著手
:::

## Cofacts search snippet 修改

Discussion: https://g0v-slack-archive.g0v.ronny.tw/index/channel/C2PPMRQGP#ts-1639796083.204700

> 今天才發現cofacts的meta content 是寫
> 「Cofacts 真的假的」是一套連結網路訊息與查證訊息的協作型系統，試圖對假訊息問題作出草根應對。
> 原以為會是寫像平常講的那種白話版  群眾協作的方式，開放大家一起來查證假訊息 
>
> 太文言讓人覺得進入門檻高，降低意願
> [name=cai]
 
 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6979270c732776566ee851af2ee3254a.png)
 
> 在 LINE 上加入「Cofacts 真的假的｜轉傳查證」好友，就能輕鬆查可疑 LINE 訊息，有沒有網友查證；也歡迎大家來到 cofacts.tw 網站，針對網傳訊息提供闢謠回應。
> [name=mrorz]

> 在 LINE 上加入「Cofacts 真的假的｜轉傳查證」好友，就能輕鬆查可疑 LINE 訊息。到 cofacts.tw 網站，可以針對網傳訊息提供闢謠回應。
> [name=bil]
> 重點是機器人可以查謠言、網站可以教機器人

> 一起來幫網路上的可疑訊息寫查核回應、共同教導聊天機器人回話，將多元的闢謠資訊傳遞給在 LINE 上收到謠言的人。
> [name=mrorz]
> 直接讓大家知道「我要你幹嘛」很好[name=bil]
> 手機板看這個比較好[name=cai]
> ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b609a72c8f278b178c3885342b1dfe5e.png) 
> ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e931a9a490e6980cebe78b4382562f15.png)


> 「Cofacts 真的假的」是一套連結網路訊息與查證訊息的協作型系統，任何人都可以到網站幫可疑訊息寫查核回應、共同教導聊天機器人回話，將多元的闢謠資訊傳遞給在 LINE 上收到謠言的人。
>太長QQ
> ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_bb1a63f7e8b849e56cdd309b310436bc.png)

> 「Cofacts 真的假的」連結網路訊息與查證訊息，任何人都能在網站幫可疑訊息寫查核回應、共同教導聊天機器人回話，將多元的闢謠資訊傳遞給在 LINE 上收到謠言的人。
> ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_43167f14e971003b66359349b0759dd8.png)
> ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e36c8b4774fe586e0e42bad4c72650ef.png)


> 若對「系統」有興趣，可能會到 cofacts.tw/hack 就能看到更為明確的定義（連結「網路訊息」與「事實查核」的「協作型系統」）；或許 Google 的 search snippet 可以只放 call to action 就好 [name=mrorz]


:::success
開PR：https://github.com/cofacts/rumors-site/pull/466

中文「一起來幫網路上的可疑訊息寫查核回應、共同教導聊天機器人回話，將多元的闢謠資訊傳遞給在 LINE 上收到謠言的人。」

英文 --> 乾脆先不改 XDDDD

https://github.com/cofacts/rumors-site/blob/master/pages/index.js#L31
:::


## LINE open chat 要怎麼詐騙（？）
Ref: 引流仲介
https://www.twreporter.org/a/online-scams-fraud-tool-insiders#%E5%BC%95%E6%B5%81%E4%BB%B2%E4%BB%8B%EF%BC%9A%E6%8A%8A%E4%B8%8D%E5%90%8C%E4%BA%BA%E5%BC%95%E9%80%B2%E5%80%8B%E5%88%A5%E7%BE%A4%E7%B5%84%E3%80%81%E7%94%A2%E7%94%9F%E5%90%8D%E5%96%AE%E5%BE%8C%E5%B0%B1%E8%B3%A3%E6%8E%89%EF%BC%8C%E5%93%AA%E7%AE%A1%E6%98%AF%E4%BB%80%E9%BA%BC%E6%A5%AD%E8%80%85%E8%A6%81%E7%94%A8


