---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20221109 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：cai
- Workis 出席：mrorz, bil, sean
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :robot_face: rumors-line-bot
LINE bot multi-language https://github.com/cofacts-/rumors-line-bot/releases/tag/release%2F20221103

## 重複圖 log

> https://g0v.hackmd.io/QPTHTIGEQpGgyYrDxNOMCQ#%E9%87%8D%E8%A4%87%E6%A1%88%E4%BE%8B
> 

- 五篇均是由同一使用者 `j4S8C_gdYIUB5gHC5ZV6hNnan7AsbMR6cToAj09IeFMIV3XW8` 送出
- 時間相差不到 1 秒
  - 2022-10-28T12:51:31.124Z: `ZYulHoQBv5it-Cx_xJHM`
  - 2022-10-28T12:51:31.030Z: `ZIulHoQBv5it-Cx_xJFa`
  - 2022-10-28T12:51:30.773Z: `YoulHoQBv5it-Cx_w5Fb`
  - 2022-10-28T12:51:30.704Z: `YYulHoQBv5it-Cx_w5Ec`
  - 2022-10-28T12:51:30.770Z: `Y4ulHoQBv5it-Cx_w5Fd`
- Log
  - `12:51:29.088Z` 傳送影片；回傳「你要請人查查這則訊息嗎？」
  - `12:51:31.196Z` "Yes" 按鈕；回傳 `YoulHoQBv5it-Cx_w5Fb`
  - `12:51:31.221Z` "Yes" 按鈕；回傳 `Y4ulHoQBv5it-Cx_w5Fd`
  - `12:51:31.423Z` "Yes" 按鈕；回傳 `ZIulHoQBv5it-Cx_xJFa`
  - （下面應該都是類似的）
- 所以是手抖＋沒有重新 search [name=mrorz]
  - 「送出」按鈕已經顯示給使用者了，按下去之後也不會消失，所以可以一口氣按很多次
  - 每次按送出時都重新 search 的 cost 有點高，而且也不一定擋得住
- 是否要改成 quick reply 這樣只能按一次？ [name=mrorz]
  - [2022/04 討論](https://g0v.hackmd.io/pGl4iqVKRXed7opCK_txVw#%E9%80%81%E5%87%BA%E8%A8%8A%E6%81%AF%E6%B5%81%E7%A8%8B%E6%98%AF%E5%90%A6%E4%BD%BF%E7%94%A8-quick-reply): 不要用 quick reply 因為桌面版不支援 
  - [似乎無解](https://www.line-community.me/en/question/600859e3851f74bb9ca1e28e?answerid=6009a2fe401690d0b656765b)
- 亦可在送出時修改 redis context 使第二次點按失效（？） [name=mrorz]
  - 在 redis 寫入目前正在上傳的 message ID、成功後刪除之類？

## Interview

以下項目以 Email 主旨紀錄：

### 需面訪

- TaiwanPlus News
    - 後兩週：citizen lab
    - 未來的週三均可，但提到可能有其他拍攝組

### 待填

- Taipei Times / 華語，deadline 不明

### 已交回、待出刊

- Media request: Interview about Cofacts and disinformation in Taiwan / 英語，10/21 已交

### 已出刊，需問授權

- 關鍵評論網-未來大人物想來約採訪時間 / 華語，10/25 已出刊
  - 好像刪掉了！！！囧 [name=mrorz]
  - https://www.thenewslens.com/article/175211
  - https://becomingaces.com/article/238

## Open data usage

- 收到來信，用來 train AI
- 過去 CC0 時政治學者有用過
- 現在 CC BY-SA 也有人說是拿來 train AI (open data 的表單回應)
  - 很難查是否有 attribution 與 share alike
  - 開共筆 追開放進度嗎 [name=cai]
    > 「同學 功課寫完記得到XXX補上分享連結阿」
    - 蒐集開放資料的影響力、放進影響力報告 [name=mrorz]
- 3rd party chatbot, III platform
  - 有 by 
  - 但不知道是否有 derived work 來 share alike
- IORG 明確遵守按照資料使用條款
  - 明確有 derived work (報告）
  - 標記：符合條款 https://iorg.tw/da/25
  - share alike：有公告 https://iorg.tw/open

:::success
- 以 IORG 做榜樣來進行溝通
- 開共筆追蹤
:::

## Error rate 增加問題

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ea0c7caf58ec3754a031802f225a58da.png)

- 前面沒有這樣
- 11/6 之後也沒有這樣
- 以下為日本時間

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1537768d15638edc8d3285cc6fb2c258.png)
(中略)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e04aeb54d4354de4e51ad2249a3b0c82.png)

當天台灣時間 20:00 左右（日本時間 21:00）確實比較忙錄
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_178448c93aa2c2b31c56525a72b1ad41.png)

21:00 (日本時間 22:00) 時有大量 nginx 499
研判是有爬蟲爬網站 + rumors-site 又發作吃很多 CPU

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_57e192b542c369f8d9a484dea145d7da.png)

- 原因不明的老問題
- rumors-site 會吃大量 CPU 使整台機器卡死
- 之前都靠 cronjob 重開 site 來 unblock
- 可以考慮 Cofacts 網站重拉 data flow + Typescript + nextjs 13
  - SSR 只出特定的欄位，用 prop 傳進 page component，不要放進 apollo cache 再整個 cache serialize 傳到 FE
  - 考慮 [ISR](https://nextjs.org/docs/basic-features/data-fetching/incremental-static-regeneration)，或甚至直接改成 [server component](https://beta.nextjs.org/docs/rendering/fundamentals)
  - Data flow 變複雜，靠 Typescript 確保資料有 load

## CCPRIP - Google cloud

https://g0v.hackmd.io/BRsJOevWSbyUMBSZEVVWrA?view#Proposal

## 小聚

- [ ] 時間:
    - 11/20 (日) 13:30-17:30 
- [ ] 場地：NPO HUB 2F key holder :Ronny
    - 台北市中正區重慶南路三段 2 號 2 樓  
- [ ] 食物？統編？
- [ ] 時間：2022/11/20
	- 活動時間：14:00 - 17:00
	- 時間分配
        - 2:00 - 2:20 開場
            - 影片
        - 2:20 - 2:40 引導註冊網站、介紹評價現有回應
        - 2:40 - 2:50 實作評價
        - 2:50 - 3:10 介紹補充資訊
        - 3:10 - 3:40 實作補充資訊、自我介紹、休息
        - 3:40 - 4:10 介紹撰寫新回應
        - 4:10 - 4:40 實作撰寫新回應
        - 4:40 - 5:00 介紹分類、RSS、合照
- [ ] 投放目標：雙北 + 基隆
- [x] KKTIX：https://cofacts.kktix.cc/events/cofactseditor33
- [ ] 誰會來呢：bil, mrorz, nonumpa
- [ ] 無法來：
- [ ] LINE 文案 
假新聞四處亂竄，對於厭煩吵架與對立的你，如果用一個下午的時間，參與本次志工活動，將可以對社會創造偉大的貢獻！
Cofacts 真的假的 在11月20日本週日下午 2 點- 5點  ，徵求新的查核協作志工，活動完全免費，現場供應點心，邀請你的到訪與參與！用鍵盤與智慧，為周圍的朋友與大家帶來和諧的力量。
(記得帶筆記型電腦與充電線唷！)
時間：11月20日(日) 下午 2 點- 5點
地點：台北市中正區重慶南路三段 2 號 2 樓
最近的捷運站是中正紀念堂站2號出口 

## 違規檢舉

> 有人檢舉此編輯在幫 39health.com.tw 打廣告
> https://cofacts.github.io/community-builder/#/editorworks?showAll=1&day=365&userId=XosaNoQBv5it-Cx_Paln
> 確實所有的出處都來自這個網站，而且出處跟原文關係有點薄弱。
> 該網站看起來應該是從中國網站 http://www.39.net/ 搬運文章的網站。要如何處理好呢？

* 這兩天觀察，似乎不只一位，回一小時內的文 [name=cai]
https://cofacts.tw/article/3fko78ebzuoix
https://cofacts.tw/article/2bc7vikk8gwwg
    - 豬頭 https://cofacts.github.io/community-builder/#/editorworks?type=1&day=365&userId=vIvGN4QBv5it-Cx_86vF&showAll=1
    - Stephinie https://cofacts.github.io/community-builder/#/editorworks?type=0&day=7&userId=XosaNoQBv5it-Cx_Paln&showAll=1
    - Phoebe https://cofacts.github.io/community-builder/#/editorworks?type=0&day=365&userId=84s1N4QBv5it-Cx_IqqQ&showAll=1
- 多人使用同一網站的來源，CIB [name=bil]

:::success
先貼 FB group 公告
:::
