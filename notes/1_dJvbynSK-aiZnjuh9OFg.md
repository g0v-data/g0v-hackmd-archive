---
title: "Open Data 上架檢核流程"
tags: hackpad
---

# Open Data 上架檢核流程

> [點此觀看原始內容](https://g0v.hackpad.tw/SA806TyuPOb)

> 官方名稱叫做「政府資料品質提升機制」
> [name=Leo C]

> 目前規劃上為於資料集上架時即進行檢查，以降低產製報告時的系統負擔並提升效率。
> [name=Leo C]



以下內容是供國發會 data.gov.tw 參考由各部會資料承辦人上架資料時，能夠怎麼樣檢核資料是否乾淨\[

- \[A\] 承辦人上傳資料
> 這裡會需要強調 data.gov.tw目前沒有保留資料的空間，因此會是對資料資源連結進行下載驗證
> [name=Leo C]

    - 如果是 zip  rar 7z 檔，到 \[B\]
    - 如果是 json 檔，到 \[C\]
    - 如果是 xml 檔，到 \[D\]
    - 如果是 csv 檔，到 \[E\]
    - 如果是 xls, xlsx, ods 檔，到 \[F\]
    - 如果是 pdf, doc, docx 檔，到 \[Z\]
    - ※如果是 API, WebService
    - ※如果是 kml, kmz, shp 檔
    - ※如果是 txt檔
    - ※如果是 其他檔，直接到 \[Z\] ?
- \[B\] 遇到壓縮檔 (zip, rar, 7z...)
    - 解壓縮開來，如果裡面只有一個檔案，以這個檔案回到 \[A\]
    - 如果解壓縮有多個檔案，進到 \[Z\]
        - PS: 這邊可以列入一些檔名忽略清單，例如 README.txt schema.csv ... 之類的，去掉這些檔案後還有多個檔案才需要進入 \[Z\]
> 若是像 [http://data.gov.tw/node/6380](http://data.gov.tw/node/6380) 這種的，也是直接歸類為\[Z\]嗎?
> [name=Leo C]

- \[C\] 遇到 JSON
    - 進行 JSON syntax 檢查，如果檢查失敗直接進到 \[Z\]
> JSON跟XML是不是也會遇到編碼問題?
> [name=Leo C]

> 不會有編碼問題，因為 JSON 和 XML 的標準就是 UTF-8 ，如果沒照標準改用其他編碼，就直接視為不合法JSON 或是 XML
> [name=Ronny W]

> 恩恩，這部分有多少不合格可能要先評估看看
> [name=Leo C]

    - 如果 syntax 檢查沒問題，進到 \[C1\]
- \[C1\] 乾淨 JSON
    - 內容檢查，如果是 table 格式的 JSON ，將之轉成 csv ，並且把欄位取出進到 \[Y\]
    - 不認得的 JSON 格式，就進到 \[X\]
- \[D\] 遇到 XML
    - 檢查如果是 xlsx 或是 ods 的 XML 檔，進到 \[F\]
    - 進行 XML 文法檢查，如果檢查失敗直接進到 \[Z\]
    - 如果 syntax 檢查沒問題，進到 \[D1\]
- \[D1\] 乾淨 XML
    - 內容檢查，如果是 table 格式的 XML ，將之轉成 csv ，並且把欄位取出進到 \[Y\]
    - 不認得的 XML 格式，就進到 \[X\]
> 這邊或許可以檢查是否是特定格式的 XML ，就我所知預決算好像有標準 XML 格式，他不會是 table 格式，但是也可以額外標記出來，供預決算研究人員用
> [name=Ronny W]

> 這的確是個問題，如果是非table格式的XML到底算不算標準? 又主要欄位應如何判別?
> [name=Leo C]

- \[E\] 遇到 CSV
    - 強制作一遍 utf-8 轉 big5 再轉回來，如果內容不變表示確定是 utf-8 CSV ，進到 \[E1\]
    - 如果確定是 big5 csv ，把他轉成 utf-8 csv ，再進到 \[E1\]
- \[E1\] 處理 UTF-8 CSV
    - 把第一行欄位抓出來檢查，如果有欄位是純數字內容(Ex: 「台北市,123,456」或是有重覆 「縣市,金額,鄉鎮,金額」 就視為有錯誤，到 \[Z\]
    - 第二行之後每一行檢查，如果有哪一行欄數大於第一行，就視為有錯誤，到 \[Z\]
    - 從第二行開始對每一列各自檢查，如果有哪一列有 95% 都是純數字，但是少數幾行卻有非純數字情況，有可能是把「總計」這種資訊也列入了，可能是不乾淨的 CSV ，到 \[Z\]
        - PS: 這一步驟其實有可能誤判，最好再加上人工檢查
    - 沒發現錯誤，到 \[Y\]
- \[F\] 遇到 xls, ods
    - 檢查是否有用到合併儲存格、繪製框線或是儲存格背景色，或使用公式，有以上情況，就進到 \[Z\]
    - 如果有使用多分頁的話，就進到 \[Z\]
    - 如果沒有以上情況，表示是個轉成 csv 也不會流失資訊的 xls 或 ods，就把他轉成 csv 之後進到 \[E\]


完結動作
- \[X\] 將這個檔案上架，不視為不乾淨資料，但是標記為非 sheet 格式資料，不做額外處理
    - 使用者仍可下載承辦上傳的資料
- \[Y\] 將這個檔案上架，標記為乾淨表格，並把資料轉成 CSV 存在資料庫中
> 也就是說，這裡的CSV都只會是UTF-8囉?
> [name=Leo C]

> Yes ，因為在 \[E1\] 時已經都轉成 UTF-8 了，如果使用者是 Excel 需求的話，可以下載轉出來的 ods
> [name=Ronny W]

    - 使用者可下載承辦上傳的原始資料
> 這裡會區分為原始資料跟轉換後資料? 那轉換後的資料資源是就放在我們平台囉?
> [name=Leo C]

> 加這個是避免平台處理過程誤判將原始資料的一些資訊流失掉，轉換後的資料就是存在平台上面了
> [name=Ronny W]

> 那平臺會需要規劃容量放東西了... 以一個資料資源10MB來估，先前看有到30,000筆資料資源，這樣應該要估到300GB的容量，依照這個發展速度，上限應該抓在600GB?
> [name=Leo C]

> 20161026更新：會內仍堅持不保有資料資源以迴避資料同步問題。
> [name=Leo C]

    - 使用者可下載轉成 CSV 的乾淨資料
    - 平台提供自動轉成 xls, ods, json, xml 等功能，另外可以自動取出欄位列表帶入平台的欄位說明中
> 這裡還是要表達會內想遏殺xls的立場XDrz
> [name=Leo C]

> btw, 如果都以CSV為基礎的話真的是很好處理，這樣轉換JSON, XML都不會是問題。但轉ods我沒找過工具就是
> [name=Leo C]

> 還有一個問題，產製後是一樣要放在平臺? 還是即時轉換呢? 這會大幅影響到平臺規劃。
> [name=Leo C]


- \[Z\] 將這個檔案上架，但是標記為平台無法解析，不做其他處理，並在各部會檢核時被列入不乾淨資料的統計中，並記錄是從哪個流程進到這步，供資料承辦參考改進
    - 使用者仍可下載承辦上傳的原始檔案

