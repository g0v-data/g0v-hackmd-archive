---
tags: g0v-summit, 2020
---

#  Sentry 練習 x Summit 網站工人回顧

在 Summit 開始前，讓我們來聊聊這半年來做 Summit 的感想吧～

在正式開始前，請先回想這半年來在 Summit 做過的各種事情，無論是寫程式、開會、熬夜趕工、聚餐，無論是開心或是批評都可以，希望每個人都能至少寫一件事情，在[網站檢討](https://g0v.hackmd.io/13d9rRhYRnyMxgZ4zT_YvQ)上

## Sentry 練習

Sentry 是用來收集各種錯誤訊息的服務，和 Rollbar 類似，不限語言與運作環境，也可綁定常見的 logger ，設定 verbose 多高（error/warn/...）的訊息要倒到 Sentry，注意開發時要關掉 Sentry。

使用 Sentry 時，可以得到幾項好處：

- 錯誤集中收納，並可依據發行版本、環境分類，也可綁定 Jira/Github ticket ，方便追蹤與分鐘
- 塞在網頁前端時，可以看到所有 JS exception ，以及錯誤發生前的 XHR 、 routing 紀錄
  - 自動統計瀏覽器、作業系統版本，不用再請客戶回報使用環境啦～
  - 可以偷塞使用者登入資訊，方便追蹤與辨別錯誤
  - 支援常見前端框架，錯誤訊息時，有機會夾帶各框架相關資訊，例如 props value
- 開源專案免費升級，沒有每月事件數上限

據說還可以：

- 綁定 [source map](https://docs.sentry.io/platforms/javascript/sourcemaps/) ，讓程式碼追蹤更方便



### 現場解 Sentry Issue

ddio 帶大家走過一次 Sentry UI 後，就來認領 issue ，解 Summit 主網站臭蟲，並且分享使用、解 bug 心得吧～

1. [範例一](https://sentry.io/organizations/g0v-summit-2020/issues/2064144897/?project=5447103&query=is%3Aunresolved) & [相關問題](https://sentry.io/organizations/g0v-summit-2020/issues/2064153034/?project=5447103&query=is%3Aunresolved)
2. [範例二](https://sentry.io/organizations/g0v-summit-2020/issues/2069492001/events/dcbc48fe5df44ed2993628a38e2d9a1e/?project=5447103&query=is%3Aunresolved)

#### 使用步驟

0. 每輪 15 分鐘
1. 認領底下任一張 Sentry issue ，標上自己的名字
2. 在 Sentry 頁面了解大致狀況，並使用 Sentry 搜尋，將確定重複的問題，合併成一個
3. 在 Sentry issue 開一張 Github issue ，指派給自己
4. 在 Git 開一個 feature branch 來解問題，送 MR 回來
5. 大家輪流分享 Sentry 使用方式，以及一起 code review ，大家都沒問題，就可以 merge

#### Sentry Issue

- [ ] `ddio` `/agenda` this.$t(...).filter is not a function / [Sentry link](https://sentry.io/organizations/g0v-summit-2020/issues/2049842651/?project=5447103&query=is%3Aunresolved) 
- [ ] `/transportation`  t is undefined / [Sentry Link ](https://sentry.io/organizations/g0v-summit-2020/issues/2032915641/?project=5447103&query=is%3Aunresolved)
- [ ] `/agenda` undefined is not an object (evaluating 'document.getElementsByTagName('video')[0].webkitExitFullScreen') / [Sentry Link](https://sentry.io/organizations/g0v-summit-2020/issues/2031299392/?project=5447103&query=is%3Aunresolved)
- [ ] `/agenda` r.matchAll is not a function. (In 'r.matchAll(t)', 'r.matchAll' is undefined) / [Sentry Link](https://sentry.io/organizations/g0v-summit-2020/issues/2002139123/?project=5447103&query=is%3Aunresolved)
- [ ] `/agenda` ResizeObserver loop completed with undelivered notifications. / [Sentry Link](https://sentry.io/organizations/g0v-summit-2020/issues/2052721376/?project=5447103&query=is%3Aunresolved&statsPeriod=14d)
- [ ] `/agenda` this.$t(...).find is not a function / [Sentry Link](https://sentry.io/organizations/g0v-summit-2020/issues/2047477553/?project=5447103&query=is%3Aunresolved&statsPeriod=14d)
- [ ] ==mango== `/agenda` n.forEach is not a function / [Sentry Link](https://sentry.io/organizations/g0v-summit-2020/issues/2047477539/?project=5447103&query=is%3Aunresolved&statsPeriod=14d)
- [ ] Chris `/transportation` Cannot read property '_leaflet_pos' of undefined / [Sentry Link](https://sentry.io/organizations/g0v-summit-2020/issues/2046762344/?project=5447103&query=is%3Aunresolved&statsPeriod=14d)
- [ ] `lai` `/partners` undefined is not a function (near '...this.partners.reduce...') / [Sentry Link](https://sentry.io/organizations/g0v-summit-2020/issues/2039127484/?project=5447103&query=is%3Aunresolved&statsPeriod=14d)


## 網站工人回顧

分享在[網站檢討](https://g0v.hackmd.io/13d9rRhYRnyMxgZ4zT_YvQ)上的內容，也聊聊 Summit 以外的各種事情。

:::info
以下複製貼上 `網站檢討`
:::

{%hackmd 13d9rRhYRnyMxgZ4zT_YvQ %}



