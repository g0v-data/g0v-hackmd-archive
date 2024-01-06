---
title: "Meeting Notes 2015-01-12 (TODC)"
tags: Open Data,外交,hackpad
---

# Meeting Notes 2015-01-12 (TODC)

> [點此觀看原始內容](https://g0v.hackpad.tw/R4w7Sd5Ti46)

This document is CC BY 4.0 [https://g0v.hackpad.com/R4w7Sd5Ti46](https://g0v.hackpad.com/R4w7Sd5Ti46)

Location: Hope Bay Technology, Neihu, Taipei
Participants: pofeng, whisky, ben, au, tonyq

### 緣由

這是由 ocf.tw 開放文化基金會、和沛科技、國發會進行的會議，由於與 open data 相關，因此秉持公開透明原則，製作全程文字紀錄並將 hackpad 放在 g0v 的 workspace 底下，供社群參與者參考。[詳情見 pofeng 的說明](https://www.facebook.com/groups/g0v.general/permalink/743116359098106/?comment_id=743390535737355&offset=0&total_comments=39)

Tentative architecture (subject to revision):

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_3699980b71b9c3c4a3d8845c1f5ef712)

Second revision, per NDC's feedback:

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d0dde5e1fabc23f5564c3aeffaf951dd)

### Preamble


ben> (off record) briefing about initiation and preparatory efforts on gathering the initial fund of this effort.
au> demo: EY training, vtaiwan.tw, hackathon in gov (now shifted to off-site facilities), [data.g0v.tw ng](https://g0v.hackpad.tw/Data.g0v.tw-ng-LA2MpOEjraI)
ben> (off record) debriefing of Simon and Terry’s previous discussions.

### Discussions


tonyq> I’m working in Jaclyn’s office as consultant as of this week.
pofeng> Current process is that gov.tw cherry-picks data into structural open data, so if there is a central archive, there is no implicit exclusivity. All we need is a well-known API that other participants can join.
au> I can help designing the API, no problem.
pofeng> I have a few concerns though:
- OCF.tw needs auditing and financial effort to get more than 10M in funding
- What is the timeline? If due in less than two months, then a new foundation is not likely possible.
- For Tax purposes, we need to spend more than ~70%~ 60% of funding, so if there is a new foundation next year then we need to sign a preparatory contract for fund transfer.

ben> the sponsor’s consensus is that I’m the trusted manager of this NTD$5M-per-sponsor fund.

pofeng> the difference between donating-for-credit versus selling-for-credit; for tax purposes it is different.

ben> selling-for-credit of access is fine.

pofeng> as long as the output is open-source then it is worth it.

ben> NDC will push data in well-known format into an archival house; it’s just we establish a new prototype for it. Foundational effort takes care of the data center, including rental of VM (standard OpenStack hosting fees, with educational and NGO discounts).

ben> unstructured data is fine, but we of course prefer structural data. the data structuring effort performed here can also get its own credit.

pofeng> the API interface, the receiver, needs to be open source.

ben> NDC will be pushing, we do not need to pull.

pofeng> as long as all involved software stack as well as web is OSI-compliant, I’m OK about it.

ben> we just need a well-known FTP-like metadata and data convention for NDC to push into it. we need a full-text search engine, with standard warranty and disclaimer.

ben> as for publishing and working on government data, how the participants get credit, needs a structural design.

whisky\> NDC will open up the API; they just want to build a catalog instead of maintaining its own mirror. however all local governments start to host their own data, instead of pushing — there’s no easy way to get exclusivity.

ben> per-5-minute pushing, can NDC take up this much bandwidth cost?

whisky\> they are already prepared to absorb the cost.

ben> yeah but that will be in 2016.

whisky\> yes so for 2015, you can make this effort as a prototypical pilot, but in 2016 there’s no prevention for NDC and other agencies and run through ZTHY’s portals. currently it’s a meta-data read-only mindset.
> ZTHY 是什麼意思啊？網路找不到
> [name=Muyueh L]

> _資拓宏宇_
> [name=Audrey T]

> 感謝感謝
> [name=Muyueh L]


ben> if ZTHY claimed this work but cannot deliver this, I won’t give a damn.

whisky\> I bring up metadata because NDC’s metadata is very unpolished; the data cleaning up service is very much where the most efforts are. NDC’s own data may have 3-star quality, but the main effort will be in cleaning up in local agencies.

au> getting officials to use metadata-aware process is crucial.

pofeng> how is NDC’s gathering process going on?

ben> NDC’s folks will be here shortly and we can check with him.

ben> we are not talking about agencies publishing the API, but raw Database and Tape Archival of all EY agencies. Local agencies may choose to use the same archival process, but of course we can only suggest.
> EY 是什麼意思啊？
> [name=Muyueh L]

> Executive Yuan
> [name=Chiao J]

> 感謝感謝
> [name=Muyueh L]


tonyq> so EY is a showcase for local governments.

ben> it’s a race between Mao and Ko actually.

whisky\> filtering process?

ben> technical metadata: all DB SQL schema is to be published first. privacy and secret-level fields are to be deliberated, but by NDC in a public forum instead of the Archive.

au> so anything passed off the firewall is already clear of identifiable information?

ben> yes.

tonyq> actually, each agency’s SQL schema differ wildly. so this platform is a good way for participants to contribute converters.

pofeng> we can do training course on structural data. how quick do you want commitment?

ben> we want to tell NDC “there is a foundation for this”. of course funding won’t arrive immediately. but why chairperson Pofeng voted _against_ this proposal at first?

pofeng> because we lack the staff power for it. this is originally our plan for 2016, and 2015 is really too early.

ben> the location of OCF needs to be in Taipei.

pofeng> it’s Bureau of Culture’s Taipei City foundation.

au> CL and NDC had previous discussions, but today I cannot speak for CL, just architectural references.

au> (demo of archive.org structure.)

ben> archive.tw Foundation?

au> OK. (registered the domain)

pofeng> any recommendation on accountants?

ben> no worries; I’ll sort this out.

pofeng> …and we need full-timers for this.

ben> at least 2-3 full timers are needed.

pofeng> for 2015, if this is in OCF’s task force, then would 3-5 representatives be too many?

ben> that's plenty if it's a task force to get things done.

ben> tonyq, can you get off-hook from Jaclyn’s efforts to work on this instead? or at least recommendations?

au> ronny has [http://data.g0v.ronny.tw/](http://data.g0v.ronny.tw/) and may be interested in technical consulting, if not full-timer.

whisky\> OpenFoundry has a team already versed in open data hosting.

ben> how large should the team be? I think 10 is not too much. the funding is plenty.

whisky\> also muyueh with [https://sheetdb.com/veggie.muyueh.com/](https://sheetdb.com/veggie.muyueh.com/) has previous experiences on presentation and delivery of semi-structured data in structured fashion.

pofeng> we just need a head for this effort, for both Tech and PM. I’ll get contact with PM candidates.

ben> what’s the fallback?

pofeng> whisky?

whisky\> (uncommitted)

tonyq> I would like to work with NDC and agencies as the gathering and structural consultant.

pofeng> OK we have a volunteer!

ben> we can start with already-open data from data.gov.tw and data.g0v.tw as the pilot, and work on privacy and de-identification later.

tonyq> what are the risks?

ben> just our reputations.

pofeng> I worry about my clinic’s tax records… (lol) anyway the Steering Committee is my idea of reducing political risk.

tonyq> I don’t really care about my career this year or anything.

ben> This is the right time. Mao has buy-in, and I actually helped Simon… (off record)… so it’s very likely to succeed. the data catalog as brought up by tony will be resolved and is critical.

pofeng> the largest risk still lies in the execution.

ben> Folks in NDC has a more open mindset as they did not go through the normal career-ladder.

whisky\> deliverables?

ben> by March, data.gov.tw’s metadata needs to appear on archive.tw. then the filtering engine’s process needs to be up for public deliberation.

tonyq> catalog is first priority, as well as most of data that does not require filtering.

tonyq> for kptaipei, the unofficial website actually has very few data set in term of quantity, but the process and quality is more of a useful PR value. this is more important than raw quantity.

ben> media strategy is another matter.

whisky\> NDC’s update interval?

au> (demo) 3du’s [consensus with terms.naer.edu.tw](https://g0v.hackpad.tw/ZFtVX8RAqjK) on exporting in sql.gz format.

whisky\> can we collect from edu.tw directly instead of going through ndc?

ben> sure, as long as they use the same endpoints as NDC, agencies can bypass NDC’s cataloging pipeline and write directly into the filtering process.

au> confirmed? then we are changing the diagram here.

pofeng> medical cloud and national palace museum are somewhat counter-example here, which raised TAHR’s attention, even ended up in a lawsuit. so this is why “release for research purpose” term is added. I feel somewhat responsible for this and will work with medical workers on this purpose.

au> yeah, one-way functions on national ID really need to be used as one-time uuids if one wants complete anonymization.

ben> but then we don’t have foreign keys anymore.

au> that’s TAHR’s main position actually.

pofeng> anyway their current proposal is double-hashing. this is very contentious. so we’re leaning on opt-in.

au> opt-out policies needs a full deliberation process before committing on anything. this is part of why we’re working on vtaiwan.tw.

pofeng> arranging 1:1 meeting time with PM candidates.

ben> (checking schedule) I’m fully booked during daytime.

au> perhaps asynchronous telecommunication?

ben> OK. here’s my phone number and contact details…

pofeng> shall we call ronny now?

au> maybe after PM commits? ronny has PoCs ready and so we can work out details once the system flow is determined.

whisky\> can we work on application package (sandboxed apps running on archive.tw) here?

au> is ben’s team working on Kubernetes support?

ben> no, just OpenStack stuff.

whisky\> google has acquired an UN data visualization team.

tonyq> our expectation of gov is rather different — ben and I would like to work from inside to get all data out, but whisky would like to see them as a partner.

ben> my expectation of gov is just for them not to block citizen’s process.

pofeng> so OpenFoundry actually closes on end of 2015 not 2014, but it’s still OK to talk with PM candidates.

pofeng> e.g. [http://drugs.olc.tw/](http://drugs.olc.tw/) has received data retraction requests, so our catalog’s revision needs to be fast enough that pulls it down in case of emergency.

au> among Ben’s 8 ideas on FB page, there is only one that is most impractical: “3b. 立法明定：只要有適當之錯誤回報及修正機制，政府人員對過去資料之錯誤不用負行政責任” because damage caused by administrative data is still a judiciary issue.

pofeng> maybe if they provide it for free, one can sign a waiver to not sue government?

au, whisky\> that does not preclude damage.

ben> actually I explicitly said “行政責任” as waiving administrative responsibility, not 刑事 or 民事...

whisky\> yeah but that does cause a chilling effect when brought up (e.g. TAHR’s case).

whisky\> open data in the current quality cannot be value-added, it needs massive cleaning up and structuring efforts.

ben> so this is a challenge. the archive needs to provide forked/cleaned-up revisions from the public.

whisky\> so gov is no longer the only “canonical” source in this view, as we need to establish a culture that says errors is normal.

whisky\> so we need a 行政命令.

pofeng> 函釋 doesn’t need to bring to LY and may be even faster.

tonyq> ben’s plan calls on agencies to unconditionally backup, this is prone to encounter resistance.

au> but that is ben’s plan’s key point. my point is that EY agencies are not using metadata-aware tools to produce content, and so if you forcibly collect data, all you will get is unstructured data.

tonyq> e.g. in taipei.gov.tw, they say “we can open all data but we don’t know the meaning or schema of this”. so my position here is about removing obstacle.

au> this calls for CfA-style ambassadors into agencies if we need structured data.

pofeng> tonyq, are you really willing to amass this team of ambassadors?

tonyq> this is Jacylin’s plan for me actually, as an IT fellow for the entire EY. I’m not exactly sure I’m fit for this role yet — it’s a rather heavy burden.

au> already suggested unstructured-data checking fields to NDC.

whisky\> how to pull back patches and forked versions in a structural way to NDC?

au> directly read-back to agencies can’t be done in a forced way, but we can provide support materials.

ben> updating diagram to include contributing-back policies.

### Action Items


- HR — Personnel (pofeng)
    - PM candidates
    - posting on g0v hackpad (au - done)
- Funding and Structure (ben)
    - Ben is in charge of overall direction
    - Implementation needs PM and Legal and Dev personnel
        - yhsiang mentioned would love to lead the Dev team ( [http://logbot.g0v.tw/channel/g0v.tw/2015-01-12/145](http://logbot.g0v.tw/channel/g0v.tw/2015-01-12/145) )
        - wildsky mentioned would help the front-end part ( [http://logbot.g0v.tw/channel/g0v.tw/2015-01-12/151](http://logbot.g0v.tw/channel/g0v.tw/2015-01-12/151) )
        - suensummit mentioned would love to in the Dev team ( [http://logbot.g0v.tw/channel/g0v.tw/2015-01-12/164](http://logbot.g0v.tw/channel/g0v.tw/2015-01-12/164) )
- Licensing
    - All user-and-operator visible products of this effort are to be OSI-compatible open sourced and developed in the open.
    - User-visible processes, if patentable, needs to be granted non-exclusively in the usual fashion.

## 與國發會討論記錄

翟：由國發會和一組開放資料專長的人來做這個工作，所有資料在 storage 上面，用一個 ftp 之類的來傳輸原檔，接下來要怎麼用的人去設法。說實在如果沒有本領做資料轉換，你也沒有本領賺這個錢。一個人做好了，預設是放給很多人用，這是沒關係的。不限定這個基金會，開放給所有有意願的。

裡面的架構剛才 au 有提到跟 archive.org 一樣，我也是剛剛才知道。民眾可以選擇 copy 資料回去做他的事情，但有時頻寬很貴，他只需要一點東西，可能在這個平台上租個 vm ，自己動手做就好了，不用 copy 回自己的機器上。

然後基金會這邊會雇用專人來做這件事情，政府單位要找有專長的人進去比較難，制度比較沒彈性。有基金會來做，如果找不到適合的人或沒有錢，可以由基金會處理。我們找到這些企業願意出錢來做這件事情。

一方面響應政府，另一方面這邊有開放資料社群，讓政府開放給社群而不是發包給廠商，他們也比較舒服一點。

高副主委仙桂：副院長就任以後非常積極推動開放資料這件事情，跟郭董見面後，提及本案，就請我們趕快來。目前開放資料的業務，是由國發會簡處長來推動，政府推動開放資料很多年，這次希望能以破釜沈舟的決心來推動。目前我們讓各部會進行資料的全面盤點。

目前國發會將制定資料開放的 guide line。副院長會督導這個計畫，發揮更大的綜效。尤其民間團隊可以來參與的話，效果會更大。

簡處長：國發會找的廠商只有建置 data.gov.tw 跟訂立規範。我的想法政府應該是要把資料做好，把標準訂好，之後標準怎麼實作應該讓民間來做。我個人認為政府不要做這些。第一版來做，嘉良就說可以複製一份，我覺得都是 ok 的。

data.gov.tw 有分階段，第一階段是資料先上，我們是 portal，資料還是在各部會。我們參考國外服務有比我們還遠的想法，我邀請他們來台灣，瞭解他們如何鬆綁法規的部分。

有一塊是民間資料該怎麼進入，我認為開放資料不只開放政府資料，也要企業開放他們的資料，但他們願不願意的問題。

翟：有些問題是民間資料進入體制的法律體制。所以我們建立外部平台，沒有政府責任問題。

簡處長：目前是 dataset 概念，不是 database 概念，所以比較不會有過濾機制。我們最近要求各部門盤點 database，並參考國外狀況，應該還有很多東西可以放。

翟：應該透過管控預算來要求他們。

簡：國發會負責計劃審議，可以要求他們在計劃中必須規劃開放。但我們考慮到一個問題。沒辦法「不開放就不編列經費」，因為還有 legacy 系統的問題。

我們的想法是我們負責資料這一塊，未來 g0v 要怎麼做都是ＯＫ的。之所以建立 api 的理由，是 g0v  希望 machine 對 machine 來用。我相信基金會也是。

翟：我們想法有一點不一樣，就是你們推資料過來就好，不用開到 API。這樣對政府會省事，需要用的資料我們自己煩惱就好了。有時你開 API 還會有 file type 的問題。

簡：我目前參考美國或英國，open data 的網站，他們有幾種格式，是沒有障礙的存取。

翟：五顆星那些，我覺得一顆星給你我們也要照收。

au：一顆星就是有網址就好。萌典計畫跟教育部合作，目前[有談到以每天弄成 SQL 檔匯出](https://g0v.hackpad.tw/ZFtVX8RAqjK)  ，這樣其實對我們就夠了，也符合三星資料的標準。

簡：目前放在 data.gov.tw 上的都要求到 csv 以上，這也是我們傷腦筋的。以美國或英國，有 1/3 都是這樣。

副主委：不然我們可以分階段，先把社群需要的資料開放，再來改善資料的格式。

翟：我們覺得可以先用，最後可以把民間開放的東西拿回去用。

翟：我們也是分階段，是先通再來才是過濾機制。

簡： 過濾這邊有點 concern ，我們是 portal 不直接擁有資料，而是連回各部會。open database 這段目前不會要求，open dataset 比較是我們現在的主要目標。像我們要求交通部 open dataset 他可能是開放航空旅客數這種概念，而不會開放資料庫對外存取。

翟：過濾跟 mirror，主要是去識別化。每些資料集該怎麼處理。備份部分主要是避免各地自建磁帶機自建備份造成問題，而是統一處理。而且未來資料出去也容易控制。

簡：機關收集資料要有法規基礎，就算戶政資料他備份在我這，我也是不能收的。

翟：可以某些部會直接對外。

簡：如果有些資料可以開放，大多都可以放在我這。政府資料收集資料都是基於業務職掌，如果我沒有這個業務職掌，我就不能收了。政府機關避免自己避免 big brother ，所以有職掌管自己的事情。

翟：「委員會」都在國發會資料中心，但「部」不在，但是你還是可以協調處理。

au：國發會能做的就是降低層級數量，以各部會為主軸。

簡： 對，可以由部會自己處理。要由資料各級處理。你可能要面對十四個部跟一些委員會。所以你沒辦法中央處理，所以你要做辦法讓部會去實作，不能自己做。很多跨機關系統做法都是我們訂標準，我們訂標準讓他們跟。我們之前是有想過我們要不要做全國部會的 backup center。這是最節省經濟效益，但執掌是不 match 的。現在狀況是只要開放在我們資料集的都沒問題。

翟：現在是收集在國發會這裡，還是連回去部會？

簡：都是連回去各部會，我們只是 portal 。只要求他們 follow 規範。我們比較大困難可以分成三個，一個是法規限制，有些大方向可以但有些不行，像地政司資料（GIS）是有些法我們之前不知道的。那個就很難。像是有要求要 GIS 不能到國外，這就一竿子打死的。

另一個是部會本身不知道哪些可以開放，這他們需要清理跟處理。去年開始的資料我們都要求他們資料 default 必須 open，所以歷史資料才是真正的問題。但大家需要的是歷史資料。

第三個是品質，我知道 clkao 之前有在規劃界定品質的事務。我後來找了一個方法就是用 fusion table 畫畫看，能畫出圖的話就好了。所以我用 fusion table 去篩選，才發現很多資料有待改善。我希望他們能先用 fusion table 先篩選過。

前面都是技術問題，現在比較難的就是說，這些資料該怎麼開放。

TonyQ：我們是想把手伸進部會去...

翟：這樣說就不對了，我們是 "想為政府貢獻心力"。(笑)

簡：我們想把部會這件事情，課責到部會。這陣子我們要講這個責任回到部會，你不要跟我說你不能開放，你去跟你的 stakeholder 講你能不能開放。你在自己單位裡面去召集資訊單位，由內部的資訊長來 review 內容，讓部會負這個責任。讓社群參與到部會裡面去，協助資訊長 push 計劃，按季 review。

除了個資跟涉及國防機密的，都應該要開放：不收費是原則，收費是例外。收費部份好處理，是可以不收費的。規費法有很多除外條件。如果真的需要可以用私法契約，現在在擬授權條款，現在授權條款沒有像英國那麼強勢還在想要不要改。我們之前請律師做引起很大反彈，但那比較接近法律用詞。我是想用 CC 但有些部會有意見，但目前**法律沒有阻礙開放資料**。

au：以前 CC 3.0 有些問題（準據法、資料庫權），後來 CC 4.0 都可以處理。

簡：Content 部份，翟提到用公開競標的方式，像是故宮這類的。之前有人說要調降解析度，但那樣沒什麼效果。我們有舉國外博物館為例，但故宮說那是少數，整個博物館界都還在觀察。

au：g0v 年會衝突性的討論後，我的想法是以CC架構，以開放為原則，不開放為例外的話，是可以不開放的啊，故宮很不想開放的話，由他們提出不開放說明書，再用 BY-NC 或 BY-ND 也是符合 CC 框架的啊。

簡：這部分（CC 框架的推動）也是政府要做的。

au：NC 跟 ND 都不是開放資料，但沒有人說我們不能拿，沒有人說我們不能放。

簡：剛剛只是說明架構，我覺得 FTP 是可行的。

翟：PUSH 很簡單，你有 list 。

au：我有提意見給國發會，包含 PDF ，excel ，word ，只要是網站能下載的資料，希望能做一個機制是讓他們打個勾讓他們說他未結構化。

簡：我很要求要三星以上，因為PDF 會跟資訊公開法扯在一起。資訊公開法有規定「應公開事項」。我想說我要做的是開放資料，所以我以結構化的方式來要求部會。

au：PDF, Excel XML, Word XML, SQL 都是 ISO 標準，所以是第三顆星（不限定閱讀軟體）符合，但第二顆星（內部具有資料結構）的部份就很凹...

簡：我們都可以加。

副主委：我們能不能分兩個 stage？

au： 以前 OOXML 不是 iso 標準時很難推，2007 就是 iso 標準。

簡：確實是這樣，這樣量就衝上來了。

TonyQ：重點是開放之後有沒有用，會不會給局處帶來麻煩。已有網址的未結構化資料反正已經上網了，顯然是最沒有問題的。

陳科長：希望修改著作權聲明，從「預設限制」改為「預設授權」。以政府資料開放授權的規範，更新網站版權規範。我們在網站上看到的資料，除了涉及第三人著作權，不然 default 該授權公開。我們希望是雙軌能讓各機關現有在網站上的東西。讓他立即就是開放，所以當時我們才沒有要求他們一星二星來開放。

au：docx , pdf , xlsx 是符合第三星的。

簡：盡量採用標準的格式。

au：微軟會有 office xml 就是他被各國政府逼的，從 libreoffice 後，這兩個轉換已經不太會掉資料了。我之前才在跟 [OfficeShots](https://nlnet.nl/project/officeshots/) 做這塊資料的確認，應該是沒問題。

簡：odf 是國家標準，但 ooxml 只有一部份是國家標準。

au：xlsx 可以用 libreoffice 轉開放資料。

陳科長：有兩件事情，新建計畫要採用這些資料格式，現在的問題是既有資料該怎麼處理。

whisky：像是科員分不清楚 utf-8 跟 big5 之類的。

au：三星開放ＯＫ，二星結構化可能不完整，但就是上傳上來讓社群補完。讓他們放上半結構化資料，我們來補完。

pofeng：放出來是簡單，民間的 argue 意見其實沒有那麼大。

簡：有關 pdf 跟特定格式我們希望帶回去想，再做回覆。

TonyQ：這兩年來，我們的期待是政府來學習社群的做法，讓你們把未結構化的資料放出來，由社群做結構化的建議，這才是我們想要達到的中期目標。

pofeng：而且從基金會出來的衍生作物**都不會有授權問題**。
> 我好像不是樣講 \*笑\* 但是我也忘了我插了什麼話,  *大笑*
> [name=Pofeng L]


簡：我覺得這是一個好機會來做：野生官網、實際介接的這兩個實務案子。

TonyQ：現在就是把存儲和 review 機制 case by case 來取得。

簡：誰對口？

翟：這部分基金會，會讓柏鋒放在開放文化基金會上，會聘請一個小組人員來真正動手處理這問題。開放資料放進來就會有 storage，想用的人可以開 vm 來用。另外一個是修正跟意見的討論。我想問一下 facebook 現在不好用，是不是需要自己的開放資料討論。

翟：政策制定以往是發包給某些法人去寫，現在希望擴大參與，因為目前會去政府網站參與的人很少。所以我們希望民間來做管道跟進去這邊。facebook 要討論這些比較困難，有很多問題。

au：gitbook 和 discourse  組合就是 vtaiwan。只是缺永久儲存，今天是來談這個。

簡：我認為 data.gov.tw 由政府維運只是短期的，未來應該由民間社群維護。我當初設定維運時間是五年。這五年間政府往下，社群往上。我想談的是蠻 match 的。

TonyQ：現在主要是部會，會不會排斥提供這十五個遵循標準的主列表。量會變大嗎？

簡：如果以三顆星的話，現在並不多，但把 PDF、ODF(OOXML)、SQL 加進入就很多了。

TonyQ：尤其是 SQL，請把 Column 直接提出來。

pofeng：COSCUP 產官學宅四界座談時的共識就是這個。

簡：部會內部對於機密與否的認定是一個問題。

TonyQ：資料欄位的後設資料不能說是機密吧？

簡：在我的立場，東西是要公開，最近的盤點是還好，但公開盤點結果需要時間。

pofeng：基金會就是殼子，能不能接還要等 clkao 做最後決定，我們有個共識是任何人都可以接，不要說成我們是私下收受這樣，這樣出去比較好講。

翟：事實上我提出來的時候郭台銘就說「我們來弄一個，搞不好三天就弄出來了」。我們討論之後，就說鴻海自己來做，會來的人不多。

簡：我們的態度都沒有變，已經在 data.gov.tw 上的資料，都可以開放複製。

pofeng：我們希望強調這個介接不是特許的，是任何機構任何人都可以申請介接。然後，萬一如果有其他人來質疑 ocf.tw 的角色，我會說這以後會有執行委員會，由翟博來統籌。另外要提醒基金會的執行細節，如果 Ben 成立新的基金會, 會至少有五百萬不能動 (補充: 要放在定存不能動)。來我們這邊就是錢要隨便用都行，但就是要~七成~六成內一年用掉（防洗錢，不然 17% 稅率），所以錢要處理好。不然就要繳稅。

簡：我們態度就一向是大家都可以用。

pofeng：其實 g0v 已經是第零個了（data.g0v.tw 介接），所以要強調「對不特定人開放」。

簡：我有要澄清一點，我們要建置任何系統，都必須公開招標... 廠商也被 push 的很慘。不管是誰，只要這裡要改系統，總是會有得標者。從 FTP 的目錄標準開始是很好的。所以是誰會把初步的目錄標準跟我們接頭？

翟：看來就是我了。

簡：行政責任免除的部份，可以加一句「以正式資料為主」。針對敏感資料，要加上時間戳記，但原本的技術架構並沒有，像實價登錄那邊，也是牽涉到許多法規的修改。

TonyQ：敏感資料，像是名牌查地建號查戶藉住址... 業務可以拿這個去做額外有風險的利用。

翟：所以才要有之前提 vTaiwan 這類的討論方式，讓人可以從目錄及後設資料，指出資料集的可能風險。

簡：我們最擔心的就是資料鏈結之後的這類問題。

（柏鋒和 whisky先離開。）

### Action Items

- 簡：三星標準和盤點標準檢討，回應給 au [到 g0v hackpad](https://g0v.hackpad.tw/Data.g0v.tw-ng-LA2MpOEjraI)
- au：確認 vTaiwan 架構可以套用在目錄及後設資料的主題上
- 柏鋒：確認人事
- 翟：確認初始資金

