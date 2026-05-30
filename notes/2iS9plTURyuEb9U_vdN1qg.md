
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

## 聯繫與貢獻

本專案目前為實驗性質，歡迎各種形式的回饋與貢獻。

| 管道 | 聯繫方式 |
|------|---------|
| g0v Slack | **Peter** `@g0v slack` |
| g0v Slack 頻道 | **#vTaiwan** |
| Email | **vtaiwan.tw@gmail.com** |

加入 g0v Slack：[join.g0v.tw](https://join.g0v.tw)