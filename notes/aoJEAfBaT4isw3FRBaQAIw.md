---
title: 2021.07 個資刪除請求紀錄
tags: log, 紀錄, slack-archive
description:
---
# 2021.07 個資刪除請求紀錄 (2)


timezone UTC+8

紀錄截止時間： 2021.07.30 08:41 PM

:::info
The back messages are directly copied and pasted from Slack interface, plus manual edits on threads.

###### Format
`Name` `time`
`Message`

> `Quotes, or threads`
> > `Quotes in threads, or quote of quotes`
:::

## #general

### 2021/07/31

ronnywang  7:56 PM
@S.. 我有一個提案作法，想確認你是否可以接受。
你說有許多網站利用我的 API 建網站放廣告，目前雖然無法確定，但是我也不否認有這種可能性。（不過更準確的說，假如那些網站真的用我的資料，他們用的應該不是 API ，而是匯出檔）
假如那些網站真的用我的匯出檔的話，一旦我停止提供檔案，那你的個資就會永遠停留在那些網站上面了。
我可以做的事是把匯出檔裡面人名的部份改成去識別化（Ex: 王向榮 => 王O榮、Ronny Wang => R____g  …)，假如那些網站是用我資料並保持更新的話，就會直接替換成去識別化版本（我有想過換成 ANNO001 的方式，但是假如外面那些網站發現我這樣改的話，可能會停止更新姓名部份，那你的名字就還會繼續在那些網站上）
company.g0v.ronny.tw 仍然不會做任何變動，繼續顯示原來的完整姓名，API 也不會改變（那些你不喜歡的廣告網站應該不是用 API 而是用匯出檔），這樣才能讓 company.g0v.ronny.tw 繼續有他原先的功用。
但我認為原始資料的姓名也還是有很重要的公共利益，因此我會提供另外一個大家可以申請下載匯出檔的機制，需要符合以下條件的人才能來申請有原來姓名的匯出檔：
要公開使用匯出檔的目的是什麼
如果是拿來做成公開服務的話，需要保證會定期更新資料到最新資料
成果需要開源
以上資訊（使用目的，公開服務或是報告位置，成果，下載記錄… ）我都會公開
細節的話也想跟大家多多討論，包括怎麼做姓名的去識別化，申請原始匯出檔要有的條件有哪些，怎麼避免漏洞

> S.  22 hours ago
Can someone translate to English? My Mandarin fails at some parts :sweat_smile:

> chihao:ocean:  21 hours ago
@S. I would find my own translator if I were you


> S.  21 hours ago
First of all, thank you for your hard work so far @ronnywang. I tried with available resources here to try to translate some parts to make sense of it. Let me be based on what I translated and what I investigated initially a few months back.
When you say "API" I am not sure which part of your service you are referring to exactly - so bear that in mind. There are public-facing APIs and private APIs. Same when you say "export". I see/name few different ways where I can "export" your website - pardon me, I am not as familiar with your project and naming convention you use as you are.
However, I would like to point out that currently, one way of scraping your website (there are multiple) by anyone, where you can access PII is by simply accessing this URL:
https://company.g0v.ronny.tw/id/[COMPANYID]
> Now, this is one way to scrape your data and I don't know exactly is this the exact way those websites utilize. What I do know for sure is that anyone who is determined enough can use this way to scrape the PII we try to protect.
So my first question would be - is this the part and endpoint you are referring to? And do you plan to safeguard this endpoint?
By "safeguard" I mean prevent bot/cyborg/human from obtaining PII (names in this case)? (edited) 

> chihao:ocean:  21 hours ago
safeguard against what exactly?

> Yi-Chung Dzeng  21 hours ago
I suppose he is mainly considering controlling access to the full dataset here:
http://ronnywang-twcompany.s3-website-ap-northeast-1.amazonaws.com/index.html

> S.  21 hours ago
@chihao I just edited and clarified what I meant.

> chihao:ocean:  21 hours ago
and why is bot/cyborg/human obtaining your name and your company name a bad thing?

> kjcl  21 hours ago
if you're not just upset about API access, but about scraping too, can't these scrapers just scrape the government website too?

> S.  21 hours ago
@chihao & others (including those who did not follow earlier)
**The problem:**
Currently, the PII can be accessed and downloaded via various endpoints/methods. Easy access = more ways for others to scrape, including bad actors.
**The solution:**
The bad actors are those we focus here on, but we don't have a way to distinguish/verify who has good intentions and who has bad intentions.
For that reason, we need to seek a method where we can provide the dataset without passively revealing PII - this is the foundation here.
The easiest way to achieve it would be through pseudonymization and in this case,
pseudonymization not just the export functionality, but any endpoint/method.
So why mask it across every endpoint/method? I see it counterintuitive if you pseudonymize only one part of the service (the "export" function) but leave multiple other ways where the PII data still can be accessed - including the endpoint I just mentioned above.
Now, before I get avalanched with thumbs down by all "open all the things!" & "corporates are evil" advocates here :D - pseudonymization of every endpoint **DOES NOT** mean that you can't run big data queries where you can do graphs and make connections between companies or even specific individuals. It would just mean that you can't expose this data passively in a programmatic or manual way.
What is left up for discussion/tinkering is the mechanism of how and when a person could request/access the data with revealed names - which is what most of the members here vouch for.
Because I think we should also focus on the fact that, you don't need the names of the owners *all the time*, you only need them at a specific time (if you uncover some shenanigans etc.). (edited) 

> S.  21 hours ago
@kjcl pardon for tagging you - please see above. Also, I am not upset about "API access", I am trying to find a way that gives people the transparency they want but also protects the PII from unnecessary abuse.

> kjcl  20 hours ago
feel free to tag me anywhere. i asked you not to contact me via DMs because I want to discuss things in the open with other community members, and I don't appreciate you posting private DM threads you've had with other community members publicly without their consent.

> S.  20 hours ago
@kjcl
> > if you're not just upset about API access, but about scraping too, can't these scrapers just scrape the government website too?
>
> Yes, I agree you could still go to gov website if you wanted to but:
A) fewer possibilities/websites to access PII = less PII abuse
B) I assume (I could be wrong) the websites that run ads won't be very hurt by not having the names of the owners, so not that suddenly they will resort to finding ways to scrape official gov websites. (edited) 

> S.  20 hours ago
@kjcl cool - I did that to defend myself from accusations you left personally on me that I mock someone's English abilities - that was never a case! Plus I did censored/redacted their nicknames. Now, back to the topic, shall we? :slightly_smiling_face: (edited) 

> kjcl  20 hours ago
@S. 我還是不太懂～ 如果你怕的是爬蟲的話，那爬蟲抓 ronny 網站的資料跟抓官網的資料的差別到底在哪裡。

> Yi-Chung Dzeng  21 hours ago
@S. Let me provide you with one use case, which may serve to justify the "when" and "how" to reveal real name - pseudonym connection would be "anytime" and "no restriction"
Say I read in the press that someone with name XXX is initiating investments in sector X. I wish to see how involved is XXX actually in the business, therefore I wish to know a list of all companies XXX is holding. After reviewing this list of companies and their board members, I start to wonder how many of these were his/her family members or were professional executives with big names in sector X, but all I can see is a list of psuedonyms. Deadend.
Therefore I hope company.g0v does not adopt your proposed solution.
> > B) I assume (I could be wrong) the websites that run ads won't be very hurt by not having the names of the owners, so not that suddenly they will resort to finding ways to scrape official gov websites. (edited)
>
> BTW, very wrong. I personally came across such sites, ~~because ronny's site was not the 1st in Google index ~~and perhaps contributed to the ad revenue and what I was looking for were exactly the names of board members and registration addresses. (edited) 

> S.  20 hours ago
@Yi-Chung Dzeng one solution would be to simply be logged in to see it. It's not a fool-proof solution of course, but much better than passively expose it for search engines and crawlers to scrape.
Well, I can't help when you want to find someone by their name. But you still have LinkedIn where every serious business owner has account.

> Yi-Chung Dzeng  20 hours ago
Are we seriously talking about embracing Linkedin rather than a easy access to commercial registry as the means for a concerned citizen to verify some facts disclosed lawfully? With the suggestion from a privacy-oriented person?

> S.  20 hours ago
I stated LinkedIn as an alternative - you may want to use it or not. Also, I am sure you know how to access websites in anonymous ways if you don't want to reveal your identity/PII. (edited) 

> chihao:ocean:  20 hours ago
So essentially “Why is it bad? Because there are bad people.” Who are these bad people? What can they do with your name and your company name?

> S.  20 hours ago
@chihao OK, long evening for me again.
>
> There are many reasons, a person - and here I would like to highlight - anyone, regardless of whether this is an owner of a company or natural person, might want to limit disclosure of PII
> - to prevent data abuse/misuse/misinterpretation - an avalanche of examples here including data selling, credit card fraud, deep fakes, revenge porn, etc.
> - if due to the nature of your profession - some jobs/positions require more security than others, you want to be more private online
> - if you have had your personal accounts hacked or security compromise
> - if someone is harassing you online and you want to limit their view of your profile or ability to find/contact you
> - If you have been a victim of blackmail
> - if you have concerns regarding the way a service/company handles your PII (e.g.: use it in a way you did not agree to initially)
> - some extreme cases (but do happen more often than you think): when someone's personal safety is at risk, eg. witnesses of murders and perpetrators being still free.

> kjcl  19 hours ago
@S. 我當然理解隱私資訊漏出的風險，但是我想理解的是你的名字跟你的公司這個關係在一個三方網站上對你來說是什麼明確的隱私風險？（要記得的是該資訊也存在政府官網隨便給大家爬。） (edited) 

> S.  7 hours ago (7/31 11:09)
Also I feel this is also something important when we are talking about potential solutions here and contributes to rejection of some ideas.
I see contradiction of values some members here stand for - specifically, the radical transparency you try to advocate:
> 1. Radical transparency is also answering to important emails when someone inquiry about their PII being used. If you don't answer them, the transparency is lost.
> 2. You reject an idea that the side requesting for data would need to be logged in or identify themselves - why wouldn't want to be identified? Isn't identifying yourself a way of being transparent with others too? Some countries require anyone who requests for PII to identify themselves and I think that's a fair exchange and definitely could deter bad actors.
>
> Bottom line: Transparency goes both ways, not just one. You want the transparency for yourself, but you don't try/wish to be transparent when not convenient or when your identity is at stake. (edited) 

> chihao:ocean:  7 hours ago
I know you think you’re making a point but you’re really not…

> kingman  6 hours ago
我認同透明是雙向的概念
這可以在以下兩點見到：
> 1. "台灣v.s中國：脆弱的民主"這部紀錄片中唐鳳被拍攝時的雙向拍攝紀錄行為
> 2. 疫調輔助平台會紀錄個資調用，個人也可以查詢誰調用過得紀錄。
>
> 另外社交距離APP承諾的開源、以及為何要開源，也是類似的概念吧。
> "台灣v.s中國：脆弱的民主"
http://viewpoint.pts.org.tw/ptsdoc_video/%E5%8F%B0%E7%81%A3vs%E4%B8%AD%E5%9C%8B%EF%BC%9A%E8%84%86%E5%BC%B1%E7%9A%84%E6%B0%91%E4%B8%BB/ (edited) 

> S.  6 hours ago
@kingman not everyone here advocates for both-ways transparency. (edited) 

> chihao:ocean:  6 hours ago
@S. not everyone here agrees with your characterization of this situation as “both-ways transparency”

> S.  6 hours ago
@chihao you can disagree. But currently, this transparency works in your favor, to your convenience. And this is one of the obstacles to achieve solution. Reevaluate.

> kjcl  6 hours ago
我覺得現狀已經是 「Solution」啊...

> chihao:ocean:  6 hours ago
And what is one of the obstacles to achieve what solution? Argue better. @S. (edited) 

> S.  4 hours ago
@chihao "Argue better" said someone who didn't reevaluate and still has the ball in his court. Try harder.

> S.  4 hours ago
@ronnywang thought bullet points as action items will work better:
>
> - **firewall** with `http.user_agent` and similar rules to weed out most of the dumb bots (I can send you a list of rules I use myself)
> - **rate limit hits on critical endpoints** at `/id/` so that even request passes the firewall, you limit the ability to do lots of requests in a short time
> - pseudonymization across the entire system, not just the "export" part
>
> Still up for discussion/finding middle ground (the radical transparency you all seek for, including me):
> - *login part to see clean PII*
> - *request to download clean PII is per-case as you proposed* - however, I have doubts whether asking someone the purpose is important. Anyone could say anything or lie about the purpose. So having some sort of identification of who they are and keeping the record of the request. This should make bad actors thinking twice about whether they really want this data.
>
> Would love to hear your input Ronny.

> S.  4 hours ago
@kjcl have you ever thought of putting the "thumbs down" emoji as your avatar? Could save you a lot of clicking.

> S.  4 hours ago
Hold on, there you go:
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b7dc1c63d8d6b3846716e3038686fce5.png)

> kjcl  4 hours ago
https://zh.m.wikipedia.org/wiki/%E8%A8%B4%E8%AB%B8%E4%B8%AD%E5%BA%B8

> chihao:ocean:  3 hours ago
@S. what ball? maybe you also need better metaphors :pensive:

> S.  3 hours ago
@chihao it's an idiom, not a metaphor. "ball in your court" means it's now your turn / its up to you / expecting your turn now. I was referencing here that I did not hear any contra arguments from you regarding the solution I proposed and the definition of radical transparency a lot of people here seek and what it means to me.

> Yi-Chung Dzeng  3 hours ago
Adding a login / identification mechanism will actually cause company.g0v to collect and process more PII then it is doing now.

> S.  3 hours ago
@Yi-Chung Dzeng PII that is not passively exposed, unlike company data is. Or are you questioning here the ability of g0v to store securely your personal data and exercise your privacy rights in the right manner?

> Yi-Chung Dzeng  3 hours ago
In my metric the liability of the project actually increases by adopting a login/identification mechanism for
Its current “passive expose” of data that is publicly displayed brings no legal responsibilities
The (legal) responsibility of company.g0v to securely save the personal identification / login credential is generated

> chihao:ocean:  3 hours ago
@S. To me it’s quite entertaining to watch your repeated display of your obsession about ronny “not replying to your email” and now justifying your entitlement by the name of “radical transparency” when it’s not about that. You might even enjoy (I hope not) the convenience of your flawed framing — calling ronny and others hypocrites without actually saying it. It’s unhealthy.
To follow your ball metaphor, I am not on that court with you and this is not a 1-on-1 tennis match or whatever. Your framework of understanding this situation is off. This is a community space and people are a reading, thinking, walking away, and coming back all the time. This discussion is not the Wimbledon and many of us are watching the Olympic games now. Everyone has their own priorities. (edited) 

> kjcl  2 hours ago
@S. 而反而可能是這個議題已經討論到一個參與者覺得不必繼續聊下去的地步了～ 我們都有自己的坑要管理。沒時間跟你在這裡沒完沒了～ 可是你真的覺得你跟我們在這個公開頻道計較會影響到該坑主怎麼處理他的網站的話，當然很歡迎你繼續吵鬧，但是身為一個創業的老闆，你一定理解把注意力集中在你的目標上的意思吧～

> S.  2 hours ago
@chihao Do you know what's unhealthy? Your obsession with witch-hunting and framing me being the bad guy, failing to see the full story, even now when I try to seek the dialogue and have a healthy conversation.
Let me clarify something you continue to fail to understand: from the very beginning, I was very protective of Ronny, his project, and this community.
Despite having multiple failed contact attempts to Ronny for over a month at that time, initially, when I joined this community here on Slack, I didn't go rant directly at #general
Instead, one more time, I sent Ronny a private message. I did not want his project to get some bad/unnecessary exposure or the fact that he was ignoring me. Only when he didn't respond to my direct messages, I decided to go public.
I never wanted this to go public, I hoped from the very beginning and tried my best to sort it out with Ronny only. Not because I want to hide something, but because I am a maker just like Ronny and I can put myself into his shoes: I genuinely care about his reputation and this project.
Now, I will appreciate it if you pay a little respect to Ronny, me, and others who genuinely trying to help. I gave you healthy arguments and I expect something healthy in return.
So if you continue to act like this, you are not contributing and you are better off watching your Olympics. (edited) 

> mrorz:orz:  1 hour ago
Back to the original proposal and the follow-up request to pseudonymizing all the endpoints, I think Ronny’s original proposal is a good starting point.
Since no one knows what channel do so called bad-actors use, it looks sensible to me to start with one channel and observe if there is any change afterwards.
Starting with data exports first with most of the original site function intact should also limit the change scope required at this stage, which is good for Ronny or any contributor that wants to send pull-requests to make the change happen. (edited) 

> chihao:ocean:  1 hour ago
Back from #g0v-slack… @mrorz’s point is pragmatic! ++ But… I believe company name + name of company head (負責人, whatever the translation) is and should remain open data. After re-evaluation I think the good outweighs the bad.

> chihao:ocean:  1 hour ago
Two things to add…

> chihao:ocean:  1 hour ago
> 1. It might be beneficial for this discussion to open a hackmd to (perhaps) list out the pros and cons?
> 2. This project is ronny’s project and he has the final say (according to g0v’s Manifesto and rough consensus). As a fellow g0v contributor, I’m thinking about forking this project as it is to provide an alternative.

> Also sent to the channel
> pm5:spock-hand:  9 minutes ago
> @ronnywang quick question: what if I apply for the full dataset according to the new rules that you proposed, and state that the purpose is to "rebuild the original company.g0v.ronny.tw service that was fully transparent"?  Would you give me the data?  How would you evaluate such an application?
@ronnywang 問個問題：如果我依照你提議的新機制申請有原來姓名的匯出檔，並且在申請目的說「我想要重建原本有完整資料的 company.g0v.ronny.tw 服務」，你會給我資料嗎？你會怎麼樣處理像這樣的申請？



