# 7/4 AHG meeting(全實驗室)
## 音樂組
### 黃靖軒報告
介紹2021年~now: 音樂家Kit
目標：AI鋼琴家與他在舞台上表演

**Kuramoto model論文: 生物之間如何做到同步**
    1.兩人敲桌，多久後會變同步敲
        誰會變leader, 誰會變follower？
    手、耳朵兩個追蹤器，轉一圈是一拍
    用數字代表第幾圈，小數點代表8分音符
    ex: 7、7.5是第七拍的兩個八分音符

**建立Model：input->w1->w2->w3->out**
w1 :電腦耳朵
w2 :電腦腦
w3 :電腦手
藉由調整之間的係數，達到同步 (學習的功效?

Input有兩個：樂譜、?

**錄音**
    錄了6個版本，有突然加快減慢
    看過了幾個拍才會反應過來
    Python寫，輸入MIDI訊號，輸出MIDI(R1Midi)

**2022年10月**
    買了Kawaii的靜音鋼琴，彈出來直接變MIDI訊號

分時多工的方法送出訊號，但輸入卡住時就會一次送出去造成音樂怪怪的

#7/7(五) 11:00 Demo
    
## 歌唱組(singing voice conversion)
### 日維報告
20專業歌手：7Alto、3Bass、3Soprano、7Tenor
在同步Bass聲音時會遇到問題

轉換Waveform to **Mel-spectrogram**
1. 同步大小聲

**WORLD VOCODER**
1. Resample audio
2. Use WORLD Vocoder

**前處理**
1. Loudness
    不只是變大聲，在不同Hz需要調的聲量大小不一樣
2. PPG model


## 耳機組
### 鄭語芳

耳聲傳射OAE
    OAE typical measurement frequency range from 500Hz~8000Hz
    
## 歌唱組
### 弘祥
依曲生詞產生器

1. 缺乏足夠詞庫
2. 沒有對應的model：因為創作性的事情，很難有標準答案，所以很難學





 
