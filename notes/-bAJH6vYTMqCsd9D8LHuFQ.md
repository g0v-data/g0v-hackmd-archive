---
title: "開放政治獻金 - 人工校對、OCR網站設計"
tags: CY 零時監察院,hackpad
---

> [點此觀看原始內容](https://g0v.hackpad.tw/yESRO4zWakp)

初步資料處理、OCR 討論請見 [OCR](https://g0v.hackpad.tw/3MX5pBhtBjZ), 之後需要人工校對

### 待校對的資料

- [http://campaign-finance.g0v.ronny.tw/](http://campaign-finance.g0v.ronny.tw/) 這邊是 Ronny 放的 API 連結(輸入 index, 輸出切出來的圖檔)，讓大家可以自由界接來做資料處理界面

### 網站介面設計

- 設計政治獻金資料呈現介面
    - [ ] wireframe
    - [ ] mockup
    - [ ] proto
- 網站設計可參考
    - 口袋國會的政治獻金查詢頁面 [http://xn--6or66eo1t8u6a.tw/part5\_2\_detail.php?sno=1](http://xn--6or66eo1t8u6a.tw/part5_2_detail.php?sno=1)
    - 第八屆立委選舉經費 [http://ccw.site44.com/](http://ccw.site44.com/)
    - maplight [http://maplight.org/us-congress/legislator/127-robert-aderholt](http://maplight.org/us-congress/legislator/127-robert-aderholt)
- Layout提案
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_b708068a412e1edb4e71077abc0fcd1b)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_8f1439f0b2ee999a135fc15b365f9871)
- icon：
    - [https://drive.google.com/folderview?id=0B0jawSySD8E3VXpnaWQyQ3VQQWc&usp=sharing](https://drive.google.com/folderview?id=0B0jawSySD8E3VXpnaWQyQ3VQQWc&usp=sharing)
> 有任何建議請在這邊留言即可～
> [name=小俞Yu]

> 請補授權方式，並建議將檔案搬移到[這裡](https://drive.google.com/#folders/0B0NsS2a-Qx8ZN19uV1p6YWd6TXc)。
> [name=nchild]

> （看懂後自刪）新手問題：嗯...怎麼標記授權方式？cc？
> [name=小俞Yu]


### 目前實作

    - 顯示 OCR 結果、校對介面
        - Timothy Lee 做了一個 [https://github.com/ctiml/campaign-finance.g0v.ctiml.tw](https://github.com/ctiml/campaign-finance.g0v.ctiml.tw)
            實際上線畫面 \- [http://campaign-finance.g0v.ctiml.tw/cell](http://campaign-finance.g0v.ctiml.tw/cell)
> clkao這是跑 Server Script?
> [name=Jimmy H]

> 背景可以弄黑色嗎? 白色很傷眼?
> [name=Andy C]


### 各種對網站的建議

> [（來亂） 建議可以增加積分功能  來鼓勵大家來人工OCR](https://github.com/kiang/tw-campaign-finance/issues/5)
> [name=Pc C]

    - [ ] 快捷鍵（hotkeys）
        - [ ] 空白鍵等於按「這是空白」
> 原建議來自[這裡](https://groups.google.com/forum/#!topic/g0v-general/IBFzyI1hOH4)
> [name=nchild]

    - [ ] 輸入次數在n(=3?)次以下的時候不提示給user看，否則第一個人打錯就不容易發現，尤其是異體字
    - [ ] 提供回上一步的功能，不然按太快就回不去了
    - [ ] 取眾數而非以最後一筆輸入為準

- [ ] 以直行為單位分開設計，「+1」扭可能要拆成「數字關」「日期關」「收支項目關」「是否關」「地獄打字關」還可以配合成就系統
    - [ ] 因為是監察院倒出來的，本來就是資料庫的型式，逆回去可以增加除錯率
    - [ ] 數字關不可出現文字(收入欄跟支出欄)
    - [ ] 收支項目關只有那十幾種，可以只用滑鼠點(收支項目欄)
    - [ ] 日期關可以只輸入YYYMMDD，還可以檢查YYY要介於０９０～１０５，MM。DD也是
    - [ ] 是否關可以用滑鼠
    - [ ] 有一欄是身份證字號，统編，和匿名，可以分快篩關跟地獄身份證關，统編關
    - [ ] 如果每一列需要一個key值的話，建議用日期+序號+名稱，應該可以找到唯一值
    - [ ] 可能要幫每一行加1~2個分類欄
    - [ ] 這應該很快，把現有的複製出來，改讀取的範圍跟輸入的界面就好了

浮水印圖例
- 彌補日後可能的自動化去除仍有疏漏可能
> 原建議來自[這裡](https://groups.google.com/forum/#!topic/g0v-general/IBFzyI1hOH4)
> [name=nchild]


開放政治獻金遊戲
- ［成就］、［記分］、［挑戰］、［排名］
    - 參考 [Cookie Click](http://orteil.dashnet.org/cookieclicker/)
    - 延伸閱讀 [台灣為什麼重要？ ](http://www.books.com.tw/web/sys_serialtext/?item=0010578430)
> 原建議來自[這裡](https://groups.google.com/forum/#!topic/g0v-general/togJIxA_7Xk)
> [name=nchild]


Captcha 系統
- 參考 [reCAPTCHA](https://captcha.net/)
> 原建議來自[這裡](https://www.facebook.com/groups/g0v.general/permalink/609945902415153/?comment_id=610269255716151&offset=0&total_comments=25)
> [name=nchild]


原住民姓名輸入提示
- 參考[這裡](https://github.com/g0v/twly-voter-guide/issues/21)，當原住民之傳統姓名或漢人姓名，以傳統姓名之羅馬拼音並列
時，建議中間手動補一個空格

"這答案沒錯"的位子
- 再稍微往右邊一點，固定住會比較方便後續使用者確認，點選速度應該會比較快，不用滑鼠移來移去的，現在會依照確認的訊息長度位子會變換

