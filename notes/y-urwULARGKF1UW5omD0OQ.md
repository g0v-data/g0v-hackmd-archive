---
title: "g0v.json spec"
tags: hackpad
---

# g0v.json spec

> [點此觀看原始內容](https://g0v.hackpad.tw/c07sSfauWSc)


### Background

g0v project 很多, 常常需要回答像這樣的問題
- 有哪些 project?
- 這個 project 好有趣, 我要去哪裡找它的網頁/文件/程式?
- 我是文字工作者, 有哪些 project 需要我?
- 我寫 c++ 有沒有哪個 project 適合我?
- 有哪些相關的 project?

所以我們需要一個方式登錄各 project 的 metadata, 方便查詢、搜尋。目前設計出來的解法是大家在自己的網站上放一個 g0v.json。再去 [http://hack.g0v.tw/project](http://hack.g0v.tw/project) "新增專案"
(譬如在 git repo 的根目錄放 g0v.json)

更詳細的規畫、討論，請見 [g0v hub](https://g0v.hackpad.tw/9IbgS6xfHZA)
> 要怎麼樣讓上面這個連結改成彈出新視窗？
> [name=Jhang J]


### 範例

[https://github.com/g0v/hack.g0v.tw/blob/master/g0v.json](https://github.com/g0v/hack.g0v.tw/blob/master/g0v.json)
更多例子: [https://github.com/search?q=path%3Ag0v.json&type=Code&ref=searchresults](https://github.com/search?q=path%3Ag0v.json&type=Code&ref=searchresults)
> 更多例子的網址找不到東西。
> [name=Jhang J]


### Tags

其實所有的欄位都沒有嚴格限制, 這邊列的只是參考/建議
- author 主要作者
- status 專案狀況
    - planning, pre-alpha, alpha, beta, production, stable, mature, inactive
- name 英文名, 一般為簡短的代號 (不含 .#$\[\] 等符號)
- name_zh 中文名
- description 英文描述
- description_zh 中文描述
- homepage 網頁
- thumbnail 縮圖 (TODO 建議大小?)
- document 說明這個 project 的文件、網頁、或 hackpad
- repository 工作資料區
    - 這欄位主要是給程式專案使用, 表示 code 公開的 url.
    - 其他類型的專案也許是 google doc 或是 dropbox folder 之類. 譬如的圖庫、照片、資料檔
- licenses 專案授權
    - 譬如 [MIT](http://mit-license.org/), [CC0](http://creativecommons.org/choose/zero/?lang=zh_TW), [CC-BY](http://creativecommons.org/licenses/by/3.0/tw/) 等等.
    - 若是少見或是特別的 license, 請加上 url, 譬如 [http://g0v.mit-license.org/](http://g0v.mit-license.org/)
- keywords 專案關鍵字
    - 目前沒有限定哪方面的關鍵字。
    - 可以是專案性質、解決哪方面的問題，也可以是用到的技術、技能。
- audience 這個專案的目標群。
    - 譬如 contributor, public
- products 這個專案的產出
    - 譬如 website, app, library, api, data, script
- projects 屬於什麼 prooject. (可以多選)
    - 譬如 kuansim-backend 屬於 kuansim 這個 project, moedict-webkit 屬於 3du
    - 填寫的 project 不一定要「實體存在」，譬如上面的例子，不一定有另一個 g0v.json 的 name 寫 3du
    - 若是一群 projects 的主 project, 可以填自己的 name
- contributors 參與者
- needs 需要哪種人、技術支援
    - 譬如 designer, writer, programmer, money

> 之後可以用 [json-ld](http://json-ld.org/) 來做格式的驗證
> [name=Superbil]


