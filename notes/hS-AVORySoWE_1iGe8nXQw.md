---
title: "Hackfoldr 2.0 儲存格語法"
tags: hackpad
---

# Hackfoldr 2.0 儲存格語法

> [點此觀看原始內容](https://g0v.hackpad.tw/jfLiSxnllO6)

附錄：編輯試算表時，可以在儲存格內使用的語法1

## #，註解 (任一行裡的任一格)

一行裡面，有任一格子的開頭是 # 號，整行當會被標記成註解，標記成註解以後，就可以亂寫，不會影響到左邊的選單 XD 註解通常是用來留言，告訴其他人哪一格不要動之類的。

### google spreadsheet id (A1)

> 這在最新的Google Spreadsheet實驗過，格式都會跑掉，因此不建議使用。
> [name=John C]

> 2017 年 [cofacts 用這個功能](https://beta.hackfoldr.org/cofacts)是沒有問題的唷
> [name=Johnson L]

A1 格子的內容如果不是註解，而且又 >= 40 字元，會被當作是 google spreadsheed id 解讀，此時資料來源轉由 google spreadsheet 提供，ethercalc 本身只扮演提供好看網址的跳板。
#### 使用時機：

    在某些特殊情況，ethercalc 管理後台「無須登入、人人可編輯」的協作特色，會影響協作進度（例如資料遭到惡意清除、需從備份回復），此時可考慮在初期「發散式」的連結收集後，轉向「收歛式」，改用 Google Spreadsheet 後端，來限定某些具編輯權限的人。
#### 使用方式:

    1.  開一個 Google 試算表，選「File（檔案）」>「Publish to the web...（發布到網頁上）」再按「Start publishing（開始發佈）」、「OK（確定）」。
    2.  取得發佈網址，如 [https://docs.google.com/spreadsheets/d/1Wbk0HiD4yRVus3qXzA2d8a7LmZ3wYWCSWWdGD39sWsU/pubhtml](https://docs.google.com/spreadsheets/d/1Wbk0HiD4yRVus3qXzA2d8a7LmZ3wYWCSWWdGD39sWsU/pubhtml)
    3.  在 /d/ 後面，直到下個斜線為止的文數字就是試算表的 ID，放到 hackfoldr.org/ 後面即為網址，例如 [http://hackfoldr.org/1Wbk0HiD4yRVus3qXzA2d8a7LmZ3wYWCSWWdGD39sWsU](http://hackfoldr.org/1Wbk0HiD4yRVus3qXzA2d8a7LmZ3wYWCSWWdGD39sWsU)
    4.  運用以上方法時，如有需要，可運用 bit.ly 等短網址服務自訂網址。
    5.  或於 ethercalc 的 A1 欄位填入 Google Spreadsheet ID ，即可在維持原本「hackfoldr.org/（你的專案的英文網址名稱）」的狀況下使用 Google Spreadsheet 作為後端，來限定只有某些具編輯權限的人才能修改。(ref [IRC Log](http://logbot.g0v.tw/channel/g0v.tw/2014-08-05#108))
試算表內的格式和 ethercalc 相同，但**目前不支援空白行**，第一個空白行以下的資料將被忽略。

### 網址 (A coulmn)

就是網址…

### <，選單層級 (A coulmn)

< 代表接下來的連結是 top level，不會被收在 subfoldr 裡面

### 標題 (B column)

從上面數來第一個有資料的 B column 格子，就是 foldr 標題。在這之後：
- 當網址 A column 沒有資料時，B column 就是 subfoldr 標題
- 當網址 A column 有資料，且不是 < 或 > 時，B column 就是連結標題

### 選項 (C column)

foldr 標題的選項：
- hide - 隱藏後台，按鉛筆按鈕時試算表不會出現。但內行的人在網址輸入 /edit 還是可以看到試算表
- unsortable - 不可排序，按鉛筆按鈕後選單的拖曳排序功能不會啟動
subfoldr 的選項：
- expand - 預設展開
- collapse - 預設收合
- 如果沒特別設定，連結項目在 3 個以下的 subfoldr 會自動展開，超過 3 個的 subfoldr 會自動收合
link item 的選項：
- blank - 在新視窗打開連結
- 如果沒特別設定，一些已知的不可內嵌的網頁會自動設定成在新視窗打開

### 標籤 (D column, for link items only)

格式：
- 標籤內容 \- 會用預設的顏色（灰色）顯示標籤內容
- 標籤顏色 標籤內容 \- 會用指定的顏色顯示標籤內容
標籤顏色選項：
- 深色系
    - black
    - deep-green
    - teal
    - deep-blue
    - deep-purple
    - red
    - orange
- 淺色系
    - gray
    - green
    - blue
    - purple
    - pink
    - yellow


