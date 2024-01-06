---
title: "辭典學字典結構 與 moedict 資料結構的比對"
tags: hackpad
---

# 辭典學字典結構 與 moedict 資料結構的比對

> [點此觀看原始內容](https://g0v.hackpad.tw/lcEFcpToerf)


### 資料來源

1.  [辭典學 \- 參考網站](http://www.christianlehmann.eu/ling/ling_meth/ling_description/lexicography/dict_structure.html)
2.  [3du.tw DB schema](https://hackpad.com/3du.tw-DB-schema-8I4XU6xc4QJ)
3.  [moedict-process/dict-revised.schema](https://github.com/g0v/moedict-process/blob/master/dict-revised.schema)
4.  [3du.tw API Design](https://hackpad.com/3du.tw-API-Design-95jKjray8uR)

### 註解方式

- Lemma, 代表辭典學網站內有提到的欄位
- +radical, 代表 moedict 特有欄位。
- moedict\['entries'\], 代表 moedict database table
- entries\['title'\], 代表 entries table 內的 title 欄位

### 辭典學詞典結構 vs MOEDICT資料結構

Dictionary
1.  Table of content
2.  Preface
3.  Instructions
4.  Grammatical information
5.  Appendices
    1.  Transliteration
    2.  Conversion table
    3.  Abbreviations
    4.  Symbols
    5.  Bibilography
1.6         Entry list
    1.  Entry
        1.  Entry Identity (moedict\['entries'\])
            1.  Lemma (詞元, entries\['title'\])
            2.  Homonym number(諧音+編號)
            3.  Sense number
            4.  Citation form
            5.  +radical (部首, entries\['radical'\])
            6.  +stroke\_count (總筆畫, entries\['stroke\_count'\])
            7.  +non\_radical\_stoke\_count (去部首筆畫, 詞語為null, entries\['non\_radical\_stroke\_count'\])
        2.  Expression(heteronyms part in moedict)
            1.  Phonological representation(語音表示, moedict\['heteronyms'\])
                1.  +bopomofo(注音, heteronyms\['bopomofo'\])
                2.  +bopomofo2(國音二式, heteronyms\['bopomofo2'\])
                3.  +pinyin(漢語拼音, heteronyms\['pinyin'\])
            2.  Sound(發音)
            3.  Phonological variants(音韻的變異)
            4.  Orthographic variants
        3.  Language variety
            1.  Dialect(方言)
            2.  Sociolect
            3.  Style(如正式用語、俚語、俗稱的註記)
            4.  Stage
        4.  Structure
            1.  Proper Name
            2.  Syntactic category(詞性, definitions\['type'\])
            3.  Morphological structure
            4.  Word formation
            5.  Derivatives
            6.  Morphological categories
            7.  Irregular inflection
            8.  Construction
            9.  Phraseology(用語，如詞句、成語等)
        5.  Meaning(字義, moedict\['definitions'\])
            1.  Meaning definitions
                1.  Native definition (原始字義, definitions\['def'\])
                2.  User language definitions
            2.  Gloss
            3.  Semantic classes(語意分類)
            4.  Semantic relations(其他相關語意, definitions\['link'\])
                1.  Synonymy(同義詞, definitions\['synonyms')
                2.  Hyponymy(上下位關係?)
                3.  Antonymy(反義詞, definitions\['antonyms'\])
                4.  complementarity (contradictory contrast(矛盾的對比??))
                5.  part-whole relation(部分與整體的關係???)
            5.  Encyclopedic information
            6.  Picture
        6.  Genetic-historical information
            1.  Origin(典源, definitions\['source')
            2.  Etymology(詞源, definitions\['quote'\])
            3.  Cognates
            4.  Examples(例句, definitions\['example')
        7.  Methodology
            1.  Bibliographical references
            2.  Comment
            3.  Problems
            4.  Date


