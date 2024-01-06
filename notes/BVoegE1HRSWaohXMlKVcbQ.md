---
tags: 吉祥物
---

# 吉祥物名冊資料集

我們使用 Airtable 表格工具，蒐集吉祥物名冊與基本資料
- 可編輯網址：http://bit.ly/2MR9Jbi 
- 瀏覽網址(資料表+地圖)：https://airtable.com/shrrJgYSjeLnJEzF6
- 地圖瀏覽網址，約 190 個角色已有經緯度定位：https://airtable.com/shrrJgYSjeLnJEzF6/tblQwomVU4s7HYYYG/viwIvvM50tfXBrYfy?backgroundColor=red&blocks=blif6wMJcUiNWOs5t&bip=full
- Airtable API 接資料：
    - https://airtable.com/app6QAKwPzqnJG3PR/api/docs#javascript/introduction
    - 注意事項：The API is limited to 5 requests per second per base. If you exceed this rate, you will receive a 429 status code and will need to wait 30 seconds before subsequent requests will succeed.
    - 其他案例：https://github.com/g0v/summit2020

<iframe class="airtable-embed" src="https://airtable.com/embed/shrrJgYSjeLnJEzF6?backgroundColor=red" frameborder="0" onmousewheel="" width="100%" height="600" style="background: transparent; border: 1px solid #ccc;"></iframe>


---
## 政府公布的資料集
- [身心障礙國民運動會歷屆資料](https://data.gov.tw/dataset/6527)
- [歷屆原住民運動會資料](https://data.gov.tw/dataset/6526)

## 資料庫內容、欄位發想：

### Airtable 已有的欄位：

- 角色基本設定
    - 名稱
    - 身高
    - 體重
    - 生日
    - 角色簡介
    - 所屬企劃或系列（例如：家族、戰隊）
    - 代表圖片網址
- 推動單位與品牌策略
    - 所屬機構
    - 角色創立時間
    - 角色授權方案（例如：原圖採用開放式授權、有條件允許二創商品、原圖與二創皆採用申請審查）
- 形象設計特點
    - 形象設計的標籤（例如：黑熊、石虎、竹筍）
    - 形象是否有 logo
    - 形象是否屬於 地區名產或地區特色景貌
- 座落或關聯的地理位置
    - 縣市
    - 行政區（鄉鎮區）
    - 村里
    - 經度
    - 緯度
- 相關研究或探討
    - 筆記區與補充資料
    - 相關研究/探討/標案

---
### 評估中的標記欄位

#### 地理類欄位，標記原則討論

- 好標，經緯度
    - 博物館、建築物、園區、景點
        - 經緯度標記在該建築園區位置
    - 若是代表特定的鄉鎮區、縣市單位
        - 標記在「區公所、鄉公所、縣市政府所在地」建物位置
            - 例如：高雄市高通通，標在高雄市政府農業局主要辦公室地址
            - 例如：台北市資訊局 230，標在台北市政府資訊局主要辦公室地址
            - 例如：區公所
- 討論中
    - 地區型的交通設施的吉祥物
        - 例如：都市捷運代言角色，可能需要標在營運總部的地址，因為路線路網有點大
            - 高雄捷運
            - 悠遊卡吉祥物
- 不好標
    - 全國型的交通設施吉祥物
        - 案例：台鐵，標在台北的台鐵總部，其實也不是很有代表性
    - 議題推廣型的角色
        - 可能要折衷找一個代表地點來標，或不標記明確地點
        - 例如推廣兒童共融遊樂場的「熊寶」，雖然是可以標在該計畫的推動單位的地址，但似乎沒有地點效果感受
        - 例如疾病擬人、害蟲擬人

#### 角色主要「應用目的」
- 可能要先累積一批標籤類型
    - 這批標籤，至少有一個功能是，協助想要創建角色的單位，可以參考標籤，確認自己創建角色的目的為何，並透過標籤來找到可參考的案例
    - 單一角色的應用目的，採用複選

列舉目的：
- 廣義的觀光行銷
    - 提升館舍門票銷售或參館人次
    - 促銷特色產品
    - 促進縣市鄉鎮區或是地區觀光
- 宣導該單位的業務，這個分類，需要拆分成「相異領域」的選項清單
    - 交通運輸推廣
    - 警政
    - 防災
    - 保育意識
    - ..等等
- 企業吉祥物
    - 職棒、職籃 等
- 縣市吉祥物
    - 業務就比較多元
- 針對單次的活動或是賽事，大會吉祥物
- 國際外交
    - 例如 2019 年由民間中華動漫出版同業協進會舉辦 Mascot Taiwan 吉祥物大賽暨海外拓展計畫
- 陪小朋友打疫苗


#### 角色設定類材料
- Guidebook 角色圖像設定集與應用規範，通常是 PDF 檔案？
    - 釋出狀況如何？
    - 有看過政府標案內提供 Guidebook 文件
        - 案例：[111年桃園市吉祥物維護管理暨品牌合作開發案](https://airtable.com/shrrJgYSjeLnJEzF6/tblbBMrbuRF1VSwuw/viwa78BHKDLbBPfX7/recP9FXb1IatZXdpD?blocks=hide)
- 「角色發音、聲音、聲調」面向的資料
- 「立體服裝版型檔案或文件」面向的資料
- 「公仔設計檔案」面向的資料，例如 3D 模型
- 其他參考：
    - 如何用資料描述一個代言角色？參考：http://schema.org/Person
