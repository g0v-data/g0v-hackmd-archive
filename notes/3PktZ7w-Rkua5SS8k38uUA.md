---
tags: edu,幸福存摺
image: https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_323fadc8583f4cdf1fd27f836d081b37.png
---

# 幸福存摺 系統設計


## 流程

https://app.lucidchart.com/invitations/accept/bfd6ca5c-ea01-46a0-86f2-e73c85a978d9
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_24dfdf5c8f078b4e44d285c969695b8d.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f9ef69c3f339fc2fd395c911a210e47f.png)


## 設計方向

欲採用Multi-SAAS的架構，未來可以推廣給其他類似機構。

- 教育機構 Organization
    - 基本資訊 Info
    - 人員 Manager
    - 任務 School Task
        - 類別
            - 贈與型 ex: 上課主動參與
            - 指派型 ex: 活動後，確認是否認真參與活動
            - 任務型 ex: 為期一週的準時進教室
        - 名稱
        - 內容
        - 需申請?
        - 人數上限
        - 截止日
        - subtask checkbox
    - 任務申請 School Task Application
        - （參考國立臺南大學學生學習護照管理系統）
    - 獎勵 School Reward
        - 名稱
        - 內容
        - 所需點數
        - 數量(ex:企業捐贈產品)
    - 學生 School Student
        - 學號
        - 點數總和
    - 學生點數紀錄 School Student Transaction
        - 類別 (任務點數，兌換獎勵紀錄...)
        - 點數
    - 學生任務 School Student Task
        - 狀態
        - 註記
- 學生（未來可跨單位）

可將School改成Company，Student改Person，也許未來可以推廣給其他企業機構提供類似服務？


### 權限

- AppAdmins
- OrgAdmins
- OrgManagers (ex:Teacher)
- [Users]

### 頁面

- 首頁
- 任務
    - 列表
    - 新增
    - 細則
- 獎勵
    - 列表
    - 新增
    - 細則
- 使用者
    - 列表
    - 細則
        - 參與任務
        - 點數紀錄
- 設定
    - 機構資訊
    - 個人帳戶管理
    


## 營運

目前預定採用John擅長的架構 AWS Amplify+ReactJS(ReactNative)，除了開發速度快外，營運費用也低(初期每個月約台幣100)。John會負責提供開發環境與初期營運的費用。

## 原始想法

小草書屋幸福存摺E化

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9961b8038cbeaba997614f15689f88d8.png)
