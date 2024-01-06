---
title: "Hackfoldr 2.0 功能列表"
tags: hackpad
---

# Hackfoldr 2.0 功能列表

> [點此觀看原始內容](https://g0v.hackpad.tw/0.jmm9642fog5vcxr)


範例：[http://hack.etblue.tw/welcome-to-hackfoldr](http://hack.etblue.tw/welcome-to-hackfoldr)

## 前台使用者導覽


### 時光麵包屑

- 按時鐘按鈕，可以找到之前看過的 foldr（html5 local storage）
    - 在同一台電腦、同一個瀏覽器看過的 foldr，都會被記住

### 說明文件連結

- 按問號按鈕，可以連到說明文件的 foldr。說明文件是 hackpad，所以可以直接在文件上留言發問或回報臭蟲（html href）

### 伸縮鏡頭

- 按放大鏡按鈕，可以單獨放大右邊內容區域（css zoom / transform）
- 在同一台電腦、同一個瀏覽器設定的放大比例，都會被記住，下次打開任一 foldr 都會套用之前設定的放大比例（html5 local storage）

### 全視窗

- 按 < 按鈕，可以把側邊欄收起來，讓內容放大到全視窗 -3rem（jquery）
    - 這個功能只有在 desktop layout 會用到

### 分享首頁

- 按 foldr 標題，可以回到 foldr 首頁，網址列上面會出現漂亮的、容易分享的網址（javascript）
- 從 foldr 首頁進入，會自動秀出第一個連結網頁的內容（javascript）

### 分享內頁

- 按選單上的連結，網址列上面會出現該內頁的獨立網址（javascript）
- 從內頁獨立網址進入，會自動秀出指定的內頁（javascript）

### 展開 subfoldr

- 按一下 subfoldr 標題可以展開或收合（semantic ui accordion）
- 從內頁獨立網址進入，包含那個網址的 subfoldr 會自動展開（jquery）
- 沒有特別指定的話，包含三個以下項目的 subfoldr 會預設展開（jquery）

### 行動版

- 視窗寬度在 1024px、640px、480px 時各自會套用不同的版面（ css media query）
- 手機或平板上畫面不會被瀏覽器自動縮小（css viewport）

### 自動圖示

- 會在新分頁打開的連結，會自動標註新分頁圖示（jquery）
- 常用服務如 hackpad、gdocs、youtube、kktix …等的連結項目，會顯示對應的圖示（handlebars）
    - 目前沒有直接取 favicon 來用，是因為各家 favicon 設計品質良莠不齊，怕破壞畫面… XD

## 後台編輯與權限控管


↓gui and browser↓

### 指定 foldr 首頁網址

- 好記網址：ethercalc id，如果沒跟別人撞名的話（ethercalc）
- 隱密網址：google spreadsheet id（google docs）

### 進入編輯模式

- 首頁網址後面加 /edit（javascript）
- 按鉛筆按鈕（jquery）

↓gui and spreadsheet↓

### 在 foldr 中加入網址

- 編輯模式中按 \+ 按鈕後填寫表單（semantic ui form）
- 編輯模式中在 spreadsheet 手動填入網址與想呈現的標題到正確的欄位（ethercalc）

### 新增 hackpad 文件同時在 foldr 中加入網址

- 編輯模式中按 \+ 按鈕後填寫表單（semantic ui form）
- 編輯模式中在 spreadsheet 手動填入網址與想呈現的標題到正確的欄位。網址可以是 https://*.hackpad.com/ 後面接想要的 pad id，如果沒跟別人撞名的話，按下網址會自動打開新的 hackpad（hackpad, ethercalc）

### 調整順序

- 編輯模式中拖曳左邊的選單項目（jquery ui sortable）
- 編輯模式中在 spreadsheet 手動複製、貼上、插入、刪除（ethercalc）

↓spreadsheet only↓

### 加標籤

- 連結網址的 column d 可設定標籤顏色和內容文字（handlebars）

### 讓選單項目在新視窗打開

- 連結網址的 column c 包含 blank 關鍵字時，該連結會設定為 target = "_blank"（handlebars）

### 新增子資料夾

- column a 空白，但 column b 有資料時，會被視為子資料夾（javascript）

### 讓選單項目回到頂層

- column a 開頭為 < 號時，以下的連結項目會被歸到 subfoldr 之外，變回頂層項目（javascript）

### 設定 foldr 選項

- foldr 標題列的 column c 包含 hide 關鍵字時，使用者無法直接從 ui 中打開試算表（javascript）
- foldr 標題列的 column c 包含 unsortable 關鍵字時，使用者無法拖曳調整順序（javascript）

### 設定後台編輯權限

- 使用 ethercalc 當資料來源時，任何人都可編輯，但可利用鎖定功能來減少誤編（ethercalc）
- 使用 google spreadsheet 當資料來源時，可利用 google docs 的權限管理（google docs）

### 設定跳板

- 需要擁有 ethercalc 的好看網址，又希望使用 google spreadsheet 當資料來源時，可將 ethercalc 設定為跳板，自動導向到指定的 google spreadsheet，詳附錄（javascript）
作法:
step1: 在beta.hackfoldr.org/(key上你想要的英文代號)
ex :[http://beta.hackfoldr.org/205eoc](http://beta.hackfoldr.org/205eoc)
step2: 會出現一個ethercalc的表格，在其a1欄填上google spreadsheet id 即可



##

本區內容移至 [Hackfoldr 2.0 教學 - 架設自己的 hackfoldr](https://g0v.hackpad.tw/G7idRJqbG3I#Hackfoldr-2.0-教學---架設自己的-hackfoldr)
本區內容移至 [Hackfoldr 2.0 儲存格語法](https://g0v.hackpad.tw/jfLiSxnllO6#Hackfoldr-2.0-儲存格語法)

