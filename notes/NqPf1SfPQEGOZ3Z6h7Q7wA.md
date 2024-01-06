---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20201209 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：bil,orz, 彤, Lucien ,文武
:::

## g0v summit 後續

Any insight from [Jamboard](https://jamboard.google.com/d/1tAfSDd8hUvKXT8VnS1ljnvLvkJ24YIsslgbztdgviok/viewer?f=0)? (已改為唯讀)

「還有另外一種說法」像是在回應個人意見：提供另外一種可能

:::success
> 感謝您的分享😊 剛剛這則訊息，我查過似乎發現有點問題。有另外一種說法是：......
> 
> 所以總之先附和～ [name=bil]

:::

(加在前面我的話)
假的。

- wording 設計是 for 含有錯誤訊息的，所以其他不會回應 [name=bil]
	- 需要是「含有不實訊息」
	- 醫療保健等 category
	- upvote >= downvote
	- 總回應數為三個以上且回應中有「含有真實訊息」的也不在群組裡回應
- 含有個人意見有些干擾，如：https://cofacts.g0v.tw/article/pqz37mki7qi9 [name=bil]
- 如果有很多回應，就選讚數多的那則 [name=bil]
	- 有人覺得正確覺得不正確的話，很可能是有爭議的訊息 [name=nonumpa]
	- 這裏是只希望回應錯誤的訊息，而且不處理政治 [name=bil]
	- 如果是健康相關的研究，可能還沒有定論 [name=nonumpa]
	- 那可能可以看回應很多（三個以上之類）的時候就不要回應也可以 [name=bil]
:::success
回應的訊息要符合以下條件
 1. 訊息原文分類在醫療保健等 category
 2. 取讚數最多的回應且要是錯誤訊息且 upvote > downvote (有效查核應該不能 upvote = downvote)
 3. 總回應數 < 3 或 總回應數 >= 3 且 ~~沒有其他type~~ 含有錯誤訊息數量 >> others (>25%)
  
 - [name=nonumpa]
:::
## Editor UI discussion
> 前情提要：[1202 小聚檢討](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/%2FvErWoVXYRTKnxpID610C-A) 的「網站 UX」

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_589e7da823636595ed42c4c96009caae.png)


### 引導編輯

`140 字以內` -->

- NOT_ARTICLE:
	請簡單說明為何 Cofacts 不該處理這則訊息
- NOT_RUMOR:
	請簡單說明它哪個部分是正確的，作為「資料來源」的導讀
- OPINIONATED:
	請簡單說明：
	- 它哪個部分含有主觀意見之處
	- 提醒讀者這不是客觀事實
- RUMOR: 請簡單說明不實之處，作為「資料來源」的導讀

Note: iOS Safari 不支援多行，但 Pixel Phone 可以
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ec6aa557a8949ad2b0e265c6778026b4.png)

:::success
Tracked: https://github.com/cofacts/rumors-site/issues/360
:::

### Reference 用語

> chatbot, website editor 與 reply display 的 wording 應該要一致。

- 其他：`References` / 資料來源 / 參考資料 / `資料佐證` / 出處
	- 資料佐證比較好 [name=bil, lucien]
	- 「資料佐證」好像比較有權威性 [name=bil]
- 個人意見：`Opinion Sources` / 意見來源 / `不同意見出處` / 不同觀點
	- 「不同觀點」會不會讓編輯誤會說要放觀點本文，而不是連結 [name=mrorz]
- `超連結與連結說明文字` : multiline placeholder
    ```
    來源說明
    » 連結網址
    
    One line summary
    » Source URL
    ```

:::success
Tracked: https://github.com/cofacts/rumors-site/issues/362
:::


| Desktop | Mobile | 
| -------- | -------- |
| ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_612288e8743d57b9170d09425fea8fe6.png) | ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_dd078f68147efd51b38f31bca152310c.png) |

### 一鍵模板

#### 不在查證範圍

- 長度太短 / 文字太短，像是使用者手動輸入的查詢語句，不像轉傳訊息。
- 商業促銷 / 這是商業活動廣告。
- 無查證需要 / 訊息與謠言查證無關。
- 聊天 / 送出文章的人在嘗試與機器人聊天。
- 意見回饋 / 對 Cofacts 真的假的的建言。
- 無意義測試 / 測試用之無意義訊息。
- 連結失效 / 連結已經失效，無法查證。

#### 含有個人意見

> - 不想要刪掉「⋯⋯」 [name=bil]
> - 可以讓高級 user (lv10+) 不會有「⋯⋯」 [name=lucien]
> - 我自己不太用，都自己打 [name=mrorz]
> - 我會用尚無共識 [name=lucien]
> - 這些模板應該是不太熟的時候用的，熟了之後應該就不會用 [name=nonumpa]

- 陰謀論 / 這個訊息含有無法查證的陰謀論，因為
- 滑坡謬誤 / 含有滑坡謬誤，因為
- 尚無共識 / 社會尚無共識。
- 個人價值 / 純屬個人價值觀，並非客觀事實。

:::success
問社團有沒有人在按「含有個人意見」的模板～
:::

### mobile / desktop

Breakpoint 設定有誤，mobile 與 desktop 版中間有一個出處沒有標題的版本：

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7a650fa0654e0df850badd851fb0c489.png)

:::success
開票: https://github.com/cofacts/rumors-site/issues/363
:::


### 搜尋改進
https://github.com/cofacts/rumors-site/issues/295

#### 使用現有回應 & 插入回應
- 「搜尋」常常找不到；即使都翻出了 article / reply，也只能用內文關鍵字搜尋
- 「我的回應」不會只列出我的回應
- 「全部的回應」可能會列出已被刪除的回應

#### 插入回應

https://www.figma.com/file/WmBIfHODsc9XMJXliXDg9E/New-editor-proposal?node-id=0%3A1

- "Keep composing my reply with this" / 「延伸此回應來查核」--> Insert this reply / 插入此回應
- 把列點按鈕改成插入區塊
    - 貼圖 | + 插入現有回應
    - 點擊「+ 插入現有回應」時顯示 dropdown 與 input box (auto focus)
    - 自動在理由的最下面展開自己的回應，blur 時不會消失，多一個「關閉」可以按
    - 顯示插入的時候隱藏資料來源視窗(因為選完之後，出處也會一併插入)，使空間變大

> 1, 2, 3 與 bullet point 用意比較像是在導引 [name=lucien]
> 目前不會用是因為 1. 很難搜到 2. 按下之後不會複製 reference [name=bil]
> 那或許先修好這兩個比較優先，UI change 再說 [name=mrorz]

:::success
先 fix https://github.com/cofacts/rumors-site/issues/295
UI 先不動
:::

## Migration

> - 改userId 的 migration https://gist.github.com/ztsai/f9445bb45bfa145a329fcfad51519346 [name=zoe]
> - 改avatarType 的 migration https://gist.github.com/ztsai/acc9c723b4254d2f31114c4959a2dfdc [name=zoe]


- 公告：12/11 1:00am 要 migration，下線至 2am
- staging 先測時間
	- ~4000 items processed for `fixBackednUserIds`, took < 3mins on localhost
	- ~1788 items processed for `fixAvatarDataTypo`
		- 要 iterate through 60000 users
		- took 12 mins
		- 居然有 1700 個 LINE 使用者有 MajesticHandlebars lol
- Migration ：reverse SSH tunnel 接到資料庫操作
    - [x] 準備 script 放在 rumors-api 的 `src/scripts` 下
    - [x] docker-compose 關閉 nginx 使 Cofacts 下線
    - [x] 備份資料庫
    	```
		# See progress
		$ curl db-ip:9200/_snapshot/gcs/_current?filter_path=snapshots.*.state,snapshots.*.stats
		```
    - [x] 建立 reverse SSH tunnel
    	```
		$ ssh -N -L 62222:db-ip:9200 root@server
		```
    - [x] 確認 .env 內的 ELASTICSEARCH_URL 指向 ssh tunnel 開啟的 port
    - [x] `npx babel-node src/scripts/fixBackendUserIds.js`
    - [x] `npx babel-node src/scripts/fixAvatarDataTypo.js`
    - [x] 關閉 reverse SSH tunnel
    - [x] docker-compose 開啟 nginx

## Dialogflow 設定

> [Intent design](https://g0v.hackmd.io/kWuTnoC1TG-MONPhxp8rGQ#2020-Q4--2021-Q1-%E9%80%B2%E5%BA%A6%E7%A2%BA%E8%AA%8D)
> 參考資料(limited access)： https://datastudio.google.com/u/0/reporting/64c3b474-a306-40f5-86b9-2e894d028da6/page/lijmB
> - 問題類：請問(xxx)、(xxx)什麼(xxx)、資料庫…
> - 無意義類：謝謝、好的、了解、OK、測試、天氣、你好、國家、人名…

## AI4SG

https://aiplus.systex.com/ai4sg-award/

Form: https://docs.google.com/forms/d/e/1FAIpQLScoGrNMW_H5HotSf4oawwEzPIDnNi6VWkSlYyDF3kvDdMcwYA/viewform

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_adfed7b8ac48d2a352f83c29db64e51d.png)


- 報名截止時間：即日起至2020年12月21日（一）中午12時

## 開放授權變更

CC0 --> CC-BY-SA

### 時程

- 先拿掉 CC0:
	- hackfoldr(「你的文字將不屬於你」)
	- github opendata repo 改成 CC BY-SA 4.0
- 預告某個時間轉換
	- 2020/12/31
	- 2021/1/1 0:00 以後的資料就是 CC BY-SA 4.0
	- FB group
- 修改網站使用者條款來取得同意
- 改登入框、編輯加入「登入時，視同您同意網站使用者條款、CC BY-SA 4.0授權」
- 轉換時間到：正式公告

:::success
mrorz 發 opendata repo 的 PR
https://github.com/cofacts/opendata/pull/19/files?short_path=b335630#diff-b335630551682c19a781afebcf4d07bf978fb1f8ac04c6bf87428ed5106870f5

改 hackfoldr:
- 編輯入口：https://beta.hackfoldr.org/1yXwRJwFNFHNJibKENnLCAV5xB8jnUvEwY_oUq-KcETU/https%253A%252F%252Fhackmd.io%252Fs%252FSyMRyrfEl
- 中文首頁： https://beta.hackfoldr.org/1yXwRJwFNFHNJibKENnLCAV5xB8jnUvEwY_oUq-KcETU/https%253A%252F%252Fhackmd.io%252Fs%252FByXgboon-
- 英文首頁：https://beta.hackfoldr.org/1yXwRJwFNFHNJibKENnLCAV5xB8jnUvEwY_oUq-KcETU/https%253A%252F%252Fhackmd.io%252Fs%252FBJSdbUMpZ
- 使用者須知：https://beta.hackfoldr.org/1yXwRJwFNFHNJibKENnLCAV5xB8jnUvEwY_oUq-KcETU/https%253A%252F%252Fhackmd.io%252Fs%252FHkHpqVrxM

:::

### 修改 UI 告知

> Wikipedia 的編輯介面：
>
> 點擊發布變更後，表示您同意我們的使用條款。
> 同時您同意依據CC-BY-SA-3.0和GFDL條款授權您的貢獻，並在CC-BY-SA-3.0的條款下以超連結或URL的方式進行署名。

:::success
mrorz 列出要改的部分
:::

### 決定 attribution

:::danger
先想幾個
https://github.com/cofacts/opendata/pull/19/files?short_path=b335630#diff-b335630551682c19a781afebcf4d07bf978fb1f8ac04c6bf87428ed5106870f5
:::

:::success
mrorz 參考 wikipedia 來寫
:::

### 網站使用者條款

> 參考 Wikipedia 與其編輯有 Licensing of Content 條款https://foundation.wikimedia.org/wiki/Terms_of_Use/en

:::success
bil:
12/20 後（AI4SG 之後）
:::


## :potable_water: Release pipeline

### :star: Released to production
[DIFF](https://github.com/cofacts/rumors-api/compare/cffc41c24d05bba13e19becb7510f6013e6904fa...5632c4532c11b30dd160c4dfab9adea500250d3c)

- #232 user profile related api changes
- #235 List reply requests
- #238 fix typo in openpeeps json

### :rocket: Staging

#### :globe_with_meridians: Site

- #356 landing page

See landing page and test if it functions well
- Login --> goes to hoax-for-you
- Check if search works
- Check if article list works
- Works on mobile / desktop, logged-in / not logged-in
- Check what will a spider see
- og-image 要用哪張？

### :eye: Under review

#### :robot_face: LINE bot

- [#235 Dialogflow NLP](https://github.com/cofacts/rumors-line-bot/pull/235)
	- last comments before merge

#### :globe_with_meridians: Site

- #356 landing page
