# 20251209 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：bil, nonumpa, mrorz, Justin, Joe, yuyu, geopepper
- 線上出席：
- https://meet.google.com/mrz-dgrd-pri
:::

## :eyes: 上次會議跟進事項

### :construction: 待辦事項
*   **[Infra]** 調查 Cloudflare health check 警報設定
*   **12/07 小聚** 回顧
*   **人權市集** 回顧

## 上週訊息

*   **nonumpa@g0v-tw**
    > 剛剛試著把 site, api, bot 的 cloudflare healthchecks `consecutive_fails` 改成 2，再觀察看看 alert 有沒有變少
    > 目前 healthcheck interval 設定為 60 秒，也就是說 60 秒內要連續戳兩次失敗才會有 alert
    2025/12/3
    - 修改後 12/3 ~ 12/9 僅一次 alert
    - nonumpa++
*   **mrorz@g0v-tw**
    > 週六人權日 Cofacts 要擺攤，上次 SITCON 擺攤的心得：
    > [https://g0v.hackmd.io/@cofacts/meetings/%2FAvpmwuvvSGaWgHLf3sITdg#SITCON-%E5%AD%B8%E7%94%9F%E8%A8%88%E7%AE%97%E6%A9%9F%E5%B9%B4%E6%9C%83%E6%93%BA%E6%94%A4%E6%AA%A2%E8%A8%8E](https://g0v.hackmd.io/@cofacts/meetings/%2FAvpmwuvvSGaWgHLf3sITdg#SITCON-%E5%AD%B8%E7%94%9F%E8%A8%88%E7%AE%97%E6%A9%9F%E5%B9%B4%E6%9C%83%E6%93%BA%E6%94%A4%E6%AA%A2%E8%A8%8E)
    - 親子活動，推廣 LINE 的話小朋友沒有手機 [name=bil]
    - 資訊月也會發生，因為小學生會被帶進來 [name=bil]
      - 假新聞清潔劑有準備小遊戲給小朋友，手板上有考題，完成之後還是有給肥皂
    - 小朋友願意看動畫 [name=bil]
    - ![](https://g0v.hackmd.io/_uploads/ryl0x4qSf-l.png)
    - 人很多沒辦法做其他事情
    - 會有人來聽之後會變成查核者


### Github Activities

*   **Pull Requests**
    *   **rumors-site#619: "fix #308: Show URL title in article list"**
        *   MrOrz 進行了 review，並請 Justin 確認手機版本的邊距。
        *   [https://github.com/cofacts/rumors-site/pull/619](https://github.com/cofacts/rumors-site/pull/619)
    *   **rumors-site#615: "fix: Redirect to new user profile URL after the user removes their slug settings #563"**
        *   MrOrz 進行了 review，並請 YUHUIYI 協助調整。
        *   [https://github.com/cofacts/rumors-site/pull/615](https://github.com/cofacts/rumors-site/pull/615)
    *   **rumors-site#620: "Update package-lock.json and package.json for node version and cross-env"**
        *   此 PR 已被關閉。
        *   [https://github.com/cofacts/rumors-site/pull/620](https://github.com/cofacts/rumors-site/pull/620)
    *   **takedowns#276: "Takedown spam user hua hua I10upZoBYwEQPWDIbGY3"**
        *   已完成下架。
        *   [https://github.com/cofacts/takedowns/pull/276](https://github.com/cofacts/takedowns/pull/276)
    *   **takedowns#277: "Takedown spam user 李蔡雄 9BnCxZoBElZarx-VOryT"**
        *   已完成下架。
        *   [https://github.com/cofacts/takedowns/pull/277](https://github.com/cofacts/takedowns/pull/277)
*   **Issues**
    *   **rumors-site#616: "[Bug] Feedback dialog 內的 comment 不會即時更新"**
        *   此問題已修復並關閉。
        *   [https://github.com/cofacts/rumors-site/issues/616](https://github.com/cofacts/rumors-site/issues/616)
*   **Releases**
    *   **rumors-site: release/20251202**
        *   [https://github.com/cofacts/rumors-site/releases/tag/release/20251202](https://github.com/cofacts/rumors-site/releases/tag/release/20251202)


## 小聚檢討

小松果: https://g0v.hackmd.io/@mrorz/SyGP7qGGbl 

- 青職基地 1F setup ![](https://g0v.hackmd.io/_uploads/H1G3WdHf-e.png)
- 延長線不夠
    - 插座在左側櫃子裡、右側柱子上
    - 再多兩條可能也不夠 QQ
- 大家很受控 [name=justin]
- 回應品質也很好 [name=bil]

## 本月 cost

![](https://g0v.hackmd.io/_uploads/B16uK9BGZe.png)

收到 projection 會超標，但隔了幾天看下來還好
- 12/1 猜是 cloud run free tier
- 11 月底的 cloud logging (10+ USD) 原因不明

## Elasticsearch Migration

可以先看看 data 長什麼樣，需使用 NPO HUB Guest WiFi

http://202.5.251.82:6223/app/discover#/doc/6227b879-2647-4e53-beff-0a28240f5c80/articles_v1_4_1-v9?id=gmdiceh1hebq

### script
```
curl -X POST "${DEST_HOST}/_reindex?wait_for_completion=false&pretty" -H 'Content-Type: application/json' -d"
{
  \"source\": {
    \"remote\": {
      \"host\": \"${SOURCE_HOST}\"
    },
    \"index\": \"${SOURCE_INDEX}\",
    \"size\": 50
  },
  \"dest\": {
    \"index\": \"${DEST_INDEX}\",
    \"op_type\": \"create\"
  },
  \"conflicts\": \"proceed\"
}"
```

### 支援續傳
"op_type": "create"
"conflicts": "proceed"

### chunk too large error
```
"error" : {
    "type" : "illegal_argument_exception",
    "reason" : "Remote responded with a chunk that was too large. Use a smaller batch size.",
    "caused_by" : {
      "type" : "content_too_long_exception",
      "reason" : "entity content is too long [184375375] for the configured buffer limit [104857600]"
    }
  }
```

source size 改小 就好了

### Next steps

1. 改 API
2. 驗證資料是否正常
    - 記錄一下 reindex 所需時間
    - reindex 時 elasticsearch 會用多少記憶體
      - 若夠小，可以直接在同一台 production 上開 DB 做 reindex，省去 snapshot restore 到 local 以及 snapshot 回 production 的時間
      - docker-compose 裡只給 2GB RAM 也能跑
3. 上 staging
