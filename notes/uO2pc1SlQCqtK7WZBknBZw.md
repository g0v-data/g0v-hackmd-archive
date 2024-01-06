---
tags: cofacts
---

Cofacts Hackath57n 協作頁面
=====

:::info
- g0v slack channel：`#cofacts`
- 🤝 地點：
- [Proposal slides](https://docs.google.com/presentation/d/1KEosMzwvOU1fHtBLoMe_X7d-weecTJ_S213g9f7Cr3c/edit#slide=id.p)
- 坑主：bil, MrOrz
:::

## Cofacts／按讚回應做功德 :pencil: 

💼 **今日任務**：參與 cofacts.tw/articles 資料庫協作查核。
🙏 **徵求**：會上網查證訊息的人

想跟大家一起來做下面 3 件事情——

### :zero: 加 Cofacts 好友
https://line.me/R/ti/p/@cofacts

### :one: 幫寫得好的回應按讚 :thumbsup: 

最新查核列表：https://cofacts.g0v.tw/replies

每則編輯所寫的回應，點進去後在左下角有大拇哥。
向上的大姆哥 :thumbsup: 表示回得還行
向下的大姆哥 :thumbsdown: 表示回得真爛
目標是有累積很多篇向上的大拇哥！！！！＝Ｄ :thumbsup: :thumbsup: :thumbsup: 

向上的大姆哥不用填理由，可以直接送出。(向下的要喔XD因為想要改進)

### :two: 回應「等你來查」的訊息
找到自己有興趣的訊息，進行回應。

https://cofacts.g0v.tw/hoax-for-you

若查到一半，也歡迎使用「我要補充」，把目前找到的資料貼進去，也簡短分享一下自己查不到的部分！

有任何問題歡迎提出 :D

:::info
詳見 [**闢謠教學**](https://cofacts.tw/tutorial?tab=bust-hoaxes)。
:::

💼 **坑**：逐字稿經驗分享
- 試試看 Cofacts 上針對影片、圖片、聲音的逐字稿共編功能
- 共編逐字稿時的習慣？（如何標記時間、分開內容等等）
- 聽打時的操作習慣？

- - -

## Cofacts／寫 code 做功德 :computer: 

💼 **坑**：Good first issues。請見：

- LINE bot (NodeJS, Svelte (LIFF)): https://github.com/cofacts/rumors-line-bot/labels/good%20first%20issue
- Community builder (React) https://github.com/cofacts/community-builder/labels/Good%20first%20issue
- Website (NextJS, ReactJS) https://github.com/cofacts/rumors-site/labels/good%20first%20issue


🙏 **徵求**：React.js, NodeJS 開發者

:::info
詳見 [**開發者入口**](https://beta.hackfoldr.org/1yXwRJwFNFHNJibKENnLCAV5xB8jnUvEwY_oUq-KcETU/https%253A%252F%252Fhackmd.io%252Fs%252Fr1nfwTrgM)。
:::

💼 **坑**：AI 訓練家經驗分享
- 用用看 Cofacts 在 Hugging Face 上的 dataset https://huggingface.co/datasets/Cofacts/line-msg-fact-check-tw
- 單一 dataset 多 table v.s. 每個 dataset 一個 table
- What to put in README
- Dataset 是否可以實際載入？

🙏 **徵求**：訓練資料從 Hugging Face 抓的人


## 協作

https://cofacts.github.io/community-builder/#/bignum?start=2023-08-26T10%3A00&panels=feedback&panels=comment&panels=replied

- Jungwon - Korean translation proofreading for video subtitle
- Anger & Bird - Debugging Cofacts' huggingface dataset format issue
  - lineterminator='\n', or engine 換 python
  - 如果要從csv檔下手，可以把所有string data裡的 `\n` 替換成 `\r\n` 
    - Default 的 lineterminator 應該就是 `\r\n` ( os.linesep )
    ```
    import pandas as pd
    '''
    csv_file_reader = pd.read_csv('articles.csv', iterator=True)
    for batch_idx, df in enumerate(csv_file_reader): # error
        pass
    '''
    data = []
    with open('articles.csv', 'r') as inputFile:
        data = [ d.replace('\n', '\r\n') for d in inputFile.readlines() ]
    with open('success_articles.csv', 'w+') as saveFile:
        saveFile.writelines(data)
    
    csv_file_reader = pd.read_csv('success_articles.csv', iterator=True)
    for batch_idx, df in enumerate(csv_file_reader): # success
        pass
    ```
    > [name=Bird]
- 承甫 看 issue

### 跳舞 :dancers: 

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_16bc51cd66bb465eaab3f13e27cbe4fa.png)
> [Image source](https://prtimes.jp/main/html/rd/p/000000254.000041300.html)

- peter
- skyler
- 豆腐
- Ted
- lydia
