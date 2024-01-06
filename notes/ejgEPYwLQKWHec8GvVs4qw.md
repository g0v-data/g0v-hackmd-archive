---
title: "「國家教育研究院雙語詞彙、學術名詞暨辭書資訊網」資料庫下載規劃"
tags: EY,hackpad
---

# 「國家教育研究院雙語詞彙、學術名詞暨辭書資訊網」資料庫下載規劃

> [點此觀看原始內容](https://g0v.hackpad.tw/ZFtVX8RAqjK)


## 2015-03-19 更新

Location: 國家教育研究院三峽院區
Participants: 林慶隆主任、au
- 2014-12 提到的定期 .sql 匯出功能已請廠商報價，預計大約五萬左右，應該還不需要群募。 XD
- 國教院原本就有開放資料集用的資料夾（wd.naer.edu.tw/open/）：
    - [http://wd.naer.edu.tw/open/naerprp.csv](http://wd.naer.edu.tw/open/naerprp.csv)
- 考量到國發會現已允許登錄 Excel 及 SQL 資料集（[2015-01-17](https://g0v.hackpad.tw/Data.g0v.tw-ng-LA2MpOEjraI)），建議使用 data.gov.tw 平台登錄。
    - 資料授權依開放平臺資料使用規範辦理。
- Daily DB Dump 放置於 /open/ 下時，仍可設置流量限制或分流。
    - 待 TODC 或 SheetHub 等外部映射啟動後，應推薦社群使用外部映射作為資料來源。
> 像是最近公布的[國語辭典](https://sheethub.com/moe.edu.tw/%E5%9C%8B%E8%AA%9E%E8%BE%AD%E5%85%B8%E7%B0%A1%E7%B7%A8%E6%9C%AC)，我們就更新在 SheetHub.com 上面
> [name=Muyueh L]


> 請問這件事情有我後續可幫忙的地方嗎？廠商是否已可定期匯出 SQL？ ~2017.08.27
> [name=isacl]


## Meeting minutes: [#d](https://g0v.hackpad.tw/ep/search/?q=%23date&via=ZFtVX8RAqjK)[a](https://g0v.hackpad.tw/ep/search/?q=%23date&via=ZFtVX8RAqjK)[t](https://g0v.hackpad.tw/ep/search/?q=%23date&via=ZFtVX8RAqjK)[e](https://g0v.hackpad.tw/ep/search/?q=%23date&via=ZFtVX8RAqjK)[-2014-12-09](https://g0v.hackpad.tw/ep/search/?q=%23date&via=ZFtVX8RAqjK)

Location: 國家教育研究院編譯發展中心台北院區
> 以下為會議時的初步共識，細節需等待辦法訂立後才知道。
> [name=isacl]


### 摘要


此專案的最終目標為：名詞翻譯一致化。
中心持開放態度，不打算限制資料的使用、修改、散布。以下的「資料授權」與「db 下載申請辦法」目的僅在於讓開發者了解其使用、修改、散布的權利，避免濫用（大量下載破壞伺服器等等），並且協助相關單位計算資料使用的績效。

「資料授權」與「db 下載申請辦法」將對所有的使用者一視同仁。（不因為國籍、使用目的等有不同的規範）



### DB Dump

1.  編譯發展中心擬定「資料授權」與「db 下載申請辦法」
    1.  「資料授權」待中心人員擬定。
    2.  「db 下載申請辦法」已確定會有以下幾個欄位
        1.  姓名 / 單位
        2.  Email
        3.  access ip
        4.  使用目的
2.  編譯發展中心聯絡廠商，請廠商在「下載專區」之下，區分為「一般使用者」（即原 excel 下載）與 「開發者專區」
3.  請廠商在「開發者專區」加上「db 下載申請辦法」並附上線上申請表格 （google form 可）
4.  請廠商設定 daily db dump ，在開發者專區提供固定的下載路徑，並限制連線 IP。
5.  當有開發者申請時，編譯發展中心聯絡外包廠商，請廠商設定允許下載的 IP. (或自動化)
6.  如果上述步驟，廠商不便協助修改。中心打算提供 ssh login 權限給 g0v 特定人員，由 g0v 人員協助設定 daily db dump。（isacl 建議：如對遠端操作有疑慮，可接受限制在台北院區現場操作，操作時有中心的人員在場擔保。）


### 詞彙 Feedback

現有的詞彙 feedback 機制為 [forum](http://terms.naer.edu.tw/forum/) 。使用者在網站上登入後，直接留言給予建議。使用率非常低。

當 g0v 下載了 db dump 後, 也可自行製作 feedback 介面來蒐集 feedback. 再把資料彙整給中心。
（中心需經由一定的程序後才正式發佈更新）


### API 化後，可能的發展

- 製作 browser extension, 在瀏覽網站時，自動翻譯學術名詞
> 有些醫學名詞的翻譯，跟衛服部所開發的[中文化病例字彙查詢](http://mrc.hatw.org.tw/)蠻相關的。有興趣也把這些內容拿來對照嗎？可以牽到裡頭認識負責人的一位醫學院畢業的替代役學生來說明狀況XD
> [name=上官良治]

- 結合萌典
> 有機會也一併dump到另外一個開放資料庫上嗎？我對資料庫不熟，但我知道最近wikidata跟歐盟打算要合作，應該可以接
> [name=上官良治]

- 改善 feedback 流程

### Others

網站上的幾個名詞解釋：
- 學術名詞
- 雙語詞彙
    - 機關建議詞彙 \- 由各機關建議，但未經完整的審核校對程序
    - 公告詞彙 \- 已經過完整程序後發佈

