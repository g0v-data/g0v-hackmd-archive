---
title: grantdash 2.0 model 規劃
tags: grants, grantdash, grant開發需求
---

# grantdash 2.0 model 規劃

 * [功能討論](https://g0v.hackmd.io/Zoy-NCQ9Q1G_KGiGYH4dUA)

## 概觀

Grantdash 可切分成數個子系統：
 * 核心系統
     * 用戶、用戶群組 ( 包含提案人、追問人、管理員等 )
     * 提案系統
     * 系統管理機制
         * 可線上操作的後台、控制提案時程、管理帳號與提案等
 * 評論系統
     * 類似 Disqus 可於任何頁面置入評論
     * 評論管理後台
 * 評審
     * 針對提案評分，另有排名機制
     * 匯整評審資料、設定名次等


## Data Schema / Model 

以下為 Schema 草案，僅列出必要部份. 若未特別註明, 均包含以下欄位:
 * createdtime timestamp default now()
 * deleted bool

### 核心系統

 * user ( 帳號管理 )
   * key int primary key
   * username text
   * email text
   * email_verified bool
   * passwd text
     * should be salted / bcrypted
   * displayname text
   * detail jsonb
     可能包含以下欄位:
     * keywords
     * expertise
     * url
     * description

 * team ( 功能群組管理 )
   * key int primary
   * slug text unique
     * camelCased, 人類可讀的字串替群組命名
     * slug 用於源碼中的權限控制
   * displayname text

 * teamUser ( team x user )
   * team_key int references team(key)
   * user_key int references user(key)
   * primary key (team, user)

 * project ( 提案 )
   * key int primary key
   * owner int references user(key)
   * board int references board(key)
   * title text
   * detail jsonb
     提案細節. JSON 格式設計上至少要支援:
     * 保存編修紀錄
     * 保留未來即時協作的擴充性

 * board (提案組, 例如某次黑客松或某屆獎助金)
   * key int primary key
   * title text
   * detail jsonb

 * token (TBD, for password reset and email verification)
   * type text
   * token
   * owner int references user(key)
   * createdtime timestamp default now()
   * expiretime timestamp

 * session (TBD, for storing user session )
   * key int primary key
   * detail text

### 評論系統

 * thread ( 用於儲存針對特定 URL 的評論設定 )
   * key int primary key
   * url text unique
   * detail jsonb

 * comment ( 某個 thread 下的單則評論 )
   * key int primary key
   * thread int references thread(key)
   * reply int references comment(key)
   * owner int references user(key)
   * content jsonb
     評論內容. JSON 格式設計上至少要支援:
     * 保存編修紀錄


## 評審系統
 * review
   * key int primary key
   * owner int references user(key)
   * board int references board(key)
   * stage int (TBD)
   * detail jsonb ( 評分表, 依前端需求設計 )

### 其它未釐清問題
 * 檔案上傳？
 * 附圖？


----
draft @ 2019/4/10

* 人相關
    * 人
        * User
            * int uid 流水號 ID
            * varchar(32) username 英文 ID
            * varchar(32) display_name 顯示名稱
        * UserAssociate
            * int associate_id 流水號 ID
            * int uid 連結到的 User->uid
            * varchar(128) openid identify
    * 提案者
    * 追問人
    * 評審
    * 內容管理者
* 提案相關
    * 獎助金屆次
    * 提案
    * 提問
* 評選相關
    * 
* 網站相關
    * 公告
    * 說明
    * 贊助商

舊版資料架構
==========
* db: hackdash
    * collection
        * dashboards
            * domain: 獎助金代碼 ex: 2019a, 2018a, 2017autumn, 2017spring
            * owner: 連結到 User
            * covers: array 所有提案封面
            * created_at
            * showcase: array 哪些是入圍提案
            * open: 是否開放報名（後來這個欄位好像沒在用了？）
            * title: 獎助金名稱
            * projectsCount: 提案數量
            * editable: 是否可以修改提案
            * description: 獎助金描述
        * drafts: 草稿
            * id: user_id 
            * draft  (把 proejcts 的內容包成一個 json 存起來)
        * projects
            * common
                * title: 提案標題
                * leader: 提案者，連結到 User
                * domain: 獎助金屆期
                * created_at
                * updated_at
                * tags: array 標籤
                * followers: array Userid
                * contributors: array Userid
                * status: 好像全都是 brainstorming
                * revisions: 修改記錄
                * finalist: boolean 是否有進到決選
                * awarded: boolean 是否有得獎
                * cover: 封面
            * 2017spring
                * description: 完整的 markdown 提案內容
            * after 2017spring(2017autumn, 2018a, 2019a)
                * money
                * desc
                * motivation
                * existed
                * problem
                * solution
                * why
                * ta
                * similar
                * refdesign
                * pastprj
                * cowork
                * usetime
                * spending
                * feedback
                * product
                * milestone1
                * milestone2
                * future
                * otherfund
                * category
                * slide
                * link
            * after 2017autumn(2018a, 2019a)
                * growth
                * difficulty
                * related
                * nonos
                * role
                * detailUser
                * detailProblem
                * detailSolution
                * detailCompetitor
                * detailCompare
                * detailService
            * after 2018a (2019a)
                * proposer
        * sessions
            * cookie sessions, 不需要轉移
        * users
            * username
            * name
            * picture
            * email
            * provider_id
            * provider
            * created_at
            * admin_in
                * array: 可以指定是在哪幾屆獎助金的 admin
            * bio