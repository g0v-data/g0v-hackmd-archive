---
tags: vtaiwan
---
# vTaiwan 的 Ghost 要怎麼管理

## 前情提要
因為現在的 vtaiwan.tw 有點太舊了，甚至還有現在沒辦法 function 的功能，有鑒於目前 vTaiwan 的行動都是以工作坊、會議、或文筆為主，頂多有時候借用開源世界的審議工具去討論特定議題。因此 Tofus 決定另外開發一個新版的 vTaiwan 網站

## 原本的方案（vTaiwan+Astro）
專案連結：https://vtw.zeabur.app/
原始碼連結：https://github.com/Tofuswang/vtaiwan-neo

這個版本是用部落格前端框架 [Astro](https://astro.build/) 架構而成的，架構於後端中介服務 [Zeabur](https://zeabur.com/zh-TW)


:::info
為什麼最終沒有採用這個方案呢？

原本 Tofus 試算用 vibe coding 製作，但因為 Tofus 目前對後端不太熟，所以在修 cms 的時候發現它很容易壞掉（還有帳號密碼功能總是搞不定＠＠，看來還要多加修煉），所以原本想說用 git push 的方式，但是學習門檻太高，於是作罷
:::

## 現在的方案（vTaiwan + Ghost）
目前的方案使用了後端中介服務 [Zeabur](https://zeabur.com/zh-TW) 的 Ghost 模板

### 使用 Ghost 方案的優點
- 成本低
    - 每月 5 usd 起
- 轉移容易
    - 只需轉移到下一位管理員的 zeabur 的帳號即可
- 具有可及性高的協作功能
    - 大家都可以到 https://vtaiwan.zeabur.app/ghost/ 進行協作
- 強大的 cms 功能
    - 基本上功能跟 https://ghost.org/ 相同，非常強大

## 網站上需要呈現的內容
- 讓人眼睛一亮的內容
- 讓人快速理解的內容

## 頁面內容

### 貢獻者
- 每個人的頭像、名字、個人網站、大概負責的工作
- 頭像或許可以使用 gravatar

### FAQ（需要徵集意見 or 夥伴一起撰寫）

### 審議方法（有沒有需要）

### 關於我們
- ~~新聞報導~~

### 多平台備份
- substack

## 待討論事項
- FAQ 該如何共編或收集意見
- 最新版的審議方法流程圖
- 審議工具的經驗分享（可單獨成部落格）