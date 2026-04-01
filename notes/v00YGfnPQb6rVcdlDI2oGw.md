---
tags: cofacts,
---

# 20260113 會議記錄

:::info
- [所有會議記錄](httpss://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：bil, alfred, mrorz, nonumpa
- 線上出席：
- https://meet.google.com/mrz-dgrd-pri
:::

## :eyes: 上次會議跟進事項

- [x] Devops manual: Update README.md
- [x] Devops manual: Create AGENTS.md
- [ ] Devops manual: Add Github Claude workflow
		- Cloudflare 文件：使用 Cloudflare MCP 紀錄現況

## 小聚籌備

- 2026/02/08 14:00-17:00 青職基地二樓借好了 [name=bil++]

02/08 (日) 2pm - 5 pm 
- 誰會來呢: bil, mrorz, nonumpa, alfred
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
  - 推播日：01/21（01/21 或是 01/25 設定）
  - 目標：雙北
- [x] KKTIX: https://cofacts.kktix.cc/events/cofactseditor51
- [ ] 記得帶：貼紙、不太環保杯 (bil)
- [ ] LINE 文案：「俄羅斯總統女兒腦腫瘤血破裂，求助台灣女婿向台積電求援，經台積電台大醫院聯手開刀診治救回成功🏆」這是生成式ＡＩ做出來的假內容。動手闢謠，讓我們一起保護家人，Cofacts 真的假的 第 51 次志工查核工作坊需要你的加入，活動完全免費，（請自備電腦）02/08(日)下午，地點青職基地，最近的捷運站是捷運板橋站1號出口。連結內報名：https://cofacts.kktix.cc/events/cofactseditor51
- [ ] VOOM 發文
- [ ] FB 發文

## Server Alerts
- `api.cofacts.tw` and `line-bot.cofacts.tw` 在 1/7 和 1/9 皆有數次不穩的狀況。
- 1/9：
    ![](https://g0v.hackmd.io/_uploads/H1eMSZDXBbe.png) ![](https://g0v.hackmd.io/_uploads/BJlYSZvXSbl.png)
    > 看起來仍然是 url-resolver 使用太多 RAM 使系統 RAM 超過臨界
    > SSH 進去重開 url resolver 之後狀況解除
    > 工程方向仍是把 url-resolver 搬出去
- 爬網頁每個 request 開 browser, process 就會爆炸 [name=nonumpa]
	- puppeteer 可能沒辦法完整的關掉 process
	- 每個 request 都有 process，即使跑在 docker 裡面也會導致 host machine 壞掉
	- Solution: 開單一個 browser 然後每個 request 都是用同一個 browser
	- 每次都起 browser 的話 memory consumption 會越來越多，可能是沒 free 乾淨
