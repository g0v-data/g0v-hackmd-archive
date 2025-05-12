---
tags: vtaiwan 
---
# 20250514 小松
時間 Time ：19:00 - 20:00
地點 Location ：線上 Online
參與者 Participants:
線上參與連結 / Link：https://meet.jit.si/vtaiwan

### 本週分享
- 議題分享樹狀圖 [name=josh]

## 自我介紹與新手導覽
- [新手簡報](https://docs.google.com/presentation/d/1ELAVIpaPVCmAx7nq-7e8-SVrckZ4ohRwn3V-TSpe78U/edit?usp=sharing)
### 自我介紹

## 小小的分享
- 專案管理頁面
- 

## 5/23 議題小聚
![](https://g0v.hackmd.io/_uploads/Bye14G5kxgl.png)
- polis 連結 (見上圖)
- [facebook貼文](https://www.facebook.com/vtaiwan.tw/posts/pfbid0Xua6ajGWgURbS3XGqU5vubpXwonnorrR3vCqsRiv2AAtu8DFYocb74q7wSkYFkTUl)
- [報名表單](https://forms.gle/MLrDbFghTJuvLD4m7)
- [polis 連結](https://polis.tw/87nnxrrj5d)
### 上週實體小聚收到對於種子意見 AI 處理的回饋？
- 正向影響：
- 負向影響：
    - 有些在地化語詞被修正掉了，例如「車手」這個詞被改掉了，改成「基層人員」。
    - 意見變得過於文鄒鄒，讓意見本身比較難以處理。
- 發現：
    - 在利用 AI 調整意見的時候，會有需要人類處理的地方。
- 修正指令：
    - 使用環境：claude 
    - 將以下意見轉換為有效的Polis意見，該意見應：
        - 使用清晰、簡單的邏輯（少於200字）
        - 使用國中生程度能理解的語言
        - 清楚定義任何複雜的概念以及主動被動的角色關係
        - 清楚定義程度
        - 僅包含一個可同意/不同意的概念
        - 如果一則意見有兩個以上的概念，拆成不同Polis意見
        - 去除情緒化或指責性語言
        - 避免絕對詞（「總是」、「從不」、「每個人」）
        - 著重於解決方案而非僅描述問題
        - 保持中立表達，不假設共同價值觀
        - 每一個意見都是獨立分開的意見
    - 格式： 原始意見： [意見] Polis意見： [轉換後的意見]
### 各個 AI 回覆的差異
- 總覺得不同的工具處理上差異 [name=allen]
- 把意見丟到 AI 工具裡面是否要分開處理？
### Action List
- 是否要重新開？
    - 不用重新開
    - 針對有問題的意見：修改後新增即可
    - 新增的意見，在處理後新增。
- 意見都已經處理好了 [name=josh]
- 這週寄信給目前報名的參與者 [name=peter]
- 
### 下一次可以換換看別的工具？
- polis 能夠修改的意見太少了。
- 而且 raw data 是沒有辦法下載。（如果不是伺服器維護者）
- [Viewpoints.xyz](https://viewpoints.xyz/）或許是一個解決方案
    - 主程式是開源的。[github 連結](https://github.com/Goodheart-Labs/viewpoints.xyz)
## 網站
- [vTaiwan 網站改版，啟動！](/Q3_hgovyRHusEq8-3nomPQ)
- 目前有一個預部署的[成果](https://vtaiwan.zeabur.app)
- 小小的問題：後台的 CNS 很容易爛掉，
- 介紹：https://blog.huli.tw/2024/04/14/zeabur-introduction-deploy-service/
- 目前伺服器部署在東京。

## 結構性討論問卷調查
![](https://g0v.hackmd.io/_uploads/B1LOG9Jxle.png)

- [ARE系統討論筆記 (歡迎加入討論！)](https://hackmd.io/5_fsKa5KTJusyroKIYCi-w?both)
- [問卷](https://docs.google.com/forms/d/e/1FAIpQLSetWsVMRU5W3JEV4Vm2gZugrbCtOEeoTFqHf_bFWVa2VXSYKA/viewform?usp=header)
    - 邀請大家花個五分鐘填寫。Argdown 應該未來還是會找場合應用。
### 討論
- 有無登入會成為進入的門檻 [name=peter]
    - 從手機操作的時候的確蠻討厭登入的流程 [name=宇亭]
    - 調查來看，登入確實會成為一個困擾
- 但是依然
- Kialo:權限控制不錯 [name=allen]
    - 對外有分成四種不同的等級，管理內容上可以比較細緻(editor,  writer, suggester ,viewer)
        - https://support.kialo-edu.com/en/hc/participant-roles-and-permissions/
- 希望可以透過 mastodon 來進行討論
    - mastodon 也有簡單的身份驗證。
        - https://joinmastodon.org/verification
- 可以考慮其他數位驗證方式？
    - 數位皮夾可以討論
    - 也有其他軟性的身份驗證平台
        - https://truanon.com/


Allen 的更新分享:
- 查詢了 Zeabur 背景
    - https://allenlinli.notion.site/Zeabur-1eb028ed1717808a88a1d2a35b770011?pvs=4
    - PAAS 替代方案：用平台如 Render、Railway 部署。但其實 Ghost 部署不難，也可以用 OCF 用的 greenhost （且支持減少碳排）。
- 正在推廣每個週末在 g0v.social 上的語音聚會，使用 Revolt
    - 時間是每週六晚上九點
- 想要架設 wiki.js，成為一個較容易編輯、且有雙方看法的維基百科
    - 成為 Kialo 的入口
    - 目前計畫使用 g0v.social 來驗證
    - 本來想要用 Discourse，但可惜 Zeabur 送郵件有問題
- 有查詢 Argdown 的作者，為德國邏輯學教授
    - 或許未來能使用 AI 來自動生成 argdown 多層次雙方論證
    - https://www.gregorbetz.de/
    - Gregor Betz
        - Gregor Betz is a philosopher and professor at the Karlsruhe Institute of Technology (KIT) in Germany, known for his work in philosophy of science, argumentation theory, and deliberative democracy
    - highlight: Pioneering work on Chain of Thought — previously termed “Thinking Aloud” — that was later picked up by Wei et al., who demonstrated its effectiveness with GPT-3.
    - 另外發現了 圖爾敏論證模型（Toulmin Model），但有些過於複雜
- 做了台灣資安門神
    - https://chatgpt.com/g/g-6813a15f1ab08191aa17f1c2f9963ee8-zi-an-men-shen-zhe-ruan-ti-ke-yi-yong-ma-tai-wan-men-shen-wei-tai-wan-ren-de-zi-xun-an-quan-guo-fang-an-quan-ba-guan
    - 目前看來相當地有效


## 提案：參與公民科技試驗場域
- [name=A4]
- 角色
  - 地方政府機關：提出待解決的問題
  - 公民科技團體：依據問題提出解方，並共同產出解決方案
  - 顧問：邀請具有經驗人士，在政府機關與公民科技團體之間的溝通橋梁。協助收束問題、解方架構等工作。
- 執行時間：
    - 6月到7月 媒合
    - 8月到12月 開發
- 可能需求：
    - 公文資料紙本電子化
    - 電子報
- 經費預估：
    - 40w~60w，有在努力看可不可以拉高

- 目標
  - 增加「公民科技」與政府機關的協作
  - 增加公共程式的實例
 - 有規劃安排團隊投稿 FOSDEM

- 為什麼邀請 vTaiwan
  - vTaiwan 長期使用的公民討論工具，或許是政府機關願意作為意見徵集工具，或藉此機會串聯
    - 如果 vTaiwan 可以自已找到願意取用的機關，成案的機率更高。

- 目前進度
  - A4 的組織準備投標
  - 希望簽 MoU，作為投標佐證資料

### 結論
- 簽署 MOU，內容為參與後續媒合會