---
tags: 藝文活水向哪流
---

# 藝文活水向哪流

:::success
### 計畫宗旨
不同公部門為藝術工作者提供多種資源，但藝術工作者卻還是感覺匱乏？中間出了什麼問題？

藝文補助是影響台灣的藝文環境的重要機制跟策略，但補助機制的制定跟資源流向，卻不夠透明。我們想蒐集全台的公單位藝文補助資料，來更好的知道政府的藝文補助到底如何流向？有沒有更健康的循環方式？

我們希望藉由整理補助資料庫，來進一步分析藝文補助的重點及落點。

### 計畫發起人
ona - 藝術工作者
seangau - 工程師、攝影師、劇場人

### 相關資訊
目前已完成的爬蟲（文化部、國藝會） [github](https://github.com/SeanGau/art_crawler)
chihao 2019年的提案 [藝文圈圈圈](https://grants.g0v.tw/projects/5c2f45a9a444a2001b05d297)
:::

## 資料列表
### 文化部
- [x] [文化部獎助網補助資料](https://grants.moc.gov.tw/Web/AnnounceName_List.jsp?P=1)

### 文化部捐助財團法人
- [x] [財團法人國家文化藝術基金會](https://archive.ncafroc.org.tw/)(補助成果資料庫）
- [ ] [國藝會補助廣場](https://www.ncafroc.org.tw/search_founding_list.html)
- [ ] [財團法人中華民國電影事業發展基金會](http://mpfroc.org/about.php?func=1)（金馬獎）
- [ ] [財團法人國家電影及視聽中心](https://www.tfai.org.tw/about/publicInfo)
- [ ] [財團法人臺灣生活美學基金會](https://www.moc.gov.tw/information_392_49785.html)（臺灣當代文化實驗場 C-LAB）
- [ ] [財團法人臺灣博物館文教基金會](https://www.taiwan-museum.org.tw/about/)（國立臺灣博物館）
- [ ] [財團法人中法文化教育基金會](https://www.fondation.org.tw/contentinfotwo_105.html)

### 縣市文化局/基金會
- [ ] 台北市文化局
    https://culture.gov.taipei/News.aspx?n=9ED7A4C097510FF7&sms=DF4A6E288182BCA2
    https://data.gov.tw/dataset/121586
- [ ] [台北文基會預算書](https://www.tcf.taipei/Content/Content.aspx?id=7169&SubID=7210)
    國際藝術村及寶藏巖駐村計畫？
- [ ] [桃園文基會預算書](http://www.taoyuancf.org.tw/%e9%a0%90%e7%ae%97%e6%9b%b8)
- [ ] 新竹市文化局
    https://data.gov.tw/dataset/92417
- [ ] 台中市文化局
    https://data.gov.tw/dataset/87842
- [ ] 

*其他縣市資料太不清楚*
> [name=seangau] 可以問問資料申請小幫手

---
*以下為節目與展演內容類，可待獎補助類後先爬完後再討論是否處理*

### 公立藝文場館機構或節目
- [ ] 關渡美術館
- [ ] 高雄美術館
- [ ] 台北美術館
### 文化部附屬機關
- [ ] 中正紀念堂、國立傳統藝術中心、國家人權博物館 >>> [全部名單](https://www.moc.gov.tw/links_342.html)
- [ ] 國家表演藝術中心
### 行政院
- [ ] 故宮博物院、故宮南院

---
*以下為獎項，暫不列入統計*
- [ ] 台新獎
- [ ] 台北獎
- [ ] ...

---

## todo
- [ ] 盤點資料列表
- [ ] 建立持續更新的資料庫
- [ ] 資料視覺化

## notes
- 大筆的補助通常是給單位，但受助單位通常不會公開內部的補助明細
- 由各縣市政府初期認養各藝術團體，在地化、社區化，如：現行的有駐村策展（南寧文學獎或大學駐校或雲林成龍斯地展覽），不知道是不是一個方向。
- 如何統整資料庫


## 0618大松 note

> [name=yanyiyi 燕子] 可以看看民間團體補（捐）助系統（CGSS）
- https://subsidy.nat.gov.tw/
- CGSS需要政府機關申請帳號
- 資料大概到縣市層級，沒有基金會
- 不確定資料拿不拿得出來

> [name=ona] 已填寫政府資料開放平台「我想要更多」
https://data.gov.tw/suggests/136544
- 6/28 行政院主計總處回覆內容：
    - 您111年6月18日於政府資料開放平臺所提，政府補助應公開，要求本總處公開民間團體補（捐）助系統（CGSS）資料數據，以供民間監督等，謹回復如下：
    - 各機關對民間團體補(捐)助相關資訊，應依規定於機關網站首頁設置專區或便捷連結方式公開。為利外界查詢使用，本總處除請各主管機關以可搜尋之一致性格式，將補（捐）助相關資訊按季公開至機關官網
    - 亦於本總處官網建置「行政院及所屬各主管機關對民間團體補(捐)助案件資訊平台」，提供連結至各主管機關網頁，爰台端如欲了解各機關補（捐）助資訊，可透過本總處平台連結或逕至各主管機關網站查詢檢視。
    - 依申請提供連結：https://www.dgbas.gov.tw/ct.asp?xItem=47840&CtNode=6754&mp=1
        - 
- 探討
    - 連結中是各單位的 PDF 文件
        - 行政院及所屬各主管機關對民間團體補(捐)助案件資訊平台 https://www.dgbas.gov.tw/cp.aspx?n=1965
        - 每一個單位的 PDF 內容格式是否一樣？
        - 能否釋出 csv 資料
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_beb45dd719fb8ef8b094235b14c8b22b.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_20a8633ad0884d05dcfeb5bfd9dedea9.png)


- 倡議路徑
    - 主計總處的 資料開放諮詢委員會
        - 委員會名單：https://data.gov.tw/consult/17078?ag=518
            - 民間委員 林恭正 臺北大學公共事務學院財政學系
            - 民間委員 黃冠華 陽明交通大學統計學研究所 教授
            - 民間委員 鄭宇庭 政治大學商學院統計學系 副教授
            - 民間委員 周麗芳 政治大學社會科學學院財政學系 教授
            - 民間委員 陳素雲 中央研究院統計科學研究所 研究員
        - 會議記錄：https://data.gov.tw/dataset/17182
            - 業務單位會針對該期間有收到的「我想要更多」，陳列出來，但不一定會聚焦討論

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d4874ed2b0aec58d1d1f9f55eb96064f.png)





> [name=stimim] 申請補助的提案資料？未獲得補助的族群

> [name=seangau] 原來這種圖是桑基圖！
> https://observablehq.com/d/5045957c105afa14
> ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c759a8b800308f9d7e86f850af560b8d.jpeg)

