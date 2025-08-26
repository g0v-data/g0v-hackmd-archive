# 20250826 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- 線上出席：
- 實體出席：
- https://meet.google.com/mrz-dgrd-pri
:::

## 本次會議待追蹤項目 (由 2025/08/19 會議記錄結案)

No updates
*   **[Johnson]** 資訊安全權限設定
*   **CCPRIP - Analytics**: Opendata trend & LINE Bot usage 报表問題
*   **cofacts.ai**: Groundness Check agent 實作 (追蹤提案與文件)
*   **Claude Code Action**: 追蹤 Vertex AI service account 與其他 repo 的整合進度、credential issue (`https://github.com/cofacts/beta-ai/issues/6`)
*   **[nonumpa, mrorz]** LLM based Topic Classifier: 追蹤 bug 修復與 benchmark 結果
*   **[mrorz]** 確認 Johnson 家是否還有中文講義
    * 我忘記看了⋯⋯

Have updates (detail in the upcoming sections)
*   **url-resolver update**: 追蹤 Gemini 實驗、unfurl 整合與結果融合，並修復記憶體問題


## CCPRIP
### [Infra] Service issue
>  - `Cofacts monitor 🚨@g0v-tw` 多次發出 api.cofacts.tw, cofacts.tw, line-botx.cofacts.tw 等服務不穩定的警告。
>  - `nonumpa` 回報服務在 2025-08-23 約 10:50 掛掉，13:30 恢復，但 linebot 需要手動重啟。


### [Comm] url context tool experiment result

> Gemini API URL context: https://ai.google.dev/gemini-api/docs/url-context

- Ordinary blog post
    - ✅ URL resolver can get title & summary
    - ✅ Gemini can also get title & summary
    - Example: https://cofacts.tw/article/76yjwnzx9qm9 / [Result](https://langfuse.cofacts.tw/project/cm3e6a2190001fdga2ruendgd/traces/7ebfaa1e-5b1a-4aaa-8fdd-0a848161464c?timestamp=2025-08-24T16:39:13.787Z&display=details)
- News site with lots of distractions
    - ✅ URL resolver can get clean title & summary
    - ⚠️ Gemini can also get title, but summary has lots of distractions
    - Example: https://cofacts.tw/article/139675setu15r / [Result](https://langfuse.cofacts.tw/project/cm3e6a2190001fdga2ruendgd/traces/da093cd1-e86c-4bd2-841c-56e9c11320ac?timestamp=2025-08-24T16:34:37.935Z&display=details)
- Ordinary youtube video
    - ✅ URL resolver can get title & summary
    - ✅ Gemini can also get title & summary
    - Example: https://cofacts.tw/article/1idh7ltnohzfq / [Result](https://langfuse.cofacts.tw/project/cm3e6a2190001fdga2ruendgd/traces/51d266f7-85fe-4c8b-9541-9983de545d32?timestamp=2025-08-24T16:45:15.529Z&display=details)
- Youtube shorts
    - ✅ URL resolver can get title & part of the summary
    - ⚠️ Gemini may return empty response, but sometimes gets content
    - Example: https://cofacts.tw/article/28m55lnwpwceb / [Result](https://langfuse.cofacts.tw/project/cm3e6a2190001fdga2ruendgd/traces/365573e8-48dc-4437-a560-2eba8dc01a99?timestamp=2025-08-24T16:42:08.951Z&display=details)
    - Example 2: https://cofacts.tw/article/2ihuzwmxplo18 / [Result](https://langfuse.cofacts.tw/project/cm3e6a2190001fdga2ruendgd/traces/b3720ec3-f3a7-431b-bc6e-c41f3e6ae72b?timestamp=2025-08-24T16:25:44.977Z&display=details)
- Facebook video
    - ❌ URL resolver gets wrong title & summary (login required)
    - ✅ Gemini returns empty response (better behavior in this case)
    - Example: https://cofacts.tw/article/yc67zrv8v4ls / [Result](https://langfuse.cofacts.tw/project/cm3e6a2190001fdga2ruendgd/traces/3dd4453e-7709-403f-a281-93cdc5d202e4?timestamp=2025-08-24T16:41:19.392Z&display=details)
- Instagram Video
    - ✅ URL resolver gets title & some of the summary
    - ❌ Gemini returns empty response
    - Example: https://cofacts.tw/article/yr0j1lujgq84 / [Result](https://langfuse.cofacts.tw/project/cm3e6a2190001fdga2ruendgd/traces/9f5bfa2e-07f4-419a-a4fa-6209a8bbecb7?timestamp=2025-08-24T16:33:50.843Z&display=details)
- Tiktok Video
    - ❌ URL resolver errors
    - ✅ Gemini returns title & summary, **even after the video is taken down**
    - Example: https://cofacts.tw/reply/Fw4dYZgBngzKCCgMt4q7 / [Result](https://langfuse.cofacts.tw/project/cm3e6a2190001fdga2ruendgd/traces/2a642d42-190e-4a0c-8f8f-ba2dac4d7722?timestamp=2025-08-24T16:20:01.714Z&display=details)

---

Discussions

### [Comm] Youtube on Gemini experiment result

- Gemini API youtube support: https://ai.google.dev/gemini-api/docs/video-understanding#youtube
    - A feature since [March 2025](https://ai.google.dev/gemini-api/docs/changelog#03-12-2025)
- [Example]( https://aistudio.google.com/app/prompts?state=%7B%22ids%22:%5B%221EyV4zR3hEBLmVoXrnFjs3yV-GIzRAAuI%22%5D,%22action%22:%22open%22,%22userId%22:%22100298319366825427383%22,%22resourceKeys%22:%7B%7D%7D&usp=sharing)

How to integrate to Cofacts?
- 1 article can have multiple Youtube video links
- Should be indexed? 
    - Indexed in Cofacts only, or allow search engine to scrape (public)?
- Should allow edit?
