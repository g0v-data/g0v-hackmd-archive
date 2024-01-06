---
title: "Moedict - United Schema"
tags: 萌典,g0v,hackpad
---

# Moedict - United Schema

> [點此觀看原始內容](https://g0v.hackpad.tw/yN21Hgu8tuL)


### 問題

阿美語、台語、信望愛台語等等，需要用到的 metadata 的欄位都不同，
目前在信望愛台語萌典是用 hack hack 的方式，這樣程式會變得很髒。

### 想法

設計一個大家要用的欄位的聯集，然後修改一下萌典的架構，讓大家可以用同一個 livescript 來 render 萌典...

### metadata


| Word.latin | koe-kang |  | mi-tangtang-ay | pa-si'ael | word.latn |
| --- | --- | --- | --- | --- | --- |
| Word.漢字 | 雞公 |  |  |  | word.hant |
| 文白 | 白白 |  |  |  | wenbai |
| 索引詞 (ID) | koe-kang_雞公 | 各地的腔口可以連接到這個詞，解釋和例句只需要寫在索引詞的 entry 中就可以了。 | mitangtangay | pasi'ael | lexem |
| 腔口 | 普 | 大家都這麼用，就寫普吧 XD | 普 / 北部 / 海岸 | 五峰 / 東河 | dialect |
| 解釋.英文 | A cock |  | Cooking | Feed | defs.def.en |
| 解釋.中文 | 公雞 |  | 煮飯 | 餵 | defs.def.cmn |
| 解釋.台語.拼音 | blah blah |  |  |  | defs.def.nanlatn |
| 解釋.台語.漢字 | 成熟e公e雞 |  |  |  | defs.def.nanhant |
| 詞性 | N |  | V | V | defs.pos |
| 例句.台語.拼音 | blah blah |  |  |  | defs.ex.nanlatn |
| 例句.台語.漢字 | 掩裡雞公恨咱命 |  |  |  | defs.ex.nanhant |
| 例句.英語 | blah blah |  | He is cooking rice. | Mother is feeding her kid. | defs.ex.en |
| 例句.中文 |  |  | 他正在煮飯 | 媽媽正在餵孩子吃東西。 | defs.ex.cmn |
| 異用詞 | 袂, \[勿會\] | 漢字。教育部有寫法的順位，但民間習慣可能不同 |  |  | variants |
| 例句.amis |  |  | Mitangtang cingra to hmay. |  | defs.ex.amis |
| 字根 |  |  | tangtang | si'ael | root |
| 例句.saysiyat |  |  |  | 'oya' mam pasi'ael ka korkoring. | defs.ex.ss |
| 相關詞 | koe-bo_雞母 | 好難舉例啊 |  |  | defs.def.link |

### Json 範例

[https://gist.github.com/miaoski/dee8eef0924681bebb4e](https://gist.github.com/miaoski/dee8eef0924681bebb4e)
[https://gist.github.com/miaoski/ee9a9609da3f49a34e5c](https://gist.github.com/miaoski/ee9a9609da3f49a34e5c)

### 某個語言超過一本字典的話

可以用同樣的 metadata, 在查詢後先 aggregate 再丟上介面...

