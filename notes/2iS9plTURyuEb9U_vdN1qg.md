
# civic talk 管理者指南

## 回到專案大共筆 [vtaiwan 2026 新專案 civic talk](/u6Z7tvLKTzWYSH49YTCw1A)

> 本平台為開源公民審議工具，任何人皆可部署自己的版本。
> 如有問題或想一起貢獻，歡迎聯繫：
> - g0v Slack：**Peter** `@g0v slack` 或 **#vTaiwan** 頻道
> - Email：**vtaiwan.tw@gmail.com**

---

## 管理後台說明

Civic Talk 的管理後台位於：

```
https://你的網址/admin.html
```

管理後台提供以下功能：
- 新增、編輯、刪除議題
- 管理各議題的素材（刪除不當內容）
- 審核民眾提交的意見摘要
- 直接編輯議題說明頁（共識、爭點、立場地圖）

---

## 管理員權限設定（使用 Google 帳號）

本平台採用 **Cloudflare Access** 管理管理員登入，透過 Google 帳號驗證身份，無需另外設定密碼。

### 前置條件

- 擁有 Cloudflare 帳號
- 網站已部署在 Cloudflare Pages

---

### 設定步驟

#### Step 1：進入 Zero Trust 後台

1. 登入 [dash.cloudflare.com](https://dash.cloudflare.com)
2. 左側選單點擊 **Zero Trust**
3. 若是第一次使用，會要求設定團隊名稱（隨意填寫即可）

---

#### Step 2：設定 Google 為身份驗證來源

1. 左側選單 → **Settings** → **Authentication**
2. 在「Login methods」區塊點擊 **Add new**
3. 選擇 **Google**
4. 依照畫面指示，前往 [Google Cloud Console](https://console.cloud.google.com) 建立 OAuth 憑證：
   - 建立專案 → APIs & Services → Credentials → Create credentials → OAuth client ID
   - Application type 選 **Web application**
   - Authorized redirect URI 填入 Cloudflare 提供的網址（畫面上會顯示）
5. 將 Google 提供的 Client ID 和 Client Secret 填回 Cloudflare，儲存

---

#### Step 3：建立 Access Application 保護管理後台

1. 左側選單 → **Access** → **Applications** → **Add an application**
2. 選擇 **Self-hosted**
3. 填寫基本資訊：
   - **Application name**：`Civic Talk Admin`
   - **Session Duration**：24 hours（或依需求調整）
   - **Application domain**：填入你的 Pages 網址
   - **Path**：填入 `admin.html`
4. 點擊 **Next**

---

#### Step 4：設定管理員名單

1. **Policy name**：`管理員`
2. **Action**：Allow
3. **Configure rules** → Include → 選擇 **Emails**
4. 填入允許登入的 Gmail 帳號，例如：
   ```
   peter@gmail.com
   collaborator@gmail.com
   ```
5. 若整個 Google Workspace 組織都要能登入，可改選 **Emails ending in** 填入網域，例如 `@yourorg.com`
6. 點擊 **Next** → **Add application**

---

#### Step 5：驗證設定

1. 開啟無痕視窗，打開 `https://你的網址/admin.html`
2. 應該會自動導向 Google 登入畫面
3. 用允許清單內的 Google 帳號登入，應可順利進入管理後台
4. 用不在清單內的帳號登入，應看到「Access denied」畫面

---

### 新增或移除管理員

往後要調整管理員名單，只需：

1. 登入 Cloudflare → **Zero Trust** → **Access** → **Applications**
2. 找到「Civic Talk Admin」→ 點擊 **Edit**
3. 進入 **Policies** 分頁 → 編輯管理員名單
4. 儲存即時生效，不需重新部署

---

## 常見問題

**Q：Cloudflare Access 要收費嗎？**
免費方案可保護最多 50 位使用者，對大多數公民科技專案足夠使用。超過 50 人才需要付費。

**Q：管理員登入後需要再輸入密碼嗎？**
不需要。通過 Google 驗證後，Session 在指定時間（預設 24 小時）內都不需要重新登入。

**Q：可以同時有多個管理員嗎？**
可以。在 Policy 的 Emails 清單中加入多個帳號即可，每個帳號都能獨立登入。

**Q：有沒有辦法看到誰登入了管理後台？**
有。在 Cloudflare Zero Trust → **Logs** → **Access** 可以看到所有登入記錄，包含時間、帳號、IP 等資訊。

---
## 如何為議題建立 polis.tw 投票

> Civic Talk 整合了 [polis.tw](https://polis.tw)，讓每個議題都可以嵌入意見投票。  
> 參與者不需要離開頁面，就能對各種立場表達支持或反對，幫助平台彙整多元觀點。

---

## 整體流程

```
在 polis.tw 建立對話  →  取得對話 ID  →  貼到 Civic Talk 管理後台  →  前台自動顯示投票
```

---

## Step 1：在 polis.tw 建立對話

1. 前往 [polis.tw](https://polis.tw) 並登入（或註冊帳號）
2. 點擊右上角 **「建立對話」（Create Conversation）**
3. 填寫對話資訊：
   - **標題**：建議與 Civic Talk 議題名稱一致，方便管理
   - **說明**：可貼上議題簡介，幫助參與者理解背景
4. 點擊 **「建立」（Create）** 完成

---

## Step 2：取得對話 ID

建立完成後，你的 polis 對話網址會長這樣：

```
https://polis.tw/3hdpvkky7k
```

網址最後面那段英數字，就是 **對話 ID**，例如：

```
3hdpvkky7k
```

把這串 ID 複製起來，下一步會用到。

---

## Step 3：新增意見陳述句（建議）

polis 投票的核心是「陳述句」，參與者對每句話表達「同意」、「不同意」或「略過」。

建議在對話建立後，先新增幾句陳述，引導討論方向，例如：

- 政府應全面禁止這項行為
- 現行法規已足夠，不需要修法
- 應優先聽取受影響社群的意見

> 陳述句不需要一次到位，參與者也可以在投票過程中提交新的陳述句。

---

## Step 4：在 Civic Talk 管理後台設定

1. 打開 Civic Talk 管理後台（`/admin.html`）
2. 找到對應的議題，點擊 **「編輯」**
3. 在 **「polis.tw 對話 ID」** 欄位貼上剛才複製的 ID（例如 `3hdpvkky7k`）
4. 點擊 **「儲存」**

設定完成後，前台議題說明頁會自動出現投票嵌入區塊。

---

## Step 5：確認前台顯示

回到前台，打開對應議題的說明頁，應該會看到：

- 說明頁內容下方出現 **「📊 加入意見投票」** 區塊
- polis 投票介面嵌入其中，可以直接操作

若沒有看到，請確認：
- polis 對話 ID 是否填寫正確（不含 `https://polis.tw/`，只填 ID 本身）
- 管理後台有確實儲存
- 頁面是否有重新整理

---

## 移除或更換投票

- **移除投票**：回到管理後台編輯議題，將 polis ID 欄位清空並儲存，前台的投票區塊會自動消失
- **更換投票**：直接把舊的 ID 換成新的 ID 並儲存即可

---

## 聯繫與協助

如果有問題，歡迎聯繫：

| 管道 | 聯繫方式 |
|------|---------|
| g0v Slack | **Peter** `@g0v slack` |
| g0v Slack 頻道 | **#vTaiwan** |
| Email | **vtaiwan.tw@gmail.com** |

加入 g0v Slack：[join.g0v.tw](https://join.g0v.tw)

## 聯繫與貢獻

本專案目前為實驗性質，歡迎各種形式的回饋與貢獻。

| 管道 | 聯繫方式 |
|------|---------|
| g0v Slack | **Peter** `@g0v slack` |
| g0v Slack 頻道 | **#vTaiwan** |
| Email | **vtaiwan.tw@gmail.com** |

加入 g0v Slack：[join.g0v.tw](https://join.g0v.tw)