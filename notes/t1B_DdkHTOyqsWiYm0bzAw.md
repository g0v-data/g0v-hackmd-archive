---
tags: AI, whisper, 逐字稿
---

# 影音轉逐字稿 / 如何在 Macbook 裝 whisper / How to Install whisper in Macbook

## 第一次安裝 First time
- 先開啟終端機（在 spotlight 輸入 terminal，或是到 啟動台 內尋找 終端機）
- > Open the terminal (Input "terminal" in spotlight or find "Terminal" in Launchpad)
- 輸入 git ，會跳出要安裝 XCode，讓他慢慢安裝
- Enter "git", choose "yes" if 
- 安裝 homebrew
    - 可參考 https://brew.sh/index_zh-tw
    - 貼上以下這串
```
$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
- 輸入你的電腦密碼後，按 enter
    - 等安裝完後，複製貼上下列文字
```
$ (echo; echo 'eval "$(/usr/local/bin/brew shellenv)"') >> /Users/APPLE/.profile
    eval "$(/usr/local/bin/brew shellenv)"」
```
- `$ brew install curl ffmpeg`
    - 安裝 curl 和 ffmpeg ，可能需要安裝十幾分鐘
- 因為 brew install 需要一段時間，可以先在下方 Terminal 按右鍵，選 New Window 直接進行下面動作
- `$ git clone https://github.com/ggerganov/whisper.cpp`
- `cd whisper.cpp`
- `make medium`
    - 下載 medium model
- `make large-v2` （共有 large-v1, large-v2, large-v3）
    - 下載 large model
    - > Teemo 推薦：中英文交雜(且中文為主)選 large_v2 不要選用 large_v3
- 錯誤排除
    - 如果硬碟空間不夠，上述 make medium/large 會安裝失敗。將電腦清出空間後，要到 whisper.cpp/models 把對應的檔案砍掉。檔案名稱會像是 `ggml-medium.bin` 並且都超過 1G。砍掉再重跑 make medium/large 即可。
- 如果需要下載 youtube 影片的話
    - `$ brew install streamlink youtube-dl`

## 日後使用
- 開啟終端機
- open .
    - 這個指令可以把現在所在位置變成資料夾顯示出來
    - open 與 . 之間，至少要有一個空格
    - 也可以開啟 Finder ，選上方的「前往」 => [個人專屬]
- 如果要下載 youtube 影片
    - ``` streamlink "網址" 1080p -o video.mkv ```
- ``` ffmpeg -i input-file -ar 16000 -ac 1 -c:a pcm_s16le output.wav ```
    - 將目標影片檔案（或 mp3/m4a）轉換成純聲音 wave 檔
    - 把影片檔案（或 mp3/m4a）拉到「input-file」的地方（要把「input-file」刪掉）
- ``` ./whisper.cpp/build/bin/main -m ./whisper.cpp/models/ggml-medium.bin -l zh output.wav > output.txt ```
- ``` ./whisper.cpp/build/bin/main -m ./whisper.cpp/models/ggml-large-v3.bin -l zh output.wav > output.txt ```
    - 使用 medium model 將 output.wav 轉成逐字稿，並存到 output.txt
    - 如果願意等久一點，可以把 ggml-medium 改成 ggml-large ，需要等更久但是結果會更精準
    - 如果要處理的不是中文的話，可以把 -l zh 改成 -l auto 自動判斷
    - 如果想要輸出到其他檔案，可以把後面的 output.txt 換成其他檔名
    - 如果想要輸出成 srt，可以在指令後面加上 ==--output-srt==，要加在 ==>== 的左邊
      - 舉例：./whisper.cpp/main -m ./whisper.cpp/models/ggml-medium.bin -l zh output.wav ==--output-srt== > output.txt
    - 如果已經在該資料夾內，可以直接改成```./main -m models/ggml-large.bin -l auto output.wav > output.txt```
    - 如果想知道進度，再開一個 terminal 分頁，進入 output.txt 的目錄下，執行 `$ tail output.txt`，就可以看到目前轉譯進度。


:::warning
### 🥴 仍有遇到困難嗎？
### 歡迎加入頻道發問 🙋‍♀️
### g0v Slack #ai-learning 
### 頻道加入方式：https://g0v.hackmd.io/@daisuke/ryjkbFyuS
:::


## 筆記區

20240323 irvin>
- whisper 裝這個跑就好了，不用 diy 整個 stack https://goodsnooze.gumroad.com/l/macwhisper
- 上上週末的讀書會紀錄，就是錄音直接跑 whisper，然後叫 gpt 整理文本 https://hackmd.io/t4Q2_0KgSeK55FlL70H2Ew

WhisperDesktop
- https://www.soft4fun.net/tech/ai/whisperdesktop.htm

用於視聽輔具應用情境
- https://www.facebook.com/share/p/T5MZzioixSQcfwZ2/