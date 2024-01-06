---
title: 2021.07 個資刪除請求紀錄
tags: log, 紀錄, slack-archive
description:
---
# 2021.07 個資刪除請求紀錄 (1)

timezone UTC+8

紀錄截止時間： 2021.07.31 14:53 PM

:::info
The back messages are directly copied and pasted from Slack interface, plus manual edits on threads.

###### Format
`Name` `time`
`Message`

> `Quotes, or threads`
> > `Quotes in threads, or quote of quotes`

:::

## #general

### 2021.07.26

S.  7:05 PM
@ronnywang could you please answer my DM? There is an urgent matter I've tried to reach you multiple times about. (edited) 

ocy  8:05 PM
joined #general along with 李柏均.

Mar Marín  9:35 PM
Heya! :wave:  :exploding_head: When you come up with a great session proposal for the Code for All Summit 2021 :rotating_light: Remember you have :five: days left to submit it. Let's GO! :dash::point_right: bit.ly/CfAll21-CFP
→ This year’s Summit will focus on Open vs. Closed Tech in Government, Democracy & Elections, Disinformation & Fake News and Power Dynamics in Tech. We’ll have different session formats: Panels, Lighting Talks and Workshops!
:mag_right: Read our Call for Proposals for more info :arrow_right: bit.ly/CfAll_CFP21 (edited) 

小朱  11:34 PM
joined #general along with 4 others.

### 2021.07.27

S.  1:06 PM
I am taking my issue public as it's been too long people responsible for it have been ignoring me.
I got to know that few Taiwanese websites list my personally identifiable information (my personal names along with company data) and abuse this data by monetizing it with ads. I investigated further and got to know @ronnywang g0v website to be one of the main sources of this data as he made it more available to others to fetch it with APIs.
I do understand this open data is provided by the government but that does not mean he should be scraping it without any privacy principles and at the very minimum - the ability for someone to have this data removed at their will.
For that reason, I decided to send him an email with a request to have my data removed, hoping it would be processed in a timely manner.
That did not happen. It's been over a month, and my constant emails, Facebook messages, even an opened GitHub issue (!) and now direct messages here on Slack are being ignored by the main author of this project. Not even a single message like: "Hey, I received your message and I am aware of your request.".
To clarify: I am not here to correct g0v policies or have someone sit down and discuss for weeks what they should do with my or similar request that will happen in the future. I just simply want my data to be removed - plain and simple. If that leads to changes in privacy policies in g0v in the future - great. But for now, please, just remove this data. (edited) 

S.  1:20 PM
@ronnywang I don't know why you are ignoring me but my request to remove my data does not require you to study any law or consult it with others. Just like if you would reach out to me and asked me to have your data removed, I would do so without hesitating.

ronnywang  1:25 PM
抱歉因為我英文沒那麼好，我擔心用英文寫用字沒那麼精準，我用中文寫，再麻煩您自行轉換成英文了。

S.  1:27 PM
如你所願。 但我的要求不需要你向我解釋任何事情。 我只想刪除這些數據。

ronnywang  1:36 PM
當初製作 https://company.g0v.ronny.tw/ 的目的是因為台灣的商業司查詢網站很難使用，因此製作此網站更方便大家查詢使用，為了使網站能有公信力，我並不打算對裡面的資料做任何我自行的塗改遮蔽，裡面的內容要與政府公開的內容全部一致，我會手動更動的條件是我網站內容與政府不一致而我的爬蟲可能沒有正確抓到時才會這麼做

S.  1:46 PM
事實上，通過尊重人們的隱私，您正在使您的平台更加可信。

adzen:cry:  1:47 PM
路過
「開放資料內的公司或商業資訊，被下載或經加值應用在其他網站上，是否涉及隱私被侵犯？有個資外洩之議題？」
https://data.gcis.nat.gov.tw/ns/qa/detail?oid=1921B2C1-153E-4AFD-9121-AA77D9393E45

ronnywang  1:55 PM
我也尊重隱私，我同意隱私是很重要的。但是公司負責人的姓名這個資訊我不認為他算是一個隱私，至少在台灣的法規上已經是合法公開的資料不受個資法保護。但我並不確定 GDPR 針對歐洲公民相關資料是否有更嚴格的保護限制，如果有的話我這邊也願意針對 GDPR 做更正，這點就需要麻煩熟悉 GDPR 的朋友是否能協助說明了，謝謝

> adzen:cry:  3 days ago
只找到這個問答
https://ec.europa.eu/info/law/law-topic/data-protection/reform/rules-business-and-o[…]egulation/do-data-protection-rules-apply-data-about-company_en

> S.  3 days ago
@ronnywang @adzen I've already spoken to a lawyer about it. I am protected because:
a) company data is different from natural person data. So you can list my company name or TAX ID but not my name, my email, or even my title that allows someone to identify me.
b) "information in relation to one-person companies may constitute personal data where it allows the identification of a natural person" - that also applies here.

> Also sent to the channel

> mikechen  3 days ago
The discussion is related to how search engines handle removal of personal information from search results, e.g. Google Search’s removal policy.  The case you’ve made thus far does not appear to qualify based on Google’s removal policy.
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_63aeb93ee449f98b0fdd4fbb4c294d74.png)


> S.  2 days ago
> Removing data from Google's servers does not equal removing data from a website.
> I think we start to diverge from the issue I am trying to solve here: I want the data to be removed from g0v website (just like it was removed from another website I requested). I am not talking here and now about Google's SERP - I will worry about this later.
> Please don't misinterpret my original request.

Sohee Yun  1:56 PM
joined #general.

S.  1:58 PM
我也製作網絡工具。 我在設計時考慮了隱私原則。 無論當地法律如何。 它應該來自你。 (edited) 
2:00
如果您環顧四周，就會發現每個可信平台都有某種數據刪除工具或流程。 這些工具只會在未來變得更加普遍。
2:01
所以不要等到當地的法律趕上來——它們可能已經過時了，不能滿足當前的需求。 相反，成為改變並展示如何完成。

clkao:g0v:  2:02 PM
好奇 S. 在意的點是哪些呢？
個人資訊被拿去放在有廣告的網頁
個人資訊在 company.g0v 容易被檢索
個人資訊在 company.g0v 的公開資料集，以致於讓 (1) 容易發生
個人資訊被政府工商服務登記公開
商業登記資料是重要的開放政府治理基本資訊，英國甚至要求所有權 25% 以上的股東 (PSCs) 就要揭露，台灣僅要求董事揭露。不過在隱私跟公共治理之間如何平衡，這是值得討論的。

> S.  3 days ago
> Let's start with the 1,2 & 3, as they are the easiest to address. It's mostly about 1, 2 & 3.


S.  2:03 PM
即使我不是欧洲人，你也应该尊重我或某人的意愿（不管他们的国籍或现居住地）。

阿昇同學  2:03 PM
資訊揭露的義務並不能完全使用隱私的理由來規避喔

S.  2:04 PM
"資訊揭露的義務並不能完全使用隱私的理由來規避喔" - okay, waiting for the moment when it will be required for the schools to list down names of your kids online. How will you feel about it? Will this still be your argument? Don't try to play God. (edited) 

shivahuang  3:15 PM
Does students own the school? I don’t think they are the same situation. If you think your information should not available on the web and you want the source to remove it, it should be the government. If you think web sites should not use your information and make money with ads, you should contact the site owner who put ads on it. So why you think g0v should take the responsibility to help you hide your information published by the government?

>S.  3 days ago
I think you completely missing the point of my request. Please refer to my original message.

>S.  3 days ago
The moment you collect and process someone's data, you are responsible for it. There is no "I think". It's a fact.

>S.  3 days ago
I will challenge any website owner or project's author who collects or process my data. This is not a particular request I am doing to g0v only.

>S.  3 days ago
g0v is fully responsible here as it contributes to the further spread of my personal data. Even @ronnywang admitted that he wanted to create a more accessible place for this data.

>shivahuang  3 days ago
>Ok, let me try to clear that.
>1. Your information is published on the web.
>1. Some web sites listed your published information and puts ads on >it.
>1. You don’t want your information public, especially someone make >money with it.
>1. Your information is public because you’re corresponding with a company, so the government make your information public.
>1. g0v organized these information from government, without any modification.
>1. You asked g0v to modify the data they fetched from government to hide your information?
>Does I misunderstand something?
My question is, why you think g0v, which doesn’t make money from these data, should modify or mask these information they fetched from government?

>S.  3 days ago
I am not sure what is your point here. I have a simple request - which part of my request you don't understand or want me to clarify?

>shivahuang  3 days ago
You’re correct! g0v should responsible for the correction of the data! That’s why they would not mask these information the fetched from government!

>S.  3 days ago
You completely missing the point. I requested for my data to be removed, not modified or masked.

>shivahuang  3 days ago
If you don’t want your information listed on government provided data, I don’t think g0v is the one you should contact with.

>S.  3 days ago
g0v takes an active part as a data processor and I have full rights to request the data processor to have my data removed. Which part of my request do you dont understand here? If you act on behalf of the legal team for g0v, my lawyers will be in touch. But if you don't, you are not contributing by acting like you know what you are talking about.

>shivahuang  3 days ago
I know you have lawyer*s*, and they’re ready to take your money. And I know you have the right to declare you have the right. Really, I do know.
The only thing I don’t know is, does the data processed by g0v incorrect? If so, which part is incorrect? If not, are you asking g0v to provide incorrect data to the public?
If your question is “I don’t think the government should provides such detail information about a company owner, what should I do?” I think you can find someone here to discuss with you and maybe take some action to make a change.  (edited) 

>S.  3 days ago
:popcorn:

>S.  3 days ago
Reading comprehension is not your strong suit, isn't it?
Let me rephrase: I don't care whether g0v data is correct or not, I care about not having my data processed and displayed on the website - am I crystal clear now? (edited) 

>shivahuang  2 days ago
I can also rephrase that: I don’t care whether the government provides or not your information, but g0v should provide these data as it is - does that solve any problem?

>Of course not. And you can call your lawyer*s* to sue me now. Just tell your lawyer*s* “this guy don’t comply my request to make g0v provide incorrect information to the public. So sue him!” I believe your lawyer*s* will very happy to take this easy case and easy money.

>S.  2 days ago
Excuse me, why do you care? This is my PII, not yours. And I have the right to have it taken down, whether you like it or not.

>shivahuang  2 days ago
Excuse me, why shouldn’t I care? This is my country provided these data. And I have the right to make sure these data is correct, whether you like it or not.

>S.  2 days ago
Because you see, I wouldn't even question someone's request if they came to me and wanted their data removed. My inner integrity tells me they have every right to have the data removed from my website. I don't need to debate over it, question them, or try to act like I am entitled to hold their data hostage. I would simply do it. Cause I respect others.
And maybe, just maybe, one day you will get that too.

>shivahuang  2 days ago
I think we should stop arguing like two little children. You don’t care what cause this problem, and you don’t care about the name of g0v. I do provided you the possible solution to cooperate with g0v to solve this problem, but you choose to ignore it and tried to terrify people here.
Let me remind you to care about your words. Not only you have lawyer*s*.

>isabelhou  2 days ago
尊重不同意見是討論的前提，並請遵守COC。https://g0v.tw/coc/

>S.  2 days ago
Solution??? I already wrote multiple times over a span of a month and so far no solution in sight - no one addressed my query, my data is still publicly displayed as of now.
So maybe we can stop chatting about solutions and actually do something about it.

>S.  2 days ago
And the way everyone was acting so far: either ignoring me or now attacking, doesn't make me feel any better.

>shivahuang  2 days ago
Have you read this? https://g0v.tw/coc/
Who claim he have lawyer*s*? Me?
Who claim other acting like a dog? Me?
Who claim other comments stupid? Me?
So please tell me, who is attacking?
The suggested solution is, discussing with people in g0v about: is it suitable government provides information about a company? How to balance the information people should know about a company and keep the owner safe? And what can we do to make the government change?
But as I said, you ignored it. You just want us to comply your orders. No thanks. (edited) 

>S.  2 days ago
You clearly have no idea about this entire situation - I am the one who is being ignored here and no one is cooperating. My messages have been ignored for all this time and that this is the very first time @ronnywang actually reacted to what I wrote and answered me - likely because I took the matter publicly and he can't continue to ignore this.
For all this time, there was a silence from him. It doesn't matter what language you speak, you can translate the message and at least write something like "hey, I am aware of your request, sorry for silence from my side" etc. . That did not happen.
And now, when I took the matter publicly and asking for a simple request of by the way - not yours, but my data to be removed, instead of actually helping me, you are putting head into the sand and question my basic privacy rights like it doesnt matter to you. (edited) 


>Caleb Rogers  1 day ago
Just ban the guy, we shouldn't have to deal with people calling our community members dogs or being rude about their English ability (edited) 

>S.  1 day ago
@Caleb Rogers but that's exactly what I have been told by someone who exchanged information with Ronny directly  - they said that his poor English ability didn't allow him to respond earlier.
Which btw I did not buy because for all this time he was fully aware of the emails and messages I have been sending his way and it only takes literally a single sentence translated via Google that he is acknowledging my request. That would be much better that a total silence. (edited) 

>Caleb Rogers  1 day ago
There's many national languages in Taiwan. None of them are English, last I checked. Also, you called another person a dog lol. Pretty uncalled for imo.

>Caleb Rogers  1 day ago
Aren't you a business owner in Taiwan? Mandarin requirement for effective communication shouldn't be a surprise to you at this point...

>S.  1 day ago
Yup so at least have balls when you upload someone PII and answer emails in Mandarin or whatever language you want instead ignoring them. I know how to use Google translate.

mikechen  4:22 PM
replied to a thread:
我也尊重隱私，我同意隱私是很重要的。但是公司負責人的姓名這個資訊我不認為他算是一個隱私，至少在台灣的法規上已經是合法公開的資料不受個資法保護。但我並不確定 GDPR 針對歐洲公民相關資料是否有更嚴格的保護限制，如果有的話我這邊也願意針對 GDPR 做更正，這點就需要麻煩熟悉 GDPR 的朋友是否能協助說明了，謝謝
The discussion is related to how search engines handle removal of personal information from search results, e.g. Google Search’s removal policy.  The case you’ve made thus far does not appear to qualify based on Google’s removal policy.
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_57699ba9227ea9616f697e97e0681294.png)

View newer replies

Chang-Chien Wong  5:12 PM
joined #general.

John Lee  5:42 PM
個資法19條第1項，非公務機關對個人資料之蒐集或處理，除第六條第一項所規定資料外，應有特定目的，並符合下列情形之一者：
三、當事人自行公開或其他已合法公開之個人資料。
-> 商工行政服務入口網 已經公開 (edited) 

kingman  5:49 PM
其實頗好奇公司法、商業登記法對於負責人以及公司相關資訊的披露，與個資法的範疇
引用adzen的連結，公司法、商業登記法已經強制規定要公開公司、行號的負責人、股東等相關資料，但是連結又有但書有相關個資法規定
*2. 本平台所公開之資訊，涉及公司資料部分，尚不適用個人資料保護法(以下簡稱個資法)， 而公司資料中之自然人姓名雖適用個資法，惟任何人如擬自網站蒐集個人資料，仍應符合個資法相關規定，如行為人違反個資法時， 台端得依個資法行使權利，以確保自身權益。*
而clkao又提到英國也要求大股東揭露原則，且也是開放政府治理的基本資訊
那政府法律已經規範必須要強制揭露的資訊，公開資料又已經完全公開的企業、行號與個人資訊(負責人姓名、董事、監察人與股東姓名)，其他人可以合理引用的範疇？又個資法相關的合理引用、違法侵權型態？ 以及政府機關對於相關法律的遵守程度？ (edited) 


>kingman  2 days ago
https://data.gcis.nat.gov.tw/ns/qa/detail?oid=1921B2C1-153E-4AFD-9121-AA77D9393E45
https://law.moj.gov.tw/LawClass/LawSingleRela.aspx?PCODE=J0080001&FLNO=393&ty=L
依公司法第393條規定，公司下列登記事項，主管機關應予公開，任何人得向主管機關申請查閱或抄錄：	
	   一、公司名稱。	
	   二、所營事業。	
	   三、公司所在地。	
	   四、執行業務或代表公司之股東。	
	   五、董事、監察人姓名及持股。	
	   六、經理人姓名。	
	   七、資本總額或實收資本額。	
	   八、公司章程。	
	   前項第一款至第七款，任何人得至主管機關之資訊網站查閱。	
https://law.moj.gov.tw/LawClass/LawSingle.aspx?pcode=J0080004&flno=19	
依商業登記法第19條規定，商業之下列登記事項，其所在地主管機關應公告於資訊網站，以供查閱：	
	   一、名稱。	
	   二、組織。	
	   三、所營業務。	
	   四、資本額。	
	   五、所在地。	
	   六、負責人之姓名及出資額。	
	   七、合夥組織者，其合夥人之姓名及出資額。	
	   八、分支機構之名稱、所在地及經理人之姓名。	
	   公告與登記不符者，以登記為準。

>kingman  2 days ago
公司法弟393條函釋
https://gcis.nat.gov.tw/elaw/lawDtlAction.do?method=lawToCons&pk=19&art=393&dash=0


kingman  5:54 PM
以及另一個文化因素的樣貌也很好奇，台灣、日本的偏東方的文化，與歐洲，以及美國的文化，對於個資、隱私、自由，以及公共利益的關聯互動
記得去年台灣一開始就要求口罩，絕大多數的人也都很願意配合，日本也是公共利益對比個人自由、利益，口罩也是可被要求的
但是同時間美國、歐洲有大量新聞與抗爭，關於戴口罩這件事情
又我們對於疫苗接種，群體免疫這件事情是認同的，但是法國現在正在抗爭疫苗接種與否的自由
延伸的，台灣對於個資相對得很不尊重，也很不重視，歐洲卻有GDPR，有點好奇個資、隱私、自由，以及企業、社會與國家群體公共利益的互動，以及個資、隱私、自由，在不同文化中的定義和型態 (edited) 

ish  5:56 PM
According to my observation, main point here is that the both side have different understanding towards “representative”. One side may think those personal data are used for the communication between the government only and this should be kept as confidential. However, the other side’s (including government) idea is, the representative’s data should be accessible to the public since this person represents the whole organization. (And that’s why lots of people have their own business phone, business email, etc).
Now the data is opened for everyone. In my opinion, those who don’t want it  to be disclosed should stop it from the original source instead of stopping it from the entities treating the consistency as the measurement of correctness. If the data does not reside in the original source, it will be a breeze for the personal to ask for removal from the downstream. (edited) 


>S.  2 days ago
That doesn't change the fact that a person has a right to request to have this data removed, whether it exists at the source or not.

>ish  2 days ago
It’s not my intention to discuss whether you have the right or not. I will leave it to your lawyers and the counterparts. Here I only provided you a strategy about where to start.

>S.  2 days ago
Fact #1: g0v is not an official government body.
The part you are missing here is that g0v or other 3rd party projects/websites are not official government bodies, therefore they should not act like one.
If for whatever reason, an official government body opens this data, this does not mean that another party can do whatever they want and disregard altogether privacy laws. (edited) 

>Caleb Rogers  1 day ago
Yea it does.


kingman  6:00 PM
其實還有另一個交連，行號沒有法人，所有的一切都歸屬於自然人，而公司為法人身份，負責人、股東的揭露問題，以及與自然人的關聯性？
是很多法人出事都是會計和負責人抓去處理拉，過去的文化背景也是公司出事，找股東和負責人賠到底，而不僅限於法人(法律)的範圍 (edited) 

S.  6:08 PM
I already said at the beginning I am not coming here to debate over your policies, Taiwanese law or tell you how to design your platform.
In fact, I have never heard of g0v before until I get to know it processes my data, without my consent. I didn't ask to be here, neither I asked to purposely sign up to your Slack group - I was forced to. Because all the other ways of me trying to reach out to the project's authors did not work, which alone, already does not sound right to me.
Seems like some people feel bad that I came here and tell them what to do - excuse me, but I didn't ask you to put my data there. So if it is so hard to process a simple data removal request, simply don't process other people's data without their consent and you will never have to deal with requests like mine.
And definitely, you shouldn't feel surprised I am unhappy with how this entire situation is being handled - first being ignored and now being attacked. (edited) 
6:11
It doesn't take a lawyer to process my request. It just takes someone with a bit of empathy.

S.  6:19 PM
Also, everyone misses the point that just because official government body provides this data publicly, it does not mean we need to copy this information left and right across 35434542 websites and act like we are entitled to process someone's personally identifiable information without their consent, and without at least the ability to request to have this data removed. (edited) 


>isabelhou  2 days ago
S.想要移除的資料是「姓名」嗎？除了「姓名」以外，網站上似乎沒有其他個人訊息？

>S.  2 days ago
@isabelhou I want to remove the data that identify me as a person: my full name and a title.
I don't mind the company name being there - that's fine.


Lynn Deng  6:23 PM
協助轉貼：GreatFire is hiring! 需要一位精通Chromium的開發者，幫助進行“自由瀏覽“的開發，詳見：https://zh.greatfire.org/xuanshang/5?cf_chl_jschl_tk=pmd_a02ee20abc749e21df5af917d558599504d6ad2a-1627380954-0-gqNtZGzNAeKjcnBszQki

John Lee  6:23 PM
也很好奇這情況是否適用個資法第三條（個人可要求刪除的權利），要求政府不公佈應該一定不行，但要求 crawler 刪除很可能可以 (edited) 

Yi-Chung Dzeng  6:27 PM
company.g0v應該不算是無特定目的的crawler, 不會有蒐集個資特定目的消失的狀況。他蒐集並mirror一份在我看來也有顯而易見的公共利益

kingman  6:27 PM
還有一個可能的文化歧異點
在台灣，別人我是不知道，但是至少我以及我周遭，我們處理事情是以情理法為順序，法律只是道德的最低底限，以及合約是在關係撕破臉的時候才會拿出來用，平日處理很多事情，如果能夠互相幫忙、通融，就會讓彼此的關係以及事情能夠順利的走下去，讓事情處理好比較重要
而在溝通的過程中，提出律師、法律，讓律師來找你談心，在我的感受已經是微恐嚇的模式，逼近撕破臉的階段，以及台灣傳統上好像很不喜歡法律和法院，很多事情都會進可能的避免到這個階段

John Lee  6:28 PM
那也只是蒐集本身沒有觸法，但不見得也可以拒絕「刪除的請求」

Killkli  7:11 PM
https://blog.104.com.tw/%E5%80%8B%E8%B3%87%E6%B3%95%E7%B3%BB%E5%88%97%EF%BC%8D%E6%B3%95%E4%BA%BA%EF%BC%88%E5%85%AC%E5%8F%B8%EF%BC%89%E8%B3%87%E6%96%99%E6%98%AF%E5%90%A6%E5%8F%97%E5%88%B0%E6%9C%AC%E6%B3%95%E4%BF%9D%E8%AD%B7/

7:11
引述上文：
「惟上述公示的法人（公司）資料中，揭露有該公司股東、董事、監察人或經理人的姓名（雖僅有姓名，因該姓名仍可與其他個人資料相對照、組合或連結，而得以間接識別特定個人，故仍是屬於本法所稱受保護的個人資料。），這些依公司法規定公示在外的個人資料，是否即不受個人資料保護法的保護？根據法務部民國104年8月7日法律決字第10403509940號函釋要旨略以：「工商行號資料有涉及負責人（自然人）部分，若其他法律明定應公開或提供者依其他法律辦理，但就未規定部分仍有前述法律適用（作者註：指個人資料保護法）。 」，亦即任何人不得未依個人資料保護法之規定而違法利用該當事人的個人資料。」
7:12
所以問題最後會回歸到這些資料的確是受個資法保護
7:13
建議是讓政府去扛這個資訊保護的責任，我覺得這位當事人的確有權要求自己的個資移除

Killkli  7:14 PM
個資法：
第 3 條
當事人就其個人資料依本法規定行使之下列權利，不得預先拋棄或以特約
限制之：
一、查詢或請求閱覽。
二、請求製給複製本。
三、請求補充或更正。
四、請求停止蒐集、處理或利用。
五、請求刪除。

>Yi-Chung Dzeng  2 days ago
個資法第三條講的是不得預先拋棄　實際上的請求類型和條件須見第十一條
公務機關或非公務機關應維護個人資料之正確，並應主動或依當事人之請
求更正或補充之。
個人資料正確性有爭議者，應主動或依當事人之請求停止處理或利用。但
因執行職務或業務所必須，或經當事人書面同意，並經註明其爭議者，不
在此限。
個人資料蒐集之特定目的消失或期限屆滿時，應主動或依當事人之請求，
刪除、停止處理或利用該個人資料。但因執行職務或業務所必須或經當事
人書面同意者，不在此限。
違反本法規定蒐集、處理或利用個人資料者，應主動或依當事人之請求，
刪除、停止蒐集、處理或利用該個人資料。
因可歸責於公務機關或非公務機關之事由，未為更正或補充之個人資料，
應於更正或補充後，通知曾提供利用之對象。

>Yi-Chung Dzeng  2 days ago
至於非公務機關處理個人資料的限制和限制的例外則在第十九和二十條

>Killkli  2 days ago
哇哈哈，真的深入去讀就發現很多可以討論的地方
個資法牽涉到公益與個人權益保障問題
必然有衝突跟爭議的空間
感覺這的確是一個很值得上法院判出個例子的東西
有志法律史留名的律師可以試看看
這個議題很讚，但是站在當事人的角度的話....
我是當事人我會選擇迴避這個問題，不過，這的確是可以一爭的議題
水很深.....

Killkli  7:14 PM
蒐集、處理&利用已經涉及這邊的保護範疇
7:14
我們的g0v終歸並非民意代表（政府）
7:15
在法理上很難說有權去使用這個個資相關訊息
7:15
民眾要透過政府的管道去獲得那是一回事
7:15
我的建議是這部分就把人名等個資相關的部分，改成link回原始政府提供的位置

### 2021.07.28

pichuchen  10:19
雖然還沒有查詢立法緣由，不過在公司公示資料當中揭露姓名應該是避免同一董事持股公司間互相交易造成公眾的不利益，因此需要揭露姓名供大眾識別任兩公司之董監事之關係，然而就目前現況而言揭露程度可能還不夠，有修法空間，舉例來說，他並沒有把實質受益人公開揭露，那因此如果有人將公司以其配偶之姓名或其子女之姓名做登記，是否還能達成揭露姓名帶來之公益性也許有待商榷。
但是從前面的討論看起來 @S. 實際上並不認為該公務機關（經濟部商業司）揭露公司董監事姓名有問題，僅要求非公務機關刪除上開之資料（董監事姓名等），然而於個資法第十九條中此資料已經公務機關合法公開，因此 @ronnywang 搜集及處理該資料應無不法。
@Killkli 提到個資法第三條請求刪除是一個 @S. 可以主張的點沒錯，但是對於 @ronnywang 也是可以主張有符合個資法第十一條的利用目的以及個人資料保護法施行細則第21條的其他不能刪除之正當事由而拒絕 （怎麼有點實聯制的既視感）
但是如果揭露姓名只是為了確認是否有公司同一負責人或是董事此一理由的話，那是否有更好的處理方式也許有待討論，例如收到該個資主體之資料轉換為一內部代碼，舉例來說，把它改成 ANNO001 這樣的標示方式，然後點擊下去之後還是可以看到所有 ANNO001 有相關的公司，這也許會是個處理方式。
然而這樣做法在實務上可能會有困難，因為在公示資料上只標示姓名，沒有標示身分證字號等，因此如果有人主張他的名字是郭台銘而要求行使整個資料庫上和郭台銘有關之人之權益，應該在執行上會有困難，而且顯然會陷公眾於錯誤。
或者是得請該公司如果需要遮蔽其董事資料，那該公司可以出具證明（公司大小章、負責人簽名或是電子簽章等足資識別不是冒用的證明）來作為請求更正之依據，而在 @ronnywang 的網頁上可能就另加著名「收到該公司來函，要求遮蔽其負責人之姓名」即可，那有需要的民眾可以直接從經濟部網站查詢到該公司實際上負責人之姓名，對於平台而言還是有達到揭露之目的，但是是否為當事人想要的保護方式就不得而知了。


>S.  1 day ago
There is a simpler solution and Singapore did it successfully: there is only one source of company data that is accessible on the official government website. You can see the company name, TAX ID, and so on but if you want names of directors - you gotta sign up and pay.
This model is simple and it's working well. How do I know this model is working?
Because no personally identifiable information data has been leaked over years or popped on various non-government-related websites, unlike it happened in Taiwan. (edited) 

>Caleb Rogers  1 day ago
What's the website? I'll go ahead and scrape and reupload it :grin:

> S.  1 day ago
@Caleb Rogers Go ahead :) Only if you can afford it. It's paywalled to weed out people like you. (edited) 

>Caleb Rogers  1 day ago
Ah, so they aren't actually transparent, they only allow upper class citizens access the information. Then, that's an immoral model that other countries shouldn't emulate :) Taiwan's is more ethical.

>S.  1 day ago
At least they reply to your emails when you inquiry them about PII.

>Caleb Rogers  1 day ago
Mate to be honest I'm not gonna depend on the ethical judgement of someone that has a habit of calling people dogs

>S.  1 day ago
Don't bite maybe? ;)


S.  10:45
I appreciate you guys want to have a debate, cite various laws and whatnot.
But no one seems to notice an elephant in the room: that we need to have a debate for such a basic request in the first place.
If I put someone's personally identifiable information on my website (regardless of this data is open source or not or that is coming from an official government body or whether the person gave me their consent or not), my moral integrity tells me to remove it upon that person's request! I would comply with their request, without a single word coming from my mouth. Not because the law tells me to do so, but because my moral integrity tells me this is the right thing to do.
If we need to have a debate whether or not to remove someone's data, there is something, fundamentally very wrong here.
I challenge anyone in this room who feels entitled to hold someone's data against their will, just because it was open-sourced in the first place. (edited) 


> Yi-Chung Dzeng  1 day ago
What you considered too basic for a debate is not regarded as granted here. The consensus here would probably be that when you started a business, that part of you enters public life, and g0v is all about enhancing people's access to public life.
You also seem to accept the model that government agencies solely control the information, which are both private personal data but are also publicly availabe (let's just omit the contradiction here). I can hardly see this idea being accepted here, not to mention the sign-up-and-pay-up part.
g0v is named as a parody spelling of gov for a reason. You have a hard time finding the type of empathy you want here.

> S.  1 day ago
Parody or not, you process PII. You can keep enhancing everyone's life with one record less in your database too.


Kevin/kjcl.  15:14
Okay, I'll bite.
It seems, based on your response to @isabelhou's message that you are concerned with the fact that you are attached to your company's name as an owner. You say that this is personally identifiable information that should be private.
I actually think there's reasonable room here to disagree.
Let's make an analogy today to a similar dataset. Campaign finance contributions. Let's say you donated to a political candidate. In either the United States or Taiwan, the established norm is that your name and your contribution amount are now part of a publicly accessible database. This is because while people have a right to privacy, the tradeoff is that society has a right to be informed of the people making campaign contributions.
In fact, the FEC in the United States currently maintains a public API that allows you to query any political donation by name. With a couple keystrokes, I can see who Rupert Murdoch has donated to this year. Is this a violation of his privacy? The Australian Electoral Commission has released public datasets in CSV format of political donations. Should they take these down? Organizations like Open Secrets maintain a copy of this data for the purpose of public transparency and accountability. Does Rupert Murdoch have a right to tell Open Secrets to take down his name?
You take issue with the fact that your name is being listed as the responsible individual for a company. But how do we think about the tradeoff between the public's right-to-be-informed and your right to privacy, using this model I discussed above?
What if (hypothetically), a company was responsible for a large environmental disaster, or an operational failure that resulted in some form of catastrophe?
Shouldn't the public have a right to know the individual(s) responsible for this company?
In a world where companies pollute the environment, damage neighbourhoods, and recklessly ruin lives, isn't having an individual's name behind a company the bare minimum of accountability?
So I will go out on a limb and say: I do think there is reasonable room here to disagree about whether or not this is PII. Also, coming into the Slack and calling people 'dogs' is not very nice.

S.  16:10
Do you know what's not nice? When someone is taking a piss on you for over a month and then when you take things public, they care more about saving their face than actually helping :slightly_smiling_face:
You also seem to completely miss my point: I never said people should not have a right to know the name of the owners. And trust me, there are simple solutions to this problem.
There is a difference between having my names plastered all over the web on some non-gov websites vs my PII accessible from one central place that is protected from search engines and gate-walled (at least a signup). Some countries are doing that. You can have the privacy of the people, and let the public still see the data at their will. Win-win.
Your "what if" scenario is not an argument either - if an owner of the company is wrongdoing and there is a public outcry about the specific company, surely the government will go after them and if this is something related to a public matter, release the names. Same with the "corrupted politician" example someone mentioned to me in private conversation. Removing publicly displayed data does not hide someone's money or make them evade the law - the government still has all the records, just that they are not displayed publicly (not to mention the fact that a corrupted politician still has basic human rights too). Then you might continue to argue and say - but wait, someone could alter the data in an official government database. Well, if they alter the data, your little crawler is going to pick it up anyways, rendering your data "incorrect" and there is nothing you can do about it. (edited) 

Slackbot  16:10
https://i.giphy.com/media/lPulaaB9lDMnGZiivs/source.gif

Kevin.  16:18

>There is a difference between having my names plastered all over the web on some non-gov websites vs my PII accessible from one central place that is protected from search engines and gate-walled (at least a signup). Some countries are doing that. You can have the privacy of the people, and let the public still see the data at their will. Win-win.

Now we're cooking with gas. :slightly_smiling_face: So it seems the issue you're having is not that your PII is on this publicly accessible API, but that there are no meaningful access constraints on this API. If the project owner were to introduce meaningful access constraints like key-based authorization, would that be a proper balance between the public's right to be informed and your desire to introduce some degree of friction and accountability in accessing this public data set?
You may not be familiar with how g0v operates (which is confusing to everyone!), so to be clear, I cannot speak for the project owner or for g0v, but I'm just seeing if there's a reasonable compromise to be struck here (which was the purpose of the discussion we're having!)

S.  16:24
My proposed solution:
* don't scrape, store and process PII (names that is) on g0v - leave this info on the official government body website.

16:25
I did not get to know that my names are publicly displayed from a gov website - I saw Google search results that pointed out to at least 5 different websites in Taiwan. None of these sites were government websites. Also, the government did not abuse my PII, the 3rd party websites did. (edited) 

Kevin.  16:26
But as many people have tried to discuss with you, it is debatable whether or not the names of directly responsible individuals for a company constitutes PII.
Should Open Secrets take down their campaign finance databases (which are not official government websites)?

S.  16:27
If someone request to have their name removed? Absolutely, they should take it down.
16:28
The problem is not you scraping public info. The problem is when you refuse to remove it and keep it against someone's will.

Kevin.  16:28
So to be clear, if Rupert Murdoch or Jeff Bezos wrote to Open Secrets and asked to remove all data Open Secrets had on them (publicly available), you believe Open Secrets has a moral obligation to take it down?

> Caleb Rogers  1 day ago
The are public officials and surely require different considerations. Especially Jeff bezos

> Isabel Hou  1 day ago
確實。Ronny在他的發言裡也提到這點。
> S.  3 hours ago
I don't know whether a guy who flies rockets wants to have his name plastered with ads on a website of 12-year old kid without his consent but perhaps you can reach out to his legal team and ask what they think about it?
What I am trying to say here is that my situation is very different. (edited) 


S.  16:31
So you feel entitled to own someone's data against their will? Whom are you policing? Or rather - who are you, to police it? (edited) 

> Yi-Chung Dzeng  1 day ago
Citizens.
The basic philosophy of g0v might summarize as follows: Whatever the gov is doing, citizens should try to see if they can do it themse

> S.  1 day ago
Somehow, people call it a "better manner" and no one minds process someone's data against their will until their data is being processed against their will :slightly_smiling_face:


Yi-Chung Dzeng  16:31
After reading the debate here, I checked a bit the court rulings with regards to 個資法第十一條，when people request their PII to be taken down from press reports or search engine autocomplete suggestions. @S. may be interested to know the outcomes, which are almost always based on arguments of proportionality to public benefit. I also believe that is the right way to go.


Kevin/kjcl.  16:35
I'm gonna go eat dinner, but all I wanted to say was that at the end of the day, I hope this exchange demonstrates to you that reasonable people can disagree on what's happening here, and there's no need to be mean about this.
please be well!

Quentin Brasseur  19:51
Not legal advice and not giving an answer on whether S.'s data can be processed
* Is the name of a director a personal data? Yes, it is. I believe the definition in the PDPA is clear. The fact that the information is public, or linked to a company (which is not personal data) doesn't put it in the "public domain" (which is a different thing).
* Can personal data (PD) be processed without the data subject's consent? Yes. Consent is only one of the legal grounds that allow a data controller (e.g., the g0v project) to process PD. In the case at hand, a data controller may also process data based on TW PDPA Art. 19 "6. where it is necessary for furthering public interest, 7. where the personal data is obtained from publicly available sources unless the data subject has an overriding interest in prohibiting the processing or use of such personal data". [6. can make sense but one can wonder about whether it is necessary. 7. fits better but is a weaker legal ground]
* Does this mean that one can do whatever he wants with data made public lawfully? No. The PDPA sets limits based on good faith, interests, the purpose, etc. (Yes, that's broad. Such a broad definition is necessary to let people balance the interests at stake).
* The data subject has rights e.g., ask to stop collection/processing, erase data, get a copy, etc. The data controller has 15/30 days to accept or reject the request (if the request is rejected, I understand the option is a civil complaint - a confirmation would be interesting).
* Thoughts on the interests at stake. S.'s has interest in his privacy. The society has an interest to know the identity of the legal representative of a company. I don't know exactly the reasons in Taiwan but Trade Registers are generally used to determine whether someone can validly engage a company (which may have an impact on his responsibility). Otherwise, how a third-party knows he's really having an agreement with a specific company? I believe that what is key is that the personal data collected from the Trade Register is processed for a purpose in line with that specific purpose (e.g., scrap that data to populate a list of prospects wouldn't be lawful IMO).
* 
I digress but I'd like to stress one thing about data privacy: Don't think my privacy = my consent or it's unlawful. That's wrong. There are other legal grounds (in the PDPA and in the GDPR) that are generally more adequate. Take the GDPR as an example: it is known for being more protective of data subject's rights. However, it is advised to use the consent of a data subject as a last option. A specific case: one of the EU Data Authority issued a fine of 150.000€ to PwC because they were using the consent of their employees to process their data for HR/Payroll purposes, instead of using a more appropriate legal ground such as complying with a contractual obligation (employment contract) or their legitimate interest.

Hope the above is useful and accurate (I'm not a pro on this topic but spent some time on it) :slightly_smiling_face:

References:
1. Taiwan PDPA (English): https://law.moj.gov.tw/ENG/LawClass/LawAll.aspx?pcode=I0050021
2. An analysis that is more easily readable than the law https://iclg.com/practice-areas/data-protection-laws-and-regulations/taiwan
3. If you're curious: the fine for using consent instead of the appropriate legal ground: https://edpb.europa.eu/news/national-news/2019/company-fined-150000-euros-infringements-gdpr_en

Li-Hsuan Lung/naush  19:54
I’m not a lawyer, so I’m not sure I can contribute to this conversation meaningfully. :simple_smile:  But I want to share a few quick observations.
1) I want to say Taiwanese generally favors collectivism over individualism, which is not an excuse for not respecting data privacy laws elsewhere, but might explain the reactions and general attitude toward this issue among this group.
2) g0v is an open-source community where decision-making is decentralized. As far as I know, there is not a single representative who can unilaterally make policy changes or require any individual contributor to change their code, so I am wondering what is the expected outcome here?
At this point, I feel invested in seeing where this discussion goes. I want to thank @S. for being patient with the community and highlighting this issue. For my own education, I would love to see a clear definition of the legal role & responsibilities of g0v projects when we are acting in the capacity of a data processor w/ regard to local and overseas data protection laws. I wouldn’t mind helping out with the translation of this exchange and (hopefully) the eventual outcome. I think it will be good for the existing and future g0v contributors.

chihao:ocean:  19:55
Have not been following the entire discussion here but think it might be good that thoughts from @Quentin Brasseur (and others) be recorded in a hackmd :smile:

chihao:ocean:  19:56
To record the trace of this discussion before it is eaten by Slack (context: g0v.tw still uses a free version of Slack which limits scrolling back to see old messages)

> mglee  11 hours ago
同意是個重要需要記錄的對話，尤其是對社群未來處理各種開放資料及removal request，logbot 好像掛了？有人正在把對話存到hackmd嗎？
我們也需要思考極端一點的狀況，例如：由政府公開但不好存取的公共資料若含有個資>>被 g0v 爬下來做成更容易應用的 API>>除了公益性質的應用外，該API也被拿去用在非公益且對當事人有巨大傷害的應用上 (比如色情、暴力、假訊息)，g0v 作為資料的中介者 (讓資料變得容易存取的角色)，有 (a) 法律責任嗎 (b) 道德責任嗎？

> pichuchen  8 hours ago
我的想法是並沒有「不好存取」這件事，但是實際上確實可以做一些機制來限制存取者身份，如此 g0v 如果要把他公開就得多做一些事情，舉理來說，在查詢頁面限定需要先登入 e政府的帳號密碼，系統會記錄查詢者的身份，那在這種情況下 g0v 去複製這些公開資料可能就得得到政府機關的授權了，而政府機關有可能不會同意授權所有的公司資料

> pichuchen  8 hours ago
不過單就公司登記資料的案例來說好了，坦白講，g0v沒做也是有其他的網站在做，而且還加上廣告，搞不好主機還放在國外...
> isabelhou  5 hours ago
g0v --> g0v 專案坑主

Ronnywang  20:30
很謝謝很多人提供法律上相關資訊，我這幾天錄完零時小學校的 QGIS 課程後，會想來把這些討論整理成共筆，是很有意義的討論。

我先回覆 @S. ，我無法給你時間，也無法保證我會將你的名字從網站上遮蔽，因為我目前還不覺得這是我一定要做的事。

我很認同隱私權的重要性，但我不認為姓名跟身份連結就一定是需要被保護的隱私。舉個例子，立法委員、行政院長的姓名也是個人資料，難道也是只有政府網站可以公告，民間網站提到只要當事人要求就必需將名字去除嗎？立委或官員的姓名可以被大家自由討論連結使用，有他的公共利益價值在，如果只有政府有公布的自由，對公共利益的傷害非常的大。

那問題就會回到，那公司負責人的姓名的公共利益的程度能跟立法委員和政府官員相比嗎？這問題就沒那麼簡單了，郭台銘和路邊飲料店負責人姓名的公共利益性就差很多了。但假如果今天網站提供了飲料店負責人可以申請遮蔽他的姓名，那之後郭台銘的法務也來說要我遮蔽，我要用什麼樣的標準同意飲料店的遮蔽卻否決郭台銘的遮蔽？這邊有幾個選擇：
1. 誰來申請都幫他把資料刪除：這或許是你最認同的方向，就算郭台銘來也一樣有他的權利，但這樣這資料可能就失去很多公共利益性了
2. 我可以審核哪些人資料可以幫他刪除，哪些不刪：如果有夠好的標準我覺得這會是個好方案，但我並不希望這是完全靠我個人的判斷，我沒有資格也沒有能力做這個判斷。
3. 比照現有公司法以及商業司資料公布：這就是我選擇的現況了。

你前面主張政府也有提供這些資料，政府已經有公布了，因此該有的公共利益已經足夠，民間不需要做這些事。這點我並不認同，我當初會做這網站就是因為政府的不夠好用，這也是很多 g0v 的朋友為什麼會想要推動 open data ，我這邊公司資料也幫助了像台電30億敦親睦鄰追追追以及一些 g0v 專案，而這些都是政府本身作不到的。

> pm5:spock-hand:  1 day ago (7/28 10:34)
@ronnywang 可有意願評估一下前面有人提出的選擇 4 嗎：誰來申請，都把這個人的姓名 hash 起來，但保留能用這個 hash 查到所有有連結的公司資料的功能？也就是不完全刪除，但也不透露姓名，的方式

> Ronnywang  1 day ago
但這方法也適用於郭台銘以及任何立法委員或其配偶姓名嗎？如果是的話就比較等於方法1了，而這樣可能會讓之後想要做一些公司與立委之間利益迴避的研究的計劃難以進行

Tkirby:kirby:  20:45
如果主張政府已經有了, 民間就不能放的話, 我覺得不光是政府好不好用的問題, 而是已經在妨礙資訊的散佈, 或者說變成言論自由等級的問題了

S.  21:39
@ronnywang I sent you first email on June 20th, 2021 asking to remove my data from your website, and multiple follow ups after, which never been replied.
Is this your official reply and a rejection of my request?


Ronnywang  21:47
我很想在 g0v 這邊討論有什麼樣標準可以判斷哪些公司負責人姓名公開有其公共利益不適合遮蔽，哪些公共性較低可以遮蔽，如果有我認為很不錯的方法我會處理公司負責人姓名的遮蔽。
但你可以先當作我拒絕你的請求，如果你想要主張個資法第13條的話

Isabel Hou  21:52
這裡有個問題，如果要判斷「哪些公司負責人姓名公開有其公共利益」，就必須在同意移除前，取得更多個人資訊，但當事人未必願意。

chihao:ocean:  21:52
不知道可不可以有公開的清單紀錄哪些 g0v 專案收到了哪些隱蔽資料的要求，還有隱蔽了哪些內容？
> Isabel Hou  1 day ago
記錄了哪些隱蔽內容，不就沒隱蔽了ＸＤ

> Ronnywang  1 day ago
https://github.com/cofacts/takedowns
cofacts 就有放在 github
>>cofacts/takedowns
這裡會放 Cofacts 管理團隊接獲申訴後，手動修改資料庫，修改訊息、回應等的處理結果。
Website
https://cofacts.g0v.tw
Last updated
a month ago
Added by GitHub

>chihao:ocean:  1 day ago
剛剛也是想到 cofacts

>pichuchen  1 day ago
可以記錄某個統編他想要隱藏某項資訊

>kiang  1 day ago
foundations.olc.tw 還蠻常收到的，甚至直接打電話來還不表明自己身份

>chihao:ocean:  1 day ago
那怎麼知道要移除什麼 XD

>Isabel Hou  1 day ago
所以@ronnywang 根本不知道對方要他移除什麼，直到我問他是不是要移除姓名。

>kiang  1 day ago
他就一直盧，要我先答應他他才要告訴我

>Isabel Hou  1 day ago
這就是我在前一則發言說的「如果要判斷「哪些公司負責人姓名公開有其公共利益」，就必須在同意移除前，取得更多個人資訊，但當事人未必願意。」

>S.  1 day ago
@isabelhou "所以@ronnywang 根本不知道對方要他移除什麼，直到我問他是不是要移除姓名。" - this is a false statement.
Ronny was clearly aware from the very beginning of what data I am referring to as I clearly stated that in my email sent to him on June 20th, 2021.

> Isabel Hou  23 hours ago
好，更正: @ronnywang 有提到S. 要求他移除姓名資和其他個資，但不清楚其他個資是什麼。@S. did mention “name among other data”. (edited) 

>S.  23 hours ago
@isabelhou I would appreciate it if you do not link to Github, given you keep records of these chats outside of Slack. Also, I was referring to the email I sent to him on June 20th, which was my very first message to him - in this email, I stated "my name" which is clear enough to understand, even by a person with a basic level of English (if someone wants to argue that).
I also made a test and translated my email via Google translate back and forth to see if, at any point, translation to Mandarin would fail, rendering my message unclear to the recipient. That was not the case, even after translating the message to Mandarin, any person would be able to comprehend it and answer it the moment they acknowledged it. (edited) 

pichuchen  21:54
不好意思我又要用中文發一篇了。
具體來說我認為 @S. 提的這個問題不是完全沒有道理的，但是公司公示資料的表示方式各國作法不同，有些確實也是十分老舊需要作法，但這不代表台灣就得 跟著新加坡的作法去做。
我剛剛去看一下新加坡的作法，基本上新加坡政府網站有公開資料以及需要付費的兩階段作法，公開資料部分也有被複製到其他第三方網站，公開資料不含負責人姓名，但是含註冊地址，付費資料一筆需要約 SGD 5.50 元，裡面含股東姓名，ID 國籍 個人住址，因此真的沒辦法說台灣或是新加坡哪邊的作法比較好，但是已公佈住址為例，可以確定的是他對於有兩間房子以上的人會比較有利，因為他不一定會住在登記住址上，因此可能可以免於騷擾。
另外再讓我舉以日本為例，日本政府印象中早期沒有提供一個官方的平台來揭露公司資訊，但是如果是上市公司的話可以在 Yahoo.jp 查到資料（對，民間公司），不過日本公司慣例上會在自家網頁上主動揭露公司資訊，包含董事長（代表取締役）姓名，但通常不會有公司統編（也有可能是這東西才剛推不久的關係）。
不確定有沒有其他取得非上市公司取得公司董事資訊等的方式。
那需要付費才能取得資訊的系統舉例來說台灣的戶籍謄本系統就是這樣，需要一張約20元台幣，然後要在指定時間才能使用。所以資訊需要付費不見得是完全不能接受。
另外是公司資料應該要登記什麼？早期台灣的公司登記還有提供「印鑑證明」，後來發現這個東西根本於法無據，所以就取消了，而最近開始導入工商憑證之後，政府也朝著廢除大小章的方向進行，另外是目前台灣公示資料會有「登記資本額」和「實收資本額」，但是對一般民眾來說恐怕不是很清楚這兩者的差別，多一項資料反而多一次令民眾陷入錯誤的機會。因此在前一次的公司法修法也對於閉鎖型公司取消股票面額以及登記資本額登記。
所以說是否公司資料一定要顯示負責人姓名這點確實是有討論空間的，在留著的益處沒有很大，但是對於沒辦法找到人頭的公司負責人來說造成的損害較大時，或者是阻礙了外國人來台設立公司的意願時，其實也不是不能討論移除的，不過就像是前面提到日本的案例一樣，日本人覺得在自家網頁上放上負責人姓名是一件自然而然的事情，所以台灣人也沒有特別認為公開負責人資訊有特別奇怪這樣。

>S.  1 day ago
One thing is for sure: I never had a case in Singapore where one of my companies or my PII data would be copied and displayed publicly over on various non-government websites. So this model works well and I can vouch for it. It’s a win-win for both sides - general public and company shareholders. (edited) 

>Caleb Rogers  1 day ago
由於資本主義的性質，公司及其所有者比個人擁有更多的權力。 個人必須集體行動以壓制公司。 集體行動的一種方法是利用國家迫使公司為人民的利益行事。 我認為公司向公眾隱瞞信息是不道德的。 無論如何，所有公司都依賴於公共資源而存在，並且在使用公共資源時不應該允許他們保守秘密。

>Caleb Rogers  1 day ago
due to the nature of capitalism, companies and their owners have more power than individuals. individuals have to act collectively to overpower companies. one method of collective action is to use the State to force companies to behave in the interest of the people. I believe it's unethical for companies to hide information from the public. One way or another, all companies depend on public resources to exist, and they shouldn't be allowed to keep secrets when they are using public resources.

>Isabel Hou  1 day ago
戶籍資料跟公司負責人姓名不能同等類比，前者是個人資料，後者是依公司法必須公開的資料。

>S.  1 day ago
@Caleb Rogers somehow, if my users/customers ask me to delete their personal information, I don't make a fuss about it. So no, not every company is an evil and act against you. We are people too.

>pm5:spock-hand:  1 day ago
To reiterate what @isabelhou has just mentioned above, company owner's data is different from personal data, as in the former is required to be made public by laws.  Let's no get side-tracked from your original requests, shall we?

>chihao:ocean:  1 day ago
I am people too :orange_heart:

>S.  1 day ago
@pm5 let me reiterate it again: I don't have anything against an idea where a person wants to access information about the names of the company owners, if needed.
But currently, the way this data is available, is up for the abuse and I reiterated it why and how multiple times here. I also introduced model used in Singapore and explained why their model is better. Once again: I never had in Singapore a single occurrence where my PII would appear on random website. So the model clearly works. (edited) 

>pm5:spock-hand:  1 day ago
Yes, completely understand the situation you're facing here as best as I can.  But we are in Taiwan's jurisdiction.  You have a company registered in Taiwan.  I failed to see why this isn't discussed under the current Taiwanese law, as @pichuchen has been trying to provide, but in Singapore's examples.

>S.  1 day ago
Well, let's put it this way: in Taiwan the privacy laws clearly aren't the best and there is a room for improvement.
But even that, regardless of current laws and a country we are in, people also have some moral ethics right?
For all the years I have been running a business, we (my colleagues or me) never rejected someone's query if they wished their PII to be removed, be it their name, or their email or a credit card information. We don't need to consult a lawyer or ask them further questions, we simply remove their data. And we don't do this out of fear that law is on X side here, we do that because this is a right thing to do.
So law is one the thing, but being a good human is another thing.

>Kevin.  1 day ago
i don't really think you're making a strong case for the 'good human' thing but to each their own i guess

>Yi-Chung Dzeng  1 day ago
In case it wasn’t clear, I sincerely disagree with your ethical arguments in this case, and consider it just and fair to reject your request to remove your name from Ronny’s site.

>Kevin.  1 day ago
to me, being a 'good human' doesn't mean coming into an online community, mocking other people's English abilities, calling them 'stupid', 'dogs', threatening them with lawsuits even as they try to contextualize and understand the nuances behind the situation you're facing.
if you're here trying to make a good-faith case appealing to our common humanity, I would try a different tact next time round!

>S.  1 day ago
Please don't take things out of context and see what circumstances I found myself in.
>1) someone in your community, without my knowledge, uploads and provide via API my PII
>2) when I found out about this, I tried to contact multiple times the author, and was ignored
>3) I didn't ask myself to be here, I was forced out of lack of other ways to reach to the maker of the project. If the author answered my email, I wouldn't be here now.
>4) when after direct message to the owner I still had no reply, I took matter public
>5) when I took it public people misunderstood me and acted like they only care about the law (edited) 

>pm5:spock-hand:  1 day ago
Totally agree that the laws are a baseline, and we people can act by our conscience and moral ethics.  Then again, the PII made to your companies, if I'm not mistaken, probably is not requesting to remove a company owner's data?  Which, as you must've understood by now, does involve public interests, and there are equally justifiable moral arguments to make them public as @ronnywang has given here -> https://g0v-tw.slack.com/archives/C02G2SXKX/p1627483066268000?thread_ts=1627475447.172500&cid=C02G2SXKX (edited) 
>>Ronnywang
但這方法也適用於郭台銘以及任何立法委員或其配偶姓名嗎？如果是的話就比較等於方法1了，而這樣可能會讓之後想要做一些公司與立委之間利益迴避的研究的計劃難以進行
From a thread in #general | 28 Jul | View reply

>hkazami  1 day ago
I really don’t think we should spend time on discussing who are good human and who not. The reason why this case raised such a big discussion is exactly that this community here cares the public interests as well as the privacy of everyone on this planet. In the end, we all are private person and general public at the same time, aren’t we? (edited) 

>Kevin.  1 day ago
i understand where you're coming from but I disagree. i think there are two conversations to be had here. at the end of the day, we have a CoC and I believe it was violated.

>Kevin.  1 day ago
i come to  g0v more than any other online community because this is a safe, kind space, and how we respond to these incidents defines the future of this community.

>hkazami  1 day ago
Back to the case, S. said in this discussion above, “But currently, the way this data is available, is up for the abuse and I reiterated it why and how multiple times here.”
If THE WAY this data is available is the problem of S., then what if the government itself made this data so available and easy-to-use that a third party can take it without effort for commercial use? Should the government take this data down? Or should it make it so hard-to-use that it impedes the use both commercially and for public interests? If the privacy and public interests cannot be satisfied simultaneously (which is obviously the case), what should we (you, Ronny, the community here, everyone in the society, and the government) do?

>S.  1 day ago
So before you point fingers, see what lead to this situation.
I am not the one who is wrongdoing here.
Instruct your members that if they want to process someone's PII, they might get queries like mine and it would be nice if they at least somewhat showed they care and responded to emails. Otherwise this doesn't put you in the best light if you just act nice when things go public.

>S.  1 day ago
You have community and CoC, I have a right to ask questions when you process my PII, is simple as that.

>Yi-Chung Dzeng  1 day ago
The circumstance you are in, as I understand, is that the following two pieces of information - your name and its connection to the business you own - being recorded and passed around publicly by non-government bodies.
And I consider this circumstance fine. (Also speaking as someone affiliated with a now-dissolved corporation registered in Taiwan, but it shouldn’t affect the argument either way). Registering a corporation lets you create a legal person and redistribute certain responsibilities. The least one should do would be to disclose the identity of the representative natural person, so the chain of responsibility does not lead into thin air. (that easily)
And in fact this level of data visibility has lead to the discovery of questionable public project biddings before, which visibility projects similar to Ronny’s has contributed greatly to, including his own. This is a very good example of “forking the government” IMO.

>Yi-Chung Dzeng  1 day ago
Also please understand that no one here is in the position/habit of instructing another. The best we do will be to advise or suggest.

>pichuchen  1 day ago
@Caleb Rogers 其實我完全不同意你的看法就是了，台灣可能有一大票的新創公司他的實收資本額小於一間在台北市的公寓，所以到哪邊的資本能量較強沒辦法從他是否為公司這點做判斷。
這部分應該是您對「公司」這個組織型態有所誤解，原則上公司是種以該國法律規定所規定的法人，有點類似「社團法人」「財團法人」這樣，而公司原則上是以營利為目的的法人（台灣公司法第一條）
那成立法人的好處主要在於財產等可以歸於法人名下，以及民事責任可以和自然人切開以保障自然人的安全，那早期台灣有規定最低資本額限制，有限公司需要五十萬元，股份有限公司需要一百萬元，現在已經沒有了，所以任何人都可以在台灣成立公司。
基本上成立公司本身會多多少權力我個人是沒什麼感覺，但是登記地址會多一大堆垃圾信是真的，然後如果辦公室電話登記住家的話，常常會有人打電話來說要找陳先生這種事問說最近有沒有需要徵才也已經習慣了。實際上有些大公司在進行發案的時候會希望可以對上的是法人而不是自然人，原因在於如果對上的是自然人，那必須要還處理勞健保、二代健保、稅籍資料，那在處理這些東西之前還要再處理個人資料同意書等等的，因此如果是法人對法人的形式的話可以讓事情比較單純，這個大致上是我想到成立公司最大的優點吧？

>S.  1 day ago
@hkazami actually, the way it was initially (this data on a government website, not easy to retrieve) was good. Only after Ronny picked it (he clearly acknowledged he wanted to make it more accessible to the public) and made an API, other websites started abusing it. So the solution was in front of our eyes for all this time - keep it in gov site in not so easy to access way. But I am afraid now this solution won't work anymore because too many people took note, so the Singaporean model seems to be a better fit. (edited)

>pichuchen  1 day ago
@S. Singapore is Singapore, Taiwan is Taiwan, Same-sex marriage in Singapore is illegal, but is legal in Taiwan. So you can't measure Taiwanese  moral by Singaporean moral, otherwise you will feel disappointment in Taiwan.
If I go to US and say that Taiwan is better because there are no guns and marijuana what would US people think?

>S.  1 day ago
Yeah, apple and bananas. But this is not my point here.
My point was, no need for the names to be copied all over the web, they can be in one place and have people inquiry for release when needed (by sign up or whatever).
It's a simple question really: Given you are a privacy-oriented person, would you prefer your PII to be spread and smeared across many unofficial websites, including websites that might abuse your data or risk it being misinterpreted or rather have it in one central place where this data is being accessed only when it's being needed? (edited) 

>Slackbot  1 day ago
https://i.giphy.com/media/lPulaaB9lDMnGZiivs/source.gif

>pichuchen  1 day ago
But, actually, in fact, there many website copy public data form their gov:
https://opencorporates.com/companies/sg/53142741B
https://xn--zcklx7evic7044c1qeqrozh7c.com/companies/6290803002968
https://www.tianyancha.com/human/2255808625-c61111911
So I think the only problem is Taiwanese (or Chinese) people believe that posting the owner's name of a company on Internet will make good public interest.
And @ronnywang make an ad-free website which just copy the public data from gov. So what gov provides, what they copy.
>>opencorporates.comopencorporates.com
101 TAIWAN FRESH MILK SOYA :: Singapore :: OpenCorporates
Free and open company data on Singapore company 101 TAIWAN FRESH MILK SOYA (company number 53142741B), 37 JALAN SAYANG, 418654
xn--zcklx7evic7044c1qeqrozh7c.com
合同会社ＡＭＰＨＩＢＩＡの企業情報(福岡県北九州市八幡西区)｜全国法人情報データベース
合同会社ＡＭＰＨＩＢＩＡ(福岡県北九州市八幡西区)の企業情報。全国法人情報データベースでは新規設立された企業、登記閉鎖した企業、企業の統廃合・合併情報などを住所情報や地図と共に網羅しています。営業に必要な新設企業リストの作成等にご活用下さい。

>S.  1 day ago
@pichuchen please note the fact that that data found on other, non-official websites in Singapore does not include names of people involved in the company. Names of directors/shareholders are gate-walled and only accessible through the official gov website.
This is done for a reason - to prevent bad actors from copying it carelessly. (edited) 

>Caleb Rogers  23 hours ago
@pichuchen 我並不是說每家公司本質上都是邪惡的，只是本質上更強大。 當然，也有異常值，比如你說的新創業公司。 當然，一家初創公司的權力不如一位億萬富翁。 但總的來說，創業公司比大多數人擁有更多的權力，因為如果它承擔的責任超過其價值，它可以宣布破產並消失。 就像你說的，有些人成立了個人公司，以將自己與責任分開。 他們通過這樣做讓自己變得更強大。 因此，公民有權知道是誰建立了這個強大的實體，因為它利用了公共資源和結構。
I'm not arguing that every company is inherently evil, simply inherently more powerful. and, of course, there are outliers, such as new startups, like you said. of course a startup won't have as much power as one billionaire. but in general, the startup has more power than most individuals, because if it becomes liable beyond its worth, it can declare bankruptcy and vanish. just like you said, some people form individual corporations to separate themselves from liability. they make themselves more powerful by doing so. and thus, the citizens have a right to know who established that powerful entity, because it leverages public resources and structures.

>Caleb Rogers  23 hours ago
@pichuchen Taiwan is better than the USA because no guns, but worse because no marijuana :wink: but then better again because boba tea

>S.  23 hours ago
@Caleb Rogers you clearly have no idea how the company operates and the laws it needs to abide by. Yes, that includes the privacy laws of its users/customers - and you can sue the hell out of a company if you feel at any point they misuse your PII.
So no, it's not like companies are not held liable for wrongdoings.
Now, if you really argue hard about "powerful billionaires" - trust me, if someone wants to hide something, they wouldn't be opening a company in Taiwan in the first place :wink: (edited) 

>Caleb Rogers  22 hours ago
You sue the company, and I wasn't talking about PII, I was talking about liability in general. Which does include PII but I was speaking broadly.

>Caleb Rogers  22 hours ago
"you clearly have no idea how the company operates and the laws it needs to abide by." i think you might benefit from reading https://news.ycombinator.com/newsguidelines.html under the "in comments" section, it's a good guide to general online behavior

>S.  22 hours ago
I stated a fact. Misinformation you spread is considered poor online behavior, do you know that? Not only does it misleads others, but also fuels up the anti-company consensus here in this community. (edited) 

>S.  22 hours ago
Furthermore, I suggest you study company's laws before you post things like "companies are more powerful".

>Yi-Chung Dzeng  22 hours ago
The fact of having limited liability already justifies the argument that companies are more powerful than a natural person. I guess this is what @Caleb Rogers means? (edited) 

>Caleb Rogers  20 hours ago
It's good to be anti-company, capitalism is inherently unethical :slightly_smiling_face:

>Caleb Rogers  20 hours ago
S, I'm actually correct companies hold more powerful in a capitalist society than individuals. You say, "study more," but I don't have to - I'm correct, and I've demonstrated why. If you have a counterargument, state it, don't just pretend you know more than me. (edited) 


chihao:ocean:  21:56
(maybe) comparative study ++

chihao:ocean:  21:58
:one:「政府做了民間就不能做」
:two:「政府做了民間就不用做」
:three:「政府沒做民間就先做」
:four:「政府做了民間繼續做」

>Tkirby:kirby:  1 day ago
不一定所有事都一樣, 但若光看"資料", 2. "政府有的資料你不用再釋出" 當成一種"不需要民間"的立論時, 會變成隱性的 1., 變相阻止民間做.
那同樣是阻止的情況下, 1 & 2 換個角度看會變成 "政府可以, 你不行"
言論也是一種資訊的散播, 再換角度看就會變成"政府可以說, 你不能說"
那就會扯到言論自由了

pichuchen  22:00
另外日本的法人番號是平成 27 年， 2015 年才開始的，真不知道他們在這之前是怎麼查核公司資料的...

Ronnywang  22:00
可能類似像美國沒戶籍制度一樣，要靠別的證明文件？

>pichuchen  1 day ago
我剛剛還看到日本還有一種叫做「匿名組合」，總之就我在台灣自己也是有開公司來說，我可以確定台灣的公司法以及相關規定相較其他國家有改進空間，然後近幾年來說經濟部也是很正面在配合修改這樣，只是像是到底應不應該表示姓名這件事情，真的沒拿出來討論還沒有認真想過這件事。

>chihao:ocean:  1 day ago
難道要開坑寫公司法修正草案了嗎 :smirk:

>Isabel Hou  1 day ago
為什麼需要公開公司代表人姓名？最基本的原因是保障交易安全。交易相對人必須透過公司登記資料，確認「代表公司與之交易的人」有代表權限，交易相對人可以信賴登記資料，如果登記資料沒有公開，就無法簡便地確認是否有代表權限。

>Yi-Chung Dzeng  1 day ago
公開公司代表人和監察人也能讓利益衝突更容易被發現

>pichuchen  1 day ago
@isabelhou 但是實務上我們也很少真的在交易時確認登記資料上的姓名，舉例來說早餐店的登記姓名我們是幾乎不會查驗的，再來是例如全家等等的可能是加盟店，另外合作窗口也常常不會是董事或是董事長本人，更多的時候是專案經理，那此時我們其實驗證是否有權限的資料往往是對方的名片，因為名片上面有 Logo ，造假的話確實有偽造文書或詐欺的事實，那此時是不是公司代表人姓名就沒有這麼必要了？

>Isabel Hou  1 day ago
並不是。@pichuchen 這可以大松見面聊。 (edited) 

>pichuchen  1 day ago
@chihao 搞不好可以轉 #digital_development

>pichuchen  1 day ago
@Yi-Chung Dzeng 確實是這樣，但是這個基本上是在公司結構比較簡單的狀況下是這樣，實際上的話有可能讓比較小的股東來當董事，或者是掛名董事長，然後再由大股東作為實質受益人，所以從幾年前開始就要求公司必須要再做「公司負責人及主要股東申報」來做洗錢防制 （ctp.tdcc.com.tw）
那在這上面的資料目前政策是不對外公開的。

>Li-Hsuan Lung  1 day ago
以美國來說各州搜尋公司資訊的方式不一，不過印象中還是要向相關單位正式申請和繳付手續費。以我在紐約的經驗，基本上除了向政府登記時需要提供我的個資，實際上和客戶簽約和交易的時候我只需要提供我的公司名(DBA)和税碼(EIN)。當然對方是否信任我和如何聯絡上我是另一回事。
不過我覺得討論的方向其實有點偏了，政府是否應該(不設門檻)公開公司代表的個資的確滿值得討論，但是這邊的重點應該是作為公開資料的傳播/使用者(data processor)而非搜集資料的政府(data controller)需要負責哪些法律責任？

>pichuchen  1 day ago
@naush 我覺得公開資料的傳播應該討論的差不多了，大部分的意見似乎都是認為 @ronnywang 的作法合法，不過 @S. 看起來接下來是打算採取法律途徑的樣子，因此可能後面就是在法院上看法官見解了。
但是在台灣政府的案例來說，顯不顯示名字的這件事確實沒有那麼簡單

>pichuchen  1 day ago
像是我們知道經濟部商業司是覺得放出負責人姓名是 OK的，但是財政部財資中心覺得不OK https://data.gov.tw/dataset/9400
那依據法務部 10504633830 函，法務部的意思看起來是「你們覺得ＯＫ就ＯＫ，不ＯＫ就不ＯＫ」
>>政府資料開放平臺政府資料開放平臺
全國營業(稅籍)登記資料集
全國營業(稅籍)登記資料集。因考量營業稅歷年停歇業資料量太大，開啟檔案困難，故所開放檔案僅涵蓋營業中資料，並建議使用Microsoft Word Viewer開檔，中文請選UTF-8中文碼；或使用Notepad++、UltraEdit等其他工具開檔。 資料連結於109年6月22日調整為https://eip.fia.gov.tw/data/BGMOPEN1.zip

>pichuchen  1 day ago
所以就說需要專責機構吧

>Li-Hsuan Lung  1 day ago
目前的做法似乎是建立在傳播方完全沒有任何法律責任的基礎上，所以個人可以判斷要不要移除個資，但是我覺得可能沒那麼單純？:thinking_face:  畢竟我記得歐盟有對data processor訂立特定的法案，尤其是牽扯到個資。不知道台灣這邊會怎麼判斷就是了:shrug:

>Isabel Hou  1 day ago
@pichuchen 稅籍登記和公司登記是不同的資料。依據法律需要公開的範圍也不一樣。 (edited) 

>Joy.Wang/kingman  1 day ago
雖然我們在小規模的交易不會去查核負責人的資料，但是正式合約、公司文件，除了早期公司紙本營登查核以外，通常都還會要大小章
這應該是可以引申公司負責人的姓名，同等於公司資料的一部分，甚至包含負責人的ID，負責人的姓名資料，並不只是負責人的個人隱私資料而已
當然現在走無紙，以及法律、社會環境改變，這個有在逐漸變化中。 (edited) 

>pichuchen  1 day ago
@kingman 這個我可以再分享一下，今天和經濟部那邊通電話的心得。
因為我們家最近變更董監事，所以要做變更登記，然後上面就說可以用工商憑證做純電子送件，不然我們就還要再蓋一張有大小章的紙寄到新北市政府。再不然就要等疫情結束臨櫃辦理，所以我們就選擇純電子送件。
純電子送件回來的東西他就沒有大小章了，那政府的說法是從此我們公司的大小章就不在政府登記的資料裡，一切以工商憑證為主，然後回來的公文是我們自己列印。
那現在自己列印的東西要怎麼驗證真偽呢？所以經濟部有個查驗平台，但是好像沒有申請方式，所以我就直接寄部長信箱去問這件事，所以今天早上他就打電話來和我溝通了。
經濟部的說法是查驗平台主要是像是銀行、投標公家機關、申請台電台水等等需要確認這間公司存在。那在一般民間的狀況來說，大部分的大小章本來就不一定一定要是公司登記的那個章了，原先的法律就是支援用簽名的，只是大家習慣要蓋大小章，但是也不是真的會去查驗那個大章就等於是公司登記的那個大章。
就民法來說，其實如果能夠知道合約上的雙方意思表示一致這樣就夠了。

>Joy.Wang  1 day ago
恩，我也是有申請工商憑證，現在很多電子化作業用這個東東代替了很多簽核(尤其煩人的健保，以及無法解決的智障勞保系統)，也省下很多事情
而現在申請公司，甚至可以是用自然人憑證做幾乎全線上電子化作業(雖然後續還是有很多地方要跑)
這也是我認為時代和社會演變，負責人與公司的關聯性變化的原因
但回過頭來想，線上公司申請，仍然是以負責人的自然人憑證(或者說任何可以代表負責人的資訊)為唯一的發動依據
"負責人" 與公司法人之間的關聯性，還是非常深，公司的負責人資料，已經並不只是普通自然人資料了 (edited) 

>pichuchen  1 day ago
那個狀況應該是因為是自己送件，如果不是自己送件的公司登記那就不一定要用負責人的自然人憑證，我們一開始是我用負責人的按，後來被會計師事務所整個打掉重來，然後他幫我們送上去的。
那至於目前傳統上確實台灣的負責人和公司之間的關係綁很深，經常公司借貸還會需要負責人作為連帶保證人的（會影響聯徵），那實際上也不是只有公司，像是社團法人的理事長也會有特殊待遇，曾耳聞有理事長交接之後新任理事長偷懶沒去改登記，然後前任就一直被國稅局找麻煩。
但是這是小公司的情況，實際上我們想追的應該是大公司之間的交叉關係嘛，舉例來說我們知道東森電視背後的老闆是茂德集團，但是如果你去查茂德建設的董事長就會發現他和東森電視的董事長其實不是同一個人。

>Yi-Chung Dzeng  1 day ago
我認為大公司之間的複雜關係更加能顯示現行資料集的效用，如你說的東森：
http://company-graph.g0v.ronny.tw/?id=86121480

>Isabel Hou  1 day ago
有檢調提過，他們會用這個網站調查公司間的關聯。

>Also sent to the channel
>Joy.Wang  23 hours ago
這幾天的事情有感，其實不只大公司披露股東、負責人對於交叉關係的公開顯示與公共事務有益，就算是中小、微型企業，負責人的公開揭露與方便易查對於中小微企業以及個人之間也是有影響的。
如最近才剛發生的台南某遊戲動漫負責人本身道德及言行造成公司內外的各種風波，這種負責人本身信用、道德的問題，小微企業之間可以查核負責人本身及其過去經營的公司有無狀況，作為是否要合作、交易的參考。
而同樣類似於這間公司所造成的職場、勞工問題，求職者也可以依據負責人過往的紀錄，檢視並評估所要求職的公司未來是否會發生同樣問題的參考。類似求職天眼通的作用。
小、微企業法人與負責人(自然人)之間的界線甚微，負責人的行為可以完全決定法人的模式，而負責人的信譽，某種程度上如商號一樣視為一體。
就像我們在拍賣購物會參考對方賣場過去的評價，負責人的道德、信譽與過往行為是對於一間小型或新設企業體是否可信賴的重要參考依據。 (edited) 

Isabel Hou  22:46
>Isabel Hou
關於使用者@S. 昨天在討論串中的言論「Stop acting like a dog and start acting like a human.」我認為已經違反COC，請slack admin處理。
Posted in #g0v-slack | 28 Jul | View message

>Also sent to the channel
clkao:g0v:  24 hours ago
re coc. please see this thread. https://g0v-tw.slack.com/archives/C01RDCVDGHZ/p1627489521142200?thread_ts=1627483499.131000&cid=C01RDCVDGHZ
>>S.
@clkao appreciate that.
I would like to clarify my comments toward that person:
That referring to someone to "act like a human, not a dog" - I feel super uncomfortable with the way people turning this case around and attacking me - it's easy to act cold when you are in the pack and anonymous (at least some are) and it's not about their personal data.
So I felt like that member is completely out of touch with reality and does not listen, throwing at me empty thoughts without trying to understand the circumstances I am in.
@shivahuang apologies for the harsh words, I am sure you are a cool guy and we all have good intentions here. So peace!
From a thread in #g0v-slack | Yesterday at 00:25 | View reply

S.  23:02
I can clearly see what's the community consensus here. You feel attacked and start picking things out of context.
None of you acknowledged what really went behind the curtains and what exactly led to this situation and why I feel unhappy with the way I've been treated, before I even joined this Slack.

23:03
Therefore, feel free to remove me. I can't communicate with someone who fails to acknowledge their fault. (edited) 

S.  23:22
Mind you, it's not me who decided to upload my data and then ignore my emails.

So if you take on dealing with someone's PII, take the responsibility too and expect that data removal requests like mine will happen.

S.  23:29
“We don't like to be instructed how to do things here” - cool, then don't hold hostage and police someone's personal data.

>Yi-Chung Dzeng  1 day ago
This is a twist of my words. You should see that some of us here have more empathy towards your situation than others, however none of us have the authority to tell the actual project owner what to do. It’s fully up to him/herself to make a decision and stand by it.

>S.  1 day ago
Somehow you recognized that “twist of your words” so tell me something I don't know?
Also, I can give you at least 5 examples here where during my conversation someone took out of context what I said :/ (edited) 

>Li-Hsuan Lung  1 day ago
yeah there are definitely some miscommunication & language barrier issues here. but @Yi-Chung Dzeng brought up a good point here because ultimately g0v is more like a gathering place for people who likes to hack civic tech stuff together. there’s nothing any one of us can do to help you out, unfortunately. it’s kinda like going to 4chan/anonymous board and demand the community to take responsibility for what one anonymous user did.

>S.  1 day ago
“Anonymous” users who feel entitled to process not so anonymous data? What could go wrong, right? :thinking_face:

S.  23:30
I would never be here if the author of this project answered my emails in the first place. So now, take responsibility for his (in)actions.
23:31
It's easy to act cold when you are in the pack and it's not about your data you don't wish to have publicly copied over random websites, I get that.
23:31
#rantover

### 2021.07.29

S.  00:10
Btw I never mocked anyone's English abilities here - I challenge you to provide at least one example where I clearly do so.
When I mentioned anything related to language (or English in this regard), I had in mind here Ronny: I was told by another member of this community that Ronny can't express himself using English (Ronny even acknowledged it somewhere here too) and they said this could be perhaps the reason why he never responded to my emails or messages.
And I would certainly buy that excuse if not the fact that Ronny is 30-something and surely if he can use the computer, he can at least reply to my email in Mandarin.
Here is the proof showing that Ronny language abilities were mentioned by another member (redacted the nickname of the person so you guys don't bully them later too): (edited) 

>Caleb Rogers  20 hours ago
nah you just suck

>![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4e6bd25d1eb03f249f94ae1020be1937.png)

>Caleb Rogers  20 hours ago
i'm genuinely shocked at how polite people here are being to you, but it does align with my experience with taiwan. People here seem to be willing to take the harshest, most arrogant criticism from self-absorbed foreigners like yourself that think they know better, in stride. Remarkable and laudable. You're quite lucky :slightly_smiling_face:

>S.  19 hours ago
You forgot this one:

>![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fb276f34d098957f11d06351c24919bd.png)

>Caleb Rogers  19 hours ago
Nah lol

>Caleb Rogers  19 hours ago
Why are you still here? Your only recourse now is to sue. nothing here will get done. Are you joining our community now? :slightly_smiling_face:

>國鈞  17 hours ago
@Caleb Rogers I think your first comment in this thread is against the community code of conduct https://g0v.hackmd.io/s/COC as in "Any sexually explicit, violent or discriminatory language and/or imagery is inappropriate at any online or offline community event/space", as for now, I don't have enough energy to take this to the admins. But this ought to be noticed.
>>HackMDHackMD
g0v 行為守則 g0v Code of Conduct - HackMD# g0v 行為守則／g0v Code of Conduct (CoC) ## g0v 社群守則（0405 定稿版） > 4/19 前，提至 slack #general，若社群沒有其他異議即通

>Caleb Rogers  17 hours ago
Thanks Guo-Jim! I'm happy to talk with the admins about it. You and I have met in person, have we not? I'm curious why you didn't DM me directly :slightly_smiling_face: I disagree that it was anything like you said, and I disagree that standing up to bullies is against the COC. Let's talk more about it though!

>Caleb Rogers  17 hours ago
Oh, you're a book club participant, that's why I recognize you.

>S.  17 hours ago
I am sorry but calling a person who came here publicly to talk about their data being leaked and abused for months (after being totally ignored by the author) a “bully” is not only misleading but also tasteless.
I am sad to learn that you identify a basic right to privacy as “self-absorbed”. (edited) 

>Caleb Rogers  16 hours ago
Crocodile tears

S.  00:18
CleanShot 2021-07-29 at 00.13.36@2x.jpg 
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6267969b76006b9c92dbbb2edc7fe7af.png)

S.  00:38
Things always work like this: Is not my business until it is my business (no pun) :slightly_smiling_face: I get that people here might not understand or feel a need for a change now, but one day when they are in similar circumstances I am finding myself in currently, they will see things differently. (edited) 

Tkirby:kirby:  00:59
Thank you for trying to communicate with Mandarin earlier, and sorry that there are different voices since this is a community. Back to this case - I think the site's owner Ronny has responded above ( while in Mandarin ), perhaps you can open a dedicated thread by responding to his comment. This is a community so comments by others are not responsible for him and vice versa, thus you probably will want to discuss directly with him, whether he respond or not - and unfortunately we can't force him to respond once he follows g0v's CoC and local government's law.
Actually many people here have their names listed. I even have my full home address been published in those websites so I know how you feel -  Indeed we may need some updates in our government's law. (edited) 
>Ronnywang
很謝謝很多人提供法律上相關資訊，我這幾天錄完零時小學校的 QGIS 課程後，會想來把這些討論整理成共筆，是很有意義的討論。
我先回覆 @S. ，我無法給你時間，也無法保證我會將你的名字從網站上遮蔽，因為我目前還不覺得這是我一定要做的事。
我很認同隱私權的重要性，但我不認為姓名跟身份連結就一定是需要被保護的隱私。舉個例子，立法委員、行政院長的姓名也是個人資料，難道也是只有政府網站可以公告，民間網站提到只要當事人要求就必需將名字去除嗎？立委或官員的姓名可以被大家自由討論連結使用，有他的公共利益價值在，如果只有政府有公布的自由，對公共利益的傷害非常的大。
那問題就會回到，那公司負責人的姓名的公共利益的程度能跟立法委員和政府官員相比嗎？這問題就沒那麼簡單了，郭台銘和路邊飲料店負責人姓名的公共利益性就差很多了。但假如果今天網站提供了飲料店負責人可以申請遮蔽他的姓名，那之後郭台銘的法務也來說要我遮蔽，我要用什麼樣的標準同意飲料店的遮蔽卻否決郭台銘的遮蔽？這邊有幾個選擇：
>1. 誰來申請都幫他把資料刪除：這或許是你最認同的方向，就算郭台銘來也一樣有他的權利，但這樣這資料可能就失去很多公共利益性了
>2. 我可以審核哪些人資料可以幫他刪除，哪些不刪：如果有夠好的標準我覺得這會是個好方案，但我並不希望這是完全靠我個人的判斷，我沒有資格也沒有能力做這個判斷。
>3. 比照現有公司法以及商業司資料公布：這就是我選擇的現況了。
你前面主張政府也有提供這些資料，政府已經有公布了，因此該有的公共利益已經足夠，民間不需要做這些事。這點我並不認同，我當初會做這網站就是因為政府的不夠好用，這也是很多 g0v 的朋友為什麼會想要推動 open data ，我這邊公司資料也幫助了像台電30億敦親睦鄰追追追以及一些 g0v 專案，而這些都是政府本身作不到的。
Show less
Thread in #general | 28 Jul | View message

Yio Chou  01:15
joined #general.

S.  01:42
@tkirby cheers. Did you get your data removed at the end if you don't mind me asking or you also had to deploy your lawyers? :smiley:
The model that works well for both sides: companies and the general public is when the names of directors/shareholders are in one central place where anyone of interest, can request to have this information revealed.
This prevents bad actors from spreading PIIs across the web and abuse them, respecting the privacy of the owners. At the same time, it serves the general public's need for transparency and the ability to view the names if that need ever arises. (edited) 


>Also sent to the channel
>gugod  1 day ago
>>... where anyone of interest, can request to have this information revealed.
This prevents bad actors from spreading PIIs across the web and abuse them, respecting the privacy of the owners.

>This idea of making bad actors’s life a bit difficult to do their job seems to me a pretty good initiative as a follow-up on this question @ronneywang brought up for himself. Quote:
>>我很想在 g0v 這邊討論有什麼樣標準可以判斷哪些公司負責人姓名公開有其公共利益不適合遮蔽，哪些公共性較低可以遮蔽，如果有我認為很不錯的方法我會處理公司負責人姓名的遮蔽。

>link: https://g0v-tw.slack.com/archives/C02G2SXKX/p1627480060223100
While I cloud only make guesses on the reason @S. would want their names to be removed/hidden in the beginning of these conversations, I could agree on this particular statement from them.
That being said... I could also see why @ronnywang  (and looks like almost everyone who participated the conversation) would tend to discuss laws/standards/rules rather than just spending 5 minutes and process the case of @S. -- It would just take about 500 company-owners to take down @ronnywang entirely, which wouldn’t be so difficult.
OTOH @ronnywang  also made a strong case that up until now whoever utilize those dataset seems to hold good intent. Quote:

>>我這邊公司資料也幫助了像台電30億敦親睦鄰追追追以及一些 g0v 專案，而這些都是政府本身作不到的。

>link: https://g0v-tw.slack.com/archives/C02G2SXKX/p1627475447172500
If we could find a few cases/evidences of “bad actors” or would be the misuses, that would definitely make the statement stronger. And should be a good news for @S. as I’m pretty sure such that  the already-public company data is copied multiple time available on multiple websites and they could just reuse the same argument when sending takedown notices. (edited) 

HS W  07:39
joined #general.

gugod  09:22
replied to a thread:
@tkirby cheers. Did you get your data removed at the end if you don't mind me asking or you also had to deploy your lawyers? :smiley:…
>... where anyone of interest, can request to have this information revealed.

This prevents bad actors from spreading PIIs across the web and abuse them, respecting the privacy of the owners.
This idea of making bad actors’s life a bit difficult to do their job seems to me a pretty good initiative as a follow-up on this question @ronneywang brought up for himself. Quote:
>我很想在 g0v 這邊討論有什麼樣標準可以判斷哪些公司負責人姓名公開有其公共利益不適合遮蔽，哪些公共性較低可以遮蔽，如果有我認為很不錯的方法我會處理公司負責人姓名的遮蔽。

link: https://g0v-tw.slack.com/archives/C02G2SXKX/p1627480060223100
While I cloud only make guesses on the reason @S. would want their names to be removed/hidden in the beginning of these conversations, I could agree on this particular statement from them.
That being said... I could also see why @ronnywang  (and looks like almost everyone who participated the conversation) would tend to discuss laws/standards/rules rather than just spending 5 minutes and process the case of @S. -- It would just take about 500 company-owners to take down @ronnywang entirely, which wouldn’t be so difficult.
OTOH @ronnywang  also made a strong case that up until now whoever utilize those dataset seems to hold good intent. Quote:
>我這邊公司資料也幫助了像台電30億敦親睦鄰追追追以及一些 g0v 專案，而這些都是政府本身作不到的。

link: https://g0v-tw.slack.com/archives/C02G2SXKX/p1627475447172500
If we could find a few cases/evidences of “bad actors” or would be the misuses, that would definitely make the statement stronger. And should be a good news for @S. as I’m pretty sure such that  the already-public company data is copied multiple time available on multiple websites and they could just reuse the same argument when sending takedown notices. (edited) 

clkao:g0v:  09:42
replied to a thread:
關於使用者@S. 昨天在討論串中的言論「Stop acting like a dog and start acting like a human.」我認為已經違反COC，請slack admin處理。
re coc. please see this thread. https://g0v-tw.slack.com/archives/C01RDCVDGHZ/p1627489521142200?thread_ts=1627483499.131000&cid=C01RDCVDGHZ
>S.
@clkao appreciate that.
I would like to clarify my comments toward that person:
That referring to someone to "act like a human, not a dog" - I feel super uncomfortable with the way people turning this case around and attacking me - it's easy to act cold when you are in the pack and anonymous (at least some are) and it's not about their personal data.
So I felt like that member is completely out of touch with reality and does not listen, throwing at me empty thoughts without trying to understand the circumstances I am in.
@shivahuang apologies for the harsh words, I am sure you are a cool guy and we all have good intentions here. So peace!
From a thread in #g0v-slack | Yesterday at 00:25 | View reply

S.  09:52
@gugod Thanks for giving a healthy look at it.
We can agree that the current model serves only the consensus of the g0v side (transparency) and completely ignores the privacy of people in the dataset.
As much as some people here might disagree to introduce some level of protection and privacy to those in the dataset I strongly disagree it's right to have PII of 1000s of people up for abuse smeared over random websites because a bunch of people here wants to play police.
As long as my names appear on any non-official websites, without my consent, I will consider it as abuse. (edited) 

S.  10:06
I am not going to post in public chat the names of the sites that abuse this data, and give them any traffic/exposure.

Joy.Wang  10:07
replied to a thread:
可能類似像美國沒戶籍制度一樣，要靠別的證明文件？
這幾天的事情有感，其實不只大公司披露股東、負責人對於交叉關係的公開顯示與公共事務有益，就算是中小、微型企業，負責人的公開揭露與方便易查對於中小微企業以及個人之間也是有影響的。
如最近才剛發生的台南某遊戲動漫負責人本身道德及言行造成公司內外的各種風波，這種負責人本身信用、道德的問題，小微企業之間可以查核負責人本身及其過去經營的公司有無狀況，作為是否要合作、交易的參考。
而同樣類似於這間公司所造成的職場、勞工問題，求職者也可以依據負責人過往的紀錄，檢視並評估所要求職的公司未來是否會發生同樣問題的參考。類似求職天眼通的作用。
小、微企業法人與負責人(自然人)之間的界線甚微，負責人的行為可以完全決定法人的模式，而負責人的信譽，某種程度上如商號一樣視為一體。
就像我們在拍賣購物會參考對方賣場過去的評價，負責人的道德、信譽與過往行為是對於一間小型或新設企業體是否可信賴的重要參考依據。 (edited) 


clkao:g0v:  11:00
How opencorporates deals with the issue might be of interests. the privacy policy clearly states the why and what, which is probably what g0v projects can learn from. however it also states clearly why they do not remove individual data, citing GDPR article 89.

```
Note that our legitimate interest in providing a comprehensive and accessible record of information about companies means that we do not give individuals the right to have information about them erased other than as set out below
```
https://opencorporates.com/legal/public_records_privacy_policy
here’s the example of the opencorporate’s page on the company it self.
also for the uk house of company, it actually publishes the director’s address along with the name (i am not sure about how detailed the disclosures are for PSCs). and opencorporate requires a login to display the information. while the director names are still publicly accessible, which is a reasonable privacy protection imo. (edited) 
>privacy-regulation.euprivacy-regulation.eu
Article 89 EU General Data Protection Regulation (EU-GDPR). Privacy/Privazy according to plan.
Article 89 - Safeguards and derogations relating to processing for archiving purposes in the public interest, scientific or historical research purposes or statistical purposes - EU General Data Protection Regulation (EU-GDPR), Easy readable text of EU GDPR with many hyperlinks.
opencorporates.comopencorporates.com
Public Records Privacy Policy :: Info :: OpenCorporates
Free And Open Company Data On Public Records Privacy Policy :: Info
opencorporates.comopencorporates.com
OPENCORPORATES HOLDING LTD :: United Kingdom :: OpenCorporates
Free and open company data on United Kingdom company OPENCORPORATES HOLDING LTD (company number 11268479), Aston House Cornwall Avenue, London, N3 1LF

Carol  17:48
joined #general along with Guanwei.


mglee  22:43
replied to a thread:
To record the trace of this discussion before it is eaten by Slack (context: g0v.tw still uses a free version of Slack which limits scrolling back to see old messages)
同意是個重要需要記錄的對話，尤其是對社群未來處理各種開放資料及removal request，logbot 好像掛了？有人正在把對話存到hackmd嗎？
我們也需要思考極端一點的狀況，例如：由政府公開但不好存取的公共資料若含有個資>>被 g0v 爬下來做成更容易應用的 API>>除了公益性質的應用外，該API也被拿去用在非公益且對當事人有巨大傷害的應用上 (比如色情、暴力、假訊息)，g0v 作為資料的中介者 (讓資料變得容易存取的角色)，有 (a) 法律責任嗎 (b) 道德責任嗎？

clkao:g0v:  23:09
So, what would it involve if a g0v project is to set up a potential PII take-down process? (not specifically for company data, but also like cofacts, campaign finance, congress video archives, etc)
* legitimacy of take-down: a trusted (by the community and the public) entity will need to process the requestor’s identity, claims, according to the project’s policy.
* a transparency mechanism for the take-down histories, like some of the dmca transparency disclosures by many content sites.

difficulties
* staffing of the above mechanism.
* paradox of the additional PII required to remove PII, and the efforts to protect the additional PII during the communications
* since g0v projects are open source, not just hosting processed data - that is, the scrapers are available to public. anyone can still reproduce the vanilla results. if the take-down needs to happen in data-pipeline level, we’ll need a registry for the take-down records, which would be another place to store more PII.

past experiences
* cofacts seems to have some practice
* the congress video archive project had a takedown request from the source (the congress), because one congress member put some underage faces (or something that’s not meant to be broadcasted) in a video clip during presentation. it’s more like a correction request, as the upstream eradicated part of the video clip and wants downstream to republish the latest version.
(edited)

>>cofacts/takedowns
這裡會放 Cofacts 管理團隊接獲申訴後，手動修改資料庫，修改訊息、回應等的處理結果。
Website
https://cofacts.g0v.tw
Last updated
a month ago
Added by GitHub

>Isabel Hou  10 hours ago
For clarification, g0v is a polycentric community, i think every project owner and contributors have to develop their own policy and be responsible for the decision made accordingly.  However, g0v.tw needs a policy and projects using g0v.tw domain shall follow the policy besides the projects’ policy.

>S.  9 hours ago
@clkao appreciate the initiative - it's a much-needed change in a better direction. Also thinking about ongoing PII collecting/processing that meets both - transparency and privacy principles:
Pseudonymization of PII seems like a good solution - the public can still enjoy all the data queries and make connections between companies/individuals without passively revealing their names. The actual name can be looked up when such a need arises, safeguarding it from bad actors, abuse, and careless handling down the stream.
Also, a place to educate people who take on projects here to design/build things with privacy principles in mind is where we can all have a real impact.
Perhaps a section with materials on the official website?

>Quentin Brasseur  8 hours ago
+1 on education material and initiative. Personal data processing is not an easy topic - I even think it should be included in the program at schools :sweat_smile:
I agree with @isabelhou - it is the project's owner responsibility to comply with laws. At best, there could be another g0v project that could brainstorm and offer resources to help other gov'ers in their projects? I wouldn't start this project myself but happy to contribute and share thoughts if it's useful :)
PDPA isn't the GDPR but the GDPR could be a source of inspiration and good practices (also, GDPR may be applicable to TW companies in some cases) and https://noyb.eu/en could be an interesting resource. This movement was created by Schrems, who won cases against Facebook. They work on data privacy enforcement. A mailing list updates on the latest fines issued by data authorities in Europe... the perfect examples to understand what is "touchy" :)
>>noyb.eunoyb.eu
My Privacy is None of Your Business
Noyb - European Center for Digital Rights is a non-profit organization based in Vienna, Austria. (27 kB)

> Also sent to the channel
Johnson Liang:orz:  3 hours ago
Cofacts 的脈絡是這樣的
>1. 2020 年一月有盜版影片在 Cofacts 上流傳
>2. Cofacts 信箱收到來自中國維權公司的信件，隨信附上營業執照與版權方律師函
>3. Cofacts 製作 cofacts/takedowns、公告來信但遮除個人聯絡資訊（原信有署名與電話，但公告時刪除，留下公司名稱）
>4. Cofacts 遮除文章裡面的侵權連結，但保留原文。
>
>Cofacts 工作小組（Cofacts WG）也有處理過更隱私的訊息流出到 LINE 的狀況。因為真的是不具公眾利益的私密訊息，所以我們在盡可能少的人看到的狀況下就以全篇遮除的方式處理，也不會透露是誰回報的。
>另外，Cofacts WG 也有收過一些來自執法機關要求特定訊息下架的 request。我們評估之後認為把訊息留著，反而更有助於澄清，而從熱門程度也可以判斷，就算下架該訊息，也會有人再回報一則一樣的，所以並沒有對資料庫做更動。在我們回信說明清楚之後，執法機關回覆表示理解，也比較少來信了。
最後，我個人認為 Cofacts 與台灣公司資料專案性質差異甚大，在 Cofacts 專案的決策，並不代表台灣公司資料專案就應該跟進。Cofacts 上的訊息與回應，都是使用者所回報，與台灣公司資料直接使用政府開放資料、增加相關資訊的近用性，有著本質上的不同。Cofacts 上的資訊是從私領域（LINE 聊天群組）回報的訊息，故個別的訊息是否具有公眾利益，確實有個案探討的空間。 (edited) 

### 2021.07.30

Guo-Jim  5:01 AM
開了記錄請求個資刪除聊天室紀錄的共筆，目前記錄到 2021.07.27 10:56 PM https://g0v-tw.slack.com/archives/C02G2SXKX/p1627397788471900

Charlie Smith
@Charlie Smith has joined the channel
Posted in #general | Jul 27th | View message

共筆連結
https://g0v.hackmd.io/D9M2zAJJRqW_1qYZDmRKAA?both

然後還有 #g0v-slack 頻道 的討論還沒記錄

Guo-Jim  8:58 AM
大家來幫忙複製貼上，還有不少

johnshao  9:53 AM
我把#general 剩下的都複製貼上了(應該沒有漏吧?! (edited) 

Johnson Liang:orz:  11:03
replied to a thread:
So, what would it involve if a g0v project is to set up a potential PII take-down process? (not specifically for company data, but also like cofacts, campaign finance, congress video archives, etc)…
Cofacts 的脈絡是這樣的
1. 2020 年一月有盜版影片在 Cofacts 上流傳
2. Cofacts 信箱收到來自中國維權公司的信件，隨信附上營業執照與版權方律師函
3. Cofacts 製作 cofacts/takedowns、公告來信但遮除個人聯絡資訊（原信有署名與電話，但公告時刪除，留下公司名稱）
4. Cofacts 遮除文章裡面的侵權連結，但保留原文。

Cofacts 工作小組（Cofacts WG）也有處理過更隱私的訊息流出到 LINE 的狀況。因為真的是不具公眾利益的私密訊息，所以我們在盡可能少的人看到的狀況下就以全篇遮除的方式處理，也不會透露是誰回報的。
另外，Cofacts WG 也有收過一些來自執法機關要求特定訊息下架的 request。我們評估之後認為把訊息留著，反而更有助於澄清，而從熱門程度也可以判斷，就算下架該訊息，也會有人再回報一則一樣的，所以並沒有對資料庫做更動。在我們回信說明清楚之後，執法機關回覆表示理解，也比較少來信了。
最後，我個人認為 Cofacts 與台灣公司資料專案性質差異甚大，在 Cofacts 專案的決策，並不代表台灣公司資料專案就應該跟進。Cofacts 上的訊息與回應，都是使用者所回報，與台灣公司資料直接使用政府開放資料、增加相關資訊的近用性，有著本質上的不同。Cofacts 上的資訊是從私領域（LINE 聊天群組）回報的訊息，故個別的訊息是否具有公眾利益，確實有個案探討的空間。 (edited) 

billion lee:giraffe_face:  11:59
Some supplemental information, those taken down information were recorded in Cofacts database owing to “another individual”(third party) sent one to Cofacts. For instance, someone disclosed private messages intimately , I don’t think it is the same condition to a government public information or other crawling projects. (edited) 

Joshua Kase  12:10 PM
joined #general.

S.  12:22 PM
S.
Just wanted to point out that @Caleb Rogers's "Nah you just suck" & "Why are you still here?" violates the CoC.
I find it counterintuitive and disrespectful to the community that after a member is asked to issue an official apology for the things they said and they do so, another member still continues to mock them with screenshots of messages they made in the past and already apologize for.
Replying "nah you just suck" under someone's official reply to false accusations other members directed at them earlier, indicates not everyone here tries to find a common language.
Also, the "Why are you still here?" and similar remarks might suggest that members in this community have an inclination tow… Show more
Thread in #g0v-slack | Yesterday at 4:18 PM | View message

bess  1:07 PM
\ 零時小學校 Demo Day 2021-22 開放提案啦 / #edu
https://g0v-tw.slack.com/archives/CN64A1FHA/p1627621560001800 (edited) 
bess
磨了一陣子的「零時小學校 2021-22 Demo Day」終於登場了！
歡迎帶著你的提案來參加，跟社群一起邊學邊做吧，有機會的話，就可以登上明年一月的 Demo Day 舞台！
還請大家多多轉貼分享，非常感謝。

「零時小學校 2021-22 Demo Day」08.01-09.28 開放提案，帶著你的創新解決方案，跟社群一起協作吧！
開源，開放，教育從自己開始
為鼓勵開源專案發展，並推廣「開源」與「協作」概念，只要你對「零時小學校 2021-22 Demo Day」徵件主題有興趣，無論是否為學生或教職員，都可以試著在 2021-22 年提案頁面提出你的想法，讓想像變成可能！
徵件主題
• COVID-19 新解方
• 遠距教學解決方案
• 社群經營與基礎建設
• 教育內容
• 其他 #自由發揮
Show more
Posted in #edu | Today at 1:06 PM | View message

isabelhou  1:51 PM
S.
First of all - I want to say "I am sorry" to those who feel uncomfortable with me bringing this issue to the public in #general or if someone felt personally offended. I did not mean to cause havoc here.
I am coming with good intentions and for a good cause that is not just about me, but about anyone who might ever find themselves in a similar situation, regardless of where you come from or where you currently live.
I was patient with my explanations and I tried to be clear about the reasons behind it.
Yet, I can't help but notice that some people still trying to give me a hard time and I feel it's important to clarify it.
1) I was bullied by few members of the community that together, in consta… Show more
Posted in #rand0m | Today at 1:10 PM | View message

>isabelhou  5 hours ago
哎，我們盡量不要用 拇指向下啦。雖然我請 g0v-slack admin處理違反 CoC的行為，但我同時也認為 @S. 提出了很好的問題，後續的討論非常棒（雖然也吵得很兇ＸＤ）

>isabelhou  5 hours ago
後續希望『有人』能開一個hackmd 來討論 g0v.tw 的相關處理流程和可能的方法，然後在八月大松提案討論。

>isabelhou  5 hours ago
如果沒有人……

>Yi-Chung Dzeng  4 hours ago
覺得需要一個"不同意"的表符

>kjcl  3 hours ago
可是我個人並不覺得這是一個我可以接受的道歉。
人家應該是要徹底了解他在哪方面用的話是傷人的，而且承諾不會再次發生。我在他的道歉裡面完全沒有看到這種反省，而是“不好意思，我帶了一個重要話題來然後我被攻擊。你們不理解我的立場“。他連違反 CoC 都不承認，怎麼把這個當成一個能夠接受的道歉呢？
我只能代表我自己說：我不覺得他違反 CoC 這個問題已解決。我也不接受這個道歉。 (edited) 

>kjcl  3 hours ago
我在這方面可能有興趣，但是不知道有沒有到願意跳坑的程度... :joy:
https://g0v-tw.slack.com/archives/C02G2SXKX/p1627631494038900?thread_ts=1627624289.032000&cid=C02G2SXKX
isabelhou
後續希望『有人』能開一個hackmd 來討論 g0v.tw 的相關處理流程和可能的方法，然後在八月大松提案討論。
From a thread in #general | Today at 3:51 PM | View reply

>isabelhou  3 hours ago
我感覺有很多人站在坑邊觀望，現在就是不知道誰會（被）跳下去。

>Caleb Rogers  3 hours ago
Kjcl 確切地。 我仍然感到驚訝的是，每個人都對這個問題如此有禮貌和體貼。 即使他的問題是合法的，他也表現得像個惡霸。 他的道歉是有毒的和虛假的。 通常我會過早地得出結論，但我認為每個人都給予了那個人比他應得的更多的信任。

>Caleb Rogers  3 hours ago
如果像這樣的人像武器一樣使用受害，它會傷害真正的受害者。 我將在此消息中包含英語，因為我認為它翻譯得不好。

>Caleb Rogers  3 hours ago
if people like that use victimization like a weapon, it hurts true victims. I'll include the English for this message because I think it'll translate poorly.

>bess  2 hours ago
我也覺得大家真的很有禮貌、體貼以及為他人著想。

>isabelhou  2 hours ago
我覺得@Caleb Rogers 的中文進步神速。

>isabelhou  2 hours ago
老實說，我也覺得我在這個社群得到比我應得更多的信任。喜歡很有禮貌、體貼以及為他人著想的大家、雖然可能有不同意見，但堅持尊重Ronny的堅持的大家。 (edited) 

>chihao:ocean:  9 minutes ago
叫別人「停止狗一般的行為」不是說別人是狗⋯嗎？真心不懂⋯

>chihao:ocean:  8 minutes ago
沒有人的耐心是有極限的（？）

>chihao:ocean:  4 minutes ago
另外，我覺得這裡並沒有被 cause havoc 啊 XD 不時出現了很多有意義的討論嗎？

> acechen  20 hours ago (7/30 21:49)
@S.
I don't think in the g0v community, specifically in the issue you brought here, there was anyone trying to silence the opinions of others. Please evidence it. Besides, many people disagreed with you for their own reasons, why did you see it as community members bullying you together?
What did you mean by "I didn't call anyone a dog, I asked them to stop acting like one"? You clearly do not understand what CoC is: it doesn’t matter whether you used like or not, you have already offended someone regardless of what your intention or purpose was.
You gotta use other examples: your name, office address and phone number - as many people have pointed out - are attached to the company, not your privacy. I certainly don't want any private information of mine, my family or anyone else being revealed publicly, but this is not the case here.
Since you have mentioned it explicitly, I also encourage you to post your DMs exchanged between others after having both sides' consent, otherwise we don't really get the full context you meant. If you can’t, stop quoting others.
(edited)

> kingman  8 hours ago
我是能體會、理解他帶著怨氣而來，當自己很重視的事情長時間被忽略、漠視，心情上一定是不愉快的，後續處理上也會帶有火氣，這是人性。難免的，當然行為與口氣上就會有各種好鬥的表現與攻擊性的行為。
但是就如他所說的，英文不好可以用Google翻譯看英文信，但是以我來說，當我的信箱都是正體中文，偶爾的英文信有90%以上都是垃圾信，信件閱讀、視覺上當然會自動忽略，當然簡體中文的信件將近100%都是SPAM & Virus.
且他一直強調個人隱私有多麼的遭受危害，又說他不想提供那些正在使用他的個資傷害他的地方，不想給他們流量與曝光，這我也能理解這種心情，但是這種狀況我也無法理解他所說的危害。
尤其當他所提到的其他例子都是相關非因果或者關聯錯置，會更難讓我理解他所說的危害型態。
認真說，我也是個人公司的負責人，我與我身邊朋友的公司資料和姓名，甚至聯絡電話、Email、地址都是公開狀態，我非常想知道這會有多大的危害，我也會擔心。
但我真的無法理解他所說的危害...

> chihao:ocean:  8 hours ago
我也是無法，所以在 ronny 提案的那一串問他可能會有什麼危害 ._.

> chihao:ocean:  8 hours ago
至於對方列出來的東西⋯我還在想 XD

> Caleb Rogers  6 hours ago
@isabelhou 我的中文不是進步，是Google translate的進步。加油Google！

> isabelhou  3 hours ago
@S. I don’t support pseudomisation. As for log-in, it takes a lot of efforts to do that and that will need contributors other than Ronny.
isabelhou  3 hours ago (7/31 14:53)
Maybe @S. can propose  a counter solution based on Ronny’s and tag Ronny. This will help to develop and conclude the action items and what should be changed to the system.

:::success
Due to Hackmd's 1,000,000 character limit, please find the follow-up messages in :point_right: 
https://g0v.hackmd.io/aoJEAfBaT4isw3FRBaQAIw
:::