---
title: "工時紀錄上區塊鏈"
tags: hackpad
---

# 工時紀錄上區塊鏈

> [點此觀看原始內容](https://g0v.hackpad.tw/hqQGdzE8KJn)


[簡報在此](https://docs.google.com/presentation/d/1kXLSx6eW1SJxFoIXZrGQ730NUPWZfoiXqICvjVO3TjE/edit?usp=sharing)
g0v slack channel: [#labor](https://g0v.hackpad.tw/ep/search/?q=%23labor&via=hqQGdzE8KJn)

## 問題

1.  有沒有更透明、正確、不可篡改的方式記錄工時？
2.  有沒有更有效率的方式協助勞檢員知道哪些企業要優先查驗？


## 今天想做的事情

- 研究一下現有的打卡系統
- 對於勞工議題了解的人可以分享一下勞檢的問題
- 討論區塊鏈是否有機會解決這個問題
- 討論不用區塊鏈是否有機會解決這個問題
- 如果要用區塊鏈解決這個問題，系統的參與者有哪些，例如：
    - 這個 app 是給勞工自行記錄工時用，提供政府資訊發動勞檢，資方沒有參與
    - 這是個 smart contract，透過政府（中央或地方）的協助，讓打卡系統廠商將打卡系統接上區塊鏈（這是實驗專案，所以會有一連串的探索可能現在還不見得有辦法實行）
- 有沒有什麼誘因可以讓勞方與資方都願意提供正確的打卡資訊

可以用類似 ifttt 的方式，建立帳號的時候記錄下公司名稱跟統一編號以及地址，利用 mobile phone 的位置紀錄，自動 punch in / punch out，然後可以簡易記錄自己工作的時間。可以把裏工時跟表工時對照起來

## 討論

經過討論，目前看起來區塊鏈使用上有些問題還不能解決：

1.  區塊鏈中的記錄可以相信，但是如何記錄進區塊鏈卻是一個無法解決的問題，如拿著別人的手機打卡
2.  目前加密貨幣 \+ Dapp 的應用還不是很普及，所以目前做這些可能還太前瞻，可能使用的人沒辦法太多。不過還是可以作為實驗的功能。
3.  每次打卡時都需要消耗一些 gas，每次打卡都需要耗費金錢，很難說服使用者把錢存進去電子錢包，每次打卡時要消耗錢。

上面是早上的討論，下午的時候又跟 [Democracy World](http://democracy.earth/) 的人討論了一下，他們提供了一些可以使用的區塊鏈技術可以應用在這個專案。

- [https://tierion.com/](https://tierion.com/)
- [https://chainpoint.org/](https://chainpoint.org/)


## 結論


### 早上的討論結果


可以先不使用區塊鏈的方式進行，可以先解決「問題二」，讓勞檢的效率可以更好。作法如下：建立一個 mobile app，並且可以登錄統一編號與工作的地址，另外也可以先讓使用者選擇是否是固定地點工作，以及是不是輪班制，用來排除不固定工作地點的資訊如業務或送貨員。

登錄地址後，可以自動化的紀錄靠近工作地點的時間，以及遠離工作地點的時間。

雖然這個紀錄可能不是很準，但是如果勞動局可以存取這個資料，就可以知道要勞檢的時候，哪些企業平均來說工時比較長，或是哪個企業種類比較有工時過長的狀況，進而可以讓勞檢的效率更高。

> 請問你坐在哪個方位?XD 我找不到坑位，我目前工作上有接觸到紀錄工時的工具，想和您討論彼此的狀況
> [name=翁馬克]

> 我們在講台前的第一桌，不過現在大家去聽唐鳳直撥了 XDD
> [name=Yuren J]

> [http://yuhsuanlinmd.blogspot.tw/p/blog-page.html](http://yuhsuanlinmd.blogspot.tw/p/blog-page.html)  know addiction
> [name=翁馬克]

> 醫師的過勞問題其實很值得做，但醫師還沒受勞基法保護...
> [name=I-Chiao H]


### 下午的討論結果


跟 Democracy World 的人討論過後，因為他們在做分散式民主的專案，他們覺得可以用一些技術克服上面的問題，如他們提到可以用 web app 並且在 web backend 連結區塊鏈，將記錄放在區塊鏈上。配合上 chainpoint 可以將多筆紀錄合併到一個 transaction 上面，費用上可以更加節省，而且把區塊鏈連接的部分放到 backend 可以讓 web app 不需要使用 Dapp 的形式開發 app，可以解決早上問題的 2, 3。至於實作方法還是可以用早上的討論結果的做法，只是在 backend 接到區塊鏈即可。

## 一些草圖與想法

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_2981d58ca644e845c5d5a55f305198ad)

勞工第一次進來 app 要輸入的資訊：
1.  是否固定工作地點
2.  工作的地址
3.  輪班制或固定時間上下班
4.  正常的上下班時間
5.  統一編號

## 更進一步的發想


如何跟[勞動權益網站](https://yurenju.github.io/laborrights/#/)結合？先盤點一下勞動權益網站已經有甚麼了，開了一個[新的 pad 記錄這些發想](https://g0v.hackpad.tw/-app-HmVaQeCbwzD)。



