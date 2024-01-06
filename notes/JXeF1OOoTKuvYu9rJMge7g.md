---
tags: 資演
---

# 資演筆記
[TOC]
## 刪除搜尋二元樹的node
:::info
**要求**
1. 刪除後的二元樹能維持搜尋二元樹的特徵
2. 搬動節點數目的次數最少
:::
- **刪除node為==leaf node==只要把parent指到null就好**
***
- **刪除node為==有一個子樹==**
    - 若刪除的node叫dpt，左邊為null
        - 若dpt在他的parent左邊，則parent.LeftNode=dpt.RightNode
        - 若dpt在他的parent右邊，則parent.RightNode=dpt.RightNode
    - 若刪除的node叫dpt，右邊為null
        - 若dpt在他的parent左邊，則parent.LeftNode=dpt.LeftNode
        - 若dpt在他的parent右邊，則parent.RightNode=dpt.LeftNode
***
- **刪除node為==有兩個子樹==**
    - 將該節點左子樹的==最大==節點取代該節點(左子樹最右邊的節點)
    - 將該節點右子樹的==最小==節點取代該節點(右子樹最左邊的節點)
### 演算法
- 如果dpt有兩個子樹(將左子樹最大的node取代dpt)
    - 若dpt的左子樹其樹根沒有右子樹，則該樹根值最大
        - dpt的LeftNode指到dpt.LeftNode.LeftNode(因為右子樹是null)
    - 若dpt的左子樹其樹根有右子樹，一直往右找，一直找到一個node叫B
    - B.RightNode=null，(若B的parent叫A)然後將B的值取代dpt
    - A.RightNode=B.LeftNode(因為RightNode本來就是null)

## Heap Tree
### Max Heap Tree




