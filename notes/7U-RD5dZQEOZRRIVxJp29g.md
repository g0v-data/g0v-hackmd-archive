# Signal Detection Theory (SDT)

## 目的：分辨「信號」和「噪音」
- 分辨噪音比分辨信號還要更重要，因為資料當中有大量的噪音。
- 舉例來說：雷達偵測敵機
## [Problem with Classic Sensitivity Measurement]
- Fail to consider internal noise
主要noise來自於內在
外在noise>內在noise→斜的那條線
內在noise>>外在→仍是平的那條線
- Fail to consider decision criterion(False alarm rate)
==訊號==：實驗task需要看的東西(例：找一個穿紅衣服的人)
==噪音==：實驗不需要的東西(例：其他穿黑衣服、綠衣服的人)
## [來源]
- Systematic deviation(可找到)
- Measurement deviation(可找到) 
量測誤差 (一把尺172.3 172.4分不太出來)
- External noise 
像是光，聲音,distractoor
- Internal noise 
神經的raising potential(啥事都沒做，他本來就有反應，濃度到了就反應)
## [找noise的方法]
- Noise的出現符合柏松分配：單位時間內會發生事件的次數
又依中央極限定理可以假設其平均數及標準差
- Moment 估計單位時間
在實際應用上隨著目的不同會避免不同的error
- Psychometric function
越陡量測會越精確(小小的刺激變化範圍內即可提升大量的正確率)
兩個分配相減，平均數相減，變異數相加(假設noise是可相加的)
# Ideal Observer
- Limited only by noise 
- Matched flter
- Full knowledge about the experimental condition
[舉例來說]
假設Rod是圓柱形的    
越長感應越好越敏感(但noise也越多)
## [Rod Retinal Read-out]
- Constraint:
    - 需要吸收光子才能引發反應
    - The response has to be transmitted
    - make a noticeable impact(e.g.,above threshold)dormstream
- For sparse signal
    - Averaging does not increase the signal to noise ratio but overwhelming the signals
        - only one rod absorb a photon but all rods provides noise
    - A mechanism that picks up the target photoreceptor but suppresses other signals and desirable 




# Identification
- Maximize percentage correct
# Bayesian Ideal Observer Analysis
- Estimate likelihood function
    - Parametric
        - Gaussian assumption
        - Nature image statistics
- 分析東西的時候很煩，前面的東西可能遮住後面的東西。
- 作法：
→收集幾萬張圖片，蒐集圖片的線段
→用likelihood function估計挑出物體邊界
- Minimal moan squared error estimation

# Code
- Receptive field
    - classic
    - Reverse correlation
        - impulse的定義是寬度無限窄(哪裡找?)
        - 系統常是非線性
        - 把刺激都加起來，如果刺激是會幫助細胞反應的話，加起來就會是正；如果會抑制細胞反應的話，加起來就會是負。
        - 刺激不能有bias，不能有過多的東西
    - kernals
        - 要做到上面那點，刺激的量需要很大，且只能出現一次
        - sequence kernals
- Natural image stastics
    - 傅立業轉換
    - 物體接近的部分，亮度差不多，彼此之間高相關
- pupulation coding
    - 怎麼用細胞去code一個物品
    - sparse coding
        - 用每一種neuron組合去code一張圖片)
            - 具有容錯機制
            - 很沒有效率
        - 電腦的話一種組合就是一張image
            - 沒有容錯機制，code錯一個就會變成其他東西

# Linear system
- 怎樣算一個線性系統
==f(x)+f(y)=f(x+y)==
==f(a^x)=af(x)==

# Convulution
- Example
    - Elurring
    - Filtering
    - Sum of random variable
- Other relevant major application
    - System identification with impulses
    - Convolution theorem and Fourier transform
- 找出系統中最大的反應
<p style="color:white;">jojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;akjsvjojodkajvn;kajdvn;akjsdvb;a</p>









