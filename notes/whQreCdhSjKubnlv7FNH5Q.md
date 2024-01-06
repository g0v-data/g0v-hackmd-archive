# AHG暑期報告
# 7/18 報告
## 家倫學長報告
### Recording enhancement
DTLN、GRU based DTLN、LSTM-GRU based DTLN
普、優、最佳
PESQ：
    
    10dB-：LSTM-GRU
    10dB+：GRU
STOI：

    10dB-：
    10dB+：
SNR：

    similar to STOI但10dB後LSTM的上升更明顯

## 
### DPOAE-IMD problem
先掛揚聲器後產生noise，因此前面加掛一個cancellation來消除雜訊
IMD：inter-modulation distortion
the swept-sine method
be the input of model
ODVF

non-linear model(1)：sinusoidal
x[n]*x-1[n] = delta funciton

## 陳冠達
### 異常音訊偵測

兩階段式訓練、音訊特徵改善、資料變異性改善
只有OK音訊進入監督式學習訓練(人工協助復判)再進入非監督式學習訓練
同時通過監督式學習與非監督式學習
音訊通過快速傅立葉轉換轉成頻譜、再辨識哪個是正常的、異常的
ＯＫ音訊轉成Mel-spectrum視覺化，再用叢集分群法(Clustering)分n群，選出最大群

## 黃敬恆
### Rendering performance with NN

給他譜去訓練之後彈出沒人彈過的東西

# 8/1報告
## Elanie
### Singing Voice Conversion Cosine Similarity
Feature Capture ->Acoustic model Trainning
Cosine Similarity make two voice hear like the same one
Some metrics
Cosine Similarity :like cos(theta):

      theta = 90 , irrelated
      0 < theta < 90, similar
      theta =180, opposite
    use this formula to count similar coefficient, 1 is best
Cosine Similariy(0-meaned) into 275pieces and into 3 categoties：
    
    Most similar 
    ~0 
    Negative similar
Voice-morphing Slider

Comparison:

    DiffSVC_m4：Worst similar, great quality
    DuelAN_m4：
    DurlAN_op：Best similar, have noises

## 子晴Rebecca
### Human musician vs. AI musician
Three required abilities which musicians need to have:

    Score reading
    Music leading and following
    Interpretation

Change to(for AI):

    Transcripts
    Alignment
    Score Information

Three core:
Ear、Brain、hand

Ave Maria

The key part: Interpretation/Score Information
    找很多鋼琴家來彈：快樂版、傷心版的...
    再丟進去給AI訓練，產生情緒
    
## 爾芸
### Mandarin Speech Emotion Recognition
給受試者填寫五大量表
Speaking Rate：

    WPM與SPM在使用中文時會一樣，because一字一音
    WPM:words per minute
    SPM:syllables per minute
    
    Speak Rate = Syllables / duration
    
## 聖倫
### Per-channel energy Normalization 
PCEN = (forground & background)/background

## 裕嵐
### ASR： Atayal cross-disciplinary project

ASR: 

    the ability of machine to identify words  convert them to readable language
    ---preprocessing>>> acoustic model ---Lexicon>>> Language model ---->>>

Continuous Sequence-to-Sequence modelling

ASR Tasks:
    
    Speech-to-text
    Phoneme Rec
    Speaker Rec
    speaker Diarization
    
    Emotion Rec
    Pathology
    Mispronuciation
    Code-switching ASR


泰雅語系=>泰雅語+賽德克
瀕危語言
Based on Latin拼音
有吸收外來語
是黏著語(Agglutinative language)

很吃重音
Use ' 表示可忽略的音/?/ (glottal stop)，舉例：know的k音不發
Voiceless uvular plosive /q/
Two types of voiceless fricative  /x/(velar) ,  /h/(glottal)
Some pronunciation rules in speaking:
    
    1.Vowel reduction，舉例：Taiwan的ai只發i的音：兩個母音在一起時，一個母音會不見
    2.Semi-vowel conversion

Phoneme Rec
仿人頭的IPA圖，把音檔分析到圖上(類似PPG)

現在都用UIUC做，叢集mapping

Encoder(Attention)-decoder(CTC) architec written in ESPnet
Language embedding
Use phonetic token error rate(PTER) to evalue the performance

## 永傳
### Voice Identity crisis
hear like a human voice but actually not

## Namita
### OAE
OAE：Otoacoustic emission：傳進耳朵裡的聲音所往外產生的回音
SSOAE analysis

用SVD(奇異值分解)找出V-vector(singular vector)
傳進耳蝸的聲音：高頻會先抵達、低頻比較慢
聲音從耳朵進到耳蝸深處裡的聲音，會差到10ms

## 人豪
### So-cits-svc(最知名的是AI孫燕姿)
SoftVC(AI孫燕姿)

## 林昊平
### 利用漢克斯矩陣進行奇異值分解來討論耳聲傳射(Otocoustic Emissions)
Otocoustic Emissions：

SSOAE：是可以用來偵測暫時性誘發聽力的工具

Previous work：

    1.Artifact rejection：可減少環境噪音
    2.Optimal Shrinkage of SV
    3.用Hankel Matrix 進行SVD

Measurement protocols:
1.Nonlinear protocal:消除linear ringing
2.Linear protocol:處理SSOAE

三種降噪方法：
    
    1.Time-Domain SVD-based OS
    2.Frequency-Domain SVD-based OS
        加上FT、InverseFT
    3.Hankel matrix SVD-based OS
        加上FT、InverseFT
        FT後將每個frequency beam建立Hankel 矩陣
        取中位數：為了保留Hankel矩陣的特性
        
怎麼判斷哪個耳朵會有SSOAE：SSOAE不是每個耳朵都有
SSOAE detection

論文的結果分析
1. 分析結果時要觀察到訓練數量造成的影響
2. 資料分段後丟進去訓練，對結果的影響
3. 將資料進行時間區間的分析
4. 自相關分析
5. 分析Hankel Matrix為什麼這麼能幫助降噪：用最簡單的noise去做模擬訊號

結論
1. 運用Hankel Matrix可以在SNR相當低的情況下提升SNR
2. 傳統的訊號處理

## 冠達
### 以複合音訊特徵及叢集分群實現非監督式異音檢測
蒐集台達風扇的聲音，進入FFT轉為頻譜，判別為OK、NG

Auto-Encoder：可做為專屬資料的編碼/解碼器

    輸入正常資料：輸出應該要把輸入還原得很好
    輸入NG資料：還原不好


問題一、特徵轉化
問題二、正常樣本會隨時間、溫度變化而有變異性
1. 將資料根據聲音特徵進行分區，每區再自己進行分類

問題三、閾值須人工制定：必須要自動制定才能達到非監督化


將資料進入STFT後轉為MFCC、Mel-spectrogram、八度音高等的圖形特徵，再疊圖產生複合特徵

選擇分群數：
    
    1.DBI指數：好的分群結果會使每個群更加聚集
    2.輪廓係數：好的分群結果會使群跟群距離比較開
    
瑕疵指數：(適用圖形)
    
    1.MMSE(最小方均根)：對於亮度敏感度超高
    2.DSSIM(結構相異性)：對於旋轉敏感度高
    3.CW-DSSIM(複小波結構相異性)：最準

閾值對召回率的影響：用平均值與不同標準差產生閾值


結論
1. 複合特徵
2. 分群、訓練、再結合改善模型欠擬合的問題


## 舫慶
### Semi-supervised learning 
流程圖
Audio Input-> 漢明窗 -> STFT -> Mel-spectrogram -> 取log

利用CRNN

SSL(semi-supervised learning)

1. Mean-Teacher Approach
    a. composed of two identical models：Students & Teacher 
2. Pseudo Labeling
3. Shift consistency Training/Shift Consistency Mean-Teacher Training
4. Interpolation Consistency Training



# 校園關懷討論
1. dataset產生的label要盡量符合人類預期想要的label
    1. 哪個先開始？應用還沒這麼急，先從dataset開始，
2. 要找一個不需要fine-tune太多的pre-trained model
3. 要嘛就找的到好的資料，要嘛就找到好的pre-trained model
    1. 也可以pre-trained model後自己再加NN...去篩選
4. pre-trained model：去state of the art看


## 湯家昶
### Space warping based dimensionality reduction of higher order ambisonics signals

ambisonics：surround sound format with spatial information
B format： B(^m_l)=Y(^m,_l) (theta, fi)*S

Warping：延展a certain region of the surronding image

Spherical Harmonics(SH)：

## 聖倫
### Few-shot learning
is few-shot learning(資料越多也無益) not deep learning(資料越多越有幫助)
feature engineering(進入model之前) > model optimization(調model參數、層數)


