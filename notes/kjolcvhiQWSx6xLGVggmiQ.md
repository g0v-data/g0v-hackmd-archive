---
title: "fr0ntend-br3dge 零時前端教學松 # 2"
tags: 零時的學習不能等,event,hackpad
---

> [點此觀看原始內容](https://g0v.hackpad.tw/0.p3fpuqq3bx1or)

> 上次也是 br2dge 耶，中英文 index 混亂了 XD
> [name=Simon P]


前情提要（看要怎麼把中英文改成一致啦）
20140614 [fr0ntend-bridge 第零次前端教學松](https://g0v.hackpad.com/sYHY4dqb1OE)
20140726 [fr0ntend br2dge 1](https://g0v.hackpad.tw/wyT1zsa43A3)


## Lesson 3 (8/16) @ BOOKSHOW

報名：[http://g0v-](http://g0v-tw.kktix.cc/events/fr0ntend-br3dge)[tw](http://g0v-tw.kktix.cc/events/fr0ntend-br3dge)[.kktix.cc/events/fr0ntend-br](http://g0v-tw.kktix.cc/events/fr0ntend-br3dge)[3](http://g0v-tw.kktix.cc/events/fr0ntend-br3dge)[dge](http://g0v-tw.kktix.cc/events/fr0ntend-br3dge)
時間：8/16 13:30~17:00
地點：BOOKSHOW 說書會（台北市信義區基隆路一段141號6樓之7，[交通地圖](http://bookshow.tw/traffic)）
費用：200元
直播：[https://www.youtube.com/watch?v=WCX1XQ0S9Yk](https://www.youtube.com/watch?v=WCX1XQ0S9Yk)

課程目標：更了解js的應用及使用jQuery，並且使用git將作品放上gh-pages。

### 時間表 (1:30pm - 5pm)

13:30 - 13:40 開場
14:00 - 14:30 js 和 jQuery 入門
14:30 - 15:00 js 和 jQuery 練習
15:00 - 15:30 git 入門
15:30 - 16:00 git
16:00 - 16:50 填坑時間
16:50 - 17:00 成果報告及心得回饋

## 行前通知

學生
明天(8/16)，下午1點30在BOOKSHOW舉行第三次的零時前端教學松，大家不要忘記來喔，活動會準時開始也請記得盡量不要遲到，一起把握短暫的學習時光。以下有幾點注意事項，請大家務必仔細閱讀。

要記得攜帶一台筆電，為了增進大家肌肉記憶力，所以安排了不少實作時間，要是沒有筆電可能會無法度過愉快的時光。

可以的話，花一些時間看一下以下的參考教材，相信會對大家更有幫助。
[http://www.codecademy.com/tracks/javascript](http://www.codecademy.com/tracks/javascript)
[http://www.codecademy.com/tracks/jquery](http://www.codecademy.com/tracks/jquery)

另外，可能事先須要安裝好用的軟體
1\. 文字編輯器例如Sublime Text等。
2\. github for windows/mac

助教
明天(8/16)，下午1點30在 \*BOOKSHOW\* 舉行第三次的零時前端教學松，大家不要忘記來喔，活動會準時開始也請記得盡量不要遲到，一起把握短暫的學習時光。以下有幾點注意事項，請大家務必仔細閱讀。

很感謝各位報名助教，這次因為助教人數不足，所以有的助教會分配到兩個學生，請各位多多擔待。

這次的目標是大家按照步驟完成一個jQuery小程式，並且使用git commit上gh-pages。
> 周末要趕東西就放棄惹 QQ 釋出一張學生票喔喔～
> [name=Summit S]


## 課前準備知識區


## 課程投影片跟教材

- [https://www.icloud.com/iw/](https://www.icloud.com/iw/#keynote/BAI0RyT7HhCz7_KoF5KBImnvt_81XUX6oNSF/fr0nt-br3dge)[#keynote](https://g0v.hackpad.tw/ep/search/?q=%23keynote&via=0.p3fpuqq3bx1or)[/BAI0RyT7HhCz7\_KoF5KBImnvt\_81XUX6oNSF/fr0nt-br3dge](https://www.icloud.com/iw/#keynote/BAI0RyT7HhCz7_KoF5KBImnvt_81XUX6oNSF/fr0nt-br3dge)
- [https://github.com/fr0ntend/lesson3/releases](https://github.com/fr0ntend/lesson3/releases)

## 參考資料

### GitHub repo

- [https://github.com/orgs/g0v/teams/leaners/repositories](https://github.com/orgs/g0v/teams/leaners/repositories)
- [https://github.com/fr0ntend/lesson3](https://github.com/fr0ntend/lesson3)
### jstutor

- [https://jstutor.herokuapp.com/](https://jstutor.herokuapp.com/#mode=display)[#mode](https://g0v.hackpad.tw/ep/search/?q=%23mode&via=0.p3fpuqq3bx1or)[=display](https://jstutor.herokuapp.com/#mode=display)
### JS Guide

- [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide)
### JS Grammar

- [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar)
- [http://www-archive.mozilla.org/js/language/grammar14.html](http://www-archive.mozilla.org/js/language/grammar14.html)
### jQuery

- [http://api.jquery.com/](http://api.jquery.com/)
### Git

- [http://git-scm.com/documentation](http://git-scm.com/documentation)
### GitHub Pages

- [https://pages.github.com/](https://pages.github.com/)

## 當天共筆


### 在網頁嵌入 js 的幾種方式


#### 放在 head


#### 放在 body

需要操作 dom element 的 js 建議放在 body 最後面，放在 head 在 dom 還沒產生的時候可能會失效。

#### inline



### js 是什麼


是我們叫電腦做事情的指令…
(嘗試 console)

### jQuery


懶人寫 javascript

啦啦啦


