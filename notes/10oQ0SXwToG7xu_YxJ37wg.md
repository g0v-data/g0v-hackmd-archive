---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20250224 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API
#### :globe_with_meridians: Site
#### :robot_face: rumors-line-bot

### :rocket: Staging

Carried over from last week
- Internet archive logging 
- uploadMedia refactor 
- Gemini transcript https://github.com/cofacts/rumors-api/pull/359
- Gemini model & location selection https://github.com/cofacts/rumors-api/pull/361
- Badge related API

New
- Header that bypasses Cloudflare proxy-read timeout mechanism (not tested) https://github.com/cofacts/rumors-api/pull/362

#### :robot_face: rumors-line-bot

Carried over from last week
- LINE bot - long response handling https://github.com/cofacts/rumors-line-bot/pull/401
  - Fixed redis reply-token & batch handling

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [ ] 應可送出「全新影音訊息」
    - [ ] 同意送出訊息後就會送出訊息，並得到 AI reply


##### ⛔️ Release Blockers

##### 未竟項目
### :eye: Under review

## RightsCon & Satelite Events


- 2/22 (Sat) 大松：https://g0v-jothon.kktix.cc/events/g0v-hackath65n 
- ~~2/24 (一) Side-event 17:00~18:00 比鄰演講~~ 取消
- 2/25 (二) 9:00~10:00 NDI Panel
- 2/25 (二) 14:00 ~ 15:00 Cofacts 自己的 talk - ID # 23894 – “Crowd-sourced fact-checking in AI era - Lessons learned by Cofacts
  - 地點：South Lobby of the 2nd floor
  - 投影片：https://docs.google.com/presentation/d/1_FGSKvgP2jh9o_22FhKSuDWLI-cu4lY3u95PL5lVb9o/edit
- 2/26 (三) **早上**擺攤
- 2/26 (三) 12:45-13:45 大平台 ~~(Promote 攤位)~~
- 2/27 (四) 11:30~12:30
  - NiemanLab / Panel Discussion / Challenge around deepfake detection
- 2/27 (四) 12:45~13:45 ID # 25017 - Global Giants, Local Influence: The Role of International Social Media in Shaping National Discourse
  - 地點：201E

### Sessions we may participate

- ~~[2/23 (日) OCF sattlelite event](https://ooni-research.ocf.tw/docs/blog/2025/02/rightscon25-tor-tails-ooni/)~~
  - 活動日期：2025/02/23
  - 工作坊 14:00 – 17:30 如何使用 Tor 避開審查並匿名瀏覽
  - 工作坊 18:00 – 19:00 如何使用 OONI 偵測與觀察網路審查狀況
  - 演講座 19:30 – 21:00 Tor 在網路監控的世界中捍衛個人線上隱私權
- ~~2/23 (日) 3pm-6pm[【工作坊】打造韌性網路：動手實作「不需海纜」的網路](https://airtable.com/appWd48vvxh0VJS1D/shrLERQDlmu6j3jMz)~~
- 2/26 (三) DWeb panel 10:15~11:15 (Promote 攤位)
- 2/24~2/27 OCF＆司改會一起擺攤
    - 在餐廳外面

### 2/26 (三) 09:00~13:00 擺攤

人
- Johnson & Bil
- Stella & Yutin

時間
- 8:30 ~ 9:00 設攤
- 9:00 ~ 13:00 擺攤
- 13:00 前必須撤收完畢

空間
- 3F Networking Lounge https://www.rightscon.org/venue2025/#floor3 / https://www.ticc.com.tw/wSite/vr360/index.html
    - 16 號 ![](https://g0v.hackmd.io/_uploads/Hyl4CBKF5kl.png)

- ~~先在 1F Help Desk 報到，才知道在哪個 booth~~ 已報到
- 180 cm x 60 cm 桌子＋2 張折疊椅 ![](https://g0v.hackmd.io/_uploads/BJ8SItF9yx.png)
- 牆上不能貼東西
- 不一定有電，延長線自備
- 沒有推車與幫手，進場撤場都是手搬

材料

https://drive.google.com/drive/folders/1U-etbZSOiFzpXgOr0GtBxkwYKk666nni

- [ ] CCC 的 Cofacts 遊戲 (結合台灣宮廟文化體驗+假資訊)
    - [ ] 台灣花布 + 流水席用紅桌布
    - [ ] 神明版乖乖 + 神桌背板 (A3)
    - [ ] 電子詩籤+籤筒 (遊戲題目)
    - [ ] 題目感測裝置 (魔法陣/USB)+RBG 燈條 (USB)
    - [ ] 螢光燈條 (USB)
    - [ ] 筆電
    - [ ] 遊戲作答按鈕裝置 (ABCD/Yes,No)
    - [ ] 延長線
    - [ ] USB 豆腐頭
    - [ ] 其他擺飾物 (台灣意象小物 : 春聯、小點心)
    - [ ] 遊戲說明牌
    - [ ] 貢獻箱- 現場提供贊助Cofacts的帳戶或QRcode資訊 (不知道要放哪, 先列在這裡待會議討論。前情提要 : 在CCC有提供Donate箱, 做為下次CCC擺攤的籌備基金及購買禮品 )
- [x] 局部上光 bil 名片
  - [x] 加中文「比鄰」小字
- [x] 更新英文版網站 news
- [x] 文宣更新與印刷
  - [x] 英文（achoo）
    - 250 張起跳 http://www.soho8d.com.tw/Form2/F102.aspx?csubid=73
    - 要更新 QR code
    - 背面有疊影，需處理掉四色黑
  - [ ] 豆腐版
  - 借放在 OCF 攤位 & 自己攤位上
- [x] 宣傳用：Logo 貼紙（透明 or 長的）
- [ ] 投影片放在多頁的透明資料夾

## LLM Transcript update

Errors and mitigations

- LINE bot
    - node-fetch connection ends prematurely
    - may be caused by Cloudflare, because no error comes from rumors-api
    - causes infinite waiting on user side --> add error handing https://github.com/cofacts/rumors-line-bot/pull/403
- [Cloudflare](https://developers.cloudflare.com/fundamentals/reference/connection-limits/#between-cloudflare-and-origin-server)
    - Proxy Read Timeout 100s
    - Proxy Write Timeout 30s
    - Not configurable in our account.
    - Before Proxy Read Timeout, send an arbitrary header to pass the 100s read timeout: https://github.com/cofacts/rumors-api/pull/362
        - Tested by sleeping in POST /graphql; request still get cut on 100s even after a header is flushed on 90th second
  - It is hard to find a video that needs to process for more than 100 seconds......
    - Tried to use ffmpeg to stretch a video to 5 mins long (LINE upper limit). It's processed within 80 seconds.
- nginx proxy
    - `proxy_read_timeout`: Default 60s; production already at 240s
        - Causing [504 errors](https://developers.cloudflare.com/support/troubleshooting/cloudflare-errors/troubleshooting-cloudflare-5xx-errors/#502504-from-your-origin-web-server)
        - ✅ Moved staging timeout from default to also 240s: https://github.com/cofacts/rumors-deploy/pull/33
    - `proxy_send_timeout`: Defualt 60s; already bigger than Cloudflare's write timeout.
- rumors-api: `ListArticles` with transcript creation turned on
    - Weird error from Vertex AI SDK ![](https://g0v.hackmd.io/_uploads/SJyuoSd9ye.png)

Other thoughts
- Suggestions from Gemini: https://gemini.google.com/share/ebad8b428ac9
    - Many of them are total rewrite of the transfer protocol
- Bypass both nginx and LINE bot using docker-compose network
    - On production, TW LINE bot & API is in the same docker-compose network
    - On LINE bot may set `API_URL` to `http://api:5000/graphql` so that it connects directly through docker-compose
        - `API_URL` is only used on NodeJS
        - LIFF calls `/graphql` on LINE bot server, and LINE bot server connects to rumors-api via NodeJS as well (w/ schema stitching)
  - --> ✅ Changed `API_URL` config near 2025/02/23 15:40 on production, LIFF & bot continued working, logging confirmed that requests come from docker network ![](https://g0v.hackmd.io/_uploads/r1ed5V8_c1e.png)


