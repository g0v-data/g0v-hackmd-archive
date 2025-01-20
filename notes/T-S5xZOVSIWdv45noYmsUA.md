---
title: "透析貪污判決--揭露與查詢網站"
tags: Judical, hackpad
---

# 透析貪污判決--揭露與查詢網站

> [點此觀看原始內容](https://g0v.hackpad.tw/OoaenzjVDKK)

(暫名,尚缺副標)
The Disclosure of Corruption Judgement,  the Web
可能網址：blackmoney.g0v.tw 歡迎各種建議
POREN：uncover.g0v.tw 之類的，感覺很有特務風XD



## 緣起

- 貪污是個表面上看起來沒什麼，實際上會對社會造成侵蝕的嚴重病灶
- 有些人會講「水至清則無魚」、「無能比貪污更要不得」，但通常例子是官員收錢所以開始選擇性做事，有益人民的事情不作為，變成「無能」
- 貪污是個表面上看起來沒什麼，實際上會對社會造成侵蝕的嚴重病灶
- 然後發現判決書落落長，動輒數百頁，如果可以用簡單方式呈現那不就太好了嗎！


## 目標

- 一個查詢貪污與判決結果的查詢網站
- 不搞法理解釋、不提論述心證（也許是第三步以後的事），用簡單幾個欄位呈現判決結果，告訴你「某某某當年就有貪污案底」
一般民眾在意的點：
1.  金額大的案子
2.  牽涉政治人物的案子
3.  跟企業財團有關的案子
與金權政治相關的法律刑責：1.貪污 2.賄選 3.公務員財產不明 4.公務員登錄不實 5.公務員洩密

## 預設欄位

由於一個案件通常會有複數被告，因此抽取案件資料傾向於以人作為抽取重點，這裡我的想法是一個判決書以兩段資料呈現：第一段是判決書的欄位，一份判決書一筆；第二段是被告的欄位，每個被告都有自己的欄位，故筆數取決於被告人數
以下是我想到覺得重要的欄位，歡迎各種建議

預定使用的資料庫：MySQL => 因為預定會使用到不只一個欄位的搜尋，資料庫的table可以直接用下面兩個資料表來製作，並把地址欄位加進去。

第一段：判決書部份

| 欄位 | 進度 |
| --- | --- |
| 資料ID* |  |
| 裁判案號 | 100% |
| 裁判日期 | 100% |
| 法院別 | 100% |
| 被告人數 | 95% |
| 案件標的 | 0% |
| 法官 | 0% |
*資料ID暫時用檔名
第一段的部份除了「案件標的」、「法官」外，其他欄位已擷取：
[google試算表](https://docs.google.com/spreadsheets/d/1vufl16kKVJIMNLO-WMA-U_8GbuX-JjuGuoRkHwGBjbw/edit?usp=sharing)


第二段：被告部份
| 欄位名 | 抽取段落 | 進度 |
| --- | --- | --- |
| 被告姓名 | 被告 | 95% |
| 行政區 | 事實 | 0% |
| 工作/職位/關係 | 事實 | 20% |
| 罪名 | 主文 附錄 | 70% |
| 有期徒刑 | 主文 | 80% |
| 易科罰金 | 主文 | 80% |
| 緩刑 | 主文 | 80% |
| 涉貪金額 | 主文 事實 附錄 | 50% |
| 政黨屬性 | 外部資料查詢 | 0% |

工人智慧/範例：
[林益世貪污案一審](http://zh.wikisource.org/wiki/%E8%87%BA%E7%81%A3%E8%87%BA%E5%8C%97%E5%9C%B0%E6%96%B9%E6%B3%95%E9%99%A2101%E5%B9%B4%E5%BA%A6%E9%87%91%E8%A8%B4%E5%AD%97%E7%AC%AC47%E8%99%9F%E5%88%91%E4%BA%8B%E5%88%A4%E6%B1%BA)
    姓名：林益世
    工作/職位/關係：立法委員, 中國國民黨之中央政策委員會執行長
    罪名：恐嚇得利罪, 公務員財產不明罪
    有期徒刑：88月
    易科罰金：FALSE
    緩刑：0年
    涉貪金額：63000000
> 雖然林益世索賄8300萬，不過實際收到是6300萬。以6300萬計算。
> [name=張淵智]

    -
    姓名：沈若蘭
    工作/職位/關係：林益世之母
    罪名：無罪
    -
    姓名：彭愛佳
    工作/職位/關係：林益世之配偶
    罪名：無罪
    -
    姓名：沈煥章
    工作/職位/關係：沈若蘭之弟
    罪名：無罪
    -
    姓名：沈煥瑶
    工作/職位/關係：沈若蘭之弟
    罪名：無罪

## 專案各階段

### 第零階段 爬貪污判決書（已完成）

2014-8
利用iMacros從[法律法源網](http://fyjud.lawbank.com.tw/index.aspx)爬所有案由為貪污的判決書（csv檔），地方、高等、最高三審級皆以爬完。法律法源網的更新頻率沒有[司法院資料庫](http://jirs.judicial.gov.tw/FJUD/)高，但是他的搜索系統比較完整好用。
判決書Data package . csv：
[地方法院&高等法院(2000-2014) 7z](https://drive.google.com/file/d/0B9fzCPAUltsqOElYc1N0TFRaSTg/edit?usp=sharing)
    解壓縮以後共2X個資料夾，H開頭為高等法院；L為地方
    ex HKaohsiung高雄高等分院；LTaipei台北地方法院
[最高法院(1996-2014) 7z](https://drive.google.com/file/d/0B9fzCPAUltsqZVBLNE1zclRFYnM/edit?usp=sharing)
待解問題：
民國100年以前絕大部分判決書，被告姓名與公司都被遮蓋起來，無法得知。據說司法院內部帳號可以看沒被遮蓋起來的版本。
11-28有寄信過去，~不過還沒有回應~：1208回應了，除了國家級研究案（如中研院申請），其他不予開放

### 第一階段 資料梳理、填充欄位（進行中）

由於發現到的遮蓋問題，決定先縮小處理範圍當作嘗試。民100-102年的判決書除了少數重審的案件外，其他都沒有匿名；而地院的內容相對單純，於是把他拉出來單獨打包：
[100-102年地方法院判決包7z](https://drive.google.com/file/d/0B9fzCPAUltsqWUZLWGw0OU8tUUU/edit?usp=sharing)
    \- 將所有地院判決【判決日期100-102年】丟到同一資料夾的版本

~判決書為了可讀性、整齊等等因素，會斷行。在資料處理上變得麻煩。~
嘗試作了脫斷行符號的處理，另外判決書內含表格，決定先不動他：
[100-102年地方法院判決包（脫符）7z](https://drive.google.com/file/d/0B9fzCPAUltsqc3YxSzRQcFNHNjQ/view)

判決書欄位（第一段）的部份，欄位為（檔名/字號/時間/法院/檢察官起訴案由/被告名單），還有一些地方需要修。11-11 怒修，應該沒什麼大問題了（有四個案件沒抓到被告，但那四件都是很神奇的案子，判決結果都不受理，暫時放著）：
欄位由左至右（檔名/字號/日期/法院/檢察官起訴案由/被告數/被告名單）
[google試算表](https://docs.google.com/spreadsheets/d/19wSWyJ2pYObcu4H40chbCH_NO7VxICJ_xd7PSJQbuRE/edit#gid=1793425348)

判決書欄位（第二段）的部份，11-28 抓了絕大部分被告的主罪，手動將判決書格式正規化，有些被告公司與代理人的部份沒處理好，有些代理人非被告，故主文不會將之列入（但有些會，判決書在這塊寫得很凌亂，還要想一下如何抽取）
12-08抓了有罪被告的宣告刑，欄位（檔名/被告/罪名/徒刑/是否易科罰金/罰金/緩刑）->（[連結](https://drive.google.com/open?id=1T3d2yLHVfFcFBiRrGIKKN9ZcAOq2nQ03WMzppAmkTys&authuser=0)）

查詢g0v資料中心，發現有歷屆公職選舉資料（包含政黨屬性）：
[http://data.g0v.tw/dataset/92/resource/f52cb013-1a1c-467b-8a8c-0bef20d55936](http://data.g0v.tw/dataset/92/resource/f52cb013-1a1c-467b-8a8c-0bef20d55936)
也許這是查詢政黨屬性的起步

### Big Issue

遇上一個大麻煩，有一部份主文在寫被告罪刑時，用附表呈現的方式（也就是在書尾的地方寫一個表格列出），舉例：

    郭美瑩,犯如附表三編號至編號所示之罪，主文及宣告刑各如附表三編號至編號所載。

    （節錄列表）
    ┌─┬────┬─────────────────────────────┐
    │編│犯罪事實│主文及宣告刑 │
    │號│ │ │
    ├─┼────┼─────────────────────────────┤
    ││如附表一│郭美瑩共同連續犯行使偽造公文書罪，處有期徒刑壹年貳月；減為│
    │ │編號1 至│有期徒刑柒月。如附表二編號1 至編號5 所示之偽造印文、署押，│
    │ │5 所示 │及扣案之手機壹支（含電池壹個、SIM 卡壹張），均沒收。 │
    ├─┼────┼─────────────────────────────┤

有沒有大大有好想法處理這段？
> 可以先觀察判決書這類表格的形式是否一致，比如說每個欄位都是由 "|(...)|"  這樣子的格式分隔開，表頭的各個欄位header亦同，但不同的地方是表頭是從 "┌(...)" 這樣子的 pattern 的下一列開始，而每一列內容則是從 "├(...)" 的下一列開始，按照這樣的規則應該可以把表格內容整併入指定的資料結構中供取用。 (不好意思，先把12/20那天的~嘴砲~討論先記錄一下，我還是優先會處理好職位身分的偵測，有需要再回來支援這邊的parsing)
> [name=Keith N]

> [http://test.ronny.tw/table.html](http://test.ronny.tw/table.html) 做了一個陽春的可以抓表格的 API
> [name=Ronny W]


表格結構化?
> 我對於這些表格做了些觀察，沒有統一的格式，甚至有表格內還有表格的情況，就像word一樣可畫任意表格，表格內容也不一定遵守column的schema。這個[evernote](https://www.evernote.com/l/AMe-3Qfov0xE4Yb63yOrvh7In82dIWOYGYI ) 有我的一些觀察和一些畸形表格”樣本” 。
> [name=煒清 林]

> [code](https://github.com/superChing/extract_declared_sentence)可以抽取cell，雖然不算完全結構化。
> [name=煒清 林]

> 各位大大好，我非資工系出身對程式也完全不通，不過工作主要接觸貪瀆案件，覺得貪瀆案件對於社會真的影響很大，無意間發現這個網站覺得你們好厲害，希望可以就自己所知貢獻，所有判決書的表格都是「漢書」系統登打，才會導致表格變成上面這個樣子，另外不知道你們是如何搜尋洩密案件，我認為洩密案件是一個貪瀆案件的前端，他是在刑法裡，貪汙治罪條例裡面不會有洩密；還要注意我曾碰過案由跟判決書內容會不一致的情形。有關新聞的部分，我推薦官方新聞會比較準確，各地檢署、調查局、廉政署對於貪瀆案件發動，基本上都會在搜索、約詢、判決當日有官方新聞稿。
> [name=胡雨露]

由於在下不是資工相關科系出身，誠徵對判決書有興趣的高手助陣
各路大神提供的Approach：
1.regular expression & pattern（目前作法）
2.~machine learning~

### 第二階段 網站上線

部份資料處理好之後，就可以開始想查詢網站的問題。
相對一般會google的問題，使用者知道問題但不知道答案；貪污查詢很可能面臨使用者「不知道問題也不知道答案」。
可以跟過去的新聞報導作連結
也可以跟其他專案整合

### 第三階段 擴充資料範圍

第一階段東西有刻出來的話，那地院就不是問題。接下來就是高等法院、最高法院的判決書處理，這時候就能夠加上案件從地方法院打到最高法院的歷審呈現。也可以爬其他相關的法律判決。

## TO-DO list

#### 資料擷取部份

- [x] 抓取被告 工作/職位/關係 欄位--\> _Keith Ning_
> 有的判決書一篇竟然就長達20~50萬字，造成原本現成的詞彙解析程式運作不能 XD 因此使用divide-n-conquer重新修改處理流程中~
> [name=Keith N]

> 超酷XD (Y)
> [name=楊孟勳]

> 對於一樓經驗表示完全可以理解XD
> [name=張淵智]

> 15/4/15：前幾天嘗試用re寫pattern去抓 大概可以抓到20%(這比例..orz) 
> [name=張淵智]

- [x] 抓取表格內容補足 宣告刑 欄位
> [code](https://github.com/superChing/extract_declared_sentence)  Brief:做的事是把表格cell抽出來再用regular expression找宣告刑。table九成可以抽取cell內容。但宣告刑recall我猜不高，這需要sample評估多少沒抓出來。
> [name=煒清 林]

> 稍微回應一下，「'禠'!='褫'」如果仔細看的話，一個是一點，一個是兩點。判決書有不少像這種差一點的（機歪）錯別字
> [name=張淵智]

- [ ] 抓取法官欄位
- [ ] 抓取涉貪金額
- [x] 國字轉數字
- [ ] 查詢被告政黨屬性
\-\-\-\-\-\-
- [ ] 處理高院/最高法院判決書
- [ ] 製作與線上判決書同步更新的程式
- [ ] 增加判決書涵蓋範圍（詐欺/圖利/財產不明/登載不實/背信）
#### 網站製作部份

- [ ] 介面/內容規劃
- [ ] 前端
- [ ] 後端
#### 資料開放部份

- [ ] 將100年後少數匿名判決書開放
- [ ] 將99年前匿名判決書開放
- [ ] 將起訴書開放

## 目前成果


判決書Data package . csv：
[地方法院&高等法院(2000-2014) 7z](https://drive.google.com/file/d/0B9fzCPAUltsqOElYc1N0TFRaSTg/edit?usp=sharing)
    解壓縮以後共2X個資料夾，H開頭為高等法院；L為地方
    ex HKaohsiung高雄高等分院；LTaipei台北地方法院
[最高法院(1996-2014) 7z](https://drive.google.com/file/d/0B9fzCPAUltsqZVBLNE1zclRFYnM/edit?usp=sharing)

[100-102年地方法院判決包7z](https://drive.google.com/file/d/0B9fzCPAUltsqWUZLWGw0OU8tUUU/edit?usp=sharing) （1109：把一些當初抓跑掉的判決書補齊）
[100-102年地方法院判決包（脫符）7z](https://drive.google.com/file/d/0B9fzCPAUltsqc3YxSzRQcFNHNjQ/view) （ver1129:手動修正跑掉的格式，1216發現做得不太好，很多地方沒脫到...）
    \- 將所有地院判決【判決日期100-102年】丟到同一資料夾的版本

判決書欄位（第一段），欄位（檔名/字號/時間/法院/檢察官起訴案由/被告數/被告名單）：[google試算表](https://docs.google.com/spreadsheets/d/1vufl16kKVJIMNLO-WMA-U_8GbuX-JjuGuoRkHwGBjbw/edit?usp=sharing)
判決書欄位（第二段部份），欄位（檔名/被告/罪名/是否易科罰金/罰金/緩刑）：[google試算表](https://drive.google.com/file/d/0B9fzCPAUltsqQUZ3MjRKLWdmTjg/view?usp=sharing)
(2015-01-31 簡化罪名 and 罰金數字化)
註1：covered指主文中被告匿名，無法確認哪位是哪位
註2：need check目前剩下未列入主文的代理人或公司，還有名字英文三種
[原始碼](https://github.com/nt90561/get_attribute) by 淵智（python2）（過期）

讀取判決書內的表格（python3） by 煒清
[https://github.com/superChing/extract\_declared\_sentence](https://github.com/superChing/extract_declared_sentence)

從判決書拿出字號、日期、案由、被告 by csferng（過期）
[https://github.com/csferng/AnalyzeVerdict](https://github.com/csferng/AnalyzeVerdict)

中文字大寫轉換（Python 3）
[https://github.com/rschiang/py-conv-digit](https://github.com/rschiang/py-conv-digit)

初版網站@heroku
[http://g0v-uncover.herokuapp.com/](http://g0v-uncover.herokuapp.com/)

## 需求&其他相關

#### 如果要顯示判決書稀少字

司法院對於非big5編碼的字會用造字的方式處理，並提供下載：
[http://www.judicial.gov.tw/download/download01.asp#D01](http://www.judicial.gov.tw/download/download01.asp#D01)
我自己使用的經驗，確實有些字因此顯示，但還是不全

#### 相關連結

[FB貼文：中國國民黨政權涉及回扣貪汙一覽表(一)~(四)](https://www.facebook.com/peng.jodie/posts/745066935582339)
[蘋論：彰化這一戰很關鍵](http://www.appledaily.com.tw/appledaily/article/headline/20141119/36216158/%E5%8F%B8%E9%A6%AC%E8%A7%80%E9%BB%9E%EF%BC%9A%E5%BD%B0%E5%8C%96%E9%80%99%E4%B8%80%E6%88%B0%E5%BE%88%E9%97%9C%E9%8D%B5%EF%BC%88%E6%B1%9F%E6%98%A5%E7%94%B7%EF%BC%89)
FB貼文：[國民黨未來對台灣危害最大的將是朱立倫，他是馬英九加強版。](https://www.facebook.com/foreign.currency.trade/posts/10204589903174787?fref=nf)
八卦版文章：[中國黨貪污一覽表](http://disp.cc/b/163-7SjF)
研究文獻：中研院政治所吳重禮：Chung-li Wu. Charge Me if You Can: Assessing Political Biases in Votebuying Verdicts in Democratic Taiwan (2000–2010). The China Quarterly, Available on CJO 2012 doi:10.1017/S0305741012000847  中文版：[http://newsletter.sinica.edu.tw/file/file/77/7792.pdf](http://newsletter.sinica.edu.tw/file/file/77/7792.pdf)

司法院量刑系統--量刑資訊系統將判決書加以「量化」，使用者只要在查詢介面 輸入查詢條件，量刑資訊系統就會將符 合查詢條件的所有類似案件檢索出來， 提供該類似案件的平均刑度、最高刑度、最低刑度及量刑分布全貌圖
[http://www.judicial.gov.tw/revolution/judReform06.asp](http://www.judicial.gov.tw/revolution/judReform06.asp)
[http://www.judicial.gov.tw/jw9706/pdf/1700-1.pdf](http://www.judicial.gov.tw/jw9706/pdf/1700-1.pdf)
透過判決書萃取出貪污金額需要專業法律人閱讀判決之文意，也就是說，這需要大量的工人智慧，而司法院已經建立一個量刑系統，或許可以嘗試用他們的資料庫取得被告對應貪污金額及刑度的資訊

網站可以參考的數據呈現方式
[http://designspiration.net/image/25875462678551/](http://designspiration.net/image/25875462678551/)

#### 相關專案

[中文處理工具簡介](https://g0v.hackpad.tw/aco0Hxp4IEz)
[議員判刑資料](https://g0v.hackpad.tw/ucTpAApiE7G)
[政商透明化](https://g0v.hackpad.tw/GuanXi--5gygVb26WId)

#### 參與活動

1/25(日) 10:00 - 18:00 [第零次法律松](https://g0v.hackpad.com/--jS8mZtWlSWo)
當天活動摘要：
- 淵智繼續資料爬梳 , 孟勳 製作網站
- 司改會: 中豪大哥提議了資料分析的建議 ;
- 宜珊律師 & 執秘 林瑋婷給了實務上關於貪汙案件的實況、
- 以及法官量刑尺度的不同 , 是未來司改會關心的爭點之一。
 技術端:
- 甯格致 ( [Keith Ning](https://www.facebook.com/keith.ning.16) ) 關於社會網路分析可以提供協助 ;
- [林鉦育](https://www.facebook.com/ntuaha) 提供資料分析建議 ;
- 郭俊儀 : 後台協助
- 姜柏任 ( [Poren Chiang](https://www.facebook.com/RenRenChiang) ) 寫完轉換器


我們歡迎下列各種夥伴：
1.  對判決書閱讀熟悉敏銳
2.  自然語言處理高手
3.  對網站提供內容有想法
4.  對貪腐、貪污、官商勾結等相關議題有興趣
↓↓↓
[https://www.facebook.com/groups/876229695725086/](https://www.facebook.com/groups/876229695725086/)
歡迎加入討論

## Parse資料上線

[https://www.parse.com/apps/uncovertw/](https://www.parse.com/apps/uncovertw/)
建了兩個表，分別是judgment和party。
需要使用api或更新的人請找張淵智XD

