---
tags: GCAA, 透明足跡, ESG
---
# 2023-10 定期討論

本文以 CC-BY-4.0 授權釋出

- 會議網址：https://meet.google.com/skq-hymk-zzg
- 台灣時間每週五 14:00



## 2023-10-27
- 簽到
     - 乾
     - ddio
     - ning
     - vivi     - 
- 討論
    - 確認測試內容與前台調整
    - 志工招募流程
        1. 目前綠盟因時程規劃，會採有PAY的方式處理，也就是招募工讀生執行
            - 目前不會對外廣招，會先從過去熟識的志工來找。（預計是在 11月中+底）
            - 想要年底有一些行動，所以在那之前要判讀完報告書
        3. 需要收集的總本數為：328本（兩個年度）
           - 2022 優先，有錢再 2021
           - 招募說明預計十一月中
        5. 主要需講解的部分：
           - 空值處理
             - -> NA?
           - 關鍵字使用
           - 其他部分，介面都算清楚，但還是需要帶準備上工的人過一次報告書。
  - beta feedback
    - 資料總管（乾）填一本時間 ~ 30 mins（填完一本的話是半小時喔）
    - UI 上說明清楚
    - 需要追蹤哪些數據？（ning）
        - metrics 
            - totoal processing time by one document
            - accuracy
            - active duration by per visiting (retention),
            - skipped items
            - most revised items (optional)
            - TBD + 訪談項目：易用性、介面理解度、流程體驗、繼續採用
    - 報告書會先分好各自的範圍（乾）
  - ODP 徵件
    - [貢獻度分數討論](https://docs.google.com/spreadsheets/d/1mddVBuxJeTQ7I5cS_tyDEff2ZcC6Vuv1R_MclnwGP_c/edit#gid=0)

### 前台介面[測試](https://gcaa-org-tw.github.io/company-report-toolkit/)

- [name=乾] 
    1. (已改)再生能源發電量、是否標明廢棄物項目，預設的關鍵字重複了。
    2. (已改)身障聘用的說明不對
       > [name=ddio]請協助修改[這個試算表](https://docs.google.com/spreadsheets/d/1Ypq8uVsJoU4RhB4shdCrygKmk6Hm_OcqNR5QbBb5bSQ/edit#gid=0)
    3. 題目順序，目前好像有多個位置不對。（水資源、人力等部分）。
       > [name=ddio] 請截圖～不確定「位置不對」的意思是什麼
       > [name=乾] ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_94a7cb24615851c2675b18ca520aa338.png) 舉例來說，排放密集度跟內部碳定價有無被擠到**取水量-地下水**後面了，但本來的位置應該接在**範疇六**之後
       > 另外一個比較混雜得比較多的 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f9257e5f29f9117d9683255acc1aab91.png) **取水量-其他來源**掉到廢棄物後面，然後**正式人員**掉到了**原民聘用人數**後面
       > [name=ddio] 題目要照順序
    4. 題目的部分，希望可以固定，不要被捲動影響，這樣可以減少回頭確認題目多花的時間。
       > 欄位名稱 + 說明要黏在置頂
       > 填寫判讀結果 + 驗證也要黏在下方 & accordion
    6. 填完之後不會自動跳回選擇報告書頁面～會循環回到第一題。
    7. 沒有單位的題目，還是要填單位才能儲存，這個部分對於剛開始用的人可能會有點困惑。
    8. 每填一題都會跳回PDF第一頁，在操作上不方便連續填答，是否可設計成切換題目時依然停留在最後瀏覽的頁面？
        - 或者是讓同群的題目可以一次性出現（這個應該比較困難？）
        > [name=ddio] 
        > 要先定義什麼是「同群」
        > 可以先處理維持頁數
        > [name=乾] 同群的部分，可以在所有收集欄位的試算表來處理，但若**維持頁數**較好處理，則以PDF這邊優先進行。
        > 之所以希望同群的題目一起出現是因為志工有反饋，這樣單位不用重新複製，可以一次性貼上，但接下來單位若會做進一步處理，則可解決單位問題。
    9. 若是沒有單位的題目，是否可以直接鎖住單位那格？ +1
       > [name=ddio] 下個 [milestone](https://github.com/gcaa-org-tw/company-report-toolkit/issues/32) 處理
    10. 目前看起來沒有紀錄已經填過的選項，這個部分在之後的版本會怎麼處理？
        > 舉例來說，重複進到同一個題目的話，不會顯示已經填答的資訊。（應該是要反向API讀取資料？）
        > [name=ddio] 應該要顯示原本已經填的答案
- [name=vivi]
    - 是否該增加 “查無資料”的選項？
        - 目前只要是沒有資料都是填"NA"
        - [name=ddio] 給大家選項選
- [name=ning]
    1. 頁數不同步，建議搜尋頁數 (頁232)> 文件總頁數 (共 228 頁) 
        ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9deb983a605a39d305d92ba6e3d19193.png)
- [name=ddio] 寫一下還能做的小改善
  1. 產業列表頁
     1. 依照填答狀態過濾
  1. 資料初始化、純工程調整
     1. seed w/ transaction to speedup
  1. 欄位判讀頁 
     1. 允許大家定義「第一頁」，因為 PDF 頁次和實際頁碼不同 -> 變成使用者的第一個任務，已點選該頁次來記錄本次任務之「P1」
     1. random scroll on pdf init 
     1. 整本報告書填答完畢、單一欄位填答完畢的 UI 回饋

### 待做整理

1. 判讀頁
   1. 更新[欄位說明](https://docs.google.com/spreadsheets/d/1Ypq8uVsJoU4RhB4shdCrygKmk6Hm_OcqNR5QbBb5bSQ/edit#gid=0)
   3. 填答後的回饋、整本報告書完成的回饋
   4. 切換題目時，維持報告書縮放、頁次
   4. 設定地一頁
   4. control panel
      1. 欄位標題 + 說明置頂
      2. 填答、驗證欄預設置底，可收摺
      3. 依照欄位順序排序   
      5. 顯示已填的數值
      6. `bug` 搜尋結果超過總頁數，例如[這個](https://gcaa-org-tw.github.io/company-report-toolkit/profession/editor/166/11127)
2. 報告詳情頁
   1. 依照欄位順序排序


## 2023-10-20
- 簽到
     - ddio
     - Ning
     - 乾
     - jojo
     - vivi
     - othsueh
- 討論
    - Hypercert 接下來要做什麼？
      - [10/19 訪談](https://g0v.hackmd.io/BX__uJCdSJOKImAcY0-_xQ#2023-10-19-%E8%A8%AA%E8%AB%87)
      - 大家都要開錢包！ [Zoey 推推 Blocoto](https://www.rayskyinvest.com/51697/what-is-blocto
)
      - [貢獻度分數更新](https://docs.google.com/spreadsheets/d/1mddVBuxJeTQ7I5cS_tyDEff2ZcC6Vuv1R_MclnwGP_c/edit#gid=0)
    - 本週[測試版網站](https://hackmd.io/@chengh/SkYHa65nO/https%3A%2F%2Fg0v.hackmd.io%2F%40ddio-io%2Fopen-csr-report%2F)進度～
      - API 快做完啦～～
    - 專業工人 報告書、進度表、閱讀器 UI [wireframe](https://www.figma.com/file/hjoPFNjKp7GUDh6CRHfDr7/ESG-flow-UI-wireframe?type=design&node-id=25-475&mode=design&t=JzyWLsj4BavGr55u-0)
    - 後續報告書閱讀器驗證分析
        - 過往志工+新訓練志工+總管
        - 組內比較：作業時間、資料品質準確度、流程體驗...
        - 主要目的：了解前端介面，確認是否有幫助，幫助在哪裡，以及有什麼可以改進的地方
        - 研究方法：是否要強制大家必須以［直接閱讀報告書來收集資料］？
        - 接下來要找志工的時候，可以跟ning一起討論
        - 乾：下週（10/27）給大家一個志工招募流程的設計，一起討論修改～
- 其他
  - 第一次估任務貢獻度估兩輪！
    - 任務：設計專業工人的招募、判讀、成效驗證的流程
    - 兩輪紀錄：
      > ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6b780902fa84ba8f8398e24781f8c841.png)
    - 第一輪釐清差異，例如規劃是草稿，還是包含討論 + 調整
    - 第二輪曲中位數

## 2023-10-13

- 簽到
  - ddio
  - ning
  - 乾
- 討論
  - 專業志工版進度討論
    - [Github issue](https://github.com/gcaa-org-tw/company-report-toolkit/milestones)
  - ODP 徵件
    - [貢獻度分數討論](https://docs.google.com/spreadsheets/d/1mddVBuxJeTQ7I5cS_tyDEff2ZcC6Vuv1R_MclnwGP_c/edit#gid=0)
  - 大松
    - 誰會來？
    - 找大家來做什麼？
      - 先以第一個 UI 來做易用/理解測試
      - 工程師
    - 隨手生個 logo XD [name=ddio]
      - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6066dec8d778ebc3d18a7f74d906cf8b.png)


{%hackmd tKv-yMkzT666mWqARQizEA %}