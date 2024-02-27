---
tags: cofacts, security, resilience, 資安, CCPRIP
---

# Cofacts Chatbot Platform Resilience Improvement Plan

整理 Cofacts 在不同層級上可用於提升穩定性、安全性與 scalability 的方式，以應對可能到來的威脅。

## Infrastructure layer 基建層

重心：機器安全、服務運作與近用

- 伺服器架構
- 主機存取權限管理
  - root access
  - ssh access (`authorized_keys`)
  - firewall settings
- 主機資源使用率
  - ram, cpu, disk usage
  - elasticsearch
  - url-resolver
  - AI
- OS security patches
- Monitoring of infrastructure
  - fail2ban
  - ram / cpu / disk alerts
- Open source / third party platform access
  - Docker hub (runtime images)
  - Github (source code)
- API, chatbot, web 使用資源
- dependency vulnerability and security patch
  - update tech stack e.g. old nextjs
- CDN
    - g0v.tw: 直連
    - cofacts.tw: 擋一層 cloudflare
- Monitoring of access
  - know where a request comes from
    - IP
    - [API key](https://g0v.hackmd.io/@mrorz/cofacts-rd/%2F51wwLHgvSUqtBDaP-yAVnA) mechanism
        - Block requests without API secret / signature
        - Ensure resource for API users
  - downtime detection and recovery
  - block abnormal traffic
- User account safety; avoid automatic account linking https://www.ory.sh/docs/kratos/social-signin/overview#dangers-of-automatic-account-linking

### 現況

- 1 台 Linode ㄏㄏ

### Proposal

- Replace Linode with Cloud service providers to eliminate infra effort
- Manage access on cloud
- Ensure horizontal scalability by leveraging public cloud
- Move servers to behind Cloudflare
- Elasticsrarch > 8
  - current 6 does not run on Apple Silicon https://stackoverflow.com/questions/68877644/how-to-run-elasticsearch-6-on-an-apple-silicon-mac
  - enables vector search

#### Phase 1: rumors-site & rumors-line-bot 上 Google cloud run

Benefits of Cloud Run:
- Fully managed, but can use container
- Billed only after access
- Can auto-deploy after image updates
- Setup env variable on GCP web console
- Alternative: AWS App Runner ([comparison](https://www.kloia.com/blog/aws-app-runner-vs-google-cloud-run))

---

- rumors-site is stateless, should be able to run on cloud run.
- rumors-line-bot 的 MongoDB 可以考慮轉到 https://www.mongodb.com/cloud/atlas/mongodb-google-cloud 一起管理 --> done on 2023/12/5
- rumors-line-bot uses redis, 但 Google cloud 的 redis （Memorystore）超爆貴，接近 50usd/mo
    - 可以用 redis cloud, free 30MB / 100MB for 5usd/mo (no HA) ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_53e030a0192a5b4d5d2996ab29ec64d9.png)
    - 如果一定要架在台灣 --> [自己開台 GCE instance 來 host](https://www.reddit.com/r/googlecloud/comments/s5an9g/cheap_temporary_memory_alternative_for/)
- Order
  1. Staging site
  2. Production en & ja site
  3. Staging chatbot 
  4. Production tw chatbot
  5. Production tw site


#### Phase 2: move API sub-services into Cloud Run

Steps include:
- 移除 `cofacts/url-resolver` 裡的 GRPC
    - 轉為如 `cofacts/media-manager` 的純 Typescript library
    - 不管 server / client communication
- rumors-api 轉為 monorepo of:
    - Application API (GraphQL)
    - URL resolver (tRPC)
        - 即現有 url-resolver 改 tRPC
        - 看看有沒有機會 request 來才啟動 browser（stateless）- https://cloud.google.com/blog/topics/developers-practitioners/taking-screenshots-web-pages-cloud-run-jobs-workflows-and-eventarc
        - 傳大 HTML string 的 performance
            - Can implement [data transformers](https://trpc.io/docs/server/data-transformers)
            - https://pouyae.medium.com/sia-an-ultra-fast-serializer-in-pure-javascript-394a5c2166b8
    - Media manager (tRPC)
        - 實作轉檔邏輯、進行轉檔
- tRPC components 上 Cloud Run
    - Authentication: https://lynn.zone/blog/trpc-service-to-service-on-cloud-run/
    - 觀察 Cloud run latency、cost
    - 觀察 Linode 下降多少 load


#### Phase 3: Elasticsearch & API 上 google cloud

- Elasticsearch: hosted elasticsearch on Google cloud https://www.elastic.co/partners/google-cloud
- API: cloud run?

Note: GCP 發票
- 其實 GCP 本來就會有發票；經銷商是會有大量採購折扣。
    - 但 Google cloud 銷售團隊也有直接寄信來聯繫這樣
- 田中 https://tscloud.com.tw/product/gcp-billing
- 宏庭 https://www.microfusion.cloud/news/google-cloud-billing/

:::info
Update: Cofacts 的 GCP 現在由 Cofacts 在 OCF 的捐款專戶支出，發票問題已經解決。
:::

### DDoS defense with Cloudflare

Website
- Use cloudflare firewall
  > - cofacts.tw--> Cloudflare --> Cofacts website
  > - cofacts.g0v.tw--> nginx w/ HTTPS --> 301 cofacts.tw --> Cloudflare --> Cofacts website
- If 301 redirect floods nginx, try using another 301 redirect service that supports custom domain

API
- **Deprecate cofacts-api.g0v.tw**
- API access management (see Op layer)

### Logging and monitoring
- Health check: [cloudflare](https://blog.cloudflare.com/new-tools-to-monitor-your-server-and-avoid-downtime/)
  - notifies email, slack, discord
- DDoS notification: cloudflare
  - same channels
- Logging
  - Google cloud logging
  - AWS Cloud watch

### Past incidents 
> https://hackmd.io/i0GcWSSVQNeDQ_OBebyk6Q
- DDoS
- RAM full
- Disk (or docker container's device mapper) full

## Operation layer 維運層

重心：Ensuring integrity of the user generated content

- CIB detection
    - reveal source of request (i.e IP addresses, account created time, last login time, etc)
        - Reveal past content from users
    - monitor certain article that is being targeted
- More automated blocking / takedown mechanism
    - Can handle article, reply, ...etc. All user-generated contents
    - Can be carried out by more administrators
    - Can still be transparent on what modification is being made
- Explicit content filtering: avoid account being busted with explicit content
  - Safesearch annotation https://cloud.google.com/vision/docs/detecting-safe-search
  - Pricing: free
- [API access management](https://g0v.hackmd.io/@cofacts/rd/%2Fj27XFAQ0R0Cuqi2jDLJuWw)
    - No public access; all access to API are authorized, managed and monitored
    - Implementiton is infra-layer
    - Managing multiple apps (including those not implemented by Cofacts) is operation
- Moderation at wartime (?) 平時照舊，但先實作機制，可以 switch to war time mode
    - Account creation: 僅開放給實體小聚參與者？
    - 改變 reply sorting mechanism 不讓新人的回應在前面？

## Community layer 社群層

重心：empowerment and capacity building of the fact-checking community

- Offline community building activities
- Intrinsic incentive: visualizing impact of own contribution
    - Reach of the reply
- Extrinsic incentive of contribution
- Topic labeling
    - Supervised learning of Cofacts topics with Vertex AI AutoML
      - [Pricing](https://cloud.google.com/vertex-ai/pricing): prediction USD5 / 1000 text records (1,000 unicode characters each)
      - Batch processing does not need to deploy endpoints
    - Cloud natural language API's classifier
      - All categories https://cloud.google.com/natural-language/docs/categories contains COVID-19, etc
      - Pricing: by unicode characters ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_aa481bf2c2cc2968f95ed2f279f92035.png)
- Technologically supporting fact-checking operation
    - Better UI/UX when searching and reusing existing replies
    - New collaborator on-boarding tutorials on the website, enabling self-served learning
- Technologically supporting fact-checking multimedia content
    - Length and thumbnails for video and audio
        - Easy to skim through various content
    - [Smarter](https://g0v.hackmd.io/aJqHn8f5QGuBDLSMH_EinA#Vector--embedding-based-similarity) dedup and better similarity comparison
    - [Crowdsourced transcripts](https://g0v.hackmd.io/@cofacts/rd/%2FOhGIQzoxR5eF6audQuS_FQ)
        - enables searching by text
        - enables related article
        - enables AI topic categorization
    - Automated OCR / speech-to-text transcripts
        - enables chatbot searching of similar content with the same piece of text, which is very common in rumors
    - [Generative AI assistive fact-checking](https://g0v.hackmd.io/@cofacts/rd/%2F%40cofacts%2FrknFrmdk3)
    - Reverse image search with CloudVision API
      - https://cloud.google.com/vision/docs/detecting-web
      - Takes image or screenshot of video
      - Search on horizontal flips
      - Pricing
        - free for first 1000 unit / mo
        - 3.5 per 1000 unit afterwards
- Project WTF - Widen The Funnel
    1. 認知到假訊息問題
        - DTL、IORG、假清、黑熊也在做
    2. 使用 Cofacts LINE bot
        - 目前沒人其他人幫忙
        - 媒體露出
        - 打廣告？
        - 把 google 上查訊息的人變成 LINE 使用者
    3. 參與培訓
        - 推播
        - 野生查核工作坊？
          - 希望講者可以確保回應品質，不夠好的要幫忙回掉，否則會增加其他協作者工作量
    4. 產生貢獻
        - 每週感謝++
        - 進 Slack / discord / FB group 後持續有東西討論
        - Badge / Organization?
        - 後續活動？
          - 再發訊息給來過的人 [name=bil]
          - 每半年到一年發訊息給曾經來過的人，請他們再來一次，可以不用聽，來喝飲料做志工
- Content generation at wartime
    - Needs an editorial mechanism coordinating information collection & writing counter-narratives?
    - Open source intelligence investigation
    - Faster response for enemy's propaganda by dedicated collaborators?
    - Connection / private groups holds contributors together [name=bil]
- Well-being of Cofacts working group members and collaborator community


