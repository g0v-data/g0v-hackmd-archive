---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20221102 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：cai
- Workis: bil, mrorz, nonumpa
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :globe_with_meridians: Site

1027 Release https://github.com/cofacts/rumors-site/releases/tag/release%2F20221027
- terms page
- video in tutorial 

### :rocket: Staging

#### :robot_face: rumors-line-bot

##### Testing checklist

zh-tw: https://lin.ee/1QUzEX4nI
ja: https://lin.ee/FTFFEPg
en: https://lin.ee/9uXBXDM

- [x] 送出「沒回應」的舊訊息，應可送出新理由
    - [x] 文章的「N 人回報」應該仍然要 + 1（除非測試者已經針對該篇送過 reply request）。
    - [x] 可從聊天視窗內打開理由視窗，繼續填寫理由送出。查看 article page 看理由是否有被送出。
    - [x] 可以修改理由送出。查看 article page 看理由是否有被送出。

- [x] 送出「有回應」的舊訊息，應自動回傳回應
    - [x] 應列出訊息所有的回應
    - [x] 選擇回應之後可以幫回應 upvote
    - [x] 可以再次選擇 downvote
    - [x] 選完回應之後，還可以捲回去選其他回應

- [x] Rich menu 測試
    - [x] 「設定」更改後再次打開，應該會保留原本設定
    - [x] 「教學」可以觸發教學流程

##### ⛔️ Release Blockers

- 圖片搜尋故障
    - Proxy URL env var 要設

##### 未竟項目

- Rich menu 沒有日文版
- 日文的看他怎麼說 還是中文 [name=cai]
  - 應該是誤植，英文是有的
- 日文的「proivider better reply」是英文
- 日文&英文的「Hi!我是個會幫你查謠言....」是中文
- 英文 Volunteer editors have published several replies...
  - fact-checking contributors / fact-checkers
- 英文 This content is provided by Cofact message... 

cai++ ++ ++ ++ ++

:::info
Tracked in https://github.com/cofacts/rumors-line-bot/issues/338
:::

## 重複案例

> 一分鐘內同樣5部影片
https://cofacts.tw/article/Y4ulHoQBv5it-Cx_w5Fd
https://cofacts.tw/article/YoulHoQBv5it-Cx_w5Fb
https://cofacts.tw/article/ZIulHoQBv5it-Cx_xJFa
https://cofacts.tw/article/ZYulHoQBv5it-Cx_xJHM
https://cofacts.tw/article/YYulHoQBv5it-Cx_w5Ec
> [name=cai]

- Hash 一樣，「相似可疑訊息」裡面有 [name=mrorz]
- Race condition [name=mrorz]
    - 先搜尋再送出
    - 同時很多搜尋 + 送出，就會不 work
    - 查 log

## 活動與宣傳

### Oslo 論壇
- 1p flyer https://docs.google.com/document/d/1w8c4GXVfm3zt9WRB_GTFPLZ4JIOL7wxODmwiIb6Dq3Y/edit
- 改 analytics 上面的圖 （editor）

### 傳單
- https://drive.google.com/drive/u/0/folders/15FPdC_ERJQaq7EykzL-p_phUCH0z8edK
- Facebook 粉專換 impact report (中文版)
- 「一」在預覽圖上好像會特別粗

## 影片自動播放 follow-up

- 拿掉自動播放後， iOS 會顯示空影片
- 如 youtube 邊捲動邊載入是否符合需求？[name=mrorz]
  - 一開始會都是白的
  - 捲到畫面內後 1~2 秒內開始自動播放
  - 未來產生縮圖時，此行為不變（白色的部分會變成縮圖）

:::info
Tracked in https://github.com/cofacts/rumors-site/issues/515
:::


## facebook login follow-ups
https://g0v.hackmd.io/K_sfKNZjRG-pSsQrEAGhEA?view

## 小聚籌備

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
