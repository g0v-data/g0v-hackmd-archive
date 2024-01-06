---
title: "一鍵 Excel 轉 .csv (含自動修復) (Ver20160305)"
tags: hackpad
---

# 一鍵 Excel 轉 .csv (含自動修復) (Ver20160305)

> [點此觀看原始內容](https://g0v.hackpad.tw/vDLLZbbikXF)


## 專案簡介

### ==最新版本下載 (Latest released version)==

- Excel\_to\_csv Delta(2016.05.17)
    - [Google drive連結](https://drive.google.com/file/d/0B0l5ONZZiOChNDBONlhJSElBSFU/view?usp=sharing)
- [安裝說明書(Google drive)](https://drive.google.com/file/d/0B0l5ONZZiOChZUJsZjF2blNHVlk/view?usp=sharing) (目前僅針對windows OS,  MS office 2010+)
    - mac OS、其他office 目前還沒摸透，==**跪求白老鼠測試**==
- 測試範例檔案 ([測試用範例一](https://drive.google.com/file/d/0B0l5ONZZiOChMURJMGVRaC13eWc/view?usp=sharing)) ([測試用範例二](https://drive.google.com/file/d/0B0l5ONZZiOChY3RWcHlYZ1hhMVk/view?usp=sharing)) ([測試用範例三](https://drive.google.com/file/d/0B0l5ONZZiOChV2xqTHRvby1iT0E/view?usp=sharing))

- 另外根據Ronny的[Excel轉換工具](https://g0v.hackpad.tw/Excel--jkpco57DjJH)寫了合併工作表的VBA
    - google drive連結 ([檔案下載點我](https://drive.google.com/file/d/0B0l5ONZZiOChU0VyYTZBSkRvSmc/view?usp=sharing))
    - 安裝方法相同
    - 適用於 每個工作表都有類似的資料需要合併
        - 例如不同的工作表 為 不同的縣市
        - 都有一樣的資料類型 (首列)
    - 依照Ronny的建議加上「首欄=工作表名稱」 的選項
    - 可以選擇轉換完是否自動另存成csv
    - 測試範例檔案 ([測試用範例一](https://drive.google.com/file/d/0B0l5ONZZiOChUzhKU3k4NG5TVkE/view?usp=sharing)) ([測試用範例二](https://drive.google.com/file/d/0B0l5ONZZiOChMTJFVk8tV3RJUkE/view?usp=sharing))

### 緣由

看到Peggy的[公務員開放資料Lesson 1](https://hackpad.com/Lesson-1-ver1.0-XdDvvmJJ6Zf) ，想說有沒有辦法直接開發程式供公務人員使用，減少轉檔後的資料格式問題

> 跪謝Q_____________Q
> [name=羅佩琪]

> 等下想討論：
> [name=羅佩琪]

> 1\. 用 "VBA" 跟 "Ronny做成網站" 這兩種方式，哪一種比較容易使用？
> [name=羅佩琪]

> 2\. VBA的功能可以也變成線上化的方式進行嗎？反之把網站功能做成VBA？
> [name=羅佩琪]

> 3\. 哪一個方法比較容易、還是不同功能必須用不同方法？
> [name=羅佩琪]

> 1.  VBA完成後可以直接變成EXCEL中的一個按鈕，EXCEL開了就可以用，沒有網路也可以；但相對的，第一次安裝也需要一些步驟。另外缺點就是更新比較困難，每次CODE更新就要重新設定一次。個人認為VBA方法對公務員比較友善，但對替代役或資訊人員比較麻煩。
> [name=Arshain C]

> 2\. & 3.  然後兩種方法核心應該依樣吧，不過語法有些不同，但理論上是可以互相轉換的。
> [name=Arshain C]

> 理解.....等下討論！
> [name=羅佩琪]

> Ronny有提到 如何讓使用者對於資安沒有疑慮
> [name=Arshain C]


> 不好意思插入一個問題， .ods格式在轉換上問題會比較少嗎? 還是說因為現成資源較少所以反而要重新開發?
> [name=Leo C]

> 其實我不懂.ods，可以等下介紹 / 討論一下。
> [name=Arshain C]

> 好的，我其實也想蒐集一下大家對於data.gov.tw的想法XD（這次應該先挖坑的...orz）
> [name=Leo C]




### 要解決的問題

1.  減少Excel檔案轉成.csv的步驟，以節省時間及降低人為犯錯機率
2.  自動修正Excel中轉成.csv時造成錯誤的潛在因子，確保轉出的.csv可供後續正確使用
3.  不要破壞原本「方便人閱讀的格式」，降低使用者抗拒因素

### 預定使用者

不習慣將Excel編輯成符合資料庫格式，但又想將其轉成csv成為開放資料的人

### 預定功能

1.  功能
    1.  修正合併儲存格(跨至欄中)的問題
        1.  搜尋資料表中的合併儲存格
        2.  解除合併並將資料整合
            ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_4f012468d84264a98a201eba42c4f52b)
            ↓↓↓↓↓↓↓變成↓↓↓↓↓↓
            ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_3dea786a9bad200097c3513d217a580b)

    2.  去除可能會造成錯誤之符號 (如 數字間的逗號 1,230,000 )
        1.  方法一：強制消去全部的,  (但要考慮會不會有其他文字屬性欄位也含有半形逗號)
        2.  方法二：將全部欄位改成無千位數逗號之數字 (但要小心破壞其他儲存格之內容)
    3.  儲存
        1.  另存成.csv檔案
        2.  檔案名稱為  原本檔案名稱 \+ 工作表名稱 \+ ".csv"
        3.  編碼格式自動選為 UTF8
    4.  其他功能 (待補充)
> 預計新增幾個功能
> [name=Arshain C]

> <A> 同一個檔案的不同工作表合併  
> [name=Arshain C]

> <B> 將同一個檔案的各個工作表分別轉出
> [name=Arshain C]


2.  介面
    1.  掛在EXCEL介面中之巨集按鈕
        1.  優點：
            - 使用方便簡單
        2.  缺點：
            - 安裝問題（如何讓使用者順利把巨集載到Excel中，並形成按鈕）
            - 版本更新問題
            - 安全性檢查（巨集是否會被系統阻擋）
    2.  額外執行程式
        1.  優點：
            - 執行檔容易傳播使用
            - 可以透過GUI設計讓使用起來方便
        2.  缺點：
            - 操作步驟可能較麻煩（要先選擇目標檔案，在執行）
            - 程式碼相容性問題
    3.  [Ronny Wang](https://g0v.hackpad.tw/ep/profile/tC7Bqff8Vp0)的網頁版本 ([連結](https://g0v.hackpad.tw/Excel--jkpco57DjJH))
        1.  優點：
            - 不需要安裝
            - 更新容易

### 現有類似專案

Ronny大大好像之前有做出 潛在錯誤檢查程式

### 相關專案

???

### 授權方式

cc by

### 使用資料

無

### 相關資訊

Archain昨天有在問，公務員目前的電腦office是哪個版本，我剛先問了一下我們(衛福部)資訊處部內的狀況：
1.  目前全面是2010的版本。
2.  行政院有指示，2010以前的版本因為不再更新，資安上有疑慮，所以不得使用。
3.  至於什麼時候會換2013，目前還不知道，應該是看微軟何時停止更新2010。
以上資訊提供。
> 很有幫助的資訊，因為2003和2007對巨集和工具列限制比較多
> [name=Arshain C]


路過補充地方政府情形：
根據2015年收資料的經驗，若散發office2010格式檔案給各縣市政府(的下屬局處單位)，大約有1/10的回收資料會用office 97-2003的格式回來。
> 感謝回饋。目前測試結果，似乎檔案本身版本不是很重要，但執行的office版本影響很大。會再持續實驗。
> [name=Arshain C]


### 專案目前狀態

1.  Delta版本完成，釋出日期為2016.05.17。 [Google drive連結](https://drive.google.com/file/d/0B0l5ONZZiOChNDBONlhJSElBSFU/view?usp=sharing)
    - 執行前自動備份
    - 修正部份bug
    - 註解增加
    - 目前尚未解決之問題
        - **有些Case在「項目」會分別有中文和英文兩個row，目前沒辦法自動合併**
        - **有些Case在奇怪的地方(如最下面)會有合併儲存格，無法正常消除**
2.  VBA巨集C-Gamma版完成，為2016.03.05 g0v黑客松後釋出版本[Google drive連結](https://drive.google.com/file/d/0B0l5ONZZiOChU3VGQmhLY0Zwd00/view?usp=sharing)
    - 【不重要資訊：之所以Gamma前有個C字，是為了排序】
3.  VBA巨集beta版([dropbox連結](https://www.dropbox.com/s/nq8shzk6bu10649/Excel_to_csv_Beta_20160305.xlsm?dl=0))完成，暫定工作環境為office2010。 (2016.03.01)
    - 新增[google雲端硬碟下載連結](https://drive.google.com/file/d/0B0l5ONZZiOChMzV1MEdvcENLXzQ/view?usp=sharing)。
    - 請下載後使用，點選第一頁的Run。若要再次測試，請關閉檔案重新開啟。
    - 將巨集指令加到Excel工具列中便可對其他文件使用，但目前還沒有極簡單且簡便的版本。
        - 人工設定可以先參考[Johnson Liang](https://www.facebook.com/johnsonliang?fref=ufi)之前錄製的[方法](http://i.giphy.com/3o7ZeMOtVaygEDsbu0.gif)，不過每次使用都會冒出一個額外的excel視窗。
        - [安裝說明書](https://drive.google.com/file/d/0B0l5ONZZiOChZUJsZjF2blNHVlk/view?usp=sharing)
        - 尚在研究更簡單、自動設定，且不會產生額外視窗的方法。
            - 基本上將巨集寫進Personal.xlsb中，就不會有額外視窗
    - beta版新增可以處理的部份 (alpha版功能繼承)
        1.  自動判別資料範圍
        2.  儲存時不再留下原始資料的副檔名
        3.  修正儲存路徑為原始檔案的同資料夾內
        4.  自動去除多餘的空白列、註解列
            - Beta版測試
            - Before

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_219346cbc9c828462ca547d1e78c074a)

            - After
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_428b3d9a50dead268ee846b5a487b5d1)

    - beta版尚未處理的問題
        1.  尚未完全驗證
        2.  一次處理同一檔案中的所有分頁 (code已完成，尚未實裝)
        3.  當已有同名檔案時，要怎麼處理
        4.  存完後是否自動關閉檔案（執行中的為.csv)
        5.  讓使用者可以很簡單地把巨集置放於工具列

> 發現問題，資料表欄列太多時會卡住 (上限待測試)
> [name=Arshain C]

> 公務員表示 dropbox會被公家機關網路擋住，可以改用google
> [name=Arshain C]


            -
3.  VBA巨集[alpha版](https://www.dropbox.com/s/udh6esh63bririi/Excel_to_csv_alpha.xlsm?dl=0)完成，測試中 (2015)
    - 請[下載](https://www.dropbox.com/s/udh6esh63bririi/Excel_to_csv_alpha.xlsm?dl=0)後使用，點選第一頁的Run。若要再次測試，請關閉檔案重新開啟。
    - 目前可處理部份
        1.  一鍵完成（不過還沒做好巨集指令移轉，所以只能在範例檔中使用）
        2.  解決「簡單的合併儲存格」問題
        3.  消除數字中的半形逗號
        4.  自動以「同樣的檔名」、「 UTF8編碼格式」儲存成.csv

    - 目前尚未處理的問題
        1.  未驗證是否適用於各種合併儲存格之情況
        2.  未能自動判別資料總行列數，所以目前固定只掃到10x10
        3.  原始檔案的附檔名會留著 （如XXX.xls.csv）
        4.  一次處理不同分頁、大量檔案
        5.  當已有同名檔案時，要怎麼處理
        6.  存完後是否自動關閉檔案（執行中的為.csv）
        7.  讓使用者可以很簡單地把巨集置放於工具列


    - 目前效果 (使用==**前**== in excel)_(表格內容為假想內容)_
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_75e01a57f6f16ee8c379eeaee3a1aba3)
    - 目前效果 (使用==**後**== in excel)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_184b42b4191c6e7e359b8fd27250738d)
    - 目前效果(使用==**前**== in wordpad)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_843cdd656a9f97e66b011ddc249a579e)
    - 目前效果(使用==**後**== in wordpad)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_e529536fd32941579328d39d7300cf98)

### 利益揭露

應該是沒有吧


## ==使用者回饋==

> 這陣子找同事幫測結果↓↓
> [name=羅佩琪]


### 整體建議

- [x] 如果沒有全部轉成功，會需要看原本轉之前的資料，但使用VBA轉完不能按復原
> 這好像是vba天生的限制，目前想法是在進行轉換之前先另存新檔備份。
> [name=Arshain C]

- [x] 轉存的csv必須是UTF8 (Q__Q 目前都被要求必須是UTF8編碼)
> 我看code目前有自動設定成UTF8，如果有發生編碼錯誤，請再和我說。
> [name=Arshain C]

- [ ] 由於會有一些狀況是無法以這個VBA處理的(下面案例會寫)，但是執行VBA後它就會直接轉csv；但通常的流程是：1使用VBA處理合併儲存格 → 2繼續在excel中清資料 → 3才需要存csv，目前會在第1步就先轉成csv，所以第3步的時候儲存時有時會記得存csv但反而忘記把原本excel存起來。又或是，如果是多個工作表，按下VBA之後就會自動存成很多csv檔，或再做修改、再儲存時就會有點怕會出問題，最後就會覺得再按一次VBA好了。

\[以下是吹毛求疵的建議，大多是一些與合併儲存格無關的問題~~~~\]

### 無法處理：[資料集連結](https://www.dropbox.com/s/ehgcz1pcjpcs5k2/%E3%80%90%E7%B4%94%E6%95%99%E6%9D%90%E3%80%91%E9%AB%98%E8%A1%80%E5%A3%93%E8%B3%87%E6%96%99.xlsx?dl=0)

- [ ] 最右邊的「平均」，跑完之後「平」被刪掉了，未被併入平均同一格
- [ ] 小計、總計欄位無法刪除 (理想狀態下希望刪除)
- [ ] 左上角的欄位名稱會維持空白 (正確做法要加上「縣市別」，但應該沒法這麼聰明XD)
> 這檔案的難度很高，應該說對於本身沒有合併儲存格的，這程式好像反而無法處理。
> [name=Arshain C]


### 無法處理：[資料集連結](https://www.dropbox.com/s/wqa8p0a8zo87bbj/%E7%B6%9C%E5%90%88%E6%BC%94%E7%B7%B4%E6%A1%88%E4%BE%8B.xls?dl=0)

- [x] 不知道為什麼第一行不見了QQ
> 程式bug，已找到原因，要想一下怎麼處理
> [name=Arshain C]

- [ ] 最下面的「平均」其實應該要整行刪除，但是因為原本有合併儲存格，所以反而被拆成四個儲存格都寫平均
> 有想到解決方法，但要測試會不會矯枉過正
> [name=Arshain C]

- [x] 最下面表尾用文字方塊插入的內容沒有刪除
> 實際上因為csv不支援文字方塊，所以該方塊並不會被儲存，excel關掉重開檔案會發現它已消失
> [name=Arshain C]


### 無法處理：[資料集連結](https://www.dropbox.com/s/n36wpv6dq7mdyss/104%E5%B9%B412%E6%9C%88%E4%BE%9D%E6%B3%95%E6%87%89%E8%A8%AD%E7%BD%AE%E5%93%BA%E9%9B%86%E4%B9%B3%E5%AE%A4%E5%90%8D%E5%96%AE.xls?dl=0)

- [ ] 多個sheet，不知道為什麼轉出來的名字會都套用第一個sheet的基隆市
> 我這邊測試是正常的，我猜會發生這問題應該是使用者對同一個檔案執行了兩次vba
> [name=Arshain C]

> 然後第一次是選轉單頁，第二次轉全部
> [name=Arshain C]

> 如此第一次會把excel的第一頁「基隆市」轉成csv；其他分頁雖然未被儲存，但仍會在excel視窗中 
> [name=Arshain C]

> 而第一次轉換已經把「基隆市」加在標題後面
> [name=Arshain C]

> 在第二次轉換時，全部縣市就又被加在後面了，所以產生了這樣的問題
> [name=Arshain C]

> 建議：每次轉換完成後，若要再次轉換，把當前檔案關閉並重新開啟原始檔執行
> [name=Arshain C]


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_cf9246e8aab7c56d1d52ceedc8f86df1)

### 無法處理：[資料集連結](https://www.dropbox.com/s/3pdd1m6zcdvkxky/%E7%B6%9C%E5%90%88%E6%BC%94%E7%B7%B4%E6%A1%88%E4%BE%8B.xlsx?dl=0)

- [ ] 跟前面提的類似，左上角空白欄位、總計欄位無法處理



## 徵求協作者

- [ ] NeedsTech: 需要技術支援（VBA 或 其他使用者友善介面)
- [ ] NeedsPotentialUser: 需要使用者 / 推廣者 給予操作心得，以改善介面或增減功能
- [ ] NeedsOpenDataUser: 需要有人以開放資料使用者/網站設計者 之角度給予建議


## 實作細節（非技術背景可跳填）


### 協作工具

- github repo：
- hackfoldr 工作資料夾網址：
- google drive 共用資料夾網址：

### 進度與 to-do

> 僅供參考
> [name=ET B]

- [ ] product planning（recommanded procedure from justin lee / 李易修）
    - [ ] strategy
    - [ ] scope
    - [ ] structure
    - [ ] wireframe
    - [ ] visual
- [ ] web front-end
- [ ] web back-end
- [ ] ui / visual design


## 成果展示（規劃文件、雛形/草稿、原型/初稿、正式發佈/完稿）






