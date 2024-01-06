-[期末考古](/eBD2KfbvRKSUKnrmG9Bxqw) :+1: 

:star:key word(modle圖=資料庫關聯圖)
## 系統分析-DFD
1. **Elements 元件符號**
    - External Entity(實體)
        - 資料的來源或去向，代表正在描述之系統以外的其他           系統或外部個體。
    - Process(動作)
        - 流入資料經此個體或程序處理後，轉換成流出資料，           代表正在描述之系統的全部或其中一部份
    - Data store
        - 代表儲存資料的地方(檔案或資料庫) 
    - Data flow(**一定是名詞**)
        - 代表資料流通的路徑，資料名稱會顯示在邊上。
2. **Hierarchy 層次**
    - 按照描述的繁簡程度分層級
        - 背景圖
            - DFD中最簡單、**最上層**的圖
            - 將整個business process顯示為一個流程
            - 顯示從系統接收訊息或為系統提供訊息的所有External Entities
        - Level 0
            - 顯示構成整個系統的主要流程
            - 顯示**major processes** 與       **dataflows**的關聯性 
            - 顯示External Entities以及其相互作用的               major processes
            - 藉由**data store**添加儲存的數據
        - Level 1
            - 為Level 0上的每個主要流程創建一個Level               1的圖
            - 在Level 0的圖上顯示包含單個流程的內部流               程
            - 顯示資訊如何往返每個流程
            - 如果將parent process分解為3個子流程，則               這3個子流程將完全構成此parent process
3. Alternative Data flows 替代數據流
    - 不同條件下的流程可產生不同的data flows
    - 同時顯示**data flows**並使用**process discription**去解釋為甚麼他們是替代方法
    - Alternative Data flows通常伴隨著**IF語句**
:::info
- process 是所有data flow的交會處
- External Entities不能跟External Entities及data store連線，一定要透過process來聯繫
:::
## economic analysis
1. compare costs and benefits
    - break even analysis(收支平衡點)
        - 收益與損失相等的點，也是總成本與總收入相等的點，能夠反映投資何時會有積極回報
        - 優點- 可以確定系統需花多長時間才能償還開發系統的成本
        - 
    - payback
    - cash flow analysis(現金流量分析)
        -  1
    - Present value analysis(現值分析法)
    - Return on investment

