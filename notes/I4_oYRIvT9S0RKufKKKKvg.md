---
tags: g0vernance
---
g0v GitHub 申請規範 v0.1
====================

文件更新歷程
------------
* v0.1 - 2020/1/18 從 [g0v domain guideline](https://docs.google.com/document/d/1g4unx-__fvCc6tPLeniPd_jb5EoIDALXOYkROWyVaTo/edit#) 複製過來，在基礎松做修改成符合 GitHub 需求


範圍
----
本文件處理 g0v 社群需要的 GitHub organization，以便程式碼管理，社群內願意參與配合皆可以加入本 Guidelines

目前相關 organizations 如下：
*  github.com/g0v

專案加入條件
---
* 符合公民科技、開放資料、開放政府、公民參與等 g0v 社群關注相關主題
* 符合開放原碼（open source）授權條款 (OSI-aprroved)
* 符合開放內容（open content）授權 (Free Culture Works)
* 專案所使用的原始資料與資料處理方式應公開並說明
* 不以流量或所搜集之使用者非公開資料盈利
* 符合 Code of Conduct
* 必須要有 README, 包含專案名稱、專案說明、授權方式
* 建議在專案的 Repository 內加入 [g0v.json](https://github.com/g0v/g0v.json) 文件
* 有前端頁面可選擇加掛 g0v 的 Google Analytics
* 有前端頁面可選擇加掛 g0v logo 與導回 g0v.tw 與相關其它 g0v 專案的連結
* 有前端頁面可選擇加掛 g0v banner (https://github.com/g0v/banner)

專案命名原則
----------
TODO

申請成為 member 機制
------------
1. 需要在 https://github.com/g0v/nobody 送出 Pull Request 申請
2. Pull Request 內必須以 members/{GitHub 帳號}.md 為檔案
3. 檔案格式如下：
```
- 我是 {xxx}
- 我的三個關鍵字是 {xxx}, {xxx}, {xxx}
- 我已同意 [g0v 宣言](https://g0v.tw/zh-TW/manifesto.html)
- 我已同意 g0v GitHub guideline
- [選填] 我的 Slack 帳號是: {xxx} 
```
4. admin 會在 24hr 內加入 member (若在黑客松現場為 1hr 內)

注意事項：
1. 三個關鍵字請盡量以關注議題或技能為主，例如：環保、假新聞、PHP、Python、前端、後端、設計...
2. 可在後面補上更多自我介紹

申請需要 admin 權限的功能
----------------------
例如 master branch protection 或是刪除 repository
流程：
1. 到 https://github.com/g0v/nobody 開 issue 說明需要的功能及原因

admin 權利義務
------------
* member 申請
    * 需要在 24hr 內審核 member 申請
    * 大松現場需要有 admin 能即時處理
    * admin 審核，符合內容要件即可
* 處理惡意 member 檢舉
    * 在 48hr 內有兩名 admin 同意，無人反對即移除 member
* 處理需要 admin 才能做的事
    * 在 48hr 內有兩名 admin 同意，無人反對即執行
* 需要開啟兩步驗證

admin 清理
-----------
* 在 x 月 x 日 以前 admin 需要在 https://github.com/g0v/nobody 的 admin/{GitHub 帳號}.md 留下自我介紹。

