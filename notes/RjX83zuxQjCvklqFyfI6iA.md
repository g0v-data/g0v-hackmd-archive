---
title: "八仙塵爆：聯合報採訪共筆"
tags: 採訪共筆,hackpad
---

# 八仙塵爆：聯合報採訪共筆

> [點此觀看原始內容](https://g0v.hackpad.tw/FKFYXmiRObq)

提問前，請先參考 [g0v 媒體區](http://hackfoldr.org/g0v-media/)、[過往](https://g0v.hackpad.com/collection/FCfDxuRKD2m)[採訪共筆](http://hackfoldr.org/g0v-media)
刊出時，請附上下列  [創用 CC 授權](https://creativecommons.org/licenses/by/4.0/deed.zh_TW)  標示字樣（中英擇一）：
```
CC BY 4.0 g0v contributors at (url)
由 g0v 貢獻者以創用 CC 姓名標示 4.0 授權，網址：https://g0v.hackpad.com/FKFYXmiRObq
```
全文以上述授權釋出，如不同意請勿編寫

截稿時間：

以下正文

## 前言

不好意思，我是聯合報的記者陳乃綾，因為昨天行政院長毛治國昨天要求新聞傳播處、災防辦、資訊處，整合八仙相關訊息以網站方式呈現，讓民眾有查詢、了解的入口平台，但我看零時政府已經製作[hackfoldr](https://beta.hackfoldr.org/627pray/)，而且事故第二天就做了[查詢傷患資訊](https://g0v.github.io/color/)的網站（非常方便，我也透過這個網站查到受傷的鄰居弟弟的醫院和資訊，先在此感謝你們），所以想要了解這次製作網站的資料如何與政府合作？不知道可以向哪位高手請教？

> 採訪共筆慣例上是先寫訪綱（問題列表），由受訪者自願填答，如有進一步問題則寫在下方。
> [name=Audrey T]


## 訪問大綱


### 誰發起架設傷者資訊查詢網站？

> tonyQ? 在 javascript 社群？ g0v 分享的版本是yutin作的，改良ui也陸續整合其他資訊
> [name=ipa c]

> [https://www.facebook.com/groups/javascript.tw/permalink/647706865330655/](https://www.facebook.com/groups/javascript.tw/permalink/647706865330655/)
> [name=雨蒼 林]


### 為何想架設？

> 我是看到計算死亡率的公式時就覺得工程師除了捐款以外還可以做些別的事情，就到 g0v 的聊天頻道看有什麼工作可以撿，看到需要分析血液庫存就做了。
> [name=Yuren J]

> 主要是眼前資訊混亂，希望能夠參與資訊的整理與轉發，讓相關傷患能夠在黃金時間內獲得足夠的醫療資源
> [name=Finjon K]

> 傷患查詢網站和hackfoldr目前的瀏覽流量大概是多少？想知道一下民眾使用的強度
> [name=Natalie C]

> Hackfoldr 似乎沒有安裝 Google Analytics...
> [name=Audrey T]

> 臉書四篇相關發文的觸及率總和為 672,898（至 6/30 2:45pm）。
> [name=Audrey T]


### 八仙事故的傷者資訊是如何取得？

> 北市資訊局 \- [http://www.gov.taipei/ct.asp?xItem=108880666&ctNode=38161&mp=100001](http://www.gov.taipei/ct.asp?xItem=108880666&ctNode=38161&mp=100001)
> [name=Finjon K]

> 新北市衛生局 \- [http://117.56.4.214/informationlist.aspx?uid=721](http://117.56.4.214/informationlist.aspx?uid=721)
> [name=Finjon K]


### 是主動與政府接洽要求開放資訊的嗎？

> 原始討論在 opendata.tw 社群
> [name=ipa c]

> [https://www.facebook.com/groups/odtwn/permalink/1256622861018796/](https://www.facebook.com/groups/odtwn/permalink/1256622861018796/)
> [name=Finjon K]

> 所以是與新北市災害應變中心有聯繫、索取資訊嗎？我看討論串中，新北市災害應變中心也有給予架站和資料運用的建議？
> [name=Natalie C]

> 台北市資訊局 ( [Saul Peng](https://www.facebook.com/saul.peng?fref=nf) ) 主動透過 opendata 群組詢問意願
> [name=Finjon K]

> ( [https://www.facebook.com/groups/odtwn/permalink/1257969007550848/](https://www.facebook.com/groups/odtwn/permalink/1257969007550848/) [)](https://www.facebook.com/groups/odtwn/permalink/1257969007550848/)
> [name=Pofeng L]

> ， TonyQ 主動接下後將資料帶到 javascript 社群，接著就遍地開花
> [name=Finjon K]

> 公部門的角色就是維護與提供資料，讓有興趣的民眾自由發揮
> [name=Finjon K]


### 與哪些政府單位、部門合作？

> 不知道算不算合作，不過血液庫存的資料是每小時自動解析台灣血液基金會的網站轉換成適合程式讀取的格式。
> [name=Yuren J]

> 病患資訊由台北資訊局開始整理後提供，接著延伸的資訊就是被動的由各開發者透過程式直接解析相關網頁
> [name=Finjon K]


### 就各位開發者觀察，政府在架設緊急事件的資訊平台，遇到什麼樣的困境？

> clkao 有篇 blog 正在處理這個主題，可以引用：
> [name=Audrey T]

> [http://blog.clkao.org/post/282889/disaster-response-information](http://blog.clkao.org/post/282889/disaster-response-information)
> [name=Audrey T]

> 感謝！這篇很詳盡
> [name=Natalie C]

> 請問clkao在新聞上該怎麼引用名字？
> [name=Natalie C]

> [Chia-liang Kao](https://g0v.hackpad.tw/ep/profile/AHlg3ouwI8g) 看看要不要自己說明囉？
> [name=Finjon K]

> 不過其實還沒寫完。就我的本名即可。
> [name=Liang K]




