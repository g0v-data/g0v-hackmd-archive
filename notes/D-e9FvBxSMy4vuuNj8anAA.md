# :sparkles: 魔術聊天門戶 Magic Chat Portals

該項目的目標是輕鬆連接所有社區的在線空間，同時讓他們繼續正確地工作。 我們希望這樣做有助於每個人找到世界應該運作的更好方法。

The goal of this project is to **easily connect the online spaces of all communities,** while letting them continue working exactly where they are. We hope that doing this will help everyone to find the better ways that the world should work.

## :sunrise_over_mountains: 為什麼？ Why?

因為在網上開始社區之間的對話或協作應該更像是在黑客馬拉鬆上走向某人。

Because starting a conversation or collaboration between communities while online should be a more like walking up to someone at a hackathon.

## :tophat::rabbit: 怎麼樣？ How? 

魔術聊天門戶可以通過名為“Matterbridge”的軟件實現。 大多數情況下，它看起來像常規聊天。 這是件好事！ 它可以在許多不同的聊天工具之間中繼消息。

Magic Chat Portals are made possible by software called "Matterbridge". Mostly, it looks like regular chat. This is a good thing! It can relay messages between many, many different chat tools.

![Screenshot of bridged chat.](https://imgur.com/mTFaQ1r.png)

此外，它做翻譯。 通過谷歌真的很糟糕的翻譯。 我的消息不會贏得台灣文學獎，但是當我喝一杯蜂蜜檸檬茶時，我會告訴你，也許你可能笑，這取決於1）這個笑話繼續是多麼熱鬧，以及2） 你是多麼有禮貌。

Also, it does translation. Really really bad translation through Google. My messages won't win a Taiwan Literature Award「台灣文學獎」, but I will tell you when I just drank a glass of honey lemon tea, and perhaps you might laugh, depending both on 1) how hilarious this joke continues to be, and on 2) how polite you are.

## :nut_and_bolt: 項目的一部分 Parts of the Project

- **Matterbridge.** The backend app that does the magic. [Code.][app-code] (Sorry, no pretty front-end yet :crying_cat_face:)
- [**Matterbridge:Viewer.**][viewer] Yay! A simple visual app showing how portals are set up. [Code.][viewer-code]
- [**Matterbridge:Heroku.**](https://github.com/patcon/matterbridge-heroku) The small code package with configuration for running the app. [Code.][heroku-code]
- [**Matterbridge:Auto-Config.**][autoconf-demo] A small backend app aspiring to allow any community member to easily set up portals. [Code.][autoconf-code]

## :scroll: 現有資源 Existing Resources

- [Slack Bridges: What are they?](http://link.civictech.ca/about-bridges) A Slack specific resource for Canadian #civictech community.
- [About chat bridges.](https://hackmd.io/3fZbzWBfRZGpbpD_V-1GhQ) A more general resource
- [How To: Set up Slack bridges.](https://hackmd.io/9ygVXBKUS3ej8moGhSVkTw) 

<!-- Link -->

   [app-code]: https://github.com/42wim/matterbridge
   [viewer-code]: https://github.com/patcon/matterbridge-config-viewer
   [viewer]: https://matterbridge-heroku-viewer.herokuapp.com/#hacklabto
   [heroku-code]: test
   [autoconf-demo]: https://matterbridge-autoconfig-g0vtw.herokuapp.com/
   [autoconf-code]: https://github.com/patcon/matterbridge-autoconfig