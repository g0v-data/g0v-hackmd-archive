---
title: "中文處理工具簡介"
tags: hackpad
---

# 中文處理工具簡介

> [點此觀看原始內容](https://g0v.hackpad.tw/aco0Hxp4IEz)


### 1\. 中研院CKIP parser

[http://ckipsvr.iis.sinica.edu.tw/](http://ckipsvr.iis.sinica.edu.tw/)
[http://parser.iis.sinica.edu.tw/](http://parser.iis.sinica.edu.tw/)
[‪](https://www.facebook.com/hashtag/%E7%B9%81%E9%AB%94?source=feed_text)[#](https://g0v.hackpad.tw/ep/search/?q=%23%E7%B9%81%E9%AB%94&via=aco0Hxp4IEz)[繁](https://g0v.hackpad.tw/ep/search/?q=%23%E7%B9%81%E9%AB%94&via=aco0Hxp4IEz)[體](https://g0v.hackpad.tw/ep/search/?q=%23%E7%B9%81%E9%AB%94&via=aco0Hxp4IEz)‬ [‪](https://www.facebook.com/hashtag/%E6%96%B7%E8%A9%9E?source=feed_text)[#](https://g0v.hackpad.tw/ep/search/?q=%23%E6%96%B7%E8%A9%9E&via=aco0Hxp4IEz)[斷詞](https://g0v.hackpad.tw/ep/search/?q=%23%E6%96%B7%E8%A9%9E&via=aco0Hxp4IEz)‬ [‪](https://www.facebook.com/hashtag/%E8%A9%9E%E6%80%A7%E6%A8%99%E8%A8%98?source=feed_text)[#](https://g0v.hackpad.tw/ep/search/?q=%23%E8%A9%9E%E6%80%A7%E6%A8%99%E8%A8%98&via=aco0Hxp4IEz)[詞性標記](https://g0v.hackpad.tw/ep/search/?q=%23%E8%A9%9E%E6%80%A7%E6%A8%99%E8%A8%98&via=aco0Hxp4IEz)‬ [‪](https://www.facebook.com/hashtag/%E5%8F%A5%E5%9E%8B%E7%B5%90%E6%A7%8B?source=feed_text)[#](https://g0v.hackpad.tw/ep/search/?q=%23%E5%8F%A5%E5%9E%8B%E7%B5%90%E6%A7%8B&via=aco0Hxp4IEz)[句型結構](https://g0v.hackpad.tw/ep/search/?q=%23%E5%8F%A5%E5%9E%8B%E7%B5%90%E6%A7%8B&via=aco0Hxp4IEz)‬ [‪](https://www.facebook.com/hashtag/%E4%BF%AE%E9%A3%BE%E9%97%9C%E4%BF%82?source=feed_text)[#](https://g0v.hackpad.tw/ep/search/?q=%23%E4%BF%AE%E9%A3%BE%E9%97%9C%E4%BF%82&via=aco0Hxp4IEz)[修飾關係](https://g0v.hackpad.tw/ep/search/?q=%23%E4%BF%AE%E9%A3%BE%E9%97%9C%E4%BF%82&via=aco0Hxp4IEz)‬
1\. 有點慢，準確率最高
2\. 可透過web service呼叫（詞性較粗）或爬網頁（詞性較細）。
3\. 可細分四十多種詞性，如名詞可細分為地方名詞、普通名詞，專有名詞等。
> 中研院的 CKIP parser 是比較建議使用在台灣語言環境中。但是很多時候分詞結果與辭典辭條的結果是不符合的，主要是因為在建立這個工具時，是依照專業家標記後的詞彙進行決定[詞彙詞性](http://rocling.iis.sinica.edu.tw/CKIP/tr/9305_2013%20revision.pdf)。但這個工具也年久失修…
> [name=August C]

> ~我申請帳號一直沒給認證信，工具下載下來也沒動靜，不知那邊出了問題~
> [name=張淵智]

> 能用了，不過速度有點慢
> [name=張淵智]

> 現在繁體中文分詞器可以做到95%正確率，詞性標記也有90%，其他功能就比較低了。中文的詞性是很複雜的，又可以『轉品』，有的時候詞庫沒有涵蓋到的例子，也parser很難正確標記出來。
> [name=Cicilia L]


### 2\. stanford parser

[http://nlp.stanford.edu/software/lex-parser.shtml](http://nlp.stanford.edu/software/lex-parser.shtml)
[http://nlp.stanford.edu/software/segmenter.shtml](http://nlp.stanford.edu/software/segmenter.shtml)
[http://nlp.stanford.edu/software/tagger.shtml](http://nlp.stanford.edu/software/tagger.shtml)
[‪](https://www.facebook.com/hashtag/%E7%B0%A1%E9%AB%94?source=feed_text)[#](https://g0v.hackpad.tw/ep/search/?q=%23%E7%B0%A1%E9%AB%94&via=aco0Hxp4IEz)[簡體](https://g0v.hackpad.tw/ep/search/?q=%23%E7%B0%A1%E9%AB%94&via=aco0Hxp4IEz)‬ [#](https://g0v.hackpad.tw/ep/search/?q=%23%E6%96%B7%E8%A9%9E&via=aco0Hxp4IEz)[斷詞](https://g0v.hackpad.tw/ep/search/?q=%23%E6%96%B7%E8%A9%9E&via=aco0Hxp4IEz)  [#](https://g0v.hackpad.tw/ep/search/?q=%23%E8%A9%9E%E6%80%A7%E6%A8%99%E8%A8%98&via=aco0Hxp4IEz)[詞性標記](https://g0v.hackpad.tw/ep/search/?q=%23%E8%A9%9E%E6%80%A7%E6%A8%99%E8%A8%98&via=aco0Hxp4IEz)  [#句型結構](https://g0v.hackpad.tw/ep/search/?q=%23%E5%8F%A5%E5%9E%8B%E7%B5%90%E6%A7%8B&via=aco0Hxp4IEz)  [#修飾關係](https://g0v.hackpad.tw/ep/search/?q=%23%E4%BF%AE%E9%A3%BE%E9%97%9C%E4%BF%82&via=aco0Hxp4IEz)  [‪](https://www.facebook.com/hashtag/ner?source=feed_text)[#](https://g0v.hackpad.tw/ep/search/?q=%23NER&via=aco0Hxp4IEz)[NER](https://g0v.hackpad.tw/ep/search/?q=%23NER&via=aco0Hxp4IEz)‬
1\. 處理繁體建議先轉成簡體以得到較佳效果
2\. 可下載單機版，可自己訓練繁體模型（不知道有沒有人分享出來）
3\. 支援多種程式語言：JAVA, Python, Ruby, PHP
4\. 詞性有十幾種
5\. 有NER 具名實體辨識

### 3\. mmseg 斷詞

[http://technology.chtsai.org/mmseg/](http://technology.chtsai.org/mmseg/)
[#繁體](https://g0v.hackpad.tw/ep/search/?q=%23%E7%B9%81%E9%AB%94&via=aco0Hxp4IEz)  [#斷詞](https://g0v.hackpad.tw/ep/search/?q=%23%E6%96%B7%E8%A9%9E&via=aco0Hxp4IEz)  [‪](https://www.facebook.com/hashtag/%E5%BF%AB?source=feed_text)[#](https://g0v.hackpad.tw/ep/search/?q=%23%E5%BF%AB&via=aco0Hxp4IEz)[快](https://g0v.hackpad.tw/ep/search/?q=%23%E5%BF%AB&via=aco0Hxp4IEz)‬
可下載單機版，可自己訓練繁體模型，可使用自訂字典
> 我執行的時候跳出視窗說windows版本不符
> [name=張淵智]

### 4.SCWS 中文分词

[http://www.xunsearch.com/scws/](http://www.xunsearch.com/scws/)
雖然是中國開發者做的，但試過處理正體中文也 OK ，只是詞庫並不是很豐富就是了。詞庫可以擴充，主要針對 PHP 開發者。

### 5.NLTK

python的自然語言處理包，需要先斷詞
[http://www.nltk.org/book/](http://www.nltk.org/book/)

### 6.CNLP

師大語言所製作的中文處理整合包(基於NLTK)，根據網頁說明，能處理經中研院斷詞、詞性標記過的文本，其他系統處理的斷詞不曉得能不能適用
[http://tm.itc.ntnu.edu.tw/CNLP/?q=node/5](http://tm.itc.ntnu.edu.tw/CNLP/?q=node/5)

### 7.結巴中文分詞（簡中）

[https://github.com/fxsjy/jieba](https://github.com/fxsjy/jieba)

### 8\. FudanNLP（簡中）

[https://github.com/xpqiu/fnlp/](https://github.com/xpqiu/fnlp/)

### 9\. Glove

Create word embeddings for further analysis
[http://nlp.stanford.edu/projects/glove/](http://nlp.stanford.edu/projects/glove/)

### 10\. OpenCC

繁簡轉換
[https://github.com/BYVoid/OpenCC](https://github.com/BYVoid/OpenCC)

### 11\. ansj

簡體斷詞
[http://www.nlpcn.org/demo](http://www.nlpcn.org/demo)
[https://github.com/NLPchina/ansj_seg](https://github.com/NLPchina/ansj_seg)

### 12\. 國教院分詞系統

中研院 CKIP 的衍生系統，據國教院的同仁說，新近詞的收量較大，跑起來也稍快些。
[http://120.127.233.228/Segmentor/](http://120.127.233.228/Segmentor/)
另外還附有一個語料索引系統：[http://120.127.233.228/Concordancer/](http://120.127.233.228/Concordancer/)

### 13\. cjknife

ref: [http://logbot.g0v.tw/channel/g0v.tw/2015-03-26#94](http://logbot.g0v.tw/channel/g0v.tw/2015-03-26#94)
異體字的辨識，輸出範例
cjknife -i 寳
```
Information for character 寳 (traditional locale, Unicode domain)
Unicode codepoint: U+5BF3 (23539, character form)
In character domains: Unicode, JISX0208, GlyphInformation, HKSCS, JISX0208_0213, BIG5HKSCS, IICore
Radical index: 40, radical form: ⼧
Stroke count: 19
Phonetic data (GR): bao
Phonetic data (MandarinBraille): ⠃⠖⠄
Phonetic data (MandarinIPA): pau˨˩˦
Phonetic data (Pinyin): bǎo
Phonetic data (WadeGiles): pao³
Semantic variants: 宝, 寶
Z-Variants: 寶
Glyph 0(), stroke count: 19
⿱宀　　⿱珎　　　　　　　　　　　　　　貝
　⿻冖？　⿰王　　　　　　尔　　　　　　⿱目　　　　八
　　　　⿱一土　　　　⿱⺈小　　　　　⿻口二
　　　　　　⿱十　　一　　⿻亅八　　　　　⿱一一
　　　　　　　⿻一丨　　　　⿰？？
Stroke order: ㇔㇔㇖㇐㇐㇑㇐㇒㇖㇚㇒㇔㇑㇕㇐㇐㇐㇒㇔ (D-D-HG H H-S-H P-HG SG P D S-HZ-H-H-H P D)
```
### 14\. Unicode Normalization

主要是用在清理一些看起來長的一樣但實際字碼不同的字
官方定義： [http://unicode.org/reports/tr15/](http://unicode.org/reports/tr15/)
PHP: [http://php.net/manual/en/class.normalizer.php](http://php.net/manual/en/class.normalizer.php)
JS: [https://github.com/walling/unorm](https://github.com/walling/unorm)

### 15.JIEBA 結巴中文斷詞

- 介紹簡報：[https://speakerdeck.com/fukuball/jieba-jie-ba-zhong-wen-duan-ci](https://speakerdeck.com/fukuball/jieba-jie-ba-zhong-wen-duan-ci)

### 16.Articut 中文斷詞暨語意詞性標記系統 (具 NER 功能)

- 商用等級的，無需自己準備資料做機器學習或模型訓練，可自定字典，也隨時可提出修正需求給原廠。300 元可處理 10 萬字。斷詞同時也做好了中文人名偵測、代名詞推理、語意詞性標記的推理…等。

- 介紹簡報：https://ppt.cc/fYCnOx

- 試用網站：https://api.droidtown.co 

- Github API 專案：https://github.com/Droidtown/ArticutAPI

- FB：https://www.facebook.com/Articut



## 名詞解釋

1\. 句型結構 syntactic structure
主語(主詞)，述語(動詞)，賓語(受詞)，子句，連接詞等
ps. 中英文的句型不一樣，所以括號內的英文句型詞彙只是簡單解釋，非相等。

2\. 修飾關係 dependency relation
例句： 猴子喜歡吃香蕉。
ccomp(喜歡-2, 吃-3) =>喜歡是吃的補語
dobj(吃-3, 香蕉-4) => 香蕉是吃的賓語

3\. NER, Named Entity Recognition, 具名實體辨識
可以抽取出特定專有名詞，常見的如人名、地名、組織名、數字、時間(time)、日期(date)。


## 經驗分享與討論

cicilia> 簡體的分詞器用在繁體文章，正確率大概是75%跟95%的差別，除了字典以外，訓練的語料庫影響也很大。繁體也有很多分詞器了。



g0v grants 2017SPRING 提案
可以不要再給我文字雲了嗎
https://grants.g0v.tw/projects/589084f646da1c001e3601d9
* 解決 text mining 技術的老舊。每個人都使用一樣的套件 (tm, jieba) 與功能，讓文本分析都長一樣。除了斷詞，關鍵詞擷取，關聯詞/語意距離，詞頻為主的文字雲 之外，我們要提供比較深層的「語詞的行為素描」，包括：
    * (多語單位）lexical bundles(congram)/MWE
    * (共現環境) concordance, collocation, colligation, lexical network（LSA, embeddings, social network of the lexicon）
    * (時間文類分佈）time-series analysis 語詞的時序分析，新詞存活力指標 stabilization measure。
* 本專案成果亦可應用至不同國家或地區的中文。我們的團隊對於處理「世界華語」(World Chineses) 有基本的前處理經驗。例如，前處理中最重要的一個步驟是「斷詞」，我們曾經比較過不同斷詞器的結果（包括北京清華大學的分詞器THULAC、香港的切詞器LIVAC，和臺大語言所的深度斷詞DeepSeg）。在實作上，我們將針對不同語料地區來源提供選擇界面，經過不同前處理之後，後續的處理工具即可一體適用。

