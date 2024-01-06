---
title: "g0v x CKAN - 開放資料彙整平台"
tags: g0v idea pool,hackpad
---

# g0v x CKAN - 開放資料彙整平台

> [點此觀看原始內容](https://g0v.hackpad.tw/8dDtG1xQaqP)


## 現況 /  為什麼

g0v 現在有許多資料四散在各處，例如：
- 專案自行提供的 API -  ex 立委大頭照
- 引用外部的開放資料 API
- 其他外部的 pdf, doc ... 等非 API 資料來源

希望有一個地方能彙整這些資料，並且能以 「專案」、「tag」、「檔案格式」、「License」等方式快速搜尋出資料
而以上描述的使用模式，正是 CKAN 所擅長的。

## CKAN 是什麼

CKAN 是一個開源的資料入口網，由 Open Knowledge Foundation 所發起。CKAN 官方自詡為 "the world’s leading open-source data portal platform"，如此稱呼確實不為過。目前 CKAN 被應用在美國、英國、日本、巴西等等國家政府的開放資料入口網，台灣也有少數開始應用的例子。
- 美國：[http://www.data.gov/](http://www.data.gov/)
- 英國：[http://data.gov.uk/data/search](http://data.gov.uk/data/search)
- 其他例子，可見：[http://ckan.org/instances/](http://ckan.org/instances/)

技術面：CKAN 由 Python 輔以一些後端搜尋技術開發而成，資料庫使用 Postgresql

詳細可參考官網：[http://ckan.org/](http://ckan.org/)

## CKAN 的結構

### 主結構

- Organization (組織) - 資料的擁有者，例如「環保局」
    - DataSet (資料集) - 資料的集合，可屬於單一組織 （也可不屬於任何組織），一個資料集內可有多筆資料
        - Resource （資料/資源） - 通常是一個資料來源連結與一些 metadata，參照到一個外部的資料來源（例如 [http://](http://api.ly.g0v.tw/v0/collections/)[api.ly.g0v.tw/v0/collections/](http://api.ly.g0v.tw/v0/collections/)）

### 其它

- Group (分類) - 資料集的分類，一個 DataSet 可以屬於多個分類
    - Group 的 member 可將 dataset 加入或移出 group
- 其餘如：tag, license, map 等東西很直覺，不多作解釋
- Organization 在 ckan 2.2 以後，可以多層
- Organization 的 member 可以看到該 organization 的 private dataset
- Organization 的 editor 與 admin 可以在 organization 底下新增 dataset

## 測試

- 暫時測試環境：[http://ckan.g0v.today](http://ckan.g0v.today) （我們安裝的版本為 CKAN 2.2）
    - 帳號：g0v 密碼：g0v
> p.s. 目前未串接 SMTP, 因此如遇到需要寄信的功能 （ex Add Member 功能），會系統錯誤為正常。
> [name=isacl]


- Issue Tracking: [https://github.com/g0v/ckan](https://github.com/g0v/ckan)

## 坑們

> 如對於系統架設面有興趣，歡迎於 irc ping isacl, 很樂意開 ssh 登入帳號給您。
> [name=isacl]


- [x] 需要 lucene / solr 高手協助解決中文斷詞、中文搜尋問題
> 已實驗過 [IKAnalyzer](http://ckan-docs-tw.readthedocs.org/ja/latest/install.html#jetty8-solr4-w) 未果（預計近期再測試別的方法）
> [name=isacl]

> 試試 [https://hackpad.com/CKAN-1.8--zhur2gtjcRk](https://hackpad.com/CKAN-1.8--zhur2gtjcRk) ？ 嗯...好像是一樣的...
> [name=Charles C]

> 第零次動員戡亂黑客松 時有發表一個當時跟青平台合作的CKAN，後來沒人用就關掉了，但 2.0a 的源碼在 [https://github.com/opendatatw/ckan](https://github.com/opendatatw/ckan) ，不確定是否有幫助。
> [name=Charles C]

> 謝謝！我再試試看。（IKAnalyzer 應該只是在小地方出錯，我會換個版本試試看。但也想尋求其他比較新的解決方案 IKAnalyzer 看似很久沒更新了）。
> [name=isacl]

> 換了一個 IKAnalyzer 版本。should be fixed now. 
> [name=isacl]

- 資料整理
    - [ ] 將 g0v 使用到的外來 (data.gov.tw 或其他地方) 開放資料整理自 CKAN (參考 [Q&A - Q2](http://tinyurl.com/nx4gpdh) )
    - [ ] 將 g0v 出產的 API 或資料整理到 CKAN
        - [ ] ly - [http://api.ly.g0v.tw](http://api.ly.g0v.tw)
        - [ ] AddressBook
        - [ ] 新聞小幫手
> 其它請補充
> [name=isacl]

> 這邊是只要把資料連結或是Export出來的資料用他的介面新增進去?
> [name=sherry l]

> 皆可
> [name=isacl]

> \+ 對於已經有放資料的主機或是已經開放 API 的專案，直接在 CKAN 加入連結即可。（避免資料重複在兩個地方）
> [name=isacl]

> \+ 對於沒有架設 API 的專案，若想透過 CKAN 提供 API, 可將資料匯入 \`CKAN DataStore\`。Ref: [DataStore API](http://docs.ckan.org/en/ckan-2.2/datastore.html#the-datastore-api)  ，會有基本的 Search API 可使用。
> [name=isacl]

- [ ] 翻譯 （歡迎熟悉 transifex 的朋友參與：[https://www.transifex.com/projects/p/ckan/language/zh_TW/](https://www.transifex.com/projects/p/ckan/language/zh_TW/) 需登入並申請進入 translation team）
> isacl: 我已經申請到 CKAN translation team 帳號了，最近正在翻譯中，如果有什麼翻譯的建議，但懶得申請 transifex 帳號，可以在此提出，我可代為貼到 transifex。感激。
> [name=isacl]

> 累積一定的翻譯修正之後，會更新到 [http://c](http://ckan.g0v.today)[k](http://ckan.g0v.today)[a](http://ckan.g0v.today)[n](http://ckan.g0v.today)[.g](http://ckan.g0v.today)[0](http://ckan.g0v.today)[v](http://ckan.g0v.today)[.t](http://ckan.g0v.today)[o](http://ckan.g0v.today)[d](http://ckan.g0v.today)[a](http://ckan.g0v.today)[y](http://ckan.g0v.today) 供大家預覽
> [name=isacl]

> 應該已經把 ISACL 加到專案協調者，就可以自行翻譯新增成員了。加油XD
> [name=Charles C]

> charlesc? 感謝幫我加入 m(_ _)m 能有前輩指點真是幸運
> [name=isacl]

- Extensions
    - [ ] Install DataStore Extension
    - [ ] Install FileStore Extension
    - [ ] Install PDF Preview Extension
    - [ ] Install Organization Hierarchy Extension


## 技術細節


- Preview
    - DataExplorer: CKAN 預設可以透過 [_recline preview extension_](http://docs.ckan.org/en/latest/maintaining/data-viewer.html#data-explorer) 以 GridView 的方式預覽 \`csv\` 及 \`xls\` 資料
    - Text preview：對於 json / html / xml ... 等資料， CKAN 會用 browser 來 preview
        - 例如 html 會顯示在 iframe
    - PDF preview
        - PDF Preview 需額外安裝 Extension, 目前未安裝

- DataStore
    - CKAN 預設只作為資料的 Reference，而不直接將「資料內容」匯入。因此也只能搜尋資料 (DataSet 或 Resource) 的 Metadata，而非內容。
    - DataStore 是一個 CKAN 的 Extension，可將「資料內容」匯入 CKAN 的 postgresql 資料庫中，並且透過介面或 API 取得或搜尋「資料內容」
> g0v 應該暫時用不到 DataStore 因此尚未安裝在測試機
> [name=isacl]


- FileStore
    - 類似 DataStore, 但是是上傳檔案，而非將檔案匯入資料庫
> FileStore 功能未在測試機啟用
> [name=isacl]


## Q & A

### Q1: 與 [http://d](http://data.g0v.tw)[a](http://data.g0v.tw)[t](http://data.g0v.tw)[a](http://data.g0v.tw)[.g](http://data.g0v.tw)[0](http://data.g0v.tw)[v](http://data.g0v.tw)[.t](http://data.g0v.tw)[w](http://data.g0v.tw) 有什麼不同

A:
    [http://d](http://data.g0v.tw)[a](http://data.g0v.tw)[t](http://data.g0v.tw)[a](http://data.g0v.tw)[.g](http://data.g0v.tw)[0](http://data.g0v.tw)[v](http://data.g0v.tw)[.t](http://data.g0v.tw)[w](http://data.g0v.tw) 比較像是 data request 平台，並非用作資料彙整
    ronnywang 提議可將 data.g0v.tw 改為 data-request.g0v.tw  : [Logbot Link](http://logbot.g0v.tw/channel/g0v.tw/2014-04-22/390)
> 那是不是data.g0v.tw的資料都應該forward過來? 就是那邊如果有人提供答案了的話就自動加過來
> [name=sherry l]

> Good idea! 但如果資料來源已經在 data.gov.tw （政府開放資料平台）了，不確定是否要加 (reference) 到 g0v CKAN.
> [name=isacl]

> updated: 我的想法是：若資料已經在 \`data.gov.tw\` 但這是 g0v 專案有使用到的資料。可將之 (用連結 reference) 加到 g0v CKAN。因此 g0v CKAN 可以漸漸成為所有 g0v 專案貢獻者想要找與專案相關的資料、API  的入口網站。
> [name=isacl]


### Q2: 與 [http://data.g](http://data.gov.tw)[o](http://data.gov.tw)[v.tw](http://data.gov.tw) (政府開放資料入口) 有什麼不同

A:
    延伸自前項的討論：
- \`g0v CKAN\` 專為 g0v 專案而設
    - 若資料已經在 \`data.gov.tw\` ，但資料是 g0v 專案有使用到的資料。可將之 (用連結 reference) 加到 \`g0v CKAN\`。因此 \`g0v CKAN\` 可以漸漸成為所有 g0v 專案參與者想要找與專案相關的資料、專案相關 API  的入口網站。
    - 可用 tag 或 group 等方式，標注該資料是被應用在哪個 g0v 專案。

### Q3: 與 [http://campaign-finance.g0v.olc.tw/](http://campaign-finance.g0v.olc.tw/) 會衝突嗎？

A:
    應不會，目前 [http://campaign-finance.g0v.olc.tw/](http://campaign-finance.g0v.olc.tw/) 看起來可用來彙整「政治獻金」還有哪些文件需要去列印出來（推坑），與此平台（整理既有資料）的方向不同。
    簡單的說就是一個認領資料的地方，為了避免有重複認領的情況才設置，或是幫忙補充應該要提早認領的原因等等；討論區的形式比較不正式，在還沒有更好的選擇之前先將就著用？


## 其他相關討論


    請問 此系統 與 OpenStack 的架構與功能
> CKAN 只是一個 web application, 應該與  OpenStack 無關，請問你的問題是？
> [name=isacl]

> 因為你要管理文件與不同性質的東西 也許 OpenStack  系統給你參考
> [name=Jack S]

> [http://lab.howie.tw/2013/03/the-develpoment-trend-of-cloudstack-and-openstack.html](http://lab.howie.tw/2013/03/the-develpoment-trend-of-cloudstack-and-openstack.html)
> [name=Jack S]

> 例如 本站 **第五權電視牆監看「評」台g8v.tv草稿  **
> [name=Jack S]

### [g8v.tv](https://g0v.hackpad.tw/lk9pamtKwyr)可能也有許多 文件要整合某個系統領域

> 所以問問兒已 沒惡意
> [name=Jack S]

> sure, 多討論無妨。我仍不了解 openstack 與 ckan 的關聯性，可否再多提供一些例子？
> [name=isacl]

> 快速認識OpenStack技術架構
> [name=Jack S]

> [http://www.ithome.com.tw/node/81095](http://www.ithome.com.tw/node/81095)
> [name=Jack S]

> 這個系統比較嚴僅有許多相當不錯的套件 供應企業內部資訊管理上的要求 且GOV須考慮資安問題如 中國網軍的殭屍攻擊
> [name=Jack S]

> [http://www.ithome.com.tw/node/81919](http://www.ithome.com.tw/node/81919)
> [name=Jack S]

> [\[技術\] 雲端開發專欄（二）：5分鐘幫你搞懂OpenStack](http://news.networkmagazine.com.tw/magazine/2012/07/05/40782/)
> [name=Jack S]

> OpenStack Swift 雲端存儲架構說明(一) [http://zmanda-taiwan.blogspot.tw/2012/05/openstack-swift.html](http://zmanda-taiwan.blogspot.tw/2012/05/openstack-swift.html)
> [name=Jack S]

> Python中的API：OpenStack裡的最秘而不宣
> [name=Jack S]

> ==**與Python綁定編寫的OpenStack自動化腳本**==
> [name=Jack S]

> [http://www.ibm.com/developerworks/cloud/library/cl-openstack-pythonapis/index.html?ca=drs-](http://www.ibm.com/developerworks/cloud/library/cl-openstack-pythonapis/index.html?ca=drs-)
> [name=Jack S]

> Thanks. I will check it out when I got some time.
> [name=isacl]


