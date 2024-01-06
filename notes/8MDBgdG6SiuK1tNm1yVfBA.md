---
title: "讓 Fire.app 支援 Jade 的方法 - 20140118之前舊版"
tags: 開發環境,hackpad
---

# 讓 Fire.app 支援 Jade 的方法 - 20140118之前舊版

> [點此觀看原始內容](https://g0v.hackpad.tw/TvnVBdyagMJ)


1.  用 command prompt 安裝 Jade
    1.  按 Windows 鍵
> 出現開始功能表，游標會自動出現在下方搜尋框
> [name=ET B]

    2.  輸入 cmd 後按 enter
> 找到 cmd.exe （也就是 command prompt）並執行它
> [name=ET B]

    3.  在 command prompt 裡輸入 npm install -g jade 後按 enter
> 會自動上網抓 Jade 的程式並安裝它，要跑一小下子
> [name=ET B]

2.  製作 Fire.app 的 Jade 設定檔
    1.  打開檔案總管，移動到需要使用 Jade 的專案的資料夾
    2.  在專案資料夾根目錄空白的地方按「滑鼠右鍵→新增→純文字檔案」
    3.  檔名設定成 http\_servlet\_handler.rb （注意副檔名要改成 .rb，不是 .txt）
> 如果看不到副檔名，在檔案總管按 Alt + F 叫出功能選單，選「工具→資料夾選項」，再選檢視分頁，找到「隱藏已知檔案的副檔名」取消打勾，然後按「確定」
> [name=ET B]

    4.  連到 [~https://gist.github.com/tka/5302996~](https://gist.github.com/tka/5302996)  [https://gist.github.com/tka/5302996/](https://gist.github.com/tka/5302996/#comment-931517)[#comment](https://g0v.hackpad.tw/ep/search/?q=%23comment&via=TvnVBdyagMJ)[-931517](https://gist.github.com/tka/5302996/#comment-931517) 網頁
> 這是 [https://gist.github.com/tka/5302996#comment-854085](https://gist.github.com/tka/5302996#comment-854085) 加了幾個字的版本，讓 /src 資料夾中的 .jade 檔案可以在 localhost 根目錄預覽，網址不用加 /src
> [name=ET B]

    5.  ~往下捲一點，找到 http\_servlet\_handler.rb for windows 這一段~
    6.  把內容複製後貼到剛才新增的 http\_servlet\_handler.rb 文字檔中，存檔
3.  測試
    1.  在專案資料夾根目錄裡新增空白的文字檔，檔名叫 foo.jade
    2.  打開 Fire.app
> 跑完以後程式 icon 會出現在開始列的通知區，剛打開時 icon 黑色的
> [name=ET B]

    3.  按下 Fire.app icon，選 watch folder... 後選專案資料夾的位置
> watch 後 fire.app 的 icon 會變成彩色的
> [name=ET B]

> 如果原本已經在 watch folder 中，先 stop watching 然後再重新 watch 一次
> [name=ET B]

    4.  連到 [http://127.0.0.1:24681/foo.jade](http://127.0.0.1:24681/foo.jade)
    5.  網頁一片空白沒有錯誤訊息，就表示成功了 :D

### Jade 的常見問題

1.  沒辦法在 Jade 裡面寫 javascript
    - 已知原因：Jade 裡的 js 是 for client side use，被 Jade 包起來了，不能和外界溝通
    - 解法：
        - Fire.app 內
            - 找到根目錄下、之前設定的 http\_servlet\_handler.rb
            - 把「body = Open3.popen3('node c:/users/etblue/appdata/roaming/npm/node_modules/jade/bin/jade --path . "') do |stdin, stdout, stderr|」這一行
                改成「body = Open3.popen3('node c:/users/etblue/appdata/roaming/npm/node_modules/jade/bin/jade --path . **-O "{require: require}**"') do |stdin, stdout, stderr|」
            - 兩者差別在於加入了粗體底線的部分，意思是叫 Jade 把 .jade 檔案裡面的 require 這個關鍵字（第一個 require）當作是 javascript 執行環境裡的 require 這個 function（第二個 require）來解讀，這樣一來，在 .jade 裡面寫的 js code 的 require 關鍵字才會生效。
        - Jade command
            - 由於 Fire.app 目前還沒有 build .jade 檔案的功能，所以必須開 command line 下指令把 .jade 變成 html，才能 push 到 gh-pages 上面給大家看
            - 指令：
                - cd src
> 移動到放 .jade 檔案的資料夾位置，我的 .jade 是放在 src/ 裡面，所以移到 src 
> [name=ET B]

                - jade -o .. -O '{require: require}' .
> 叫 Jade 把這個目錄裡（.）的 .jade 檔案 compile 成 html（-o）丟到上一層目錄（..）中，並且把 .jade 檔案裡面的 require 關鍵字解讀成 javascript 的 require function（-O '{require: require}'）
> [name=ET B]



