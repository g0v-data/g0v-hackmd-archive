---
title: "國土巡守隊"
tags: 國土巡守隊,hackpad
---

# 國土巡守隊

> [點此觀看原始內容](https://g0v.hackpad.tw/0NkW64xhg7g)


簡報： [https://kiang.github.io/pdf/20180519.pdf](https://kiang.github.io/pdf/20180519.pdf)
實做介紹： [https://www.youtube.com/watch?v=JmxFhvGzw6E](https://www.youtube.com/watch?v=JmxFhvGzw6E)
線上展示： [https://kiang.github.io/lands_patrol/](https://kiang.github.io/lands_patrol/)

目前能夠掌握的資料：
1.  全國農地 \- [https://github.com/kiang/map.coa.gov.tw](https://github.com/kiang/map.coa.gov.tw)
2.  全國公有地 \- [https://data.gov.tw/dataset/34315](https://data.gov.tw/dataset/34315)
> 部分縣市會釋出的自己管理的公有地，與中央的資料型態應該是類似，是否有需要納入本次探討中？此頁面列舉 [台北市政府釋出的公有土地資料](https://docs.google.com/spreadsheets/d/1R80Gq408ZALOieUaErRiJmslaQZoxSd3Sn4pq1OIl-g/edit#)
> [name=che l]

> 理想上還是希望所有地籍資料釋出，這次的實做可能會先以比較大批的資料為主
> [name=kiang]


預期會以 Ushahidi ( [https://www.ushahidi.com/](https://www.ushahidi.com/) )為基礎，透過 API 串接去帶出符合期待的使用者介面

問題：
### 地籍作為國土巡守的必然基礎為何？

> 以公有地佔用為例，如果沒有土地的明確範圍，其實很難具體看出哪些區域有佔用情況；而個別問題通報，如果能夠明確提供地號資訊，理論上經辦單位可以加速處理過程，而不用先等待第一線現場勘查後才開始動作。
> [name=kiang]

> 提報公有地佔用之專案：揪地霸 [http://9d8.tw/](http://9d8.tw/)；[https://github.com/dz1984/9d8TW](https://github.com/dz1984/9d8TW)；[hackpad](https://g0v.hackpad.tw/-9d8.tw-M71q8C7WWPB)；[demo影片](https://youtu.be/bxnqqFN1lYE)
> [name=che l]

> 感覺網站已經消失了 XD
> [name=kiang]

> 驚！補上 demo 影片，介面特點在於，使用者點擊地圖畫面中的地點後，跳出登錄視窗，來記錄他的通報內容，且可選擇匿名
> [name=che l]

### 巡守隊要查緝的標的與狀態為何？

> 農地工廠、農舍、廢棄物傾倒、公有地佔用等
> [name=kiang]


### 巡守資訊以圖台揭露後創造什麼價值？

> 過去案件直接通報給政府單位後大多石沉大海，中間總有各種怪異的理由造成案件停止追查，如果能夠由民間自發建置圖台進行追蹤，透過資訊的揭露我們可以明確知道哪些單位在處理案件通報時遇到了瓶頸，累積的資料可以產生社會壓力讓問題可以被重視，而透明化則是可以避免許多政治性的干涉。
> [name=kiang]

> 另外，是否也能讓政府政策歷史中所允許的安居聚落（如「[非列管眷村](http://www.coolloud.org.tw/node/67750)」等），或是原住民土地系統與國家土地登記之間的衝突（如「[達悟族共有地並非無主地卻收歸國有](https://newtalk.tw/news/view/2014-09-21/51658)」），進行申訴與立場說明？
> [name=che l]


### 我們的系統為現況做了什麼樣的改善或提升？

> 我們開發的系統可以聚焦在問題如何被解決，而不是因應各種行政流程而讓系統架構變得龐大又破碎；現有的政府單位在橫向溝通部份一直缺乏有效的進展，民間自發建置就可以主動串接各單位資訊，而不是任由平行單位互相踢皮球。
> [name=kiang]


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_44c4c17c4663ae61505b4d2d5feef2f0)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_7196164f21aa0a1dd47db333e701fe27)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_bad269ddb84a2d63da279b6736894025)

目前實做雛型： [https://kiang.github.io/lands_patrol/](https://kiang.github.io/lands_patrol/)

操作介紹：

[https://www.youtube.com/watch?v=JmxFhvGzw6E](https://www.youtube.com/watch?v=JmxFhvGzw6E)

期末簡報：
1.  描述問題的嚴重性：情境 = 鈺均/建科
    1.  以農委會釋出的農地工廠資料，有 130831 筆土地資料，但並不清楚代表多少工廠
2.  解決方案：實作 = 明宗
3.  效益：如何改變這個世界? = Clare
    1.  你們的實作會有甚麼效益? =\> 共同思考
        1.  讓使用者容易上手的一個通報服務
        2.  透過政府開放資料讓民眾可以進行精準的通報
        3.  發揮開放資料被開放後的價值
        4.  群眾幫忙主管機關做些前置工作，避免現況稽查人員遠低於違規案件的情況，希望提高稽查效率
4.  里程碑：逐步的社會實踐 = 鈺均/建科
    1.  找到對這個議題感興趣的 NGO ，具體討論需求
        1.  社區大學、地球公民基金會、關心水文、自然的組織
    2.  與 NGO 共同合作推動，要求政府端開啟系統介接可能
    3.  系統完成介接後依據資料的記錄去統計個別案件處理生命週期，作為各種議題、政策研究的基礎，不再空談
5.  彙整：Clare & 書正

### FAQ

- 如何累積足夠的資料？
> 目前以農地工廠為例，取用的資料是來自農委會釋出的農地盤查結果資料，裡面約有 13 萬筆的土地資料是可能的農地工廠位置，以這份資料作為基礎去引導民眾協助提供資料會有清楚的標的存在，因此會好過從零開始的情況
> [name=kiang]

- 這個應用能否避免新的農地工廠產生？
> 過去對政府單位的舉報資料很少對外揭露，國土巡守隊做的事情是第一時間揭露再監督後續處理狀況，資訊的公開會先嚇阻一些在意社會輿論的上市上櫃公司繼續抱著投機心態；其次也因為資料公開，蒐集的資料會持續累積，讓更多民眾可以累積具體行動成果，期待當力量累積到一定程度時會讓相關單位能夠正視這個問題。
> [name=kiang]

- 如何驗證資料的正確性？
> 現階段只能由志工做初步的審核篩選，進一步的也許可以由程式介面去延伸交叉檢驗機制，例如讓後面參與的人可以幫忙確認鄰近區域資料的正確性
> [name=kiang]

- 審核 後的 這些 "農地工廠、農舍、廢棄物傾倒、公有地佔用" 資訊 有沒有可能透過現有的開放資料管道 釋出，例如 轉成 符合「共通示警資料標準」格式的CAP資料。目前NCDR正在舉辦活動鼓勵 名間提供資料，相關活動公告如下：[https://lihi.cc/pZJKU/g0v](https://lihi.cc/pZJKU/g0v)
> 災害示警資料跟目前國土巡守隊的目標不太一樣，不確定 NCDR 會不會拒收？
> [name=kiang]

> 我覺得「共通示警資料標準」的可用範圍可以很大唷，例如國外案例就有用在失蹤兒童通報(連結參考：[wiki](https://zh.wikipedia.org/wiki/%E5%AE%89%E7%8F%80%E8%AD%A6%E6%8A%A5))歡迎大大來試試看
> [name=Paul L]

> 也許可以嘗試實做，只是因為活動地點在台北，最近已經太常北上了，所以暫時休息一下 XD
> [name=kiang]


