---
tags: edu, nonprofit-helper, nonprofit, ngo, nonprofits
title: nonprofit-helper 0st meeting
---

# nonprofit-helper 0st meeting

## 架構
- DB
    - [DataStax](https://www.datastax.com/)
- 網頁
    - bootstrap 輕鬆刻
- 後端
    - 伺服器
        - AWS or
            - 已建
        - [zeabur](https://zeabur.com/docs/zh-TW/billing/sponsor) 
            - 要寫信先問一下時程趕不趕得上
## 參考資料
- [如何 5 分鐘內，幫你的 GPTs 加上資料庫](https://chatgptlanding.substack.com/p/gpts-oauth-astradb)
- https://github.com/admineral/OpenAI-Assistant-API-Chat
- [Assistants_API_overview_python.ipynb](https://github.com/openai/openai-cookbook/blob/main/examples/Assistants_API_overview_python.ipynb)
- [A Survey of Techniques for Maximizing LLM Performance](https://www.youtube.com/watch?v=ahnGLM-RC1Y)

## 分工
### Paul
- prompt
- assistant-api breakdown
- frontend


### Wei-ting
- maintain AWS Server 
- DataStax DB <-> OpenAI


## scope for now
- 生成式 AI 聊天機器人協助釐清行政法規和流程
    - 該系統利用生成式 AI 技術解析複雜的行政規定和流程，幫助非營利組織理解並遵守相關規範。功能包括：
        - 需要將法規和函釋相關的資訊 embedding，才能給予使用者精確的回覆
        - 用於理解使用者詢問的問題和內容，將前述 query 轉成 JSON 進行搜尋

### Todo items
#### Inbox
- [ ] 彙整公益社團法人相關法規 + 函釋
- [ ] 測試出可用的 prompt
- [ ] 刻出網頁畫面
    - [ ] Chatbot interface
    - [ ] import custom regulation file interface
        - [ ] e.g. 該組稱組織章程
    - [ ] calculator of meeting member counter
        - [ ] input fields for present member's number
        - [ ] 可能要串章程 + 會議規範（內政部頒布）
    - [ ] guide to found a new orgnization (nice to have)
        - [ ] input fields for require informations
- [ ] 去敲零時先輩時間
- [ ] 講解 OpenAI Platform
- [ ] 

#### Doing
- [ ] 拆產品架構和功能
- [ ] 設定 server and DB
#### Done
- [x] 設定 OpenAI API orgnization and charge credit

## **DDay from now: 30 days left**


## issues
- 疑似：法規資料若以 GPT-4  and assistant api 做 retrieval token 數會超多
    - 要考慮改用 chat completion and embedding