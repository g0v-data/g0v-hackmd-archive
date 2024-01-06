---
title: "臺灣言語平臺"
tags: nan,hackpad
---

# 臺灣言語平臺

> [點此觀看原始內容](https://g0v.hackpad.tw/DqitE1wSSIo)

資訊技術的部份移去[https://g0v.hackpad.com/f4rSgcFTIzz](https://g0v.hackpad.com/f4rSgcFTIzz)

## 計劃目錄

- [http://hackfoldr.org/](http://hackfoldr.org/tai5-uan5_gian5-gi2_phing5-thai5/)[tai5-uan5_gian5-gi2](http://hackfoldr.org/tai5-uan5_gian5-gi2_phing5-thai5/)[_phing5-thai5/](http://hackfoldr.org/tai5-uan5_gian5-gi2_phing5-thai5/)

## 相關專案

- 新台語運動
    - [https://g0v.hackpad.com/moed7ct-taigi-neologism](https://g0v.hackpad.com/moed7ct-taigi-neologism)
    - [TaigiLex](https://g0v.hackpad.tw/TaigiLex)
- 萌典
    - [MoeDict ](https://g0v.hackpad.tw/jBwY0uGjPfB)

## 動機

- 母語工作者需要一個編輯、分享平臺
    - 母語資料散亂一地
    - 做研究時不能公開，做完又沒地方公開

## 目的

3.  提供母語研究者一個編輯平臺
    - 全部線上處理
    - 自由選擇是否公開

## 提供功能

- 語料收集
    - 每個人可加自己找到的語料
    - 可以讓人公開fb塗鴨牆、母語社團資料
- 眾人資料庫語料修改
    - 綁ＦＢ帳號crowdsourcing，
    - 拿出語句給每個人修改，並給每個人參與分數，類似plunker的karma
> 我想這是叫做 [Gamificaiton](https://en.wikipedia.org/wiki/Gamification)，如果真的要做的話可以做到很高度遊戲化。
> [name=Tsun-Huai S]

- 資訊技術
    - 語言分類、語料對齊
    - 語言模型、斷詞、翻譯
    - 語音辨識、語音合成
- 個人語料編輯
    - 上傳語音、線上切音/聽打
        - [http://otranscribe.com/](http://otranscribe.com/)
        - [https://www.ldc.upenn.edu/language-resources/tools/xtrans](https://www.ldc.upenn.edu/language-resources/tools/xtrans)

## 收集資料形式

1.  母語文字檔
2.  母語語音轉寫文字檔
    - 變調後的文字檔，同化異化等等作用後文字檔
    - 待討論
        - 母語語音轉寫文字檔有很多形式
            - 只有變調
            - 有變調+同化作用
3.  母語聲音檔
-
## 資料庫內對應

- 收集資料形式1~3項和華語語料兩兩對應
    1.  母語聲音和母語文字對照
    2.  母語語音轉寫文字檔和母語文字對照
    3.  母語語音轉寫文字檔和母語聲音對照
    4.  華語文字和母語文字對照
    5.  華語文字和母語聲音對照
        - 例如一般電視、廣播字幕和聲音對照
- 收集資料形式第1~3項混外來語
    6.  混外來語(華語、英語)的文字檔
        - 像是ＴＧＢ通訊、ＦＢ資訊
    7.  混外來語(華語、英語)的語音轉寫文字檔
        - 像是民視連續劇(華語閩南語混雜)
    8.  混外來語(華語、英語)的聲音檔
        - 像是民視連續劇(華語閩南語混雜)

## 個人語料編輯做法

- 上傳語音、文字
- 聽打工具
    - 有頻譜
    - 標文本
    - 多語者
    - 可參考xtrans
        - [https://www.ldc.upenn.edu/language-resources/tools/xtrans](https://www.ldc.upenn.edu/language-resources/tools/xtrans)

## 實作

- 框架/函式庫
    - django
    - 綁ＦＢ帳號
- 子計劃
    - 臺語言語工具
        - 台語好像沒有文字。如何處理呢?
> 不好意思因為兵役隔了有點久才回。漢字和音標預計以教育部的規範為主，[http://twblg.dict.edu.tw/holodict_new/index.html](http://twblg.dict.edu.tw/holodict_new/index.html)
> [name=薛丞宏]

    - 臺語言語資料庫

## 版權處理

- 無開放的資料
    - 文字檔
        - 語句打散，沒有上下文即沒有版權
    - 聲音檔
        - 不公開，做為內部資訊技術訓練語料


