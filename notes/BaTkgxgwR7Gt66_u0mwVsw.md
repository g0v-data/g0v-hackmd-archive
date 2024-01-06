---
title: 實名家用快篩供需資訊平台
tags: COVID-19, 家用快篩, antigen, API
description: 這是 g0v 社群協作的家用快篩供需資訊平台，歡迎更多幫手加入協作的行列。
image: https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ba46c424a409ff7841a410c4ccba1843
---

實名家用快篩供需資訊平台
===

因應家用快篩在 2022/4/28 開始透過實名制供應，衛生福利部中央健康保險署提供 [健保特約機構防疫家用快篩剩餘數量明細](https://data.nhi.gov.tw/Datasets/DatasetDetail.aspx?id=698) 開放資料，歡迎社群朋友製作應用界面。

* 輸入你的 Email，加入 g0v slack 討論聊天室： https://join.g0v.tw/ （歡迎參考[如何加入 g0v Slack ](https://g0v.hackmd.io/@jothon/g0v-cowork-guideline/%2FPwJcrD23SBag6sg15epZMA)說明文件）。
* 加入 #covid19 頻道（[公開頻道紀錄](https://g0v-slack-archive.g0v.ronny.tw/index/channel/CTMK5QPA8)）。

資料範例
```csv
醫事機構代碼,醫事機構名稱,醫事機構地址,經度,緯度,醫事機構電話,廠牌項目,快篩試劑截至目前結餘存貨數量,來源資料時間,備註
2340170016,嘉義縣大埔鄉衛生所,嘉義縣大埔鄉大埔村５３－１號,120.5928,23.29397,2521214,羅氏家用新冠病毒抗原自我檢測套組,379,2022/04/27 09:42:31,無
3501200000,臺北虛擬診所,臺北市中正區許昌街１７號８樓　醫務管理科,121.5169,25.04613,27065866,羅氏家用新冠病毒抗原自我檢測套組,414,2022/04/27 09:42:31,無
5901024678,大安健康人生藥局,臺北市大安區信義路４段３４號,121.5447,25.03316,27025553,羅氏家用新冠病毒抗原自我檢測套組,461,2022/04/27 09:42:31,無
```

- 每 30 秒更新。
- 存貨數量的單位是「份」[name=au]

### QA
1. 資料集內容會有：
    1. ✅ 販賣家用快篩的健保藥局
    2. 參與「[COVID-19社區加強監測方案](https://www.cdc.gov.tw/Category/Page/vA0tHhdatBEwkoyjoePhDw)」、醫師評估後發給「來掛號看診的人」的健保診所
    3. ✅ 其他
    > 1, 3
    > 4909 家藥局 & 58 個偏鄉衛生所
    > 2. 大約705家醫療院所(資料來源:https://data.cdc.gov.tw/dataset/covid19_free_rapid_antigen_test_clinics)，不會在資料集裡
2. 資料集的【廠牌項目】，如果一間藥局同時有兩種以上廠牌的家用快篩，那麼【廠牌項目】這個欄位會包含兩種快篩的名字，【存貨數量】是各種快篩的總數嗎？或者是會有兩筆藥局資料，分別對應不同的快篩試劑？
    1. 這期不會碰到這個情況。至於日後假設出現此情況時，我今早是建議 @chi-shun Chen 評估用前者的模式（畢竟價格相同，像口罩購買時也不挑廠牌，而且這樣前端比較好寫），但還是以當時實際狀況為準
3. 為什麼「備註」很多都是口罩？
    - 備註欄出現口罩的資訊應該是藥局端沒維護 [name=chen.chishun]
    - 藥局端若想要改備註，請打開快篩實名制購買頁面，捲到最下方有些提醒字樣，最後那點就是如何改備註的說明 [name=au]
4. 為什麼資料集的資料會越來越少？會不會資料顯示有存貨，但到了藥局依然要排隊領號碼牌？
    - 當日如販售完畢，該藥局就不出現在CSV檔中。[name=chi-shun Chen]
    - 如果號碼牌發完，藥局端有「今天已售完」按鍵，按了就會從資料集裡消失 [name=au]


---


#### 給非工程師的小幫手指南，我們很需要你幫忙：
* 實際使用看看，發現了什麼樣的問題？你建議怎麼改善比較好？
* 編輯共筆，新增內容或整理看不懂的地方（[HackMD 教學](https://hackmd.io/s/quick-start-tw)）。
* 製作或蒐集可以用的文案或圖片素材，提供給開發者使用（[防疫文宣彙整](https://hackmd.io/8mcxozG1T3K2w3Ave9IgCA?view)）。
* 轉貼文章，協助擴散正確資訊。
* 更多 g0v 社群協作方式請參考：[g0v 開源協作手冊](https://g0v.hackmd.io/@jothon/g0v-cowork-guideline/)。
* <span style="color: rgb(250, 135, 7)">標記已下架、已停止維護，或無法正常運作的專案</span> ⚠️
* 其他你想得到的（請幫忙新增在共筆吧）。

### 應用清冊：（歡迎放上自己的連結）

<details>
<summary>家用快篩地圖 by <a href="https://kiang.github.io/" target="_blank">kiang</a></summary>
<img max-height="500px" max-width="500px" src="https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ee3e9b096ee2486c882bd907dd2d5cda">
</details>

https://kiang.github.io/antigen/

<details>
<summary>COVID-19實名制快篩試劑地圖 by <a href="https://yasco.com.tw" target="_blank">Jetter@YASCO</a></summary>
</details>

https://yasco.com.tw/tw/covid19sefttest.asp

<details>
<summary>COVID-19公費快篩發放院所資訊 by <a href="https://yasco.com.tw" target="_blank">Jetter@YASCO</a></summary>
</details>

https://yasco.com.tw/tw/covid19test.asp

<details>
<summary>家用快篩熱度圖 by <a href="https://mowd.tw" target="_blank">Mowd</a></summary>
</details>

https://selftest.mowd.tw


<details>
<summary>全台快篩低價販賣所（LINE） by <a href="https://github.com/funtuan/taiwan-buy-covid19-rapid-test-kits-linebot" target="_blank">FunTuan</a></summary>
</details>

https://line.naver.jp/ti/p/@960iorjj

<details>
<summary>臺灣COVID-19快篩試劑購買地圖 by <a href="https://github.com/becory/covid-19-test-kit-tw" target="_blank">becory</a></summary>
</details>

https://becory.github.io/covid-19-test-kit-tw/

<details>
<summary>我要買快篩 by <a href="https://github.com/peter279k/" target="_blank">peter279k</a> & <a href="https://github.com/albertma2020/" target="_blank">albertma2020</a></summary>
</details>

https://peter279k.github.io/pharmacy-test-kit

<details>
<summary>COVID-19 快篩實名制地圖 by <a href="https://github.com/taichunmin" target="_blank">戴均民 taichunmin</a></summary>
</details>

https://taichunmin.idv.tw/pug/covid19-testkit-maps.html

<details>
<summary>COVID-19 家用抗原快篩藥局販售地圖 by <a href="https://github.com/SiongSng" target="_blank">SiongSng/菘菘</a></summary>
</details>

https://siongsng.github.io/Rapid-Antigen-Test-Taiwan-Map

<details>
<summary>快篩試劑還有嗎?
 by <a href="https://github.com/pokobunhsu" target="_blank">poko</a></summary>
</details>

https://poko.cf/CovSelfTest/

<details>
<summary>快篩&公費快篩&採檢站地圖
 by <a href="https://www.facebook.com/pupu21/posts/3176888778992065" target="_blank">Pupu(DotNet)</a></summary>
</details>

https://mohw-mask.pu.idv.tw/

<details>
<summary>COVID-19 實名制防疫家用快篩庫存查詢
 by <a href="https://github.com/GPXCAT" target="_blank">JSCAT</a></summary>
</details>

https://cov19t.cat2.me/

<details>
<summary>快篩試劑查詢 - COVID-19
 by <a href="https://yslinear.dev/about/" target="_blank">Ying-Shan Lin</a></summary>
</details>

https://covid19.yslinear.dev/fst

### 非官方 API 資料來源：（歡迎放上自己的連結）
<details>
<summary>優化版的家用快篩資料與藥局營業時間 by <a href="https://www.github.com/SiongSng/" target="_blank">SiongSng/菘菘</a></summary>
多增加了一些資訊，例如營業時間等</br>
如果藥局販售完畢或停止販售則會將剩餘數量設為 0，而不是直接刪除</br>
品牌的欄位改成了Array方便未來有多個品牌的時候可以處理</br>
修正了一些資料型別，而不是都是 str

OpenStreetMap 格式: https://raw.githubusercontent.com/SiongSng/Rapid-Antigen-Test-Taiwan-Map/data/data/antigen_open_street_map.json</br>

純快篩資料版: https://raw.githubusercontent.com/SiongSng/Rapid-Antigen-Test-Taiwan-Map/data/data/antigen.json
純藥局資料版: https://raw.githubusercontent.com/SiongSng/Rapid-Antigen-Test-Taiwan-Map/data/data/pharmacy.json
純藥局營業時間資料版: https://raw.githubusercontent.com/SiongSng/Rapid-Antigen-Test-Taiwan-Map/data/data/pharmacy_uptime.json
原始碼: https://github.com/SiongSng/Rapid-Antigen-Test-Taiwan-Map
<img max-height="500px" max-width="500px" src="https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_15f99a6196b90ce4af1259a3c4f781cb.png">
</details>

https://raw.githubusercontent.com/SiongSng/Rapid-Antigen-Test-Taiwan-Map/data/data/antigen_open_street_map.json

<details>
<summary>GeoJson 格式的資料 by <a href="https://kiang.github.io/" target="_blank">kiang</a></summary>

會保留出現過的藥局資料，每分鐘更新一次資料
<img max-height="500px" max-width="500px" src="https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_39f7be8ce0f8742df04a05ad02852aa6.png">
</details>

https://kiang.github.io/data.nhi.gov.tw/antigen.json
<details>
<summary>
 by <a href="https://github.com/pokobunhsu" target="_blank">poko</a></summary>
</details>

https://poko.cf/CovSelfTest/
