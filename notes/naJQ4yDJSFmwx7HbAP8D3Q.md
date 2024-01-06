---
title: "Excel 轉完美 CSV"
tags: hackpad
---

# Excel 轉完美 CSV

> [點此觀看原始內容](https://g0v.hackpad.tw/dLlq1x8Y2YM)


考慮到政府為了衝三星 Open Data ，造成常常放出直接 Excel 轉 CSV 的檔案，合併儲存格資訊流失造成 CSV 亂七八糟，所以這邊想要做一個系統可以把 Excel 丟進去，可以產生出完美的 CSV

### 完美CSV定義

- UTF-8
- 逗點分格
- 阿拉伯數字就是數字，沒有用逗點分隔
- 第一行是欄位名稱，第二行就是資料開始，除此以外沒有其他東西
- 欄位名稱不會重覆 (不過有兩個「日期」欄位)
- 該是數字欄位就全部都是數字、該是日期欄位就都是日期

### 常見需處理情況

1.  一張 sheet 裡面放了 2 ~ 3 個表格
2.  前幾欄是 title 、使用單位 等資訊
3.  使用合併儲存格的欄位要合併成一格
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_a4ef8dae6e8bc7334481b7766af8281a)

    上面最好改成 台北市/人數  台北市/比例 新北市/人數  新北市/比例
1.  使用合併儲存格

