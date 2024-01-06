---
tags: cofacts
---

# 2018/10/21 Cofacts chatbot incident report

## Incident 1 LINE bot does not respond when URL is attached

### Problem

文武在 10/21 15:00 發現很多的 error。調查發現只要 `ListArticle` 查詢含有 URL，就會有錯誤：

```
{
  "data": {
    "ListArticles": null
  },
  "errors": [
    {
      "message": "Cannot destructure property title of 'undefined' or 'null'.",
      "locations": [
        {
          "line": 2,
          "column": 3
        }
      ],
      "path": [
        "ListArticles"
      ],
      "authError": false
    }
  ]
}
```

### Analysis

SSH 進機器撈 url-resolver 的 log 看，發現跟 socket 斷裂相關的 error：

https://github.com/cofacts/url-resolver/issues/9

研判是 puppeteer 與 headless chromium 之間的 websocket close 的關係。

### 處理

透過 docker-compose 把 `url-resolver` 重啟之後即正常。

### 追蹤

1. Rollbar 中仍然有零星的「`Cannot destructure property `title` of 'undefined' or 'null'.`」發生： https://rollbar.com/mrorz/rumors-line-bot/items/19/occurrences/56553337227/

2. 將 websocket error 記至 github issue 待修，否則未來可能還會再發生。
https://github.com/cofacts/url-resolver/issues/9

## Incident 2. LINE bot does not remember the context after user submitted content

### Problem

傳一則新訊息之後，跳出問理由的對話窗。輸入理由之後，卻又鬼打牆說找不到，要我們輸入理由。

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_252e8553b9d4d14c712b54ec1a5abb54 =250x)


### Analysis

判斷是 bot 的 redis 不知為何沒有把對話 context 記下來。

連到 Heroku dashboard，亦可確認此狀況：
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d6f174566775e1db40065b4113740371)

Heroku redis 的免費版 quota 是 25 mb，看起來已經滿了。

### 處理

根據[文件](https://devcenter.heroku.com/articles/heroku-redis#maxmemory-policy)，heroku redis 在到達上限之後預設的行為是噴 error。因此我們使用下面指令將其行為改成「刪掉最舊的」。

```
$ heroku redis:maxmemory redis-concave-55484 -a rumors-line-bot -p allkeys-lru
```

## 後續追蹤

為何 redis error 沒有在 rollbar？ 需要再追蹤。
是這個嗎：https://rollbar.com/mrorz/rumors-line-bot/items/96/
