---
tags: summit2024
---

# 直播口譯設備規劃

## 問咪卡

* 提醒一下，目前議程表規劃 Day 1 的活動到 17:30，Day 2 到 17:00。議程表細流出來以後，會再跟你們協調。
> [name=咪卡]
這個沒問題


* 控台是設在哪裡？我好確定有線網路有拉到。
> [name=咪卡]
 R0：面舞台右側的第三 or 四排
 R1：最後一排 (中控室前)
 R2：最後一排 (中控室前)
 口譯：R0 5 樓

* 確定一下，UD Talk 也是咪卡全部處理完嗎？如果是的話，似乎沒有規劃技術人員？
> [name=咪卡]
信件上提到的時候是請我們把訊號送上 UDTalk 電腦，後續會有工程師協助將畫面送上視訊會議，所以報價單上只有規劃硬體器材。因為只有單純音訊輸入，所以預計場佈日安裝完畢後就不需額外操作，故無另外排設人力，但剛剛回頭確認 UDTalk 似乎只有在 android & iOS 上有提供服務，有在 slack 上向 yutin 確認以往投放出來的做法，屆時再來調整設備項目

* 「議程錄影紀錄與直播」這項是不是沒有規劃技術人員？
> [name=咪卡]
有含技術人員，直播錄影的會議廳皆會有一位攝影師及一位直播導播。
* 「議程錄影紀錄與直播」是否包含講者螢幕擷取子母畫面？
> [name=咪卡]
有，本次的議程直播錄影皆含講者簡報的子母畫面擷取，列在細項第二條客製版面開框，通常有開框就是有含擷取，這邊補述說明。
子母框的設計可以參考 [直播素材規範](https://drive.google.com/file/d/1fSlmDYD2Kh1aDsPKcTKUV6Y24hMYxKYE/view?usp=sharing)，目前是需要由大會提供製作完成的字卡。
* R0「LED 訊號」操作是什麼？
> [name=咪卡]
R0 大螢幕（電視牆）的訊號，在訊號送回中研院前我們會再放一台導播機，確保 R0 螢幕在更換電腦時不會有插拔造成的黑畫面，以及無斷投放廣告素材或其他需求。

另外雖然目前是選擇無遠距會議的方案，但關於遠距會議方案，也有些想多瞭解的：

* 「R0 遠端講師連線演講」這一項，如果集中在同一天，會不會比較便宜？
> [name=咪卡]
會，費用是以器材的天數跟數量計算，所以如果集中在同一天、同一廳費用會比較低，或是再次跟中研院確認現在能否提供不同聲音訊號的技術協助，因為各會議廳設備狀況不同，可能略有差異。
* 「R0 遠端講師連線演講 之 音控技術人員」與「 R0 視訊投影操作（含技術人員）」是不同人嗎？
> [name=咪卡]
遠距演講的規劃因為有自備音控台，會有音控串接訊號、調整麥克風音量大小等狀況，使用場地系統都是預設值無法調整，所以會有一名音控人員，視訊技術人員與音控技術人員為不同人。
* 「視訊會議用筆電」需要兩台嗎？「無線麥克風組」意思是現場人員要使用與中研院現場不同支麥克風？
> [name=咪卡]
視訊會議筆電要兩台（簡報）（人臉）呈現如現場錄影的開框處理，兩台在訊號擷取上比較美觀且有彈性。
無線麥克風部分在於，中研院不一定可以給跳這麼多聲音訊號出來(平常錄影只需要現場全部的聲音)，線上會議為了處理跟現場的即時對談，我們會需要額外送純粹的麥克風訊號給遠端講師，一般跟場地要到的訊號會是系統全部的聲音，會造成回授。
通常都是直接自帶音控台＋無線麥克風自行處理訊號，然後使用中研院喇叭。這個部分也可以跟中研院再次確認現在是否能夠協助串接遠距會議。


---
## R0 簡單架構

![截圖 2024-04-18 下午3.56.37](https://hackmd.io/_uploads/HkmBzI0gC.png)

- 講台視訊：HDMI
- 電腦聲音：over HDMI
- 若有廣告、素材等需要播放，整理完提供給 R0 控台區，廠商有人放

## R1 & R2 簡單架構
![截圖 2024-04-18 下午4.09.23](https://hackmd.io/_uploads/SJ-rHLAeR.png)

- 講台視訊：HDMI
- 電腦聲音：over HDMI
- 若有廣告、素材等需要播放，需自行準備公用電腦，可以事先接在無縫切換器上，切換器會放置於講台下，需要自行操作

## UDTalk 規劃
[UDTalk 筆記](https://g0v.hackmd.io/@Pno233SAS8G5UfL5OvSRmA/B1Qmv34Ta)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_752e9b6d2725cf30be74a2436029a2a7.png)

- 咪卡處理收音＆進輸入 UD Talk 系統
- 會眾自行掃描 QRcode 進入 UDTalk 系統觀看、志工同時進入系統校正翻譯

## 即時口譯實作規劃
- 講中文翻英文，講英文翻中文同時只會有一個方向？
- 使用 Youtube 口譯送無畫面串流

# 2024-04-22 口譯 & UD Talk 會議

- UD Talk
    - Skyer 幫忙找人校正
        - UD Talk 校正實作要做怎麼做，有沒有 Demo
        - 校正輸入的語音資料，如果有人做多少就盡量
    - 設備部分看起來 daisuke 沒問題
    - 開連結跟 QR code 這件事情，要誰開？
        - 希望每天每個會議室一個連結
        - 跟 Aoki 約個時間測試一下
        - 4/25, 26 其中一天的 20:00~21:00 看能不能直接開一個 event 讓我們做測試
- 口譯
    - Tiff 有提能不能雙向口譯的問題
        - https://g0v-tw.slack.com/archives/C04U8DKBGSX/p1713750200917099
    - 我們的規劃是單場只有「英->中」或「中->英」擇一
        - 因為是一個語言是固定一個 YouTube 頻道
        - 沒辦法現在講中文就翻英文，現在講英文就翻中文
        - 再跟 Wilt 確認一下 Youtube 無畫面串流是否是 ok 的
    - 選項一：Tiff 也聽講英文，變成整場都是英文議程
        - Skyler 跟 Tiff 確認一下
    - 選項二：如果真的要中英穿挿，要找人做逐句口譯比較可行。同步口譯，會變成前一句英文還在翻，下一個人已經在講中文，這樣亂掉
    - 要跟 Wilt 確認無畫面的不公開直播 YT 串流，是否不須增加費用
- 場地
    - 場佈 5/3 09:00-17:00
    - Day 1 到 18:00
    - Day 2 到 18:00
        - Unconf 不錄影
        - 17:00 準時結束的話，R0 18:00 應該拆得完
        - 跟 R0 許兄講 19:00 關門比較保險，但 18:00 理論上收得完 
- 直播連結
    - 拜三可以先開，我們也可以提早放到網站上
        - Day 1 R0 的在 4/24 之前開給 pm5，可以拿給 A N 宣傳
- 議程
    - 確定都沒有遠端連線的講者嗎？那就比較沒有問題
- 咪卡贊助
    - 廣告再寄
    - 最後的報價也再寄


# 2024/04/25 UD Talk 測試 Action item

- 要確認末端瀏覽的頁面是否有連線數的限制
- 如何公告現場參與者可以協助編輯校正輸入（說明文件）
- 確認需要切換的時間（議程語言）
- UDTalk 需要有人協助確認輸入語言是否設定正確（希望議程助理可以協助？）

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9a1239aed3b35027aba8d46289a4b7c7.png)
