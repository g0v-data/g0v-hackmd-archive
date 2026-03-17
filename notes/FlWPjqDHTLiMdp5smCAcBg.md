# 20260317 會議記錄

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

### DB migrate to elasticsearch 9.2
- [x] code review API & DB PR [name=mrorz]
- [x] migration SOP 文件 (for coding agent to execute migration) [name=nonumpa]
	- [x] 要同時開兩台 db，需要調整 resource
	- [x] https://github.com/cofacts/rumors-api/pull/381/changes/09ac28f366a855feb58bc8717c9e1a0937488293

## Updates

- Claude code action updated - https://github.com/cofacts/ai/pull/21#issuecomment-4069380648

### 綜合頻道

- **mrorz@g0v-tw**
  > Cloudflare 有爬網頁的 API 惹
  > https://developers.cloudflare.com/changelog/post/2026-03-10-br-crawl-endpoint/

- **mrorz@g0v-tw**
  > Cofacts 的 Linode 開了很久，Linux 與 docker engine 都卡在好久以前的版本。我想趁著接下來升級 Elasticsearch 的停機時間，直接把目前的老 Linode instance 換掉。
  >
  > 目前評估下來，放在台灣的 GCE with Container Optimized OS 好像是個滿好的選項，試算如下：
  > https://docs.google.com/document/d/1sZ4jOsrZPvbJv4QjlMxgbqFsh_pTZNBRs-NbG-HU0rM/edit?tab=t.8j5j4xlz2qmo#heading=h.c9s30vhbbc9t
  > RAM 開到 32GB 的話，或許網站也能從 cloudrun 搬回來。另外，通通都放在 Google Cloud 上，對我們管理 access 也比較有好處（可以直接用 google account），連帳務處理都更容易。
  >
  > 大家可以協助評估一下這份報告裡的作法，我也會找時間開個小的 GCE with Container Optimized OS 看看是否用得順手。

- **bestian@g0v-tw**
  > 有無可能佈署到CloudFlare 用serverless 環境？

- **mrorz@g0v-tw**
  > Elasticsearch 和 API 應該不可能 XD 不管是否考慮 cloudflare pages & worker，都是要開台機器的，本文重點也在這。文中有關網站這類 client 是順便塞的。
  >
  > 另一方面，cloudflare worker and pages 是 PaaS + edge computing 架構，不是以 docker image 為主的 container 部署平台，塞過去要大改架構，因此目前不考慮。

:::info
TODO - @mrorz 
- 執行 https://docs.google.com/document/d/1sZ4jOsrZPvbJv4QjlMxgbqFsh_pTZNBRs-NbG-HU0rM/edit?pli=1&tab=t.31x22849fdr2
- 確認 docker-compose 與 rumors-deploy script 是否可以共用
- 可以的話，開一台 production 設定好 ES6 snapshot，準備 migrate
	- 準備好後先停機，省 cost
:::


### Github 活動

- **Cofacts AI Repository**
  - **New Pull Request**: [Enhanced Langfuse Integration: Trace Text Extraction & User Feedback](https://github.com/cofacts/ai/pull/19)
  - **New Pull Request**: [Session List and Title Management](https://github.com/cofacts/ai/pull/20)
  - **New Pull Request**: [Implement Markdown support and message parts refactoring](https://github.com/cofacts/ai/pull/21)
  - **Closed Pull Request**: [refactor: improve type safety with openapi-fetch and simplify API with server functions](https://github.com/cofacts/ai/pull/18)

### 伺服器警報

- **2026-03-14**
  - `cofacts.tw` and `api.cofacts.tw` services were unhealthy (HTTP timeout).

---

## Design

- COS https://docs.google.com/document/d/1sZ4jOsrZPvbJv4QjlMxgbqFsh_pTZNBRs-NbG-HU0rM/edit?tab=t.31x22849fdr2#heading=h.qmggrn3hmjbo
- AI
	- Polarization https://docs.google.com/document/d/1sZ4jOsrZPvbJv4QjlMxgbqFsh_pTZNBRs-NbG-HU0rM/edit?tab=t.xhkm0lgp8yph#heading=h.bds7a9ytl0eb
	- AI https://docs.google.com/document/d/1sZ4jOsrZPvbJv4QjlMxgbqFsh_pTZNBRs-NbG-HU0rM/edit?tab=t.898ssgv1wzmk#heading=h.exs6cbiyoz13
	- Defense https://docs.google.com/document/d/1sZ4jOsrZPvbJv4QjlMxgbqFsh_pTZNBRs-NbG-HU0rM/edit?tab=t.z3mp0t1qzjyy#heading=h.ch3h3ngppkxg



----

## 小聚籌備

- 2026/04/12(日) 14:00-17:00 青職基地二樓借好了 

04/12 (日) 2pm - 5 pm 
- 誰會來呢: bil, mrorz, nonumpa, Lahna
- 辦在青職基地，已經確認借好
- [ ] 食物：沒有
- [x] 場地：新北市青年局青職基地
- [ ] 時間：13:00 擺桌子場佈
	- 活動時間：14:00 - 17:00
	- 時間分配
        - 2:00 - 2:20 開場
            - 影片
            - Slido 暖身
        - 2:20 - 2:40 引導註冊網站、介紹評價現有回應
        - 2:40 - 2:50 實作評價
        - 2:50 - 3:10 介紹補充資訊
        - 3:10 - 3:40 實作補充資訊、自我介紹、休息
        - 3:40 - 4:10 介紹撰寫新回應
        - 4:10 - 4:40 實作撰寫新回應
        - 4:40 - 5:00 介紹分類、RSS、合照
- [ ] 投放目標：
  - 推播日：03/26（04/01 或是 03/24 設定）
  - 目標：雙北
- [x] KKTIX: https://cofacts.kktix.cc/events/cofactseditor52
- [ ] 記得帶：貼紙、不太環保杯 (bil)
- [x] LINE 文案：假訊息的起手式：「只要年滿 65 歲，把資費改成每月 149 元的樂齡方案，兩年合約省出 8000 多元，這些錢本來都在幫電信公司賺業績，今天就教你怎麼把它們全部省回來。」這是生成式ＡＩ做出來的假內容。動手闢謠，讓我們一起保護家人，Cofacts 真的假的 第 51 次志工查核工作坊需要你的加入，活動完全免費，（請自備電腦）04/12(日)下午，地點青職基地，最近的捷運站是捷運板橋站1號出口。連結內報名：https://cofacts.kktix.cc/events/cofactseditor52
- [ ] VOOM 發文
- [ ] FB 發文