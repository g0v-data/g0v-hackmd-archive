---
tags: DD技術讀書會
---
> DD技術讀書會 
> # Composite Pattern 組合模式 
> [name=Ada][time=Sat, Oct 5, 2019] [color=#907bf7]

---
<i class="fa fa-file-text"></i> 目錄：
- [Reference](#Reference)
- [導讀](#導讀)
----
## Reference

| 成員 | Reference | 語言 |
| ------ | ----------- | ----------------- |
| Kelly |   |   |
| Ada | |   |
| 成員3 |  |  |
| 成員4 |  |  |
| 成員5 |  |  |
| 成員6 |  |  |
| 成員7 |  |  |


----
## 導讀

### + 組合模式：
:::info
【 組合模式 】
將物件組織成樹狀結構、『部分』與『整體』的層次結構。
組合模式使得用戶對『單個物件』和『組合物件』的使用具有一致性。
:::

+ **時機**：
  * 希望用戶可以忽略『單個物件』和『組合物件』的不同，使用一致的方式對待所有物件時。
+ **結構圖**：
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d56e21734a40c6ae2fc67a34b9d83fa0)




### + 範例：
+ **公司與部門的結構圖**：
  * ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_bdf79199b3f058bb0b06f6c66d885c58)
  * ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_20ab6b8c75d4e17fc39aff4f8b6df151)


### + 『透明方式』與『安全方式』

+ **透明方式：在component（類別階層頂端）制定管理子節點介面**
  * 優點：Leaf（葉節點）和composite（枝節點）對外沒有什麼區別，他們具備完全一致的行為介面。
  * 缺點：犧牲安全性，因為無法避免別人寫出『增加、刪除 Leaf 的子節點』的惡搞程式。
+ **安全方式：在composite（枝節點）類別制定管理子節點介面**
  * 優點：安全性高。（因為像C++這種靜態語言就能在編譯期揪出『增加、刪除 Leaf 的子節點』的錯誤程式）
  * 缺點：Leaf 和 composite 有著不同的介面，用戶端的調用就需要做相對應的判斷，帶來不便。


