# whisperX 操作記錄

[whisperX](https://github.com/m-bain/whisperX) 是基於 OpenAI whisper 模型產生的生態系去組合起來的工具，這裡記錄一下操作的參數過過程。

使用設備：
* i9-13900HX CPU
* RTX 4080 筆電版本, 12GB VRAM
* 64G 主記憶體
* Ubuntu 22.04.4 LTS

`whisperx your_file.mp3 --model large-v2 --align_model WAV2VEC2_ASR_LARGE_LV60K_960H --batch_size 24 --language zh --no_align`

* --model large-v2
    * 使用 large-v2 模型，因為執行速度夠快、需要的記憶體減少，就不再需要使用小模型跑；如果跑不動就把參數改成 base
* --align_model WAV2VEC2_ASR_LARGE_LV60K_960H
    * 如果需要精準到每個字的時間，會需要這個指令；如果跑不動就把參數改成 base
* --batch_size 24
    * 批次程序數量，試過拉到 36 就跑不動
* --language zh
    * 直接設定以中文為主，可以減少自動偵測的時間
* --no_align
    * 不透過 align_model 處理，少了這個指令後每個中文字都會中間隔一個空白，參考 [github issue 討論](https://github.com/m-bain/whisperX/issues/200)
* --diarize
    * 依據不同的聲紋區分講者
* --hf_token xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
    * [Hugging Face](https://huggingface.co/) Settings > Access Tokens ，用來下載模型檔案的 token ，部份模型檔案會要求下載前閱讀並且同意授權聲明，初次執行遇到錯誤會需要找到模型對應頁面完成操作

執行後會在同樣目錄產生 5 個格式，包含 json/srt/tsv/txt/vtt ，會再執行下面指令進行簡繁轉換

`opencc -i your_file.srt -c s2tw -o result.srt`

* -c s2tw
    * Simplified Chinese to Traditional Chinese (Taiwan Standard) 簡體到臺灣正體，參考 [github](https://github.com/BYVoid/OpenCC)