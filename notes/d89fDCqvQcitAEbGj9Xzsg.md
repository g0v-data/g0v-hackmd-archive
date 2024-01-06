成就 2.0 規劃
============

## 目標
- 讓 g0v 各坑主可以開立自己坑的成就
- 讓新手任務也可以納入成就
- 讓零時小學校的學習歷程也納入成就
- 把原有的 badge.g0v.tw 的 hackpad, hackmd, kktix, github, slack 成就納入
- 可以用 github, gmail, slack 等登入方式

## 資料庫規劃
### 使用者相關
- user 使用者資料
    - PK: user_id INT
    - user_name VARCHAR(32) (不重覆名稱，用在網址上面)
    - meta JSON 存放頭像、三個關鍵字、自介等資訊
    - created_at INT 註冊時間
    - login_at INT 最近登入時間
- user_association 使用者登入身份
    - PK: association_id INT
    - user_id INT 連結到哪個使用者
    - login_name VARCHAR(64) 登入身份識別，Ex: google://ronnywang@gmail.com, github://ronnywang, slack://U123456 ...
    - created_at INT 新增身份時間
- user_badge 使用者已得到成就
    - PK: user_badge_id INT
    - user_id INT: 哪個使用者
    - hole_id INT: 屬於哪個坑
    - hole_badge_id INT: 屬於哪個坑的哪個成就
    - got_at INT: 取得成就時間
    - title VARCHAR(64): 成就標題
    - extra JSON: 成就額外資訊
### 坑相關
- hole: 坑
    - PK: hole_id INT
    - hole_name VARCHAR(32) (不重覆名稱，用在網址上)
    - meta JSON 存放頭像、關鍵字、相關網址等資訊
    - created_at INT 建立時間
- hole_staff: 坑的管理員
    - PK: staff_id INT
    - hole_id INT: 屬於哪個坑
    - staff_type INT: 0-owner, 1-admin: owner 可以增減 admin, admin 不能變更 staff
    - created_at INT: 建立時間
- hole_badge: 坑內成就列表
    - PK: hole_badge_id INT
    - hole_id INT: 屬於哪個坑
    - title VARCHAR(32)
### 管理員相關
- admin: 管理員列表
    - PK: admin_id INT
    - user_id INT 管理員 ID ，可以開坑

## 網址規劃
### 基本網址
- https://badge-api.g0v.tw/{user_name}
    - 個人成就資料
- https://badge-api.g0v.tw/@{hole_name}
    - 坑的資料
- https://badge.g0v.tw/@{hole_name}/badge/{badge_id}
    - 坑內的某個成就的完整資訊
- https://badge.g0v.tw/_/latest/user
    - 列出最新的 30 個使用者
- https://badge.g0v.tw/_/latest/hole
    - 列出最新的 30 個坑
- https://badge.g0v.tw/latest/user_badge
    - 列出最新的 30 個取得到的坑
- https://badge.g0v.tw/_/new
    - 註冊帳號頁
### 登入相關
- https://badge.g0v.tw/_/login
    - 使用帳號密碼登入頁
- https://badge.g0v.tw/_/logout
    - 登出
- https://badge.g0v.tw/_/login/{oauth_type}
    - 使用外部 oauth 登入，Ex: google, github, slack ...
- https://badge.g0v.tw/_/login/{oauth_type}done
    - 使用外部登入回來頁面