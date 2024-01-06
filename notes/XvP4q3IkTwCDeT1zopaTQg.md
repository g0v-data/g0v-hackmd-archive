---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20210113 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：bil, hsiao, 文武, mrorz, nick, ggm
:::

## 影響力地圖
> bil
> 參考：https://g0v.hackmd.io/6w3TV_D2TCG501qkACEnog


## Profile page pilot study results 

成果：https://g0v.hackmd.io/lIedGsQWTeScBTWfr4Zq0w

### 進行狀態
- 訪問 4 人，完訪 2 人
### 建議
#### Usability
- 回應 sort by 最多人評價、瀏覽量最高 [name=二]
    - 可以透過 [nested filtered sorting](https://hackmd.io/dfAkGHLCShacnOoruGxr0w?view) 達成: filter 出該使用者的 articleReply、用 articleReply 的 `positiveFeedbackCount` 或 `negativeFeedbackCount` 或加總或相減來排序 
    - https://github.com/cofacts/rumors-api/issues/243
- reply type filter 應該也要加上 `userId` [name=三、1]
    - 目前是「列出 user 有回過、且有一個 reply type 符合要求的 article」
    - 但應該要是「列出 user 回成該 reply type 的 article」
    - [Related code](https://github.com/cofacts/rumors-api/blob/master/src/graphql/queries/ListArticles.js#L395-L444)
    - https://github.com/cofacts/rumors-api/issues/243
- 「編輯頭像」功能從頭像點進去 [name=三、2]
	- 右下角放一個小鉛筆按鈕，表示這裏可以編輯 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_44bc607f4524ab0e515fdd0b73b67f43.png =x200)
	- https://github.com/cofacts/rumors-site/issues/379
- 使得按 banner 上的數字也可以切換分頁 [name=三、3]
- 修好絕對時間 timestamp [name=三、6、a]
    - 目前 server render 的 `title` 是錯的，因為他會使用 server 的時區。或許可以改成 tootip，這樣就能在前端滑鼠移上去時再算？
    :::success
    Under discussion
    :::



#### Enrollment
- deploy 時先把點 reply 名字進到 profile 的功能 comment 掉，只有編輯自己可以從自己的選單進去；兩週後再補回此功能 [name=ㄧ、2]
 
:::success
Implemented in https://github.com/cofacts/rumors-site/pull/378
:::
 
#### 其他想法

- 等級高與等級低的差別 [name=bil]
	- 等級高可以看比較多的東西
	- 等級高可以選擇隱藏自己的東西
	- 考慮到 ㄅ 想公開給第三方看，但又有 concern
	- 提供類似「關閉 timeline」的選項


## Downstream bot 2020 數據

> MrOrz

目標：計算 Cofacts 回應在這些 bots 上的總影響力
影響力：「reply 曝光次數」or 其他的 metric

Reply 曝光次數：
| bot | 一月 | 二月 | ⋯⋯ | 十二月 |
| -------- | -------- | -------- | - | - |
| Cofacts     | 1,000     |  2,000     | | 1,000 |
| 防詐達人     | 1,000     |  2,000     | | 1,000 |
| 美玉姨     | 1,000     |  2,000     | | 1,000 |
| 總曝光次數 | 3,000 | 6,000 | | 3,000 |

- 是否有「點擊次數」？
- 是否有「人次」？


### 趨勢科技防詐達人


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f7dbc1b3a9d9fc9a0747bcb776020c13.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_961eaea5f4bdca4184111d6ecf4550a3.png)

:::success
MrOrz
- 問「文字假消息」的定義是 impression 還是 click
- 是總數還是含 Cofacts 的數字
:::

### 美玉姨
- 想去詢問 2020/1/1 ~ 2020/12/31 的回應的次數 (impression)、使用者選擇的次數 (action) [name=mrorz]
- 可能會沒有統計過，那就是已有統計的區間為準

:::success
MrOrz
確定趨勢科技有哪些資料之後，再去問美玉姨有沒有相同的資料

最後呈現在影響力報告時：
- 沒有交集的部分分開呈現
- 有交集的部分可以分開與加總呈現
:::
## 第 23 次小聚
- [ ] 主題：大過年的來闢謠
	- [2020](https://cofacts.kktix.cc/events/cofacteditor18)
	- [2019](https://cofacts.kktix.cc/events/cofacteditor12)
	- [2018](https://cofacts.kktix.cc/events/cofacteditor7)
- [ ] 時間：2/21（日）
	- **活動時間：14:00 - 17:00**
	- 場地借用 13:30 - 17:30 （上限 4hr）
- [ ] KKTIX
- [ ] 準備貼紙
- 場地：NPO Hub 4 樓廚房 （台北市中正區重慶南路三段 2 號 4 樓）
    - Keyholder: ronny
    - [ ] 場地單
    - [ ] 食物
    - [ ] 延長線 (場地有)
    - [ ] wifi
        - [ ] Nighthawk M1 + 4G sim
        - [ ] ASUS RT-N12 Wireless N300 (2x 5dbi高增益天線)
- [ ] 誰會來呢？
- [ ] 誰不會來
- [ ] 志超做圖
- [ ] LINE 文案：

## 翻譯
- 希望可以有其他語言的翻譯，翻譯大塊的文字成英語跟華文之外的其他語言（landing page） [name=bil]
- 新增一個版本 = 1~2% 記憶體 for whole site，所以翻越多越划算 (?) 因為都是加一台 server  [name=mrorz]

:::success
等英文翻完 tutorial
:::

## 海報

- 摺頁 40 塊，海報可以一直貼著 [name=bil]
- 海報貼在
	- 社區大學
	- 假清活動
	- 午營咖啡、剝皮寮、workis
	- 塞給地方人士 (R、alumni) 辦公室 / 服務區

:::info
等確定真的會海報
:::

## :potable_water: Release pipeline

### :star: Released to production

#### Nginx settings
- 拿掉語系自動判定 https://github.com/cofacts/rumors-site/issues/347

#### :robot_face: LINE bot
https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20210107

- #236 CC BY-SA support

#### :globe_with_meridians: Site
https://github.com/cofacts/rumors-site/releases/tag/release%2F20210107

- #356 landing page
- #371 Landing page SEO
- #366 og-image
- #364 CC BY-SA notice

### :rocket: Staging

#### :globe_with_meridians: Site

- [#376 landing page fix](https://github.com/cofacts/rumors-site/pull/376)
    - Fix「landing page header 多了底線」
    - Fix 「landing page menu 變白的時機太晚 」

##### 未竟項目
- desktop landing page 字全部小一級, mobile 不變 [name=nick]
- 「大家都想知道」太寬

:::success
Added to https://github.com/cofacts/rumors-site/issues/377
:::

### :eye: Under review

#### :globe_with_meridians: Site
- #367, #374, #368, #369, #375, #373 User profile page display & edit
- [#376 landing page fix](https://github.com/cofacts/rumors-site/pull/376)

## 影片

40 秒形象影片提案
1. for 老人
	- 但老人已經有摺頁了
2. for 核心使用者 / donor，呈現 impact，讓觀眾得到認同感、並主動參與

:::success
選 2 的方向
:::

現有影片
- shadow：加好友
- TWB：招募 chatbot 使用者，並且導向協作
- 闢謠編輯現身：編輯導向，大家都是一般人

目前沒有影片的內容
- top-down 的方式介紹 Cofacts 運作 (MIT solve or [hackfoldr 用文字介紹的東西](https://cofacts.org/hack))
- 包裝後的 impact，如 ecosystem 的介紹等等
	- 類似影響力地圖
	- 更接近廣告
- 產生認同 > 把人導向協作、導流 etc
	- 導向協作或導流的影片都有了
	- 看完產生認同後，會自己去找上面的影片來看，或是看網站

### 例：IFCN code of principles
{%youtube OVrx_2OYuTg %}


