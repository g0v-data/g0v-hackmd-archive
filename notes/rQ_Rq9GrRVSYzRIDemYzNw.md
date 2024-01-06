---
title: "藥要看 API (alpha)"
tags: g0v idea pool,hackpad
---

# 藥要看 API (alpha)

> [點此觀看原始內容](https://g0v.hackpad.tw/V9f5Q6QHUyZ)


基本上每個前端的網址前面加上 /api 就是對應的 api 路徑 ( 像是 [http://drugs.olc.tw/drugs/index/page:2](http://drugs.olc.tw/drugs/index/page:2) 的 api 位置就是 [http://drugs.olc.tw/api/drugs/index/page:2](http://drugs.olc.tw/api/drugs/index/page:2) )，網頁最下方也可以看到 "本頁 API" 的連結，任何的 api 網址加上 ?pretty 就會用比較容易閱讀的格式呈現

\*\* 如果需要大量存取，麻煩[直接跟我聯絡](http://k.olc.tw/%E8%81%AF%E7%B5%A1%E6%98%8E%E5%AE%97/) ，我可以隨時把資料庫匯出給你，機器超弱的...

欄位說明
Drug
| Column | Type | Null | Default | Comments | MIME |
| --- | --- | --- | --- | --- | --- |
| id | binary(36) | No |  | 主索引 |  |
| license_uuid | binary(36) | No |  | 藥證索引 |  |
| license_id | varchar(32) | No |  | 許可證字號 |  |
| cancel_status | varchar(32) | Yes | NULL | 註銷狀態 |  |
| cancel_date | date | Yes | NULL | 註銷日期 |  |
| cancel_reason | varchar(255) | Yes | NULL | 註銷理由 |  |
| expired_date | date | No |  | 有效日期 |  |
| license_date | date | No |  | 發證日期 |  |
| license_type | varchar(32) | Yes | NULL | 許可證種類 |  |
| old_id | varchar(32) | Yes | NULL | 舊證字號 |  |
| document_id | varchar(32) | Yes | NULL | 通關簽審文件編號 |  |
| name | varchar(128) | Yes | NULL | 中文品名 |  |
| name_english | varchar(128) | Yes | NULL | 英文品名 |  |
| disease | text | Yes | NULL | 適應症 |  |
| formulation | varchar(255) | Yes | NULL | 劑型 |  |
| package | varchar(255) | Yes | NULL | 包裝 |  |
| type | varchar(128) | Yes | NULL | 藥品類別 |  |
| class | varchar(128) | Yes | NULL | 管制藥品分類級別 |  |
| ingredient | text | Yes | NULL | 主成分略述 |  |
| vendor | varchar(255) | Yes | NULL | 申請商名稱 |  |
| vendor_address | varchar(255) | Yes | NULL | 申請商地址 |  |
| vendor_id | varchar(32) | Yes | NULL | 申請商統一編號 |  |
| manufacturer | varchar(255) | Yes | NULL | 製造商名稱 |  |
| manufacturer_address | varchar(255) | Yes | NULL | 製造廠廠址 |  |
| manufacturer_office | varchar(255) | Yes | NULL | 製造廠公司地址 |  |
| manufacturer_country | varchar(64) | Yes | NULL | 製造廠國別 |  |
| manufacturer_description | text | Yes | NULL | 製程 |  |
| submitted | date | No |  | 異動日期 |  |
| usage | text | Yes | NULL | 用法用量 |  |
| package_note | text | Yes | NULL | 包裝 |  |
| barcode | varchar(64) | Yes | NULL | 國際條碼 |  |

License
| Column | Type | Null | Default | Comments | MIME |
| --- | --- | --- | --- | --- | --- |
| id | binary(36) | No |  | 主索引 |  |
| license_id | varchar(32) | No |  | 藥證編號 |  |
| nhi_id | varchar(255) | No |  | 健保代碼(逗點分隔) |  |
| shape | varchar(32) | Yes | NULL | 形狀 |  |
| s_type | varchar(32) | Yes | NULL | 特殊劑型 |  |
| color | varchar(32) | Yes | NULL | 顏色 |  |
| odor | varchar(32) | Yes | NULL | 特殊氣味 |  |
| abrasion | varchar(32) | Yes | NULL | 刻痕 |  |
| size | varchar(32) | Yes | NULL | 外觀尺寸 |  |
| note_1 | varchar(128) | Yes | NULL | 標註一 |  |
| note_2 | varchar(128) | Yes | NULL | 標註二 |  |
| image | varchar(64) | Yes | NULL | 圖片 |  |

Category
| Column | Type | Null | Default | Comments | MIME |
| --- | --- | --- | --- | --- | --- |
| id | int(10) | No |  | 主索引 |  |
| parent_id | int(10) | No |  | 父分類 |  |
| code | varchar(16) | No |  | 分類代碼 |  |
| name | varchar(255) | No |  | 原文名稱 |  |
| name_chinese | varchar(255) | No |  | 中文名稱 |  |
| lft | int(10) | No |  | 左索引 |  |
| rght | int(10) | No |  | 右索引 |  |

CategoriesLicense
| Column | Type | Null | Default | Comments | MIME |
| --- | --- | --- | --- | --- | --- |
| id | binary(36) | No |  | 主索引 |  |
| category_id | int(10) | No |  | 分類索引 |  |
| license_id | binary(36) | No |  | 藥證索引 |  |
| type | varchar(32) | No |  | 分類類型 |  |

Ingredient
| Column | Type | Null | Default | Comments | MIME |
| --- | --- | --- | --- | --- | --- |
| id | binary(36) | No |  | 主索引 |  |
| license_id | binary(36) | No |  | 藥證索引 |  |
| remark | varchar(128) | No |  | 處方標示 |  |
| name | varchar(128) | No |  | 成分名稱 |  |
| dosage_text | varchar(32) | No |  | 含量描述 |  |
| dosage | decimal(20,8) | No |  | 含量 |  |
| unit | varchar(32) | No |  | 含量單位 |  |

Link
| Column | Type | Null | Default | Comments | MIME |
| --- | --- | --- | --- | --- | --- |
| id | binary(36) | No |  | 主索引 |  |
| license_id | binary(36) | No |  | 藥證索引 |  |
| url | varchar(255) | No |  | 網址 |  |
| title | varchar(255) | No |  | 連結標題 |  |
| type | tinyint(3) | No |  | 類型 |  |
| sort | int(10) | No |  | 排序 |  |

Price
| Column | Type | Null | Default | Comments | MIME |
| --- | --- | --- | --- | --- | --- |
| id | binary(36) | No |  |  |  |
| license_id | binary(36) | No |  |  |  |
| nhi_id | varchar(32) | No |  | 健保代碼 |  |
| nhi_dosage | varchar(32) | Yes | NULL | 用量 |  |
| nhi_unit | varchar(32) | Yes | NULL | 用量單位 |  |
| date_begin | date | No |  | 開始日期 |  |
| date_end | date | No |  | 結束日期 |  |
| nhi_price | decimal(10,2) | No |  | 健保價格 |  |

