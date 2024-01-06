---
title: "萌典 @ 美麗島黑客松"
tags: hackpad
---

# 萌典 @ 美麗島黑客松

> [點此觀看原始內容](https://g0v.hackpad.tw/tDx3D5FZya5)


這是初步的一些想法，有興趣的朋友可以挑一兩樣實做，也歡迎加入新的項目。
    簡報:  [**http://tinyurl.com/hackath5n-moedict**](http://tinyurl.com/hackath5n-moedict)

## [兩岸詞典](https://github.com/audreyt/moedict-webkit/issues/83)

> Needs: Design, Testing
> [name=Audrey T]

- [ ] 設計兩岸詞典與現行三部詞典之間的跨語交叉檢索
- [ ] 設計排版：第二級縮排（如「太」 [http://](http://www.moedict.tw/~%E5%A4%AA)[w](http://www.moedict.tw/~%E5%A4%AA)[w](http://www.moedict.tw/~%E5%A4%AA)[w](http://www.moedict.tw/~%E5%A4%AA)[.](http://www.moedict.tw/~%E5%A4%AA)[moedict.](http://www.moedict.tw/~%E5%A4%AA)[t](http://www.moedict.tw/~%E5%A4%AA)[w](http://www.moedict.tw/~%E5%A4%AA)[/~%E5%A4%AA](http://www.moedict.tw/~%E5%A4%AA) )
- [ ] 設計排版：||也作「某某」是代表以上義項都相同。如：\[[上頭](https://www.moedict.tw/#~%E4%B8%8A%E9%A0%AD)\] 第二條，輕聲，第三義項，應先呈示例，換行，再加||也作「某某」。

## [筆順動畫](https://github.com/g0v/zh-stroke-data/tree/compose)

> Needs: Node, Chinese
> [name=Audrey T]

- [x] 修正補缺字程式，使用部件的實際長寬，而非框線長寬組字
- [x] 用 indices 的方式補上非整字的部件，如礻辶等

## [單詞分享鏈結](https://github.com/audreyt/moedict-webkit/issues/14)

> Needs: Design, Node, JS
> [name=Audrey T]

- [ ] 讓目前網址去掉 # 號時傳回完整的分享頁面，如 [https://moedict.tw/萌](https://moedict.tw/萌)
- [ ] 加入 OpenGraph 支援
- [ ] 加入 oEmbed 嵌入支援

## [書籤功能](https://github.com/audreyt/moedict-webkit/issues/49)

> Needs: Design, JS
> [name=Audrey T]

- [x] 在詞目旁邊加上星號★
- [x] 選單裡加上一個「字詞紀錄簿」選項，列出之前使用者按星號的條目。

## [字型呈現校正](https://github.com/audreyt/moedict-webkit/issues/77)

> Needs: Typographer, JS
> [name=Audrey T]

- [x] 修正 Chrome Blink (Android 4.3) 的台文輕聲調號[組字問題](https://github.com/audreyt/moedict-webkit/issues/54)
- [ ] [注拼音直橫混排](https://www.moedict.tw/experimental-mps/right-angle.html) 做成 JS plugin，並確認各瀏覽器的位置無誤
- [ ] 修正各螢幕寬度的避頭點問題

## [全文檢索](https://github.com/audreyt/moedict-webkit/issues/81)

> Needs: Technical Review
> [name=Audrey T]

- [ ] 評估後端檢索方案 (gugod 對國語辭典部份做了 ElasticSearch)
- [ ] 評估前端檢索方案 (SQL in browser? emscripten?)

## [手勢操作界面](https://github.com/audreyt/moedict-webkit/issues/31)

> Needs: UX Designer
> [name=Audrey T]

- [ ] 改進目前 click、touchstart、pinch 混合使用的情況，訂出 guideline
- [ ] 設計 swipe left/right 的歷史導航操作，以及其他 swipe 操作效果

## [各語種成為獨立 App](https://github.com/audreyt/moedict-webkit/issues/26)

> Needs: Cordova, iOS, Android, JS
> [name=Audrey T]

- [ ] 定義 URL scheme 讓跨語交叉檢索可以切換到別的 App (如有安裝)
- [ ] 定義 [離線語音包](https://github.com/audreyt/moedict-webkit/issues/26#issuecomment-26613125) 需要時可下載使用

## [Firefox Open Web App](https://marketplace.firefox.com/app/moedict/)

> Needs: Testing, JS
> [name=Audrey T]

- [x] 製作、測試 Firefox OS 和桌面 (Prism) 上的離線版萌典
- [ ] 評估 appCache/localStorage 與 package app 整合之可能性

