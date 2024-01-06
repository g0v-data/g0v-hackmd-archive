---
title: "User Story 空白模版 (Socialtext Style)"
tags: hackpad
---

# User Story 空白模版 (Socialtext Style)

> [點此觀看原始內容](https://g0v.hackpad.tw/mvxkbtlXlDf)

> 空白模版，請勿直接填寫，複製後貼到你的 hackpad
> [name=ET B]

> 對 hackpad 不熟悉嗎？這裡有詳細的教學：[空白模版使用方式](https://g0v.hackpad.com/QUrgIRJEpv4#空白模版使用方式)
> [name=ET B]


## 本模版使用說明


這份 user story 模版源於 socialtext 開發流程。這套流程的好處是，處在三個不同時區的 pm、dev、qa 可以遠端接力協作，因此，也很適合應用在開發團隊結構鬆散的 g0v 專案。另，如果有 design 加入的話，design 跟 pm 最好是同一時區，因為這兩位都是設定 high level scope 的人。流程如下：

### 籌備

> (應該要準備一些 kickoff 會議用的資料...?)
> [name=ET B]

-

### kickoff meeting

- 專案一開始的時候進行的簡短會議，時間約一個小時
- 會議的目的是決定要做什麼、誰來做，會議的產出就是這份 user story (sample: beautiful testing ch16)
- 與會者包括 pm dev qa 團隊的代表各一，如果要開發的是使用者看得到的東西，與會者會多一個 design
- 與會人數最多 4 人，最少兩人。兩人的狀況就是 dev + qa (實做組自己開會)
- 開會時，pm 先寫 level1 的 checklist，dev 會問接下來呢？如果失敗會怎樣？pm 接著回答下個步驟要做什麼，qa 聽完以後問這功能測試成功的定義是什麼？然後表示手頭上的資源有沒有辦法測……如此循環。最後 pm 要把文件修到手上資源可以測的程度
- pm dev qa 一起寫完 user story 以後，就表示專案「符合需求、可以開發、有辦法測」，這份文件就是一個三方契約，從此接替的人不管是不是原來的與會者，都只要照做即可

### 實做

- dev 在開發完的項目中打第一個勾
- qa 測試完以後，在該項目中打第二個勾
- pm 確認成品後，整行打勾表示 sign off
- 然後那個項目就可以 release 了
- 過程中有任何討論，可以在該項目底下 comment
- 如果出現新 feature 發想，移到下一階段的開發
- QA 新增 feature sample
    - [ ] if thief want to break in, sound alarm too
        - [ ] ...

以上內容由 au 口頭傳授，et 打字整理。

以下正文開始。


## Meta


### Summary

> why: 要解決什麼問題、為什麼要開發這個東西 (一段文字)
> [name=ET B]



### High Level Scope

> how: 要怎麼做才能解決上面說的問題 (幾句話)
> [name=ET B]

-

### Sample Use Case

> 誰會來怎麼用 (幾句話)
> [name=ET B]

-

### Prerequisites

> 要先具備什麼條件才能做這個 (optional)
> [name=ET B]

-

### Estimated Efforts

> 時間估算 (optional)
> [name=ET B]



## Spike

> 這是什麼東西？ QAQ
> [name=ET B]

> 就是之前已做過的單純測試可行性但不能直接重用的小規模成品連結
> [name=Audrey T]



## Mockup

> wireframe / mockup 抓圖，如果有互動功能，在圖片上面指出來
> [name=ET B]



## Spec

> 由 high level scope 衍生出的對話樹，寫使用者做一件事情的每個步驟 (使用者跟系統的互動) 
> [name=ET B]

> dev 開發完以後在行首加上 :ok: ( : 後面打  ok 再打 : )
> [name=ET B]

> qa 測完以後加上 :+1: ( : 後面打 +1 再打 : )
> [name=ET B]

> pm 驗收完以後整行打勾
> [name=ET B]

> deploy 後…如果全部 ~像這樣劃掉~ 會不會很爽？ XD
> [name=ET B]

> qa 發現不在 scope 內的新問題時，如果沒有這個真的沒辦法上線，則自己加 checkbox，不然就等下一階段的開發再說
> [name=ET B]


- [ ] ...
    - [ ] ...
    - [ ] ...
- [ ] ...
- [ ] ...


## Dev Journal

> 這個我也不知道是什麼… QAQ
> [name=ET B]

> 就是實作日誌，和 Spec 不連動
> [name=Audrey T]


