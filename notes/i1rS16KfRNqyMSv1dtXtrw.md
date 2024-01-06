---
title: "data.gov.tw 資料整理"
tags: hackpad
---

# data.gov.tw 資料整理

> [點此觀看原始內容](https://g0v.hackpad.tw/ncklnWyH1QY)

> 以下資料感謝Ronny大神提供!!!!!!!
> [name=羅佩琪]


這邊列出一些 data.gov.tw 資料整理的情況，列為給國發會的參考

### 整理規則

1.  總資料數 13545 筆
2.  先篩選有包含
    1.  XML, JSON, RSS
    2.  CSV, ODS, EXCEL, XLS, XLSX
    3.  SHP, KML, KMZ
    4.  ZIP / RAR / 7Z 解開來看
    5.  完全不包含以上檔案之資料組，濾掉 2858 個 (剩下 10687 個)
    6.  [https://worker1.sheethub.net/~srwang/data.gov.tw/no-support-format.csv](https://worker1.sheethub.net/~srwang/data.gov.tw/no-support-format.csv)
3.  包含預算、決算、結算、會計等資料集
    1.  這些格式都超不統一又很不 table ，但說他們不 machine readable 也不是，因為它們都是 XML 為主，這些跳過不處理
    2.  包含預算、決算、會計等文字資料有 3274 個(剩下 7413 個)
    3.  感覺就是拿來湊數用的.....
    4.  [https://worker1.sheethub.net/~srwang/data.gov.tw/stats.csv](https://worker1.sheethub.net/~srwang/data.gov.tw/stats.csv)
4.  針對 CSV 先處理 ，一共有 5031 個
    1.  CSV 檢查
        1.  欄位:
            1.  不能超過 128 欄 (超過的話有可能是解析錯誤)
            2.  不能有亂碼 (亂碼的檢查方式是把資料轉成 Big5 再轉成 UTF-8 要能不變)
            3.  不能有純數字 (不過會有例外，假如欄位是年份，而且寫成 2001, 2002, 2003, 2004 ....)
            4.  不能過長 (檢查方式，超過 64 bytes ，可能就是根本就不是 CSV)
            5.  不能重覆
            6.  不能有空白
        2.  值:
            1.  數量不能比欄位數多
            2.


- [http://data.gov.tw/node/11395](http://data.gov.tw/node/11395)
    - 上櫃公布注意股票資訊
    - Excel 匯出的 CSV，CSV 內還包含其他資訊
- [http://data.gov.tw/node/11369](http://data.gov.tw/node/11369)
    - 上櫃股票市場現況
    - 不是 sheet 型式，應該要另外客製每天抓
- [http://data.gov.tw/node/11628](http://data.gov.tw/node/11628)
    - 上櫃股票熱門股證券商進出排行
    - Excel 轉出來的，欄位名稱有兩排....
- [http://data.gov.tw/node/11627](http://data.gov.tw/node/11627)
    - 上櫃股票現股當沖交易統計資訊
    - Excel 轉出來的，裡面混合了兩張 sheet
- [http://data.gov.tw/node/11857](http://data.gov.tw/node/11857)
    - 上櫃股票自營商買賣超彙總表
    - 欄位名稱跟值對不上
- [http://data.gov.tw/node/11259](http://data.gov.tw/node/11259)
    - 體育署政策宣導相關廣告執行情形
    - 看起來不是好的程式產生的 CSV ，有的內容被逗點分開造成欄位混淆
- [http://data.gov.tw/node/9462](http://data.gov.tw/node/9462)
- [http://data.gov.tw/node/9463](http://data.gov.tw/node/9463)
    - 中華民國一百零三年政府行政機關辦公日曆表
    - 只是把日曆的 Excel 轉成 CSV... 變超爛的 CSV
- [http://data.gov.tw/node/11695](http://data.gov.tw/node/11695)
- [http://data.gov.tw/node/11696](http://data.gov.tw/node/11696)
- [http://data.gov.tw/node/11697](http://data.gov.tw/node/11697)
- [http://data.gov.tw/node/11698](http://data.gov.tw/node/11698)
    - 信用卡國內清算金額及筆數
    - 還有備註
- [http://data.gov.tw/node/11602](http://data.gov.tw/node/11602)
    - 個股類全市場部位限制
    - 還插了一個日期資訊在第二行是怎樣
- [http://data.gov.tw/node/12079](http://data.gov.tw/node/12079)
    - 入境行李運送總數
    - 也是將 Excel 轉出來成 CSV 的，欄位有兩欄
- [https://sheethub.com/data.gov.tw/公司登記家數及實收資本額異動](https://sheethub.com/data.gov.tw/公司登記家數及實收資本額異動)─按縣市別分
    - 公司登記家數及實收資本額異動─按行業別分
    - 欄位有點髒
- [http://data.gov.tw/node/11873](http://data.gov.tw/node/11873)
    - 欄位名稱標錯，出現兩個「漲停價」
- [http://data.gov.tw/node/7529](http://data.gov.tw/node/7529)
    - Excel 轉的 CSV
- [http://data.gov.tw/node/12982](http://data.gov.tw/node/12982)
    - 很多公司重覆兩次
- [http://data.gov.tw/node/11660](http://data.gov.tw/node/11660)
- [http://data.gov.tw/node/11590](http://data.gov.tw/node/11590)
    - 兩個 csv 交錯出現 orz
- [http://data.gov.tw/node/13629](http://data.gov.tw/node/13629)
    - 很難 parse 的 xls (不過感謝至少沒有轉成 csv XD)
- [http://data.gov.tw/node/13733](http://data.gov.tw/node/13733)
    - 用到合併儲存格
- [http://data.gov.tw/node/8154](http://data.gov.tw/node/8154)
    - 一點都不髒，只是因為 rar 裡面放了很多 csv ，需要另外處理


TODO
- [https://sheethub.com/data.gov.tw/%E4%BD%8F%E5%AE%85%E5%9C%B0%E9%9C%87%E9%9A%AA%E7%B4%AF%E7%A9%8D%E8%B2%AC%E4%BB%BB%E9%A1%8D(%E8%B2%A1%E5%9C%98%E6%B3%95%E4%BA%BA%E4%BD%8F%E5%AE%85%E5%9C%B0%E9%9C%87%E4%BF%9D%E9%9A%AA%E5%9F%BA%E9%87%91](https://sheethub.com/data.gov.tw/%E4%BD%8F%E5%AE%85%E5%9C%B0%E9%9C%87%E9%9A%AA%E7%B4%AF%E7%A9%8D%E8%B2%AC%E4%BB%BB%E9%A1%8D(%E8%B2%A1%E5%9C%98%E6%B3%95%E4%BA%BA%E4%BD%8F%E5%AE%85%E5%9C%B0%E9%9C%87%E4%BF%9D%E9%9A%AA%E5%9F%BA%E9%87%91))
    - 應該是有機會可以程式解決的 XML
- [https://sheethub.com/data.gov.tw/%E5%85%A8%E5%9C%8B%E5%A4%A7%E5%AE%A2%E8%BB%8A%E7%A6%81%E8%A1%8C%E8%B7%AF%E6%AE%B5](https://sheethub.com/data.gov.tw/%E5%85%A8%E5%9C%8B%E5%A4%A7%E5%AE%A2%E8%BB%8A%E7%A6%81%E8%A1%8C%E8%B7%AF%E6%AE%B5)
    - 有 KMZ 可以倒
    -

