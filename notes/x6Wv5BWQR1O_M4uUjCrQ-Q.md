社會經濟資料庫資料結構
=========

這邊筆記一下社會經濟資料庫的現狀
資料結果： https://docs.google.com/spreadsheets/d/1VnL-xBALMihqMSZvS8DlQaf1I7Kfn0BT323-DQPs1u8/edit?usp=sharing

- 所有資料都有 Info.ini, Schema.ini ，記錄每個資料的 meta 及每個 column 的 meta。

## 列表
- MAIN_SUB_PRIDUCT_ID: ID + SUB_PRODUCT_ID
- SUB_PRODUCT_ID: 固定是 0
- ID: 流水ID
- CODE	CNAME	APPLY_TYPE_ID	OPEN_TYPE_ID	STATUS_ID	TYPE_ID	USER_ID	CREATE_DATE	BOUNDARY_DESC	BOUNDARY_INDEX	STLAYER_NAME	STFILE_TYPE_ID	STTIME	METADATA_ID	NGIS_TYPE_DIVISION_ID	NGIS_TYPE_SECTION_ID	MID	MD_TYPE_ID	STUNIT_NAME	STUNIT_CODE	STUNIT_ID	STTIME_TW	STTIME_YEAR	STTIME_PART	APPLYERS	APPLYERS1	APPLYERS3	APPLYERS4	APPLYERS5		
## Info.ini
### 產品資訊
- 產品名稱
    - Ex: 100年3月全國15歲以上人口五歲年齡組統計_縣市
    - 名稱是唯一的
- 詮釋資料
    - Ex: TW-04-301000000A-010052
    - 詮釋資料再加上時間和行政區別才會是唯一的
- 分類
    - Ex: 40102
- 空間範圍
    - Ex: 全國
- 空間統計單元代碼
    - Ex: U01CO
    - U01 表示全國等級, U02 表示地方等級
    - U01CO, U01TO, U01VI 分別是縣市、鄉鎮、村里
    - U0200, U0201, U0202 分別是最小統計區、一級發布區、二級發布區
- 空間統計單元級別
    - Ex: U01
- 資料時間 STTIME
    - Ex: 100Y03M
- 取得日期 STTIME_TW
    - Ex: 104/4/13
### 共用性空間統計單元資訊
- 表示他跟哪些圖資可以連結起來
- TODO: 應該可以直接 link 到 map sheet
### 自設空間統計單元資訊
- 表示他有 X,Y 座標
- TODO: 可以變成 (x,y) sheet
