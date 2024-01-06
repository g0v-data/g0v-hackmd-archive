---
title: "立法院表決資料分析"
tags: hackpad
---

# 立法院表決資料分析

> [點此觀看原始內容](https://g0v.hackpad.tw/76CBR5VkIQn)


2015/4/18 黑客松討論

主題：立委投票指南表決資料分析
問題：投票指南有很多表決資料，但是提案的敘述一般使用者很難看懂。希望可以讓使用者更容易從表決內容決定自己心中理想的候選人。


### 使用者要什麼東西

- 謝ㄆ：上次我就是在立委投票指南表決這一頁迷路，希望點選某個議題（例如「食品衛生管理法」），可以知道這些表決和議題的關聯性。
    - 選舉前幾天了，謝ㄆ很焦躁要選誰，於是就進了「立委投票指南」網頁。當時很不熟悉各個議題，當時選了一個覺得還算熟悉的「核四」，然後就看到「一整排」的表決紀錄，覺得有點小崩潰。但是當時還是有試著看提案文字，也有看贊成反對，但是還是看不懂。然後就放棄了...
        - 當時謝ㄆ大約知道國民黨對核四的立場，是想透過表決再次確認。失敗之後就依照原本的印象去做。
    - pm5：最重要的是解決「焦躁」這個情緒
        - tag 不是 tag 「核四」，而是「停建核四」，一個明確的命題，不是一個名詞而已
    - 謝ㄆ：可能我當時對議題根本也沒有概念，有沒有可能做「我朋友關注的議題」「環境資訊協會關心的議題」
    - pm5：使用者可能隱隱有一些立場，只是自己講不出來
    - 謝ㄆ：選舉前三天我可能也不會再重新了解議題了，因為時間太趕

- 環資關心的議題：
    - 停建核四
    - 設置溼地保育法
    - 設置海岸保護法
    - 設置國土計畫法
- 同志婚姻合法化


### if我是選民，選前3個月~選前10天...

- 選票還有可能搖擺，還有機會被影響判斷
- 假設：價值判斷一般選民已從各種資訊來源中作出，但他想要了解現在動態民意，以及因各事件而產生的民意變化 =\> 因「議題/事件/價值判斷」而影響「對候選人的偏好」
- 提供服務：「呈現網路即時動態民意」
    - 網友互動：提報更多事件、對候選人的偏好投票

### if我是選民，選前10天...

- 已經不是改變選民價值判斷的時候～？
- 提供服務：「讓選民快速找到相仿價值的候選人」

我想要從議題
->對議題的專業度/議題立場表態 來判斷一個候選人值不值得選
->清楚的價值陳列，讓我輕鬆找到跟我價值一樣的候選人


### 介面發想

1\. 資料來源：hover過去才出現
- 出處：[http://hacktabl.org/taipei-mayoral-election-2014](http://hacktabl.org/taipei-mayoral-election-2014)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ee3c637968717acfa9a2fdd81804a774)
2.互動機制：用顏色標出行動的立場（五個按鈕太多了～？）
- 出處：[http://platoforum.herokuapp.com/comment_534f96653337330002760300](http://platoforum.herokuapp.com/comment_534f96653337330002760300)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0fa30a8a0547d4088000670eee31f2a3)

3\. 網友report機制。出處：[https://fepztw.github.io/](https://fepztw.github.io/)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ade08296e59ea646e4cbda1946772964)


## 4/18 初步成果 demo

### ==問題：立法院表決資料可不可以更容易懂？==


- 投票指南有很多表決資料，但是提案的敘述一般使用者很難看懂。希望可以讓使用者更容易從表決內容決定自己心中理想的候選人。






### 故事是這樣的.....

[http://vote.ly.g0v.tw/legislator/voter/1724/8/?keyword=%E6%A0%B8%E5%9B%9B](http://vote.ly.g0v.tw/legislator/voter/1724/8/?keyword=%E6%A0%B8%E5%9B%9B)

- 選舉前幾天了，謝ㄆ很焦躁要選誰，於是就進了「立委投票指南」網頁。當時很不熟悉各個議題，當時選了一個覺得還算熟悉的「核四」

**![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_937eea5bf38c4934e4d148d85807d29e)

**

    - 故事繼續：.... 看到「一整排」的表決紀錄，覺得有點小崩潰。但是當時還是有試著看提案文字，也有看贊成反對，但是還是看不懂。然後就放棄了...（迷路了！）
        - 當時謝ㄆ大約知道國民黨對核四的立場，是想透過表決再次確認。失敗之後就依照原本的印象去做。


**問題**：
- 提案文字落落長，不會解讀
- 列表頁面無法確定是「程序表決」還是「議案表決」
- 有很多 tag，例如「核四」，但是沒有命題，投票的「支持/反對」無法解讀意義


### 目前解法

- 提案文字落落長，不會解讀
    - ===> == google spreadsheet 協作，落落長的表決內文 summarize，[LINK](https://docs.google.com/spreadsheets/d/1_k0VAwidgJl3mUx62Er0vHpHWrJHf7mz3WvZxoOyd7o/edit?usp=sharing)

- 列表頁面無法確定是「程序表決」還是「議案表決」
    - ===> ==  tab filter

- 有很多 tag，例如「核四」，但是沒有命題，投票的「支持/反對」無法解讀意義
    - ===> ==  把 tag 改成「有立場的命題」，例如「核四」=>「續建核四」「停建核四」

demo: [http://soidid.github.io/voteMeta/build/](http://soidid.github.io/voteMeta/build/)

- 選擇「停建核四」，可以看到歷年來的表決意向結果
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_cf1b56e5bad82dea97e68b851d28bcf1)
- 展開截圖：
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_5bb25c4b5d71293cb4ecdc2b0d610708)
- 點選表決連到「立委投票指南」

### TODO

- 協作方式優化：介面優化、增加投票功能 ... etc
- 要嘗試更多的議題，看看其他議題是否可以這樣做
- 爭議性的“表決”判斷問題=>公投

## 進度

感謝各位的意見，已做了雛型如下：
- 使用者可對表決增加命題、對命題投票，[例](http://vote.ly.g0v.tw/vote/08-06-YS-17-001/)
- 可看立委個人表決立場，[例](http://vote.ly.g0v.tw/legislator/voter_sp/966/8/)



