# Day 2 - 後端規劃

## 動手之前，想一想
既然應用的部分選擇記帳作為主要功能，勢必要對此功能先做一番規畫

以前曾遇過一個協作的專案，就是對於功能沒有足夠的審視了解就直接開工，團隊間片面的處理自己的需求，導致中期在功能疊加之後才發覺最初的設計是完完全全的錯誤，由此可見，匆匆下手只會徒增困擾

所以今天的主題就是針對本次主題的初步規劃

### 功能面發想
(按實作順序)
1. 可以做帳務的 CRUD
2. 可以做帳本間的轉移
3. 可以擁有自己的帳本
4. 可以看酷酷的圖表
5. 可以收一點錢錢

### 資料表設計

從功能面發想可以接著理解並延伸我們所需要的資料表

#### 帳務的 CRUD
最基本的要可以記帳，所以這裡會需要一張表可以記基本的金流進出

1. 計數 amount
2. 名稱 name
3. 種類 flow_type，因為預計有收支兩個部分

Accounting
| 名稱 | 型態 |
| --- | --- | 
| flow_type | integer | 
| amount | integer |
| name | string |
----
#### 帳本間的轉移
要能做轉移，所以會有 Accounting 會屬於 Ledger 概念


Ledger
| 名稱 | 型態 |
| --- | --- | 
| name | string |


----
#### 擁有自己的帳本
「自己」的意識出現，意味著有 User
且有 Ledger 會屬於 User 概念

User
| 名稱 | 型態 |
| --- | --- | 
| name | string |
| email| string |
| password | string |

#### 酷酷的圖表
這會是 Accounting 的統計，評估目前不會是有需要規畫表的概念

#### 可以收一點錢錢
預估這會是有需要「紀錄」存在表中，但因為這部分不會是應用的本體，可以稍等到金流串接的部分再來規劃也不會造成太大的影響

## 小結
今天是完全的紙上談兵，還沒開始動手，但也正是因為還沒動手，才有機會先「預防」錯誤產生
當然也有一部分的聲音說「不要過度設計」，這兩者我都是百分百的同意
能多少「正確地」預防乃開發者的功力，在還沒到達未來視的境界之前，適當的著眼於現在相較之下會是更好的選擇
所以今天只粗略的規劃，金流的部分也擱置，都待之後實作時遇到問題再來修正
