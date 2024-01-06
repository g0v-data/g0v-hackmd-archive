---
title: "2016 中選會選舉資料意見回饋"
tags: hackpad
---

# 2016 中選會選舉資料意見回饋

> [點此觀看原始內容](https://g0v.hackpad.tw/b6qi8pie35p)


### API意見回饋

1.  沒有候選人唯一識別碼
2.  API中無法分辨全國不分區和僑居國外國民兩選區，[API連結](http://2016.cec.gov.tw/opendata/cec2016/getJson?dataType=2)
3.  欄位名稱不固定
> 例如政見，在全國不分區是politics；區域或原住民都是rptpolitics，雖然說全國不分區的是政黨統一政見，意義上有些不同，在此提出意見供討論
> [name=johnny]

4.  異體字
> 彰化縣第二選區黄玉芬，黄 vs 黃，也許是候選人自己選擇的，但是[中選會登記概況](http://web.cec.gov.tw/bin/downloadfile.php?file=WVhSMFlXTm9Mek12Y0hSaFh6STFOelk0WHpjeE1qRTVOakpmTkRNeU5qSXVjR1Jt&fname=HDJHUWEHUXSTKLDDA511HD40A5OPRP50KLA5EDOPMLNLKL04ML11UWCHRLMLCDQPHD01WTCH15QPCDLO14B531OPMLFDTWRPSXEDQLPKHDRPGHVT51VTUWOPUTVTUX45KLA5EHDDHDQP505545IHHD4015OP11RPHD01OPCDA5B5HCQPML11GDEHKLMLGHVTHD01STOP35OPCDLOCDIH31OPRLVTTWSXMLRPST45HDMLKLVTCDA5QPRPHDVT45VTUXRPEDUXKLZX15OPUTWXKOPK)時釋出的資料是正體字
> [name=johnny]

5.  無候選人照片
6.  出生地是否需要臺灣省
> 臺灣省彰化縣 vs 彰化縣
> [name=johnny]

7.  選舉區對應行政區的 sessiontownship 中會有多餘的{"area":"000"}，[API連結](http://2016.cec.gov.tw/opendata/cec2016/getJson?dataType=6)
8.  api 介面命名過於草率，目前是用 1~8 作為命名，也許該思考所有資料納入後的介面應該長什麼樣子去設計
9.  選舉區對應之行政區，如果已經是該鄉鎮市區所有村里應該列舉鄉鎮市區即可，每個都列出村里會有些多餘
> 個人覺得官方可以完整列出，各應用再視需求過濾，但如果能提供一些條件查詢會更好
> [name=johnny]

10.  投開票所應該直接附上 WGS84 地理座標，理想上應該還有該投開票所涵蓋行政區或 polygon 座標
11.  公辦政見會資料應該一律錄影並且提供檔案位置（或 youtube 連結）
> 目前看起來立委也是逐步提供了，只是不清楚會不會全部涵蓋
> [name=Finjon K]

12.  各種代碼應該進一步在文件提供完整代碼表的參考資料
13.  應該可以直接連結並且提供監察院政治獻金專戶的資料共同呈現
14.  實際產生選舉公報後希望能夠比照 2014 提供電子檔，並且將連結加入各候選人 api 資料中
15.  跟第一點一樣希望有唯一識別碼，並且希望依據這個識別碼能夠新增一個介面去查詢該候選人過去參選記錄，因為跨年度的資訊直接用姓名連結的錯誤很多
16.  回應的 http header 希望能夠加入 Access-Control-Allow-Origin: * 等聲明，讓外部應用可以直接讀取(ref: [https://developer.mozilla.org/zh-TW/docs/HTTP/Access\_control\_CORS](https://developer.mozilla.org/zh-TW/docs/HTTP/Access_control_CORS)  )
17.  個別資料希望加入版本號、建立日期與異動日期
18.  可以考慮提供申請，讓外部引用各種資料的網站或 app 可以將網址等資訊提供給中選會做交叉連結

### 很棒的部分

1.  候選人名字中如有英文的部分統一以固定符號隔開
> 馬躍‧比吼^Mayaw‧Biho、嘎礌‧武拜‧哈雅萬^Galahe‧Wubai‧Hayawan
> [name=johnny]

2.  候選人生日是標準時間格式
> Sep 14, 1981 12:00:00 AM
> [name=johnny]

3.  縣市、政黨資料使用代碼
> 臺灣省基隆市 10017
> [name=johnny]





