# Diffusion Model相關技術
### template
* Category:
* Introduction:
* Advantages:
* Disadvantages:
* Link:(paper, github, introduction articles or videos...)

## Stable Diffusion Model
* Category: Base model
* Introduction: 使用latent diffusion作為基本架構，訓練在internet-scale dataset上，有強大的
* Advantages: 結果多樣性強，並且質量高
* Disadvantages: 要達到其他特殊目的需要通過其他技術處理
* Link:

## Zero 1-to-3
* Category: Finetune
* Introduction: 使用大量多視角data做finetune，並在輸入引入camera pose，使模型能生成有一致性的novel views
* Advantages: 有感知方向的能力，用在3D reconstruction任務中時可以保持目標的consistency
* Disadvantages: 由於經過大量data finetune，可能失去原本的能力，比如多樣性及高質量的結果
* Link:

## Text Inversion

* Category: embedding optimization
* Introduction:
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