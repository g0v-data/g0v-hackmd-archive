---
tags: GIS,
---

# 環境法令整合查詢

> [點此觀看原始內容](https://g0v.hackpad.tw/LGQjB0Lozmc)

> 討論串 [https://www.facebook.com/groups/odtwn/permalink/1635895016424910/](https://www.facebook.com/groups/odtwn/permalink/1635895016424910/)
> [name=che l]


## 基本構想

任意點選一個地理位置，即呈現相關的環境與開發法令，更進一步知道容許使用或是相關條件是什麼。

1.  「在哪裡？」地點與區位
> 關於地點的選擇，若要先與環境法令配套，也許較適合的包括「特定水土保持區（水保法）」、環評爭議區（原大肚山彈藥庫 台積電擴廠案 台中市將砍數百萬棵樹）、台塑廠區（雲林縣最近為了減少台塑造成之空污，通過禁燒生煤與石油焦自治條例 ）
> [name=Xavier S]

> 環境法令包含空污、水污、廢棄物與毒化物，因此可選的地點極其廣泛，但可以先選幾個較重要、與法令相違背或有爭議的地點。比如上個月原本要排的水土保持法修正案就扯到爆炸，也需可以一一檢視這些「特定水土保持區」的核定過程（[相關文章](http://www.taiwanwatch.org.tw/drupal/node/1151)）
> [name=Xavier S]

> 是否需要立體向度？例如海域（例：海岸法）、有地下設施的都市地區（例：大眾捷運法、管線...）...
> [name=che l]

2.  「你要做什麼？」預計使用行為
> 3\. 相關法令：[環境基本法](http://law.moj.gov.tw/Law/LawSearchResult.aspx?p=A&t=A1A2E1F1&k1=%E7%92%B0%E5%A2%83%E5%9F%BA%E6%9C%AC%E6%B3%95)、[環境影響評估](http://law.moj.gov.tw/Law/LawSearchResult.aspx?p=A&t=A1A2E1F1&k1=%E7%92%B0%E5%A2%83%E5%BD%B1%E9%9F%BF%E8%A9%95%E4%BC%B0%E6%B3%95)、[環境影響評估法施行細則](http://law.moj.gov.tw/Law/LawSearchResult.aspx?p=A&t=A1A2E1F1&k1=%E7%92%B0%E5%A2%83%E5%BD%B1%E9%9F%BF%E8%A9%95%E4%BC%B0%E6%B3%95%E6%96%BD%E8%A1%8C%E7%B4%B0%E5%89%87)、[政府政策環境影響評估作業辦法](http://law.moj.gov.tw/Law/LawSearchResult.aspx?p=A&t=A1A2E1F1&k1=%E6%94%BF%E5%BA%9C%E6%94%BF%E7%AD%96%E7%92%B0%E5%A2%83%E5%BD%B1%E9%9F%BF%E8%A9%95%E4%BC%B0%E4%BD%9C%E6%A5%AD%E8%BE%A6%E6%B3%95)  、[軍事秘密及緊急性國防工程環境影響評估作業辦法](http://law.moj.gov.tw/Law/LawSearchResult.aspx?p=A&t=A1A2E1F1&k1=%E8%BB%8D%E4%BA%8B%E7%A7%98%E5%AF%86%E5%8F%8A%E7%B7%8A%E6%80%A5%E6%80%A7%E5%9C%8B%E9%98%B2%E5%B7%A5%E7%A8%8B%E7%92%B0%E5%A2%83%E5%BD%B1%E9%9F%BF%E8%A9%95%E4%BC%B0%E4%BD%9C%E6%A5%AD%E8%BE%A6%E6%B3%95)
> [name=Nien-Ping H]


### 籌備要點


TODO
1.  了解環境法令現況與立法邏輯
2.  確認環境法令的切入觀點、架構
3.  融合地圖與圖說來呈現環境法令的內容，包含提供後續資料查找方向

官方資料
- 營建署「查詢環境敏感地區 單一窗口來幫您」
    - [http://www.moi.gov.tw/chi/chi\_ipmoi\_note/ipmoi\_note\_detail.aspx?sn=153](http://www.moi.gov.tw/chi/chi_ipmoi_note/ipmoi_note_detail.aspx?sn=153)
- 單一地號查詢是否位在山坡地範圍
    - [http://tcgeswc.taipei.gov.tw/ilgmountant.aspx](http://tcgeswc.taipei.gov.tw/ilgmountant.aspx)
- 國土規劃地理資訊圖台 (民眾版)：[http://nsp.tcd.gov.tw/ngis/](http://nsp.tcd.gov.tw/ngis/)
- 整理相關法條原條文：[全國法規資料庫](http://law.moj.gov.tw/) [http://law.moj.gov.tw/](http://law.moj.gov.tw/) [法規下載](http://law.moj.gov.tw/PublicData/DevelopGuide.aspx)
    - 中央法規
    - 地方法規
- 工作頁面
    - [https://docs.google.com/spreadsheets/d/14K1BsQGC2bWFsOdX_j5fV9r-165dV9F5qDl9fyGygnk/edit#gid=0](https://docs.google.com/spreadsheets/d/14K1BsQGC2bWFsOdX_j5fV9r-165dV9F5qDl9fyGygnk/edit#gid=0)

### 盤點：已明確「範圍」的法令圖台
營建署「查詢環境敏感地區 單一窗口來幫您」
https://eland.cpami.gov.tw/seportal/
https://github.com/kiang/eland.cpami.gov.tw
http://www.moi.gov.tw/chi/chi_ipmoi_note/ipmoi_note_detail.aspx?sn=153
海岸資訊整合圖台
營建署海岸地區管理資訊網
https://eland.cpami.gov.tw/CAMN/Web_GIS
內政部海域資訊整合平台
https://ocean.moi.gov.tw/Map
單一地號查詢是否位在山坡地範圍
http://tcgeswc.taipei.gov.tw/ilgmountant.aspx
國土規劃地理資訊圖台 (民眾版)：http://nsp.tcd.gov.tw/ngis/
飛航相關
線上地圖：https://www.flyerlee.com/rcrmap.php
交通部民航局禁飛限飛區 
https://www.facebook.com/notes/%E9%A3%9B%E9%9A%BC%E7%A7%91%E6%8A%80/%E4%B8%AD%E8%8F%AF%E6%B0%91%E5%9C%8B%E4%BA%A4%E9%80%9A%E9%83%A8%E6%B0%91%E8%88%AA%E5%B1%80%E7%A6%81%E9%A3%9B%E9%99%90%E9%A3%9B%E5%8D%80/1305083486223236/
交通部民航局：機場四周禁止施放有礙飛航安全物體範圍GIS圖層
http://www.caa.gov.tw/big5/content/index.asp?sno=960



### 相關專案與構想

- 法規法條數位化面向的專案
    - 法規亦毒氣
        - [https://chrome.google.com/webstore/detail/%E6%B3%95%E8%A6%8F%E4%BA%A6%E6%AF%92%E6%B0%A3/iedodmlnmhobigohbkalkkjlbmdkjalj/related](https://chrome.google.com/webstore/detail/%E6%B3%95%E8%A6%8F%E4%BA%A6%E6%AF%92%E6%B0%A3/iedodmlnmhobigohbkalkkjlbmdkjalj/related)
        - 將網頁中的法規與條號都轉變成連結，讓您快速查閱指定條文。偵測網頁中提到的法規與法條，滑鼠移於其上時即可看該法規或該條文的內容，點選時即連向\[全國法規資料庫\]關於該法規或條文的頁面。亦支援大法官解釋的連結與預覽。
    - 台灣法規
        [https://github.com/victorhsieh/tw-law-corpus](https://github.com/victorhsieh/tw-law-corpus)
- 勞基法掃描器——如何把法條轉譯成自動化的判讀程式？以勞動基準法為例
    - [https://www.facebook.com/groups/odtwn/permalink/2307433222604416/](https://www.facebook.com/groups/odtwn/permalink/2307433222604416/)
- 「究竟何種動物被釋放在何處會涉及那些法律造成什麼問題？」
    - [https://www.facebook.com/shenhornyen/posts/10206528737015532](https://www.facebook.com/shenhornyen/posts/10206528737015532)
- 「營建法令隨手查」g0v grant 提案
    - 簡介：台灣營建法規中的法條過於繁瑣與臃腫，造成使用上效率極差，且查找異常不便。希望藉由"連結"、"整合"串聯散落的法令資料，提升使用效率，以及讓一般有需求的民眾更容易了解並使用法令。
    - 提案網址：[https://grants.g0v.tw/projects/596639f6c293de001ef0bd61](https://grants.g0v.tw/projects/596639f6c293de001ef0bd61)
- 將消防法規與文法邏輯寫入程式當中
    - [https://www.facebook.com/HengBang/videos/1985115138168361/](https://www.facebook.com/HengBang/videos/1985115138168361/)
- 嘗試用法條的規則式來輔助建築物設計
    - [https://www.facebook.com/groups/106313709484026/permalink/1253179758130743/](https://www.facebook.com/groups/106313709484026/permalink/1253179758130743/)
- 法令機器人
    - [https://www.facebook.com/lawsnote/photos/a.164841847355740.1073741828.161008204405771/332579640581959/](https://www.facebook.com/lawsnote/photos/a.164841847355740.1073741828.161008204405771/332579640581959/)


## 各種國土法系切入觀點列舉


### 土地法規的立法角度：

- 參考土地法規/陳立夫
- 法規架構
    - 基本法規
        - 土地法、平均地權條例、土地徵收條例、住宅法、公寓大廈管理條例、憲法...
    - 地籍法規
        - 土地測量類：國土測繪法、建築基地法定空地分割辦法、耕地分割執行要點...
        - 土地登記類：土地登記規則、地籍清理條例、祭祀公業條例、地政士法...
    - 地價法規
        - 不動產估價師法、不動產估價技術規則、地價調查估計規則...
    - 土地利用法規
        - 利用計畫類：區域計畫、非都市土地使用管制規則、都市計畫法...
        - 土地重劃類：市地重劃實施辦法、農地重劃條例、農村社區土地重劃條例...
        - 土地開發類：都市更新條例、新市鎮發條例、國民住宅條例、國軍老舊眷村改建條例、都市計畫容積移轉辦法、海埔地開發管理條例、風景特定區管理規則、休閒農業輔導管理辦法、原住民保留地開發管理辦法...
        - 建築管理類：建築法、山坡地建築管理辦法、農業用地興建農舍辦法、大眾捷運系統兩側禁建限建辦法、航空站飛行場助航設備四周禁止限制建築物及其他障礙物高度管理辦法...
    - 公產管理法規
        - 國有財產法、國有非公用不動產出租管理辦法、國有非公用海岸土地放租辦法、國有非公用設定地上權作業要點、公有土地經營及處理原則...
    - 土地賦稅相關法規
        - 土地稅法、房屋稅條例、工程受益費徵收條例、稅捐稽徵法、地方稅法通則...
    - 產業發展相關法規
        - 農業相關：農業發展條例、農村再生條例...
        - 促進民間參與公共建設法、獎勵民間參與交通建設條例
        - 產業創新條例
        - 離島建設條例
        - 發展觀光條例
        - 園區相關：科學工業園區設置管理條例、加工出口區設置管理條例、農業科技園區管理條例、國際機場園區發展條例
        - 不動產證券化條例
    - 不動產經紀相關法規
        - 不動產經紀業管理條例、公平交易法、消費者保護法...
    - 環境與資源保育法規
        - 環境基本法、環境影響評估法、原住民基本法、森林法、海岸法、山坡地保育利用條例、水土保持法、飲用水管理條例、國家公園法、濕地保育法、文化資產保存法、野生動物保育法、漁業法、礦業法、土石採取法、土壤及地下水污染整治法...
    - 公物與公共設施相關法規
        - 水利法、河川管理辦法、溫泉法、鐵路法、大眾捷運法、電信法、電業法、商港法、要塞堡壘地帶法...
    - 行政關係法規
        - 行政程序法、政府資訊公開法、訴願法、行政訴訟法、國家賠償法、行政執行法、規費法...


### 國土環境規劃的角度：

- 參考 楊重信/國土保育講座
- 法規架構
    - 國土規劃｜地理要素，正面表列，條件允許
        - 國土計畫法
        - 國家公園法
        - 區域計畫法
        - 都市計畫法
        - 海岸法
    - 產業與設施｜地理要素、使用行為
        - 森林法
        - 礦業法
        - 漁業法
        - 發展觀光條例
        - 台灣地區近岸海域遊憩活動管理辦法
        - 遊艇管理辦法
        - 海埔地開發管理辦法
        - 國有財產法
        - 商港法
        - 漁港法
        - [軍事秘密及緊急性國防工程環境影響評估作業辦法](http://law.moj.gov.tw/Law/LawSearchResult.aspx?p=A&t=A1A2E1F1&k1=%E8%BB%8D%E4%BA%8B%E7%A7%98%E5%AF%86%E5%8F%8A%E7%B7%8A%E6%80%A5%E6%80%A7%E5%9C%8B%E9%98%B2%E5%B7%A5%E7%A8%8B%E7%92%B0%E5%A2%83%E5%BD%B1%E9%9F%BF%E8%A9%95%E4%BC%B0%E4%BD%9C%E6%A5%AD%E8%BE%A6%E6%B3%95)
    - 國安與巡防｜地理要素
        - 海岸巡防法
        - 國家安全法
    - 保育與維護｜地理要素
        - 水利法
        - 濕地保育法
        - 野生動物保育法
        - 文化資產保存法
        - 水土保持法
            - 相關圖資:[山坡地(需申請)](https://tgos.nat.gov.tw/TGOS/Web/Metadata/TGOS_MetaData_View.aspx?MID=91972F4E8586CA0667573D5AD971F80E&SHOW_BACK_BUTTON=false&keyword=%E5%B1%B1%E5%9D%A1%E5%9C%B0)、[特定水土保持區](http://data.gov.tw/node/31118)、[水庫集水區](http://data.gov.tw/node/13795)、[保安林](http://data.gov.tw/node/35566)、集水區
            - 台北市，單一地號查詢是否位在山坡地範圍  [http://tcgeswc.taipei.gov.tw/ilgmountant.aspx](http://tcgeswc.taipei.gov.tw/ilgmountant.aspx)
        - 山坡地保育利用條例
            - 相關圖資:[山坡地(需申請)](https://tgos.nat.gov.tw/TGOS/Web/Metadata/TGOS_MetaData_View.aspx?MID=91972F4E8586CA0667573D5AD971F80E&SHOW_BACK_BUTTON=false&keyword=%E5%B1%B1%E5%9D%A1%E5%9C%B0)
        - 土石採取法
        - 環境影響評估法
        - 環境基本法
        - 原住民族基本法
            - 公告傳統領域範圍 [https://www.apc.gov.tw/portal/docDetail.html?CID=3552F8D90DBCC5DB&DID=2D9680BFECBE80B690639AF4378B3ADF](https://www.apc.gov.tw/portal/docDetail.html?CID=3552F8D90DBCC5DB&DID=2D9680BFECBE80B690639AF4378B3ADF)
        - [第一級環境敏感地區及第二級環境敏感地區查詢表(計54項查詢)](http://www.taitung.gov.tw/land/News_Content.aspx?n=29A3216FC2A44D43&s=95A3E028E494F688)
            - 相關圖資:**第一級環境敏感地區**:
                - 1.[特定水土保持區](http://data.gov.tw/node/31118),
                - 2.[河川區域](http://data.gov.tw/node/9823),
                - 3.洪氾區一級管制區及洪水平原一級管制區([歷史淹水資料](http://data.gov.tw/node/25770)),
                - 4.區域排水設施範圍([中央管部分](http://data.gov.tw/node/32732),[臺中市](http://data.gov.tw/node/29289)),
                - 5.[活動斷層](http://data.gov.tw/node/35587),
                - 6.[國家公園區](http://data.gov.tw/wise_search?kw=%E5%9C%8B%E5%AE%B6%E5%85%AC%E5%9C%92)內之特別景觀區、生態保護區
                - 7.[自然保留區](http://data.gov.tw/node/9933),
                - 8.[野生動物保護區](http://data.gov.tw/node/35564),
                - 9.[野生動物重要棲息環境](http://data.gov.tw/node/35559),
                - 10.[自然保護區](https://自然保護區),
                - 11.沿海自然保護區,
                - 12.[國際級重要濕地](http://data.gov.tw/node/25659)或國家級重要濕地核心保護區、生態復育區,
                - 13.古蹟保存區,
                - 14.[遺址](http://data.gov.tw/node/6967),
                - 15.[重要聚落保存區](http://data.gov.tw/node/6966),
                - 16.[國家公園內](http://data.gov.tw/wise_search?kw=%E5%9C%8B%E5%AE%B6%E5%85%AC%E5%9C%92)之史蹟保存區,
                - 17.[飲用水水源水質保護區](http://data.gov.tw/node/6377)或[飲用水取水口](http://data.gov.tw/node/8813),
                - 18.重要水庫集水區,
                - 19[.水庫蓄水範圍](http://data.gov.tw/node/13795),
                - 20.森林（國有林事業區、保安林等森林地區）,
                - 21.森林（區域計畫劃定之森林區）,
                - 22.森林（大專院校實驗林地及林業試驗林地等森林地區）,
                - 23.[溫泉露頭](http://data.gov.tw/node/32504)及其一定範圍,
                - 24.動植物繁殖保育區.
            - 相關圖資:**第二級環境敏感地區**:
                - 1.[地質敏感區](http://www.moeacgs.gov.tw/newlaw/newlaw_SHP.htm),
                - 2.洪氾區二級管制區及洪水平原二級管制區,
                - 3.海堤區域([中央管海堤](http://data.gov.tw/node/32731)),
                - 4.[嚴重地層下陷地區](https://tgos.nat.gov.tw/TGOS/Web/Metadata/TGOS_MetaData_View.aspx?MID=A87AC063AA2E91EE657EDF62A376FC2A&SHOW_BACK_BUTTON=false&keyword=%E5%9A%B4%E9%87%8D%E5%9C%B0%E5%B1%A4%E4%B8%8B%E9%99%B7%E5%9C%B0%E5%8D%80),
                - 5.[山坡地(需申請)](https://tgos.nat.gov.tw/TGOS/Web/Metadata/TGOS_MetaData_View.aspx?MID=91972F4E8586CA0667573D5AD971F80E&SHOW_BACK_BUTTON=false&keyword=%E5%B1%B1%E5%9D%A1%E5%9C%B0),
                - 6.[土石流潛勢溪流](http://data.gov.tw/node/35647),
                - 7.沿海一般保護區,
                - 8.海域區,
                - 9.國家級重要濕地核心保護區、生態復育區以外分區或地方級重要濕地核心保護區、生態復育區,
                - 10.[歷史建築](http://data.gov.tw/node/6965),
                - 11.聚落保存區,
                - 12.文化景觀保存區,
                - 13.[地質敏感區（地質遺跡）](http://www.moeacgs.gov.tw/newlaw/newlaw_SHP.htm),
                - 14.國家公園內之一般管制區及遊憩區,
                - 15.[水庫集水區](http://data.gov.tw/node/13795)（非供家用或公共給水）,
                - 16.[自來水水質水量保護區](http://data.gov.tw/node/25787),
                - 17.優良農地,
                - 18.[礦區（場）(需申請)](https://tgos.nat.gov.tw/TGOS//Web/MetaData/TGOS_MetaData_View.aspx?MID=1B9C3BCD63D3EA71&SHOW_BACK_BUTTON=false)、礦業保留區、地下礦坑分布地區,
                - 19.[地質敏感區（地下水補注）](http://www.moeacgs.gov.tw/newlaw/newlaw_SHP.htm),
                - 20.[人工魚礁區](http://data.gov.tw/node/36326)及[保護礁區](http://data.gov.tw/node/36327),
                - 21.氣象法之禁止或限制建築地區,
                - 22.電信法之禁止或限制建築地區,
                - 23.民用航空法之禁止或限制建築地區或高度管制範圍,
                    - 機場禁限建管制查詢系統：[http](https://bit.ly/2ssUVp7)[s://bit.ly/2ssUVp7](https://bit.ly/2ssUVp7)
                - 24.航空噪音防制區([桃園機場](http://data.gov.tw/node/26115)),
                - 25.核子反應器設施周圍之禁制區及[低密度人口區](http://data.gov.tw/node/28261),
                - 26.公路兩側禁建限建地區,
                - 27.大眾捷運系統兩側禁建限建地區,
                - 28.高速鐵路兩側限建地區,
                - 29.海岸管制區、山地管制區、重要軍事設施管制區之禁建、限建地區,
                - 30.要塞堡壘地帶
    - 污染防治｜地理要素、使用行為
        - 海洋污染防治法
        - 水污染防治法
        - 土壤及地下水污染整治法
        - 空氣污染防治法
    - 地政制度｜
        - 土地法
        - 土地法施行法

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c1b5c8225759aae96da395ce9b1e2f7a)



### 國土計畫法國土功能分區

- 國土功能分區圖繪製作業辦法草案總說明
    - [https://www.cpami.gov.tw/kids/filesys/file/chinese/dept/rp5/10601172.pdf](https://www.cpami.gov.tw/kids/filesys/file/chinese/dept/rp5/10601172.pdf)
- 第四條 國土功能分區及其分類之劃設 條件如下：
    - 一、國土保育地區
        - （一）第一類：
            - 1.符合下列條件，但不包含符合 城鄉發展地區第一類、第二類 及第四類劃設條件之地區： (1)活動斷層兩側一定範圍。 (2)特定水土保持區（水庫集水 區、主要河川集水區須特別保護者、海岸、湖泊沿岸、 水道兩岸須特別保護者、沙 丘地、沙灘等風蝕嚴重者）。 (3)河川區域。 (4)洪氾區一級管制區及洪水平 原一級管制區。 (4)區域排水設施範圍。 (5)一級海岸防護區（非屬海域 範圍者）。 (7)自然保留區。 (8)野生動物保護區。 (9)野生動物重要棲息環境。 (10)自然保護區。 (11)一級海岸保護區（非屬海域 範圍者）。 (12)國際級重要濕地、國家級重 要濕地之核心保育區及生態 復育區。 (13)古蹟保存區。 (14)考古遺址。 (15)重要聚落建築群。 (16)重要文化景觀。 (17)重要史蹟。 (18)飲用水水源水質保護區或 飲用水取水口一定距離內之 地區。 (19)水庫集水區(供家用或供公 共給水) 。 (20)水庫蓄水範圍。 (21)國有林事業區（自然保護 區、國土保安區）、保安林。 (22)依原區域計畫劃定之森林 區。 (23)大專院校實驗林地及林業 試驗林地等。 (24)溫泉露頭及其一定範圍。
            - 2.位於前目範圍內之零星土地， 應一併予以劃入。
        - （二）第二類：
            - 1.符合下列條件之地區： (1)地質敏感區(活動斷層、山崩 與地滑、土石流)。 (2)洪氾區二級管制區及洪水平 原二級管制區。 (3)嚴重地層下陷地區。 (4)淹水潛勢。 (5)山坡地。 (6)土石流潛勢溪流。 (7)二級海岸防護區（非屬海域 範圍者）。 (8)依原「莫拉克颱風災後重建 特別條例」劃定公告之「特 定區域」。 (9)二級海岸保護區（非屬海域 範圍者）。 (10)國家級重要濕地之核心保 育區及生態復育區以外分 區、地方級重要濕地之核心 保育區及生態復育區。 (11)歷史建築。 (12)聚落建築群。 (13)文化景觀。 (14)紀念建築。 (15)史蹟。 (16)地質敏感區(地質遺跡)。 (17)水庫集水區(非供家用或非 供公共給水)。 (18)自來水水質水量保護區。 (19)礦區(場)、礦業保留區、地 下礦坑分布地區。 (20)地質敏感區(地下水補注)。 (21)國有林事業區（森林育樂 區、林木經營區）。 (22)特定水土保持區（山坡地陡 峭，具危害公共安全之虞 者、其他對水土保育有嚴重影響者）。
            - 2.位於前目範圍內之零星土地， 應一併予以劃入。
        - （三）第三類：實施國家公園計畫地區。
    - 二、海洋資源地區
        - （一）第一類：使用行為具排他、獨占者。
        - （二）第二類：使用行為具部分排他、 部分獨占者。
        - （三）第三類：尚未使用之海域或其 他非屬前列之分類者。
    - 三、農業發展地區
        - （一）第一類：
            - 1.具優良農業生產環境、維持糧 食安全功能或曾經投資建設重 大農業改良設施之地區，包含 農地資源分類分級之第一種農 業用地、環境優良且投入設施 建設之養殖使用土地。
            - 2.位於前目範圍內之零星土地， 應一併予以劃入。
        - （二）第二類：
            - 1.具良好農業生產環境、糧食生 產功能，為促進農業發展多元 化之地區，包含農地資源分類 分級之第二種、第三種農業用 地、其他養殖使用土地。
            - 2.位於前目範圍內之零星土地， 應一併予以劃入。
        - （三）第三類：
            - 1.擁有糧食生產功能且位於坡地 之農業生產土地，以及無國土 保安之虞且可供經濟營林之林 產業發展土地，包含農地資源 分類分級之第四種農業用地、 林產業土地等。
            - 2.位於前目範圍內之零星土地，應一併予以劃入。
        - （四）第四類：
            - 農村主要人口集居地 區，其現有聚落人口達一定規 模，且與農業生產、生活、生 態之關係密不可分之農村聚 落，面積達五公頃以上者，包 括原依區域計畫法劃設之鄉村 區（但不包含符合城鄉發展地 區或國土保育地區劃設條件之 地區）。
    - 四、城鄉發展地區
        - （一）第一類：
            - 1.實施都市計畫之地區。
            - 2.都市計畫區面積超過百分之五 十屬符合國土保育地區第一級 劃設條件之地區者，應予註記。
        - （二）第二類：
            - 1.依原區域計畫法劃定之鄉村區 或建築用地，聚集面積達五公 頃以上者（但偏鄉及離島地區 得視實際情況酌減之）。
            - 2.前目範圍內面積超過百分之五 十屬符合國土保育地區第一級 劃設條件之地區者，應予註記。
            - 3.位於第一目範圍內之零星土 地，應一併予以劃入。
        - （三）第三類：
            - 直轄市、縣(市)國土 計畫指定提供城鄉發展儲備之地區。
        - （四）第四類：原住民族保留地範圍內依原區域計畫法劃設之鄉村區，面積達三公頃以上者。
- 國土功能分區及其分類之劃設順序如下：
    - 一、第一優先：國土保育地區第一類、 國土保育地區第三類。
    - 二、第二優先：農業發展地區第一類、 農業發展地區第二類、農業發展地區第三類、農業發展地區第四類。
    - 三、第三優先：其他國土功能分區及其分類。
- 都市計畫或國家公園計畫範圍經依法劃出之地區，應依第一項規定劃 設國土功能分區及其分類。



### 土地利用導向的角度

- 參考：土地利用計畫法導論
- 法規架構：
    - 土地利用規劃
        - 都市計畫法
            - 相關圖資: [都市計畫土地使用分區圖(需申請,尚未開放)](https://tgos.nat.gov.tw/tgos/Web/Metadata/TGOS_MetaData_View.aspx?MID=CF8233A90A9FC54B47F1A6053691F34D&SHOW_BACK_BUTTON=false&keyword=%E9%83%BD%E5%B8%82%E8%A8%88%E7%95%AB)
> 土地使用分區有個系統可以看，但是要查˙或是要用甚至是開放都還要另外處理。
> [name=林立哲]

> [http://luz.tcd.gov.tw/WEB/](http://luz.tcd.gov.tw/WEB/)
> [name=林立哲]

        - 區域計畫法
            - [區域計畫e化網](http://60.248.163.235/nulpweb/genmap/map.aspx)（都計、非都使用分區、限制及條件發展區地理圖資）
            - [非都市土地編定統計](http://statis.moi.gov.tw/micst/stmain.jsp?sys=100)
        - [http://www.taitung.gov.tw/land/News_Content.aspx?n=29A3216FC2A44D43&s=95A3E028E494F688](http://www.taitung.gov.tw/land/News_Content.aspx?n=29A3216FC2A44D43&s=95A3E028E494F688)
        - 非都市土地使用管制規則
            - 相關圖資: [非都市計畫土地使用分區圖(需申請,尚未開放)](https://tgos.nat.gov.tw/tgos/Web/Metadata/TGOS_MetaData_View.aspx?MID=CF8233A90A9FC54B657EDF62A376FC2A&SHOW_BACK_BUTTON=false&keyword=%E9%83%BD%E5%B8%82%E8%A8%88%E7%95%AB)
    - 土地重劃與徵收
        - 平均地權條例
        - 市地重劃實施辦法
        - 土地徵收條例
        - 區段徵收條例
        - 農地重劃條例
        - 農村社區土地重劃條例
        - 農業發展條例
        - 其他
    - 開發建設
        - 都市更新條例
        - 新市鎮開發條例
        - 促進民間參與公共建設法
        - 獎勵民間參與交通建設條例
        - 大眾捷運法
        - 農業發展條例
        - 農業用地興建農舍辦法
        - 文化資產保存法
        - 環境影響評估法
        - 水土保持法
        - 水利法
        - 其他
    - 建築管理
        - 建築法
        - 山坡地建築管理辦法
        - 其他

### 土地開發者與建築營造的角度：

- 參考：土地開發與建築法規應用
- 法規架構
    - 先區分都市土地，或是非都市土地，或是山坡地
        - 都市土地
            - 只有「主要計畫」的都市土地
            - 已有「細部計畫」的都市土地
            - 希望「變更使用分區」的都市土地
        - 非都市土地
            - 已編定分區使用的非都市土地
                - 按原編定使用
                - 相同分區變更編定使用
                - 變更分區及編定使用
            - 未編定分區使用的非都市土地
        - 國家公園土地
        - 山坡地
            - 山坡地的定義與範圍
            - 山坡地基地不得開發建築之認定標準
            - 山坡地管理法規的歷史演變
    - 基地外部的法規分析
    - 基地內部，建築物外部的法規分析
    - 基地內部，建築物平面的法規分析
    - 建築管理法規分類
        - 建築管理
        - 設計階段
        - 請照階段
        - 施工、竣工階段
        - 使用管理階段
            - 公共安全
            - 違建處理
            - 公寓大廈管理
        - 其他


### 從特定區位來檢視涉及什麼法令

- 海岸相關的各種法令
    - https://www.facebook.com/834991856533304/photos/pb.834991856533304.-2207520000.1438245642./897389633626859/?type=3&theater
    - 海岸法適用範圍探討
        - https://www.facebook.com/chinyi.wu.7/posts/1871258816223795
    - 海岸相關的各種法令表格 
        - [https://goo.gl/photos/JjxE6iRWGzafXKeQ7](https://goo.gl/photos/JjxE6iRWGzafXKeQ7)
- 部落觀點
    - https://www.facebook.com/100000255730306/posts/5425011260850678/

### 應用情境列舉

- 建物行政輔助查核作業
    - [https://www.facebook.com/media/set/?set=oa.1964156740538989&type=3](https://www.facebook.com/media/set/?set=oa.1964156740538989&type=3)
        - 利用GIS及BIM的技術開發系統，系統已具有完整的輔助查核功能。
        - 行政輔助主要提供申請者在評估基地開發時，先行查核該基地必須注意及相關列管事 項及內容，此項作業可以讓申請者快速綜整該基地的狀況，以作為該基地開發及後續 送件審查的參考
        - 竣工模型上繳系統
- 新加坡政府透過地圖來展示「都市設計管制區域範圍 polygon 」
        - [https://www.ura.gov.sg/maps/](https://www.ura.gov.sg/maps/)
- 這是一個關注新北市新店行政生活園區開發案的粉絲頁，正在尋找相關審議報告資料，以下摘自[粉絲頁](https://www.facebook.com/newgoodlifehd)貼文：
    - 「本案資料尚未取得，需要眾人幫忙的：交通影響評估報告（缺，審查中）、新北市及營建署關於本案的都市計畫審議會議記錄。。。。。。請大家多多幫忙尋找。」
    - 「本案資料已經收集完成以及案件進度：都市更新事業計畫（公展版，審查中）、都市更新權利變換計畫（公展版，審查中）、環境影響評估報告（公開版，審查中）、變更新店都市計畫（部分機關用地為行政園區特定專用區、部分機關用地為住宅區、部分住宅區為行政園區特定專用區）書（預定核定版，審查完成尚未公告）、擬定新店都市計畫（行政園區特定專用區）細部計畫書（預定核定版，審查完成尚未公告）。。。。。。。有需要的朋友可以留下訊息索取。。。」
- 商業登記與土地使用分區管制：[https://g0v.hackpad.tw/1G0DUVd6vsg](https://g0v.hackpad.tw/1G0DUVd6vsg)
- [國家公園生物多樣性地理資訊系統資料庫/National Park Biodiversity GIS Database](https://www.facebook.com/inpgis)
- [台灣國家公園設立問題之社會學分析](http://nccur.lib.nccu.edu.tw/handle/140.119/34610)
- [海域使用現況重疊示意圖](https://www.facebook.com/834991856533304/photos/pb.834991856533304.-2207520000.1438245642./897389633626859/?type=3&theater)
- [https://www.facebook.com/chinyi.wu.7/posts/1871258816223795?](https://www.facebook.com/chinyi.wu.7/posts/1871258816223795?)
- 環境風險與災害潛勢評估
- 「關渡自然保留區」
    - https://www.facebook.com/104951650949326/photos/a.132642528180238/132642371513587/
- 「假設我到一般的海邊，挖一小塊珊瑚上來帶回家，這樣違反了什麼法？」
    - https://www.facebook.com/1132914889/posts/10224487508711903/
- 在海邊的通報事務
    - https://www.facebook.com/lucky200412/posts/10228327824928955
    - 遇到海邊才會發生的事：118(海巡署專線)
    - 遇到樹林樹木有關的事：0800-000-930(林務局專線)
    - 遇到髒亂污染相關的事：0800-066-666(環保局專線)
    - 遇到平常到處都有的事：110 / 119
    - 電燈不亮道路破損之類的：1999

## Mockup 初步構想

### 以地圖為基礎

- 底圖：OSM 為基礎銜接不同圖資來源
- 法圖：
    - 已經 polygon 化的法
        - 土地使用分區(國家公園、都市計畫土地使用分區、非都市土地編定)
        - 野生動物保育法的野生動物保護區
        - 網格資料（土壤類型、土地利用、高程、土地使用分區）
            - 以內政部20公尺網格數值地形模型資料 20m＊20m 坐標點位資料為基礎產置不同網格資料屬性
        - 向量資料（集水區、蓄水範圍、河川範圍、都市計畫）
        - 向量資料連結法律條文、實行時間、法條本身允許什麼以及在什麼例外條件下允許
    - 尚未 polygon 化的法
        - 海域類的法，好像還沒地理圖資化？
        - 飛航管制？
        - ...
    - 無法 polygon 化的法律
        - 這樣的法有哪些？
        - 例如查詢者要給定條件（可能是開發強度）才有辦法往下探討的？...其他構成方式








