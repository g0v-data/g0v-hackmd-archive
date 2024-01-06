---
title: "JSON, XML 匯出入範例"
tags: Data Quality,UDN,hackpad
---

# JSON, XML 匯出入範例

> [點此觀看原始內容](https://g0v.hackpad.tw/lqlPtqrJSZG)


本文是因應 data.gov.tw 政府資料開放平台今年目標是能納入各機關上架資料時的資料檢核，以及可以將表格式資料匯出成  JSON or XML 方便程式使用，因此先列出初步的標準。

這邊的匯入資料無法通過，不代表資料不乾淨，只是代表沒有被規則納入而已。

## 匯入

XML
- \[A\] 檢查 XML 是否為合法 XML
    - 不合法，到 \[Z\]
    - 合法，到 \[B\]
> 合法與否的定義是指之前的syntax檢查嗎?
> [name=Leo C]

> 純粹檢查是不是合法 XML ，這是可以抓出他到底放的是 xml 的網址，還是 zip 檔或者是網頁網址還要另外再點下載的情況
> [name=Ronny W]

> 那這裡的"合法"該如何檢查?
> [name=Leo C]

> [http://www.w3schools.com/xml/xml_validator.asp](http://www.w3schools.com/xml/xml_validator.asp)  或者 google 找 xml validator ，應該很多方法，XML 跟 HTML 不太一樣，HTML 可以很寬鬆很多容錯，XML 的語法是很嚴格的
> [name=Ronny W]

> (Y)
> [name=Leo C]

- \[B\] 檢查開頭是否有「<?mso-application progid="Excel.Sheet"」
    - 有，當作 Excel 處理，到 \[X\]
    - 沒有，到 \[C\]
> 這邊可能要再多加入一些判斷，Excel 應該不只這一種
> [name=Ronny W]

> XML還有Word轉的哦~
> [name=Leo C]

> 也許可以先用這些條件都掃過一次現有的 XML ，然後把 \[V\] 步驟的 XML 找找看能不能找到有哪些常見的可處理情況再拉出來處理
> [name=Ronny W]

> 這是 XLSX ([https://en.wikipedia.org/wiki/Microsoft\_Office\_XML_formats](https://en.wikipedia.org/wiki/Microsoft_Office_XML_formats))
> [name=張欽隆]

> 這邊主要是要解決很多資料集傳 xlsx ，自稱自己是 xml ，這對使用者來說會覺得超詐騙的，應該要能抓出來警告
> [name=Ronny W]

> 這個一定要抓，太GY又浪費人力
> [name=Leo C]

- \[C\] 檢查 root tag 是否為 KML
    - 是的話，進到 \[W\]
    - 不是的話，到 \[D\]
- \[D\] 從 root tag 出發往 children 掃，掃到 childNodes 數量不等於一後停止
    - 如果 childNodes 全部的 tag name 都一樣，就進到 \[E\]
    - 如果 tag name 有不同，就進到 \[V\]
> 嚴格來說是 Tag Name
> [name=張欽隆]

> 我把他改成 tag name 了，我寫 node name  是直接沿用 libxml  的名稱 XD
> [name=Ronny W]

> node name 在 XML 內包含了 text node 等非 tag 的資料 ，所以用 tag name 才是符合描述中的狀況。
> [name=張欽隆]

- \[E\] 再檢查下一層的 childNodes ，如果數量都相同並且都是只有一層，並且 tag name 也相同，就視為表格型資料的 XML
    - 符合，到 \[S\]
    - 不符合，到 \[V\]

- \[S\]  符合表格型資料，標記起來， nodeName 可以是欄位名
> [http://data.gov.tw/node/6213](http://data.gov.tw/node/6213)
> [name=Ronny W]

> [http://data.gov.tw/node/6624](http://data.gov.tw/node/6624)
> [name=Ronny W]

> [http://data.gov.tw/node/6074](http://data.gov.tw/node/6074)
> [name=Ronny W]

> 這幾個都可以合法進到這一步
> [name=Ronny W]


- \[V\] 無法判斷的 XML ，結束處理
- \[W\] 進到 KML 處理流程
- \[X\] 進到 excel 處理流程，不當作 XML 處理
- \[Z\] 標示為不合法 XML，需要警告
### json

- \[A\] 檢查是否為合法 JSON
    - 不是合法 JSON ，到 \[Z\]
    - 是合法 JSON ，到 \[B\]
> [https://tools.ietf.org/html/rfc7159](https://tools.ietf.org/html/rfc7159)
> [name=Joye L]

> or [https://tools.ietf.org/html/rfc4627](https://tools.ietf.org/html/rfc4627)
> [name=Joye L]

- \[B\] 看最外層的格式
    - 是 array ，到 \[C\]
    - 是 object ，到 \[D\]
    - 其他，到 \[Y\]
- \[C\] 檢查 array 內的每一個 element
    - 全部都是 array ，到 \[E\]
    - 全部都是 object ，到  \[F\]
    - 其他，到 \[X\]
- \[D\] 檢查是否有 type 這個 properties
    - 沒有，進到 \[X\]
    - 有，是 FeatureCollection（GeoJSON) ，進到 \[V\]
> 僅用一個 type field 就判定 GeoJSON 似乎風險過高
> [name=張欽隆]

> 不過依經驗目前平台上 geojson 應該不多，地理圖資還是以 shapefile 為主，這邊也可以先佔不處理，等跑一輪發現夠多再處理
> [name=Ronny W]

    - 其他，進到 \[X\]
- \[E\] 檢查 array 內是否每個元素都是非 array, object 的值
    - 是，進到 \[S\]
    - 不是，進到 \[X\]
- \[F\] 檢查是否每個 object 的 properties 的集合都相同，並且  value 都是非 array, object
    - 是，進到 \[T\]
    - 不是，進到 \[V\]


- \[S\] 是二維陣列並且矩形的 array JSON ，可以匯出成 CSV
> 這個範例現在好像沒有遇到過...
> [name=Ronny W]

> JSON 二維陣列是把第一個子陣列當成 heading 嗎？
> [name=張欽隆]

> 其實我還沒看到這種具體案例，所以在想要不要乾脆把這個拔掉了
> [name=Ronny W]

> 可以留著，但要定義標頭是那個。
> [name=張欽隆]

- \[T\] 是 properties 都相同的 array JSON ，可以匯出成 CSV
> [http://data.gov.tw/node/6624](http://data.gov.tw/node/6624) 的第二個 JSON 就是這種(剛發現第一個 JSON 實際上是 XML)
> [name=Ronny W]

> 像那種內容是 A format 但附檔是 B format 的，應該直接不處理？
> [name=張欽隆]

> 標 JSON 結果出來是 XML ，直接就變成 invalid JSON ，應該要警告? 已經不是機器讀不懂的問題，而是標示錯誤了
> [name=Ronny W]

> 這邊補充一下，未來的上架模是我其實是希望檔案格式能由系統自動判讀，若真的不吻合使用者可以再自行調整，這樣應該可以大幅降低錯誤率。
> [name=Leo C]

> 自動判讀 ？是指需要對每個檔案都去測試所有的格式？這不僅效率慢, 可靠性也不高。個人認為應標示格式錯誤即可。
> [name=張欽隆]

> 如果是需要先標示格是錯誤的話，表示使用者還是要填這項囉?
> [name=Leo C]


> \[S\]跟\[T\]的差異是在?
> [name=Leo C]

> S會像是  \[\["姓名","性別"\],\["小明","男"\],\["小美", "女"\]\] ， T 會是 \[{"姓名":"小明","性別":"男"},{"姓名":"小美","性別":"女"}\] ，只是我沒印象有看過 S 的案例過，也許 \[S\] 可以先不處理改成跳到 \[X\] ，等到真的有遇到再實作
> [name=Ronny W]

- \[V\] 確定是 GeoJSON ，也可以支援匯出 CSV

- \[X\] 標示為不認得的 JSON 格式
- \[Y\] 標示為不認得的最外層 JSON 格式，可能需要警告
- \[Z\] 標示為不合法 JSON ，需要警告
## 匯出

這邊匯出只針對已經確定「可匯出成CSV」的資料，這個範圍只有在原始資料的格式已經是表格性質的格式
> 匯出的 CSV 與匯入的 CSV 應制定一個規範
> [name=張欽隆]

> 匯入CSV的部分就不在這份文件的範圍了，不過我認為匯入CSV最少可以做一個檢查，就是第二行以後的欄位數有沒有大於第一行，有的話就應該噴錯誤，因為理論上第一行的欄位應該要最多。這個檢查可以抓到很多直接用逗點分隔卻沒 escape 掉逗點的 CSV
> [name=Ronny W]

> 我個人還是覺得，國發會應該規範一個標準的 CSV，凡不符合就當作不能處理的資料，回應給使用者變更。上次討論結論也是如此不是？
> [name=張欽隆]



> 匯出 CSV 的部分，由於 CSV 本身沒有標準規範，這邊可能要研究一下 python, r, php, d3, github 這些常用在資料分析的工具中的 csv lib 預期的 escape 法是什麼，怎麼處理 跳行, 逗點, 雙引號, 斜線等出現在值中的情況
> [name=Ronny W]

> PHP 跟 github preview (不太確定是不是用 Ruby 的 哪個 csv RubyGem 處理的) ，看起來都可以正常處理當跳行或是逗點存在時，用雙引號括起來的情況，遇到雙引號時會變兩個雙引號 ，像是 [https://gist.github.com/ronnywang/86a4883261f89e7a42883a11b5726a9e](https://gist.github.com/ronnywang/86a4883261f89e7a42883a11b5726a9e) 這邊就有遇到 csv 內需要有逗點、雙引號、跳行的情況
> [name=Ronny W]

> 因為 CSV 沒有標準，所以才需要統一一個規範，這樣輸出才有所依據，輸入輸出都應該採取這個規範。
> [name=張欽隆]

> 其實目前在跟Ronny討論的就是一個盡可能完整的檢核邏輯，至於說是規範... 不知道耶，覺得會被吐槽XD （例如最近常被問Open Data四星五星的認定與否，這似乎不是我們能做的事）
> [name=Leo C]

> 例如前面說的\[逗點分隔\]，\[資料內含逗點須用雙引號夾住\]，\[結構化資料需有明確欄標題（以1列為原則）\]，這些判斷規則我覺得是OK的，但不能說是規範XD 不合的資料依據目前的判斷邏輯，的確就是丟到不處理的項目，所以大家說的作法其實是一致的。
> [name=Leo C]

> 至於像是要不要\[強制UTF-8編碼\]等，這就可以討論。
> [name=Leo C]



### XML

- <dataset>
    - <row>
        <col1>value1-1</col1><col2>value1-2</col2>
        </row>
    - <row>
        <col1>value2-1</col1><col2>value2-2</col2>
        </row>
    </dataset>

### JSON

- \[{"col1":"value1-1", "col2":"value1-2"}, {"col1":"value1-2","col2":"value2-2"}\]
> 不太確定以上兩者有沒有更標準的作法
> [name=Ronny W]

> 好像有 [http://specs.frictionlessdata.io/json-table-schema/](http://specs.frictionlessdata.io/json-table-schema/) JSON Table Schema 這種東西，不過對大部分程式設計師來說上面兩個最單純的格式應該就很好用了
> [name=Ronny W]


> 除了 XML 和 JSON 的 table 形式外，KML, KMZ(KML archive format), GeoJSON 和 SHP 檔的表格化型式也請一併定義。
> [name=張欽隆]

> 匯出也應要求格式基本符合 
> [name=Joye L]

> [https://tools.ietf.org/html/rfc7159](https://tools.ietf.org/html/rfc7159)
> [name=Joye L]


