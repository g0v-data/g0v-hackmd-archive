---
tags: cofacts, meeting note
---
20191218 會議記錄
===== 
orz,bil,4cat,文武,ci, Raymond (water only)

> 上次開會紀錄：https://g0v.hackmd.io/@mrorz/S1cpqgCpr
> 

## 拜訪
- New york times 採訪

## 聖誕節
1. 改去 NPO hub(同意了)
2. 帶食材
3. NHK 採訪


## 其他採訪

《青觀點》採訪共筆 https://docs.google.com/document/d/1_pMx707izTwje_mKhjEdsblVpwG4XTTwNxes0GCiWu4/edit

:::success
orz 回信
:::

## 週末面海松

報告：比鄰（台語，英文 slide）
徵求：如首頁
分配：如首頁

首頁：https://g0v.hackmd.io/F9TublsbRriZUed2NOgrhw

## Rumors-site 升級 next9
1. [x] Article list --> PR to dev
2. [x] Article page （見 API 更新）
3. [x] Reply list
4. [x] reply page
5. [x] docker build
6. [x] landing page
7. [x] 上 staging
8. [x] 上 production --> 新台幣升級
9. [x] google analytics (w/ gtag)
10. [ ] All i18n (including levels...)
11. [ ] RSS feed


### PRs
- Rollbar 整合 https://github.com/cofacts/rumors-site/pull/187
- `/analytics` & `/hack` route: https://github.com/cofacts/rumors-site/pull/188 (還是做在 nginx 好?) --> 換成在 nginx 做，之後發到 rumors-deploy


### TODOs
- 從其他頁面點進 `/replies` 會壞掉
- 字太小

### Performance issue follow-ups

:::success
討論串:
https://g0v-tw.slack.com/archives/C2PPMRQGP/p1576478257010400
https://g0v-slack-archive.g0v.ronny.tw/index/channel/C2PPMRQGP/2019-12#ts-1576478257.010400
:::

即使禮拜日升級伺服器，禮拜一的時候，中文網站還是很慢，CPU 100%，但英文版不會。
我現在沒辦法解釋的是我沒有動他的時候CPU是100%但是關掉重開就會比較正常？？

改 nginx 的 `proxy-cache` 之後，不會再花時間在 serve assets 但還是會 CPU 100%

在週一半夜 restart `site-zh` 之後才恢復正常。

Billion:這件事情再觀察一個禮拜

:::success
Orz:
每天中午 12:30 重開 rumors-site-tw 好了
:::

## OCR

Deployed to production :tada: 

TODO: 粉專文案

:::success
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_3db9a9a1b36659239b47cd870f289f99)

大家可以試試看查圖片功能了唷～～～
雖然不是每張圖都可以成功，但一些熱門的謠言，就讓Cofacts 真的假的幫你查一查吧❤️
跟Cofacts一起踹踹看！！！！
hashtag OCR 踹踹中
:::

## Newsgeist 2020, Mar 13 - 15 in Singapore

Any TODO?
:::success
桓誠去
:::
