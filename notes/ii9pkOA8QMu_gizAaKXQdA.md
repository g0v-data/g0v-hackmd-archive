---
title: "localwiki export / import"
tags: localwiki,hackpad
---

# localwiki export / import

> [點此觀看原始內容](https://g0v.hackpad.tw/YghsHsKGadh)

_"Our dream is for LocalWiki to not only be the best way to learn and share knowledge about your local community, but also to be a platform upon which a countless civic and locally-relevant applications will be built. In the same way that OpenStreetMap has become a platform for open, cartographic knowledge,_ **_we hope that LocalWiki can become an open, global platform for local knowledge_** _and human experience--places, people, neighborhoods,...everything!"  -_ [_API Documentation_](https://localwiki.org/main/API_Documentation)

localwiki 算是親切的圖文書寫介面，適合一般大眾共筆編輯，也很方便建立地理資料，希望完備平台匯出以及匯入功能，讓一般書寫者可以批次匯入，也可以讓共筆成果打包，作為其他應用的素材。

## 專案目標

匯出 localwiki 的內容（文字、表格、圖片、地理資料...）
- issue: [localwiki/localwiki#752](https://github.com/localwiki/localwiki/issues/752)
- [https://localwiki.org/api/v4/maps/](https://localwiki.org/api/v4/maps/)

匯入
- issue: [localwiki/localwiki#754](https://github.com/localwiki/localwiki/issues/754)
- 欄位型資料，匯入時如何判釋欄位內容組成 localwiki 的標題或內文
- 圖片
    - 圖片僅有檔案連結
    - 圖片檔案批次上傳

### 討論

- 目前需要 coder 才能夠處理
- 匯出結果為何
    - 格式
        - GeoJson ? 方便其他應用
        - kml ? 方便 google earth 使用者瀏覽運用
        - 圖片怎麼辦？
    - 匯出時若需要欄位化
        - 內文匯出時，是否有可能匯出為欄位化，或是說若希望匯出時能匯出成欄位，那麼 localwiki 頁面上該如何編寫。例如內文中有「營業時間：am9:00-pm5:00」，能否於匯出時建立「營業時間」，「am9:00-pm5:00」
- 授權面向
    - 圖片與文字的授權版本若不一致，該如何表現在匯出的成果中


## 實作參考
- 「防災地方誌改過的 localwiki 有匯入匯出的功能耶，在 lowiki.org。匯出格式有 CSV、TXT、KML；匯入格式有 CSV。」
    - 轉自：https://www.facebook.com/groups/localwiki/permalink/1820025584679467/

