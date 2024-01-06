---
title: "g0cr / g0vcaptcha"
tags: hackpad
---

# g0cr / g0vcaptcha

> [點此觀看原始內容](https://g0v.hackpad.tw/Lyk6kEGWSNH)


## Strategy

此專案的目的在批次處理文件的掃描圖檔，轉換為文字。

*.gov.tw 上許多報告文件雖是 PDF，但其內容卻是紙本報告掃描而成的圖檔，無法快速傳成文字格式、或建立索引。因此必需要由人工來處理。

運作方面，打算仿效 recaptcha 的方式，先把圖檔切成較小的文字區塊，一方面可以丟給程式做 OCR，另一方面做出界面讓使用者提供正確答案。

最終的產品，是把上傳的圖檔轉成純文字格式，讓人可以搜尋，或讓外部搜尋引擎可以抓取內容回去。

## Scope

web app: [http://g](http://g0cr.gugod.org/)[0](http://g0cr.gugod.org/)[c](http://g0cr.gugod.org/)[r](http://g0cr.gugod.org/)[.g](http://g0cr.gugod.org/)[u](http://g0cr.gugod.org/)[g](http://g0cr.gugod.org/)[o](http://g0cr.gugod.org/)[d.o](http://g0cr.gugod.org/)[r](http://g0cr.gugod.org/)[g](http://g0cr.gugod.org/)[/](http://g0cr.gugod.org/)
git repo: [https://github.com/g0v/g0vcaptch](https://github.com/g0v/g0vcaptch)


Web App
- [x] 讓人上傳文件
- [x] 顯示機器辨識的結果
- [ ] 實做多種機器辨識演算法，以提升整體的正確率（recall）
- [ ] 讓人可修正機器辨識的文字
- [ ] 顯示人工辨識的結果
- [ ] 提供搜尋介面，讓人可搜尋文件內容
- [ ] 提供每份文件的靜態版，讓外部搜尋引擎抓取
- [ ] 讓人可提供文件的輔助資訊，例如：來源，摘要，原下載網址。

Background job
- [x] 抓取文件中有字的區塊，並進行機器辨識
> 目前使用 tesseract 做成 HOCR 格式的輸出。
> [name=Kang-min L]

- [ ] 整合所有區塊，製成成靜態版（純文字及 HTML）


## Structure


## Wireframe / Content


## Visual


## 白老鼠/狗食部落客

- 如果有這功能，我可以把我們所有客戶的captcha都逐步換上。



