---
title: "Hackfoldr 2.0"
tags: hackpad
---

# Hackfoldr 2.0

> [點此觀看原始內容](https://g0v.hackpad.tw/7TMSpXasDWl)


### 緣由

想 fork 一個內建 moztw 常用連結的 hackfoldr 用來整理 mozilla 台灣社群的文件，結果一開始動手就忍不住想改介面，又因為看不懂村長的 livescript，只好放棄 fork，開一個新的 repo 全部重寫 www

### 可能的用途

- 整理網路上的資料
- 和朋友或工作夥伴分享書籤
- 改造動線難用但內容優質的網站
- fork 後改放成靜態資料，變成個人網站

### 目前成果

- mockup [http://hack.etblue.tw](http://hack.etblue.tw) js part by tkalu++, au++
- repo [https://github.com/hackfoldr/hackfoldr-2.0](https://github.com/hackfoldr/hackfoldr-2.0)
- doc [http://hack.etblue.tw/welcome-to-hackfoldr](http://hack.etblue.tw/welcome-to-hackfoldr)
    - [Hackfoldr 2.0 基礎教學](https://g0v.hackpad.tw/welcome_to_hackfoldr?r=2)
    - [Hackfoldr 2.0 儲存格語法](https://g0v.hackpad.tw/jfLiSxnllO6)
    - [Hackfoldr 2.0 功能列表](https://g0v.hackpad.tw/0.jmm9642fog5vcxr?r=3)
    - [Hackfoldr 2.0 自行架設教學](https://g0v.hackpad.tw/G7idRJqbG3I)

## feedback

可寫在這，也可直接上 github 開 issue [https://github.com/hackfoldr/hackfoldr-2.0/issues](https://github.com/hackfoldr/hackfoldr-2.0/issues)

- (mobile) Hackpad 頭上有東西，而螢幕寬度的時候會擠到搜尋框 (好像無解？) [http://i.imgur.com/kns8hJu.png](http://i.imgur.com/kns8hJu.png)
    - 發現好像是 RWD 沒寫好 XD 設了 viewport 以後似乎有改善
- .travis.yml 裡面的 env->global->secure 需要改嗎？這邊看不太懂，只知道是加密後的字串。
    - 啊，那個應該要改，可上 irc 問 Lee1092，感謝回報，說明文件要補強一下 >"< 那是把 master 自動 deploy 到 gh-pages 用的，如果你沒有要用 master 改東西，也可以直接全部都在 gh-pages 上操作，這樣就不用管 travis 幹嘛了 XD
    - 我需要從 master 自動 deploy 到 gh-pages XD 我上 IRC 問一下好了，有機會的話我再看是否幫忙更新文件。
    - 請問是在 g0v 的 channel 嗎？
    - yes, freenode 的 [#g0v](https://g0v.hackpad.tw/ep/search/?q=%23g0v&via=7TMSpXasDWl).tw，剛改了一下文件結構，架站的部分在這 XD [http://hack.etblue.tw/welcome-to-hackfoldr/G7idRJqbG3I](http://hack.etblue.tw/welcome-to-hackfoldr/G7idRJqbG3I) 歡迎補完 lol

## to-dos


### moztw version

repo at [https://github.com/moztw/hackfoldr-moztw](https://github.com/moztw/hackfoldr-moztw)
- [x] CNAME
- [ ] shortcuts menu for moztw
- [ ] add new pad to mopad or moztw.hackpad.com by default (instead of g0v)


### emergent



### bug fix

- [x] hackpad url - problem
- [x] fixed by smart collapse
    - [x] chrome 底下 sidebar collapse 後再 expand 回來時 icon 會歪掉
    - [x] sidebar 出現垂直捲軸時，collapse 後鉛筆 icon 會偏左

### hackfoldr 1.0 feature

#### ui

- [x] responsive design
- [x] when a menu link is selected, apply active class
- [x] when a level 2 menu link is selected, expand parent folder
- [x] while kktix, facebook, github... etc., auto target: _blank
- [x] display different icons depending to link url type (not favicon, though)
- [x] open shortcut menu links in iframe
#### content

- [x] support google spreadsheets
- [x] dynamic html head title
- [x] make edit button link to correct ethercalc sheet by tkalu++
- [x] setup default folder
    - [x] add about.html or welcome page -> using hackpad
    - [x] redirect homepage to about.html or welcome page or sandbox

### hackfoldr 2.0 feature

#### ui

- [x] 明顯且夠大好按的的展開  / 收合按鈕
- [x] 可直接在 iframe 內編輯 ethercalc，不用另開分頁
- [x] 放大鏡：單獨縮放 iframe 的內容，但導覽列不會跟著放大
- [x] save zoom in preference in local storage
- [x] while kktix, facebook, github... etc., auto new window icon
- [x] history jumping feature via html5 local storage
- [x] auto new tab icon while target: _blank
- [x] go back to foldr home url via clicking on foldr title
- [x] customize icons, icons, icons!
- [x] flickr 網址預設 blank
- [ ] 收集：不允許內嵌 iframe 的大站列表
#### content

- [x] enable /edit path
- ~complete nav bar menu~
    - ~g0v version~
    - ~moztw version~
#### performance

- [x] while foldr jumping, reload etherclac data instead of reload the whole page

### advanced (hard to implement) features

- [x] manually create and add new hackpad
    - [https://hackpad.com/Legacy-API-Documentation-AWDGdlYpQto#:h=Create-a-Pad](https://hackpad.com/Legacy-API-Documentation-AWDGdlYpQto#:h=Create-a-Pad)
    - [https://hackpad.com/Hackpad-API-v1.0-k9bpcEeOo2Q#:h=Create-a-New-Pad](https://hackpad.com/Hackpad-API-v1.0-k9bpcEeOo2Q#:h=Create-a-New-Pad)
    - [x] ui design
    - [x] js
- [x] drag and drop to reorder
- [x] easy white label setup for ngo / other communities

