---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20210901 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：mrorz, bil
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :globe_with_meridians: Site

[20210901 Release](https://github.com/cofacts/rumors-site/releases/tag/release%2F20210901)

- #445 Unify all "reference" title logic


### :rocket: Staging

#### :robot_face: rumors-line-bot

- #281 Turn URLs in reference section into hyperlinks 
- #283 Refactor: FeedbackForm use vote (enum) instead of deprecated score (1 | -1)
- #282 Article LIFF with feedback submission

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [x] 送出「有回應」的舊訊息，應自動回傳回應
    - [x] 應列出訊息所有的回應
    - [x] 選擇回應之後可以幫回應 upvote
    - [x] 可以再次選擇 downvote
    - [x] 選完回應之後，還可以捲回去選其他回應
- [x] 用 LINE 造訪 article LIFF（多回應）- https://liff.line.me/1563196602-X6mLdDkW?p=article&articleId=2gvs0nu9ynjo7
    - [x] 可以 upvote 沒 vote 過的回應
        - [x] 用桌機看[同一 article](https://dev.cofacts.tw/article/2gvs0nu9ynjo7) 可以看到自己的回應
    - [x] 可以 downvote 沒 vote 過的回應
        - [x] 用桌機看[同一 article](https://dev.cofacts.tw/article/2gvs0nu9ynjo7) 可以看到自己的回應
    - [x] 可以把 upvote 的回應改成 downvote 的
- [x] 用 LINE 造訪 article LIFF（單回應） - https://liff.line.me/1563196602-X6mLdDkW?p=article&articleId=3tu9btf8s50sm&replyId=ArnghHkBpYB_rtUxsxtQ
    - [x] 可以正確顯示單一回應

##### ⛔️ Release Blockers

可 release

##### 未竟項目


###### TODO before GA
:::info
要做完下面的東西才通知其他 bot 說可以上了
:::

- Link to website (article page & tutorial)
- Cofacts闢謠志工 --> 「真的假的」闢謠志工
- 「這則 cofacts 回應」--> 「真的假的回應」

###### GA 後再說

- Cofacts logo as favicon? https://engineering.linecorp.com/en/blog/liff-our-latest-product-for-third-party-developers/
    - 可以考慮在「查核回應」title 也放一個 cofacts logo，讓標題更清楚 [name=mrorz]
- 按「修改評價」時載入之前寫的評價內容
    - 不然使用者按「關閉」就會洗掉之前寫的評價文字
- 很多回應的時候會有點像是文章列表 [name=bil]
    - 「此訊息有 3 個查核回應」不太明顯
    - 一則回應的時候很好

### :eye: Under review

#### :robot_face: rumors-line-bot

- #281 Turn URLs in reference section into hyperlinks 
- #283 Refactor: FeedbackForm use vote (enum) instead of deprecated score (1 | -1)
- #282 Article LIFF with feedback submission

## Article LIFF

Target: receive input (feedback, reply requests) from outside of Cofacts chatbot

https://www.figma.com/file/DvmAQjMJCncuPORWKnljM1/?node-id=3004%3A224
1. [x] 實作 common component storybook
2. [x] 實作 feedback form + 使用在目前的按鈕上
3. [x] 實作 article page 的 article 部分
4. [x] 實作 article page 的 reply
5. [ ] 實作 article page 的其他回應連結、cofacts 網站連結 `Before GA`
6. [ ] Google analytics + `utm_source` (影響到 URL 整合，要先說) `Before GA`
7. [ ] 載入使用者自己的 feedback
8. [ ] 列出其他人的的 feedback
9. [ ] 實作 article page 的 reply request form + 使用在目前的按鈕上
10. [ ] 實作 article page 的 reply request list
11. [ ] 實作 article page 的 related article

本週開發：article reply data feedback 送出邏輯



### LIFF HTML 被 cache 住的問題

- 更新 LIFF 之後，點入打開 LIFF 的按鈕，會卡在「Loading」
- Rollbar 會收到「js 找不到」的 error
- 可能原因：更新 LIFF 後 js 檔有換名字，但 LINE 內建瀏覽器 cache 住了 HTML（內有舊名字）卻沒有 cache 舊的 assets
- 可能解法：不要 cache html https://developers.line.biz/en/docs/liff/overview/#liff-browser-cache
    - cloudflare 不會 cache HTML ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_65e017b0dac8fdf2cad901cb2ad7fee3.png)
    - 但我們的 chatbot server 確實是會對 liff 下的每一個檔案（包含 html）下 cache ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b799f3879b193f25568660be0d3d6b6a.png)
    - 可能在 serve HTML 時特別加上不要 cache 的 header
    - 或直接刪掉 `maxage`，讓 cloudflare 來 cache 就好
        - Cloudflare on CSS: ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a2a81a84daabe978e9db75061407e75b.png)

:::success
直接刪掉 maxage 設定，用 cloudflare 就好
:::

## 26th 小聚籌備

[前次小聚檢討](https://g0v.hackmd.io/ie1Ymj_3SlmHp0jAIy6mJw#%E5%B0%8F%E8%81%9A%E6%AA%A2%E8%A8%8E)

- [ ] 主題：26th 柚子、優酪乳與香蕉編輯小聚
    - 中秋節前後
    - 經典謠言
- [ ] 時間：9/25
	- **活動時間：14:00 - 16:00**
	- 時間分配
        - 2:00 - 2:20 開場
            - 放影片可，但要
                - 開麥克風才有聲音
                - 只分享一個視窗且拉小一點，否則畫面會有一塊不動
        - 2:20 - 3:00 進行評價 (20則)
        - 3:00 - 3:20 介紹工具
        - 3:20 - 4:00 進行回應（1則）
- [ ] Jitsi 50 人
- [ ] 投放目標
    - 60% 報到率，預計到場 30 人
    - 上次投放：![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e2e657535c77c1b681ac947ca6b51583.png) ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0c4e8937ea7d8420265ddfc93e430ac2.png)
        - 目標 10 萬人
        - 5 萬人在活動前一天晚上打開訊息
        - 2 千人在活動前一天晚上點進連結
        - 報名人數 50 人全滿
        - 實際進入聊天室約 20 人
        - 7/22 + 7/23 約 2,000 人封鎖，但 7/28 (一周內) 好友數就回來了
    - 目標 All - 北北基桃 約 10 萬人
- [ ] 如何 50 人分工：
    - 提供 spreadsheet
- [ ] KKTIX：
- [ ] 誰會來呢：
- [ ] 誰不會來
- [ ] 做圖：
- [ ] LINE 文案：

## 在同一篇重複引用已經回過的回應

> 發現一則在同一個訊息下面重複引用別人回應的回應，雖然看起來高機率是誤用，但可能也要考慮之後會不會有人故意用這種方式洗 credit
> https://cofacts.tw/article/3v74tlg49nudw
> [name=nonumpa]

- 「使用現有回應」已經會 dedup by reply ID [name=mrorz]
    - 但這個 case 是，reply 作者自己複製貼上回應在很多 article 下，所以有很多 reply 長得一樣，但卻有不同 reply ID
    - 可能可以考慮用內文判斷，如果此訊息下已經有很像的回應，就跟使用者確認一下
    - 判斷直接做在網站即可

:::success
開票紀錄上述機制
:::

## 採訪共筆

9/15 前交

https://docs.google.com/document/d/1J8EVhWkJxHkRkRuoatfQRTQF_ZAPkCkf/edit

:::success
MrOrz 回信說 9/13 Monday
:::

## [慕哲政經塾](https://future.org.tw/civicrm/event/info?reset=1&id=92) 參與者 QA

- 一個假消息的補充、查核，如何成案
- 就是我在網站上的回覆，要經過什麼程序才會變成機器人回覆的內容
- 相同的假新聞出現，網站可以自動抓取比對嗎？
- 現在很多軍公教群組都會把機器人當成敵人，這種問題有辦法解決嗎？😮‍💨
- 我剛剛看到2017的假新聞，又被散佈出來
- 請問「Cofacts真的假的」和「MyGoPen賣擱騙」有什麼不同嗎？
- 承上，有些假消息可能已有學者專家專文寫作或者在mygopen已經有專文查核。我在cofact如何查核闢謠？ 直接貼上網址，或者原文直接搬過來？（但通常原文都很長）
- 好奇平台上協作查核或補充的使用者人數，有在什麼事件（新增某功能/某時事影響）後，出現顯著成長嗎？還是比較偏向一直以來穩定線性成長的趨勢？
- 假使有些消息，比較偏向政治傾向的爭辯，平台會怎麼處理呢
- 不好意思，我想請問一下，幫忙闢謠的人員會不會因為某些立場而呈現出一些偏頗的訊息?
- 我有聽過長輩認為機器人 或那些闢謠的平台，的背後資源是某些特定政黨支持，所以才對那些平台有敵意
- 補充一下，是有謠言散播者會說這些都是蔡陰文的洗腦工具之類的XD 
- 所有訊息必然有立場，人工或machine learning的 編輯的角色是協助交叉比對，有的消息有標準答案．可能相對簡單。但尚未有標準答案或「訊息多樣卻有立場差異」的訊息，怎麼來確認？有時候就不是真的假的，而是閱聽人看到的不同，剛講到真的假的用很多大家按讚 浮現到上面，那人海戰術的按讚大隊出現時，如何處理？

## 真的假的 <> 防詐達人

- Update 開發進度
- GA ready 時給正式網址
