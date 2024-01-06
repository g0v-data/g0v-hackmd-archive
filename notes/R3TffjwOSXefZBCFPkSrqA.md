---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20201014 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：
:::

- RSS 教學
    - [x] 完成[投影片](https://g0v.hackmd.io/TfCHhvtFTLmP0YKmaU1yVA)
    - [x] [UI「進階教學」文案](https://g0v.hackmd.io/GhVhBlK_QwKT3E5clAfkJw?both#Cofacts-Next-%E8%BF%BD%E8%B9%A4)
    - [ ] 實作[新 UI](https://www.figma.com/file/zpD45j8nqDB2XfA6m2QskO/Cofacts-website?node-id=3146%3A324) - 文武
    - [x] 完成影片   [請改腳本](https://g0v.hackmd.io/TfCHhvtFTLmP0YKmaU1yVA?view)
        - 已上 staging
        	- 需要把 embedded player 的 title 那些藏起來
        - LINE - https://youtu.be/jKDllYf9bFQ
        - Slack - https://youtu.be/G5sUpDhzjR0
        - TG - https://youtu.be/PgsjQHgEnyQ
        	- 背景音效有點忽大忽小 [name=nonumpa]
        	- 可以用 compressor 壓壓看，讓動態範圍變小一些，比較不那麼搶 [name=mrorz]
    - [ ] FB 教學
    - [x] 觀察 RSS 使用率 - https://datastudio.google.com/reporting/18J8jZYumsoaCPBk9bdRd97GKvi_W5v-r/page/hN8iB
- 推播
    - [x] [修正 LIFF title](https://github.com/cofacts/rumors-line-bot/pull/226)
        - [x] 更換 rich menu 字樣 
    - [x] Rich menu 教學 - [文案](https://g0v.hackmd.io/yEp9JJtHSyK18bxCQV4dUg#Rich-menu-%E4%BB%8B%E7%B4%B9)
        - [x] 志超教學圖用來主頁
        - [x] LINE 的「歡迎訊息」
        - (Rollbar) LIFF 裡面每天好像有什麼 cursor error，應該要看一下 [name=nonumpa]
    - [x] 觀察 [Rich menu 使用率](https://datastudio.google.com/reporting/18J8jZYumsoaCPBk9bdRd97GKvi_W5v-r/page/DtzfB)
    - [ ] 啟動推播功能（見下）
- User ID refactor: https://github.com/orgs/cofacts/projects/8
- Profile page
    - [x] Related APIs 
    - [x] UI components (shared with detail pages)
    - [ ] `/user/[id]` page
    - [ ] Edit name / photo UI
- Landing page, 教學頁, final report
    - [x] 教學頁 [mobile design](https://www.figma.com/file/zpD45j8nqDB2XfA6m2QskO/Cofacts-website?node-id=2011%3A0) done
    - [ ] 設計 final report
    - [ ] 實作

## 推播上線

- [8/12 討論](https://g0v.hackmd.io/eitM7s0bSSeS3kg-MAcpDw#Cofacts-Next-%E8%BF%BD%E8%B9%A4
)
	- Migrate 時先讓所有使用者都關閉
	- 新使用者依然會自動開啟
	- 送新訊息時，要多問使用者是否要開啟 ( [rumors-line-bot#217](https://github.com/cofacts/rumors-line-bot/issues/217) )
- 現況
	- `allowNewReplyUpdate: false`: 89,102  人
	- `allowNewReplyUpdate: true`: 5,693 人
		> 跟 [20200909](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/%2F5JMzChJOQPqKe_CX_wbRmg) 剛 migrate 完 `userSettings` 比起來，多了 4000 多人的 `allowNewReplyUpdate` 變成 `false`。
	- `userSettings` 總共 94,794 個 document
		> 有效好友 14 萬，代表有很多人完全沒跟 chatbot 說過話⋯⋯
    - 實作 #217 的 PR：https://github.com/cofacts/rumors-line-bot/pull/228
- 計畫
	- env vars 設定見 https://g0v.hackmd.io/eitM7s0bSSeS3kg-MAcpDw?both#-Chatbot
	- 預計設定每天中午 12:30 執行 notification。
	- Buffer 可以再久一點 --> 換成 24hr [name=bil]

## User ID refactor 上線

- [x] Merge [migration script PR](https://github.com/cofacts/rumors-api/pull/226)
- [ ] Test using DB backup
- [ ] Prepare SOP
- [ ] Merge API PR (for new users)
- [ ] Merge [API PR](https://github.com/cofacts/rumors-api/pull/227)
- [ ] Perform SOP on staging, measure time spent
- [ ] Announce maintenance period on FB & Slack
- [ ] Perform SOP on production

## Chatbot highlight & matching improvement

- Highlight improvements：https://g0v.hackmd.io/-j-fAX0tS62amv9LejshOg#-Chatbot
	- 可能要讓 client 設定 highlight snippet 長度
	- 增加 more_like_this 要查的字，增加查詢時間但也增加 recall / sensitivity (敏感性) & 更好的 highlight
- Matching:
	- 因為有了 highlight，chatbot 比對的標準可以低一點 [name=bil]
	- 「看起來 N% 像」可能要考慮網址的字等等 [name=mrorz]
		- 現在 mygopen, TFC 也會顯示相似度 [name=bil]
		- 加上「文字 N % 像」太長了，應該可以不用解釋 [name=bil]
		- 那這個 part 就保留 [name=mrorz]
- 推廣
    - 還沒發文感謝斌綸的 highlight

:::success
開票:
- Better highlight (API side) https://github.com/cofacts/rumors-api/issues/229
- Lower chatbot threshold (chatbot side) https://github.com/cofacts/rumors-line-bot/issues/53
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :globe_with_meridians: Site

[10/09 release](https://github.com/cofacts/rumors-site/releases/tag/release%2F20201009)

- Favicons & banner
- `<Card>` related items

#### :electric_plug: API

[DIFF](https://github.com/cofacts/rumors-api/compare/e611d5c2b1e10a18b87e5a951f73bd2ab39f10ee...77f009788e5f011eb1a8acf7a56d5d1ebc5a6208)

- #225 Similar replies API

### :rocket: Staging

#### :robot_face: LINE bot

##### Feature
- Hint user to turn on notification to get updates #228

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [x] 應可送出「全新訊息」
    - [x] 問訊息來源時選擇「我自己打的」或「LINE 外面看到的」，應該會被擋下。
    - [x] 提供正確訊息來源後跳到理由頁面，關掉理由視窗，訊息應該還是有被送出。
    - [x] 可從聊天視窗內打開理由視窗，繼續填寫理由送出。查看 article page 看理由是否有被送出。
    - [x] 可以修改理由送出。查看 article page 看理由是否有被送出。
    - [x] （若沒開啟推播）應該要看到「開啟小鈴鐺」泡泡，且可打開 setting 頁面
    - [x] 「分享到 Facebook」、「分享到 LINE」可以正常運作

- [x] 送出「沒回應」的舊訊息，應可送出新理由
    - [x] 跳出來源視窗後關閉，文章的「N 人回報」應該仍然要 + 1（除非測試者已經針對該篇送過 reply request）。
    - [x] 提供正確訊息來源後跳到理由頁面，關掉理由視窗，可以看到「提供更多資訊」按鈕，按下去可以再打開「理由」視窗
    - [x] 可從聊天視窗內打開理由視窗，繼續填寫理由送出。查看 article page 看理由是否有被送出。
    - [x] 可以修改理由送出。查看 article page 看理由是否有被送出。
    - [x] （若沒開啟推播）應該要看到「開啟小鈴鐺」泡泡，且可打開 setting 頁面

- [x] 送出「有回應」的舊訊息，應自動回傳回應
    - [x] 應列出訊息所有的回應
    - [x] 選擇回應之後可以幫回應 upvote
    - [x] 可以再次選擇 downvote
    - [x] 選完回應之後，還可以捲回去選其他回應
    - [x] （若沒開啟推播）應該要看到「開啟小鈴鐺」泡泡，且可打開 setting 頁面

##### 未竟項目

發現有[空的回應](https://dev.cofacts.org/article/vrx238h5nyvd)，會跳出 [Error](
https://rollbar.com/mrorz/rumors-line-bot/items/268/occurrences/138327930510/)
> 已有 [ticket](https://github.com/cofacts/rumors-line-bot/issues/212)[name=nonumpa]

----

:::danger
注意：deploy production / staging 後要手動更新 LIFF URL！否則 bundle URL 會被 cache --> https://rollbar.com/mrorz/rumors-line-bot/items/214/
:::

#### :electric_plug: API

[DIFF](https://github.com/cofacts/rumors-api/compare/77f009788e5f011eb1a8acf7a56d5d1ebc5a6208...c678c946517685dd8b0a6764a0bd9af295a71def)

- migration script to create backend users referenced in the db #226

因為是 migration script 所以應該不會有任何影響；
不過 code 裡頭有些修正 elasticsearch API 呼叫之處。

:::warning
確認：
應該可以在沒跑 migration 的狀況下先上？`fetchStatsFromGA` script 這樣可以ㄇ？

- 應該沒差，只是多紀錄東西，所以可以上 production [name=zoe]

:::

#### :globe_with_meridians: Site
🈚️


### :eye: Under review

#### :electric_plug: API
- index user if not existed and log last active time for user accessing apis via backend apps #227


#### :globe_with_meridians: Site
- Reply detail page and side section #349


#### :robot_face: LINE bot

