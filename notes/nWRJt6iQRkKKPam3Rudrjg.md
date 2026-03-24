---
tags: cofacts,
---

# 20260324 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：bil, lahna, mrorz, nonumpa
- 線上出席：
- https://meet.google.com/mrz-dgrd-pri
:::

## 上次會議待辦

### Cofacts.ai 開發

https://github.com/orgs/cofacts/projects/12

- [ ] React-markdown --> 回應編輯器
- [ ] 資料關聯整理：準備 source list 然後掃 messages
- [ ] Session list
- [ ] Deploy to production w/ Claudelare
- [ ] 整理 header (logo、menu、搜尋⋯⋯ etc)
- [ ] landing page focus issue
- [ ] input 在組字時 enter 會直接送出
- [ ] tool call 細節調整
- [ ] Langfuse feedback buttons
- [ ] ADK 升級到可以看到 openapi.json
- [ ] 直接用 ADK type 來 render events 而非轉成 messages
- [ ] 在 tool call 中間關掉瀏覽器視窗再打開同一個 session page，要可以繼續串流結果

### 主機遷移至 GCE
- [x] @mrorz 執行 https://docs.google.com/document/d/1sZ4jOsrZPvbJv4QjlMxgbqFsh_pTZNBRs-NbG-HU0rM/edit?pli=1&tab=t.t599bt7kwc4o#heading=h.351xoil28n2
- [x] @mrorz 確認 docker-compose 與 rumors-deploy script 是否可以共用
- [ ] @mrorz 可以的話，開一台 production 設定好 ES6 snapshot，準備 migrate
	- 準備好後先停機，省 cost


---

> COS 下是可以在 home 底下做出大家都可讀寫的 rumors-deploy
> 但 home 底下的 script 不能執行
> 我連 docker-compose 都沒辦法好好跑，心好累
> 想回到 ubuntu XDDDD
> [name=mrorz]

新 Design document：https://docs.google.com/document/d/1sZ4jOsrZPvbJv4QjlMxgbqFsh_pTZNBRs-NbG-HU0rM/edit?pli=1&tab=t.t599bt7kwc4o#heading=h.351xoil28n2

```mermaid
flowchart TB
    subgraph Internet ["網際網路 (Internet)"]
        User(("👥 一般使用者<br>(瀏覽器/Cofacts.ai)"))
        LINE_Server(("📱 LINE 平台<br>(Webhooks)"))
        Admin(("🧑‍💻 系統管理員<br>(DevOps/RD)"))
    end

    subgraph CF ["Cloudflare 邊緣網路"]
        CF_Edge["☁️ Cloudflare<br>(WAF / DNS / DDoS 防禦)"]
    end

    subgraph GCP ["Google Cloud Platform (GCP)"]
        IAP["🛡️ Identity-Aware Proxy<br>(IAP)"]
        Ops_Dashboard["📊 Cloud Monitoring / Logging"]

        subgraph VPC ["VPC 網路 (Deny All Ingress / 暫時性外部 IP)"]
            subgraph GCE ["🖥️ GCE: e2-highmem-4 (Ubuntu 24.04 LTS)"]
                
                subgraph OS ["Linux OS 層"]
                    PAM["🔑 pam_group.so<br>(登入自動指派 dockerops 群組)"]
                    Ops_Agent["📈 Google Cloud Ops Agent<br>(收集 Metrics & Logs)"]
                end

                subgraph Docker ["🐳 Docker Compose V2 環境"]
                    Cloudflared["🚇 cloudflared<br>(Zero Trust Tunnel)"]
                    Site["🌐 Web (site-tw)<br>(SSR 前端站台)"]
                    API["⚙️ rumors-api<br>(核心 API Server)"]
                    Bot["🤖 line-bot-zh<br>(LINE 機器人)"]
                    ES["🗄️ Elasticsearch 9<br>(TF-IDF + Gemini 向量檢索)"]
                    Resolver["🔗 url-resolver<br>(記憶體限制 512m)"]
                    Cron["⏱️ cron-runner<br>(排程腳本執行)"]
                end
                
                Disk[("💾 Persistent Disk<br>(pd-balanced)<br>- /var/lib/docker<br>- /srv/rumors-deploy")]
            end
        end
    end

    %% End User Flow
    User -- "HTTPS (cofacts.tw 等)" --> CF_Edge
    LINE_Server -- "HTTPS (api.cofacts.tw)" --> CF_Edge
    
    %% Zero Trust Tunnel Flow (Outbound from GCE)
    Cloudflared -. "1. 主動建立出站連線<br>(Outbound)" .-> CF_Edge
    CF_Edge == "2. 安全路由流量至內網" ==> Cloudflared
    
    %% Internal Proxy Routing
    Cloudflared -- "HTTP 轉發" --> Site
    Cloudflared -- "HTTP 轉發" --> API
    Cloudflared -- "HTTP 轉發" --> Bot
    
    %% Internal Microservices
    Site -- "GraphQL 請求" --> API
    Bot -- "GraphQL 請求" --> API
    Cron -- "定期觸發任務" --> API
    Cron -. "自動更新 Image 並重啟" .-> Docker
    API -- "CRUD & HNSW 近似最近鄰比對" --> ES
    API -- "爬取與解析外部網頁" --> Resolver
    
    %% Admin Flow
    Admin -- "gcloud compute ssh" --> IAP
    IAP -- "經由安全通道 (Port 22)" --> PAM
    PAM -- "取得免 sudo 操作權限" --> Docker
    PAM -. "讀寫共用部署設定檔 (setgid)" .-> Disk
    Docker -. "掛載 Volume / 資料持久化" .-> Disk
    
    %% Monitoring Flow
    Docker -. "容器日誌與主機效能" .-> Ops_Agent
    Ops_Agent -- "即時監控數據" --> Ops_Dashboard
    
    %% Styling
    classDef external fill:#f9f9f9,stroke:#333,stroke-width:2px;
    classDef gcp fill:#e3f2fd,stroke:#1976d2,stroke-width:2px;
    classDef gce fill:#ffffff,stroke:#388e3c,stroke-width:2px;
    classDef container fill:#fff3e0,stroke:#f57c00,stroke-width:1px;
    
    class Internet,CF external;
    class GCP gcp;
    class GCE,VPC gce;
    class Cloudflared,Site,API,Bot,ES,Resolver,Cron container;
```

新 Devops manual https://github.com/cofacts/devops/pull/1/changes

### 小聚籌備
- [ ] 投放目標：雙北
- [ ] VOOM 發文
- [ ] FB 發文
- [ ] 食物：沒有
- [ ] 記得帶：貼紙、不太環保杯 (bil)

