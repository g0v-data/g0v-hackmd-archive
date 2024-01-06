---
tags: cofacts, meeting note
---

20190123 會議記錄
====
orz,ci,bil 
  
> 前次會議記錄：https://g0v.hackmd.io/s/S1D8FVqf4
> 

## Dev items

### 已上線

- API 回應次序
- feedback 數無法超過 10
- 資料庫膨脹問題
    - 已經執行在 production，目前 5GB
    - 每日 cronjob 會刪除 8k 個 urls
    - 問題：是否可以把 snapshot repo 架在 GCS?
- 理由長度限制
    - 上線日期：20190118
    - 看結果：https://docs.google.com/spreadsheets/d/1tKS7O_6mWvSlywYkHAgcTkca9_t_xA7TfakeRg3y90Y/edit#gid=673812547
        - 效果顯著
        - ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_a9ad2c3b3264aa3acacd708d579e2896)
 
    - LIFF 重構：token based
- Rich menu 附範例
    - Ticket 追蹤 TBD
    - 訊息 & 影片: Ci
        1. 查詢一則只有一個回應的，立即得到結果
        2. 查詢一則剛好有正反回應的，選擇回應
        3. 查詢一則資料庫裡沒有的，示範送出文章
- Wording 檢討 （僅 staging，今天上 production）
    - 上了
    - 美玉姨也更新囉 CarolHsu++

### 下一步？

#### 編輯頁面

:::info
之前討論：
https://g0v.hackmd.io/s/B1X3aNfzE#%E7%B7%A8%E8%BC%AF%E5%80%8B%E4%BA%BA%E9%A0%81%E9%9D%A2
:::

- 重整 Nav bar
- Profile 頁面
    - 公開給其他人看
    - 展示基礎數字：經驗值相關數值、badge 相關數值
    - 經驗值：
        - 把一則訊息與回應連在一起 --> 1 點
        - 有人（包含自己）把你的回應跟別的文章連在一起 --> 1 點
        - 有用程度加總 --> 每個正的有用程度 * 2 點 for 回應者 & 連線者
    - Badge
        - 回了 n 則
        - 加入了幾天
        - 連續登入
        - 連續闢謠
        - 例：plurk badge ![Plurk](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_b5a4f74c5ef2e6aa0e6e445e997356a9)
    - 自己的回應的列表（可搜尋關鍵字）
    - 自己連接的回應列表
    - 自己撰寫的回應被其他人引用在哪些文章
    - 最多人覺得有用（最近 n 天，n 可調）
    - 最多人覺得沒用（最近 n 天，n 可調）
    - (nice to have) github contribution graph ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_74ab88e1683c34fd8f580a9c5cbfeefa)
    - (nice to have) github contribution activity ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_b2a573720ad83d4ab988c1008e4a3da2)

- 列表頁面
    - 加入 time filter 限制搜到的文章 or 回應時間

- 文章頁面
    - 第一次 (localstorage) 進入文章頁面，強制進入教學模式
    - Ex: https://introjs.com/
    - steps:
        1. 介紹「訊息」與「理由」
        2. 現有回應
        3. 撰寫新回應

#### Editor 也可以送出 reply request

Related issue: https://github.com/cofacts/rumors-site/issues/13

- 按下去之後會跳出填理由視窗，文案跟 LINE bot 相同
    - lucien: 感覺不依樣
    - orz: 因為最近我們讓 reply request 變得像是請使用者做初步查證，所以使用者跟編輯越來越像，才會覺得編輯也能送 reply request
    - lucien: 好喔
- 字數限制相同
    - orz：編輯可以用這個功能來交流查到一半的東西，跟 LINE 使用者的使用方法相同
    - bil: 有時候使用者只是想表達意見，如果給他們這個按鈕還不錯
    - ci: 編輯與編輯之間現在無法互相講話，只能去 FB 問
    - orz: 跟 FB group 有點重疊，但是 FB group 也很少人求救
- 一樣鼓勵把查到一半的東西丟出來
- 計入 reply request count 或跟 LINE 的分開計算？
    - bil, ci: 不分。凡是人都想知道
- 已經有回應之後是否還能送 reply request
    - orz: 跟 LINE 一樣不能送還不錯

#### 調查 + 引導對話去其他 LINE@
https://github.com/cofacts/rumors-line-bot/issues/121

orz:
理由長度變長之後似乎已經有擋住

bil
還是會有來問問題的人
每天 ２～５ 個
https://cofacts.g0v.tw/article/3cf781it8n4jj
https://cofacts.g0v.tw/article/dt8hqg9uswlv
2        
orz:
所以還是值得解的問題
手動輸入的很討厭

ci:
變成google 大神的意思

#### 我愛家我解惑

- 我愛家我解惑資料庫
- 123打到掛 + 我愛家我解惑的文案

#### 載入時閃動（FOUC）


## 小聚
- 假新聞清潔劑（Ci）：會先準備十五分鐘，但是之前短講經驗，加上經驗交流通常都會拖到三十分鐘，給個心理準備

- [ ] 視覺 by lucien (reuse 去年)
- [ ] 散佈
    - [ ] Facebook fanpage
    - [ ] Facebook group
    - [ ] LINE bot 貼文
    - [ ] LINE bot richmenu


## 活動結果

> GGM 分享？