---
title: "PM2.5 空污視覺化時間軸功能"
tags: hackpad
---

# PM2.5 空污視覺化時間軸功能

> [點此觀看原始內容](https://g0v.hackpad.tw/MdxrRL6f6D2)


### 專案原始碼：

[https://github.com/g0v/env.g0v.tw](https://github.com/g0v/env.g0v.tw)
### 原 fb g0v 後勤中心討論串：

[https://www.facebook.com/groups/g0v.general/permalink/794389260637482/](https://www.facebook.com/groups/g0v.general/permalink/794389260637482/)

### 需求：

1.  可查詢 [http://env.g0v.tw/air/](http://env.g0v.tw/air/) 的舊資料，利用過往圖資產生空污動畫。
2.  改為每30分鐘甚至10分鐘更新一次。


### 問題

- 時間精度是依賴氣象局資料他們的實際更新頻率來決定。
- [x]  graphite 資料停在四月一日，需更新。

### 處理說明（gugod++）：

[gugod](https://www.facebook.com/groups/g0v.general/permalink/794389260637482/?comment_id=799606703449071&offset=0&total_comments=35&comment_tracking=%7B%22tn%22%3A%22R4%22%7D): 「還沒全部做完，但先來中途說明一下... 」

        目前已經加上「時間參數」，可以手動在空污圖網址後加上 `?t=<數字>` 來看歷史記錄。例：
        [http://env.g0v.tw/air/?t=201505020105](http://env.g0v.tw/air/?t=201505020105)

        這數字個格式為「年月日時分」，但對應到的時間是是 GMT 時區，而非台灣的 CST 時區。
        在參數 "t" 有值時，會去從以下的網址抓取舊的空污資料集：
        [https://github.com/g0v-data/mirror-2015/tree/master/epa/aqx](https://github.com/g0v-data/mirror-2015/tree/master/epa/aqx)
        以 "t=201505020105" 為例，對應到的資料集網址為
        [https://github.com/....../epa/aqx/2015-05-02/01-05.csv](https://github.com/....../epa/aqx/2015-05-02/01-05.csv)
        只要在 g0v-data/mirror-2015 中有 CSV 檔案，就可以推算出 "t" 的值，畫出空污圖。
        例如，此頁中有一月一日的空污資料集：
        [https://github.com/....../tree/master/epa/aqx/2015-01-01/](https://github.com/....../tree/master/epa/aqx/2015-01-01/)

        00-05.csv
        01-05.csv
        02-05.csv
        03-05.csv
        ...

        t 值就是把檔名中的 "-" 字符去掉，並在前方補上日期，

        201501010005
        201501010105
        201501010205
        201501010305
        ...

        另外做出時間軸介面後就可以省去腦補 t 值的功夫，但在除那之外，另外尚在設定
        空污資料集的自動更新。目前我只手動做了一次，所以停在五月二日。

### UI 發想

- 類似 [calendar chart](https://developers.google.com/chart/interactive/docs/gallery/calendar) （每天一小點，可顯示當日最糟數值的顏色），點選後跳至當日


### 其他

- 使用 DTM 資料模擬山區屏蔽（比測站高 100 公尺就減少 x%)

