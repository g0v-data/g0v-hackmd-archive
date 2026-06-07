# 20260602 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：bil, mrorz, nonumpa, 
- 線上出席：
- https://meet.google.com/mrz-dgrd-pri
:::

## 上週待辦

### GCE Migration
- [ ] 跑幾週看穩定度，決定是否要再把 tw site 也搬進 GCE
- [ ] 跑幾個月看實際用到的運算量，決定 GCP committed use discount 怎麼買比較划算
    - 每個月 30X USD

### Kaggle
- [ ] 手動在 johnson 個人帳號上傳，並處理授權條款
- [ ] 研究自動化上傳
- [ ] 申請 Org 帳號

### cofacts.ai
> https://github.com/orgs/cofacts/projects/12/views/1


- https://github.com/cofacts/ai/issues/39
- [x] 處理多媒體 articles
  - [Issue #70: Handle multimedia articles in cofacts.ai](https://github.com/cofacts/ai/issues/70)
  - [PR #72: feat(adk): multimodal support for non-TEXT Cofacts articles](https://github.com/cofacts/ai/pull/72)
  - [PR #73: fix: forward user JWT to rumors-api so attachmentUrl is non-null for video/audio](https://github.com/cofacts/ai/pull/73)
  - [PR #76: Pass auth token via Authorization header + ContextVar instead of session stateDelta](https://github.com/cofacts/ai/pull/76)

### url-resolver

- 測過 cf-browser, url-context, url-resolver
- url-context 效果不太好
    - score 不高，沒有仔細看結果
    - 可能遇到 recitation error，cofacts.ai 也有遇到 [name=mrorz]
    - 所以可能不太合用
- `computer-use` 在 cloudflare browser rendering 上很容易 fail
    - timeout
    - 可能是打 gemini 的部分沒回應 etc
- 跑完做分類
    - JS 比較重的，固定跑 browser
    - 其他好爬的：用輕量的
    - 有些網站特別讓 AI 爬，有作的話可以走 https://blog.cloudflare.com/markdown-for-agents/

### 其他

**逐字稿功能修復**
- [PR #391: fix(CreateMediaArticle): generate transcript when AI response is missing](https://github.com/cofacts/rumors-api/pull/391)
- [PR #392: test(CreateMediaArticle): add createTranscript mock and fallback test](https://github.com/cofacts/rumors-api/pull/392)
- [Allow missing content-length](https://github.com/cofacts/media-manager/pull/12)

## 大松檢討

https://g0v.hackmd.io/@cofacts/meetings/https%3A%2F%2Fg0v.hackmd.io%2FhNNxb6m5Qy6as18Dt9AXdw

## 小聚籌辦

- 6/7 (日) 青職基地 1F
    - 上次在一樓的檢討<https://g0v.hackmd.io/J8vWYqIzRn687khHpPLQvw#%E5%B0%8F%E8%81%9A%E6%AA%A2%E8%A8%8E>
    - Impression count 是上次的 6 成，但 click through rate 差不多
    - 再送推播，這次
        - 拿掉前面的謠言，開門見山
        - 換成中午 12:30
- 週六早上
    - [x] KKTIX 行前通知：提醒時間、使用電腦而非手機
  > Hello 你好，
	>
	> 本週日就是 6 月 7 日查核志工培訓囉！
	>
	> 志工培訓需要大量查詢資料，請自備筆電 💻 與充電器 🔌 並帶著愉快的心情來參加。帶順手的平板也可以的！Cofacts 資料庫也有很多影音謠言，請自備耳機唷 🎧！
	>
	> 🕒 時間：06/07（日）14:00 - 17:00
	> 📍 地點：新北市青年局青職基地1樓 / 新北市板橋區民權路170號1樓(近板橋捷運站)
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
        - 增加 cofacts.ai 介紹
	- [x] 準備 Slido `#cofacts`
- 當日準備 / 攜帶
    - [ ] 樓下用的標語 - bil
    - [ ] **拍照用大布條** - bil
    - [ ] 貼紙 - orz, bil
    - [ ] 黏土 - orz
    - [ ] 手板 - bil
    - [ ] 講義 - bil
    - [ ] 一次性杯子 - bil
    - [ ] 延長線 - bil, nonumpa
        - 比鄰有 5 條
        - nonumpa 有 2 條
        - (Optional) 和揪松借
    - [ ] Wifi 機 - mrorz
        - [ ] rt-ax57 go
        - [ ] 電源線
    - [x] 多帶一條 type-c 公公線 for dongle 的電
    - [ ] 備用 wifi 機 [name=nonumpa]
- 13:00 - 場佈 
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
    - [ ] Google Chrome tab: [KKTIX](https://cofacts.kktix.cc/events/cofactseditor53)
    - [ ] Google Chrome tab: [Slido admin](https://admin.sli.do/event/rFQZd27cVvgEMyJAgv4BqT/polls)
    - [ ] Google Chrome tab: [Slido](https://wall.sli.do/event/rFQZd27cVvgEMyJAgv4BqT/?section=215e56d0-a002-4b7e-9bf0-c58acbacc9bf)
    - [ ] Google Chrome tab: [開場影片](https://www.youtube.com/playlist?list=PLz8KCDL90tNWn16J2xBzl53imUiDbNOzs)
    - [ ] BGM
    - [ ] Analytics
- 14:00 - 14:20 開場
    - 放[長影片](https://www.youtube.com/playlist?list=PLz8KCDL90tNWn16J2xBzl53imUiDbNOzs) 8min
    - 場地、Slido、Cofacts 機器人系統簡介
- 14:20 - 14:40：引導 註冊網站、介紹評價現有回應
- 14:40 - 14:50：實作評價
    - 讓大家從網站找訊息按讚
- 14:50 - 15:10 介紹補充資訊
- 15:10 - 15:40 實作補充資訊、自我介紹、休息
    - 閒聊「看到覺得最好的回應、覺得哪裡好」
- 15:40 - 16:10：介紹撰寫新回應
- 16:10 - 16:40：實作撰寫新回應
    - 大家從網站挑選「一篇」覺得最有興趣的回
- 16:40 - 17:00 介紹 RSS、社群、合照

# Cofacts AI 週會回顧：2026/5/22 – 6/2

> 資料來源：Langfuse (`langfuse.cofacts.tw`) sessions / traces / scores + git commit 歷史
> 期間：2026-05-22 ～ 2026-06-02

## 一、整體使用狀況

| 指標 | 數量 |
|------|------|
| Sessions | **55** |
| Traces | **115** |
| 使用者 feedback（`user-thumbs`）| **31**（扣除 3 筆測試 → 實質 **28**）|
| 👍 正面 | 13（實質 10）|
| 👎 負面 | 18 |

**每日 trace 分布**

```
5/22 ████████████ 12
5/23 ████████████████ 16
5/24 ████████████████ 16
5/25 █ 1
5/27 ██████████ 10
5/28 ██ 2
5/29 █ 1
5/30 ████████ 8
5/31 ███████████████████████████████████████████ 43   ← dogfooding 高峰
6/01 ██████ 6
```

> 5/31 是密集 dogfooding 日（43 traces、11 筆 feedback），也直接催生了 6/1 的大改版。

---

## 二、Prompt 迭代時間軸 vs. Feedback

下面把這兩週的 prompt 改動分成 6 個階段，並對應到「**觸發改動的 feedback**」與「**改動後的 feedback**」。整段期間呈現一條清楚的主線：**verifier / 出處可信度** 問題反覆出現，prompt 一路被收緊。

### 🟠 階段 0：基線（~5/23 下午前）

**這段期間的 feedback（全是負面，集中在影片）**
- 👎「verifier 沒看到 youtube short 內容，100% 完全錯誤」
- 👎「verifier does not respond」（×2）
- 👎「兩個影片明顯是同時拍攝，卻錯誤回報說兩則影片是 2024 年的，完全誤導 AI writer」
- 👎「建議往個人意見的方式說明，畢竟是醫療建議」
- 👍「語氣適合」

➡️ **直接催生 → 階段 1**：verifier 根本「看不到」YouTube 影片內容，只讀到 HTML，導致對影片的判斷全錯。

### 🟡 階段 1：YouTube 原生影片理解（5/23 18:03 – 5/24）

| commit | 內容 |
|--------|------|
| `3d68a5c` | verifier 將 YouTube URL 以 **FileData** 注入，讓 Gemini 直接「看」影片 |
| `15adc24` / `9d2f4ad` | 擴充 YouTube regex（`/shorts/`、`/live/`、`/embed/`、`/v/`）|
| `7c0b106` | 防止 training knowledge 滲漏與捏造引用 |
| `c17c19f` | FileData 注入同一個 user message |
| `d704bf7` | 中立影片 metadata 報告；investigator 也注入 FileData |

**改動後 feedback**
- 👍「可以被指正」👍「出處精準」👍「具有說服力」
- 👎「提供不存在的出處」 ← 引用捏造問題仍在

### 🟢 階段 2：強制 url_context + 三層報告（5/25）

| commit | 內容 |
|--------|------|
| `f5aed77` | YouTube URL **強制呼叫 url_context** 以取得 `uploadDate` |
| `f3700de` | verifier instruction 重構為「**三層報告**」：①頁面 metadata（uploadDate 必需）②上傳者 metadata ③影片可觀察內容 |

> 理由：舊影片可能被重新上傳，`uploadDate` 是判斷年份的唯一信號（呼應階段 0「2024 年」誤判）。

### 🔵 階段 3：模型 GA 升級（5/27）

| commit | 內容 |
|--------|------|
| `934ed37` | 4 個 proofreader 從 `gemini-3.1-flash-lite-preview` 換成 GA 版 `gemini-3.1-flash-lite` |

**這段期間 feedback（升級前的舊 prompt）**
- 👎「Verifier 沒有驗證影片和標題的相關性」
- 👎「叫 investigator 去看影片上傳日，但 **investigator 沒有 url context tool**」 ← 工具能力錯配
- 👎（無註解）

### 🟣 階段 4：型別/容錯強化（5/30 – 5/31）

| commit | 內容 |
|--------|------|
| `6f69093` | writer 加 `on_tool_error_callback`，工具失敗不再讓整輪崩潰 |
| `7bb9536`* | grounding metadata 改可選 |
| `299eb84` | 強化 `inject_youtube_filedata` |

**這段期間 feedback（5/31 dogfooding 高峰）**
- 👎「**回應文字與出處不符**」（×3）
- 👎「出處不足，claim 一大堆，就是只回 5 個出處？另外兩個 AI 找了那麼多出處，為何搞到 source 無法 fully cover claim？」
- 👎「沒用 verifier 查原始影片」
- 👍「出處精準」👍「出處精準/具有說服力/語氣適合/篇幅適中」（4 項全勾）

➡️ **直接催生 → 階段 5**：核心問題從「影片看不看得到」轉移到「**writer 引用了未經 verifier 確認的出處 / 出處 cover 不了所有 claim**」。

### 🔴 階段 5：Writer 紀律改革 + 出處覆蓋強制（6/1）★ 本期最重要

| commit | 內容 |
|--------|------|
| `7931d10` | **改善 writer orchestration 紀律 + source-coverage 強制**：`draft_factcheck_response` 新增 `claim_sources`，每個 claim 須對應 `source_url` 且 `verifier_confirmed=true` |
| `c33789b` | `claim_sources` URL 改為與 reference URL **精確比對**（非 substring）|
| `57934a8` | 放寬：允許平行呼叫工具，但**禁止 draft 與其他工具同輪** |
| `107743a` | 把 Working Discipline 規則收進單一 Orchestration Process |
| `0cb1a8a` | `grounding_supports` 從「證據」降級為「吵雜的候選提示」 |
| `adf784d` | **完全移除** investigator 輸出中的 `grounding_supports` |
| `b9d73d7` | 「Track editorial constraints」改用領域中立範例，避免 overfit |

**新增的核心紀律**：先看源再研究、維護 editorial constraints 清單、**沒有 verifier ✓ 的 claim 不准寫進 draft**、不准對已標 ✗ 的 claim 重送同一 URL。明確區分 **Investigator DISCOVERS vs. Verifier CONFIRMS**。

> `grounding_supports` 被移除的依據：Google grounding 嚴重過度歸因（平均 4.5 來源/句、最高 9 個），被過度引用的 claim 往往正是 verifier 最後標 ✗ 的 → 只有真的讀過頁面的 verifier 才是引文真正來源。

**改動後 feedback（全部正面，且直接點名新流程）**
- 👍「出處精準 — 1. Verifier is called at the first place 2. investigate & proofreader first 3. all claims are included in sources」
- 👍「具有說服力 — Nice use of verifier & proof readers」
- 👍「先選擇請 proofreader 再 investigate 滿好的」

✅ 三筆改版後 feedback 全為正面，且明確稱讚「verifier 先行」「所有 claim 都被出處覆蓋」——正是這次 prompt 改動的設計目標。

---

## 三、Feedback 主題彙整（實質 28 筆）

| 主題 | 出現次數 | 對應的 prompt 回應 |
|------|---------|-------------------|
| Verifier 看不到/沒驗證影片 | 5 | 階段 1 FileData 注入、階段 2 url_context |
| 影片日期誤判 | 1 | 階段 2 強制 uploadDate |
| 提供不存在/不符的出處 | 4 | 階段 5 `claim_sources` + verifier_confirmed gate |
| 出處覆蓋不足（claim 多、source 少）| 1 | 階段 5 source-coverage 強制 |
| 工具能力錯配（investigator 無 url_context）| 1 | 流程釐清 discover vs confirm |
| 語氣/篇幅/說服力正面肯定 | 多筆 👍 | — |

---

## 四、給週會的三個 takeaway

1. **問題重心已經轉移**：從「agent 能不能看到影片」（5/23–5/27）演進到「writer 會不會亂引用出處」（5/31–6/1）。Prompt 也從「擴充能力」轉向「**強制紀律 / 驗證閘道**」。
2. **6/1 大改版見效**：改版前 5/31 出現密集的「出處不符 / 覆蓋不足」負評；改版後同類 session 全數轉正，且使用者明確點名新流程的優點。
3. **feedback → prompt 的閉環很健康**：幾乎每一波負評都能對應到 24–72 小時內的具體 prompt commit，dogfooding 的回饋確實在驅動迭代。

---

### 附錄：完整 feedback 清單（依時間）

| 時間 | 評價 | Session | 註解 |
|------|:---:|---------|------|
| 5/22 15:27 | 👍 | 2ed734c7 | 語氣適合（測試）|
| 5/23 03:55 | 👎 | b66074f7 | 出處不足/資訊錯誤（測試）|
| 5/23 04:07 | 👍 | 3c245461 | test up（測試）|
| 5/23 05:25 | 👎 | b5d83023 | verifier 沒看到 youtube short，100% 錯誤 |
| 5/23 05:36 | 👎 | b5d83023 | — |
| 5/23 05:38 | 👎 | b5d83023 | verifier does not respond |
| 5/23 05:38 | 👎 | b5d83023 | verifier does not respond |
| 5/23 05:39 | 👎 | b5d83023 | 兩影片同時拍卻報 2024，誤導 writer |
| 5/23 15:26 | 👎 | 289c50f8 | 醫療建議宜以個人意見方式說明 |
| 5/23 15:34 | 👍 | 5ff85787 | 語氣適合 |
| 5/24 02:27 | 👍 | b5d83023 | 可以被指正 |
| 5/24 15:10 | 👍 | e5749a8b | 出處精準 |
| 5/24 15:39 | 👍 | 9143f84d | 具有說服力 |
| 5/24 15:48 | 👎 | 6d81a32b | 提供不存在的出處 |
| 5/27 12:47 | 👎 | da1c2dce | verifier 沒驗證影片和標題相關性 |
| 5/27 12:52 | 👎 | da1c2dce | investigator 沒有 url context tool |
| 5/27 13:02 | 👎 | da1c2dce | — |
| 5/29 10:31 | 👍 | 8ba804f0 | 語氣適合 |
| 5/30 06:50 | 👎 | fcb16d6f | （空）|
| 5/31 04:56 | 👎 | 240aa16e | 沒用 verifier 查原始影片 |
| 5/31 05:25 | 👍 | 02d6a67e | 出處精準 |
| 5/31 05:34 | 👎 | 33f80fed | （空）|
| 5/31 06:39 | 👍 | 88a2af3c | 出處精準/說服力/語氣/篇幅 |
| 5/31 07:42 | 👍 | 040960fb | — |
| 5/31 13:48 | 👎 | ebc732b2 | 回應文字與出處不符 |
| 5/31 13:48 | 👎 | ebc732b2 | 回應文字與出處不符 |
| 5/31 14:05 | 👎 | 1878006f | 回應文字與出處不符 |
| 5/31 14:54 | 👎 | 2d97c04f | 出處不足，claim 多卻只回 5 個出處 |
| 6/01 15:12 | 👍 | 8d667352 | Verifier 先行、all claims included in sources |
| 6/01 15:14 | 👍 | 09d18a1b | Nice use of verifier & proof readers |
| 6/01 15:15 | 👍 | d6d291df | 先 proofreader 再 investigate 滿好的 |



---

# Cofacts 狀態報告（2026-05-22 ～ 2026-06-02）    

### 一、GCE 主機（cofacts-prod）指標

#### 每日資源使用率（格式：min | avg | p95 | max）

| 日期  | CPU                                  | Mem                                  | Swap                            |
| ----- | ------------------------------------ | ------------------------------------ | ------------------------------- |
| 05-25 | 17.5% \| 31.3% \| 51.5% \| **99.9%** | 51.3% \| 56.4% \| 60.8% \| 73.7%     | 99.7% \| 99.9% \| 100% \| 100%  |
| 05-26 | 11.8% \| 27.0% \| 40.5% \| **91.1%** | 51.5% \| 55.5% \| 58.4% \| 65.6%     | 99.8% \| 99.9% \| 100% \| 100%  |
| 05-27 | 13.1% \| 22.0% \| 29.1% \| 46.8%     | 51.8% \| 55.2% \| 57.3% \| 58.6%     | 99.9% \| 100.0% \| 100% \| 100% |
| 05-28 | 16.5% \| 26.4% \| 36.4% \| 47.3%     | 52.4% \| 55.9% \| 58.4% \| 68.5%     | 99.9% \| 100.0% \| 100% \| 100% |
| 05-29 | 16.0% \| 25.9% \| 40.7% \| 48.6%     | 51.6% \| 55.8% \| 58.0% \| 60.3%     | 99.3% \| 99.9% \| 100% \| 100%  |
| 05-30 | 15.7% \| 27.5% \| 43.3% \| 46.8%     | 52.4% \| 56.1% \| 58.2% \| **74.8%** | 98.1% \| 99.6% \| 100% \| 100%  |
| 05-31 | 16.5% \| 24.4% \| 34.8% \| 42.0%     | 53.2% \| 55.8% \| 57.6% \| **76.4%** | 99.6% \| 100.0% \| 100% \| 100% |
| 06-01 | 13.9% \| 22.2% \| 36.7% \| 46.0%     | 52.0% \| 55.5% \| 58.1% \| 58.6%     | 99.7% \| 100.0% \| 100% \| 100% |
| 06-02 | 19.1% \| 28.6% \| 40.3% \| 40.4%     | 53.7% \| 55.9% \| 58.2% \| 58.3%     | 99.9% \| 100.0% \| 100% \| 100% |

**目前即時狀態：** 已開機 26 天 | RAM 18GB / 31GB (58%) | Swap **4.0GB / 4.0GB（幾乎全滿）** | 磁碟 44G / 67G (66%)

---

### 二、GCE 程序資源（Top 消費者）

#### 記憶體（RSS）

| 程序                                       | 一般用量（avg）   | 穩定性                 | 備註                                                 |
| ------------------------------------------ | ----------------- | ---------------------- | ---------------------------------------------------- |
| **Elasticsearch**                          | ~15,400–15,550 MB | 穩定（std ~50–150）    | 最大消費者，佔實體記憶體約一半                       |
| **node /srv/www/server.js**（API）         | ~400–470 MB       | 不穩定（std ~115–149） | 05-24、05-25 峰值高達 **2,326 MB**，05-27 後恢復正常 |
| **node /srv/www/build/index.js**（worker） | ~150–180 MB       | 穩定（std ~4–12）      | 05-24、05-25 峰值高達 **2,227 MB**，05-27 後恢復正常 |
| **adk api_server**（cofacts-ai）           | ~230–260 MB       | 穩定（std ~0–26）      | 近期呈緩升趨勢，但仍合理                             |

#### CPU（單位：ms CPU time / 小時，數值越大越耗 CPU）

| 程序                    | 一般用量（avg）  | 穩定性   | 備註                                       |
| ----------------------- | ---------------- | -------- | ------------------------------------------ |
| **Elasticsearch**       | ~360,000–540,000 | 中等波動 | 05-24 峰值 1,108,799（約 1.1 倍 CPU 核心） |
| **node server.js**      | ~240,000–423,000 | 高波動   | 05-24 峰值 1,054,889，05-27 後大幅下降     |
| **node build/index.js** | ~148,000–194,000 | 中等波動 | 走勢與 server.js 一致                      |
| **cloudflared**         | ~26,000–38,000   | 穩定     | 正常                                       |

> **重要發現**：05-24（週六）～05-25（週日）出現顯著 CPU 與記憶體峰值，Elasticsearch 和 Node.js 同步飆升。Swap 記憶體長期接近 100% 已是長期趨勢。

---

### 三、Cloud Run 服務指標

#### CPU（單位：vCPU 比例，1.0 = 1 個 vCPU 滿載）

| 服務                | 正常範圍（p50） | 穩定性（p95 / p99）                 | 備註                               |
| ------------------- | --------------- | ----------------------------------- | ---------------------------------- |
| **site-tw**         | 0.09–0.16       | p95 ~0.82–0.90 / p99 ~0.95–**1.01** | 尖峰時 CPU 接近上限                |
| **cofacts-ai**      | ~0.015（閒置）  | p95 ~0.12–0.36 / p99 up to **0.44** | 處理 AI 請求時有明顯爆發，整體正常 |
| **site-staging-\*** | 非常低          | 偶有短暫爆發                        | 正常（測試環境）                   |
| **line-bot-en/ja**  | ~0.005–0.008    | p99 ~0.10–0.31                      | 正常                               |

#### 記憶體（佔分配上限的比例）

| 服務                   | 正常範圍（p50） | 穩定性（p99）      | 備註                           |
| ---------------------- | --------------- | ------------------ | ------------------------------ |
| **site-tw**            | 76–81%          | **~100% 超過上限** | ⚠️ 記憶體極為緊張，有 OOM 風險 |
| **site-staging-tw**    | 72–91%          | ~98–100%           | 同樣接近上限                   |
| **site-staging-ja/en** | 70–87%          | ~80–98%            | 偏高                           |
| **cofacts-ai**         | ~5.5%           | ~6–10%             | 非常充裕                       |
| **line-bot-en/ja**     | ~37–42%         | ~39–44%            | 正常                           |

#### 網路輸出（每日）

| 服務                | 一般每日流量               | 備註                                       |
| ------------------- | -------------------------- | ------------------------------------------ |
| **site-tw**         | 6.1–7.7 GB                 | 主要流量來源，06-02 僅 1.58 GB（當天部分） |
| **cofacts-ai**      | 極不規律（48 KB ～ 54 MB） | 依 AI 請求頻率而定                         |
| **site-staging-ja** | 11–56 MB                   | 偶有較高的測試活動                         |

---

### 四、重點摘要與建議

| 項目               | 狀態       | 說明                                             |
| ------------------ | ---------- | ------------------------------------------------ |
| GCE CPU            | 正常       | 平均 22–31%，偶有峰值但已恢復                    |
| GCE RAM            | 注意       | 物理記憶體 58%，**Swap 持續接近 100%**，長期壓力 |
| GCE 磁碟           | 正常       | 66%，尚有餘裕                                    |
| 05-24/25 異常事件  | 已恢復     | CPU/記憶體同步飆升，05-27 後恢復正常，原因待查   |
| **site-tw 記憶體** | ⚠️ 警告    | Cloud Run p99 超過 100% 限制，建議增加記憶體配額 |
| cofacts-ai         | 正常       | 06-02 02:03 有新部署                             |
| Cloud Run 服務     | 全部運行中 | 11 個服務均健康（✔）                             |

**主要建議：**
1. **site-tw Cloud Run 記憶體不足**：p99 持續超限，建議調高記憶體上限以避免 OOM 重啟
2. **GCE Swap 滿載**：長期問題，建議評估擴充實體記憶體或調整 Elasticsearch 的 JVM heap 設定
    - Elasticsearch 吃掉 Swap 的 96%（3.89 GB），因為 JVM heap（16 GB）+ off-heap（最高 8 GB）理論需求超過 `mem_limit: 22g`
    - `memswap_limit: 22g`（與 `mem_limit` 相同）原本應禁用 Swap，但因 Docker 29.x 在 cgroupv2 上的 bug，`memory.swap.max` 未被正確設定，形同無效
    - **建議：** 在 `db` 服務加上 `bootstrap.memory_lock: true` + `ulimits.memlock: -1`，從 OS 層鎖定記憶體，不依賴 Docker cgroup。
4. **05-24/25 異常峰值**：建議調查當天是否有異常流量、爬蟲攻擊或排程任務觸發，以免未來重演
    - Cloudflare 上看不出理由
    - p95 仍在正常值，只有在 max 時 >90%，不需要擔心

### 補充：JVM 記憶體理論需求的原理

Elasticsearch 的記憶體分成兩塊：

**1. JVM Heap（`-Xms16g -Xmx16g`）**
Java 物件存放的地方，包含 ES 的 cache、index metadata 等。上限設死 16 GB，加上 `-XX:+AlwaysPreTouch` 啟動時就會把這 16 GB 全部映射進實體記憶體。

**2. Off-heap（`MaxDirectMemorySize=8g`）**
JVM Heap 以外、但同樣佔用實體記憶體的空間，主要是：
- Lucene 用 `mmap` 把 index 檔案映射到記憶體（讓 OS 管理 page cache）
- Netty 的 direct byte buffer（網路 I/O 用）

這 8 GB 上限是軟性的，預設是 heap 的一半（因此在 Cofacts 上是 16GB 的一半）實際用多少由 OS 決定，但加上 JVM overhead（thread stack、metaspace 等）數百 MB，理論峰值約 **24+ GB**。

而 `mem_limit: 22g` 設了 22 GB 的硬上限 → **缺口約 2–4 GB 被 OS 擠出去用 Swap**，這和實際觀察到的 3.9 GB swap 完全吻合。

#### 建議

Heap（16g）+ Direct Memory（8g）= 24g，但 JVM 本身還有額外 overhead：thread stacks、metaspace、code cache 等，實際上再多佔 500MB～1GB。所以 `mem_limit: 24g` 設完還是可能輕微超限。

再來，即使把 `mem_limit` 調到 25-26g，`memswap_limit` 的 Docker cgroupv2 bug 還在——`memory.swap.max` 仍然會是 `max`，ES 還是可以用 Swap。

所以單靠調 `mem_limit` 只治標、不治本。**`bootstrap.memory_lock: true`** 才是根本解，它讓 OS 直接把 ES 的記憶體頁釘住，完全不走 Swap，不依賴 cgroup accounting。

如果你們要兩個都做：`mem_limit: 26g`（給 JVM overhead 留空間）+ `bootstrap.memory_lock: true`，這樣最穩。

```yaml=
db:
  image: docker.elastic.co/elasticsearch/elasticsearch:9.3.2
  mem_limit: 26g
  memswap_limit: 26g
  ulimits:
    memlock:
      soft: -1
      hard: -1
  environment:
    - discovery.type=single-node
    - ES_JAVA_OPTS=-Xms16g -Xmx16g
    - xpack.security.enabled=false
    - bootstrap.memory_lock=true
  # ... 其餘不變
```
