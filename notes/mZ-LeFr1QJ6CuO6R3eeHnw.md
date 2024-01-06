---
tags: g0vernance
---
# g0v 首頁社群治理機制
（於 2023.3.4 基礎松提案討論）

## 動機

為了讓 g0v 相關專案，都能透過 g0v 首頁，傳達自己的專案資訊，我們需要一套治理機制，來規範包含治理角色、專案資訊編修。

治理機制將涵蓋：

1. 社群治理的審核者、編輯者的加入與退出
2. 首頁（ https://g0v.tw ）的專案輪播調整
3. 活動行事曆 （ https://g0v.tw/intl/zh-TW/event/ ） 的調整

## 聯絡方式

g0v slack #gov-landing-page 頻道

## 審核者的加入與退出

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

[討論過程](https://g0v.hackmd.io/Q1kxZgObSBihH5ZrHKNiJg)

### 發文流程

1. 將欲發文章依照格式貼入[編輯台]()
2. 於 g0v slack #sns 發文 ，貼上文章連結，並 tag reviewer 2 位
   > Reviewer 請用[抽籤器](https://ronny.tw/g0v-sns/?type=calendar)抽出後，前 2 位即是該篇文章的 reviewer，請欲發文者 tag reviewer 
3. 確認被抽中的 reviewer 看過無誤後，其中有 FB 權限的 reviewer 會幫忙貼上 FB 設定排程
4. 到[編輯紀錄](https://docs.google.com/spreadsheets/d/1xyxYGKU7iia3xSu6rF9F6YCcXOcEqrFsI2RD493bAxE/edit#gid=1776966921)更新本次的 review 狀況

## 活動行事曆

[討論過程](https://g0v.hackmd.io/ym6CHeYQS7aVPB1gM-UCUg)


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


## 編輯者 (2023.3.4)

### 首頁：


### 行事曆：

- 有編輯權限者：
    - 四個 GoogleGroup：g0v-talks、g0v-intl、g0v-jothon、cofacts
- 「揪松團職工」可主動協助更新日曆內容，新增活動、修改活動內容 ..等

## Reviewer (2023.3.4)

- [Reviewer 清單](https://docs.google.com/spreadsheets/d/18oekxIDN84iPhP7fUYMleV7jmfWpr9UdZuujPFJmTBM/edit#gid=1776966921)
  - ddio
  - Teemo
  - isabelhou
  - tofu
  - 揪松
  - chihao






    
