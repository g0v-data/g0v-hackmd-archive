---
title: "hackfoldr 孤兒園"
tags: hackpad
---

# hackfoldr 孤兒園

> [點此觀看原始內容](https://g0v.hackpad.tw/Nkxax2XjzHI)


目前 [hackfoldr-backup](https://github.com/JmeHsieh/hackfoldr-backup-g0v) 的機制是掃瞄所有 g0v hackpads 以找出 hackfoldrs。
所以如果某個 hackfoldr 不曾出現在任何一個 hackpad，[hackfoldr-backup](https://github.com/JmeHsieh/hackfoldr-backup-g0v) 不會 index 到。因此這個 pad 專門蒐集沒被其他 hackpads mention 過，**但屬於公開**的 hackfoldrs。


==congressoccupied==
[http://beta.hackfoldr.org/congressoccupied](http://beta.hackfoldr.org/congressoccupied)
[https://ethercalc.org/congressoccupied.csv.json](https://ethercalc.org/congressoccupied.csv.json)

回復了一個測試的 318 反服貿 hackfoldr（有許多連結已失效）2014/7
[http://beta.hackfoldr.org/1v3anz7jfe_test/http%253A%252F%252Ffact.g0v.tw%252Ftisa.html](http://beta.hackfoldr.org/1v3anz7jfe_test/http%253A%252F%252Ffact.g0v.tw%252Ftisa.html)

==nonuke2014==
[http://beta.hackfoldr.org/nonuke2014](http://beta.hackfoldr.org/nonuke2014)
[https://ethercalc.org/nonuke2014.csv.json](https://ethercalc.org/nonuke2014.csv.json)
[https://ethercalc.org/_/nonuke2014/csv.json](https://ethercalc.org/_/nonuke2014/csv.json)

==Kaohsiung-explode-20140801==
[http://beta.hackfoldr.org/Kaohsiung-explode-20140801](http://beta.hackfoldr.org/Kaohsiung-explode-20140801)
ethercalc json api：
[https://ethercalc.org/Kaohsiung-explode-20140801.csv.json](https://ethercalc.org/Kaohsiung-explode-20140801.csv.json)
其中使用了 hackfoldr-2.0 的跳轉機制，但是卻沒有符合跳轉規則，
規則為「在 A1 放 google spreadsheets id 會自動跳轉」
而 _Kaohsiung-explode-20140801_ 的 gsheets id 卻是放在 B2
經詢問了解，這個 special case 是 hardcode 在 nginx 的設定裡了
google spreadsheets id = 1WVWrKC-Tbry3ltgouQPpZH2Cd2HkKeZ8DjLs4PWa1z4
google spreadsheets 位置在
[https://spreadsheets.google.com/feeds/list/1WVWrKC-Tbry3ltgouQPpZH2Cd2HkKeZ8DjLs4PWa1z4/od6/public/values?alt=json](https://spreadsheets.google.com/feeds/list/1WVWrKC-Tbry3ltgouQPpZH2Cd2HkKeZ8DjLs4PWa1z4/od6/public/values?alt=json)
> 更新：已在原始 ethercalc A1 加上 google spreadsheets id
> [name=JmeHsieh]


==code4hk (google spreadsheets 版本) ==
code4hk 有兩個版本
一個是 ethercalc，另一個是後來移去 google spreadsheets 的。
目前看起來 ethercalc 版本已經沒在更新了，主要內容都在 gsheets
ethercalc 版本：
[http://beta.hackfoldr.org/code4hk](http://beta.hackfoldr.org/code4hk)
[https://ethercalc.org/_/code4hk/csv.json](https://ethercalc.org/_/code4hk/csv.json)
google spreadsheets 版本 (使用 ethercalc 跳轉)：
[http://beta.hackfoldr.org/1VJPg85Ub1rcSpH1Hr0PZ7ybBuepxFWi6QEBtO6qMsZs](http://beta.hackfoldr.org/1VJPg85Ub1rcSpH1Hr0PZ7ybBuepxFWi6QEBtO6qMsZs)
[https://ehtercalc.org/_/1VJPg85Ub1rcSpH1Hr0PZ7ybBuepxFWi6QEBtO6qMsZs/csv.json](https://ehtercalc.org/_/1VJPg85Ub1rcSpH1Hr0PZ7ybBuepxFWi6QEBtO6qMsZs/csv.json)
[https://spreadsheets.google.com/feeds/list/1VJPg85Ub1rcSpH1Hr0PZ7ybBuepxFWi6QEBtO6qMsZs/od6/public/values?alt=json](https://spreadsheets.google.com/feeds/list/1VJPg85Ub1rcSpH1Hr0PZ7ybBuepxFWi6QEBtO6qMsZs/od6/public/values?alt=json)

==tpebudget==
[http://beta.hackfoldr.org/tpebudget/](http://beta.hackfoldr.org/tpebudget/)

