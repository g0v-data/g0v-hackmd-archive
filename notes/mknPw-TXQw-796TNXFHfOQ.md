# 20251202 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：
- 線上出席：
- https://meet.google.com/mrz-dgrd-pri
:::

## 上次會議
*   **[mrorz]** Code review `rumors-site` PR #615 (https://github.com/cofacts/rumors-site/pull/615)
*   **[Bug]** `rumors-site` feedback dialog cache 問題
*   **[Infra]** ElasticSearch v9 reindex 研究進度
*   **12/07 小聚籌備**


### 演講分享
* **mglee@g0v-tw** 分享了兩場關於假訊息與 Cofacts 的演講：
    > 12/4 & 12/10 分別在中山社會創新研究所和政大創新國際學院有兩場演講，這次會主講假訊息跟 Cofacts的案例。中山的是中文演講；政大的是英文演講。跟你們分享！

## 系統狀況 (Server Alerts)

* **cofacts.tw** 網站從 11/25 開始至今天 (12/2) 持續出現 `HTTP timeout occurred` 的不健康狀態警報，頻率相當高。
* **line-bot.cofacts.tw** 在 11/30 曾出現 `Response code mismatch error` 的警報。
* **api.cofacts.tw** 在 11/27 曾出現 `Response code mismatch error` 的警報。

## 開發者動態 (Github Activities)

### cofacts/rumors-site
* **新功能開發中**
  * [[PR #618] fix: issue #308 "Show URL title in article list"](https://github.com/cofacts/rumors-site/pull/618)
  * [[PR #615] fix: Redirect to new user profile URL after the user removes their slug settings #563](https://github.com/cofacts/rumors-site/pull/615)
* **已完成/關閉**
  * [[PR #617] fix: update feedback dialog comment in real-time #616](https://github.com/cofacts/rumors-site/pull/617) (Merged)
* **新議題**
  * [[Issue #616] [Bug] Feedback dialog 內的 comment 不會即時更新](https://github.com/cofacts/rumors-site/issues/616)
* **新版本發布**
  * [release/20251126](https://github.com/cofacts/rumors-site/releases/tag/release/20251126)

### cofacts/worker
* **新功能開發中**
  * [[PR #3] Url resolver article classifiers](https://github.com/cofacts/worker/pull/3)
* **已完成/關閉**
  * [[PR #1] feat: implement rumor classification workflow with OpenAI batch API](https://github.com/cofacts/worker/pull/1) (已關閉)

### cofacts/takedowns
* **處理垃圾訊息**
  * [[PR #277] Takedown spam user 李蔡雄 9BnCxZoBElZarx-VOryT](https://github.com/cofacts/takedowns/pull/277) (已完成)



## 小聚 rundown

- 週六早上
    - [ ] KKTIX 行前通知：提醒時間、使用電腦而非手機
    > Hello 你好，
	>
	> 本週日就是 6 月 15 日查核志工培訓囉！
	>
	> 志工培訓需要大量查詢資料，請自備筆電 💻 與充電器 🔌 並帶著愉快的心情來參加。帶順手的平板也可以的！如果願意協助編修影片逐字稿，請自備耳機唷🎧！
	>
	> 🕒 時間：06/15（日）14:00 - 17:00
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
    - [ ] 開場使用材料更新：https://docs.google.com/presentation/d/1N9DxoN1NuxdtQILkcV67y_q8EM8CJF5GhoYLcCKFpAc/edit [name=mrorz]
	- [ ] 準備 Slido `#cofacts`
		- [ ] 放投影片網址
- 當日準備 / 攜帶
    - [ ] 樓下用的標語 - bil
    - [ ] 貼紙 - orz, bil
    - [ ] 黏土 - orz
    - [ ] 手板 - bil
    - [ ] 講義 - bil
    - [ ] 一次性杯子 - bil
    - [ ] 延長線 - bil / mrorz
        - 比鄰有三條
    - [ ] Wifi 機 - mrorz
        - [ ] rt-ax57 go
        - [ ] 電源線
    - [ ] 多帶一條 type-c 公公線 for dongle 的電
    - [ ] 備用 wifi 機 [name=nonumpa]
- 13:00 - 場佈 [排法](https://g0v.hackmd.io/0rzXk22PQZ2g5aswKIAXdw?view)
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
    - [ ] Google Chrome tab: [KKTIX](https://cofacts.kktix.cc/events/cofactseditor47)
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

