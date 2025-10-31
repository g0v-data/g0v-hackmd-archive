---
tags: edu, 
---

# 地理資料：全國國小就學人數推估 / 分校分班清單資料 / 歷年廢併校國小清單資料

:::info 方便分享共筆網址

廢校預警 🚨 學校就學人口變化趨勢推測 🏫 校地校舍的未來

工作文件 / 工作事項
https://g0v.hackmd.io/TG6CtrxyRdudWawzTXfPiw?view

GitHub / Dataset 資料集
https://github.com/g0v/small_school_renaissance

展示
https://sites.google.com/view/reschool/

地圖
- 民國 130 年就學人口統計推估地圖 https://g0v.github.io/small_school_renaissance/
- 個案探討地圖 https://maps.app.goo.gl/zrZRjUGzmKQhwhee7

![](https://g0v.hackmd.io/_uploads/rJfCS-OVlxx.jpg)


聯繫我們：
- 專案聯繫信箱：reschool@googlegroups.com
- g0v Slack 頻道 #edu-school-學校存續議題
https://g0v-tw.slack.com/archives/C08NDP85ASF
- FB 社團: 零時小學校 Sch001 學習中心 https://www.facebook.com/groups/240879797438433

討論素材相簿
https://photos.app.goo.gl/AAG1nM1Wc5PKGcsp9

:::

:::warning
文件目錄
[toc]
:::

跳坑：明錡, chewei, yellowsoar, Tiff, 小夏, Tmonk, 蔡阿薛Eden,
總統盃黑客松成員：chewei, yellowsoar, 簡老師, 守傑, Klye, Ronny, 郭博勝, 

專案介紹影片：https://youtu.be/6UyYrYeWFks

<iframe width=100% height="480" src="https://www.youtube.com/embed/6UyYrYeWFks?si=pIkQ82TWTMmDJUJM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## 近期任務

### 專案切入角度

Data 資料清點與清理
- 【歡迎跳坑自己的家鄉縣市】建立「全國分班分校名單」，沒找到全國整批資料，教育部學校代碼也沒有幫分班分校建立代碼
    - 已整理：南投縣、雲林縣、彰化縣 
    - 歡迎跳坑各縣市，請整理於以下 google sheet 「全國分班分校名單」檔案 https://docs.google.com/spreadsheets/d/16AiaOpquE1gm2PaRTNlJkqWZ3vajcGlkvaTjJ2YWRik/edit?gid=1977442313#gid=1977442313
    - 資料用途：
        - 例如 雲林縣口湖鄉縣立文光國小學生總數為 202 人，實際上是由三個地方所加總，文光國小本校校區 + 湖口分校校區 + 過港分校校區，全國就學人口統計數字並沒有提供各分校校區的學生人數
- 歷年已廢校地點
    - 先登載到 Google My Map 
    - 工作文件：https://g0v.hackmd.io/@hackpad-importer/BJ-xeloFsLm
- 學區
    - 學區有鄰界，網路上沒查到 鄰界 GIS
    - 可能要用 門牌 拼湊出來大概的鄰界範圍
        - https://addressrs.moi.gov.tw/address/index.cfm?city_id=64000
- 最小統計分區
    - 基本上還是會跨里界
    - 可能沒辦法乾淨俐落的把 最小統計分區 Grouping 給學區 (里界、鄰界的邊界組合)
- 整理專案執行過程中，所使用到的資料集種類，建立資料及目錄與索引
    - https://docs.google.com/spreadsheets/d/16AiaOpquE1gm2PaRTNlJkqWZ3vajcGlkvaTjJ2YWRik/edit
    - 註明各種資料集是否開放、資料可用度說明 (是否還需要清理、清理重點) 

Population Projection
- 教育部製作_各教育階段學生數預測報告 https://g0v.hackmd.io/nrFF3PNXTEWWtH2HxgxeGw?view


Reform 評估校地與校舍使用
- 災害防救觀點
    - 災害潛勢套疊與研判校地是否安全：
        - 災害潛勢地圖：https://dmap.ncdr.nat.gov.tw/
        - 地形特徵圖：https://atlas.geo.ntnu.edu.tw/
    - 災害種類：土石流潛勢溪流衝擊區
        - 是否評估遷校
        - 案例：新北市猴硐國小遷移
    - 災害種類：水患與易淹水地區
        - 能否進行承洪調適
- 公害迴避觀點
    - 大林蒲 https://dalinpu.kcg.gov.tw/DRP/web_page/index.jsp
- 使用群體：找尋校園用地的辦學團體
    - 走路可以到達台鐵站點的學校
    - 關心學校校舍建物與用地現況
- 使用群體：關心在地發展的人
    - 想針對就學人數較少的學校，校地與校舍空間資源可以釋出再運用，再運用的機能種類評估過程所需要的輔助圖資
    - 日本有案例是高速公路交流道鄰近的學校，可以發揮物流人流可及的區位功能
    - 關心學校校舍建物與用地現況
- 蒐集學校空間轉型使用的案例
    - 蒐集案例，並針對案例進行分類
        - 引入產業或服務業
            - 加工
            - 零售
            - 住宿
            - 再生能源
            - ..等
        - 引入非義務教育的公共服務
            - 但也要評估該服務是否長期要設置在此，或短期間設置在此
        - 環境復育促進：
            - 修護自然生態環境，可以用國土生態綠網的促進地區
            - 因應災害的緩衝區
    - 類別一：仍保留未成年學生的學習機能
        - 名稱發想：幫小校找學伴、半學半Ｘ
        - 找案例
    - 類別二：未使用既有校地，新設實驗教育學校
        - 不老部落原根職校- 原根團體實驗教育 https://www.facebook.com/bulautrvs/
    - 類別三：未保留未成年學生的學習機能
        - 找案例
- 學校的環域分析
    - 要探討學校週邊____公里的範圍，才能反映出前述學校空間轉型使用的評估
        - 例如：再生能源，若要連接至台電饋線，一般來說廠商尚可接受的佈線距離為？超過就視為無饋線可接
        - ..等
    - 記得要一起跨縣市探討
        - 例如：臺南市白河區仙草國民小學關嶺分校坐落的地區，旁邊就是嘉義縣中埔鄉
- 建立評估流程
    - 探討名單，包含以下分類：
        - 縣市政府已決定廢校
        - 縣市政府決定不廢校
        - 縣市政府尚未決定是否廢校
        - 納入原住民族重點學校
        - 上述之外，本專案基於資料分析，預警應納入討論的學校

Connect 累積行動團體網絡名單
- 關注南投偏鄉教育的大學教師
- 鄉育基金 https://www.instagram.com/reel/DDwiYJ4O_Ag/
- 親子天下
- ...等

### 廢校推估與法規

:::info
跳坑：yellowsoar, 明錡
:::

使用學校基本統計資訊資料集，來看各學校的就學人口趨勢，結合法規所列舉的廢校標準，推估可能廢校年份

盤點廢校議題相關法規
- 小學、中學廢校的母法
    - 全國法規資料庫：公立國民小學及國民中學變更或停辦準則
        - https://law.moj.gov.tw/LawClass/LawAll.aspx?pcode=H0070070
    - 教育部主管法規查詢系統：公立國民小學及國民中學變更或停辦準則
        - https://edu.law.moe.gov.tw/LawContent.aspx?id=GL001597
        - 
- 各縣市政府教育部門依據母法所制定的作業辦法/施行細則
- 偏遠地區學校教育發展條例 https://edu.law.moe.gov.tw/LawContent.aspx?id=GL001698
- 原住民族教育法
    - lafin>《原住民族教育法》明確規定，國民教育階段的原住民重點學校在合併或停辦時，必須獲得學區內超過半數成年原住民的書面同意。此項規定體現了對原住民族教育權利和自決權的尊重。原住民重點學校的具體認定標準則由《原住民族教育法施行細則》規定，並根據地理位置（原住民族地區或非原住民族地區）有所不同，且需每三年重新認定。大概就是，如果是原住民重點學校如果要廢校須要經過學區內同意，但如果第三年沒有認定為原住民學校就轉一般學校廢校資格認定這樣。
    
### 廢校與地區轉型發展

:::info
跳坑：chewei,
:::

將已經廢校的名單，整理成資料集
- 已經停辦的學校清單在教育部統計處的學校名錄頁面裡面可以找到資料
    - https://depart.moe.edu.tw/ed4500/News.aspx?n=63F5AB3D02A8BBAC&sms=1FF9979D10DBF9F3
    - 廢校資料集欄位：
        - 廢校年份、經度、緯度 ...
- 相關議題共筆：台灣廢校盤點與再生 https://g0v.hackmd.io/sTanR4YKQNq45GjWinU_yg?view
- 近期執行事項：
    - 詢問教育部為什麼撤站，能否釋出當時的地理資料？
        - 教育部國民中小學 整併後校園空間 活化再生案例，但是主題網站關閉了@_@ http://ssdelt.nhps.tp.edu.tw/
        - 教育部廢校活化網站 撤站之前的樣貌 https://web.archive.org/web/20221206201303/http://ssdelt.nhps.tp.edu.tw/
        - 國教署新聞稿頁面 https://www.edu.tw/News_Content.aspx?n=9E7AC85F1954DDA8&s=7E9E989F1DEFD729
- 資料集用途？
    - 了解過往廢校的地點位置

相關政策
- 產業園區設置
    - 整理個案經驗，園區設置後對於周邊多少範圍的就學人口，如何影響
        - 磁吸
        - 或居住人口有因此移動
- 新市鎮 (但無明確的產業就業人口引入)
    - 例如淡海新市鎮
- 地方創生
- 國土署生活地景框繪結果
- 部落傳統領域、原保地
    - https://www.cip.gov.tw/zh-tw/news/data-list/9A8362871EA0BBFF/7BC58CB745833C26AE9B30328A2228A5-info.html
    - https://gis.ardswc.gov.tw/news/map/303
- 林業事業區 https://www.facebook.com/share/p/16xAHyUTgG/


### 縣市教育治理政策情境

:::info
跳坑：chewei, 
:::

#### 高雄市
- 2025 總統盃黑客松，有開展與 高雄市教育局的交流合作

#### 南投縣
- 預計於 10 月底，chewei 聯繫 張力亞老師
    - https://www.facebook.com/share/p/1FizvRtwo7/

#### 臺南市
- 預計於 10 月底，chewei 聯繫 台南新芽


#### 嘉義縣


#### 雲林縣



---

# File 工作資料夾

:::info
共用資料夾，可以放工作檔案、簡報
https://drive.google.com/drive/folders/15tozJQMI0TLAms9mXgW_BjZYRdl3fWTo
:::

## Slide 簡報

https://docs.google.com/presentation/d/1ayz3C60x4jnEabPkE1-2YZ3el2mVGoKxONKQnRHOHQ0/edit?usp=sharing

## Data 資料集

:::info
GitHub https://github.com/g0v/small_school_renaissance/
:::


全國學校地點資料
- https://g0v.hackmd.io/kb9Sn5u0TZuvWwFbfgt3Hg

歷年各學校就學人口資料
- 學校基本統計資訊1998~2024 https://depart.moe.edu.tw/ed4500/News.aspx?n=5A930C32CC6C3818&page=1&PageSize=40&fbclid=IwY2xjawJKFblleHRuA2FlbQIxMAABHVxw1Je5gUogRsOQl30yL2tXD4xF_lKVfteRKMTqMccMQx6wvBTayeqZXQ_aem_fP4cQl1tMf0siIiACHBClg
- https://depart.moe.edu.tw/ed4500/News_Content.aspx?n=5A930C32CC6C3818&sms=91B3AAE8C6388B96&s=33128143574210DF&fbclid=IwY2xjawJKEohleHRuA2FlbQIxMAABHVxw1Je5gUogRsOQl30yL2tXD4xF_lKVfteRKMTqMccMQx6wvBTayeqZXQ_aem_fP4cQl1tMf0siIiACHBClg

關於「學校代碼」
- https://depart.moe.edu.tw/ed4500/News.aspx?n=63F5AB3D02A8BBAC&sms=1FF9979D10DBF9F3
- 這個頁面裡面也有解釋學校代碼的含義
- 合併的學校會取得新的學校代碼，例如：「原澎湖縣立虎井國小(164612)→澎湖縣立馬公國小虎井分班(164601)」
- 所以看起來學校代碼應該是可以當作 UID 的

原住民族地區
- 盤點原住民族重點小學 csv https://airtable.com/appEy0jH7wgeFfcMY/shrjmzerb0sobb2oY/tblXkKfDdxXyZF61O/viw5fJFBCcmoPcCCu/recXkz9axQ5SY0TdY?blocks=hide
    - 地圖 https://www.google.com/maps/d/u/0/viewer?mid=1XST8W_wgSXo2qa5xP_pQAeENvoVbM7A&ll=24.17340168083134%2C120.11524999999997&z=7

<iframe src="https://www.google.com/maps/d/embed?mid=1XST8W_wgSXo2qa5xP_pQAeENvoVbM7A&ehbc=2E312F" width=100% height="480"></iframe>

- 台灣原住民族部落基礎資料庫(2021年6月) https://airtable.com/appEy0jH7wgeFfcMY/shrjmzerb0sobb2oY/tblXkKfDdxXyZF61O/viw5fJFBCcmoPcCCu/rec9WT7YbVpcnLlBh?blocks=hide
- 教育部公布有關於原住民族學生資料地圖集 https://airtable.com/appEy0jH7wgeFfcMY/shrjmzerb0sobb2oY/tblXkKfDdxXyZF61O/viw5fJFBCcmoPcCCu/recyOUIQrPIHdqgp3?blocks=hide
- 個別學校素材蒐集
    - 花蓮縣萬榮國小，設立超過百年，目前雖然學生只有47名，老師加校長不到10人，但仍持續辦學 https://www.facebook.com/permalink.php?story_fbid=pfbid02e7xjC8o7fvkVZ6tg4hhrcaieeFcLw12JRaPU1pCRrrXFRpoxykor2vZW6F7bT1w8l&id=100051170178681

學區範圍
- 臺北市可以看到的地理圖框 https://schooldistrict.tp.edu.tw/gis/index.jsp?school=%25E9%25BE%258D%25E5%25AE%2589%25E5%259C%258B%25E5%25B0%258F@undefined@undefined
    - 🔥🔥🔥 要趕快爬！今年圖資要下架！「學區查詢系統將於114年8月31日終止服務，造成您的不便，敬請見諒。」
- 臺南市學區
    - http://std.tn.edu.tw/sis/anonyquery/SchoolDistrict.aspx
    - kiang 做的視覺化 - https://tainan.olc.tw/p/school/
        - 以里界來呈現該里界內，涉及到的國中與國小學區

戶籍人口資料
- 社會經濟資料服務平台 https://segis.moi.gov.tw/STATCloud/Index 


# 待整理的資訊

## 偏遠地區相關學術研究

- 偏遠地區國民中小學教育資料建置與教育生態分析研究
    <https://srda.sinica.edu.tw/file/24a4cce9-96be-4257-b6e6-bb988ae7f0be>

- 《強制移住：臺灣高山原住民的分與離》葉高華 著 https://reurl.cc/x6oz4e

## 學校名單

- 原住民族學校
    教育部國民及學前教育署/原住民族教育資訊網/學校名錄(單)
    - 官網： <https://ieiw.k12ea.gov.tw/School/Index>
    - OpenData: <https://data.gov.tw/dataset/162567>
    - 地址+經緯度(google map查詢) <https://docs.google.com/spreadsheets/d/1jv5n7SViMDAH-s91fgd6dQCvuKzBw3VR/edit?usp=sharing&ouid=117409746054058070911&rtpof=true&sd=true>

- 實驗教育學校
    - 學校型態原住民族實驗教育學校名冊
        - 官網： <https://ieiw.k12ea.gov.tw/School/Index>
        - OpenData: <https://data.gov.tw/dataset/162568>

- 非山非市學校名單
    - 教育部國民及學前教育署： <https://www.k12ea.gov.tw/files/common_unit_id/c4faaee2-686f-47b2-9cc3-90be1e7603fb/doc/110至112學年度國民中小學非山非市學校名單.pdf>


