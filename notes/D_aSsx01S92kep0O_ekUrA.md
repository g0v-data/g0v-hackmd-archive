---
title: "MaD | clkao: Open Source, Open Data, Open Government 字幕翻譯"
tags: 翻譯共筆,Talk,hackpad
---

# MaD | clkao: Open Source, Open Data, Open Government 字幕翻譯

> [點此觀看原始內容](https://g0v.hackpad.tw/reo7f4xdWAy)

[https://www.youtube.com/watch?v=-BYb5wFAxOA&feature=youtu.be](https://www.youtube.com/watch?v=-BYb5wFAxOA&feature=youtu.be)


字幕 CC-BY 釋出

協作方式：校對英文，並將中文打在下面（part 2 時間軸要加上 10m13s，不過請不要修改，到時候在用程式一併改正）

Note: 口語中 嗯嗯啊啊 或改口部分請直接刪除 讓英文通順

認領請先簽名：（可分中文、英文。英文完成後請 mark done；中文請等英文校對後再開始進行）
part 1
1-30:
- [x] isacl(英 done)  , clkao(中, done)
31-60:
- [x] Pichu Chen(英 done)  , ipa (中 done)
61-90
- [x] jiayan(英done) , CHIU-HSIN(中done)
91-120:
- [x] jiayan(英done),  megan(中,done)
121-150:
- [x] jiayan(英done)  , megan(中,done)
151-
- [x] ballII(英done. reviewed)  , ballII(中done)

part 2
1-30:
- [x] LCamel (英 done,  reviewed) LCamel (中, done, reviewed)
- [x] 31-60: ballII(英done, reviewed) ballII(中done)
- [x] 61-90: ballII(英done) ballII(中done)
- [x] 91-120: cades(英done, reviewed)  <沒有人>(中)
- [x] 121-: clkao(英 done)

### Part 1

=========
1
00:00:06,599 --> 00:00:08,339
In 2012
2012 年的時候

2
00:00:08,339 --> 00:00:12,230
the Taiwanese government aired a
commercial about "Economy power up plan"
台灣政府播放了一個「經濟動能推升方案」的廣告

3
00:00:12,230 --> 00:00:15,269
Essentially the commercial is saying that
基本上這個廣告的內容是在說

4
00:00:15,269 --> 00:00:18,439
"Economy affairs are very complicated
經濟事務非常的複雜

5
00:00:18,439 --> 00:00:22,730
you, or we, the citizens don't need to know the
details.  They will take care of it."
我們公民們不需要知道細節，政府會嚴格把關

6
00:00:22,730 --> 00:00:27,449
"And we should just mind our business and let them do
whatever they think it's appropriate."
而我們應該只要管好我們自己的事務，讓他們去做他們認為是恰當的事

7
00:00:27,449 --> 00:00:30,670
I was kinda disturbed by this
我對「你不需要知道細節」

8
00:00:30,670 --> 00:00:34,420
idea of being, like, well you don't need to know
that.
這樣的概念感到惱火

9
00:00:34,420 --> 00:00:38,050
So what I felt  is that tax money is burning
我覺得我們繳的稅金就這樣被燒了

10
00:00:38,049 --> 00:00:42,789
like for free. So I felt really angry
我覺得非常生氣

11
00:00:42,789 --> 00:00:46,308
I really wanted to do something about
this.
於是我很想做點什麼

12
00:00:46,308 --> 00:00:51,649
As you probably know I write software.
I really like writing software
你大概知道我是寫軟體的
我很喜歡寫軟體

13
00:00:51,649 --> 00:00:54,878
even when I broke my spine and had to be
hospitalized for
甚至當我摔斷脊椎需要住院躺平三個禮拜

14
00:00:54,878 --> 00:00:58,119
three weeks lying flat I still like writing software.
我還是很喜歡寫軟體

15
00:00:58,119 --> 00:01:02,828
Anyway, that's my twitter (@clkao) you can follow me.
總之，這是我的 twitter 帳號 (@clkao)，你可以 follow 我

16
00:01:02,829 --> 00:01:06,579
So being like a software developer what
I wanted to do
作為一個軟體開發者，我想做什麼呢？

17
00:01:06,579 --> 00:01:10,030
is that \- okay the government is spending
money in some
好，既然政府用一種我無法理解的方式在花錢

18
00:01:10,030 --> 00:01:14,200
way I didn't understand.  How about that
take a closer look at it?
不如我們來仔細看看這件事情

19
00:01:14,200 --> 00:01:17,759
So a couple of friends and I tried to look at how
the government budgets
於是我和一些朋友開始看政府預算支出

20
00:01:17,759 --> 00:01:21,118
is spent.  Of course government released a
budget
當然政府預算是用長得像這樣的 pdf 檔釋出

21
00:01:21,118 --> 00:01:25,109
in a PDF file looks like that.  So with
some programming
於是我們寫了一些軟體

23
00:01:30,478 --> 00:01:35,769
we turned that into bubbles.  This is the
budget visualization.
把預算變成了一個個的泡泡
這是預算的視覺化

24
00:01:35,769 --> 00:01:38,939
Each of the bubbles represent an entry of a budget.
每個泡泡代表一筆預算

25
00:01:38,939 --> 00:01:42,459
You can group that by sectors or the
你可以用政事別來看

26
00:01:42,459 --> 00:01:46,810
ministry that responsible for it.  And
also when you hover over
或者權責機關來看
並且滑鼠移上去時

27
00:01:46,810 --> 00:01:49,868
the bubbles you can see a history of
individual entries.
你可以看到該筆預算過往的紀錄

28
00:01:49,868 --> 00:01:56,618
That's easier to understand,  right ?
這讓人更容易了解，不是嗎？

29
00:01:56,618 --> 00:02:00,728
So the  idea of the g0v movement is that
we know the government website in Taiwan is called "gov.tw",
g0v 運動的概念是這樣
台灣的政府網站叫做 gov.tw

30
00:02:00,728 --> 00:02:03,969
what if we just replace one letter
要是我們能代換網址的一個字母

### 31

00:02:03,969 --> 00:02:08,419
'O'(oh) to '0'(zero).  It suddenly becomes a better
從 O 變成 零
他突然就變成一個更好用的網站

32
00:02:08,419 --> 00:02:11,780
and easier to use website. So

33
00:02:11,780 --> 00:02:15,640
that  also stands for the idea that
同時，他也代表了

34
00:02:15,639 --> 00:02:19,229
it's from the digital natives  like me and many of you,
數位原生世代，如我自己和許多在座各位

35
00:02:19,229 --> 00:02:23,039
who are rethinking how the government should
work in this digital age from zero.
我們來重新思考
在數位時代，政府該如何運作

36
00:02:23,039 --> 00:02:28,090
So what we do is that we start  Hackathons.
因此我們就開始舉辦黑客松

37
00:02:28,090 --> 00:02:31,289
Hackthon is the kind of event it's essentially
黑客松是一種工作坊

38
00:02:31,289 --> 00:02:34,328
Hack Marathon.   So Hack it's not like
就是黑客馬拉松

39
00:02:34,329 --> 00:02:37,500
breaking into someone else computers.
It's like creating things
這不是指入侵別人的電腦主機

40
00:02:37,500 --> 00:02:40,669
or magically making things happen. This's called
"Hacking"
而是創造新的東西、用巧妙的方式解決問題
我們稱為 hacking

41
00:02:40,669 --> 00:02:44,039
so it's like a one day long food
consuming
黑客松當天會提供很多食物

42
00:02:44,039 --> 00:02:48,519
or working session. Because the
大家就聚在一起工作一整天

43
00:02:48,519 --> 00:02:51,718
the kind of problem that we want to
visualize the
我們想把很複雜的議題視覺化

44
00:02:51,718 --> 00:02:55,408
things like budgets and other
things that is very complicated.  We need
例如中央政府總預算

45
00:02:55,408 --> 00:03:01,548
a lot of people to help.  How do you
get a lot of people to help on projects?
我們需要很多人的投入
要怎麼樣找來很多人一起加入專案工作呢？

46
00:03:01,549 --> 00:03:03,939
You buy them foods.
就是準備很多食物！

47
00:03:03,939 --> 00:03:07,789
Lots of food. So a typical Hackthon is like that
通常一整天的黑客松流程大概是這樣

48
00:03:07,789 --> 00:03:11,109
we have about a hundred of people in the room, in
the morning
每次大約有一百人參加

49
00:03:11,110 --> 00:03:14,640
there's no agenda.  So people come with
their own projects
沒有預定的議程，每個人帶著自己想做的專案來

50
00:03:14,639 --> 00:03:18,019
and tell other people what they have been doing and
what kind of  help they want from
上台報告自己手上的專案，並說明需要什麼樣的協助

51
00:03:18,020 --> 00:03:21,450
others and they start talking to
each other and see they can have a
接著就開始討論自行組隊，在一天內衝刺

52
00:03:21,449 --> 00:03:25,549
group together in one day.  In the
afternoon people hack and
下午就是一直  hack  和吃東西作軟體

53
00:03:25,550 --> 00:03:29,540
eat and create software.
What's amazing is that usually
令人訝異的是，通常到了下午

54
00:03:29,539 --> 00:03:33,400
in the afternoon we start having working prototypes
people come on
就會產出一些雛形

55
00:03:33,400 --> 00:03:37,250
stage and presenting  them to others.
Just in one day
每一組上台報告當天的工作成果

56
00:03:37,250 --> 00:03:40,770
we can build something that's useful and can be
improved later on.
這些初步雛形之後還能繼續開發改善

57
00:03:40,770 --> 00:03:44,210
so the way

58
00:03:44,210 --> 00:03:48,689
you get lot of people like hundreds
of people to work together
所以上百人來一起工作

59
00:03:48,689 --> 00:03:52,379
effectively its kind of  weird and then
還要有效率，聽起來很難對吧？

60
00:03:52,379 --> 00:03:56,340
hard to manage right?
But luckily we have
idea  of
但還好我們有開放原始碼的文化幫助推動社群工作

### 61

00:03:56,340 --> 00:04:00,729
open source that's been helping
how the community work.
開放源碼有助於
社群的推動

62
00:04:00,729 --> 00:04:05,389
so the central idea of open source is that when
you release your software
開放源碼的中心思想是
當你釋出你的軟體時

63
00:04:05,389 --> 00:04:09,139
you release in source form which means that
people can look at how
以源碼的形式釋出, 意味著人們可以查看

64
00:04:09,139 --> 00:04:13,369
it works and then they can modify it and
improve it and release it again
軟體是如何運作，而且可以修改它、
精進它、並且再一次將他釋出

65
00:04:13,370 --> 00:04:17,739
so I myself have been open source developer for 15 years
我自己已經擔任了15年的開源碼開發人員

66
00:04:17,738 --> 00:04:21,439
most of the time spent is  writing software
幾乎所有的時間都花在撰寫軟體

67
00:04:21,439 --> 00:04:24,689
pretty much
花了非常多時間

68
00:04:24,689 --> 00:04:28,050
all the time when I was not sleeping so
只要我不是睡著的時候都是

69
00:04:28,050 --> 00:04:31,160
most of the software I wrote is released
to the public for anyone to use
大多數我所寫的軟體都釋出
公開讓任何人都能使用

70
00:04:31,160 --> 00:04:35,240
and the open source idea came up from a simple idea that
開放源碼這個想法來自一個簡單的主意

71
00:04:35,240 --> 00:04:38,480
the engineers who solve
the problem
工程師解決問題後

72
00:04:38,480 --> 00:04:42,310
they want to share the solution to
others so people don't have to solve the
他們想要跟其他人分享解答
如此一來，人們便不需要

73
00:04:42,310 --> 00:04:43,259
same problem again
重複去處理相同的問題

74
00:04:43,259 --> 00:04:46,699
instead they can build the solution on
together
反而可以共同建立解決方案

75
00:04:46,699 --> 00:04:50,939
into solving bigger problems so it
soon become like a massive
進而處理更大的問題
所以他很快地變得像個大社群

76
00:04:50,939 --> 00:04:55,209
community because people can improve
each others' work
因為人們可以讓彼此的工作更加完好

77
00:04:55,209 --> 00:04:59,219
and then create more useful tools
並且製造更多有用的工具

78
00:04:59,220 --> 00:05:03,169
So, recently I contributed to a open source
project released  by Google
最近我參與
由谷歌（Google）釋出的開源碼專案

79
00:05:03,168 --> 00:05:07,649
the project has about 20,000 people
watching it
這專案已經有大約20,000人關注它

80
00:05:07,649 --> 00:05:11,539
and has about 600 contributors
而且有600個貢獻者

81
00:05:11,540 --> 00:05:15,870
it is really hard to imagine a piece of
software by any commercial company can be
對商業公司來說
難以想像一個軟體元件

82
00:05:15,870 --> 00:05:16,329
written

83
00:05:16,329 --> 00:05:21,159
by so many people
but it is very common  in open  source project
可以由這麼多人一起開發
但這在開源碼專案中是相當稀鬆平常的

84
00:05:21,160 --> 00:05:22,289
but what's more interesting is that
但更有趣的其實是

85
00:05:22,288 --> 00:05:25,689
at this given moment of time there are 250
就在此刻

86
00:05:25,689 --> 00:05:29,399
different versions of this software
that's made by other people
這個軟體有250種不同版本
被其他人寫出

87
00:05:29,399 --> 00:05:33,339
being submitted to the maintainer of the
project.  Each of these
被提交給專案的維護者

88
00:05:33,339 --> 00:05:37,299
different version, or we call branch, is either
a bugfix
這些不同的版本，或者我們稱作分支
要不是修復臭蟲

89
00:05:37,300 --> 00:05:41,100
or a new feature
so you can see this massive concurrent
就是一個新功能
所以你可以在這樣的模式中看見

90
00:05:41,100 --> 00:05:44,970
collaboration and development of
software in this model
軟體的大規模同步協作和開發是非常有效率的

### 91

00:05:44,970 --> 00:05:47,970
being very effective.
是相當有效率的

92
00:05:47,970 --> 00:05:51,330
So, for those of you not very familiar with software development
有些人可能不是很熟悉軟體開發的流程

93
00:05:51,329 --> 00:05:55,459
imagine as you use Google Doc or some
similar online document tools
想像你在使用 Google 文件或是類似的線上文件工具

94
00:05:55,459 --> 00:05:58,939
imagine you have a Google Doc and a lot
of people
想像有份 Google 文件，很多人可以同時編輯

95
00:05:58,939 --> 00:06:02,819
can edit it at the same time. So you see a lot of different color of cursors down there.
於是可以看到下面有很多不同顏色的游標

96
00:06:02,819 --> 00:06:06,389
And what's different from
that software development
和這不同的是，軟體開發更複雜

97
00:06:06,389 --> 00:06:09,629
a bit more complicated so we allow
people to make
所以我們讓人們可以做他們自己的版本

98
00:06:09,629 --> 00:06:13,519
their own version of it and then later we decide
之後再決定如何合併成一個新的標準版本

99
00:06:13,519 --> 00:06:16,759
how they are merged together into a new
canonical version

100
00:06:16,759 --> 00:06:19,810
so this is kind of like a

101
00:06:19,810 --> 00:06:23,060
effective way of working and this soon become
這種有效率的工作方式

102
00:06:23,060 --> 00:06:26,490
like a hobby of software
developers
很快地這變成了軟體開發者的嗜好

103
00:06:26,490 --> 00:06:30,810
into a whole eco-system, by eco-system I
mean there are successful commercial
成為一套完整的生態系統，我指的「生態系統」，是指這一整套系統，可以有成功的商業應用

104
00:06:30,810 --> 00:06:34,019
usage or business built  a ton of   the whole
system
或以此系統為基礎，發展出的商業模式

105
00:06:34,019 --> 00:06:37,810
for example, any of you not using Android or iPhone?
舉例來說，你們之間有人不是用 Android 或 iPhone 手機的嗎？

106
00:06:37,810 --> 00:06:41,410
probably all of you (are using it), so you are the user of
大概全部的人都有使用。
所以你們都是開放源碼科技下的受惠者

107
00:06:41,410 --> 00:06:45,550
open source technologies.  Imagine this
being a close system
試想如果是一個封閉的系統

108
00:06:45,550 --> 00:06:48,829
like when you sometimes see ATM
crashing into blue screen
例如我們看到自動提款機故障，成為藍白畫面

109
00:06:48,829 --> 00:06:52,569
It's not very nice. So, this is a
感覺很不好，對吧？
> 這兩個舉例（手機與 ATM) 不知道怎麼翻比較連貫
> [name=isacl]


110
00:06:52,569 --> 00:06:55,959
powerful idea of collaboration without central coordination.
這樣的一個無中央統籌，分散式地協作方式
是個很強大的工作模式

111
00:06:55,959 --> 00:06:59,299
So things can happen  simultaneously
很多事情可以同時發生

112
00:06:59,300 --> 00:07:02,889
and very efficiently.  So
非常有效率

113
00:07:02,889 --> 00:07:07,538
The seemingly chaotic way of working
together
這個混沌無主的協作模式

114
00:07:07,538 --> 00:07:12,519
soon inspire a smart guy saying "Hey! can
we not use this model and put
> not? should be "now"
> [name=isacl]

啟發了一個聰明人
他說：「我們來應用這樣的模式吧！」

115
00:07:12,519 --> 00:07:16,459
all the human knowledge  together in a place for anyone
to access
「把人類的知識，蒐集到一個大家都能免費取得的地方」

116
00:07:16,459 --> 00:07:19,948
for free?" yes Wikipedia! so
「維基百科」因此誕生

117
00:07:19,949 --> 00:07:23,540
most of us know Wikipedia from that
because it's like a wiki
我們了解，維基百科是一種共筆系統

118
00:07:23,540 --> 00:07:28,389
everyone can edit, right? but more importantly
is that the content on Wikipedia
但更重要的是維基百科的內容

119
00:07:28,389 --> 00:07:31,579
is opening licensed and everyone can reuse it
是開放授權的，且任何人都能再利用

120
00:07:31,579 --> 00:07:35,300
and that's the reason why people are
willing to contribute
這也是為何人們願意貢獻高品質內容給它的原因

### 121

00:07:35,300 --> 00:07:39,300
quality content to it.  So by using it
I mean
所以藉著這樣的方式

122
00:07:39,300 --> 00:07:42,680
things like you can build different ways of
我們可以做許多事，例如建立不同方式

123
00:07:42,680 --> 00:07:46,040
viewing Wikipedia articles.
來瀏覽維基百科的文章

124
00:07:46,040 --> 00:07:49,139
Most of you probably know this moral and
national education
大多數人大概都知道，香港現在進行德育及國民教育的新聞

125
00:07:49,139 --> 00:07:54,000
thing in Hong Kong right? This is really well
written article on Wikipedia
在維基百科上有一篇撰寫得很好的文章

126
00:07:54,000 --> 00:07:57,459
so but it's very long so it's like
但這篇文章很長

127
00:07:57,459 --> 00:08:00,500
you can't really tell people what happened
不容易在短短幾句話內，解釋讓其他人了解

128
00:08:00,500 --> 00:08:05,110
within three sentences right? so there's a
g0v project that turns any Wikipedia
因此產生了一個g0v的專案，能將任何一篇維基百科的文章

129
00:08:05,110 --> 00:08:08,939
page into a timeline representation
轉換成一個時間軸展示

130
00:08:08,939 --> 00:08:12,550
so you can scroll through all the
important date of what happened
捲動時間軸，你就能看到重要事件發生的日期

131
00:08:12,550 --> 00:08:16,129
and this data is from Wikipedia so
that's the power
而這些資料全部來自維基百科，而這就是開放內容的力量

132
00:08:16,129 --> 00:08:22,000
of open content.  You can make use in
some creative ways
你可以用某些創新的方式利用資料

133
00:08:22,000 --> 00:08:25,180
and right
而且

134
00:08:25,180 --> 00:08:31,389
scroll through. And you can link into individual
content
只要往下捲動，就可以連結到個別的內容

135
00:08:31,389 --> 00:08:38,389
another example is the TV license.  How
many of you were there?
另外一個例子是電視牌照。你們有多少人去了？

136
00:08:38,589 --> 00:08:41,729
okay so this crazy idea like
所以這個瘋狂的想法：

137
00:08:41,729 --> 00:08:44,949
openly creating content also inspire
people say
「內容的開放創建」，也帶給人們靈感
138
00:08:44,948 --> 00:08:48,409
“okay can we not make maps like Wikipedia?"
有的人問：「那好，我們能用建立維基百科的方式繪製地圖嗎？」

139
00:08:48,409 --> 00:08:51,549
so this is the OpenStreetMap project
we talk about
而這就是我們提到的OpenStreetMap專案

140
00:08:51,549 --> 00:08:54,549
and this flashing thing on the earth
地面上這個亮點

141
00:08:54,549 --> 00:08:57,740
is the mapping data being edited by someone.
代表有一位參與者正在編輯地圖資料

142
00:08:57,740 --> 00:09:01,419
By mapping data, I mean roads or building or
landscape
地圖資料指的是道路、建築、地景等相關資料

143
00:09:01,419 --> 00:09:06,129
things like that but the Wikipedia is just text content
維基百科只有文字資料

144
00:09:06,129 --> 00:09:09,828
but mapping is the actual data so
而繪製地圖使用的是實際資料

145
00:09:09,828 --> 00:09:13,189
with actual data, you can do a lot of
creative things like
使用實際資料時，可以做許多創新的事

146
00:09:13,190 --> 00:09:16,390
here's an example for wheelchair map
這是一個輪椅地圖的例子

147
00:09:16,389 --> 00:09:20,600
so in Hong Kong which subway exits are
wheelchair friendly
可以看到在香港那些地鐵出口能夠使用輪椅

148
00:09:20,600 --> 00:09:24,000
you can use it to to see.

149
00:09:24,000 --> 00:09:27,070
or you can plot the highways with
或者你可以畫出各高速公路

150
00:09:27,070 --> 00:09:30,970
speed limit on them
so there are about hundreds of different
其上顯示速限
有上百種不同的方式

### 151

00:09:30,970 --> 00:09:34,149
ways of using mapping data based on
來利用OpenStreetMap的地圖資料

152
00:09:34,149 --> 00:09:37,379
OpenStreetMap data and that's also the
power of open
這也是開放授權的資料有力的地方

153
00:09:37,379 --> 00:09:41,708
openly  license data

154
00:09:41,708 --> 00:09:46,500
so when we talk about Open Data
essentially Wikipedia and
當我們在談開放資料時
基本上，Wikipedia和

155
00:09:46,500 --> 00:09:50,889
OpenStreetMap are  kind of crowd contributed
Open Data
OpenStreetMap是種群眾貢獻的開放資料

156
00:09:50,889 --> 00:09:55,429
but when we talk about it nowadays
usually we mean government Open Data
但目前我們談的 Open Data 大多是指政府的開放資料

157
00:09:55,429 --> 00:09:59,399
and because government want to release
more information to the people
因為政府希望釋放更多資訊給人民

158
00:09:59,399 --> 00:10:04,169
to show their commitment of transparency
and transparency is the prerequisite
以展示他們對資料透明化所付出的心力
而且透明化是群眾參與所不可或缺的先決條件

159
00:10:04,169 --> 00:10:07,698
for participation
so you have to have all the data available
所以你必須讓所有資料易於取得

160
00:10:07,698 --> 00:10:11,049
for people to see to discuss and then people can
participate
如此人民才能看到、討論它們，進而參與

### Part 2

========= offset 10:13
1
00:00:01,139 --> 00:00:03,958
So to better understand how the government works,
為了更了解政府如何運作

2
00:00:03,959 --> 00:00:07,108
we tried to look at the legislative branch,
我們嘗試觀察立法院

3
00:00:07,108 --> 00:00:10,490
the congress.  So for example, here's a  government
國會. 舉例來說, 這是[政府](https://g0v.hackpad.tw/uPMzOyt3n2j#政府)

4
00:00:10,490 --> 00:00:14,519
congress vote record.  It's really hard
to read these tiny text, right?
國會投票記錄. 這些小字看起來很難懂吧?

5
00:00:14,519 --> 00:00:19,528
So we turned that into a nice chart.  And you can easily see
所以我們把它轉成漂亮的圖表. 這樣你可以輕易地看出

6
00:00:19,528 --> 00:00:23,339
who did what.  And similarly
誰做了什麼. 同樣地,

7
00:00:23,339 --> 00:00:28,089
we try to visualize how a bill was
introduced and put into a committee,
我們視覺化了法案如何產生, 交付委員會,

8
00:00:28,089 --> 00:00:32,429
being discussed.  And maybe there is a hearing
or something.  And then maybe they are passed
如何討論, 或許有公聽會或什麼, 或許通過了,

9
00:00:32,429 --> 00:00:33,289
or they are just
或許他們根本

10
00:00:33,289 --> 00:00:37,009
not handled in the congress.
And here's a way to see
沒被國會處理. 這裡我們能看到

11
00:00:37,009 --> 00:00:40,229
how each bill, how many bills  up there
每個法案是如何, 有多少法案正在

12
00:00:40,229 --> 00:00:44,128
in what stages and things like that.  Also,
哪個處理階段等等. 另外,

13
00:00:44,128 --> 00:00:47,820
when a bill was proposed, it is about to
change the law,
當法案提出時, 會改到現有的法律,

14
00:00:47,820 --> 00:00:52,270
right?  But the actual text for changing a
law is really hard to read
對吧? 但是法案增修的文字很難閱讀

15
00:00:52,270 --> 00:00:55,620
in government data as well.  So we also
turned that into
在政府版本的資料中. 所以我們也把它轉成

16
00:00:55,619 --> 00:01:00,280
something we called the "diff".  So the "diff"
is the way that programmers  are very
我們所謂的 "差異" (diff). "差異" 是程式設計者們

17
00:01:00,280 --> 00:01:01,439
familiar with,
很熟悉的.

18
00:01:01,439 --> 00:01:04,459
because they need to know
因為他們必須知道

19
00:01:04,459 --> 00:01:08,309
what change was made by whom  at what time.
誰在什麼時候改了什麼東西.

20
00:01:08,310 --> 00:01:12,590
So we kinda reuse this idea and then
apply it to
所以我們重用了這個概念, 把它用在

21
00:01:12,590 --> 00:01:17,090
the bill being proposed.
So in the amendment you can see that
法案上. 所以在修正案中你可以看到,

22
00:01:17,090 --> 00:01:20,329
this is a bill introduced made in Taiwan
that
這裡有個台灣的法案

23
00:01:20,329 --> 00:01:23,950
about allowing same-sex marriage.  And
關於接受同性婚姻的.

24
00:01:23,950 --> 00:01:28,140
when we have that, we give every
bill a single URL that people can
而且我們賦予每個法案一個可分享的網址

25
00:01:28,140 --> 00:01:28,828
share

26
00:01:28,828 --> 00:01:34,868
so people can share it easily and discuss on that
這樣大家可以很方便地分享與討論

27
00:01:34,868 --> 00:01:37,920
rather than arguing without a common basis.
而不是沒有基準地互相爭吵.

28
00:01:37,920 --> 00:01:41,799
And
此外,

29
00:01:41,799 --> 00:01:46,670
in the Taiwan congress we have live video feed,
but it's only available for Windows IE.
台灣的國會有現場轉播, 但只能用 Windows IE 看.

30
00:01:46,670 --> 00:01:49,689
How many of you are using IE?
你們有人用 IE 嗎?

### 31

00:01:49,688 --> 00:01:52,989
It's horrible right? so we kind of turned that into
超苦的，對吧？

32
00:01:52,989 --> 00:01:57,199
into like a mobile-friendly on modern
browser friendly UI
所以我們把他轉換成手持裝置和現代瀏覽器可以看的

33
00:01:57,200 --> 00:02:01,950
but to make it more interesting
we allow people to throw things to
但為了讓它更有趣
我們讓人們能丟東西

34
00:02:01,950 --> 00:02:05,210
the legislator or the government officials if
that
向這些立委和政府官員

35
00:02:05,209 --> 00:02:11,859
they are talking things you don't like
如果他們的發言讓你不滿意的話

36
00:02:11,860 --> 00:02:16,360
and we also do some were
constructive things  like
我們也做一些有建設性的事

37
00:02:16,360 --> 00:02:19,500
showing that the wave form
例如展示一整天議會記錄的音頻波型

38
00:02:19,500 --> 00:02:22,860
of the whole day length of the congress video

39
00:02:22,860 --> 00:02:27,010
but this is not really a good
example of Open Data
不過這不是一個開放資料的最佳範例

40
00:02:27,009 --> 00:02:30,348
because the congress data is not open we
have to
因為議會資料其實不「開放」

41
00:02:30,348 --> 00:02:33,378
download the PDF and turn that
我們必須先下載PDF檔

42
00:02:33,378 --> 00:02:38,030
back into raw data and  present it
in the previous form you see the
將它轉回成原始資料，再將它展示成你們剛剛看到的美觀模樣

43
00:02:38,030 --> 00:02:38,949
beautiful ones

44
00:02:38,949 --> 00:02:42,419
so it's kinda of the crawling
這是一種爬資料過程

45
00:02:42,419 --> 00:02:45,939
process and but a better example is
that
更好的例子是：

46
00:02:45,939 --> 00:02:49,699
a couple months ago the Taiwanese Environment
Agency released
幾個月前，台灣環保局

47
00:02:49,699 --> 00:02:54,399
open data for air quality and then
I was able to turn this
釋出了空氣品質的開放資料
而我有辦法

48
00:02:54,400 --> 00:02:57,719
PM 2.5 information into this beautiful
map
將這PM 2.5資訊轉成美觀的地圖

49
00:02:57,719 --> 00:03:02,949
within 30 minutes and being able to put
it in 30 minutes it's not just
這工作在30分鐘內就完成了，能夠如此的原因

50
00:03:02,949 --> 00:03:04,509
because the Environment Agency
除了因為環保署開放了資料

51
00:03:04,509 --> 00:03:08,098
has it in open data but  also because we've
done this before
還因為我們過去已有類似經驗

52
00:03:08,098 --> 00:03:12,439
so last year in the typhoon season we're
not happy with the official
去年在颱風季節，我們對官方雨量圖不甚滿意，

53
00:03:12,439 --> 00:03:15,729
rain chart  on the left because it's
updated only like
就是左方這張，因為它每小時才更新一次

54
00:03:15,729 --> 00:03:20,229
hourly and you know during typhoon is very
sensitive we kinda want to know
你知道颱風是瞬息萬變的，我們希望知道

55
00:03:20,229 --> 00:03:24,139
how much rain was spitting like
即時降雨量

56
00:03:24,139 --> 00:03:29,109
in real time so the rain
sensors are actually updated every 10
雨量站其實每10分鐘就更新一次

57
00:03:29,110 --> 00:03:29,680
minutes

58
00:03:29,680 --> 00:03:33,090
so we download the data and then draw
something very ugly
於是我們下載數據，並將它畫成一個很醜的圖

59
00:03:33,090 --> 00:03:36,509
on the right
but the important thing is that
就是右邊這張
但重要的是

60
00:03:36,509 --> 00:03:39,609
we publish the data  and make it available
for anyone to use
我們公開這資料，讓所有人都能取得使用

### 61

00:03:39,610 --> 00:03:44,120
and then soon after people turn that
into something really really beautiful
不久就有人們將它變得美輪美奐

62
00:03:44,120 --> 00:03:47,739
and then this person also released that  as open
source
然後這個人也開放資源與工具

63
00:03:47,739 --> 00:03:51,489
toolkit so we can reuse that and put it
together with the environment
以便我們再利用，於是我們整合環保局資料

64
00:03:51,489 --> 00:03:55,459
agency data and put a nice PM 2.5 map
within 30 minutes
在30分鐘內做成了一張漂亮的PM 2.5地圖

65
00:03:55,459 --> 00:03:58,878
so this is where we are
所以我們成就了這些東西

66
00:03:58,878 --> 00:04:02,109
the g0v project it's like a movement
and
g0v計畫像是一種運動

67
00:04:02,110 --> 00:04:05,430
very young about an year we have lots of
Hackathons
它還很年輕，大約只有一歲，而我們已經舉辦了很多場黑客松

68
00:04:05,430 --> 00:04:09,879
lot of contributors so
有非常多貢獻者

69
00:04:09,878 --> 00:04:13,389
the way we work is like we tried to
encourage people to use the open source
我們運作的方式類似這樣：
我們嘗試鼓勵人們使用開放源碼的模式協作

70
00:04:13,389 --> 00:04:15,139
model to collaborate even that

71
00:04:15,139 --> 00:04:19,469
they are not software developers
so when people have an idea we encourage them to
即使他們不是軟體工程師
當人們有新點子，我們鼓勵他們將它寫下

72
00:04:19,470 --> 00:04:20,160
write it down

73
00:04:20,160 --> 00:04:24,330
because if you're just talking about it
people cannot help
因為如果你只是用說的，旁人幫不了忙

74
00:04:24,329 --> 00:04:29,189
the idea and perfect it and better
yet we encourage people to
無法進一步將你的點子變得更完美
我們也鼓勵人們

75
00:04:29,189 --> 00:04:33,649
draw something of their imagination
here's an imaginary congress site being
畫下他們的想像。
這是他們幾個月前畫出的想像中的國會網站。

76
00:04:33,649 --> 00:04:34,228
drawn

77
00:04:34,228 --> 00:04:37,789
couple months ago
and when you have something in drawing
一旦你畫出一些東西

78
00:04:37,790 --> 00:04:42,330
people can turn that into actual kind of
fake website with fake
其他人可以把它轉變成網頁實品

79
00:04:42,329 --> 00:04:47,050
data but like a almost working website
and there are people who can put real data in it
用的暫時是虛構資料，但是個會動的網頁。
然後又有另一群人能夠找出真實資料放上去，

80
00:04:47,050 --> 00:04:51,020
so it's like a a like open source
project developing
所以這就像個開放源碼計畫

81
00:04:51,019 --> 00:04:55,609
asynchronously
平行發展中

82
00:04:55,610 --> 00:04:58,720
so it also goes the same for design
process
設計過程也是一樣

83
00:04:58,720 --> 00:05:02,840
and on the left you can see the first
revision of our logo is really ugly
從左邊這張圖，你可以看到我們的第一版logo有夠醜

84
00:05:02,839 --> 00:05:06,769
and some designers thought oh this is too
ugly I have to make it better
一些設計師看的覺得：噢，醜不忍賭，我必須改良它

85
00:05:06,769 --> 00:05:10,620
so here's a tip for people to contribute
to your project community
所以，吸引他人對你的計畫或社群參與及貢獻的撇步就是：

86
00:05:10,620 --> 00:05:15,610
make typos in document and make really
ugly logos
在文件裡打錯字、畫很醜的logo

87
00:05:15,610 --> 00:05:19,319
and it's important because you attract
people to contribute  they are now part of
吸引人來貢獻是很重要的
因為他們成為此社群的一份子

88
00:05:19,319 --> 00:05:20,538
the community

89
00:05:20,538 --> 00:05:24,159
and their names are  listed in the contributors
so they don't want to see this
他們的名字被列為貢獻者
所以他們不想看到這個計畫最後失敗

90
00:05:24,160 --> 00:05:28,130
project to fail

### 91

00:05:28,129 --> 00:05:31,409
So we've had like about 30 projects
我們目前大概有30個專案

92
00:05:31,410 --> 00:05:37,280
so far and they're very diverse and all of  them are open  source.
它們非常分散，而且它們全都開源

93
00:05:37,279 --> 00:05:40,909
The important idea for this to work
is that,
讓這件事可以運作的一個重要概念就是

94
00:05:40,910 --> 00:05:44,120
it is a similar idea how the internet  was built today.
這個概念類似於現今網際網路建立的方式

95
00:05:44,120 --> 00:05:48,129
We roughly  know that there's a idea
我們有一個大略的想法

96
00:05:48,129 --> 00:05:52,168
somewhere we want to reach,  there's a place we
want to reach, but we don't know exactly
某個我們想到達的地方，一個目的地，雖然我們還不很確定

97
00:05:52,168 --> 00:05:57,310
we have had a rough consensus that
we want  a more open government
但我們有個概略的共識，我們想要一個更開放的政府

98
00:05:57,310 --> 00:06:00,860
But more importantly, we have running
code.  We have working prototypes
更重要的是，我們擁有運作的程式碼、會動的雛形

99
00:06:00,860 --> 00:06:01,910
for people to participate,
能讓人們參與

100
00:06:01,910 --> 00:06:06,020
for people to improve.  And this
is how the internet was built today
讓人們參與改進。而這正是現今網際網路建立的方式。

101
00:06:06,019 --> 00:06:09,839
There's no grand plan like we have to have
browsers and mobile devices
沒有一個像我們一樣的大型計劃去包含了瀏覽器和
移動裝置

102
00:06:09,839 --> 00:06:13,060
they just happened along the way.  So
他們就是一路上各種不斷發生演進的結果。

103
00:06:13,060 --> 00:06:16,829
in summary g0v is pushing toward
open government
總的來說，g0v用開放資料推動開放政府

104
00:06:16,829 --> 00:06:20,439
with Open Data, or if that data is not open we
try to liberate it,
或者如果遇到不開放的資料，我們試著讓資料可以自由流通

105
00:06:20,439 --> 00:06:24,060
and talk to the data  owner nicely
about opening up.
並且與資料擁有者做開放的溝通

106
00:06:24,060 --> 00:06:27,879
And this is run as an open source
community.
它的運作的方式就像開源社群一樣

107
00:06:27,879 --> 00:06:32,069
So, what's next?
所以，下一步是什麼？

108
00:06:32,069 --> 00:06:35,389
In 2008, when Iceland was badly struck by
在 2008 年，當冰島被金融危機重重的傷害

109
00:06:35,389 --> 00:06:38,439
the financial crisis, people raged
民眾非常的憤怒

110
00:06:38,439 --> 00:06:41,689
and then this people demand a new constitution.
於是他們的人民要求要制定新的憲法

111
00:06:41,689 --> 00:06:45,978
And the Prime Minister accepted that.
Okay, we need a new constitution
他們的總理接受了。
好的，我們需要新的憲法

112
00:06:45,978 --> 00:06:49,068
and that new constitution should be drafted
by the people
而且新的憲法應該由人民來起草。

113
00:06:49,069 --> 00:06:53,729
so they have a national assembly of
1,000 randomly selected people
於是他們隨機選了一千多位民眾組成了國民大會

114
00:06:53,728 --> 00:06:56,879
to decide how constitution should be drafted.
去決定憲法應該如何被起草。

115
00:06:56,879 --> 00:07:01,848
And there was a national election of 25
committee members.
而且還有 25 位委員會的成員。

116
00:07:01,848 --> 00:07:05,029
They are responsible for collecting public opinions
他們負責從公聽會以及網路去蒐集公眾的意見

117
00:07:05,029 --> 00:07:08,098
from public hearing and from the internet

118
00:07:08,098 --> 00:07:13,089
so at the end they drafted a version of
constitution that was approved
最後他們所起草的憲法在 2012 年經過公投通過

119
00:07:13,089 --> 00:07:16,959
by referendum  in 2012

120
00:07:16,959 --> 00:07:21,029
And once this constitution is ratified by
Icelandic parliament, it will be the first constitution  that is
一旦這部憲法被冰島的國會核准的話，它將會是第一部

### 122

00:07:22,089 --> 00:07:25,529
drafted by the crowd and on the Internet
由群眾在網路上撰寫的憲法

123
00:07:25,529 --> 00:07:29,489
similar things are happening in Finland
where they have a new offroad
類似的事情也發生在芬蘭

124
00:07:29,490 --> 00:07:34,090
traffic regulation and
they're collecting opinions before they
當他們要制定新的雪地越野交通法令之前
他們從公眾蒐集意見

125
00:07:34,089 --> 00:07:35,029
make the law

126
00:07:35,029 --> 00:07:38,179
from people so they collected about 100
所以他們蒐集了約  100

127
00:07:38,180 --> 00:07:42,340
submissions of proposals and thousands
of comments
份提案書以及數以千計的意見

128
00:07:42,339 --> 00:07:46,668
and so things happen this way
so we can see that the technology is
因為這些事情的發生，我們可以看到科技

129
00:07:46,668 --> 00:07:51,149
not just allowing us to are socially
sponsoring interesting project on
不只是可以讓我們透過社群在kickstarter贊助有趣的專案

130
00:07:51,149 --> 00:07:52,448
Kickstarter

131
00:07:52,449 --> 00:07:55,788
or renting out your spare room on airbnb
或者把你多餘的空間租給 airbnb

132
00:07:55,788 --> 00:08:00,560
it's also changing how policies are made
科技是可以改變政策制定的方式

133
00:08:00,560 --> 00:08:04,319
so I wish you take this back
我希望你們把這個想法

134
00:08:04,319 --> 00:08:07,620
to your country,  try to open up
your government
帶回你的國家
試著讓政府開放

135
00:08:07,620 --> 00:08:10,930
and because compared to the examples mentioned
正因為和前面提到的例子相比

136
00:08:10,930 --> 00:08:14,389
previously, democracy in Asia is
民主在亞洲

137
00:08:14,389 --> 00:08:18,918
rather young, so we need to work together
and that's why we started
算是相當的年輕
因此我們需要彼此合作

138
00:08:18,918 --> 00:08:23,370
g0v.asia, hopefully we can have open government community
這就是我們成立 g0v.asia 的原因
希望我們可以有一個開放政府的社群彼此合作交流

139
00:08:23,370 --> 00:08:29,759
to work together
so this afternoon we will have an exchange session
在下午我們會有一個交流的議程

140
00:08:29,759 --> 00:08:33,028
and you welcome to post comments and ideas
歡迎你把意見或想法

141
00:08:33,028 --> 00:08:36,189
on [http://g0v.asia/mad](http://g0v.asia/mad)
張貼在 [http://g0v.asia/mad](http://g0v.asia/mad)

142
00:08:36,190 --> 00:08:36,870
thank you for listening
謝謝各位的聆聽






