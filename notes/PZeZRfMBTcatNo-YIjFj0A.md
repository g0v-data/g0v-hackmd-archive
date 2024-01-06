---
title: "你被服貿了嗎 beta 測試討論"
tags: 反黑箱服貿串連,hackpad
---

> [點此觀看原始內容](https://g0v.hackpad.tw/2spPf82j4ZH)

數十萬人催促下（誤？），即將填完的[服貿坑群](https://g0v.hackpad.tw/-g0v--SUkMbG4IV6v)
> 預計2014/3/30上線，alpha 測試~切忌~切記低調，e.g. 要實測 social buttons 可以等3/29
> [name=nchild]

> 真的是數十萬人的催促下
> [name=Shelling F]

> 要在 3/29 上線？
> [name=howard c]

> 現在已算上線，只是還未公佈。
> [name=nchild]

> 3/30 先去[這裡](https://www.facebook.com/events/1471107093105919/)晃晃吧！
> [name=nchild]

> 上線＆公布啦！[http://tisa.g0v.tw/](http://tisa.g0v.tw/)
> [name=Bropheus H]

> 請協助測試，有問題在此回報~
> [name=Bropheus H]

## 功能

### 預計要加

> 這塊請保留給開發團隊編輯
> [name=nchild]

- 公聽會資料
    - [http://letsfumou.github.io/LetsFuMou/](http://letsfumou.github.io/LetsFuMou/)
- ~滿意量表~
> 是指使用網站的滿意量表，或是對服貿的滿意量表？
> [name=Shelling F]

- 整合大陸人民來台投資業別項目及 WTO 資料
> 這邊需要一些 raw data，還要討論一下如何和 CPC, STD, Categories 作連結
> [name=Shelling F]

- 行業關鍵字搜尋
> 行業搜尋在下次 deploy 就可以使用
> [name=Shelling F]

> Delayed.
> [name=nchild]

- 職稱關鍵字搜尋

### 功能建議

----建議功能請利用這塊接著寫----
- 一致使用 AngularJS
- ~用統編進行查詢~
    - 統編 done in [a75fdc](https://github.com/g0v/tisa-map/commit/a75fdca4776ae3f8633011d63f76907866ff42ec)
- 針對使用者輸入的產業別關鍵字，直接列出相關的原始條文左右對照，再補充只解釋條文的影音檔，讓看不懂條文的民眾點閱，並可添加相關產業勞工觀點的影音檔
- [http://review.fumao.today/videos](http://review.fumao.today/videos) 這邊有公聽會立院公報逐字稿，重點整理 slide 有每人發言時間碼；Let'sFuMou 分段影片好像不全但找不到協作窗口，可以對照這邊的時間碼接力

## 資料需求

- 白話版開放承諾（開箱聞翻譯中）
> 已將部分翻譯版上線
> [name=Johnson L]

> wei hung 開放出來分身伐樹啦！
> [name=nchild]

- 大陸人民來台投資業別項目整理
- WTO 資料整理
- 手寫營業登記項目，與現行營業項目代碼對照方式
    - 數十萬家公司行號年代久遠，沒有現行的營業項目代碼
## Bug 或調整

### 處理中

> 這塊請保留給開發團隊編輯
> [name=nchild]

- ~autocomplete performance tuning -- debounce, 還有讓注音輸入法候選字區不要也一起觸發 autocomplete~ done
- ~result_affected 頁面的手機版，還有樣式調整~
- ~poll-result 手機版~
- ~選業務類別 form validation~ done
- ~增加對照表連結、 CPC 分類資訊到 result_affected~ done
- 收集連結、公聽會資訊、活動資訊，讓「我想更了解服貿」與「我要採取行動」兩個按鈕更有內容 \-\- (目前連到 g0v.today 和 123.g0v.today)
- not-affected
- 加上附註、開放限制，減少 false positive (positive = 回報被服貿了)

### 待處理

> 回報 bug 請用這裡
> [name=nchild]

- ~social button layout~
- ~Safari layout bug~
- 可以搜尋行業標準分類，列出營業登記項目（ex: 打「醫院」可以搜尋到醫院）
- fb分享的[連結](http://tisa.g0v.tw/result/?id=29151337&cat%5B0%5D=F218010&cat%5B1%5D=F118010&cat%5B2%5D=I301010&cat%5B3%5D=I401010&cat%5B4%5D=E605010&cat%5B5%5D=JB01010&cat%5B6%5D=F209060&cat%5B7%5D=F113050&cat%5B8%5D=F399990)發生internal server error
- Internal Server Error
- 進行查詢偶爾會 Internal Server Error
- 已經每次 curl '[http://tisa.g0v.tw/search?keyword=test](http://tisa.g0v.tw/search?keyword=test)' 都 Internal Server Error 了 (星期日早上 9:04)

## 問答、討論

-

