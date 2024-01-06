---
title: "注音標音OpenType Font計畫"
tags: moedict,hackpad
---

# 注音標音OpenType Font計畫

> [點此觀看原始內容](https://g0v.hackpad.tw/bFFqBpPmcz0)

- 提案人：董福興
- 執掌單位：教育部終身教育司第四科「[閱讀與語文教育科](http://www.edu.tw/pages/detail.aspx?Node=3932&Page=21619&Index=1&WID=c5ad5187-55ef-4811-8219-e946fe04f725)」

## 說明

　　注音符號在Web上的顯示，除了使用[Polyfill](http://css.hanzi.co)處理以外，還是希望能夠通過標準化的方式在各瀏覽器上得到[實作](https://hackpad.com/Ruby-LEe9MlhFMGl)。尤其是[ruby-position: inter-character的實作](https://vimeo.com/106509250)，幾乎讓注音在Web上的顯示只差一步，而那一步就是調號（tone mark, e.g. ˊˇˋ）該怎麼被放到注音的右側。

　　最近在W3C i18-CJK的討論群組上開始[討論這個議題](https://lists.w3.org/Archives/Public/public-i18n-cjk/2015JanMar/)，而有了比較清楚的輪廓。可以確定的是調號不屬於Layout Engine的處理範圍，而交由OpenType來實作會較佳，而最好是能做出一套僅有注音符號與調號的開源OpenType字體，具備對應的GPOS功能，能將調號放到右側去。不管是透過安裝、內嵌或者網路字型（Webfont）的方式提供，都能讓調號得以放到對的位置。
> 來自Ishi Koji的[推坑信](https://lists.w3.org/Archives/Public/public-i18n-cjk/2015JanMar/0033.html)。
> [name=Bobby]

> @But 的注音符號字體感覺可以直接用了[http://but.tw/font/bpmfpy.html](http://but.tw/font/bpmfpy.html)
> [name=Chen Y]

> 这个好强大，连竖排支持都不需要了，直接用字体解决全部问题。
> [name=Xidorn Q]

> 這我知道，但真不能什麼都用Font做掉w
> [name=Bobby]


- 注音符號Ruby標注範例：

```
<ruby>我<rt>ㄨㄛˇ</rt></ruby>

```
- 調號僅會與以下符號一併出現：ㄓㄔㄕㄖㄗㄘㄙㄚㄛㄜㄝㄞㄟㄠㄡㄢㄣㄤㄥㄦㄧㄨㄩ，即U+3113—U+3129。
- 調號位置請參考《[國語注音符號手冊](https://www.dropbox.com/s/09yk4int5t1b5m8/mandarin_zhuyinfuhou_handbook.pdf?dl=0)》。
- 調號Unicode
    - 二聲U+02CA MODIFIER LETTER ACUTE ACCENT
    - 三聲U+02C7 CARON
    - 四聲U+02CB MODIFIER LETTER GRAVE ACCENT
    - 輕聲U+02D9 DOT ABOVE
- 注音符號Unicode
    - U+3105-U+3129（即ㄅ到ㄩ）
    - 應該不用包括U+312A-U+312D
    - U+31A0-U+31BA（方言音擴展）
- OpenType GPOS registered feature: "[mark](https://www.microsoft.com/typography/otspec/features_ko.htm)"
> Description: [https://www.microsoft.com/typography/otfntdev/standot/features.aspx](https://www.microsoft.com/typography/otfntdev/standot/features.aspx)
> [name=Bobby]

> Gecko Ruby的實作者Xidorn[認為](https://lists.w3.org/Archives/Public/public-i18n-cjk/2015JanMar/0028.html)"mark"較適合。
> [name=Bobby]

> 其实我在想是不是不用任何 feature 也可以？我不是很了解字体这边一般的做法是什么，不过如果正常文本中都是这样做的话，是否也一定需要一个注册的 feature 呢？
> [name=Xidorn Q]


## 人力需求

熟OpenType規格與製作的Font Designer & Font Engineer。
> 萌典的 font engineer 是 魏藥 (medicalwei)，另外 kcwu 也參與思源黑的製作
> [name=Audrey T]

> 另外 BiaoDian Pro 注音字型是 ethantw 製作的，以上是萌典字體三人組~
> [name=Audrey T]

> Twitter上已經推坑，kcwu怎麼聯絡好呢？
> [name=Bobby]

> @kcwu 也在 Twitter 上~
> [name=Audrey T]

> 也找到@But K
> [name=Bobby T]


## 技術實作需求

1.  首先，從開源字型中取出U+3105-U+3129（即ㄅ到ㄩ）、以及二聲U+02CA、三聲U+02C7、四聲U+02CB、輕聲U+02D9的Subset。
2.  套用GPOS Feature "[mark](https://www.microsoft.com/typography/otspec/features_ko.htm)"。
3.  當文字直排，且U+02CA、U+02C7、U+02CB三個調號前接U+3113（ㄓ）-U+3129（ㄩ）時，將調號放到符合《[國語注音符號手冊](https://www.dropbox.com/s/09yk4int5t1b5m8/mandarin_zhuyinfuhou_handbook.pdf?dl=0)》的右上角位置。
> 僅需近似，不需完全符合。
> [name=Bobby]

> 有用 fontforge 做過 0 寬度的字體，可以試著做出 0 高度的字體並且將調號移動到負字元高度…（我試著做看看）
> [name=Ming-ting W]

> ↑受小弟一拜。
> [name=Bobby]

> [http://code.newtypography.co.uk/creating-contextual-ligatures-in-fontforge/](http://code.newtypography.co.uk/creating-contextual-ligatures-in-fontforge/)
> [name=Ming-ting W]

> （我還在載思源黑體的原始 ps 檔……）
> [name=Ming-ting W]

> 思源黑體的字符很容易搬來搬去的，我找別套改看看 orz
> [name=Ming-ting W]

4.  （可能功能）U+02D9輕聲（˙）的位置在直排中偏高，可能在U+02D9後接U+3105-U+3129時，改變Glyph成扁一點的點，以接近標準位置？
> 但目前輕聲是否要標成<ruby>呀<rt>˙ㄧㄚ</rt></ruby>，即在注音符號前，還沒有定論。
> [name=Bobby]

> 當然，但無論 <rt> 怎麼標，字型照著顯示即可，標在後方的不要移到前方。
> [name=Audrey T]

> 意思是「˙ㄧㄚ」跟「ㄧㄚ˙」顯示結果會不一樣嗎？
> [name=Chen Y]

> 目前初步的结论应该是这样的，不过如果有充分的理由证明由渲染引擎重排更好的话，也可以再来讨论一下。
> [name=Xidorn Q]

5.

## 技術細節

- ruby-position: inter-character 是一種橫中直的概念，瀏覽器對於 <rt> 的內容必須視為直排處理。
    - e.g. 解釋 vmtx 所規定的直排坐標，套用 vert/vrt2/vkrn 等直排特有的 feature
- 是否需要相容於 Adobe-CNS1-x 的問題
    - 既有繁體中文OpenType字型標準是Adobe-CNS1-x，若需要相容該標準，就不能增加新glyphs。
    - 允許增加新glyphs，能得到比較多彈性：例如可準備兩組注音符號（實務上是ㄓ～ㄦ共23個），在vert/vrt2時GSUB處理，即可能用同一套GPOS敘述同時支援橫排與直排。另外可增加一個寬/高度較小的輕聲符號。
- 原始碼中輕聲必須置於前方（˙ㄉㄜ），因為置於後方難以推算要回推幾個字元。
> 這一點在www-style的討論上，有提到需不需要reorder，我認為就讓輕聲放在前方，這應該沒問題。
> [name=Bobby T]


## 實作回饋

> 請問哪一個軟體可以支援 mark 的？我現在想要測試從 Droid Sans Fallback 跟 Roboto 弄出來的字體不知道該怎麼測試。
> [name=Ming-ting W]

> [https://dl.dropboxusercontent.com/u/4582065/Bopomofo3DU.otf](https://dl.dropboxusercontent.com/u/4582065/Bopomofo3DU.otf)
> [name=Ming-ting W]

> 我改了注音測試html範本，輕聲有套用，但二到四聲似乎沒出來，我問問Unicoder目前狀況如何：
> [name=Bobby]

> [https://www.dropbox.com/s/ld2ert8tr5hprzb/bopomofo\_vert\_gpos.xhtml](https://www.dropbox.com/s/ld2ert8tr5hprzb/bopomofo_vert_gpos.xhtml)
> [name=Bobby]

> 然後Mark應該各瀏覽器都通用：
> [name=Bobby]

> [https://www.typotheque.com/articles/opentype\_features\_in\_web\_browsers_-_tests](https://www.typotheque.com/articles/opentype_features_in_web_browsers_-_tests)
> [name=Bobby]

> 回報一下目前進度，這是在 Chrome Canary 上面測試的結果：[https://www.dropbox.com/s/9eb5m63xzwlle59/Screenshot%202015-02-05%2003.21.45.png?dl=0](https://www.dropbox.com/s/9eb5m63xzwlle59/Screenshot%202015-02-05%2003.21.45.png?dl=0)
> [name=Ming-ting W]

> 目前發現 fontforge 在垂直文字「不等高」的部分處理有問題，關掉之後雖然顯示看起來比較正常，但是所有文字（包含被 mark GPOS 指令移動的調號）都會留下空白。若啟用該選項，整體的文字會被往下 shift 約一個 x-height，且 shift 的高度不等高。
> [name=Ming-ting W]

> fontforge sfd: [https://www.dropbox.com/s/a5e2xltia6kik8j/threedu-bopomofo.sfd?dl=0](https://www.dropbox.com/s/a5e2xltia6kik8j/threedu-bopomofo.sfd?dl=0)
> [name=Ming-ting W]

> OpenType (CFF): [https://www.dropbox.com/s/q9n72yycrw2tnxl/Bopomofo3DU.otf?dl=0](https://www.dropbox.com/s/q9n72yycrw2tnxl/Bopomofo3DU.otf?dl=0)
> [name=Ming-ting W]

> Richard Ishida開了個W3C i18n testing case: [http://www.w3.org/International/tests/test-incubator/bopomofo/](http://www.w3.org/International/tests/test-incubator/bopomofo/)
> [name=Bobby]


> 做了一個測試版本（Adobe-CNS1-x規格，沒有增加新字元）
> [name=But K]

> Chrome - 橫排正常，直排˙不正常 (Chrome 疑似在直排時無法演算GPOS的mark anchor)
> [name=But K]

                補上不正常的圖片（Chrome Mac 41&43）
                ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_55f16b09b6763f9069aea341c31b78b0)
> Safari 7.1.2 - 橫排、直排位置移動正常，但其實直排數值是亂湊的，Safari解釋直排GPOS mark anchor 的方式很詭異，目前的數值雖疑似能顯示，但意義不明。 (另外，Safari會有符號仍占用一個字寬的問題，無法克服˙)
> [name=But K]

                Safari 8.0.5
                ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_5a0d571455b560264ee0d87559fabaf2)
> Firefox - 似乎不支援ruby與直排....
> [name=But K]

                Firefox nightly 39
                ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_e4ccc3c7ace1aa8311b1bf2ee3fdf233)
> [https://www.dropbox.com/sh/oxumuuxx5blinc7/AABGJKRWDpAYHcfgQXtOpVbaa?dl=0](https://www.dropbox.com/sh/oxumuuxx5blinc7/AABGJKRWDpAYHcfgQXtOpVbaa?dl=0)
> [name=But K]

> 另外，放棄使用mark feature tag。改用 kern （橫排）與 vkrn（直排）。
> [name=But K]

> 因為橫排時與直排時，聲調的相對位置並不同，必須分開處理。技術上的問題，我不太可能在 mark  同一個feature裡，寫入直排、橫排兩種不同GPOS條件。
> [name=But K]

> 總之目前問題在，各瀏覽器解釋GPOS的方法還不是很正常，尤其˙在直排的情況，一團亂。
> [name=But K]

> Firefox 的话，可以试用最新的 Firefox Developer Edition 38，ruby 已经默认启用，直排也已大体可用，但需要到 about:config 里面启用 layout.css.vertical-text.enabled。预计将于 39 或 40 时默认开始启用直排。
> [name=Xidorn Q]

> 現在主要問題是各瀏覽器對GPOS的定位方式，我試試Firefox Nightly（？）。
> [name=Bobby T]

> 好，Nightly 里面直排似乎好像也已经默认启用了，我昨天好像看到了签入代码，不很确定最终进去没有。不过无论如何都可以启用那个选项来启用。
> [name=Xidorn Q]

> GPOS 除了浏览器以外，其他排版软件应该也有支持的？是否可以依据一个比较有意义的写法，然后让其他某个排版软件可以正常渲染出来？如果 Firefox 里面显示有异常的话可以去提 bug。主要是有参考的话大概也许会比较好，我不是很熟悉字体这块。
> [name=Xidorn Q]

> 我也是，所以只能請 @But K 來協助。
> [name=Bobby T]

> 另外我想如果兼容性很差的话，或许可以考虑改用 GSUB 而不是 GPOS 来处理？
> [name=Xidorn Q]

- [ ] _或许可以考虑改用 GSUB 而不是 GPOS 来处理？_
> 這要呼叫But來看看了。也看看Richard怎麼想，我在新發的信裡把Ken Lunde加了進來，聽聽他們的意見。畢竟注音的調號只確定不在ruby-position: inter-character的範圍內，我們只是在試如何處理。
> [name=Bobby T]

- [ ] 除了用在Ruby標音外，也包含行內的呈現？見R.I.的[Test Case](http://www.w3.org/International/tests/test-incubator/bopomofo/)

## Test Case


**Test Case 1:** [http://binb.tw/bopomofo/case01/](http://binb.tw/bopomofo/case01/)

- 文字：橫排
- 注音：橫排
- 嵌入字型：bpmfgpos.otf by [But Ko](https://g0v.hackpad.tw/ep/profile/EExJhZAws6k)
- 效果：透過OpenType GPOS（本案例為'kern'）調整調號位置
- 說明：這一點在呈現上，幾乎在各瀏覽器都沒有問題，也是比較確切的成果。

**Test Case 2:** [http://binb.tw/bopomofo/case02/](http://binb.tw/bopomofo/case02/)

- 文字：直排
- 注音：直排
- 嵌入字型：bpmfgpos.otf by [But Ko](https://g0v.hackpad.com/ep/profile/EExJhZAws6k)
- 效果：透過OpenType GPOS（本案例為'vkrn'）調整調號位置
- 說明：
    - Firefox請使用Nightly build並且將layout.css.vertical-text.enabled設定為True，但似乎不支援GPOS位置調整。
> 关于这一点，我询问了相关开发者，其表示由于调号字符在Unicode中的方向属性为R，根据Writing Modes标准，当text-orientation为默认的mixed时，这些字符会以sideways的方式显示，与前面注音符号的upright不同，导致textrun断开从而使GPOS失效，类似于字体fallback的情况。此处将text-orientation手动设置为upright应可解决。
> [name=Xidorn Q]

> 這倒是一語點醒夢中人。注音調號當時unification到這幾個歐文調號的位置上，常常顯示成奇怪的歐文˙造型不說，現在連直排都造成影響.....
> [name=But K]

> Firefox Nightly里直排的GPOS支持应该已经修复了，可以再测试一下
> [name=Xidorn Q]

> 另外关于调号的方向属性的问题，前一段在CSSWG上[有过一些讨论](https://lists.w3.org/Archives/Public/www-style/2015Aug/0315.html) ，Koji表示可以去Unicode的邮件列表询问是否可以将调号的方向属性修改为U
> [name=Xidorn Q]

    - Google Chrome請使用Chrome Canary，但會發生調號原位置出現空白的狀況。

**Test Case 3:** [http://binb.tw/bopomofo/case03/](http://binb.tw/bopomofo/case03/)

- 文字：橫排
- 注音：直排
- 嵌入字型：bpmfgpos.otf by [But Ko](https://g0v.hackpad.com/ep/profile/EExJhZAws6k)
- 效果：透過OpenType GPOS（本案例為'vkrn'）調整調號位置
- 說明：除Webkit Nightly外，不支援ruby-position:inter-character。


## 發行與普及

做出來再說(；´Д｀)。




