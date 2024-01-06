---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20211110 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：MrOrz, bil, nonumpa, 4000, cai
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API

https://github.com/cofacts/rumors-api/releases/tag/release%2F20211105

- Causes 5min downtime for chatbot, API & website on 11/05 ~1:00AM

## 小聚籌備

- 三人交集：11/21
- [x] 主題：感恩志工編輯小聚（感恩節 Thanksgiving）
- [x] 場地：[小樹屋](https://thehapp.com/space/267)
    - 捷運行天宮站 1 號出口，步行約 4 分鐘
    - 民生東路二段90巷4號1樓-101房
    - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1c36f1b5d2ff5be4ab073c070b2e44e0.png)
    - 租用時間：13:00 - 17:30（門鎖密碼在 12:55 時生效）
- [x] 食物 
    - 熱的燒仙草之類
    - Ubereats? @ggm :tada:
    - https://www.ubereats.com/tw/store/%E5%85%AB%E6%99%82%E7%A5%9E%E4%BB%99%E8%8D%89-%E6%9D%BE%E8%8F%B8%E5%BA%97/S1gfxwEaQBmQNMnSJba1ow [name=cai]
- [x] 時間：
	- 活動時間：14:00 - 17:00
	- 時間分配
        - 2:00 - 2:20 開場
        - 2:20 - 2:40 介紹 mission 1 - 按讚 
        - 2:40 - 3:00 進行評價 (20則)
        - 3:00 - 3:30 休息、自我介紹、交流 
        - 3:30 - 3:50 介紹 mission 2 - 寫回應
        - 3:50 - 4:30 進行回應（1則）
        - 4:30 - 5:00 介紹分類、RSS、合照
- [x] 投放目標：北北基桃
- [x] 事前產生 spreadsheet 25 人分工
- [x] KKTIX：https://cofacts.kktix.cc/events/cofacteditor27 先 publish
- [x] 誰會來呢：bil, mrorz, nonumpa, ggm
- [x] 做圖：Lucien :tada: - 推播前上傳圖片
- [x] LINE 文案：
真的假的 2021下半年的實體編輯小聚回歸！
2021年 11月 21日 (日))下午2點到5點
最近的捷運是行天宮站 1 號出口，步行約 4 分鐘
民生東路二段90巷4號1樓-101房
活動完全免費，邀請從來沒參加過的你一起來！

## Spammers

- jhon wanone
    - https://cofacts.tw/article/AVwB_30vyCdS-nWhuY1o
    - https://cofacts.tw/article/AWAG3C_syCdS-nWhuj7Z
- 林芭比
    - https://cofacts.tw/reply/VsNOA30BucwAqrbaE3Hh
        - 此訊息下有一個 articleReply

:::success
MrOrz add to https://github.com/cofacts/takedowns
:::

## rumors-ai data labeling

- 開發中：https://github.com/cofacts/rumors-api/pull/265
- codegen：https://g0v.hackmd.io/@mrorz/HyRr8DSDK
    - 是否要自動寫入手動標記？
    - 如果要，那要用什麼身份（userId、appId填啥）？
- 問題
    1. 如果 article A 已經有若水標的 category c1 & c2，有人標了 c3 且我們 review 完之後覺得應該加，那 article A 的 JSON 裡應該要是 c1, c2 & c3 還是只要 c3?
        - c1, c2 & c3
        - 透過 existing categories 欄位
    3. 如果 article B 有 AI 標的 category c3 但被使用者覺得是錯的、我們 review 完也覺得是錯的，那 article B 的 JSON 裡應該要是什麼？
        - 下一次產出 JSON 時 tags 裡不會有 c3

要不要使用一個比較兼容的格式
- `tags`: 「人」標的、我們看過覺得可以用的 tag
    - i.e. tag 的「結論」
    - 不含 AI 標記。
    - 當時若水 tag 有什麼特徵嗎 [name=mrorz]
    - 全都是 AI 標的，若水的 ground truth 沒在資料庫裡 [name=ggm]
    - 可以再把若水的 ground truth 批次塞成 articleCategory [name=mrorz]
        - 特別的 appId or userId

```JSON
{
  "createdAt": "2018-11-14T01:24:49.719Z",
  "hyperlinks": "",
  "id": "1pt6j5jf6s6dq",
  "reference": "LINE",
  "tags": ["lT3h7XEBrIRcahlYugqq"],
  "text": "自中國進口水壺蓋 太和工房被爆驗出殘渣值超標57倍",
  "url": "https://cofacts.g0v.tw/article/1pt6j5jf6s6dq"
}
```

- AI model 本身沒有記憶性，若水 ground truth 需要另外加
    - 加進去比較好 [name=ggm]

:::success
- ggm
    - 找若水的那包 ground truth
    - 改 predict script 拿掉 mapping
    - 把 docker 搬去 cofacts organization
- mrorz
    - 完成 script 1 & script 2
    - 設計 ground truth feedback

下週三 9:30 follow-up
:::
