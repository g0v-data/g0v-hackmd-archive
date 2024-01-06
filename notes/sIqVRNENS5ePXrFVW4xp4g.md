---
tags: cofacts, meeting note
---
20200219 會議紀錄
=====

> 
> bil, mrorz, 文武, lucien
> 上次開會紀錄：https://g0v.hackmd.io/@mrorz/r1dQQZbmU
>

## 4 月台南小聚（第19次編輯小聚）

- [x] 主題：
    - 我:heart:台南
        - 主視覺：孔廟 牛肉湯
        - 
- [ ] 時間：4/18 (六) 2:00pm ~ 5:00pm
- [ ] KKTIX
- [ ] 攜帶貼紙
- [ ] 場地：會是[好想工作室](https://goo.gl/maps/MBd7jz6gDK3J3fJV9)（含場佈：1:00 ~ 6:00）
    - [ ] 茶水
    - [ ] 麥克風+插座+網路
    - [ ] 投影機
    - [ ] 延長線
    - [ ] 食物
    - [ ] 垃圾
    - [ ] Talk
    - [ ] wifi
        - [ ] Nighthawk M1 + 4G sim
        - [ ] ASUS RT-N12 Wireless N300 (2x 5dbi高增益天線)
- [ ] 誰會來呢？
- [ ] 誰不會來：
- [ ] LINE 文案

lucien:
11點10點高鐵來得及嗎

bil
台南兩小時 可以當日來回

文武
高鐵轉沙崙線 or 公車

bil
場地已經辦過 3~4 次 g0v 專案聚會
RR 參加過

orz
高鐵票單據？手機票證購票證明可以嗎

bil:
正本車票報銷，須自己先墊錢
手機票證購票證明，會去 OCF 問。

## LINE chatbot 換 logo

bil
明天會有合約給我們

換 logo:
https://drive.google.com/drive/folders/1nnOFuxW70m7OgGfAI3fVcB8ri2ugODki

選擇黑底「真的假的」，字要大

orz:
嗯，這樣也跟原本的差不多，維持辨識度

:::success
Lucien 會改成橘色字看看
:::

## 名片

bil:
我名片發完了

orz:
我去甦活印ㄅ

[雙霧P + 背面局部上光](http://www.soho8d.com.tw/Form2/F102.aspx?id=497)

:::success
在 Lucien 另一台電腦裡
:::

## 開發
GitHub activities
https://datastudio.google.com/u/0/reporting/18J8jZYumsoaCPBk9bdRd97GKvi_W5v-r/page/WSQFB

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ce2f2ea7f399fd38d6f56b9148af3612)

### Carry-over
See [上次會議記錄](https://g0v.hackmd.io/@mrorz/r1dQQZbmU)

#### "Invalid reply token" 成因
https://github.com/cofacts/rumors-line-bot/issues/154


### In progress
#### CreateReply 不要等 url resolving，有時候還會出錯
- API: done, on staging
- UI: https://github.com/cofacts/rumors-site/pull/217

### Done
#### Mobile 上取消 share 造成 error
> Norman++
https://github.com/cofacts/rumors-site/pull/216
on Staging

#### 老回應打不開
> Norman++
> https://github.com/cofacts/rumors-site/pull/215

ex: https://cofacts.g0v.tw/reply/5605652568811-answer / fixed: https://cofacts.hacktabl.org/reply/5605652568811-answer

:::info
比較好的範例：
好的：https://cofacts.hacktabl.org/reply/5487673377361-answer
壞的：https://cofacts.g0v.tw/reply/5487673377361-answer
:::

### New issues
Date range filter
https://github.com/cofacts/rumors-api/issues/148

### 網站 CPU issue

原本的 cronjob (from: [20191225](https://g0v.hackmd.io/@mrorz/B1XErJZyL))
```
30 4 * * * cd /home/docker/rumors-deploy;  /usr/local/bin/docker-compose restart site-zh >> /var/log/cron.log 2>&1
35 4 * * * cd /home/docker/rumors-deploy;  /usr/local/bin/docker-compose restart site-en >> /var/log/cron.log 2>&1

```

這會整個 container restart，會有短暫 downtime，導致 nginx 回傳 503。

但只要不重開 server，CPU 還是可能會很高；只有重開之後才會下降。
感覺只要開太久就有殭屍 @@

pm2 有內建 `cron_restart` 功能可以 graceful reload 機器，但是這個功能[是壞的](https://github.com/Unitech/pm2/issues/4307)。

另外，pm2 有 `reload` 指令本身[可以達到 0-downtime restart](https://stackoverflow.com/questions/44883269/what-is-the-difference-between-pm2-restart-and-pm2-reload)。因此，設定新的 cronjob 每小時 reload:
```
# Site recover
0 * * * * cd /home/docker/rumors-deploy;  /usr/local/bin/docker-compose exec -T site-zh node_modules/.bin/pm2 reload all >> /var/log/cron.log 2>&1
5 * * * * cd /home/docker/rumors-deploy;  /usr/local/bin/docker-compose exec -T site-en node_modules/.bin/pm2 reload all >> /var/log/cron.log 2>&1
```

執行後可以在 pm2 plus 看到 reload 數字：![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d4758642bbb3b8f34746db2841ab549f)

### Chatbot RAM issue

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_1a4699e29a4801d97876b10ba0eba03b)

