---
tags: edu, aray
---

# ARAY: 專案議題分類 (Project Category)

## 說明

> https://github.com/g0v/aray/issues/29
> 看起來這部分是比較屬於有一套分類架構，或許用詞上更適合「影響力類別、議題分類」等用詞
> 英文：category
> 中文：影響力類別、議題分類 .. 等用詞
> 擴充方案：待確認，例如 2020 出現的「防疫」，如果重要程度已提升至「影響力類別」，那麼要如何提出、確認
> 若採用上述方案，就可以讓「標籤」一詞，用於較為彈性的標註
> cheweiliu

>關於專案議題的分類，個人認為可以用專案之「**相關單位**」、「**相關技術**」來分類 (結合現有 UI 構想可參見此 [簡報](https://docs.google.com/presentation/d/1dSjegiYOGDMti9LFQGgQXLdr_njvQa9G8LrrpyGYP1k/edit?usp=sharing) )，和 bess 討論後建議可放進共筆中：
>
>考慮到 g0v 的專案內容可能包含很多面向，在定義與歸類標籤比較難清楚劃分。以 [原本的分類法](https://github.com/g0v/awesome-g0v) 為例，若搜尋「立法」或「視覺化」，會發現相關的專案分佈多個標籤，這些性質相似的專案雖然標籤不同，但在處理的事務或技術上可能有互相借鏡、整合之處。
>
>若改用專案之「**相關單位**」、「**相關技術**」來分類，好處是上述性質相似的專案會自動篩選成一組；且單位組織與軟體技術都有現成分類，無論時事如何演變，依然會有對應單位與技術且變化不大，只需定期做一下滾動式調整即可。
>
>承接 cheweiliu 的提問，以近年興起的「防疫」專案《口罩地圖》為例，相關單位可能是「衛生福利部」、相關技術為「資料視覺化」(視情況可複選)。用現有之單位與技術框架篩選，可以有效分類並找到類似性質的專案，就無需為定義新標籤的準則而傷腦筋。
>
>如果對應單位非單純只有 **政府**，那麼還有 **NGO**、**民間社群** 等選項可以勾選；若是與 g0v 基礎建設有關，則可以勾選民間社群的「g0v」選項來歸類。
>
>**可能遇到的問題**：雖然用單位與技術較容易分類專案，但各選項具體要如何劃分，才可有效分類專案又不會太籠統or瑣碎，這部分在實作上還可以研究看看，或許可以保留讓使用者自行新增選項，定期做滾動式調整。
>ArK

> John: 我覺得"相關單位"與"相關技術"可以加入，但是對於初來乍到的人，我覺得很難找到想要的東西，例如想找醫療相關的專案，除了打字搜尋外，是無法輕易用分類來搜尋。
> - 標籤
> - 議題
> - 相關單位 
> - 相關技術 
> 我覺得四者是可以並存

> 回覆 John:
> 謝謝認同~說到關鍵字搜尋，或許可類似 Google 設計時間篩選條件，會有助於新手找到近期較熱門如「防疫」相關的專案。 ("專案活躍度"也能有類似效果)。
> ArK

> John: 在“令人驚奇的零時政府”裡面的活躍度是用 Github Issue/PR 和 Hackmd 的更新來做 https://chunyenhuang.github.io/awesome-g0v-projects/#/
> 把這點子用在議題/標籤很不錯 https://github.com/g0v/aray/issues/45

> chewei 建議也許標籤可以用 SDGs (1-17) 
> 議題讓專案自主 tag
> 其他相關單位或相關技術可以並存
> 這樣就變成：
> - 標籤（SDGs）
> - 議題（專案自主定義）
> - 相關單位（政府相關單位）
> - 相關技術（程式語言）

```
chewei: 
延續 SDGs 的 17 項目標，我想提議，回顧公民科技與專案的推動經驗中，建議新增「行政制度變革與民主治理」這個類別作為第 18 個目標
SDGS-1-終結貧窮
SDGS-2-終結飢餓
SDGS-3-健全生活品質
SDGS-4-優質教育
SDGS-5-性別平權，例如 Herstory
SDGS-6-乾淨飲用水
SDGS-7-人人可負擔的乾淨能源
SDGS-8-良好就業和經濟成長
SDGS-9-工業化、創新及基礎建設
SDGS-10-消弭不平等
SDGS-11-永續城鄉，例如 Disfactory
SDGS-12-負責任生產消費循環
SDGS-13-氣候變遷對策
SDGS-14-海洋生態
SDGS-15-陸域生態，例如 tbbca
SDGS-16-和平、正義和公平的制度
SDGS-17-全球夥伴關係
建議新增-SDGS-18-行政制度變革與民主治理，例如 總預算視覺化、vTaiwan、立法院相關專案、投票指南、太陽花學運相關專案 等 (edited) 
```

```
Ark:
好奇問，SDGS-16 與某些類別如 SDGS-10、SDGS-18 部分重疊，可用複選的方式分類？
另外 SDGS 是聯合國定的議題分類，g0v 的專案若不在這些類別中，也可考慮用「其他」類別來囊括。 (edited)
```

```
chewei

複選+1
名稱用詞我覺得可以用「行政制度變革與民主治理」，作為第 18 個類別，輔助標註者標記
———
類別的新增機制，例如提議者以具體專案，至 aray 頻道提議詢問，討論 18 個類別之外還有沒有需要新增
例如「新聞小幫手」，會適用 1～18 哪一些類別呢？ (edited) 
```

```
Ark
「新聞小幫手」要處理的是社會面「虛假消息」的問題，但就沒有被 SDGS 列入，我認為主要的原因是，聯合國匡列 SDGS 是想聚焦"部分"全球面向的議題，而非要把公民社群的"全部"專題做歸類。出發點跟層面有所不同，因此會遇到難以歸類的情況。
```

```
chewei
看起來可以以新增類別方式處理？
是否新增「19 新聞與訊息 (字詞待確認)」，用於標記例如 真的假的 linebot、新聞小幫手、0archive 零時檔案局 (edited) 
是否新增「20 開放資料與開源文化」用於標記例如 資料申請小幫手、 CC 授權小幫手、開源星手村桌遊 (edited) 
```

## 標籤來源

- https://docs.google.com/spreadsheets/d/1C9-g1pvkfqBJbfkjPB0gvfBbBxVlWYJj6tTVwaI5_x8/edit#gid=1563040282
- https://github.com/g0v/awesome-g0v

## 標籤

ex: 公營服務（基礎建設、健康與醫療、教育與研究、服務要求與陳情）


| 名稱 | 說明 | 其他註記 |
| -------- | -------- | -------- |
| g0v 基礎建設 Infrastructure |      | Awesome 分類 |
| 開放資料、開放政府 Open Data Open Gov |      | Awesome 分類 |
| 社會參與 Social Engagement |      | Awesome 分類 |
| 新媒體 Media |      | Awesome 分類 |
| 政策共筆 Policy Feedback |      | Awesome 分類 |
|   |      |      |
|   |      |      |
|   |      |      |
|   |      |      |

以下嵌入的試算表網址為
https://docs.google.com/spreadsheets/d/1C9-g1pvkfqBJbfkjPB0gvfBbBxVlWYJj6tTVwaI5_x8/edit#gid=1553521133
<iframe src="https://docs.google.com/spreadsheets/d/e/2PACX-1vT0oqWKBwSjyUo5k9uPTJItYkSpxZmpz0QFH65myqXasM9K7ldzuEY1eN6lGElTKlz52TozB94Os7oG/pubhtml?gid=1553521133&amp;single=true&amp;widget=true&amp;headers=false" width="100%" height="600"></iframe>

## SDGs

> Chewei:
> 週五前我來嘗試用以下 137 個專案，來嘗試標記前面大家討論的 20 個影響力類別，看看有沒有什麼標記課題
> https://docs.google.com/spreadsheets/d/1C9-g1pvkfqBJbfkjPB0gvfBbBxVlWYJj6tTVwaI5_x8/edit
> 開始標註～
> 20 個影響力類別，與 137 個專案
> 例如：Aray 專案，我先標記「20-開放資料與開源社群基礎建設」
> https://airtable.com/invite/l?inviteId=invkv7bbVxaAT0wlX&inviteToken=7cc70ddbff7a9f2ef80125ff7bb436ac5ff085feba1314d5ded8e40494f69a9e&utm_source=email
> https://airtable.com/shrHT6ylhRFHqOdfv
> 先用 141 個專案進行標記 20 個影響力類別，標記過程中的選入條件，我目前筆記於頁面中，類別允許複選
1-SDGS-終結貧窮，數量 3
2-SDGS-終結飢餓，數量 3
3-SDGS-健全生活品質，數量 21
4-SDGS-優質教育，數量 16
5-SDGS-性別平權，數量 1
6-SDGS-乾淨飲用水，數量 1
7-SDGS-人人可負擔的乾淨能源，數量 1
8-SDGS-良好就業和經濟成長，數量 5
9-SDGS-工業化、創新及基礎建設，數量 1
10-SDGS-消弭不平等，數量 1
11-SDGS-永續城鄉，數量 15
12-SDGS-負責任生產消費循環，數量 1
13-SDGS-氣候變遷對策，數量 1
14-SDGS-海洋生態，數量 0
15-SDGS-陸域生態，數量 6
16-SDGS-和平、正義和公平的制度，數量 3
17-SDGS-全球夥伴關係，數量 6
18-行政制度變革與民主治理，數量 21
19-新聞訊息與媒體識讀，數量 6
20-開放資料與開源社群基礎建設，數量 38 (edited) 
> https://app.awesome-table.com/-MnVz4_I6B5OzsFZUcaq/view
> 
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_68886f1747d36b23cec088f31907514e.png)
