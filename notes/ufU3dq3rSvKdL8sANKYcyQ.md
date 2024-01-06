---
title: "公務人員考察網 - 資料結構"
tags: 公務人員考察網,hackpad
---

> [點此觀看原始內容](https://g0v.hackpad.tw/HNf2pEOYnWe)



### 使用資料

以上這些資訊可以在主計處抓到. 如果可以抓到考察主題更好(不過可能會變得更雜)
- **公務出國報告資訊網** [http://report.nat.gov.tw/ReportFront/index.jspx](http://report.nat.gov.tw/ReportFront/index.jspx)
    - 這裡頭的資料似乎不包含立法院
    - [http://n.yam.com/lihpao/arts/20130529/20130529520985.html](http://n.yam.com/lihpao/arts/20130529/20130529520985.html)  目前立法院行政人員與行政院所屬機關各分別依據《立法院職員出國考察實施要點》與《行政院及所屬各機關出國報告綜合處理要點》，規定必須在出國考察結束一定時間內，提出考察報告，唯獨針對立委尚無相關規範。
- 每年審計部的決算書會有資料. 有分中央 五都 和 台灣省. 主計處則有匯總資料(無明細)
- 地方政府網
    - [基隆市政府](http://report.klcg.gov.tw/OpenFront/report/report_main.jsp)，[新北市政府](http://www.rova.tpc.gov.tw/OpenFront/report/report_main.jsp)，[臺北市政府](http://www.openreport.taipei.gov.tw/OpenFront/report/report_main.jsp)，[桃園縣政府](http://163.29.253.35/OpenFront/report/report_main.jsp)，[新竹縣政府](http://report.hsinchu.gov.tw/OpenFront/report/report_main.jsp)
    - [新竹市政府](http://open.hccg.gov.tw/OpenFront/report/report_main.jsp)，[苗栗縣政府](http://163.29.206.100/OpenFront/report/report_main.jsp)，[臺中市政府](http://abroad.tccg.gov.tw/OpenFront/report/report_main.jsp)，[彰化縣政府](http://open.chcg.gov.tw/OpenFront/report/report_main.jsp)，[南投縣政府](http://open.nantou.gov.tw/OpenFront/report/report_main.jsp)
    - [雲林縣政府](http://report.yunlin.gov.tw/OpenFront/report/report_main.jsp)，[嘉義縣政府](http://k2vm.cyhg.gov.tw/OpenFront/report/report_main.jsp)，[嘉義市政府](http://report.chiayi.gov.tw/OpenFront/report/report_main.jsp)，[臺南市政府](http://210.69.40.134/OpenFront/report/report_main.jsp)，[高雄市政府](http://report.kcg.gov.tw/OpenFront/report/report_main.jsp)，[屏東縣政府](http://210.69.151.187/OpenFront/report/report_main.jsp)
    - [宜蘭縣政府](http://210.69.148.49/OpenFront/report/report_main.jsp)，[花蓮縣政府](http://210.69.167.71/OpenFront/report/report_main.jsp)，[臺東縣政府](http://163.29.101.85/OpenFront/report/report_main.jsp)，[澎湖縣政府](http://report.penghu.gov.tw/OpenFront/report/report_main.jsp)，[金門縣政府](http://ocbr.kinmen.gov.tw/OpenFront/report/report_main.jsp)，[福建省連江縣政府](http://210.241.9.21/OpenFront/report/report_main.jsp)

### 如何取得出國考察費用資料？

從公務出國報告資訊網無法取得費用的資訊。以下列舉一些可行方案：

- 需要從公務人員採購網取得。技術上的困難是公開招標很難對應到公務出國報告
> 如果先不針對系統對應。先做備份的可能性來做，之後在做日期和名字的比對是否可行，目前中央還沒找到對映的決標結果。
> [name=Bert W]


### 資料庫規劃書


資料明細：
| 說明 | 型態 |
| --- | --- |
| 索引ID | id |
| 系統識別號 | sysid |
| 計畫名稱 | name |
| 主題分類 | scId |
| 施政分類 | pcId |
| 計畫主辦機關 | agencies |
| 出國人數 | people |
| 出國國家 | countries |
| 出國期間-開始 | periodStart |
| 出國期間﹣結束 | periodEnd |
| 報告名稱 | reportName |
| 報告日期 | reportDate |
| 報告書頁數 | reportPages |
| 參訪機關 | authorities |
| 出國類別 | category |
| 關鍵詞 | keyword |
| 備註 | remark |
| 報告內容摘要 | report |
| 來源網址 | source |

出國人員名單：
| 說明 | 型態 |
| --- | --- |
| 明細ID | abId |
| 姓名 | name |
| 服務機關 | agencies |
| 服務單位 | units |
| 職稱 | title |
| 職等 | official |

機關及國家：
| 說明 | 型態 |
| --- | --- |
| 索引 | aId |
| 母目錄ID | bId |
| 類型 | dataType |
| 名稱 | name |
| 參數 | desc |

附件檔對應：
| 說明 | 型態 |
| --- | --- |
| 明細ID | rId |
| 類型 | fileType |
| 檔案名 | fileName |
| 下載位置 | fileUrl |

出國和明細對應：
| 說明 | 型態 |
| --- | --- |
| 明細ID | rId |
| 國家ID | aId |




