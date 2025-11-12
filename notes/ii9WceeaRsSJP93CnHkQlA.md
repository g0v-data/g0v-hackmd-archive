---
tags: vTaiwan
---


## 如何將新議題貼上 vTaiwan 網站

以下步驟說明如何將新議題發佈到 [vTaiwan.tw](https://vtaiwan.tw) 官網，並正確顯示於[議題區](https://vtaiwan.tw/topics) 。

---

### 1️⃣ 在 talk.vtaiwan.tw 建立貼文

進入 [https://talk.vtaiwan.tw](https://talk.vtaiwan.tw)，建立一篇新貼文並輸入標題。

注意：標題後面要加上一個空白鍵，再加上一段英數組合，用來當網址連結。
> 如果格式不完整，網站上該議題點入後，會變成空白頁 [name=Bestian]

❌不完整的格式：```花蓮救災爭議之後：未來台灣救災程序與資訊流通如何改進？——公民意見徵集```
✅正確的格式：```花蓮救災爭議之後：未來台灣救災程序與資訊流通如何改進？——公民意見徵集 2025_Hualien_Event```

產生的連結如：https://www.vtaiwan.tw/topic/2025_Hualien_Event

---

### 2️⃣ 移除「討論中」標籤

預設會自動加上 `討論中` 標籤。
請**移除這個標籤**，否則無法設定分類為 `meta`。

---

### 3️⃣ 設定分類為「meta」

*note: this step需要talk.vtaiwan.tw的管理員權限，若無管理員權限，可先完成後面的steps，再聯絡管理員來改分類為meta*

只有將分類設定為 **meta**，
貼文才會顯示在主網站的首頁或議題列表中。



---

### 4️⃣ 製作封面圖

* 使用 AI 或繪圖軟體建立封面圖
* 調整圖檔大小（建議寬度 1200px 以內, 檔案大小1MB以內）
* 檔案大小需 **小於 1MB**

---

### 5️⃣ 上傳封面圖

將封面圖放入 `vue.vTaiwan-neo` 專案中的
`/public/cover/` 資料夾，
然後 push 到 GitHub，圖檔就會自動上網。

如果檔名是`2025_hualien_event.png`
圖檔網址就會是`http://vtaiwan.pages.dev/cover/2025_hualien_event.png`

---

### 6️⃣ 貼文格式範例

貼文內容的前段需包含 **slogan** 與 **cover** 欄位，例如：

```markdown
slogan : 花蓮救災爭議之後：未來台灣救災程序與資訊流通如何改進？
cover : http://vtaiwan.pages.dev/cover/2025_hualien_event.png

---
# 簡介

日期：2025 年 10 月 8 日（星期三）

在 2025 年 9 月的超級颱風中，花蓮地區因堰塞湖潰壩與洪水釀成重大傷亡與破壞……
```

---

### 7️⃣ 留言回覆範例

貼文底下加上一篇留言回覆，貼上意見徵集連結，例如：

```markdown
意見徵集 init 2025-10-08 2026-01-08  
https://pol.is/4fxd6ehrfj
```

---

✅ 完成後，vTaiwan 網站會自動同步顯示新議題及封面。
