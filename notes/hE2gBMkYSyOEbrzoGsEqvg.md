# 20260407 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：
- 線上出席：
- https://meet.google.com/mrz-dgrd-pri
:::

## 💬 Discord 上聊了什麼？

### general

- **mrorz@g0v-tw**
  > 上面這個 15 天前的訊息，紀錄了我們從 COS 轉 ubuntu 的心境轉折
- **Alfred chen@g0v-tw**
  > 我們不是ubuntu嗎？

### server-alerts
- `line-bot.cofacts.tw` 在 `2026-03-31 20:05:25 +0000 UTC` 回報為 Unhealthy，原因是 `Response code mismatch error`。

## 💻 Github 上發生了什麼？

- **cofacts/takedowns**
  - [Add privacy removal report for message in database #291](https://github.com/cofacts/takedowns/pull/291)
    - MrOrz 開了 PR，希望能移除包含家庭隱私資訊的訊息。
  - [Takedown spam user 日本外送茶TG：yy9882 YMwgWJ0BZgZZYBoadwoP #290](https://github.com/cofacts/takedowns/pull/290)
    - nonumpa 關閉了這個 PR。
- **cofacts/ai**
  - [design: Cofacts design system component library #22](https://github.com/cofacts/ai/pull/22)
    - MrOrz 開了 PR，新增了 Cofacts design system component library。


## :mag: 本週確認事項

### GCE Migration
- Cost review
- Cloudflare HTML cache and AI crawler defense - 還沒做
- 3/27 migration 之後，LINE bot 很常在整點 15 分的時候有 502 error ![](https://g0v.hackmd.io/_uploads/Sk5ZlwG2bg.png)
	- Linode 上我們本來就會每個整點 15 分時重啟 Line bot（處理 group chat 機制不穩定問題），但當時用的是 pm2 reload 指令 
	- GCE migration 時，這個 cronjob 被寫成直接用 docker-compose restart，導致有 downtime。
	- 4/7 傍晚發現並已經修正，19:15 開始應該會正常無 downtime。

### Elasticsearch 升級

:::spoiler Production cutover status
我已經連入 `cofacts-prod` 檢查過整體的運作狀態與系統資源了。

整體來說，你的 v9 migration 看起來非常成功，核心的 DB 與 API 都已經穩定運作了整整 6 天。但有幾個小細節（以及兩個不斷在重啟的周邊服務）值得你留意一下：

### 1. Elasticsearch v9 升規與資源佔用（狀況良好 ✅）
目前的 `rumors-deploy-db-1` 正在穩穩地跑著 `elasticsearch:9.3.2`，系統中這台容器的實體記憶體佔用約為 **15.14 GiB**。這個數字完美貼合了你設定的 `-Xms16g -Xmx16g` Heap Size。而且目前整台 GCE 的記憶體總共有 31 GiB，可用（Available）的包含 cache 還有將近 15 GiB，留給 OS 與 Lucene 檔案快取的空間非常充足。

### 2. Swap 使用量達 99%（無須緊張 ℹ️）
GCE 登入後的提示與 `free -h` 顯示 Swap 空間 (4.0GiB) 已經用滿了 (99%)。
這大概率是**升級期間 (Phase 1 & 2)** 同時跑 v6（16GB Heap）加上 v9（8GB Heap）再疊加第一次 Reindex 時，把記憶體撐爆，造成了大量的分頁被交換到 Swap 所遺留的歷史痕跡。
現在由於可用實體記憶體空間很大，這些 Swap 裡的東西就只是一些長期未存取的不活躍分頁（Inactive pages），不用理它也不會影響效能。若看著不順眼，你可以另外找時間手動重置它：`sudo swapoff -a && sudo swapon -a`。

### 3. URL Resolver 正在觸發 OOM 被砍（值得注意 ⚠️）
`rumors-deploy-url-resolver-1` 在我檢查時，顯示運作時間只有 15 分鐘（近期有重新啟動的跡象）。  
我查了一下本機的 `dmesg` 跟 `syslog`，發現該容器內的 `chrome` 程序觸發了 `Memory cgroup out of memory` 而被砍掉。這是因為 `docker-compose.yml` 裡面可能給予了該服務大約 `512MiB` 的記憶體限額，但 Puppeteer/Chrome 開網頁非常吃記憶體，因此超過了 CGroup 的限制被砍。
* **評估**：這不影響 GCE 主機，只是純粹容器內限額達到上限。這對於 URL Resolver 來說通常是被預期的操作（藉由 Docker 重啟來釋放洩漏或暴增的記憶體）。如果不希望它一直重啟，且主機目前記憶體還很充裕，或許可以考慮稍微調高一點記憶體上限，例如到 `1GB`。

### 4. LINE Bot 持續報 Apollo 錯誤（值得注意 ⚠️）
`rumors-deploy-line-bot-zh-1` 在我檢查時也顯示才剛起來幾分鐘而已。從這個服務的 Log 裡，發現了一整排很頻繁的錯誤訊息：
```text
Error reporting server info to Apollo during schema reporting: Error: An unexpected HTTP status code (401) was encountered during schema reporting.
```
* **評估**：看起來是傳遞給 Apollo 的 Token 失效或是過期了（401 Unauthorized）。這本身可能不影響使用者查核的功能，但如果該服務因為 error 或是 healthcheck 一直 crash 重啟的話，可能會遺漏 webhook。可以檢查一下對應的環境變數。

### 5. 作業系統更新提示
登入時會看到 `*** System restart required ***`，表示 Ubuntu 的底層 Kernel 順著 package update 已經安裝好了新版本，但需要你手動重啟機器才會套用。你可以在未來確認沒有重大活動的離峰時間，下一道 `sudo reboot`，重啟後所有 `restart: always` 的服務都會自己長回來，非常方便。
:::

### Cofacts.ai 開發
- Progress update: https://github.com/orgs/cofacts/projects/12
- Hybrid search: https://docs.google.com/document/d/1sZ4jOsrZPvbJv4QjlMxgbqFsh_pTZNBRs-NbG-HU0rM/edit?tab=t.lhafy6bbdc9p
    - 例子：AI 假海嘯影片 https://cofacts.tw/article/6w6rYJgBngzKCCgMrohC
    - 例子：鳥喝水暴斃 https://cofacts.tw/article/Ar4e2pgB6nor6FKt1vXc

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


## API access

verify1st.tw / https://github.com/topben/cryptotruth/pull/50

Product
- 主要是用 LLM 生成防詐文案
- Cofacts 用來作為 Crowd-source evidence，會交給 LLM 生成最後訊息

Concerns
- 源頭活水：希望流量數字可以收得到、feedback 收得到
- 不要有 extra effort for us

https://github.com/cofacts/opendata/blob/master/LEGAL.md

- 不在 LINE 所以給 LIFF URL 沒有太大幫助


