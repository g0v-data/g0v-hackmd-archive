---
tags: g0vernance
---
# g0v 首頁社群治理機制

:::warning
機制建構歷程
- 2023.3.4 基礎松提案討論，並隨後建立三項治理流程 (1) 審核者的加入與退出 (2) 首頁專案輪播 (3) 活動行事曆
- 2024.3.2 Jasmine、Yvonne、宸維，針對官網提出「勘誤需求」與「改動提議」
:::

:::success
文件目錄
[TOC]
:::

## 動機

為了讓 g0v 相關專案，都能透過 g0v 首頁，傳達自己的專案資訊，我們需要一套治理機制，來規範包含治理角色、專案資訊編修。

治理機制將涵蓋：

1. 社群治理的審核者、編輯者的加入與退出
2. 首頁（ https://g0v.tw ）的專案輪播調整
3. 活動行事曆 （ https://g0v.tw/intl/zh-TW/event/ ） 的調整

## 聯絡方式

g0v slack #gov-landing-page 頻道

## 治理機制成員名單

### 編輯者 (2023.3.4)

#### 首頁：

?

#### 行事曆：

- 有編輯權限者：
    - 四個 GoogleGroup：g0v-talks、g0v-intl、g0v-jothon、cofacts
- 「揪松團職工」可主動協助更新日曆內容，新增活動、修改活動內容 ..等

### Reviewer (2023.3.4)

- [Reviewer 清單](https://docs.google.com/spreadsheets/d/18oekxIDN84iPhP7fUYMleV7jmfWpr9UdZuujPFJmTBM/edit#gid=1776966921)
  - ddio
  - Teemo
  - isabelhou
  - tofu
  - 揪松
  - chihao

### 審核者的加入與退出

參考自 [SNS 社群治理](https://g0v.hackmd.io/THKRsDsNRXGsa_0zFUn3Gw)

- 輪播、活動行事曆的修改，都需要經過 review
    - 有一個 reviewer group [[名單]](https://docs.google.com/spreadsheets/d/18oekxIDN84iPhP7fUYMleV7jmfWpr9UdZuujPFJmTBM/edit#gid=1776966921)
        - 目前 9 人 (as of 2023/03/04)
        - 名單公開
        - 加入機制
          - 預設值 g0v-jothon
          - 邀請制，兩人同意就加入
        - 退出機制
          - 逾二次經指派未 review 即踢出
          - 自行要求即可退出
    - 每一個 reviewer 都有這些權限
        - 審閱修改，給出 YES
        - 審閱修改，給出 NO
    - 每則修改隨機指派 2 reviewer
        - 用 Slack bot，或其他自動、手動機制指派、[隨機抽籤](https://aws.ronny.tw/g0v-sns/proxy.php?type=calendar)
        - 紀錄每則修改狀況 [[紀錄]](https://docs.google.com/spreadsheets/d/18oekxIDN84iPhP7fUYMleV7jmfWpr9UdZuujPFJmTBM/edit#gid=1776966921)
    - 審閱期
        - 一般狀況
            - review 24 小時
            - 2 reviewer YES && 0 reviewer NO 就可以發文
- 任何修改通過 review 就需要被發出去
    - 如果發起人是 reviewer，則自行貼文
    - 如果發起人不是 reviewer，則被指定的 reviewer 協調幫忙貼文

## 首頁專案輪播

主要討論文件：g0v 首頁 - 專案介紹的輪播機制
https://g0v.hackmd.io/Q1kxZgObSBihH5ZrHKNiJg?view

## 活動行事曆

### 張貼活動的流程

1. 坑主在 #g0v-landing-page 登記想要辦的活動，提供下列資訊：
    1. 專案資訊：授權方式 + 專案連結（hackmd, website......。）
    2. 活動頻率（每週、每月第幾週等等）
    3. [抽籤出 2 位 reviewer](https://ronny.tw/g0v-sns/?type=calendar)
2. 審查規則：
    1.  在大小松提案
    2.  成果開放授權
3. reviewers 審核通過
   - 2 位 reviewer ++
4. editor 更新 google 行事曆

:::warning
活動內容格式舉例：
- 「OH!SHOWN - 黑熊通報系統定期小聚」舉例
- 活動時段：聚會想要改成從 Feb 8 開始，每個月（每個月的第二個週三）一次
- 活動標題：OH!SHOWN - 黑熊通報系統定期小聚
- 內容欄位：專案共筆 Meeting note https://lihi1.cc/VDemi （聚會線上連結在共筆內）
:::

### 其他討論
- [技術討論文件 github -> google calendar ](https://g0v.hackmd.io/ym6CHeYQS7aVPB1gM-UCUg)


## 官網通報報修類 (流程草案撰寫中)

- 例如 2024.03 已提出 [新手指南區域，「提案小訣竅」、「非資訊人參與指南」連結失效](https://hackmd.io/t97cH7tFQPyUCgwmfCsFiw?view#%E7%AC%AC%E4%B8%80%E9%83%A8%E5%88%86-%E6%80%A5%E9%9C%80%E6%9B%B4%E6%96%B0%E7%9A%84%E8%B3%87%E6%BA%90)
- 下一步如何推進工作？


## 官網改動類提議 (流程草案撰寫中)

- 例如 2024.03 已提出 [希望調整與新增的事項](https://hackmd.io/t97cH7tFQPyUCgwmfCsFiw?view#-%E6%96%B0%E5%A2%9E)
    - 新增嵌入式網頁
    - 在特定內文中，增加資源連結一：slack archive
    - 在特定內文中，增加資源連結二：g0v 開源協作手冊
- 下一步如何討論可行性、共識？






---

## 討論區

20240302 Jasmine、Yvonne、宸維，針對官網有提出相關勘誤與修改提議
- 內容：https://hackmd.io/@iazze/SJYqfBep6/
    - 勘誤類：
        - 新手指南: 以下連結失效
            - 提案小訣竅
            - 非資訊人參與指南
    - 改動提議類：
        - 提議內容請見該 hackmd
- 如何推進相關工作？
    - 首頁可編輯權限名單？




    
