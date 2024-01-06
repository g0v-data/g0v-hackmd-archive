---
title: "g0v addressbook iOS app"
tags: hackpad
---

# g0v addressbook iOS app

> [點此觀看原始內容](https://g0v.hackpad.tw/MEZ33mTjHB9)


## 政府通訊錄 iOS 版

需要聯絡政府單位或是政府官員時候，需要查詢電話資料及內容，或是聯絡相關人員之時，提供行動版的查詢功能

簡單的說就是 [政府公開通訊錄](http://hack.g0v.tw/kuansim/g6v6MpyacFb) 的手機連接端~，但是是離線版~


## Feature Version

- 0.x
    - 提供 URL open 的功能，讓其他 app 可以直接開啟或查詢
    - 標記結果頁面
    - 建議查詢字串
- 0.1
    基本功能及使用情境設定、回報錯誤資料功能
    - [x] 主要查詢頁面
        - [ ] 可選人員或是機關
        - [ ] 切換到設定頁面
    - [x] 查詢結果頁面
    - [ ] 詳細資料頁面
        - [x] 電話 (可播出)
        - [ ] 地址
            地址可以使用 Map 相關打開
        - [ ] 備註
        - [ ] 顯示圖片
            主要是個人照片或是機關照片
    - [ ] 設定頁面
        - [ ] 提供意見、回報問題
            打開 Mail 介面，寄信
        - [ ] AppleStore 留下評價

## Strategy

主要目標：
- 可以提供快速查詢功能
- 從標記清單中快速找回聯絡人
- 提供其他 App 可用 **open URL** 方式(打開)查詢資料

主要族群
- 手邊暫時沒有電腦只有智慧型手機
- 沒有網路也想要知道聯絡方式
- 只會使用手機不會使用電腦的人

## Scope

- 依姓名、電話查詢資料
- 標記特定資料 (機關單位或是聯絡人)
- 有網路的地方連線資料庫更新資料庫
    以可以**離線使用**為目標

## Structure

- 主要頁面
    使用三個不同的頁面去切換 (tab bar)
    - 查詢頁面
        - 設定頁面
    - 標記頁面
- 資料格式
    - [機關單位(popolo.organization)](http://popoloproject.com/specs/organization.html#serialization)  [討論](https://github.com/g0v/addressbook/issues/10)

## Wireframe / Content

- 查詢頁面
    - 詳細資料頁面 (機關單位/單一聯絡人)
        - 照片 (機關照片或是人員照片)
        - 名稱
            點選提供複製名稱
        - 電話
            點選直接使用系統電話播出
        - 地址
            點選打開地圖程式 (Ex: Google Map or Apple Map)
        - 標記該筆資料
        - 備註
- 標記頁面
    - 顯示有標記的聯絡人
    - 編輯標記清單及順序
- 設定頁面
    - 更新資料庫選項
    - 簡單說明
    - 免則聲明
    - 版本號

## Visual

> 每頁實際上看起來會長什麼樣子
> [name=ET B]

> 精確的排版、配色、字體大小、視覺特效
> [name=ET B]

> （產出文件：識別系統 / 設計稿 / prototype）
> [name=ET B]

Visual Reference:
apple Phone, whatsthenumber

POP prototype
- [https://popapp.in/projects/5329a0817a01b30c240c0966/preview](https://popapp.in/projects/5329a0817a01b30c240c0966/preview)



## 實作


### Use Case:

使用者查詢公家機關電話：
1.  點"查詢頁面"，在上方輸入機關的關鍵字，關鍵字可以用空格分開，如"台北 立法院"。就出現搜尋的結果。點選搜尋的結果，進入該單位的頁面。頁面顯示如名稱、縣市、負責人、上方單位、照片等資訊。點擊電話開始撥電話。

公家機關頁面：
1.  顯示地圖、地址
> 不用顯示地圖會比較簡單， Open in in google Map or 內建地圖
> [name=Superbil]

2.  liked, call phone, share
3.  Related websites

### DB:

- ~o~~rganization~~:~
    - ~機關名稱~
    - ~地址~
    - ~電話~
- ~contact (ly)~
    - ~姓名~
- favorites:
    - org.id
    - 標記 (BOOL)

org <-> fav 的關係是一對一

直接下 request [http://pgrest.io/hychen/api.addressbook/v0/collections/organizations?q=](http://pgrest.io/hychen/api.addressbook/v0/collections/organizations?q=){"name":{"$matches":"questString"}}

### 分工及成員

- superbil
    - [x] 資料庫連接
- allenlinl
    - [x] 查詢頁面
    - [ ] 標記頁面
    - [ ] 設定頁面

### 其他

- 政府機關沒有圖片、人物有，政府機關就用首頁那張圖，人物若沒有才用首頁那張

