---
title: "開放政治獻金文字校正管理系統"
tags: CY 零時監察院,hackpad
---

# 開放政治獻金文字校正管理系統

> [點此觀看原始內容](https://g0v.hackpad.tw/UChWZQoE6DG)


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_fdcbae496f9e9c54219b50c75031428e)

上圖使用 mysql workbench 繪製，原始檔案 -
[https://github.com/kiang/tw-campaign-finance/blob/master/peopleocr/kiang/db.mwb](https://github.com/kiang/tw-campaign-finance/blob/master/peopleocr/kiang/db.mwb)

資料表：
1.  documents - PDF 文件資料
2.  pages - 個別頁面資料
3.  cell_text - 校正文字內容
4.  messages - 頁面訊息通報

使用者故事：
1.  使用者進入系統後會自動提示輸入暱稱，作為個別資料表記錄 author 欄位用，資料會儲存在 cookie 免去重複輸入
2.  入口畫面呈現個別文件完成狀態，同時提供一個快速開始按鈕，使用者點選後系統自動挑選一個 pages.locked\_at < now() & pages.completed\_at is null 的 pages 讓使用者線上進行校對
3.  校對頁面直接描繪了頁面的表格，並且在每一格旁邊呈現對應的圖片方便使用者進行校對。進入校對的同時會將 now() + 5 minutes 時間寫入 pages.locked_at 避免有人操作同樣頁面
4.  校對過程自動每隔 15 秒就儲存結果（如果有異動的話），或是使用者離開校對頁面時進行儲存，結果都會放在 cell\_text.cells 中，每次更新時也將 now() + 5 minutes 時間寫入 pages.locked\_at 避免有人操作同樣頁面
5.  校對完成後，會將 now() + 3 days 寫入 pages.locked_at ，接著使用者可以點選 下一頁 進行另外一頁的校對工作，重複 2, 3, 4 的流程
6.  審閱者進入系統後可以看到新建立的校對內容，進行審閱如果完成就會將該頁關閉（將 now() 寫入 pages.completed\_at, documents.count\_completed += 1 ），如果尚未完成就把 now() 寫入 pages.locked_at 來釋放頁面鎖定
7.  如果使用者進入的 pages 存在舊有 cell_text 就會取出最新的一筆作為草稿基礎
8.  如果使用者發現個別頁面圖片存在著問題（像是圖片顛倒、圖片無法清楚辨識等），或是有相關問題想要反應，可以透過頁面留言板發布。新建立的留言 messages.is\_public = 0 ，在審閱者確認要公開訊息後將 messages.is\_public = 1 ，公開留言內容

