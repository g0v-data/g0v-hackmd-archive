---
tags: Disfactory
---

# 違章工廠舉報系統第35次小聚

時間：20200610
地點：地公北辦
線上：meet.google.com/ywj-qvoc-sze


## 參與者簽到：
* deeper
* yellowsoar
* ael
* yukai

## 待討論
* deeper報告使用者部分
    * GA數據
        * 5/13~5/26使用者總覽
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1646da9375c523896e15c18ab34e871e.png)
        * 5/27~6/9使用者總覽
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_65b1ec31d49f95b03e01ec22c563ea82.png)
        * 5/13~5/26行為流程
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_de9e24c64b148883d2f58a322359698c.png)
        * 5/27~6/9行為流程
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b9893ccffde9922d737664d0c8f497b3.png)

    * 災情
        * 6/5現勘志工社團
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f372ab8a11536ca686f6fbd4373a5ce0.png)
        * 6/5現勘志工社團2
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_cc6071aa2d07d56e080c175dd62d2849.png)
        * 6/7 email進來
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_cdf32db348fe71b3bb428b753affcd8a.png)

* 最近的貼文
    * 5/25（一）[第二次月報](https://bit.ly/2MMpKio)
    * 6/2（二）[原工輔法落日](https://bit.ly/2AUquze)
    * 6/4（四） [舉報有效](https://bit.ly/2UsCPBs) 近期地公粉專「自主觸及人數」最高
    * 6/5（五） [分享上下游報導](https://bit.ly/2MIb0Rq)

    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f1d8bc65779499efc45c3e7fb187355c.png)
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ef93fc771608add4b812e9ab5331d691.png)


* [後台使用情境](https://docs.google.com/document/d/1uBqD_Ms1-HHAH1B1SCagsVZS_XKMxYDFuQHOHxkJ4_8/edit#)持續更新
 
* 前端：@yukai @IU
    * 上傳照片的 bug 問題到底在哪裡？以及是不是在 merge imgur upload 這麼大的改動之前，我們沒有做好 user testing 確認沒問題。
    * front-end 2.0 to do 切好了嗎？我下禮拜可以看到哪個畫面？

* 後端：
    * csv download 的 bug @cph
    * 後端需新增的四個 table 討論確認 @cph
    * 1-1 工廠 List view update @cph @LittleWhiteYA
    * 1-2 產出公文的 spec 確認了？ @Sonia @Darren Hsu
    * 1-3 要先動哪塊呢 @tobyliu

* 設計：
    * 抱歉我們後端還是一團亂，spec 還沒有切的很好，沒有辦法很精確跟你們說能夠給前端使用者顯現什麼東西。
    * 確認 design system 與前端合作的進度
    * 介紹目前後台使用流程與不同表單的分別
    * 討論有哪些是要放到使用者介面給 user 看到的（我有點悲觀有沒有時間處理這件事）

## 會議記錄
* flow chart要畫好，才能做好
    1. 前端顯示的舉報狀態
    2. dashboard
* 四個table
    * 新增 doc single page
        * factory single page 來的資料(fixed)
        * doc_io 的往返進度 => 在 doc single page 裡面的 table view 新增一條（要問一下會不會太難，或是怎麼 UX 怎麼設計）
    
    * 新增一張 table `doc_io` 來追蹤公文往返進度 先跟 @cph 確認
        * 記錄進度 log 的，概念跟 ReportRecords 一樣
        * 印出來的資訊
        * 公文產生時間、
        * 可能還是需要權限管理

    * 新增一張 table `doc`：公文本人的 meta data
        * 公文號
        * creator
        * factory

    * 新增權限管理 user 名單 @Toby（細節待改）
        * reviewer_name
        * reviewer_role
        * 負責人_name
        * 負責人_email
        * 新增一張 `review_records` @Toby（公文發出去之前）

    * 新增一張 `立委 contact/縣市 contact` @IU @Sonia => 受文單位


## 下次待討論事項
