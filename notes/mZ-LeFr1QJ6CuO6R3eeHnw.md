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

* 2024.04.20 [基礎松](https://g0v.hackmd.io/SAHzDkZeRNqTvOj-qIalwQ?both)提案討論，建置「官網報修機制」定義與流程
:::

:::success
文件目錄
[TOC]
:::

# 動機

為了讓 g0v 相關專案，都能透過 g0v 首頁，傳達自己的專案資訊，並且適時修改、更新、維護相關網頁，我們需要一套治理機制，來規範包含治理角色、專案資訊編修等事宜。

治理機制將涵蓋：

1. 社群治理的審核者、編輯者的加入與退出
2. 首頁（ https://g0v.tw ）的專案輪播調整
3. 活動行事曆 （ https://g0v.tw/intl/zh-TW/event/ ） 的調整
4. [2024.03 提議，可藉由後續基礎松擴大討論與確認方案] 網站通報報修、小規模內容更新工作
5. [2024.03 提議，可藉由後續基礎松擴大討論與確認方案] 涉及網站版面的改動提議

# SNS社群治理機制

請參照 [SNS 社群治理](https://g0v.hackmd.io/THKRsDsNRXGsa_0zFUn3Gw)


# 行事曆
## 治理機制成員名單
- 輪播、活動行事曆的修改，都需要經過 review

- 有編輯權限者：
    - 四個 GoogleGroup：g0v-talks、g0v-intl、g0v-jothon、cofacts

- 群體相關介紹
    - g0v-talks
        - g0v-talks@googlegroups.com
    - g0v-jothon 名單說明
        - 「揪松團決策委員與職工」可主動協助更新日曆內容，新增活動、修改活動內容，名單：https://jothon.g0v.tw/about/
    - g0v-intl
        - https://g0v.hackmd.io/@chihao/rypH_tpoE
    - cofacts
        - https://cofacts.tw/about

- [Reviewer 清單](https://docs.google.com/spreadsheets/d/18oekxIDN84iPhP7fUYMleV7jmfWpr9UdZuujPFJmTBM/edit#gid=1776966921)
  - ddio
  - Teemo
  - isabelhou
  - tofus
  - 揪松 (「揪松團決策委員與職工」名單：https://jothon.g0v.tw/about/)
  - chihao


## 首頁專案輪播

請參照：g0v 首頁 - 專案介紹的輪播機制
https://g0v.hackmd.io/Q1kxZgObSBihH5ZrHKNiJg?view

## 張貼活動的流程

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

# 官網報修機制
根據2024.04.20基礎松的[討論](https://g0v.hackmd.io/SAHzDkZeRNqTvOj-qIalwQ?both)

## 聯絡方式

g0v slack #gov-landing-page 頻道

>~~** To do: 在slack上面開一個關於網頁報修的channel **~~

## 相關角色

### 提議者
* 提議方式：
    * 於 slack 提議與描述 （general channel、g0v-landing-page）
    * 開 github Issue
    * 建立共筆文件
    * 或其他方式
* 建議：
    * 希望能透過草稿、簡報、mockup、手繪等方式將內容明確化
        
### 開發者相關
* 把前端的問題寫成程式
* 可以先製作一個展示網址
* 送出 pull
* 不需要有 github g0v 組織權限

### Reviewer
* 名單公開
* 技能建議：可以確認網站跑起來，修改網頁程式碼，瀏覽程式，Review Code, push, merge
* 現況：64 admins, 276 members
    * https://github.com/orgs/g0v/people
    * admin 有權限可以砍光光所有 repositories (也可以順便把其他人都踢出 admin)
    * members 都有權限可以在 g0v.tw 首頁塞入任何東西，跟在上面專案塞入任何有害程式碼
    * 但也因為自由度很高，**g0v 是在 github 上世界前三大的 civic tech 社群**
        * https://www.ithome.com.tw/news/106629 

* Reviewer 邀請方式
    - reviewer: 
        - 願意擔任 reviewer 名單的人上 github 開 issue 請求加入
        - 參考SNS 邀請機制，透過三個既有 reviewer 推薦，再到 github 發 issue 請求加入
    > - **To do: 召集新的reviewer (via Slack, Facebook, 後勤中心)、在SNS or FB 發邀請文，
    > 確認報名者且通過審核者，可將資訊填入 https://docs.google.com/spreadsheets/d/18oekxIDN84iPhP7fUYMleV7jmfWpr9UdZuujPFJmTBM/edit#gid=1776966921
    > * 通知 GitHub 上面的 contributor 加入 Slack 頻道


* Reviewer 權限
    * 每則修改隨機抽籤指派 2 reviewer
        * 抽籤指派方式
        - 用 Slack bot，或其他自動、手動機制指派、[隨機抽籤](https://aws.ronny.tw/g0v-sns/proxy.php?type=calendar)
        - 紀錄每則修改狀況 [[紀錄]](https://docs.google.com/spreadsheets/d/18oekxIDN84iPhP7fUYMleV7jmfWpr9UdZuujPFJmTBM/edit#gid=1776966921
    * 每一個 reviewer 都有這些權限
        * 審閱修改，給出 Review Pass
        * 審閱修改，給出 NO
        * Pass: 否則是無回應
        * 若有兩次無回應紀錄則移除此人的 memeber 權限
    * 審閱期
        * 一般狀況：review 3 days
        * 提案者可以自行定義

## 修改的定義
### A-1. 通報報修類
* 移除、更新失效連結
* 不改變用詞用字
* 例如：內文網址連結更新，例如 2024.03 已提出 [新手指南區域，「提案小訣竅」、「非資訊人參與指南」連結失效](https://hackmd.io/t97cH7tFQPyUCgwmfCsFiw?view#%E7%AC%AC%E4%B8%80%E9%83%A8%E5%88%86-%E6%80%A5%E9%9C%80%E6%9B%B4%E6%96%B0%E7%9A%84%E8%B3%87%E6%BA%90)


### A-2. 官網小規模更新類
* 不改變網站架構的前提下
* 增加條列內容
  - 例如：在特定內文中，增加資源連結一：slack archive
  - 例如：在特定內文中，增加資源連結二：g0v 開源協作手冊
    - 不影響原意的文字抽換

### B. 官網改動類
- 涉及版型調整
- 新增嵌入式網頁
- 移除特定內容
- 難歸納為報修類與小規模更新類的改動提議等 

## 修改流程

### A類：靜態型，A-1. 通報報修類、A-2. 官網小規模更新類

* 於 g0v slack #gov-landing-page 頻道提議
    * 建議附上說明文件
    * Developer 進行開發
    * Reviewer 確認 ／ Editer 更新
 
 * 審核方式
     * 較不需要程式基礎、可由members快速審核
     * 抽籤3位reviewers確認
     * 有一個測試的網址，直接截圖標記，告訴reviewer 差異，點進去看確認，就可以放行。
 
### B類：功能型，B.官網改動類
* 在大松、基礎松等場合提案，邀請社群討論
   * 建議附上說明文件
   * 建議提議者畫 Mockup、試做範本，方便工程師對齊
* 通常會涉及到 版型 UI 考量，技術可行性，手機版體驗感受如何等

* 審核方式
    * 需要較有程式基礎的members審核
    * 抽籤2位reviewers確認
    * 慢速過審：由reviewer run 起來，檢查差異，確認後過審。

---

### Landing page 頁面設計
 
 在官網新增「問題回報」功能，
 
 兩種方式：
 1. 擅長撰寫程式的人群：**連結 github issue or slack channel**
    > To-do: hackmd教學如何發issue

2. 較少程式知識的人群：**google form 連動到 slack channel 確保較多人看到訊息**
    > To-do: 建立google form 並開通連動slack

---
### 定期回顧機制
- 每次基礎松開始時**安排 review 時間**，回顧 google form/slack 上尚未解決的問題


---

### 過去的討論草稿區

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
        - 二、官網小規模更新類提議
        - 三、官網改動類提議

待討論：
* 如果網站更新上去有bug，要由誰來協助主責處理？
* 問題：Github landing-page 程式碼更新、部署方式
- 參考 summit 更新機制？使用 github action 撰寫部署腳本？
* 問題：Github 權限管理辦法
    - 既有 3xx 位 memeber 是否需要留存？或是否需要篩選機制？
    - 直接廣發詢問既有 memeber 是否願意參與新 reviewer 機制？
* 程式碼 review 的標準？
    - 程式碼的規則嚴謹度？
    - 官網內容的審閱標準？
    - 功能性 ＆ 安全性檢查？
