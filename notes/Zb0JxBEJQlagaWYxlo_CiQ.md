---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20210421 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：bil, mrorz, lucien
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :globe_with_meridians: Site

[2021/4/16 Hotfix](https://github.com/cofacts/rumors-site/releases/tag/release%2F20210416) fix old android & safari loading issue

## Code for Sch001ing Camp

Anything to update?

- 男生班很可怕 [name=bil]

## [LINE bot 送出流程改版](https://github.com/cofacts/rumors-line-bot/issues/214)

Prev discussion: https://g0v.hackmd.io/BBeVH2VxRNOCq5QB_HC6EQ?both#Devs---Q2

1. [ ] LINE bot LIFF 可呼叫 Cofacts API https://github.com/cofacts/rumors-line-bot/pull/248
2. [ ] 改寫 feedback LIFF 與回應 bubble
    - 「分享」按鈕與「覺得有用」、「覺得沒用」應該同時出現，「分享」不該被 feedback 擋住
    - 「覺得有用」、「覺得沒用」在 LIFF 內告知已送出，不要再 `sendMessage` chatbot
4. [ ] 改寫送出流程為[方案二](https://g0v.hackmd.io/r3NK7xssSwCNPFxthlw7tA?view#chatbot-%E4%B8%8D%E5%95%8F%E4%BE%86%E6%BA%90) 移除 `sendMessage`
5. [ ] 改寫未有回應的 reply request 流程，送出 reply request 後直接顯示[方案二](https://g0v.hackmd.io/r3NK7xssSwCNPFxthlw7tA?view#chatbot-%E4%B8%8D%E5%95%8F%E4%BE%86%E6%BA%90)最後的按鈕 bubble
6. [ ] 移除 `urlToken` 機制
    - must remove dependency of context in LIFF workflows
7. [ ] 移除 `sendMessage` scope 以及 [external browser check](https://github.com/cofacts/rumors-line-bot/blob/dev/src/liff/lib.js#L85-L99)
8. [ ] 實作 [LIFF article page](https://g0v.hackmd.io/0RX4MsjRRJmBqJSKVilWMA#article-amp-reply-LIFF) 


## 防詐顯名

- follow-up?
    - 法務如何
    - call to action: 討論

## Elevate Taiwan
- 4/24 10:30am - 3:30pm
- Art Reading Cafe (雅痞書店)




