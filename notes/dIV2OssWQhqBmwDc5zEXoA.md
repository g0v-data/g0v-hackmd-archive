---
tags: 吉祥物
---

# 吉祥物 - 工作事項

:::warning
工作事項目錄
[TOC]
:::
:::warning
吉祥物專案資料夾
- [共用資料夾](https://drive.google.com/drive/folders/1c7AdM6U9iX24XYo8prxWizLKo9VjHG-T?usp=sharing)
- [簡報](https://docs.google.com/presentation/d/1AE_A5Yjvo3lXi9Hjwx_fxf0B3wALLtQWElGNRXlU0F0/edit?usp=sharing)
:::

## 一、專案基礎建設

### 本專案的共筆文件使用 HackMD
- 2023 HackMD 簡介文字
    - 跳坑：cai, chewei
    - 80 個字，放在共筆目錄 yaml 區的 description 
        - 試寫1：熊讚、貓裏喵、高通通..台灣吉祥物角色大蒐集，超過 1300 個台灣吉祥物角色基本資料，並標記角色原型標籤，適合吉祥物角色設計師參考評估，歡迎瀏覽與加入專案開發。
        - 試寫2：
        - 試寫3：
    - [HackMD 書本模式的 SEO 措施](https://g0v-slack-archive.g0v.ronny.tw/index/channel/CBLASC4CF/2022-11#ts-1669793048.407979)　
- 先列出，待討論
    - 要不要申請一個 g0v.hackmd Team Name
        - 申請說明 https://g0v.hackmd.io/zNfe2MGfTrWo_5GZI0E5pQ
        - 好處：
            - 目前共筆整合網址 https://g0v.hackmd.io/@chewei/actor/
            - 可以讓網址改成 https://g0v.hackmd.io/@自訂名稱/xxxxx/

### 本專案的公開聊天頻道 g0v slack

- 主要工作討論：g0v slack #吉祥物資料蒐集_マスコット_mascot
- FB 社團
    - FB 社團：https://www.facebook.com/groups/621830738607724
        - 不定期同步貼一些分享圖文
    - 其他相近主題的 FB 社團，可以轉貼至該社團
        - https://www.facebook.com/groups/307358649974488

### 本專案 Google 共用資料夾
- 存放內容：
    - 專案簡報
    - 政府標案招標文件
    - 參考資料
- 網址：
    - https://drive.google.com/drive/folders/1c7AdM6U9iX24XYo8prxWizLKo9VjHG-T?usp=sharing


## 二、「吉祥物資料彙整」與「前端試作」

### 由 tmonk 建置 wiki 平台
- wiki 頁面：https://mascots.tmonk.tw/doku.php
- 跳坑：tmonk 

### 用 Airtable 蒐集吉祥物名冊資料 
- 工作頁面：https://g0v.hackmd.io/BVoegE1HRSWaohXMlKVcbQ
- 共筆者簽到：cai, chewei
- 工作：
    - :bulb: 持續標註吉祥物形象靈感標籤，看看最常見的設計靈感排行榜，例如：水滴、黑熊、白熊、藍熊、泰迪熊與玩偶熊、機械體、人類、擬人。
    - 已建立一個 table，並放入吉祥物相關的碩博士論文、grb 政府研究網相關研究、較深入的專題報導等探討
    - 預計在 airtable 中加入一個「決標標案」的 table 分頁
        - (1) 用手工方式把「標案名稱中包含吉祥物這個關鍵詞」的標案，手動貼到 airtable
        - (2) 標案本身的欄位，決標金額、決標年度，發包機關
        - (3) 並嘗試標記「airtable 已建檔的吉祥物」與「決標標案」的關聯，感覺應該不容易，因為標案階段通常都還沒有吉祥物名稱 ... 可能先從發包機關去對對看 
    - 2023 開啟「Airtable 地圖功能」
        - 190 個角色有標記經緯度
        - 地圖網址：https://airtable.com/shrrJgYSjeLnJEzF6/tblQwomVU4s7HYYYG/viwIvvM50tfXBrYfy?backgroundColor=red&blocks=blif6wMJcUiNWOs5t&bip=full
    - 2023 針對 Airtable 免費版限制，釐清短期因應方式
        - 跳坑：chewei
        - 短期方案：2 月初，開好空白資料列與 table，以供日後持續編修
            - 既有 table 開設未來要使用的資料列數量* (例如角色 table 目前已有 1375 個資料列，所以建議再開設 1500 個空白資料列)
            - 先開設「空白 table 以及其資料列」*(例如先新增 5 個 table，且每個 table 開設 1000 個資料列)
            - 以此方案運作 1-2 年
            - 預計 2023.02.xx 務必一定要完成上述短期方案事項！ 
        - 長期
            - 方向ㄧ：招募跳坑建立自行管理的資料庫，如採用開源版方案
                - 優點：
                    - 不會受制於 Airtable 的商業公司政策變化
                - 課題：
                    - 若無法招募開發人力、系統維護管理人力，則資料彙整工作難以進行
            - 方向二：採用 airtable 付費方案價格
                - 優點：
                    - 既有的 資料蒐集與標記工作流程 不變
                    - 既有的 專案網址 不變
                - 課題：
                    - 開始產生 年度費用，且需長期估計經費
                    - 若採用專案募款，需著手相關募款方案與金流管理
                    - 仍受制於 Airtable 的商業公司政策變化
            - 方向三：尋找 其他資料庫服務

### Polymer 資料網頁化工具
- [前端查找介面 polymer 🔍](https://app.polymersearch.com/cai/mascot/)
- 待確認 polymer 能否資料同步更新？

### Airtable 2 GoogleSheet 2 Sheet2site
- 跳坑：chewei
- Sheet2site 頁面：http://bit.ly/2GkInGT 
- 工作：定期需要檢查一下資料同步環節，Airtable 2 GoogleSheet 這段好像有停止同步
- Issue
    - 資料只能轉出 1000 筆
        - 目前角色資料已超過 1000 筆
        - Couple.io 免費版有限制只能轉 1000 筆，To fetch more than 1,000 rows, please upgrade your plan 


## 三、探討：設計特點、政策探討..等

探討
- [設計方法觀察 📐](https://g0v.hackmd.io/pDPwp3lHQiaqJvDbNxlbAg)
    - 角色設計、角色創建
- [公共政策探討 📝](https://g0v.hackmd.io/GyDvu_USTHiGfRYLY8X1Cw)
    - 課題整理
- [公部門標案關鍵字：吉祥物](https://ronnywang.github.io/pcc-viewer/search.html?query=%E5%90%89%E7%A5%A5%E7%89%A9)

chewei> 陸陸續續把 [hackpad 內容](https://g0v.hackpad.tw/Mascot-nJx0ss5BlC3) 搬到 hackmd，並且拆分成主題頁面，放入 bookmode

## 四、歷來成果發表：專案成果分享影片

https://g0v.hackmd.io/oz9h--rWTSSYhe8ovSs7JA

## 五、參賽：2022 總統盃黑客松 - 籌備工作
- 跳坑簽到：chewei, 
- 共筆文件：[2022 總統盃提案文字](https://g0v.hackmd.io/mLr14VN8TuiIgG6kKByD2A)


## 其他

- CRM

