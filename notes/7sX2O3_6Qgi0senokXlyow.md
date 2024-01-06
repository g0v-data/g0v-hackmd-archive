---
title: "臺語語音轉文字輸入法"
tags: hackpad
---

# 臺語語音轉文字輸入法

> [點此觀看原始內容](https://g0v.hackpad.tw/q5zhtMJeVQm)

提案人：[**薛丞宏**](https://www.facebook.com/chenghung.hsueh)
、[**許嘉勇**](https://www.facebook.com/kaiong.khoo)(鹿港腔)、
[**莊文龍**](https://www.facebook.com/win3798?fref=nf)(宜蘭腔)先生
**顧問:**[**POCHUNG PEKTIONG CHEN**](https://g0v.hackpad.com/ep/profile/rskoUyLFJ6N)**教授、潘科元教授、**[Liz Lim](https://www.facebook.com/liz462?fref=nf)
所有成員陸續邀請加入中~~聯絡人win3798@gmail.com莊文龍0911217668

10/1的萌典松：[http://moe.kktix.cc/events/moedict-10-1](http://moe.kktix.cc/events/moedict-10-1)

Forvo 現成閩南語（有的是福建的）語音語料：[http://zh.forvo.com/languages/nan/](http://zh.forvo.com/languages/nan/)（CC BY-NC-SA 3.0）

## 目標

做臺語語音辨識
- 使用的情境是？
    - 語音輸入法
    - 規句？
    - 一個詞？
    - 平常時講話？
> 宜蘭腔臺南腔金門腔鹿港腔所有腔口攏會使通用!
> [name=薛丞宏]

> 手機輸入&衛星導航
> [name=薛丞宏]

> 電腦拍文件，像咱對話免拍字用麥克就有字出現，留下會議紀錄等。
> [name=薛丞宏]

- 使用的對象是？

## 語音辨識

### 需要語料

- 臺語音檔，佮對應的臺羅
    - 中研院高明達教授有253點鐘的臺語聽拍
    - 臺羅需要照腔口
- 大量的臺語語句
    - 臺羅、漢羅攏會使
    - 這馬手頭有欲規百萬句
        - [https://github.com/sih4sing5hong5/tai5-uan5\_gian5-gi2\_hok8-bu7/wiki/Taiwanese-Corpus%E8%AA%9E%E6%96%99](https://github.com/sih4sing5hong5/tai5-uan5_gian5-gi2_hok8-bu7/wiki/Taiwanese-Corpus%E8%AA%9E%E6%96%99)
### 技術

- 軟體
    - HTK、kaldi, CMU Sphinx
> HTK is not Open Source, and reuse of modified version seems uneasy）
> [name=A-Tsioh]

> 我是希望借重GOOGLE技術，目前請國內專家先試做，若有法度就免靠GOOGLE。
> [name=莊文龍]


- 有佇用上新深度學習做語音辨識的老師
    - 曹昱，陳信宏，李琳山，簡仁宗，陳柏琳

## 分工

### 錄臺語音檔

1.  準備語句，有漢字佮臺羅
    1. 稿部分我想對[臺語歌詞先做](http://xn--https-me4hp9cjy1i7w3b0srcua/www.facebook.com/groups/922800454445724/)[https://www.facebook.com/groups/922800454445724/](https://www.facebook.com/groups/922800454445724/)
    2. 教育部臺語常用典例句，您敢會使予我所有例句的Excel檔案?
    3. 其他文獻，或辭典必做的建議。我感覺初期若做到以上兩種應該就真豐富囉?
    4.  Taiwanese [http://163.20.42.2/country/FIVE_LANG/5L/M/mn/A.html](http://163.20.42.2/country/FIVE_LANG/5L/M/mn/A.html)  五語快譯通已有文稿語音
    5.  教育部臺語常用典 [http://blog.ilc.edu.tw/blog/blog/3860/post/37836/190706](http://blog.ilc.edu.tw/blog/blog/3860/post/37836/190706)
        1.  18207words [http://blog.ilc.edu.tw/blog/gallery/3860/3860-770766.doc](http://blog.ilc.edu.tw/blog/gallery/3860/3860-770766.doc)
    6.  教育部臺語朗讀文章&聲音檔 [http://163.17.109.129/language/old/%E9%96%A9%E8%AA%9E%E6%9C%97%E8%AE%80.htm](http://163.17.109.129/language/old/%E9%96%A9%E8%AA%9E%E6%9C%97%E8%AE%80.htm)
    7. 錄家己捌寫過的文章
        1.  講的較順，較口語
        2.  閣念一擺，就會知影文章有佗位會當閣進步
        3.  有一个機會整理家己的文章
    8.  揣囡仔冊來錄
        1.  閣會當有別的用途
> 教育部辭典： [https://github.com/g0v/moedict-data-twblg/tree/master/uni](https://github.com/g0v/moedict-data-twblg/tree/master/uni)
> [name=薛丞宏]

> 用歌詞、例句，錄出來的語氣、講語速度可能會無仝
> [name=薛丞宏]

> 會當麻煩先佇「目標」彼爿整理，咱錄音較有效率
> [name=薛丞宏]


> 恁若是
> [name=薛丞宏]

2.  做網頁用電腦錄音，抑是做app用手機仔錄音~~這个部分我會當請啥人先做?
    - 100句做伙唸，毋過逐句中央閬較久咧
        - 無一定逐擺攏愛100，50、70、30句攏會使，免逐擺攏仝款、只是愛記錄是佗幾句
    - 有wav檔上好，盡量莫壓縮做mp3
    - 取樣頻率盡量選48000HZ
> 我做一個簡單的網站，予逐家傳音檔
> [name=薛丞宏]

> 非常感謝!錄音順序可能請先思考好a~f佗一項先做，我才來排。
> [name=莊文龍]

> [https://github.com/sih4sing5hong5/TaiwaneseInputMethod](https://github.com/sih4sing5hong5/TaiwaneseInputMethod)
> [name=薛丞宏]

> [http://錄音檔.語音輸入法.意傳.台灣/](http://錄音檔.語音輸入法.意傳.台灣/)
> [name=薛丞宏]

> 若有老師先錄音，先加減用。
> [name=薛丞宏]

> 網路頂錄音，工足大的，
> [name=薛丞宏]

> 我這馬無法度做，建議10/1去萌典松報告，揣別的工程師做伙來做
> [name=薛丞宏]

> 錄音檔案一開始就要wav檔
> [name=莊文龍]

> 如果一開始毌是，轉檔的音檔品質就有問題。
> [name=莊文龍]

> 取樣頻率盡量選48000HZ
> [name=莊文龍]




  3.錄好的音照實際發音腔口修正臺羅
  4.莊文龍負責整合分配語料錄音部分。
  5.願意鬥相共錄音的人員[**許正輝**](https://www.facebook.com/tsing3hui1)、[**蔡惟華**](https://www.facebook.com/profile.php?id=100000568187509)、[**許嘉勇**](https://www.facebook.com/kaiong.khoo)(鹿港腔)、[**莊文龍**](https://www.facebook.com/win3798?fref=nf)(宜蘭腔)、[**Ling-ing Koo**](https://www.facebook.com/linging.koo) 、[**陳文傑**](https://www.facebook.com/chenwujack.chen?fref=ufi) (宜蘭腔)、[**劉玉玲**](https://plus.google.com/100640047021666587663)、紀品志
> 敢有佮逐家講，錄好的音檔，愛用啥物版權釋出予人用？CC0？
> [name=薛丞宏]

> 遮愛閣通知逐家!!CC0
> [name=莊文龍]

 [http://creativecommons.tw/cc0](http://creativecommons.tw/cc0)
### 技術

- 丞宏會先試HTK佮kaldi
> 我10月前會先做出20～30分的作品出來，才看狀況。看後一步欲按怎行
> [name=薛丞宏]

- 等kaldi有法度接錄音檔後，會當提供予教授，予in做研究
[sih4sing5hong5/tai5 uan5\_gian5 gi2\_kang1 ku7#281](https://github.com/sih4sing5hong5/tai5-uan5_gian5-gi2_kang1-ku7/issues/281)

