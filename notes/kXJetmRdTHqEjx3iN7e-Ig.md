---
title: g0v Language Portal
tags: 翻譯, 在地化, 語彙庫, translation, localization, glossary
---

# g0v Language Portal 語彙庫計畫

:::info
💬 目前討論在 [g0v](https://g0v.tw/) [Slack](https://join.g0v.tw/) [#localization](https://app.slack.com/client/T02G2SXKM/C0483Q7ALN6) 進行。
:::

專案連結 / Project Source：[GitHub](https://github.com/g0v/language-portal)

## 一、提案構想 / Idea

{%speakerdeck rschiang/g0v-hackath52n-proposal-language-portal %}

以搜尋引擎的方式讓社群夥伴貢獻翻譯的詞彙表，確保台灣在地的翻譯用詞能被保存。

Allow communities to contribute to the translation glossary through a search engine approach, ensuring that local Taiwanese translation terms are preserved.

## 二、名詞解釋 / Definition

* **詞彙表 (glossary)**：譯者在翻譯時為了統一譯名整理出的參考文件，類似專案的迷你辭典。
    * 跟實際的翻譯語料檔（如 `.po`）不同。
    * 可以記載詞性、單複數與使用語境等注意事項。
    * 以影音剪輯軟體而言，可能就會有：
        * 語境：`channel`「頻道」 ↔ 「聲道」(`audio ~`)、「色版」(`color ~`)
        * 詞性：`filter`(v.)「篩選」 ↔ `filter`(n.)「濾鏡」

* 語言入口網：其實是微軟查詢各產品所使用的翻譯詞彙表的[網站](https://www.microsoft.com/language/)名稱，被拿來當這類網站的代稱。


* **Glossary**: A reference document compiled by translators for consistent translations, similar to a mini-dictionary for a project.
    * Different from actual translation files (such as `.po`).
    * Can record part of speech, singular/plural, and usage context, among other considerations.
    * For example, in video editing software, there might be: 
        * Context: channel "channel" ↔ "audio channel" (audio ~), "color [plate](https://en.wikipedia.org/wiki/Offset_printing)" (color ~)
        * Part of speech: filter(v.) “filter” ↔ filter(n.) “filter effect” 
* Language portal: the website name of Microsoft’s query for translation glossaries used in various products, taken as a generic term for websites of this kind.

## 三、網站規格 / Specification

:::warning
<em style="font-style: normal; font-family: Hannotate TC, Kaiti TC, BiauKai, 標楷體, cursive;">底下目前還是初步討論的內容。The content below is still in the discussion stage.
</em>
:::

### 使用者 / For Users

* 搜尋 / Searching
    * 語彙 / Phrase
    * 語言 / Language
    * 領域（天文、地理、經濟學、作業系統⋯⋯）/ Domain
    * 專案（LibreOffice、g0v summit⋯⋯）/ ~~Project~~ Source
    * 詞性？/ Category? [Part-of-Speech](https://en.wikipedia.org/wiki/Part_of_speech)?
* 搜尋結果 Search results
    * 要不要有字典定義式的例句？ / Should we have dictionary-style example sentences?
    * 允許推噓？ / Allow upvotes and downvotes?

### 貢獻者 (Contributor)

* 登入 (Login)
    * GitHub
    * Slack 或其他方式？ (Slack or other methods)
* 匯入詞彙檔 (Import Translation Memory)
    * 允許匯入詞彙檔以外的格式（如 `.po`）再手動挑選適合作為單詞匯入的部分？ (Do we want to allow importing regular translation files other than translation memory and allow contributors to manually pick suitable contributions?)
    * 如何更新與合併？ (How do we update and merge new contributions?)
* 手動編輯 (Manually Editing)
    * CRUD
    * 新增例句？ (Adding up with example sentences?)
* 個人頁 (Personal Page)
    * 自介、聯絡方式、貢獻清單之類的 (Self Intro, Contact, list of contributions, etc.)

## 四、討論紀錄

### 6/10 Facing the Ocean Jeju
* Deployed the basic skeleton code with Next.js and Github Pages https://g0v.github.io/language-portal/
* Created new repository https://github.com/g0v/language-portal
* We have explored as a reference to the following:
    * https://terms.naer.edu.tw/
    * http://dict-plugin.naver.com/participation/word_list.dict#common/register/all/ko/
* Hello from @sigridjineth
    * \Hi! (・ω・)ノ/ ——[name=RSChiang]

### 4/8 g0v hackath55n

* 資料來源確保
    * 國教院 Open Data CSV 資料已上線開放資料平台，但沒有詞彙領域的總目錄、無法知道[公開資料](<https://www.naer.edu.tw/opdata/>)是否齊全
    * 官網[下載專區](https://terms.naer.edu.tw/download/1/) 是 ZIP + ODS 格式，需要後處理
    * 進度：重寫 [NEAR-Terms](https://github.com/g0v/moedict-data-terms) parser

### 12/17 g0v hackath53n

> [name=chewei] 預計於 12/17 週六舉辦

### 10/22 g0v hackath52n @ AS

* 收錄範圍
    * 軟體在地化（使用情境明確）還是包含各類學術與非學術名詞（服務廣泛）？
    * Ludwig：對一般譯者也很有幫助
    * 子魚：希望能支援英文以外的語言、語系（如日文）
    * 可以整合之前 g0v 萌典國教院雙語詞典的一些資源，當作其中一種 data source
* 帳號管理方式
    * GitHub、Slack (?)
    * 宏信：如果開發能量是個問題，或許可以先用 GitHub PR、靜態編譯
* 詞彙表匯入
    * 提供譯者上傳現有詞彙表的方式
    * Q: 如何更新？如何維護？

### 9/25 初步發想

* 收錄範圍？（僅軟體在地化，還是包含各類學術與非學術名詞？）
* 整合 GitHub 登入？
* 要提供類似 iTaigi 的比分系統（按呢講好、按呢怪怪）嗎？
* API?
* Urban dictionary 可能是個好的社群翻譯（外加創造）詞彙的方式？

## 五、參考連結

* [Microsoft 語言入口網站](https://www.microsoft.com/language/)

### 類似專案

* [開放歡譯](https://g0v.hackmd.io/iyDArJr1QUe7pcLI9f5trw) — 群眾討論統一詞彙翻譯
* [為你翻譯](https://g0v.hackmd.io/ryjRzf3CSZiEwXl3L9Tcvw)（前[翻吧！台灣](https://g0v.hackpad.tw/M6aHMLt3fn8)） – 群眾協助翻譯計畫

### 討論串

* [2021/09/01 g0v 社團](https://www.facebook.com/groups/g0v.general/posts/4227170847359289/)
* [2022/09/17 數位發展部 au 臉書](https://www.facebook.com/digitalminister.tw/posts/pfbid0LMbJHhdy1xAFmsVNYUCx8U9JNKMFcPUBVE9628jDKeJs2VaHxqUUit3YFd57Q92Ul?comment_id=1113956792886524)

### 潛在資料來源

* [各領域專用語快速瀏覽](https://g0v.hackmd.io/AgI7aZ-sTVqBg4t6BGolPA)
* [特殊詞彙英文通用翻譯](https://g0v.hackmd.io/-dumiiZtS5Wr1eCJdnjbBA)
* [g0v summit 2014 口譯 glossary](https://g0v.hackmd.io/x7js5d6XRNag-YlkBh5qWA)
* [g0v 黑話及語錄](https://g0v.hackmd.io/hosZS2MqRR-JLwhomnDU3w)
* [常用專業英文](https://g0v.hackmd.io/VLwN_eOKSg6W4RZ32XZg5A)
* [資訊科技術語表](https://g0v.hackmd.io/SZHpaN8yQAyHeamQ7GwK3w)
* [PTT Translate-CS 版](https://www.ptt.cc/bbs/Translate-CS/index.html)
* [Chinese-l10n 郵件群組](https://groups.google.com/g/chinese-l10n)
* [中文化詞彙搜尋](https://glossary.pank.org/)
* [Mosky 詞彙表及蒐集方法](https://paper.dropbox.com/doc/My-Glossary-Moskys-Notes-bNm2zmNds0J2kg9QDxUxv)
* [Civic tech phrase - 各語言用詞](https://docs.google.com/spreadsheets/d/1FzmvVAKOOFdixCs7oz88cz9g1fFPHDlg0AHgHCwhf4A/htmlview#)


### 其他

* [2014 國教院雙語詞彙下載規劃](https://g0v.hackmd.io/ejgEPYwLQKWHec8GvVs4qw)

