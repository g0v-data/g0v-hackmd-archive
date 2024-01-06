---
title: "中立電力資訊分析與蒐集平台"
tags: hackpad
---

# 中立電力資訊分析與蒐集平台

> [點此觀看原始內容](https://g0v.hackpad.tw/SC1NEFiB5uQ)

fb 討論串：[https://www.facebook.com/groups/g0v.general/permalink/614352328641177/?stream_ref=3](https://www.facebook.com/groups/g0v.general/permalink/614352328641177/?stream_ref=3)

## 要解決的問題

\> 電力系統中立資訊與數據分析資訊一直都不好找，太亂了。

### 發起人、拋磚人：[Opop Kuo](https://www.facebook.com/yuyuopop?fref=nf)


### 專案說明

\> 若有資訊正確分析指出改善電力系統其實可以全面廢核，或許可以讓更多人覺醒反核(至少核四)、而不會願意冒核災風險。
\> 擁核的立場其實也有許多須正視之處，不可偏頗無視，台灣電力確實存在短期可見之問題
\> 網路上關於電力浪費的謠言也常見錯誤、造成台電專業被質疑，民意與台電專家的對立相立原因若起始於錯誤也非大眾之福。

希望催生項目：中立電力資訊分析與蒐集平台

### 現有類似專案

（現成的是否可以直接使用？或者有什麼不足之處？國外專案可參考？）

### 相關專案

（衍生自某專案/衍生出某專案/API串接自某專案.）
[省電取代蓋電廠，數據收集](https://g0v.hackpad.tw/1xcAfdHtkv0)
[發電成本計算機](http://muyueh.com/see/nuk/)

### 授權方式

（程式碼部分如 MIT/BSD /文件部分，如 CC-BY）
> 資料數據本身無著作權之適用，若有編排則本專案成果應為編輯著作。
> [name=nchild]


### 使用資料

[我國電力需求零成長評估報告](http://slidesha.re/1cLDjta)
> 此報告易讀性很差，若需降低進入門檻可參閱[懶人包](http://power.hotline.tw/)。
> [name=nchild]

> 能源局每年都有「長期負載預測與電源開發規劃摘要報告」，另外去年臺灣綜合研究院開始做電力負載預測（[參考](http://www.tri.org.tw/action/past1.html?id=236) ）。
> [name=Wind H]

[台灣2050能源供需情境模擬系統](http://my2050.twenergy.org.tw)
> 可由進階版連結[下載核心模型](http://2050.twenergy.org.tw/tw2050calculator.xlsx)。
> [name=nchild]

> [進階版](http://2050.twenergy.org.tw/)左下角每一個產業點進去，會有工研院的 PDF 資料，說明該產業可以如何省電，分成 Level 1 ~ Level 4 四種程度的方案（ex: [服務業照明的方案](http://2050.twenergy.org.tw/assets/onepage/%E7%85%A7%E6%98%8E.v4.pdf)）程度越高，就越擾民 (?)。
> [name=Johnson L]

> 右下角每一個再生能源也都可以點進去，介紹該再生能源在台灣可以如何使用，分成 Level 1 ~ Level 4 四種發展程度（ex: [海洋能](http://2050.twenergy.org.tw/assets/onepage/%E6%B5%B7%E6%B4%8B%E8%83%BD.v5.pdf)） 程度越高，就越需要仰賴技術突破。
> [name=Johnson L]

> 另外，在進階版選好能源路徑之後，他可以在最上面算出 2050 年時的台電購電成本、碳排放量，以及 GDP 衝擊。
> [name=Johnson L]


### 專案目前狀態

（構想 / 規劃 / 雛形 / 實作）
架構 (子架構也在 fb 上需要整理)
a. 電力現有資訊
    a.1 台灣分區電網架構
    a.2 各區電力供需情形
        1) 年平均用量
        2) 年尖峰用量
        3) 基載電廠
        4) 尖載電廠
    a.3 台灣電廠分布
        1) 火力電廠
        2) 水力電廠
        3) 風力電廠
        4) 核能電廠
        5) 其他
    a. 4 屆退與待役電廠
    a. 5 各發電方式之優缺點
b. 反對核能於台灣之論述
    b.0 待補資訊
c. 支持核能於台灣之論述
    c.0 待補資訊
d. 反對**核四**於台灣之論述
    d.0  待補資訊
e. 支持**核四**於台灣之論述
    e.0 待補資訊
f. 終止電力相關謠言
    f.0  待補資訊
g. 省電從你我做起：並於各大標題標示出預計此舉可節省總電量多少%用電
    e.1 民眾省電
    e.2 企業省電

ps. .0 待補資訊用意：蒐集主題，但慢慢補完內容。公告出來還缺哪些討論、可能可以得到其他人支援協助～

f.0 須分割主題之論述
[http://disp.cc/b/163-7CmM](http://disp.cc/b/163-7CmM)
f.1 反核謠言
[http://www.ptt.cc/bbs/Gossiping/M.1398231630.A.9BF.html](http://www.ptt.cc/bbs/Gossiping/M.1398231630.A.9BF.html)
f.2 擁核謠言
[https://www.facebook.com/shihyi.huangterrier/posts/662545177116521?stream_ref=5](https://www.facebook.com/shihyi.huangterrier/posts/662545177116521?stream_ref=5)


資訊蒐集狀況： (都在 fb 上，有空再整理過來)

## 目標與功能（要如何解決）

預定功能
- 有架構的主題文章發表區
- 文章架構：標題 \-  簡短白話文 \- 專業文 \- 關鍵字 \- 資料來源區：兼顧一般人可以看得懂、想要深入瞭解者就看專業文。須注意資料來源於此專題相當重要
> 我是想要在資訊後面再加上可信度的客觀評等，內容作者的背景專業度、資料的充實度、來源有無等等可信度相關的參考
> [name=鏡 暗]


可能功能
- 相同前提之反核擁核論述是否可以有專家評斷/投票何者為勝、作為懶人包？
    - ex 核四安全無虞：以現在狀態是不可能無虞的，所以可分勝負

預定使用者
- 觀眾：一般不夠瞭解/部份瞭解/有興趣瞭解台灣電力之一般民眾


## 徵求協作者

發起人/拋磚人：

opop：預計每日可協助之工時 1~2hr
1\. 資訊協助整理
2\. 專業文補充白話易懂版本
3\. 架構協助
4\. 資源協助

分工與成員
- [ ] NeedsWriter: 需要文案幫手（撰寫基本資訊、報導專案etc）
    - [ ] 需要網站名稱
- [ ] NeedsDesigner: 需要介面設計
- [ ] NeedsData: 需要資料（擷取、清理）
    - [ ] 資訊編輯：g0v 有志人士、電力田野研究者
    - [ ] 募集文章：領域專家見解
- [ ] NeedsTech: 需要技術支援（程式、架站 etc)
    - [ ] 需要架像 [http://g0v.today/](http://g0v.today/)  的站，應該這樣架構就夠了，不用另外架
    - [ ] 13:37 < yhsiang> opop: [http://hackfoldr.org/about](http://hackfoldr.org/about)
    - [ ] 13:37 < yhsiang> opop: 還是你需要custom domain ?
    - [ ] 13:38 < superbil> opop: 他們是用 [http://hackfoldr.org/](http://hackfoldr.org/)<your_keyword>
    - [ ] 13:38 < superbil> 就可開惹
    - [ ] 13:41 < yhsiang> opop: 可以先試看看hackfoldr.org 有需要power.today 再來研究看看怎麼做
- [ ] NeedsProcess: 需要幫忙設計作業流程
- [ ] NeedsTalkingToRealPerson: 需要有人幫忙和其他機關聯絡
> 設定成 project registry 中的 tags，需要幫忙的會自動 promote 到 g0v project hub
> [name=ET B]



## 實作細節（非技術背景可跳填）

協作工具
- github repo：
- hackfoldr 工作資料夾網址：
- google drive 共用資料夾網址：

進度與 to-do
> 僅供參考
> [name=ET B]

- [ ] product planning（recommanded procedure from justin lee / 李易修）
    - [ ] strategy
    - [ ] scope
    - [ ] structure
    - [ ] wireframe
    - [ ] visual
- [ ] web front-end
- [ ] web back-end
- [ ] ui / visual design


## 成果展示（規劃文件、雛形/草稿、原型/初稿、正式發佈/完稿）





