---
title: "立法院開放資料使用問題"
tags: hackpad
---

# 立法院開放資料使用問題

> [點此觀看原始內容](https://g0v.hackpad.tw/AJnmSQO2kKk)


## 還希望有什麼資料

- 立院、委員會表決資料
是否考慮整併其他部門之資料，如中選會、監察院
> 這大概超過立院職權，比較適合民間做
> [name=Chia-liang K]

- 會議紀錄希望結構化呈現，可以參考 [http://sayit.archive.tw/speeches](http://sayit.archive.tw/speeches)
> 目前主要是委員會紀錄比較亂，ivod 現在開始有 link 到片段的發言紀錄
> [name=Chia-liang K]


## 委員類

- 缺少唯一識別碼，無法辨認不同屆的同一委員
- 離職立委如有遞補立委，是否加開欄位補充說明
- JSON 格式的下載網址中 selectTerm 應為 term，否則無法依屆期查詢
- 國會圖書館有第一屆立委資料，可否整併

## 質詢類

- 可將本院委員提出之質詢與行政院之答覆合併，或至少提供對應代碼，方便理解來龍去脈
> 國會圖書館的查詢有連結回應，希望國會圖書館的資料庫整個開放
> [name=Chia-liang K]


## 議事類

- ** 法律條文對照表**
    - 是否與法律提案資料集（[http://data.ly.gov.tw/getds.action?id=20](http://data.ly.gov.tw/getds.action?id=20)）整合，兩者有共通的billNo
> <平臺回覆>您好; 有關台端建議一事(是否與法律提案資料集整合)，您的建議我們將列入資料集調整之參考，謝謝您的寶貴意見。 立法院開放資料服務平臺 敬復
> [name=johnny]


    - 條文對照表中的每一條分別放在不同的dictionary {...}中，是否可將同個billNo的條文整合成一個有順序的 array，例如：
        ```
        {
        "billNo": "123",
        "lines": \[
            {
            "activeLaw": "abcde",
            "reviseLaw": "bbcde",
            "description": "some change",
            ...
            },
            {
            "activeLaw": "12345",
            "reviseLaw": "22345",
            "description": "some change",
            ...
            },
```
  ]
}
```
        ```
    - 不同會議被提出的條文目前在平台上會重複出現（同billNo不同會議），但內容都是一樣的，請問不同會議的條文有可能不一樣嗎？
    - 欄位說明與實際的值意義不符：e.g. docUrl：關係文書doc檔案下載位置，實際資料："docUrl":"院總第1574號委員提案第12885號",
> <平臺回覆>您好; 有關台端建議一事(欄位說明與實際的值意義不符：e.g. docUrl：關係文書doc檔案下載位置)，經檢討後已於近日修正完畢，謝謝您的寶貴意見。 立法院開放資料服務平臺 敬復
> [name=johnny]


    - docUrl修改成連結後，可否加開欄位保留提案號資訊（例如：院總第1574號委員提案第12885號）
> <平臺回覆>您好; 有關台端建議一事(加開一欄位保留原提案號的資訊)，在提高資料集完整性之考量下，接受您寶貴意見且於近日修正完畢(增加一欄位docNo:文號)，謝謝您的寶貴意見。 立法院開放資料服務平臺 敬復
> [name=johnny]


    - null變成文字型態："meetingTimes":"null"
    - "1021220070200100"、"1021227070200900"這兩個billNo有同樣的資料
    - 第八屆法案在立法院議事及發言整合系統（[http://lis.ly.gov.tw/lylgmeetc/lgmeetkm_lgmem](http://lis.ly.gov.tw/lylgmeetc/lgmeetkm_lgmem)）中有，但在開放資料平台此資料集中找不到，如下列：（[https://goo.gl/KqQk8h](https://goo.gl/KqQk8h)）
- ** 法律提案**
    - 提案人、連署人是否應將資料型態轉成 array，目前為全形空白分隔
    - 提供審議進度，如立法院議事及發言整合系統中的資訊
    - 提供主題、類別，如立法院議事及發言整合系統中的資訊


