---
title: "國道車速預測和分析系統"
tags: hackpad
---

# 國道車速預測和分析系統

> [點此觀看原始內容](https://g0v.hackpad.tw/freewayAnalysis)


### 主旨:

此專案目的在收集高速公路各路段的車速, 利用統計的方式來預測一個禮拜內的車速, 方便使用者可以利用這判斷未來的車速避免遇到塞車的時段. 如果很多很多人使用, 說不定可以達到紓緩交通的目的. 避免國定假日車潮造成預測誤差, 統計的方式會將國定假日和平日分開統計.


### 希望可提供功能有:

- 未來七天所有路段的車速預測
- 顯示過去的車速資料
- 某路段的統計資料
- web api 方便第三方整合

### 目前系統開發狀態:

1.  爬資料, 目前是抓 [http://1968.freeway.gov.tw/](http://1968.freeway.gov.tw/) 資料
```
 https://github.com/lyanchih/goamf
 https://github.com/lyanchih/FreewayCrawler
```
2.  資料分析和 web api
```
 https://github.com/polor1010/freewayanalysis
```
3.  前端顯示部分
```
 http://polor1010.github.io/

```
目前爬蟲和資料分析都是用 golang 來寫, 由於在web開發上經驗不足, 所以開發速度很慢很慢, 去年十一月就開始寫了QQ. **很需要前端部分的人來幫忙完成**. 這樣會比較能專心在後端的開發和預測模型的建立. 大概就這樣子.



