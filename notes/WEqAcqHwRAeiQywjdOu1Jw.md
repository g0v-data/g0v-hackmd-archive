---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20211215 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis 出席：bil, mrorz, nonumpa
- 線上出席：cai
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :globe_with_meridians: Site
https://github.com/cofacts/rumors-site/releases/tag/release%2F20211212


### :rocket: Staging

#### :globe_with_meridians: Site
##### Testing checklist
http://dev.cofacts.tw/

未登入下檢測：
- [x] Landing page 最上方 header 有「使用教學」且會導向到「查謠言」教學
- [x] 進入 Cofacts 後 最上方 header 有「使用教學」且會導向到「查核」教學
- [x] 影響力報告頁都是中文

登入自有帳號後檢測：
- [x] Article detail
  - [x] Should be all Mandarin
  - [x] 有回應的訊息，回覆時會告知這裡不是討論區
- [x] Can go to profile page on menu
    - [x] edit own name, bio, URL 介面應該是中文

##### ⛔️ Release Blockers

##### 未竟項目

### :eye: Under review
- https://github.com/cofacts/rumors-site/pull/465

## 大松檢討
- 場地非常適合 [name=bil]
    - 桌子夠大
    - 食物可以在場內吃
    - 廁所很近
    - 可惜下次不會在這個場地
- 讓第一次參與的人報成果很好 [name=bil]
    - 會覺得是自己的專案
    - 要特別提到要唱名
    - 不然會變成「這是今天的夥伴」然後說自己做的事情
    :::success
    繼續做～
    :::
- 準備學習歷程的高中生又變多了 [name=bil]
    - 可以好好把握
    - 應該要帶電腦

## 小聚

- [ ] 1/8 or 1/9
- [ ] 主題：
- [ ] 場地：
    - NPO Hub (1st priority)
        :::info
        Bil 會去問 1/8 or 1/9 是否有 NPO hub
        :::
    - [小樹屋](https://thehapp.com/space/267)
        - 捷運行天宮站 1 號出口，步行約 4 分鐘
        - 民生東路二段90巷4號1樓-101房
        - 1:30 開始借就好，很好佈置；~ 5:30
        - 缺少延長線
- [ ] 食物 
    - 熱的燒仙草之類
    - Ubereats
    - https://www.ubereats.com/tw/store/%E5%85%AB%E6%99%82%E7%A5%9E%E4%BB%99%E8%8D%89-%E6%9D%BE%E8%8F%B8%E5%BA%97/S1gfxwEaQBmQNMnSJba1ow [name=cai]
- [ ] 時間：
	- 活動時間：14:00 - 17:00
	- 時間分配
        - 2:00 - 2:20 開場
        - 2:20 - 2:40 介紹 mission 1 - 按讚 
        - 2:40 - 3:00 進行評價 (20則)
        - 3:00 - 3:30 休息、自我介紹、交流 
        - 3:30 - 3:50 介紹 mission 2 - 寫回應
        - 3:50 - 4:30 進行回應（1則）
        - 4:30 - 5:00 介紹分類、RSS、合照
- [ ] 投放目標：北北基桃
- [ ] 事前產生 spreadsheet 25 人分工
- [ ] KKTIX：
- [ ] 誰會來呢：bil, mrorz, nonumpa, ggm
- [ ] 做圖：Lucien :tada: - 推播前上傳圖片
- [ ] LINE 文案：

## 公投回應狀況
- 我有掃 analytics https://datastudio.google.com/u/0/reporting/18J8jZYumsoaCPBk9bdRd97GKvi_W5v-r/page/NrUQ [name=mrorz]
- 以前選前前 25 熱門訊息，2/3都是政治 [name=mrorz]
- 今年公投前 7 天，11/50 熱門訊息是政治 [name=mrorz]
- FB: reach 1499, 191 engagement, 10 shares
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5087ffc9c80275eb28322fc8a3377cf1.png =x400)
- 好像有一個新編輯


## 二次詐騙使用者

- Comment 廣告還有 [name=bil]
- 首次 block: https://github.com/cofacts/takedowns/blob/master/2021/1125-2nd-spam.md
- 有幾個確實 12 月仍然有上線
- 大部分 spammer 的 `lastActiveAt` 停留在 11 月 or 更早

## AI 現況
- 12/10 上傳 17,111 個 article https://github.com/cofacts/ground-truth/blob/main/20211210_17111.zip
- 包含 12/9 以前的 review result https://github.com/cofacts/ground-truth/commit/f163f191233de41e16b5ef2a25c3b064a8aff4d5
    - 感謝 cai 幫很多訊息標記準確的分類 :pray: 
- to GGM:
    - tag 放 category ID 而非過去的數字
    - 更新 AI

## 新分類？

- 求生類(目標編輯：消防隊，救難隊)  eg. 地震 山難 虎頭蜂 [name=cai]
    - 如果是新政策如開放山林，會放在新法規分類 [name=bil]
    - 虎頭蜂是農業局 XD [name=cai]
    - 地震這些是「災防」嗎，有些地震「預測」的又是氣象局了 [name=mrprz]
    - https://cofacts.tw/article/1n43kahxx8hl1 虎頭蜂處理的方法
	- https://cofacts.tw/article/3thmr76tqeozk 虎頭蜂的攻擊
	- https://cofacts.tw/article/3iotbzburtk5 地震時先打開大門？消防署破除7謠言
	- https://cofacts.tw/article/1rfb9yrq9zz89 地震常識．如居住大樓！先打開對外大門！走到電梯周邊
	- https://cofacts.tw/article/2b9lk7ym3yvte 瓦斯外漏
