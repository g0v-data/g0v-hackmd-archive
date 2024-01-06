---
title: "OO-2"
tags: hackpad
---

# OO-2

> [點此觀看原始內容](https://g0v.hackpad.tw/ZST3Kw5lOag)

## [Composite](https://g0v.hackpad.com/Composite-GR01FzDqs4n)

角色結構 :
Model : Structural
client component composite Leaf
個別類別 Leaf 和組合類別 Composite 都繼承 Component

#### Define:

    數個物件組成樹狀結構表示"部分與整體"，客戶對單個物件和組合物件使用方式一致。
#### 違反原則：

    依賴倒置(Component為abstract)

## Strategy

角色結構 :
Model : Behavioral
client context物件 Stategy行為
一個物件可以有多個行為
每個行為都有不同的狀態
根據物件不同的狀態切換不同的行為

#### Define:

    定義一組演算法，個別封裝起來，讓他們之間可以互相替換，此模式讓演算法的變動，
    不會影響到使用演算法的程式。

#### _Link:_ [Sourcemaking](https://sourcemaking.com/design_patterns/strategy)


## Iterator

角色結構 :
Model : Behavioral
Aggregate集合體 Client Iterator依序掃描元素的介面

#### Define:

    取得容器內的每個元素，不需將此容器原本實踐暴露出來。

## [Visitor](https://g0v.hackpad.com/Visitor-iOnq0iCkqcI)

角色結構 :
Model : Behavioral
Visitor Client
Visitor Pattern 把 資料結構 和 處理 兩者分開，另外寫一個表示在資料結構內穿梭來去的主體 訪客 的類別，然後把處理交給這個類別來進行。如此一來，如果想追加新的處理動作時，只要再建立一個新的訪客即可。而在資料結構這邊，也只要能接受來敲門的訪客就能完成動作。

#### Define:

    在不改變物件結構得前提下，將內部操作提煉成物件使客戶定義的新操作。

#### _Link:_ [Sourcemaking](https://sourcemaking.com/design_patterns/visitor)


## Memento

角色結構 :
Model : Behavioral
Client 備忘錄 備忘錄管理者

#### Define:

    在不破壞封裝的情況下保存及恢復物件的內部狀態。

## Abstract Factory

角色結構 :
Model : Creational
client abstractFactory concreteFactory abstractProduct concreteProduct

#### Define:

    為創建一組相關或互相依賴的物件提供介面，無需指定具體類別。
#### 違反原則：

    開放封閉，類別會隨著產品而增加方法，也就是說需要修改類別。


## Builder

角色結構 :
Model : Creational
client builder director
把process 跟 step 分開所以他們就可以有彈性的組合在一起??
封裝一個產品的建構過程，並允許可依照步驟建構

#### Define:

    將複雜的物件的建構與表示分離，使同樣建構過程可創建不同表示。
Untitled

This pad text is synchronized as you type, so that everyone viewing this page sees the same text.  This allows you to collaborate seamlessly on documents!


