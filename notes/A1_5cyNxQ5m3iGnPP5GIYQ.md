---
title: "vtaiwan 小松 2017.02.15"
tags: vTaiwan小松, hackpad
---

> [點此觀看原始內容](https://g0v.hackpad.tw/QrnoEOTvZnM)




## 電子報訂閱


smith 將電子報訂閱功能做得差不多了，我幫忙筆記一下：


### 設定方式

目前電子報訂閱是使用 discourse 的 watch 功能，設定如下：
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_a89f51e02f6cccbfa26cc074d404337b)

使用 "default categories watching first post" 來迫使新的 talk.vtaiwan.tw 使用者收到 "電子報發佈" 分類的主題，並且只有 first post，也就是後面的回文不會收到通知。


### 訂閱方式

點了 vue.vtaiwan.tw 頁面下方的「訂閱電子報」連結，會引導寄出一封 email 到 vtaiwan.tw

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_7165bce9a2f50a539f5c4c534f1cca10)

可能因為是 "replies+subscribe" 所以會發佈一篇文章到 「電子報訂閱區」[https://talk.vtaiwan.tw/c/newsletter/subscribe](https://talk.vtaiwan.tw/c/newsletter/subscribe)，**似乎應該改成不發佈文章，只默默訂閱（默默自動註冊帳號）就好**。

##

## 電子報待解問題



###  測試發報未成功


實際發了一篇文章到「[電子報發佈區](https://talk.vtaiwan.tw/c/newsletter/newslettercontant )」，等了 30 分鐘，發現**沒有收到電子報**。

不確定是否系統有 "watch topic 的人多久會收到通知" 的設定。
需要：
1.  檢查設定
2.  請有 vtaiwan mailgun 權限的人確認是否有發信紀錄

> Updated: smith 說發現使用 email 訂閱方式註冊 discourse 帳號的人，不會被 "default categories watching first post" 設定影響，需要另找解決方法。
> [name=isacl]

> 有必要可考慮修改 discourse 收到信後的處理的那段程式
> [name=isacl]


###  舊用戶是否要自動訂閱

 已存在的使用者因為不受新設定的 "default categories watching first post" 影響，因此不會訂閱到電子報，現有兩個選擇。

 1.  我們幫這些人設定成 watch 該 category
 2\. 不幫他們訂閱，寄信給他們告訴他們要怎麼訂閱。



### 先訂閱電子報，然後才到 talk.vTaiwan 註冊帳號會怎樣


 理論上它的 email 會已經存在，需要 reset 密碼。但我還未測試過。






