# 發哥準備

## 職位來源

晶片太複雜 → 需要軟體自動化設計 → EDA 工具誕生 → 工具需要命令介面 → 選了 TCL → 三十年累積大量 TCL flow → 現在想用 AI 加速寫 TCL → 這個職缺出現


公司
產品
主打
Synopsys
Synopsys.ai Copilot
EDA flow 助手、RTL 生成
Cadence
JedAI Platform + Cerebrus + ChipStack
全流程 agentic AI
Siemens EDA
散布在各工具中
較低調


## Agentic Work

```
┌─────────────────────────────────────────────────┐
│              Orchestrator / Planner             │  ← 拆解任務、決定下一步
└─────────────────────────────────────────────────┘
           │              │              │
           ▼              ▼              ▼
    ┌──────────┐   ┌──────────┐   ┌──────────┐
    │  Agent A │   │  Agent B │   │  Agent C │   ← 各司其職的 sub-agent
    │ (Synth)  │   │  (APR)   │   │ (Verify) │
    └──────────┘   └──────────┘   └──────────┘
           │              │              │
           ▼              ▼              ▼
    ┌─────────────────────────────────────────────┐
    │      Tool Layer (EDA tools + scripts)       │  ← 真正動手的執行層
    │  Synopsys DC, PrimeTime, Innovus, Calibre   │
    └─────────────────────────────────────────────┘
           │
           ▼
    ┌─────────────────────────────────────────────┐
    │  Knowledge Base (RAG) + Mental Model         │  ← 領域知識
    │  PDK docs, flow templates, past designs      │
    └─────────────────────────────────────────────┘
```

plan and exec

```
┌─────────────┐
User ──▶│   Planner   │ ← 大模型，做高階規劃
        └─────────────┘
               │
               │ 產生 step-by-step plan
               ▼
        ┌─────────────┐
        │  Executor   │ ← 小模型/專用模型，逐步執行
        └─────────────┘
               │
               ▼
         [EDA tools]
```


critic and refine

```
┌──────────┐
        │ Generator│ ← 產生候選 RTL/SDC/script
        └──────────┘
              │
              ▼
        ┌──────────┐
        │   EDA    │ ← 跑工具拿到實際結果
        │  Tool    │   (compile, sim, lint, DRC)
        └──────────┘
              │
              ▼
        ┌──────────┐
        │  Critic  │ ← 分析 error message，給修正方向
        └──────────┘
              │
              └─────loop back──────┐
                                   ▼
                            ┌──────────┐
                            │ Refiner  │ ← 根據 critique 修改
                            └──────────┘
```


plan and make each step to critic and refine

共享 mental state


1. 狀態管理（State Management）
EDA flow 的中間產物極多——netlist、DEF、SDC、library、各種 report。Agent 之間怎麼共享這些？怎麼避免一個 agent 改了狀態破壞別人？
主流做法是用 file-based + metadata index:每個 artifact 有 manifest 記載它的「設計階段、corner、版本」，agent 透過查 manifest 找正確檔案。

2. 長時間執行（Long-Running Tasks）
跑一次 P&R 12 小時，agent 不能就 block 在那。需要 async job queue + checkpoint，agent 提交任務後去做別的，定期回來看狀態。



## RAG

Query router to different domain.

```
┌─────────────────────────────────────────────────────────┐
│                  Query Router (LLM)                      │
│  分析問題: 這是知識問題？流程問題？當前設計問題？        │
└─────────────────────────────────────────────────────────┘
       │            │            │            │
       ▼            ▼            ▼            ▼
┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐
│ Static   │ │ Code     │ │ Design   │ │ History  │
│ Knowledge│ │ Knowledge│ │ State    │ │ Log      │
│   RAG    │ │   RAG    │ │  Query   │ │   RAG    │
└──────────┘ └──────────┘ └──────────┘ └──────────┘
     │            │            │            │
     ▼            ▼            ▼            ▼
  PDK docs    Verilog/TCL  目前的 netlist   過去專案
  Tool manual  scripts     SDC, reports    JIRA tickets
  Internal     templates                    Slack chats
  guidelines
```

Metadata 是 pre-filter 的關鍵
hybrid search (BM2.5 + dense)

純 dense（向量）會漏掉精確命令名稱；純 sparse（BM25）會錯過語意相近的問法。兩個都要、加權合併。


Neo4J for graph DB

```
使用者: "我跑 dc_shell 出現 UID-401 警告，怎麼處理？"
          │
          ▼
   ┌─────────────────┐
   │  Query Analysis │  ← LLM 分析: 這是工具錯誤碼問題
   │     (LLM)       │     需要: tool manual + 歷史經驗
   └─────────────────┘
          │
     ┌────┴────┐
     ▼         ▼
┌─────────┐ ┌─────────┐
│ Tool RAG│ │History  │
│         │ │ RAG     │
└─────────┘ └─────────┘
     │         │
     │ Filter: │ Filter:
     │ tool=DC │ tag=UID-401
     │ ver=當前 │ resolved=true
     ▼         ▼
[手冊片段]  [過往三個ticket]
     │         │
     └────┬────┘
          ▼
   ┌─────────────────┐
   │  Re-ranker      │  ← 把所有 chunks 重新排序
   │  (cross-encoder)│     基於 query 的相關性
   └─────────────────┘
          │
          ▼ top 5 chunks
   ┌─────────────────┐
   │ LLM Generation  │  ← 生成回答
   │  with citations │     必須引用來源
   └─────────────────┘
          │
          ▼
"UID-401 通常是 timing library 沒讀進來。
 [來源: PrimeTime manual §3.2]
 
 三週前 CPU team 也碰過，他們的解法是:
 [來源: JIRA TICKET-1234]
 在 .synopsys_dc.setup 加入 search_path 設定 ..."
```

## Metadata Design

1. Pre-filter（檢索前過濾）
向量搜尋成本高、結果雜訊大。Metadata 讓我們先把「不可能相關」的文件排除。例如「我在 N3 專案，只查 N3 相容的文件」這種硬性過濾。
2. Re-rank signal（重排訊號）
兩個語意分數相近的結果，metadata 告訴我們哪個更可信。例如近期文件 > 舊文件、官方手冊 > 內部 wiki、資深工程師寫的 > 新人寫的。
3. Provenance（來源追溯）
工程師看到答案，要能追到「這來自哪個文件、哪個版本、誰寫的、什麼時候」。沒這個 EDA 場景無法上線。
4. Access control（權限控制）
A 專案的人不能 retrieve 到 B 專案的內容。Metadata 是權限決策的依據。
5. Lifecycle management（生命週期管理）
文件會過期、會被取代、會被廢棄。Metadata 記錄狀態，讓系統知道哪些該 retrieve、哪些該排除。




