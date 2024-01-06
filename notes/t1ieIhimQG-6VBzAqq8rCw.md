---
tags: Disfactory
---

# 違章工廠舉報系統第33次小聚

時間：20200527
地點：地球公民基金會北辦
線上：https://meet.google.com/wwa-hwiw-ukj

## 參與者簽到：
- deeper
- sandra
- 鉦寰
- yellowsoar
- yukaii
- andy
- anthony（線上）
- darren（線上）

## 待討論

- user story 和 feature
    - ael在issue[312](https://github.com/Disfactory/Disfactory/issues/312)列了三個主要的 feature
    - 也算是 Django Admin 需要看到的 View
        1. 審核照片
        2. 自動產生公文
        3. 回復管理
    - 超大的 epic spec 放在[這裡](https://github.com/Disfactory/Disfactory/issues/312)，之後會再把每一個小 task 都切出去開新的 issue 或是說放棄不要做
    
- 前端的部分
    - review imgur 的那個 PR
    - 測試 dev 上面的東西
    - 沒問題的話把座標輸入和 imgur 的改動推到正式版
    - 首頁前端的部分可以開始動工啦～～可以自己先開 issue

- 設計的部分
    - design system製作中
    - 釐清一下後台權限要怎麼切

## 會議記錄
- 和ael在5/22整理的user story（見github issue #[312](https://github.com/Disfactory/Disfactory/issues/312)）
- 和sandra 18:30~19:45又順了一個版本
    - **[後台使用情境](https://docs.google.com/document/d/1uBqD_Ms1-HHAH1B1SCagsVZS_XKMxYDFuQHOHxkJ4_8/edit#) google doc**
- 前端
    - deeper測試完成，可以merge上正式版了
- 跟在場後端工程師再次檢視了一遍spec，並在後台使用情境上修正
    - 主要修正
        - 把生產公文的單獨頁面拿掉。主因在於需求是「修改公文」，那只要公文下載時是odf即可解決。
        - 以URL角度思考feature所需頁面
    - 分feature如下

**1-1. 審查照片、公文下載｜總覽(table view)**
- url: api.disfactory.tw/staff/review_table

| 地公要能看到 | 地公要能做到 |
| -------- | -------- |
| factory_id <br>行政區 (篩選,排序)<br>段名 (篩選,排序)<br>段號 (篩選,排序)<br>地號 <br> lng <br>lat <br>工廠類型 (篩選,排序)<br>others <br>name (篩選)<br>image_path<br>googlemaps_URL<br>檢舉狀態：尚未審查/已審查-不檢舉/已審查-需補件/已審查-待檢舉/已審查-已檢舉 (select、篩選) | 勾選後下載公文檔案或開啟個別工廠(single page)<br>在tableview中按下「批次下載公文」按鈕<br><br>Nice to Have:整張表的內容下載成 csv,xlsx,json,xml|

**1-2 審查照片、公文下載｜個別工廠（single page）**
url:api.disfactory.tw/staff/review_table/[factory_id]/

| 地公要能看到| 地公要能做到 |
| ---------- |---------- |
| 此工廠的基本資料<br>最後更新日期<br>工廠編號<br>地段地址<br>照片<br>工廠類型<br>工廠描述<br>工廠外部文字<br>經緯度<br>此工廠的相關照片<br>照片本人<br>照片上傳者的資訊<br>此工廠地點在2016.5.20的空照圖（google earth）or googlemaps_URL |輸入審查人<br>輸入審查日期（自動）<br>輸入google earth比對成果<br>選擇工廠狀態（照片審查結果）<br>　　已審查-不檢舉<br>　　　　reason（多選一；並在前端自動標記）<br>　　已審查-需補件<br>　　　　reason（多選一；並在前端自動標記）<br>　　已審查-待檢舉<br>　　已審查-已檢舉<br>輸入是否需要特別追蹤<br>　　不需要<br>　　需要，可能為中高污染<br>輸入筆記備註 <br>下載公文按鈕 |

**1-2-1 公文下載功能｜最後決定不用popup**
- 當按了「下載公文」時的動作
    1. 檢舉狀態改為「已審查-已檢舉」
    2. 賦予工廠一個流水號
    3. 把資料轉成 ODF 檔案並提供下載連結
- 公文內容裡需自動填上的欄位（參見issue#[283](https://github.com/Disfactory/Disfactory/issues/283)）
    * 負責人email
    * 日期
    * 文號
    * 行政區
    * 段名
    * 地號
    * 正本受文者：ＸＸ縣市政府
    * 副本受文者：經濟部工業局、經濟部中部辦公室、內政部營建署、行政院農業委員會、ＸＸＸ立法委員國會辦公室
- 批次下載時：生成寄送相關標籤、表格
    * 正本受文者、副本受文者地址標籤
        * 將已勾選的工廠輸出「去重複的」受文者地址成一個 ODF 檔案
        * 規格
            * 單格，長7cm，寬3.82cm
            * 每列，3格
            * 每行，7格
            * 邊界，上1.5cm，下1.45cm
    * 郵局大宗交寄存根、執據
        * [模板檔案](https://www.post.gov.tw/post/download/交寄大宗限時掛號及掛號函件執據存根2聯單（全球資訊網下載檔10404版word）.doc).doc


**2-1 回覆管理｜總覽（table view）**

| 地公要能看到 | 地公要能做到 |
| -------- | -------- | -------- |
| factory_id<br>公文文號<br>行政區、段名、地號<br>公文發送狀態（已檢舉/已排程稽查/已稽查/處理中/已拆除/不再追蹤<br>上次追蹤時間<br>上次回文時間 | filter已經寄出公文<br>sort依上次追蹤時間<br>filter同一個行政區<br>filter同一位承辦|

**2-2 回覆管理｜（single page）**

| 地公要能看到 | 地公要能做到 |
| -------- | -------- | -------- |
| 公文文號<br>工廠編號<br>行政區、段名、地號<br>照片<br>工廠類型<br>回報說明（others） | n/a |
|公文發送狀態（已檢舉/已排程稽查/已稽查/處理中/已拆除/不再追蹤）<br>該建築法律狀態（未登記工廠 / 非工廠違建 / 合法建物）|標記回文狀態<br>　　地方政府回覆狀況-經發單位（還沒回 / 已受理 / 不受理，已轉給其他單位 / 已排程稽查 / 已限期改善 / 已斷水斷電 / 已拆除 / 已確定不處分，轉給其他單位）<br>　　地方政府回覆狀況-建管單位（還沒回 / 已受理 / 已排程稽查 / 已限期改善 / 已排拆 / 已斷水斷電 / 已拆除 / 已確定不處分）<br>　　地方政府回覆狀況-土管單位（還沒回 / 已受理 / 已排程稽查 / 已限期改善 / 已裁罰 / 已裁罰並轉給建管單位 / 已確定無違規）<br>　　地方政府回覆狀況-農政單位（還沒回 / 已受理 / 已排程稽查 / 已稽查 / 已轉給其他單位處分 / 已確定不處分）<br>　　中央代行狀況(中央尚未回應 / 中央排入代行清單)|
|依timeline彙整起來的回覆紀錄（公文+電話）|公文檔案匯集（可 popout）<br>　　上傳公文jpg<br>　　下載公文檔案<br>　　標記負責人<br>新增紀錄<br>　　日期 *2020XXXX*<br>　　類型 *主動追蹤/政府回應*<br>　　回應局處科 *建築管理處使用管理科*<br>　　紀錄（note）<br>　　　　主要內容*ex：公所回文確實是違建，自己沒有去看。將依照違建處理要點開罰。如想要知道他們是倉儲還是工廠，還是要找經濟發展局處理*<br>　　　　次要內容*ex：處理陳情目前只有一個人力，複查頻率就不會這麼高。但目前檢舉案件沒有變多，也沒有到無法負荷。*<br>　　待辦事項<br>修改紀錄|
|預設受文者資訊<br>　　單位<br>　　姓氏<br>　　電話<br>政府承辦清單（當有相關承辦資料後，可以hide預設受文者資訊）<br>　　單位<br>　　姓氏<br>　　電話|新增政府承辦<br>刪除政府承辦|

### 最後
yellowsoar幫忙畫了一張追蹤經發單位進度的flow chart

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_33910c3443fb65204a77ce07436cab87.png)

<iframe frameborder="0" style="width:100%;height:500px;" src="https://app.diagrams.net/?lightbox=1&highlight=0000ff&edit=_blank&layers=1&nav=1&title=Flow.drawio#Uhttps%3A%2F%2Fdrive.google.com%2Fuc%3Fid%3D1e5lltgMEwUugJBBosTvq2n0aCtY2vQ72%26export%3Ddownload"></iframe>

> https://drive.google.com/drive/u/1/folders/1oucSdcboLClB6obQp_xaV7Yv9vs9Yzf0

## 下次待討論事項

- user story現在出現了三個版本，需要統一
- 把後台資料有哪些要在前端呈現抓出來
- 開好spec
