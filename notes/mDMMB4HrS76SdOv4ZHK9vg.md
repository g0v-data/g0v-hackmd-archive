# admin router

## 商品管理 `product`
+ 商品提報 `/product/draft`
    + 單一商品提報內容查詢 `/product/draft/query`
    + 單一商品提報 `/product/draft/single`
    + 單一商品批次提報 `/product/draft/batch`
    + 選項內容管理 `/product/draft/option-content`

+ 銷售商品 `/product/sale`
    + 銷售商品內容查詢 `/product/sale/query`
    + 銷售商品內容 `/product/sale/content`

+ 銷售商品異動 `/product/change`
    + 銷售商品異動內容查詢 `/product/change/query`
    + 加減量申請 `/product/change/amount-apply`
    + 加減量歷史紀錄 `/product/change/amount-log`
    + 上下架申請(批次) `/product/change/shelve-apply`
    + 圖文異動申請 `/product/change/content-apply`
    + 變價申請 `/product/change/content-apply`

+ 行銷活動 `/product/marketing`
    + 折扣行銷活動查詢 `/product/marketing/discount-query`
    + 折扣行銷活動申請 `/product/marketing/discount-apply`
    + 贈品行銷活動查詢 `/product/marketing/giveaway-query`
    + 贈品行銷活動申請 `/product/marketing/giveaway-apply`


## 訂單管理 `order`
+ 出貨管理 `/order/ship`
    + 未出貨訂單 `/order/ship/unship`
    + 未押出貨客辦退 `/order/ship/undeposited`
    + 已出貨訂單 `/order/ship/shipped`
    + 
+ 回收管理 `/order/retract`
    + 未回收訂單 `/order/retract/unretracted`


## 活動管理 `campaign`
+ 站內活動 `/campaign/inside`
    + 活動查詢 `/campaign/inside/query`

## 供應商管理 `vendor`
+ 帳號管理 `/vendor/account`
    + 子帳號管理 `/vendor/account/sub-account`
    + 子帳號權限管理 `/vendor/account/sub-account-permission`

+ 資料管理 `/vendor/data`
    + 供應商資料異動 `/vendor/data/change`
    + 供應商資料異動查詢 `/vendor/data/change-query`

## 報表管理 `statement`
+ 銷售 `/statement/sales`
    + 銷售分析總覽 `/statement/sales/analysis`
    + 銷售排行榜 `/statement/sales/ranking`

+ 商品 `/statement/product`
    + 商品銷售明細 `/statement/product/sales-details`
    + 商品追蹤清單總覽 `/statement/product/trackingList`

+ 物流庫存 `/statement/inventory`
    + 高庫存商品 `/statement/inventory/over-stock`
    + 物流配送分析 `/statement/inventory/delivery-analysis`


## 帳務管理 `accounting`

## 聯絡窗口/反應 `contact`