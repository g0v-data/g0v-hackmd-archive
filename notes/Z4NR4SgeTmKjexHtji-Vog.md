# 發哥面試準備

> **目標職位**:MediaTek AI 工程師（Chip Design / EDA + AI）
> **核心 talking points**:EDA 產業脈絡 → Agentic Workflow → RAG → Metadata 系統設計

---

## 0. 開場敘事:這個職位為什麼存在

一句話版本:
> 「晶片太複雜 → 需要 EDA 工具自動化 → EDA 工具用 TCL 當命令介面 → 三十年累積了大量 TCL flow 知識 → 現在想用 LLM 加速整套流程 → 所以這個職位出現了。」

完整邏輯鏈（口頭講述用）:

1. 現代晶片有數百億顆電晶體，人類不可能手畫
2. 因此誕生了 **EDA（Electronic Design Automation）**:用軟體把 RTL 自動轉成可製造的版圖
3. EDA 工具需要命令介面，1990 年代選了 **TCL**（當時 Python 尚未成熟）
4. 三十年下來，**SDC 約束、flow 腳本、客戶 know-how 全綁在 TCL**
5. LLM 出現後，產業意識到可以用 AI 加速「寫 TCL flow」這件事
6. MediaTek 作為 EDA 大客戶，需要建內部的 **AI-assisted EDA 平台**

---

## 1. 產業競爭格局（提一下就好）

| 公司 | 產品 | 主打方向 |
|---|---|---|
| Synopsys | Synopsys.ai Copilot | EDA flow 助手、RTL 生成 |
| Cadence | JedAI + Cerebrus + **ChipStack AI Super Agent** | 全流程 agentic AI |
| Siemens EDA | 散布在各工具中 | 較低調 |
| NVIDIA（自用） | ChipNeMo / Bug Nemo | 內部專屬 LLM |

**MediaTek 的位置**:大客戶 + 自建內部系統，類似 NVIDIA ChipNeMo 的路線。

---

## 2. Agentic Workflow:核心架構

### 2.1 整體骨架

```
┌─────────────────────────────────────────────────┐
│         Orchestrator / Planner                  │  ← 拆解任務
└─────────────────────────────────────────────────┘
       │              │              │
       ▼              ▼              ▼
  ┌────────┐    ┌────────┐    ┌────────┐
  │ Synth  │    │  APR   │    │ Verify │       ← 各司其職的 sub-agent
  │ Agent  │    │ Agent  │    │ Agent  │
  └────────┘    └────────┘    └────────┘
       │              │              │
       ▼              ▼              ▼
  ┌─────────────────────────────────────────┐
  │  Tool Layer (DC, PrimeTime, Innovus...) │   ← 真正執行
  └─────────────────────────────────────────┘
       │
       ▼
  ┌─────────────────────────────────────────┐
  │  Knowledge Base (RAG) + Mental Model    │   ← 領域知識
  └─────────────────────────────────────────┘
```

### 2.2 兩個關鍵 sub-pattern

**Pattern A:Planner-Executor（規劃-執行分離）**

```
User ──▶ ┌─────────┐
         │ Planner │  ← 大模型，做高階規劃（昂貴但聰明）
         └─────────┘
              │ step-by-step plan
              ▼
         ┌─────────┐
         │Executor │  ← 小模型，逐步執行（便宜可批量）
         └─────────┘
              │
              ▼
         [EDA tools]
```

**為什麼有效**:大模型擅長規劃但貴；小模型擅長重複執行但不會規劃。分開後成本/品質雙贏。

**Pattern B:Critic-Refiner Loop（生成-檢驗-修正）**

```
┌──────────┐
│Generator │ ← 產生候選 RTL/SDC/script
└──────────┘
      │
      ▼
┌──────────┐
│ EDA Tool │ ← 跑工具拿實際結果（compile/sim/lint/DRC）
└──────────┘
      │
      ▼
┌──────────┐
│  Critic  │ ← 分析 error，給修正方向
└──────────┘
      │
      └──── loop ────┐
                     ▼
              ┌──────────┐
              │ Refiner  │ ← 根據 critique 修改
              └──────────┘
```

**為什麼 EDA 特別適合**:工具本身就是最好的 ground truth verifier，不像寫文章需要主觀判斷。

### 2.3 組合使用

實際的設計是 **Plan → 每個 step 內部跑 Critic-Refine → 共享 mental state**。

### 2.4 工程上的兩大挑戰

**1. 狀態管理（State Management）**
- 問題:netlist / DEF / SDC / library / 各種 report 中間產物極多
- 解法:**file-based + metadata index**，每個 artifact 有 manifest 記載「設計階段、corner、版本」

**2. 長時間執行（Long-Running Tasks）**
- 問題:一次 P&R 跑 12 小時，agent 不能就 block
- 解法:**async job queue + checkpoint**，agent 提交任務後做別的、定期 poll 狀態

---

## 3. RAG:讓 LLM 不要亂噴

### 3.1 為什麼 EDA 的 RAG 特別難（30 秒版）

- 內容極度異質（PDF / TCL / report / 對話）
- 語義相似 ≠ 答案正確（依賴當前設計狀態）
- 答案需要精準的命令與參數
- 知識會「靜默過期」（PDK 換版、tool 升級）
- 機密性極高（必須 on-premise）

### 3.2 Query Router 架構

```
┌──────────────────────────────────────────┐
│            Query Router (LLM)            │
│ 分類: 知識題？流程題？當前設計題？歷史題？│
└──────────────────────────────────────────┘
    │          │          │          │
    ▼          ▼          ▼          ▼
┌──────┐  ┌──────┐   ┌────────┐ ┌────────┐
│Static│  │ Code │   │ Design │ │History │
│ RAG  │  │ RAG  │   │ State  │ │  RAG   │
└──────┘  └──────┘   └────────┘ └────────┘
    │         │           │          │
    ▼         ▼           ▼          ▼
 PDK doc   Verilog    當前 netlist  過去專案
 Manual    TCL        SDC,reports   JIRA / Slack
 Guideline templates
```

**關鍵 insight**:不同問題該查不同來源。一個 generic「all-in-one」RAG 品質會很差。

### 3.3 兩個必備技術

**Hybrid Search（BM25 + Dense Vector）**
- 純 dense:會漏掉精確命令名稱（如 `set_max_delay`）
- 純 sparse（BM25）:會錯過語意相近的問法
- **兩個都要、用 RRF 合併**

**Graph DB（Neo4J）for relational queries**
- 設計區塊之間的階層關係、訊號連接關係，圖結構查詢比向量適合

### 3.4 完整查詢流程

```
使用者:"我跑 dc_shell 出現 UID-401 怎麼處理？"
        │
        ▼
   ┌─────────────────┐
   │ Query Analysis  │  ← LLM 抽出: 工具錯誤碼問題
   │     (LLM)       │     需要: tool manual + 歷史經驗
   └─────────────────┘
        │
   ┌────┴────┐
   ▼         ▼
┌────────┐ ┌──────────┐
│Tool RAG│ │History   │
│ filter:│ │ RAG      │
│tool=DC │ │ filter:  │
│ver=當前│ │UID-401   │
│        │ │resolved  │
└────────┘ └──────────┘
   │             │
   └──────┬──────┘
          ▼
   ┌─────────────────┐
   │   Re-ranker     │  ← cross-encoder 重排
   └─────────────────┘
          │
          ▼ top 5
   ┌─────────────────┐
   │ LLM Generation  │  ← 強制 citation
   └─────────────────┘
          │
          ▼
"UID-401 通常是 timing library 沒讀進來。
 [來源: PrimeTime manual §3.2]
 三週前 CPU team 也碰過: [JIRA-1234]
 在 .synopsys_dc.setup 加 search_path 設定..."
```

---

## 4. Metadata 系統設計（重頭戲）

> 💡 **核心觀念**:Metadata 不是向量搜尋的附屬品，是整個系統的骨架。

### 4.1 Metadata 的五大職責

1. **Pre-filter（檢索前過濾）**
   向量搜尋成本高、雜訊大。Metadata 先排除不可能相關的文件。例:「N3 專案只查 N3 相容文件」。

2. **Re-rank signal（重排訊號）**
   兩個語意分數相近的結果，metadata 告訴你誰更可信。例:近期 > 舊、官方 > wiki、資深 > 新人。

3. **Provenance（來源追溯）**
   工程師看到答案要能追到「哪份文件、哪個版本、誰寫的、何時」。**沒這個 EDA 無法上線**。

4. **Access control（權限）**
   A 專案的人不能 retrieve 到 B 專案內容。

5. **Lifecycle management（生命週期）**
   文件會過期、被取代、被廢棄。Metadata 記錄狀態。

### 4.2 三層 Schema 架構

```
┌────────────────────────────────────┐
│  Universal Metadata（所有都有）     │
│  chunk_id / source / author /      │
│  time / status / visibility /      │
│  embedding_version                 │
└────────────────────────────────────┘
          │
    ┌─────┼─────┐
    ▼     ▼     ▼
┌──────┐┌──────┐┌──────┐
│ Doc  ││ Code ││Design│  ← Doc-Specific
│ Meta ││ Meta ││ Meta │
└──────┘└──────┘└──────┘
          │
          ▼
┌────────────────────────────────────┐
│  Computed / Derived Metadata        │
│  auto_summary / linked_chunks /     │
│  CTR / dwell_time                   │
└────────────────────────────────────┘
```

**關鍵欄位（口頭可以舉這幾個來秀深度）**:

- `embedding_model` + `embedding_version`:處理 embedding drift
- `supersedes` / `superseded_by`:處理 PDK / tool 版本更替
- `author_seniority`:re-ranking 時加權
- `tool_version_compat`:確保不答錯版本
- `pdk_node`:N3 / N5 等製程節點過濾

### 4.3 儲存:三庫分離

```
┌─────────────────────────────────────────┐
│         Vector Database                  │
│   (Qdrant / Weaviate / pgvector)         │
│   chunk_id + embedding + 少量 metadata    │  ← 5-10 個 filter 用欄位
└─────────────────────────────────────────┘
                │
                ▼
┌─────────────────────────────────────────┐
│         Metadata DB (PostgreSQL)         │
│   完整 metadata / 關係 / 權限             │  ← 複雜 SQL / JOIN
└─────────────────────────────────────────┘
                │
                ▼
┌─────────────────────────────────────────┐
│         Object Storage (S3 / MinIO)      │
│   原始 chunk content + 原始文件           │
└─────────────────────────────────────────┘
```

**為什麼分三層（口頭講四個理由）**:

1. **各司其職**:Vector DB 做相似度、PostgreSQL 做結構化、S3 做大檔。
2. **效能**:Vector DB 的 metadata filter 欄位多了會退化，高基數欄位丟 PostgreSQL。
3. **演進靈活**:換 embedding model 不影響 metadata；換 vector DB 不影響權限。
4. **權限決策必須走 SQL**:EDA 權限規則複雜（專案 × 團隊 × 機密），向量庫的 filter DSL 表達不了。用 PostgreSQL **row-level security**。

### 4.4 查詢流程的四個關鍵點

1. **Pre-filter 大幅縮小搜尋空間**:幾百萬 → 幾千 chunks，向量搜尋速度與精度都提升。
2. **Filter 條件來自 query 分析**:LLM 先做 query 結構化抽取（這一步需要 prompt engineering）。
3. **Re-ranking 結合多訊號**:cosine + BM25 + author_seniority + recency decay + thumbs_up/down。
4. **Citation 強制輸出**:Prompt 要求每個 claim 附 `[source: chunk_id]`，後處理替換為人類可讀引用。

---

## 5. Bonus:Text2SQL 架構（可主動提）

如果聊到「結構化資料怎麼查」，可以帶到 text2SQL:

- 對 EDA 場景:**將 timing report / area report / DRC violation 視為結構化資料**
- 工程師問「show me top 10 setup violation paths」→ 自然語言 → SQL → 查 PostgreSQL → 回傳
- 跟 RAG 互補:**RAG 找知識，text2SQL 查當前設計狀態**

---

## 6. 面試 talking points 收尾

如果要用一段話總結你能帶來的價值:

> 「這個職位本質上是 build 一個 MediaTek 內部版的 Cadence ChipStack——把 LLM、Agentic Workflow、RAG 整合進現有 EDA flow。我熟悉這套技術棧背後的設計取捨:Plan-Execute vs Critic-Refine 該怎麼選、RAG 為什麼要 query router + hybrid search、Metadata 為什麼要三庫分離。這些不只是知識，是能直接動手做的工程能力。」

---

## 7. 預期會被問的問題（準備答案）

1. **LLM 寫 TCL 怎麼避免幻覺？**
   → Mental Model + RAG ground + schema validation + dry-run mode
2. **Agent 怎麼處理 12 小時的 P&R job？**
   → async job queue + checkpoint + polling
3. **RAG 怎麼處理 PDK 換版本？**
   → metadata 的 supersedes / tool_version_compat + 強制 version filter
4. **多 agent 之間怎麼共享狀態？**
   → file-based artifacts + manifest metadata index
5. **怎麼評估 RAG 系統好不好？**
   → retrieval log + CTR + dwell time + thumbs feedback + 定期 negative example 標註
