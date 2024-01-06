---
title: "g0v designer set 前端半條龍手冊"
tags: 零時的學習不能等,hackpad
---

# g0v designer set 前端半條龍手冊

> [點此觀看原始內容](https://g0v.hackpad.tw/R7BEW2muCbU)


### Skill Sets


可以參考以下的學習流程
html → jade → svg
css → sass  → compass → css3
```
                    ├  bootstrap / semantic-ui
```
javascript → jquery → angularjs → firebase → d3js
```
           → nodejs → brunch / grunt
```
git


### HTML & Jade

- html 寫著網頁的內容，讓 chrome, firefox, safari 等瀏覽器讀取、轉換成我們看到的畫面
- jade 是覺得寫 html 很煩的懶人發明的，把 html 裡一堆重複的地方省略，只打最重要的部分，其他地方叫電腦幫你補完變成 html
- 使用 jade 的方式
    1.  安裝 jade
        1.  安裝 node.js 程式
            - 在安裝 jade 之前，要先安裝 node.js，因為 jade 程式是在 node.js 環境裡執行的。如果你的電腦裡還沒裝 node.js，請看官網的 [安裝方式](http://nodejs.org/)
        2.  安裝 jade 程式
            - 這個程式是把 jade 語法補完變成 html 用的。請看官網的 [安裝方式](http://jade-lang.com/command-line/)
    2.  在你愛用的文字編輯器裡安裝 jade 的語法提示，這樣程式碼才有漂亮顏色。sublime text 安裝方式詳下面章節
    3.  在瀏覽器裡預覽 jade 變成 html 以後在網頁上看起來的樣子
        - 因為瀏覽器只認得 html，所以想一邊修改 jade 一邊預覽結果的話，要有個程式幫你隨時把最新修改的 jade 補完變成 html，再給瀏覽器去讀
        - 作法一：透過 Fire.app。[步驟](https://g0v.hackpad.com/-Fire.app-Jade--FK7eBR4BdAj)
        - 作法二：透過 npm
> 這個我要問科比 XD
> [name=ET B]

    4.  網頁寫好要上線了，把 jade 檔案輸出成 html 檔案
        - 作法一：使用 jade 指令, 例如:
            - jade source.jade
                - 即會產生 source.html
        - 作法二：透過 npm
            - 如果使用一些方便的 template 時, 有些會提供即改即轉(watching)的功能. 他們有些會透過 "npm start" 這個指令來達成
                - npm start 會找 package.json 裡的 "start" 這一項, 把內容拿來執行, 所以 npm start 會發生甚麼是端看 template 是怎麼寫的
> 原來如此！所以我打 npm start 的話是抓 jade 官方程式的 package.json 的 start 來執行，執行的結果就是只要這個目錄裡的 .jade 檔案一修改，他就會馬上出一份 .html 到 .jade 的同一個地方？
> [name=ET B]

- 常和 jade 相提並論的東西：erb
    - jade 需要在 node js 環境中執行，所以常常會跟 node js 家族的其他工具一起使用
    - erb 需要在 ruby 環境中執行，所以常常會跟 ruby 家族的其他工具一起使用
    - 在 jade 裡面可以寫 javascript 程式，但不能寫 ruby 程式
    - 在 erb 裡面能寫 ruby 程式，但不能寫 javascript 程式
    - 嗯，你說為什麼要在 jade 或 erb 裡面寫程式？那就是另一個超懶人的故事惹…正所謂：科技始終來自於惰性（茶）
    - 為什麼 g0v 專案用 jade 而不用 erb 呢？因為村長選了 jade，所以大家就跟著用 jade，這樣出事有村長頂著啊哈
    - 其實我一開始因為學 ruby 的關係，是先寫 erb 的，而且出自 rubyist 之手的 fire.app 也原生支援 erb，不過自從來到 g0v 以後……[喔no！喔no！](http://cornguo.atcity.org/test/mjcount/#ohno_ohno)
    - haml... ?
    - handler... ?

### CSS & Sass & Compass

- css 寫著顏色、字體、排版規則等樣式，讓 chrome, firefox, safari 等瀏覽器讀取、把 html 網頁的內容變漂亮
- sass 是覺得寫 css 很煩的懶人發明的，把 css 裡一堆重複的地方省略，只打最重要的部分，其他地方叫電腦幫你補完變成 css
- compass 是連寫 sass 都覺得煩的更懶人發明的，把 sass 裡面一些比較囉唆不好寫的地方換個寫法，再叫電腦幫你跟 sass 一起補完變成 css
- 使用 sass + compass 的方式
    1.  安裝 sass + compass
        - 作法一：刻苦耐勞腳踏實地白手起家法
            1.  安裝 ruby 程式
                - 在安裝 sass 或 compass 之前，要先安裝 ruby，因為 sass 和 compass 程式是在 ruby 環境裡執行的。如果你的電腦裡還沒裝 ruby，請看官網的 [安裝方式](http://www.ruby-lang.org/zh_tw/)
            2.  安裝 rubygems 程式
                - ruby 程式可以加上各種外掛功能，大家把這些外掛程式稱做 gem，而 rubygems 是用來管理這些 gems 的程式。ruby 的 1.9 版以後都有內建 rubygmes，不過不見得是最新版，可能需要更新它。請看官網的 [安裝方式](https://rubygems.org/pages/download)
            3.  安裝 sass 程式
                - 這個程式是把 sass 語法補完變成 css 用的。請看官網的 [安裝方式](http://sass-lang.com/install)
            4.  安裝 compass 程式
                - 這個程式是把 compass 語法補完變成 sass 用的。請看官網的 [安裝方式](http://compass-style.org/install/)
        - 作法二：一帆風順魚躍龍門惰性光輝法
            - 安裝 fire.app
                - 裝了 fire.app 以後，上面作法一寫的 ruby 啦，sass 啦，compass 啦全部都不用手動安裝，fire.app 會幫你搞定一切。關於 fire.app 的介紹及安裝方式，詳見下面章節
    2.  在你愛用的文字編輯器裡安裝 sass 的語法提示，這樣程式碼才有漂亮顏色。sublime text 安裝方式詳下面章節
    3.  在瀏覽器裡預覽 sass + compass 變成 css 以後在網頁上看起來的樣子
        - 因為瀏覽器只認得 css，所以想一邊修改 sass / compass 一邊預覽結果的話，要有個程式幫你隨時把最新修改的 sass / compass 補完變成 css，再給瀏覽器去讀
        - 作法一：透過 Fire.app
        - 作法二：？
    4.  網頁寫好要上線了，把 sass + compass 檔案輸出成 css 檔案
        - 作法一：透過 Fire.app
        - 作法二：？
- 常和 sass 相提並論的東西：less
    - sass 需要在 ruby 環境中執行，所以常常會跟 ruby 家族的其他工具一起使用
    - less 需要在 javascript 環境中執行，所以常常會跟 javascript 家族的其他工具一起使用？（沒用過 less 不瞭解，請幫忙糾正）

### JavaScript & jQuery & Angular JS & LiveScript

- javascript 寫著「當使用者按了這個就跑出那個」之類的互動效果，讓 chrome, firefox, safari 等瀏覽器讀取、讓 html 網頁不只是靜態展示內容，還可以針對使用者當下的動作做出反應
- jquery 是覺得寫 javascript 很煩的懶人發明的，把 javascript 裡一堆很常用但卻很囉唆不好寫的功能預先寫好，打包成簡潔的函式，讓你可以用好寫的語法達到同樣的效果
- angular
- livescript
    - 用 livescript 寫 json 假資料
        - 範例 [https://github.com/g0v/ly.g0v.tw/blob/master/bower.json.ls](https://github.com/g0v/ly.g0v.tw/blob/master/bower.json.ls)
        - 假資料龐大時，拆分成多個檔案來寫，再合併成同一個檔案輸出
            - 寫法 [https://gist.github.com/audreyt/8599670](https://gist.github.com/audreyt/8599670)
            - 指令類似 lsc -cj *ls (by au++)
            - 如果已經 compile 了同名 json 檔，lsc -cj 會不動作，把檔案刪掉再下指令即可

### Fire.app

- fire.app 是覺得每次用 sass + compass + erb 開發網站時都要刻苦耐勞腳踏實地白手起家地到處安裝程式或反覆打指令很煩的人發明的，把設計網站過程中一堆常常需要重複做的事情預先寫好，打包成一支電腦軟體，讓你可以按幾下選單就搞定不屬於寫網頁本身的周邊雜事。
- 使用 fire.app 的方式
    1.  安裝 fire.app
        - 安裝來源一：直接向開發團隊購買，一次付費終身更新，只要  US$14。詳情見 fire.app 官網
> 利益揭露：fire.app 的作者是強者我室友 XD
> [name=ET B]

        - 安裝來源二：使用 g0v 贊助版本，請上 irc 向 clkao 或 hlb 詢問
> 詳情待確認
> [name=ET B]

        - 安裝來源三：請向手上持有 fire.app 安裝檔的朋友詢問，fire.app 是開源軟體，以 GPL 授權，所以散佈是沒有版權問題的
        - 安裝來源四：自己從 github 下載原始碼編譯。請見 [github repo](https://github.com/KKBOX/FireApp)
> 我是自己編的, 可是不會用, 還被強者你室友知道了QQ
> [name=Yuan C]

> 不用太難過……ㄟ反正你也用不到啊那是給不會開 server 的人用的 =3=
> [name=ET B]

    2.

### LiveReload

- livereload 是覺得每次改完網頁都要去瀏覽器按 F5 或 ctrl + r 重新整理頁面很煩的人發明的，

### Semantic UI

- semantic ui 是覺得每次寫不同的網站都要一直重複寫類似的導覽列、選單、按鈕……等元件很煩的人發明的，

### Sublime Text 2/3

- 讓 jade, sass, ls (livescript) 的語法有漂亮顏色
    1.  安裝 sublime text 的 package control，[安裝方式](https://sublime.wbond.net/installation)
        - 安裝時，視窗最下面的狀態列左邊會有個 = 跑來跑去，跑完就表示裝完了
    2.  安裝語法提示
        1.  打 command (ctrl) + shift + p 叫出 command palette 小輸入框
        2.  打 package，從自動跳出的清單中找到 package installation，移到它上面 enter
        3.  打你想安裝的 syntax highlight，jade /  sass / livescript …等，一樣從自動跳出的清單中選取，通常會是第一個
    3.  從右下角語法選單選擇目前檔案想套用的語法提示
    4.  恭喜你！你的人生變成彩色的了！（[讚嘆聲](http://cornguo.atcity.org/test/mjcount/#wow)）
- 避免製造多餘的空白
    - 安裝 EditorConfig，[安裝方式](https://github.com/sindresorhus/editorconfig-sublime#readme)
        - 按照作者建議，同時在 Sublime Text Preferences 加入 "draw\_white\_space": "all" 的設定
- 一日千行懶人鍵
    - 想要同時改好多個 html 標籤或 class name
        - 選取幾個字以後…
        - command (ctrl) + d 找到並選起下一段一樣的字
        - command (ctrl) + u 剛才 d 按太多下了倒帶一步
        - 選好後直接打字或按方向鍵等，就可以同時編輯所有被選起來的部分
        - 按 esc 離開多段編輯模式
    - 想要同時打好幾行類似的東西
        - 一次選起好幾行
        - command (ctrl) + shift + l 即進入多行同時編輯模式
        - 按 esc 離開多行編輯模式
- 在小螢幕上更有生產力
    - 按著 command (ctrl) 不放，然後按 k 接著按 b，可以顯示或隱藏左邊的 sidebar

### TEMP 區

angular js
- [http://www.codeorbits.com/blog/2013/12/20/rapid-angularjs-prototyping-without-real-backend](http://www.codeorbits.com/blog/2013/12/20/rapid-angularjs-prototyping-without-real-backend)
firebase
- [https://www.firebase.com/tutorial/](https://www.firebase.com/tutorial/#session/s7u1bt0nk0m)[#session](https://g0v.hackpad.tw/ep/search/?q=%23session&via=R7BEW2muCbU)[/s7u1bt0nk0m](https://www.firebase.com/tutorial/#session/s7u1bt0nk0m)
angular js + firebase
- [http://angularfire.com/](http://angularfire.com/)
- [https://github.com/dypsilon/frontend-dev-bookmarks](https://github.com/dypsilon/frontend-dev-bookmarks)
### 學習資源


