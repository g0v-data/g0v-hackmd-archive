---
title: "臺南市政府 opendata 平台意見回饋"
tags: hackpad
---

# 臺南市政府 opendata 平台意見回饋

> [點此觀看原始內容](https://g0v.hackpad.tw/XUCEk87ljVZ)


台南市政府方面來函，希望社群針對近日上線的「平台本身」及「資料」提供一些意見回饋 [http://data.tainan.gov.tw/](http://data.tainan.gov.tw/)

授權：CC-BY g0v contributors

### 平台部分

- 似乎沒有提出資料需求的管道或討論區
> 後續會新增上去
> [name=Jung]

- 大部分的資料集授權皆為「[政府資料開放平臺資料使用規範](http://data.gov.tw/principle)」，右邊 filter 也許不需要依照授權選資料集
- 希望避免再有新的平台出現，甚至直接將資料整併到 data.gov.tw 去，畢竟 data portal 只需要一個會比較好。像是現在又看到 [http://data.itour.org.tw/](http://data.itour.org.tw/) 這樣的網站，感覺很多餘、浪費錢。
> 當初在建置規劃時就有聯絡中央，不過中央平台並不提供存放資料，政策是分散建置集中列示，所以台南至少還是要有一個存放資料的地方，而因為中央那邊有個出口，所以規劃的考量就不想頭太多資源在建置上面，最後綜合其他的考量就直接用CKAN建置，把錢和資源花在內部資料的串接和流程。最終目標就是台南各局處在台南市平台的後台上架，系統幫他同步過去中央的平台。
> [name=Jung]

> 至於[http://data.itour.org.tw/](http://data.itour.org.tw/是經濟部南部休憩園區計畫的平台之一)[是經濟部](http://data.itour.org.tw/是經濟部南部休憩園區計畫的平台之一)[南部](http://data.itour.org.tw/是經濟部南部休憩園區計畫的平台之一)[休憩園區計畫的平台之一](http://data.itour.org.tw/是經濟部南部休憩園區計畫的平台之一)，因為在該案結束之後可能會移交給地方台南市，因此該團隊建置平台前有過來和台南市談，為方便之後的整併與管理就建議他們直接採用CKAN，等他們計畫結束後再看如何處理。
> [name=Jung]

> 其實當時台南市平台規劃上就考量要降低資源的浪費與重複投資，所以台南市目前的環境其實是和他們共用。
> [name=Jung]

> 所以現在資料同步的部份有在進行嗎？目前一些 data.tainan 的資料其實是 data.gov 的子集合，像是人口、村里界圖等等
> [name=Finjon K]

### 資料集部分

- 1999 raw data
- 主計處的各項資料
> 目前台南市主計處有的統計資料網址如下[http://database.tainan.gov.tw/pxweb2007/dialog/statfile9L.asp](http://database.tainan.gov.tw/pxweb2007/dialog/statfile9L.asp)，不過該系統是行政院主計總處所開發，現行版本並沒有API，若所需資料是指這些資料庫，還是可以想辦法放上開放資料平台
> [name=Jung]

    - 需要的是中位數跟眾數
    - 家庭收支
    - 產業資訊
        - 企業規模
> 其實透過 [http://gcis.nat.g0v.tw/](http://gcis.nat.g0v.tw/) 的資料就可以計算，只是不知道有沒有公示資料以外的資訊可以提供
> [name=Finjon K]

> 就我了解地方的商業登記等資料也是直接進經濟部商工行政系統操作。
> [name=Jung]

        - 產業市值
        - 產業分佈

- 台南市轄下所有住址對應的座標，目前知道 [http://maps.nlsc.gov.tw/](http://maps.nlsc.gov.tw/) 有提供 住址轉換座標的服務，但是資料並未開放
> 內部已建議點位資訊須有座標，應可逐步加入
> [name=Jung]

- 台南市轄下所有土地建物登記資料，如果有個資法疑慮，可以移除個人資料，僅 開放其他資訊，像是建物建造、增建日期、土地對應地理資訊等等
> 建物登記資料已請工務局研究
> [name=Jung]

- 建物獎勵容積資訊
- 各類預算案資料以 CSV 等開放格式釋出，像 [http://www.tainan.gov.tw/tainan/Budget.asp?nsub=A6c300](http://www.tainan.gov.tw/tainan/Budget.asp?nsub=A6c300)  目前是難以整理的 pdf 格式
> 和主計研究以CSV釋出，不過主計現有的CSV格式仍然不是結構化，還是得再處理，據我之前去了解他們所用的系統其實是全國統一的，後續想去了解是否有改版計畫，覺得這才是長久之計。
> [name=Jung]

> 就 release early 的概念吧，現階段丟出 CSV 格式應該會容易些，長久當然會希望提供更完整的結構資料
> [name=Finjon K]

- 各類工程案標案資料（特別是議員交辦事項），提供標案承包公司的完整資訊 （與交辦議員）、施工進度等等，像 [http://www.tainan.gov.tw/tainan/Grants.asp?nsub=A6C400](http://www.tainan.gov.tw/tainan/Grants.asp?nsub=A6C400) 格式不是很好處理、資訊也不完整
- 各地警局公開活動申請資料，像是廟會路線圖等
- 農地普查資料，農地範圍、主要耕作作物、農會收購數量等等
- 戶籍地址對應勞保公司住址的資料，兩點模糊化座標即可，可以計算通勤相關資訊


