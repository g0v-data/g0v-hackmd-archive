2022 年政府採購網改版相關變更事項
============================
2022-07-01 [政府採購網](https://web.pcc.gov.tw/pis/) 大改版，造成很多網址修改。這個共筆記錄一些相關的修改，主要供 Ronny 開發的 [標案瀏覽](https://ronnywang.github.io/pcc-viewer/index.html) 改版參考用


網址變更
-------
- 每日標案：https://web.pcc.gov.tw/prkms/tender/common/noticeDate/indexNoticeDate
- 新網址：TIQ-1-53341522.xml
    - 上公報類的都會是以這種格式
    - 符合類型
        - 公開招標公告
        - 公開招標 更正公告
        - 經公開評選或公開徵求之限制性招標 公告
        - 經公開評選或公開徵求之限制性招標更正公告
        - 決標公告
        - 決標更正公告
        - 決標資料定期彙送公告
        - 決標資料定期彙送更正公告
        - 無法決標公告
        - 無法決標更正公告
    - 會導向 https://web.pcc.gov.tw/prkms/tender/common/noticeDate/redirectPublic?ds=20220519&fn=TIQ-1-53341522.xml
    - [招標類] 會再導向 https://web.pcc.gov.tw/tps/QueryTender/query/historyTenderDetail?fkPmsMainHist=NzIwMTk2NTg=
        - base64_decode(NzIwMTk2NTg=) = 72019658
    - [決標類] 會再導向 https://web.pcc.gov.tw/tps/atm/AtmAwardWithoutSso/QueryAtmAwardDetailHist?fkPmsMainHist=NzIxMTg4MTA=
        - base64_decode(NzIxMTg4MTA=) = 72118810
    - 舊網址 http://web.pcc.gov.tw/prkms/prms-viewTenderDetailClient.do?ds=20220519&fn=TIQ-1-53341522.xml
- 新網址：unPublish.tender.NTM4MDg5MjM=
    - 公開取得報價單或企劃書公告(不刊公報)
    - 會導向 https://web.pcc.gov.tw/tps/QueryTender/query/searchTenderDetail?pkPmsMain=NTM4MDg5MjM=
    - base64_decode(NTM4MDg5MjM=) = 53808923
    - 舊網址：http://web.pcc.gov.tw/tps/tpam/main/tps/tpam/tpam_tender_detail.do?searchMode=common&scope=F&primaryKey=53808923
