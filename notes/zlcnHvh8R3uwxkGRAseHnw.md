# 20260204 會議記錄

:::info
- [所有會議記錄](https://gov.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：bil, mrorz, mg
- 線上出席：
- https://meet.google.com/mrz-dgrd-pri
:::


## 📝 一般討論 (General)

### 伺服器記憶體問題

:::spoiler

#### System Overview
- Uptime: 406 days
- Load Average: 1.05, 1.02, 1.07 (on 6 Cores) -> Healthy CPU Load
- Memory: 16GB Total
- Used: ~12GB (Applications) + ~3GB (Cache)
- Free: ~340MB
- Swap: 100% Used (4GB / 4GB) -> CRITICAL

#### Resource Consumers
##### Memory
The system is under heavy memory pressure with Swap completely full.
1. Elasticsearch (rumors-deploy_db_1): ~7.83GB (50% of Host RAM)
2. Uptime: 2 hours (Recently restarted, yet memory filled again).
3. Heap Setting: ES_JAVA_OPTS=-Xms7g -Xmx7g.
4. Docker Daemon (dockerd): 2.3GB (RES). This is unusually high for a daemon and is a significant contributor to memory pressure.
5. Page Cache: ~3.1GB. usage is normal for Elasticsearch (Lucene indices interally use OS cache), but in a constrained system, this competes with applications.

##### Swap Analysis
- Swap Usage: 100% (4GB).
- Swappiness: 10 (Low).
- Interpretation: Even with a low preference for swapping (vm.swappiness=10), the system was forced to swap out 4GB because physical RAM was completely exhausted.

##### CPU
1. API (rumors-deploy_api_1):
    - Process node /srv/www/build/index.js (PID 14667) was using 74.6% CPU in top snapshot.
    - Averaged ~3.5% in docker stats.
    - This indicates traffic spikes or a heavy query processing, but keeping overall load low (~1.0).
2. Elasticsearch: ~58% of 1 core (in docker stats).

#### Resolution (Implemented 2026-01-28)
User applied the following limits to prevent OOM Killer from targeting random system processes:
1. Elasticsearch (db):
    1. Java Heap: 7g.
    2. Status: Healthy (7.6GB used).
2. URL Resolver:Status: Healthy (82MB used).

Result:
- System Swap is still full (expected without host reboot)

Post-Reboot Verification (2026-01-28 03:00台北時間)
The system rebooted successfully at 19:00 UTC.

Current Status
- Uptime: 5 minutes
- Memory:
    - Used: 7.3GB (Much lower than the previous 12GB + 4GB Swap)
    - Free: 8.3GB
    - Swap: 0B / 4GB (Completely cleared!)
- Docker Daemon: Memory usage is reset and healthy.
- Service Verification:
    - All core services are Up.
    - Note: `db` and `url-resolver` required a manual `up -d` right after reboot as they did not auto-start initially, but they are now running stable with the new limits.

Final Configuration
- Elasticsearch: Heap 7G
- Result: The system now has ~5-8GB of breathing room for OS cache and other services, significantly reducing the risk of a system-wide freeze.

:::

- **mrorz** 回報 API 服務不穩，主因是伺服器記憶體耗盡。
> "API not accessible now"
- 2026/1/28 **mrorz** 進行了緊急處理，包括調降 Elasticsearch 的 Java heap space，並重新啟動伺服器。
> "System Swap is still full (expected without host reboot), but apps are now contained."
> "The system rebooted successfully at 19:00 UTC."
- **mrorz** 提供了詳細的系統狀態分析，指出 Elasticsearch 是主要的記憶體消耗者。

要注意的事情：現在 Linode 上的 Linux 核心沒有開啟 cgroup memory，導致
- docker stats 現在不會顯示各個 container 的 RAM usage
- docker-compose 無法使用 mem_limit (本來我們也沒在用)

總之現在跟昨晚最大的差別就是
- elasticsearch container 的 Java heap space 從 8GB 調降到 7GB
- 重開過機器所以 swap 清空了、docker daemon 用的 RAM usage 也變低了
- docker stats somehow 看不到 RAM 了

:::success
看是否要增加 java heap space
:::

### 會議與協作
- **mglee** 表示想參加 2/4 的會議，了解 AI agent 的開發狀況。
> "請問可以參與 2/4 小聚嗎？想多了解目前 Cofacts 開發 AI agent 的狀況~"
- **edchen93** 與 **chewei 哲瑋** 討論了 HackMD 的筆記權限問題。

## 🚨 伺服器警報 (Server Alerts)

- 從 2026-01-27 到 2026-02-03，Cloudflare 多次發出 `cofacts.tw`、`api.cofacts.tw` 和 `line-bot.cofacts.tw` 的服務不健康警報，原因多為 HTTP timeout 或 回應代碼不符 (response code mismatch)。這似乎是一個持續存在的問題。

## 🤖 Github 活動 (Github Activities)

### cofacts/beta-ai
- **Pull Request #12: [Setup Langfuse for all ADK agents](https://github.com/cofacts/beta-ai/pull/12)**
  - 由 `MrOrz` 於 2026-02-02 發起，目的是為所有 ADK agents 設定 Langfuse 以進行觀察。
  - `gemini-code-assist[bot]` 和 `google-labs-jules[bot]` 已提供 review 意見。

### cofacts/takedowns
- **Pull Request #282: [Takedown spam user bk8linkvip iK_cEpwBRkUkW3J-LOKq](https://github.com/cofacts/takedowns/pull/282)**
  - 於 2026-01-31 建立並完成，處理了垃圾訊息使用者的下架。

## 小聚 rundown

- 週六早上
    - [ ] KKTIX 行前通知：提醒時間、使用電腦而非手機
  > Hello 你好，
	>
	> 本週日就是 2 月 8 日查核志工培訓囉！
	>
	> 志工培訓需要大量查詢資料，請自備筆電 💻 與充電器 🔌 並帶著愉快的心情來參加。帶順手的平板也可以的！如果願意協助編修影片逐字稿，請自備耳機唷🎧！
	>
	> 🕒 時間：2/08（日）14:00 - 17:00
	> 📍 地點：新北市青年局青職基地2樓 / 新北市板橋區民權路170號2樓(近板橋捷運站)
	> 
	> 費用全免，會很準時開始。若不克前往，記得取消報名 :)
	> 
	> Cofacts 真的假的 查核協作 VIP 臉書社團在這裡 👉 https://www.facebook.com/groups/cofacts
	> Cofacts 真的假的 查核協作 Discord 在這裡 👉  https://cofacts.tw/discord
	> 說你會來查核小聚優先加入 ＝Ｄ
	> 
	> 感謝你的閱讀。
	>
	> 那麼明天見囉😊
	>
	> 比鄰敬上
    - [x] 開場使用材料更新：https://docs.google.com/presentation/d/1N9DxoN1NuxdtQILkcV67y_q8EM8CJF5GhoYLcCKFpAc/edit [name=mrorz]
	- [ ] 準備 Slido `#cofacts`
		- [ ] 放投影片網址
- 當日準備 / 攜帶
    - [ ] 樓下用的標語 - bil
    - [ ] **拍照用大布條**
    - [ ] 貼紙 - orz, bil
    - [ ] 黏土 - orz
    - [ ] 手板 - bil
    - [ ] 講義 - bil
    - [ ] 一次性杯子 - bil
    - [ ] 延長線 - bil
        - 比鄰有 5 條
    - [ ] Wifi 機 - mrorz
        - [ ] rt-ax57 go
        - [ ] 電源線
    - [ ] 多帶一條 type-c 公公線 for dongle 的電
    - [ ] 備用 wifi 機 [name=nonumpa]
- 13:00 - 場佈 [排法](https://g0v.hackmd.io/9IEjq11XSwCyES_VFn8JEg#%E5%B0%8F%E8%81%9A%E6%AA%A2%E8%A8%8E) ![](https://docs.google.com/drawings/d/e/2PACX-1vSZhu49XCUS50miXVUNYO9taFST862ov-EY3zD03qcPy9edM8qU5Q6QpCTFRpzQBwcCQX78pblmzi39/pub?w=943&h=652)
  - 桌子一邊 4 張椅子
  - [ ] 簽到（問飲料）
  - [ ] 排桌子椅子 
  - [ ] 投影位置？
  - [ ] 麥克風
  - [ ] 延長線佈置
  - [ ] 門口黏引導牌
  - [ ] WIFI
      - [ ] 佈機，手機 USB 選擇網路分享，等待白燈亮
      - [ ] 用 ASUS Device Discovery 確認可連線到 ASUS
  - [ ] 投影的電腦用 google chrome 開好
    - [ ] Google Chrome tab: [投影片](https://docs.google.com/presentation/d/1N9DxoN1NuxdtQILkcV67y_q8EM8CJF5GhoYLcCKFpAc/edit)
    - [ ] Google Chrome tab: [Bignum](https://cofacts.github.io/community-builder/#/bignum/setup)
- [ ] browser tabs
    - [ ] Google Chrome tab: [KKTIX](https://cofacts.kktix.cc/events/cofactseditor50)
    - [ ] Google Chrome tab: [Slido admin](https://admin.sli.do/event/rFQZd27cVvgEMyJAgv4BqT/polls)
    - [ ] Google Chrome tab: [Slido](https://wall.sli.do/event/rFQZd27cVvgEMyJAgv4BqT/?section=215e56d0-a002-4b7e-9bf0-c58acbacc9bf)
    - [ ] Google Chrome tab: [開場影片](https://www.youtube.com/playlist?list=PLz8KCDL90tNWn16J2xBzl53imUiDbNOzs)
    - [ ] BGM
    - [ ] Analytics
- 14:00 - 14:20 開場
    - 放[長影片](https://www.youtube.com/playlist?list=PLz8KCDL90tNWn16J2xBzl53imUiDbNOzs) 8min
    - 場地、Slido、Cofacts 機器人系統簡介
- 14:20 - 14:40：引導註冊網站、介紹評價現有回應
- 14:40 - 14:50：實作評價
    - 讓大家從網站找訊息按讚
- 14:50 - 15:10 介紹補充資訊
- 15:10 - 15:40 實作補充資訊、自我介紹、休息
    - 閒聊「看到覺得最好的回應、覺得哪裡好」
- 15:40 - 16:10：介紹撰寫新回應
- 16:10 - 16:40：實作撰寫新回應
    - 大家從網站挑選「一篇」覺得最有興趣的回
- 16:40 - 17:00 介紹 RSS、社群、合照

## nDX

https://ndx.dta.tw/google-%e5%8f%b0%e7%81%a3%e6%96%b0%e8%81%9e%e6%95%b8%e4%bd%8d%e5%85%b1%e6%a6%ae%e5%9f%ba%e9%87%91%e6%94%af%e6%8c%81%e4%b9%8b-ndx-%e6%95%b8%e4%bd%8d%e5%89%b5%e6%96%b0%e7%8d%8e%e5%8a%a9%e8%a8%88-2/

Cofacts.ai：打造多代理人 AI 陪伴公民查核者對抗網路不實訊息 - 台灣實科協會

beta.cofacts.ai - code: https://github.com/cofacts/beta-ai/blob/master/cofacts_ai/agent.py
- Langfuse 接好了
- Transfer to agent 會導致「整個控制權會換成另一個 agent」的問題：https://mrorz.github.io/adk-session-json-viewer/
- 改寫 prompt
    - 簡化邏輯，不要區分「初學者」和「專家」
    - proofreader 會通通換成 AgentTool
- 招募 Beta AI Users (Cloudflare access control / policies)

焦點小組運作
- 換 term？

社群工作坊與國際交流
- 國內分享
- 國際交流

## DB Migration 

已修正大部分測試程式的 error 
下禮拜有機會可以有個版本可以讓大家試玩

## 5 月 MG 演講

114學年下學期清華通識主題座談會活動流程
（一） 時間：115年5月13日（三）19:00-21:00
（二） 地點：旺宏館國際會議廳
（三） 主題：人文社會AI的協作創新
（四） 講者：李梅君(中研院民族所)、王道維(清大物理系)

清華通識教育中心
https://cge.site.nthu.edu.tw/p/403-1573-10094-1.php?Lang=zh-tw
類似活動： https://cge.site.nthu.edu.tw/p/406-1573-275239,r10094.php?Lang=zh-tw
邀請者林文源老師同時也是學界「公共化 AI」計畫的主持人: https://nthuhssai.site.nthu.edu.tw/p/412-1535-18453.php

MG：曾用 cofacts 的資料庫、結合《資訊判讀力》一書的方法，製作一份事實查核的學習單。
- 該學習單收錄在[「人文社會課程之生成式AI指令集」](https://nthuhssai.site.nthu.edu.tw/p/404-1535-254188.php)種子範例網頁
- 我會再次修改，用在114學年於台大人類學系開設的「數位人類學」課程中，作為期中作業。
