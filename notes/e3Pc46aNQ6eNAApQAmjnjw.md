# 網頁靜態化方案評估

資料庫為基礎的網站適合用來做資料的管理，但同時提供公開瀏覽介面時常常成為效能瓶頸，因此普遍會建議公開瀏覽介面試著讓內容靜態化，以下整理一些可用的解決方案。

## 砍站軟體
對於一個已經存在的網站，最簡單的方式就是透過爬蟲( web crawler )取得整個網站的公開副本，只是這個作法往往需要很長時間

1. [wget](https://superuser.com/questions/970323/using-wget-to-copy-website-with-proper-layout-for-offline-browsing)
  `wget --mirror --convert-links --adjust-extension --page-requisites --no-parent http://example.org`

2. [HTTrack Website Copier](https://www.httrack.com/)

## 靜態頁面產生器

1. [Jekyll](https://jekyllrb.com/)
2. [Hugo](https://gohugo.io/)