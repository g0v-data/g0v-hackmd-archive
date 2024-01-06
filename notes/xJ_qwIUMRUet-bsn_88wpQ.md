---
title: "資料庫Schema"
tags: hackpad
---

# 資料庫Schema

> [點此觀看原始內容](https://g0v.hackpad.tw/uPosk9mVzd9)

以後直接在這邊修改，留下紀錄吧
最近更新是根據8/16的討論後重新設計的DB Schema
[https://g0v.hackpad.com/X2h4X1iYek7](https://g0v.hackpad.com/X2h4X1iYek7)

DB使用Mongo

Collection －News：抓取到的新聞
    欄位：
        \[_id\]：預設主鍵。內容物為ObjectID。
        \[newspaper\]：此新聞所屬媒體。內容物為字串。
        \[topicId\]：此新聞歸屬議題，由後臺指派。內容物為ObjectID陣列，ObjectID對應Collection－Topic的主鍵。
        \[title\]：新聞標題。內容物為字串。
        \[article\]：新聞內容。內容物為字串。
        \[newsTime\]：新聞發布時間。內容物為Date物件。
        \[createTime\]：資料建立時間。內容物為Date物件。
        \[updateTime\]：資料更新時間。內容物為Date物件。
        \[author\]：新聞作者。內容物為字串。
        \[picture\]：新聞相關圖片。內容物為網址字串陣列。
        \[sourceUrl\]：新聞來源網址。內容物為字串。
        \[score\]：新聞分數，定時依據Collection －Comment的資料計算而出。內容物為物件，各屬性分別儲存不同類別、評論員等級的分數。
    索引：
        主鍵：\[_id\]，唯一性。
        索引：\[topicId\], \[newsTime\]。
        Unique: \[_id\], \[sourceUrl\]

Collection －Topic：議題列表，由後臺編輯。
    欄位：
        \[_id\]：預設主鍵。內容物為ObjectID。
        \[name\]：String = 議題名稱。內容物為字串。
        \[description\] : String = 議題介紹
        \[sort\]：Number = 在App顯示時的排序，直接由後臺設定。內容物為數字。設為null時不顯示該議題。
        \[topicTagSet\]：議題關鍵字。內容物為字串陣列。
        \[score\] : Object = 本議題目前的發霉分數，定時依據Collection －Comment的資料計算而出。內容物為物件，各屬性分別儲存不同類別、評論員等級的分數。
        \[photo\] : String =  議題照片URL
        \[createdTime\] : Time = 議題開始時間
        \[latestTime\] : Time = 議題最後更新時間，指派新聞至某議題時亦會更新此時間。內容物為Date物件。
    索引：
        主鍵：\[_id\]，唯一性。
        Unique: \[_id\], \[name\]
        索引：\[sort\]。

Collection－Comment：評論列表，來源為App使用者評論。
    欄位：
        \[_id\]：預設主鍵。內容物為ObjectID。
        \[news\]：評論的新聞。內容物為ObjectID，對應至Collection－News的主鍵。
        \[user\]：評論者。內容物為字串，對應至使用者資料的主鍵。
        \[level\]：評論等級，紀錄評論者評論時的會員等級（註冊、認證、專家）。內容物為字串。
        \[version\]：評論時所使用的評論機制版本。內容物為字串。
        \[score\]：評論分數，當評論送出後，後臺依據評論機制版本與評論選項內容計算而出。內容物為數字。
        \[data\]：評論資料，記錄使用者送出評論時勾選跟填入的所有資料。可能會有的論述亦存在其中，顯示時前段依評論機制版本取出展示。內容物為物件，物件格式依評論機制版本而有不同。
    索引：
        主鍵：\[_id\]，唯一性。
        唯一鍵：\[news\]＋\[user\]，唯一性。
        索引：\[news\]+\[level\]+\[version\]+\[score\]。

Collection－Discuss：討論資料，來源為App使用者對新聞的討論。
    欄位：
        \[_id\]：預設主鍵。內容物為ObjectID。
        \[news\]：評論的新聞。內容物為ObjectID，對應至Collection－News的主鍵。
        \[user\]：評論者。內容物為字串，對應至使用者資料的主鍵。
        \[like\]：按讚紀錄。內容物為字串陣列，對應至使用者資料的主鍵。
        \[dislike\]：按噓紀錄。內容物為字串陣列，對應至使用者資料的主鍵。
    索引：
        主鍵：\[_id\]，唯一性。
        索引：\[news\]。
        索引：\[user\]。

Collection－users：使用者資料。（這裡大部份是meteor帳號系統的預設值）
    欄位：
        \[_id\]：預設主鍵。內容物為字串。
        \[username\]：使用者帳號。內容物為字串。
        \[email\]：使用者Email，內容物為物件陣列。
        \[profile\]：使用者資訊，含等級與經驗值等。內容物為物件。
        \[services\]：使用者登入資訊，含加密之密碼及facebook登入token等資料。
        \[createdAt\]：使用者註冊日期，內容物為日期物件。
    索引：
        主鍵：\[_id\]，唯一性。
        索引：\[username\]，唯一性。











