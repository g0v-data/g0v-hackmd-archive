---
title: "動民主 2.0 設計概念 - 研究其他類似系統"
tags: hackpad
---

# 動民主 2.0 設計概念 - 研究其他類似系統

> [點此觀看原始內容](https://g0v.hackpad.tw/LtyupWZ8OzN)



## LQFB 設計概念

Liquid Democracy In Context, or, An Infrastructuralist Manifesto
[http://seed.sourceforge.net/ld\_k5\_article_004.html](http://seed.sourceforge.net/ld_k5_article_004.html)

### recommendation

- 列出你相信的人他們支持哪些提案，或者他們的意向（正反論點贊成否、建議支持採納否）
    - [ ] 如果可以顯示目前 effective delegate list 對於此議案各方案的態度 可能就不錯 / clkao
    - [ ] 通訊錄成員的最新動態（facebook activity side bar）
    - [ ] 推薦通訊錄成員所參與的議案


## BEO 設計概念

[http://lqfb-](http://lqfb-6y7test.g0v.tw/ep/p/lqfb)[6](http://lqfb-6y7test.g0v.tw/ep/p/lqfb)[y7](http://lqfb-6y7test.g0v.tw/ep/p/lqfb)[test.g0v.tw/ep/p/lqfb](http://lqfb-6y7test.g0v.tw/ep/p/lqfb)
一整套的直接民主，整合線上線下
審議系統與表決系統分開，德國法令很嚴，表決系統需要高度的資安保護
也是以 recommandation 為中心，像是 follow 某些專家的 twitter
> delegation 無法維護秘密投票
> [name=ET B]

> 另外 recommandation 參與感遠大於 delegation
> [name=ET B]

表決
- 線上表決採別名制
- 每月固定時間投票
- range voitng + 棄權
（聯想）議案生命週期：發想與辯論→集氣→表決→執行


## Polly 設計概念

Goal: "Foster participative democracy" \[Polly Project\]
[http://wiki.polly-project.org/high-level-requirements](http://wiki.polly-project.org/high-level-requirements)

### 不需說明文字就自然會操作

- [x] ui 設計中拿掉所有 action icon 註解文字（已於v2完成）
> 反正那些都是按按看就知道會怎樣的按鈕，再按一下就可以恢復，可以隨意嘗試
> [name=ET B]

- [ ] 取而代之的是提供 toast 回饋（gmail，gcalendar）

### 更完整的議事功能

- 事前的先決要件
    - [ ] 列出方案的背景環境
    - [ ] 如果先決要件改變，是否支持此方案也需重新考慮
- 事後的實際行動
    - [ ] 能夠明確指派執行者與時間等細節
> 目前的動民主裡面大部分議案的執行者都是 clkao... XD
> [name=ET B]

> 以 g0v 來說，執行者的部分比較適合用認領而非指派
> [name=ET B]

    - [ ] 執行者要同意此項決議\* （待討論）
- 處理超大議題的能力
    - 測試與收集情報
        - [ ] 在狀況超不明確的超大議題鼓勵實際實驗後回報資料
    - 子議案
        - [ ] 可以把超大議題拆小
        - [ ] 拆小後的子議案的排序用投票決定
        - [ ] 子議案還可以有子議案
    - 用不同角度審視
        - [ ] 列出議案會有哪些考量的點
        - [ ] 可以編輯考量點清單，直到善盡周延
        - [ ] 每項考量點可以設定權重
        - [ ] 每個方案可以針對各項考量點評分
        - [ ] 評分經過加權後的總和形成該方案的總分
> 個人是不太希望這麼量化，原本就無法精確量化的東西其實不適合用精確的單位來衡量，否則很容易拘泥於數字
> [name=ET B]

        - [ ] 過程可以 pdca 循環，而不是一次就敲定
- （聯想）處理系列議題的能力
    - 議案有來龍去脈
        - [ ] 可以設定議案之間的關連，顯示一整個系列（世界奇觀）

### 在正式議案之外

- [ ] 可以方便的產生文件（現在的動民主應該就有了，雖然不知道要去哪裡開 XD）

### 歡迎多元意見但避免大聲公

- [ ] 類似 youtube 的 comments 評分系統
> 嘛... 原本的 prfb 算是有？
> [name=ET B]


### 更複雜的表態

- 2D投票
    - [ ] 可以投「我有多關心」x「我有多同意」
> 個人不太喜歡這樣的投票法，有多關心可以從議案內的發言程度看出來，如果需要知道關心程度，看他們直接用腳投票就可以了，多一個東西要手動投會越來越眼花撩亂 = =
> [name=ET B]

- 雙頭方案 / 連動票
    - [ ] 「我投給 A 方案的前提是 B 方案也一起」的情況下，撤銷任何一邊都會導致另一邊也失效
> 在 "Concept: Build-in Deal Making" 這段，其實看不太懂... = =b 他講的似乎是兩黨間的交易，但我想像的是「某些方案必須有配套措施才能成立」的情況
> [name=ET B]


### 更機車的委任

- 追蹤委任票
    - [ ] 通知我委任給別人的票投到哪去了
    - [ ] 通知我代理人偷懶沒投票，浪費了我的委任
    - [ ] 投票完成後有一段凍結期間可以調整委任票，避免代理人故意在投票最後一秒變卦
    - [ ] 一張票可以拆成小塊委任給多個人（類似 adhocracy 吧我猜）
- 決定要委任給誰：聲望系統
    - [ ] 顯示個人的 reputation 與變化趨勢
    - [ ] 顯示個人投票史
> 還有一堆雜七雜八的...以後再說吧 zz
> [name=ET B]


### 提高黏度

- 推薦議案
    - [ ] 推薦投票中議案
    - [ ] 通知我有訂閱但未投票的議案
> （聯想）也許可以在右上角放那種討人厭的小紅字 XD
> [name=ET B]

    - [ ] 推薦我可能會喜歡的議案（related issue）
    - [ ] 推薦我的朋友感興趣的議案
- （聯想）提高傳染率
    - [ ] sns 分享按鈕
    - [ ] 個人成就（ptt、stackoverflow）

### 推坑新人

- 提示新人可以做什麼
    - [ ] 顯示老人的 activity history（facebook）
    - [ ] 顯示老人做了什麼貢獻而得到 reputation（guild wars 2）
    - [ ] 顯示老人是管理者嗎？有幾張代理票之類的
- 鼓勵新人
    - [ ] 可以針對 activity 按讚（facebook / google plus）
> 有些看不太懂...再說吧 zz
> [name=ET B]


### 符合現行法律或章程

- [ ] 可以票選 moderator
> 個人是不太喜歡需要額外 moderator 的機制，但如果是在宅圈以外的地方實際執行動民主的話也許真的會需要這樣的角色
> [name=ET B]

- [ ] moderator 可以下 tag，指出議案違反現有章程的地方，讓提案人參考以便修改
- [ ] moderator 可以把需要用到額外的錢/資源的議案提交給議會審核
- [ ] 不服 moderator 的話可以上訴（？）到議會

### 防範數位弊端

- [ ] email 通知個人動態，避免盜帳號
- [ ] 投票時記名，但可以使用別名參與，避免光暈效應或是造成實際生活上的困擾


## 其他領域...


### 商務企畫概念

便利貼腦力激盪法、[企業問題分析與解決](http://www.books.com.tw/products/0010572614)

### Airesis - Scegli di partecipare

[http://airesis.us/proposals](http://airesis.us/proposals)
Airesis is a free software platform, built by a team of Italian developers and contributors, to enable communities and groups to organize themselves in a productive manner according to the principles of direct democracy and participation. To achieve this goal, the application has been designed as a multifunctional system, which integrates all the tools that can help the development of a community, in particular

### Insights

[http://www.insights-us.com/](http://www.insights-us.com/)
Insights helps leaders make smarter decisions by leveraging the insights of their stakeholders. Insights’ online consulting platform turns the wisdom of stakeholders into advice decision-makers can use. Its technology enables government agencies, businesses and non-profits to improve their outcomes and create partners for change. Innovative crowdsourcing algorithms allow users to perform most of the analytical tasks, relieving decision-makers from wading through tons of responses.

### Civic Eagle

[http://www.civiceagle.com/who-we-are](http://www.civiceagle.com/who-we-are)
We are a group of thinkers obsessed with the idea of changing the way that we, the people of the United States, engage with our Congress and each other. We share the belief that a revolution within the realm of civic engagement is necessary; that our national and local leaders can help us, instead of exploit us; and that when simple, efficient, and easily available, everyone is willing to participate.



