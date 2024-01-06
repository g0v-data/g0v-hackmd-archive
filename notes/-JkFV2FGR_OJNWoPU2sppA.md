---
title: "翻吧，台灣！"
tags: 翻譯共筆,g0v.us,hackpad
---

# 翻吧，台灣！

> [點此觀看原始內容](https://g0v.hackpad.tw/M6aHMLt3fn8)

「翻吧，台灣！」是一個協力翻譯平台，提供需要與國際媒體發聲的社會議題、介紹台灣的中文影片、反映輿論的文章...一個簡易工作介面。我們的目標是建立一個介面活潑的多人共同協作的翻譯介面，能召喚全球鄉民24小時無時差的持續工作，讓重要的資訊在最短的時間內可以轉換成其他語言。

「翻吧，台灣！」是一個開放協作平台，歡迎任何人協助修改！:)

## Mockup

### 頁面一：首頁

首頁，列出現有翻譯專案讓網友選擇。同時有「上傳專案」按鈕，以及一個「About」介紹這個網站，以及未完成的功能和願景。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_246dd74603487b3b3fffcd178fe126ed)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_39989baa37c34a69c46ffd2d8cafc04d)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_cbb64cae74a9d43deeb4409d1572738a)


### 頁面二：新增 Project


1.  案件標題，案件簡介（100字以內, TBD）
2.  直接貼上文字。
3.  上傳文字檔
4.  設定公開翻譯或是私人（只有知道連結的有編輯權）、方邊需要特殊需求的翻譯使用
5.  可以寫email邀請人參與翻譯project，（公開私人皆可，但私人的一定需要寫上email才會拿到project的網頁link）
6.  （未定）可以選擇ICON，或是上傳代表照片，作為首頁的圖示。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_1b0114602dd4f1cae634380e1bb49de9)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_2f02da971a07baea052bb7da4b25cd61)




### 頁面三：翻吧！

1.  頁面最上方，是「案件標題」，和「案件說明」
2.  完成度顯示區，完成度最少需要兩條bar，最多有四條bar，一條是「完成」，一條是「校稿」（也可以是三條，分別是一/二/三校稿）
3.  翻譯頁面切分成左右兩欄，左邊為原文，右邊為待翻譯的文字區。只有正在翻譯的段落會正常亮度，其他區域都會暗掉。
4.  翻譯文字區，可以加註腳。
5.  在翻譯文字欄位區旁邊，有至少兩個check方塊，一個是「完成」，另外一個是「校稿」（也可以是三個，分別是一/二/三校）
6.  下方是關鍵字字典，文章中經常重複的關鍵字必需要能列表對照。同時在大家的翻譯中蒐集關鍵字翻譯，集合成詞彙表。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d3ba1619b7806d1fcbed0025faf3163d)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_4908a5a9c5eb1793de33806c53a5543a)


## Alpha 0.1

在「g0v 東岸零時起義黑客松」展示
- prototype: [http://chihaoyo.net/fanba](http://chihaoyo.net/fanba)
- github repo: [https://github.com/chihaoyo/fanba](https://github.com/chihaoyo/fanba)

## TODO

試驗用 source text：台灣吧影片字幕
> 有人要跟台灣吧連絡看看嗎?  還是這是我的坑?  XD
> [name=Chiohh C]

> 我發現ipad版的hackpad不好用...我在想我們先把平台弄起來再開始聯絡台灣吧，讓第一印象好一點～
> [name=Jiàn-gēng C]

> Agreed. Hackpad app is shit (now). Mobile Web 版的好像還 OK
> [name=chihao y]

> ~我知道是誰，可以去問一問。~算了還是正式詢問較好。
> [name=Yau-Hsien H]

> 台灣吧出第二集ler~ :D
> [name=chihao y]

> 對耶...我們要來翻翻看了嗎?  XD
> [name=Chiohh C]

> 呼叫戰友~~~~~
> [name=Chiohh C]

> iPa說要我們翻一下"大腸花"耶~~~~
> [name=Chiohh C]



## Tech & datastructure

以 Firebase! (acquired by Google...) 為資料庫。
- fanba
    - projects
        - \[project-id\]
            - title
            - description
            - langs: e.g. **zh-tw,en,jp** (first is the lang of the original text)
            - paragraphs
                - \[paragraph-id\]
                    - translations
                        - \[translation-id\]
                            - lang
                            - locked
                            - original
                            - text
                            - timestamp

## API (todo)

Link to translation of any pagraphs in any project with GET requests
[http://fanba.tw/](http://fanba.tw/)\[project-id\]/\[paragraph-id\]/\[lang\]

## Contributors (add yourself!)

[Jiàn-gēng Chiōu](https://g0v.hackpad.tw/ep/profile/G3fpegpCDhx)
[chihao yo](https://g0v.hackpad.tw/ep/profile/yiSmCALal9z)
[Ayo Yunyu Shih](https://g0v.hackpad.tw/ep/profile/mGuNRTHIhgR)
[Chiohh Caroline](https://g0v.hackpad.tw/ep/profile/o4gCbACYKI7)

## 現有相關專案

### 字典類

各領域專用語快速瀏覽 [https://g0v.hackpad.com/CPpKKRhPkWs](https://g0v.hackpad.com/CPpKKRhPkWs)
g0v summit 口譯詞彙表 [g0v Summit 口譯 Glossary](https://g0v.hackpad.com/vjbMYVgK9gZ)
常用專業英文  [https://g0v.hackpad.com/tuMXUE9NCxX](https://g0v.hackpad.com/tuMXUE9NCxX)

### 翻譯類

- 【公平翻譯交易所】
    - [http://www.twaprf.org/aprfssee/se/proposal/178](http://www.twaprf.org/aprfssee/se/proposal/178)
    - **長程目標（3年﹣5年）：**建立台灣本地的「公共服務翻譯」（Public Service Interpreting）制度及語料庫，使翻譯人才得以在醫院、警局、法庭、教育機構提供語言服務，幫助外籍人士及新住民與本地社會融合，打造穩固社會結構的基礎。
- Translate4you 一鍵多語翻譯器
    - github: [https://github.com/g0v/Translate4you](https://github.com/g0v/Translate4you)
    - hackpad：[https://g0v.hackpad.com/j5b4i4DdTbX](https://g0v.hackpad.com/j5b4i4DdTbX)
    - 提案簡報：[https://goo.gl/YIY1hh](https://goo.gl/YIY1hh)
    - FB：[https://www.facebook.com/Translate4you-109297822764810/](https://www.facebook.com/Translate4you-109297822764810/)

## Archive

### 11/22前封存討論


目標與功能
預定功能
1.  篩選網路媒體文章，將能呈現台灣輿論風向的代表性文章（社論、網路瘋傳文章...）挑出，由網友 submit request， VoF 系統自動 cache 圖文之後進入協作翻譯階段。
2.  每一篇文章進入系統後，自動產生下列步驟：
    1.  確立關鍵詞翻譯
    2.  拆成小段落翻譯
    3.  一校
    4.  二校
    5.  專業校稿
    6.  每篇文章顯示網友翻譯熱門程度。
    以上步驟在 VoF 協作平台上進行，讓網友可以簡單快速加入共同翻譯的行列。
> 我在思考把它做成像小遊戲的平台會不會比較吸引人XDDD
> [name=Jiàn-gēng C]

> Me too LOL
> [name=chihao y]

> XDDDD
> [name=Jiàn-gēng C]

> 成就系統？貢獻點數？
> [name=chihao y]

> 這邊簡介就好，細節的部份寫在下面，我分成你說的平台，內容、宣傳了
> [name=Jiàn-gēng C]

> 感謝。
> [name=chihao y]

3.  建立有效對外宣傳管道（？）
> 這個不錯！！
> [name=Yuan C]

> 不只是國外智庫學者，而是讓任何外國人更關心台灣的現況 :)
> [name=chihao y]

> 可以想一下翻譯哪些文章，用什麼形式刊登會最有效益～我們不可能什麼都翻
> [name=Jiàn-gēng C]

> 會不會像是太陽花學運團隊內部的外電組，把即時資訊翻譯成各國語言再加以發佈？我也同意需要斟酌一下要翻譯哪些類型的文章。
> [name=Bo-Yi L]

> 可以先列一些想翻譯的，就可以開始有輪廓了 @@ 
> [name=ipa c]

> 對，也要請教對台美關係熟的學者、組織，哪類的文章比較有價值，會發揮什麼潛在影響力，知道觀眾在哪裡，翻譯者翻起來可能會比較有勁。
> [name=Tzu-Yao L]

> 我的意思是：不只是要給國外學者看，而是要把觀眾設定成任何外國人。更多人知道台灣的現況就對我們越有利，不只要有學者專家客觀的論述，也要靠公民的覺知來宣傳台灣。如果我們能建立一個容易使用的平台，讓更多人加入共同翻譯，那能翻譯的文章數目就多。如果把要翻譯的文本切成段落，讓人能快速翻完一小段？像之前 OCR 一樣 divide and conquer。
> [name=chihao y]

> 同意！！就是想做把坑挖小，切割成小段落crowd translate的專案！！不過找目標群眾就是一個問題了，我們願意翻，但更重要的是要有人來看。每個人想看、覺得有用的東西不一樣，一個媒體剛起步，應該要有鎖定的觀眾群。目前覺得能發會最大效益的應該是能影響台美政策的政策制定者、智庫等單位。所以才會想說先鎖定這群人。
> [name=Tzu-Yao L]

> 了解。我自己也常在翻譯中英各種短文，不過都沒什麼人看！要有人看的確是一大課題。對於觀眾，我建議加入國外（不限於美國）的 political/activist group，民間團體的串連也很重要！
> [name=chihao y]

> 我最近在想這件事情：其實寫台灣的文章不是沒有，很多網站有關於台灣的英文文章，像Ketagalanmedia之類的網站。但是做台灣政治的「專家」多數還是cite 聯合報和旺中，更不用說一般人，根本沒有訊息管道，原因是因為Ketagalanmedia還沒有建立起公信力，而他們cite中時、聯合已經cite了幾十年。所以其實不是沒有資訊來源，是沒有建立觀眾群的慣性。我覺得要翻譯就要翻有公信力的東西。我有點想要翻蘋果、自由，甚至聯合的社論的專欄文章，然後拿去投國外的媒體。原因是1. 台灣市佔率最高的三大報紙，有代表性。2. 拿去投國外媒體，曝光度比放在自己的網站高。3. 像蘋論很多文章是從沃草之類的網路媒體來的，可以利用蘋果名聲建立網路評論對外發聲的空間。不知道大家覺得怎樣～
> [name=Jiàn-gēng C]

> 我覺得也許可以分成 1\. 平台 2. 內容 3. 宣傳 來討論？第一點可以討論協作翻譯的機制（切割翻譯、共同審議？），第二點可以討論要找那些內容來翻譯以及怎麼找（洽談、授權？），第三點可以討論我們目標的觀眾以及怎麼吸引他們來閱讀。
> [name=chihao y]

> 嗯嗯～我覺得我們應該要開一個新頁面了～
> [name=Jiàn-gēng C]

> 應該就是 "Voice of Formosa"？[Voice of Formosa](https://g0v.hackpad.com/M6aHMLt3fn8)
> [name=chihao y]

> 對啊，我正在打，幫我！
> [name=Jiàn-gēng C]

> 有一些朋友/網友長期在CNN iReport上面做這件事，也許可以去把他們挖來。
> [name=Miia C]

> 有沒有可能, 一開始像[Jiàn-gēng Chiōu](https://g0v.hackpad.com/ep/profile/G3fpegpCDhx)說的翻三大報紙,然後我們有個自己的CNN iReport帳號/頁面,把翻好的文章PO上去?  而且其實CNN iReport有提供讀者comment&評論，(this belongs on CNN, Close but need some work, this is inappropriate)  或許也可以幫助曝光率?  不顧有些新聞算是有時效性的，就必須要考慮的時間問題。
> [name=Chiohh C]

> 感覺要是有大事發生CNN有在關注時這個會很好用～！
> [name=Jiàn-gēng C]

> 其實這幾天有些台灣選舉後的分析文就可以翻翻看了說~  
> [name=Chiohh C]

翻吧，台灣！
正式對外名稱：福爾摩沙之聲  Voice of Formosa
> 代號 VoF 可以嗎 XD
> [name=chihao y]

> 我覺得給網友協作的平台名字和拿去對外推銷的名字應該要差很多，這是推銷用的XD感覺在Hackpad上面應該要放協作用的名字。福爾摩沙之聲不夠白痴，應該要用「翻吧，台灣！」之類的XDDD
> [name=Jiàn-gēng C]

> 翻吧台灣——完美。
> [name=chihao y]

> 喜歡翻吧，台灣XD年輕族群貌似不能用太正常的名字...引不起注意。
> [name=Winnie K]

> 同意。也許這樣也沒什麼不好？（說服自己）
> [name=chihao y]

> 今天那個長輩也很愛阿~~~  XDDD
> [name=Chiohh C]

來自臺灣底層微弱而堅定的聲音

專案簡介
專案說明
希望能打破少數媒體壟斷台灣對外的發聲管道，讓國際媒體及政治學者、智庫能真正了解近年來快速變遷的台灣輿論風向，並藉此讓台灣人民的意志發揮影響力

要解決的問題
為什麼國際輿論還是普遍以為服貿只是反對自由貿易、或只是害怕中國
_其實寫台灣的文章不是沒有，很多網站有關於台灣的英文文章，像_[Ketagalanmedia](http://www.ketagalanmedia.com/)_之類的網站。但是做台灣政治的「專家」多數還是cite 聯合報和旺中，更不用說一般人，根本沒有訊息管道，原因是因為Ketagalanmedia還沒有建立起公信力，而他們cite中時、聯合已經cite了幾十年，所以台灣的輿論就被旺中和聯合代表了。其實不是沒有資訊來源，是沒有建立觀眾群的慣性。_

那麼觀眾群是誰？
_每個人想看、覺得有用的東西不一樣，一個媒體剛起步，應該要有鎖定的觀眾群。目前覺得能發會最大效益的應該是能影響台美政策的政策制定者、智庫等單位。所以才會想說先鎖定這群人。_
_對於觀眾，我建議加入國外（不限於美國）的 political/activist group，民間團體的串連也很重要！_

建立篩選機制
_方案一：我有點想要翻蘋果、自由，甚至聯合的社論的專欄文章，原因是 1\. 台灣市佔率最高的三大報紙，有代表性。2. 像蘋論很多文章是從沃草之類的網路媒體來的，可以利用蘋果名聲建立網路評論對外發聲的空間。_

建立協作平台:翻吧，台灣！
_如果我們能建立一個容易使用的平台，讓更多人加入共同翻譯，那能翻譯的文章數目就多。如果把要翻譯的文本切成段落，讓人能快速翻完一小段？像之前 OCR 一樣 divide and conquer。_
前端：類似割闌尾V計畫網頁，做成有趣活潑的介面，讓民眾進去可以點選自己的英文能力/專業能力，並依此選擇任務：我要幫忙查字典、我要翻一段、我要翻整篇、讓專業的來！

後端：
1\. 確立關鍵字詞翻譯
2\. 切成段落：一段一份、兩段一份...
3\. 一校
4\. 二校
5\. 專業校稿

福爾摩沙之聲
_找目標群眾就是一個問題了，我們願意翻，但更重要的是要有人來看。_
給英文使用者的國際平台，顯示每篇社論在台灣的出處、點閱率、作者相關訊息、寫信給作者的e-mail link，讓外媒可以方便採訪
- CNN iReport

成果展示（規劃文件、雛形/草稿、原型/初稿、正式發佈/完稿）

