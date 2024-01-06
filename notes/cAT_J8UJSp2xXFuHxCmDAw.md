---
title: "公有土地資料擷取討論"
tags: 公有地大行動,hackpad
---

# 公有土地資料擷取討論

> [點此觀看原始內容](https://g0v.hackpad.tw/UJdwBmX2NU2)


## 一般注意事項

- 資料的**基本規格**，以下各種項目之間無法相互推敲，是描述土地特性根本的資料項目
    - ==在哪裡==：不動產標示，包含 縣市,行政區,段小段,地號
    - ==有多大==：面積 與 持份比例
    - ==誰的地==：所有權人、經管單位(管理者)
    - ==怎麼了==：公用or非公用狀態、開發方式
    - ==圖面與文書==：現況圖片、計劃圖、報告書、判決書...等等
    - ==相關租售價資料==：公告現值...
    - ==建立資料的時間==：因為土地資料會隨時間變動，所以必須知道資料時間

### 舉例

所有權人：中華民國
管理者：財政部國有財產署
縣市：台北市
行政區：中正區
段小段：永昌段一小段
地號：00300000
面積(平方公尺)：9
分母：1
分子：1
持分面積(平方公尺)：9
使用分區：第三種住宅區
地目：
編定使用種類：
狀態：標售
公告現值日期：
公告現值單價(元/平方公尺)：
公告現值總價(元)：
資料時間：2015
圖片：.....

- 前述基本規格的資料，衍生可查到的資料
    - 縣市+行政區+段小段+地號→
        - 土地形狀（參考[地號轉地圖](https://g0v.hackpad.tw/-Land-No.-Mapper-uhB6qAwYXe5)）
        - 計畫分區（例如是否位在商業區內）
        - 該筆土地歷年轉手資料，基本上從有紀錄的時代開始都可以查的到，但需繳交費用給中華電信?
        - 待確認：建築物登記、建照、使用執照
        - 民眾的回應資料（例如以前這是做什麼用途的）
    - 段小段地號、開發方式→開發進度與相關資料庫、政策決議、新聞
    - 面積→單位換算(坪..)

## 資料清理

由於目前主流文字編碼都採用UTF-8，但是台灣政府系統依舊使用BIG5編碼，在文字編碼轉換上有時候會出現問題，例如下方心得列舉中的「_も魚堀段_」問題。
從資料面來看，目前最正確完整的應該是[內政部地政司](http://www.land.moi.gov.tw/ngis/chhtml/query3.asp?dnformat=2)，政府資料開放平台提供的[土地段名代碼](http://data.gov.tw/node/7504)原始來源也是這裡，但是該檔案除了編碼有問題，也幾乎沒在更新，所以這邊先做了一個爬蟲，先把內政部地政司提供的資料抓下來，並將編碼從「Big5-HKSCS」轉成「UTF-8」，可以正確對應到已經上線的[地號轉地圖工具](http://codepen.io/dz1984/full/NqgVPj/)。
之後抓取的資料都會先跟這裡的名稱進行初步比對，至少段、小段名稱要正確才會儲存，如果比對錯誤可能就是程式Bug或者應該找管道回報。

程式位置：[https://github.com/Shihta/FNP_Crawler](https://github.com/Shihta/FNP_Crawler)
已經轉檔好的土地段名放在：OtherDatas/landnames.json
編碼參考：[Mozilla 系列與 Big5 中文字碼](https://moztw.org/docs/big5/)
> [Ronny Wang](https://g0v.hackpad.tw/ep/profile/tC7Bqff8Vp0)  也有做一個  [http://twland.ronny.tw/](http://twland.ronny.tw/)  ，不確定兩者資料有沒有顯著差異
> [name=Finjon K]

> 我有查到這個，但是找不到背後資料庫的原始檔，這個系統的原始來源「國土測量中心」就是[Ronny Wang](https://g0v.hackpad.com/ep/profile/tC7Bqff8Vp0) 之前提到的，需要透過影像處理才能把地籍資料弄出來的這件事
> [name=Shihta]

> 所以.....還是想問一下Ronny這個系統背後的資料庫要去哪裡拿啊？如果我把抓下來的東西都透過網路去問，感覺很操他的系統......
> [name=Shihta]


## 心得列舉

- ==「段小段&地號」最重要！==
- 可以用議題經驗，去蒐集需要關注的公有土地資料。例如，在公有土地的茫茫大海中，以「位在可建築區位，但目前沒有建築物登記的土地」，其實也是一種找到需要關注土地對象的方法，因為這種土地非常有機會被開發與被處分。
- 所挖出的資料，可以上傳到，[零時資料中心](http://data.g0v.tw/group/%E5%85%AC%E6%9C%89%E5%9C%B0%E5%A4%A7%E8%A1%8C%E5%8B%95)。
- 土地段名代碼：[~http://data.gov.tw/node/7504~](http://data.gov.tw/node/7504)
    - 這份資料有亂碼，可參考前段「資料清理」
- 公有地專案，即將以 PostgreSQL 為 DB。

財政部國有財產署北區分署資料如下：
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_8f07a02da8326d9d4dddf71a708ca710)
看起來缺少「地號」與使用狀態，其中土地明細如下：
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_768167433cdddc340a9203e644940759)
這資料不知道該如何處理呢？
> 表格中「不動產標示」的內容，即是「段小段」與「地號」，例如 新北市林口區小南灣段下福小段 1655-0002 
> [name=che l]

> 縣市：新北市
> [name=che l]

> 行政區：林口區
> [name=che l]

> 段小段：小南灣段下福小段
> [name=che l]

> 地號：1655-0002 
> [name=che l]

> 以「新北市,小南灣段下福小段,1655-2 」丟到 [http://codepen.io/dz1984/full/NqgVPj/](http://codepen.io/dz1984/full/NqgVPj/)  可看到輪廓位置
> [name=che l]

> ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6c45d1339c01f2b4c14a2c1041a4fb0e)
    
> [name=che l]

另外想請教以這張圖為例，所謂的「段小段」是不是「德音段0574」呢？
此外關於政府的「土地段名代碼」是不是也要合併使用呢？[http://data.gov.tw/node/7504](http://data.gov.tw/node/7504)
好像沒找到已有的資料表關聯？
> 代碼說明，可參考 友善地號資訊查詢界面：[https://g0v.hackpad.com/ZrNxaKVn8jt](https://g0v.hackpad.com/ZrNxaKVn8jt)
> [name=che l]

> 看來我搞錯了，這個的「段小段」是「德音段」，「地號」是「574」？
> [name=Shihta]

> 我以「新北市,德音段,574」丟到 [http://codepen.io/dz1984/full/NqgVPj/](http://codepen.io/dz1984/full/NqgVPj/)  有查到輪廓，所以可能是德音段沒有「小段」(猜)？
> [name=che l]

> ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_40eb73bf7089079cb917e352ca276fac)
    
> [name=che l]

有些資料好像查不到...
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ba54916030bb1743eb7abba0ed470365)
我查詢「新北市,坪林區,大粗坑段虎寮潭小段,57」沒有顯示資料，另外還有些日文字，不知道是亂碼還是？![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d468041b3de79058940a982b3d0e1417)
> ◐**も**_◐       這什麼XD!!
> [name=che l]

> 若運用 [https://g0v.hackpad.com/ZrNxaKVn8jt](https://g0v.hackpad.com/ZrNxaKVn8jt) 來查輪廓，可能不能輸入「行政區」（ex坪林區）。這部分看看之後 DZ1984 地號轉地圖改版時要不要設想一下。
> [name=che l]

> \[x\] 新北市,も魚堀段も魚堀小段,241 （國有財產署資料）
> [name=che l]

> \[x\] 新北市,魚堀段魚堀小段,241（政府資料平台資料）
> [name=che l]

> \[o\] 新北市,㝃魚堀段㝃魚堀小段,241（內政部地政司資料）
> [name=che l]

> 所以應該是「==**㝃**==字呈現問題」？
> [name=che l]


國有財產署的有一個業務是紀錄國有土地上的狀況，所以除了一般的土地地號相關欄位之外，以這塊 200 坪的臺北市中正區福和段二小段0244 地號的「土地明細」來看，國產署自己有紀錄他們認定目前地上的狀況（ex保留、占用），不過每一筆錄號的範圍形狀、位置、狀況判定，可能只有國產署自己有紀錄方法吧我猜。至於是什麼樣的，現場現勘、紀錄、面積計算的流程，我就不太清楚了。以下是國產署針對此地號的「土地明細」表格。第二張圖片則是此地號範圍的衛星圖，可以看到有許多建築物。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_8ddf07f4ca58a641c105d277f80f2aed)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_029c72ba19ba6b4a49d187f28624dd54)

