---
title: "第二次視覺化分享會筆記"
tags: hackpad
---

# 第二次視覺化分享會筆記

> [點此觀看原始內容](https://g0v.hackpad.tw/oCKjReXddvH)


時間： 2016/01/10
地點： Appier 1F ( 暫定 )
人數： ~40
費用：0 ( 場地費均攤 )


## Opening




## Visual Information Seeking: Tight Coupling of Dynamic Query Filters with Starfield Displays

by Christopher Ahlberg
講者: Li-Ting Huang. [pdf](http://wiki.lri.fr/fondihm/_files/dynqueries-chi94-ahlberg.pdf) / [slide](https://drive.google.com/file/d/0B3GcrxhjXW_pNlcxUzh2RlVZbVE/view?usp=sharing)

互動式視覺化的先驅

三大原則
- Dynamic Query Filter（控制）
    - home finder 的範例
    - 元素週期表
- Starfield Displays（呈現）
    - 散佈圖 \+ zoom in/out + selection
- Tight Coupling（控制項與呈現端保持一致性）
    - 讓使用者可以了解軟體的狀態，也避免使用者作出無用的操作。
    - filter 自動對應 — 避免 filter 過程造成其它條件的空集合產生
    - 連續性的呈現
    - 漸進式的改良
    - detail on demand

範例：電影資料庫搜尋
- 因為大家都愛看電影，而且當時只有文字搜尋工具


Future work
- 更大型的資料、更完整的 query 方式
- fuzzy search
- zoom in/out 的順暢性
- tight coupling 機制邏輯性的驗證


## Florence Nightingale's Hockey Stick :The Real Message of her Rose Diagram

by Hugh Small
講者: Whitney Hung. [pdf](http://www.florence-nightingale-avenging-angel.co.uk/Nightingale_Hockey_Stick.pdf) / [slide](https://drive.google.com/open?id=0BxlKN3AQm1igeDJNcHU5NkdsQjA)
- Florence Nightingale introduction
    - 有人叫他雞冠圖 (coxcomb ) 但是是錯的
    - 用面積表示多少，每塊代表一個月份，不同顏色代表不同死因
    - 克里米亞戰爭：南丁格爾抵達發現環境很差，試著改善了環境，大大降低了死亡率

- 為什麼沒有用 bar chart
    - 不易比較前後兩年的差異
    - 不易比較季節的差異

- 拿破崙征戰俄羅斯
    - 灰色進攻、紅色撤退
    - 寬度：士兵數量
    - 溫度、日期
    - 地圖

- 用面積降低差異性的感受

討論
- 長條圖不適合週期性資料，雷達圖，或是像 GA 兩個週期疊合的方式
- 一月可以有兩個 bar，表達不同年份
- 一個問題一個圖，例如同一個季節畫在一起
- 生態如果要做三年的比較，會做三個長條圖，Y 軸對齊

> 今天不小心跳過很重要的部分在這裡補充
> [name=Whitney H]


補充說明：
Rose diagram V.S. Pie chart
Rose diagram的角度是固定的，以半徑作為參數; pie chart則是以角度作為變化參數
Rose diagram常應用在表示風的風向（方位）以及強度（半徑）稱作Wind rose
例：![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_7219d0c5faad87056147feca7937bee0)



## Beyond Memorability: Visualization Recognition and Recall

by Michelle A. Borkin
講者: YF Lin. [pdf](http://vcg.seas.harvard.edu/files/pfister/files/infovis_submission251-camera.pdf) / [slide](http://www.slideshare.net/iflin87048/beyond-memorability-visualization-recognition)

四大類作品來源
- 政府、資訊圖表、 媒體、科學
- 一秒的記憶實驗，分出「好記」、「不好記」的圖表
- 進一步探討
    - 是哪些元素在幫助記憶？
    - 一秒拉到十秒的話會有差嗎？
    - 要使用什麼元素來幫助？
- 從四大類作品來源中挑了 393 篇，33人無色盲，
- 實驗設計
    - Encoding：隨機看其中 100 篇，每張看十秒（Eye-Tracking Data）
    - Recognition：看過的 100 張 + 沒看過的 100 張隨機出現，每張 2 秒，間隔 0.5 秒，使用者若看到認為是前一步驟曾出現過的圖表，就按下空白鍵。利用按下空白鍵的方式，記錄辨識正確率(Hit Rate)。
    - Recall：集合所有正確辨識的作品，給受試者20 分鐘描述內容。
        ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_8fe81195d4343c5c0bd67a158ab12e17)
- 實驗數據分析
    - 眼球追蹤
    - Hit Rate = Hits / (Hits + Misses)，0 < HR < 1
    - 文字描述：專家系統。三位文字專家分析描述的內容，跟資訊圖表內資訊是否接近。
- 實驗結果
    - 好辨識的：兩秒鐘看中央即可辨識（人眼辨識的第一步）
    - 不易辨識：繼續搜尋其他可以幫助記憶的物件元素，眼球會做更多移動來幫助回憶
        - 一秒 / 十秒對不易遍識組都一樣
        - 政府作品最不容易辨識 \- 因為用太多相同模板及美學模式 (也就是說，缺乏創意？)
- 可以幫助記憶的物件
    - 視覺連接 ( visual associations ) - 具體圖示 etc
    - 語意連接 ( semantic association ) - 標題 etc
- 再描述（Recall）
    - 視覺圖表效果最好
    - 政府作品最差
- 眼球停留最高：標題。科學 paper 的圖表大部份沒有標題。有標題的描述平均分數較高。
    - 有標題作品再描述分數：平均1.90
    - 無標題作品再描述分數，平均1.30
- 標題放在上方，眼球停留數較高。下方較低。政府大多放下方。
- 標題的好壞也會影響到 recall 分數
    - 好標範例："Top 10 Most Read Book ... "
    - 壞標範例："Cities"
- 最常 recall 的物件：標示、標題、短敘述
- 額外標示有利於 recall ( 圖 + 文 ) - 前 1/3 最好作品中, 50% 都有這樣的標註
- 容易辨識的視覺作品，內容及細節容易受迴響，其內容描述較好

對本篇的批評
- 受試者沒有看同樣 100 篇作品
- 每個受試者的背景、學經歷不同（記憶與再描述能力不同）
- 針對「好記憶、不好描述」，「不好記憶、好描述」的領個群組沒有討論。有的「不好記憶、好描述」的圖，可能是因為受試者的背景的影響。
- 系統隨機取樣（什麼都 random，結果搞不好也是 random 的 XD）

- 研究方法的設計有缺陷（不夠清楚辨識問題）
    - 問：如何學習有系統的研究計劃，避免做出有缺陷的研究計劃？
    - 回答：可以查詢「[研究方法](https://www.google.com.tw/search?q=%E7%A0%94%E7%A9%B6%E6%96%B9%E6%B3%95&ie=utf-8&oe=utf-8&gws_rd=cr&ei=YR-SVsjCPInO0gTrlY7oAg)」，有些老師有翻譯中文。

feedback
- 每個資訊圖表想要傳達的資訊複雜度不同，可以這樣比較嗎？
- 沒有把 input 做系統化的分類
- 像他選 Nature 的，就是三類多，感覺領域上就有偏差


## Connected Scatterplot for Presenting Paired Time Series

by Steve Haroz
講者: Kuan-Lin Tung. [pdf](http://kosara.net/papers/2016/Haroz-TVCG-2016.pdf) / [slide](http://www.slideshare.net/viator75/the-connected-scatterplot-for-presenting-paired-time-series)

- 作者看了紐時的油價、車禍的 connected scatterplot 之後想來研究其效果
- 即時範例：[http://steveharoz.com/research/connected_scatterplot/](http://steveharoz.com/research/connected_scatterplot/)
- 想探究：
    - 對 relationship of data or understandability 的幫助 / cs vs dual axis line
- 三元素：點位置、方向、箭頭 ( imply direction )
    - 沒有箭頭就哭哭了，無法還原成 dual axis
- 資料不變就停在同一點

Limitation
- fixed intervals
- extremely complex shapes
- 讀者總是從左上角開始看，所以從右下角開始的圖就會有些問題

Loop Case：
- Prey and Predator Relationship
    [https://www.google.com.tw/search?biw=1280&bih=648&tbm=isch&q=prey+and+predator+relationship&revid=911276899&sa=X&ved=0ahUKEwiZ6K7Tq57KAhVGKJQKHe92DEYQ1QIIIw](https://www.google.com.tw/search?biw=1280&bih=648&tbm=isch&q=prey+and+predator+relationship&revid=911276899&sa=X&ved=0ahUKEwiZ6K7Tq57KAhVGKJQKHe92DEYQ1QIIIw)


## Ending




