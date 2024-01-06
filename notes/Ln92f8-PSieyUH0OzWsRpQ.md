---
title: "MoeDict - 萌典"
tags: hackpad
---

# MoeDict - 萌典

> [點此觀看原始內容](https://g0v.hackpad.tw/jBwY0uGjPfB)


[https://mo](https://moedict.tw/)[e](https://moedict.tw/)[di](https://moedict.tw/)[c](https://moedict.tw/)[t.tw](https://moedict.tw/)[/](https://moedict.tw/)

## 開發方向

今天除了將 a-tsioh 整理的新版英法德文包裝釋出之外，也想開始：
- 整理＜客家話常用詞典＞
    - 上次黑客松取得的原始資料: [http://www.audreyt.org/newdict/hakka.tar.gz](http://www.audreyt.org/newdict/hakka.tar.gz)
    - 需要轉成 [https://github.com/g0v/moedict-data-twblg](https://github.com/g0v/moedict-data-twblg)  相容格式
        - 參考其中的 dict-twblg.json，原有欄位意義保持一致下，請任意新增新欄位
        - 例句的格式用 \\uFFF9 \\uFFFB，如 hakka/9990.html ：
                {"def": "形容力量巨大，氣勢壯闊。",
                "example": \["\\ufff9大浪排山倒海打過來，企在海脣个人險險分佢捲走。\\ufffb大浪排山倒海打過來，站在海邊的人差一點被它捲走。"\]}
        - PUA 造字可忽略，能轉多少是多少，即使只有 title 都好
    - 客家典語音清單:
        - [https://github.com/g0v/moedict-data-hakka/blob/master/mp3-urls.txt](https://github.com/g0v/moedict-data-hakka/blob/master/mp3-urls.txt)
        - 正在轉成 ogg 中 -au
- 閩南語 拼音 輸入界面
- 試試新版型。hlb 做了一些開頭:
    - [http://moe.hlb.the-hold.handlino.com/](http://moe.hlb.the-hold.handlino.com/)
    - [https://github.com/audreyt/moedict-webkit/tree/master/ios/www](https://github.com/audreyt/moedict-webkit/tree/master/ios/www)
- 整合 ethantw 的直排注音樣式
    - [https://twitter.com/hlb/status/342664167246921729/photo/1](https://twitter.com/hlb/status/342664167246921729/photo/1)
    - [http://ethantw.net/lab/han/css/han.css](http://ethantw.net/lab/han/css/han.css) 國語注音符號（直式）
- 其他平台 (Win8, MeeGo, XULRunner, ...)
- ...請自行加上新主意!
- <閩南語多語詞典>
    - 資料來源：信望愛輸入法詞庫
    - 詞庫維護軟體：[http://wesay.palaso.org/](http://wesay.palaso.org/)
    - 詞庫 XML schema [https://code.google.com/p/lift-standard/](https://code.google.com/p/lift-standard/)
    - sync 信望愛輸入法詞庫的方法
        - [https://bitbucket.org/pcchen/nan](https://bitbucket.org/pcchen/nan)
        - private repo, 需要 get data 的人請跟 pcchen 說
- 想詢問萌典的開發方向，因個人背景關係。有一段時間喜歡越南文化。了解越南文化的當中發現越南與中華文化的密切關係，甚至越南歷史上曾經一度想要自創【漢喃】文字。且越文其實裡面也有很多古漢字的發音。
    - 漢喃 on Wiki: [https://zh.wikipedia.org/wiki/%E6%B1%89%E5%96%83](https://zh.wikipedia.org/wiki/%E6%B1%89%E5%96%83)
    - 範例: 漢文（[越南語](https://zh.wikipedia.org/wiki/%E8%B6%8A%E5%8D%97%E8%AF%AD)：Hán Văn／漢文），越南人又稱「[儒字](https://zh.wikipedia.org/wiki/%E5%84%92%E5%AD%97)」（[越南語](https://zh.wikipedia.org/wiki/%E8%B6%8A%E5%8D%97%E8%AF%AD)：Chữ Nho／??儒）  (前面的 ?? 好像是因為 hackpad 沒有支援 unicode 4.0 ? )
- 東南亞文化系列沙龍─第二場：東南亞語言同根生: [https://docs.google.com/forms/d/1RW8sWeRByeERY6EieQG1yAy-hqaJmngF2fC4DvdGics/viewform?pli=1](https://docs.google.com/forms/d/1RW8sWeRByeERY6EieQG1yAy-hqaJmngF2fC4DvdGics/viewform?pli=1)

## 開發者

au, a-tsioh, kcwu, yllan, ethantw, hlb, racklin, pcchen=pektiong, ...

### 分工與成員

- [x] NeedsData: 需要資料（擷取、清理）
- 客家典 HTML 轉 JSON  [http://www.audreyt.org/newdict/hakka.tar.gz](http://www.audreyt.org/newdict/hakka.tar.gz)
- 另外 fork 一個處理客家典 HTML 的 repo:
    - 初步成果 (a-tsioh): [https://github.com/g0v/moedict-data-hakka](https://github.com/g0v/moedict-data-hakka)
- [x] NeedsDesigner: 需要介面設計
- 從一個詞和它的注音 \+ 拼音 (如 [https://moedict.tw/uni/%E9%80%9A%E8%A8%8A%E8%87%AA%E7%94%B1](https://moedict.tw/uni/%E9%80%9A%E8%A8%8A%E8%87%AA%E7%94%B1) )，畫出結合拼音和直排注音的 CSS 來

## 閩南語 羅馬字 輸入界面

endkey:
space 表示完整結束
123456789 表示單一音節結束，有可能會繼續打下一個音節

case study
單字
g (not valid)
gu 顯示 gu*, gú*, gù*, gu̍* (gu̍p,gu̍t,gu̍k,gu̍h)
gu2 顯示 gú-* (遇到數字表示音節已結束)
gú 顯示 gú* gúa, gúng (知道是這個調，可是後面還可能出現其他母音)
si̍t-tsāi 顯示  si̍t-tsāi*
sit8-tsai7 顯示  si̍t-tsāi*
sittsai\[space\] 顯示  si̍t-tsāi, sit-tsâi, etc (任何可能的斷詞)

which means (my interpretation) :
except for gú -> gúa : are you sure we want this ?
onset and voyels are mandatory, tones and final may be omitted. and we input prefixes only.

如果設計的方向是：打多少羅馬字進來，就顯示跟目前以以輸入的羅馬字「相容」的可能詞彙。

I'm also not sure for the sittsai->sit-tsai, this may enlarge the search space a lot, especially with 入聲 that may be interpreted as onset consonnant

Need to make an index using "toneless format". 打多音節詞彙的時候，許多使用者習慣「無調號無連字符號」的方式。

無調：done
無連字：si-tsai和sit-sai就分不出來，介紹所有的結果會不會奇怪？而且一定會比較慢
\*\* 這是 UI 要怎麼設計的問題，是否讓使用者在可以輸入「不那麼明確的query」然後系統吐出所以可能的相容的結果。要求使用者「正確」的輸入連字符號的結果可能是使用者找不到想找的詞彙（因為不知道正確的寫法是什麼）。

Q:要不要支援 wildcard '!' and '*'

輕音問題
打 ah 要不要顯示 --ah ?
要

POJ -> TL conversion
ch->ts, chh->tsh, ou->oo, ek->ik, eng->ing,

### 羅馬字輸入 as a webservice

query as json {query:'sit8-tsai7', mode='<some mode>'}

results as {exact:\[string list of 臺語漢字\], prefix:\[string list\], fuzzy:\[string list\]}


### 整理＜客家話常用詞典＞類似


- [https://github.com/g0v/moedict-data-hakka](https://github.com/g0v/moedict-data-hakka)
    已完成：造字處理
    還需要：華<->客對照、線上語音、詞性

