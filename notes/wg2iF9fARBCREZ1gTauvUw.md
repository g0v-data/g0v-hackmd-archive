---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240117 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis 出席：bil, mrorz, daisuke
- 線上出席：nonumpa
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API

- [Hackathon fixes](https://github.com/cofacts/rumors-api/releases/tag/release/20240111)
- [Collab server unit tests](https://github.com/cofacts/collab-server/releases/tag/release/20240111)

#### :globe_with_meridians: Site
- [hackathon contribution & blocked user can't transcribe](https://github.com/cofacts/rumors-site/releases/tag/release/20240111)
- [Cooccurrence display](https://github.com/cofacts/rumors-site/releases/tag/release/20240112)

#### :robot_face: rumors-line-bot

- [article/reply time and multi-msg](https://github.com/cofacts/rumors-line-bot/releases/tag/release/20240111)

### :rocket: Staging


#### :globe_with_meridians: Site
##### Testing checklist

Facebook 審核員一直跟我跳針說
- https://cofacts.tw/terms 無法載入
- 要有東西不然違規

我跟他說我用 browserstack 看、給他看錄影，都沒用，他就是要在他的謎之環境下能打開
所以我只好把 terms page 做 server render

https://github.com/cofacts/rumors-site/pull/562

http://dev.cofacts.tw/

**未登入**下檢測：

- [x] Can load user agreement page (使用者條款)

##### ⛔️ Release Blockers

##### 未竟項目


### :eye: Under review

- https://github.com/cofacts/rumors-site/pull/562

## CCPRIP

### [Op] Transcript spam
> nonumpa
> https://g0v.hackmd.io/vKCvrqSQTlm7GEx9MAXGaw?view#op-Transcript-spam-處理

沒進度QQ
已開票: https://github.com/cofacts/rumors-api/issues/332

### [Comm] Cooccurrence / article group

TODO

- [x] Fix blocker & bugs
- [x] 大松
- [x] 選前週會 test & release (如果沒問題)
- [x] Implement website display cooccurrences
- [x] 選舉
- [ ] 實作 ASKING_CONTEXT (Optional?)
- [ ] 補 unit tests

Enhancement on websites

- Reuse reply in article group
  - 相似可疑訊息納入搭配的回應
- Want to know if article article in group are replied or not (how many replies)
  - 想知道哪些還沒回，要補回應
  - 有回應的話就知道可以重用
  - 試排：每個 item 有 reply、group last report 移到最上面

### [Op] 檢舉處理

每天都有，已經 84 篇
https://cofacts.github.io/community-builder/#/editorworks?type=2&day=365&userId=j4S8C_VlGKtPU9HfXCNBrSCWw9vzC9IMTMouPEID1ILw0BJyE&showAll=1
- 看起來像小孩在玩機器人 [name=nonumpa]
- 提議 block [name=mrorz]
- 同意 [name=bil]
- 貼社團詢問，沒有異議就進行
  - 沒有違反 LEGAL https://github.com/cofacts/rumors-line-bot/blob/master/LEGAL.md沒
  - 覺得這個使用者送出的內容對社群正常運作有影響，但很難通案認定，未來有狀況如果我們想要有所行動，也是會問社群。

[過去](https://g0v.hackmd.io/EfM4Xqn4TA-nIXF8Njjovg#%E6%AA%A2%E8%88%89%E8%99%95%E7%90%86)：[狂貼 Youtube](https://cofacts.github.io/community-builder/#/editorworks?type=2&day=365&userId=j4S8C_aLDBZJEJGJ3Lomo6A8o19GrR6GUdFQCvgDYGuuvVirc&showAll=1)

[過去](https://g0v.hackmd.io/Fmkhf62_SKGIlwwwLrRnAw#%E6%AA%A2%E8%88%89%E8%99%95%E7%90%86%EF%BC%9A%E4%B8%AD%E4%BA%8C)：[中二](https://cofacts.github.io/community-builder/#/editorworks?type=2&day=365&userId=j4S8C_UGoyBvoeIT1ATe1Wz02jFh_IsMOKLf7lqR3k2UpZqGk&showAll=1)

## 徽章

縮小成 2cm x 1.6cm，每個單價便宜了 1 元 XD
[報價單](https://drive.google.com/file/d/19MJb6SYVFoywzUMG5yu2X76vANpo16aB/view?usp=drive_link) NT$6,195

## 2 月小聚籌備

- [ ] 日期：2/24
- [ ] 食物
- [ ] 場地：宜蘭？沒有就 npo hub
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
- [ ] 投放目標：
  - 推播日: 農曆年間 / 前（提早）
- [ ] KKTIX:
- [ ] 誰會來呢：bil, mrorz, nonumpa (maybe)
- [ ] 記得帶：貼紙、環保杯
- [ ] LINE 文案
- [ ] VOOM 發文

## 下週會議

- 改週四 (1/25)？[name=bil]
  - OK

