# **資料結構**
## **系統開發生命週期**
**1. 需求(Requirement)**
確認系統的要求，包含精確的input和output。
**2. 分析(Analysis)**
將問題切割成許多小部分來解決並進行不同方法間的互相比較，有兩種分析方法:
* 由下而上(Bottom-up)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9a1328fea78c4a9549c7428e6b419ab3.png)
較古老、無結構化
強調細微處程式編寫
* 由上而下(Top-down)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_42f7ffe2dfa191f3be423566dc0140bd.png)
以程式最後的目標為開端
將程式分割成許多可管理的片段
<font color="#f00">開發較複雜的軟體系統時，Top-down為較好的方式</font>

**3. 設計(Design)**
觀察需要甚麼: 資料物件(Data Object)、運算(Operation)
第一部分:創造抽象資料物件
第二部分:演算法的精確需求、演算法的設計策略

**4. 細化與編碼(Refinement and Coding)**
必須先為資料物件裡的各個運算設計獨立的演算法，然後選擇資料物件的表示方式，表示方式的選擇通常影響到演算法的效率<font color="#f00">(設計演算法和決定資料物件表示方式的順序很重要)</font>

**5. 驗證(Vertification)**
驗證程式的正確性