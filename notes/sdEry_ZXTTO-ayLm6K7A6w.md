---
title: "在 Fire.app 中使用 Jade 樣板語法（以 Windows 版為例）"
tags: 開發環境,hackpad
---

# 在 Fire.app 中使用 Jade 樣板語法（以 Windows 版為例）

> [點此觀看原始內容](https://g0v.hackpad.tw/FK7eBR4BdAj)

> Linux 跟 Mac 請以此類推... XD
> [name=ET B]


2014/09/06
1.  download fire.app for windows
    - [https://app.box.com/s/mb01rj6xuje4k3crz57h](https://app.box.com/s/mb01rj6xuje4k3crz57h)
2.  setup repo: 在你的 repo 根目錄中加入這兩個檔案
    - [https://github.com/hackfoldr/hackfoldr-2.0/blob/gh-pages/config.rb](https://github.com/hackfoldr/hackfoldr-2.0/blob/gh-pages/config.rb)
    - [https://github.com/hackfoldr/hackfoldr-2.0/blob/gh-pages/tilt_jade.rb](https://github.com/hackfoldr/hackfoldr-2.0/blob/gh-pages/tilt_jade.rb)
        - [https://github.com/hackfoldr/hackfoldr-2.0/blob/gh-pages/tilt_jade.rb#L20](https://github.com/hackfoldr/hackfoldr-2.0/blob/gh-pages/tilt_jade.rb#L20) 修改路徑
        - [https://github.com/hackfoldr/hackfoldr-2.0/blob/gh-pages/tilt_jade.rb#L21](https://github.com/hackfoldr/hackfoldr-2.0/blob/gh-pages/tilt_jade.rb#L21) 修改路徑
    - mac: try this [https://gist.github.com/tka/5302996#file-http\_servlet\_handler-rb-for-mac](https://gist.github.com/tka/5302996#file-http_servlet_handler-rb-for-mac) 不過……我問一下好了等等 XD
3.  記得在你的 os 裡安裝 node.js 和 jade
4.  按正常程序用 fire.app watch folder
5.  要產生 html 檔案時，用 jade 的 command line 產生
    - 例： jade . -o .



[讓 Fire.app 支援 Jade 的方法 - 20140118之前舊版](https://g0v.hackpad.tw/TvnVBdyagMJ#讓-Fire.app-支援-Jade-的方法---20140118之前舊版)

20140118後新版Fire.app已經內建Jade支援，使用方式：
1.  取得Fire.app執行檔
    - 方法一：購買Fire.app
    - 方法二：從[github](https://github.com/KKBOX/FireApp/)抓下來自己compile
    - 方法三：參加 g0v 專案或找認識的人要檔案
2.  設定專案
    1.  到你的專案資料夾中，把根目錄下的config.rb檔案弄成[這樣](https://gist.github.com/ETBlue/8481039)。跟原本的config.rb不同的地方在於多了第1-3行。
    2.  同樣在專案資料夾根目錄下，新增[這個檔案](https://gist.github.com/ETBlue/8481193)。如果你的作業系統是Windows，要把第18、19行的「etblue」改成你的Windows使用者名稱。
        - 如果執行時出現找不到 jade 的錯誤訊息，但是明明已經安裝 jade 了，那麼檢查 c:/users/etblue/appdata/roaming/npm/node\_modules/jade/bin/jade 這個檔案是否存在，2014/05/16 新版 jade 需要加上 .js 副檔名才能用，因此需要在 tilt\_jade.rb 內把兩個用到 jade 的路徑都改成 c:/users/etblue/appdata/roaming/npm/node_modules/jade/bin/jade**.js**
    3.  在專案資料夾的根目錄下，開一個叫做views的資料夾，把你的.jade檔案放在裡面
    4.  在專案資料夾的根目錄下，開一個叫做public的資料夾，給Fire.app等一下輸出檔案用
    5.  把css、js、img…等資料夾，都移到public資料夾內
3.  執行Fire.app
    1.  執行Fire-app.exe後，讓它watch你的專案資料夾，再用瀏覽器打開[http://localhost:24681](http://localhost:24681)，就可以預覽views資料夾中的index.jade
> 使用Jade的專案資料夾，必須是執行Fire.app後第一個watch的資料夾，如果已經先watch過別的專案，需要到Fire.app選單中按quit然後重開Fire.app
> [name=ET B]

    2.  成功watch專案資料夾後，在Fire.app選單中按「build project」，所有jade、sass就會輸出成html跟css在public資料夾底下
> 如果你的css、img檔是使用絕對路徑，那麼直接用瀏覽器開public下的html的話路徑會跑掉，要讓Fire.app改成去watch這個public資料夾才會正常。
> [name=ET B]

    3.  所有專案根目錄下的資料夾都會被輸出到public中，如果有放ai工作檔之類的資料夾不需要被輸出的話，可以更改設定……（待補）

### Jade 的常見 bug（i.e. 使用 Jade 的菜鳥的腦袋的常見 bug）

1.  jade 的 extend 失效了
    - 原本好好的，突然之間網頁預覽畫面變成一片空白
        - 已知原因：我的 block 名稱寫錯了（茶）
    - 出現莫名其妙的錯誤訊息，但看不出錯誤源頭（linux 底下 tka 遇到的）
        - 已知原因：我的某個 .jade 的 html attribute 用空白分隔，沒有改成 , 分隔（茶茶）
2.  沒辦法在 Jade 裡面寫 javascript
    - 現在已經內建了，不需要再hack，使用方式請見上面步驟，這裡的原本內容已移至[舊版文件](https://g0v.hackpad.com/-Fire.app-Jade-20140118-TvnVBdyagMJ)

