---
title: "公務員出國考察追蹤網_政大WebProgramming第三組"
tags: hackpad
---

# 公務員出國考察追蹤網_政大WebProgramming第三組

> [點此觀看原始內容](https://g0v.hackpad.tw/7PA3GGkb7m1)

我們是政大Web Programming設計課程的學生，合作的g0v專案是『公務員出國考察網』

小組成員：
資科三  郭士傑  100703009
資科三  吳孟翰  100703052 (組長)
傳播三  楊翔伊  100404012
日文二  陳玉美  101506002
資管三  謝孟霖  100306062
地政三  黃悅      100207430


## 目標理想

- 與現有g0v專案『公務員出國考察網』合作，將網站架構實體化
    g0v專案：[http://hack.g0v.tw/abroadplay/nOWhTpJPKx7](http://hack.g0v.tw/abroadplay/nOWhTpJPKx7)
> 歡迎加入[論壇討論](https://www.facebook.com/groups/abroadplay/) 將其結果實體化
> [name=Bert W]


- 網站的設計架構：前端（網頁風格呈現、使用者體驗等）＋後端（資料庫建置、搜尋資料存取）

- g0v原專案者對於網站的後端處理已有初步的成果，透過這學期我們學習到的網頁設計技巧，目標為將現有的網頁頁面做出合適的外觀呈現，達到最佳的使用者體驗。

- 對於後端處理，目前考慮重新規劃資料庫，並除了現有「中央政府」以外，擴及「地方政府」的資料


## 資料來源

- 公務出國報告資訊網
    \[中央政府\]
        行政院：  [http://report.nat.gov.tw/ReportFront/index.jspx](http://report.nat.gov.tw/ReportFront/index.jspx)
    \[地方政府\]
        台北市：[http://www.openreport.taipei.gov.tw/OpenFront/report/report_main.jsp](http://www.openreport.taipei.gov.tw/OpenFront/report/report_main.jsp)
        新北市：[http://www.rova.tpc.gov.tw/OpenFront/report/report_main.jsp](http://www.rova.tpc.gov.tw/OpenFront/report/report_main.jsp)
        台中市：[http://abroad.taichung.gov.tw/OpenFront/report/report_main.jsp](http://abroad.taichung.gov.tw/OpenFront/report/report_main.jsp)


## 預計功能

- [ ] 網站外觀美化、排版
    改善整體網站外觀，達到瀏覽網頁時的最佳使用者體驗
    需求支援：網站版面 CSS、動態效果 Javascript、架構工具 Framework

- [ ] 行動裝置版 Responsive Design
    目前網站尚未設計出適合行動裝置瀏覽的版面，技術層面預計需要 Media Query，根據瀏覽網頁的裝置的不同，載入不同的 CSS 網站樣板（區分電腦版本＆行動版）
    需求支援：Media Query、行動裝置版 CSS

- [ ] 精簡化各項行程表重點內容，其他細項以bar的方式呈現
    實際執行 → wiki手機版頁面（拉bar小選單“＾”）：[http://ppt.cc/TVsf](http://ppt.cc/TVsf)
                →Facebook的「閱讀更多」功能

- [ ] ~新增考察行程評論留言板~（擱置）
    使用者可以在行程下面發表評論，評論結果會統一彙整至大留言板，（新增大留言版於Navigation Bar）。如此一來，使用者可以看到其他使用者對於行程的評論和建議，也可以針對評論和建議提出自己的看法。（類似FB之動態消息）
> 要自己implement留言板還是外掛fb留言板?
> [name=Yuan C]

> 後來考慮到留言功能對於現有網站功能、定位的適切性，所以先擱置這個想法
> [name=吳孟翰]


- [x] 排序
    加入對於搜尋結果排序（點擊表格）。
    可以對於編號.主辦機關.出國開始.出國結束.地區.人數

- [ ] 出國考察大事表Timeline（部門）
    做出各部會出國考察時間圖表，檢查有無可能為亂報預算的出國高峰期。
    實際執行  →  分部門、分時間（月，如果跨月取出發月份）
                →  為部會分類之內容（待改名）
    需求支援：圖表化工具 Framework、Google Charts、D3.js

- [ ] 國家統計頁面
    改善國家統計頁面的內容顯示，除了現有地圖國家統計外，將新增可看到時間區間的部門資料。
    實際執行  →依地區分析行程
                →給定時間區間，定部門的行程分析

- [ ] 資料庫重新規劃與補完
    現有資料庫的規劃不夠完善，而目前擁有「中央政府」資料，未來需擴及到「地方政府」資料

- [x] 合併主題分類與施政分類
    主題分類＋施政分類 → ＂主題分類＂。因兩項內容分別為施政的主題與對象，而原有資料的分項資訊稍嫌複雜，容易令使用者混淆，所以將之合併。

- [x] 合併時間查找與報告查找
    時間查找＋報告查找 → ＂報告查找＂。因兩頁資訊相似度過高，所以將之合併。
    實際執行：→改進報告查找功能：
        不用時間與關鍵字都打才能搜尋，要搜尋單一也能搜尋


## 歷程事紀

\[2014 年\]
- 5 / 14：根據原有g0v網站進行美化、設計網站LOGO
- 5 / 28：細部頁面美化、加入新功能
- 6 / 18：政大Web Programming課程期末展演
- ? / ??：Mission Complete


## 協作工具

1.  HackPad
2.  社群論壇討論：[https://www.facebook.com/groups/abroadplay](https://www.facebook.com/groups/abroadplay)
3.  Prototyper
4.  google drive 共用資料（Core & Path sheet）


## 專案狀態

### （一）雛形初稿

- 網站架構 (structure)：
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0b1c3e0ea8a0cc0f19cc37367b440354)

- LOGO圖示
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_1a1af0221a4655c265a30439f447ad33)

- Core & Path sheet  (5/3修)
    首頁：[http://ppt.cc/FRqW](http://ppt.cc/FRqW)
    行程：[http://ppt.cc/6JR4](http://ppt.cc/6JR4)
    公務員：[http://ppt.cc/Aa37](http://ppt.cc/Aa37)

> 「熱門／喜愛 考察城市排行」是宣傳旅遊景點的網站才需要的資訊
> [name=jones f]

> 主要目標是要看到公務人員出國是否有假公濟私的行為才是設計重點。
> [name=jones f]

> 預算資料目前無法取得。
> [name=Bert W]

> FB上有轉貼不錯的思考點: [http://blog.ilyagram.org/post/84932490386](http://blog.ilyagram.org/post/84932490386)，你們應該要針對這部分做討論。
> [name=jones f]



### （二）網站分頁

- [http://rohanwu.github.io/wp2014s_project/](http://rohanwu.github.io/wp2014s_project/)
    首頁 > 報告查找 \> 國際護理協會四年期...
    首頁 > 主題分類 > 內政及國土安全 \> 民政-其他
    首頁 \> 國家統計
    首頁 \> 出國人員

- Responsive Design:
[http://monorhapsody.github.io/web/index.html](http://monorhapsody.github.io/web/index.html)（首頁）
[http://monorhapsody.github.io/web/%E5%87%BA%E5%9C%8B%E4%BA%BA%E5%93%A1_%E6%89%8B%E6%A9%9F%E6%9D%BF.html](http://monorhapsody.github.io/web/%E5%87%BA%E5%9C%8B%E4%BA%BA%E5%93%A1_%E6%89%8B%E6%A9%9F%E6%9D%BF.html)（出國人員）
[http://emilyoao.github.io/100404012/c10200768_mobile](http://emilyoao.github.io/100404012/c10200768_mobile)（行程內容）


### （三）實際頁面

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_586779f246e878b775431d34c00a5fe0)
- [http://report.nat.g0v.tw/](http://report.nat.g0v.tw/)（已上線網站）
- [http://rohanwu.github.io/wp2014s_project/](http://rohanwu.github.io/wp2014s_project/)（網站整體版型）
- [http://rohanwu.github.io/BootstrapTest/](http://rohanwu.github.io/BootstrapTest/)（*單一頁面，請以行動裝置瀏覽）
- [https://www.dropbox.com/s/w7g904vzu6zu7ik/crawler.rar](https://www.dropbox.com/s/w7g904vzu6zu7ik/crawler.rar)（爬蟲：定期更新資料）

- 期末Demo 評審/助教建議
*Jones老師 :
首頁→可顯示即時更新統計資訊(ex:每個月 哪個部門 出國最多次 去哪 多少人？)
報告查找→可將時間搜尋分開
部門分類→如果資料庫之值=0, 則不顯示該部門資料
Table之Responsive顯示可考慮為"卡片式"

*王康文學長：
首頁→Icon可設計為點擊超聯結
Bootstrap的特效→會讓人想點→可以設計成點擊超聯結
時間搜尋→改成點選日期
時間搜尋→搜尋欄大小修改
可於Navigation bar放上搜尋列
網站圖像化

*台大助教：
想想User來網站最想要獲得的資訊是什麼？為何user會想來此網站？
搜尋→可以Key words合併形式呈現


## 授權方式

- 採取「MIT License」授權條款 [http://opensource.org/licenses/MIT](http://opensource.org/licenses/MIT)
- 使用者有大範圍的利用權利＋少量義務（Non-copyleft Licenses）
1.  明示提醒商標權未授權
2.  明示提醒可收費提供擔保
3.  相容於 GPL v3




