---
tags: infras, 基礎建設, g0v
---

# 2018 Slack -> Zulip Import Incident 

> [name=kjcl] 為了迅速寫資料，我先寫了英文。麻煩大家協助慢慢翻譯成華語 (To write more quickly, I wrote in English as I'm more comfortable with it. Currently working on translating it

## Incident Review Meeting:
* Prep:
    * Please read updates to [the Zulip issue](https://github.com/zulip/zulip/issues/18622), "Slack import should respect Slack's counterpart of EMAIL_ADDRESS_VISIBILITY."
* Meeting Time: [Fill out this poll](http://whenisgood.net/9h55m9x).
    * Meeting time set for morning (9am) to accommodate engineers from Zulip in California who wish to attend. They want to take feedback and understand how they can improve their import processes for the future. 
* Agenda:
    * Intros: 5 minutes
    * kjcl: Summarize incident (2-3 minutes)
    * chris: Not only "never have bad things happen" (this is *very hard* when systems are complex), but also "make good things happen more, because humans are resilient". The distinction comes from a school of thought that talks about Safety-I vs. Safety-II. Safety-II is the "make good things happen more" view. When faced with complexity and many points of failure that are hard to know about, it can be helpful to see what features of a system/process help things to go right, and replicate those features elsewhere.
    * Understand key systems/processes (in-depth; 30+ minutes?). "systems/processes" is intentionally vague: can mean pieces of software, lines of code, etc., but also things like checklists, policies, etc. For each one:
        * What do we *know* about it (and how it worked in the relevant situation)?
        * What do we *want to know* about it (and how it worked in the relevant situation)?
        * Fill in those knowledge gaps, or make plans to do so.
        * What did it do well? How could it be more resilient?
    * Summarize / assign action items


## Incident Summary 基本簡介
g0v participant kjcl had API Key and gave access to Zulip, a Slack alternative, allowing them to import all e-mail addresses of g0v participants into a Zulip server intended as a hackathon project for g0v participants. The server privacy settings were misconfigured, allowing anyone to see anyone else's e-mail address.
社群內參與者 kjcl 開了一個 API key 然後把 API key 發給了 Zulip, 一個做類似於 Slack 的通訊軟體公司/開元案子。 Zulip 透過了這個 API key 把 g0v Slack 裡成員的電子郵件帶到了一個 Zulip 服務器上。因為 kjcl 沒有設好 Zulip 組織的隱私權設定，所有裡面成員的電子郵件是公開給其他參與者的。

## Key Terms 技術細節定義
* API Key: 工程師為了去使用比較敏感的數據需要的一個密碼。我們通常登入一個電腦或網站的時候，會需要我們自己個人的用戶名跟密碼。API Key 也就是電腦跟網站認證的另一種方式。(Engineers use API keys to access private/sensitive information. Think of it like a password for computers. Just like you use your username and password to access a website, a computer uses an API key to prove to a website it can do something.)
* Zulip: [Zulip 網站](https://zulip.org/) 一個開元模式開發的類似於 Slack 的軟體。(Zulip is an open-source Slack alternative)
* Slack Import: 為了方便個個團體從 Slack 移動到 Zulip，Zulip 的員工有一個移動軟體。如果組織給他們一個 API Key 的話，它可以把你的聊天室，使用者，一次全部帶到 Zulip 去。(To help organizations migrate from Slack to Zulip, Zulip employees have an importer. If organizations give them an API key, they can migrate your chat history and user information directly to Zulip).
* Bridge: 一個允許兩個不同的軟體的使用者溝通的服務。例如：使用者 A 在 Slack 上面發一個訊息。使用者 B 在 Zulip 或者 IRC 上可以收到。(A piece of software that allows people on different chat apps to communicate. For example, User A writes a message on Slack. User B receives a message on IRC or Zulip. )

## Incident Timeline 事件時間表
* December 2018: 2018年十二月 
    * kjcl 有興趣試試看移動 g0v 的 Slack 到 Zulip。他創造了一個 API Key 以及下載了 Slack 的備份。(kjcl is interested in exploring migrating g0v slack to Zulip as an alternative to Slack. kjcl requests a data export of Slack messages and creates an API key.)
    * kjcl 把 API Key 給 Zulip 的工程師，符合他們所需要的資料。 (Kjcl gives the API key to the Zulip team in order to complete migration. )
* May 19 2021: 2021年五月19日：
    * (jothon team creates new policies around use/misuse of Slack API keys. An audit after the creation of this policy results in the API key that kjcl sent to Zulip being revoked. After this point, no more API key misuse was possible.) 啾松團寫了關於使用 API KEY 的新使用範圍。在查看現在各種 API Key 的使用的時候，把這個發給 Zulip 的 API KEY 解除掉。我們可以確認這個解除發生了之後，無法在採用這個 API Key 去查看使用者資料。
    * 
* May 26 2021: 2021年五月26日
    * kjcl 跟一個其他參與者/Zulip的員工開始設一個 Zulip 到 Slack 的橋 (bridge) 。（kjcl working with g0v participant/zulip employee attempts to set up Slack bridge with g0v.zulipchat.com. Requests permission.)
    * 社群內參與者開始加入 Zulip (g0v.zulipchat.com) 了解一下它的功能。(g0vers start joining g0v.zulipchat.com to check out Zulip's features. )
    * g0v 參與者發現 Zulip 允許他們查詢其他使用者的電子郵件。 g0vers notice that Zulip by-default sets e-mail privacy to public, allowing all Zulip users to see the g0v usernames of all users. 
* May 27 2021: 2021年五月27日
    * g0v 參與者表達 Zulip 現狀的一些一或。g0vers express concern over e-mail addresses being exported without permission. 
    * 社群內的 Zulip 員工把隱私權設定改成沒有人看得到使用者的電子郵件。 zulip employee/g0v participant responds and turns off e-mail visibility for anyone.

## Incident Impact 事件影響
* 2018年12月前所有 Slack 的使用者的電子郵件有被拷貝到 Zulip 的服務器上，以及公開了三年。(All e-mail addresses of g0v participants registered on the Slack before December 2018 were accessed by this API key. They were publicly accessible  for 3 years.)
* 我們沒有原因相信 Zulip 除了初次 import 使用者資料在之外還有透過這個 API Key 去做其他事情。我們可以透過跟他們的聯繫去確認。 (We have no reason to believe that Zulip ever used this API key for any other purpose than the one-time import. We can confirm with them.)

## Follow-up Action Items: 必處理項目
- [x] 解除被使用的 API Key (Disable API key that was leaked.)
* [ ] 跟 Zulip 團隊通信，了解一下他們的 Slack Importer 怎麼使用數據，然後確認只有電子郵件被 Importer 使用到。 Communicate with Zulip team to understand how their Slack importer uses data, and what other data may have been accessed. 
* [ ] 決定該不該刪除這個 Zulip 服務。如果該刪除的話，跟 Zulip 團隊確認一下刪除完畢。Decide if g0v.zulipchat.com should be deleted. If so, delete and confirm with Zulip team deletion has taken place. 

## Prevention: 怎麼防止類似的事件再次發生
* [x] 查看一下能不能夠把使用者電子郵件以及其他個人資料透過 API 的改善鎖住。 See if we can lock down user.email from being accessed by Slack API keys.
![好像不行](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_93c8d8561dac64bc830b2ef25119ff0c.png)
*好像不行*

## Question and Answer 關於事件的問答
*Please add your Slack handle and your question as such:*
> [name=slackuser] 問題? 
> [name=answerer] 答案

## kjcl and Zulip Team e-mail archive

Hi zulip employee,
I'm wondering if we could try the import again. I've set up a Matterbridge instance so this should be the last time. Thanks so much for your time! :)
Best,
kjcl

### On Wed, Dec 19, 2018, at 00:14, kjcl wrote:
Everything looks fantastic! Thanks so much, Tim! :)

Best,
kjcl

### On Mon, Dec 17, 2018, at 09:16, zulip employee wrote:
kjcl,

Sorry for the delay!  You should now be able to login to a properly imported organization as https://g0v.zulipchat.com.  The notes about how to login apply as before (we deleted and recreated the organization, so you should no longer be logged in).

Enjoy, and sorry for the trouble!

—
zulip employee

### On December 12, 2018, 6:28 PM PST zulip employee wrote:

kjcl,

Oops, there was a regression in the Slack import tool.  We're working on a fix and re-import -- will let you know when that's ready.  Sorry for the inconvenience!

—
zulip employee

### On December 11, 2018, 2:16 AM PST wrote:

Hi zulip employees
our help! For your information, I have just logged in, and I don't see any chats whatsoever and all the channels show no threads nor any messages at all. Am I doing something wrong?

Best,
kjcl

### On Mon, Dec 10, 2018, at 22:45, zulip employee wrote:
kjcl,

The import is complete!  As discussed, we renamed the existing g0v.zulipchat.com to g0v-old.zulipchat.com and your data is imported at g0v.zulipchat.com.  You team members will either need to use SSO/Google auth to login, or reset their passwords, since obviously Slack doesn't include users' passwords in their data exports.  For reference when you're potentially doing a final import, the data import process took about 30 minutes to run to completion.

Let us know if there's anything else we can do to help!

—
zulip employees

### On December 9, 2018, 12:55 AM PST support@zulipchat.com wrote:

Great! I've sent it to the person that does our imports; I expect he'll be able to do the import in the next 1-2 days.

Best,
zulip employee

### On December 9, 2018, 12:53 AM PST kjcl wrote:

Hi zulip employee,
The Slack API token is here: 
<REMOVED></REMOVED>

Thank you!
Best,
kjcl

### On Sat, Dec 8, 2018, at 20:31, zulip employee wrote:

Thanks for the kind words :).
I realized we need one more thing, a Slack API Token. Instructions are at https://zulipchat.com/help/import-from-slack.

zulip employee

### On December 7, 2018, 10:53 PM PST kjcl wrote:

Thanks! Uploaded! Heads-up, this is not the newest export, but it would just serve as a way for us to see what our Zulip org would look like with current Slack data. In the future, we may have to do another import with our newest data. I hope that's okay!

(To you as a human being, I love how much thought you're putting into all of your answers and thank you so much for your hard work :) )
Best,
kjcl

### On Sat, Dec 8, 2018, at 09:49, zulip employee wrote:

Hi kjcl,

You can upload it to https://www.dropbox.com/request/puFw1k091rFS0QVmcGzK

I should also note that we can't merge Zulip organizations (or import into an existing Zulip organization). I can rename g0v.zulipchat.com to something else (like g0v-old.zulipchat.com), and then import into g0v.zulipchat.com if you'd like?

zulip employee

### On December 7, 2018, 9:18 PM PST kjcl wrote:

Hi zulip employee,
I'm trying to e-mail the slack import.zip to you, but gmail on your end appears to be blocking the zip file from being delivered. Is there another way I can get the data to you to do a test export?

We currently have a test instance on g0v.zulipchat.com and that's the desired subdomain we want to work with!

Best,
kjcl

### On Sat, Dec 8, 2018, at 06:10, zulip employee wrote:

Good question.

On our side, if you have a lot of history, we recommend doing a test export and import with us before doing the final cutover, in case something particular in your data hits a bug in our import system.

Other than that, you'll want to read
https://zulipchat.com/help/getting-your-organization-started-with-zulip
https://zulipchat.com/help/moderating-open-organizations

and maybe send your users
https://zulipchat.com/help/getting-started-with-zulip
https://zulipchat.com/help/about-streams-and-topics
https://zulipchat.com/why-zulip/
(though of course all of these are in English).

I think a lot of the bigger open source projects tend to switch over gradually, but they generally also aren't worried about preserving their slack history or porting users over. So e.g. they'll first move one working group over, then another, and over time (like months) things will drift from whatever they were on before onto Zulip. Not sure if that helps.


zulip employee

### On December 7, 2018, 6:55 PM PST me@liaokev.in wrote:

Thank you zulip employee!
May I ask if other communities have migrated from Slack before and the best practices for doing so?

Best,
kjcl

### On Sat, Dec 8, 2018, at 05:52, zulip employee wrote:

Done!

### On December 7, 2018, 6:50 PM PST kjcl wrote:

Hi zulip employee!
Thanks for your response! I've created a zulip workspace under the name g0v.zulipchat.com Please convert that to an open source plan when you have time!
Much thanks!

Best,
kjcl

### On Thu, Dec 6, 2018, at 05:56, zulip employee wrote:

Hi kjcl,

Thanks for writing in! We'd be happy to host g0v.tw for free, under our open source plan.

We do have a partial translation into Traditional Chinese, but probably not sufficient for someone who didn't speak English. I expect you could get it into a pretty good state with less than a day of work, especially if you skip translating uncommon error messages. To get a feel of what translating is like, you could create an account on https://www.transifex.com/zulip/zulip/ and try translating a few strings.

Best,
zulip employee

### On December 5, 2018, 6:18 PM PST kjcl wrote:

Hi All,
I hope this e-mail finds you well. I'm writing as a civic hacker in Taiwan. We have a large community of over 4,000 civic hackers working on projects that are open source and in the public domain. We are decentralized and our entire community relies on chat to collaborate.

I would like to propose to the community that we migrate to Zulip because of your open source hosting plan and also because of Zulip's threaded nature. Before I propose this, I'm wondering:

Is Zulip translated into Traditional Chinese? (not Simplified)
Can Zulip offer a free open source plan to our civic hacker network?
You can read more about the g0v network here:

https://g0v.tw/en-US/about.html
a large list of open source projects we have created is here: https://g0v.tw/en-US/project-from-registry.html

Please let me know if you have any questions! Thank you so much for your time!
Best,
kjcl

:::danger
(chihao) 以下是 g0v Slack 對話紀錄，除非涉及隱私或其他違反 coc、g0v 宣言之事項，否則請勿更動 
:::

## `#bridge` 頻道 https://g0v-tw.slack.com/archives/C01SHPD80UD/p1622034205006500

### 2021/5/26
kjcl 2021/5/26 at 21:03

嗨大家， #vaccine 的坑主～ 我是想試一試看能不能把部分的通訊改換到 ZULIP，因為覺得不用擔心失去通訊紀錄而且覺得更適合開放模式的溝通。
@Chris Bobbe 是我的大學學長也是 ZULIP 的一位職業工程師。我很高興他願意跳坑幫忙我們。希望這個 Bridge 的 Setup 會順利～
Zulip 開源 project 溝通方式是自己的一個 Zulip server.  上面有20，000多個參與者。他們現在正在開始翻譯台灣華語。如果有興趣的話可以去 https://chat.zulip.org/#narrow/stream/377-translation.2Fzh_tw 看一下 (edited) 
:wave: 2

ael 22:43
我忘了加哪個 slack bot 進頻道可以被 archive 到這邊。不過我覺得試試 Zulip 會很有趣
https://g0v-slack-archive.g0v.ronny.tw/index/channel/C02G2SXKX

### 5/27
chewei 9:19
有考慮針對已有的 archive 基礎來增進嗎？
#vaccine channel archvie
https://g0v-slack-archive.g0v.ronny.tw/index/channel/C020EQ0R8TW (edited) 

chewei 9:22
replied to a thread:
我想確認 在 https://g0v.zulipchat.org
可以看到他人的 email，這在 slack 也是ok的嗎？是不是 slack 也可以查得到
我截圖先以我自己的 email 為例，我目前是可以看到其他明顯尚未加入 zulipchat 的人員的暱稱與 email 清冊
Image from iOS 
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6c5dd3f5339bd19398fe56d8ad85d3c3.jpg)

pm5 9:25
Slack 應該查不到 Email。「可以看到其他明顯尚未加入 zulipchat 的人員的暱稱與 email 清冊」這樣嗎？可以看到我的嗎？（我沒加入

Chris Bobbe:speech_balloon:  9:26
Does this answer your question? https://g0v.zulipchat.com/help/restrict-visibility-of-email-addresses (edited) 

gugod  9:36
@pm5 看來一定程度上 zulip 是有把 nick 跟 email 關聯起來的.
在 web 版畫面正上方搜尋框中輸入 “pm5”，會直接帶出一個 `@gmail .com` 的 email

9:36
chewei
Who are Admins??? :scream:
Plz Fisrt turn off this Instantly (edited) 
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_725015c85c63bb1ec6afb1282b5674eb.jpg)

pm5:spock-hand: 9:40
@Chris Bobbe that helps a bit but not quite fully answer our questions.  Can you or @kjcl tell us about the current status of g0v.zulipchat.com bridging? because from what I know, I haven't joined zulip yet, but my actual (although outdated as far as I can tell) Email address on g0v Slack (considered by me to be private information) is visible of zulip.  That feels problematic to me.

Chris Bobbe:speech_balloon: 9:40
@kjcl has the "Owner" role, and he gave that same role to me. I would be happy to be removed from that role, as I said in my first post in #bridge. (edited) 

Chris Bobbe:speech_balloon: 9:40
I have changed that setting to "Nobody":

Chris Bobbe:speech_balloon: 9:41
Your email address would have been imported with the initial Slack import @kjcl did around three years ago. (edited) 

pm5:spock-hand: 9:41
Apart from visibility, the issue to me seems to be that I haven't joined zulip yet, so how did it get information about me?

Chris Bobbe:speech_balloon: 9:41
(I did not work for Zulip at that time, and I wasn't involved with the import.)

pm5:spock-hand: 9:42
Ah I see.  @kjcl can you tell us more about it?

gugod 9:44
somehow my account is already roled “Owner” in Zulip … I guess this bit of info was also carried from Slack too.

Chris Bobbe:speech_balloon: 9:44
The import would have been done when g0v.zulipchat.com was first set up, following an earlier version of this doc: https://zulip.com/help/import-from-slack (edited) 

kjcl 10:46
Hi, so the import comes from a Slack export that we did from the g0v slack. E-mail addresses were exported because the idea was someone who was on the g0v slack can come to Zulip, reset their account, put in their e-mail, and get access to an account with all of their old addresses. It's a way to make migration easier.
The e-mail address publicness was a bad default, and certainly not intentional. I'm very sorry!
:smiling_face_with_tear:
1

kjcl 10:47
Roles and account information are imported over as part of the full Slack export.


Chris Bobbe:speech_balloon: 12:27
> The e-mail address publicness was a bad default
> 
Kevin is right, this was a bad default in the Slack import process that was done years ago. When the Slack data is imported, it would be better if Zulip applied the same email-address visibility setting as Slack, without waiting for someone to change it manually. I apologize on behalf of the Zulip team. I've opened https://github.com/zulip/zulip/issues/18622 and announced the incident internally. And, as I said above, I changed the email-address visibility setting to "Nobody" immediately after I understood that it was desired. (edited) 

Slackbot 12:34
先承認你就是沒有人

Chris Bobbe:speech_balloon: 12:34
The Slack export was done, years ago, by an admin on Slack who had access to everyone's email addresses. Please understand that the email addresses were exported for a legitimate purpose (so that Zulip users could "claim" their old messages, as Kevin described), and that the wrong visibility setting on Zulip's side was an accident that we hope to help people avoid in the future, with https://github.com/zulip/zulip/issues/18622. (edited) 

Chris Bobbe:speech_balloon: 13:10
The Matterbridge experiment would still be possible if g0v.zulipchat.com (with the years-old data from Slack) were deactivated and a new Zulip instance were created, if the admins would prefer that option.

## `#bridge` 頻道 https://g0v-tw.slack.com/archives/C01SHPD80UD/p1622083077016600
chewei 5/27 10:37
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a1008cc4a78e034f6bb70b34365ebf70.jpg)

## `#bridge` 頻道 https://g0v-tw.slack.com/archives/C01SHPD80UD/p1622103010021500
chihao:ocean: 5/27 16:10
Who’s data have been exported? Have you asked for consent? @Chris Bobbe @kjcl

kjcl 16:26
I asked @ronnywang for a one-time export in 2018 and the export files were deleted from my machine afterwards. It was a hackathon project out of frustration with Slack and I did not think to ask for consent at the time. I did not realize the Slack export would include people's e-mail addresses and that was a mistake on my part.
I defer to the jothon team for advice. If they feel this was a misuse of data, the Zulip team will be happy to delete this instance and we can start a new Zulip instance without this data.

## `#infras` 頻道

5/27 08:40
pm5:spock-hand: 這個原則也可以適用於幫忙設 matterbridge 的前提（相關討論在 #bridge）：

1. 公開
2. 有紀錄可查
3. CoC
4. 符合 g0v 精神（「相容」是這個意思（對過去與未來相容）？） (edited) 

09:14
gugod 
> CoC 與目標和 g0v 的有相容
我的原意是：“CoC  相容” 且 “目標相容”
不過「目標相容」好像十分廣泛。

09:43
isabelhou g0v宣言
:jump-g0v:
1

09:55
chewei Slack 目前開始有 Admins 與治理機制
可能這類 bridged 的服務，也要考慮，我建議是先有 Admins 與機制，並說明 bridged 服務有什麼風險，特別是成員資料送出去這樣的狀況
舉例來說 zulipchat 在剛才之前，直接是把 slack 這邊的暱稱與註冊 email 全部公開連 guest 都可以查看，一來是 slack 也不允許的事情，反而在 bridged 的服務卻被允許，也無人知曉監管，然後 想找 Admins 卻不曉得是誰，現在正在釐清這個匯出且公開 成員暱稱-註冊email 的操作發生時間點（可能是三年前）與操作者 #bridge (edited) 
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_cc69340ae0dee720335dbccf5545ca04.jpg)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_801cd5d00cfd18ba5cec88d0e14223cb.jpg)

10:14
ronnywang slack 的 export 檔本身好像不包含 email 資訊，不知道 zulipchat 那邊是怎麼抓到 email 的？
:dizzy_face: 4 :broken_heart: 3 :warning: 4
6 replies -> [thread](https://g0v-tw.slack.com/archives/C0386M58S/p1622081665033200)

10:19
chewei 像是與 Telegram bridged 會有這樣的狀況嗎？
還有誰  於何時 接上了哪個服務呢？:dizzy_face: (edited) 

10:40
chewei
replied to a thread:
Slack 目前開始有 Admins 與治理機制…
Image from iOS 
Image from iOS

10:58
chewei
replied to a thread:
slack 的 export 檔本身好像不包含 email 資訊，不知道 zulipchat 那邊是怎麼抓到 email 的？
是否要來確認 Full Slack Export 是什麼..
https://g0v-tw.slack.com/archives/C01SHPD80UD/p1622083639017300?thread_ts=1622034205.006500&channel=C01SHPD80UD&message_ts=1622083639.017300

16:11
chihao:ocean: export 任何資料之前，不用有某種公告和確認嗎？

16:15
ronnywang 當初執行 export 的應該是我，我先道歉當時未進行公告，但我印象中我當時有確認過 export 檔裡面並不包含 private channel 資料以及個人隱私資料，只是我這邊已經沒有保留當時的匯出檔了

16:20
chihao:ocean: 原來如此
16:20
ronny ++ 感謝說明
16:21
這是個有趣的案例呢 :stuck_out_tongue:

16:22
ronnywang https://g0v-slack-archive.g0v.ronny.tw/index/channel/C02G2SXKX/2018-12#ts-1544236915.148600
時間的話應該是 2018 年 10 月
:raised_hands: 1

16:30
gugod web ui 上看來 zulip 那邊大部分使用者的建立日期是2018/12/17
16:30
那可能是實際執行匯入的日期
16:31
ronnywang g0v-slack-archive 的 import script 也是在 2018 年 10 月寫的，可能也是用同一份 export 檔匯入的，但是我剛檢查 g0v-slack-archive 裡面的資料並不包含 email 個資
16:31
https://github.com/ronnywang/g0v-slack-archive/blob/master/webdata/scripts/import-directory.php

## `#infras` 頻道關於 zulip 怎麼抓得到 email https://g0v-tw.slack.com/archives/C0386M58S/p1622081665033200

ronnywang 5/27 at 10:14
slack 的 export 檔本身好像不包含 email 資訊，不知道 zulipchat 那邊是怎麼抓到 email 的？
:dizzy_face: 4 :broken_heart: 3 :warning:4
6 replies

chewei 10:58
是否要來確認 Full Slack Export 是什麼..
https://g0v-tw.slack.com/archives/C01SHPD80UD/p1622083639017300?thread_ts=1622034205.006500&channel=C01SHPD80UD&message_ts=1622083639.017300

> kjcl
> Roles and account information are imported over as part of the full Slack export.
> From a thread in #bridge | Today at 10:47 | View reply

pm5:spock-hand: 11:31
要請 slack admins 幫忙確認囉

ronnywang 11:33
應該是好幾年前我有用 slack 內建的 export 功能提供匯出檔給 @kjcl，但我印象中預設的 export 檔是沒有 email 的，我剛剛也有試著匯出過一次裡面沒有（https://g0v-slack-archive.g0v.ronny.tw/ 裡面也沒有 email 資訊)

gugod 16:00
看來我登入後就自動變成 zulip 那邊的 org owner，如果需要看什麼機密文件(?)的話可能我的畫面上有得看 (edited) 

gugod 16:05
https://github.com/grundleborg/slack-advanced-exporter/blob/master/cmd_fetch_emails.go#L136
看來是有校正回歸事後補登 email addr. 的手段
> cmd_fetch_emails.go:136
```
func fetchUserEmails(token string) (map[string]string, error) {
```
https://github.com/grundleborg/slack-advanced-exporter|grundleborg/slack-advanced-exporter grundleborg/slack-advanced-exporter | Added by GitHub (Legacy

gugod 16:17
https://api.slack.com/methods/admin.users.list 這招

## `#g0v-slack` 頻道 
5/27 16:35
ronnywang slack 治理機制有一個項目可能需要增加討論，歡迎大家提供意見，就是關於 slack 的 export 問題

16:41
ronnywang 先簡單說明一下狀況，2018 年 12 月時 @kjcl 提議想要使用 zulip ，因為 zulip 有提供給 open source project 免費的完整功能，會比 slack 更方便。當時有開 #zulip 頻道討論（對話記錄）
當時我有協助 export slack 對話記錄，我印象中我當初有確認過裡面只有包含 public channel ，user 資料也不包含 email 等個資，所以我認為應該是安全的。
（我先道歉，當時應該要有公開公告這樣的討論事項和運用方式）
然後今天 @chewei 有發現 zulip 那邊有揭露了會員的 email 資訊（https://g0v-tw.slack.com/archives/C01SHPD80UD/p1622034205006500），目前還在追查是哪個環節造成 email 資料外流至 zulip。
不過 slack export 檔的運用方式應該也要列入 slack 治理機制討論，這邊想說丟出這議題大家可以討論看看

## `#infras` 頻道 https://g0v-tw.slack.com/archives/C0386M58S/p1622105424052400
5/27 16:50
kjcl 我犯了大錯了。。。那時候我把 API key 直接發給他們了。不好意思大家。我把我全部跟他們的 e-mail 記錄放到共筆

16:50
他們應該是透過這個方式把 email 帶進 Zulip 的

17:02
ronnywang API key 好像不是我提供的，應該是 @kjcl 自行產生的，當初 slack 的設定是人人都可以自行申請 API key ，去年才改成要 admin 同意才能申請
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2a85f24788e4e5a56d696b473520244f.png)

17:02
不過 slack 這點還真奇怪，users:read.email 的權限一般使用者也可以取得？這個我確認一下
