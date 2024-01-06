---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20231025 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis 出席：bil, nonumpa, mrorz, Crystal
- 線上出席：cai, 4000
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API
https://github.com/cofacts/rumors-api/releases/tag/release%2F20231019
- OCR sensitivity

#### :globe_with_meridians: Site
https://github.com/cofacts/rumors-site/releases/tag/release%2F20231020
- Comment section requires login first [name=marcusfu]++

#### :robot_face: rumors-line-bot

https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20231019
- Webhook handlers in Typescript
- Context refactor



### :rocket: Staging

API: reduce hallucination https://github.com/cofacts/rumors-api/pull/323


#### :robot_face: rumors-line-bot

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [x] 送圖片、影片、聲音進 staging bot 並送出到資料庫

#### :globe_with_meridians: Site

- Fix collab line break https://github.com/cofacts/rumors-site/pull/552

##### Testing checklist
http://dev.cofacts.tw/

**未登入**下檢測：

- [x] 可以顯示逐字稿（含有斷行）
- [x] 無法編輯逐字稿

登入自有帳號後檢測：
- [x] 可編輯 AI 做的逐字稿
- [x] 可編輯其他查核者寫的逐字稿
- [x] 可以看到同時編輯者的 cursor
- [x] 可以看到逐字稿歷史紀錄

##### ⛔️ Release Blockers

##### 未竟項目

- 此訊息不存在 https://dev.cofacts.tw/article/20eQLYgB800gity8yQLX
  ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d95809cfd948896db7804cecd13363e3.png) [name=nonumpa]
  - non-null on `createdAt`
- 斷行無法顯示 history [name=nonumpa]
  - 其實有，只是無法 hover ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_69768851a5c7719a54b82a04507ef069.png)
- 錯的修改者 https://dev.cofacts.tw/article/UZR8JosBXtQmmerobXll [name=nonumpa] 
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d70a6c73ae4069eabd6d1e29a84c75d6.png)
  - 斷行有紀錄
  - 但「西」的刪改很奇怪
  - 可能是 y-snapshot 自己的 bug
- 編輯紀錄差異 [name=cai]
  - 如果是直接在編輯器編輯，歷史紀錄會顯示只改一個字
  - 如果是用複製貼上到記事本改錯字再貼回來會顯示改一大段

### :eye: Under review

https://github.com/cofacts/rumors-site/pull/552

## CCPRIP

> https://g0v.hackmd.io/@mrorz/ccprip

### [Comm] Transcript

#### Crowd-sourced

- 更新 [crowd-sourced transcript 文件](https://g0v.hackmd.io/@cofacts/rd/%2FOhGIQzoxR5eF6audQuS_FQ)
    - Interaction between UI, API, collab-server and DB
    - Record latest fields

#### docker test db 起不來

- Elasticsearch 6.8 不支援 Apple silicon [name=nonumpa]
  - 7 or 8 的 docker image 才有

#### API jest test 

- package.json 放 config, [roots](https://jestjs.io/docs/configuration#roots-arraystring) 是掃 test 的地方
- import root 在 babelrc

#### 斷行問題

- 舊的逐字稿不見的 root cause
    > 我在網站上想改 prosemirror schema Collaborate/Schema.js
    > 把它弄得很簡單像 https://prosemirror.net/examples/schema/ 第一個例子只有 text node 與 doc node
    > 結果整個逐字稿就會消失，歷史紀錄也會消失 ._. [name=mrorz]

#### Transcript Migration

> https://drive.google.com/drive/folders/1lxRqYqgR8tXO7TT9mWP7fMHkuiQawLt-

- 圖片： 12264 uploaded / 12264 total
- 影片： 2956 uploaded, 3922 OCR / 7238 total

#### VAD to reduce hallucination

https://g0v.hackmd.io/wkx286lmTDaFUpgRhnUawQ#VAD-to-reduce-hallucination

下週再更新

### [Infra] Downtime detection

> 今天 2:00 ~ 12:09 API server 有 downtime，症狀是 api.cofacts.tw 、 cofacts-api.g0v.tw 均無法存取。
> 主因是
> 凌晨時我更新 API 版本 https://github.com/cofacts/rumors-api/releases/tag/release%2F20231019
> 更新時 docker 可能更新了 api container 的 IP
> 即使 docker-compose 有使用 hostname 沒有寫死 IP，但 nginx 會 cache 住 IP 直到 configuration reload。
> 可能之後更新任何 container 都要記得 reload nginx config orz
> [name=mrorz]

Update: https://g0v.hackmd.io/BRsJOevWSbyUMBSZEVVWrA?view#Logging-and-monitoring

## Hypercert 回溯公眾投資

- Sync：collect more wallet addresses

## 小聚籌備

- FB、LINE 貼文 for 新營

> Previous 貼文：https://www.facebook.com/2booksite/posts/pfbid0GSSQyvGAyHrSQAvjBy4y7bQJ1UFZPiKHeL7E5vWpuGcKdAjhiB7hguGjYEKj7jqzl?__cft__[0]=AZUtLXYdvCizygW1dJysf5sbtHI6c3dPVfE7YNcvYGp10Sk3BPfwm7DAgZTGpIcBAcK4ctJrgbBNVXCz4L_SosFshqL7gbbEIIJU0TsOj9MfB1Ggd2JwZHV1evg8HIh86gEmevVDjpXawlAjSxvhwzyCha9kiZ1AnUhfGAU2sgCa77JMx_J-qXmldqv7SBLliOA&__tn__=%2CO%2CP-R

Cofacts 真的假的 第一次前往新營！！
感謝這份難得的緣分，好喜歡一層層樓梯間曬書店的雅緻與對議題的重視。 
免費的志工培訓就在 2023年11月18日 14:00-17:00 曬書店，期待各位的參與，讓我們一起透過鍵盤與查找資料，用民眾草根的力量對抗假資訊的威脅。記得帶電腦唷！
730台南市新營區中山路93-2號（請上樓）