## 2022.05.09課堂觀念題


### 2022.05.02觀念題作業題解
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d0501e57c473fa540401d137d230af74.png =60%x)

[原題目作業連結](https://g0v.hackmd.io/NaDDO0MWTd2fJJJKggj1VA?view)

---

### 2016.10觀念題12

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c07e9df7be37d97ea48da554ba3c6fea.png =60%x)
上述程式片段執行過程中
的輸出為何？
A) 5 10 15 20
B) 5 11 17 23
C) 6 12 18 24
D) 6 11 17 22
```
1 i=0; i<20; i=i+1 #從0開始，小於20，每次執行完+1
2 i=i+a            #i=0+5 → print 5
3 i=i+1, i=i+a     #i=5+1, i=6+5 → print 11
```
---
### 2016.03月觀念題6
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_435d1a24b30117bb5a7dff9b0c12d787.png =50%x)
題目：List 是一個陣列，裡面的元素是 element，它的定義如右。List 中的每一個 element 利用 next 這個整數變數來記錄下一個 element 在陣列中的位置，如果沒有下一個 element， next 就會記錄-1。所有的 element 串成了一 個串列 (linked list)。
例如在 list 中有三筆 資料
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_60f0fbb3027685554b9409308f464767.png =60%x)
它所代表的串列如下圖：
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_12c05e803ee94e7943a172ac3a776d9d.png =60%x)
RemoveNextElement 是一個程序，
用來移除 串列中 current 所指向的下一個元素，
但是必須 保持原始串列的順序。
例如，若 current 為 3 (對應到 list[3])， 
呼叫完 RemoveNextElement 後，串列應為：
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9e9f3d042b823d868b7d1e2e5649bb69.png =60%x)
請問在空格中應該填入的程式碼為何?
(A) list[current].next = current ; 
(B) list[current].next = list[list[current].next].next ; 
(C) current = list[list[current].next].next ;
(D) list[list[current].next].next = list[current].next ;

#### 詳解
假如current = 3
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_88a976c5687b8d2e136a49e0488eea8c.png =70%x)
要怎麼變成這樣?
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a5731fa77785755ad67a01693b2f4b45.png =70%x)

    (A)list[current].next = current ; 
    意思是：
    (A)list[3].next = 3;
    
    --------------------------------------------------------
    (B) list[current].next = list[list[current].next].next ; 
    意思是：
    (B)list[3].next = list[list[3].next].next;
                    = list[1].next;
                    = 2
                    
    --------------------------------------------------------
    (C) current = list[list[current].next].next ;
    意思是：
    (C) 3 = list[list[3].next].next;
            = list[1].next;
            
    --------------------------------------------------------
    (D) list[list[current].next].next = list[current].next ;
    意思是：
    (D) list[list[3].next].next = list[3].next;
        list[1].next = list[1]

---
### 2016.03月觀念題7
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_66ed0939c6b2fd1ff89bd5778058d636.png)

請問以 a(13,15)呼叫右側 a()函式，
函式執 行完後其回傳值為何？ 
(A) 90 
(B) 103 
(C) 93 
(D) 60
#### 詳解
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c13c39b6293d2d385d8c0bf0566ee9da.png)
---


