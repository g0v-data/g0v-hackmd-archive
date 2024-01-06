---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20220216 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis: bil, mrorz, nonumpa
- 線上出席：kukka, cai, 4000
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## 圖片 Hash 效果與搜尋

### Hash length

`bits=12` --> 144 bits hash --> 24 characters in Base64 / 36 characters in Hex
`bits=16` --> 256 bits hash --> 44 characters in Base64 / 64 characters in Hex

### Indexing

Given hash (binary vector)，下面有些 hamming space 裡做搜尋的方式。

應屬於 [Nearest neighbor (NN) & Approximate NN (ANN) search](https://www.youtube.com/watch?v=SKrHs03i08Q) 右下角的 Hamming-based solution。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e995d9317ca6c2c003bb02d385419ccf.png)

- 資料結構 https://stackoverflow.com/questions/6389841/efficiently-find-binary-strings-with-low-hamming-distance-in-large-set
- HmSearch (2013)
    - Paper - https://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.353.1266&rep=rep1&type=pdf
    - JS lib - https://github.com/commonsmachinery/hmsearch-node
- Multi-Index Hashing (2012)
    - C++ https://github.com/norouzi/mih
- GPH (2018) https://jqin.gitee.io/files/icde2018-qin.pdf
- Summary of above techniques (2021) https://szudseg.github.io/kdd21-tutorial-high-dim-simqp/
- 在 Elasticsearch 做 exact NN search on Hamming space (2019): [Fast and Exact Nearest Neighbor Search in Hamming Space on Full-Text Search Engines](https://arxiv.org/pdf/1902.08498.pdf)
    - 原理
        1. 用 painless 實作一個算 64bit 的 hamming distance 的 script ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_cb50829761e63a7e8e0b28f3c54712e4.png)
        2. `m`-bit binary code 可以被切成 `s` 個 sub-code (每段小於等於 64 bits) ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_70735faae67a8ccf07dc8bd9520eeff6.png)
            - 我們可以把 256-bit hash，每 64 bit 切成一個 subcode，只需 4 個 subcode。
        4. 找出跟 `q` 的 hamming distance 小於 `r` 的 vector，就是把 `q` 的那 `s` 個 sub-code，與資料庫裡的 vector 的 `s` 個 sub-code 拿去算 hamming distance 加總
        5. 根據鴿籠原理，如果 `q` 跟資料庫裡的 code `b` 的 hamming distance < `r`，那它們的 subcode 們至少有一對的距離會小於 $\lfloor\frac{r}{s}\rfloor$。用這個原理進行 sub-code filtering 可以減少實際需要計算 hamming distance 加總的數量。
    - 範例 query, 給定 `q` 的 subcode `q1`~`qs`： ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_100ceb4141d6f33ec1d8bac98935e78b.png)
        - L5 的 `query` 是 sub-code filtering
            - [Elasticsearch `terms` query](https://www.elastic.co/guide/en/elasticsearch/reference/current/query-dsl-terms-query.html) 是窮舉，數量有[上限](https://www.elastic.co/guide/en/elasticsearch/reference/7.16/query-dsl-terms-query.html#query-dsl-terms-lookup)
                - `b1`~`bm` 用 `keyword` 會不會比用 `long` 好？https://www.elastic.co/guide/en/elasticsearch/reference/7.16/number.html
            - `r/m-neighbor of qs`: 假設 qs = `00000000` (8-bit sub-code), 那 3-neighbor of `qs` 應該就是所有包含 0~3 個 1 的 code，有 $1+C^8_1+C^8_2+C^8_3=93$ 個
            - 假設 qs 是 64 bit sub-code, r = 10, m = 256/64 = 4, 那 r/m = 2.5。算 2 的話，2-neighbor 就有 $1+C^{64}_1 + C^{64}_2=2080$ 個。
        - L19 的 `functions` 是實際算 hamming distance 用來排序的。
        - L2 的 `min_score` 把距離 cut-off 在 `r`
        - `m` 跟 `s` 差在哪我搞不懂 [name=mrorz]
    - Running demo (包成 container ㄌ) https://github.com/gyang274/visual-search
    - 裡面用 binary hash 是用中研院的 [Semantics-Preserving Deep Hashing (SSDH)](https://github.com/kevinlin311tw/Caffe-DeepBinaryCode)
- [Elasticsearch Fuzzy Query](https://www.elastic.co/guide/en/elasticsearch/reference/6.8/query-dsl-fuzzy-query.html)
    - 算 Levenshtein edit distance
    - 距離最多只有 2



## 遮除電話

https://cofacts.tw/article/5661460621638-rumor

應考慮以下需求：
1. Google 「立法委員手機號碼」後，不會有此頁面，或者是進到此頁面但無法打電話
2. 真的假的 LINE bot 使用者將此訊息傳入之後，不要讓使用者再送一份新的進來
    - 若無法達成，就未來送進來時再處理一次

以下為 staging 測試結果。


### 原文
用一樣的網傳訊息搜尋，得到 100% 相似度
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_42b687ec2b223dab9a935e85ae06a282.png)

看起來 more_like_this query 會選擇電話作為重要關鍵字


### 用「X」遮除中間三碼、或刪掉所有號碼留下名字

chatbot 用完整帶電話的訊息來搜尋，就完全找不到原文了
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2b72d3ab8f5e2c2f372b68b02ac2e114.png)


### 只刪掉名字

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_670d7994274ec5b47bb1cf483d22d168.png)

結果：78% 像
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f842ae6dc162ae736fff5f20747622b1.png)

### 只留下第一段文字

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9ea4c312fb09c04270bf55be74b46bec.png)

結果：找不到
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b620a63d37cd78591090ffd7dd322a1e.png)

### 討論

- 即使是「只刪掉名字」的 solution，78% 的相似度還是不夠高，LINE 使用者仍可能會選擇「找不到我想查的」然後把此隱私訊息送進資料庫。 [name=mrorz]
    - 因此，看起來「真的假的 LINE bot 使用者將此訊息傳入之後，不要讓使用者再送一份新的進來」應是無法達成之事。
- 名字跟電話拿掉，因為電話的次序還在的話，還是對得到是誰 [name=bil]
- 如果 LINE 使用者送「完全一樣」的訊息進資料庫，會因為 article ID 相同，而不會產生新的文章 [name=nonumpa]
    - 不過如果差個空白，就會被算成另一篇了，會需要另外處理 [name=orz]
- 可以讓他找得到但不顯示嗎 [name=bil]
    - 這就要看 elasticsearch 是不是能讓 index 的值跟印出來的值分開的東西了 [name=orz]

:::success
結論:
1. 先把名字與電話通通拿掉
2. 如果有 LINE 使用者再成功送進來，就再手動處理

takedown notice 內文提及？
- 立委辦公室成員反應
- 原需求：Google 「立法委員手機號碼」就會有隱私

考量
- 手機為個人隱私
- 陳情應使用公開管道（過往社群專案亦如是）

執行 by mrorz
- 「只留下第一段文字」的版本
- 「我想補充」處留下 takedown announcement link
:::

## 大松籌備

- 線上大松
- 誰會到: bil, mrorz (提案)
- Good first issue
- [檢討](https://g0v.hackmd.io/cjyi0ezPSzS2Dsgw1oBfmg#%E5%A4%A7%E6%9D%BE%E6%AA%A2%E8%A8%8E): 小精靈放音樂、投影 community builder
- 整點 ~ 10 分是休息時間
- 程式 = 網站的 good first issue https://github.com/cofacts/rumors-site/issues?q=is%3Aissue+is%3Aopen+label%3A%22good+first+issue%22

## 小聚籌備
- 場地借到了 NPO hub 2F


