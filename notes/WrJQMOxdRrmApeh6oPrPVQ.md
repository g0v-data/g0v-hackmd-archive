---
title: "零時黑板(goban)協作"
tags: goban,hackpad
---

# 零時黑板(goban)協作

> [點此觀看原始內容](https://g0v.hackpad.tw/ziWKUvOISVt)


    主頁:[goban.tw](https://goban.tw)
    使用說明:[https://autolearn.hackpad.com/l1OAS7HV3t2](https://autolearn.hackpad.com/l1OAS7HV3t2)


### 徵人啟事


- [ ] needDesigner: 版型與視覺提示、感應式設計、小圖示優化等
- [ ] needWriter: 如何使用、新手上路、開發者使用說明等
- [ ] needMobileAppDeveloper: 徵求手機版
    (建議使用ionic framework + goban.js開發會比較輕鬆)


## 部件



### 源碼協作-模組部份

[https://github.com/bestian/goban](https://github.com/bestian/goban)


### 源碼協作-UI部份

[https://github.com/g0v/goban](https://github.com/g0v/goban)


### 文作協作-說明部份

- for g0v社群[https://g0v.hackpad.com/ziWKUvOISVt](https://g0v.hackpad.com/ziWKUvOISVt)
- for模組開發與使者[https://github.com/bestian/goban/blob/master/README.md](https://github.com/bestian/goban/blob/master/README.md)
- for非程式員[https://autolearn.hackpad.com/l1OAS7HV3t2](https://autolearn.hackpad.com/l1OAS7HV3t2)



## 功能許願與錯誤回報


[https://github.com/g0v/goban/issues](https://github.com/g0v/goban/issues)






- [x] 有時顯示不出聯想
    - [x] 原因: webConfig有時讀不到
    - [x] 正規方案:
        1.  讀不到時用angular廣播，自動重讀
        2.  用$timeout做確認
        3.  聯絡ethercalc的設計維護者，請求確認同時兩次ajax get請求時能否順利回應
> 請改用 [https://ethercalc.org/goban_introConfig.csv.json](https://ethercalc.org/goban_introConfig.csv.json)，不用自行解析 CSV，也會稍微穩一些
> [name=Audrey T]

> ok, thanks a lot
> [name=Bestian T]

> 這樣的話，資料結構也會要跟著微調一點，要把related和icons分成兩個Config，這樣也比較好寫
> [name=Bestian T]

> 過幾天閒下來時來改^_^
> [name=Bestian T]

> 改好了~
> [name=Bestian T]


