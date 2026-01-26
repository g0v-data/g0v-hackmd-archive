# omniverse streaming
[toc]

| 比較項目 | Streaming Client | Nucleus Server |
| -------- | -------- | -------- |
| 本質    | 遠端畫面串流    | 共享資料／場景    |
| 是否串流畫面 | ✅ |❌ |
| 是否多人同改    |❌|✅   |
| 協作方式 |共用一個畫面 |各自一個 Isaac Sim|
| 使用 GPU    |Server 的 GPU     |各自本地 GPU   |
| 適合用途    |Demo、展示、遠端操作     |論文協作、共同建模   |


## [Isaac Sim WebRTC Streaming Client](https://docs.isaacsim.omniverse.nvidia.com/5.1.0/installation/download.html#isaac-sim-latest-release)
1.  使用者啟動 Streaming Client![](https://g0v.hackmd.io/_uploads/Bk55ocE8Zl.png)

2.  Streaming Client 連線至 Isaac Sim Server(實際執行 Isaac Sim 的那台電腦)
3.  Isaac Sim Server 檢查：Streaming 功能是否已啟用`window-->extension-->輸入livestream`![](https://g0v.hackmd.io/_uploads/S16pvq4IZx.png)

4.  Server 端進行模擬與渲染
5.  畫面串流回 Client
6.  使用者操作回傳
7.  Server 更新模擬
![](https://g0v.hackmd.io/_uploads/SJK3QqEI-l.png)

## Nucleus
1. 使用者啟動各自的 Isaac Sim
    - 使用者 A（Windows）啟動 Isaac Sim A
    - 使用者 B（Windows）啟動 Isaac Sim B
    - 每位使用者都在自己的電腦、本地 GPU上執行模擬
2. Isaac Sim 連線至 Nucleus Server
    - 分別連線至同一台 Nucleus Server
    - 並開啟「同一個 USD Scene」
3. 使用者 A 在 Isaac Sim A 修改場景(移動物件、修改位置 / 狀態)
    - 變更內容被轉換為 USD 資料更新
4. USD 變更同步
    - Isaac Sim A 將更新後的 USD 資料送至 Nucleus Server
    - Nucleus Server 即時將 USD 變更同步給 Isaac Sim B
5. 使用者 B 即時看到變更
    - Isaac Sim B 接收到 USD 更新
    - 場景立即更新
    - 使用者 B 即時看到使用者 A 的修改
6. 以此類推使用者 B更改 Isaac Sim B 內容也會即時更新同步到 Isaac Sim A

![](https://g0v.hackmd.io/_uploads/Byy-V9VLWl.png)

