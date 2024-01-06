---
title: g0v AI 機器人 aka 找專案分類帽
tags: AI, chatgpt
---
# g0v AI 機器人 aka 找專案分類帽

:::info
- 坑主：slack @ichieh
- slack channel： #g0v-aibot
:::

---

## 專案起心動念
- 每次新手加入 g0v，都想知道可以做什麼，因此常常會需要長期參與者幫忙當分類帽，看看有沒有適合的專案可以加入。
- 有人會問，請問 g0v 有沒有ＯＯＯ 類型的專案，希望有機器人可以直接回答這個問題

---

## 作法
- ChatGPT 的出現感覺可以拯救已經 program hub 9.0 的進度

---

### 不會寫程式的我&大家
- 使用現有的工具 [DocBots](https://docsbot.ai/app) 把 g0v data base 的資料灌入

---

### 會寫程式的大家
- 會寫程式的大家：用 chatGPT 訓練一隻有 g0v data base 的機器人來專門回答問題
    - [我看不懂但好像可以的解法](https://betterprogramming.pub/how-to-build-your-own-custom-chatgpt-with-custom-knowledge-base-4e61ad82427e)
        - pip install openai
        - pip install llama-index
        - pip install google-auth-oauthlib
        - python
    - [flower framework](https://flower.dev/)

---

## 資料
- [官網](https://g0v.tw)
- [g0v database 原始檔案不要編輯](https://docs.google.com/spreadsheets/d/1C9-g1pvkfqBJbfkjPB0gvfBbBxVlWYJj6tTVwaI5_x8/edit#gid=1563040282&fvid=1102076775)
- [g0v chatbot database 合併上面的 database 可以複製編輯](https://docs.google.com/spreadsheets/d/1jB-8uR30OE4EBlCcLr2XOZb9kU4amoPH76U8OxOymmI/edit?usp=sharing)
### 0408 成果
- [sample code](https://colab.research.google.com/drive/1QG1TRdgRBMhqMxPxCIvDMMGfFhw19-mo?usp=sharing)
- [參考文檔：llama index](https://gpt-index.readthedocs.io/en/latest/)
- [code中要用的資料](https://drive.google.com/file/d/12uPW1vpeLNhncvFjEBOxbFiL9157mdR0/view?usp=sharing)
- [live demo 影片](https://www.youtube.com/watch?v=FG9LHt80uBA)


---

## 先前成果
- DocBots：需要再加一些 prompt、有使用上限
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_85186cea87762707fedaa66c54285c3e.png)

---

## 說到闢謠你會想到....

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6dc554d8e021703272abe40b7777ec49.png)

---

## 所以機器人說什麼

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8e299f46e327da60235bbe47c9f45166.png)

---

## 歡迎大家一起來救救機器人

### 2023/04/08 大松討論
- ky database 找坑
    - 使用者
        - 找有主坑>>覺得可以先專注在這塊
            - 找坑主認領資料庫裡的提案
            - 讓機器人可以列出資料庫裡有興趣的提案
            - g0v 人力資源部需求表
            - https://docs.google.com/spreadsheets/d/1iuHB3nrtz09BvOwdZdX1YL7MrFq_ZeV2SgYwotZfhjQ/edit#gid=0
        - 找無主坑

- ronny 做的歷代大松提案逐字稿轉換：https://github.com/g0v/g0v-proposal-text

- 成果可以看上面的程式碼

### 其他資料

貢獻者的影音發言語料，聚焦明確專案的側寫與採訪
- Podcast 零時電台 
    - 專案主題導向，容易標記「專案標籤」
    - https://linktr.ee/g0vpodcast
- 歷年提案短講成果報告 youtube 影片
    - 專案主題導向，容易標記「專案標籤」
    - https://www.youtube.com/@g0vTW
- Why 開坑？來蒐集 g0v 坑的開坑故事 (有部分是採訪寫手採訪坑主團隊所寫成的文章，但都算是聚焦專案內容，比起一般媒體報導來說更聚焦)
    - 專案主題導向，容易標記「專案標籤」
    - https://g0v.hackmd.io/@jothon/keng/https%3A%2F%2Fg0v.hackmd.io%2F93xg-Gv2TyiiEwenLLEKQw
- 松後推坑，介紹每次大松的提案，產出文字描述
    - 專案主題導向，容易標記「專案標籤」
    - https://g0v.hackmd.io/@jothon/afterg0vhackathon/
- 社群九分鐘，每月整理 g0v 事件
    - 專案主題導向，容易標記「專案標籤」
    - https://g0v.hackmd.io/@jothon/community99/
- g0v.hackmd 
    - 專案主題導向
        - 文件有 tags 則容易標記「專案標籤」
        - 文件如果沒有 tags 則不一定容易標記
    - https://g0v.hackmd.io/
- g0v Slack archive
    - 有一些「頻道=專案」，其他則不一定
    - https://g0v-slack-archive.g0v.ronny.tw/

結構化的資料
- 成就系統 https://badge.g0v.tw/
- John 整理過「專案、github 帳號、youtube 影片」對應成果 https://chunyenhuang.github.io/awesome-g0v-projects/#/
- g0v database https://docs.google.com/spreadsheets/d/1C9-g1pvkfqBJbfkjPB0gvfBbBxVlWYJj6tTVwaI5_x8/edit
    - 200 個專案清單
- [ky 的人力徵求](https://docs.google.com/spreadsheets/d/1iuHB3nrtz09BvOwdZdX1YL7MrFq_ZeV2SgYwotZfhjQ/edit?usp=sharing)
> [name=ael]
> 提案者 id 也很適合連結 
> 另外，也許可以不只抓提案？可以抓 Slack archive? 
> https://g0v-slack-archive.g0v.ronny.tw/


待評估是否合用的資料來源
- 中外媒體報導，這類文本比較會參雜更多不一定與社群相關的內容，有英文、日文等
    - https://docs.google.com/spreadsheets/d/1YaD9e3HQ19ft2lSz_B9nnxjw8A-4Tbfain9OvnS38aw/edit#gid=0


### 應用情境

- 找坑找專案
- 是否適合擬人化、取名稱



