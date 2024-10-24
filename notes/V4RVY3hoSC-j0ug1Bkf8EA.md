# whisperX 操作記錄

[whisperX](https://github.com/m-bain/whisperX) 是基於 OpenAI whisper 模型產生的生態系去組合起來的工具，這裡記錄一下操作的參數過過程。

使用設備：
* i9-13900HX CPU
* RTX 4080 筆電版本, 12GB VRAM
* 64G 主記憶體
* Ubuntu 22.04.4 LTS

安裝指令
`pip install git+https://github.com/m-bain/whisperx.git`

執行
`whisperx your_file.mp3 --model large-v2 --batch_size 24 --language zh --no_align --chunk_size 10`

* --model large-v2
    * 使用 large-v2 模型，因為執行速度夠快、需要的記憶體減少，就不再需要使用小模型跑；如果跑不動就把參數改成 base
* --align_model WAV2VEC2_ASR_LARGE_LV60K_960H
    * 如果需要精準到每個字的時間，會需要這個指令，但產出的字幕檔案每個中文字中間都會加入一個空白；如果跑不動就把參數改成 base ，跟 no_align 參數衝突
* --batch_size 24
    * 批次程序數量，試過拉到 36 就跑不動
* --language zh
    * 直接設定以中文為主，可以減少自動偵測的時間
* --no_align
    * 不透過 align_model 處理，少了這個指令後每個中文字都會中間隔一個空白，參考 [github issue 討論](https://github.com/m-bain/whisperX/issues/200)
* --chunk_size 10
    * 調整每句話長度，預設 30 ，目前中文影片使用 10 的效果還不賴，數字越小執行時間越久，試過 1 大概要跑多很多倍的時間，產出的結果也很破碎
* -f srt
    * 只產生 srt 格式，預設會產生 json/srt/tsv/txt/vtt 五個格式
* --diarize
    * 依據不同的聲紋區分講者
* --hf_token xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
    * [Hugging Face](https://huggingface.co/) Settings > Access Tokens ，用來下載模型檔案的 token ，部份模型檔案會要求下載前閱讀並且同意授權聲明，初次執行遇到錯誤會需要找到模型對應頁面完成操作
* --compute_type float32
    * 在系統陸續更新後沒辦法順利執行，必須要加入這個參數

所有參數可以在[程式碼](https://github.com/m-bain/whisperX/blob/main/whisperx/transcribe.py)找到

會再執行下面指令進行簡繁轉換

`opencc -i your_file.srt -c s2tw -o result.srt`

* -c s2tw
    * Simplified Chinese to Traditional Chinese (Taiwan Standard) 簡體到臺灣正體，參考 [github](https://github.com/BYVoid/OpenCC)