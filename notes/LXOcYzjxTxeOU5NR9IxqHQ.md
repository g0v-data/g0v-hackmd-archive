# OpenBMC 輕量化零信任架構系統規格書

**專案名稱：** 基於樹莓派之 OpenBMC 邊緣設備零信任安全防禦系統實作  
**文件版本：** v1.0  
**架構核心：** 永不信任，始終驗證（Never Trust, Always Verify）

---

## 1. 專案概述 (Project Overview)

本專案旨在現有的 OpenBMC（基於樹莓派平台）架構下，捨棄傳統「邊界防禦」的思維，導入微隔離、持續驗證與動態審查的**零信任架構（Zero Trust Architecture, ZTA）**。透過純軟體配置與系統整合，在不更動 OpenBMC 底層核心原始碼的前提下，達成身分識別、網路限縮與即時資安監控的三維防禦。

---

## 2. 系統架構與安全拓樸 (System Architecture)

本系統主要由兩個核心實體組成：

1. **OpenBMC 端（樹莓派）：** 扮演受保護的基板管理控制器（BMC），負責收集模擬環境數據並執行管理指令。
2. **資安監控與管理端（x86 主機）：** 扮演管理員工作站與 SIEM（安全資訊和事件管理）中心。

> 💡 **安全核心原則：** 縱使管理員工作站與 OpenBMC 處於同一區域網路（LAN），在未通過憑證校驗與防火牆白名單審查前，任何網路封包皆視為潛在威脅。

---

## 3. 技術規格與實作細節 (Technical Specifications)

### 3.1 認證層：強固型雙向 TLS (mTLS) 驗證

傳統密碼機制易受暴力破解與側錄攻擊，本系統將關閉傳統密碼認證，全面導入 mTLS。

* **實作組件：** OpenBMC 內建 Web 伺服器（`bmcweb` / `Nginx`）。
* **憑證管理：**
  * 由專案建立專屬的內部憑證授權中心（Private CA）。
  * OpenBMC 持有伺服器憑證（Server Cert），管理端持有用戶端憑證（Client Cert）。
* **設定規格：**
  * 修改 Web 伺服器組態，啟用客戶端憑證強制驗證（如 Nginx 設定 `ssl_verify_client on;`）。
  * 傳輸加密協議限定 **TLS v1.3**，停用所有已知弱加密演算法。
* **預期行為：** 未導入合法憑證的設備存取 Redfish API 或 WebUI 時，連線將在 TCP/TLS 握手階段被直接中斷，無法接觸到登入介面。

### 3.2 網路層：微隔離防火牆與動態白名單 (Micro-Segmentation)

限制攻擊者在管理網路內的橫向移動（Lateral Movement）與惡意掃描。

* **實作組件：** Linux 核心內建防火牆子系統（`iptables` / `nftables`）。
* **規則策略（預設拒絕 - Default Drop）：**
  * **INPUT 鏈：** 預設為 `DROP`。
  * **白名單規則：** 僅允許來自「特定管理端 IP」且帶有特定連接埠（如 TCP 443）的連線。
  * **ICMP 限制：** 停用 Ping 回應，或僅限特定主機，防止網段內的自動化掃描工具（如 Nmap）偵測到 BMC 的存在。
* **編譯組態：** 確保 Yocto 的 `local.conf` 中包含 `IMAGE_INSTALL:append = " iptables nftables"`。

### 3.3 監控層：持續完整性審查與日誌外發 (SIEM 整合)

落實零信任「持續監控」的精神，確保所有操作皆留下不可篡改的稽核軌跡。

* **實作組件：** OpenBMC 內建 `rsyslog` 服務 + 遠端 ELK Stack 或 Grafana Loki 伺服器。
* **日誌轉發配置：**
  * 設定 `/etc/rsyslog.conf`，將所有系統日誌（`*.*`）以 UDP/TCP 協定即時推送到遠端 SIEM 伺服器。
  * 重點監控日誌：`/var/log/auth.log`（驗證嘗試）、`/var/log/nginx/access.log`（API 存取軌跡）。
* **SIEM 儀表板實作：**
  * 收集日誌並進行結構化解析。
  * 建立告警規則：當出現「連續 TLS 握手失敗」或「非白名單 IP 嘗試連線被阻擋」時，儀表板立即發出高風險視覺警示。

---

## 4. 系統建置與布署流程 (Deployment Workflow)

1. **Yocto 環境編譯**
   * 在 x86 主機配置 Ubuntu 環境。
   * 加入 `meta-raspberrypi` 與防火牆相關套件。
   * 編譯出 `.wic` 映像檔並燒錄至樹莓派 SD 卡。
2. **憑證初始化與佈署**
   * 生成 Private CA、Server Certificate 與 Client Certificate。
   * 將 Server Certificate 寫入樹莓派安全路徑，並將 Client Certificate 導入管理端瀏覽器。
3. **安全組態配置**
   * 修改 Nginx/bmcweb 啟用 mTLS 與強固型加密套件。
   * 寫入 `iptables` / `nftables` 規則，並設定開機自動載入腳本。
4. **監控鏈路建立**
   * 配置樹莓派的 `rsyslog` 導向遠端 x86 的 ELK/Loki 監控中心。

---

## 5. 測試與驗證計畫 (Testing & Validation)

| 測試項目 | 測試手法 (Methodology) | 預期結果 (Expected Result) | 零信任對應指標 |
| :--- | :--- | :--- | :--- |
| **未授權存取測試** | 使用未安裝憑證的電腦嘗試連線 WebUI / Redfish API | 瀏覽器顯示 TLS 連線錯誤，伺服器拒絕回應 | 身分持續驗證 |
| **網路隱蔽性測試** | 從非白名單 IP 使用 Nmap 對樹莓派進行全連接埠掃描 | 顯示所有連接埠為 `Filtered`，且無法 Ping 通 | 最小權限 / 微隔離 |
| **攻擊行為告警** | 模擬惡意設備強行觸發連線，並檢查遠端 SIEM 儀表板 | SIEM 於 3 秒內收到 rsyslog 阻擋紀錄並觸發紅字告警 | 持續監控與回應 |

---

## 6. 專題創新點與資安價值

1. **實務導向的防禦演練：** 本專題跳脫了傳統純攻擊（Red Team）的範圍，專注於合規、日誌鑑識與架構強化的藍隊（Blue Team）實務。
2. **邊緣運算安全範例：** 證實了即使在資源受限的嵌入式系統（樹莓派）上，也能透過合理的架構設計，不耗費額外硬體成本達成 NIST SP 800-207 標準的零信任安全度。