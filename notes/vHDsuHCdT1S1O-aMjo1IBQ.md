---
tags: AI,vTaiwan 
---
# Whose Opinions Do Language Models Reflect?

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b0f992041b0c4268af6c35644eb3a8e0.png)


這是OpenAI的社群活動，由g0v社群參與者peter紀錄

Language models (LMs) are increasingly being used in open-ended contexts, where the opinions reflected by LMs in response to subjective queries can have a profound impact, both on user satisfaction, as well as shaping the views of society at large. In this work, we put forth a quantitative framework to investigate the opinions reflected by LMs -- by leveraging high-quality public opinion polls and their associated human responses. Using this framework, we create OpinionsQA, a new dataset for evaluating the alignment of LM opinions with those of 60 US demographic groups over topics ranging from abortion to automation. Across topics, we find substantial misalignment between the views reflected by current LMs and those of US demographic groups: on par with the Democrat-Republican divide on climate change. Notably, this misalignment persists even after explicitly steering the LMs towards particular demographic groups. Our analysis not only confirms prior observations about the left-leaning tendencies of some human feedback-tuned LMs, but also surfaces groups whose opinions are poorly reflected by current LMs (e.g., 65+ and widowed individuals). Our code and data are available at this https URL.

講者：Shibani Santurkar

LM 反映了特定的價值
- 來自資料
- 來自使用者
- 來自優化使用者的人

如何了解LM的立場？
- 設定選項
- LOG PROBS
- opinion distribution

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_16f8afb3552510ae0d4c2a133a7b547c.png)

LM 與人類的立場比較
- 跟人類比較
    - 以民意調查結果作為人類的標準
- default opinion: 未有控管，直接回應
- steered opinion 

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7a0ecc90ad2edec82db1e7ec4a6dc0ab.png)

Dataset: Opinion QA
- 問題來自民意調查


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8683467cba2c274459cd400c9403d572.png)

研究對象
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_625b2c137aa8db59f22b7b1626b5d0e8.png)

發現：
越新，越 human-aligned 的LM 反而跟主流民意越不像

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3d73fd9a7b371642f0fd06722d757e98.png)



LM 會與有些族群不合（摩門教徒、寡婦）
目前LM 有高中左右的教育程度

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3b6d2d23935724713e35fe427a49ece7.png)


探究：為何在default的情況下，越 human-aligned 的LM 反而跟主流民意越不像(Less representative)
- 以前的 model: 會有較為多元的回答
- 現在的 model: 回答較為單一
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1e34969d14f1bd86a6f41a7d8ea3e450.png)

下一個問題：在 steered 的情況呢？
- 是否能夠steer LM 以符合特定族群的價值？可以做到的程度為何？
- ChatGPT 是最 steerable 
- 在不同的族群間會有不同的情況
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c89d5289f252bf5dab58a2b8f56a8bb1.png)

下一個問題：一致性
- LM 能夠表現出一定的一致性
- 但是即使是最自由派的LM也會在宗教議題上有保守表現

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1e7ab214a8ad461fa7c046aaf3a7139a.png)


takeaways: 
- 我們應該要從AI應服膺人類價值，提升到要問AI應符合哪些特定族群的價值了

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_cf91e21a2dfb53811435bb6b1bf36580.png)

問題：

1. 目前的研究仍然是美國中心，可以擴展到其他國家嗎？
- 可以，問題在於能否取得資料

2. 可否透過更多的 prompting study來訓練 model?
- 可以。

3. 除了 large poll 以外，能否有其他的 benchmark?
- 目前的研究方法是希望建立標準，不過其實可以透過專家會議等方式來進行比較。
4. 是否會產生其他的風險？例如aligned to the group
- 需要有更 nuanced 的觀察，不過接下來要做的就是討論哪些價值應該要被處理。這會是個困難（tricky）的過程。

5. 




