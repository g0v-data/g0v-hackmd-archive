# C#的一些知識 & 常用筆記


---


# 強型別 v.s. 弱型別

* 強型別 (Stronly Type)

定義：相對弱型別而言，較不允許隱性型別轉換，程式在檢查上較為**嚴格**。因此，在開發過程中也會相對較難撰寫，但是同時也能夠**降低**遇到 Bug 的風險性。
例如：Java、C#、Python

* 弱型別 (Weakly Type)

定義：相對強型別而言，較允許隱性型別轉換，程式在檢查上較為**寬鬆**。因此，在開發過程中也會相對較容易撰寫，但是同時也會**增加**遇到 Bug 的風險性。
例如：C、C++、PHP、JavaScript

【Q】靜態語言一定是強型別？動態語言一定是弱型別？
【A】不一定。靜態語言和動態語言最大的差別在於 Data Type 的處理方式。因此，與強型別或弱型別並無一定關係。

| 語言型態 | 強弱型別 |       程式語言        |
|:--------:|:--------:|:---------------------:|
|   靜態   |    強    |       Java, C#        |
|   靜態   |    弱    |         C/C++         |
|   靜態   |    強    |     Python, Ruby      |
|   靜態   |    弱    | Perl, PHP, JavaScript |

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e7e6a84d26a0f7d97993884dbc95dd8d.png)


---

# 泛型容器 (Dictionary & List)

* 泛型(Generics)：泛型允許我們根據自身需求在定義類別、方法或資料結構時暫時不指定具體的資料類型，而是在使用時根據需求指定類型。也就是可以設定可變型別的參數來傳遞，讓我們可以用更有彈性的方式來設計 Class、Method，操作資料等。

* Dicitonary<>
* List<>


---

# Legacy Objects (Array, ArrayList, DataTable)




---

# Oracle 的 Lock Type 運作模式




---

# 變數(variable)與屬性(property)本質上的差異




---
