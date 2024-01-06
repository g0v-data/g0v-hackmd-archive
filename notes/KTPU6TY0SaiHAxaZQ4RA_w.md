# 字形生成論文整理
{%hackmd 6D5WHIqJTDSFQ266FpnqXA %}
# [[1]](https://www.cnblogs.com/Stareven233/p/17112073.html) Few-shot Font Generation by Learning Style Difference and Similarity
## 背景
現存FFG方法很難保證生成結果和參考字形在組件層面上風格一致。
一些研究（MF-Net, FsFont）使用注意力機制捕捉多級風格，但這忽略不同風格字形的差異和相同風格字形的相似性，導致局部失真或風格不一致。
## 模型
輸入為單個內容圖$I_c$，跟多個風格圖$I_s$，輸出結果$I_{cs}$。
1. $I_s\xrightarrow{MSP}風格編碼z$
2. 根據風格標籤計算每個風格的類別中心
3. 將每個類別的中心編碼$z_j$存進內存字典

$I^+$,$I^-$分別是跟$I_{cs}$相同、不同風格的圖片。
$\hat{z}^+$,$\hat{z}^-$分別是對應字體跟其他字體圖片的編碼，用作正、負樣本。
1. $I_{cs}\xrightarrow{MSP}風格編碼\hat{q}$
2. 利用$\hat{z}^+$,$\hat{z}^-$計算cluster-level對比風格損失$L^G_{contra}$、對抗損失、L1損失。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_53770dc811a6fd6176569d31b8af0faf.png)
## Multi-layer Style Projector
字體風格精細複雜，特徵抽取要考慮不同尺度，如component-level, stroke-level, 和even edge-level。MSP可以將多層特徵分別投影到獨立的隱風格空間，編碼不同粒度的風格。
這裡3種尺度分別對應圖片1, $\frac{1}{2}$, $\frac{1}{4}$的原始分辨率，然後通過平均池化和最大池化分別獲取通道方向的（channel-wise）均值和峰值，然後再將其分別投影成K維風格編碼。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2f11f0cc0538b3d9c2d4adc901e56ba8.png =75%x)
## Multi-task Patch Discriminator
* 兩個patch判別器
    * 分別區分內容和風格
    * 僅區分是否正確，不考慮不同類別間的差異
* 多任務判別器
    * 辨別不同的風格/內容
    * 分辨整張圖，卻忽略圖中每個部份的貢獻

結合二者提出的判別器能夠獨立判別圖片的不同區域，有助於$I_{cs}$的局部細節跟groundtruth更一致。
## Generator
基於FTransGAN的encoder-transformation-decoder架構。
通過self-attention和layer-attention匯聚風格特徵，以此捕捉局部與全局特徵。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_736426356000cf78a558c1fe99a8873a.png =75%x)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5544ba623698aa0eb8539b5b8915c95b.png =75%x)
# [[2]](https://www.cnblogs.com/Stareven233/p/17167660.html) SGCE-Font: Skeleton Guided Channel Expansion for Chinese Font Generation
## 背景
之前的方法無法同時顧及局部和全局的訊息。
skeleton直接作為輸入，而不是給判別器加約束。
## 模型
1. $輸入\xrightarrow{Zhang-Suen算法}skeleton$
2. $RGB+skeleton\rightarrow cex$
3. CycleGAN
4. 計算對抗損失（source、target各一個）、循環一致性損失、skeleton一致性損失

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_483167f1488809ac86047399701a79a9.png =75%x)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ebf629954078e4067d0e929f1015ffec.png =75%x)
# [[3]](https://www.cnblogs.com/Stareven233/p/17027164.html) Diff-Font: Diffusion Model for Robust One-Shot Font Generation
## 針對問題
1. font gap
    source和target差異過大
2. font varation
    相似的字體無法區分
3. complicated characters
    無法正確生成複雜字符

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_06ba917ec615881fa1ea536237b90e27.png)
## 模型
1. 字符屬性編碼器f
    將字符屬性（內容c、風格sty、筆畫sk）編碼為隱變量$z=f(c, sk, sty)$
2. DDPM(UNet架構)
    將z作為條件從高斯噪聲中生成字符圖片

不同於StrokeGAN的32維畫筆變量，每一維不是0/1，而是筆畫的數量。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d8ee9341085b9d21725071fe8dec0ad8.png =75%x)

* 擴散階段
    逐步給真實圖片$x_0$添加高斯噪聲，使其成為噪聲$x_T$
* 反擴散階段
    使用z作為條件訓練DDPM，以預測每個擴散階段添加的噪聲
1. 從$x_1$~$x_T$隨機抽樣一個$x_t$
2. $x_t\xrightarrow{添加噪聲}x_{t+1}$
3. $x_t\xrightarrow{DDPM}\hat{x}_{t+1}$
4. 計算$x_{t+1}$和$\hat{x}_{t+1}$的L2損失

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d26989fada2452ed79bc7d42aee0e622.png)
## 指標
1. SSIM(Structural Similarity)
    比較結構相似度、亮度對比度、結構
2. RMSE(Root Mean Square Error)
    計算兩張圖片像素值的均方根誤差來衡量相似度
3. LPIPS(Learned Perceptual Image Patch Similarity)
    衡量圖片在深度特徵空間的距離
4. FID(Frechet Inception Distance)
    衡量生成圖片跟真實圖片在分布上的不同
# [[4]](https://www.cnblogs.com/Stareven233/p/17017964.html) StrokeGAN: Reducing Mode Collapse in Chinese Font Generation via Stroke Encoding
## Stroke Encoding
* 用長度維32的01串，表示漢字是否包含對應序號的筆畫。
* 對筆畫位置、數量、大小、形狀等都沒有約束。
## 模型
* CycleGAN
* 計算對抗損失、循環一致性損失、筆畫編碼重建損失（即預測的生成字的筆劃編碼和真實筆畫編碼的L2范數）

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_26fc4f54ddfb55dc84e9126af755f50e.png)
Stroke encodings似乎沒有輸入Discriminator，僅有用來計算損失
# [[5]](https://www.cnblogs.com/Stareven233/p/16940757.html) Few-shot Font Style Transfer between Different Languages
## 背景
* I2I缺點
    1. 訓練過程分為兩階段：預訓練和微調，要求較高的計算資源
    2. 微調需要成百上千的訓練樣本，數據準備也很繁瑣
## 模型
提出FTransGAN(Font Translator GAN)，無須fine-tuning。
兩個編碼器分別抽取內容、風格表達，拼接後輸入解碼器。
判別器是PatchGAN的設計，局部驗證真假圖像塊。
內容感知注意力網絡（Context-aware Attention Network）跟層注意力網絡（Layer Attention Network），同時捕獲局部跟全局風格特徵。
計算L1損失、風格損失、內容損失。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2e7a0e58da30e465130c5d0f67279b41.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b2ae539706cd38187a1c0e7bd9eb1a9f.png =50%x)
## 指標
1. Pixel-level
    * mean absolute error(MAE)
    * structural similarity(SSIM)
    * multi-scale structural similarity(MS-SSIM)
2. Perceptual-level
    * top-1精度
    * mFID(mean FID)
3. Human-level
    用戶調查
# [[6]](https://www.cnblogs.com/Stareven233/p/16922519.html) MF-Net: A Novel Few-shot Stylized Multilingual Font Generation
## 字體生成目標
1. 保持轉換前後結構一致，使人類閱讀沒有困難。
2. 應從風格字體轉換大部分風格特徵給目標字。
## Language Complexity-aware Skip Connection
不同語言對於局部/全局特徵需求程度不同，可以調整不同卷積層抽取的特徵圖的信息度，取得局部全局信息的平衡。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f2b3edaabc4dc307012502f5dbe7c7f4.png =75%x)

## 模型
context-aware上下文感知注意力模塊通過捕捉全局信息能獲得更大的感受野跟上下文信息。
decoder將內容、風格向量拼接後作為輸入。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7ce06fb85bab560b32c98c7923d090d4.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_062b1e09a9d86cd01705099658968774.png =75%x)
style encoder
# [[7]](https://www.cnblogs.com/Stareven233/p/16898394.html) FontTransformer: Few-shot High-resolution Chinese Glyph Image Synthesis via Stacked Transformers
## Chunked Glyph Image Encoding
基於字形圖片有許多重複的塊這一事實，設計了分塊字形圖像編碼方案，可以合成高分辨率圖片而不過多增加計算開銷。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_33b003cde06f23604102098e97c8fdee.png)
## 模型
利用parallel Transformer避免預測錯誤的累積，且利用serial Transformer增強合成筆畫的質量。
在模型的編碼器中使用掩碼注意力，能夠過濾掉大部分地信息的圖片patch，若沒有這項機制，合成結果會有斷裂/不正確的筆劃。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_de5e8284091911ed956980e52b0df27a.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0e106f223ee5a3a6c115a81d5096a827.png)
# [[8]](https://www.cnblogs.com/Stareven233/p/16727713.html) Look Closer to Supervise Better: One-Shot Font Generation via Component-Based Discriminator
## 模型
Generator基於SAGAN，雙編碼器解耦風格、內容特徵，採用AdaIN在Mixer中混和風格和內容並得到生成圖片。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b88606f08650f63e435ad2f3784a8895.png)
## Component-Aware Module
component extraction：每個漢字都可以遵循深度優先閱讀順序從而拆分成一個獨特的組件集，將組件抽取過程視作序列問題。
為生成器提供多尺度的風格和內容監督，促使其實現部件級別的風格內容解耦，引導生成器保持多尺度風格一致，字形正確性和圖像真實性，使它更多地關注字形的局部細節。
CAM得到的信息將通過反向傳播反饋給生成器，能夠端到端進行訓練（各模塊都不用預訓練）。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_57739caec704becd01a79295d02f861d.png)
## 指標
SSIM、RMSE、LPIPS、FID
# [[9]](https://www.cnblogs.com/Stareven233/p/16649554.html) Few-Shot Font Generation by Learning Fine-Grained Local Styles
使用基於transformer的cross attenstion機制，使模型能夠更加容易匹配內容字和風格字的空間特徵，風格字的風格能完美地遷移到目標字的對應位置

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7de9fac505548e9147b76168b3b0695a.png =75%x)
## Style Aggregation Module(SAM)
* 即為Attention機制
* $F_s$、$F_c$分別是內容字和風格字提取出的feature map
* $F_s$、$F_c$ $\xrightarrow{線性變換}$ 注意力機制的Q、K、V三個矩陣

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c25b563e79dde442a38c238fbc39294e.png)
## Reference Selection
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_501029749eaaa2933baf52964cad51dd.png =50%x)

1. 基於[分解表](https://github.com/cjkvi/cjkvi-ids/blob/master/ids.txt)，將每個字符分解為部件樹，定義級別0、1、2的部件為高級部件(conspicuoius-level)
2. 選取參考字集
    * 參考字集應覆蓋盡量多的高級部件
    1. 選取一個小的子集(通常包括100個字符)
    2. 將包含兩個以上新部件的字符加入參考字集
    3. 當參考字集達到固定數量，即得到風格參考字集和它相應所包含的部件
3. 內容-參考映射
    為每個字符找出k個參考
    每次都找出跟目標字符有最多公共部件的參考字符（如果有多種選取方式，就選有最多部件且具有相同結構組成的字符）
    選完後將其從參考字集中移除，繼續選取下一個參考字符
## Self Reconstruction
黃色流程為Self-Reconstruction，用目標字風格與來源字內容重建目標字
綠色流程為參考字提取風格跟來源字內容生成目標字

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8d1cedbfd07a2ab6f990c322011959cf.png)
# [[10]](https://www.cnblogs.com/Stareven233/p/16649550.html) DG-Font: Deformable Generative Networks for Unsupervised Font Generation
因為內容相同的兩種不同風格的字體，它們的每一筆畫都是對應的

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a30f1eae6be852e6a3d9fc5472e11161.png =50%x)
## 模型
* Style Encoder
    從Style Images學習Style Representation
* Content Encoder
    提取Content Images的結構特徵
* Mixer
    混和$Z_c$和$Z_s$來生成輸出字符
    使用AdaIN方法將style特徵注入Mixer
* FDSC(feature deformation skip connection modules)
    預測一個位移映射map，去對low-level的特徵圖做變形卷積
    保留文字本身的模式（筆畫、偏旁部首）
* Multi-Task Discriminator
    對每個風格同時進行判斷

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_75ffedae121b25061fc37694221a5d56.png)
# [[11]](https://www.cnblogs.com/Stareven233/p/16608500.html) Multiple Heads are Better than One: Few-show Font Generation with Multiple Localized Experts
現存FFG方法都不足以捕捉多樣局部風格或者保存未知語言的全局結構
1. 通用風格表示
    同一字體的不同字共享同一種風格
2. 基於組件的風格表示
    同一種組件共享同一種風格
    效果好，但編碼器與目標語言域的特定組件標籤緊密耦合，阻礙處理那些未知組件或跨語言的字體生成
3. 多局部專家風格表示（本文）

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_23c29a5d9173925d1fe126f8c3a52d31.png)
## 分類器
風格特徵分類器$Cls_s$
組件特徵分類器$Cls_u$
只有訓練時使用，用來預測風格/內容標籤

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1a8d99895e97e7114e10ec17052465a1.png =60%x)
若得到均勻預測，表示分類器無法分類（例如將風格特徵給內容分類器）

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_23956cceee50c2f27f3b16602331cc0a.png =50%x)
任一條邊表示專家和對應組件之間的預測概率，由組件分類器$Cls_u$給出
目標是找到一個邊集來最大化預測概率
## MX-Font
* 可以捕捉多個局部風格
* 不限於某一語言
* 有一個多頭的編碼器（多個局部專家），每個專家學習不同局部概念，而不是一個專家對應一個組件
* 利用分類器防止不同專家學習同一個局部組件

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_da912379e4278352234b7264fd24abf1.png)
# [[12]](https://www.cnblogs.com/Stareven233/p/16577120.html) XMP-Font: Self-Supervised Cross-Modality Pre-training for Few-Shot Font Generation
當目標語言的字庫很大，或是難以取得許多目標字符，用卷積編碼器直接抽取的風格不夠可靠，對字形結構和字不同區域的關注有限
* 使用筆畫標籤代替組件標籤（因為筆畫只有約28種，比組件少多了）
* 使用統一多尺度風格表達
    用跨模態transformer編碼器，兼顧筆畫、組件和字符級的風格
    * 自注意力層利於捕捉局部和全局風格特徵
    * 自監督預訓練有助於學習筆畫對齊
* 基於LSTM的筆劃損失跟風格內容解耦網路
    * 考慮空間信息轉換，增強模型可靠性
    * 為了有正確的筆畫順序，而不是存在就可以
## 模型
* 輸入
    1. 某一風格的字符圖片
    2. 相應字符的筆劃標籤序列
預訓練時，編碼器後面接一個卷積解碼器和筆畫標籤預測器（用於重建輸入）
之後凍結跨模態編碼器

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c30627da4c60722374ded36e5c512e0a.png)
## 跨模態編碼器
* 將輸入數據轉換為兩個分開的嵌入序列（字符嵌入、筆畫嵌入），筆畫序列由28個筆畫嵌入組成，按書寫順序排列
* 每個筆畫嵌入都是三種嵌入的總和
    1. 筆畫標籤嵌入
        512維，從筆畫標籤映射而來
    2. 位置嵌入
        512維，筆畫的位置索引（0~29）投影而來
    3. 模態類型嵌入
        512維，0表示筆畫，1表示字符圖像

