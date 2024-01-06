---
title: "動民主 2.0 設計概念"
tags: hackpad
---

# 動民主 2.0 設計概念

> [點此觀看原始內容](https://g0v.hackpad.tw/1V1g67duANj)


### 整體大方向


stackoverflow / quora / 知識家：知識系統，累積群體智慧
wikiargument：辯論系統，著重在正反兩面併陳
lqfb / prfb：以流動式民主為手段的決策系統，目的是規劃與表決
facebook / plurk：社交系統，人際互動優先
blogspot / google+ / twitter / tumblr / branch：網誌/微網誌/寫作系統，內容優先
github：程式的分散式協作系統（目的跟動民主 2.0 最相似）
動民主 2.0：公民協作系統，以提供友善的工作環境為目標，取代傳統的國會、政策制訂單位

> 問一下或許可以幫助釐清動機的問題：
> [name=Simon P]

> 1\. 以整個動民主系統來說, 它對目前社會 (理想&實質) 的著力處在哪裡? (例如, 今天有一群人用這個系統設計一套政策, 那麼這項產物的實現手法會是如何?)
> [name=Simon P]

> 可能的實踐途徑有：
> [name=ET B]

> a.政黨內部自己的提案，則政黨自己去推
> [name=ET B]

> b.公民團體主導的提案，由公民團體遊說代議士送入國會
> [name=ET B]

> 也就是說，以現行的體制，還是需要透過代議士，只是我們可以透過系統證實這份政策的民意基礎，而實際實踐這份政策則必須仰賴資訊工具以外的力量
> [name=ET B]

> 2\. 承上, 基於著力方法的不同, 以工具/平台來說, 其產物也會不一樣 (例如, 如果實現政策手段是游說立院, 那麼就是出產一份游說攻略; 如果是手法是允許即使透過杯葛也可以強推, 那麼其產物可能就是參與者間的一份政治合約)
> [name=Simon P]

> 規劃出來的產物，可分為
> [name=ET B]

> a.政策本身，這類的規劃希望開放所有公民一起來參與
> [name=ET B]

> b.實踐政策的方式，這類的規劃要視執行單位是誰而定，不同的執行者（公民團體、政黨、商業公會等）根據自己的條件，會有不同的手段，而採用什麼樣的手段，就是他們內部要決定的事情，所以這類的規劃，會變成該團體的成員參與
> [name=ET B]

> (海盜黨因為角色是政黨+目前已經開啟席位, 他們的路線應該就是直接在議會推動, 這點比較明確, g0v 的話就要多解決那一段的問題)
> [name=Simon P]

> 沒錯，目前對動民主強烈表示興趣的，只有……沒有政黨席次的綠黨 XD
> [name=ET B]

> 這也是雞蛋問題, 如果某政黨願意採用動民主, 也可能得到支持而拿到席次 XD
> [name=Simon P]

> 如果動民主的機制設計得宜，透過動民主產生的決議就能代表民意，而支持民意的政黨就可能爭取到席次。
> [name=Pearl S]

> 整理文件乾坤大挪移中，東西可能會搬來搬去，弄好再跟你說 XDXD
> [name=ET B]

> ok ok XD
> [name=Simon P]

> 全部集中在這份  [2.0 Social Democracy](https://g0v.hackpad.tw/iTXM54EBWVo)
> [name=ET B]




### 系統設計者給經營者們的信


動民主 2.0 ，是為了日理萬機的國家老闆們，所設計的公民協作系統。

系統經營者的心態就像是企業經營者想盡辦法激勵全體員工一般，以「鼓勵所有公民發揮所長、一起完成事情」為目標，每個人都是來做事的，我們要讓做事的人如魚得水，並且盡量減少嘴砲和筆戰的空間。所謂的做事包括：找資料、收集資料、整理分類資料、筆記、彙整與發表報告、共同編輯、尋找靈感、腦力激盪、思考與規劃解決方案、提供專業支援……等具有學術風氣的行為。

在這樣的概念之下，動民主 2.0 的預設值會盡量關閉不必要的評價（嘴砲）機制，如果需要評價，建議以「行動」為指標，比方說，不提供按讚功能，但取而代之的，提供書籤、訂閱、引用功能。


### 系統經營者給系統設計者們的信


> 嗯..感覺系統很細緻/複雜/龐大，恐非日理萬機的國家老闆門所能負荷？
> [name=Charles C]

> 可能要在前端把不同元件拆開成幾個獨立的小app，雖然後端是共用的（正在拆）
> [name=ET B]



## 動民主 2.0 的基本組成

[http://g0v.github.io/don-republic/public/index.html](http://g0v.github.io/don-republic/public/index.html)
1.  entry，有三種類型
    不同類型的 entry 採用不同的功能模組
    - 開放式問答題
        - 像 stackoverflow 或 quora 的問題。用在一個人無法獨立完成、需要集思廣益的研究主題，像是「服貿協議對台灣各產業的衝擊」之類的。
> SO 是以解決問題 (problem) 為導向的系統，Quora 則是回答問題 (question)，在這裡大概是 Q 型系統會比較有用。
> [name=Simon P]

> 但我們家曾經把自家論壇改成 SO 型系統，結果是討論 (discussion) 的需求全部爆炸；這代表 SO/Q 型系統支援討論可能不夠力。
> [name=Simon P]

    - 優缺點評估題
        - 像 wikiargumants 並列某個見解的正反意見。對於要表決的提案有初步靈感、但細節還不明確的時候，可以作為提案的前置作業，像是「兵役從徵兵制改成募兵制有什麼優缺點」之類的。`
    - 文章
        - 像 blogger 或 google+ 的文章發表。當專業研究者已經針對某個主題做了完整的分析報告，可以不需要透過問答，直接把完整文章貼上來，像黃國昌、郝明義、李茂生之類的專業人士，通常習慣在自己 facebook 發表見解，希望他們可以不需要改變發文習慣，只要在動民主設定跟 facebook 同步發表即可。
> 所以動民主的編輯介面有同步發表到其他地方的選項，之後可能也需要 browser extension 讓他們在 facebook 發文時可以選擇同步發表至動民主
> [name=ET B]

2.  collection，有兩大類型，十種子類別
    不同類型的 collection 採用不同的功能模組，且不能設定父子關連，只能互相 tag
    - board 看板型 collection：用來執行某些特定任務，分為幾種子類別
> 用詞思考中：about 關於 / group 群組 / board 看板 / forum 討論區...
> [name=ET B]

        - 議題：分析研究用途
        - 提案：政策規劃用途
        - 專案：執行追蹤用途
    - tag 標籤型 collection：用來過濾感興趣的內容，標籤內部又分為幾種子類別
        - 領域/主題：學術性分類
            - 可以抓圖書館分類名稱或大專院所的學科名稱來內建，同時允許使用者新增
        - 國家/地區：地域性分類
            - 可以抓 iso 資料來改加上 g0v 的台灣縣市村里資料來內建，同時允許使用者新增
        - 組織/單位：行政性分類，政府部門、委員會、非營利組織、基金會、企業、財團法人等
            - 可以抓商業司之類的資料來內建，同時允許使用者新增
        - 行業/職位：產業性分類，各行各業的上下游產業鏈以及工作職務
            - 可以抓產業分析機構的資料，同時允許使用者新增
        - 公眾人物：對社會有重大影響力的個人，各級單位政務官、各大財團董事長、...
            - 不曉得哪裡可以抓... ，同時允許使用者新增
        - 族群：性傾向、年齡、種族、收入、所患疾病、特殊際遇... 等各種軟性分類
            - 不曉得哪裡可以抓... ，同時允許使用者新增
        - 自訂標籤：系統沒有內建相關的標籤子類別，因而無法納入現有子類別的標籤。如果被很多使用者採用，則想辦法另開標籤子類別，讓它轉為系統內建
3.  user，有兩種類型
    - 個人
        - account：包含跨角色共用的基本登入資訊、投票權
        - character：最多 5 個，每個角色有獨立的
            - profile page
            - name
            - level（1 - 80）XD
            - experience
            - interest
            - subscription
            - bookmark
            - ...
        - 區分 account 跟 character 的用意來自 polly 的別名概念，主要目的是保護個人不會遭到人或騷擾（如果他爆卦而得罪了黑道之類的），次要目的是讓 A 領域的達人在不熟悉的 B 領域發言時可以採用別名避免光暈效應，更次要的附加價值是提供更彈性的使用環境自訂空間，可以把一個角色當作一組設定值來用
    - 團體
        - 類似 g+ 或 facebook 的專頁，沒有投票權
        - authors：可以以團體名義發言的個人 user

## entry


### 功能

- 可收藏書籤（收藏後，如果興趣指數夠高的話會出現在個人 timeline 中）
- 可訂閱（有新動態時會在 nav bar 右上角跳出小紅字）
- 可分享（按下後自動帶出連結的 sns 帳號）
- 可回應
- 可追問（產生子 entry）
- 可邀請其他使用者回應
- 可 upvote / downvote / report（？）（保留空間，未來有需要再加）
> 換句話說，是否要有針對整個 entry 評價的機制？這要考慮兩點：
> [name=ET B]

> 1.是否需要downvote：是否會出現 entry 本身品質不良（問題問得不好、範疇混亂、隱含偏激的預設立場等）的情況？
> [name=ET B]

> 我想可以保留空間，等上線後視情況決定，一開始希望能先找到對的人上車，塑造出正面的社群文化，如果能吸引到對的人，也許可以不必一開始就動用到這種有點懲罰性質的 downvote 機制。
> [name=ET B]

> 2.是否需要upvote：品質優良的發問是否需要獎勵？
> [name=ET B]



### 組成

1.  content
    - title（140 字以內）
        - 權限
            - 開放共同編輯
    - description（500 字以內）
        - 權限
            - 開放共同編輯
    - answer wiki
        - 權限
            - 開放式問答 / 優缺點評估 \- 開放共同編輯
            - 文章發表 \- 僅作者可編輯
        - 功能
            - 可加入個人 library
    - responses
        - 權限
            - 僅作者可編輯
        - 功能
            - 可 upvote
            - 可 downvote
            - 可加入個人 library
        - 名稱
            - 開放式問答 \- answers
            - 優缺點評估 \- pros & cons
            - 文章發表 \- suggestions
    - comments（answer wiki / response 底下的推文串，500 字以內）
        - 權限
            - 僅 comment 作者可編輯
        - 功能
            - 可 upvote（按鈕「+1」）
            - 可 mark as resolved 同時封存（按鈕「已解決」）
        - 類似概念
            - google docs 的 comments
2.  meta
    - log - entry 內容的建立與變更記錄
    - statistics - 訂閱、書籤、分享、回應等各種統計數據
    - comments - 針對 entry 定位、適當性等非關內容本身的討論
    - connection
        - 關連的其他 entries
            - parent - 上一層問題，涵蓋範圍較廣較模糊的
            - children - 下一層問題，涵蓋範圍較窄較明確的。產生方式：
                - 按下「追問」按鈕後將 new entry 編輯完成並發佈，new entry 就會自動和原 entry 產生父子關連
                - 或者也可以在 meta 編輯畫面手動設定父子關連
            - alias - title 的別名，也就是同義 entry
            - similar - 容易混淆而被誤認為同義的近似 entry
        - 關連的 collections - 看板、標籤
        - 關連的 users - 我追蹤的人裡面哪些人正訂閱這個 entry

## collection


### 功能

- 可收藏書籤（收藏後，如果興趣指數夠高的話會出現在個人 timeline 中）
- 可訂閱（有新動態時會在 nav bar 右上角跳出小紅字）
- 可打包（匯出供離線閱讀）

### 組成

1.  content
    - title（80 字以內）
        - 權限
            - 開放共同編輯
    - description（140 字以內）
        - 權限
            - 開放共同編輯
    - summary wiki
        - 權限
            - 開放共同編輯
        - 功能
            - 可加入個人 library
    - related entries
        - 權限
            - 開放共同編輯關連
        - 功能
            - 一般檢視功能 \- 可排序、可選擇時間區間
            - 可在此 collection 內新增 related entry
    - related boards 相關看板 (related issues / related proposals / related projects )
        - 關連的不同子類別的 collections。產生方式：
            - 按下「新增相關 issue / proposal / project」按鈕後將 new collection 編輯完成並發佈，new collection 就會自動和原 collection 產生關連
        - 權限
            - 開放共同編輯關連
        - 功能
            - 可在此 collection 內新增 related collection
    - comments（summary wiki 底下的推文串，500 字以內）
        - 權限
            - 僅 comment 作者可編輯
        - 功能
            - 可 upvote（按鈕「+1」）
            - 可 mark as resolved 同時封存（按鈕「已解決」）
        - 類似概念
            - google docs 的 comments
    - export
        - 功能
            - 預覽自動匯出的結果
            - 更新預覽畫面
            - 在預覽畫面中編輯匯出結果
            - 儲存編輯過的匯出設定
            - 分享編輯過的匯出設定
            - 匯出 html / pdf 供離線閱讀
            - 採用別人的匯出設定
2.  meta
    - related collections - 關連的相同性質的 collections
        - parent - 上一層議題，涵蓋範圍較廣較模糊的
        - children - 下一層議題，涵蓋範圍較窄較明確的。產生方式：
            - 按下「新增子 issue / proposal / project」按鈕後將 new collection 編輯完成並發佈，new collection 就會自動和原 collection 產生父子關連
            - 在 meta 編輯畫面手動設定父子關連
        - alias - title 的別名，也就是同義 collection
    - tags - 標籤
    - comments - 疑慮 - 針對 collection 定位、適當性等非關內容本身的討論
    - followers - 關注者
        - 我追蹤的人裡面哪些人正訂閱這個 entry
    - log - 記錄 - collection 內容的建立與變更
    - statistics - 統計 - 類似 google analytics
        - 問答數、瀏覽人次、訂閱人數、書籤人數折線圖
        - 議題排名
            - 人氣排名
            - 問答數排名
            - 提案數排名
            - 專案數排名

### issue 議題

介面
- 議題摘要共筆
    - 權限：開放共同編輯
- 相關問答 (數字)
- 相關提案 (數字)
- 相關專案 (數字)
- meta

### proposal 提案

介面
- 提案摘要共筆
    - 權限：開放共同編輯
- 提案列表（動民主 1.0 的 issue 頁）
- 相關問答 (數字)
- 關連 / 延伸閱讀
    - 相關議題 (數字)
    - 相關專案 (數字)
- meta

### project 專案

介面
- 專案摘要共筆
    - 權限：僅 assigned 者可編輯
- 專案執行者名單
- 專案 google calendar / hackfoldr / google drive / google groups / ... 內嵌頁（optional）
- 相關問答 (數字)
- 關連
    - 相關議題 (數字)
    - 相關提案 (數字)
- meta
> 在建立相似度過高的議題/提案/專案時，應自動彈出詢問視窗，詢問建立者要不要移步到繼存的議題/提案/專案中一起討論。
> [name=Pearl S]

> 自動搜尋並列出相似議題供選擇
> [name=ET B]



### tag 標籤

介面
- 標籤摘要共筆
    - 權限：開放共同編輯
- 相關問答 (數字)
- 相關議題 (數字)
- 相關提案 (數字)
- meta

## user


### 功能

- 可收藏書籤（收藏後，如果興趣指數夠高的話會出現在個人 timeline 中）
- 可訂閱（有新動態時會在 nav bar 右上角跳出小紅字）
- 可舉報（若發現是spammer / 黨工）
- 可封鎖（封鎖後對方無法 follow 或 tag 我）
> 要如何避免「開分號」、「虛構人氣」等弊病？
> [name=Pearl S]

> 需要像stackoverflow或it幫幫忙的reputation system做帳號管理
> [name=ET B]


### 組成

- account
    - e-mail
    - account ID
- character
    - profile
        - name
        - expertise
        - reputation
> 有做事就有 exp，但有功績才有 badges
> [name=ET B]

            - level (1-80) / experience (每一級經驗值指數遞增) - 同 GW2
            - badges
        - content
            - questions
            - answers
            - posts
            - reports
        - interest
            - bookmarks
            - subscriptions
        - followers
            - bookmarked by
            - subscribed by
    - settings
        - linked account - 不同角色的連結帳號重複時跳出提醒
        -



## 各種關連


- entry-entry 之間的關連形式包括
    - 父子：A 的討論內容範圍涵蓋在 B 之內
    - 同義：不同標題，但指向同一個 thread，像 quora 的 alias
    - 近似：可能會以為是同義，但其實兩者並不同，標為近似後，可避免後人持續提出合併為同義題的請求
    - 前身：當兩個獨立 entry 經過使用者反應標註為同義，所有內容合併至另一個新的 thread，原本 entry 保留但凍結，成為合併後新 entry 的前身
- entry-collection 之間的關連形式包括
    - 相關：嗯... 就是被 tag 了
- collection-collection 之間的關連形式包括
    - 父子：同一類型的 collection 之間可以設定為父子關係（不同類型的不行）
    - 相關：不同類型的 collection 之間可以設定為相關（同 entry-collection 之間）
- entry-user 之間的關連形式包括
    - 訂閱
    - 收藏
    -
- collection-user 之間的關連形式包括
    -

### 功能模組

- ~會議室 ?~
- ~企劃室 ?~
- ~辦公室 ?~
- ~眺望台 ?~
- ~成就系統 ? ~
以上舊版用語忽略忽略 XD


\-\-\-
是否需要採用類似 知識家 / quora / stackoverflow 的代幣機制？
- 在知識系統中，reputation 點數通常可以拿來交易，懸賞作答之類的。背後的意義是「聲望不只是榮譽，也會帶來實質的好處」。
- 不過動民主並不是單純的知識系統，動民主的重要貢獻者往往在真實世界中已經擁有一定的聲望，不需要靠動民主系統中的 reputation 點數來得到自我肯定，即使有也是附加的。對這些人來說，需要的是類似 twitter 或 g+ 的官方帳號認證機制，確認這個帳號就是本人。
- 引入代幣機制同時也會產生操作誘因，引誘人追逐數字……這不是動民主所需要的。動民主需要的是榮譽感、對自己的言論負責任的謹慎態度。這些都不是任何點數可以換來的。相對地，量化的點數還可能令人感到被估價了，而讓動機變得不單純。
- 結論：沒有點數 XD


