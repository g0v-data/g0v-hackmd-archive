# 豆腐小魚 0325 會議
會議主題：vTaiwan 網站更新

## 今天要處理的事情
- 週六的簡報要講什麼
- 網站大概的設計架構
- 討論會使用的方法
- 大概理一下預算規劃
- 確認一下資金池的要求

## 資金池提案資格與相關義務說明
【青年世代】團隊成員須至少半數以上為青年世代（35歲以下）。
【回應社會需求，並開源專案成果】專案主題必須符合以下兩個條件：
請留意：若您的專案內容無法符合以下兩種特質，主辦單位揪松團有權力具有婉拒您參加本次資金池計畫，請您見諒 🙏。
條件一：回應社會問題及公眾需求。
您可以參考總統盃黑客松評選標準：https://presidential-hackathon.taiwan.gov.tw/index.html#id-3
您可以參考聯合國永續發展目標項目：https://globalgoals.tw/
條件二：專案成果採用開源授權方式。
輔助您選擇程式碼的開源授權條款：https://www.facebook.com/share/p/1KUv2S2D8U/
輔助您選擇文件圖像的 Creative Commons 授權方案：https://g0v.github.io/cchelper/
【您必須全程參加 3/29 週六於臺南市舉辦的 g0v 黑客松】
請務必完成報名 3/29 g0v 友愛青年黑客松活動
活動日期：2025 年 03 月 29 日（六）10:00-17:00
活動地點：好想工作室
活動地址：台南市中西區友愛街117號2樓
Google Map：https://maps.app.goo.gl/dhMkit25oyprxNXz9
活動報名網址：https://g0v-jothon.kktix.cc/events/g0v-hackath66n
請提前於 3/29 活動提案列表中的三分鐘提案區，填上您的專案內容。
提案列表網址：https://docs.google.com/spreadsheets/d/18lc-knz8u9f1Cwxa6vlqBUU1zZKnK-ODBlvQb0Vnld0/edit?usp=sharing
當天的提案三分鐘時段中，您需要說明專案與團隊簡介、專案目標與期程、所需資源、預期成果、影響力、成果分享方式 (Open Source 或 Creative Commons 授權)，向大家介紹你們的專案 (拉票！)。
當天請在黑客松現場，設置你們的專案工作區，可以當作專案工作小聚，也可以向大家介紹專案內容細節，拉人入坑！
16:00 現場來領獎金！

## 資金池提案價格試算
| 服務                      | 計畫                | 月訂閱費 | 預估額外使用費 | 每月合計     | 備註 | 價格連結 |
|---------------------------|---------------------|----------:|----------------:|--------------:|------|----------|
| **Zeabur**                | Developer Plan      | $5.00     | $5.60           | **$10.60**    | 包含 $5 免費用量/月；RAM (0.5 GB × $10.80/GB‑月) + 網路 (50 GB × $0.10/GB) + 儲存 (1 GB × $0.20/月) | [Zeabur 價格](https://zeabur.com/zh-TW/pricing) |
| **Decap CMS**             | 無                  | $0        | $0              | $0            | 開源、免費 | — |
| **Astro**                 | 無                  | $0        | $0              | $0            | 開源、免費 | — |
| **Windsurf (Codeium)**    | Pro Ultimate        | $60.00    | —               | **$60.00**    | 無限 User Prompt；3,000 Flow Action credits/月 | [Codeium 價格](https://codeium.com/pricing) |

## 網站需求（from [議題小聚](https://g0v.hackmd.io/@Pno233SAS8G5UfL5OvSRmA/S1V39jMnJx)）
- 做一個 landing page 連結其他的功能
- 中英文結合，而不是放在不同的網頁上
- 懂程式與不懂程式的人都能夠更新
- 上面可以放活動資訊、相關的專案連結、更多想要達成的願景（如上面）
- 需要放的資訊
    - 想要了解 vTaiwan 的人需要知道的
        - vTaiwan 基本介紹
            - vTaiwan 的歷史
            - 大事記：可以把現在已經 Archive 的議題變成時間軸之類的 [name=joey]
            - vTaiwan 的程序有何特殊之處？
        - 如何參與
        - vTaiwan FAQ 
        - 共筆連結
    - 專案進度
        - 每週小松
        - 議題小聚
            - 最近在處理的議題
            - 議題小聚的活動資訊
        - 其他專案的共筆連結
            - 專案案例資料表 airtable

總結：
- 需要有雙語網頁
- 有易於閱讀且包含重要資訊的前端 landing page
    - 活動資訊
    - 專案連結
    - 小聚共筆
    - 如何參與
    - FAQ
- 類似 blog 的文章發佈管理後台
- vTaiwan 大事記

## vTaiwan 官方網站架構圖
```
vtaiwan-website/
├── 首頁
│   ├── 語言切換（繁體中文 / English）
│   ├── 最新活動資訊
│   ├── 精選專案連結
│   ├── 小聚共筆區塊（前一期紀錄摘要 + 連結）
│   ├── 如何參與（簡要引導）
│   ├── 常見問答（FAQ 精選）
│   └── 導覽連結至其他主要頁面
├── 專案介紹
│   ├── 專案列表
│   └── 單一專案詳情頁（背景說明、專案進度、參與方式）
├── 小聚共筆
│   ├── 小聚紀錄列表（依日期時間線排序）
│   └── 單一共筆頁（嵌入 HackMD 或內嵌內容）
├── 如何參與
│   ├── vTaiwan 參與方式介紹
│   ├── 工具與平台介紹（如 Discourse, pol.is 等）
│   └── 加入我們（Slack、Discord、Email 等資訊）
├── FAQ
│   └── 常見問題分類與解答
├── 大事記
│   ├── 年表檢視（以年/月為節點）
│   └── 重大事件相關專案連結
├── 最新消息／部落格
│   ├── 文章列表（依發佈日期排序）
│   └── 單一文章頁面（可切換語言）
├── 關於我們
│   ├── vTaiwan 簡介
│   ├── 團隊與貢獻者
│   ├── 媒體報導
│   └── 合作單位
└── 後台管理系統（僅管理員）
    ├── 登入頁
    ├── 文章管理（新增／編輯／刪除）
    ├── 小聚紀錄管理
    ├── 活動資訊管理
    └── FAQ 管理
```

## 網站方案

### Astro + Decap CMS + Zeabur
```
vtaiwan-website/
├── public/                             # 靜態資源目錄
│   ├── admin/                          # Decap CMS 管理介面
│   │   ├── config.yml                  # Decap CMS 配置檔案
│   │   └── index.html                  # Decap CMS 入口頁面
│   ├── assets/                         # 公共資源，如字體、圖示等
│   └── favicon.ico                     # 網站圖標
├── src/                                # 原始碼目錄
│   ├── pages/                          # 頁面路由
│   │   ├── index.astro                 # 首頁
│   │   ├── projects/
│   │   │   ├── index.astro             # 專案列表頁
│   │   │   └── [project].astro         # 動態路由：單一專案詳情頁
│   │   ├── meetups/
│   │   │   ├── index.astro             # 小聚共筆列表頁
│   │   │   └── [meetup].astro          # 動態路由：單一小聚共筆頁
│   │   ├── join.astro                  # 如何參與頁面
│   │   ├── faq.astro                   # 常見問答頁面
│   │   ├── timeline.astro              # 大事記頁面
│   │   ├── blog/
│   │   │   ├── index.astro             # 部落格列表頁
│   │   │   └── [post].astro            # 動態路由：單篇文章頁面
│   │   └── about.astro                 # 關於我們頁面
│   ├── components/                     # 可重複使用的元件
│   │   ├── Header.astro                # 頁首元件
│   │   ├── Footer.astro                # 頁尾元件
│   │   └── LanguageSwitcher.astro      # 語言切換元件
│   ├── layouts/                        # 版面配置
│   │   ├── BaseLayout.astro            # 基礎佈局
│   │   ├── ProjectLayout.astro         # 專案頁面佈局
│   │   └── BlogLayout.astro            # 部落格頁面佈局
│   ├── content/                        # 內容資料夾
│   │   ├── projects/                   # 專案內容
│   │   │   └── [project].md            # 單一專案的 Markdown 檔案
│   │   ├── meetups/                    # 小聚共筆內容
│   │   │   └── [meetup].md             # 單一小聚的 Markdown 檔案
│   │   ├── blog/                       # 部落格文章
│   │   │   └── [post].md               # 單篇文章的 Markdown 檔案
│   │   └── faq/                        # 常見問答內容
│   │       └── [question].md           # 單一問答的 Markdown 檔案
│   ├── styles/                         # 樣式表
│   │   └── global.css                  # 全域樣式
│   └── assets/                         # 圖片等資源
│       ├── images/
│       │   └── [image-files]           # 圖片檔案
│       └── js/
│           └── [javascript-files]      # JavaScript 檔案
├── package.json                        # 專案依賴與腳本
├── astro.config.mjs                    # Astro 配置檔案
├── tsconfig.json                       # TypeScript 配置檔案
└── zeabur.json                         # Zeabur 部署配置檔案
```

## 經費評估