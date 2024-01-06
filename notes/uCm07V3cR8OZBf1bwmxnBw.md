---
title: "9 月萌典松: moed6ct (含直播及文字轉播)"
tags: event,moedict,hackpad
---

# 9 月萌典松: moed6ct (含直播及文字轉播)

> [點此觀看原始內容](https://g0v.hackpad.tw/9-moed6ct)


時間：9/20 11am-9pm（歡迎遲到早退）
地點：[Bookshow.tw](http://bookshow.tw/traffic/)  基隆路一段 141 號 6 樓之 7（捷運市政府站步行三分鐘）
名額：30 人（[報名頁面](http://g0v-tw.kktix.cc/events/moedict-9-20)）
內容：比照[前五次萌典松](https://g0v.hackpad.tw/8-moed5ct) ，採「併松」模式舉行，歡迎 g0v 各大小專案加**萌**參加。
費用：採量力而捐、自由贊助方式。如有剩餘，捐給下次黑客松。
直播：[http://j.mp/livemoed6ct](http://j.mp/livemoed6ct)

流程：
- 11:30 專案、想法簡報介紹
- 12:00 自介、午餐、分組意見交流
- 13:30 十五分鐘短講
- 14:30 hack, eat, hack
- 17:00 第一次成果報告
- 17:30 hack, eat, hack
- 19:30 第二次成果報告

### 萌典相關開發項目


- 由使用者切換漢語拼音之外的注音方式，如通用拼音、威妥瑪拼音、注音二式等。
    - 這個已經初步完成，但音調標注方式要請教方家。
        - 調號同漢語拼音
    - 臺灣閩南語、客家語的拼音系統（POJ、通拼等）需要對照表。
- 思源黑體的自訂網頁字型服務（類似 [justfont](http://www.justfont.com)）。
    - 這是第一套開放源碼、符合教育部方體字規範（筆畫結構與楷書相同）的黑體字型，故事可參考葉平（思源黑的命名者，同時也是萌典專案發起人）的[科學人專欄](http://audreyt.org/newdict/noto-yalib.pdf)。
    - 雛形：[https://www.moedict.tw/SourceHanSansTW.ttf?subset=認得幾個字](https://www.moedict.tw/SourceHanSansTW.ttf?subset=認得幾個字)
        - 需要加上快取，以及其他粗細的選項。
        - 也許整合到萌典字圖？
- 增進楷書的機器辨識率。
    - 緣起是 Bullszip PDF driver 會保留 TTF 字型，但字碼會亂掉，需要與標楷體比對。
    - 公文辨識也很需要這個技術，例如近期的各縣市投開票所名單數位化專案。
- 徐老師客語典 [EUDC 自造字](https://github.com/audreyt/moedict-data-shaucan) 的 Unicode 萬國碼對應，這部份也考慮用群眾分散式處理。
    - 部件表：[https://github.com/audreyt/moedict-data-shaucan/blob/master/%E9%80%A0%E5%AD%97%E9%83%A8%E4%BB%B6%E8%A1%A8.csv](https://github.com/audreyt/moedict-data-shaucan/blob/master/%E9%80%A0%E5%AD%97%E9%83%A8%E4%BB%B6%E8%A1%A8.csv)
    - 歡迎幫忙在 [http://nccu.ksana.tw/kzy/](http://nccu.ksana.tw/kzy/)
        - 查詢之後填上 [https://ethercalc.org/shaucan](https://ethercalc.org/shaucan)
        - 使用 C 欄即可，A 欄的字型有缺時可在 [https://github.com/audreyt/moedict-data-shaucan/raw/master/EUDC.TTE](https://github.com/audreyt/moedict-data-shaucan/raw/master/EUDC.TTE) 檢視，或從 B 欄想像即可
        - 感謝 [Jackie Fei](https://g0v.hackpad.tw/ep/profile/A176x1ocBvN) 填了大部份!

### 短講


- [萌典考](https://g0v.hackpad.tw/9-moed6ct--2BAArXyPOlM) \- [caasi](https://g0v.hackpad.tw/ep/profile/n097KVBPoh0)
    列出萌典重要開發時刻，並和所解決的問題連結。
> 其實我的國文超爛
> [name=caasi H]

- [科哲露西](http://www.accupass.com/go/lucy)活動預告： [phi10sophy 籌備處](https://g0v.hackpad.tw/BNYMepSBzw9) 第一發，跨領域對談前導測試 \- nchild
- M project 下年度規劃 - a0kman
- [Taiwan Bar](https://www.facebook.com/taiwanbarstudio) using [AMARA](http://amara.org/en/) 號召字幕翻譯協作 \- DJ Hauer

## 併松

> 歡迎把想做的專案/計劃列在這裡！
> [name=Audrey T]


### 農域松

[超農域](https://hackfoldr.org/agriculture/)啊啊啊啊
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_7646675cdf4432bd4b7aeb00bcafa9bf)

### 陽光松

chewei> 預計討論 [GuanXi 親族關係+公司關係->政商透明化](https://g0v.hackpad.tw/GuanXi--5gygVb26WId)（[http://hackfoldr.org/gxv/](http://hackfoldr.org/gxv/)）
討論內容及 todos：[20140920 政商關係討論紀錄 @萌典松](https://g0v.hackpad.tw/byvCrtHhRML)

## 文播


pipi:來弄 summit
[Rhozan](https://g0v.hackpad.tw/ep/profile/v2FoVsCJSQ7): 除黴計劃
travis: 來學活動的內容和方式
哲瑋: 親族和公司關係專案，「總統的親戚」政商家族譜系
clkao: 村長來純路過，兩點松山的飛機，來**鬼混**一下，投票所數位化放到 OpenStreetMap 上面，同時可以增進圖資，有 OSM 的朋友可以幫忙上台介紹
ipa: 也是來弄 summit，g0v contributor 票今天截止，歡迎先貢獻後補票
yinfan: 氣候選戰，徵求前端工程師
dongbai: 跟著來幫忙
jackie: 之前做過漢字王的遊戲，形音意用遊戲來玩，想要找伙伴開發現有的雛形
a0kman: 超農域的內容，第二個大坑
momo: 來幫超農域的
tuiry: 來畫科哲露西之夜
simonpai: 超農域
?: 路過
miaoski: 在徵求會上下左右剪下貼上的阿美
yujun: 超農域
venev: 政商關係的 present（陳柔縉?），包括 g0v 的火力展示的 demo 準備，下午可能會來的 DJ hauer 有台灣 bar 的專案，看看史普影片是否可以協作跨語言的字幕。


專案報告：
- 11:50 [投開票所 Geocode](http://comap.clkao.org/comap)
- 12:00 氣候選戰 [Vote for Climate](https://g0v.hackpad.tw/4ac9ap7zhrn)
- 12:05 政商人物關係圖。cf.[邱文達](https://www.facebook.com/photo.php?fbid=728954573843624&set=a.162786293793791.40993.100001872656795&type=1&theater)，[中國老虎家族](http://datanews.caixin.com/2014/zhoushicailu/)，[新加坡華人銀行家族](http://thehearttruths.com/2014/09/10/singapores-straits-chinese-banking-families-%E6%96%B0%E5%8A%A0%E5%9D%A1%E6%B5%B7%E5%B3%A1%E5%8D%8E%E4%BA%BA%E9%93%B6%E8%A1%8C%E5%AE%B6%E6%97%8F/)
- 12:10 阿美語萌典
- 12:18 雲端華語自學系統
- 12:24 超農域

12:30 第二次自介
weiwei: 政大學生，新文藝論壇，受老師之託來瞭解萌典松
呂北: 國中特教老師
a-tsioh: 會做台語的輸入法和阿美詞典
莊銘彥: 去年的萌典松認識余伯泉老師，今天來弄通用拼音的部份
weihung: 好久沒有來了，要跟 nchild 等人討論科哲露西的對話
海綿: weihung  的朋友，沃草記者，今天被抓過來玩

venev 報告: 簽到表傳遞中
12:50 午餐 pizza 傳遞中

13:30  短講
caasi 列出萌典的重要開發時刻(萌典娘之後空了....很....久....)
a0kman 簡介 [g0v 全部拆掉改造王](https://g0v.hackpad.tw/rEzVnbqCZrz)

17:00 晚餐統計：20 人會留下來用餐
19:30 成果報告（待補）
21:00 以後
- au、Bobby Tung 聊電子書、數位出版標準格式、編輯經驗、工具與範例、萌典軍火庫
- 聽 a-tsioh 和 miaoski 聊語言、台語文學書、鄉土語言（而非母語）教學.....不知為何很喜感
    - miaoski: how do you say "E-mail", "CD-ROM", ......?
    - a-tsioh 列示不同的法語講法後 -> 魁北克說法比較 classic，~其實挖洗魁北克人（誤）~

## 照片

授權預設 CC by 4.0，張貼時在此簽名確認 ok: Bropheus, chewei
> [che wei liu](https://g0v.hackpad.tw/ep/profile/zsVEYFJyWhm) 再麻煩補確認一下使用授權囉
> [name=venev]

by [Bropheus Huang](https://g0v.hackpad.tw/ep/profile/GpC5QLM6Mdf)  :arrow_down:
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d4101fd4b02e42b393f798f0f1682ad1)

by chewei  :arrow_down:
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0d46f2c12869d070eae089680fd2e015)


## 找人

chewei> 今天有一位(退休、戴眼鏡、製作魚菜共生系統)朋友提到，想要製作環境數據偵測裝置，沒能記得聯繫方式QQ，想提供他一個案例作為參考：**Birdi-Better than a smoke detector**  [http://getbirdi.com](http://getbirdi.com) 室內煙霧偵測器與數據資料庫。以及 [SciCore(Arduino) 開放科學儀器開發群 Public Group](https://m.facebook.com/profile.php?id=1510845375816453) 。

## 慶祝 M Project 開張: book floating 試跑

> 大家帶書來都說可以留給我們看（顯示為書櫃滿）那來玩玩漂書好了。有興趣看的可以來翻或借閱。漂書規則之後想想來開 pad
> [name=venev]


- [《長歌行過美麗島：寫給年輕的你》](http://www.books.com.tw/products/0010617031)（三月佔領松 ipa）
- [《消費行為之前的心理學》](http://www.books.com.tw/products/0010646389)（moedi6t a0kman）
- [《觀看的方式》](http://www.books.com.tw/products/0010477040)（moedi6t tuiry）
- 電影 [Bulworth](http://www.imdb.com/title/tt0118798/)（moedi6t simon 推薦, BP 久尋, nchild 贈碟）

## 總務

> 睡醒補
> [name=venev]


新增 [萌典松活動紀錄](https://drive.google.com/#folders/0B4W4blozmO71MUV3NmU3MzUzUEk) 資料夾

[小松基金明細](https://docs.google.com/spreadsheets/d/1JLdXfMQops2lBsgwpnQHE_L_S4yLi3yB4Y4yRuaYBd4/edit?pli=1#gid=0)
- 上次餘額 459，本次零錢箱 9,268，venev 捐[訪談](https://g0v.hackpad.tw/news98--0EM9nq4zUiX)車馬費 1,000，主揪 au 捐 3,825。

飲食
- BOOKSHOW 飲料贊助：冰紅茶、可樂、茶裡王、瑪露連嫩仙草（廣獲好評並開發奇妙吃法）
- 甜點贊助：雞蛋糕（感謝呂北）、俊美鳳梨酥（感謝___）、日本抹茶巧克力（感謝 tuiry）、新鮮麻糬（感謝____）
- 上次萌典松未開零食：pocky 巧克力棒
- Cama 黑咖啡、紫蘇梅汁 / 1,500
- 午餐達美樂披薩   / 2,392
- 晚餐常旺熱炒 /  2,660

場地 10:30~22:30 / 8,000


## 人來人往簽到表

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_1ad25167457ce81b65cccb6b36348caf)




