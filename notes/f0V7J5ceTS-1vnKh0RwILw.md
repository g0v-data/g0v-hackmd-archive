---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20201223 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：bil, mrorz, hsiao, nonumpa
:::

## 開放授權變更

### Wording

> This work by "Cofacts crowd-sourced fact-checking community" is licensed under a Creative Commons Attribution-ShareAlike 4.0 International License.

> 本資訊由 "Cofacts 群眾查核社群"提供，以創用CC 姓名標示-相同方式分享 4.0 國際 授權條款釋出。

- 大家都可以參與：crowd-source / collaborate / 眾包 / 協作 / 群眾XX
（- 對象 = 即時訊息）
- 做的事情 = 提供查核 fact-checking / reality-checking / 查核
- 非特定人：community / 社群

Cofacts crowd-sourced fact-checking community
Cofacts 機器人 真的假的群眾查核社群

----

bil: 機器人呢？開發者的 attribution 呢
bil
 加上「真的假的」？
orz: 
- cc-by 通常沒有包含程式的部分，因為開放的是內容。
- Cofacts 程式是 MIT 授權，CC BY 開放的內容其實不包含程式碼，
- wikipedia 的 CC BY 也是 for 內容。
- github 也會列出 contributor。

nonumpa
加機器人會有點奇怪
是 chatbot 的部分
機器人不太適合跟資料扯在一起

orz
會以為是機器人的社群（？）
產出內容的是社群而不是機器人
不過 chatbot user 回報 data 是否算社群的一環。

bil
應該是，而且很重要
沒有他們資料量會下降、也沒有「覺得是否有幫助」的協作 feedback

也可以把查核拿掉，換成協作，不希望被認為是個查核組織

orz
"Cofacts 真的假的群眾協作社群"

bil
機器人。

orz
"Cofacts 真的假的群眾查核與 chatbot 協作社群"
群眾查核（instant message 的回報與複查） + chatbot 使用者的協作
- 即時訊息回報與ＯＯ
ＯＯ：解惑？查核？查證？核實？

"Cofacts 真的假的訊息回報與查證協作社群"

bil
看起來沒有科技感
公民科技

orz
AI
自動化
大數據
資料庫（database）
開放資料
資料集（dataset）
但科技的部分其實是 MIT 授權出去的 xd

"Cofacts 真的假的訊息回報 chatbot 與查核協作社群"
- [name=bil]++
(chatbot 社群是開發機器人的人 !== 查核社群)

"Cofacts 真的假的資訊回報與查核協作社群"

"Cofacts 真的假的訊息回報 chatbot 使用者與查核者協作社群"
- bil: 者太多了
- 聊天機器人

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3e4d58233d986c1ae8c92138e149642f.png)
「真的假的 聊天機器人 協作社群」
- 沒有「查核」（但有真的假的）
- 以為是做聊天機器人（技術）的社群？

:::success
丟去 slack / 編輯社群

@here 大家好～我們最近希望把資料的開放授權改成 CC BY-SA。由於 BY 署名的部分會彰顯在所有用到 Cofacts 資料的地方（參考[網站](https://github.com/cofacts/rumors-site/pull/364)、[chatbot](https://github.com/cofacts/rumors-line-bot/pull/236)），所以想要可以選一個好名字。

我們希望這個署名可以囊括 Cofacts 社群的下面的幾個概念，越多越好：

- 是大家都可以參與的，不是封閉的
- 是一群人，不是特定幾人
- 參與者包含回報訊息的人、替回應評分的人、以及闢謠編輯
- 做的事情：提供查核或不同意見
- 查核對象：即時訊息
- 使用到公民科技、自動化技術


有想到幾個 candidate：

🐊 Cofacts 群眾查核社群
🦒 真的假的 聊天機器人 協作社群
🐘 Cofacts 真的假的訊息回報與查證協作社群
🐪 Cofacts 真的假的訊息回報 chatbot 與查核協作社群
🐴 （大家想到的其他組合）

:::

### 編輯端
使用者條款：使用者同意我們，用上面的名義來開放資料
- chatbot 端 - https://hackmd.io/t2DSbtU9RsS8cNTi-uLtSQ
- website 端 - https://hackmd.io/mFSlWs4IQke_9RnFAOWlfQ

> by bil
> https://hackmd.io/xYCRvT6dQVi-k0ySgZYaLg
LINE bot 
> https://hackmd.io/UA0Mqo5ISyKH3yLPCC0YVA
> 網站

### 開發端

License 本文：https://github.com/cofacts/opendata#terms
所有開發者都要同意上述 terms。

- [Staging API](https://dev-api.cofacts.org) 已經啟用 x-accept-license
    - 不加 header 就不能用 API
    - 加了 header 的，就當成 developer 已經同意該 license 了。
- Staging LINE bot 加入 [CC BY-SA attribution](https://github.com/cofacts/rumors-line-bot/pull/236)
- Staging website 加入 [CC BY-SA notice & attribution](https://github.com/cofacts/rumors-site/pull/364)
- AI component rumors-ai 要改嗎？？@ggm @darkbtf

#### Downstream bots modification
##### 美玉姨

Nick：美玉姨的圖卡顯示
文案：

 Cofacts 裡沒有訊息時
圖卡顯示（給Nick)「傳給真的假的機器人問問看吧！」 - 
圖卡下方文字：他有最大的資料庫，也會搜集新謠言，我平常都是問他的喔
[（之前的 wording）](https://github.com/CarolHsu/rumor-checker/pull/39)

Cofacts 有訊息但沒回應 or 有回應：
圖卡顯示：「有更好的解答嗎？一起來回應吧！」
下方文字：回應平台是開放的，任何人都可以修正現有的回應。

Source: https://g0v.hackmd.io/vErWoVXYRTKnxpID610C-A?both#%E7%B5%90%E8%AB%96

CC BY-SA 標示——

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3e4d58233d986c1ae8c92138e149642f.png)

跟 Cofacts chatbot 一樣放在文字後，可以用小字 / 灰字，license 用中文全名或「CC BY-SA 4.0 授權條款」
- 重點是「授權條款」四個字讓人看懂是授權條款
- 只放圖沒人看得懂

##### 趨勢科技

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d4d5178e9c9729dc6adea06af968715b.png)

- bil: 個人不喜歡「看看 Cofacts 怎麼說」，美玉姨的寫法（真的假的 聊天機器人 協作社群）比較好

與美玉姨同，灰色小字、CC BY-SA 4.0 授權條款等字樣，放在文字後、按鈕前

#### Notify known data users about API breaking change

:::warning
等社群討論完 attribution name
:::

## Yegogo honeypot 討論

次數
https://github.com/cofacts/takedowns/tree/master/2020

:::success
先採現況（回報後跑 script）
:::

## 群組功能問題
 
- ga
   - 訊息不在有效的標籤內也 +1
   - 用 groupId 當 cid 
   		- cid = GA client id 欄位，讓 GA 分辨不同使用者，以前都放 user id
		- LINE 會給 有傳的人 user id 以及 group 的 id
		- 但因為沒有要追蹤是誰，放 group id 即可
   - 加一個 user scope 的 custom dimension 欄位記錄 source.type
   		- 可以加
   		- 其實也是可以拿 ID 的首字來看，user 會是 `U` 開頭，group 會是 `C` 開頭
- 如果太慢回應，Bot 回應可能不會在原訊息的下方，可能會讓人不知道它在回什麼
   - 沒有回覆的 api 可以用
   - 回應前面引用前幾個訊息內文
- 無法 tag bot
	- 偵測 “Hi Cofacts” 時自我介紹
		- 寫在置頂文章
		- 可以多加教學頁（網站）
- room message 要當成 group 嗎？不知道 room/group 功能差在哪...
	- 支援 room，行為跟 group 同
- 需要英文版 wording
   > 感謝您的分享😊 
   > 剛剛這則訊息，我查過似乎發現有點問題。有另外一種說法是：
   > 
    > Thank you for sharing “${slicedMessage}” 😊
    > I found that there are some disagreement to the message:
- API 會被一直問，需要做什麼處理嗎 ？ 10 字以內 skip?
	- yes
	- 跳過圖片
	- 不特別處理網址，一起送進 API
- 回應的訊息的條件微調
     1. (不變)訊息原文分類在醫療保健等 category
     2. (不變)取讚數最多的回應且要是錯誤訊息且 upvote > downvote (有效查核應該不能 upvote = downvote)
     3. 總回應數 < 3 或 總回應數 >= 3 且 ~~沒有其他type~~ 含有錯誤訊息數量 >> others (>25%)
- "出處"改成"參考資料"比較好? (測試群組功能時發現的問題)
  - 沒有出處的訊息 https://dev.cofacts.org/article/3nbzf064ks60d
  - 「資料佐證」 https://github.com/cofacts/rumors-site/issues/362 、 https://g0v.hackmd.io/NqPf1SfPQEGOZ3Z6h7Q7wA#Reference-%E7%94%A8%E8%AA%9E

## :potable_water: Release pipeline

### :star: Released to production

#### :globe_with_meridians: Site
[20201217 bugfix](https://github.com/cofacts/rumors-site/releases/tag/release%2F20201217)
"Add this reply" reference

### :rocket: Staging

#### :electric_plug: API
[DIFF](https://github.com/cofacts/rumors-api/compare/5632c4532c11b30dd160c4dfab9adea500250d3c...c2ff8f2c8f7221bf431fb760438d09b01a8e6608)
- #240 CC BY-SA license header
- #241 expose user's `appId` field

##### Deployment
- Need to add `LICENSE_URL=https://github.com/cofacts/opendata#terms`

#### :globe_with_meridians: Site

- #356 landing page
- #366 og-image
	![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_56c5a563de2a8747d5293787ad286026.png)
- #364 CC BY-SA notice
    - [ ] 使用者條款連結 --> 另外有 hackmd 
    - [x] License 連結 --> https://github.com/cofacts/opendata#terms


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_52af54db08f0c5966da06a8c53b8ec29.png)

nonumpa:
第一頁沒有按鈕，注意力反而會被 (1) (2) 吸過去
其他網站通常會有個明顯的 start

#### :robot_face: LINE bot
- Changed to `heroku-20` stack
- #236 CC BY-SA support

##### Deployment
- New env var: `LICENSE_URL=https://github.com/cofacts/opendata#terms`

:::info
網站、LINE bot：到 wording、terms 決定之後再上

API 可以先上，但 `LICENSE_URL` 可以在之後再設定（其他開發者不會覺得太趕的時間，與公告 open API 不一定要同時間，可以有個 grace period）
:::


### :eye: Under review

#### :globe_with_meridians: Site
- #357 openpeep avatar
- #365 Upgrade dialog 
- #367, #368, #369 User profile page display & edit