---
title: "LawEasyRead"
tags: hackpad
---

# LawEasyRead

> [點此觀看原始內容](https://g0v.hackpad.tw/lYxzvhLiUYk)


工具性質。
讓沒有學過法律的人，在閱讀提到法律的文章時，能夠快速地連結、查詢指定法規或條文的內容；
讓有學過法律的人，能夠方便地向沒有學過的人引出實際的法條與相關解釋、判例、裁判、決議。

例如司法院釋字第584號其中一句「中華民國八十八年四月二十一日修正公布之道路交通管理處罰條例第三十七條第一項」，若能顯示成「88.04.21修正公布之 道交條例§37 第1項」並加上連結，或是滑鼠移過去時顯示浮動視窗、顯示該條內容，查閱時將會變得相當方便。

實作方向有三：
- 前台（分為內嵌與瀏覽器外掛二種呈現）：
    - 直接取用政府網站的資料
    - 取用後台的資料顯示
    - 對支援的網站重新排版（瀏覽器外掛限定）
- 後台（架站）：
    - 供網路程式連接的API
    - 網站
- 手機程式：
    - 標榜離線功能，否則使用排版良好的網站即可
    - 看能不能比 KNY 和 法源法律網做的更好

## 來龍去脈


### 主旨

每次查閱法條時，常會遇到提及其他法令或是條文的文句，但每次均需花數十秒以上才可能找到被提及的條文。例如行政訴訟法第19條：「法官有下列情形之一者，應自行迴避，不得執行職務：一、有民事訴訟法第三十二條第一款至第六款情形之一。…」但是民事訴訟法的該條文究竟說了甚麼，就得另開視窗才能查詢。

而網民們討論時事（例如最近的智財局、電信法、國安法、會計法）時，也缺乏直接的搜尋工具列出法令的修法歷程。當需要說明「公投案被否決時，其實政府想做甚麼都可以」、「偷騎別人的腳踏車並不算竊盜罪」和「兒童性侵案件問『有無違反意願』是法律要求」時也都很麻煩。

另一個需求是行政法類。例如個資法第20條第2項規定「…當事人表示拒絕接受行銷時，應即停止利用其個人資料行銷」但是沒學過法律的人並不能一望即知「商家違反該條的話，我能不能告他或檢舉，檢舉後主管機關卻不處罰該怎麼辦？」（參閱同法48條3款與民法184條；簡言之：「法律允許或禁止甚麼行為」是一回事，「違反法律的效果如何」是另一回事。）

希望網民們監督政府、討論時事而要引用條文，或是查閱立法院公報、而其中提及法令時，能夠快捷地知曉該法令內容，促進對議題的瞭解。

### 牽涉領域

法律 / 教育

### 相關組織單位

評律網 / 司改會

### 相關專案

> 衍生自某專案/衍生出某專案/API串接自某專案...etc.
> [name=ET B]


### 授權方式

> 程式碼部分（如 MIT/BSD）
> [name=ET B]

> 文件部分（如 CC-BY）
> [name=ET B]


### 使用資料

以下述兩者為主：
- 立法院法律系統：有法條歷史可供對照，缺點是沒有行政院的行政命令。（正確術語是「法規命令」與「行政規則」）
- 法務部全國法規資料庫：有法律、命令、條約等，缺點是只有最新的版本。
此二者未含所有法規，例如地方自治法規即均無收錄。

### 專案目前狀態

- 後台架設於 [http://laweasyread.herokuapp.com](http://laweasyread.herokuapp.com)
    - API 見 [https://github.com/g0v/laweasyread#api](https://github.com/g0v/laweasyread#api)
- 前台
    - 已有瀏覽器外掛
        - Firefox: [https://addons.mozilla.org/zh-TW/firefox/addon/laweasyread/](https://addons.mozilla.org/zh-TW/firefox/addon/laweasyread/)
        - Chrome: [https://chrome.google.com/webstore/detail/iedodmlnmhobigohbkalkkjlbmdkjalj](https://chrome.google.com/webstore/detail/iedodmlnmhobigohbkalkkjlbmdkjalj)
    - 有內嵌功能（[示範頁](http://g0v.github.io/laweasyread-front/embed.html)），並亦實作一供使用者[貼文字立即轉換](http://g0v.github.io/laweasyread-front/userInput.html)的頁面。

[http](https://github.com/g0v/laweasyread)[s](https://github.com/g0v/laweasyread)[://github.com/g0v/laweasyread](https://github.com/g0v/laweasyread)
[https://github.com/g0v/laweasyread-data](https://github.com/g0v/laweasyread-data)
[https://github.com/g0v/laweasyread](https://github.com/g0v/laweasyread-front)[-front](https://github.com/g0v/laweasyread-front)
[https://laweasyread.hackpad.com/LawEasyRead-5nGaomJOqkU](https://laweasyread.hackpad.com/LawEasyRead-5nGaomJOqkU)


## 目標與功能


### 預定使用者

網站製作者與瀏覽者

### 預定功能

- 轉換網頁中的法規名稱為連結，讓瀏覽者能夠直接看到全國法規資料庫該法規的所有條文。（此部分不需要處理條文內容）
- 承前，但支援連結到特定法規的特定條文。
- 承前，可用浮動視窗顯示。
- 於法規網站或是另外架設的站台上，瀏覽特定條文時，列出：
    - 此條引用的條文－－較容易，直接分析其內文即可。
    - 引用此條的條文－－應會需要伺服器先將所有法條分析過，或是讓client端連向立法院的特定網頁（參閱[http://kong0107.blogspot.tw/2013/04/law-to-programmers-3.html#ltp3\_3\_5](http://kong0107.blogspot.tw/2013/04/law-to-programmers-3.html#ltp3_3_5) ）
    - 比較同一條文的歷史版本（仿版本控制系統的分析方式），並列出修法理由與立法院於該次修法之會議記錄連結。
- 比較不同條文之間的構成要件或效果。例如：[http://images.plurk.com/kAGZ-7sbeIAyST93jLDq0lqExYg.jpg](http://images.plurk.com/kAGZ-7sbeIAyST93jLDq0lqExYg.jpg)![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0849c6c47e04fb9eeb4b1cfbd5ae9ac4)
- 列出引用過指定條文的司法判決或解釋（需分析司法院網站，另可開專案分析裁判書）
- 瀏覽指定法條於指定日期時的版本（例如蘇建和更一審時的刑事訴訟法條文），最好能區分當時最新修正的版本是否已經上路（例如個資法是2010年5月修正，但卻是2012年10月施行。故如指定搜尋「2011年7月時的個資法」時，輸出舊版）

### 使用方式

- 連結功能部分：
    - 製作瀏覽器外掛，將所有法規名稱與網址對應都包進去。
    - 撰寫可讓網站設計者引入的JavaScript，達成特定class 的HTML Element內的文字自動加上連結。
- 比較功能：需架設網站。

## 實做細節


### 使用技術與工具

JavaScript, Node.js, AngularJS, LiveScript

### 產出檔案格式

HTML, JSON

### 進度與 to-do


### 現有成果

如前述

## 開發者


### 技術指導


### 分工與成員

- [x] NeedsWriter: 需要文案幫手（撰寫基本資訊、報導專案etc）
- [x] NeedsDesigner: 需要介面設計
- [x] NeedsData: 需要資料（擷取、清理）
- [x] NeedsTech: 需要技術支援（程式、架站 etc)
- [x] NeedsProcess: 需要幫忙設計作業流程
- [ ] NeedsTalkingToRealPerson: 需要有人幫忙和其他機關聯絡
> 設定成 project registry 中的 tags，需要幫忙的會自動 promote 到 g0v project hub
> [name=ET B]




