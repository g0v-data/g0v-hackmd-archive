---
tags: cofacts, meeting note
---
20191225 會議記錄
===== 
@ NPO hub~~~
bil, mrorz, 文武, NHK 記者們

> 上次開會紀錄：https://g0v.hackmd.io/@mrorz/SJ8GSNv0B
> 

## Rumors-site 升級 next9
1. [x] Article list --> PR to dev
2. [x] Article page （見 API 更新）
3. [x] Reply list
4. [x] reply page
5. [x] docker build
6. [x] landing page
7. [x] 上 staging
8. [x] 上 production --> 新台幣升級
9. [x] google analytics (w/ gtag)
10. [ ] All i18n (including levels...)
11. [ ] RSS feed

### Stackimpact native extension
https://g0v-slack-archive.g0v.ronny.tw/index/channel/C2PPMRQGP#ts-1577188090.022800

MrOrz 改改


### Performance follow-up

現在每天中午 12:30 重新 site-zh, site-en
```
30 4 * * * cd /home/docker/rumors-deploy;  /usr/local/bin/docker-compose restart site-zh >> /var/log/cron.log 2>&1
35 4 * * * cd /home/docker/rumors-deploy;  /usr/local/bin/docker-compose restart site-en >> /var/log/cron.log 2>&1
```


### TODOs
- 從其他頁面點進 `/replies` 會壞掉 - https://github.com/cofacts/rumors-site/issues/193
- 字太小

## Token 過期

> 文武：自動更新