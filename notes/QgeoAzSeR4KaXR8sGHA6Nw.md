---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20220824 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis 出席：記者x3, bil, mrorz
- 線上出席：nonumpa
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :rocket: Staging

#### :robot_face: rumors-line-bot

- chatbot 送出圖片 https://github.com/cofacts/rumors-line-bot/pull/318

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [x] 應可送出「全新訊息」
    - [x] 問訊息來源時選擇「我自己打的」會被擋下。（圖片訊息不會問來源）
    - [x] 選擇「整篇轉傳」後會詢問是否要送出訊息。（圖片訊息不會問來源）
    - [x] 不同意送出訊息後可以收到感謝。
    - [x] 同意送出訊息後就會送出訊息，並得到：
        - [x] Cofacts article page 按鈕
        - [x] 寫理由的按鈕
        - [ ] （若沒開啟推播）應該要看到「開啟小鈴鐺」泡泡，且可打開 setting 頁面
        - [x] 「分享到 Facebook」、「分享到 LINE」且可以正常運作
    - [x] 可從聊天視窗內打開理由視窗，繼續填寫理由送出。查看 article page 看理由是否有被送出。
    - [x] 可以再打開理由視窗，此時會載入上次填寫的理由。修改理由送出後，查看 article page 看理由是否有被送出。

- [ ] 送出「沒回應」的舊訊息，應可送出新理由
    - [x] 文章的「N 人回報」應該仍然要 + 1（除非測試者已經針對該篇送過 reply request）。
    - [x] 可從聊天視窗內打開理由視窗，繼續填寫理由送出。查看 article page 看理由是否有被送出。
    - [x] 可以修改理由送出。查看 article page 看理由是否有被送出。
    - [ ] （若沒開啟推播）應該要看到「開啟小鈴鐺」泡泡，且可打開 setting 頁面

##### ⛔️ Release Blockers
N/A

##### 未竟項目

#### :globe_with_meridians: Site

- `articleTypes` https://github.com/cofacts/rumors-site/pull/501

##### Testing checklist
http://dev.cofacts.tw/

**未登入**下檢測：

- [x] Article list
  - [x] Filter works
  - [x] Sorting works
  - [x] Can go to article page

##### ⛔️ Release Blockers

##### 未竟項目


### :eye: Under review

## 大松檢討

https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/https%3A%2F%2Fhackmd.io%2F%40mrorz%2FBklLwE6C5

- 大家都在打共筆，35000 字 [name=bil]
- 有 weber & patrick 寫回應，現場來有查核 [name=bil]
- 很有產出

## Image support
> https://github.com/orgs/cofacts/projects/9

- Chatbot state diagram 更新
    - 參考：https://docs.google.com/drawings/d/1N6RYK3KYlSzLDu6SClNwz57U0QfakIrat5sG5uUhovU/edit

### Processing existing image
- Colab: https://colab.research.google.com/drive/1EmCgNtPVr_U3PZ-HDSn1OzjlPRVC0jqh

### Extended goal
> https://g0v.hackmd.io/uZ3gouRWRamtrCFzKFrgnw?both#Extended-goal

- 噁心圖片怎麼處理
    - 模糊化，但我分不出來哪一張 disturbing [name=mrorz]
    - 每一張都 blur 會很妨礙查核 [name=bil]
    - 建議鯫檢舉 [name=bil]
    - 絕大多數的圖都不是 distrubing，此種圖片佔很少數 [name=bil]
    - Extended goal: use Google API detect disturbing content [name=mrorz]
        - After 檢舉 is implemented
- OCR 可能要優先處理，大多的圖都有字 [name=mrorz]


## 檢舉處理

- 檢舉 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_64049ff689ca4a3fbc1a873941d61a4f.png)
    - 被檢舉：https://cofacts.tw/reply/Eoo4xoIBv5it-Cx_30dX
    - 前情提要：https://g0v-slack-archive.g0v.ronny.tw/index/channel/C2PPMRQGP/2022-08#ts-1661181470.5332

## APAC trusted media summit
https://www.trustedmediasummit.com/zh

- Hybrid?
    - 線上直播 + 實體
- bil 報了
    - 實體: talk [name=bil]
- 可能不會有 booth [name=bil]

## 宜蘭在地青年培訓

> https://g0v.hackmd.io/sDlMC1SiQM-7R72UZUBSkA#%E5%9C%A8%E5%9C%B0%E9%9D%92%E5%B9%B4%E5%9F%B9%E8%A8%93

1hr talk

- 從詐騙入手 小孩的補助
- 用錯誤訊息帶疑美論 (PTT 9400萬假圖)
- 查核技巧
    - 事實＆意見
    - 工具

## 8/31 會議暫停一次

