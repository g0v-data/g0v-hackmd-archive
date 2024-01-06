---
title: "airesis 中文翻譯與架設"
tags: hackpad
---

# airesis 中文翻譯與架設

> [點此觀看原始內容](https://g0v.hackpad.tw/lhUMItDUIZw)


### 線上測試


中文測試版：[http://www.airesis.cn/](http://www.airesis.cn/)

決策平台 airesis：[http://movimento5stelle-airesis.beepworld.it/](http://movimento5stelle-airesis.beepworld.it/)
_流程圖_ [_http://movimento5stelle-airesis.beepworld.it/attuale-struttura.htm_](http://movimento5stelle-airesis.beepworld.it/attuale-struttura.htm)
> 請問有人可以把流程圖翻譯一下嗎？用Google translate只能猜到大概而已。
> [name=Truman Y]


### 翻譯進度


直接改到這邊，有興趣翻譯者請申請帳號，並且申請加入翻譯，有設定自動加入了
[~https://www.transifex.com/projects/p/g0v-airesis/~](https://www.transifex.com/projects/p/g0v-airesis/)
~ttcat 完成了!!~

新的翻譯工具，目前 75%：[https://crowdin.net/project/airesis/zh-TW](https://crowdin.net/project/airesis/zh-TW)


### 作者來信

介紹他們的文件和使用平台 / 翻譯 guideline
[https://docs.google.com/document/d/12ysocZbtsAw7meYEuPlTdHAxbU8tDU58C8petdk6vXQ/edit?usp=sharing](https://docs.google.com/document/d/12ysocZbtsAw7meYEuPlTdHAxbU8tDU58C8petdk6vXQ/edit?usp=sharing)

### 架設目前進度


ETBLUE:
\* hackath6n 當天由 +[李小蟹](https://plus.google.com/106253399830072484387)  、 +[Ly Cheng](https://plus.google.com/101938059377637333597)  和 +[Poga Po](https://plus.google.com/100833531244712650174) 把 airesis 的首頁推上 heroku。事後發現airesis 官方已經把 +[Ly Cheng](https://plus.google.com/101938059377637333597) +[Ttcat Wu](https://plus.google.com/112041531514953102862) +[Audrey Tang](https://plus.google.com/108097168863179836693)翻譯的中文版上架，但域名搞錯了囧，不過總之是有中文版可以使用了 [http://www.airesis](http://www.airesis.cn/)[.cn/](http://www.airesis.cn/)

- [x] 需要寫信去請他們改成 tw
> 等待回信
> [name=Wu H]

> 有消息嗎？選擇地區台灣也出現「中國一省」（丟筆）
> [name=ipa c]


\* +[Ian Wu](https://plus.google.com/106285007951180572450) 針對圖書館編目、quora 標籤進行研究，尋找適當的木材，以便整合進為動民主 2.0 內建標籤系統，發現可以砍一些公民媒體的標籤來用 XD


安裝的問題似乎修正了，需要重新試試看

Hi Ttcat,
glad to hear that from you.
The most stable version is the master branch so please use that one.
Secondly, I need to know the exact problem you are facing, the Gemfile.lock is updated and all gems are working good right now.
Just give a bundle install and not a bundle update.
Please give me a more accurate feedback so I can help you solve the problem.
Please take a look at [https://crowdin.net/project/airesis](https://crowdin.net/project/airesis) to translate Airesis in Chinese Traditional and Simplified.

Hope to hear you back and sorry for late reply.

Cheers,
Alessandro Rodi



*hackath6n 嘗試架到 heroku 失敗了
github 上的版本直接抓下來還有很多要修改
是不是寫信去請他們 push 新版？

[https://github.com/coorasse/Airesis](https://github.com/coorasse/Airesis)
[https://github.com/g0v/Airesis](https://github.com/g0v/Airesis)

### Setup


bundle install 過了 ( rubytheracer好像需要比較舊版的libv8)
如果是rubytheracer請用gem uninstall libv8 再重新跑一次看看

需要調整 config/environment.rb 把 DemocracyOnline3換成Airesis
en.yml, it.yml 和pt.yml 裡面都有些小問題

- [x] 經典的
order:
   \- :day
   \- :month
   \- :year
- [x] 有些string忘了加 " "
- [x] 或者是多了空白行

- [x] rake db:setup 會hang住 取消之後但rails s 可以run
> hicloud 似乎是網路不穩的問題
> [name=Yuan C]


- [x] 稍後把翻譯好的zh.yml 放進去看看
> [https://github.com/g0v/Airesis](https://github.com/g0v/Airesis) zh-han branch
> [name=Yuan C]


- [x] development下, <head>裡面的application.js 和application.css都不會展開造成無法套用正確的css, 首頁沒有套用 這兩個所以顯示正常 ...
 模版

> 把rails 版本升到 3.2.12就好了
> [name=Yuan C]

- [x] signup會有問題
> 把recaptcha那段拿掉或者到config/enviroment.rb填上secret 
> [name=Yuan C]

- [ ] 無法註冊
> User Exists (0.4ms)  SELECT 1 AS one FROM "users" WHERE "users"."email" = 'test@g0v.tw' LIMIT 1, users裡面是空的, 不知道什麼妖術
> [name=Yuan C]

- [ ] 弄cookbook

### 可能要拿掉的Feature

1.  社群登入

