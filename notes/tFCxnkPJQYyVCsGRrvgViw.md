---
title: "開源之道 2015 場外 Q&A 之一"
tags: hackpad
---

> [點此觀看原始內容](https://g0v.hackpad.tw/boSpHWmBebf)


聽完 [Audrey Tang](https://g0v.hackpad.tw/ep/profile/HfWHMi7irO5) 的「開源之道 2015 」後，冒出一些問題，雖然私下詢問得到了回答，但是答案對同行同好朋友們應該比對我更重要，經過講者同意後整理如下。下次會直接開共筆整理問題。

### 大部全文（去掉不是問題的部分）


_caasi:_
聽完演講還想起你常提到「空間」。把軟體看成線上人們互動的空間的話，讓我想起 patterns ，不是語言的 design patterns ，是建築的那個。
有緣看過簡短版本的「模式語言」一書，現在想起來，裡面提到的 patterns 多半是讓建築可以與人互動，或者讓人與人互動得更好。
像是在狹窄的通道或樓梯間後，突然有扇可以看到戶外風景的小窗，或者怎麼安排建築好讓社群比較容易進行建築師期待的互動之類的。
這樣看來，雖然軟體的設計模式受到建築的模式語言影響，卻多是解決特定問題，甚至暴露語言的缺點
有沒有人從你說的「空間」還有人與人互動的角度，談軟體設計呢？而這個部分，是不是也有一些整理出來的 patterns 了？這似乎比侷限在特定語言上的 design patterns 更有用。

_au:_
空間 (Space-based communities) 是朋友 Stefanie Wuschitz 到印尼領悟出來的博士論文，概述 [http://www.slideshare.net/autang/the-sunflower-movement-online-communities-governments-transparency/57](http://www.slideshare.net/autang/the-sunflower-movement-online-communities-governments-transparency/57)
(全文 [http://www.slideshare.net/autang/wuschitz-dissertation-ss2014](http://www.slideshare.net/autang/wuschitz-dissertation-ss2014) )

caasi 表示_先看 introduction ，深怕吃不下_

_au:_
這不是很容易喫，畢竟 Metalab 是 Hackerspace / Makerspace 的源頭，然後這份論文等於總結了它的過去和未來可能
如果互動應用在軟體上，一般會是從 UX 開始談吧？人與人的話，之前看過一些 SxD "social interaction design"

_caasi:_
上上次的萌典松 RS 曾說，他覺得軟體業比起法律還不能說成熟。因為法學會有法律哲學可以變成立法的原則，但軟體業要討論實作的好壞不太有這樣的指導原則。我想我是斷章取義，但 UX 這點也讓我覺得對比建築，軟體也許也是不成熟的。

_au:_
這次原本想講但沒講的 Agda/Idris 就有點像用數理哲學作軟體的原則
但是生態圈要成熟到可以講可能還要五年吧

_caasi:_
Agda XD
先用 Agda 證過重要的商業邏輯，再開始實作應用程式嗎？ XD

_au:_
是，DARPA 的幾項無人飛行器專案就是這樣做的
然後跑在 seL4 上

_caasi:_
這，真是意料之外的消息，而且我不會質疑你的話所以會開始查。這個說出來沒關係嗎？

_au:_
都沒關係啊，是公開知識
目前的 chain of proof 還不是 self-hosted agda
詳細的 chain 見 [http://www.darpa.mil/program/high-assurance-cyber-military-systems](http://www.darpa.mil/program/high-assurance-cyber-military-systems)
可以看到  Galois 以外的 team 還在用 Coq 和 Java，而 Galois 的無人機的底層大都有 open source

_caasi:_
開始聽不懂了，讓我求助一下 google XD
seL4 那個 jserv 聽到應該會很開心，可惜跟他不熟不知道他是不是早就知道了。（沒 follow 他的課程）

_au:_
jserv 開了 issue #1 應該是台灣最早知道 seL4 open source 的人 [seL4/seL4#1](https://github.com/seL4/seL4/issues/1)

_caasi:_
XD 太酷了，小小世界...

