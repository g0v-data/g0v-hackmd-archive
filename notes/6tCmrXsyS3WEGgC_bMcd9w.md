---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240229 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :globe_with_meridians: Site
- 實科協會 footer

### :rocket: Staging

- API: 送新影片時會算縮圖與預覽
- Site: 太多 feedback 現在可以全部載入 https://github.com/cofacts/rumors-site/pull/556 marcussfu++


#### :robot_face: rumors-line-bot

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [ ] 送影片到 staging bot 可以正確送出

#### :globe_with_meridians: Site

##### Testing checklist
http://dev.cofacts.tw/

**未登入**下檢測：

- [ ] Article list 可以看到新送的影片（2x 速度）
- [ ] Article detail
  - [ ] 可以看到 reply feedback，有寫字的優先
  - [ ] 如果超過 10 則，有「載入更多」可以按

登入自有帳號後檢測：
- [ ] Article detail
  - [ ] Can submit, remove own reply
  - [ ] Can upvote, downvote other's article reply

##### ⛔️ Release Blockers

##### 未竟項目


### :eye: Under review


## CCPRIP
> https://g0v.hackmd.io/@cofacts/rd/https%3A%2F%2Fg0v.hackmd.io%2FBRsJOevWSbyUMBSZEVVWrA

### [Op] Transcript spam
> nonumpa
> https://g0v.hackmd.io/vKCvrqSQTlm7GEx9MAXGaw?view#op-Transcript-spam-處理


### [Comm] article group 收尾
> nonumpa


### [Comm] Thumbnails for video and audio
> https://github.com/cofacts/rumors-api/issues/326

- 增加了影片 thumbnail
    - 10s thumbnail (2倍速播放) 用在各種列表
        - chatbot 列表要改 code
    - 30s preview 用在 article page 等處
        - 壓縮 + 長寬 0.75x 節省ㄌㄧ
        - 需要另外改網站、LINE bot code
        - 要揭示「登入後」
    - 因為只處理前 10s / 30s，process stream 會比下載檔案的 stream 提早，要一起改 https://github.com/cofacts/media-manager/pull/10 裡的實作
- CI 一直壞
    - alpine linux 可以運作，ubuntu 預設 ffmpeg 卻沒有這次用的新 codec 可用
- ffmpeg 轉檔會導致 CPU 飆高
    - 不確定上 production 之後的 loading
    - 理想上整個 media manager 相關 utility 應該分拆成另一個 microservice deploy 在 cloud run 之類的地方

### [Op] FB 申請與 Google 非營利

- Facebook business verification: 已通過
  - 已驗證 profile & email 的 advanced access ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_bad308e375c9961c19d9a7dff53336bf.png)
  - 可測試是否能以 Facebook 登入
- Google: 失敗
  - 網路討論：發 ticket 給 Percent https://support.google.com/nonprofits/thread/254596080/contacting-google-or-percent?hl=en&sjid=7865925514358855560-AP
  - 官方文件：發 ticket 給 Percent https://poweredbypercent.zendesk.com/hc/en-us/articles/13805863075857-My-nonprofit-has-been-rejected-by-Percent
  - Percent 說他無法確定我跟組織的關係
      - 送了護照與理事長當選的圖給他

## User organization / badge

> [name=mrprz]
> - TFC 希望可以把有上過課的人（的回應）與其他查核者做區分
> - 十傑當時也有一組人，想要顯示為同一組人

### Proposal #1: 做成 badge
- 跟在 user 上
- 一人可以有多個 badge、一個 badge 可以很多人有
- https://www.figma.com/file/zpD45j8nqDB2XfA6m2QskO/Cofacts-website?type=design&node-id=3752-399&mode=design&t=sKRA2zwLRCy5YS6U-4

#### Pros
- 可以跟其他成就一起做一做

#### Cons
- 會跟其他成就混在一起
    - 哪些成就要在 reply 標出來、哪些又不用？

### Proposal #2: 做成 organization
- organization 會顯示在作者欄（顯名）
    - LINE bot 也會顯示「某組織標記此篇為」⋯⋯等等
    - 像是藍勾勾
    - 可以避免任意 user 亂冠名自己是 TFC 或 MyGoPen 之類
- organization profile page
    - 可以設定網址；如果他人 reply 裡面有人引用這個網址，也可以列為此 organization 的貢獻
- 一個 user 可以有多個 group
    - 撰寫 reply 時可以選擇要用個人，還是 group
    - 會另外在其他地方顯示是哪一個使用者用了這個 group 的身份
        - （可以像 FB 一樣，只有 group 內的人看得見是誰發的？）
- 總覺得這個提案好像我幾年之前提過，但一直找不到⋯⋯[name=mrorz]

#### Pros
- 組織可能會很開心

#### Cons
- 需要處理組織的 governance——誰能開組織 etc
    - 當時是想說有網站的，只要能證明自己是網站 owner 都能來開
    - 其中，IFCN certified 的會有更顯著的標記之類

## 大松籌備

- 這次沒辦法提案 QQ
- good first issue?
