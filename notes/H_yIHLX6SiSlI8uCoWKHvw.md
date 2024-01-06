---
title: "你佇寫啥物！？臺灣語言資訊技術"
tags: hackpad
---

# 你佇寫啥物！？臺灣語言資訊技術

> [點此觀看原始內容](https://g0v.hackpad.tw/f4rSgcFTIzz)

Demo頁
    [http://用.意傳.台灣](http://用.意傳.台灣)
    在網頁文字上附聲音：[http://gaga978.github.io/gongdaigi/](http://gaga978.github.io/gongdaigi/)

## 相關專案

- iTaigi新台語運動
    - [https://g0v.hackpad.com/moed7ct-taigi-neologism](https://g0v.hackpad.com/moed7ct-taigi-neologism)
    - [TaigiLex](https://g0v.hackpad.com/TaigiLex)
- 萌典
    - [MoeDict ](https://g0v.hackpad.com/jBwY0uGjPfB)

## 進度

### 2016/2/20萌典松

[https://g0v.hackpad.com/oeBceDBeNA2](https://g0v.hackpad.com/oeBceDBeNA2)
- [ ] 替專案想個名字
- [ ] 前端要怎樣，使用者才方便
- [ ] 如何有效率的得到語料
    - [ ] 客家電視臺
    - [ ] 原視
        - 線上直播
        - [Aliyang網路廣播](http://aliyang.ipcf.org.tw/index.html)
        - [https://bitbucket.org/pcchen/nan](https://bitbucket.org/pcchen/nan)
    - [ ] ptt文章、推文（臺語的居多：呷飽、…）
        - [https://www.ptt.cc/bbs/Gossiping/M.1455729673.A.38B.html](https://www.ptt.cc/bbs/Gossiping/M.1455729673.A.38B.html)
    - [ ] 原住民族語言線上詞典
        - [http://e-dictionary.apc.gov.tw/Index.htm](http://e-dictionary.apc.gov.tw/Index.htm)

### 其他副本

    - [ ] 我會族語！！！我想要幫忙族語的語音技術
    - [ ] 我有語料，要怎麼貢獻出來
    - [ ] 我知道哪裡有母語資料，網址是……
- 我是工程師
        - [ ] 我要改翻譯程式，使用moses、…
> （我有捌用 moses 鬥過 MT pipeline，毋知敢有啥物通鬥變个無？）
> [name=Chu-Cheng L]

> 會當麻煩你研究moses的訓練無？
> [name=薛丞宏]

> 這馬我是用'scripts/training'/train-model.perl'佮預設的訓練參數
> [name=薛丞宏]

> 伊會產生alignment model、language model佮reorder model，三個model
> [name=薛丞宏]

> alignment model需要平行語句佮辭典
> [name=薛丞宏]

> reorder model干焦愛平行語句，無愛辭典
> [name=薛丞宏]

> 我這馬共平行語句佮辭典攏下入去訓練
> [name=薛丞宏]

> 毋過進前有學長講，辭典下入，會影響伊的reorder模型
> [name=薛丞宏]

> 想講敢有法度，予辭典莫影響著reorder model無？
> [name=薛丞宏]

> 你講个辭典是啥物款？尚簡單个模型干焦需要平行語料耳，總--是，若是有辭典feature，會當tune出較好个模型。
> [name=Chu-Cheng L]

> 我頂擺主要是照tsit份做个：[http://www.statmt.org/moses/?n=Moses.Baseline](http://www.statmt.org/moses/?n=Moses.Baseline)
> [name=Chu-Cheng L]

> （抑是敢卜來試看覓這馬尚時行的seq2seq? XD [https://www.tensorflow.org/versions/r0.7/tutorials/seq2seq/index.html](https://www.tensorflow.org/versions/r0.7/tutorials/seq2seq/index.html)）
> [name=Chu-Cheng L]

> 我這馬是用這個baseline
> [name=薛丞宏]

> 這是我整理到一半的語料 [https://www.dropbox.com/s/5ej3dcwpz3p2wia/%E9%96%A9%E5%8D%97%E8%AA%9E.tar?dl=0](https://www.dropbox.com/s/5ej3dcwpz3p2wia/%E9%96%A9%E5%8D%97%E8%AA%9E.tar?dl=0)
> [name=薛丞宏]

> 嘛是我下佇網站的moses訓練語料，我的意思是「字詞」下入去平行語料是毋是會影響著翻譯效果？
> [name=薛丞宏]

> seq2seq我拄仔查，看起來門檻無低，愛用心調參數才有法度比moses好XDD
> [name=薛丞宏]

> 你嘛會使用這語料試驗覓seq2seq
> [name=薛丞宏]

> 感恩！我共語料下落來矣。毋過這暫仔較無閒，愛拜六才有通詳細來看。
> [name=Chu-Cheng L]

        - [ ] 我要改合成程式，用HTS、…
        - [ ] 我想做語音辨識，可以考慮HTK、Kaldi、…


## 動機

- 提供一般人可以用臺灣母語的資訊技術
    - 網路上都是華語的資料
    - 提供一般人學母語、查母語的所在
    - 辭典是有母語基礎的人才有辦法使用
        - 初學者需要母語語句正確寫法、母語唸法
            - 司機B: 那會 chiah gâu 講台語。
            - Tâi-gí-bûn chhut-thâu-thiⁿ!

- 整理母語語料
    - 母語資料散亂一地
    - 做研究常常遇到找不到語料的問題

## 目的

- 讓一般人能輕易學會正確寫法
    - 輸入「我要吃飯」、「我要呷飯」，顯示「我欲食飯」
> 這個idea讚！類似自然/新注音輸入法一類的自動校正
> [name=Chou S]

    - 技術：正規化/翻譯

- 讓電腦/手機講母語
    - 技術：語音合成


## 做法

- 正規化/翻譯
    - 統計的技術，所以語料的數量影響翻譯的效果
- 語音合成
    - 同一個人，清楚的音檔一千句以上，愈多愈好


### 臺語

- 翻譯
    - [ ] 語料不足
    - [ ] 語料勘用
    - [ ] 語料足夠
- 語音合成
    - [ ] 沒聲音模型
    - [ ] 聲音模型勘用
    - [ ] 聲音普通
    - [ ] 聲音好聽

### 客語

- 翻譯
    - [x] 語料不足
    - [ ] 語料勘用
    - [ ] 語料足夠
- 語音合成
    - [ ] 沒聲音模型
    - [ ] 聲音模型勘用
    - [ ] 聲音普通
    - [ ] 聲音好聽

### 南島語

- 翻譯
    - [ ] 語料不足
    - [ ] 語料勘用
    - [ ] 語料足夠
- 語音合成
    - [ ] 沒聲音模型
> 我帶的開源虛擬歌手計畫，其實有子計畫-台語的聲音庫以及虛擬歌手合成引擎的衍生應用-超清晰、自然的語音合成，只是還在努力當前主任務-華語聲音庫中，還顧不到台語聲音庫製作（錄音表已經完成基本單獨音整理，待跟已錄好的日語、華語音diff，找出台語需要新錄音的部份）以及歌手轉語音合成的延伸模組製作。有人有興趣有耐心的話，請跟我聯絡，將來就會有嬌滴滴的女生聲音可用囉:P
> [name=Chou S]

    - [ ] 聲音模型勘用
    - [ ] 聲音普通
    - [ ] 聲音好聽


