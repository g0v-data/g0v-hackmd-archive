---
title: "選舉黃頁與公報連結整理"
tags: hackpad
---

# 選舉黃頁與公報連結整理

> [點此觀看原始內容](https://g0v.hackpad.tw/4EfvaDqwVnr)


公報專案： [https://github.com/kiang/bulletin.cec.gov.tw](https://github.com/kiang/bulletin.cec.gov.tw)

中選會選舉公報的資料有備份到公報專案，針對 103 年的部份中選會有一個尚未對外正式宣傳的網站 [http://103bulletin.cec.gov.tw/103/](http://103bulletin.cec.gov.tw/103/) ，這個網站有各地選委會上傳的資料，所以額外處理，目前公報專案的資料集中在 [https://github.com/kiang/bulletin.cec.gov.tw/tree/master/Console/Command/data](https://github.com/kiang/bulletin.cec.gov.tw/tree/master/Console/Command/data)  ，說明如下：

- bulletin.csv - [http://db.cec.gov.tw/](http://db.cec.gov.tw/) 取得的公報資料清單
    - 連結目錄
    - 連結名稱
    - 檔案網址
    - 隨機產生的 uuid
- bulletin_103.csv - [http://103bulletin.cec.gov.tw/103/](http://103bulletin.cec.gov.tw/103/) 取得的公報資料清單
    - 連結名稱
    - 檔案網址
    - 隨機產生的 uuid

透過清單中的 uuid 可以分別在 pdf ( bulletin.csv uuid ) & pdf\_103 ( bulletin\_103.csv uuid ) 目錄下找到對應的 pdf 檔案，這些 PDF 檔案進一步透過 [pdf2htmlEX](https://github.com/coolwanglu/pdf2htmlEX) 產出了文字座標檔案放在 txt 與 txt_103 目錄下對應的 uuid 中。

現在進一步的試著要將這些公報資料與選舉黃頁進行連結，所以透過程式產出了對應表
[https://github.com/kiang/elections/blob/master/Console/Command/data/bulletin_map.csv](https://github.com/kiang/elections/blob/master/Console/Command/data/bulletin_map.csv)

檔案中三個欄位說明如下：
- bulletin\_name - bulletin\_103.csv 取得的連結名稱
- bulletin\_key - bulletin\_103.csv 取得的 uuid
- election_id - 對應到選舉黃頁選區的 uuid ，多個選區之間以 | 符號區隔

因為命名並未統一，所以這個自動產生的對應表有諸多錯誤，所以另外產生了一個修正表
[https://github.com/kiang/elections/blob/master/Console/Command/data/bulletin\_map\_prefix.csv](https://github.com/kiang/elections/blob/master/Console/Command/data/bulletin_map_prefix.csv)

修正表格式與原本的表一致，只是程式會以修正表的資料為主，每次執行後會合併程式自動過濾的結果，所以錯誤的資料列可以複製到修正表進行人工的修正，然後由程式處理最後的合併與連結。

election_id 可以透過[選舉黃頁](http://k.olc.tw/elections/)的選舉區查詢功能，點選結果後網址的參數就是 election_id ，像是
[http://k.olc.tw/elections/candidates/index/53c0207b-32e8-4ba0-a87c-5c5aacb5b862#/discussion/embed](http://k.olc.tw/elections/candidates/index/53c0207b-32e8-4ba0-a87c-5c5aacb5b862#/discussion/embed)

53c0207b-32e8-4ba0-a87c-5c5aacb5b862 就是希望取得的 election_id

而 bulletin_key 可以透過網址預覽，像是 546e068c-43f4-4e44-b9f7-1a32cf91e152 就可以在下面網址看到
[http://k.olc.tw/bulletin/546e068c-43f4-4e44-b9f7-1a32cf91e152/546e068c-43f4-4e44-b9f7-1a32cf91e152.html](http://k.olc.tw/bulletin/546e068c-43f4-4e44-b9f7-1a32cf91e152/546e068c-43f4-4e44-b9f7-1a32cf91e152.html)

這是透過 [pdf2htmlEX](https://github.com/coolwanglu/pdf2htmlEX) 產出的結果

