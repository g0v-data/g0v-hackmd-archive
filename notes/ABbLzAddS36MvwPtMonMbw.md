---
title: "公立動物收容所資訊統整系統"
tags: Animal,hackpad
---

# 公立動物收容所資訊統整系統

> [點此觀看原始內容](https://g0v.hackpad.tw/JBhVDOPxhxe)


## 欲統整之資料來源（坑！）

＊全國各縣市公立動物收容所網站資訊初步統整 (5/30更新連結 GOOGLE可編輯連結)
    (網頁連結整理以及名詞對照表以及各縣市收容所資料下載處)
[https://docs.google.com/spreadsheets/d/1c-m1acP78YY5Y8rTtSM1XfARM1GVEwzZ6Y5RdemTRjY/edit?usp=sharing](https://docs.google.com/spreadsheets/d/1c-m1acP78YY5Y8rTtSM1XfARM1GVEwzZ6Y5RdemTRjY/edit?usp=sharing)
> 網址裡的 \- 有些被換成 ─ ，連不到時檢查一下
> [name=otaq]

> 我在底下的 table 修了，感謝回報
> [name=Audrey T]

- FB專頁：[https://www.f](https://www.facebook.com/groups/483935991762364/?notif_t=group_added_to_group)[acebook.com/groups/483935991762364/?notif\_t=group\_added\_to\_group](https://www.facebook.com/groups/483935991762364/?notif_t=group_added_to_group)
- e.g. 台北（[HTML](http://www.tcapo.gov.taipei/ct.asp?xItem=68666118&CtNode=69752&mp=105033)、[JSON](http://data.taipei/opendata/datalist/apiAccess?scope=resourceAquire&rid=f4a75ba9-7721-4363-884d-c3820b0b917c)、[CSV](http://data.taipei/opendata/datalist/apiAccess?scope=resourceAquire&rid=f4a75ba9-7721-4363-884d-c3820b0b917c&format=csv)(big5)、[Metadata help](http://data.taipei/opendata/datalist/datasetMeta?oid=ee2dbabd-4e41-4f2f-96b2-3189ed2644f6)）桃園（[Word+PDF](http://www.tycg.gov.tw/animal/home.jsp?id=82&parentpath=0,37)）... 六都的資料比較齊
- ...歡迎認領 & 轉成下列 Schema 欄位（先用 CSV 輸出即可）
    - 共用 repo: [https://github.com/g0v/animal.coa](https://github.com/g0v/animal.coa)
    - 單縣市可以兩三組人做，互補長短，坑很寬不會擠的 XD
        - 多組程式碼/網址時，可以用 Ctrl-Enter 鍵入（例如「嘉義市」）
> 那在 repo 裡的話要怎麼放呀？
> [name=JmeHsieh]

> 「嘉義市-JK」or 「嘉義市-dirty」or「嘉義市-VisualBasic」
> [name=Audrey T]

> okok，瞭解～
> [name=JmeHsieh]

> repo中的"台"需要轉成"臺"嗎？
> [name=johnny]

> 好主意 — 幫忙 git mv + push 一下?
> [name=Audrey T]

> 完成 :)
> [name=johnny]

> 想要建一個「嘉義市-JK」，請問該如何做呢？
> [name=Jimmy K]

> GitHub 的 Web 界面 [https://github.com/g0v/animal.coa/new/gh-pages](https://github.com/g0v/animal.coa/new/gh-pages)
> [name=Audrey T]

> 可以鍵入檔名為 JK/parse_test.bas 但中文好像不支援
> [name=Audrey T]

> 要用中文目錄名，可能得用 [GitHub Windows](https://windows.github.com/) 取出 g0v/animal.coa 再新增目錄。
> [name=Audrey T]

> 感謝！
> [name=Jimmy K]

> **6/13投影片** [https://drive.google.com/file/d/0B1XnVAHwQZa7YzB6blhMMHRrcnc/view?usp=sharing](https://drive.google.com/file/d/0B1XnVAHwQZa7YzB6blhMMHRrcnc/view?usp=sharing)
> [name=Eric]

> **FB專頁**
> [name=Eric]

> [https://www.facebook.com/groups/483935991762364/?notif\_t=group\_added\_to\_group](https://www.facebook.com/groups/483935991762364/?notif_t=group_added_to_group)
> [name=Eric]

> 各縣市政府動保預算表
> [name=Ocean L]

> [**h**](https://docs.google.com/spreadsheets/d/19fjjEfVEpkwRp1gsZaNXuZ85JYgHne-jZOArNRtAJwU/edit#gid=0)[**ttps://docs.google.com/spreadsheets/d/19fjjEfVEpkwRp1gsZaNXuZ85JYgHne-jZOArNRtAJwU/edit#gid=0**](https://docs.google.com/spreadsheets/d/19fjjEfVEpkwRp1gsZaNXuZ85JYgHne-jZOArNRtAJwU/edit#gid=0)
> [name=Ocean L]



| **行政區** | URL | 認領人 | 程式碼 | Notes | 範例輸出網址 |  |
| --- | --- | --- | --- | --- | --- | --- |
| 臺北市 | [http://www.tcapo.gov.taipei/ct.asp?xItem=68666118&CtNode=69752&mp=105033](http://www.tcapo.gov.taipei/ct.asp?xItem=68666118&CtNode=69752&mp=105033) | jimmy | [https://gist.github.com/jimyhuang/894d699351dbba2e2018](https://gist.github.com/jimyhuang/894d699351dbba2e2018) | 欄位名稱尚未轉換 | [https://github.com/g0v/animal.coa/blob/gh-pages/%E8%87%BA%E5%8C%97%E5%B8%82/all.csv](https://github.com/g0v/animal.coa/blob/gh-pages/%E8%87%BA%E5%8C%97%E5%B8%82/all.csv) | php |
| 新北市 | [http://www.ahiqo.ntpc.gov.tw/adopt_list.php](http://www.ahiqo.ntpc.gov.tw/adopt_list.php) | jme | [https://github.com/JmeHsieh/animal.coa/tree/gh-pages/新北市/new\_taipei\_animal/spiders](https://github.com/JmeHsieh/animal.coa/tree/gh-pages/新北市/new_taipei_animal/spiders) | 欄位名稱尚未轉換 | [https://github.com/JmeHsieh/animal.coa/blob/gh-pages/新北市/2015-05-31/2015-05-31.csv](https://github.com/JmeHsieh/animal.coa/blob/gh-pages/新北市/2015-05-31/2015-05-31.csv) | python |
| 基隆市 | [http://www.klaphio.gov.tw/receiving_notice.php](http://www.klaphio.gov.tw/receiving_notice.php) | hanksudo | [https://github.com/hanksudo/crawlers/tree/master/animal.coa](https://github.com/hanksudo/crawlers/tree/master/animal.coa) |  | [https://github.com/g0v/animal.coa/blob/gh-pages/%E5%9F%BA%E9%9A%86%E5%B8%82/all.csv](https://github.com/g0v/animal.coa/blob/gh-pages/%E5%9F%BA%E9%9A%86%E5%B8%82/all.csv) | python |
| 桃園市 | [http://www.tycg.gov.tw/animal/home.jsp?id=82&parentpath=0,37](http://www.tycg.gov.tw/animal/home.jsp?id=82&parentpath=0,37) | au | [https://github.com/g0v/animal.coa/blob/gh-pages/%E6%A1%83%E5%9C%92%E5%B8%82/html2csv.pl](https://github.com/g0v/animal.coa/blob/gh-pages/%E6%A1%83%E5%9C%92%E5%B8%82/html2csv.pl) | 欄位名稱尚未轉換 | [https://github.com/g0v/animal.coa/blob/gh-pages/%E6%A1%83%E5%9C%92%E5%B8%82/2015-05-29.csv](https://github.com/g0v/animal.coa/blob/gh-pages/%E6%A1%83%E5%9C%92%E5%B8%82/2015-05-29.csv) | perl |
| 新竹市 | [http://puppy.hccg.gov.tw/?cn.html](http://puppy.hccg.gov.tw/?cn.html) | ly | [https://github.com/g0v/animal.coa/blob/gh-pages/%E6%96%B0%E7%AB%B9%E5%B8%82/html2csv.js](https://github.com/g0v/animal.coa/blob/gh-pages/%E6%96%B0%E7%AB%B9%E5%B8%82/html2csv.js) | 前一百筆, 欄位名稱可能不一樣 | [https://github.com/g0v/animal.coa/blob/gh-pages/%E6%96%B0%E7%AB%B9%E5%B8%82/all.csv](https://github.com/g0v/animal.coa/blob/gh-pages/%E6%96%B0%E7%AB%B9%E5%B8%82/all.csv) | php |
| 新竹縣 | [http://animalprotection.hchg.gov.tw/sca/C/Animal.aspx](http://animalprotection.hchg.gov.tw/sca/C/Animal.aspx) | jimmy | [https://gist.github.com/jimyhuang/e94f9cd5a3fd651a99ed](https://gist.github.com/jimyhuang/e94f9cd5a3fd651a99ed) | 欄位名稱尚未轉換 | [https://github.com/g0v/animal.coa/blob/gh-pages/%E6%96%B0%E7%AB%B9%E7%B8%A3/all.csv](https://github.com/g0v/animal.coa/blob/gh-pages/%E6%96%B0%E7%AB%B9%E7%B8%A3/all.csv) | php |
| 臺中市 | [http://www.animal.taichung.gov.tw/lp.asp?CtNode=7813&CtUnit=1687&BaseDSD=57&mp=119020](http://www.animal.taichung.gov.tw/lp.asp?CtNode=7813&CtUnit=1687&BaseDSD=57&mp=119020) | johnny | [https://github.com/g0v/animal.coa/blob/gh-pages/%E8%87%BA%E4%B8%AD%E5%B8%82/crawler.py](https://github.com/g0v/animal.coa/blob/gh-pages/%E8%87%BA%E4%B8%AD%E5%B8%82/crawler.py) | 註：共有三個URL(見上excel)，網址1、2內容相同呈現方式不同(擇一即可)，網址3和前二者內容不同，皆須抓下來。  
  
欄位名稱尚未轉換 | [https://github.com/g0v/animal.coa/blob/gh-pages/%E8%87%BA%E4%B8%AD%E5%B8%82/2015-06-03-adopt.csv](https://github.com/g0v/animal.coa/blob/gh-pages/%E8%87%BA%E4%B8%AD%E5%B8%82/2015-06-03-adopt.csv<br/><br/>https://github.com/g0v/animal.coa/blob/gh-pages/%E8%87%BA%E4%B8%AD%E5%B8%82/2015-06-03-keep.csv) | python |
| 南投縣 | [http://adcc.nantou.gov.tw/introduce/leading.asp?id=](http://adcc.nantou.gov.tw/introduce/leading.asp?id={F8D1EE49-C251-424F-B145-BA84F111E897}) | johnny | [https://github.com/g0v/animal.coa/blob/gh-pages/%E5%8D%97%E6%8A%95%E7%B8%A3/crawler.py](https://github.com/g0v/animal.coa/blob/gh-pages/%E5%8D%97%E6%8A%95%E7%B8%A3/crawler.py) | 註：共有兩個網址(見上excel)，兩者內容不同，皆須抓下來。 | [https://github.com/g0v/animal.coa/tree/gh-pages/%E5%8D%97%E6%8A%95%E7%B8%A3/csv/2015-06-04](https://github.com/g0v/animal.coa/tree/gh-pages/%E5%8D%97%E6%8A%95%E7%B8%A3/csv/2015-06-04) | python |
| 嘉義市 | [http://www.dog.dias.com.tw/announcement.html](http://www.dog.dias.com.tw/announcement.html) | JK, dirty | [https://github.com/g0v/animal.coa/blob/gh-pages/%E5%98%89%E7%BE%A9%E5%B8%82/get.ls](https://github.com/g0v/animal.coa/blob/gh-pages/%E5%98%89%E7%BE%A9%E5%B8%82/get.ls<br/><br/>https://github.com/g0v/animal.coa/blob/gh-pages/%E5%98%89%E7%BE%A9%E5%B8%82-JK/vb/parse_test.bas<br/><br/>https://github.com/g0v/animal.coa/blob/gh-pages/%E5%98%89%E7%BE%A9%E5%B8%82-JK/py/py_parse_test.py) | 第二個是visual basic  
  
第三個是python | [https://github.com/g0v/animal.coa/blob/gh-pages/%E5%98%89%E7%BE%A9%E5%B8%82/all.csv](https://github.com/g0v/animal.coa/blob/gh-pages/%E5%98%89%E7%BE%A9%E5%B8%82/all.csv  <br/><br/>https://github.com/g0v/animal.coa/blob/gh-pages/%E5%98%89%E7%BE%A9%E5%B8%82-JK/vb/jiayi_wt_img.csv<br/><br/>https://github.com/g0v/animal.coa/blob/gh-pages/%E5%98%89%E7%BE%A9%E5%B8%82-JK/py/eggs.csv) | 第二個是visual basic  
  
第三個是python3 |
| 嘉義縣  
(全國) | [http://www.ldcc.gov.tw/Announce/LawKSIndex?AnnounceTypeID=15](http://www.ldcc.gov.tw/Announce/LawKSIndex?AnnounceTypeID=15) | ninthday |  | 在全國動物推廣動物認領養平台上有資料 |  | php |
| 臺南市 | [http://asms.wsn.com.tw/TN/webClientMain.aspx?Page=0](http://asms.wsn.com.tw/TN/webClientMain.aspx?Page=0) | 小嘉,kiang | [https://github.com/g0v/animal.coa/tree/gh-pages/%E8%87%BA%E5%8D%97%E5%B8%82](https://github.com/g0v/animal.coa/tree/gh-pages/%E8%87%BA%E5%8D%97%E5%B8%82) |  | [https://github.com/g0v/animal.coa/blob/gh-pages/%E8%87%BA%E5%8D%97%E5%B8%82/all.csv](https://github.com/g0v/animal.coa/blob/gh-pages/%E8%87%BA%E5%8D%97%E5%B8%82/all.csv) | php |
| 高雄市 | [http://asms.wsn.com.tw/KS/webClientMain.aspx?Page=0](http://asms.wsn.com.tw/KS/webClientMain.aspx?Page=0) | 小嘉,kiang | [https://github.com/g0v/animal.coa/tree/gh-pages/%E9%AB%98%E9%9B%84%E5%B8%82](https://github.com/g0v/animal.coa/tree/gh-pages/%E9%AB%98%E9%9B%84%E5%B8%82) |  | [https://github.com/g0v/animal.coa/blob/gh-pages/%E9%AB%98%E9%9B%84%E5%B8%82/all.csv](https://github.com/g0v/animal.coa/blob/gh-pages/%E9%AB%98%E9%9B%84%E5%B8%82/all.csv) | php |
| 宜蘭縣 | [http://asms.wsn.com.tw/eland/webClientMain.aspx?Page=0](http://asms.wsn.com.tw/eland/webClientMain.aspx?Page=0) | kiang | [https://github.com/g0v/animal.coa/tree/gh-pages/%E5%AE%9C%E8%98%AD%E7%B8%A3](https://github.com/g0v/animal.coa/tree/gh-pages/%E5%AE%9C%E8%98%AD%E7%B8%A3) |  | [https://github.com/g0v/animal.coa/blob/gh-pages/%E5%AE%9C%E8%98%AD%E7%B8%A3/all.csv](https://github.com/g0v/animal.coa/blob/gh-pages/%E5%AE%9C%E8%98%AD%E7%B8%A3/all.csv) | php |
| 臺東縣 | [https://sites.google.com/a/jbps.ttct.edu.tw/tai-dong-xian-dong-wu-fang-yi-suo/ren-yang-dong-wu-zhuan-qu/liu-lang-dong-wu-shou-rong-zhong-xin-1/dai-ling-yang-quan-mao-gong-gao](https://sites.google.com/a/jbps.ttct.edu.tw/tai-dong-xian-dong-wu-fang-yi-suo/ren-yang-dong-wu-zhuan-qu/liu-lang-dong-wu-shou-rong-zhong-xin-1/dai-ling-yang-quan-mao-gong-gao) | Eric | [https://github.com/fa23427/animal.coa/blob/gh-pages/%E5%8F%B0%E6%9D%B1%E7%B8%A3/main.php](https://github.com/fa23427/animal.coa/blob/gh-pages/%E5%8F%B0%E6%9D%B1%E7%B8%A3/main.php) | 欄位名稱尚未轉換 | [https://github.com/fa23427/animal.coa/blob/gh-pages/%E5%8F%B0%E6%9D%B1%E7%B8%A3/1040529.csv](https://github.com/fa23427/animal.coa/blob/gh-pages/%E5%8F%B0%E6%9D%B1%E7%B8%A3/1040529.csv) | php |
| 金門縣 | [http://www.kinmen.gov.tw/Layout/sub_A/index.aspx?frame=93](http://www.kinmen.gov.tw/Layout/sub_A/index.aspx?frame=93) | jme, hanksudo | [https://github.com/hanksudo/crawlers/tree/master/animal.coa](https://github.com/hanksudo/crawlers/tree/master/animal.coa<br/><br/>https://github.com/g0v/animal.coa/tree/gh-pages/金門縣-jme/jinmen_animal/spiders) | 欄位名稱尚未轉換 | [https://github.com/g0v/animal.coa/blob/gh-pages/%E9%87%91%E9%96%80%E7%B8%A3/all.csv](https://github.com/g0v/animal.coa/blob/gh-pages/%E9%87%91%E9%96%80%E7%B8%A3/all.csv<br/><br/>https://github.com/g0v/animal.coa/tree/gh-pages/金門縣-jme/files) | python |
| 澎湖縣 | [http://www.phldcc.gov.tw/ch/home.jsp?mserno=201110130001&serno=201110130001&contlink=ap/unit1.jsp](http://www.phldcc.gov.tw/ch/home.jsp?mserno=201110130001&serno=201110130001&contlink=ap/unit1.jsp) | kerker | [https://github.com/g0v/animal.coa/blob/gh-pages/%E6%BE%8E%E6%B9%96%E7%B8%A3/parse2csv.py](https://github.com/g0v/animal.coa/blob/gh-pages/%E6%BE%8E%E6%B9%96%E7%B8%A3/parse2csv.py) | 進所資料，非待認養資料。 | [https://github.com/g0v/animal.coa/blob/gh-pages/%E6%BE%8E%E6%B9%96%E7%B8%A3/output.csv](https://github.com/g0v/animal.coa/blob/gh-pages/%E6%BE%8E%E6%B9%96%E7%B8%A3/output.csv) | python |
| 苗栗縣 | [http://www.miaoli.gov.tw/animal_health/](http://www.miaoli.gov.tw/animal_health/) |  |  | 註: 官網首頁有放每日動物收容中心認領養公告，是pdf檔  
  
PDF似乎是公文掃描!! |  | php |
| 彰化縣(全國) | [http://www.chcgadcc.gov.tw/dog.asp](http://www.chcgadcc.gov.tw/dog.asp) | Eric | [https://github.com/g0v/animal.coa/blob/gh-pages/%E5%85%A8%E5%9C%8B%E8%B3%87%E6%96%99/ParseUrlJson2MySQL2.php](https://github.com/g0v/animal.coa/blob/gh-pages/%E5%85%A8%E5%9C%8B%E8%B3%87%E6%96%99/ParseUrlJson2MySQL2.php) | 註：彰化縣網站內容較少，希望以全國認領養平台增補 | [https://github.com/g0v/animal.coa/blob/gh-pages/%E5%85%A8%E5%9C%8B%E8%B3%87%E6%96%99/animal_table.sql](https://github.com/g0v/animal.coa/blob/gh-pages/%E5%85%A8%E5%9C%8B%E8%B3%87%E6%96%99/animal_table.sql) | php |
| 雲林縣(全國) | [http://animal-adoption.coa.gov.tw/preload.php?url=index](http://animal-adoption.coa.gov.tw/preload.php?url=index) | Eric | [https://github.com/g0v/animal.coa/blob/gh-pages/%E5%85%A8%E5%9C%8B%E8%B3%87%E6%96%99/ParseUrlJson2MySQL2.php](https://github.com/g0v/animal.coa/blob/gh-pages/%E5%85%A8%E5%9C%8B%E8%B3%87%E6%96%99/ParseUrlJson2MySQL2.php) | 官網資料直接連到全國認領養平台 | [https://github.com/g0v/animal.coa/blob/gh-pages/%E5%85%A8%E5%9C%8B%E8%B3%87%E6%96%99/animal_table.sql](https://github.com/g0v/animal.coa/blob/gh-pages/%E5%85%A8%E5%9C%8B%E8%B3%87%E6%96%99/animal_table.sql) | php |
| 屏東縣(全國) | [http://animal-adoption.coa.gov.tw/preload.php?url=index](http://animal-adoption.coa.gov.tw/preload.php?url=index) | Eric | [https://github.com/g0v/animal.coa/blob/gh-pages/%E5%85%A8%E5%9C%8B%E8%B3%87%E6%96%99/ParseUrlJson2MySQL2.php](https://github.com/g0v/animal.coa/blob/gh-pages/%E5%85%A8%E5%9C%8B%E8%B3%87%E6%96%99/ParseUrlJson2MySQL2.php) | 註: 官網無任何資料。全國認養平台也只有5隻狗。 (電詢收容所表示收容量每日超過上百隻，但不會每天公告上網) | [https://github.com/g0v/animal.coa/blob/gh-pages/%E5%85%A8%E5%9C%8B%E8%B3%87%E6%96%99/animal_table.sql](https://github.com/g0v/animal.coa/blob/gh-pages/%E5%85%A8%E5%9C%8B%E8%B3%87%E6%96%99/animal_table.sql) | php |
| 花蓮縣(全國) | [http://animal-adoption.coa.gov.tw/preload.php?url=index](http://animal-adoption.coa.gov.tw/preload.php?url=index) | Eric | [https://github.com/g0v/animal.coa/blob/gh-pages/%E5%85%A8%E5%9C%8B%E8%B3%87%E6%96%99/ParseUrlJson2MySQL2.php](https://github.com/g0v/animal.coa/blob/gh-pages/%E5%85%A8%E5%9C%8B%E8%B3%87%E6%96%99/ParseUrlJson2MySQL2.php) | 官網資料直接連到全國認領養平台 | [https://github.com/g0v/animal.coa/blob/gh-pages/%E5%85%A8%E5%9C%8B%E8%B3%87%E6%96%99/animal_table.sql](https://github.com/g0v/animal.coa/blob/gh-pages/%E5%85%A8%E5%9C%8B%E8%B3%87%E6%96%99/animal_table.sql) | php |
| 連江縣(全國) | [http://animal-adoption.coa.gov.tw/preload.php?url=index](http://animal-adoption.coa.gov.tw/preload.php?url=index) | Eric | [https://github.com/g0v/animal.coa/blob/gh-pages/%E5%85%A8%E5%9C%8B%E8%B3%87%E6%96%99/ParseUrlJson2MySQL2.php](https://github.com/g0v/animal.coa/blob/gh-pages/%E5%85%A8%E5%9C%8B%E8%B3%87%E6%96%99/ParseUrlJson2MySQL2.php) | 官網無動物資料，只能查全國認領養平台 | [https://github.com/g0v/animal.coa/blob/gh-pages/%E5%85%A8%E5%9C%8B%E8%B3%87%E6%96%99/animal_table.sql](https://github.com/g0v/animal.coa/blob/gh-pages/%E5%85%A8%E5%9C%8B%E8%B3%87%E6%96%99/animal_table.sql) | php |
| 統整 |  |  |  |  |  |  |

**SQLite schema**
(ps:但這個是政府開放資料的Schema資訊較少)
                   -->所以目前有打算去parse各縣市的資料
```txt
CREATE      (
id, animal\_id, animal\_subid,
animal\_area\_pkid, animal\_shelter\_pkid,
animal_place,
animal_kind,
animal_sex,
animal_bodytype,
animal_colour,
animal_age,
animal_sterilization,
animal_bacterin,
animal_foundplace,
animal_title,
animal_status,
animal_remark,
animal_caption,
animal_opendate,
animal_closeddate,
animal_update,
animal_createtime,
shelter_name,
album\_name, album\_file, album\_base64, album\_update,
cDate);

```
需要的多的欄位（參考初步統整試算表）請補充中英文在下面：
| 進所日期 | 動物種類 | 品種 | 年齡 | 性別 | 體型 | 晶片 | 絕育 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| animal_opendate | animal_kind | animal_pedigree | animal_age | animal_sex | animal_bodytype | animal\_has\_chip | animal_sterilization |
|  |  | new |  |  |  | new |  |
| 進所原因 | 個體情況描述 | 入所後醫療照護 | 地點 | 備註 | 照片 |
| --- | --- | --- | --- | --- | --- |
| animal\_entry\_reason | animal\_individual\_condition | animal\_medical\_care | animal\_found\_place | animal_remark | album_file |
| new | new | new |  |  |  |
| 收容所名稱 | 動物狀況 | 毛色 | 籠號 | 晶片號碼 | 開放認養日期 |
| --- | --- | --- | --- | --- | --- |
| shelter_name | animal_status | animal_colour | animal\_cage\_number | animal\_chip\_number | animal\_available\_date |
|  |  |  | new | new |  |
> animal\_chip\_number 跟 animal_chip 是否有重複？
> [name=JmeHsieh]

> 因為有的縣市只有提供"有/沒有"晶片，有的縣市有提供"晶片號碼"，所以新開一欄位
> [name=Eric]


記錄流水編號以及區域編號有助於全國與各地區資料整合。目前已知全國網站中與地區網站中使用相同編號的縣市：台北市、基隆市、新竹縣、台中市、台南市、高雄市、宜蘭縣


政府開放平台sqlite,每日更新(5/30):[https://www.dropbox.com/s/iu3j5du8ogcu45c/test15.sqlite?dl=0](https://www.dropbox.com/s/iu3j5du8ogcu45c/test15.sqlite?dl=0)

＊動物保護資訊網(這裡有各縣市公立動物收容所連結，如果上面整理的連結壞掉可以從這裡找)
 [http://animal.coa.gov.tw/html3/index\_09\_map.html#](http://animal.coa.gov.tw/html3/index_09_map.html#)
＊全國動物認領養平台原始資訊公開
    [http://data.coa.gov.tw/Query/ServiceDetail.aspx?id=177](http://data.coa.gov.tw/Query/ServiceDetail.aspx?id=177)
＊動物保護資訊網之「全國公立收容所收容處理情形統計表」下載處
 [http://animal.coa.gov.tw/html3/index\_06\_2.html](http://animal.coa.gov.tw/html3/index_06_2.html)



## 專案說明

        要解決流浪動物的問題，不能不**了解流浪動物的來源**。除了動保志工或愛心人士的親身觀察外，系統性的分析公立動物收容所的每日捕捉公告可提供另一種角度。

        過去幾年來，政府共編列一千五百多萬預算設計公立動物收容所資訊系統(如下表)，但實際檢視各縣市動物收容所或動物防疫所的網站發現，**每個縣市的動物捕捉公告之公布型態各異，公佈項目與用詞並不統一，許多重要的訊息也未完整公佈**，尤其是動物進所原因(來源)、年齡、是否結紮、個體行為觀察或健康狀況…等。甚至有縣市未即時公佈捕犬資訊，或者沒有公布照片，不利於民眾認養犬隻或尋找走失家犬；有時民眾需要另行下載每日公告再開啟，**使用不便**。雖然農委會後來成立的「全國推廣動物認領養平台」，無法確定此平台公佈與是否為各縣市全部的捕捉量，公佈項目也較精簡，**無法完整了解全國流浪犬捕捉資訊**。

        因此，我們希望**藉助各位的力量(如下「徵求協作者」中項目)建構一個平台，統整各縣市收容所的動物捕捉公告資訊**，以**有意義的方式整理及以「圖像」呈現**，並提供**互動式資料庫**以及**討論區**；使用者可以在平台上選擇自己需要資訊再匯出，也能在討論區發表自己的觀察與想法，**促使政府的資訊系統能更趨近於民眾的需求**。

       透過公立收容所內動物來源之分析，例如：來自民眾棄養、繁殖業者棄養或生於街頭的比例，公民團體、媒體與關心動物福利的民眾都可**檢視政府資源使用是否投入有效的政策**。這個平台也可以用於檢視犬隻絕育與晶片施打、動物救援等政策之成效。透過資訊以及政策之比對，可以進一步提出政策的具體調整方向。

        另外，這個平台也能檢視動物從進所到離開，整個過程的**收容品質與動物福利**，以及檢視公立收容所於提升送養比例之努力與成效，並進一步提出改善方向。

 【表】

| 計畫名稱 | 研究期間 | 研究經費(千元) |
| --- | --- | --- |
| 公立動物收容所資訊管理應用系統之建立 | 9303~9312 | 700 |
| 公立動物收容所資訊管理應用系統之建立 | 9403~9412 | 2607 |
| 公立動物收容所資訊管理應用系統之建立 | 9503~9512 | 3710 |
| 公立動物收容所資訊管理應用系統與犬貓進出離島地區追蹤檢疫系統之建立 | 9601~9612 | 5850 |
| 整合建置全國推廣動物認領養平台 | 10203~10212 | 1400 |
| 整合建置全國推廣動物認領養平台 | 10301~10312 | 1020 |
|  |  | 合計  
15287千元 |
| [https://www.grb.gov.tw](資料來源：政府研究資訊系統GRB https://www.grb.gov.tw) |  |  |

**發起人/拋磚人**：
EAST([社團法人台灣動物社會研究會](http://www.east.org.tw/))

## 平台初步設計(尚待討論)

**1\. 提供統整資料(首頁)：**
以台灣地圖為基底，以「點」呈現下列資訊在各縣市之密度，以不同顏色的點代表不同項目，例如不同來源以不同顏色的點標示。
圖表項目如下：
- 各縣市收容隻數以及認養、安樂死、不明原因死亡比例：
- 各縣市收容動物來源
- 各縣市收容動物年齡分布
- 各縣市收容動物結紮比例
- 各縣市收容動物性別分布
- 各縣市收容動物品種分布
- 各縣市收容所棄養原因分布
- 各縣市收容所經費與動物數量比較
- 對照此平台統計數據與農委會「動物保護資訊網」公佈「全國公立收容所收容處理情形統計表」 (兩張圖，對照點多寡)

附帶功能：
- 每個圖表項目加註說明，幫助使用者了解圖像意義。
- 點擊某項目地圖上的某一縣市，可以顯示該縣市該項目的長時間圖表，例如點擊「認養、安樂死、不明原因死亡比例」圖的「台中市」，則顯示台中市認養安樂、不明原因死亡比例一年以來的圖表，並標注零安樂死政策起始時間。
- 標註出不合常理的資訊(eg. 幼犬都有結紮、救援比例高的離奇)，並開放使用者對訊息貼標籤表示態度(eg. 懷疑、很棒、誇張, etc.)

**2\. 資料庫：**
將收集到的資料建置為資料庫，供使用者調閱，可以自行選擇需要的資料並於此平台上做出簡易圖表或統計，或得到原始資料。

附帶功能：
資料配合當時政策附註，例如標注台南開始執行TNVR、新北市開始推動陪伴犬政策...等時間點，有助於民眾理解收容資料與政策間的關聯性。

**3\. 公開討論區**
使用者可以於此表達、討論相關議題想法，或者反映自己所觀察到的奇怪的現象等(主要是希望民眾也可以幫忙debug收容所公布資訊有沒有可疑的地方。ex: 公布數量與實際收容數量不符、未註明動物健康情況、動物在所內大量死亡...等)。

**4.   延伸閱讀連結**
希望可以將使用本平台資料庫的文章、報告等，自動彙整為超連結列表。


**5.** **預定使用者**
公民團體、媒體與關心動物福利的民眾

2015/6/13 討論架構
> 14th大松的時候討論的筆記，不完整的部分請沒有人幫忙補充
> [name=Jimmy K]

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_b8d0fbd59f11cd11157018e6f69c2292)
## 如何參與協作?

有意願共同協作者，請於下**「徵求協作者」**項目下留ID，或直接聯繫eastfree@east.org.tw

## 徵求協作者

分工與成員
- [ ] NeedsDesigner: 需要介面設計
- [ ] NeedsData: 需要資料（擷取、清理）
- [x] NeedsTech: 需要技術支援（程式、架站 etc)
- [ ] NeedsProcess: 需要幫忙設計作業流程
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

網頁版型參考：[http://www.kyoto-u.ac.jp/explore/data/](http://www.kyoto-u.ac.jp/explore/data/)

## 成果展示（規劃文件、雛形/草稿、原型/初稿、正式發佈/完稿）


