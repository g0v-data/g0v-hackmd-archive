---
title: "TaigiLex"
tags: Taigi,hackpad
---

# TaigiLex

> [點此觀看原始內容](https://g0v.hackpad.tw/TaigiLex)


## Objectives overview

1.  Basic toolbox for online text editing in Taiwanese, to allow (2) (more below)
2.  an editable version of 萌典, to allow (3)
3.  The crowd-compilation of a Taiwanese dictionary in Taiwanese, post-reviewed by a small team
4.  the description of various lexical relations between the entries in the lexicon to allow more intelligent text-processor.

(English version and Mandarin version may not totally in sync.)

（目前英文及華文版說明尚未同步）
## 目標簡介

1.  發展可在線上編輯多重書寫系統台語文的書寫工具。
2.  發展可以協同編輯的萌典。
3.  發展群眾編輯、專家審議的開放台語詞典。
4.  增修台語詞典詞條與詞條之間關係的描述，以幫助開發更智慧的台語文書寫工具。

## Detailed description


###  The Toolbox


 What should it include:
-  Input Method from multiple romanisation systems and 注音符號 that permits output in various romanisations or 漢字 and keeps track of what was inputed for further edition.
- conversion tools between all the different scripts. (allowing for manual correction after the automatic processing)
- possibility to annotate the text using ruby

This shall be done as independent libraries that will be release in Open Source.

### A platform for the crowd compilation of a dictionary.


Those libraries will be used by an interface to have the dictionary edited by the netizens. (Probably integrated or directly linked with 萌典, to be discussed maybe forking or adding modules to etherpad would be better...)

### Supervision of the compilation process

A small team shall follow the edition of the dictionary (for selection/correction)
The dictionary will be released under C.C. licence, made available through 萌典 (and downloadable as epub ?)

### Towards a lexical graph

Time should be spent to describe the relations between the entries of the dictionary (synonyms, antonyms, metonyms,... ) to build a machine-readable lexicon to help and promote Taiwanese Text Processing

## 詳細說明

### 台語文書寫工具


### 協同編輯詞典的平台


### 語意網（？）



##  What we need


a small team of 2 to 4 pple for 6 to 12 month ?
I think it's reasonable for the coding part  (1 person)
one pb would be that the lexicographic work can only start once the code is working.

More precisely:
- 3~4 month for the toolbox
- +1 month for to define the dataformat and agregate some existing sources (in parallel of developping the toolbox, with help of pektiong and miaoski)
- +2month on hacking 萌典 / setting up the crowdsourcing platform
- +forever to crowdsource definitions

conclusion: ask for at least 3man×month budget for the tools and base dataset, then another 2~3month to setup and start crowdsourcing + any amount of $ for taiwanese lexicographers, the more the better.

## Discussion

- data of the Taiwanese dictionary (don't really need online editing tool?)
> If we want a small team of people working on the dictionary, that's true, but for crowdsourcing a good plateform working nicely in POJ/TL/hanji with 0-install would help.
> [name=A-Tsioh]

- tool to convert the data into 萌典 format
> what data ? the tool has to be data-source specific.
> [name=A-Tsioh]


### User scenario

-  online editing tool to
    - create new content in Taiwanese.
    - to better maintain/present/update current Taiwanese related digital archive. For example [http://pojbh.lib.ntnu.edu.tw/script/artical-3956.htm](http://pojbh.lib.ntnu.edu.tw/script/artical-3956.htm) has content in dual scrpts, but it is difficult to maintain.
> sounds like the next steps. I'd love to help on such projects.
> [name=A-Tsioh]


## Related resource and problems

### Online dictionary

#### 教育部

- 台灣閩南語常用詞辭典（有萌典）（中文解釋，有台語例句）
信望愛
- 甘字典：字的台語白話字解釋（及對應漢羅轉寫）
- 台日大詞典台語譯本（無日語原文解釋，有精簡？版台語翻譯解釋）
- [信望愛台語語料庫](https://bitbucket.org/pcchen/nan)（使用 [WeSay](http://wesay.palaso.org/) 編輯，透過 hg 與 bitbucket 同步）
#### 中研院

- 廈英大辭典（含增補廈英大辭典）
- 英廈辭典
#### 楊允言

- Tw-Ch台文中文辭典（台語羅馬字，台語漢字，中文詞條對照。無解釋）
- [台語文數位典藏](http://ip194097.ntcu.edu.tw/memory/TGB/MoWT.asp)（羅馬字，漢羅）
- [台語文記憶](http://ip194097.ntcu.edu.tw/Memory/TGB/mowt.asp)（圖檔）
#### Wikipedia

- [http://nan.wikipedia.org](http://nan.wikipedia.org) （白話字）
李勤岸
- [台語白話字文獻館](http://pojbh.lib.ntnu.edu.tw/script/index.htm) （白話字，漢羅。CC授權）

### Imput Methods

- 信望愛台語客語輸入法（Windows, OSX）

## Goals/Dreams (To be sorted into short/mid/long term goals later)

- Community based orthography recommendation (to avoid the term link standard or normalization XD)
    - 羅馬字（台羅，白話字）
    - 漢字
- Better imput methods (on different OS/devices; web-based)
- Better **off-line** dictionary (including a Taiwanese-Taiwanese dictionary
    - Taiwanese-Taiwanese
    - Taiwanese-Mandarin
    - Taiwanese-English
    - Taiwanese-Japanese
    - Taiwanese-Hakka
    - Taiwanese-Other languages/dialects in Min/SouthernMin (Wordnet of the South, long term)
- Dual script text processing
    - Semi-automatic tool to perform 羅馬字 to 漢字 and 漢字 to 羅馬字 conversion
    - Infrastructure to keep dual script sync (for editor or for web-content)
    - Semi-automatic annotation (Ruby) tool

## Current status

Case 0: Taiwanes Orthography

Case 1: From FHL-IME to FHL-DIctioanry
From pektiong=pcchen: Currently, the [信望愛台語料庫](https://bitbucket.org/pcchen/nan) uses LIFT as data format, uses WeSay as the client to edit and to sync with the hg server (bitbucket). [lift-convert](https://github.com/lukhnos/lift-convert) is then used to convert the entry (in the formate of "lomaji hanji") to csv, then be converted into database for the FHL-IME.

In principle multiple people can use WeSay to edit the same data, when WeSay sync with the hg server, it will perform auto-merge. Unfortunately, most of the time I am the only user. On can also edit the LIFT XML directoy, then use WeSay to sync to the hg server.

WeSay is slow and has only stable version on windows for now. WeSay also comes to some tools to convert the LIFT into HTML/PDF/Word but they don'w work well with large XML (such as 信望愛台語料庫). LIFT is designed for storing lexical information, so in principle it is a good choice for the data format for the Taiwanese dictionary. For a long time I cannot find good dictionary software so I didn't try tro use WeSay/LIFT to build a Taiwanese dictionary. Currently it only has many entries in the formate like "jiû-hî 鰇魚" to be used for IME.

We can also consider LMF ([http://www.lexicalmarkupframework.org/](http://www.lexicalmarkupframework.org/) , [http://en.wikipedia.org/wiki/Lexical\_Markup\_Framework](http://en.wikipedia.org/wiki/Lexical_Markup_Framework) )

With the birth of the 萌典, it becomes more likely that one can build a Taiwanese dictionary by (1) create/aggregate dictionary data (2) convert the data to 萌典 format. This is something I am testing now. The idea is to
- Aggregate data from on-line Taiwanese dictionaries into some dict data (say WeSay/LIFT)
- Create a conversion tool (miaoski has written a prototype)
- Enhance 萌典 （羅馬字搜尋，全文搜尋）etc
- After the inital bootstrap, need some way to 校對 and maintain/update the data

### Links

- [WeSay ](http://wesay.palaso.org/)
- [LIFT](https://code.google.com/p/lift-standard/) (Lexicon Interchange FormaT) is an XML format for storing lexical information, as used in the creation of dictionaries. It's not necessarily the format for your lexicon. That can be tied to whatever program you're using. But LIFT allows you to move that data between programs (hence the term 'interchange').

Case 2: Wikipedia and Digital Archive




