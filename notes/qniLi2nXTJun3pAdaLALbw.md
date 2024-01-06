---
title: "politwoops.tw 我說錯了嘛"
tags: politwoops.tw,hackpad
---

# politwoops.tw 我說錯了嘛

> [點此觀看原始內容](https://g0v.hackpad.tw/TMZxxNandPs)


## 專案簡介

收集政治人物刪除的facebook posts，先以立委為主
後端 facebook collector
- [https://www.facebook.com/help/interest-lists](https://www.facebook.com/help/interest-lists)
- [tweet-collector](https://github.com/sunlightlabs/politwoops-tweet-collector)
    - python
> 有沒有一些範例的政治人物 facebook page? 如果沒有政客用 twitter 的話，就不做 twitter 吧? 
> [name=ihower C]

> 對啊所以是要用facebook page
> [name=Yuan C]

> 換句話說，需要依據 politwoops 的 spec 寫另外一個 facebook-collector 囉？
> [name=Jeff H]

> 是，不過facebook有些機制跟tweet不一樣，所以可能要調整一下
> [name=Yuan C]

- facebook-collector (not existing yet)
    - Tools - [https://developers.facebook.com/docs/other-sdks](https://developers.facebook.com/docs/other-sdks)
        - [https://github.com/pythonforfacebook/facebook-sdk](https://github.com/pythonforfacebook/facebook-sdk)

- Schema SQL: [https://gist.github.com/yhsiang/d8bb81aa488ba9bebf39](https://gist.github.com/yhsiang/d8bb81aa488ba9bebf39)

前端
- [politwoops frontend](https://github.com/sunlightlabs/politwoops)
    - rails

[http://community.g0v.tw/t/politwoops-tw/220](http://community.g0v.tw/t/politwoops-tw/220)
- 提案題目： 我說錯了嘛 (([idea4](http://logbot.g0v.tw/channel/g0v.tw/2014-06-19#370)。
- 主要把 [http://politwoops.sunlightfoundation.com/](http://politwoops.sunlightfoundation.com/) rewrite for .tw 用
> 這一頁現在是 404 耶
> [name=Jeff H]

> 多了一個4 XDD
> [name=Yuan C]

- 提案內容：
    - 把 politwoops.tw 整個架起來
    - 建後端的 collector
    - 做資料測試
    - 修 mockup and web 介面
- 提案進度：
    - 期中報告前完成 1\. ，2.的部份希望可以做到一半...
    - 成果報告前做完 3\. ，速度夠快的話希望可以把 4. 做完
    - ((但感覺有困難QQ
- 為什麼可以完成：
- 唔這部份...其實我也沒信心QAQ... (畢竟collector using python, web using rails, 兩個算是都沒碰過)
- 語言的部份是這樣，但 web1.0 的時候有刻過站，也幫學校刻過電子報的網頁...(都用刻是因為現在回頭想都覺得寫得很糟=_=)，大四專題的Code 也大部份是我在寫(含規劃，不過是本來就有 idea)，邏輯上還行(?)， script 類之前學 flash 的時候碰過 as2, 3，有用 Adobe Flex 寫過外包的東西QQ....所以動態語言應該也…還行？
- 總之就試看看吧XD

## 政治人物粉絲專頁


- 政治人物fb 或fb page
    - [蔡正元](https://www.facebook.com/tsaichengyuan) (fb page)
    - [羅淑蕾](https://www.facebook.com/profile.php?id=100001773850305&fref=ts)
    - [丁守中](https://www.facebook.com/drtingsc?fref=ts)

| 政治人物 | Facebook 個人頁 | Facebook 粉絲頁 | Facebook 社團 | Facebook 活動頁 | Twitter | Plurk | G+ |
| --- | --- | --- | --- | --- | --- | --- | --- |
| (特性) | 可自定privacy，可「申請好友」 | 公開，可「按讚」 | 需被邀請才能進入 | 有時間性，活動期間才容易進入留言 |  |  |  |
| 蔡正元 |  | [https://www.facebook.com/tsaichengyuan](https://www.facebook.com/tsaichengyuan) |  |  |  |  |  |
| 丁守中 |  | [https://www.facebook.com/drtingsc](https://www.facebook.com/drtingsc) |  |  |  |  |  |
| 羅淑蕾 | [https://www.facebook.com/profile.php?id=100001773850305&fref=ts](https://www.facebook.com/profile.php?id=100001773850305&fref=ts) |  |  |  |  |  |  |
| 馬英九 |  |  |  |  | [https://twitter.com/PresidentMa19](https://twitter.com/PresidentMa19) |  |  |
| 民進黨 |  |  |  |  | [https://twitter.com/DPPonline](https://twitter.com/DPPonline) |  |  |
| 國民黨桃園縣縣黨部 |  |  |  |  | [https://twitter.com/kmttyparty](https://twitter.com/kmttyparty) |  |  |
| 王丹 | [https://www.facebook.com/profile.php?id=700949667&fref=ts](https://www.facebook.com/profile.php?id=700949667&fref=ts) | [https://www.facebook.com/pages/%E7%8E%8B%E4%B8%B9%E7%BD%91%E7%AB%99-Wang-Dans-Page/105759983026?ref=stream&fref=nf](https://www.facebook.com/pages/%E7%8E%8B%E4%B8%B9%E7%BD%91%E7%AB%99-Wang-Dans-Page/105759983026?ref=stream&fref=nf) |  |  | [https://twitter.com/wangdan1989](https://twitter.com/wangdan1989) |  | wangdan@gmail.com |
| 謝長廷 |  |  |  |  |  | [http://www.plurk.com/frankcthsieh](http://www.plurk.com/frankcthsieh) |  |
| 朱學恆 |  |  |  |  |  | [http://www.plurk.com/luciferchu](http://www.plurk.com/luciferchu) |  |
> 這個好專業 XDDD
> [name=Yuan C]

[我的選區立委是誰？](https://sites.google.com/site/ccwdata/monitoring/whosmylegislator)  by 公督盟
[區域立委資料.json](https://www.dropbox.com/s/dgj7ay9fjsuukoj/localLy.json) ↑ parse.
[不分區立委資料.json](https://www.dropbox.com/s/p3r3puy3ry9r0jw/nationwideLy.json)

