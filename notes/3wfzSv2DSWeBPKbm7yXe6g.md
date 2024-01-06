---
tags: g0vernance
---
# g0v IRC 現況

現在 g0v 主要的 IRC 頻道是 #g0v.tw ，位在 freenode 這個 IRC 網路上。 freenode 近期有些管理爭議，一些開源社群搬家到 libera.chat 上。

* 2021/06/26 之前的 logbot 網址： https://logbot.g0v.tw/channel/g0v.tw/today
* 2021/06/26 之後的 logbot 網址： https://logbot.g0v.tw/channel/g0v-general/today

## libera.chat 待處理事項

### 是否搬家到 libera.chat ？

gugod 在 2021/05/19 分享了：

* [The Freenode resignation FAQ, or: "what the fuck is going on?"](https://gist.github.com/joepie91/df80d8d36cd9d1bde46ba018af497409/)

大意是 freenode staff 因為和 Freenode Limited 的 Andrew Lee 之間的爭議，決定開始一個新的 IRC network [libera.chat][libera-chat] 。

目前一些開源社群（例如 haskell, lobsters ）已經在 [libera.chat][libera-chat] 上開設頻道。兩方的 bot 攻防也還在進行。

> 第一步我想先做到接通 Slack 到 freenode g0v 頻道和 libera.chat g0v 頻道 [name=caasih]

2021/06/26 搬到 libera.chat 了，但還沒申請下面提到的 community channel namespace 。

### 是否在 libera.chat 上申請 g0v community channel namespace ？

[libera.chat][libera-chat] 為社群提供了 [community channel namespace][libera-chat-chanreg] 。

申請時需向站方提出：

```
# About your community
Your community name(s):
Your community description:
Can we list your community publicly, such as on the libera.chat website:
Libera Chat staff member you have discussed this registration with:

# About you and your staff
Your NickServ account:
Your relationship / affiliation with the community:
NickServ of group contacts and if they're primary/secondary, hidden/public:

# Channels and cloaks (see below)
Channels you'd like to claim:
(typically #communityname and #communityname-*)
(The cloaks will be formatted like this:
about/YourCommunityNameHere/accountname)
```

目前先建立了 #g0v 和 #g0v-general 頻道， founder 權限在 caasih, gugod, yhsiang 上，但還沒申請 community namespace 。

社群負責人未來如果申請了 channel namespace 應該可以 claim 上述頻道。

[libera-chat]: https://libera.chat
[libera-chat-chanreg]: https://libera.chat/chanreg

## ~~freenode 待處理事項~~

### ~~是否取回 freenode 上的 IRC 頻道管理權？~~

2021/05/24 在管理員 Tabmow 和 t-42 的協助下，已取回 founder 權限。

> 之後打算把 founder 權限給 gugod, kcwu, yhsiang [name=caasih]

2021/06/14 [freenode 不再允許 IRCCloud 連線][freenode-banned-irccloud]， gugod 的帳號也掰掰了，考慮撤出 freenode 。

2021/06/26 logbot 和 slack-bridge 改接 libera.chat 上的 #g0v-general 頻道。

[freenode-banned-irccloud]: https://twitter.com/IRCCloud/status/1404153550159159298

### ~~是否在 freenode 上申請 g0v community group ？~~

freenode 也有 channel grouping 機制：

* [Group registration](https://freenode.net/groupreg)

文末提到：

> If you wish to discuss the group registration process, find out if freenode could be a good fit for your project or register your project as a group, please feel free to drop any of the team members a line on IRC. If none are online, feel free to reach out to staff in general and they will forward your request to the team, which will get back to you as soon as possible.

但 freenode 自殺了，不用申請了。
