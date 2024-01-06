---
title: "開放政治獻金 - OCR技術討論"
tags: 零時的學習不能等,CY 零時監察院,hackpad
---

> [點此觀看原始內容](https://g0v.hackpad.tw/3MX5pBhtBjZ)

給最終使用者的人工 OCR/校對網站在[這邊](https://g0v.hackpad.tw/--yESRO4zWakp)討論

### 圖檔格式

> 圖檔用 jpg 存好肥阿!!! 我看原始檔是純黑白的，用 png 會小很多阿~~~
> [name=Shenk W]

> 沒特別注意，手滑就把三千多張轉成 jpg 了 XD
> [name=Finjon K]

> 如果原圖是彩色或灰階建議就存 jpg 比較能保留比較多顏色資訊。如果原圖是純黑白，那用 png 會比較小。建議掃描成灰階, 才比較容易分辨是雜點還是真的字(無論對人或是程式都是)
> [name=Kuang-che W]

> [Nicemaker](https://g0v.hackpad.tw/ep/profile/z2MDE06YfdY) says: _原圖是純黑白，會灰階是因為掃描髒掉的問題。。。btw我是掃描組的，大家好_
> [name=venev]

> 我要舉手問：背景的「浮水印」算是灰階嗎？
> [name=venev]

> 理論上浮水印也是碳粉印出來的，也是純黑色。但實際上因為浮水印的點很小，若掃描的解析度不夠高，很小的碳粉點可能只占掃描點的半格或更小，若是用灰階掃會變當灰色，用黑白掃就要看運氣(面積夠不夠大)可能就被當黑色。若被當黑色就會影響判斷，若黑色多一點可能人眼也無法辨別。
> [name=Kuang-che W]

### 縮印?

> ~~~討論的部份都去 [http://community.g0v.tw/t/topic/145](http://community.g0v.tw/t/topic/145)  吧，這裡只留結論，感恩~~~
> [name=Finjon K]

> 我註冊了但一直收不到確認信，暫時回在這裡，kiang 等人可否幫我貼後刪除：1. 只要先確認「縮印圖檔」-> 「切豆腐格」這段流程 ok; 2. 就懇請 NiceMaker 幫寫「列印SOP」，並估計單一立委所需印量、時間; 3. 宣傳端集火排任務表號召申請調閱。
> [name=venev]

> 目前已經偷偷徵招衝組，準備一天叫出 [五都 的市長資料](https://drive.google.com/folderview?id=0ByObdQAbysqedHRDQ0JRWkpMbTA&usp=sharing)(已印完約7萬筆資料，掃描建檔中)，請各位支援 
> [name=Nicemaker]

> 最新印出來的長 [這樣](https://drive.google.com/folderview?id=0ByObdQAbysqeRGVMSFR4dXQ4QWM&usp=sharing) 麻煩測試看看
> [name=Nicemaker]

> 那個編碼, 方便直接放在檔名嗎? 還有那登記表, 用 google spreadsheet 方不方便?
> [name=Kuang-che W]

> 我手動放檔名看看，因為比起在紙上面蓋印章，改檔名快多了
> [name=Nicemaker]

> 至於登記表呢，因為以現在的規模來看，只要我直接發派任務，依序去列印，很快就好了。平均一個時段可以帶出500MB的圖檔。
> [name=Nicemaker]

> 至於堅持要統一掃描規則且編碼的原因是，回頭找有少才知道。像吳育升現在已經OCR好的公關支出，內容是捐贈收入，而且好像是李慶忠的..
> [name=Nicemaker]

> 也就是說，目前 已有電子檔->OCR 這段是沒有問題的，但 列印->電子檔 目前完全無法驗證，連紙本都散在各地
> [name=Nicemaker]


### 浮水印處理

- 浮水印 sample
    目前掃描的結果至少有三種比較不一樣的 pattern
    1.  [http://pic.pimg.tw/ronnywang/1398355833-3935933860.jpg](http://pic.pimg.tw/ronnywang/1398355833-3935933860.jpg) 字比較粗，浮水印的點比較小
    2.  [http://pic.pimg.tw/ronnywang/1398356068-3799096785.jpg](http://pic.pimg.tw/ronnywang/1398356068-3799096785.jpg) 字比較細，浮水印的點比較大
    3.  [http://pic.pimg.tw/ronnywang/1398270666-705020037.png](http://pic.pimg.tw/ronnywang/1398270666-705020037.png)
- 後勤中心 [Shenk Wang 建議](https://www.facebook.com/groups/g0v.general/permalink/609945902415153/?comment_id=610031869073223&offset=0&total_comments=5) 使用 [http://scantailor.org/](http://scantailor.org/) 進行前置處理，可以補強 ClearScan 無法處理浮水印的問題，值得一試!
    - Note: 我測試的參數是
        - scantailor-cli \
            --layout=1  \
            --margins-left=10 \
            --margins-right=10 \
            --margins-top=5 \
            --margins-bottom=5 \
            --color-mode=black\_and\_white \
            --threshold=-50 \
            --despeckle=aggressive \
            *.png out
        -  --threshold 負越多，去污能力越強
- 浮水印我之前是透過 image magick 處理，透過下面這樣的指令可以有不錯的效果
        convert {$file\_orig} -morphology thicken '1x3>:1,0,1' {$file\_target}
> 把半徑 2 以下的點都拿掉效果也不錯：
> [name=Shenk W]

> convert all-000.tif -morphology Close Octagon:2 result2.png 
> [name=Shenk W]

> (sample a) 先正規化 (平均分散灰階值)  --> 模糊 (去雜訊)  --> 然後二元化:
> [name=Hialan L]

> convert -normalize -gaussian-blur 2x2 -threshold 70% input.png output.png
> [name=Hialan L]

> 結果如下: [https://www.dropbox.com/s/p71d2vcss7rv6mt/ImageMagic_dewatermark.png](https://www.dropbox.com/s/p71d2vcss7rv6mt/ImageMagic_dewatermark.png)
> [name=Hialan L]

> 高斯效果參數可見此文件：[http://www.imagemagick.org/Usage/blur/](http://www.imagemagick.org/Usage/blur/#blur_args)[#blur_args](https://g0v.hackpad.tw/ep/search/?q=%23blur_args&via=3MX5pBhtBjZ)
> [name=Hialan L]


> sample a 混合 [Finjon Kiang](https://g0v.hackpad.tw/ep/profile/G4yGGowBe3x)  的方法
> [name=Hialan L]

> sample a 結果:  [https://www.dropbox.com/s/00peomxdk60q2jb/ImageMagic\_sample\_a_3935933860.png](https://www.dropbox.com/s/00peomxdk60q2jb/ImageMagic_sample_a_3935933860.png)
> [name=Hialan L]

> sample a 參數: convert -morphology thicken '1x3>:1,0,1' -normalize -gaussian-blur 1x3 -threshold 60% 1input.jpg output.png
> [name=Hialan L]


> sample a 三合一
> [name=Hialan L]

> sample a 3in1 結果: [https://www.dropbox.com/s/xiy5qrbdm8ywnsi/ImageMagic\_sample\_a_3935933860-3in1.png](https://www.dropbox.com/s/xiy5qrbdm8ywnsi/ImageMagic_sample_a_3935933860-3in1.png)
> [name=Hialan L]

> sample a 3in1 參數: convert -morphology thicken '1x3>:1,0,1' -normalize -gaussian-blur 1x3 -threshold 60% -morphology Close Octagon:1.5 1398355833-3935933860.jpg output.png
> [name=Hialan L]


> sample c  
> [name=Hialan L]

> sample c 結果: [https://www.dropbox.com/s/1hkdu564wdpd795/ImageMagic\_sample\_c.png](https://www.dropbox.com/s/1hkdu564wdpd795/ImageMagic_sample_c.png)
> [name=Hialan L]

> sample c 參數: convert -morphology thicken '1x3>:1,0,1' -normalize -threshold 70% sample_c.png output.png
> [name=Hialan L]


- 利用表格左上右上兩點找出浮水印的位置再強力清除處理那附近的雜點不曉得可行性多高
    - 範例圖: [https://www.dropbox.com/s/yam9ykpcjl1kznm/sample.png](https://www.dropbox.com/s/yam9ykpcjl1kznm/sample.png)
    - 試著寫了一下，目前只要給我表格最上面那條線的兩點座標就可以把浮水印的區塊拿出來特別處理，見：
    - [https://github.com/shenkyw/tw-campaign-finance/commit/070de4d3d372375c7454eb3e86019f4b1ca0cdf6](https://github.com/shenkyw/tw-campaign-finance/commit/070de4d3d372375c7454eb3e86019f4b1ca0cdf6)

### 欄位、格式分析

- Ronny Wang 分享[如何抓出掃描文件的每個欄位](http://ronnywang.pixnet.net/blog/post/40488349)
- 切框線確認（[demo 網頁](http://ronnywang.github.io/tw-campaign-finance/demo.html)：速覽每份表格欄位切得如何）
- 從圖檔抓出欄位資訊，所有程式碼和資料在 [github](https://github.com/ronnywang/tw-campaign-finance) （以上 [Ronny Wang](https://g0v.hackpad.com/ep/profile/tC7Bqff8Vp0) ++）
- "發現 tesseract 的 hocr config 可以抓出有字的 bbox: tesseract foo.png out/foo hocr -- 輸出是 html tag. 姑且不論辨識是否正確，拿到 bbox 後至少可以切出來做人工ocr" [from gugod1 @ irc](http://logbot.g0v.tw/channel/g0v.tw/2014-05-02/671)
> 輸出格式為 [http://en.wikipedia.org/wiki/HOCR](http://en.wikipedia.org/wiki/HOCR) ，透過 [這個](https://github.com/kiang/tw-campaign-finance/blob/master/scripts/kiang/13_jpg2bbox.php) 程式測試了一百多張圖片，還是會有些遺漏的情況，浮水印的干擾也是一個問題
> [name=Finjon K]

> 請問有處理"政治獻金表格"的bbox結果圖嗎
> [name=Sin-Yu C]

> [http://203.69.90.98/tw-campaign-finance/bbox.zip](http://203.69.90.98/tw-campaign-finance/bbox.zip) 試試吧
> [name=Finjon K]

> 有辦法把最上面的Title(第八屆立法立法。。。那邊),現在頁/共幾頁那邊獨立切一個出來給人工OCR嗎？這樣所有檔案就不用分開掃描了。只要抓到最左上跟右上角的座標往上切就好了。這樣做可以給每ㄧ列有唯一key
> [name=Nicemaker]


### 以現有工具自動 OCR

    - [x] 將 PDF 轉為 ClearScan，並做第一階段的機器識別 -au
        - [x] 參考[範例檔](https://drive.google.com/file/d/0B9tD1zENsweyektyYUU0NlpKeXM/edit?usp=sharing) ，其中文字已可剪下貼上
        - [x] 已經上載 ClearScan + OCR 結果: [https://drive.google.com/folderview?id=0B9tD1zENsweyUmZycEhWZjR5MUk&usp=sharing](https://drive.google.com/folderview?id=0B9tD1zENsweyUmZycEhWZjR5MUk&usp=sharing)
            - 目前只識別沒有疊到浮水印的欄位，如果能移除浮水印則更佳
> 在 yllan 的協助下已經將上述 OCR 結果轉成文字與座標，放在
> [name=Finjon K]

            [https://github.com/yllan/TextPositionExtractor](https://github.com/yllan/TextPositionExtractor)
            接著就是要以這個結果去處理文字排版，然後找出欄位對應關係，接著就是人工 captcha 了
        - [ ] 已經將 Ronny 與 yllan 的成果合併到
            [https://github.com/kiang/tw-campaign-finance](https://github.com/kiang/tw-campaign-finance)
            展示頁面可以參考
            [http://kiang.github.io/tw-campaign-finance/demo_text.html](http://kiang.github.io/tw-campaign-finance/demo_text.html)
    - [ ] 使用 tesseract 辨識
        參考 sample code: [https://github.com/hialan/php-strip-watermark/blob/master/php/batch_tesseract.php](https://github.com/hialan/php-strip-watermark/blob/master/php/batch_tesseract.php)
        - 英文數字辨識較佳
        - 中文偶爾會成功
            - 測試結果，目前每個豆腐高 50 px ，中文辨識率較佳
        - 辨識訓練工具 \- [http://vietocr.sourceforge.net/training.html](http://vietocr.sourceforge.net/training.html)
            可以藉由這個工具去產生比較好的 OCR 資料庫，這樣一來就可以提昇辨識結果
        - 各種外掛 \- [https://code.google.com/p/tesseract-ocr/wiki/AddOns](https://code.google.com/p/tesseract-ocr/wiki/AddOns)
    - [ ] [https://github.com/buganini/ocrap](https://github.com/buganini/ocrap)
        以行為單位半自動的辨識，需要人工介入，接網站API的部份待實作，但網站上看起來有些(舊?)資料似乎沒有deskew，表格沒切好，遇到這種狀況miss rate會很高

### 整合開發

- polor1010
    - [ ] 圖檔做文字的擷取，包含過濾浮水印，和文字定位（目前只能定位數字）
        [https://www.dropbox.com/s/0dlkiyik1s6ypqb/WordExtract.zip](https://www.dropbox.com/s/0dlkiyik1s6ypqb/WordExtract.zip) （處理結果 ）
        - [ ] 有些定位結果不準確，研判是斷掉的元素connect component無法連接。小弟正著手加強這部分。
            Ex: 顏清標_雜支支出_雜支支出\_0\\cell7\_1\_R, cell13\_1\_R, cell1\_4\_R, cell2\_1_R
        - [ ] 數字辨識演算法數字部分完成
```
    https://www.dropbox.com/s/xthh56gqpzda2nu/recognition%20results.zip  (辨識結果)
```
        - [ ] 數字辨識結果更新至政治獻金伺服器
        - [x] 新增 command mode,  辨識結果 json 格式輸出
```
    https://www.dropbox.com/s/33q9qnjnwbt1loj/test.zip (test檔案和辨識結果)
```
        - [ ] 程式碼請參照 [https://github.com/polor1010/tw-campaign-finance-recogntion](https://github.com/polor1010/tw-campaign-finance-recogntion)
        - [ ] 中文字定位 (未完成)

### 其他

-

