# 違章工廠舉報系統第44次小聚

###### tags: `Disfactory` `違章工廠` `違章工廠舉報系統`

時間：20200812
地點：地公北辦
線上：https://meet.google.com/egx-zvjk-ouv


## 參與者簽到：

* deeper
* oriyar
* ael
* 小白
* jsaon
* yellowsoar
* 鉦寰
* swind
* yukai
* sandra

## 待討論
- 議題面

- 後端
    - [x] 公文回覆追蹤 table 欄位確定 @deeper @cph @yellowsoar @swind @toby @ael
        - [x] cross-table fields
        - [x] document tag
    - [x] Digital Ocean Team
    - [x] 跟小白討論工廠編號

## 會議記錄
- 本週GA數據
    - 使用者數量：237 -> 244
    - 新使用者數量：196 -> 196
    - 平均工作階段時間：02:17 -> 03:48
    - 跳出率：21.78% -> 16.17%
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f6ff8dc045f29088621baf7f8b84d45b.png)

    - 相較上週

| 使用者 | 新使用者 | 跳出率 |
| ----- | ------ | -------|
| +7   |   +0  | -5.61% |


- 來源
    - disfactory.tw
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_cf1abcba08ef199bb978263d436f8193.png)
    - about.disfactory.tw
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_47b345b46618c224a71e33815e4bc986.png)

- 後台新spec
    - 已完成討論
        - `document` list view @littlewhite @jsaon
        - `document single page` @swind
        - `followup`
    - 待討論
        - `user model`
        - `review record`
    - 待詢問
        - `立委縣市contact` @IU @swind
        - `GovAgency` @deeper修改後給小白

- 後端
    - 流水號
        - ~~無腦一點~~
        - 累加不回溯
        - 規則
            - [民國年份(3碼)][000]
            - 2020年 ex:109001, 109002, 109003, 109004...
            - 2021年1月1日之後的公文 ex:110001, 110002, 110003, 110004... 
    - CET狀態
        - tag還沒做
    - 希望可以改變部分測試的可維護性
    - DigitalOcean Team setting


## ael 紀錄後端公文追蹤討論結果

### 1. Create document (Action) on Factory (List View) @LittleWhite @jsaon

=> 自動產生 doc_id 和把 Factory 資料塞進 Document(table)
=> doc_id 是產生流水號，就算不小心誤按在 Document table 刪掉後，流水號繼續編下去
=> @deeper 要給流水號規則

### 2. Document (table) @LittleWhite @jsaon
- `id`
- `factory_id`(我忘了跨表格的命名方式)
- `created_at`
- `last_updated`:公文上任何欄位上次被修改的時間
- `cet_staff`：公文負責人
- `cet_report_status`: tag (many to many)
- `cet_next`： CET 下一步要做什麼。 tag（不太會同時有多個）
- `cet_next_last_updated` 
- `gov_response_status`: multiple tags (many to many)。可能會有針對四個地方政府單位進度不同的 tag。
- `display_status`:tag（不太會同時有多個，但是要保留不是線性更新進度的可能，可能會跳來跳去）。前端顯示給使用者看的，只有這個 tag 要加上 timestamp，記錄新增和刪除特定 tag 的時間
- 縣市 
- 鄉鎮區
- 政府承辦人、單位、電話（這邊忘了討論怎麼存，因為會有不只一個單位的承辦人）
- `note`: long paragraph. 讓志工打電話時可以紀錄進度。
- 政府公文連結
- 政府回函 summary
- lat
- lng

### 3. Document (List View) @LittleWhite @jsaon
- `id`
- `factory_id`
- `created_at`: [sort]
- `last_updated`：[sort] 
- `cet_staff`
- `cet_report_status`: [filter] 
- `cet_next`： [filter] 
- `cet_next_last_updated` [sort]
- `gov_response_status`: 
- `display_status`:[filter] 
- 縣市 [filter]
- 鄉鎮區 [filter]
- 政府承辦人 [filter]


### 4. Print documents (Action) on Document (List View) @Swind
- 自動產生公文下載

### 5. Document (Single Page) @Swind

- doc_id
- ==Factory info embedded（待補指定欄位，應該就是公文上印出來的欄位）==
    - factory_id
    - image
    - ...
- All fields in Document table: 需要 deeper 給顯示優先順序

### 6. Display_status (原本的FollowUp table)
`timestamp`
`doc_id`
`display_status`

新增和刪除都要記錄時間

### 7. 整合縣市->立委 contact @Swind
- @IU 已爬好 
https://github.com/Disfactory/findTaiwanLegislator
- @swind 接下來要整合到印公文的 process

(8/18 已做完)

### 8. User Model @Toby (not urgent)
- name
- email
- role: staff, volunteer, tech

### 9. GovAgency (承辦人聯絡清單) @deeper
- editable
- low priority
- 主要是可以在 Document table 被 refer 承辦人，可以 filter 承辦人和方便打電話

### 10. Review (table) => low priority
 on Factory page
 - reviewer
 - image_check (null)
 - if_after_2016 (null)
 - factory_id


### 加入農委會新增的圖資
ael: 先 pending，因為 API 被鎖無法重現，可能資料來源會被質疑。

## 下次待討論事項
