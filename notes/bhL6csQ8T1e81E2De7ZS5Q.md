---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20220119 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis 出席：bil, mrorz
- 線上出席：柏寬
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## 群組功能壞掉 update

- [上週](https://g0v.hackmd.io/SETMQ8DaQDu3a5ZYnrvfpA#%E5%B0%8F%E8%81%9A%E6%AA%A2%E8%A8%8E)發現 2021/11/15 後群組功能就壞掉了
- localhost
    - 傳測試訊息之後正常執行
    - 用 nodejs-bull-monitor 接上去看：![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b0f262ec770e5edce18d90edd075f632.png)
        - 只有 `expiredGroupEventQueue` 會出現
        - 傳訊息的時候不會有東西
- Production
    - 傳測試訊息之後完全不會動
    - line-bot-zh docker 在 2021-10-13 重啟之後就沒有重開過
    - 完全沒有 log
    - 用 nodejs-bull-monitor 接上去看：![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8692f36b09a0ac1d64b025796fb88c22.png)
        - 不知為啥，啥都沒有囧
    - 連進 redis 執行 `KEYS bull*`
        - 8 萬多筆
            ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b288fc3d2355e7dd269ed252120d493b.png)
        - 有些 value 是空陣列，但也有些是有東西的
            ```
            127.0.0.1:6379> HGETALL bull:groupEventQueue:1538707b
            (empty array)
            127.0.0.1:6379> HGETALL bull:groupEventQueue:1537828
             1) "timestamp"
             2) "1642388796221"
             3) "opts"
             4) "{\"attempts\":1,\"delay\":0,\"timestamp\":1642388796221}"
             5) "name"
             6) "__default__"
             7) "priority"
             8) "0"
             9) "data"
            10) "{\"type\":\"message\",\"replyToken\":\"<redacted>\",\"groupId\":\"C7249d850d37c5f476032aa35cd9208c8\",\"otherFields\":{\"message\":{\"type\":\"text\",\"id\":\"15432040754237\",\"text\":\"<redacted>"},\"timestamp\":1642388795553,\"source\":{\"type\":\"group\",\"groupId\":\"C7249d850d37c5f47603<redacted>\",\"userId\":\"Uc95d1b1faec<redacted>\"},\"mode\":\"active\"}}"
            ```
        - 該時間戳為：2022年 1月17日 週一 11時06分36秒 CST
    - 參考 bull 在 redis 的 [data structure](https://github.com/OptimalBits/bull/blob/master/lib/queue.js#L30-L45)
        ```
        list
        127.0.0.1:6379> type bull:groupEventQueue:waiting
        none
        127.0.0.1:6379> type bull:groupEventQueue:paused
        none
        127.0.0.1:6379> type bull:groupEventQueue:active
        none
        127.0.0.1:6379> get bull:groupEventQueue:id
        "1580554"
        127.0.0.1:6379> type bull:groupEventQueue:wait
        127.0.0.1:6379> LRANGE bull:groupEventQueue:wait 1 10
         1) "1580553"
         2) "1580552"
         3) "1580551"
         4) "1580550"
         5) "1580549"
         6) "1580548"
         7) "1580547"
         8) "1580546"
         9) "1580545"
        10) "1580544"
        127.0.0.1:6379> type bull:groupEventQueue:delayed
        none
        127.0.0.1:6379> type bull:groupEventQueue:stalled-check
        string
        127.0.0.1:6379> get bull:groupEventQueue:stalled-check
        "1642745787705"
        127.0.0.1:6379> get bull:groupEventQueue:stalled
        (nil)
        127.0.0.1:6379> get bull:groupEventQueue:failed
        (nil)
        127.0.0.1:6379> get bull:groupEventQueue:completed
        (nil)
        127.0.0.1:6379> get bull:groupEventQueue:drained
        (nil)
        127.0.0.1:6379> get bull:groupEventQueue:progress
        (nil)
        ```
        - redis list `bull:groupEventQueue:wait` 有大量 key，將最新的 ID 抓出來看 timestamp，是幾秒之前
        - 因此放 job 進 queue 這裡是好的，是 worker 沒在吃 job
    - 研判是重開就會好，但原因不明

Resolution
- 就重開 [name=bil]
- 可能要先清掉 queue [name=mrorz]
    - https://nyogjtrc.github.io/posts/2019/12/delete-keys-matching-a-pattern-in-redis/
    - `redis-cli --scan --pattern bull:expiredGroupEventQueue:*` 會有 80000 多筆

:::success
- 94重開
- 固定重開: 週一凌晨 3am 重啟 line bot 的 pm2
- 加上 monitor 機制
    - [`queue.getJobCounts`](https://github.com/OptimalBits/bull/blob/develop/REFERENCE.md#queuegetjobcounts)
    - [`queue.isPaused`](https://github.com/OptimalBits/bull/blob/develop/REFERENCE.md#queueispaused
    - Timestamp for jobs last completed & last in queue: https://github.com/OptimalBits/bull/blob/develop/REFERENCE.md#queuegetjobs
:::

## 測試現有圖片與 hash 的效果

### Collected images
- 103441 files (including `.` and `..` though)
- 17GB in total
- Google Colab 頻繁遇到 [timeout](https://research.google.com/colaboratory/faq.html#drive-timeout)
    - 可能改用 drive API?
    - See https://colab.research.google.com/notebooks/io.ipynb#scrollTo=c2W5A2px3doP

### Search with similarity

Image retrieval implementations in the wild in 2020:
https://matsui528.github.io/cvpr2020_tutorial_retrieval/

- This do not replace the current image-hash in https://github.com/cofacts/rumors-api/pull/273
    - image-hash is to avoid duplicates when storing images and search for near-duplicates (100% hash match)
    - The research below is for similarity search

- 把圖（或多媒體）轉成向量
    - For database items & query
    - 還沒研究 QQ
        - image-hash 已經是一種做法(?)
    - [Live coding image search](https://www.youtube.com/watch?v=M0Y9_vBmYXU)
        - Keras + flask
        - 用 [VGG16](https://ithelp.ithome.com.tw/articles/10192162) 抽 feature
        - server 在記憶體載入資料庫(5 張？)所有 feature，query 來時用 numpy 爆搜，算 L2 distance
- 把向量放進可以查詢的 poroduction-ready 資料庫
    - 2020 Summary：[Nearest neighbor (NN) & Approximate NN (ANN) search](https://www.youtube.com/watch?v=SKrHs03i08Q)
        - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4ae1b80a5d700d133858e1b0344eab1f.png)
        - Exact nearest neighbor: should try first, can do million scale ($10^6$)
        - ANN: Can support billion scale ($10^9$)
    - [OpenSearch knn](https://opensearch.org/docs/latest/search-plugins/knn/index/)
        - elasticsearch 7 的 fork
        - 實作 nmslib & faiss ANN 與暴力法 Exact NN
    - Elasticsearch plugin [elasticknn](https://github.com/alexklibisz/elastiknn)
        - [自幹方法](https://elastiknn.com/posts/tour-de-elastiknn-august-2021/)把 vector 存進 lucene index
        - LSH
    - Milvus
        - 文字上還是用 elasticsearch（不會取代它），但圖片等轉向量後可以用
        - https://zhuanlan.zhihu.com/p/352518729
        - https://towardsdatascience.com/up-and-running-with-milvus-2466161e8b1f

## 廣告處理

- [檢舉表單](https://docs.google.com/forms/d/e/1FAIpQLSf7d8xCAz682vR3WLRVTxqqbWiFXLd6ShZpOnsXXTmAbPFcUA/viewform)
