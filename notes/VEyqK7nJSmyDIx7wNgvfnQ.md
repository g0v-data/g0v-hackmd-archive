---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20250526 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- NPO Hub:
- 線上出席：
- Gather Town: https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline


### :star: Released to production


## 大松檢討

協作：https://g0v.hackmd.io/@cofacts/meetings/%2F%40mrorz%2Fry8K7jdblg

- beta.cofacts.ai
  - staging machine -- Cloudflare tunnel -- Cloudflare Access (Cofacts moderators only) -- Internet
  - Blocked by hackmd API ![](https://g0v.hackmd.io/_uploads/SyUm_K-fee.png)
- Open165
  - Discussed with 網址變青蛙
    - M will try vercel + Cloudflare
    - 交流想法與資訊（urlscan、whois 等）
    - 避免 block each other，我們各自開發但可互相交流資訊
  - Open165 refactor
    - Github workflow --> Cloudflare workflow
      - [Open165/worker] Pull request opened: #5 feat: migrate 165 site sync to Cloudflare Workflows by MrOrz
      - [Open165/site] Pull request opened: #37 Migrate database update to Cloudflare Worker by MrOrz
  - Open165 TODOs
    1. schema 也移動到 worker 來管
    2. worker 裡建立子 workflow
       - host --> urlscan --> 存 DB
       - host --> whois --> 存 DB
       - DB --> 某種資料交換格式 for 下游 application?
    3. Website display

## 小聚籌備
06/15 (日) 2pm - 5 pm 
- OK: 
- 辦在青職基地
- [ ] 食物：
- [ ] 場地：新北市青年局青職基地
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
  - 推播日：06/03（5/26 設定）
  - 目標：雙北
- [ ] KKTIX: https://cofacts.kktix.cc/events/cofactseditor47
- [ ] 誰會來呢： 
- [ ] 記得帶：貼紙、不太環保杯
- [ ] LINE 文案： Cofacts 真的假的 第 47 次志工查核工作坊需要你的加入，活動完全免費，（請自備電腦）06/15(日)下午，地點青職基地，最近的捷運站是捷運板橋站1號出口，連結內報名：https://cofacts.kktix.cc/events/cofactseditor46
- [ ] VOOM 發文
- [ ] FB 發文

