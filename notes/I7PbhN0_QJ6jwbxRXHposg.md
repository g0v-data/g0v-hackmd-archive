---
title: "給力萌典：動詞分類庫建置計劃"
tags: hackpad
---

# 給力萌典：動詞分類庫建置計劃

> [點此觀看原始內容](https://g0v.hackpad.tw/s1olVpQVFRS)


網站位址：[http://dodo.moedict.tw/](http://dodo.moedict.tw/)
使用介紹：
簡報說明：[線上簡報分享](https://www.google.com/url?q=https://docs.google.com/presentation/d/1EEWhYUmcD_bOjj_dHTwZ7Wn0mJzEUrYMI3-KnjV19iE&usd=2&usg=ALhdy2_oY8eSmmLrQIAccCcwvBQyWgHKBA)
hackath9n成果報告：[https://www.youtube.com/watch?v=FsP-IUpPZio](https://www.youtube.com/watch?v=FsP-IUpPZio)

感謝 [Audrey Tang](https://g0v.hackpad.tw/ep/profile/DaKXhWfoD7Q)提供萌典動詞字典內容，並神速建置網站，以及 [ET Blue](https://g0v.hackpad.tw/ep/profile/AzI6AT10vbD)也是神速測試與回饋。
> 大家都是神速啊可是我hackpad寫好慢，而且介面說明也還沒改 QQ
> [name=A-Han L]


歡迎大家共筆參與！！！ :smiley:
Hackpad 第1.、2. 兩大項的內容只是為了分享。如果有任何技術實作上的建議可直接跳到第3. 部分喔 :p
[https://g0v.hackpad.com/s1olVpQVFRS#:h=3.-目標與進程](https://g0v.hackpad.com/s1olVpQVFRS#:h=3.-目標與進程)


## 1\. 為什麼發起給力萌典？

基於萌典「[還文於民](https://g0v.hackpad.tw/3du.tw-ZNwaun62BP4)」的精神，我們希望萌典不僅是一本「字典」以供查詢。[萌典](https://www.moedict.tw)作為公民可共同取用的公開資訊，我們希望萌典可以發揮更大的用處，讓公民共同參與、協作。

事實上，萌典在2013年已發起[國語辭典啄木鳥](http://www.ettoday.net/news/20131124/299826.htm)活動，即是這樣的想法。透同一個平台，讓公民針對引文相同而用字卻不相同的條目，共同進行勘誤與校正。啄木鳥活動指出了萌典的內涵：「語言文字」這項資產，並非只是單向讓公民查詢使用；由於公民可以共同參與、協作，因此**全民共享的知識可以不斷地有新的內容，而不必透過學者專家的壟斷**。

### 1.1 為什麼不要求學者專家做完開放就好？


我們可以假想上述的情況，如果透過學者專家來執行，將會是什麼樣的情形？可以想見，學者專家會編列預算，找工讀生來加以編輯字典內容，並且將成果作為自己的研究發表。這麼一來，「語言文字」這樣的資產，將作為學者專家所獨佔的智慧財產權，因此學者就未必有意願開放資料內容，並且也可能將這項資產作為營利用圖。

然而，學者專家編列預算找工讀生來產出這些知識，是透過自己的資本轉換而成的嗎？並不是。事實上，學者專家的預算仍來自政府，即公民的納稅付出；而公民的資本雖然投資在學者專家的研究上，最後卻被學者專家獨佔，而不能取得新的知識內容，這是不公平也是不正義的作法。知識之所以屬於公民，乃是因為知識的來源、生產以及結果，往往都是整體社會共同付出所致。因此，除非學者專家響應學界所發起的[機構典藏](http://zh.wikipedia.org/wiki/%E6%A9%9F%E6%A7%8B%E5%85%B8%E8%97%8F)，將所有研究成果授權所屬機構「全數公開」；否則，學者專家的獨佔，即竊佔了納稅人的資本與產出。

為了避免知識獨佔的情形，我們認為：如果有好的架構和平台，可以透過公民參與、協作來完成，我們根本**不需要花費納稅人的金錢，即可讓知識內容達到更好的生產目的：校正、分類，以及更為便利的使用**。

因此，**所謂「資訊公開」並非只是「要求學者專家公開」，而是完全開放讓公民參與知識內容的生產。所以公民也不再只是「知識的使用者」，而是「知識的生產者」**。

:smiling_imp:  是的沒錯，這就是**_自己的語言自己做！！！_** :smiling_imp:

### 1.2 為什麼編輯字典內容要選擇句型？


給力萌典的開發項目，著重於當代**國語的使用內容**，因此給力萌典**不同於國語辭典中所引用的古典文獻**。傳統古典文獻有版本依據，可資考據、比對、校正與查詢，但當代國語卻是日常生活中不斷變動的內容。對於所有華人所使用的國語而言，我們應該思考一個問題：**如何讓語言學習者可以輕易地掌握該語言的結構，並說出正確、可理解的句子？**

為了讓語言學習者可以輕易地掌握語言結構，並說出正確、可理解的句子，我們就必須相信一個「好的架構」可以達到上述目標，這樣就可以把「好的架構」介紹給語言學習者。然而，整理出「好的架構」並不是一件容易的事。因為，對於國語的母語使用者來說，國語是三歲以前就會自然習得的語言，從來沒有「刻意、有意識地」透過學習而得：包括背單字、記文法，以及大練繁複、枯燥的練習。對於國語的母語使用者來說，我們其實也未必知道，什麼是國語的「好的架構」。

為了確立這項「好的架構」，語言學家[喬姆斯基](http://zh.wikipedia.org/wiki/%E8%AF%BA%E5%A7%86%C2%B7%E4%B9%94%E5%A7%86%E6%96%AF%E5%9F%BA)指出一個好的研究方法，以符合母語使用者的語言心理狀態——[內省法](http://zh.wikipedia.org/wiki/%E5%86%85%E7%9C%81%E6%B3%95)。內省法原本是一種哲學方法，但喬姆斯基於50年代在語言學領域展開[認知革命](http://www.cs.princeton.edu/~rit/geo/Miller.pdf)之後，將這方法延伸為語言分析的重要方法。其最重要的核心為：母語使用者對於自身語言有絕佳的語感，以判斷什麼是正確、可理解的句子，而什麼不是。換而言之，「好的架構」就是要透過母語使用者的判斷，來確保該架構的正確性。如果在該架構的運算過程當中，所得出的所有句子「都是母語使用者認為正確、可理解」的句子，那麼該架構就是有效的。

舉例來說，我們會知道「我喜歡看書」是一個「正確、可接受」的句子，但「書我看喜歡」則不是，而這是一個母語使用者可以立即判斷的。然而，若要透過一個好的分析以整理出架構，就必須符合科學方法中的實驗標準，也就是「排除條件」以確立實驗對象是否會產生預期的作用。在上述的例子，我們可以排除許多變因（參數），只留下一個。比如「我喜歡看書」和「我愛看書」兩個句子，變因只有「喜歡」和「愛」在同一個位置中的不同；由於這兩個句子都是「正確、可接受」的句子，因此我們知道這兩個詞可以暫且歸為同一個單位，即「動詞」。或者「我愛看書」和「我愛」兩個句子，變因只有「愛」後面的位置是否應「填入一個單位」這樣的不同；由於只有「我愛看書」是「正確、可接受」的句子，因此我們知道「愛」這個動詞，後面一定要「填入一個單位」，才符合母語使用者的語感判斷。

對於一個外語學習者來說，他就是要學母語使用者這種語感判斷；對於程式應用來說，語言翻譯或人工智慧就是要展現出這種語感判斷。因此上述的例子所指出的判斷，就是「好的架構」之所以有效的依據，也是目標。

這就是為什麼給力萌典要「選擇句型」，因為**「選擇句型」就是讓母語使用者，即從小就說國語的所有公民，依據自己的語感判斷來確立「好的架構」**。這麼一來，「好的架構」就會確保有效地應用在更多領域，包括外語學習、語言翻譯，或語言資訊處理。

### 1.3 為什麼要透過多人選擇句型？


經1.2我們會發現，**讓母語使用者判斷「正確、可理解」的句子，一反過去我們認為「字典所規範的內容才是正確的」這樣的觀點**。事實上，由於傳統字典涵蓋太多古代中文的語言內容，這些內容在現代國語的使用過程中，未必是「正確、可理解」的，也因此這些字典內容未必讓語言學習者可以迅速、有效地掌握現代國語；相反的，由於語言是不斷變遷的，我們應該要相信母語使用者的語感直覺，讓母語使用者的語感發揮最大效用，以建立便於公民使用的「好的架構」。
> 關於古代中文（古典文獻）和現代國語在「正確、可理解」的區別，可參考 [3.1.3 的 e.「欲窮千里目」的「窮」](https://g0v.hackpad.com/s1olVpQVFRS#:h=3.-目標與進程)這個例子。
> [name=A-Han L]


在學者專家的語言分析過程中，這種仰賴「母語使用者的語感判斷」過程，即仰賴學者專家自己。然而，學者專家的判斷未必符合現代國語的使用現況。如果我們在「選擇句型」的過程中，只讓學者專家來判斷，他們很可能判斷出「我在讀書」這種「在字句」是不正確的，但現代國語的日常使用中，這句子卻極其常見，並且人人都覺得「正確、可理解」。誠然，保持和社會互動良多，並且持開放心胸的學者專家，也可以理解「我在讀書」是「正確、可理解」的句子；然而，如果讓使用者一同參與判斷，透過資訊的累積與數據的呈現，來指出現代公民正在使用的、活絡的、屬於公民自身的語言事實，以建立起語言學習者容易掌握並應用的「好的架構」，這不是比學者專家的判斷更有效嗎？

## 2\. 給力萌典的操作設計

本說明搭配[線上簡報](https://www.google.com/url?q=https://docs.google.com/presentation/d/1EEWhYUmcD_bOjj_dHTwZ7Wn0mJzEUrYMI3-KnjV19iE&usd=2&usg=ALhdy2_oY8eSmmLrQIAccCcwvBQyWgHKBA)效果更好！

給力萌典希望透過「好的架構」，透過公民協作，一同編輯字典內容。主要的核心架構即為「國語[與格](https://www.google.com.tw/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0CB0QFjAA&url=http%3A%2F%2Fzh.wikipedia.org%2Fzh-tw%2F%25E4%25B8%258E%25E6%25A0%25BC&ei=H4WpU4SeCcvRkQXV4IHYDQ&usg=AFQjCNGVTEmMFKQWjWQY_sLBF5otNqmMsw&sig2=_3oBjbz5oVhPdDOtSvuLSA)轉換」：
**A**我送一本書給你←→**B**我送你一本書
**A**我寫一封信給他←→**B**我寫他一封信
**A**小張提供吃穿給弟弟←→**B**小張提供弟弟吃穿

上述轉換可得知兩種句型的必要條件：
1\. 動詞為及物動詞
2\. 動詞在整個句子裡，一共合併了三個名詞：1個主詞和2個受詞

在這個「國語[與格](https://www.google.com.tw/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0CB0QFjAA&url=http%3A%2F%2Fzh.wikipedia.org%2Fzh-tw%2F%25E4%25B8%258E%25E6%25A0%25BC&ei=H4WpU4SeCcvRkQXV4IHYDQ&usg=AFQjCNGVTEmMFKQWjWQY_sLBF5otNqmMsw&sig2=_3oBjbz5oVhPdDOtSvuLSA)轉換」的架構下，有許多句子不能這樣轉換，這是因為**動詞類別不同**的緣故：
**A**我丟一顆球給他 **≠ B**我丟他一顆球
**A**我拿十塊錢給他 **≠ B**我拿他十塊錢
**A**我通知這個消息給他 **≠ B**我通知他這個消息
**A**媽媽限兩小時給他打掃房間 **≠ B**媽媽限他兩小時打掃房間
**A**葉問打十拳給他 **≠ B**葉問打他十拳

以上，只要讓國語的母語使用者（公民）一起來選擇「**A句或Ｂ句，是不是正確、可理解的句子」**，就可以建立「給力」的「好的架構」。

本項架構為語言學家[Ray Jackendoff](http://en.wikipedia.org/wiki/Ray_Jackendoff)所建置的模型，該研究主張人類的語言結構是基於大腦長年演化的認知結構而產生。上述「[與格](https://www.google.com.tw/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0CB0QFjAA&url=http%3A%2F%2Fzh.wikipedia.org%2Fzh-tw%2F%25E4%25B8%258E%25E6%25A0%25BC&ei=H4WpU4SeCcvRkQXV4IHYDQ&usg=AFQjCNGVTEmMFKQWjWQY_sLBF5otNqmMsw&sig2=_3oBjbz5oVhPdDOtSvuLSA)轉換」所呈現的A句與B句，即該模型的「時空的轉換」與「本質的改變」兩個認知面向。A句「時空的轉換」呈現「致使一個受詞在時間或空間上移動到另一個受詞」，B句「本質的改變」呈現「致使一個受詞在本質上改變而擁有另一個受詞」。

由於人類大腦長年演化的認知結構，是所有人類都具備的。因此我們可以理解所有人類語言都具備「[與格](https://www.google.com.tw/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0CB0QFjAA&url=http%3A%2F%2Fzh.wikipedia.org%2Fzh-tw%2F%25E4%25B8%258E%25E6%25A0%25BC&ei=H4WpU4SeCcvRkQXV4IHYDQ&usg=AFQjCNGVTEmMFKQWjWQY_sLBF5otNqmMsw&sig2=_3oBjbz5oVhPdDOtSvuLSA)轉換」的上述架構。[**線上簡報**](https://www.google.com/url?q=https://docs.google.com/presentation/d/1EEWhYUmcD_bOjj_dHTwZ7Wn0mJzEUrYMI3-KnjV19iE&usd=2&usg=ALhdy2_oY8eSmmLrQIAccCcwvBQyWgHKBA)**可見中文和英文都可以用同樣的架構來理解，因此這項架構必然可以讓外語學習者更容易以自己的語言來掌握**，也容易應用在語言翻譯與語言資訊處理上。

因此根據「[與格](https://www.google.com.tw/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0CB0QFjAA&url=http%3A%2F%2Fzh.wikipedia.org%2Fzh-tw%2F%25E4%25B8%258E%25E6%25A0%25BC&ei=H4WpU4SeCcvRkQXV4IHYDQ&usg=AFQjCNGVTEmMFKQWjWQY_sLBF5otNqmMsw&sig2=_3oBjbz5oVhPdDOtSvuLSA)轉換」架構，及物動詞是否滿足架構中的兩個面向，則產生2x4=4種結果。因此透過公民協作「選擇句型」，我們可以分出「[與格](https://www.google.com.tw/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0CB0QFjAA&url=http%3A%2F%2Fzh.wikipedia.org%2Fzh-tw%2F%25E4%25B8%258E%25E6%25A0%25BC&ei=H4WpU4SeCcvRkQXV4IHYDQ&usg=AFQjCNGVTEmMFKQWjWQY_sLBF5otNqmMsw&sig2=_3oBjbz5oVhPdDOtSvuLSA)轉換」的四類動詞。
★架構圖詳見[線上簡報](https://www.google.com/url?q=https://docs.google.com/presentation/d/1EEWhYUmcD_bOjj_dHTwZ7Wn0mJzEUrYMI3-KnjV19iE&usd=2&usg=ALhdy2_oY8eSmmLrQIAccCcwvBQyWgHKBA) pp.16

## 3\. 目標與進程


### 3.1 20140622 hackath9n

本階段為[**給力萌典BETA**](http://dodo.moedict.tw/)，篩選出2300筆動詞作為第一階段「初校」。
成果報告：[https://www.youtube.com/watch?v=FsP-IUpPZio](https://www.youtube.com/watch?v=FsP-IUpPZio)

#### 3.1.1 網站建置

感謝 [Audrey Tang](https://g0v.hackpad.tw/ep/profile/DaKXhWfoD7Q)在hackath9n不到兩小時，就依照「[與格](https://www.google.com.tw/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0CB0QFjAA&url=http%3A%2F%2Fzh.wikipedia.org%2Fzh-tw%2F%25E4%25B8%258E%25E6%25A0%25BC&ei=H4WpU4SeCcvRkQXV4IHYDQ&usg=AFQjCNGVTEmMFKQWjWQY_sLBF5otNqmMsw&sig2=_3oBjbz5oVhPdDOtSvuLSA)轉換」架構，建置好[網站](http://dodo.moedict.tw/)了！！！！！
我們由萌典選出動詞，透過網站讓使用者「選擇句型」，以判斷該動詞屬於「[與格](https://www.google.com.tw/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0CB0QFjAA&url=http%3A%2F%2Fzh.wikipedia.org%2Fzh-tw%2F%25E4%25B8%258E%25E6%25A0%25BC&ei=H4WpU4SeCcvRkQXV4IHYDQ&usg=AFQjCNGVTEmMFKQWjWQY_sLBF5otNqmMsw&sig2=_3oBjbz5oVhPdDOtSvuLSA)轉換」架構裡，四類動詞中的其中哪一類。

20140625網站介面修改：
1（按鈕顏色黃）「（句子）」（搜尋扭）
2（按鈕顏色藍）「（句子）」（搜尋扭）
3（按鈕顏色綠）兩個都可以填入同一個名詞，而且意思都一樣。
3（按鈕顏色綠）兩個都可以填入同一個名詞，但是意思不一樣。
4（按鈕顏色紅）兩個都不可以填入名詞，因為這個動詞本來就不能接一個受詞。
4（按鈕顏色紅）兩個都不可以填入名詞，因為這個動詞不是現代國語的動詞。
無法判斷（按鈕刪除）

#### 3.1.2 第一階段動詞篩選標準

**a.** 單音節動詞
    e.g. 「放置」屬於雙音節動詞，暫且不作為第一階段動詞分類庫的目標。
**b.** 排除破音詞
**c.** 篩選出「主要義項為動詞」的條目。
    e.g. 條目「打」顯然為動詞，但同一條目另一義項「一打筆」為名詞。假若我們完全排除多個義項的條目（多義詞），則剩下來的動詞全為冷僻的古代中文動詞。因此 [Audrey Tang](https://g0v.hackpad.tw/ep/profile/DaKXhWfoD7Q)另寫程式以演算「該條目具動詞性質」的積分，積分顯示為一定標準以上者，列入給力萌典BETA的測試。

#### 3.1.3 可預知的情況

**a.** 為避免不同義項可能橫跨不同詞類，會產生誤會。因此在網頁上列出詞義與舉例。
    e.g. 「花」有名詞「紅花」與動詞「花錢」兩個義項，如果只看到「花」，使用者會容易想到名詞。因此要把詞義和舉例放在頁面上。

**b.** 目前2300筆動詞是以程式演算「該條目具動詞性質」的積分而得出，因此「**並非所有的條目都是動詞**」。
    e.g. 測試時有遇到這例子。_「畢」：古代打獵用的網，有長柄。_

**c.** 與a.相同的情形，就算同一條目多個義項，也未必橫跨不同詞類，但不同義項還是要區分。因此使用者須**依照網頁上所指出的「詞義與舉例」來選按**。
    e.g.「呼」這動詞，在現代國語會想到「呼巴掌」，同時也有另一義項「呼氣」。這兩個義項顯然在「[與格](https://www.google.com.tw/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0CB0QFjAA&url=http%3A%2F%2Fzh.wikipedia.org%2Fzh-tw%2F%25E4%25B8%258E%25E6%25A0%25BC&ei=H4WpU4SeCcvRkQXV4IHYDQ&usg=AFQjCNGVTEmMFKQWjWQY_sLBF5otNqmMsw&sig2=_3oBjbz5oVhPdDOtSvuLSA)轉換」架構下，是不同類別的動詞。「呼巴掌」不能說「我呼一巴掌給你」，但可以說「我呼你一巴掌；「呼氣」則兩種句型都不能說。類似這種情況，「呼」這動詞的類別，使用者還是要仔細看網頁上所指出的「詞義與舉例」。

**d.** 有些動詞在「[與格](https://www.google.com.tw/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0CB0QFjAA&url=http%3A%2F%2Fzh.wikipedia.org%2Fzh-tw%2F%25E4%25B8%258E%25E6%25A0%25BC&ei=H4WpU4SeCcvRkQXV4IHYDQ&usg=AFQjCNGVTEmMFKQWjWQY_sLBF5otNqmMsw&sig2=_3oBjbz5oVhPdDOtSvuLSA)轉換」架構下，兩種句子都是正確、可接受的，但不一定屬於[動詞A](https://docs.google.com/presentation/d/1EEWhYUmcD_bOjj_dHTwZ7Wn0mJzEUrYMI3-KnjV19iE)。這類動詞在選項「兩個句子都可以填入『同一個名詞』」還要再加區分。
    e.g. 動詞「拿」即屬此例。「我拿十塊錢給你」和「我拿你十塊錢」兩個句子都是正確、可接受的，但意思完全不同。因此不能屬於[動詞A](https://docs.google.com/presentation/d/1EEWhYUmcD_bOjj_dHTwZ7Wn0mJzEUrYMI3-KnjV19iE)。

**e.** 有許多古代中文的動詞，現代國語已經不會用了。這種情況在選項「兩個都不可以填入名詞」還需要再加區分。
    e.g.比如動詞「站」為非及物動詞，所以「我站一＿＿給你」和「我站你＿＿」都無法填入任何名詞；然而，動詞「羅」也是兩個句子都不是正確、可理解的，但原因卻不相同。動詞「羅」有「羅列」的意思，古代中文可以理解這樣的意思，但現代國語不行。因此[動詞D](https://docs.google.com/presentation/d/1EEWhYUmcD_bOjj_dHTwZ7Wn0mJzEUrYMI3-KnjV19iE)選項「兩個都不可以填入名詞」還要區分出「這是現代國語的動詞」，或者不是。
            ★★關於這一點感謝 [ET Blue](https://g0v.hackpad.tw/ep/profile/AzI6AT10vbD)的測試與回饋。事實上，就連現代國語在特殊情況下，也會使用像「羅」這樣的動詞，這是可以理解的。以下再舉另一個例子。
            比如我們容易知道「窮」是「貧窮」的意思，但其實我們也可以知道「窮」有動詞「窮盡」的意思，並且在古代中文這是及物動詞，比如「欲窮千里目」。如果我們想到了這樣的意思，那麼中文系看到漂亮的美景，可能會說「我好想窮千里啊」，那麼在這種情境下是可以理解的。
            然而，給力萌典之所以講求「母語人士使用現代國語的語感判斷」，是希望這樣的判斷可以應用在外語學習或其他應用領域。比如一個外語學習者在生活當中說「這風景好漂亮喔，我們來『窮』一下！」那麼很可能國語使用者都無法聽懂他的意思。在這樣的情況下，為了讓外語學習者可以簡單、輕易地掌握國語，並且避免他們說出錯誤的句子，我們就必須把「窮盡」這個義項，在兩個都不可以填入名詞」的選項裡選擇「這不是現代國語的動詞」。

#### 3.1.4 下一階段想解決的問題

**a.** 多義詞的問題雖然已經解決，但有些多義詞中的義項，僅限於特殊結構。比如「打」有「打字（書寫）」的意思，可以說「我打一個文件給你」，但是現在國語「[動賓](http://zh.wikipedia.org/wiki/%E8%BF%B0%E8%B3%93%E7%9F%AD%E8%AA%9E)」結構中，受詞會和動詞有緊密的結合，比如「打電話」，這種情況雖然在動詞類別上會和「打字（書寫）」相同，但意義不同。這樣的例子尚有待區分。

**b.** 有許多「[動賓](http://zh.wikipedia.org/wiki/%E8%BF%B0%E8%B3%93%E7%9F%AD%E8%AA%9E)」結構，也是基於結構本身過於穩定的緣故，不容易在分類中獲得。比如動詞「吃」應屬於[動詞D](https://docs.google.com/presentation/d/1EEWhYUmcD_bOjj_dHTwZ7Wn0mJzEUrYMI3-KnjV19iE)，但「吃豆腐」卻是極其特殊的[動賓](http://zh.wikipedia.org/wiki/%E8%BF%B0%E8%B3%93%E7%9F%AD%E8%AA%9E)結構，也屬於相同義項「口中咀嚼食物後嚥下」，卻是「佔便宜」的隱喻。因此雖然「吃」是[動詞D](https://docs.google.com/presentation/d/1EEWhYUmcD_bOjj_dHTwZ7Wn0mJzEUrYMI3-KnjV19iE)，但我們卻可以說「豬哥亮吃林志玲豆腐」，卻又不能說「豬哥亮吃林志玲三塊豆腐」。這樣的區分如何展開，還有待解決。

**c.** 動詞分類後，除了編輯字典內容外，進一步的知識內容有待第二階段分析。比如同一筆資料，如果僅有一人判斷，則未必準確；或可固定一筆資料十人判斷，再觀察數據。

**d.** 自hackath9n當天測試後，就發現選項的分類和說明頁面如果不完善，就容易誤導使用者，也容易讓使用者選錯，這會得出動詞分類的結果未必準確。目前BETA先以建立完善架構為目標，至於好的字典內容可尚待下一階段完成。



