---
tags: g0vernance
---
# g0v 首頁社群治理機制

:::warning
機制建構歷程
- 2023.3.4 基礎松提案討論，並隨後建立三項治理流程 (1) 審核者的加入與退出 (2) 首頁專案輪播 (3) 活動行事曆
- [2024.03 開始討論] 2024.3.2 Jasmine、Yvonne、宸維，針對官網提出「勘誤需求」與「改動提議」
    - 相關共筆：[g0v github 社群規範討論](https://g0v.hackmd.io/1wFAJoQeTrmw9pnjcqPkXg)
    - [2024.03 開始討論] 2024.3.8 chewei 提議依照改動程度，分流處理
        - (A) 維護類的修改，可以依循流程：頻道提議 -> Reviewer -> Editer 
        - (B) 透過基礎松來討論較大幅度改動的可行性與共識
:::

:::success
文件目錄
[TOC]
:::

## 動機

為了讓 g0v 相關專案，都能透過 g0v 首頁，傳達自己的專案資訊，並且適時修改、更新、維護相關網頁，我們需要一套治理機制，來規範包含治理角色、專案資訊編修等事宜。

治理機制將涵蓋：

1. 社群治理的審核者、編輯者的加入與退出
2. 首頁（ https://g0v.tw ）的專案輪播調整
3. 活動行事曆 （ https://g0v.tw/intl/zh-TW/event/ ） 的調整
4. [2024.03 提議，可藉由後續基礎松擴大討論與確認方案] 網站通報報修、小規模內容更新工作
5. [2024.03 提議，可藉由後續基礎松擴大討論與確認方案] 涉及網站版面的改動提議

## 聯絡方式

g0v slack #gov-landing-page 頻道

## 治理機制成員名單

### 編輯者 (2023.3.4)

#### Landing page 首頁：（TBD）

* TBD
 *現況
    * 64 admins, 276 members
        * https://github.com/orgs/g0v/people
    * admin 有權限可以砍光光所有 repositories (也可以順便把其他人都踢出 admin)
    * members 都有權限可以在 g0v.tw 首頁塞入任何東西，跟在上面專案塞入任何有害程式碼
    * 但也因為自由度很高，**g0v 是在 github 上世界前三大的 civic tech 社群**
        * https://www.ithome.com.tw/news/106629

#### 行事曆：

- 有編輯權限者：
    - 四個 GoogleGroup：g0v-talks、g0v-intl、g0v-jothon、cofacts

群體相關介紹
- g0v-talks
    - g0v-talks@googlegroups.com
- g0v-jothon 名單說明
    - 「揪松團決策委員與職工」可主動協助更新日曆內容，新增活動、修改活動內容，名單：https://jothon.g0v.tw/about/
- g0v-intl
    - https://g0v.hackmd.io/@chihao/rypH_tpoE
- cofacts
    - https://cofacts.tw/about

### Reviewer (2023.3.4)

- [Reviewer 清單](https://docs.google.com/spreadsheets/d/18oekxIDN84iPhP7fUYMleV7jmfWpr9UdZuujPFJmTBM/edit#gid=1776966921)
  - ddio
  - Teemo
  - isabelhou
  - tofu
  - 揪松 (「揪松團決策委員與職工」名單：https://jothon.g0v.tw/about/)
  - chihao

### 審核者的加入與退出

參考自 [SNS 社群治理](https://g0v.hackmd.io/THKRsDsNRXGsa_0zFUn3Gw)

- 輪播、活動行事曆的修改，都需要經過 review
- *＃＃是否加入官網的更新？（TBD）*
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


## 官網通報報修類 (流程草案撰寫中、TBD)

- 什麼是「通報報修類」？
    - 移除、更新失效連結
    - 不改變用詞用字
        - 內文網址連結更新，例如 2024.03 已提出 [新手指南區域，「提案小訣竅」、「非資訊人參與指南」連結失效](https://hackmd.io/t97cH7tFQPyUCgwmfCsFiw?view#%E7%AC%AC%E4%B8%80%E9%83%A8%E5%88%86-%E6%80%A5%E9%9C%80%E6%9B%B4%E6%96%B0%E7%9A%84%E8%B3%87%E6%BA%90)
- 流程：
    - 頻道提議
        - 建議附上說明文件
    - Reviewer 
    - Editer 
        - 目前尚未建立 Editer 名單

## 官網小規模更新類提議 (流程草案撰寫中、TBD)

- 什麼是「小規模更新類」？
    - 不改變網站架構的前提下
    - 增加條列內容
        - 例如：在特定內文中，增加資源連結一：slack archive
        - 例如：在特定內文中，增加資源連結二：g0v 開源協作手冊
    - 不影響原意的文字抽換
- 流程：
    - 於 g0v slack #gov-landing-page 頻道提議
        - 建議附上說明文件
    - Reviewer 
    - Editer
        - 目前尚未建立 Editer 名單

## 官網改動類提議 (流程草案撰寫中、TBD)

- 什麼是「改動類」？
    - 涉及版型調整
    - 新增嵌入式網頁
    - 移除特定內容
    - ...等 
- 流程：
    - 如何討論可行性、共識？
    - 辦理線上討論、或基礎松等


---

## 討論區

20240302 Jasmine、Yvonne、宸維，針對官網有提出相關勘誤與修改提議
- 內容：https://hackmd.io/@iazze/SJYqfBep6/
    - 20230308 chewei 依據內容，嘗試分類為三種提議類型
        - 官網通報報修類：像是，內文網址連結更新
        - 官網小規模更新類提議：像是，增加條列內容、原本的文字抽換
        - 官網改動類提議：像是，新增嵌入式網頁、移除特定內容
            - 這個可能就需要 基礎松 來邀請社群確認
                - 通常會涉及到 版型 UI 考量，技術可行性，手機版體驗感受如何等
- 如何推進相關工作？
    - 提議：
        - 首先先確定，首頁可編輯權限名單
        - 依據三種改動程度，建立各自工作流程
        - 一、官網通報報修類
            - 頻道提議
            - Reviewer 
            - Editer
        - 二、官網小規模更新類提議
            - 頻道提議
            - Reviewer
            - Editer
        - 三、官網改動類提議
            - 這個可能就需要 基礎松 線上或實體，來邀請社群確認
            - 通常還需要畫 Mockup, 試做 




    
----
----
----
(以下為Yvonne, Jas, Vivian 討論共筆，待基礎松確認)


## 治理機制成員名單

### 編輯者 (2023.3.4)

#### Landing page 首頁：（TBD）

* TBD
 *現況
    * 64 admins, 276 members
        * https://github.com/orgs/g0v/people
    * admin 有權限可以砍光光所有 repositories (也可以順便把其他人都踢出 admin)
    * members 都有權限可以在 g0v.tw 首頁塞入任何東西，跟在上面專案塞入任何有害程式碼
    * 但也因為自由度很高，**g0v 是在 github 上世界前三大的 civic tech 社群**
        * https://www.ithome.com.tw/news/106629

### Reviewer (2023.3.4)

- [Reviewer 清單](https://docs.google.com/spreadsheets/d/18oekxIDN84iPhP7fUYMleV7jmfWpr9UdZuujPFJmTBM/edit#gid=1776966921)
  - ddio
  - Teemo
  - isabelhou
  - tofu
  - 揪松 (「揪松團決策委員與職工」名單：https://jothon.g0v.tw/about/)
  - chihao

### 審核者的加入與退出

參考自 [SNS 社群治理](https://g0v.hackmd.io/THKRsDsNRXGsa_0zFUn3Gw)

## 官網通報報修類 (流程草案撰寫中、TBD)

- 什麼是「通報報修類」？
    - 移除、更新失效連結
    - 不改變用詞用字
        - 內文網址連結更新，例如 2024.03 已提出 [新手指南區域，「提案小訣竅」、「非資訊人參與指南」連結失效](https://hackmd.io/t97cH7tFQPyUCgwmfCsFiw?view#%E7%AC%AC%E4%B8%80%E9%83%A8%E5%88%86-%E6%80%A5%E9%9C%80%E6%9B%B4%E6%96%B0%E7%9A%84%E8%B3%87%E6%BA%90)
- 流程：
    - 於 g0v slack #gov-landing-page 頻道提議
        - 建議附上說明文件
    - Developer 進行開發
    - Reviewer 確認 ／ Editer 更新
        - CTA: 建立 Editer 名單

## 官網小規模更新類提議 (流程草案撰寫中、TBD)

- 什麼是「小規模更新類」？
    - 不改變網站架構的前提下
    - 增加條列內容
        - 例如：在特定內文中，增加資源連結一：slack archive
        - 例如：在特定內文中，增加資源連結二：g0v 開源協作手冊
    - 不影響原意的文字抽換
- 流程：
    - 於 g0v slack #gov-landing-page 頻道提議
        - 建議附上說明文件
    - Developer 進行開發
    - Reviewer 確認 ／ Editer 更新
        - CTA: 建立 Editer 名單

## 官網改動類提議 (流程草案撰寫中、TBD)

- 什麼是「改動類」？
    - 涉及版型調整
    - 新增嵌入式網頁
    - 移除特定內容
    - 難歸納為報修類與小規模更新類的改動提議等 
- 流程：
    - 於 g0v slack #gov-landing-page 頻道提議
        - 建議附上說明文件
        - 建議提議者畫 Mockup、試做範本，方便工程師對齊
    - 社群討論：
        - 如何衡量共識、可行性
        - 透過大松活動環節、基礎松等實體線下社群活動確認
        - 投票
        - 完成之後進入review與更新環節
    - Developer 進行開發
    - Reviewer 確認 ／ Editer 更新
        - CTA: 建立 Editer 名單

待討論：
* 如果網站更新上去有bug，要由誰來協助主責處理？
* Reviewer 名單
    * Suggestion by Teemo 
    * 快速過審的模式：有一個測試的網址，直接截圖標記，告訴reviewer 差異，點進去看確認，就會放行。
    * 慢速過審：由reviewer run 起來，檢查差異，確認後過審。
* Editer 名單
    * 也可以提案自己找人進去當editor
    * 看現有成為editor的機制（例如：2人推薦）

* 角色定位：提議者相關
    提議方式：
        於 slack 提議與描述 （general channel、g0v-landing-page）
        開 github Issue
        建立共筆文件
        或其他方式 表單
        希望能將內容明確化
        草稿
        Mockup
        手繪
        也可以用簡報方便協作
    主要檢核：工程師看得懂或看不懂
* 角色定位：開發者相關
    把前端的問題寫成程式
    可以先製作一個展示網址
    送出 pull
    不需要有 github g0v 組織權限
* 角色定位：審核者／上傳者（要建立名單？）
    優先找曾經參與開發 g0v.tw 的 contributor
    優先找也在 g0v Slack 的人
    或通知 GitHub 上面的 contributor 加入 Slack 頻道
    Review Code, push, merge
    技能建議：網站跑起來，修改網頁程式碼，瀏覽程式

