---
title: "twlaw UI (abstract)"
tags: hackpad
---

# twlaw UI (abstract)

> [點此觀看原始內容](https://g0v.hackpad.tw/0ilwh2aVnYn)


## 前情提要

在 [g0v/twlaw](https://github.com/g0v/twlaw) project 中，我們已經將法律條文歷年的變更轉換成 [git repository](https://github.com/victorhsieh/tw-law-corpus)。但是為了讓社會大眾與法律界人士能有效利用，我們需要一個網站來呈現、讓大家討論對現類法條的想法、進而提出條文的修正。

### Target Audiance

- 立法委員：將提案更透明地呈現，誘發公開的討論，一起提高修正的品質。
- 法律人：希望提供法界人士、學生一個平台，讓他們能發表對現行法條的修正。同時提供各種對修法有用的資訊，讓整個過程更有效率。最後希望能將好的修正送進立法院。
> Hi Victor, 我的背景是法律，很樂意協助你這項project。我自己與夥伴自今年8月開始進行eCourt/eLobby專案，目標適用對象是改革法案推動之壓力團體。目前還在基礎工程中，進展很慢。但藍圖中eLobby正是針對法案修訂部分，期待可以做出朝向Westlaw結合Open Congress/Open States的功能(個人背景的關係，頗熟悉這兩個平台)。目前進度是還在等待評律網的David協助建立eCourt資料庫的部分，之後進行下階段將會提企劃案邀請東吳與台大法學院一同參與UX開發。期待更成熟後再搬家住進g0v。
> [name=Shufen]

> 太好了。我還滿好奇對法律背景的人來說，那一些功能是最需要的（例如，看每次修法的變動實務上有幫忙嗎?)。如果可以把規格開出來，大家可以一起來把工具做出來。g0v 的東西都是集眾人之力一起前進的，歡迎有什麼想法、做了什麼東西，隨時丟出來!
> [name=Victor H]

> 請問你心中的藍圖程式開發所期待對應的使用族群是法律人嗎？還是透過立法手段推動社會議題相關的修法工作？二者不必然有重疊。（個人淺見：法規還在修訂期的透明化，政治所訴求的目的性大於純粹法律正確性。）
> [name=Shufen]

> 法律工作的大宗是針對案子找問題的徵點,找法源,找判決。（請參考Westlaw）
> [name=Shufen]

> 社會大眾與法律修訂者是完全兩種類別。您心中之真意是想朝向哪方面？
> [name=Shufen]

> 其實一開始的想法是更理想性的 semi-直接民主。也許直接民主不切實際，但是在網路時代，目前的間接民主感覺又不太民主。所以本來的想法是，是不是能有一個(可持續使用的)方式能由民眾發起、討論、然後改變什麼事。以修法為例，如果能透過這樣的討論累積民眾的共識，也許對立法效率有幫助。但是其實我一直覺得有點理想化而沒有真的動手做... 從這個角度來說，也許更像是修正政治而不是法律? 我猜我想清楚之前可能不會訂下長遠的目標，而是做一步想一步吧。
> [name=Victor H]

> 另外，不知道台灣有沒有網路上的法律社群? 有點好奇他們的討論內容都是那一些東西
> [name=Victor H]

> 法律的領域太廣泛，除了討論學校的考試與國家考試的功能性討論外，一般事務所會以領域別經營部落格作為輔助行銷。
> [name=Shufen]



- 社會大眾：除了提供基本的查詢介面，也希望能讓大眾關注：
    - 已被提出的修正中的條文
    - 比較不同版本的修法
    - 對尚未被提出的修法建議：
        - 表達支持
        - 表達支持（含本修法提出者之後更新的任何版本）
        - 提出意見
> Open Congress : [http://www.opencongress.org/](http://www.opencongress.org/)
> [name=Shufen]

> Open States: [http://openstates.org/](http://openstates.org/)
> [name=Shufen]

> 動民主有預計要做類似的事情, 也許可以整合, 或以各自提供 Open API 給對方的方式來做
> [name=Kirby W]


### 相關專案

- [http://publicmarkup.org/](http://publicmarkup.org/) \- 線上法律提案 review/comment
- 立法院提案 api sample: [提案資訊](http://api-beta.ly.g0v.tw/v0/collections/bills/1108L15461)、[修法內容](http://api-beta.ly.g0v.tw/v0/collections/bills/1108L15461/data)
- 立法院提案 view: [http://ly.g0v.tw/bill/1011130070300200](http://ly.g0v.tw/bill/1011130070300200)
- 法律 api: [憲法第44條](http://laweasyread.herokuapp.com/api/article?name=%E4%B8%AD%E8%8F%AF%E6%B0%91%E5%9C%8B%E6%86%B2%E6%B3%95&article=44)

## UI features

- Browse
    - Web entry point.  May provide related resources as well.
- Search, should support abbreviation (e.g. 兒少法)
- Diff view
- Fork

Given the git backend, it should be fairly easy to implement advance features like, browsing the law in 1985, showing diff from 2000 to 2010, etc.

### Possible workflow

This is what we really want.
- Fork -> review -> send PR
- Issue.  What needs to be fixed, the priority, the progress.  Who are working on it.

## Tasks

### Non-dev task

- UI mockup, UX
- User study

### Frontend task

- May just use github API as backend
- Browse interface (render a github .md file)
- Search interface (use github search api? or with our own index)
- Diff view
- Fork view (existing fork, diff between fork, etc.)
- ~Issue tracking~ (may just use github interface)

### Backend task

- Caveat: since we check in law changes as git commit, what if we need to modify mistake in the commit history?  How do we maintain the history view after the change?  Currently it happens quite often because of the problematic source page.  Can we just push -f to master, and expect all the fork to merge without mess up the history too much?
- Refine crawler
    - Source page is not stable, and crawling involves human input
- Source-to-Markdown/JSON-to-git translation
    - This was done in twlaw, but we need to fix git translation to support incremental changes.
    - Open question: is putting every laws in a single git repo a good idea?  Should we split them by law?
> Plz split them by two dimentions: one is by law and the other is by committees of the Legislative Yuan. 
> [name=Shufen]


### Memo

- [https://code.google.com/p/google-diff-match-patch/](https://code.google.com/p/google-diff-match-patch/)

