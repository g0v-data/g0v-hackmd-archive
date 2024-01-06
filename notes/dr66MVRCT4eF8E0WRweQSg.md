---
title: 20200516 線上揪松改版
tags: jothon online, 2d-online-chat,
---

20200516 線上揪松改版
===================
目前進度：
* 可以自我介紹
    * https://meet.jothon.online/event/show/g0v-hackath39n
        * Repo: https://github.com/g0v/g0v-intro
* 有主頻道和次頻道
    * https://meet.jothon.online/meet/show/g0v-hackath39n
* 分割畫面小幫手
    * https://g0v.github.io/jitsi-screen/screen2.html
        * Repo: https://github.com/g0v/jitsi-screen/
* 2D Chat Online
    * https://g0v.github.io/2d-online-chat/
        * 編輯器：https://g0v.github.io/2d-online-chat/map-editor.html
        * Repo: https://github.com/g0v/2d-online-chat/

需要幫助：
* 主頻道和次頻道的介面改版
* 分割畫面小幫手的排版設計
* 2D RPG 線上大松的場景設計


# jitsi-screen

generate a URL:
`jitsi-screen/share.html?jitsi_url=...&password=...`


# Port swonline features to 2d-online-chat

common ancestor: 7f0e16a (diff size 2135 lines...)
Features need porting:
- multiple tile source
    - first commit: 21aae24
- [[WIP]](https://github.com/Stimim/2d-online-chat/tree/master) [P1] mobile support (rwd)
    - keyword: "mobile"
    - first commit: 87ff28f
    - 47febbb4d, e51b291bb
- emojis
    - ae32d09 replace chat with emojis
- [P0] [Done] 732a16d warn about adblock browser plugins (???)
- character chooser
    - probably just check the "login-form" "selected-character"
- [P0] object editor
    - [Done] NPC interaction
    - [Done] iframe (e.g. youtube)
- [P2 but easy] Highlight this user (heroes.me)
    - 2fca088b