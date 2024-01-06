---
tags: cofacts
---

# Cofacts @ COSCUP 2019 大綱

## 簡短介紹 Cofacts
- chatbot 用法
- 送到資料庫
- 編輯寫完之後會回到 chatbot、請使用者自行判斷
- 橫向的架構圖
- 開放：授權、Cofacts hackfoldr, open data, open API
- 應用：2018/12/23 [美玉姨](https://medium.com/@sheseee/%E4%BD%A0%E4%BB%8A%E5%A4%A9%E4%B9%9F%E6%8A%8A%E7%BE%8E%E7%8E%89%E5%A7%A8%E5%8A%A0%E5%85%A5-line-%E7%BE%A4%E7%B5%84%E4%BA%86%E5%97%8E-6c71bf4e347)、趨勢科技防詐達人
- 以 LINE bot user count 為背景來看事件
    - 2016/10 第一次提案
    - 2017/1 [宇宙大爆炸](https://www.facebook.com/groups/1847232902175197/permalink/1895293667369120/)
    - 2019 的現在
    - 發生什麼事？做了哪些 design choice
- Back in 2016 --> 只有 chatbot
- 講的東西都在 Cofacts hackfoldr「舊資料」


## Design Choices we have made - Cofacts 如何煉成
:::info
過去的文章：
https://matters.news/@johnsonliang7/%E5%9B%9B%E8%90%AC%E4%BA%BA%E5%8A%A0%E5%A5%BD%E5%8F%8B%E7%9A%84-cofacts-%E7%9C%9F%E7%9A%84%E5%81%87%E7%9A%84-%E6%98%AF%E5%A6%82%E4%BD%95%E7%85%89%E6%88%90%E7%9A%84-zdpuAudkbVoY4yUfrrfNzEdteftkrUih9rErcSDsxMHzUyF3d
:::

### 1. From automation to collaborative
講的東西都在 Cofacts hackfoldr
翻開
2016.10.15 第一次提案: 尋求 google indexing 高手
https://g0v.hackpad.tw/-LINE-bot-Zb4bFLB7pnv

2016.12.17 換成協作
https://hackmd.io/XjBpsn35TdGHNUwKx68LdA
從過去的編輯守則來看⋯⋯
- 多則回應也 ok
- 編輯身份：沒設限
對比 Wikipedia 模式：單一頁面，對編輯也沒設限但是有其他補救措施

2017.1 因為 airtable 不堪使用，要換到網站
airtable 爆炸
2017.3 大改版：通通從 airtable 搬到 elasticsearch

討論：
2017.2.9回應要不要登入？
https://beta.hackfoldr.org/cofacts/https%253A%252F%252Fhackmd.io%252Fs%252Fr1fvCz9Og

「不把協作者拒於門外」

- - -

### 2. Chatbot flow

2017.1.5「有用嗎？」
系統「有用嗎」問卷： https://www.facebook.com/groups/1847232902175197/permalink/1894866897411797

不執著於「第一個搜尋到的東西」
--> 讓使用者選擇

放進 chatroom v.s. 1-on-1 的設計
越來越複雜  XD
對比：美玉姨、趨勢科技

#### ~~Team up! 成立團隊~~
~~既然要組織編輯，那自己也要組織起來⋯⋯
2017.1 公民科技獎助金 開始提案
2017.1.26 開始討論～
每週會計紀錄都放在 hackfoldr~~


### 2. Categorizing instant messages into types

2017.3.6 ~  18 二分法問題「怎麼分類」
「分類方式討論」https://hackmd.io/s/rk1KHEgsg

下面有分法歸納
https://beta.hackfoldr.org/cofacts/https%253A%252F%252Fhackmd.io%252Fs%252FrJ0nBnYsx
其他網站怎麼分
https://beta.hackfoldr.org/cofacts/https%253A%252F%252Fhackmd.io%252Fs%252FSyRA-J-Te
2017.3.30 歸納成「核心價值」
Design decision 紀錄:
https://beta.hackfoldr.org/cofacts/https%253A%252F%252Fhackmd.io%252Fs%252Frk1KHEgsg


2017.5.30 很難回 --> 加 type
https://beta.hackfoldr.org/cofacts/https%253A%252F%252Fhackmd.io%252Fs%252Fr1HvVA9Jb

「無法壓抑的個人意見」
「雙贏」

- 2017.8.16 [Medium 貼文公告](https://medium.com/cofacts/2017-8-16-%E6%96%B0%E5%9B%9E%E6%87%89%E5%88%86%E9%A1%9E-%E5%80%8B%E4%BA%BA%E6%84%8F%E8%A6%8B-%E5%8F%83%E4%B8%8A-f96d92a9965f)
- [現在「含有個人意見』的比例](https://datastudio.google.com/reporting/18J8jZYumsoaCPBk9bdRd97GKvi_W5v-r/page/ckUQ)

lucien:
https://hackmd.io/@Jqvgv0-WQmKlQ3Lt21pMog/BJxsXEc3g?type=view#%E6%96%87%E7%AB%A0%E5%9B%9E%E6%87%89%E7%9A%84%E5%88%86%E9%A1%9E

2019: 修改 wording 成更隱晦，以內文為主，把判斷延後

### 3. 詢問 chatbot user 理由

#### 問題
編輯太少，爛訊息太多
> 1. 內文就有出處：https://cofacts.g0v.tw/reply/AWBfG4NFyCdS-nWhulMy 、 https://cofacts.g0v.tw/article/AWBtW4WUyCdS-nWhulY1
> 2. Replies list 查詢「新聞 報導」 https://cofacts.g0v.tw/replies?before=&after=&q=%E6%96%B0%E8%81%9E%20%E5%A0%B1%E5%B0%8E 約有 500 篇之譜，佔 3.8%
> 4. 人氣拉票 https://cofacts.g0v.tw/reply/AWCOD5QkyCdS-nWhul0a
> 5. 各種美景表演食譜經驗分享 https://cofacts.g0v.tw/replies?before=&after=&q=%E5%88%86%E4%BA%AB 約有 250 篇，佔比 1.9%

討論過的解方：
* 201710 [避免使用者把 LINE bot 當 siri 來用](https://hackmd.io/s/BJRJxopTb#避免使用者把-line-bot-當-siri-來用) --> 字數太短 or 只有 URL (2018/2 ~ 2018/10選舉前)
* [查證單一訊息的效益](https://hackmd.io/BwRmFYDME4HYCMC0AGEJaICwFMDGGBDSAZmEXhADZJtrtl5Zcg==?both#查證單一需求的效益)
* [限縮發文權益](http://beta.hackfoldr.org/cofacts/https%253A%252F%252Fhackmd.io%252Fs%252FS1zuSP--G) --> 黑名單白名單, 只開放編輯（在網站上回應過）的人能透過 LIEN bot 送新文章進來, 只開放知道要送「轉傳訊息」、而且是送來「進行事實查證」的人送出新文章
* [是否該處理新聞、對文章 downvote](http://beta.hackfoldr.org/cofacts/https%253A%252F%252Fdocs.google.com%252Fdocument%252Fd%252Fe%252F2PACX-1vQTgQtH5W-Co4UX--1bV8CBRbklr_kSYppCIlLpJ0W3x0BnPET0zJN50lx0P_MyyK-KHVCYuO2RkWyG%252Fpub)

這個功能 2018/[1 月](https://hackmd.io/@mrorz/HJEGZfmVM?type=view#Proposal-LINE-bot%E3%80%8C%E8%A9%A2%E5%95%8F%E7%88%AD%E9%BB%9E%E3%80%8D%E5%8A%9F%E8%83%BD)就開始醞釀，目的是為了解決越來越多使用者把 Cofacts 當 Siri 的問題。

1. 墊高發文門檻，過濾單純只是想傳進來玩玩看的使用者——根據訪談，這樣調皮的人確實存在。
2. 明白使用者到底想知道什麼，讓使用者來說服我們說「這則訊息該查」。同時也實作對理由的 upvote / downvote，讓編輯對這則「是否有查證價值」有初步評分的機制。
3. 透過反問 LINE 使用者「爭議在哪」，希望能促進使用者開始思考並且表述自己認為這則訊息的問題點在哪裡、並且開始對自己看到的資訊產生懷疑。這是媒體識讀的第一步，也是專案一直以來努力的方向。


#### 效益
- 很有用嗎
    - 2018/7 https://beta.hackfoldr.org/cofacts/https%253A%252F%252Fhackmd.io%252Fs%252Frkj-S9m4m 不太 work
    - 2018/12/24 LIFF https://www.facebook.com/groups/cofacts/permalink/2295896103975539/
    - 2019/1/2 限制字數 https://g0v.hackmd.io/s/SyN-sb8b4#%E7%90%86%E7%94%B1%E5%A4%AA%E7%9F%AD%EF%BC%8C%E6%B2%92%E6%9C%89%E5%8F%83%E8%80%83%E5%83%B9%E5%80%BC - 成效 https://g0v.hackmd.io/s/B1uUy3VQ4#%E5%B7%B2%E4%B8%8A%E7%B7%9A
    - delay 問題：https://g0v.hackmd.io/s/rJB1nENcN#Chatbot-log%E3%80%8C%E6%98%AF%E5%90%A6%E8%A6%81%E9%80%81%E5%87%BA%EF%BC%9F%E3%80%8D%E5%87%BA%E7%8F%BE%E6%AC%A1%E6%95%B8%E8%88%87%E8%A8%8A%E6%81%AF%E7%B5%B1%E8%A8%88
- 怎麼改善
    - 放寬囉 https://g0v.hackmd.io/s/rkEn4TtqE#%E7%90%86%E7%94%B1%E6%AA%A2%E8%A8%8E

#### 新問題
訊息太晚進來。多晚？分析的 meeting

### 4. Bulding the editor community

2017.6.19 第一次小聚
- 人數 照片
- LINE 推播（掉 friend lol）

- 貼圖！貼紙！
- 等級制度

https://miro.medium.com/max/4800/1*8383nCn2_N0I4TbkESSL3A.jpeg

https://miro.medium.com/max/2000/1*xZWapXJ7OAS5lVkoqo5_vw.jpeg

下一次：8/31!

以身作則：小精靈

### ~~5. 插曲們~~

- 2017/1/9 突然爆紅
https://www.facebook.com/groups/1847232902175197/permalink/1895293667369120/
~~- 2017/3 被攻擊 https://beta.hackfoldr.org/cofacts/https%253A%252F%252Fhackmd.io%252Fs%252FSkHt8JZ6l~~
- (...待整理)
- 2018/12/24 美玉姨
- 2019 陰謀論
:::info
舊公告
https://www.facebook.com/notes/cofacts-%E7%9C%9F%E7%9A%84%E5%81%87%E7%9A%84%E7%B7%A8%E8%BC%AF%E4%BA%A4%E6%B5%81%E5%A4%A9%E5%9C%B0/201722-%E4%BB%A5%E5%89%8D%E7%9A%84%E6%9B%B4%E6%96%B0%E8%88%87%E5%85%AC%E5%91%8A/1906280316270455/
:::

## Cofacts beyond 2020: connection & bridges of all conflicting opinions

Accelerate loop



2017.1.25 到 LINE 報告時的「初衷」：「連結」訊息與回應
https://docs.google.com/presentation/d/1FUcDH5rARTDktlzCXvwBZCor6UM8RmsS-_ezuF-mlWU/

labeling, etc
