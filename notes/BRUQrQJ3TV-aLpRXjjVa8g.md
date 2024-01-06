中天新聞分析
==========

步驟
---
* 先下載 [中天52CH新聞 Youtube 頻道](https://www.youtube.com/channel/UCpu3bemTQwAU8PqM4kJdoEQ) 所有新聞
    * [程式碼](https://github.com/ronnywang/twtvnews/blob/master/get-youtube-video.php)
    * [記錄](https://gist.github.com/076e184fee54b4a15c2c767a9e4c1da0)
* 針對每隻影音的主標題區域逐秒比較計分
    * 主標題區域：325x24+100+193
    * 用 ImageMagick 的 compare ，AE 演算法，fuzz=10% 計算逐秒分數
    * 逐秒切割計算 [程式碼](https://github.com/ronnywang/twtvnews/blob/master/youtube-crop.php)
* 人工檢查每日標題是否有誤判情況
    * 開啟 http://your-server/group-yt-crop.php?date=YYYYMMDD
    * 群組顯示 [程式碼](https://github.com/ronnywang/twtvnews/blob/master/group-yt-crop.php)
    * 寫入 [skip-crop.csv](https://github.com/ronnywang/twtvnews/blob/master/skip-crop.csv)
* 產生每日主標題合併檔
    * [產生程式](https://github.com/ronnywang/twtvnews/blob/master/get-youtube-crop-merge.php)
    * [成果](https://github.com/ronnywang/twtvnews-youtube-titles/tree/gh-pages/ctitv)
        * /ctitv/YYYYMMDD.png
            * 當天主標題合併成一張圖的大圖，一個標題大小是 325x24
        * /ctitv/YYYYMMDD.csv
            * 各行圖片對應到的標題列表
* 透過每日影像跟前兩日的 Youtube 新聞主標題做比照對應
    
    
TVBS 主標分離
-----------

* ffmpeg 取得每秒畫面 (`ffmpeg -i 2019032112.ts -r 1 2019032112/%05d.jpg`)
* 從 frame 分離 title
* 找出一個 title 當作 reference 取得前方一塊的顏色 (0, 20, 3, 23)
* Iterate 過所有 title, 連續 8 個畫面相同且為 title 的取出 (跟 title reference compare)

已知問題：
* TVBS 有黃色底的快訊
* 沒有文字的狀況 (報導結尾, 某些畫面只有藍色底...etc)


改只參考連續超過 8 個畫面，不跟 title reference 相比
* 可以拿出黃色底的快訊
* 但是會有廣告
* <del>拿 tesseract 測有沒有文字</del> (無效)

改正：
![](https://i.imgur.com/o6nhp3l.jpg)
* 擷取其他 static 部份當作 reference，能夠有效解決問題
* title 長度 mean 落在 25, std 17 (?),  median 20
    * 擷取超過 10 個畫面的 (能夠有效濾掉 speaker subtitle)