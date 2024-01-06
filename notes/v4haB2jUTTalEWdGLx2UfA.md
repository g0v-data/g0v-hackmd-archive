透過 YouTube 新聞頻道 Stream 抓取新聞出現頻率
========================================

這個研究想要做的是統計中天新聞台一天確切有幾分鐘的比例的新聞是在播報跟韓國瑜有關的新聞。這個 HackMD 記錄相關筆記和技術心得，這邊實驗會以中天新聞實驗，但是應該可以套用在其他新聞頻道。

原理和猜想
--------
* 新聞頻道的排版方式通常是固定的，以中天為例，大概是左上是節目名稱，右上是頻道名稱，左下是時間和氣象，右下是大標題和小標題，中間是節目內容。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_224542e4d268c605fae9490129fc940d)
* 大標題和小標題通常會顯示 10 秒左右後切換（要確保觀眾看完文字），節目名稱和頻道名稱幾乎不會動，中間的節目畫面則是不斷地在變動。
* 只要一秒抓一張圖，統計連續兩張圖之間的差異，就可以大概判斷出哪個區塊是大標題和小標題。
* 抓大標題和小標題可以用工人智慧劃座標出來更快，但是我這邊想讓程式可以自動猜出哪裡是大標小標位置，這樣子換成其他電視台就可以減少人工，也可以自動因應新聞改版面。
    * (20190315 )Ronny: 我覺得還是工人智慧來畫比較簡單 XD 放棄人工智慧... 
    * \工人/ \工人/ \工人/ <chihao>
* 進廣告時大標題小標題會不見，不再有連續時間兩張圖大小標不變的規律在，因此可以透過這規律消失的時間判斷現在是廣告區間。
* 同一個大標題的新聞一天應該會重覆出現好幾次，因此一個大標只要 OCR 一次知道確切文字之後，之後出現都只要用圖片比對就可以知道他是什麼大標不需要重測了，可以大幅減少 OCR 的數量，也可以記錄出一則新聞一天出現過幾次跟確切時間。

具體作法
-------
* 利用 [streamlink](https://github.com/streamlink/streamlink) 和 [ffmpeg](https://www.ffmpeg.org/) 截圖
    * 指令：streamlink 'https://www.youtube.com/watch?v=wUPPkSANpyo' 240p --stdout | ffmpeg -i pipe:0 -vf fps=1 output/out%010d.png
    * 這個分析需求 240p 畫質就很夠用了
    * Ronny: 不知道為什麼，照上面 fps=1 預期要一秒截一張，但實際上效果是 5 秒才截一張（而且頻率很不穩定），希望有熟 ffmpeg 或 streamlink 的朋友能幫忙解惑
    * Ronny: 再來試試看先用 streamlink 直接存成影片，再用 ffmpeg 另外每秒做截圖，看看會不會比較來的及...
    * [update] 分開做方法二:
        * streamlink 'https://www.youtube.com/watch?v=wUPPkSANpyo' 240p --hls-duration 01:10:00 -o 2019031513.mp4 每小時做 70 分鐘的檔案出來 (最好不要剛好一小時，多個幾分鐘留 buffer)，這樣假如下個小時啟動慢了一點還有互相涵蓋到。
        * 240p 70 分鐘影片一小時大約 200MB
        * 再用 ffmpeg -i 2019031513.mp4 -vf fps=1 output/%010d.png 分成 70 x 60 個檔案
        * 4200 個檔案 900MB ，還是保留原影片比較省空間 XD
        * 
* 利用 [ImageMagick](https://www.imagemagick.org/) 做圖片比對
    * 指令：magick compare -metric AE -fuzz 40% -highlight-color White -lowlight-color Black ctitv-2019-03-12_00-00-30.png ctitv-2019-03-12_00-00-35.png diff.png
    * 成果示意圖：左上 00:00:17 畫面, 左下 00:00:22 畫面, 右上右下 差異圖（黑色表示相同、白色表示不同、允許 40% 誤差)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_beaa6ecc9900a0c296ac1f8456065d71)
    * 允許 40% 誤差原因是有時 youtube 抓的截圖會因為 buffer (不確定?) 而模糊（可從圖中看出左上角的標題比右下角稍微模糊一些，因此無法作到完全比對，需要允許誤差）
    * 這個 40% 數字還要實驗一下看換成多少比較好 (上面 magick 指令的 fuzz 參數)
    * 示意圖的產生指令：convert -size 852x480 xc:none -gravity NorthWest ctitv-2019-03-12_00-00-30.png -composite -gravity SouthWest ctitv-2019-03-12_00-00-35.png -composite -gravity NorthEast diff.png -composite -gravity SouthEast diff.png -composite sample.png
* 利用程式統計一天下來所有的差異圖中，各區塊重覆的比例的排名
    * TODO: 程式待上傳
    * 下面的圖是將 2019/3/12 前 1000 張圖上面的差異計算統計，顏色越深表示該點越常跟前一次時間抓到的是同顏色，上面圖用的是 256 等分色（有點像中位數的概念，盡量做到每個顏色在圖上出現的比例都差不多），下面圖用的是相對色，以重覆次數最多次的為黑色，其他點的顏色相對他的數字。
    * fuzz=40%
    * ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0efebd23a5fb8bb72ad952838ad132a4)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9f6c6d12690b36ab7e13eceb9878f7a8)
    * fuzz=30%
    * ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_37028a195966e7b03bc872e6348a9aa4)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_47a8a482c82188aad7b6a42e717b350b)
    * fuzz=20%
    * ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c59d273d9f0d6da3db7217dabda6e8f2)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_eb91e617917223646366e4955dd11d3b)
    * fuzz=10%
    * ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_94bfbecadd0c3583c4cd65d05121b847)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_f222511d3444794e456e801a71345408)
    * fuzz=0%
    * ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_8b4b769e0ceeef4019a69c95adead33e)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9f377f5e87797a025a8dcc8dc1ccfee1)
* 從上面測試看起來，好像 fuzz = 10% ~ 40% 效果差不多（0%效果很差），另外如果能將影片變成一秒一張的話好像會更理想。


閒聊區
-----
Ronny: 這邊是歡迎大家隨意亂聊的地方，歡迎提想法跟自己的其他研究試驗成果。

> [name=企鵝]中天之外有要包含tvbs等頻道嗎？
> [time=Thu, Mar 14, 2019 4:20 PM]

Ronny: 我這邊先以技術研究為主，所以先鎖定單一媒體，但研究目標是希望這方法可以輕易套用到任何其他媒體。

Michael_LI：你用的技術　我看了 HackMD 說明　讓我想起我錄影存檔　八仙塵爆100天12台24小時　的資料處理當時的猜想　用截圖來比對一樣跟不一樣　那個時候靠媒觀的側錄機器　我買了十幾顆硬碟來備份存檔。
　　[g0v tw hackath15n 提案 這個社會的新聞樣貌：以八仙塵爆意外為起點 2015資料科學黑客](https://youtu.be/xjlwf9eUA1c)
  
Scott: Azure speaker recognition (分辨人聲的一種方法？)  
https://azure.microsoft.com/en-us/services/cognitive-services/speaker-recognition/  