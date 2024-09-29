# 如何在 GPTs 之上進行開放協作？

> OpenAI 跟 ChatGPT 不是一點都不開放嗎？要怎麼在那上面做開放協作？

好問題，一個閉源的大語言模型怎麼可能做到開放協作呢？不過，至少我們可以就我們能夠做到的部分，盡可能地讓大家都有機會了解「如何將這些大語言模型融入到我們的日常生活之中」。

不能強求 OpenAI 分享同一個大語言模型背後用來訓練的知識與資料，但至少由自己產出的 GPTs 指令，應該是有機會開放出去讓大家了解如何活用的吧？

本次短講將以 GPTs 為例，跟大家分享如何透過 GitHub ，進行 GPTs 指令開放協作的做法

---

最近因為休學的關係很常在一位社群朋友開的咖啡廳鬼混，叫作 cozy cowork cafe

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_47f9fab16c985e94dc141f6d7a786a2f.png)

它是一個為加密遊牧設計的共享咖啡廳，裡面有各式各樣的設施可以使用（例如會議電話亭、沙發區、書櫃、social battery badge、狀態立牌）。有各種奇怪的設計，但要讓大家在剛進店裡的短時間內就理解這些設計並不是一件容易的事，因為如果把它們都寫成一份文件放在書櫃裡的話肯定不會有人把它拿起來看，因為靜態文本無聊又難讀


但大語言模型的好處就是，大語言模型可以幫我們從茫茫的資訊大海中取用我們所需要的資訊。沒有人會讀無聊的靜態文本，但大語言模型可以幫我們讀。這個時候我就想到了 GPTs，作為大家最常使用的 AI 服務之一，建立一個了解這間店的各種公開資訊的聊天機器人對我們來說是一個機會

所以就一如往常地建了一個 GPTs，就跟我上次期末考時用自建的 GPTs 「豆腐的總經小老師」去消化龐大的上課材料一樣，我把一些脈絡指令還有一頁頁菜單的 pdf 檔放了上去

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_25f9fd6dfaa125d12049504fc194011a.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_61d729a565d41ea927b0c1121ac1ba54.png)

但現在問題就來了，老闆之一在我建完這個 GPT 之後就跑過來跟我說這個 GPT 生成出來的東西有一些問題，比方說在要求 GPT 推薦一杯熱茶的時候，卻推薦一杯康普茶，然後就請我透過我的帳號修改指令，然後類似的修改需求前前後後出現了好幾次

然後我就在思考，修改的反饋雖然很重要，但有沒有可能可以在這個 GPT 之上進行開放協作（因為最實用的反饋不可能都是從老闆那邊來，顧客的反饋顯然是更重要的，但 OpenAI 的協作功能顯然沒辦法滿足我們的需求）

接著我就想到或許可以試著把這個 GPT 的設定文件放到 GitHub 上，如果需要修改的話，就直接請他們發 issue 或開一個 pull request 就好了（？

然後就變成這個樣子了

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_57c2441c4a06751405a72aad0afdaee2.png)

然後裡面長這樣

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_cbee792303971c57ab8bcd77726b19b7.png)


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fee3802eb0cb8590d4fbb3b16bb66d97.png)


