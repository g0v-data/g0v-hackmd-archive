# 網頁靜態化方案評估

資料庫為基礎的網站適合用來做資料的管理，但同時提供公開瀏覽介面時常常成為效能瓶頸，因此普遍會建議公開瀏覽介面試著讓內容靜態化，以下整理一些可用的解決方案。

## 砍站軟體
對於一個已經存在的網站，最簡單的方式就是透過爬蟲( web crawler )取得整個網站的公開副本，只是這個作法往往需要很長時間

1. [wget](https://superuser.com/questions/970323/using-wget-to-copy-website-with-proper-layout-for-offline-browsing)
  `wget --mirror --convert-links --adjust-extension --page-requisites --no-parent http://example.org`

2. [HTTrack Website Copier](https://www.httrack.com/)

## 靜態頁面產生器

1. [Jekyll](https://jekyllrb.com/)
   因為 Github Pages 支援所以有相當龐大的生態系，相關文件也做得很完整、容易上手，許多需求可以比較容易找到第三方開發的元件支援，只是因為主體架構聚焦在個人的 Blog ，所以要做其他類型網站使用需要比較多調整。
2. [Hugo](https://gohugo.io/)
   網頁的編譯處理速度很快，在一個約 60 萬頁的編譯工作，時間幾乎是 Jekyll 的 1/10 ，適合頻繁更新的網站使用；格式支援廣泛，但是文件與技術細節相對艱澀許多，有些執行上的問題光靠錯誤訊息不容易找出癥結，進入門檻高一些。
   
## 託管

1. [Github Pages](https://pages.github.com/)
   因為 Github 在開發社群的普及，這個延伸的網站託管服務也累積了龐大的使用者群，已經是個很成熟的服務，只是在台灣尚未落地，遇到國際頻寬塞車時網站服務效能也會打折扣。個別網站容量上限為 10GB ，個別 commit 太多異動會被拒絕 push ，佈署時間超過 10 分鐘也會直接被中斷而持續佈署失敗。
2. [Cloudflare Pages](https://pages.cloudflare.com/)
   以服務速度著稱，只是個別網站只接受最多 20000 個頁面。
3. [Google Cloud Storage buckets](https://cloud.google.com/storage/docs/buckets)
   試著傳送到台灣(asia-east1)伺服器， 8.3GB/542674 個檔案，傳輸費用 2.69USD ，每月每 GB 會收取 0.02 USD 費用，網路使用另計。 gcloud console 有提供 rsync 功能只傳輸異動部份，還算方便。