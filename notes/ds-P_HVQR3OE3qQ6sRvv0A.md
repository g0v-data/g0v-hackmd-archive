---
title: "逐字稿打字坊"
tags: 聽打共筆,字幕,hackpad
---

# 逐字稿打字坊

> [點此觀看原始內容](https://g0v.hackpad.tw/ntF2esfIsSj)

> 還是要叫 G0V打字坊 比較好?
> [name=Wen-Chi C]

> 好專案！推（先幫加到最接近的「聽打共筆」collection，未來可和文播相關專案經驗結合）
> [name=venev]

> 為什麼都沒下文了啊??沒有需要嗎?
> [name=Wen-Chi C]

過了四個月都沒人回應，大概是無疾而終了。剛好看到這個工具，雖然只能個人使用，但至少支援影音檔播放兼打字，應該可以提供有需要的朋友參考。
> _oTranscribe 推薦！聽打逐字稿雲端服務，不用下載安裝軟體：_[http://free.com.tw/otranscribe/](http://free.com.tw/otranscribe/)
> [name=Wen-Chi C]

106.6.14補充：更理想的出來了，直接語音辨識，自動轉錄音檔
> SwiftScribe 打逐字稿必備！線上語音辨識服務，自動將錄音轉文字輸出[https://free.com.tw/swiftscribe/](https://free.com.tw/swiftscribe/)
> [name=Wen-Chi C]


原始心智圖
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_845ceac7ac3d48fd9a0e2b00f3963e67)
[http://i.imgur.com/fDHoqdM.jpg](http://i.imgur.com/fDHoqdM.jpg)

## 目的

整合需要逐字稿的資源，方便大家一起跳坑
- 現在各種需要上字幕的影音檔案越來越多，每個都要個別挖坑再上來請人幫忙打字，實在有點麻煩
- 要挖坑或跳坑都需要有一定的技術門檻，不是每個人都知道怎麼做
- 仿照P2P分享原理，由系統自動整合原始文件並加以分割，然後提供專案網址，方便分享給更多有空的人幫忙打字
- 如此可以降低門檻，提高志工參與率，或許也能提高供檔者把原始文件拿出來建檔的意願，讓更多東西得以曝光

## 那些東西需要逐字稿?

- 無字幕影片
- 錄音檔：mp3、wav...
- 掃描文件：pdf、jpg...
- 需要翻譯的原文資料
> 我覺得翻譯跟打逐字是不同層級的東西，可能要另開討論。因為就算我完全不懂醫學，也是能把中文參考書key成電子檔。翻譯沒辦法碎片化。
> [name=Nicemaker]

> 我是覺得，從系統角度來看，兩者所用到的系統功能是很相近的，所以我會想把它整合再一起。等上傳開成專案後，志工就可以選擇自己能力範圍內能做的專案參加。總不至於標題都說這是翻譯坑了，還有人以為是打字坑跳進去。
> [name=Wen-Chi C]

> 當然，這是以我原來的設計(影音分時間、文件逐頁打字)來看的，以你所提的碎片化遊戲模式來說，當然就無法應用在翻譯坑了。因此我是建議，如果要做成遊戲，可能要另開專案比較好。
> [name=Wen-Chi C]

> 有道理，我想想看@@a
> [name=Nicemaker]


## 應用

- **影音旁白**
    - 議會現場直播
    - 手機側錄畫面
    - 會議錄音
- **文件打字**
    - 外流公文
    - 挖出來的掃描文件檔案
- **翻譯蒟蒻**
    - 多人合作翻譯同一份原文資料
    - 將一份文件翻譯多國語言，以便進行國際宣傳
> 多人同譯可能還要開會討論，領域不同整合會差很多
> [name=Nicemaker]

- **學術應用**
> 學生的恩物?
> [name=Wen-Chi C]

    - 上課內容錄影
    - 原文資料協同翻譯
    - 高手前輩的筆記建檔
    - 題庫詳解建檔

## 作法

- **粗胚**
    - 影片
        - 上傳Youtube後提供網址
    - 錄音檔
        - 直接上傳
        - 上傳Youtube後提供網址
> (需要轉檔教學,或是幫轉檔的工具)
> [name=Nicemaker]

    - 文件
        - 直接上傳
        - 各別JPG掃描檔是否可自動合併?
        - 或由上傳者自己合併成pdf再上傳?
        - 掃描檔可否先經過OCR初步辨識後，再分段交由志工校對以節省時間?
- **切割**
    - 影片、錄音檔
        - 依固定時間分段(1分 or 5分?)
        - 每段前後延伸3-5秒，以免分段處聽不清楚
    - 文件
        - 依頁數分段
- **封裝**
    - 每個專案提供獨立網址，方便分享找志工
    - 系統提供此檔案的基本資料(標題、長度、頁數)
- **測試**
    - 系統顯示目前各分段處理情形
        ～以燈號顯示：紅：待領、黃：打字中、綠：完成
    - 志工挑選\[待領\]片段
    - 系統顯示該段內容(影片、聲音或文件)
    - 志工直接將文字輸入在下方，完成後送出
    - 回到前面繼續認領下一片段
> 可以亂入給建議嗎？要不要出個打字王的App，社交用的？也就是說，根本不是志工，是來玩遊戲的。玩家拿到的是很細很細的分割，而且會亂跳。這樣就只Focus在打［單字］。
> [name=Nicemaker]

> 至於檢查王又是另外的關卡了XD
> [name=Nicemaker]

> 這招是不錯，就怕需要逐字稿的苦主沒時間等...
> [name=Wen-Chi C]

> 可是如果倚靠的是『志工』，那題目的『神聖性(?)』就會導致完成速率差很多，像黃國昌演講，可能一堆人搶著打，至於政治獻金。。應該沒什麼人打，因為除非全打完，不然看不出效果。(一直打匿名捐贈應該沒人要認領吧。。。)，更不用提共筆類的東西。
> [name=Nicemaker]

> 遊戲化可以強化許多回饋機制，像成就系統，甚至可以換錢，而錢的來源可以是很急的苦主嘍(也可以是願意贊助公民運動的贊助商，想早點知道八卦的魯宅，實際需要選舉的團體，作業做不完的研究生？)。越早拿到付越多。有付錢的檔案就會有比較高的機率被打到。而不付錢的人就要公佈文件結果嘍。
> [name=Nicemaker]

> 至於打字的玩家根本不知道自己打了什麼東西，不用擔心外洩或是其他問題。
> [name=Nicemaker]

> 這個平臺就會可以變成一個去中心化的打字平臺了。唯一要做的就是文件分割(不用精確的切，只要切的有重疊就好了)，發包，統合(把重疊的部分疊起來)，校稿，發佈。
> [name=Nicemaker]

> 其實我無法想像要切碎到甚麼程度才能讓人看不出自己在打甚麼東西，因為原始文件可能是影片、音訊檔或者掃描文件影像檔，這樣要怎麼切、又要怎麼播放才行?另外就是，會想要製作逐字稿，通常是想要再做加值化利用，例如幫影片上字幕、翻譯或者方便檢索關鍵字，如果只是想知道內容，其實只要直接看原始檔就行了，這些原始檔往往也是公開資料，只是沒有文字而已。真正的機密檔案，大概也沒有人敢這樣公布給不相干的人看吧?
> [name=Wen-Chi C]

> 其實是監察院OCR想到的，切到以半行為單位，並且亂數跳出題目，大概只能知道在打是國字，但完全不知道在打什麼。如果是多分檔案一起亂數，我只能知道我打了很多字。。錄音檔也差不多，切到５秒+-1秒。影像檔其實可以只抓音檔，效果一樣。
> [name=Nicemaker]



- **組裝**
    - 後臺顯示已完成片段內容，可供檢查是否有問題
    - 確認後，系統自動合併輸出
    - 完整逐字稿
    - 校對稿：時間+內容 或 頁數+內容

## 可能遇到的問題

- 挖到寶了怎麼處理
    - 問題：如果挖到大量掃描文件，還要這樣逐篇處理嗎?
    - 建議對策：支援壓縮檔上傳，並由系統自動挖出裡面的文件檔批次處理
    - 衍生問題：要如何讓系統自動辨識那些檔案是需要處理的?
    - 衍生對策：掃描檔可否先經過OCR初步辨識後，再分段交由志工校對以節省時間?這樣在處理大批文件時應該會更有效率。
> 居然還有這種東西：Project Naptha 讓圖片裡的文字可被複製、選取 (Chrome 擴充功能) [http://www.freegroup.org/2014/04/project-naptha/](http://www.freegroup.org/2014/04/project-naptha/)
> [name=Wen-Chi C]

> ~不過看來中文辨識好像還是不太準...
> [name=Wen-Chi C]

- 志工有空全程在線上輸入嗎?
    - 問題：線上直接輸入固然方便，但志工會有被綁住的感覺
        ～不能下載離線打完再上線回傳嗎?
    - 建議對策：除線上直接輸入外，另提供附件上傳功能
    - 衍生問題：附件只限TXT檔嗎?
- 逐字稿不一定是純文字
    - 問題：線上直接輸入只適合純文字，但掃描文件可能包含表格和插圖
    - 建議對策：提供附件上傳功能，支援DOC檔
    - 衍生問題：如何讓系統自動合併一系列DOC+TXT附件檔
- 安全隱私問題
    - 問題：有些文件可能涉及機密，或不便太早曝光
    - 建議對策：由上傳者決定是否要公開放到清單上，若不公開就提供網址讓他私下找人打字
    - 衍生問題：本系統需要支援這種涉及機密或純粹學術(私人)用途的文件打字嗎?

