---
title: "租屋基礎資料收集"
tags: Rentea
---

# 租屋基礎資料收集

> [點此觀看原始內容](https://g0v.hackpad.tw/x1M9qr6Syqw)


這是份發想中的文件，目標是把決定租屋政策、產生完整租屋產業圖像的基礎資料來源，以及資料的計算方式，整理出來。目前屬於想到什麼寫什麼的階段，大概要明年才能來好好整理 XD

#### 授權

CC-BY-SA3

## 租屋人口、分佈資料

1.  普查資料【租屋人數與統計資料】
2.  間接數據【房屋仲介資料】
3.  間接數據【從「居住者身分」找資料】


### 普查資料【租屋人數與統計資料】

- 主計處
    - 行政院主計總處[人口及住宅普查](https://www.dgbas.gov.tw/np.asp?ctNode=2834) ，每 YYYY mod 10 == 0 普查一次，下一次是 2020年
    - 行政院主計處家庭收支調查（每年）：[2016 總樣本數 20,000](https://www.stat.gov.tw/ct.asp?xItem=27900&ctNode=511&mp=4) ，依戶籍抽樣，所以沒遷戶口的算不到
- 戶政司
    - 戶政司人口統計資料庫：[http://www.ris.gov.tw/346](http://www.ris.gov.tw/346)
- 內政部
    - 內政部十年一次的住宅狀況調查：[2015 年總樣本數 17,705](https://pip.moi.gov.tw/Upload/sys/study/869.pdf) ，依建物類型抽樣，所以住頂加或其他違建的算不到
- 其他
    - 「行政院提案指出，約有285萬多人有租賃住宅需求」\[[出處](https://tw.mobi.yahoo.com/news/%E7%AB%8B%E9%99%A2%E4%B8%89%E8%AE%80-%E5%8C%85%E7%A7%9F%E5%85%AC%E5%A9%86%E5%8F%AF%E4%BA%AB%E7%A7%9F%E7%A8%85%E5%84%AA%E6%83%A0-041116668.html)\]


### 間接數據【房屋仲介資料】

因為租屋市場是黑市，所以政府無詳盡資料，可預期需要有其他數據推估

- 已彙整
    - 本資料集的來源目前為591 租屋網， 後續也會持續擴充資料來源至各大租屋網與其他代管業者的公開資訊， 預計每月、每季、每年都會發佈一份該期間內曾經出現過的所有出租物件， 除了資料標準化外，不做額外的資料處理與刪減，希望盡量保持資料的原始狀態。
    - [https://www.facebook.com/ddioibb/posts/10216845791282300](https://www.facebook.com/ddioibb/posts/10216845791282300)
- 個別業者
    - [台灣租屋網](http://www.twhouses.com.tw/netc/chhistory/quote.html) 租屋價格，有具體的路段
        - repo: [https://github.com/yhsiang/twrentdata](https://github.com/yhsiang/twrentdata)
    - [樂屋網](http://www.rakuya.com.tw/price/deallist)  租屋行情
    - [好房網](http://rent.housefun.com.tw/) 雅房、套房、住家租屋價格
    - [591租屋](http://rent.591.com.tw/) 雅房、套房、住家租屋價格
    - 中研院附近租屋網: [http://app.sinica.edu.tw/rent/](http://app.sinica.edu.tw/rent/)
    - 福爾摩沙租屋網: [http://www.formosa-house.com/](http://www.formosa-house.com/)
    - citylife租屋售屋資訊網: [http://house.citylife.com.tw/](http://house.citylife.com.tw/)
    - 易租網: [http://www.e-rent.com.tw/2000/](http://www.e-rent.com.tw/2000/)
    - 中時租屋網: [http://cti.twhouses.com.tw/](http://cti.twhouses.com.tw/)
    - 崔媽媽租屋網: [https://rent.tmm.org.tw/](https://rent.tmm.org.tw/)
    - [這篇](https://www.urent.cc/blog/taipeiapartmentsrent) （urent部落格）也有提到好幾間
    - Airbnb
    - 東森集團的 [2018房市前瞻論壇](https://tw.finance.appledaily.com/realtime/20180609/1369178/)
        - 報載做了「台灣房市交易信心調查結果」，「...租房族群民調結果顯示，每月房租以「5000-10000元」居多（佔32.2%），坪數在20坪以下為主（佔59.2%）」，但查無調查資料，論壇似乎無公開。
- 統計資料 (針對租屋仲介市場)
    - [內政部不動產資訊平台](https://pip.moi.gov.tw/V2/A/SCRA0901.aspx)  有列出[各租屋網站的行情統計](https://pip.moi.gov.tw/V2/A/SCRA0901.aspx)、內政部的租屋成交價格..等
    - 租屋 NGO 組織所掌握資料，例如崔媽媽基金會 行政、捷運、學區等租金統計


### 間接數據【從「居住者身分」找資料】

由年齡、職業、國籍、身份等區分，看看是否能找到其對應的租賃住宅資料

- 公務員與公務宿舍
    - 找國家分類方法，軍、警、消...等，或中央單位、地方政府...等
    - 參考資料：
        - 歷年國宅地圖 [https://www.google.com/maps/d/viewer?mid=1EoGPbSm6MaPvg6M8vuQsCm9p2pzuLn2E&ll=24.994938778073706%2C121.46346239360128&z=15](https://www.google.com/maps/d/viewer?mid=1EoGPbSm6MaPvg6M8vuQsCm9p2pzuLn2E&ll=24.994938778073706%2C121.46346239360128&z=15)
        - 國(住)宅計畫發展沿革 [http://publichousing.cpami.gov.tw/files/11-1000-238.php](http://publichousing.cpami.gov.tw/files/11-1000-238.php)
        - 台灣歷史建築都市，其中的戰後軍警及眷村 [https://goo.gl/maps/4iHqDbYest72](https://goo.gl/maps/4iHqDbYest72)
- 社會住宅
    - 社會住宅已完工及已動工資訊地圖：[https://goo.gl/3aKmEB](https://goo.gl/3aKmEB)
        - 政府興建的社會住宅、租賃住宅、青年住宅等
            - 各地方政府有相關資料
        - 民間籌辦的社會住宅
            - 例如位在台南由伊甸基金會經營的「大林雙福園區」
- 學生與宿舍
    - 大專院校以上
        - 教職員與學人宿舍
        - 學生
        - 相關素材簡記
            - 大專外宿生電器用品使用模式之調查研究 [https://bit.ly/2kXOar9](https://bit.ly/2kXOar9)
            - https://www.facebook.com/1278664757/posts/10217532373802736/
    - 高中
    - 國中
    - 其他
- 企業員工與宿舍
    - 國營事業
        - 台灣南部糖廠「會社住宅」布局規畫與盛行風向之關係 [http](https://bit.ly/2sOLuAB)[s://bit.ly/2sOLuAB](https://bit.ly/2sOLuAB)
    - 醫院
        - [http://upmedia.mg/news_info.php?SerialNo=42990](http://upmedia.mg/news_info.php?SerialNo=42990)
- 安養長照機構導向的居住
    - 相關資料可能為衛生福利部所統計
- 醫療機構內的租住
    - 如何定義
- 原住民族
    - 新北市原民局101年原住民生活狀況調查 [https://www.grb.gov.tw/search/planDetail?id=2872172&docId=409335](https://www.grb.gov.tw/search/planDetail?id=2872172&docId=409335)
- 申請租金補貼者
    - 內政部針對租金補貼核定弱勢戶分析（[相關新聞](http://news.ltn.com.tw/news/business/breakingnews/2424269) ）
    - 弱勢家庭居住協助選擇與政策評估之研究
        - [https://www.grb.gov.tw/search/planDetail?id=11726337&docId=480944](https://www.grb.gov.tw/search/planDetail?id=11726337&docId=480944)
    - 臺北市
        - 租金分級補貼 [https://bit.ly/2GAQmNC](https://bit.ly/2GAQmNC)
        - 台北市低收入家庭房租補助標準之研究 [https://bit.ly/2sXDqga](https://bit.ly/2sXDqga)
- 街友與無定居者的居住
    - 官方開設的居住空間
    - 民間單位經營的居住空間
- 外籍工作者住宅，不曉得是否有相應的資料
    - 移民署？
- 前科假釋者？
    - 定期向警察局回報的現況資料中，是否有租屋資訊？
- 低薪工作者
    - 建構我國低薪工作者社會安全網絡機制之研究
        - [https://www.grb.gov.tw/search/planDetail?id=8265970&docId=437452](https://www.grb.gov.tw/search/planDetail?id=8265970&docId=437452)


#### 其他「找資料的思考途徑」暫記

- 房屋其他業務面向
    - 例如消防局會關切轄區內因為租屋市場而導致具有火災危險潛勢的住宅區域，像是大學周邊的分割出租空間、地下室出租、工廠外籍勞工居住區域...等
- 房屋物理
    - 是否可能由水費、電費、建物資料、其他類型的資料，旁敲側擊地判釋出該建物屬於租賃住宅？此思路參考的是空餘屋推斷方法 [https://g0v.hackpad.tw/xMXb4BUm1Sg](https://g0v.hackpad.tw/xMXb4BUm1Sg)


## 探討資料格式

資料欄位定議參考
- [http://schema.org](http://schema.org)；[http://schema.org/House](http://schema.org/House)

觀察簡記
- 租屋資料
    - 有「統計資料」，或是「可以描述出單項房屋的資料」
    - 「屋子」可以分成「招租中」或「已租出」
- 租客資料
    - 「租客」通常就是已租到房子的人才會在普查時表明自己是租房子


## 其他專案頁面


### 專案

- 租屋資訊地圖(暫定)
    - [https://g0v.hackpad.tw/Am1bLeHLumF](https://g0v.hackpad.tw/Am1bLeHLumF)
- ［工具］台北租房專題／新聞作業需要的資料與工具／爬租屋資訊
    - [https://g0v.hackpad.tw/gbw3lkzwd7y](https://g0v.hackpad.tw/gbw3lkzwd7y)
- yhsiang 有試著寫一隻程式去爬台灣租屋網的資料
    - [https://github.com/yhsiang/twrentdata](https://github.com/yhsiang/twrentdata)
- 薪資與租屋居住品質
    - [https://youtu.be/onZ3ihBGw6w](https://youtu.be/onZ3ihBGw6w)
- 9425 - 就是惡屋
    - 透過揭露房屋交易市場資訊，消彌房屋需求者在市場上的弱勢地位。補足現有房屋交易網站與凶宅網的不足之處， 建立整合平台匯整各地凶宅、惡房東資訊，本專案期盼讓每個人安居樂業，實現居住正義。
    - [https://grants.g0v.tw/projects/5a648893900e86001bf9f536](https://grants.g0v.tw/projects/5a648893900e86001bf9f536)
- 建築資料探討
    - [https://g0v.hackpad.tw/fs4ojVnb1tX](https://g0v.hackpad.tw/fs4ojVnb1tX)
- 新加坡 Information on Rental Prices
    - [https://www.ura.gov.sg/maps/?service=rentalprices](https://www.ura.gov.sg/maps/?service=rentalprices)
    - 1\. This map service comprises of private residential properties with rental contracts submitted to IRAS for Stamp Duty assessment within the last 36 months.
    - 2\. This map service is updated monthly on the 15th of every month. If the scheduled update falls on a Saturday, Sunday or public holiday, it will be updated on the following working day.


### 研究文獻

- 市場分析
    - 住展雜誌社：[http://www.myhousing.com.tw/](http://www.myhousing.com.tw/)
- 學術研究
    - 學術論文
        - 碩博士論文網
            - 都市仙丹─台北市「小套房」之空間生產與消費
                - [https://drive.google.com/open?id=0B9KyxXC_y1sLcUJDdlVCNm1NYzA](https://drive.google.com/open?id=0B9KyxXC_y1sLcUJDdlVCNm1NYzA)
        - 期刊
    - [政府研究資訊系統](https://www.grb.gov.tw/index)
        - 租屋需求者負擔能力之衡量---租金與品質觀點
            - [https://www.grb.gov.tw/search/planDetail?id=853956&docId=162476](https://www.grb.gov.tw/search/planDetail?id=853956&docId=162476)
        - 台灣家戶的住宅需求---分配觀點之個體資料長期分析
            - [https://www.grb.gov.tw/search/planDetail?id=2116742&docId=338580](https://www.grb.gov.tw/search/planDetail?id=2116742&docId=338580)
        - 家戶居住遷移與換屋決策之研究
            - [https://www.grb.gov.tw/search/planDetail?id=2647109&docId=399633](https://www.grb.gov.tw/search/planDetail?id=2647109&docId=399633)
        - 不動產租賃服務產業發展與推動策略之研究
            - [https://www.grb.gov.tw/search/planDetail?id=1999812&docId=327779](https://www.grb.gov.tw/search/planDetail?id=1999812&docId=327779)
        - 住宅所有權的來源如何影響政治態度？以臺灣為例的考察
            - [https://www.grb.gov.tw/search/planDetail?id=1249735&docId=230950](https://www.grb.gov.tw/search/planDetail?id=1249735&docId=230950)
    - 其他國家針對台灣租屋市場的分析
    - 針對其他國家的研究
        - 租買選擇、強迫儲蓄與消費支出：中國大陸家計單位的實證分析
            - [https://www.grb.gov.tw/search/planDetail?id=11891953&docId=489136](https://www.grb.gov.tw/search/planDetail?id=11891953&docId=489136)




## 租屋議題，誰關注？


租屋公共政策權責單位
- 《租賃住宅市場發展及管理條例》法令
    - [https://bit.ly/2JHFG5e](https://bit.ly/2JHFG5e)

租賃市場
- 仲介業者

租屋權益倡議團體
- 租客權益與市場合理性
    - 崔媽媽基金會：[https://www.tmm.org.tw/](https://www.tmm.org.tw/)
        - 蹣跚學步後的嚐試—談弱勢者的租屋困境與因應 [https://www.slideshare.net/OURsOURs/toddling-try-vulnerable-persons-situation-and-solution-in-rental-housing-market](https://www.slideshare.net/OURsOURs/toddling-try-vulnerable-persons-situation-and-solution-in-rental-housing-market)
    - 懶人包 Directed by：圖文不符｜簡訊設計
        - [https://www.simpleinfo.cc/works/tenant](https://www.simpleinfo.cc/works/tenant)
        - [https://www.simpleinfo.cc/works/tenant-argue](https://www.simpleinfo.cc/works/tenant-argue)
- 學生居住議題關注團體
    - 北醫居住權益小組
        - [https://www.facebook.com/TMUHJ/posts/1413388658760841](https://www.facebook.com/TMUHJ/posts/1413388658760841)
- 弱勢居住
    - 芒草心：[http://www.homelesstaiwan.org/](http://www.homelesstaiwan.org/)
    - 起家工作室：[http://www.homelesstaiwan.org/kige](http://www.homelesstaiwan.org/kige)

社會住宅倡議團體
- 社會住宅推動聯盟

媒體業者
- [https://www.mirrormedia.mg/projects/rent-house/](https://www.mirrormedia.mg/projects/rent-house/)

探討「居住形態」
- with many more of us now co-living, there is no one configuration. discover what type of co-living would be uniquely suited for you.reserve your spot for ONE SHARED HOUSE 2030.
    - [http://www.onesharedhouse2030.com/](http://www.onesharedhouse2030.com/)

其他
- New research finds that housing instability can affect the mental and physical health of family members of all ages.
    - [https://www.citylab.com/equity/2018/01/rent-anxiety-is-making-us-sick/551660/?utm_source=SFFB](https://www.citylab.com/equity/2018/01/rent-anxiety-is-making-us-sick/551660/?utm_source=SFFB)
- [https://www.facebook.com/groups/481382605221218/](https://www.facebook.com/groups/481382605221218/)

