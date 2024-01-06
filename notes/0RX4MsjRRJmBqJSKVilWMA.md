---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20210106 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：bil, nonumpa, mrorz, hsiao
:::

## 2021 一月 Planning
- 1/07 台灣吧說說 粗剪(要延期嗎？)
	- 可以延到 1/22 (五) 演講前晚上
- 1/13 前
	- Release landing page & 暫行版 CC BY-SA attribution 網站 & upgrade dialog
	- Staging：profile page & edit 收 feedback
		- qualitative feedback: 是否滿意呈現、是否受到鼓勵、是否揭露太多或太少 etc
		- 先問認識的編輯，再去社團問
- 1/13 (三) 下次開會
~~- 1/15 台灣吧影片上線~~
- 1/18 (一) license 會議
- 1/20 (三) 下下次開會 - 決定 license attribution & terms
- 1/22 (五) 台灣吧影片上線
- 1/23 (六) g0v 大松
- 2 月：公布新 terms 與 API license header
- 2/6 編輯小聚？
- 2 月底：enforce API license header

## 第 23 次小聚

- [ ] 主題：大過年的來闢謠
	- [2020](https://cofacts.kktix.cc/events/cofacteditor18)
	- [2019](https://cofacts.kktix.cc/events/cofacteditor12)
	- [2018](https://cofacts.kktix.cc/events/cofacteditor7)
- [ ] 時間：2/6 or 2/20
- [ ] KKTIX
- [ ] 準備貼紙
- 場地：NPO Hub 4 樓廚房 （台北市中正區重慶南路三段 2 號 4 樓）
    - Keyholder:
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

:::success
bil 先借場地
:::

## Downstream bot follow-up

### 有回報
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_861aff975bb3614838e846bcfc15f68c.png)

- 圖：![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f9dd1b488219c2e5542132ba62ed8b6c.png =x200) https://drive.google.com/file/d/1VSk4GrAhZarh5-_NcGyqAf74jpGxmAqN/view?usp=sharing 
- 標題：Cofacts 社群有人查到
	- 美玉姨用哪個 [name=bil]
	- ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_79e8eea146303dec741a605eb65a6011.png =x200) 
	- 美玉姨的是一致性的「查核者 OOO」但這更可能會被誤會為查核組織 [name=orz]
	- 希望使用者看到之後會認為不是「他人」社群，而是自己可以幫忙的 [name=bil]
	- 「Cofacts 的回應你來寫」[name=bil]
	- 「問問查核聊天機器人」[name=bil]
- 按鈕文字：查看 Cofacts 給予評價
	- 「給予評價」是希望使用者點入，但他不一定會做，整體流程會是在 Cofacts chatbot「查看 OOO」開始
	- 有「真的假的」不一樣，不用「給予評價」 [name=bil]
	- 「《真的假的》幫你確認」[name=bil]

:::success
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f9dd1b488219c2e5542132ba62ed8b6c.png =x200) 
問問查核聊天機器人
(內容)
《真的假的》幫你確認
:::

### 沒查到
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_58cf571ad454e7fed762ad2a55c07d66.png)

拿掉第一張卡片最下面的「回報給真的假的」，改成新卡片放旁邊？

- 圖： ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4e8820c46f63a3783c3d22facde22452.png =x200) 
https://drive.google.com/file/d/1oqZWMSAjsva7yHRVzaGGD72H1W-yzqOx/view?usp=sharing
- 標題：問問查核聊天機器人
- 內文：真的假的機器人有最大的資料庫，也會搜集新謠言，我平常都是問他的喔。
- 按鈕文字：回報謠言去

:::success
如上
:::

## LIFF share dialog proposal

### article & reply LIFF
- 內容
    - 在 LIFF 裡呈現被回應的訊息、以及特定回應（或所有回應），以取代第三方 bot 利用「`📃 查看這篇的回應`」的機制。
    - 針對回應，提供 feedback 按鈕、分享按鈕
    - 針對訊息，提供「我想補充」功能
    - 功能類似網站的 article page，但用 LIFF 實作，可以用 LINE 使用者身份操作，無需登入 Cofacts 網站
        - 若沒有開過 Cofacts LIFF，還是會先跳出 consent window
            - 但 consent window 完之後就會進入 LIFF 功能，比帶入「📃 查看這篇的回應」還要自己按送出還直覺
            - 但此 consent window 可以帶入說加 Cofacts 好友
        - 技術細節
            - LIFF query 參數：`articleId`, `replyId`
            1. LIFF Javascript [持 LIFF SDK 提供的 id token 與 LINE bot GraphQL 溝通](https://github.com/cofacts/rumors-line-bot/blob/dev/src/liff/lib.js#L42)
            2. [LINE bot GraphQL 驗證 id token 為 LINE 發送，取得 LINE ID](https://github.com/cofacts/rumors-line-bot/blob/dev/src/graphql/index.js#L49-L66)
            3. LINE bot GraphQL server 在 resolver 內持 LINE ID 與 x-app-secret 與 Cofacts API 溝通
- Entry points
    - 美玉姨列出 Cofacts 回應下的「看完整回應」按鈕 --> 打開此 LIFF
    - 防詐達人列出 Cofacts 回應下「看看 Cofacts 怎麼說」 --> 打開此 LIFF
    - Cofacts「看過的訊息」LIFF 點按訊息 --> 打開此 LIFF
    - Cofacts 回報新訊息（[新流程](https://github.com/cofacts/rumors-line-bot/issues/214)）後的「查看訊息」按鈕 --> 打開此 LIFF
    - *(optional)* 讓電腦環境也能使用，這樣就能直接分享此 LIFF 的 URL，使用者點開之後進行 LINE 登入，方可使用包含 feedback 在內之所有功能。

> 在 LINE 裡面跳出 LIFF 視窗
> 會嚇到人
> 不然會以為是廣告或是中毒
> [name=bil]
> 
> 那可能用在第三方 bot 解決使用者不知道要按送出的問題就好
> [name=mrorz]

### Share 卡片
- 內容：flex message card
    - 很少的訊息片段
    - 回應節錄
    - 「查看細節」按鈕，打開上述 article & reply LIFF
    - 「分享」按鈕
    - [Google analytics beacon image 偵測閱讀裝置數](https://hackmd.io/@taichunmin/slide-coscup-2020#/41)
    - **傳到任何聊天視窗（Cofacts, 第三方聊天群組之外），都可以收 upvote / downvote / 我想補充 etc 並且追蹤看過的裝置數**
- Entry points
    - Cofacts 群組訊息的回應
        - 讓群組裡的人直接分享出去
        - 出處那些收在卡片「查看細節」裡，比較不會打擾群組對話
    - Cofacts article & reply LIFF 的分享按鈕，分享後的內容
    - Cofacts Share 卡片的「分享」按鈕，分享後的內容
    - *(optional)* Cofacts 內詢問回應之後，也跳出這個卡片，不再於 LINE 跳出整篇文字
        - 引導使用者透過分享按鈕，分享整張卡片，方便計算 impression
        - 注意：**過去「長按轉傳」的分享方式將不復存在**！
        - 如果有人想要節錄回應內容、稍加修改之後再貼，他還是可以點進 article & reply LIFF 之後，自行複製貼上自己想要的文字


> share 卡片之後，連結應該不能塞在卡片裡 [name=nonumpa]
> 可以，不過我覺得 LINE 裡面維持在 LIFF 比較好，可以收互動；網站的話他要登入網站 [name=mrorz]
> 但也不一定要他登入，例如說看其他回應 [name=nonumpa]
> 那也是可以用 [LINE login --> 網站的整合方式](https://developers.line.biz/zh-hant/docs/line-login/secure-login-process/#using-access-tokens)
> 不過我想 LIFF 最後也可以直接顯示複數個回應，在 LINE 上取代 article page 的作用，拿掉不適合在 LINE 進行的功能（如撰寫新回應）、LIFF 本體就以 LINE 上的 UX 為主來設計 [name=mrorz]

:::success
開票～
:::

:::spoiler 提案全文備份
> 我回家的過程中突然有個爆炸性的想法，可以解決「收不到回應有用沒用」的問題，也可以解決送出訊息的問題——使用 LIFF。
>
> LINE 的 LIFF 其實是可以在 chatbot 之外的其他 LINE 聊天視窗開啟的。
所以我們可以準備一個 LIFF 是顯示回應、出處、「覺得有用」「覺得沒用」「分享」「加 Cofacts 好友」等等大按鈕。「覺得有用」「覺得沒用」按下去就會打 Cofacts LINE bot 與 LIFF 對接的 GraphQL API，去跟 Cofacts API 溝通；「分享」「加 Cofacts 好友」則是相對應的 LINE URL scheme。
>
> 對美玉姨或趨勢科技來說，他們只要把 LIFF URL 設定成按鈕的 URI action（可能要把 articleId, replyId 透過 URL param 傳進 LIFF），使用者在在 card 下面的按鈕按下去的時候，就會打開這個由我們設計的 LIFF。
>
> LIFF 做好之後，甚至我們可以學國家災害防救科技中心的那個可以分享的 card 來呈現我們自己的回應以及 LIFF 按鈕，這樣當我們的回應從 Cofacts bot share 出去（或透過群組 bot 呈現）時，看到回應的人也能點按鈕進到同一個我們設計的 LIFF，計算訊息的真正影響力。
> 這樣一來
> - 對美玉姨與趨勢科技防詐達人來說，與 cofacts bot 的整合難度一模一樣，且難度遠小於直接 call Cofacts API
> - 對 Cofacts 來說，我們可以完全控制 LIFF 內的呈現方式，要求分享、求回饋、求加好友，在 LIFF 裡面可以完全自理
> - Cofacts bot 自己也可以在群組功能裡，吐出的回應包含這個按鈕，打開同一個 LIFF；或者是 Cofacts bot 一對一聊天的分享功能，就是會用 share target picker (國家災害防救科技中心的 card 背後用的 API) 吐一個包含此 LIFF 按鈕的 card 出去
>
> 是個 downstream bot 與 Cofacts bot 多贏的局面呢
> [name=mrorz]
:::


## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API
[DIFF](https://github.com/cofacts/rumors-api/compare/5632c4532c11b30dd160c4dfab9adea500250d3c...c2ff8f2c8f7221bf431fb760438d09b01a8e6608)
- #240 CC BY-SA license header
- #241 expose user's `appId` field

:::info
`LICENSE_URL` 尚未設定
:::

### :rocket: Staging

##### Deployment
- Need to add `LICENSE_URL=https://github.com/cofacts/opendata#terms`

#### :globe_with_meridians: Site

- #356 landing page
- #366 og-image
	![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_56c5a563de2a8747d5293787ad286026.png)
- #364 CC BY-SA notice
    - [ ] 使用者條款連結 --> 另外有 hackmd 
    - [x] License 連結 --> https://github.com/cofacts/opendata#terms
- [#365 Upgrade dialog limitation](https://github.com/cofacts/rumors-site/pull/365)
	- 已知問題：會落後 1 次送出
- [#371 Landing page SEO](https://github.com/cofacts/rumors-site/pull/371)

##### 未竟項目

- landing page header 多了底線 [name=nonumpa]
	- https://www.figma.com/file/zpD45j8nqDB2XfA6m2QskO/Cofacts-website?node-id=994%3A111
	- 底線好像是原生外觀 很多地方都有 [name=hsiao]
- landing page menu 變白的時機太晚 [name=nonumpa]
	- 目前是算 100% 螢幕高 [name=hsiao]
	- 建議用 [intersection observer](https://developer.mozilla.org/en-US/docs/Web/API/Intersection_Observer_API) [name=lucien]
- Landing page 在 desktop 的 logo 剛載入的時候會看到 mobile 版 icon [name=nonumpa]
	- 可能要改用純 CSS 實作才能避免 [name=mrorz]
- [nice to have] 當 landing page menu 背景變白之後，可以使用有橘色放大鏡（？）版本的彩色 logo [name=nonumpa]

:::success
開票紀錄
https://github.com/cofacts/rumors-site/issues/377
:::

#### :robot_face: LINE bot
- Changed to `heroku-20` stack
- #236 CC BY-SA support

##### Deployment
- New env var: `LICENSE_URL=https://github.com/cofacts/opendata#terms`

### :eye: Under review

#### :globe_with_meridians: Site
- #367, #374, #368, #369, #375, #373 User profile page display & edit
