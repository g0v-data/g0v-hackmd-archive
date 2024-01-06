從 youtube 直播影片縮時攝影的技巧
=============================

因為今年 [鳳頭蒼鷹實況](https://www.youtube.com/watch?v=kGvrcQSvFqc) 又開始了，這會是一個好幾週的實況，但實況完後感覺又很難留下記錄，因為先前 [透過 YouTube 新聞頻道 Stream 抓取新聞出現頻率](https://g0v.hackmd.io/v4haB2jUTTalEWdGLx2UfA) 計畫累積了一些 youtube 直播抓取和處理的經驗，因此剛好可以用在這裡。成果像是這樣 [20190430 (試傳)](https://www.youtube.com/watch?v=9GmGeC6FPNA)

準備
---
* 需要 streamlink 和 ffmpeg 兩個軟體

相關指令
-------
* streamlink --force 'https://www.youtube.com/watch?v=kGvrcQSvFqc' best --hls-duration 04:00:00 --hls-start-offset 04:00:00 -o tmp.ts
    * 回頭抓取四小時影片，存成 tmp.ts
    * --hls-start-offset 是指要回他抓多少時間
    * --hls-duration 是總共要抓多少時間
    * best 是指最佳畫質，可以換成 480p, 240p ...
* ffmpeg -i tmp.ts -vf fps=1/60 output/%04d.png
    * 將 tmp.ts 以 60 秒一張，存到 output 資料夾下，以檔名 0001.png, 0002.png, 0003.png ... 命名
* ffmpeg -framerate 24 -pattern_type glob -i "output/*.png" -c:v libx264 -r 30 -pix_fmt yuv420p out.mp4
    * 將 output/ 資料夾下所有的 png 檔案以 24fps 存到 out.mp4
    * 檔名那邊一定要 "output/*.png"，後面 png 不能省略， ffmpeg 才能知道是要把圖片拼成影像
* streamlink --force 'https://www.youtube.com/watch?v=H2Il7lRBKD0' best --hls-start-offset 03:00:00 -O | ffmpeg -i pipe:0 -vf fps=1/30 -strftime 1 "picture/%Y%m%d%H%M%S.png"
    * 組合技，把 streamlink 直播結果，直接導給 ffmpeg 存成 30 秒一張圖檔，檔名以日期為格式（另外 --hls-start-offset 03:00:00 表示回推三小時）