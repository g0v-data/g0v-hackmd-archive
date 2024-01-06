---
tags: GCAA, 透明足跡, ESG
---
# 開放企業永續資料庫 x 開源普渡黑客松

本文以 CC-BY-4.0 授權釋出

💡 [專案來龍去脈、詳細介紹請點我](https://g0v.hackmd.io/K_N6QOg1QgC8lMneeJqdEg)

[本次提案簡報](https://docs.google.com/presentation/d/17UZOjEWXwNjMWzsyd4H4__Tx4DQWfnffxaTzF_GBoek/edit?usp=sharing)


https://gcaa-org-tw.github.io/company-report-toolkit/")

## 今天想做的事：

1. **對工人智慧、ESG、企業淨零轉型有興趣的人** ，一起來試玩尖端工人智慧原型吧！
   - 請用筆電、桌機、平板的大螢幕開啟： https://github.com/gcaa-org-tw/company-report-toolkit/
   - 走完至少一次流程、填寫問卷
   - 歡迎來找我們聊聊心得
2. **前端工程師**，打造順順的 PDF 閱讀器以及各種酷酷 UI
3. **UX 設計師**，理出順順的工人智慧、群眾外包流程
4. **UI 設計師**，幫 PDF 閱讀器找到最棒的排版
5. **AI 專家**， 訓練出能夠幫忙讀懂永續報告書的機器人

## 今天會用到的資源

1. [專案共筆](https://g0v.hackmd.io/@ddio-io/open-csr-report)
2. [Github 程式碼](https://github.com/gcaa-org-tw/company-report-toolkit/)
3. [CC0 釋出的工人智慧資料](https://airtable.com/appsREnwMpxAZmaRv/shrhubstEzdWYZWfh)

## 本日貢獻者簽到

- 原型測試、使用體驗回饋：ooo1, Stanley, nick, vivi, 波, 宥, ddio, Ryno, Ning, Oliver, 百變怪, yoga
  - 54 筆填答紀錄，154 筆驗證紀錄，18 筆驗證通過（ 33% 達成率！）
  - 本日貢獻前三名： ooo, oliver, 宥
  - 使用者回饋 & 分析 - Ning
- 技術 POC： Tim - [natural lang. search over vector DB](https://github.com/wittenator/ESGDocQuickNavigation)

## 本日討論紀錄

### 觀察到的現象

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_87762aad45fe264cf87f26afbde38bfb.png)

1. 不知道關鍵字可以按
2. 想要直接跳到某頁、想要按頁面上的頁次超連結
3. 通常會想要看最後一年的資料
4. 如果有關鍵字、答案連結夠強的欄位，可以直接把命中的頁面列出來，給大家看，不用自己點
5. 驗證時，給出答案的頁次
6. 要看欄位資料型態，決定要不要顯示：
   1. 文字方塊、核取鈕
   2. 單位欄位
7. 年份溝通容易誤解，之後可以統一用資料年份，而不是報告書出版年份

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_446bf55fc21382e4f1539e1d9dd6617f.png)

### Ux 觀察 (raw note)：
- 閱讀器輸入，與閱讀UI不清楚
- 關鍵字搜尋部分
    - 不知道關鍵字可以點
    - 新手難以理解能搜尋關鍵字 -> 可由 UI 提示優化
    - 報告年份不清楚
    - 左上角關鍵字部分提示若缺少背景知識，難以理解搜尋查找什麼（例如，不確定是群創與否，以為報告書是包含更多間。於事使用者輸入「群創離職」）

-驗證 flow
 - 沒有意識到驗證區有「頁數」可以查詢
 - 意識到有頁數後，詢問可以怎麼在驗證時直接跳頁數
- 填寫有無的關鍵字欄位，不確定要填什麼

https://gcaa-org-tw.github.io/company-report-toolkit/

## 使用者回饋問卷：
- 75% 為過往並未積極關注 ESG 相關議題
- 新手使用者相關背景知識較少
- 針對 ESG 資料庫閱讀器，哪些部分讓使用者困惑
    - #需要更多關鍵字描述/背景知識
    - #關鍵字輸入區塊 UI
    - #閱讀器使用體驗 = 跳頁數、關鍵字顯示
    - #無法修改驗證數字


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5e54cf0532ff1e42434295b0f9af7892.png)


{%hackmd tKv-yMkzT666mWqARQizEA %}