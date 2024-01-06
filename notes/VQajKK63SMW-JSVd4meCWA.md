---
tags: DD技術讀書會
---
> DD技術讀書會 
> # Template Method 範本模式 
> [name=Ada][time=Fri, May 31, 2019] [color=#907bf7]

---
<i class="fa fa-file-text"></i> 目錄：
- [Reference](#Reference)
- [導讀](#導讀)
----
## Reference

| 成員 | Reference | 語言 |
| ------ | ----------- | ----------------- |
| Kelly | [InputStream Template](https://g0v.hackmd.io/c/S1-JBQXqE/%2FapPYzpMGT2qXea3rxbE8Qg) | JAVA |
| Ada | [https://ithelp.ithome.com.tw/articles/10204797](https://ithelp.ithome.com.tw/articles/10204797) | javascript |
| 成員3 |  |  |
| 成員4 |  |  |
| 成員5 |  |  |
| 成員6 |  |  |
| 成員7 |  |  |


----
## 導讀

### + 範本方法模式：
:::info
【 範本方法模式 】
定義一個操作中的演算法的骨架，而將一些步驟延遲到子類別中。
範本方法使得子類別可以不改變一個演算法的結構，即可重新定義該演算法的某些特定步驟。
:::

+ **時機**：
  * 當我們要完成一個系列的步驟，或某一細節層次一致的過程，但其個別步驟在更詳細的層次上實現可能不同時。
+ **模式特點**：
  * 透過把不變的行為搬移到超類別，去除子類別中重複的程式碼。
___

### + 範例：考試卷

* Bad:
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_80acf49d9427bba514eb095ef7418962)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_77bd97281b0142de6d1a9c828542eefc)

* Good:
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_fc448017496513289ce7c537e1695141)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_a1eec4e6234a12af2ad9baa22568de97)



