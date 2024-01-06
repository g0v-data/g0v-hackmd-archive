---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20220727 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis 出席：bil, mrorz
- 線上出席：nonumpa
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :eye: Under review
- https://github.com/cofacts/rumors-api/pull/289

## 小聚檢討

- [20220724 Cofacts 真的假的 31st 小松果](/PPczQa-9Q8ay0ZHwdp997g?both)
	- 14:00 開場、介紹
	- 15:10 讓大家進行我想補充
	- 15:20 自我介紹 —— 15:26 就介紹完了 XD
	- 15:35 開始介紹撰寫新回應
	- 15:55 講解個人意見
	- 16:05 撰寫新回應
	- 16:30 講解小鈴鐺
	- 16:41 拍照
- [新投影片](https://docs.google.com/presentation/d/1N9DxoN1NuxdtQILkcV67y_q8EM8CJF5GhoYLcCKFpAc/edit)
    - 投影片有什麼地方太長太短嗎 [name=mrorz]
    - 等於是提早 20min 結束ㄌ [name=mrorz]
    - 有提到個人貢獻圖，但可以加講列表，回來看其他人對自己回應的評價 [name=mrorz]
    - community builder bignum 可以新增「我想補充」的數字

## Image support
> https://github.com/orgs/cofacts/projects/9

- 寫 test 這兩天可以寫完 [name=nonumpa]
    - 之後再看一次 state 有沒有重複的行為
    - 之後再檢視 context 裡的 sessionId, searchedText, selectedArticleText
- Documentation 預計怎麼做
    - 想放在 Media-manager Wiki https://github.com/cofacts/media-manager/wiki
    - 一篇講 [Media indexing big picture](https://g0v.hackmd.io/bhL6csQ8T1e81E2De7ZS5Q#Search-with-similarity) & [hashing technique (hamming space)](https://g0v.hackmd.io/xsDcMPySQM69vA0xHO8_dA#%E5%9C%96%E7%89%87-Hash-%E6%95%88%E6%9E%9C%E8%88%87%E6%90%9C%E5%B0%8B)
    - 一篇講 Related work (基本上就 [opendream's approach](https://github.com/cofacts/rumors-line-bot/issues/7#issuecomment-890709756))
    - 一篇講 [Cofacts media manager 實際選用技術 ＆ design alternative](https://g0v.hackmd.io/C8dW2cFiR1-N5Z0wcOefuA#Processing-images)、 [hash length determination experiment](https://g0v.hackmd.io/LHhF_VQ1RdS12C0k0ESQ_Q) ([另一篇](https://g0v.hackmd.io/lkGJU4TpQ7evxDoXYK1rtQ#%E5%9C%96%E7%89%87-hash-%E6%95%88%E6%9E%9C))
    - Readme 更新 usage、補上圖與圖說
    - Typedoc 產生 API reference 文件放到 github pages

## Trend and contribution
> https://github.com/orgs/cofacts/projects/10

- https://github.com/cofacts/rumors-api/pull/289
    - unit test
    - 正確性驗證 with production data
    - Migration 資料 quota 試算
 