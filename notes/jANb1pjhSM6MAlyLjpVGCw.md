# {也生官網} 只提供資料API，大前端就交給你們了

## 專案簡介
你的下一個官網，何必是官網？也可以是網頁、App、Line Bot...。但對於靠熱血的專案來說，維護上是大問題。
亂丟就是浪費，回收就是資源（吉安鄉回收車的 slogan）。透過對現有 g0v 專案的回顧，找出並鼓勵將後端資料轉換為結構化的資料格式，讓公有資料容易在各種使用者介面（網頁、App、Line Bot...）上重用。

## 緣由

g0v 活動挖出了許多公用資料，各種網站、訊息、散落各處，有待回收利用。
例如看到 g0v 產品入口頁模板樣式還不錯，但可見專案後續維護人力的困難。

如果能讓非程式人員提供格式化資料，而程式人員專注在爬梳出資料/製作各種前端 (Web、App、Line bot) 上呈現這些資料，透過更換資料集，同樣的前端也可用來展示未來或過去的資料。這樣是不是可以更好的共用有限的人力？

## 要解決的問題
headless 易於共用的結構化資料格式
permissionless 不同意見的人只要在其他地方提供相容的資料格式，使用者也可以用各種開發好的前端查看
maintenance 資料長期維護的容易度 / 激勵方式

## 預定使用者
（成品要給誰用、在什麼場合用、怎麼用）
網頁/App/Bot開發者：提供 JSON 格式的資料集，網頁/App/Bot開發者可以專注前端的展示
非程式人員：根據結構化資料，提供資訊
使用者：可在相容的頁面上查看結果

## 預定功能
（成品要有哪些功能來滿足上述使用情境）
更新 2022 縣市長選舉人資訊到 WikiData，建立格式化範本 -> 網站 -> 提供查詢。

## 現有類似專案
（現成的是否可以直接使用？或者有什麼不足之處？國外專案可參考？）

- 柯文哲[野生官網](https://slides.com/tonyq/community-and-v-world-46-57/fullscreen)
沒有後續維護
- [EveryPolitician](http://everypolitician.org/taiwan/legislative-yuan/term-table/9.html) 全球各地的政治人物
https://github.com/everypolitician/everypolitician-data/tree/master/data/Taiwan
沒有後續維護
- http://vote2014.g0v.ronny.tw/
沒有App端
- 選舉黃頁 https://github.com/kiang/elections
沒有App端
- [Wikidata](https://m.wikidata.org/wiki/Wikidata:WikiProject_Taiwan) 提供結構化資料

## 相關專案
（衍生自某專案/衍生出某專案/API串接自某專案.）

## 授權方式
（程式碼部分如 MIT/BSD /文件部分，如 CC-BY）

## 使用資料
（會使用到哪些資料來源、各是什麼授權）

## 專案目前狀態
（構想 / 規劃 / 雛形 / 實作）
- 構想 / 搜集資料 / 諮詢相關 channel (wikidata)
- 簡報 https://docs.google.com/presentation/d/1wTKeY8iWl4W2Yiwh2gDW8d62s_v6HPAe6a6EYO0dFVU/edit?usp=sharing
- 目前關注於編輯/開放 API 與重用
- 參考 Headless Content Management System 的作法，提供後端編輯與資料 API（JSON）。

## 利益揭露
（牽涉到哪些組織團體、有哪些已知的或潛在的金錢或物質或無形利益報酬）


## 徵求協作者

發起人/拋磚人：gasolin
NeedsWriter: 需要文案幫手（撰寫基本資訊、報導專案etc）
NeedsDesigner: 需要介面設計
NeedsData: 需要資料（擷取、清理）
NeedsTech: 需要技術支援（程式、架站 etc)
NeedsProcess: 需要幫忙設計作業流程
NeedsTalkingToRealPerson: 需要有人幫忙和其他機關聯絡

根據參與者的性質，往對應的偏向發展

## 實作細節（非技術背景可跳填）

### 協作工具
github repo：
hackfoldr 工作資料夾網址：
google drive 共用資料夾網址：

### 進度與 to-do
僅供參考
product planning（recommended procedure from justin lee / 李易修）
strategy
scope
structure
wireframe
visual
web front-end
web back-end
ui / visual design


## 成果展示（規劃文件、雛形/草稿、原型/初稿、正式發佈/完稿）

