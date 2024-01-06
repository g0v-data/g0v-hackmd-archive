---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20211208 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis 出席：bil, mrorz, nonumpa
- 線上出席：cai, 4000
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API
https://github.com/cofacts/rumors-api/releases/tag/release%2F20211203
- Expose blockedReason
- Category review spreadsheet generation

#### :globe_with_meridians: Site
https://github.com/cofacts/rumors-site/releases/tag/release%2F20211204
- Set blocked user's cookies

### :eye: Under review
- Script 2 of category review https://github.com/cofacts/rumors-api/pull/272

Reviewed categories:
https://docs.google.com/spreadsheets/d/1Y9FrI01in2hz5eiveGknH0HE081sr7gVuk0a7hqqKuc/edit#gid=1990197018

## 大松籌備

- 誰會到 bil, 
- 徵人：
    - 對公投訊息有興趣的人
    - 1. 寫公投相關訊息的回應
    - 2. Review 公投相關訊息的標記
    - 3. 看看 category 投影片有沒有需要改進的地方
    - 工程師做編輯教學？
        - 先不要，沒人寫編輯教學的文案 [name=mrorz]
- 場地不一定適合工作 [name=bil]

## 公投與 Category 教學

Draft: https://g0v.hackmd.io/rf0A7MRfTOC613QZmFehQA#TODO-items

- 介紹 category 與公投的關係
- 各公投與 category 的 mapping
- 訂閱教學
- 連到撰寫教學
    - 寫得不夠好 --> 回應原始訊息，不是回應別人的回應！
    - 太進階先不要 [name=bil]

## Category 改名
From discussion: https://g0v.hackmd.io/TEbULkjbSE-3GDyk-Whj2A#Category-review-milestones

- 藏 category: 希望藏但沒空做 QQ [name=mrorz]
- 免費訊息詐騙 --> 假優惠、假投資、假工作、網路詐騙
    >
    > 目標編輯：
    > - 詐騙受害者
    > - 警政署 165 反詐騙等主管機關
    >
    > 此分類蒐集詐騙貼圖、假行銷手法等訊息。
    >
    - 「假優惠等網路詐騙」
        - 假優惠跟商業活動也有重疊 [name=cai]
        - 會變成標記者要先預判這是不是詐騙，不是的話才丟去商業活動，對人跟 AI 都滿困難的 [name=mrorz]
    - 「網路詐騙」 [name=mrorz]
    - 「詐騙」 [name=nonumpa]
        - 「假博士詐騙」這種被人標詐騙怎麼辦？[name=mrorz]
        - 但好像換成比較長的標籤名字，也沒辦法阻止政治狂熱份子亂標另一個立場的人「詐騙」。 [name=mrorz]
        - 在 review 時擋掉ㄅ，AI 不要學壞就好 [name=mrorz]
    :::success
    「詐騙」
    :::
- 中國影響力 -->
    > - 目標編輯：
    > - 關注中國動態的人或政黨，如台灣基進、時代力量、促統黨、新黨。
    > - 關注兩岸與資訊戰的學術單位。
    >
    > 兩岸三地、疆獨藏獨相關事件的消息，或來自中國官方的論述、對中國事務全然正面的描述等疑似為大外宣一環的訊息。
    - 現況：很多訊息內沒有中國相關東西（如國內的政治口水），被某些人「懷疑」是中國在散佈的訊息，就被標成「中國影響力」了。
    - 「中國影響力」很抽象。中美貿易戰算中國影響力ㄇ？[name=bil]
        - 比較像「跨國互動」 [name=mrorz]
    - 「中國外宣」 --> 具體、不會讓人亂標，但有縮 scope
        - 上海最新的垃圾處理場 像是內宣，會放在中國影響力但可能不是外宣 [name=mrorz]
    - 「中國宣傳」 [name=mrorz] 「中國政治宣傳」[name=bil]
        - 但這樣香港國安法之類的不確定要怎麼標，要看看具體例子⋯⋯
    - 希望讓熟悉中國的人訂閱並且回覆。大外宣或對中國的批評，這些人應該都熟悉，所以可以標 [name=mrorz]
    - 「華語文化圈」 [name=bil]
        - 受眾包含香港外國華僑、新加坡馬來西亞，影響看得懂華語（但可能不太熟其他語言）的人 [name=bil]
        - 一些針對僑民的訊息，例如美國某城市治安變很差、被偷少於多少錢竊盜不成案的訊息，可以猜測背後是誰在散佈，但好像是在美國的人比較容易回，跟原本中國影響力的目標編輯不太一樣 [name=mrorz]
    :::success
    中國政治宣傳
    :::
- 政治、政黨
    > 目標編輯：
    > - 各政黨支持者與反對者
    > - 政治從業人員
    >
    > 針對國內政黨或政治事件的批判或護航之論述。
    - 會標美國的政治訊息「政治、政黨」[name=bil]
    - 當時給[若水的範例](https://docs.google.com/spreadsheets/d/1xKiqli1Sal-QOaTKlSHKtMKfZnbYpQGHgFXrGjxNmAc/edit#gid=1089726768)是國內政治口水就是了
    :::success
    台灣政治、政黨
    :::
- 「台灣政治宣傳」
    - 李淳對台灣開放萊豬、何美鄉說團膳排除萊劑不是雙標 是台灣政治宣傳嗎 [name=mrorz]
    - 政治宣傳最常引用學者對政策的意見或研究，所以算ㄛ [name=bil]
        - 學者對政策的意見比較像政論 [name=cai]
    - 但這個又好像應該標「台灣政治、政黨」[name=mrorz]
    - 或者縮到「台灣大外宣」[name=bil]
        - 「台灣好棒棒」 [name=cai]
        - Taiwan No.1 [name=nonumpa] [name=cai]


## 編輯教學

- [常見錯誤回應樣態](https://g0v.hackmd.io/6mTYVWhLSTWfDcyaxYLaXA#%E5%B8%B8%E8%A6%8B%E9%8C%AF%E8%AA%A4%E5%9B%9E%E6%87%89%E6%A8%A3%E6%85%8B)
- header 的「討論區」換成「教學」（ https://cofacts.tw/tutorial?tab=bust-hoaxes ）
    - https://github.com/cofacts/rumors-site/pull/464
- 初次進入的教學
    - 偵測使用者 < Level 1 且按下「闢謠」時跳出 dialog 邀請去看[教學](https://cofacts.tw/tutorial?tab=bust-hoaxes) [name=mrorz]
    - 更多的教學連結 in editor
- 告知編輯之後會怎麼呈現這些回應
    - From: https://g0v.hackmd.io/TEbULkjbSE-3GDyk-Whj2A#%E7%B6%B2%E7%AB%99%E6%95%99%E5%AD%B8%E7%9A%84%E5%95%8F%E9%A1%8C
    - Fancy 版：如 LINE business manager 群發訊息的 Preview 功能
    - 正常版：小聚教學裡面的箭頭示意圖
        - 這個應該就 OK [name=mrorz]
    - 多個回應時會怎麼顯示
- 已經有回應時，叫使用者回訊息而非別人的回應
    - 應該是因為line 那邊寫 「如果你對這則訊息有不同看法，歡迎到下面這裡寫入新的回應：」這點 [name=cai]
    - 提示使用者「其他人不會先看到你想回的回應」
        - 直接在編輯欄那邊用灰字寫請針對原始訊息寫 [name=cai]
    - 送出時再次 confirm「這是針對訊息原文的回應」？
        - 可以看關鍵字再跳 confirm [name=mrorz]
        - 研究這類回應別人回應的人會用啥關鍵字 [name=bil]
    - https://github.com/cofacts/rumors-site/issues/463
- tutoal「是什麼」白底區域放台灣吧影片 https://github.com/cofacts/rumors-site/issues/462

:::success
整理成 issue
:::

## Category review update

> 這個 script 2 最後預計會產出的 tags 就是 list of string (category ID in Elasticsearch) 而非數字唷
> 跟之前開會時提到的一樣
> 再麻煩 GGM 協助改 AI 的 training & prediction script 來兼容這件事情了

- 訊息裡只有地點的，在疫情的當下是指疫情，但疫情過後可能沒有用 [name=nonumpa]
    - 人標成疫情相關對編輯確實是有用的，所以讓 AI 學到這個應該可以 [name=mrorz]
    - 但疫情過後可能要排除 [name=nonumpa]

