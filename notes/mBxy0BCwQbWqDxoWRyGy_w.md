# 建立普惠測試環境 新UIUX 
## GCP
* 到**網路端點群組** 新增網路端點群組與網路端點*test-webserver-newui*
* 到load balancing(Network services)編輯puhui-client-lb
* 確認 NEG 建立完成
   - 確認你建立的 NEG 是哪種類型（通常是 GCE_VM_IP_PORT、SERVERLESS、INTERNET_IP_PORT 等）。
   - 如果是用於 HTTP(S) 負載平衡器，通常會用「**區域性網路端點群組（Zonal NEG）**」。
* 建立或編輯「後端服務（Backend Service）」
   - 前往 GCP Console → Network services → Load balancing。
   - 找到你要設定的負載平衡器，點進去後選「編輯」。
   - 在「**後端設定（Backend Configuration）」** 部分，新增或修改「後端服務（Backend Service）」。
   - 在後端服務裡面，選擇「新增後端」→ 選擇「網路端點群組（NEG）」。
   - 從清單中選擇剛剛建立的 NEG。
* 調整健康檢查（Health Check）**
   - 後端服務需要設定健康檢查，確認 NEG 中的端點是否健康。
   - 如果沒有健康檢查，可能會導致流量無法導入 NEG。
* 在**轉送規則**新增:
    * 主機 - puhui.pasha.tw
    * 路徑 - /newUIUX/*
    * 後端 - test-webserver-newui
* 到防火牆開port 
* 如果要過load balancer 要到health check那邊也開port



在 GCP（Google Cloud Platform）中，當你 **新增完「網路端點群組（NEG, Network Endpoint Group）」** 之後，要讓它參與到 **負載平衡器（Load Balancer）** 的轉送規則中，大致上需要完成以下步驟：

---

### ✅ 基本流程如下：







4. **儲存後端服務修改**

5. **設定「轉送規則（Forwarding Rule）」**
   - 轉送規則通常是在負載平衡器的最前面（例如 HTTP(S) LB 的 URL map）決定流量走向的地方。
   - 如果已經有設好的轉送規則，通常不需要再修改，除非要調整 URL 對應到不同的後端服務。
   - 確認 URL map 是否正確指向包含 NEG 的後端服務。

6. **發布 & 測試**
   - 儲存所有設定。
   - 使用外部 IP 或 domain 來測試是否成功將流量導入到 NEG 中的實例或端點。

---

### 🚀 總結重點：

✅ **NEG → 加入到後端服務 → 後端服務綁定健康檢查 → 後端服務參與轉送規則**

---

如果你方便的話也可以告訴我：

- 你使用的是哪種類型的負載平衡器？（HTTP(S)、TCP/UDP、SSL Proxy 等）
- 你的 NEG 是哪種類型？

這樣我可以幫你提供更精確的操作指引！