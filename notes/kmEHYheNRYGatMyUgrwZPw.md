---
title: "地方政府開放資料彙整與評比建議"
tags: hackpad
---

# 地方政府開放資料彙整與評比建議

> [點此觀看原始內容](https://g0v.hackpad.tw/eDY68cTC3Hv)

[http://local.data.g0v.tw/](http://local.data.g0v.tw/) \- 地方的資料需要普查

Update SEP2015: 因為 google spreadsheet 改版, opendatacensus backend 改成 postgresql, 想要繼續進行這個普查的話需要更新現有的 local.data instance，歡迎接手。 2014 普查的 data dump 在[這邊](https://docs.google.com/spreadsheets/d/1W-0i_n0flamQYkFYvIZWWaWUJCfWJTkehEK5pEc5Uy0/edit#gid=0)。

### FAQ


Q: 這是幹嘛的？
A: 常常一種資料是由地方政府各自公布的，希望透過這個表單，統整「單一資料」在各地的發佈現況，並提供目前社群已處理好的資料的資訊，以利利用。

Q: 如何增加一個資料普查的項目？
A: 到 [http://data.g0v.tw/](http://data.g0v.tw/), 登入候選擇「加資料」，填寫時勾選「此為地方普查資料」，再到 [http://local.data.g0v.tw/admin/reload](http://local.data.g0v.tw/admin/reload) 即可

### Status update

2014/09/18: 至目前為止，瀏覽量約一千人次，約有十人協助填寫約 70 個項目，但被提出需要普查的資料集數目不多，雖然有在兩次黑客松活動提及。若社群的跨縣市資料彙整需求不高，則需先集中理出各機關核心業務產生的資料，作為普查項目，再和幾堂相關的大學課程合作，協助完成普查。

### 其他問題與意見

> 請直接寫在[這裡](https://g0v.hackpad.tw/eDY68cTC3Hv)
> [name=Chia-liang K]

> 錯字 feedback : [http://logbot.g0v.tw/channel/g0v.tw/2014-08-06/196](http://logbot.g0v.tw/channel/g0v.tw/2014-08-06/196) (fixed)
> [name=lanfon]


### 資料評析蒐集部分

- data.g0v.tw 部分
    - [x] 提供 api query 「由地方政府釋出之資料集」，其中包括中央主管機關
> 主要覺得比較難的部份，是如何處理「更新」的偵測、自動化問題？
> [name=Jimmy H]

    - [ ] 新資料出現後, hook local.data.g0v.tw/admin/reload ([#11](https://github.com/g0v/local.data/issues/11))
- local.data.g0v.tw 部分
    - [x] 介面中文化
    - [ ] 增加「問題」部分 [#5](https://github.com/g0v/local.data/issues/5)
    - [x] 「問題」部分說明中文化 (可幫忙編輯[表中](https://docs.google.com/a/clkao.org/spreadsheet/ccc?key=0ApylrzoEp98gdEtUcGprZEVtZEhKaGJ4cEk3TC1PYmc#gid=0) @TW 部分, 參考[中國](http://cn-city.census.okfn.org/submit/))
    - [ ] Review 機制
    - [ ] 分數部分顯示調整
    - [ ] 多筆 review 整合（紀錄資料蒐集期間，資料集的改進）
    - [ ] 資料集 filter (過多時選擇顯示 subset)

> 或可以用 data.g0v.tw 開一個新欄位，對 data 進行縣市行政區的分類
> [name=Jimmy H]

> 然後用用 api 撈統計餵進去給 opendatacensus
> [name=Jimmy H]

####

### 評比規劃


###     評比相關想法


（此處實際評比部分由  ODA 進行，不在本顧問案中，但他們也很樂意聽取社群意見）

評比部分預計於七月實際進行，可考量的評分方式：
- 指標性資料集的開放現況
- 資料集在評比活動進行期間有所改善
- (your idea?)
-
單一評比指標為「各縣市政府在某一資料集提供」的「是否以數位方式提供、是否以結構化格式提供、是否開放授權，以及資料集網址」等客觀性條件。由社群提出各類指標並協作填寫該指標在各縣市現況之詳細內容。單一資料集亦可加註資料應用構想或現有成果。

接著由 ODA 選定 15-20 個項目，作為評比用指標。選定的條件以「已有中央主管機關將此類資料彙整、再發布」或「已有跨縣市資料之整合應用」為原則，並依照「資料集所屬業務主管機關」之分布平均為原則，以求各類業務涵蓋之廣度及代表性。
> 5 星open data的評比方式有在考慮之中嗎
> [name=Yuan C]


### 效益


除評選出單一縣市在各類資料釋出之情況總體努力外，亦可看出單一業務資料之主管機關與地方執行單位之整合度，並可讓民間快速了解何類資較完整，可由業者優先加值應用。


### 前情提要


【利益揭露】由於 ODA 邀請 clkao 至倫敦出席 opendata 交流，但因旅費無法直接報銷，需要找個 project 來做，因此雙方同意藉由進行「地方政府開放資料評比規劃」顧問案，經費 NT$105k 來 cover 旅費（預計實際工時 20hr）。對社群來說，可以順便整理各類已經從地方政府分別處理好、有在利用的資料，而 ODA 可由上述產出的資料現況，選擇一些指標性資料，來作為地方政府的評比依據。

ODA 方面同意所有產出原始碼以 MIT License 釋出、相關報告以 CC-BY-ND 釋出。


###     參考資料

> [http://tw-city.census.okfn.org/](http://tw-city.census.okfn.org/) CfT弄的
> [name=Yuan C]


[https://speakerdeck.com/clkao/di-fang-zheng-fu-kai-fang-zi-liao-ping-bi-gui-hua](https://speakerdeck.com/clkao/di-fang-zheng-fu-kai-fang-zi-liao-ping-bi-gui-hua)


