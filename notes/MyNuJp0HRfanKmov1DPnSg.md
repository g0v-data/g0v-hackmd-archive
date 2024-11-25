在網路交換機 (Switch) 的設定中，Tagged Ports 和 Untagged Ports 是 VLAN (Virtual Local Area Network) 配置的重要概念，以下是它們的詳細說明及用途：
1. Tagged Ports (標記的埠)
    說明：

    *     Tagged Ports 是用來傳輸多個 VLAN 的流量。
    *     資料封包會被加上 VLAN 標記 (Tag)，標記中包含 VLAN ID，這樣接收裝置就可以知道該封包屬於哪個 VLAN。
    *     一般用於連接其他交換機 (Switch-to-Switch) 或路由器 (Router) 的 Trunk 埠上。
    用途：

    *     跨交換機傳輸多個 VLAN 的流量：
    *     如果一個網路架構中有多個 VLAN，且需要跨越多台交換機，則需要使用 Tagged Ports 傳輸這些 VLAN 的封包。
    *     連接支援 VLAN 的裝置：
    *     如伺服器或無線控制器等裝置，需要處理多個 VLAN 的流量時，也會使用 Tagged Ports。
    *     提高網路效率：
    *     Tagged 封包可在同一埠上攜帶多個 VLAN 的流量，減少埠數需求。
    
2. Untagged Ports (未標記的埠)
    說明：

    *     Untagged Ports 是用來傳輸單一 VLAN 的流量。
    *     傳輸的封包沒有 VLAN 標記，或在到達埠後，交換機會自動移除標記，適合不支援 VLAN 的終端裝置使用。
    *     每個 Untagged Port 只能屬於一個 VLAN。
    用途：

    1. 連接終端裝置：
    如電腦、印表機、IP 電話等，不支援 VLAN 協議的裝置，通常會配置到 Untagged Port。
    2. 簡化裝置配置：
    對於不需要多 VLAN 的設備，Untagged Port 提供了簡單的網路分段方式。
    3. 確保 VLAN 隔離：
    每個 Untagged Port 所屬的 VLAN 是獨立的，確保不同 VLAN 的終端流量互不干擾。
Tagged 與 Untagged 的關係
*     一個埠可以同時具有 Tagged VLAN 和 Untagged VLAN：
    *         Untagged VLAN 稱為該埠的 PVID (Port VLAN ID)，即預設 VLAN，處理沒有標記的封包。
    *         Tagged VLAN 用於傳輸多個 VLAN 標記的封包。
    當一個封包進入或離開一個 Tagged Port 時：
    封包內會包含 VLAN 標記。
    當一個封包進入或離開一個 Untagged Port 時：
    封包不會包含 VLAN 標記。