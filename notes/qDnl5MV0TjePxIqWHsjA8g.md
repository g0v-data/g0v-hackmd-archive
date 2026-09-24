---
tags: vTaiwan
---

# vTaiwan 工程季報｜夏季工程摘要

> 希望本工程季報可以讓社群更瞭解目前vTawian的工程進展，以及如何參與。我們特別需要「先期使用者」、「UI/UX設計師」和「前端工程師」的幫忙。
> [name=bestian]



> 資料範圍：本季成果依 [g0v／vTaiwan Project #2 的 Previous iteration View](https://github.com/orgs/g0v/projects/2/views/8)，第 5 節展望依 [Current iteration View](https://github.com/orgs/g0v/projects/2/views/3)；查閱時間：2026-09-24。「夏季」是本季報的名稱，工作範圍以 `iteration:@previous` 為準，**時間範圍07/01~09/22**。
>
> [name=由GPT-6 sol整理，Bestian細修]

## 本季主線：把分散的審議功能接成可參與的流程

本期工作從主站的整體視覺與資訊架構出發，延伸到 Civic Talk 的議題探索、閱讀與發言，再處理內容查核、後台治理與會議支援。幾個儲存庫的改動可以連成同一條使用者路徑：**看見議題 → 理解議題與平台 → 形成並分享意見 → 由志願者和管理者維護討論品質**。這是對本期卡片的編輯性歸納，而非單一議題宣稱已完成整套流程。

## 1. 主站新視覺從分支進入主線，並連往議題討論

主站的 [2026 新視覺工作](https://github.com/g0v/vue.vTaiwan-neo/issues/133)以設計稿為基礎，經由 [PR #154](https://github.com/g0v/vue.vTaiwan-neo/pull/154)合併至 `master`。合併摘要列出 FAQ、Topics、首頁議題、Meetups 等既有路由的視覺搬移，共用頁面元件、繁中／英／日介面及可及性狀態，同時保留原有資料來源與會議行事曆。這是一項跨頁面的整合工作，並非只替首頁換皮。

新介面也開始指向實際的審議入口：[「提案討論」頁加入 Civic Talk 連結](https://github.com/g0v/vue.vTaiwan-neo/issues/152)，讓訪客能從主站進入公共議題討論。議題卡的[分享與書籤操作](https://github.com/g0v/vTaiwan-hono/issues/113)、[首頁卡片顯示瀏覽人數](https://github.com/g0v/vue.vTaiwan-neo/issues/158)，以及[單一議題頁的標題與分享標題](https://github.com/g0v/vTaiwan-hono/issues/114)，則處理了「找到議題後能否保存、轉傳並辨識它」的細節。

新視覺完成整合後仍有回歸檢查：[逐字稿管理頁的複製與編輯大綱按鈕](https://github.com/g0v/vue.vTaiwan-neo/issues/161)曾因改版消失，本期卡片記錄了找回功能、對齊新樣式及維持管理員編輯權限的工作。它提醒我們，介面改版的驗收也包括原有工作流程是否可繼續使用。

## 2. Civic Talk 依參與角色整理議題，降低閱讀與發言門檻

議題首頁的排序從單一時間序列，轉向考慮使用者角色與議題階段。[角色切換與排序需求](https://github.com/g0v/civic-talk-hono/issues/77)區分公民與志願者：公民優先看到可參與的議題，志願者則能找到需要收集素材或彙整的工作；[後續排序調整](https://github.com/g0v/civic-talk-hono/issues/90)進一步明列「已發布、彙整中、素材收集中」在兩種角色下的優先順序。這使首頁同時能服務參與討論的人與協助備料的人。

閱讀體驗也有一組相互呼應的修正：[手機上的議題說明、素材與意見字級，以及全域字級切換](https://github.com/g0v/civic-talk-hono/issues/79)處理可讀性；[素材摘要與意見的安全 Markdown 呈現](https://github.com/g0v/civic-talk-hono/issues/82)兼顧格式與內容安全；[「民眾意見」改稱「公民意見」](https://github.com/g0v/civic-talk-hono/issues/85)使介面用語更貼近公共參與者的角色。這些工作分別碰到可及性、內容呈現與語意，但共同目的是讓議題內容更容易被理解與使用。

[「關於」頁的平台導覽](https://github.com/g0v/civic-talk-hono/issues/83)把流程說成關注議題、建立討論基礎、參與討論、分享觀點與意見綜整，也重新說明志願者如何運用自己的 AI 工具協作。議題說明仍將「對其他意見投票」與「意見綜整」標為研發中；季報不宜將它們寫成已交付功能。

## 3. 信任與治理：查核服務、誤判回饋、帳號權限

事實查核相關工作跨越兩個儲存庫：[fact-check-api 對 Civic Talk 網域開放 POST 跨來源請求](https://github.com/g0v/fact-check-api/issues/29)，使兩個服務可以銜接；[fact-check-core 納入 MyGoPen 來源白名單](https://github.com/g0v/fact-check-core/issues/9)，擴充可辨識的查核來源。這兩項是整合與來源管理的工作，不能直接推論每則內容已有可靠的自動判定。

[AI 查核誤擋新聞的回報](https://github.com/g0v/civic-talk-hono/issues/89)尤其值得保留在摘要中：議題記錄中央社新聞因日期與未來產品資訊而被阻擋的例子。View 將此卡列於 Done，但季報仍應把它視為查核機制須持續量測誤判、提供複核與申訴路徑的訊號，避免把「阻擋較多」誤認為「查核較好」。

另一條治理工作是 [vTaiwan-hono 的停權／解除停權 PR](https://github.com/g0v/vTaiwan-hono/pull/78)：它加入後台操作、停權理由與日誌顯示，並在應用權限層阻止被停權帳號繼續使用管理、會議與轉錄功能。PR 已合併到 `feat/better-auth` 分支，附有程式檢查與測試紀錄；其清單中的部分本機整合驗收仍未勾選，因此本摘要只確認合併與設計範圍，不宣稱所有部署情境已完成驗證。

## 4. 工程與審議活動同步推進

[9/11 審議會的工作卡](https://github.com/g0v/vTaiwan-meetings/issues/6)記錄會前準備，包含 Slido 調整的子議題。它與上述網站功能不同，卻說明工程並非孤立的產品開發：線上議題整理、會議互動與後續意見呈現需要互相銜接。該卡描述較簡略，無法據此推論活動成效或參與人數。

## 5. 秋季展望

從 [Current iteration View](https://github.com/orgs/g0v/projects/2/views/3) 來看，下一階段的重心，是讓夏季建立的「看見議題、閱讀意見」路徑，延伸成**表達立場、看見分歧、取得綜整**的審議循環。[公民意見投票](https://github.com/g0v/civic-talk-hono/issues/107)已結案，採同意、不同意與略過的三態設計；[廣泛傾聽實驗](https://github.com/g0v/civic-talk-hono/issues/41)也列為完成。但[意見綜整功能](https://github.com/g0v/civic-talk-hono/issues/113)仍是待實作工作：規劃以 AI 綜整與圖像分群呈現意見，並引導下載相容的 CSV，到 Sensemaker 產生進階分析報告。[Sensemaker 首頁的匯入說明](https://github.com/g0v/sensemaker-frontend/issues/72)亦待加入 Civic Talk，讓資料出口與分析入口連成一條可理解的路徑。

參與門檻方面，[Civic Talk 的手機優先版面](https://github.com/g0v/civic-talk-hono/issues/76)與[頁面版型優化](https://github.com/g0v/civic-talk-hono/issues/4)持續推進；[投稿表單的 Markdown 預覽與字數計數](https://github.com/g0v/civic-talk-hono/issues/106)則希望讓投稿者在送出前看見內容的實際呈現。主站重構線的[實機測試](https://github.com/g0v/vTaiwan-hono/issues/93)已涵蓋電腦、手機及橫放等情境，仍有平板待測；手機視訊加入與工具列問題曾由測試者回報，並拆出後續議題。這些工作共同指向同一個驗收標準：一般人能否在自己的裝置上順利參與討論和會議，而不只是在桌機畫面上看到完整功能。

支撐這套流程的服務也要能長期運作。[素材提交前的自動查核](https://github.com/g0v/civic-talk-hono/issues/87)及 [fact-check-api 原型](https://github.com/g0v/fact-check-api/issues/5)已列為完成；接下來的[查核服務分層與 x402 守護機制](https://github.com/g0v/fact-check-api/issues/31)尚未全部完成，規劃讓 Civic Talk 透過 Service Binding 使用私有核心、示範入口受總量限制、公開 API 另設收費閘門，以兼顧可近性、成本與防濫用。工程協作上，[貢獻者自架 Cloudflare 測試環境的文件與設定](https://github.com/g0v/civic-talk-hono/issues/112)、[逐字稿校對](https://github.com/g0v/vTaiwan-meetings/issues/12)及[國際審議工具協作](https://github.com/g0v/vTaiwan-meetings/issues/5)也仍列於本迭代。這些是秋季看板的工作方向；未完成的卡片不應被寫成已交付或已上線的成果。

## 後續值得追蹤的銜接點

1. **跨站使用路徑**：從主站連到 Civic Talk 後，追蹤訪客是否找得到議題、看得懂各階段，並能返回或分享。[主站入口](https://github.com/g0v/vue.vTaiwan-neo/issues/152)與[角色排序](https://github.com/g0v/civic-talk-hono/issues/90)是同一條路徑的兩端。
2. **上線與驗收證據**：將看板 Done、程式碼合併、正式部署及人工驗收分別標示；尤其注意[停權整合驗收](https://github.com/g0v/vTaiwan-hono/pull/78)和[視覺改版後的後台操作](https://github.com/g0v/vue.vTaiwan-neo/issues/161)。
3. **查核的品質與救濟**：持續記錄[誤擋案例](https://github.com/g0v/civic-talk-hono/issues/89)與人工複核結果，讓查核服務保護討論品質，也保留合格內容進入討論的機會。


## 團隊貢獻與認領現況
> 包含有明確認領者的「已完成」和「已認領」的項目

https://github.com/orgs/g0v/projects/2/views/2

## 待認領事項

> 新參者友善的項目，會打上`good first issue`標籤，方便新參者辨識與認領，歡迎入坑參與貢獻，從做中學。不一定要寫code，做測試、提issue，參與工程討論也很歡迎。

https://github.com/orgs/g0v/projects/2/views/7

## 給先期使用者

秋季重點實測：**Civic Talk公民審議平台**

概念：https://civic.vtaiwan.tw/about

首頁：https://civic.vtaiwan.tw

議題區(錯誤回報與功能請求)：https://github.com/g0v/civic-talk-hono/issues