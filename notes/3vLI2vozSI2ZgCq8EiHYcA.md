---
title: "台灣公家機關+黨部IP收集計劃"
tags: hackpad
---

# 台灣公家機關+黨部IP收集計劃

> [點此觀看原始內容](https://g0v.hackpad.tw/81RtWpVBI84)


## Why? ：為什麼要做[這個](https://j.mp/g0vtwip)

要講原因，得先講兩個跟維基百科相關的故事。

最近在收集維基百科與國會之間的關係，發覺在美國最近發生了一件[紐約警局惡意的編纂警察打人的相關英文維基百科條目](https://www.facebook.com/groups/tw.wiki/permalink/368080586713053/)事件，引起了美國的網民們開始收集由NYPD的IP過來匿名的維基百科編輯資料，並且做成一個隨時找到匿名編輯就放上推特的機器人[NYPD edits](https://www.facebook.com/groups/tw.wiki/permalink/368080586713053/)。

這是今年(2015)才發生的事情，至於兩年前，國會山莊的資訊中心有跟維基在華盛頓特區的志工合作，把從capitol hill出來的維基百科匿名編輯做成[推特推播](https://twitter.com/congressedits)。

所以光是很小的看，如果能夠把這些IP都整理出來，至少可以做中文維基百科的匿名推播機器人，確認沒有利益衝突的編輯從各個公家的電腦中發出來（比方說大埔事件的從條文中刪除掉）。至於其他的應用也許像是在ptt的匿名編輯也可以追來源？（不只是在台科大或清交的IP可以查出來）

## How? ：打算怎麼做，授權方式

### 授權方式

對照表就採CC0吧，這本來就是整理資料而已，沒什麼創作成份在裡頭
倒是做推特的方式得查一下，看美國的做法是什麼、怎麼授權的。

### 具體的SOP：還在產生中

底下是一些零碎的想法
- 資料收集其實可以用sheethub？
- 另外有人提議寫公文去問立法院是用哪些IP...
- 蒐集台灣所有的公家機關（初步可以先從鄉鎮市公所以及議會）的地址
- 填入這些地址所用的IP區段
- 另外一個可能是請張善政開放open data？
- 網路上[隨便亂查發現的資料](http://www.cha086.com/ip/HyGl0Gc5L3DJJOb2) ，講立法院的IP是192.192.16.0 至 192.192.16.255 IP段信息（跟中國工商專科學校共用）
- 目前台灣發放IP的單位好像還是TWNIC，去調一下資料應該就知道目前發給[GSN（政府網際服務網）](http://gsn.nat.gov.tw/index.html) 的有哪些區段了
- [http://rms.twnic.net.tw/twnic/User/Member/Search/main7.jsp?Order=ORG.ID](http://rms.twnic.net.tw/twnic/User/Member/Search/main7.jsp?Order=ORG.ID)
- 看國民黨黨部的IP不知道會不會很有趣XD
- 先從台北市政府的IP搜尋（因為柯文哲一心向善）
- 或者是圖書館

### 進階查詢維基編輯歷史設定

用萬用字元查詢維基百科編輯歷史，需要打開進階功能，請照下列步驟進行：
1.  用自己的帳號登入維基百科
2.  進入「偏好設定」 --> 「小工具」 --\> 「瀏覽工具」這段落
3.  勾選『進階用戶貢獻查詢 使用API查詢IP區段或指定前綴字串的使用者貢獻，支持/16及/24至/32的CIDR區段及通配符「*」』」
4.  儲存設定，這樣就可以用萬用字元查詢特定區段IP的編輯歷史了！

## Need?：需要哪些技術

其實就是google spreadsheet＋跟公家機關要資料的討資料技能吧...
> 這個計畫很有趣，我會建議可以順便把一些法人的IP也找出來。
> [name=YingChu C]

> 寫在這:只好等這一陣子先把自己的工作完成才能開始了。+++
> [name=YingChu C]

> 與其建議，不如動手作：直接開共筆或補充，把法人IP列出。
> [name=ipa c]

可參考連結：
- [台灣學術網路連線單位IP位址及領域名稱](http://life.nthu.edu.tw/~fmhsu/network/tanet-ip.htm)
- [IP/Domain網域查詢](http://www.ntunhs.net)
- 對照表（整理中）[https://docs.google.com/spreadsheets/d/1U78660VCZhYSe99jL4qF-cHq3UuH337MjoXuY2GX_Es/edit?usp=sharing](https://docs.google.com/spreadsheets/d/1U78660VCZhYSe99jL4qF-cHq3UuH337MjoXuY2GX_Es/edit?usp=sharing)

### 把匿名編輯公告做成機器人公告放在臉書或推特的技術

> 不知這有沒有專業的工程師能來幫忙...
> [name=上官良治]


### 這份對照表可能有多大？

也許我們得先從「到底台灣有多少政府和法人的網域？」來查起，根據[TWNIC的資料庫查詢](http://www.twnic.net.tw/newdn/data/data.htm) ，2015年的域名如下：
| gov.tw | 2232筆 | 通常政府機構都是gov.tw結尾，所以所有的行政、立法、司法機關應該都在這個域名下 |
| --- | --- | --- |
| edu.tw | 479筆 | 維基百科的匿名編輯，以大學院校的佔大宗，這裡頭絕大多數是edu.tw結尾，例如台大。（不過教育部這個政府機構也是以edu.tw結尾） |
| org.tw | 11544筆 | 大多數台灣的法人團體都是org.tw結尾，像是中國國民黨（kmt.org.tw），靈糧堂（www.llc.org.tw） |
| net.tw | 1722筆 | net.tw是一個比較什麼都可以的域名，詳見此討論： www.domainclub.org/showthread.php?t=34675#.VUtA4BfZ_uc |
| 總計 | 15977筆 |  |
所以，除去com.tw的域名，這筆資料在2015年如果蒐集完整，約最大值會是16000筆域名。看TWNIC的資料庫近年的成長趨勢，這些域名應該這幾年已經達到高原期，不會再增加了。不過我估計幾個重要應該監督流量大的宗教團體、倡議組織、政府機關等法人單位加起來，幾百筆重要的應該就很常用了。


