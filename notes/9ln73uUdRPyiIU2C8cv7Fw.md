# Diffusion Model相關技術
### template
* Category:
* Introduction:
* Advantages:
* Disadvantages:
* Link:(paper, github, introduction articles or videos...)

## Stable Diffusion Model/ SDXL
* Category: Base model
* Introduction: 使用latent diffusion作為基本架構，訓練在internet-scale dataset上，有強大的
* Advantages: 結果多樣性強，並且質量高
* Disadvantages: 要達到其他特殊目的需要通過其他技術處理
* Link:

## Text Inversion

* Category: embedding optimization
* Introduction: 建立特殊詞匯與特定圖像的對應關係，使得模型學會一個新的圖像概念
* Advantages:
* Disadvantages:
* Link:

## Dreambooth

* Category: Finetune
* Introduction: 挑選一個不常用的詞（比如css），並且使用某個物體的幾張圖（比如小狗A），通過finetune讓模型學會css即小狗A這個指代關係，這個技術可以用來做image editting等
* Advantages: 相對Text inversion能力更強大，因為text inversion能學習的參數很少，只有text embedding的大小
* Disadvantages: finetune的成本相較來說比較大
* Link:
 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ba6562a801b62fbda309b800483b90cb.png)
 
 ## ELITE
 * Category: Finetune/embedding optimization
 * Introduction:作者發現 word embeddings 中越深的層包含了更加主要的concept，而其他層則描述了較爲無用的特徵，以此作者通過構建全局網絡Global Mapping和局部網絡Local Mapping 來幫助diffusion model 學習圖片中的概念，全局網絡通過fine tuning text transfoemer 來讓模型學到主要的概念，局部網絡通過對物體的mask來標定物體從而提供給更多的概念細節和可編輯性。
 * Advantages:僅需一張圖片便可以讓模型學會concept
 * Disadvantages:concept的生成效果還有待改進。
 
 ## BLIP-Diffusion
 
 * Category: adapt
 * Introduction:作者使用經過pretrain的VLM-BLIP2 來引導diffusion model 進行subject learning，在訓練階段作者通过合成具有随机背景的主体来合成输入图像，然后，BLIP-2 的任务是产生subject prompt embedding，然后由潜在扩散模型用于生成输出subject image。图像编码器在预训练期间保持冻结状态。
 * Advantages: 結合VLM的知識來引導擴散模型生成，效果拔群。
 * Disadvantages: 需要較大的訓練資源
 