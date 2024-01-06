---
title: "動民主 2.0 設計概念 - 相關系統超級比一比"
tags: 動民主,hackpad
---

# 動民主 2.0 設計概念 - 相關系統超級比一比

> [點此觀看原始內容](https://g0v.hackpad.tw/Y5f4w3JWs2Y)


## Liquid Feedback / Pirate Feedback

- 特點
    - 解決代議僵化的問題
        - 委任出去的投票隨時可抽回，而不是一選上議員委員後就可以把選民當空氣。
    - 解決鳥籠公投的問題
        - 表決不是選「是」或「否」，而是選「贊成」「反對」「無意見」，且可以在多個贊成的方案之間排定優先順序。
> 如果在提案階段加上一個「其他意見」的選項呢？透過表達其他意見，或許可以讓提案人將內容更加完備。
> [name=Pearl S]

> 這段在講的是lqfb這套系統的表決功能，由於原開發者已經決定跳槽砍掉重練，大概不會花心思去新加功能…真的很想要的話可以去找他們提提看 :P
> [name=ET B]

    - 解決公投陷阱題的問題（審議式民主取代表決式民主）
        - 候選方案一發表其他人就可以表態、討論、提建議、提正反論點，而不是少數人決定選項之後其他人只有投票的份
    - 解決空談的問題
        - 任何議案提出時必須已附帶一個解決方案，所有的討論都是圍繞著解決方案，不會有天南地北發散完以後結果什麼結論都沒得到的情況。
- 不採用的原因
    - 空中方案
        - 問題解決的生命週期三階段包括「分析」「規劃」「執行」，LQFB 僅處理「規劃」階段，沒有事前的分析，也沒有後續的執行追蹤。然而，沒有分析過程就直接進入規劃階段的作法無法應付像是核四、都更、服貿等複雜的大型社會議題，又，規劃沒有轉換成行動且持續追蹤的話一切討論都是沒有意義的。然而，如果要替 LQFB 補上分析和執行的部分，那麼系統也就幾乎等於重寫了。
> 以台灣的政治現況而言，執行面本來就不是LQFB能解決的問題，但是找代理人應該比建立一個完整的民意來得簡單些，也就是說「分析」和「規劃」面完成之後，「執行」面相對來講可能比較容易些（至少已經有可以選擇的制度）。
> [name=Pearl S]

> 如果將LQFB分成兩大程序呢？第一程序是意見形成（比方說建立主要的兩三個選項）、第二程序是意見表決（從這兩三個選項中選出最多人認同的一個），這樣有機會一併處理「分析」和「規劃」的問題嗎？
> [name=Pearl S]

> 是的，就是為了做這件事情所以才開發動民主2.0
> [name=ET B]

> 「LQFB僅處理規劃階段，沒有事前的分析」好像不然。我看 lqfb ebook 第一章有說明它鼓勵成員提出變化版的倡議，變成原始版的 'clone'，lqfb 就是要充分地勾出所有的 'clones' 倒回來更清楚地定義原來的議題。但不管哪套系統總得先有辦法充分實驗。哪套可以使用於限定必須團體產生著手的班際、校際的棋賽？
> [name=Boidunion]

> 對某些規模特大的議題來說，事前的分析工作會很龐大，龐大到沒辦法在各個提案 clones 裡面處理，比方說，核四到底要不要續建？牽涉到的不僅是核四本身，還包括核能，以及更上層的整體能源政策，於是核電火電風電水電…各種能源的成本結構發展現況環境影響……等背景資訊，都變成規劃提案和投票決策的參考。這些客觀的背景資訊，是所有提案共用的知識庫，在這個共通的知識基礎上，再去規劃提案，比較能避免各說各話的情形（回想核四議題的各種網路論戰…XD）
> [name=ET B]

> Tks! 一看核四的例子，瞬間腦塞，那是個哲學問題。回到 lqfb, 經本篇用功的分析看來似乎沒有一個能用的，但取法自然界不長眼睛地在演進，它是通通都好有什麼用了再說，活得下來就對了。那就是只管來辦「[Lqfb杯象棋賽](https://g0v.hackpad.tw/jVZASsoi0Ql#Lqfb杯象棋賽)」，只限定次一著必須團體決策產生不限制用哪一種民主程序，希望由做中學，比較不傷腦筋。
> [name=Boidunion]

    - 代理的教訓
        - 代理機制無可避免地會造成秘密投票上的漏洞，如果採用代理機制，在正規投票場合中將無法使用此系統。因此以公民參與為最終目標的話，代理機制不免會成為未來系統發展的絆腳石。
> 代理機制和秘密投票一定會互斥嗎？如果代理和投票只辨識認證而不辨識身分的話，是不是可以解決這個問題呢？（也就是說代理和投票時只確認「他有一票」或「他代理了一票」，而不去辨認這一票是來自「誰」）
> [name=Pearl S]

> 委託人必須知道代替自己投票的人究竟投了什麼，才能在苗頭不對的時候收回自己的委任，所以是的，一定會互斥
> [name=ET B]

> 不一定互斥喔！[LiquidFeedback 堅持「公開透明」就一定與「秘密投票」原則衝突嗎？](https://g0v.hackpad.tw/LiquidFeedback--ggBlvqzmtcW)
> [name=Boidunion]

> 不是「公開透明（地討論倡議）」跟「秘密投票」互斥，是「委任投票」跟「秘密投票」互斥
> [name=ET B]

        - 民主的本質就是公民要當老闆，當老闆的人要思考要動腦要做決定，不能偷懶。然而代理機制會間接地導致怠惰，由於設定代理後可以安心去忙自己的事情，公民參與度跟著降低，結果反而違背民主制度的初衷。（來自德國的LQFB使用率統計顯示使用越久活動率越低）
        - 綜合以上兩點可知線上代理機制是人類一項失敗的嘗試，然而 LQFB系統中最主要的元件就是代理，抽掉代理功能後這系統也所剩無幾，直接重寫一個比較快。（德國海盜entropy如是說）（看起來比較像是"代理機制/代議政治是人類一項失敗的嘗試"？）
> 或者是乾脆直接把代理機制抽掉呢？
> [name=Pearl S]

> lqfb有關閉代理機制的選項
> [name=ET B]

- 值得重複利用的零件
    - 可以表達多元意見的彈性表決機制
    - 透過認同程度的高低找出最迫切、最普世的問題

## Adhocracy

> 沒有深入研究，先跳過 ^^b
> [name=ET B]

> 剛剛註冊，出現500 不給我用 ...><...
> [name=Edgar C]

> 不確定是否跟中文化有關，試試 openid/google  log-in, 或改用英文介面的瀏覽器?
> [name=Charles C]

> 重開，log in完成，免開英文介面
> [name=Edgar C]

- 特點：
    - 可直接申請使用，例如 [https://greenpartytaiwan.adhocracy.de/](https://greenpartytaiwan.adhocracy.de/)
- 不採用的原因
- 值得重複利用的零件
- 中文化翻譯中，歡迎加入： [https://www.transifex.com/projects/p/adhocracy/language/zh_TW/](https://www.transifex.com/projects/p/adhocracy/language/zh_TW/)
    - 已初步翻譯完成，網站已有中文介面。( 2014/06/28 )
    - 待對照網站使用脈絡後，進行潤飾/調整

## Wikiarguments

- 特點
    - 解決在辯論串中迷路的問題
        - 正反意見分開來列，集中在左右兩邊，一目了然。
        - 每一則 argument 還可評論，辯論串集中在各自的 comments thread，不會出現不同爭點的討論全部攪在一起的情形，跟 disqus 原理相似，但介面對於討論結構的呈現比 disqus 更為凸顯。
- 不採用的原因
    - 只適合小型、處於提案階段的議題
        - 問題本身要是一個立場鮮明的見解，才會需要正反辯論，因此不適用於能源政策、兩岸協議等需要廣泛收集各種立場的大型議題
        - 問題本身要已經完成背景分析、進入提案階段，才會有立場的產生，因此不適用於尚在發散階段、需要多方探索的議題
- 值得重複利用的零件
    - 整個正反辯論串的機制可以用在某些特定的題型

## Polly（概念階段）

- 特點
> [http://hack.g0v.tw/meta/P8vYztFYSpN](http://hack.g0v.tw/meta/P8vYztFYSpN)
> [name=ET B]

    - 整個系統的主軸偏向於組織內部使用，在管理、投票等功能著墨甚多，甚至搞得有點複雜。
- 開發中，目前無法採用
- 值得借鏡的概念
    - 推薦議題給使用者直接參與，而非著重在代理投票（直接民主 vs 流動式代議民主 vs 代議民主）（同BEO，LQFB原始設計概念）
    - 以實際解決問題為目標而不只是以討論為目標。除了方案規劃之外，還有前期的分析與後期的執行，包含一個完整的問題解決生命週期。
    - 針對問題分析階段的設計概念，如鼓勵發想、切割子議題。
    - 需要身份認證但可使用別名，保護使用者免於被人肉或實體騷擾的危險。

## BEO（概念階段）

- 特點
> [http://hack.g0v.tw/meta/P8vYztFYSpN](http://hack.g0v.tw/meta/P8vYztFYSpN)
> [name=ET B]

- 開發中，目前無法採用
- 值得借鏡的概念
    - 線上民主是整個民主機制的一環，要整合線上投票與實體投票
    - 每個月有固定的投票時間
    - 把議事系統與需要嚴謹身份認證的表決系統獨立開來
        - 議事、表決、資料收集等系統可以彼此獨立，再以 api 組合

## Open Ideo

- 特點
    - 解決未經全盤思考就提出片面見解的問題
        - 議題在同一時間內只能做一種事情，強迫大家先思考才決策，發想階段結束後才能提解決方案，進入下個階段後就不能回去做前面階段的事情
        - 提出一組基本問題吸引所有人來回答
    - 可愛的介面
        - 用豐富的圖片和漂亮的設計，吸引非宅族加入
- 不採用的原因
    - 瀑布型的思考模式並不符合真實世界的運作情況，現今複雜的世界裡，事情的發展是 PDCA 循環組成的螺旋形，事情的先後順序並不是絕對，每個人的起跑點也不同，如果硬要規定所有人用瀑布型的模子思考，就得對使用者加諸限制，結果只會澆熄靈感與熱情。如果想要提升內容品質，不應該以限制使用者為手段，而應該採用引導的方式，並提供多元切入點給身處不同起跑點的人（望向quora）
    - 事先設定好議題框架（問題組）再讓人來參與，並不符合直接民主的精神，主導的人難免把自身的立場帶入框架中，但理想的直接民主應該是開放所有人一起來決定框架。open ideo 的主軸不是民主，而是某特定單位舉辦的徵文活動。
> OpenIDEO的執行方式著眼於更大的問題，並且有階段性的一步一步收斂。所以一開始的問題必須要是Big Question，接著再透過充分的research與prototyping，期望能夠得到真正可以執行的方案。OpenIDEO通常鼓勵以團隊的方式來進行整個design process並且確保其方案可以執行並且解決問題，確實與直接民主不太一樣。但是OpenIDEO應該不只是一個可愛的徵文比賽平台，要不然IDEO是沒辦法靠這個做這麼多案子的。
> [name=Kaba S]

    - 介面繽紛可愛，但強調可愛大過於強調內容，行銷包裝的功能勝過於議題討論的功能。讓人長期使用的東西本身應該盡量低調，像 dropbox 等。
- 值得重複利用的零件
    - issue > question > answer 階層結構，把不同規模不同性質的 item 區隔開來，便於呈現整體結構。

## Change.org / 台灣連署資源運籌平台

- 特點
    - 集氣
- 不採用的原因
- 值得重複利用的零件

## Stackoverflow / Ask.com / Yahoo 知識+

- 特點
- 不採用的原因
- 值得重複利用的零件

## Quora

- 特點
- 不採用的原因
- 值得重複利用的零件

## Branch.com

- 特點
- 不採用的原因
- 值得重複利用的零件

## Facebook / Google+

- 特點
- 不採用的原因
- 值得重複利用的零件

## 實體公民論壇

- 特點
- 不採用的原因
- 值得重複利用的零件

## iVoter

[http://ivoter.ecrc.nsysu.edu.tw/test-analysis](http://ivoter.ecrc.nsysu.edu.tw/test-analysis)

## 善蟻雄兵


## Loomio


## Politeia 2.0

希臘人 (?) 做的民主平台. 先記著, 詳情還沒瞭解.
[http://www.polites2.org/en/](http://www.polites2.org/en/)

## We the People

[https://petitions.whitehouse.gov/](https://petitions.whitehouse.gov/)
[https://github.com/WhiteHouse/petitions](https://github.com/WhiteHouse/petitions)

## ParliamentWatch

[http://www.abgeordnetenwatch.de/](http://www.abgeordnetenwatch.de/)
選民可以直接上去問候選人問題（不需要聯署至一定的門檻）、請願（必須聯署）、討論表决項目、觀看候選人在國會的表現。像是國會大代誌＋動民主想做的事。可能人民之間的串聯和討論沒有動民主那麼多。

## open gov idea scale

[http://opengov.ideascale.com/](http://opengov.ideascale.com/)

## Betatext

[http://techpresident.com/news/wegov/23161/german-green-party-encouraging-online-participation-legislative-process](http://techpresident.com/news/wegov/23161/german-green-party-encouraging-online-participation-legislative-process)

## Wasa2il

[http://piratetimes.net/solving-democracy-through-technology-introducing-wasa2il/](http://piratetimes.net/solving-democracy-through-technology-introducing-wasa2il/)

## agora voting

[https://agoravoting.com](https://agoravoting.com) - [https://github.com/agoraciudadana/agora-ciudadana](https://github.com/agoraciudadana/agora-ciudadana)

## democratia os

[http://democraciaenred.org/](http://democraciaenred.org/) \- [https://github.com/DemocracyOS/app](https://github.com/DemocracyOS/app)

## 希望地圖

類便利貼： [http://hopemap.net/](http://hopemap.net/)
成效 [http://webcache.googleusercontent.com/search?q=cache:Ldz_ivnlEVwJ:www.wretch.cc/blog/HopeMap/11508142&hl=zh-TW&gl=tw&strip=1](http://webcache.googleusercontent.com/search?q=cache:Ldz_ivnlEVwJ:www.wretch.cc/blog/HopeMap/11508142&hl=zh-TW&gl=tw&strip=1)

## poplus

[https://groups.google.com/forum/#!topic/poplus/74zW55yAFwI](https://groups.google.com/forum/#!topic/poplus/74zW55yAFwI)

## Polis

[https://pol.is/10824](https://pol.is/10824)


## formosa pirates

大家好，我是一個新成立的小團體Formosa pirates的發起人之一。關於動民主的部分我最近寫了一個企劃案。詳細內容整備中。主要方向是打算先設定好架構再集資請遊戲廠商架設軟體。我採取的概念是一個理性討論的平臺，包含媒體過濾，尊重權威機制，榮譽制度，還有實質登錄註冊。最後會採取組織化形成公民聯盟的方式，嘗試類似德國海盜黨的理念下去結合。

這是我部分的企劃書起草:
[https://db.tt/rclIQP0K](https://db.tt/rclIQP0K)
[https://db.tt/qFlAU0KG](https://db.tt/qFlAU0KG)
[https://db.tt/o14H3APR](https://db.tt/o14H3APR)
[https://db.tt/GGqlTomy](https://db.tt/GGqlTomy)
其他內容還在整理中。

目前計畫5/3,5/4在臺北和幾個有興趣的夥伴一起討論整個架構的設計。我想這邊很多對這方面有研究的前輩，或者能給予我們各種不同方向的建議與指導，如果可以的話歡迎隨時與我聯絡~~感激不盡。
> 伸 mockup XDD 可以用這個畫 [https://moqups.com/#!/](https://moqups.com/#!/)
> [name=ET B]

> 我過陣子直接放影片好了。簡單概念在第三個檔案[https://db.tt/o14H3APR](https://db.tt/o14H3APR) 裡有草圖。
> [name=Bo-Jung C]

> 陳醫師，製作上似乎也不一定要遊戲開發商。政黨應該是邀請他們協作提供相關資料。看完計畫有幾個問題可以再討論，一是這是單純的公民參與平台或是要成立另一個政團或組織，可能要再釐清一下。若為公民參與平台，似乎可以與動民主專案作結合。5/4若無特殊事件，我應該可以參加討論，如不嫌棄我只會出一張嘴、打打字的話～XD
> [name=Edgar C]

> 這些問題我都有想過，動民主平臺內有些設定上的問題和我架構上有某部分本質上的衝突。而我設計的民主也並非人人平等，而是採取專業取向，如果沒有一個全然負責的組織維護平臺，實際上操作會有很多問題，像g0v這樣的話，自由度創意度很高，但整合力度上及平臺維護上終究是個麻煩。目前是暫定"5/3 中午台北市大同區承德路三段52號 "會和大家討論。出一張嘴當然要來，就怕連嘴都沒有的了。我也是出張嘴XD。
> [name=Bo-Jung C]

> 5/3我就無法到了，週六整天都在上課～抱歉。
> [name=Edgar C]

> 星期日場還在統計人數，否則場地難借。如果有辦再po上來。個人是覺得沒有真的組織化很難對政府有實質上的監督力道。
> [name=Bo-Jung C]


## socialbakers

選舉 x 社交網站影響力
[http://www.socialbakers.com/elections-2014/taiwan/](http://www.socialbakers.com/elections-2014/taiwan/)

## hacktabl

議題 x 觀點整理
[http://hacktabl.org/taipei-mayoral-election-2014](http://hacktabl.org/taipei-mayoral-election-2014)
Github: [https://github.com/MrOrz/hacktabl](https://github.com/MrOrz/hacktabl)


## 國發會公共政策參與平台

[http://join.gov.tw/openup/index](http://join.gov.tw/openup/index)

