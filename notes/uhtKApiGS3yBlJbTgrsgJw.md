---
title: "iThome Open Source 專題採訪"
tags: 採訪共筆,hackpad
---

# iThome Open Source 專題採訪

> [點此觀看原始內容](https://g0v.hackpad.tw/7Ev6ApUzYtA)

本文授權為 CC BY 4.0 [https://g0v.hackpad.com/7Ev6ApUzYtA](https://g0v.hackpad.com/7Ev6ApUzYtA)

刊登於iThome電腦報695期封面故事：開源吃掉全世界
【開源在臺灣】國際開源社群領導者唐鳳：[開源是新時代交換典範](http://www.ithome.com.tw/news/93603)

共筆人：唐鳳、李建興（記者）
與會人：王宏仁（主編）、胡瑋佳（記者）

## 可以跟我們介紹一下自己嗎？過去的經歷、背景，而又是什麼機緣下，進入開源圈呢？

我這二十年來都在做 Web 相關的工作，簡歷可以參考 [LinkedIn 頁面](http://www.linkedin.com/in/tangaudrey)。

初次接觸開源是在 1993 年左右，接觸到 Peter Deutsch 等人開發的 [Archie](http://scholar.google.com/scholar?cluster=9587128569624948312&hl=zh-TW&as_sdt=0,5&as_vis=1) 檢索系統，以及 1994 年 Annihilator 等人開發的 [ES LPMud](https://zh.wikipedia.org/zh-hant/MUD#.E5.98.97.E8.A9.A6.E5.89.B5.E4.BD.9C.E9.9A.8E.E6.AE.B5.EF.BC.881993-1994.EF.BC.89) 系統。之後短暫參與 [Gopher](http://www.scn.org/~bkarger/gopher-manifesto) 超文本社群，但因開發團隊（明尼  蘇達大學）要求收取權利金，所以轉向 Tim Berners-Lee 新提出的 Web 架構，並參與相關的 Usenet 與 Perl CPAN 社群，之後一直持續到今天。

### 那您為什麼會想一直參與開源社群呢？


其實當年還沒有開源的概念（這個詞出現在 [1998 年](http://opensource.org/history)），但已有作為其基礎的[黑客文化](https://en.wikipedia.org/wiki/Hacker_%28programmer_subculture%29)與[自由軟體運動](https://www.fsf.org/about)。

當時因為自己對計算語言、人工智慧和網絡社會很有興趣，發現許多的工作者都在線上，相關的工具也往往都是開放的，所以會覺得作品跟大家分享是自然的事情，比較像一種生活方式。

### 20年是一段很長的時間，你的什麼想法讓您在這圈子待這麼久？


開放的作品能觸及到的人通常較多，而開源模式更是讓願意接力工作的人可以持續下去。
我想這是主要的想法：**開站是一時的，開源是一輩子的。**

### 一開始與現在的想法有什麼改變嗎？


想法沒有改變，只是隨著網絡社會的普及，分享變得更容易了，也有更多人願意參與。

### 參與開源社群的這段時間有遇過什麼困難或是情緒難以接受的事，而萌生退出的念頭過嗎？


2006 年在巴西參加 [CONISLI 年會](http://www.slideshare.net/autang/ofun-optimizing-for-fun)時，因為對實作方式的取向不同，而從 Perl 6 社群退出，轉向為開發 Haskell 語言。當時主要是想避免自己成為社群的瓶頸，現在看來是正確的決定，今年也將是 [Perl 6](https://fosdem.org/2015/interviews/2015-larry-wall/) 和 [Haskell](https://www.fpcomplete.com/blog/2015/01/announcing-lts-haskell-1-0) 雙雙邁向主流應用的一年。

## 這一兩年臺灣Open Source社群活動開始興盛，您認為原因是什麼？


我想主流的開發平台（包括 Oracle Java 及 Microsoft .NET Core）全部開源化之後，軟體開發社群與開源模式之間已經高度重疊，幾乎沒有差別了。行動裝置系統更是以 Linux 與 BSD 為大宗，多年前的專屬式授權系統也較為少見。

加上 GitHub 等社群網站的興起，我想以開源方式做系統，這兩年來已經為大部份資訊工作者所接受。

### GitHub在開源社群中扮演什麼樣的角色，有哪些因素使GitHub成為開源的匯集地？


    GitHub 首先是藉由易用的 Web 界面，普及了 Git 的分散治理模式，幾乎完全取代了以 Subversion 為代表的集中模式。其中的差異，可以參考這篇[以香港佔領運動為背景的文章](http://www.vjmedia.com.hk/articles/2014/11/03/89747) 。

此外，GitHub 將源碼、修訂、瑕疵回報等開發過程的產物定址成[鍵連資料](https://en.wikipedia.org/wiki/Linked_data)，進而將它們轉化成[社會物件](http://www.zengestrom.com/blog/2005/04/why-some-social-network-services-work-and-others-dont-or-the-case-for-object-centered-sociality.html)，因此取得了類似新興社群媒體的[網絡效應](https://zh.wikipedia.org/zh-hant/網絡效應)，使 [Google Go](http://www.infoq.com/news/2014/11/golang-goes-git-github) 和 [Microsoft .NET](http://blogs.msdn.com/b/vbteam/archive/2015/01/10/we-re-moving-to-github.aspx) 團隊都放棄了自家的源碼平台，移轉到 GitHub 上開發，以爭取社群支援。

## 臺灣Open Source過去跟現在有什麼不一樣？


之前主要由軟體工作者參與，但隨著[創用 CC](http://creativecommons.org.tw/explore)、[自造文化](https://en.wikipedia.org/wiki/Maker_culture)的開展，現在文字、硬體、音樂、影像、設計、教育、政治工作者，也都開始參與開放文化，Source 的範圍愈來愈廣闊了。

### 可以給我們一些有趣的例子說明開源範疇的擴大，不僅只限於軟體開發上？


文字如 [Wikimedia](https://commons.wikimedia.org/wiki/Main_Page)，硬體如 [Arduino](http://www.arduino.cc/) / [Thingiverse](https://creativecommons.org/tag/thingiverse)，音樂如 [Blend](https://blend.io/) / [SoundCloud](http://help.soundcloud.com/customer/portal/articles/243852)，影像如 [YouTube](https://support.google.com/youtube/answer/2797468) / [Flickr](https://www.flickr.com/creativecommons/)，設計如 [Behance](https://www.behance.net/search?user_tags=1240221)，教育如 [Khan Academy](https://www.khanacademy.org/) / [OCW](https://ocw.mit.edu)，科學如 [arXiv](http://arxiv.org/)，政治如 [g0v](http://summit.g0v.tw/zh-TW/speaker.html) 等。

## 國際跟臺灣Open Source社群有無差異？


除了使用的語言之外，並沒有顯著差異。早年比較需要做翻譯工作來連絡社群，但現在自動翻譯進步，參與者的英文大致都沒有問題，因此國際連結的動能也很強。

## 開源跟社會運動間的關係？


開源是一種協作的具體方式，而自由軟體運動則是希望人們主動爭取這種分享、協作的自由，兩者是相輔相成的。

### 您認為亞洲的國家中，臺灣在開源的表現如何（或許有個排名）？


可能因為我是[安那其](https://zh.wikipedia.org/wiki/%E5%80%8B%E4%BA%BA%E7%84%A1%E6%94%BF%E5%BA%9C%E4%B8%BB%E7%BE%A9)，開源社群也[比較沒有國家的觀念](https://zh.wikipedia.org/wiki/世界主義)，所以很抱歉無法提供相應的認知。
（今年的 [OKFN 政府開放資料普查](http://global.census.okfn.org/)是有各國排名的，也許是最接近的數據了。）

### 那日本以及韓國等先進國家是不是開源社群也很發達？


我在開源社群認識許多日本朋友，在地社群非常發達，也多次造訪當地的友人。
我沒有去過韓國參與社群活動，所以並不清楚在地的情況。

### 中國的開源風氣似乎也很盛行？例如網路資源的翻譯等。


正如你所說，簡體中文的線上社群很活躍，尤其是翻譯的協作能量很強。

### 是不是國家政權的壓迫，在網路的開源社群成了另一個宣洩的出口，但同時也打壓了實體開源社群？


從中國友人處瞭解到的在地開源社群，往往是以企業與國家經濟政策為推動力量，和台灣的草根發展方式稍有不同，但倒是沒有聽說實體社群被打壓的情況。

## 這一兩年臺灣的社會運動與Open Source社群的發展有什麼關聯？


網際網路使得人們可以用分享、協作的精神，在各自關心的社會議題上進行協作，而開源社群提供了一些良好的運作先例與平台。運動者們可以拿這些[作為起點](https://0sdc.tw/)，針對特定的議題打造相應的社群協作模式。

## Open Source的理念顛覆了世界哪些事情？


在經濟模型上，從匱乏/分配的心態，轉向豐足/分享的心態。
在政治模型上，則是從科層的心態，轉向協作的心態。

### 可以跟我們多闡述一下您提到的「匱乏」是指哪一部分？制度面還是資源面？


都是。社會朝向[後稀缺模式的轉型](https://medium.com/@RickWebb/the-economics-of-star-trek-29bab88d50)，需要制度和資源兩方面的配合。

自由軟體和[豐足心態](https://en.wikipedia.org/wiki/The_Seven_Habits_of_Highly_Effective_People#Abundance_mentality)的連繫則是從一開始就有的，例如 Richard Stallman 在 1985 年撰寫的 [GNU 宣言](https://www.gnu.org/gnu/manifesto.html)裡提到：「\[這\]是邁向**不虞匱乏的世界**的一步驟...  我們已經大量減少了達到目前生產力所需要的工作量，但是只有其中的一部份轉化成工作者的閒暇，因為要達到有生產力的活動往往伴隨著很多沒有生產力的活動 \[...\] 為了使科技對生產力的增益能實質上減少我們的工作量，我們必須這麼做\[GNU計劃\]。 」（[蕭永慶譯文](http://www.linux.org.tw/CLDP/OLD/doc/gnu-manifesto.html)）

### 開源又是怎麼影響經濟以及政治模型的？


在經濟方面，傳統分配模式的[公地悲劇模型](https://zh.wikipedia.org/wiki/%E5%85%AC%E5%9C%B0%E6%82%B2%E5%8A%87)已被證明為過時的想像，開源社群也提出[分享經濟](https://en.wikipedia.org/wiki/Sharing_economy#Origins)作為新的思考架構。其中除了台灣近年較為熟悉，由 [Clay Shirky](http://search.books.com.tw/exep/prod_search.php?key=Clay+Shirky&f=author) 提出的[串聯模型](https://g0v.hackpad.tw/Opening-Keynote-g0v-unconference-2014#:h=%E4%B8%AD%E6%96%87%E7%BF%BB%E8%AD%AF)之外，由 Jeremy Rifkin 提出的[零邊際成本模型](http://www.books.com.tw/products/0010658142)和 Yochai Benkler 提出的[協造共有模型](http://benkler.org/Pub.html#Cooperation)，都是從開源社群實地觀察出來的思想。

政治方面，開源專案去中心化的成功運作，促成了各地的[網絡民主](https://en.wikipedia.org/wiki/E-democracy)實驗。Lawrence Lessig 將開源理念擴增為（以創用 CC 為先導的）自由文化運動後，也進一步針對美國的[金權政治結構](http://lesterland.lessig.org/)，用群募模式來經營以[獻金透明化](https://www.opensecrets.org/)為訴求的新政團，以改進現有民主體制。更接近安那其的這端，則有[柄谷行人](http://www.books.com.tw/products/0010574820)提出透過開源分享的實踐，來**消弭國族與資本造成的隔閡**。

### 可以給我們一些實際例子嗎？因為這對我們來說很抽象。


是，這些真的很抽象，因為都牽涉到對「社會發展」這個現代化核心概念的[重新想像](http://pekkahimanen.org/content/oup-book.html)。Federico Pistono 最近寫了一本[少年小說](https://audreyt.github.io/AToTF/)，裡面舉了許多近未來的實例，也許可以參考。

以目前實際運作中，與食衣住行相關的分享經濟模式實行者，較知名的有：Airbnb, Kitchit, Rent the Runway, Getaround, Uber,  Couchsurfing, NearDesk, MakerSpaces, JustPark, Spacious, Hassle,  BlaBlaCar, Zipcar, DogVacay, Spinlister, RiseArt, Streetclub, FarmDrop, Grub Club, BrandGathering, Nimber...

## OpenStack、GitHub在近年竄紅的原因為何？和過去開源運作方式有什麼不一樣的地方？


過去的專案運作模式，有像 [IETF](https://www.ietf.org/) 那樣任何貢獻者都可以加入工作組的，但也有較為傳統、科層式的。
GitHub 和 OpenStack 都是現代[開源治理模式](https://en.wikipedia.org/wiki/Open-source_governance)的好例子，前者是基礎建設，後者則體現了具體的模式運作。

### GitHub 和 OpenStack 對開源社群的發展有什麼影響？


GitHub 及其他類似的開源平台（如 GitLab 等），讓沒有軟體開發經驗的新手，也能漸進熟悉各項專案協作工具（持續整合、交互審核、待辦事項等）。這降低了文字、影像、模造、甚至是[數學](https://github.com/HoTT/book)工作者的進入門檻，讓更多人能進入開源社群。

我有使用 Rackspace 的 OpenStack 服務，也理解它使運算平台的提供者與使用者，能有效合作出開源的各式基礎建設，但其實我平日較常參與的是較為輕量的 [Docker 生態系](http://www.ithome.com.tw/news/91839)，以及同樣基於 Linux Container 架構的 [Sandstorm 社群](https://sandstorm.io/)。這類的「貨櫃化」技術，大幅簡化了開源系統的部署：無論架設開發環境、串接網路服務、甚至整套系統的昇級（如 [Ubuntu Snappy](http://www.ubuntu.com/cloud/tools/snappy)）等，都較以往方便許多。

這讓社群開發者可以花更多心思在「**系統介接優先**（API First）」的架構設計上，在節省技術支援時間的同時，也使「參與者」成為「貢獻者」變得更加容易。

### 而在整體IT層面與商業模式運作上會產生什麼影響？


關於降低參與社群的門檻，並且持續將維運簡化後，會產生的影響，這裡引用 2014 年 4 月我在 [RailsGirls.tw 講座會後座談](http://audrey.nu/-/2014/06/16/railsgirls-panel)的部份意見：

我認為程式教學和服務業 ，將會變得非常分散。在 20 年前，我們有所謂「[結蛹期](http://foldoc.org/larval+stage)」的概念。這是黑客詞典 Jargon Files 裡的一個詞。它說，基本上要成為一個專業的程式員或黑客，你必須花三、四年的時間沉迷於電腦當中，你會完全打亂你的睡眠模式，一次寫 20 個小時的程式。然後，到了某個點，你就會頓悟。這其實很像禪宗的想法。

一旦你到了那個點，所謂「零的轉移、巫術的權勢」，基本上你就成為一個[巫師](http://foldoc.org/wizard)。一旦你成為巫師，正如[松本行弘](https://zh.wikipedia.org/zh-tw/%E6%9D%BE%E6%9C%AC%E8%A1%8C%E5%BC%98)所說，所有關於性別、種族、年齡、國籍的差別都會消失。這就像《駭客任務》中 Neo 把一切都看成是綠色數字的一幕。到了那個階段，沒有東西能夠影響你的客觀判斷。這也是一個非常禪宗的概念。

可是我認為這算是一個神話，主要是因為那個時候如果沒有網路社群，要學習程式是非常困難的事。

現在有 RailsGirls 和類似的社群，我們就有了一個緩坡。你可以非常舒適地留在斜坡上的任何一點，還有很多人會在同一級階梯上**互相支持**，不一定需要兩三年的密集時間。用這種方式，你可以學上五、六年 —— 你甚至可以一天睡 8 個小時也不會退步。我認為這會大幅改變市場，因為除了業餘愛好者和專業人士之外，階梯上的每一點還會有細分的市場，這樣市場和社群都會變得大很多。

## Open Source為什麼對於這世界很重要？


目前這個充份資訊化的世界，已經進入匱乏/分配/科層等交換模式難以為繼的時代。此時開源社群提供了一個示範，由「向不特定人分享」開始，經過「集合眾人貢獻」的過程，使能夠永續、接力與共享的創造得以發生。這裡再次引用 2014 年 4 月座談時的發言：

傳統上，有三種為人熟悉的交換或市場營銷行為。其中一種是**內團體**（In-group），就像我們同在一個家庭，或者是處於同一個「社區」裡，當中有分內團體（In-group）和外團體（Out-group）。家庭或是這些內團體的成員，他們會共享一切、交換一切，可是他們不會跟外人，比如說非我族類（「外來人」）分享。這是其中一種交換模式。

第二種交換，就是我們在政府或者是其他層次結構中看到的，我們只會跟梯子上方或下方的人進行交換。比如說，我只會向我的經理報告，然後我的經理會跟他們的經理報告，再往下分配資源。這種交換是完全**科層式**的。

第三種就是我們跟任何有錢的人交換。我們向有錢的人提供服務或貨品，然後我們用這筆錢再與別人交換，與其他向我們賣東西的營銷者交換。基本上就是使用**貨幣交換**。以上是世界上三個主要的交換模式。

可是，以行銷者的身份參與開放源碼（像 Ruby 社群），你就能學會世界上第四種交換模式，也就是說，你可以自由地**跟世界上任何人，為了任何目的而交換**。這是一個非常革命性的想法：我不在乎你是否跟我來自同一個族群；我不在乎你是不是台灣人。我不在乎你是不是老闆或經理；我不在乎你有沒有錢。我想向你提供我的服務，我就慷慨給你。

我們已經證明了，這種行銷方式（像 Linda Liukas 的 [Kickstarter 活動](https://www.kickstarter.com/projects/lindaliukas/hello-ruby)）比起前三種傳統交換模型，能夠更有效地在更短的時間內接觸到更多的人。這將會是 21 世紀的潮流。參與開源社群，你會親眼看到它如何運作，以及掌握它的運作方式。

### 您認為充分資訊化的世界為何會進入「匱乏/分配/科層等交換模式難以為繼」的時代？


有了網際網路，人們可以直接聯繫到任何一個人，而發行給十萬人跟一百萬人時，成本並不會增加。但 WWW 的特性除了發佈之外，更重要的是[交互連結](http://www.cluetrain.com/newclues/#31)：「每個人做出的超連結，都是慷慨無私的展現，邀請讀者離開作者的頁面，去看看其他人是怎樣看世界的。」

舊有的文化交換模式，例如「製作大英百科全書很耗時，所以要賣很貴」（**匱乏**）、「學校沒有那麼多經費，大家要輪流到圖書館借百科全書」（**分配**）、「借閱規則要由校方制定」（**科層**）等等，與上述交互連結的文化相比，顯然是蒼白而緩慢的。

除了文化傳播外，在公共領域裡，對於習慣直接聯繫，並且在**不設定特定用途**的網際網路上生活的行動者來說，舊有的參與和運動型態也難以沿用。這裡可以引用 [Manuel Castells 的觀察](http://pugs.blogs.com/audrey/2013/12/networks-of-outrage-and-hope-1.html)：

「從歷史上來看，社會運動依賴特定通訊機制的存在：謠言、佈道、手冊和宣言，從講台、出版界出發，透過種種可行的交流方式，在人與人之間流傳。在我們的時代，多重模態的橫向交流與數位網路，是史上最快、自主性、互動性、可重編程性及自我擴張性最高的交流方式。

從事社會運動之個體間的通訊機制，決定了社會運動本身的組織特性：通訊方式愈互動、愈能自我建構，組織的層級就愈少，而運動的參與度愈高。因此，數位時代的網路化社會運動，足以成為社會運動的一種新的型態。」

### 「向不特定人分享」是否能徹底解決這個問題？


新的分享模式總是和現有的交換模式並存，所以我想並不會有「徹底解決」的一天。

誠如 Julian Assange 所說：「這是自古以來就存在於**投機者**與**合作者**之間的鬥爭，所以我認為它不會消失。我想我們可以取得一些重大的進展，而取得這些進展、投身於奮鬥的過程，對人是有益的。所以這個過程，其實就是最終目的裡的一部份。事實上，對人們有價值的並不是最後達成某個狀態，而是讓人們感覺**值得投入奮鬥**的**這個過程**。」（出處：[施密特與亞桑傑的會談紀錄](https://docs.google.com/document/d/1CydI-434RtH0YvNs9QqRTok6tM48Cttbc1mane2WJ0E)）

### 是否有實例可以讓我們更明白開源模式改善「匱乏/分配/科層等交換模式難以為繼」？


以個人的經驗來說，這裡引用 [2014 年 12 月 20 日的訪談](https://g0v.hackpad.com/Kbw8wn6vhYg)：

...所以我其實國一後來就沒有再去上學了，那我覺得對我最大的影響就是覺得說，需要學甚麼的時候，可以都在網路上找到，因為剛好我13歲的時候，就是 Tim Berners-Lee 發明 World Wide Web 的時候。
> 請問您13歲是西元幾年，我們需要這個時間點，感謝：Ｄ
> [name=蒲君 李]

> 「沒有人」回答：生日是1981年04月18日，13歲是西元1994年
> [name=蒲君 李]


在那之前，我沒有那個信心說，我要的一切在BBS、或FTP、或Gopher上都找得到，可是看到WWW社群的爆炸性的成長，我就發現說，我不管對甚麼有興趣，像我對例如人工智慧有興趣，我只要發一封email，我就可以給[Douglas Hofstadter](https://zh.wikipedia.org/wiki/%E4%BE%AF%E4%B8%96%E9%81%94)，實際做AI最前端的研究者，他就會回我信，這中間是沒有時間差的，那我們中間做的[任何成果](http://audrey.nu/-/1997/12/07/chickadee)可以發佈在網站上給大家看到。所以我覺得這個對我的影響就是說：**不需要經過中介**，就可以接觸到我感興趣的東西。

換句話說，從 1994 年開始，舊有的交換模式對我個人來說，就已經難以為繼了。

## Open Source的發展有遇到什麼困難嗎？


早期主要是與工業時代的「軟體製造」模式相互拮抗，但隨著「軟體即服務」概念被廣泛接受，現在在軟體界推行開源模式已經沒有特別困難之處。延伸到其他社群時，可能也會經過類似的過程。

### 軟體即服務與開源模式之間的關係是什麼呢？


在「軟體製造」模式下，販賣套裝軟體後的維護成本較低，而初次開發成本較高，所以會把軟體視為資產。

反之，在訂閱式的「軟體即服務」模式下，幾乎所有成本都花在回應訂閱者和新環境帶來的需求，也就是**維護和支援**工作上。此時任何未充份元件化的軟體都是持續的[技術負債](https://en.wikipedia.org/wiki/Technical_debt)，並非資產。

而若要促進軟體元件化，並找人分攤維護、支援的工作，開源社群是目前所知最有效的模式。

## Open Source人應該具備什麼能力？


語文溝通、邏輯思維的能力是必要的，其他只要保持好奇心即可。

## 給想進入開源社群的新手一些建議吧？


想做到什麼，就動手去做。真心想做一件事時，全宇宙的「沒有人」都會來幫你的。

### 那新手的第一步應該從哪裡開始呢？


把你的想法放到某個空間，讓其他人可以看到，並且歡迎大家提出改進。
不用怕想法不完整，也不用覺得有瑕疵很丟臉。
誠如 Leonard Cohen 所說：「[萬事萬物都有缺口，缺口就是光的入口](https://www.youtube.com/watch?v=mDTph7mer3I&t=3m0s)。」

## 未來開源發展的趨勢？


我想主要會靠「更多元化的參與者」、和「更跨領域的專案」，來觸及生活的更多層面。

### 您認為「更多元化的參與者」、和「更跨領域的專案」運作模式和現在有什麼不一樣的地方？


在參與者方面，隨著紀錄、發佈、版本追蹤成為表現活動的一部份（例如這份共筆），只要有溝通或創作意願，即使只有[零星的時間](https://www.moedict.tw/%E9%9B%B6%E6%98%9F%E7%87%8E%E5%8E%9F%E6%8B%86%E9%99%8B%E6%94%BF%E6%99%82%E9%9B%A8%E6%BD%A4%E7%89%A9%E5%BB%BA%E6%96%B0%E5%BA%9C%E3%80%80%E3%80%80%E3%80%80%E3%80%80%E3%80%80%E3%80%80%E3%80%80)也能進入社群協作，不再只是少數嫻熟工具、時間充裕的創作者才能參與。

在跨領域方面，輸入工具的普及（觸控、聲音、手勢、情感訊號等）讓愈來愈多的類比表意訊息進入數位世界，與之相應的協作空間操作門檻也持續下降，再沿著新的輸出方式（立體印製、擴增實境、可程式化物質）進入生活。這樣一來，開源專案的內容也將不受平面影音文字媒材的侷限。

### 另外，有關生活更多層面，可以給我們一些例子嗎，且和過去相比產生了什麼變化？


從維基百科的分類來看，舉凡[公民科學](https://en.wikipedia.org/wiki/Citizen_science)、[研究論文](https://en.wikipedia.org/wiki/Open_access)、[協作空間](https://en.wikipedia.org/wiki/Open_collaboration)、[創作內容](https://en.wikipedia.org/wiki/Open_content)、[電傳通訊](https://en.wikipedia.org/wiki/Open_communication)、[開放資料](https://en.wikipedia.org/wiki/Open_data)、[設計](https://en.wikipedia.org/wiki/Open_design)、[教育](https://en.wikipedia.org/wiki/Open_education)、[政府](https://en.wikipedia.org/wiki/Open_government)、[治理](https://en.wikipedia.org/wiki/Open-source_governance)、[協同創新](https://en.wikipedia.org/wiki/Open_innovation)、[公民媒體](https://en.wikipedia.org/wiki/Open-source_journalism) 、[開放硬體](https://en.wikipedia.org/wiki/Open-source_hardware)等社群，可以說全部都是受開放標準及開源運動影響，涉及的層面已**遠超出軟體的範圍**，這是和過去最大的不同。


## 修訂紀錄

2015年1月5日
> 這時間戳記該不會要手動吧＠＠
> [name=蒲君 李]

> 不用手動啦，Hackpad 會存
> [name=Audrey T]

> 謝謝XD
> [name=蒲君 李]

> 第一輪回答完了~
> [name=Audrey T]


2015年1月6日
> 第二輪提問完成，麻煩您了！
> [name=蒲君 李]

> 先回答了一半，因為舉例要查文獻比較費時，醒來再繼續...
> [name=Audrey T]

> 麻煩您了，謝謝
> [name=蒲君 李]

> 抱歉今天先整理[另一篇訪問逐字稿](https://g0v.hackpad.com/Kbw8wn6vhYg)（也是 CC By 授權，也許可以視需要引用？）醒來會繼續這裡的對話。
> [name=Audrey T]

> It's okay~THX
> [name=蒲君 李]


2015年1月9日
> 「理念」那段查文獻終於告一段落了。XD 其他問題比較屬於個人經驗，會比較快回答完。
> [name=Audrey T]

> 謝謝：）
> [name=蒲君 李]

> 除了「網絡社會中交換模式範型之轉移」之外的問題都答完了，也盡量舉了實例。歡迎先加入第三輪的問題。
> [name=Audrey T]

> 我會仔細想想要如何在不使用文獻和引用範例，純就個人經驗的方式，來回答「交換模式範型之轉移」的問題。感謝耐心等候。
> [name=Audrey T]

> 好的，待我們消化一番，有一種看論文追reference的FU ：Ｄ
> [name=蒲君 李]

> OK! 已貼完回答 :+1:
> [name=Audrey T]


2015年1月10日
> 補上了大部份 reference 的超連結。如果有需要其他注釋請再和我說。感謝！
> [name=Audrey T]


2015年1月12日
> 也請美編在排版內文時，同樣保留完整的授權字樣，如「CC BY 4.0 [https://g0v.hackpad.com/7Ev6ApUzYtA](https://g0v.hackpad.com/7Ev6ApUzYtA)」。
> [name=Audrey T]

> 另外，今天依據國教院的[雙語詞彙網](http://terms.naer.edu.tw/)校正了用詞及譯名，可以作為定稿了。感謝提問！
> [name=Audrey T]

> 好的，謝謝。
> [name=蒲君 李]


2015年1月16日
> 修訂紀錄移到這裡，有空時請改成 public pad。感謝！
> [name=Audrey T]

> iThome電腦報695期已出刊，採訪過程已設定為公開，謝謝：）
> [name=蒲君 李]

> 非常感謝願意公開原稿。刊登稿有兩處訂正，如不麻煩的話，希望能在線上版修改：
> [name=Audrey T]

> 1\. 「發起」請改「參與」（確實從 2012 年就在 IRC 上參與了，只是沒有到現場）。
> [name=Audrey T]

> 2\. 「成員」希望改成「參與者」，原因請見 [g0v Media Policy](https://g0v.hackpad.tw/Rbpc5FiUyA5) 。
> [name=Audrey T]

> 然後「十大電腦高手」是黃創夏在新新聞 1996 年做的專題，當時並未徵得同意，如果不麻煩的話，也敬請刪除或注明年份出處。感謝！
> [name=Audrey T]


2015年1月17日
> 已看到線上版訂正了「發起」→「參與」字樣。:+1:
> [name=Audrey T]

> hi 唐鳳，
> [name=王宏仁]

> 謝謝您的分享，我們真的很高興，有機會能夠採訪您的分享。關於您的幾點希望，
> [name=王宏仁]

> 1.原本提及2013年發起的原因，第一次g0v黒客松是2013年1月之故，此未詳細向您再查證，是我們有錯，網頁會修正，紙本也會同步勘誤.
> [name=王宏仁]

> 2.內文提及十大電腦高手的敘述請恕無法刪除，因為我至今還是這樣認為，所以才會同意這樣的行文。但尊重唐鳳的意願，我們會在網頁上修正敘述方式來交代年份和概略出處，讓描述更清楚。不過，因非內容的錯誤，這部分紙本無法勘誤。
> [name=王宏仁]

> 3.對於「成員」希望改成「參與者」的部分，我詳細讀過了「g0v Media Policy」和「社群對自稱 g0ver 的幾種方式」兩文的討論。
> [name=王宏仁]

> 因一開始未以g0v角度邀約，只是因為唐鳳您在開源中的資歷，所以，使用我認為對一般大眾容易理解的詞彙「成員」來描述。
> [name=王宏仁]

> 因為g0v雖不是組織（Policy提及怕用「成員」會暗示g0v是組織），但g0v是社群，社群成員是一般社會對於加入社群的人的形容，而且參與者有一種只是參加，但參與不深，不向「成員」更有一種對社群歸屬感的意思。所以，我用重要成員來形容您跟g0v的關係。
> [name=王宏仁]

> 不過，若唐鳳您希望凡是所有您的分享，都希望以g0ver的身份發言，所以，都要遵守g0v Media Policy，那麼，我們會修改網頁內容的稱呼。但請恕無法勘誤，因難以在紙本上詳細說明社群「成員」和社群「參與者」的細緻差別。
> [name=王宏仁]

> 另有一事，紙本排版限制，[https://g0v.hackpad.com/7Ev6ApUzYtA](https://g0v.hackpad.com/7Ev6ApUzYtA) 是以QRCode和縮網址形式呈現，而無法依記者在採訪上所答應以原整網址呈現，這還請您見諒。報導文章文末也同樣有提供連結和QRCode採訪原稿，我剛剛也加上完整的授權字樣了。
> [name=王宏仁]

> iThome主編 宏仁
> [name=王宏仁]

> 宏仁您好，非常感謝您半夜即時回覆！全部如您所說處理即可。
> [name=Audrey T]

> 仍會希望在網頁將「成員」改稱「重度參與者」或「貢獻者」，但同意紙本不需勘誤。
> [name=Audrey T]

> 黑客松從「第零次」起跳，確實容易出人意表（也就是很宅的意思...），無心之失不用介意。 :cat:
> [name=Audrey T]


