---
title: "電腦端立院IVOD下載器"
tags: g0v ly,hackpad
---

# 電腦端立院IVOD下載器

> [點此觀看原始內容](https://g0v.hackpad.tw/KdTs5gZb3yw)


目前有一些團體會抓下立法院IVOD影片來進行編輯，但目前立法院的影片很難直接抓下。
Command Line工具已經有了，希望有人可以幫忙製作Windows、Mac版本的GUI版工具，方便大家下載IVOD。

### 工具需求：

輸入（貼上）IVO[http://ivod.ly.gov.tw/Play/Full/11610/300K](http://ivod.ly.gov.tw/Play/Full/11610/300KD網址)[D網址](http://ivod.ly.gov.tw/Play/Full/11610/300KD網址)
自動轉為高品質網址（把300K改為1M）
下載影片並重新命名為好讀的影片，例如「2014-09-25 內政 段宜康」

### 測試網址：

[http://ivod.ly.gov.tw/Play/VOD/76394/300K](http://ivod.ly.gov.tw/Play/VOD/76394/300K)
[http://ivod.ly.gov.tw/Play/Full/7959/300K](http://ivod.ly.gov.tw/Play/Full/7959/300K)

### Command Line工具（Mac、Windows版可用）：

- python version
    - [https://github.com/billy3321/ivod-download-client](https://github.com/billy3321/ivod-download-client)

./ivod\_single\_downloader.py -u '[http://ivod.ly.gov.tw/Play/VOD/76394/300K](http://ivod.ly.gov.tw/Play/VOD/76394/300K)'

-u IVOD URL

### GUI (Windows可用)：

###     巴克里版本

    - 使用：下載後解壓縮就可以使用，執行 run.exe 檔案。 下載 [http://blog.jangmt.com/2014/10/ivod-gui-win-protable.html](http://blog.jangmt.com/2014/10/ivod-gui-win-protable.html) 。
    - 這程式用 phpdesktop ([http://code.google.com/p/phpdesktop/](http://code.google.com/p/phpdesktop/)的工具)[)的工具](http://code.google.com/p/phpdesktop/)的工具)，它已經把 chrome 、PHP及 IVOD PHP程式碼整個包起來，看起來更像是一個桌面程式。(實際是本地端的 Client-Server 架構的程式)
###     PHP-GUI版

```
https://github.com/cic-tw/ivod-downloader
```
###     PyQT版

        [https://github.com/chpaul/iVodDownloader](https://github.com/chpaul/iVodDownloader)
        裡面有包Mac app，不過使用前還是要預先安裝php-mcrypt。安裝方式：
        先安裝brew，然後
        brew install php56-mcrypt
### Chrome Extension 版

- 需使用改寫中的 ivod-download-client 內的 ivod\_schedule\_download_web.py 啟動 local web
- 原始碼與使用說明 [https://github.com/qrtt1/ivod-download-chrome-extension](https://github.com/qrtt1/ivod-download-chrome-extension)
    - 這個 extension 會呼叫 ivod-download-client 提供的 twly-ivod-dl-chrome-extension-receiver 進行下載工入，需先向 chrome 註冊此外部程式方能使用。
    - 雖然有寫「安裝」步驟，但是還是很麻煩，希望有空時再加安裝程式
- 希望獲得協助：
    - windows installer
        [https://github.com/qrtt1/ivod-download-chrome-extension/blob/master/INSTALL_WIN32.md](https://github.com/qrtt1/ivod-download-chrome-extension/blob/master/INSTALL_WIN32.md)
    - osx installer

### 網頁下載器

- LY做的網路下載器
    - [https://ivod-ly.herokuapp.com/](https://ivod-ly.herokuapp.com/)

### 其他工具

- ivod 影片清單 - [https://github.com/kiang/ivod.ly.gov.tw](https://github.com/kiang/ivod.ly.gov.tw)
    - 只是一個小程式，把 ivod 網站上的資訊做個清單，方便批次使用 Command Line工具下載影片。根目錄的 csv 檔案是依據年份切割，個別影片的 meta data 可以在 Legislator 目錄中找到
-

