---
title: "g0v 文化部授權中心"
tags: hackpad
---

# g0v 文化部授權中心

> [點此觀看原始內容](https://g0v.hackpad.tw/LoscL87LD2a)


\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-

### 授權中心 @ hackath6n


- 整理所有文化部作品與授權資訊，不用重複詢問檔案在哪、授權是什麼
- 不用手動做每個網頁，寫程式自動生出 html 來

雛形
- [http://g0v.github.io/moc-license-center/index.html](http://g0v.github.io/moc-license-center/index.html)
- [http://g0v.github.io/moc-license-center/illustration-newshelper.html](http://g0v.github.io/moc-license-center/illustration-newshelper.html)

使用技術
- mockup: sass, compass, jade, fire.app, semantic ui

需要
- [x] front end programmer: ddio
    - 寫一段神奇的 script，抓取 portfolio/ 底下的所有圖檔，從 jade template 自動生出首頁的作品清單以及作品個別頁面來
    - 制訂 json 檔格式，以後只要照這格式寫，作品 metadata 就會自動被塞到 jade template 裡面去生 html


\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-

### 緣由


g0v 內部的美術、設計、音樂、投影片、作品散落各處，自己人很難找，外人更難取得，所以需要有一個介面，讓一般人上網就可以觀賞、下載文化部的作品。

主旨：整理所有針對一般大眾（非開發者或參與者）的資原，讓他們可以方便取用
牽涉領域：基礎建設
現有類似專案：文化部協作檔案大多放 google drive ，但不適合展示，權限也沒控管，怕分享者不小心刪檔或搞爛東西。

相關組織單位：g0v 文化部
相關專案：g0v 人力資源部、[著作權小幫手](https://g0v.hackpad.com/--dzGPPZoP4bO)

授權方式：程式碼部分…MIT或BSD？給 clkao 決定 XD
使用資料：要自己生各作品的 json 檔

### 目標與功能


預定使用者：非 g0vers，不瞭解 g0v 的一般使用者
預定功能：可以在同一個介面裡輕鬆地看到所有 g0v 成果，除了文藝類的之外也同時收錄各專案上線網址（而不是很宅的 github repo）
使用方式：上網、看圖、聽歌、下載、改作
浮水印功能參考（見其中 copyright 部分，可手動或抓 metadata）：

[http://youtu.be/KcQAPXG5KWc](http://youtu.be/KcQAPXG5KWc)

### 實做細節


使用技術
- 前端： sass, compass, jade, fire.app, semantic ui
- 後端？

協作工具
- github repo：[https://github.com/g0v/moc-license-center](https://github.com/g0v/moc-license-center)
- hackfoldr 於 [基礎建設](http://hack.g0v.tw/meta/LoscL87LD2a)
- google drive 參考 [文化部](https://drive.google.com/folderview?id=0B0NsS2a-Qx8ZLTBpakgwVTJmak0&usp=drive_web)
- google groups 參考 [文化部](https://groups.google.com/forum/#!forum/g0v-moc)
- irc channel 同 g0v.tw

產出檔案格式
- html / css

進度與 to-do
- [ ] 網站架構
    - [x] 首頁
        - [x] 授權中心主頁
            - [x] 插畫作品頁面 [http://](http://g0v.github.io/moc-license-center/illustration-newshelper.html)[g0v.github.io/moc-license-center/illustration-newshelper.html](http://g0v.github.io/moc-license-center/illustration-newshelper.html)
            - [ ] 漫畫作品頁面
            - [ ] 設計作品頁面
            - [ ] 音樂作品頁面
            - [ ] 攝影作品頁面
            - [ ] 投影片作品頁面
        - [x] 軟體中心主頁
- [ ] 內容管理
    - [ ] 自動化功能：自動抓取所有檔案路徑然後套到 html 模版中，自動生出作品頁面
- [ ] github issue: [g0v/dev#18](https://github.com/g0v/dev/issues/18)

### 成果


雛形
- [http://g0v.github.io/moc-license-center/index.html](http://g0v.github.io/moc-license-center/index.html)
- [http://](http://g0v.github.io/moc-license-center/illustration-newshelper.html)[g0v.github.io/moc-license-center/illustration-newshelper.html](http://g0v.github.io/moc-license-center/illustration-newshelper.html)

### 開發者


分工與成員
- 規劃、設計：ETBlue
- 前端：ddio


----------開發筆記----------

完成後，授權中心網站的連結可以放在 hackfoldr 或 g0v.tw 官網

包含內容
- 文字
- 圖片
    - 單張圖片：純插圖、內含文字的插圖
    - 多張圖片：連環漫畫、連環投影片
- 照片
- 影片
- 投影片
- 音樂
- 上述幾種混合而成的素材

架站用
- github pages XD

有哪些授權方式？
- WTFPL（聽起來就很酷，但沒有免責聲明，好像比較不完整）
- CC0
- CC 系列
- non-free charityware (careware) [來源](https://plus.google.com/u/0/110174937980629662857/posts/dmax9wuCRQf)
    - careware 的捐贈方式有哪些？
        - 捐給指定 NPO 組織
        - 購買軟體、硬體、資訊服務... 後捐給指定 g0v 專案


### irc 上的討論


[http://logbot.g0v.tw/channel/g0v.tw/2013-08-16#737](http://logbot.g0v.tw/channel/g0v.tw/2013-08-16#737)
- clkao: ETBlue, tuiry 對了，我昨天想到一個 idea - 就是如果有創作要 CC-BY-NC，也就是歡迎非營利使用，但商用（如刊登於媒體）可以有一個地方列出每項作品的授權金，但只接受捐贈給某些個社福團體的收據，作為付款方式
> 這會是獨立的授權方式，可與 CC 並列，需要仿 CC 擬完整條款，名稱要獨特一點才容易搜尋
> [name=Hsiao-hsien Y]

- clkao: .... 然後數字要訂怪一點的，每種作品不同.. 如 3133.7 元 以免用同份捐款收據 XD
- 可以捐贈 amazon coupon、code school gift of code、指定廠牌型號的硬碟、... 等物品嗎？

[http://logbot.g0v.tw/channel/g0v.tw/2013-08-27#257](http://logbot.g0v.tw/channel/g0v.tw/2013-08-27#257)
- dirty_應該要做個 g0v presentation hub 的
- billy3321 dirty_: 可以規劃在文化部授權中心的一部份
- yhsiang presentfoldr?
- billy3321 yhsiang: 但是投影片有好幾種耶
- [11:49:05](http://logbot.g0v.tw/channel/g0v.tw/2013-08-27#261)billy3321 pdf、prezi、google docs、ppt...
- [11:51:55](http://logbot.g0v.tw/channel/g0v.tw/2013-08-27#262)tkirby話說回來, github 上有個 slide 的集散地
- ipa  [https://github.com/g0v/dev/tree/gh-pages/talks](https://github.com/g0v/dev/tree/gh-pages/talks)
- [11:52:19](http://logbot.g0v.tw/channel/g0v.tw/2013-08-27#264)ipa[http://g0v.tw/news.html#news_media](http://g0v.tw/news.html#news_media) 首頁也有
- dirty_ presentation hub 除了 bily3321 講的幾種格式外, 有一些有錄影的也可以加進去
-

