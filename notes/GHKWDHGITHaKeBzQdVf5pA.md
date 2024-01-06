---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20230907 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：orz, nonumpa, bil
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API
- https://github.com/cofacts/rumors-api/releases/tag/release%2F20230902

#### :robot_face: rumors-line-bot
- https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20230902

## CCPRIP

### [Comm layer] 逐字稿
> https://g0v.hackmd.io/@cofacts/rd/%2FOhGIQzoxR5eF6audQuS_FQ
> [name=nonumpa]

#### History
> [name=nonumpa]

PRs
- [Site](https://github.com/cofacts/rumors-site/pull/545)
  - 完成編輯後馬上去看版本歷史紀錄的話，可能會有問題 [name=nonumpa]
  - 類似寫了 feedback 點開卻沒東西 [name=mrorz]
- [API](https://github.com/cofacts/rumors-api/pull/316)
- [Collab-server](https://github.com/cofacts/collab-server/pull/4)
- [DB](https://github.com/cofacts/rumors-db/pull/66)

#### AI
##### LINE bot: Merging `processImage` & `processMedia`
- On production

##### API 寫入 ydoc
> Design doc https://g0v.hackmd.io/wkx286lmTDaFUpgRhnUawQ#CreateMediaArticle
> Related discussion on 2023/8/2: https://g0v.hackmd.io/0tPABSZ6SRKswBYqAc1vZw#API
> [name=mrorz]

- createMediaArticle 時，查詢 ai responses，把現成的逐字稿寫入
  - 若無現成逐字稿，先不做事
- 寫入 ydoc 的部分：
  1. extract `write(db, state, documentName)` in https://github.com/cofacts/collab-server/pull/4/files#diff-2328e74e7ccb28094c3e5470aea7aa50289a9033aab07612097d447d49a1b4d9R43-R57 into utility
  2. Expose it in npm package `hocuspocus-extension-elasticsearch`
  3. rumors-api depend on `hocuspocus-extension-elasticsearch` and use the utility to write `ydoc`

#### Auth
> [name=mrorz]

No progress yet

## Cofacts 外觀改版

Figma: https://www.figma.com/file/nFFi6c8ennXV8CxeF58Asl/Confact?type=design&node-id=0-1&mode=design&t=LqEgNlweKaYIfdXa-0

- Latest replies list
  - 排版還沒有支援圖片影片
- Article detail
  - 「關注」沒有實作。目前只有檢舉違規內容。把關注換成檢舉？

NextJS 13 + Tailwind + cloud run
https://g0v.hackmd.io/@cofacts/rd/%2F%40cofacts%2FHJ_O1Xhhs

:::success
MrOrz 實作 nextjs 13 + tailwind + components 試排
:::

## 美玉姨眼花

> Related discussion
> 6/21 時討論過，在 Cofacts LINE bot 內 https://g0v.hackmd.io/NwQhGGgkSvCp6jR-DqB7JQ#Chatbot-%E6%A8%99%E8%A8%98%E8%A8%8A%E6%81%AF%E5%9B%9E%E6%87%89%E6%99%82%E9%96%93
> https://github.com/cofacts/rumors-line-bot/issues/354

---

>  https://cofacts.tw/article/zrs2dk48ar41
想說這篇倒讚數有點多，再看了查詢日期。難道是[9/4颱風假的公告](https://www.facebook.com/chenchimai/posts/pfbid02fTBAs6JCJHmbvfAsGNGzJW7MkB8crXQbbf8dyLn5QVvE7F1jx2ezTiwRA7a8ciqGl)太像所以被匹配到嗎 
> [name=cai]

### Cofacts 的場合

85% 相似度，標示一樣的地方
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c9af343659e4655c3f54f90eadd4c5ff.png =300x)

### 美玉姨的場合

直接顯示
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0d0f5e776ab095823c21fb06b3d37919.png =300x) ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_91b7efcd91695381cfd8bc754c999fe1.png =300x)

- 少了確認的問題，就會答非所問 [name=bil]
- 文不對題的狀況一定很多，不可能要我們這裡處理，不應該花時間在上面 [name=bil]

:::warning
跟美玉姨反應這個 case
orz（developer relation 的角度）反應給美玉姨
:::


## 9 月小聚
- 2023/9/17 (日) 2pm - 5pm
  - 台中好民文化行動協會
- [ ] 食物
- [x] 場地費：2500/4hr 公益團體價
- [x] 時間：
	- 活動時間：14:00 - 17:00
	- 時間分配
        - 2:00 - 2:20 開場
            - 影片
            - Slido 暖身
        - 2:20 - 2:40 引導註冊網站、介紹評價現有回應
        - 2:40 - 2:50 實作評價
        - 2:50 - 3:10 介紹補充資訊
        - 3:10 - 3:40 實作補充資訊、自我介紹、休息
        - 3:40 - 4:10 介紹撰寫新回應
        - 4:10 - 4:40 實作撰寫新回應
        - 4:40 - 5:00 介紹分類、RSS、合照
- [ ] 投放目標：中彰投 50000 人
  - 按照台南 case 可能到場約 5 人
  - 嘗試提早推播（9/8 就推？）
- [ ] KKTIX: https://cofacts.kktix.cc/events/cofactseditor38
- [ ] 誰會來呢：bil, nonumpa, mrorz
- [ ] 記得帶：貼紙、環保杯
- [ ] LINE 文案 
9月17日星期天下午，Cofacts 真的假的 來到台灣好民文化協會舉辦查核志工培訓了，了解資訊戰中公民可以發揮的影響力嗎？我們需要的就是你，只要帶上筆記型電腦，就能以一己之力，保護我們自己的國家與民主哦！
活動完全免費，會提供點心，請幫我們先報名。☺️☺️☺️

報名連結：https://cofacts.kktix.cc/events/cofactseditor38

- [ ] VOOM 發文

好民文化行動最近的 drama (?)

- https://www.facebook.com/fangru.lin.90/posts/pfbid0yeUSwTZUj1shcyQsJxctttotxeZddGc67oMkcZaRFCrw4HLeGyLqLGrLAL7wTKiWl
- https://www.facebook.com/photo.php?fbid=270015642641208&set=p.270015642641208&type=3
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a6633aaba476e003429a6f926cf114ad.png)
- 讓我想到 https://www.facebook.com/837370859956705/photos/a.837696063257518/1177733872587067/



