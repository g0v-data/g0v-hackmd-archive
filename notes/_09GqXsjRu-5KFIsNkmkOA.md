---
title: "議員投票指南"
tags: hackpad
---

# 議員投票指南

> [點此觀看原始內容](https://g0v.hackpad.tw/KjfdRZ08FZ3)

[立委投票指南](http://vote.ly.g0v.tw/) 議會版
## 各縣市議會專案

[議員投票指南－架站流程](https://g0v.hackpad.tw/uGplqkYholX)
**台北市**
    - [https://github.com/g0v/councilor-voter-guide](https://github.com/g0v/councilor-voter-guide)
    - 6/16 [會議記錄](https://github.com/thewayiam/councilor-voter-guide/tree/master/meeting_minutes/taipei)  [crawler](https://github.com/g0v/councilor-voter-guide/blob/master/crawler/taipei/spiders/meeting_minutes_spider.py) done
    - 6/18 [議員資料](https://github.com/thewayiam/councilor-voter-guide/blob/master/data/pretty_format/taipei_councilor-11.json)  [crawler](https://github.com/g0v/councilor-voter-guide/blob/master/crawler/taipei/spiders/councilor_spider.py) done
    - 6/19 議員資料 [parser](https://github.com/g0v/councilor-voter-guide/blob/master/parser/councilors/councilors.py) done(json to db)
    - 6/20 merge 台南市議員資料 done
    - 6/22 議會大會出缺席紀錄 done
    - 6/23 [網站](http://councils.g0v.tw/)上線
    - 6/25 [議案crawler](https://github.com/g0v/councilor-voter-guide/blob/master/crawler/taipei/spiders/bills_spider.py) half way
    - 6/28 [議案](https://github.com/g0v/councilor-voter-guide/blob/master/data/pretty_format/taipei/bills-11.json)  [crawler](https://github.com/g0v/councilor-voter-guide/blob/master/crawler/taipei/spiders/bills_spider.py) done, 議案 [parser](https://github.com/g0v/councilor-voter-guide/blob/master/parser/bills/bills.py) (json to db) done
    - 6/29 [議員依提出議案數排序](http://councils.g0v.tw/councilors/bills/%E8%87%BA%E5%8C%97%E5%B8%82/11/) ( [程式](https://github.com/g0v/councilor-voter-guide/commit/149d43f76c32cbec84d0063e27cf49a878b6d207) ) ；[議員個人提出議案](http://councils.g0v.tw/councilors/biller/%E8%B3%B4%E7%B4%A0%E5%A6%82_1964-03-23/11/)、[依選區分組](http://councils.g0v.tw/councilors/countys/%E8%87%BA%E5%8C%97%E5%B8%82/11/) ( [程式](https://github.com/g0v/councilor-voter-guide/commit/acf36f4418cdb7d9f1e90d18f38125d7868f43cc) )
    - 7/4 [議案檢索](http://councils.g0v.tw/bills/%E8%87%BA%E5%8C%97%E5%B8%82/normal/)、個別議案頁面 ( [程式](https://github.com/g0v/councilor-voter-guide/commit/83dbf8fb48e5bee4a7c437a6bc579454e945f7bb) )
    - 7/6 [個人議案的共同提案人政黨分布圖](http://councils.g0v.tw/councilors/biller/%E8%B3%B4%E7%B4%A0%E5%A6%82_1964-03-23/11/)
    - 7/8 加入1-11屆議員，[離職議員名單](http://councils.g0v.tw/)
    - ˙7/9 表決parser
    - 7/10 表決資料呈現：[脫黨投票](http://councils.g0v.tw/councilors/conscience_vote/%E8%87%BA%E5%8C%97%E5%B8%82/11/)、[投票缺席](http://councils.g0v.tw/councilors/not_voting/%E8%87%BA%E5%8C%97%E5%B8%82/11/)、[表決總覽](http://councils.g0v.tw/councilors/not_voting/%E8%87%BA%E5%8C%97%E5%B8%82/11/)、[個人表決紀錄](http://councils.g0v.tw/councilors/voter/%E9%8D%BE%E5%B0%8F%E5%B9%B3_1962-08-27/11/)
    - 9/10 [候選人專頁](http://councils.g0v.tw/candidates/2014/%E8%87%BA%E5%8C%97%E5%B8%82/)

**新北市**
    - 會議記錄未公佈出缺席紀錄，只寫詳見簽到簿，WTF，[範例](http://www.ntp.gov.tw/UpFile/ProceedingsFile/%E6%96%B0%E5%8C%97%E5%B8%82%E8%AD%B0%E6%9C%83%E7%AC%AC1%E5%B1%86%E7%AC%AC1%E6%AC%A1%E8%87%A8%E6%99%82%E6%9C%83%E3%80%81%E7%AC%AC1%E6%AC%A1%E5%AE%9A%E6%9C%9F%E6%9C%83%E3%80%81%E7%AC%AC2%E6%AC%A1%E8%87%A8%E6%99%82%E6%9C%83.pdf)
        新北市議會的簽到資料放在摘要紀錄裡面而不是會議記錄喔
> 哦哦！感謝，在[議事錄日程表](http://www.ntp.gov.tw/content/Proceedings/P2013_1/Schedule_1.htm)的摘要紀錄中。[PDF呈現的會議](http://www.ntp.gov.tw/content/information/information04.aspx)大部分都還是寫詳見簽到簿，例：新北市議會第1屆成立大會 (PDF檔)、新北市議會第1屆第1次臨時會、第1次定期會、第2次臨時會 (PDF檔)、新北市議會第1屆第3次臨時會、第2次定期會、第4、5次臨時會 (PDF檔)，不知有沒有其他資料來源可參考？
> [name=johnny]

        看來簽到簿是沒有掃瞄放上網路，只有html那邊有整理上去
> 瞭解，另外請問，html部分發現有 "議次" 的摘要才有出席名單，其他議次空白的還是寫詳見簽到簿，[例](http://www.ntp.gov.tw/content/Proceedings/P2014_2/Schedule_4.htm)，請問這是某種議事規則嗎？還是可以說有議次的才算是全體議會，議次空白的是分組委員會會議？
> [name=johnny]

> 我個人覺得....那是不同人紀錄的緣故 似乎是只有一個記錄的情況下就會用詳見簽到簿帶過
> [name=Jimmy L]

> 上線囉！[新北市](http://councils.g0v.tw/candidates/2014/%E6%96%B0%E5%8C%97%E5%B8%82/)，有特別標註來源資料不完整
> [name=johnny]


**桃園市**
        ~想幫忙做桃園市這個區塊的整哩，不知道該如何開始，跪求老鳥帶領。~
        ~所以桃園縣的已完成了嗎？我也願意幫忙做桃園縣市的。~
        已經上線囉 [http://councils.g0v.tw/candidates/2014/%E6%A1%83%E5%9C%92%E5%B8%82/](http://councils.g0v.tw/candidates/2014/%E6%A1%83%E5%9C%92%E5%B8%82/)
> 抱歉晚回覆了，桃園目前已有桃園縣現任議員的基本資訊（[爬蟲](https://github.com/g0v/councilor-voter-guide/blob/master/crawler/tycc/tycc/spiders/councilors.py)），看您要仿造桃園縣做桃園市，或是抓[桃園縣歷屆議員](http://www.tycc.gov.tw/page.aspx?wtp=1&wnd=319)資料，都是抓資料不錯的起頭。如果對工程建議款有興趣，可看看桃園縣是有沒有[類似的資料](https://g0v.hackpad.tw/jjNta3y2alH#:h=資料)。有時間的話還是[上來 irc](http://hack.g0v.tw/irc)找大家聊天討論吧 :)
> [name=johnny]

> 大家好，感謝桃園市已經有人在弄了，小弟想幫忙補齊桃園市的資料，不知道該從何處開幫忙。
> [name=Tim H]

> Tim大大的話，挑戰出缺席吧！大致流程：下載[各會議的議事錄](http://www.tycc.gov.tw/page.aspx?wtp=1&wnd=217) （pdf檔）-> 轉txt  ->  抓取 "出席："、"請假：" 缺席："裡的議員，建出缺席紀錄，[新北市範例](https://github.com/g0v/councilor-voter-guide/blob/master/parser/votes/ntcc/votes.py)。會議記錄也可找裡面有沒有記名表決，可能的關鍵字：贊成、反對、棄權、記明表決、表決名單...等等，可先手動搜尋看看脈絡，在寫程式抓取，[台北市範例](https://github.com/g0v/councilor-voter-guide/blob/master/parser/votes/tcc/votes.py#L39-L52)，個人覺得很笨很麻煩的方法，但目前也不知怎麼改進。
> [name=johnny]

> 感謝，但桃園市好像連連議事紀錄都找不到的樣子
> [name=Tim H]

> [各會議的議事錄](http://www.tycc.gov.tw/page.aspx?wtp=1&wnd=217)
> [name=johnny]

> 桃園目前應該無法做出缺席，但是應該可以補上議案資料。
> [name=Tim H]

> 補上 [issue](https://github.com/g0v/councilor-voter-guide/issues/60)
> [name=Tim H]

**新竹市**
        議程表內容都在doc檔裡面，不知道該怎麼辦，所以現在bills傳回的item都還沒有欄位  [http://www.hsinchu-cc.gov.tw/Agenda/Agenda.htm](http://www.hsinchu-cc.gov.tw/Agenda/Agenda.htm)
> 新竹有點悲劇，看起來沒什麼可以做的
> [name=johnny]

**新竹縣**
> 議員資料已上線，還可找找看議案、出缺席、表決
> [name=johnny]

**台中市**
    - 找不到有表決過的紀錄，有沒有人有認識的可以確認看看。[會議紀錄](https://www.dropbox.com/s/l6a6i9cmpc8nzmo/meeting-2010.pdf?dl=0)
    - 9/16 初版上線（包含候選人）[http://councils.g0v.tw/](http://councils.g0v.tw/)
**南投市**
    - 議員基本資料 done
> _感謝[miheille](https://www.irccloud.com/#!/irc.freenode.net:6667/miheille)  [已手動key完本屆ＸＤ](https://docs.google.com/spreadsheets/d/1akk-svh7rVGC7m2OVrqCwikPzFuVwzKgpYo_FETAmK8/edit?pli=1#gid=0)比寫程式快（誤）(11/13) 
> [name=Thea W]

    - 議事提案爬蟲done:
> 完工了真是太感人～QQ! (11/15)
> [name=Thea W]

    - 11/13初版上線
**彰化縣**
    - 議員基本資料 done: 缺黨籍
    - 議案done
**嘉義縣**
    - 議員基本資料 done~: 缺黨籍和照片~
    - 黨籍與照片 done
    - ~議案處理中 ~   seadog007 DennyHuang pcchou 已經先處理完畢了
**雲林縣**
    - 議員基本資料 done: web format 不是很統一. 有些議員資料缺乏
    - [議案pdf](http://www.ylcc.gov.tw/index.php?parent=201205210000408&keyword=&page=&office=%E8%AD%B0%E4%BA%8B%E7%B5%84&inner=dload&menu=201008030000001)慢慢手動copy中...
> （應該沒人做吧！）(11/18)
> [name=Thea W]

> 做好了 ^O^
> [name=Kuanhung C]

    - 使用工具: [Tabula-extractor](https://github.com/tabulapdf/tabula-extractor) 可以將 PDF 表格轉存成 CSV
        - 議員議案 pdf 定期會 9 筆, 臨時會 14 筆全部轉換成 CSV 並彙總並彙總成 bills.json 完成
        - 議員提案 pdf crawler 撰寫完成, 可搭配 pdf2json 自動會總成 bills.josn
    - [會議記錄](http://www.ylcc.gov.tw/index.php?parent=&keyword=&page=&inner=dload&menu=201008030000001)裡的議員報到有出缺席紀錄
**嘉義市**
    - 議員基本資料 done
    - 議案done
**台南市**
    - [https://github.com/kiang/tncc](https://github.com/kiang/tncc)
    - 6/7 [議員基本資料](https://github.com/kiang/tncc/blob/master/tnccp.json) done
    - 6/17 [議會議案記錄](https://github.com/kiang/tncc/tree/master/motions) crawler/parser done
    - 6/21 [以 cakephp 實做一個議員資訊網站](https://github.com/kiang/parliamentary)
    - 6/22 [初步成果對外開放了](http://k.olc.tw/tncc/)
    - 會議記錄有公佈出缺席紀錄，但是被塞在 pdf 中，並且[用相對難處理的格式](http://k.olc.tw/2014/07/%E5%8F%B0%E5%8D%97%E5%B8%82%E8%AD%B0%E6%9C%83%E5%87%BA%E5%B8%AD%E7%8B%80%E6%B3%81%E7%B5%B1%E8%A8%88/)
    - 沒有個別議案的表決記錄
**高雄市**
    高雄上線了 [http://councils.g0v.tw/](http://councils.g0v.tw/)
> 已有大神爬出JSON，檔案我就刪掉了。　ＸＤ
> [name=Thor L]

> ~不會爬網頁資料，不過看看html的原始碼＋取代整理了一份倒是有辦法。但是不知道為什麼在google driver上看都是亂碼，下載後的.csv應該是正常的。看有沒有爬網頁資料的高手或者等我慢慢練到會的那一天。（遠目）~
> [name=Thor L]

> 已爬高雄議會官網 =\> [JSON檔](https://github.com/g0v/councilor-voter-guide/blob/master/data/pretty_format/kcc/councilors_terms.json)，[爬蟲](https://github.com/g0v/councilor-voter-guide/blob/master/crawler/kcc/kcc/spiders/councilors_terms.py)
> [name=johnny]

    - 看起來只有合併後第一屆(沒有的話, 看能不能跟議會要)
    - ~先訂出最後要呈現的內容, 然後再整理出坑~
        - ~可以參考北市:~ [~http://councils.g0v.tw/bills/%E8%87%BA%E5%8C%97%E5%B8%82/normal/~](http://councils.g0v.tw/bills/%E8%87%BA%E5%8C%97%E5%B8%82/normal/)
    - ~目前期望有的最終資料:~
        - ~議員~
            - [x] ~基本資料~
            - [x] ~政見~
            - [x] ~議事相關~
                - [x] ~提案~
                - [x] ~參與表決(還沒找到source)~
> source在會議紀錄中，[會議記錄全文](https://github.com/g0v/councilor-voter-guide/blob/master/data/kcc/meeting_minutes-2010.txt)已合併
> [name=johnny]

                - [x] ~出席(還沒找到source)~
> source在會議紀錄中，[會議記錄全文](https://github.com/g0v/councilor-voter-guide/blob/master/data/kcc/meeting_minutes-2010.txt)已合併
> [name=johnny]

        - 議案
    - 影音也可以parse下來, 放上youtube, 方便分享
    - 目前有的source data:
        - 議員個人資料(含新聞, 議事參與紀錄):[http://www.kcc.gov.tw/PeriodMembers/Search.aspx](http://www.kcc.gov.tw/PeriodMembers/Search.aspx)
            [JSON檔](https://github.com/g0v/councilor-voter-guide/blob/master/data/pretty_format/kcc/councilors_terms.json)
> 好像只有 64 位議員資料
> [name=Rick Y]

> [http://220.132.233.59:5984/kaohsiung\_city\_council/\_design/councilor/\_view/info](http://220.132.233.59:5984/kaohsiung_city_council/_design/councilor/_view/info)
> [name=Rick Y]

> 可在 URL 後面加上 ?key="名稱" 進行查尋
> [name=Rick Y]

> ~好像沒有爬議事參與紀錄的部分 是打算從議案記錄對過來嗎?~
> [name=King A]

> ~議案紀錄不含投票名單, 只有議員提案~
> [name=King A]

        - 記錄(pdf):[http://cissearch.kcc.gov.tw/System/MeetingRecord/Default.aspx](http://cissearch.kcc.gov.tw/System/MeetingRecord/Default.aspx)
> 轉成文字了： [https://github.com/kiang/kcc/tree/master/MeetingRecord](https://github.com/kiang/kcc/tree/master/MeetingRecord)
> [name=Finjon K]

> 沒有簽到資料？ 這樣好像無法看出席狀況
> [name=Mikimoto C]

> ~會議記錄寫（如簽到簿）....跟新北市一樣~
> [name=johnny]

> 會議記錄有列請假人員，有到的需要自己處理一下
> [name=johnny]

        - 議案： [http://cissearch.kcc.gov.tw/System/Proposal/Default.aspx](http://cissearch.kcc.gov.tw/System/Proposal/Default.aspx)
> 卡關的爬蟲： [https://github.com/kiang/kcc/blob/master/proposal.php](https://github.com/kiang/kcc/blob/master/proposal.php)
> [name=Finjon K]

> [卡關的爬蟲(scrapy)](https://github.com/g0v/councilor-voter-guide/blob/master/crawler/kcc/kcc/spiders/bills.py)：有bug，不知為啥少爬很多
> [name=johnny]

> 主機好像有擋爬蟲吧，很討厭 XD
> [name=Finjon K]

> 成功了，[JSON檔](https://github.com/g0v/councilor-voter-guide/blob/master/data/pretty_format/kcc/bills.json)，這是2010~現在的所有議案
> [name=johnny]

        - 議員通訊錄： [http://cand.moi.gov.tw/of/index.jsp](http://cand.moi.gov.tw/of/index.jsp)
> 可以參考 public function moi() / [https://github.com/kiang/elections/blob/master/Console/Command/CandidateShell.php](https://github.com/kiang/elections/blob/master/Console/Command/CandidateShell.php)
> [name=Finjon K]

> [JSON檔](https://github.com/g0v/councilor-voter-guide/blob/master/data/pretty_format/kcc/councilors_terms.json)已有包含通訊資料，詳見contact_details
> [name=johnny]

> [http://220.132.233.59:5984/kaohsiung\_city\_council/\_design/councilor/\_view/contact_details](http://220.132.233.59:5984/kaohsiung_city_council/_design/councilor/_view/contact_details)  key = 名稱, value = { /* 通訊資料 */ }
> [name=Rick Y]

> 查詢範例: [http://220.132.233.59:5984/kaohsiung\_city\_council/\_design/councilor/\_view/contact_details?key=%22%E](http://220.132.233.59:5984/kaohsiung_city_council/_design/councilor/_view/contact_details?key=%22%E5%90%B3%E7%9B%8A%E6%94%BF%22)[5%90%B3%E7%9B%8A%E6%94%B](http://220.132.233.59:5984/kaohsiung_city_council/_design/councilor/_view/contact_details?key=%22%E5%90%B3%E7%9B%8A%E6%94%BF%22)[F%22](http://220.132.233.59:5984/kaohsiung_city_council/_design/councilor/_view/contact_details?key=%22%E5%90%B3%E7%9B%8A%E6%94%BF%22)
> [name=Rick Y]

> ............?key="名稱"，注意雙引號！
> [name=Rick Y]

        - **CouchDB**: [http://](http://220.132.233.59:5984/_utils/)[220.132.233.59:5984](http://220.132.233.59:5984/_utils/)[/_utils/](http://220.132.233.59:5984/_utils/)
> 感謝 Lorex 大德提供此 server，功德無量!!
> [name=Rick Y]

> admin: KSDG
> [name=Rick Y]

> password: KSDG
> [name=Rick Y]

> 未來可將相關之 JSON 資料存放於此，以利前端作業。
> [name=Rick Y]

> 感謝各位大神的協助，如果還有人需要使用 Server，歡迎與我聯絡，我這邊還有一些硬體資源可以提供 :))
> [name=楊天罡]


**花蓮縣**
        不曉得有沒有人做了@@? ，也不知道來不來的及XD 反正就試試看口貝!
> 看起來是沒有ＸＤ 做吧！！ 南投製作ing... [參考一下這邊吧](https://github.com/g0v/councilor-voter-guide/tree/master/crawler)
> [name=Thea W]

> s:嗚嗚，我覺得我好像進入叢林惹orz  ...趕快跟英文裝熟先www
> [name=許浩然]

> 還是霧煞煞= =...
> [name=許浩然]

> 我先去整理資料好了，再看看有沒有會程式的來支援再說~"~
> [name=許浩然]

> 歡迎週六來參加現場coding活動XD [http://www.meetup.com/Taipei-py/events/218592523/](http://www.meetup.com/Taipei-py/events/218592523/)
> [name=Thea W]

> 現任議員基本資料的 crawler done
> [name=Swind O]

> [已手動key完本屆ＸＤ](https://docs.google.com/spreadsheets/d/1akk-svh7rVGC7m2OVrqCwikPzFuVwzKgpYo_FETAmK8/edit?pli=1#gid=0)  議會資料 crawler done
> [name=Swind O]

> 但是目前找不到會議記錄，無法計算出缺席
> [name=Swind O]

> 議員和議案已上線，swind ++
> [name=johnny]

**金門縣**
    金門縣有人做嗎？我先試著整理一下資料~

**台東縣**
    目前應該沒有人做台東縣吧？！我就先來整理
    [http://www.taitungcc.gov.tw/ourteam/01ourteam.html](http://www.taitungcc.gov.tw/ourteam/01ourteam.html) (台東縣議會現任議員資料)
- [x] 現任議員基本資料 (完成) (11/18)
- [ ] 議案
> 台東可以幫忙整理
> [name=Kobe Y]

> KOBE有找到議案嗎？
> [name=Wei-Chih]

> 議員提案 :[http://www.taitungcc.gov.tw/motion/motion_main.asp](http://www.taitungcc.gov.tw/motion/motion_main.asp)
> [name=Kobe Y]

> 縣府提案：[http://www.taitungcc.gov.tw/law/law_main.asp](http://www.taitungcc.gov.tw/law/law_main.asp)
> [name=Kobe Y]

> 我打算開始做爬蟲,會先爬現任議員資料 （資料夾名稱 ttcc ）
> [name=Kobe Y]

> 現任議員的crawler完成 (11/18)
> [name=Wei-Chih]


**屏東縣**
    - 議員基本資料done

**澎湖縣**
> [http://www.phcouncil.gov.tw/](http://www.phcouncil.gov.tw/)
> [name=Li-Han C]

> 好像根本連不進去 ...
> [name=Li-Han C]

**連江縣**
    [連江縣議會資料](http://www.mtcc.gov.tw/cu_representative.htm)
    - 議員基本資料done
    - 議案資料研究中(11/17)

### 基隆市

    好像目前還沒有做基隆的，目前製作爬蟲中...github 還不會用，還有很多東西要學QQ，11/15要來大進補了
    [基隆市議會網站](http://www.kmc.gov.tw/)
- [x] 現任議員資料(DONE)
> 2014/11/15 現行議員基本資料爬蟲初步完成
> [name=Rz C]

> ~尚缺性別欄位：也許可用~[~開放資料~](http://cand.moi.gov.tw/of/ap/cand_json.jsp?electkind=0200000)~進行交叉比對，放入議員性別 =\> DONE~
> [name=Rz C]

> 本屆應有 32 位, 但市議會網站上只有列 31 位
> [name=Rz C]

> 比對 wiki 後發現 仁愛區 中國國民黨 曾水源 (已過世) => [wiki](http://www.wikiwand.com/zh-tw/%E7%AC%AC17%E5%B1%86%E5%9F%BA%E9%9A%86%E5%B8%82%E8%AD%B0%E5%93%A1%E5%88%97%E8%A1%A8)
> [name=Rz C]

> 2014/11/15 市議會網站上沒有提供歷屆議員資訊
> [name=Rz C]

> 2014/11/15 市議會網站上疑似議案資料網頁，僅列案由、時間、議決 (沒有提案人) => [link](http://www.kmc.gov.tw/KMCII/discuss.aspx)
> [name=Rz C]

> 再詢問看看市議員...了解網站上資料的公開程度
> [name=Rz C]

> 2014/11/15 市議會網站上未找到會議相關記錄 ...
> [name=Rz C]

> [縣市議會議事透明度評分表](http://www.ccw.org.tw/p/19784?) 中基隆市為 0 分 orz
> [name=Rz C]

> 2014/11/25 你可看一下[地方議會議事錄檢索系統 \- 基隆市議會](http://kmc.digital.tpa.gov.tw/)。
> [name=Yau-Hsien H]

> 2014/11/26 YAU-HSIEN 太讚了, 再來研究可以如何處理
> [name=Rz C]

> 請參考 mcc 的 crawler （2014/11/26 目前正在 pull request ）
> [name=Yau-Hsien H]

> 要先 ?act=GuestLogin 才能拿 ?act=opendata ，離開時可以 ?act=logout
> [name=Yau-Hsien H]

> 而我想知道是否可以從議事錄中整理出議案，能教一下嗎？
> [name=Yau-Hsien H]


### 苗栗縣

    來做點基本資料給可憐的苗栗
- [x] 現任議員基本資料
- [x] 議事錄
> 2014/11/21 嗨，我有意願ㄧ起來做苗栗。
> [name=Yau-Hsien H]

> 2014/11/22 發現「[地方議會議事錄檢索系統](http://mcc.digital.tpa.gov.tw)」，有 open-data ，但沒有最新資料，只~有次晚近資料（到2013年底）~，可以做做看。
> [name=Yau-Hsien H]

> 2014/11/24 議事錄 crawler 完成。
> [name=Yau-Hsien H]

> ~想問：議事錄中的一些內容，可以列為議案嗎？~ （後補）已經由[架站流程](https://g0v.hackpad.tw/uGplqkYholX)理解。
> [name=Yau-Hsien H]


### 金門縣

    [門打開，阮顧厝](http://www.kmcc.gov.tw/men/)

## 參考資料：

- 議員公開資料
    - [縣市議員](http://data.gov.tw/node/7054)
    - [直轄市議員](http://data.gov.tw/node/7055)
- 議事資料
    - [地方議會議事資料數位平台](http://digital.tpa.gov.tw)：內容為掃描檔案，以掃瞄影像、描述資料、及頁況回報等方式維護資料。有 Open Data 下載點的提供。
- [各縣市議會議事透明狀況](https://www.dropbox.com/s/0r60j1x9ggw6ph7/%E5%90%84%E7%B8%A3%E5%B8%82%E8%AD%B0%E6%9C%83%E8%AD%B0%E4%BA%8B%E9%80%8F%E6%98%8E%E7%8B%80%E6%B3%81.xlsx)
    - [【會後新聞稿】縣市議會透明度慘 1兆預算陷黑箱](http://www.ccw.org.tw/p/19783?)
    - [【聲明稿】針對部份縣市議會質疑透明度調查之聲明](http://www.ccw.org.tw/p/19784?)
- 各地監督團體
    - [大台中市政監督聯盟](https://zh-tw.facebook.com/ngotaichung)
        - 是地方監督議會動能較強的團體，連續兩年有辦[烏龍預算票選](https://www.facebook.com/ngotaichung/app_126231547426086)。[資料](http://civicwatchtaichung.blogspot.tw/)。「[台中市十大烏龍預算網路票選活動！TOP 10！](https://www.facebook.com/events/254520378008666/)」、「[好議會](https://www.facebook.com/media/set/?set=a.219613264865902.1073741825.120312334795996&type=1%20https://pinvents.com/event/207082242806601/)才有好市政Ｘ預算研習活動」。
    - 宜督盟目前有辦理議員評鑑、推動議會透明化；
    - 高督盟除了議員評鑑、推動議會透明化外，也在推動「議員分配款」的改革，並於七月時向監察院檢舉。
    - [台南市政監督聯盟](https://www.facebook.com/groups/tainangogo/)
        - 以監督「不當預算」為主，關注包括「關注議會議員領取出席費浮濫」、「未執行預算」等問題。

## Idea pool

各縣市需分開下手，以桃園縣議會為例[http://www.tycc.gov.tw/page.aspx?wtp=1&wnd=217](http://www.tycc.gov.tw/page.aspx?wtp=1&wnd=217)，可先研讀議事錄，觀察有無具指標性的資料適合抓取，例如出缺席、質詢、預算

突然想到個問題   如果是新科候選人
那不就空白   沒有資料可以去參考????
還是能多設個區塊   開放給人提供資料
或是  直接能KEY IN 與其有關之資料
(像原本是里長 或 社團領導人 之類的
> 由公開欄位提供資料輸入，會引起資料品質的爭議。像「[選舉黃頁收到了第一個妨礙名譽的指控](http://k.olc.tw/2014/11/選舉黃頁收到了第一個妨礙名譽的指控/)」就是一個資料發行方所面對的問題。
> [name=Yau-Hsien H]

=\> 以立委投票指南為例，有個想法是請候選人來平台"模擬"投票和提案，他也可以解釋為何投這樣的票提這樣的案，現任的立委當然就請他對過往的行為作解釋說明，另外還想設計讓候選人選前就公開政治獻金和財產申報資訊(可選非必填)，也可以設計一些基本的小問題，例：座右銘、是否有兒女定居國外...，另外想搭配群眾募資平台，幫助素人參選。

需要熟悉議會流程的人，檢視「資料開放程度」能夠更精確。或是指出哪些資料/會議對民眾來說最關鍵。



Yuren: 我覺得也需要照選區來分。像我是文山區的選民，我第一個就想知道文山區的出席紀錄，作為年底投票的依據。
這個有資料，差UI就可以顯示了
OK了，[依台北市選區分組](http://councils.g0v.tw/councilors/counties/%E8%87%BA%E5%8C%97%E5%B8%82/) <-這個link目前失效
Stardog: 現在呈現是各候選人分開, 但是分開看沒感覺, 一起看才知道高下.  例如出席率, 提案數等
是否可以再多一個頁面來呈現overall 的簡單比較圖?
*連結已更正，overall是比如說整個台北市在同一個頁面同時顯示上述這些指標嗎？
*咦? 我連 [http://councils.g0v.tw/councilors/countys/%E8%87%BA%E5%8C%97%E5%B8%82/11/](http://councils.g0v.tw/councilors/countys/%E8%87%BA%E5%8C%97%E5%B8%82/11/) 還是失敗哩
*直接改連結居然無效，已修正
*關於比較圖, 是想要跟平均數字比較, 這樣選民會對這樣的出席率與提案數較有感覺. 可以跟新北市全區的平均數字或是單區的平均數字比較.
*這個好，已開 issue

網站本身可以先把 Open Data 這條主線維護好，也就是將 crawling-parsing 產生的原始檔（JSON檔案）用 API 端點放出來，這樣子將來別處要做什麼應用都比較好做，因為你已經先辛苦找過資料而且 parse 過一次了。而且也可以把一些 overall 的數字算好，放給 API 提供。在呈現方面，網站也可以使用自己的 open-data API 。
*目前已有API，是瀏覽式的

可有一張以選區為單頁的候選人清單，提供各候選人QR碼連結到個人專頁，方便集合列印成紙本，或以大圖輸出貼在手舉牌上，方便在選舉前在公開場合、擺攤處，讓路人掃描查詢。

能做外文版本嗎？讓新住民可以閱讀。

[議會透明度](https://docs.google.com/spreadsheets/d/1JB2zLj8ZZqvnv31NvfwlR7HO_b99AtTjO_Gj1qMilL4/edit#gid=0) 我們要把各議會缺失的項目都整理出來, 並且公布. 還要有熱心人士持續去push議會把缺失項目補上. 力求各議會在新會期能把缺失內容補上.

請問有小夥伴們要一起來 trace 這個專案的程式碼嗎？
建議：我建議可以另外開個 Trello 或 Asana，列出目前專案功能的優先開發順序。並且上面可以提供投票。這邊 hackpad 提供詳細討論和 idea pool，不過 Trello 可以清楚列出開發的進度。

## 疑問

- 為何一個議案收文和發文差距長達七年？[http://tccmis.tcc.gov.tw/OM/OM\_SearchDetail.asp?sys\_no=27261](http://tccmis.tcc.gov.tw/OM/OM_SearchDetail.asp?sys_no=27261)
> 前議員助理回答：要馬是寫錯，要馬就真的是拖很久  我想...應該是這個案子拖很久...因為台北市的市場用地是一個大問題...我猜想而已，因為市議會議事系統爛，這種事情都無法追蹤的～
> [name=Li-Ting H]

- 立院聽過很多助理說過第一提案人的概念，請問議會也有嗎?例如[這個議案](http://tccmis.tcc.gov.tw/OM/OM_SearchDetail.asp?sys_no=29804)
> 前議員助理回答：應該也是有，不過都沒人在管法規的 哈哈哈 而且也沒人在審法規～～～平常議會真得很少在審議案 排完質詢就差不多要散會了
> [name=Li-Ting H]

- 技術提問（Development Setup）
> 我把專案clone回來了，但我無法處理這問題
> [name=OtomeSound]

```txt
'Settings' object has no attribute 'ROOT_URLCONF'
```
> 想請問 [Tony Hsu](https://g0v.hackpad.tw/ep/profile/H3Xx19XGl8b)  怎麼啟動的？需要多點資訊
> [name=Tim H]

> 沒有問題的，只是clone的問題（clone下來的資料不完全）
> [name=OtomeSound]

    CSS Library使用問題
> 目前看到的是Bootstrap 2 + Semantic UI並用狀況，雖然不是不行，但Bootstrap 2有點舊了，有打算升級成Bootstrap 3嗎？
> [name=OtomeSound]

> 等選後有空吧XD 2 -> 3感覺改動不小
> [name=johnny]


> 請問若我想用類似介面做成一個縣市長對環保團體問卷的回復情形與內容  該從哪裡著手？
> [name=Xavier S]

> 聽起來是一個全新的專案，也許可以直接到g0v黑客松提案 :) 。黑客松資訊可[鎖定g0v FB](https://www.facebook.com/g0v.tw)
> [name=johnny]

- 可以提供政見跳票率的數值和明細嗎？例如原本把公宅當政見，當選後又檔公宅的。
> 也許可以先蒐集資料或提供合適的呈現方式？這類議題需要大量人工協助處理，除非有熱心的朋友願意主導特定議題資料的蒐集與整理，否則空有資訊系統也沒有意義
> [name=Finjon K]

- 請問爬蟲的目標網頁有變動會自動反映在資料上嗎？如果會的話大約多久更新一次呢？

Bug 回報
以 [https://councils.g0v.tw/suggestions/lists/新竹縣/?keyword=張鎮榮&or=協會,協進會,促進會,研習會,婦聯會,婦女會,體育會,同心會,農會,早起會,健身會,宗親會,功德會,商業會,長青會,民眾服務社,聯盟&page_size=50](https://councils.g0v.tw/suggestions/lists/新竹縣/?keyword=張鎮榮&or=協會,協進會,促進會,研習會,婦聯會,婦女會,體育會,同心會,農會,早起會,健身會,宗親會,功德會,商業會,長青會,民眾服務社,聯盟&page_size=50)  為例
第一頁顯示查詢結果998個搜尋結果，這是第1頁（共100頁）
選擇下方一頁顯示 50 筆結果後，會更新為 998個搜尋結果，這是第1頁（共20頁）
但是按下一頁後，就會跳回單頁顯示 10 筆資料

