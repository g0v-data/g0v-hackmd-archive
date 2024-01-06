---
tags: 逐字稿, 直播,
---

# 影片轉逐字稿經驗談

影片轉文字的方法
1. 手動邊看邊打：要一直按暫停，耗時間。
2. 利用程式將語音轉文字，不一定省時，但不用反覆看影片。

### 使用 google doc 語音輸入功能
1. 準備一條音源線，兩端各接電腦的語音輸出輸入 (有程式可以替代)
2. 開 google doc 點選語音輸入，影片按播放等他跑完

缺點：網路順暢度影響準確度，我連 google doc 常斷線，這條路行不通

### 使用 pytranscriber

https://github.com/raryelcostasouza/pyTranscriber

需先將影片下載，網路順暢度影響準確度

### 使用 WhisperDesktop
https://github.com/Const-me/Whisper  

1. 將影片從網站下載
2. 打開 whisperdesktop 設定好影片位置，選 text file ，按 transcribe 執行。
執行速度跟電腦效能有關，執行完後開文字檔。  
也可以不下載影片搭配音源線直接用 audio capture 功能。
3. 模型選 small 執行速度很快但後續要手動修改的多；選 medium 執行時間會比影片時間長，但準確率比 small 好。
曾碰過到片尾最後一句後半段不見的未知問題。  

安裝參閱：
* [電腦玩物：WhisperDesktop 語音轉文字免費單機軟體，AI 影片字幕實測比較](https://www.playpcesor.com/2023/04/whisperdesktop-ai.html)
* [如何在全新的 Macbook 裝 whisper 撰寫 by Ronny ](https://g0v.hackmd.io/t1B_DdkHTOyqsWiYm0bzAw)

### 進階用法
在 colab 跑 whisper


