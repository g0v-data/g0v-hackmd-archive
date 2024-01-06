---
tags: cofacts, meeting note
---
20200122 會議紀錄
=====
> bil, mrorz

> 上次開會紀錄：https://g0v.hackmd.io/@MODl5abnQpKy6ifB4DPGcQ/SJWE4eQ3e8
> 

## 開發相關

### 新年

- [ ] API server & url-resolver protobuf update
    - Dockerfile + auto build
    - 上 staging 1 week
    - url-resolver 會加上 https://github.com/uw-labs/bloomrpc 開發教學、API 接取教學
- [ ] articlereplies API
- [ ] 從其他頁面點進 `/replies` 會壞掉 - https://github.com/cofacts/rumors-site/issues/193

### Chatbot Token 過期

> 文武：自動更新
> 

Cronjob done!

```
0 20 1,15 * * cd /home/docker/rumors-deploy;  bash scripts/update-line-bot-token.sh >> /var/log/cron.log 2>&1
```

每個月 2 日、16 日凌晨 4am 會更新
一個月兩次是怕其中一次失敗，還有另一次可以 cover ~

:::warning
下一次：2/2
:::

## 二月小聚(第18次編輯小聚)

NPO hub
2/8 (六) 1:30 ~ 5:30，廚房那間，可以小組討論，也有投影機

- [x] 主題：
    - 元宵
        - 平平安安慶元宵。
        - 看著滿月，年節也終於到尾聲了。
        - 2020，Cofacts 第一次的編輯小聚，就在02月08日星期六下午。
        - 這次換了一個新的場地，NPO HUB！！
- [x] 時間：2/8 (六) 14:00-17:00 
- [ ] KKTIX(bil上班寫)
- [ ] 攜帶貼紙
- [ ] 場地：NPO hub 2/8 (六) 1:30 ~ 5:30
    - [x] 茶水
    - [x] 麥克風+插座+網路
    - [x] 投影機
    - [x] 延長線 (jothon 4條)
    - [ ] 食物
    - [x] 垃圾
    - [ ] Talk
    - [ ] wifi
        - [ ] Nighthawk M1 + 4G sim
        - [ ] ASUS RT-N12 Wireless N300 (2x 5dbi高增益天線)
- [x] 誰會來呢？ MrOrz, bil, 文武, 蝴蝶, ci, lucien
- [ ] 誰不會來：ggm
- [ ] LINE 文案

:::success
Lucien 出出圖
:::
