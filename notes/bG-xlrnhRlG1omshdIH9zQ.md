# **Image Processing _ Lecture2**
**OUTLINE**
- Elements of Visual Perception
- Light and the Electromagnetic Spectrum•Image Sensing and Acquisition
- Image Sampling and Quantization•Some Basic Relationships Between Pixels
- Introduction to the Basic Mathematical Tools Used in Digital Image Processing

Image Sensing
- Scene
    - molecules
    - buried rock formation
    - ...
- illumination
    - radar 
    - infrared
    - x-ray
    - sun
    - ...


0 < f(x,y) < unlimit
(i,j), i=row, left to right: 0~255
       j=column, top to buttom: 0~255

- [L~min~, L~max~ ] is called gray scale
- shift this interval to [0,L-1]
- l=0 is black, l=1 is white, all intermediate value are shades of gray

*Quantization: process of converting continuous nalog signal into its digital representation
[link text](https://electronics.stackovernet.com/cn/q/57706"Quantization signal")
 Saturation: highest intensity...
 
 Noise:grainy twxture pattern
 
 spatial resolution空間上的解析度(畫面顆粒狀):用多少畫素來存放一張圖
 intensity resolution強度上的解析度(色彩區隔):表示用多少bits來存放一張影像
 
 
 - process of using known data to estimate unknown values
 - 
     - resampling
     - [link text](https://en.wikipedia.org/wiki/Bicubic_interpolation#/media/File:Comparison_of_1D_and_2D_interpolation.svg "title")
    
    
4-neighbors of p, N4(p )
four diagonal neighbors[ND(p)]
- 8-Neighbors: N8(p )=N4(P )+ND(P )
    - some neighbor points fall outside ...
adjacency
    4-adjacency(aka first order connectivity)
        Two pixels p and q with values from V are 4-adjacency if q is in the set N4(p)
    8-adjacency(aka Second order connectivity)
        Two pixels pand q with values from V are 8-adjacent if q is in the set N~8~(P ).
    m-adjacency:mixed adjacency
            - q is in N~4~(P )
            - q is in N~D~(P ) and the set N~4~(p )∩ N~4~(q) has no pixel in V.

Connected Components


HW:
- resize the lina image 512, 256, 128, 64, 128, 
- Find 4-adjacency, 8-adjacency, and m-adjacency of a pixel.


Image defference:
image correction:
ROI:







//影像處理常在"減"，我們要的 usually equal "原圖-我們不要的部分"




# word
-spectrum(n):光譜
-luminance(n):亮度。是表示人眼對發光體或被照射物體表面的發光或反射光強度實際感受的物理量，亮度和光強這兩個量在一般的日常用語中往往被混淆使用。簡而言之，當任兩個物體表面在照相時被拍攝出的最終結果是一樣亮、或被眼睛看起來兩個表面一樣亮，它們就是亮度相同。
-photopic(n):明視覺。人眼使用**三種類型的視錐細胞**來感測三個顏色帶中  的光。明視覺是在**光線充足**的條件下的眼睛視覺。與暗視相比，明視視  覺能夠使視錐細胞介導的顏色感知和更高的視敏度和時間分辨率。
-Quantization(n):量化。量化是將輸入值從一個大集合（通常是一個連續集合）映射到一個（可數）較小集合的輸出值的過程，通常使用有限數量的元素。
在數位訊號處理領域是指將訊號的連續取值（或者大量可能的離散取值）**近似**為有限多個（或較少的）離散值的過程。量化**主要應用於從連續訊號到數位訊號的轉換中**。連續訊號經過採樣成為離散訊號，離散訊號經過量化即成為數位訊號。注意離散訊號並不需要經過量化的過程。訊號的採樣和量化通常都是由ADC實現的。
split(v):切開、撕裂、使破裂 ; (n)分割

分類分析(Classification)：已經主觀決定出分類，例如決定好將會員分成三類：低消費群、中消費群、高消費群。依照消費金額，主觀地將所有會員分進去這三類，主觀地決定哪兩個金額門檻，可以把會員分成三群，例如平均每月消費999元以下者為低消費群、1000~9999元中消費群，10000元以上高消費群。
重點在於四個字：**人為主觀**。三類是人決定的、金額門檻也是人決定的。

群集分析(Clustering)：
這項分析可謂博大精深，Clustering也是在做分群，其中K-mean演算法，是最為人熟知且常用的演算法，透過不同演算法的分析技巧和特性，分析人員在演算法下，可以找出較適合的分類數量(分幾群)，可能不是如上分成三類，而是分A~E五類，甚至到了最後，分析人員會對於到底要分A~E五類還是A~F六類而猶豫不決。但不論分成多少類(多少群)，【群集分析(Clustering)】的演算法會直接把所有樣本分進不同的類別(群集)裡，等於是演算法會將分好的會員直接計算出數據，例如A類的會員平均消費金額多少、B類的...等等以此類推，進而去描述不同群會員的相貌。重點在於四個字：**系統客觀**。不管是分類或是計算而得的門檻，都不是由人去決定的，而是透過演算法的技術去訂定，人能決定的，只在於選擇哪種演算法，和當演算法跑出幾個很相近的(最佳)分類結果時，要選擇哪一個分類。