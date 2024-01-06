---
tags: cofacts, meeting note
---

20181010 會議記錄
=====
蝴蝶、文武、bil、MrOrz
## 程式進度

### 主機升級

- Linode 4GB
- Production Elasticsearch 1.5GB ram; staging 1GB;

### URL preview
PRs:
- https://github.com/cofacts/rumors-site/pull/140
- https://github.com/cofacts/rumors-api/pull/106
- https://github.com/cofacts/rumors-site/pull/141

### Tagging 
> btf

把資料整理乾淨了

Orz:
data cleaning 的手段可以 apply 到其他文章嗎？

蝴蝶：
只是把垃圾字元或是網址濾掉，剩下的都是有意義的字

Orz:
有辦法自動 data cleaning 嗎？

蝴蝶：
可能有些可以，但像這個是照格式濾掉一些東西，應該還算

新的東西進來之後，在經過一樣的程序就可以用

這是 generalize 的 data cleaning，沒有針對特定主題做，所以新主題也 ok

Orz:
現在有 URL summmary，會有更多的字可以用

但 opendata 不知道怎麼做，hyperlinks 是 array of objects，要在 CSV 裡包 JSON 還是 normalize?

蝴蝶：
CSV 裡包 json 怪怪的，那不如一開始就 json。

normalize 吧。

Orz:
那就丟掉 articles & replies 的 hyperlinks field，直接吐 urls index 吧。2GB，連 HTML 都有。

是說開放 `urls` 是重製資料，這會不會有著作權問題，可以合理使用嗎？

orz:有沒有辦法在GCE上面弄一台chrome的機器，平常關起來需要時打開來的機器？

想做 pipeline:
1. 從 linode 的 production elasticsearch backup esdata 到 google cloud storage
2. 在 GCE 上的 cron 會去拉這個 DB backup，mount 到會跑的 elasticsearch，跑 opendata extraction script，產出各個 index 的 opendata (xxx.csv.zip)
3. 把 xxx.csv.zip 們丟上 GCE 給大家下載


蝴蝶：要排程嗎
orz:我們要先把備份撈出來，然後打開一個elastic search，然後跑open data的instrution code
我只要公開GCE的連結他就可以吐結果來

:::success
修改 opendata:

1. 開放 `urls` index 到 opendata
2. 需要再詢問 `urls` 可不可以放 opendata Orz
3. 排程需要再研究，目前先丟到 GCE 再說 --> Orz 會做
:::

### iOS 按鈕 bug
https://github.com/cofacts/rumors-line-bot/issues/105

## Workshop 整理分享
> Bil
> 


來 workshop 的人提供下面的想法：
參與者說學到很多，帶得很細。

這次 workshop 帶的是思辨與整理，跟事實不太一樣，closed chatroom 都是價值觀的散步，如果你有類似價值觀就會轉傳。

大家都說是滿好的討論機會，可能是覺得不好的不會來主動說吧。

Jason 建議時間要長一點，可能要兩到三個小時才拿把它做完。大家還在熟悉，時間就結束了。

https://g0v.hackmd.io/s/Hklp-iqHq7

workshop 來的人可能比較同溫，但看大家遇到問題的質疑，可以理解站在中性來討論是比較困難的事情，大家還是會有情緒、會用反詰的語氣來質問原文。

另外對法規的不熟悉，會讓自己對文章很不信任。

另外，即使是與會來賓，也會把性解放與放縱搞混。

## Interview from NTU undergraduate
- Email 主旨：[g0v-talks] Request for Interview on Fact Checking Research
- Link: https://docs.google.com/document/d/1tdysg3_bj291D1rS2fJAxZa5yuMT6jbqHzaYHZ2A8_k/edit?usp=sharing

## 11 月小聚

- 11/11 (日) 雙十一闢謠節
> 鼓勵大家闢謠換購物金（誤
> 謠言闢一則送一則
> 謠言翻倍送


### 地點：tmot

tmot 搬家了！！變成比較大一點，但也遠一點，在昆陽站附近。

需要場勘 + 新的「只有前方的走法」 + 大肆宣傳地點換了這件事情。

> FB group 討論中

## 貼圖O2O

> 選一些給 Hazel 去問

Bil:
被 LINE 打槍的我們就出，畢竟錢也付了。

Orz:
我會想貼在筆電上的只有「我到底看了什麼」那張（真的假的）。

其他真的會有人想貼嗎？

Bil:
Lucien 的貼紙在 summit 很受歡迎。

不要小看「轉發不會有好運」貼紙了，大家都很想要蓮花版的「轉發也不會有好運」

UCCU 應該也會有很中二的人想貼吧。

文武：
我會想貼「長度太短」。

:::success
試著把被 LINE 退回的貼圖都做成貼紙ㄅ～
:::

## [LINE Boot Award](https://www.line-community.me/awards/)
> GGM 沒來。

## Messenger bot 進度
技術上，使用者看起來可以分享到 bot（[相關 slack 對話串](https://g0v-slack-archive.g0v.ronny.tw/index/channel/C2PPMRQGP#ts-1538754278.000200)）
![]』(https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c48664c1451598e513c1e95455798162)
