---
title: "magic-mirror"
tags: hackpad
---

magic mirror
====

本專案的目的，在於自動化修復 *.gov.tw 各資料源的格式問題，以加速化目前開放資料來源的應用。

經過修整後資料，列於：http://g0v-data-mirror.gugod.org/ 

:warning: 目前正在大幅度重新整理。2013 年至 2019 年份的資料集將改以 .tar.gz 的形式釋出。github 上的副本亦將會被刪除。有任何問題請到 slack 找 @gugod

## 鏡射站址

網址別
- https://github.com/g0v-data/mirror

年份別
- https://github.com/g0v-data/mirror-2013
- https://github.com/g0v-data/mirror-2014
- https://github.com/g0v-data/mirror-2015
- https://github.com/g0v-data/mirror-2016
- https://github.com/g0v-data/mirror-2017
> 切割檔案使用的是 GMT 時間，因此 mirror-2017/taipower/loadareas/2017-05-28/06-30.csv 事實上是 14:30 (GMT+8) 取得的檔案[name=kiang]

- [ ] TODO: 資料及將會被重新整理，依年份別，另外放在其他網址。以後不會一直使用 github 作為散佈這些資料集的手段。

## 來龍去脈

在 data.gov.tw 上條列出了許多目前政府機機關有開放出的資料。不過有仍有幾點問題：

1. 多數資料集都會在更新於同一網址，而在更新之後，舊版的資料便無法取得
2. 有許多資料為 CSV 格式，但各欄位的內容與格式卻良萎不齊
3. 資料 URL 分佈各站，且不容易得知各資料表中各筆資料是否彼此之間有關聯性

為此，希望能有一中介的鏡像站一併解決上述三項問題。

1. 定時備份原始資料，並存入 git，因此也能回頭再取得舊版
2. 將各 CSV （或其他）格式的檔案轉成 JSON，以便其他程式利用。並同時修復內容中的格式錯誤。其他程式可利用 github （或其他）做為資料源。
3. 各資料檔之間若有關聯，也可另行合併一次，另做成去正規化的輸出。

牽涉領域：基礎建設

現有類似專案

相關組織單位：

相關專案
- g0vre
- aec-data

授權方式
程式碼部分 CC0
文件部分 CC0

使用資料

專案目前狀態
自動營運中。
仍需需作更多資料處理函式。


## 目標與功能

預定使用者
其他開發人員。

預定功能

使用方式
可透過 github.io 網址取得 json 格式的資料。


## 實做細節

使用技術
- perl
- git

協作工具

github repo：
http://github.com/g0v/magic-mirror
http://github.com/g0v-data/mirror/ # 內容為自動產生
hackfoldr 工作資料夾網址：無
google drive 共用資料夾網址：無
irc channel：#g0v.tw

## 運行狀態

目前 magic-mirror  中的程式碼已設定為定時執行，抓取新版後、自動處理後公佈於：

http://g0v-data-mirror.gugod.org/

各資料源的 URL 及檔名對應、時程等等，設定檔為 JSON 格式放在源碼的 etc/ 目錄中。另外，歷史資料也存於 github 上： http://github.com/g0v-data/mirror/  。repository 內以政府網站域名做為資料夾。以「停水通知」（water/suspension.csv) 為例，以下分別為網頁觀看版與下載版：

- https://github.com/g0v-data/mirror/blob/gh-pages/water/suspension.csv
- http://g0v-data-mirror.gugod.org/water/suspension.csv

因為累計 commit 數極多，被 github 站方通知此自動生成的頁面耗去不少資源，因此我另外架在 linode 上。網址為：

http://g0v-data-mirror.gugod.org/

為了方便批次處理， 各年份的所有資料集，另行匯出至不同的倉儲：

https://github.com/g0v-data/mirror-2013
https://github.com/g0v-data/mirror-2013
https://github.com/g0v-data/mirror-2014
https://github.com/g0v-data/mirror-2015
https://github.com/g0v-data/mirror-2016
https://github.com/g0v-data/mirror-2017

此倉儲中，所有的資料集的所有歷史紀錄皆依照其下載日期時間，整理在目錄中。此版本的倉儲十分佔據空間，mirror-2016 在 `git clone`  之後需要 91GB 硬碟空間。請稍加注意。

## 開發者
[@gugod](https://g0v.social/@gugod)

分工與成員
NeedsWriter: 需要文案幫手（撰寫基本資訊、報導專案etc）
NeedsDesigner: 需要介面設計
NeedsData: 需要資料（擷取、清理）
NeedsTech: 需要技術支援（程式、架站 etc)
NeedsProcess: 需要幫忙設計作業流程
NeedsTalkingToRealPerson: 需要有人幫忙和其他機關聯絡
設定成 project registry 中的 tags，需要幫忙的會自動 promote 到 g0v project hub





