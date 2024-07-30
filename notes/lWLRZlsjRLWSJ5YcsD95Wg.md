---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20230412 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis: bil, mrorz
- 線上出席: nonumpa
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API
Full URL message + failed url resolving --> null resonse
- https://github.com/cofacts/rumors-api/releases/tag/release%2F20230406

#### :robot_face: rumors-line-bot
Handle null response
- https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20230406

### :eye: Under review
- https://github.com/cofacts/rumors-api/pull/303 (以下討論)

## 大松檢討

> https://g0v.hackmd.io/@cofacts/meetings/%2Fa217McHYSpmfzW3E86Dbdg%3Fview

- 感謝 @chewei ，把真的假的按讚放進 5min 貢獻
- Caleb 說會看 issue
- Marcus will fix PR https://github.com/cofacts/rumors-site/pull/537#discussion_r1163257209 

## CCPRIP

### [Comm] Crowd-source transcript
> https://g0v.hackmd.io/@cofacts/rd/%2FOhGIQzoxR5eF6audQuS_FQ
> [name=nonumpa]


### [Comm] assistive fact-checking via ChatGPT
> - Implementation https://g0v.hackmd.io/@cofacts/rd/%2F%40cofacts%2FrknFrmdk3
> - Research https://g0v.hackmd.io/mU8qi721RZeAQ9PDfj7XRA?both

- 關於 chatgpt 亂回，記錄在這：
https://g0v.hackmd.io/mU8qi721RZeAQ9PDfj7XRA?both#202346-Release-issues
- PR: https://github.com/cofacts/rumors-api/pull/303

### [Comm] Article group / surrounding text 相關圖文

> https://g0v.hackmd.io/@cofacts/rd/%2Ff_Ze19PhQuqx_fzOAOkohQ



## 內容 takedown

### 看似色情但好像是在回報網傳壯陽藥詐騙

兩人被檢舉
- https://cofacts.github.io/community-builder/#/editorworks?type=2&day=365&userId=j4S8C_b2Wx-tvf1fKEGtT3oBHO86AwcHqU3W2ILvsKpIy-s4I&showAll=1
- https://cofacts.github.io/community-builder/#/editorworks?type=2&day=365&userId=j4S8C_41VGEhobOKgQ_Yf7wX_B74dC9XCJ8bq2T3lKCZfv_U8&showAll=1

分析
- 同時回報了「漢方顧精堂」文字與 logo
- 香蕉貼圖一樣

---

- 要下架嗎？他有遮 [name=mrorz]
- 他沒有遮。 [name=bil]
  - 放別人的不是放自己的，就有隱私問題 [name=bil]
- 把文字與 logo 回應成詐騙即可 [name=bil]

:::success
由於使用者應是在回報詐騙，故僅修改圖片（避免 Google 把我們鎖掉）、但不封鎖使用者
:::

### 疫苗陰謀論廣告

https://cofacts.github.io/community-builder/#/editorworks?showAll=1&day=365&userId=Ofn2PIcBn6k8q-JURn5i

- 沒有其他互動
- 被檢舉數次廣告投放

:::success
刪除該篇回應，不用封鎖
:::

### 對自身的廣告
https://cofacts.github.io/community-builder/#/editorworks?showAll=1&day=365&userId=EPwPv4YBC7Q3lHuUv0_f

- 洗版
- 廣告投放、洗版屬惡意文章散佈

:::success
封鎖 both
:::
