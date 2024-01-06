###### tags: `daodao`
# g0v 50th 黑客松協作任務

## 任務／新增你覺得好棒棒的資源 :pencil: 
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_026b187c86397d64e723662a10f17fb3.png)
可以直接進入[此網頁](https://www.daoedu.tw/contribute/resource)，分享一個資源！

## 任務／製作==新增教育活動==的教學頁
教學可放在notion or trello


## 任務／島島阿學專案授權討論
內容 CC BY-NC-SA 4.0
https://creativecommons.org/licenses/by-nc-sa/4.0/deed.zh_TW
https://zh.wikipedia.org/zh-tw/%E7%9F%A5%E8%AF%86%E5%85%B1%E4%BA%AB%E8%AE%B8%E5%8F%AF%E5%8D%8F%E8%AE%AE
https://www.ndc.gov.tw/Content_List.aspx?n=5253FD73B3ABA360

討論島島阿學網站的開源形式
- MIT
- CC0
- LGPL

https://medium.com/@ellierellier/%E6%A6%82%E5%BF%B5%E7%AD%86%E8%A8%98-%E4%BB%80%E9%BA%BC%E6%98%AF%E8%BB%9F%E9%AB%94%E6%8E%88%E6%AC%8A%E6%A2%9D%E6%AC%BE-software-license-%E6%8E%88%E6%AC%8A%E6%A2%9D%E6%AC%BE%E7%9B%B8%E9%97%9C%E6%A6%82%E5%BF%B5%E4%B8%80%E6%AC%A1%E9%87%90%E6%B8%85-9d70e29f3a29
詢問到開源定義需要開放、允許商用，如果商用不想公開，就需要另外討論授權。

小結：內容：CC\程式：LGPL

結論：星期三待討論內容細節授權

▌g0v schooling 獲獎團隊義務

提案內容、提案之初版軟體（demo）或解決方案，必須符合 g0v 社群宣言精神。
提案內容、提案之初版軟體（demo）或解決方案，在獲獎之後，必須符合 Free Culture Works 定義，以「CC 姓名標示 4.0 國際」授權條款授權釋出。
軟體開發專案必須使用符合 OSI 認可之授權，並考量行動裝置友善（Mobile-Friendly）。

FYI
https://www.ewdna.com/2012/02/open-source-licensegpl-lgpl-bsd-apache.html
https://g0v.hackmd.io/cq_WocqpRAGHBM3wVWJjqA (裡面有大神回覆)
[cc授權小幫手](https://g0v.github.io/cchelper/)
https://medium.com/@ellierellier/%E6%A6%82%E5%BF%B5%E7%AD%86%E8%A8%98-%E4%BB%80%E9%BA%BC%E6%98%AF%E8%BB%9F%E9%AB%94%E6%8E%88%E6%AC%8A%E6%A2%9D%E6%AC%BE-software-license-%E6%8E%88%E6%AC%8A%E6%A2%9D%E6%AC%BE%E7%9B%B8%E9%97%9C%E6%A6%82%E5%BF%B5%E4%B8%80%E6%AC%A1%E9%87%90%E6%B8%85-9d70e29f3a29

目前公開專案
https://github.com/daodaoedu/daodao-extension

## 任務／會員功能
- 使用者註冊時需填寫的內容（介紹頁）
    - 個人介面（要涵蓋哪些介紹）
        - 使用者ID: uuid
        - 照片：
        - 姓名：
        - 暱稱：
        - 信箱：
        - 年齡：
        - 孩子的年齡：
        - 身份（多選）：學習者、教育工作者、家長、自定義
        - 三個標籤：
        - 我是否想要公開分享個人介紹
        - 我想來：找學伴、找老師
        - 我想分享的：
        - 我需要的：
        - 所屬的單位／學校／社群：
        - Facebook（選填）：
        - Instagram（選填）：
        - 島島阿學 Slack ID（選填）：
        - 創建日期：
        - 曾經新增的資源：
        - 主要所在地：
        - 徽章：
    - 新增資源與收藏資源的紀錄
- 使用者資料隱私權條款


## 任務／架資料庫
規劃資料庫儲存與格式設計
- 近期規劃：
    - noSQL: firebase使用（有用過的夥伴歡迎支援）

- For RDBMS:
```sql

CREATE TABLE UserAccount{
    id UUID
    username text
    password binary(bcrypt)
    email text
    updated_at datetime
    create_at datetime
    user_profile_id UUID
}

CREATE TABLE UserProfile{
    id uuid
    name text
    nickname text
    age int
    location text
    public boolean `true if show up on public page`
    topic text
    updated_at datetime
    create_at datetime
}

CREATE TABLE UserSocialMedia{
    user_id int
    facebook_id text nullable true
    google_id text nullable true
    instagram_id text nullable true
}

CREATE TABLE UserTags{
    id int
    name text
}

CREATE TABLE UserAssociateTag{
    user_id uuid
    tag_id int
    created datetime
}

CREATE TABLE CourseResource{
    id uuid
    raw_data jsonb
    created_by uuid 'User ID'
}

CREATE TABLE Award{
    id uuid
    name text
}

CREATE TABLE UserAssociateAward{
    award_id uuid
    user_id uuid
}
```

- RDBMS Reference: 
        1.  https://blog.cloudflare.com/introducing-d1/ 
        2.  https://stackoverflow.com/questions/1279613/what-is-an-orm-how-does-it-work-and-how-should-i-use-one

- 長期規劃：討論noSQL or SQL建置與設計

## 任務／教育幣or共學幣（想參考 DAO 的思維與機制）
歡迎加入 g0v channel [#colearning-dao](https://g0v-tw.slack.com/archives/C0182TQTVV2)

## 任務／兩週年活動（八月？）

### 元素、主題

- 互相學習
- 自由交流
- 參考方向
    - 學習的樣貌是什麼？是否要有目的？
    - 什麼值得共學？需要訂嗎？
- 參考的方式
    - 上下午？（上午Open Space Technology ，下午工作坊或繼續）
- 主題與兩週年的關係？
- 如何長期多方舉行


### 對象
- 學生
- 教育工作者
- 不限定

### 進度
- **討論規劃**
- 活動場地、時間設定
- 活動介紹、文案、圖
- 活動上架宣傳
- 活動人員培訓
- 活動人員行前會
- 活動材料準備
- 活動執行
- 會後討論


### 長期舉辦
- SOP
    - （參考哪個資料版本?）
        - [RxC 2021 開放空間年會](https://g0v.hackmd.io/@jothon/unConf2021/https%3A%2F%2Fg0v.hackmd.io%2F%40jothon%2FrJVIH6TBK)
- 各個組織者如何共同組織
    - **共同的元素**
    - 是否一定是OST？



### 形式
開放空間會議技術（OST）

工作人員
- 大場主持、控場
- 行政（報到茶水...）
- 桌長需求？（暗樁培訓，分到每一組）
- 紀錄
- 攝影


### 結構
- 分幾組？
    - （視報名狀況）
- 時程
    - 破冰介紹
        - 暖身
        - 島島阿學兩週年介紹
        - OST 概念介紹
            - 人
                - 議題主（～桌長）
                    - 責任
                - 紀錄（桌長指定）
                    - 討論標題
                    - 討論內容
                    - 參與者
                    - 最後貼出
                - 其它討論參與者
            - 討論時間
                - 時間到停止
                - 是否可以提前結束？
    - 上午1場實驗
    - 下午2場 
    - 結尾、心得交流
- 時間
    - 整天上下午








- 內容接受者 給予 內容輸出者 獎勵？

## 任務／Google extension 設計：新增資源



## 任務／Blog：未來可跟 UI 討論如何優化加強

