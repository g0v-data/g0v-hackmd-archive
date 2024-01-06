---
title: "⭐ hackfoldr 使用說明"
tags: 新手教學,hackpad
---

> [點此觀看原始內容](https://g0v.hackpad.tw/b80fhUVlnBe)


你知道嗎？近來的太陽花（ [http://g0v.today](http://g0v.today) ）、停建核四（[http://nonuke.today](http://nonuke.today) ）等公民運動，都採用 hackfoldr（唸作 hack-folder）來架設資訊入口網站。

hackfoldr 是 g0v 開源專案之一，本來是為了整理社群在黑客松產出的大量文件而誕生。現在，它是個開放給所有人使用的平台，你也可以為專案、活動，建立屬於自己的「黑客公事包」，讓所有文件、網頁一目了然。

:warning: 如果你希望用 hackfoldr 整合緊急或災難事件（例如 801 高雄氣爆）紛雜的資訊，建議同步參閱 [hackfoldr 災況資訊整合 SOP](https://g0v.hackpad.tw/QXHns2XZrIo)。

以下，說明開始（原文轉自 [http://hackfoldr.org/about](http://hackfoldr.org/about)，並補註使用者觀點說明。如有版本差異，請以原始網址內容為準。）

## Welcome to Hackfoldr

Hackfoldr 是你的黑客公事包，用一個網址就可以和夥伴們分享所有的專案文件！ :D

## 為你的專案製作 hackfoldr

**建立 hackfoldr**
- 想好專案英文網址名稱（例如：your-project-name）
- 在瀏覽器網址列輸入「hackfoldr.org/(你的專案的英文網址名稱)」

恭喜！你已經建立自己的 hackfoldr 了！[hackfoldr ](https://g0v.hackpad.tw/b80fhUVlnBe)

###  自訂 hackfoldr

- 點左上 home 圖案旁文字連結，會自動在新分頁打開 ethercalc，也就是專案網址的後台
> ethercalc 使用上非常類似 google spreadsheet 試算表，這裡的更新會直接顯示於 hackfoldr 前端
> [name=venev]

- 在 B2 格子中輸入本 hackfoldr 名稱（通常是中文）
- 接著從第 3 行開始，可以增加你想收集的網址
- 輸入格式為：在 B3 中輸入第一份文件名稱，A3 格子中輸入第一份文件網址
- 以此類推，把所有文件的顯示名稱和網址都輸入進去
- 切回「hackfoldr.org/(你的專案的英文網址名稱)」這個瀏覽器分頁
- 按 F5 / Ctrl + R 重新整理頁面

恭喜！你已經打造出屬於自己的 hackfoldr 了！

### hackfoldr 進階用法

- 第3欄的格子為參數設定，常用的有：
    - '{"expand":true} 為資料夾預設展開、false為關；
    - '{"target":"_blank"} 為此連結開啟新視窗
- 第4欄的格子為註解，主要有四種型別：info、warning、important、issue，打法為 '註解:型別
- 顏色：藍:info、橘:warning、紅:important、灰:issue
- 第1欄的格子網址多空一格會成為子目錄，例：A3為'www.example.com，A4為' www.google.com，則A3變為資料夾，A4為A3子目錄

註：使用 ethercalc 不需登入，編輯後即自動存檔。如果想修改 ethercalc 試算表的名稱，直接開新的 ethercalc.org 網址後，將舊試算表的內容剪貼過來即可。

### 圖示說明

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_a6af7776de3bd9f6f68940f76de4174d)



### hackfoldr about

- hackfoldr 是 clkao 為了 g0v 黑客松活動而開發的開源專案，原始碼也在[github](https://github.com/hackfoldr/hackfoldr)上。
> 功能建議、bug 回報，請到 github 提出 issue。
> [name=venev]


## 使用 Google Spreadsheet 管理 hackfoldr

Live Demo 影片 [http://www.youtube.com/watch?v=B9jAzO1oI68&t=8h3m25s](http://www.youtube.com/watch?v=B9jAzO1oI68&t=8h3m25s)

在某些特殊情況（例如佔領立法院時期），ethercalc 管理後台「無須登入、人人可編輯」的協作特色，會影響協作進度（例如資料遭到惡意清除、需從備份回復），此時可考慮在初期「發散式」的連結收集後，轉向「收歛式」，改用 Google Spreadsheet 後端，來限定某些具編輯權限的人。方式如下:

1.  開一個 Google 試算表，選「File (檔案)」>「Publish to the web... (發布到網頁上)」再按「Start publishing (開始發佈)」、「OK (確定)」。
2.  取得發佈網址，如 [https://docs.google.com/spreadsheets/d/1Wbk0HiD4yRVus3qXzA2d8a7LmZ3wYWCSWWdGD39sWsU/pubhtml](https://docs.google.com/spreadsheets/d/1Wbk0HiD4yRVus3qXzA2d8a7LmZ3wYWCSWWdGD39sWsU/pubhtml)
3.  在 /d/ 後面，直到下個斜線為止的文數字就是試算表的 ID，放到 hackfoldr.org/ 後面即為網址，例如 [http://hackfoldr.org/1Wbk0HiD4yRVus3qXzA2d8a7LmZ3wYWCSWWdGD39sWsU](http://hackfoldr.org/1Wbk0HiD4yRVus3qXzA2d8a7LmZ3wYWCSWWdGD39sWsU)
4.  如有需要，可運用 bit.ly 等短網址服務自訂網址。

試算表內的格式和 ethercalc 相同，但**目前不支援空白行**，第一個空白行以下的資料將被忽略。

### 2014_08-05 新功能

於 ethercalc 的 A1 欄位填入 Google Spreadsheet ID ，即可在維持原本「hackfoldr.org/(你的專案的英文網址名稱)」的狀況下使用 Google Spreadsheet 作為後端，來限定只有某些具編輯權限的人才能修改。( ref [IRC Log](http://logbot.g0v.tw/channel/g0v.tw/2014-08-05#108) )
> 請問現在google 試算表 已經沒有發怖的功能   那可以怎麼上鎖呢？
> [name=志工 T]

> 發佈功能在 google spreadsheet 選擇 **檔案** → **發佈到網路**，相關的教學可看↑上方的 LiveDemo影片。
> [name=lanfon]



## Hackfoldr / Ethercalc 的備份與還原

### 手動備份

方法一：
        開 excel (或是google spreadsheet) 把所有欄位全選後複製貼上。
方法二：
        點選 A 欄左邊的 :arrow\_right\_hook: ，存成 csv。
> 不存成 html 的好處是， spreadsheet 可以直接讀 csv 。
> [name=lanfon]

> excel 如果打開來會是亂碼.... 那是 編碼的關係XD
> [name=lanfon]

### 系統自動備份清單

[https://ethercalc.org/static/history/](https://ethercalc.org/static/history/(你的專案的英文網址名稱)/)[(你的專案的英文網址名稱)](https://ethercalc.org/static/history/(你的專案的英文網址名稱)/)[/](https://ethercalc.org/static/history/(你的專案的英文網址名稱)/)
> 這個不見得每個 hackfoldr 都會有...QQ 不知道是不是把功能關了
> [name=lanfon]

> 在 EtherCalc 上的都有，在 Google Doc 上的沒有。如果有缺請跟我說。
> [name=Audrey T]

> 昨天半夜的時候讀不到QAQQ (resp 404) 想說是不是特殊情況才會開, Google Doc 有內建的版本修定應該可以直接用XD
> [name=lanfon]

### 還原方法

方法一：
            使用 ethercalc 的復原界面（待補）

方法二：
```
目前的復原方式可以用 Clipboard -> SocialCalc save format -> .txt 貼進文字框 -> load SC clipboard with this -> 回 A1 貼上 來達成

```
方法三：
```
使用命令列的回復方式（cmd.exe、powershell、bash、terminal）
curl https://ethercalc.org/static/history//(欲還原的文件編號).txt)(你的專案的英文網址名稱)/(欲還原的文件編號).txt)//(欲還原的文件編號).txt)(/(欲還原的文件編號).txt)欲還原的文件編號/(欲還原的文件編號).txt))/(欲還原的文件編號).txt).txt/(欲還原的文件編號).txt) | curl -i -X PUT --data-binary @- https://ethercalc.org/_/(你的專案的英文網址名稱)/(%E6%96%87%E4%BB%B6%E7%B7%A8%E8%99%9F).txt)

