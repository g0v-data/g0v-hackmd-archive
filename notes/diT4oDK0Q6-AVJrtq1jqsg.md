
# 全國中央政府總預算和地方預算 MCP Tool - g0vcongressthon

:::info
📌 **專案目標**：將全國中央政府總預算和地方預算以 MCP Tool 共享
:::

## 🎯 專案由來

受到 ronnywang 整理 2025 政府預算資料的啟發，嘗試整合到 AI 工具鏈中，讓政府預算資料能被更廣泛地應用。

## 🚀 MCP Tool 整合狀況

### 現況：PostgreSQL MCP Server (暫時方案)

目前透過自建的 PostgreSQL MCP Server 提供服務：

```json
{
  "servers": {
    "postgres": {
      "type": "sse",
      "url": "https://g0vcongressthon-data.funtuan.work/sse"
    }
  }
}
```

chatmode 範例
```markdown=
// government-budget-related.chatmode.md
---
description: 'Query government budget-related data and respond to user inquiries'
tools: ['postgres']
---

# Government Budget Data Query Assistant

## Overview
This assistant specializes in querying and analyzing government budget data from PostgreSQL databases to provide comprehensive responses to user questions about public financial information.

## Query Strategy

### 1. Schema Discovery
- Use `list_schemas` to identify all available database schemas
- Map out the data structure to understand available budget categories and tables

### 2. Iterative Query Refinement
- Employ `explain_query` multiple times to narrow down the scope
- Validate query logic before execution to ensure accurate results
- Progressively refine queries based on initial findings

### 3. Comprehensive Response Generation
- Aggregate results from multiple `explain_query` operations
- Provide detailed analysis based on collected data
- Present findings in a clear, structured format that addresses the user's specific inquiry

## Best Practices
- Always start with broad schema exploration
- Use iterative querying to build understanding
- Validate data relationships before drawing conclusions
- Provide context and explanations alongside raw data
```

:::warning
⚠️ **問題**：PostgreSQL MCP Server 可能有安全風險
:::

### 目標：Supabase Anonymous Key MCP Tool 🔍

**理想狀態**：直接使用 Supabase Anonymous Key 作為 MCP Tool，優點包括：
- ✅ 無需自建伺服器維護
- ✅ Supabase 穩定性更高
- ✅ 內建 RLS 安全機制
- ✅ 官方支援和文件完整

**已上傳至 Supabase**：
- Project URL: `https://hubgcccdtbtkcfbuupvp.supabase.co`
- Anonymous Key: `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6Imh1YmdjY2NkdGJ0a2NmYnV1cHZwIiwicm9sZSI6ImFub24iLCJpYXQiOjE3NTg0NTM0NDAsImV4cCI6MjA3NDAyOTQ0MH0.jRyskWZF0t49ItsEuDuAn1KOFsBQ2_gFyWZ1muT8SrA`

### 🔬 技術探索方向

#### 方案一：尋找現有的 Supabase MCP Tool（Support Anonymous Key）
- 搜尋 MCP registry 是否有 Supabase 相關工具
- 檢查 GitHub 上的開源 MCP 專案
- 詢問 MCP 社群是否有相關經驗

#### 方案二：開發 Supabase MCP Tool（Support Anonymous Key）

如果沒有現成工具，可能需要自建


## 🔍 使用範例（使用 GitHub Copilot 作為 Agent）

### 查詢範例 1：外交部的護照預算如何？
![](https://g0v.hackmd.io/_uploads/B1_-Bcpsee.png)


### 查詢範例 2：台北市5年內衛生相關的預算成長多少？協助找出台北市預算成長的關鍵？跟新北市比較呢？
![](https://g0v.hackmd.io/_uploads/SywvH5piel.png)
![](https://g0v.hackmd.io/_uploads/SkCwS5Tjge.png)
![](https://g0v.hackmd.io/_uploads/rJEdH9ajee.png)

### 查詢範例 3：高雄這幾年有花錢在清理排水嗎？預算是變多還變少？

![](https://g0v.hackmd.io/_uploads/SJnmY5pseg.png)
![](https://g0v.hackmd.io/_uploads/HytsY5asll.png)


## Repo

### PostgreSQL ETL
[https://github.com/funtuan/g0vcongressthon-data-etl](https://github.com/funtuan/g0vcongressthon-data-etl)


*最後更新：2025年9月21日*
*專案維護：funtuan*