---
tags: g0v-summit, 2020
---
# Summit 網站技術架構提案

使用 [Nuxt.js](https://nuxtjs.org/) ，一個以 Vue 為基礎，加上預設的資料夾結構、Pre Rendering 的框架，適合拿來當作需要 SEO 的純前端方案。
1. 選用 Nuxt + [SPA mode](https://nuxtjs.org/api/configuration-mode)，避免 SSR (server side rendering) 需要的額外複雜度，例如要避免在 SSR 階段使用瀏覽器獨有的操作，包含使用 window
2. css 建議使用 scss 
3. html 建議使用原生 html
4. 使用 dotenv 支援環境變數和 .env 檔案
5. 文字、圖片的來源：
   1. 結構化資料，如議程、贊助商等，使用 Airtable 或其他可以用程式，自動匯出為 json 的工具
      1. airtable token 或其他的認證資訊，可存在 .env 裡
      2. 用 `npm run sync:db` 下載新資料
   2. 各種文案，例如首頁文案、交通資訊，以 Markdown 寫在 g0v Hackmd 上，用 [Hackmd CLI](https://github.com/hackmdio/hackmd-cli) 匯出成 markdown 使用
      1. 每篇 hackmd 都是一則文案的一種語言，也就是說，每則文案都要有兩篇 hackmd
      2. 文案可用 hackmd book mode 整理
      3. 每則文案對應的 hackmd ID ，可用 yaml 記在 git 裡
      4. 使用 [vue-markdown](https://github.com/miaolz123/vue-markdown), `<vue-markdown>{{$t('markdown')}}</vue-markdown>`
      5. 用 `npm run sync:article` 下載新資料
      6. [**待解決**] hackmd 的權限管理，如果文案變多時，要加人進來寫會變得很麻煩，revision control 也沒有 git 清楚
   3. 幾乎不會更動的資料，如選單，可直接寫在 nuxt 裡
   4. 為了確保網站資料的穩定，圖片也須下載
   5. 以上各種資料皆要包含華英雙語，使用 [nuxt-i18n](https://nuxt-community.github.io/nuxt-i18n/basic-usage.html) 判斷
   6. 用機器人每日定時同步所有內容到 git 裡
6. SEO、社群分享
   1. 使用 [nuxt 內建功能](https://nuxtjs.org/api/pages-head/)
   2. 除了手動塞一堆 tag 外，可以看看 [Nuxt PWA Meta](https://pwa.nuxtjs.org/modules/meta.html#options) 能否讓事情簡化些，不然就要自己寫 mixin 了～
   3. 議程相關網頁，要使用正確的 h1 和把資訊塞入 meta tag

## 1. 綁定非資料庫後端的靜態網站
```
**User Story**
身為 Summit 網站維護者，我想要使用純前端解法，減少網站長期營運成本，例如照顧伺服器
```
1. 但網站須呈現許多結構化，且有可能頻繁修改的資料，包含：
   - 贊助商
   - 議程
2. 其中議程的不確定性較高，要看今年的議程規劃，才能決定資料結構，而且可以遇見，越接近開幕時間，變動頻率越高，因此需要結構化的方式描述它，才能減少犯錯機率 XD
3. 基本要求：
   1. 假設資料來源是某個已經結構化的資料庫，例如 MongoDB / Airtable / Google Spreadsheet
   2. 提出下載資料、將資料轉為網頁的工具和大概流程
:::info
參見 5.1 + 5.5
:::

## 2. 測試、正式雙站架設
```
**User Story**
身為 Summit 內部成員，我想要維護開發網站 -> 測試網站 -> 正式網站，的開發流程，
- 讓開發時可以即時看到結果
- 讓所有工作人員可根據測試網站給回饋
- 讓所有人可以看到檢查過得正式網站
```
1. 基本要求
   > IJS 有 FTP 可以當測試站，給所有工作人員檢查，再推上 master[name=mango]
   1. 整個網站可以直接在工程師的電腦裡跑起來，盡可能連網站資料都能放到開發機中，呈現完整內容
   2. 網站要能一行指令發佈到測試網域，並盡量使用獨立的 branch ，方便區分穩定程度
   3. 網站要能一行指令，將測試 branch 的東西，發佈到正式網域，並盡量使用獨立 branch ，方便區分穩定程度

:::info
初步想法：
1. 採用 [Gitlab flow](https://about.gitlab.com/blog/2014/09/29/gitlab-flow/)
   - feature branch + master branch + staging branch + production branch
2. 用 [summit2020](https://github.com/g0v/summit2020/) 的 github page 當 staging
3. 用 [summit.g0v.tw](https://github.com/g0v/summit.g0v.tw/) 當 production ，但需要釐清目前 travis CI 的發動條件
:::

## 3. 雙語切換
```
**User Story**
身為 Summit 網站的不同語言的使用者，我想要有方便的語言切換、記憶功能，
讓我無論是第一次進來、日後瀏覽，或是想要分享網站給其他人時，
都可以使用同樣的語言設定
```
1. 基本要求：
   1. 可在網頁上一鍵雙語切換
   2. 切換後此瀏覽器記住語系設定
2. 加分：
   1. 搜尋引擎友善的雙語設定
   2. 分享時，會連語言設定一起帶走 aka 網址要包含語系
:::info
參見 5.5 ，`nuxt-i18n` 支援上述功能，網址規則為： `/<lang>/route/to/a/page`

但需要真的踩過，才知道洞在哪兒
:::

## 4. SEO + Social Share
```
**User Story**
身為 summit 營運者，我想要讓我的網站更容易被搜尋、社群分享，
讓大家的貢獻更容易被其他人找到與分享
```
1. 基本要求：
   1. 基本 SEF ，包含標題、網址、RWD、ssl，所有頁面都要靜態生成（雖然 google 目前已經可以偷跑 js XD）
   2. 支援 open graph 以及 twitter 分享，可設定每頁、每項議程的網址、縮圖以及內容
2. 加分：
   1. 其他 SEO 相關功能
2. 參考套件
    - https://www.npmjs.com/package/nuxt-seo

:::info
參見 6.*
:::

## 5. 麻瓜（？）友善的文案共筆機制，方便共同編輯雙語文件 + 網站上稿，和第一點有關
```
**User Story**
身為 summit 網站的文案提供者（議程組、行銷組等），
我想要有一個方便編輯議程以外的文案的地方，包含中英雙語，
讓我就算不懂程式、github，也可以快速編修文案，減少與工程師來回溝通的時間
```

1. 基本要求
   1. 提出一套工作流程，盡可能讓文案提供者可以使用簡單的文字編輯器，例如 Hackmd / Spreadsheet / Airtable / Wordpress 等等，編修議程以外的所有網站內容
   2. 編輯器須支援中英雙語，讓程式可以在相對的語系設定中，顯示該語系的內容
   3. 用編輯器編輯後的文字，可以半自動地更新到網站上，也就是要能用單一指令就完整部屬

:::info
參見 5.2 ~ 5.6
:::

## 6. 回應式網頁設計 (RWD)
1. 為了手機與 SEO ，RWD 一定要作的～

:::info
很想推銷 [tachyons](http://tachyons.io/) ，因為很適合拿來作客製化程度高的 UI ，但不熟的人上手有點門檻 XD 
:::

## 7. CICD
```
**User Story**
身為一個網站開發者，我想要讓網站有 CICD ，
這樣才其他人想更新網站內容時，就不用再來騷擾我了
```

1. 基本要求：
   1. 有新的 commit 進到 test branch 或 production branch 時，自動發佈到網頁上
   2. 有新的內容出現時，包含議程與非議程的文案，可以自動或辦自動地產生新 commit ，或直接發佈到網頁上
    
:::info
TBD ， 如果所有步驟都可以用指令執行，那就只剩整合的問題，風險相對低
:::
       
## 8. 測試、正式網站的錯誤追蹤工具
   ```
   **User Story**
   身為一個網站開發者，我想要在測試與正式網站，增加錯誤追蹤工具，
   如此一來，才能知道有哪些開發時沒有處理到的錯誤正在發生
   ```
   1. 基本要求：
      1. 測試、正式網站要埋錯誤追蹤工具，例如 Sentry 
      2. 錯誤要能被網站組的所有成員看到，也可使用 slack 通知（所以不能只是 Sentry ，或要付錢）

:::info
發現 Sentry 其實有 [Open Source plan](https://sentry.io/for/good/) ，包含每月 500k events + 無限帳號數，可以用 g0v summit 2020 的名義來申請看看。
:::

