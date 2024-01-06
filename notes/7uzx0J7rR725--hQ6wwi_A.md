---
title: "打臉高手 brainstorm"
tags: g0v.us,g0v us,hackpad
---

# 打臉高手 brainstorm

> [點此觀看原始內容](https://g0v.hackpad.tw/BoKu2ClFSE3)

## Overview

提供低瀏覽門檻，不容易歪樓謾罵的網路八卦版+新聞版yelp
- 利用群眾智慧
- 發現問題新聞
- 正確打臉資料
- 吸引大家圍觀
打臉原則：附出處
compact summary:
- 非PTT族群不好access, 歪樓情況->低瀏覽門檻
- 搜尋功能
- log-in default name: facebook
- category: 為何要打臉的原因
- keyword: offline grouping功能
- 講話要附reference
- 欠打指數--被打臉/觀看次數
- 回應: 正反雙方 取前三名計算血條 like量決定權重

## Core Features

1.  轉貼 Input source: 新聞小幫手(Computer)，User input.
    1.  link (URL)
    2.  文摘(ex, FB)
2.  Post Comment (FB pattern)
    1.  理由
    2.  論點
3.  Tag (不能太自由); 打臉理由是一種Tag (例如：證據不足, 詐騙)
4.  Categorize
    1.  Keyword (Grouping)
    2.  Auto assign
5.  市場機制(好文會浮上)
    1.  like
    2.  unlike
    3.  time (最後回應)
6.  回文
    1.  Support 有建設性地浮上(多數決)
    2.  打臉
7.  用FB確認身份, po文(map to a nickname)
    公開FB account(optional, but default set to yes)

## System Architecture

### Database

_Post_ \-\- id: pk; news_url: url; reason: String; vote: Int; views: Int; time: Ts;
        tag: Tag; author: User; keyword: Keyword;
_Response_ \-\- id: pk; original\_post: Post; response\_text: Text; upvote: Int;
        downvote: Int; author: User; timestamp: Ts;
_User_  \-\- id: pk; fb-id: String; nickname: String; reputation: Int; fb_link: boolean
_Subscribe Table_ \-\- user: User; post: Post;
_Tag_ \-\- id: pk; tag: String;
_Keyword_ \-\- id: pk; keyword: String;
### Web page

### Android (EXT)

### IOS (EXT)


## Use Cases

1.  User login
    1.  Core-7
2.  User posting (問卦) 有發文限制(5mins 1篇)  (rating: subscribe/views)
    1.  Core-1
    2.  Core-2
    3.  Core-3
3.  User response(戰)
    1.  Core-6
4.  User rating(補刀/聖光術)
    1.  Post rating
        1.  Core-5.a
        2.  Core-5.c
    2.  Response rating
        1.  Core-5.a
        2.  Core-5.b
5.  Backend
    1.  Core-4
    2.  Core-5
6.  Browsing
    1.  sorting  (post time, reply time, rate, views, # of replies, trending)
    2.  filter (unanswered, tag, keyword, )
7.  新聞小幫手Auto generate API  (EXT)
> 忽然發現這個好像滿重要的，不然我們沒有 data, 有沒有人要跳坑的 XD
> [name=dw5566]


## Reference

### Some Templates

1.  [http://support.lampcms.com/questions/](http://support.lampcms.com/questions/)
2.  [https://github.com/ialbert/biostar-central](https://github.com/ialbert/biostar-central)
3.  參考model:[新聞小幫手](http://newshelper.g0v.tw/)(原文新聞連結+打臉文連結)
4.  [http://www.factcheck.org/](http://www.factcheck.org/)
5.  [http://taipei.wethepeople.tw/#!/](http://taipei.wethepeople.tw/#!/)   (市長給問嗎？)

### Tools

1.  [url normalizer](https://github.com/g0v?query=normalizer) (under g0v)
2.  [django](https://docs.djangoproject.com/en/1.7/intro/install/) tutorial
3.  [http://nthn.me/posts/2012/facebook-registration.html](http://nthn.me/posts/2012/facebook-registration.html)
GINA version: (test.html use only; )
FACEBOOK\_APP\_ID = '1507946739477315'
FACEBOOK\_SECRET\_KEY = '2ae7ab56208209dce836dea7386ac3a9'
[https://developers.facebook.com/apps](https://developers.facebook.com/apps)
偷用駒的網路空間 [http://ece.umd.edu/~chou7337/login_page.html](http://ece.umd.edu/~chou7337/login_page.html)


## Code

[https://github.com/dwhuang/slap](https://github.com/dwhuang/slap)
> 等初步成果出來以後 merge 到 g0v 的 github [https://github.com/g0v/slap](https://github.com/g0v/slap)
> [name=dw5566]


> 剛剛把基本的 add post, add response, list posts 大致弄出鶵形，我把怎麼跑起來的步驟寫在 readme 裡 (github 上可以看到)，歡迎超展開
> [name=dw5566]


## Mockup

1.  打臉本文
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_077850b4059f9ff984e8335b6eaa802d)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_5849eae4bdbf10e5fa2a25e5b334ec84)
2\. 打臉文瀏覽頁
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_43c05ec78fdc7f2a8a98071a56c7789f)
3\. 打臉文輸入介面
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_721df9d57006fe99d88b8b47b398248d)
4\. 首頁
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_23296e0a73c31f2259c07b854eaa8658)
> 呼叫策群把投影片的圖放上來~
> [name=dw5566]

> 需要截圖~~拜託拜託...
> [name=Chiohh C]


## Feedback

- 如果有明顯邏輯錯誤的新聞，打臉文可能無法引用證據
- 如果新聞內容沒問題，只是下標題故意誤導(或純粹爛標題)怎麼辦?
> 這好像無法打臉... 我們是不是應該要界定一下我們要管多寬? 錯誤的新聞跟只是爛標題好像不太一樣..
> [name=dw5566]

> 我好像有偏文章想要你們來打臉... XDDDDDD  怎麼submit?
> [name=Chiohh C]

> 現在還沒實際成果可以用 XD
> [name=dw5566]



