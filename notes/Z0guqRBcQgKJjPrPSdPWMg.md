---
title: "國債問題"
tags: 財稅,hackpad
---

# 國債問題

> [點此觀看原始內容](https://g0v.hackpad.tw/1BtcHyNhuGI)


[Idea Pool](https://g0v.hackpad.tw/ZhayTz2Om0n)

## Taiwan Debt Clock

- 拋磚人：ipa（稅務國債完全不熟，先筆記，有興趣請撿來作）
- 專案簡介：台版國債（可納入 budget.g0v.tw）
- 關鍵字：國債、赤字、預算、債留子孫
- 參考：
    - [http://www.usdebtclock.org/](http://www.usdebtclock.org/) 米國
    - [http://www.linyuda.url.tw/OurDebtU8.htm](http://www.linyuda.url.tw/OurDebtU8.htm) 台版（好像是稅改會做的？）
> 看了一下 html source，數字是寫死的，即使 refresh 也不會變。不確定是不是 daily 改數字。
> [name=Jeff H]

        - 這是[公平稅改聯盟](http://blog.yam.com/fairtax)上的一個 widget - [說明](http://blog.yam.com/fairtax/article/18495233)、[語法](http://blog.yam.com/fairtax/article/18378233)
- 工作目標：
    - 列出希望呈現數據 1\. 國家預算前三名 2. 赤字 3. 稅收 4. 國債（先亂想）
    - 找相關數據
        - [主計處](http://www.dgbas.gov.tw/)\- [政府統計總覽](http://www.dgbas.gov.tw/ct.asp?xItem=13213&CtNode=3504&mp=1) 以及於 [data.gov.tw](http://data.gov.tw/)  開放的[資料](http://data.gov.tw/opendata/orgList?oid=2.16.886.101.20003.20071) 。
        - [\[資料\] 台灣國債鐘記錄](http://huangkai2001.blogspot.tw/2013/01/national-debt-clock.html)
        - [財政部統計處](http://www.mof.gov.tw/mp.asp?mp=62)
        - [財政統計資料庫查詢(系統)](http://web02.mof.gov.tw/njswww/WebProxy.aspx?sys=100&funid=defjspf2)
> 看不懂，不曉得怎麼解讀。:-(
> [name=Jeff H]

> 是這個數字嗎？ \- 選 各級政府歲入歲出淨額 > 預算數 \> 歲出淨額按政事別分：政府別選「總計」，政事別選「債務支出」，按「查詢」可得到 101 年為 143,179 百萬元。
> [name=Jeff H]

- 授權方式：[open source](http://opensource.org/)
- 使用資料：
- 狀態：胡思 ，純粹拋磚
    - 可以做個 numbers.g0v.tw，先從政府已經 open 的資料開始做起，朝向將[政府統計總覽](http://www.dgbas.gov.tw/ct.asp?xItem=13213&CtNode=3504&mp=1) 或類似數字來源，以方便易用的方式「開放」出來。
        - 像 www.usdebtclock.org 的 dashboard 顯示現狀與趨勢
        - 提供分類完善的數字目錄 (directory)
        - 每個數字都應該有相關說明，並有 link 連到原始來源
        - 每個數字都應該有對應的 API 可以供其他專案使用。
- 徵求夥伴：在有興趣的主題下簽名，並加上希望達成什麼、補充資訊、需要什麼幫忙的 tag
    - NeedsDesigner: 需要介面設計
    - NeedsData: budget.g0v.tw資料？
> 除了 data.gov.tw 已經開放的資料以外，也可以按照[政府統計總覽](http://www.dgbas.gov.tw/ct.asp?xItem=13213&CtNode=3504&mp=1) 的目錄，運作要求政府開放更多的資料 (到 data.gov.tw)。這需要人力與時間來推動。
> [name=Jeff H]

    - NeedsTech: 需要技術支援（程式、架站 etc)
    -

