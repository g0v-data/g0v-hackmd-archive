# 發哥準備

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

