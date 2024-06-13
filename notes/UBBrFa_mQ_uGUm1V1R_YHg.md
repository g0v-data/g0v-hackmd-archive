# 斐姨所思 范琪斐訪談黃國昌

完整版
{%youtube yfwXL_sJTlI %}

剪輯版
{%youtube ymR6Ed5f2aQ %}

被剪內容集合版
{%youtube j7GCLLsJfFQ %}

* [完整版字幕檔案(逐字)](https://github.com/chiuhans111/kc-huang-on-fan-american-time-video-compare/blob/main/src/data/1.srt)
* [剪輯版字幕檔案(逐字)](https://github.com/chiuhans111/kc-huang-on-fan-american-time-video-compare/blob/main/src/data/2.srt)

chiuhans111 技術說明：
1. 影片音軌使用 OpenAI Whisper 技術轉字幕後，透過 Difflib 比對兩部影片逐字稿重
   疊位置，初步判斷來源影片時間軸對應情形
2. 音軌轉梅爾頻譜後進行互相關運算，進一步將影片對齊至誤差約0.1秒
3. 剪輯部分逐字稿使用 Gemini 1.5 Flash 摘要重點，並人工校對後做成 Timecode
4. 輸出影片時間軸對應關係，結合 YouTube IFrame API 製作成可互動式播放體驗

互動程式可以同時看剪輯版與完整版差異
https://chiuhans111.github.io/kc-huang-on-fan-american-time-video-compare/