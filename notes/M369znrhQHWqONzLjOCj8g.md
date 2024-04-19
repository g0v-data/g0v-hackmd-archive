---
tags: GIS
---

# 臺北市文山區碳收支地圖 / 淨零議題資料蒐集


:::warning
目錄
[TOC]

工作用相簿：https://photos.app.goo.gl/gu6im4edscy2Xrjb7
:::

## 文山區碳收支地圖試作

跳坑：
- chewei 找資料、讀論文中的推估方法
- Vik 協助製作地圖

感謝 🙏
- 感謝 [林子平老師](https://www.arch.ncku.edu.tw/cht/module/pageinfo/242-i5.html) 分享研究方法建議

參考 [舊臺南市－地區碳收支分析](https://docs.google.com/document/d/1rk_lQvK5rN0BDIFF7mLOVJKUA8NrZvnAAfm5iwidSxk/edit) 研究方法 ([文獻](https://drive.google.com/file/d/1RE1Kr8xsh1-FgWeM8oPkeP1oas22QQ1u/view))，並針對臺北市文山區嘗試製作年度碳收支地圖。依照論文中「第五節、碳收支計算方法」架構，特點筆記：
- 文獻蒐集的目的
    - 整合不同建築用途的能源耗用密度(Energy Use　Intensity, EUI)
    - 各土地使用類型的碳吸存係數
    - 各車種汽油耗用的碳排放當量
- 此方法有採用「網格」200 公尺乘以200公尺
    - 討論：預計先嘗試採用 polygon 成為 rawdata

## 第一類：建築、植栽、土壤與水體二氧化碳排放

### 係數表：建物地貌單位面積每年碳排係數
18 種建物類型 + 7 種植栽土壤與水體
<iframe src="https://docs.google.com/spreadsheets/d/e/2PACX-1vR9To97j35hbXxGQrG-2GnUSd1VzFPzjXIVqLZJz1hBgQ4OHf7Ttdk9SGGoHvkWAy2Ddx02dynzfqEp/pubhtml?gid=0&amp;single=true&amp;widget=true&amp;headers=false"　height="600px" width="100%"></iframe>

### 討論區

7 種種植栽土壤與水體
- 少了「森林」這個類別，可能要另外找文獻係數，來應用於臺北市文山區的山區森林範圍

18 種建物類型
- 建物類型定義釐清
    - 住宅I(低層住宅)、住宅II(無電梯公寓)、住宅III(電梯公寓)
        - 三者定義？
        - 文山區，要如何知道上述三項，GIS 且帶有 Polygon 分布位置?
    - 交通轉運站
        - 是指哪一種程度？
    - 垃圾處理場
        - 會是指焚化爐嗎？例如木柵垃圾焚化廠 https://www.mcrip.gov.taipei/
- 係數應用、採計範圍
    - 建築物類的係數，是用建築物投影面積，還是總樓地板面積？
    - 如果是學校類，像是大學/高中：是使用整個校園範圍嗎？或是校舍建築物的投影面積（或樓地板面積）？
        - 學校情境，有可能容積沒有用完，所以若是用 土地使用分區允許容積來計算，有時候會高估碳排量，例如政治大學有不少尚未開發土地
    - 林子平老師有分享，便利商店的係數數字可能高達 4 位數
- 本次論文的係數，注意事項補充說明
    - 一般來說，建築物營運階段，三種碳排來源：
        - 用電、燃氣、燃油
        - 本次論文的係數，除了住宅建築外，其他類型建築暫不考量「燃氣」及「燃油」部分的能耗。
        - 「燃氣」使用量乃參酌張又升(2002)查住宅使用中二氧化碳排放比例來預估，即住宅的燃氣能耗量為電力 0.23 倍。
    - 本次論文，對於台灣每 kWh 的單位二氧化碳排放量，採用 0.521 kgCO2/kWh，這個數字可以依照比較新的公布結果進行調整。
    - 是否會因為結構材料，同性質的建築物，其係數而有所不同？
        - 例如磚造住宅、RC住宅、鋼構住宅？
        - 不過，係數是基於使用行為 (用電、燃氣、燃油)，所以構造材料本身是否會影響使用行為呢？

### 圖資整理試作 

可以運用哪些圖資，產出文山區 18 種建物、7 種水綠環境，且 GIS 要有面積
- 土地使用分區，有一份比較新的
    - 如果是已開發地區，土地使用分區應該也是符合現況
- 國土利用調查，有一份比較舊的
    - 有些地區國土利用調查比較符合實際，例如一大塊農業區或保護區裡面有建物群，國土利用調查會基於現況進行調查標記出建物，但土地使用分區就是一大塊無法反映出建物群
- 先放到 Google My Map：https://maps.app.goo.gl/agmYSYzcty9ca6ZcA

<iframe src="https://www.google.com/maps/d/embed?mid=1_cZYRmxBvPc3Uh_v0ihe8QscrDThoJY&ehbc=2E312F" width="100%" height="480"></iframe>


其他圖資資料來源評估
- 都市設計及土地使用開發許可審議服務平台
    - 施工地圖
- 臺北城市儀表板開源版圖臺（如公有空地、開放空間等）
- 臺北市歷史圖資展示系統
- 臺北市社區營造案件地圖資料庫 (Localwiki 平台)


## 第二類：道路運輸二氧化碳排放

### 論文中的推估方法
- 參酌 Lin(2010)之研究，三種汽機車單位距離碳排放量
    - 小客車為 0.00025 kgCO2/m
    - 重車為 0.00036 kgCO2/m
    - 機車為 0.00010 kgCO2/m
- 論文中區分出「都會區」與「核心地區」
    - 為什麼？是基於交通車流量資料來源，有兩份各處理不同範圍？
- 「都會區」界定三種路寬，有各自碳排係數
    - 路寬 25 公尺以上的主要公路
    - 10-25 公尺的次要道路
    - 10 公尺以下的地區公路
- 「核心地區」
    - 123

### 臺北市資料蒐集

112 年動態號誌路口流量(上傳檔).7z
- 資料檔案下載網址：https://drive.google.com/file/d/10YX0HXeRN1RoHZtdKa-cQwN3jFpBUL2E/view
    - 從這份文件「交通流量調查資料(PDF下載)」找到的：https://www.bote.gov.taipei/Content_List.aspx?n=EAC17E905EB08680


臺北市車輛偵測器(VD)資料
- 車輛偵測器(VD)資料，不過並不是每一條道路都有車輛偵測器
    - 資訊局有把 車輛偵測器(VD)資料 放到地圖上呈現，可以快速瀏覽哪些路段有車輛偵測器
        - https://tuic.gov.taipei/dashboard-demo/mapview?index=transport
        - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ec5c7ed01e6d9bdf1eb94048beb4e8a8.png)
        - 沒有資料的路段：
            - 高速公路
- 目前查閱了台北市道路流量資料：https://www.bote.gov.taipei/Content_List.aspx?n=EAC17E905EB08680
    - 既有資料給定的項目是：繁忙路口、橋樑在交通尖峰時刻的車種流量（上下班）
    - ~~和台南資料提供的「全路段流量」有很大的區別，不確定是否能用論文中的公式去計算？~~
- API 臺北市道路速率
    - https://data.taipei/dataset/detail?id=b5aaf33a-a6dc-4836-bce6-09986241fe11
    - 說明
        - 提供道路即時資訊，包含車速、流量及道路績效。
        - 介接欄位說明文件：https://www-ws.gov.taipei/001/Upload/public/mmo/dot/臺北市交通控制中心資料庫介接說明文件.pdf
    - 資料範例
        - <vd:SectionData>
            - <vd:SectionId>Z2ASP40</vd:SectionId>
            - <vd:SectionName>木柵路 萬芳路-秀明路</vd:SectionName>
            - <vd:AvgSpd>62.454544</vd:AvgSpd>
            - <vd:AvgOcc>1.2</vd:AvgOcc>
            - <vd:TotalVol>22.0</vd:TotalVol>
            - <vd:MOELevel>0</vd:MOELevel>
            - <vd:StartWgsX>121.571743</vd:StartWgsX>
            - <vd:StartWgsY>24.994856</vd:StartWgsY>
            - <vd:EndWgsX>121.571124</vd:EndWgsX>
            - <vd:EndWgsY>24.991654</vd:EndWgsY>
        - </vd:SectionData>
        - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_428356764dcd29137518f368098b661e.png)


臺北市道路長度及面積-按寬度分
- https://www.dot.gov.taipei/News.aspx?n=CE59C4615C1AB800&sms=2360897E5315503F
- 依照 12 個行政區，計算以下各種寬度道路的面積
    - 6公尺以下、6～未滿10公尺、10～未滿15公尺、15~未滿20公尺、20～未滿30公尺、30～未滿40公尺、40～未滿50公尺、50～未滿60公尺、60～未滿70公尺、70公尺寬以上
- 討論：
    - 高速公路、立體高架橋或隧道，有一起計算嗎？
    - 有沒有可能，參考「建物地貌單位面積每年碳排係數」，產出一套「各級道路單位面積每年碳排係數」？
        - 好處
            - 常見的土地圖資，像是土地使用分區或國土利用調查，可取得道路面積，且保有地理資料分佈特點，而非僅統計數字
            - 可以與建物水綠資源一起作為一套概全國範圍概估用的單位面積碳排係數
        - 只是說，「道路面積」如何合理推論出「道路車流量」再接續推論「道路車流量碳排」？
            - 區位問題：同樣寬度的道路，文山區與中正區，也可能很難都用同一個係數數字
            - 車道種類：
                - 高速公路（汽車）
                - 一般公路（汽機車）
    - 如果以「臺北市車輛偵測器(VD)資料」這些主要道路，作為已知路段資料，來推論比這些主要道路還要窄的路段們，各自的車流碳排量？
        - 應該還算相對合理吧？
        - 一些條件：
            - 只能推論同一個行政區，不要跨區推論；或是可以界定一個「交通系統區」？
                - 例如文山區與深坑區應該可以一起看，因為主要道路是連貫的
                - 例如文山區與新店區，可能就不能一起看，因為兩者雖然互相相鄰，但車流都只能透過瓶頸橋梁連接
        - 例如木柵路從萬芳路-秀明路這段 20 米寬的路，可以透過年度資料知道道路車流量
            - 以此車流量有辦法推論出周邊地區 12m、10m、8m、6m 道路各自的單位面積車流量嗎？
            - 已知周邊各種寬度道路的長度


詢問臺北市交通局
- 受理機關：臺北市政府交通局，承辦人：陳先生，聯絡電話：02-27208889或1999轉6847
- 回覆日期：113/01/22
- 有關您反映是否有臺北市文山區交通運輸二氧化碳排放估算成果及文山區車流種類推薦之圖資或統計成果一事，本局說明如下：
    - 本市溫室氣體排放量分析報告（無單獨調查各行政區），已由本府環境保護局統計分析後公開於資訊網站，相關參考資料可至本府環境保護局/業務資料/氣候變遷管理科網站下載。
    - 另本市交通管制工程處每年針對本市重要路口及路段橋梁進行交通流量調查，有關文山區車流量之相關參考資料可至本市交通管制工程處/業務資訊/業務服務/交通資料網站下載。


彰化縣平均每日交通量計算表
- https://labor.chcg.gov.tw/files/%E5%B9%B3%E5%9D%87%E6%AF%8F%E6%97%A5%E4%BA%A4%E9%80%9A%E9%87%8F%E8%A8%88%E7%AE%97%E8%A1%A8_6_1060808.pdf

路口影片計算車輛數
- http://cheliuyun.com/#stepMenu

其他種類的交通類碳排且不是用道路面積計算
- 軌道運輸捷運與輕軌，找有沒有推估係數
    - 文山區有捷運
- 軌道運輸鐵路，找有沒有推估係數

TODO
- 寫信給交通局，詢問對於上述車道車流碳排，有沒有什麼估算方式建議
    - 20240118 chewei 已寄信詢問臺北市交通局，對於「臺北市文山區碳收支地圖」所需之交通碳排放量資料，有什麼建議；20240122 已收到回覆


# 綜合討論

## Google EIE 
- 網站：https://insights.sustainability.google/?hl=zh-TW
- 計算方式說明：https://insights.sustainability.google/methodology
- 推廣影片：案例分享－新北市 https://youtu.be/92ZmNHw_u9g
- 註冊：
    - 20240114 chewei 註冊申請中

文山區，未註冊狀態下網頁提供的資料
- 提供建物總樓地板面積
    - 總樓地板面積：11,200,000 平方公尺 | 共 11,600 座建築物
    - 住宅：64%
    - 非住宅：36%
- 各交通方式佔總行程比例

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d91aaf84f910542187311518e599e392.png)


---

## 提問：可能的應用場景？

1. 為何是文山區  
    - chewei> 因為 2024 chewei 參加文山社區大學籌畫 淨零工作坊活動，邀請民眾、中學生，討論淨零對策，所以想說會不會有一份文山區碳收支地圖，可以當作認識目前碳收支概況
        - ┃永續街區┃綠運具┃綠消費┃低碳飲食┃ https://maps.app.goo.gl/3GkjpfXQRFosMjCRA

<iframe src="https://www.google.com/maps/d/u/0/embed?mid=1_cZYRmxBvPc3Uh_v0ihe8QscrDThoJY&ehbc=2E312F" width=100% height="480"></iframe>

2. 日後需要碳收支圖資（地圖）的機關/民間單位
    - chewei> 鄉鎮市區 我覺得是一個適合的對象
        - 基於「地方創生政策」、「自治體投票」、「代議者的選區」、「縣市社區大學的設立與辦學地理範圍也會參考鄉鎮區架構」等

---

# 2024 文山區淨零工作坊活動內容延伸相關資料與議題探討

## 2024 活動回顧

文山社大辦淨零工作坊 12歲～60多歲居民共商在地氣候解方
https://e-info.org.tw/node/238846

氣候治理因地制宜 文山區25年公民參與經驗值得借鏡
https://e-info.org.tw/node/238845


## 文山區地景變遷與環境特點

臺北文山地區百餘年來的發展與變遷
https://photos.app.goo.gl/19Ux5KgFfdQXJ2t19

萬芳地區環境特質
https://www.facebook.com/share/p/fMjDjQdpdP2Rh9XR/?mibextid=WC7FNe

民間團體保育文山區 378 坪山林土地
https://www.facebook.com/share/p/y6cnmXXnSUdPzhFi/?mibextid=WC7FNe

大文山地區 保儀大夫
https://www.facebook.com/share/p/Km7DWQrAmJZuW53L/

安康社區與越南族裔
https://www.facebook.com/share/p/2fTWeVPwRaQ3R1vU/
https://www.facebook.com/share/p/xRr41hghriP5Mnmp/

政治大學周邊商圈現況，影片
https://youtu.be/Qwmw0jWqtA0?si=A7F02VTm0x6uHJlO

文山區參與式預算提案點
https://pb.taipei/cp.aspx?n=2E567C53BBB9D0AE
https://canet.civil.taipei/TP105-1/PartiBudget/index_111.html?town=zs

文山社大辦淨零工作坊 12歲～60多歲居民共商在地氣候解方
https://e-info.org.tw/node/238846

氣候治理因地制宜 文山區25年公民參與經驗值得借鏡
https://e-info.org.tw/node/238845


## 機構

政大?

世新大學永續報告書
https://canopi.tw/esgcase/

中國科大

## 綠運具

郭佩棻 副教授 （國立成功大學測量及空間資訊學系）講題：多時空角度的交通需求預測（multi-scale spatio-temporal prediction of transportation demand）
https://www.facebook.com/asgis/posts/pfbid0vMozr8NjTgLcQixJSiDg4FLFFn1hTpNAwzZpUL1sEDMDTjVJg6yS6z9i6kBTJMkUl

深坑輕軌
https://www.dorts.ntpc.gov.tw/news/conventionInfo/MVamXM4l28rj?page=1

加油站提供電動汽車快速充電服務之最佳選址分布 研究–以臺北市為例 A Study on Optimal Siting of Electric Vehicle Fast Charging at Existing Gas Stations – A Case Study of Taipei City
https://www.facebook.com/DENDoENergy/posts/pfbid0ucZ1wksMzmbCJSbPG4dtHX1CG4x1TLyqRFKcZdXiLFKAXLsDZCoiyxTTHK6Bq9sXl
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2fa9d1bad3c0739d1dead151a351e6aa.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9341ec877a16ea7690b677674bfe7515.png)

針對電動車停車場、儲能設備 火災風險
https://youtu.be/b5fB1SNQ-pQ
防災，深坑火災
https://www.facebook.com/share/p/KrHqjhZh1bF2mtM1/

大台北公車路線
https://www.facebook.com/share/p/ERatswAqs7XNpfJE/

行政院「行人交通安全設施條例」草案，說明簡報，以景興路興隆路一帶作為示範說明地區
https://www.ey.gov.tw/Page/9277F759E41CCD91/da325d4d-bafa-40fb-8e9e-eb00c8ff268d

youbike
https://www.facebook.com/share/p/CV1ohsHKg4F15XJQ/
天氣、都市綠地特徵與公共自行車使用之關聯性
- https://photos.app.goo.gl/g2tt3hYvDZw37ouk7
- 研究結果發現，站點周邊綠地面積與假日較平日增加之租借量呈現顯著正相關，代表站點周邊的綠地面積越多，假日增加的公共自行車租借量會越高。
- 此說明了若妥善規劃站點周邊的綠地分布，可以增加假日的自行車使用者數量。
- 此外，站點周邊與行經路段周邊的綠蔭條件皆與受熱天影響而租借量的減少呈顯著負相關，亦即當路段的綠蔭條件越佳，其租借量較不會受天氣炎熱影響而降低。
- 同時也說明若能增進行道樹之分布密度，建立舒適涼爽的騎乘環境，將可提升熱天時的公共自行車租借量。
- 因此，未來規劃自行車相關政策時，也可著重於都市綠地的規劃設計，以改善使用者的騎乘環境條件，並推廣綠色運具之使用。

路面充電線路
https://www.facebook.com/share/v/j96xGjabVkNKUfhf/

## 運動與休閒

https://docs.google.com/forms/d/e/1FAIpQLScQRslpUWnDUyNiB4P1uqwtz8rQU4z7nM_by0LlyugXJn1sWg/formResponse


## 綠消費與生活

計算工具：
環境部-事業溫室氣體排放量資訊平台、產品碳足跡資訊網
經濟部-碳排金好算、碳排乎你知(服務業)
https://moda.gov.tw/digital-affairs/democracy-network/operations/6625

氣候變遷與永續生活調查暨網路輿情分析報告
https://www.facebook.com/share/p/EQFQNoqnKqqthGkK/

產品碳足跡標籤
https://www.facebook.com/share/p/8rud26c3DuthGJBo/

書本 的碳足跡
https://www.facebook.com/story.php?story_fbid=pfbid09DbRZqtbrnCSXQv11T2Zuhd9XBCAao8JKyrVsnAhv9nsLcE2WGWNt8dA4oT4EvZkl&id=100080067891410

龍山寺 不燒香
https://www.facebook.com/share/p/4qx4na8FtbKxqxg9/

都市蚓農
https://recycledoit.com/doitbox.html

## 低碳飲食

關於低碳飲食，分享美國規劃界近年建構的 Food System Planning 研究方法，以下有各國案例與參考架構
https://g0v.hackmd.io/@chewei/Urban-Agri/https%3A%2F%2Fg0v.hackmd.io%2FskGo9n_eSDWyhS9VHJgR9Q

------------------------------
案例：美國大費城地區採用相關方法的政策文件
- 大費城地區食物系統【研究成果】2010
- 大費城地區食物系統【全市行動計畫】2011 Eating Here: The Greater Philadelphia Food System Plan
- 地區層級的食物系統【地區行動計畫】2015 Cultivating Camden: The City's Food Economy Strategy 
https://docs.google.com/presentation/d/1rJBbNrMqwZ4zNmLKl5d7wymVaTraKaBV5juR6PMLFks/edit

-----------------------
國內：永續都市的代謝分析、評估與管理-都市食物系統與空間變遷分析：物質流與生態系統服務功能評估之整合應用

本計畫以大台北地區為探討範圍
第一年：https://www.grb.gov.tw/search/planDetail?id=3116530
第二年：https://www.grb.gov.tw/search/planDetail?id=8359173
第三年：https://www.grb.gov.tw/search/planDetail?id=11585282
結論與建議
- 大台北地區目前廚餘處理情形並不理想，除了養豬廚餘收集後餵豬外，台北 市於廚餘收集後以暫放於內湖、北投、木柵等三座焚化廠進行堆肥化處理為 主；而新北市則有暫放焚化廠、自有堆肥廠、委外堆肥、跨行政區處理等不 同處理方式，均未能有效資源化處理。
- 為尋求將廚餘資源化處理，2011 年起新北市環保局配合環保署政策，曾規劃 「北部地區廚餘厭氧消化試辦計畫」，期能對廚餘厭氧消化處理技術做可行性 及效益評估，但執行後卻被環保署中斷試辦計畫。
- 台北市目前年廚餘收集量約為 66,288 公噸（2014 年），自 2011 年後有下降之 趨勢；新北市目前年廚餘收集量約為 134,929 公噸（2014 年），也是自 2011 年後有下降之趨勢。
- 在估算廚餘產生量上，成分推估法優於人均值推估法。
- 若以成分推估法計算台北市廚餘產生量約為 156,406 公噸（2014 年），而目前 實際收集量為 66,287.6 公噸，因此廚餘收集處理率為 42.38 ％，即約有 57.62 ％的廚餘未進行分類收集處理。
- 若以成分推估法計算新北市廚餘產生量約為 258,248.1 公噸（2014 年），而目 前實際收集量為 134,928.6 公噸，因此廚餘收集處理率為 52.24 ％，即約有 47.76 ％的廚餘未進行分類收集處理。
- 透過本研究分析，不論是廚餘產生量或是廚餘收集量和社經指標之關連性並不顯著。
- 本研究透過分析層級程序法（Analytic Hierarchy Process，AHP）收集各界對 於不同廚餘處理方式之意見，完成 18 份有效問卷之調查，彙整各方意見。
- 評估構面以環境為主（0.545）、經濟次之（0.235），社會（0.220）其次。環 境評估指標部份包含能資源消耗、二次污染、減碳效益、資源回收率、處理 效率，其中以二次污染選項（0.350）最重要。
- 經濟評估指標部份包含土地使用成本、工程建設成本、操作處理成本、維護 與其他成本、資源化產品之經濟效益，不若其他構面和評估指標有較一致的 意見，重要性排序由大到小分別為工程建設成本（0.249）、操作處理成本 （0.240）、資源化產品之經濟效益（0.230）、維護與其他成本（0.185）、土地 使用成本（0.096）。
- 社會評估指標部份包含鄰避效應、民眾分類回收行為、科技穩定性、法規限 制、跨世代正義，可知以鄰避效應（0.349）選項為主，廚餘處理設施常受鄰 近居民所排斥進而影響其作業，如何使處理方案不影響周圍居民就成為了最 重要的社會考量因素；其次為科技穩定性（0.212）。
- 而在不同廚餘處理方案評分上，結果顯示最佳方案依序為厭氧消化（6.12）、 區內堆肥化（5.71）、區內乾燥飼料化（5.47）、區外堆肥化（4.94）、區外乾 燥料化（4.85）。
- 本研究完成大台北地區食物系統氮與磷消費量分析，可發現，大台北地區肉 類人均值消費量呈現上升趨勢，民國 70-87 年間上升趨勢較大，87 年以後上 升趨勢趨緩；而大台北地區人均氮消費總量則在 86 年和 87 年間出現反折， 開始出現下降趨勢。進一步分析，可發現可能和奶類、豆類和蛋類之人均值 消費量下降有關。本研究研究也同時發現人均值之牛肉消耗量有逐漸增加之 趨勢。
- 另可發現，大台北地區人均磷之消費量也是從民國 86 年附近開始呈現下降趨 勢，和人均值之總體肉類消費量不同。而此種消費趨勢似乎跟大台北地區豆 類、蛋類、和奶類人均值消費量之變化趨勢有關。豆類人均值消費量從 86 年之後開始下降趨緩，而蛋類更是從民國 86 年後出現明顯之轉折下降趨勢； 而奶類之人均值消費量大抵在 86-90 年呈現水平狀態，而 90 年以後就呈現下 降趨勢。
- 本研究亦進行人均氮消費量以及人均磷消費量與社會經濟指標進行分析，可 以發現相關性並不顯著。
- 本研究進行廚餘處理技術之生命週期評估，發現廚餘與下水道污泥厭氧共消 化系統除了可以產生淨能源收益，以及磷資源回收，同時比其將廚餘直接焚 化處理可以產生更佳之溫室氣體減排效益。
- 而在廚餘與下水道污泥厭氧共消化系統之發酵後污泥後續操作處理方案中， 若同時考量淨能源收益、溫室氣體減排效益、以及磷資源回收，則以堆肥化 處理最佳。
- 日本目前已有許多實際運轉之廚餘與下水道污泥厭氧共消化系統，廚餘資源 化處理效率佳。
- 分析比較不同國家平均每人每日食品廢棄物之產生量，約為 0.296-0.964 公 斤，其中瑞典人產出最少，而法國人產出最多。而其中家庭廚餘之每人每日 產出量為 0.029-0.663 公斤，其中瑞典人產出最少，而法國人產出最多。
- 本研究發現台北市每人每日家庭廚餘產生量為 0.157 公斤，略少於日本（0.230 公斤）與德國（0.224 公斤）。

## 水綠環境

指南溪護岸改造
https://heo.gov.taipei/cp.aspx?n=165C129DDE416166

水利處目前針對 新店溪與景美溪匯流口推動方案
https://heo.gov.taipei/News_Content.aspx?n=1C35353E4DE6D317&sms=59AD6E6606F6002F&s=4E07DFE2483A75C1
https://www.geo.gov.taipei/News_Content.aspx?n=1C2986DF71D12359&sms=59AD6E6606F6002F&s=ABE1067A729466B3

## 文山區萬和里情境

萬和里 參考
https://www.facebook.com/story.php?story_fbid=pfbid02EeEFhSwYRQjgFVyxqP33J7cxyCiXVaSM5tbeCAyjDm765XnnGCEqBhZMBcVM9f5rl&id=100000432932151&mibextid=WC7FNe

## 20240502 公民週活動籌備討論

籌辦討論文件
https://docs.google.com/presentation/d/1So9YIE00FmW6H1eENEVUIX4N2uyTMfGnDkdvzJSrNvs/edit

公眾的角度
- 市府已有臺北市淨零自治條例
    - 有明確列出局處業務
    - https://g0v.hackmd.io/EwoH0T7qR6a42dOyl_9EXg
- 從「排放量」找大戶
- 論壇中指認的「受衝擊對象」
- 公有建築與場域
- 市政府已推動熱島降溫政策措施
    - 2011-2020年夏季(6-9月)盛行風風向 (參考文獻：台北盆地的夏季風紋與溫度分佈初探，作者：石婉瑜、陳品瑜)，可以瞭解大致風向
- 公害改善、減災 = 減碳

類似：
- 文山好行
- 文山淨零


## 其他地區機制參考

日本地域ストックマネジメント／脱炭素地域戦略研究（opossum）
https://www.facebook.com/opossum.chiba

宜蘭 J-Path 宜路有你
https://www.facebook.com/Yilan.J.Path