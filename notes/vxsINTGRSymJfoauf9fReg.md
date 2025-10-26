# 20251021 會議記錄

:::info
- [所有會議記錄](https://gov.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：bil, mrorz, Justin, Joe(yuyu20:08)(geopepper 20:11)
- 線上出席：nonumpa, helen
- https://meet.google.com/mrz-dgrd-pri
:::

## 上次會議待追蹤項目

- **Cloud Run Migation**: error rate & cost estimation update.
  - Error rate 有下降
    - **Cloudflare** 持續回報 `cofacts.tw` 和 `api.cofacts.tw` 服務不穩定，出現多起 HTTP timeout 和 5xx 錯誤。
    - 頻率：10/19 一日 12 次，其他日子一天 1~3 次
    - 10/18 ~ 10/20 帳號攻擊也比較多，有的有 hyperlink 而且每個都不一樣 [name=bil]
    - url resolver 就會很忙 [name=mrorz]
  - Production sites 5USD/day, total budget < 200USD/mo
- **Takedown request**: 確認文章 (https://cofacts.tw/article/2fS7y4oBAjOeMOkl_Ljg) 是否已下架。
  - Done
- **[Johnson]** 資訊安全權限設定
- **CCPRIP - Analytics**: Opendata trend & LINE Bot usage 報表問題
- **[nonumpa, mrorz]** LLM based Topic Classifier: 追蹤 bug 修復與 benchmark 結果
- **[mrorz]** `cofacts/devops-manual` 撰寫進度。
- **[mrorz]** 新 URL resolver 設計文件進度 (https://github.com/cofacts/worker/issues/2)。
- **cofacts.ai**: Ground    ness Check agent 實作 (追蹤提案與文件)
- **[mrorz]** cAdvisor 研究與安裝

### Langfuse 停止運作 & 升級
- **mrorz@g0v-tw** 發現 Langfuse 自 10/2 起就沒有收到 rumors-api 和 takedown 的資料，原因是 langfuse-worker 和 redis 的連線斷開了。

> **mrorz@g0v-tw**:
> Cofacts 的 Langfuse 在 10/2 之後就收不到東西了 QQ
> rumors-api 和 takedown 都是，我還沒想到為啥

> **mrorz@g0v-tw**:
> 查了一下，10/2 開始 langfuse-worker 和 redis 的連線斷開了
> 應該是這個緣故

:::info
10/2~10/18 沒有 Langfuse trace
:::

Mitigation: redis 增加 restart: always

----

Langfuse 從 3.66 升級到 3.119
- UI 在 evaluation 有不少新功能


## 開發與程式碼庫活動 (GitHub Activities)

### 處理詐騙與垃圾訊息
- 持續進行垃圾訊息與詐騙使用者的下架作業，相關 pull requests 皆已完成。
  - [Add 2025/10/16 financial scam report detailing removal of fraudulent image](https://github.com/cofacts/takedowns/pull/270)
  - [Takedown spam user 優質外約+gleezy：k66099 C14Yp5cBfs35m9MiCypf](https://github.com/cofacts/takedowns/pull/272)
  - [Takedown spam user 五益 5cBJ8pkBWwAUNc5b-3gz](https://github.com/cofacts/takedowns/pull/271)
  - [Create 1014-privacy.md](https://github.com/cofacts/takedowns/pull/269)
  - [Takedown spam user Lei Meng lbEh4ZkBFga8s_Raiu76](https://github.com/cofacts/takedowns/pull/268)

### URL Resolver 效能問題
- `rumors-api` 的 [追蹤 URL Resolver 效能問題與重構](https://github.com/cofacts/rumors-api/issues/373) 已關閉，後續將由 [worker repo](https://github.com/cofacts/worker/issues/2) 的新計畫取代。

## [Infra] 降載 production

- ElasticSearch v9 https://g0v.hackmd.io/65JMCYDEQCeCYSAkBwJNTA?view#Elasticsearch-v9 --> 可以試試看 reindex 是否可行
  - vector search 對無文字的 AI 影片很重要
  - 之前的研究：https://g0v.hackmd.io/aJqHn8f5QGuBDLSMH_EinA#Search-amp-indexing
- Linode --> Compute Engine + Container-optimized OS
  - docker-compose --> cloud-init
- url-resolver 改寫 (如上)

## 小聚 rundown

- 週六早上
    - [x] KKTIX 行前通知：提醒時間、使用電腦而非手機
    > Hello 你好，
	>
	> 本週日就是 10 月 26 日查核志工培訓囉！
	>
	> 志工培訓需要大量查詢資料，請自備筆電 💻 與充電器 🔌 並帶著愉快的心情來參加。帶順手的平板也可以的！如果願意協助編修影片逐字稿，請自備耳機唷🎧！
	>
	> 🕒 時間：10/26（日）14:00 - 17:00
	> 📍 地點：103台北市大同區南京西路185巷6之1號 小樹屋 紅豆杉201 （捷運北門站 3 號出口，步行 10 分鐘）
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
    - [ ] 開場使用材料更新：https://docs.google.com/presentation/d/1N9DxoN1NuxdtQILkcV67y_q8EM8CJF5GhoYLcCKFpAc/edit [name=mrorz]
	- [ ] 準備 Slido `#cofacts`
		- [ ] 放投影片網址
- 當日準備 / 攜帶
    - [x] 樓下用的標語 - bil
    - [x] 貼紙 - orz, bil
    - [x] 黏土 - orz
    - [x] 手板 - bil
    - [x] 講義 - bil
    - [x] 一次性杯子 - bil
    - [x] 延長線 - bil / mrorz
        - 比鄰有 3 條
        - 場地有 2 條
    - [ ] Wifi 機 - mrorz
        - [ ] rt-ax57 go
        - [ ] 電源線
    - [ ] ~~多帶一條 type-c 公公線 for dongle 的電~~
    - [ ] 備用 wifi 機 [name=nonumpa]
- 13:00 - 場佈 ~~[排法](https://g0v.hackmd.io/0rzXk22PQZ2g5aswKIAXdw?view)~~
  - ~~桌子一邊 4 張椅子~~
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
    - [ ] Google Chrome tab: [KKTIX](https://cofacts.kktix.cc/events/cofactseditor49)
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
    - 撤收黏在牆上的東西
- 16:40 - 16:50 介紹 RSS、社群、合照
    - 撤收延長線 x2、網路
