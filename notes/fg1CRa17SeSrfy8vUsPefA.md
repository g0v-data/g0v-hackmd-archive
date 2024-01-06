---
title: "通訊加密方案"
tags: 零時的學習不能等,hackpad
---

# 通訊加密方案

> [點此觀看原始內容](https://g0v.hackpad.tw/Jwu1z932KKt)

本篇源自 2013/8/3 凱道萬人送仲丘相關討論：
[https://groups.google.com/forum/#!topic/g0v-general/zabwyXJB7mg](https://groups.google.com/forum/#!topic/g0v-general/zabwyXJB7mg)
1.  開源社群如何支援大型公民運動、實現公民不服從
2.  如何確保（媒體發稿）網路暢通、（內部人員）通訊安全
3.  場子太大，如何解決影音現場傳送、向外轉播問題
4.  街頭運動如何有效計算人次

### 電話 Voice


### BlackBerry Messager(BBM) for BlackBerry, iOS, Android, Windows Phone

    [_Features_](http://en.wikipedia.org/wiki/BlackBerry_Messenger#Features)
    - _Make BBM Video calls or Screen Share over Wi-Fi or the mobile network on the latest smartphones (only_ [_BlackBerry 10_](http://en.wikipedia.org/wiki/BlackBerry_10)_)._
    - _Send and receive messages with unlimited length._
    - _Choose a personal BBM display picture and status._
    - _Real-time confirmations when messages are being written, delivered and read._
    - _Share photos, videos and more with multiple contacts at once._
    - _Add contacts by scanning QR Codes, using NFC technology or sharing PINs._
    - _Send files such as documents, photos, music, videos up to 100MB._
    - _Create and join groups where you can share and discuss lists, photos etc._
    - _Share location._
    - _Create, likes or comment BBM Channels._
    - _Free Call BBM contacts over Wi-Fi (only_ [_BlackBerry OS_](http://en.wikipedia.org/wiki/BlackBerry_OS)_)._
    - _Voice Call BBM contacts over Wi-Fi and mobile data \[BBM app Android\]_
###     BBM中文頁面介紹（含下載點）：[http://www.bbm.com/bbm/zh_cn.html](http://www.bbm.com/bbm/zh_cn.html)


###     [BBM Protected 企業、團體組織版介紹](http://us.blackberry.com/enterprise/products/bbm-protected.html)

###     《影片介紹》[BBM Protected - Secure IM](https://www.youtube.com/watch?v=NqQYxJoBVec)

###         PROTECT DATA IN-TRANSIT

###         BBM Protected is designed to provide full end-to-end message encryption from the time a BBM Protected user sends a message to when the recipient receives the message. It incorporates three layers of security.

        - _BBM Protected introduces a new layer of encryption to the existing BBM security model._
        - _Messages between BBM Protected users are encrypted using a PGP like model. The sender and recipient have unique public/private encryption and signing keys._
        - _These keys are generated on the device, by the FIPS 140-2 certified cryptographic library, and are controlled by the enterprise._
        - _BBM and BlackBerry are not involved in brokering the key exchanges, so at no time are they stored within the BlackBerry infrastructure._
        - _Each message uses a new random symmetric key for message encryption. _
        - _A Triple DES 168-bit BBM scrambling key encrypts messages on the sender’s smartphone, and is used to authenticate and decrypt messages on the recipient’s phone. _
        - _TLS encryption between the smartphone and the BBM infrastructure helps protect BBM messages from eavesdropping or manipulation._
![](http://us.blackberry.com/content/dam/bbfoundation/images/enterprise/products/bbm-protected/products-bbm-protected-encryption.png.original.png)


### RedPhone

RedPhone - (only for android)  [https://play.google.com/store/apps/details?id=org.thoughtcrime.redphone&hl=zh_TW](https://play.google.com/store/apps/details?id=org.thoughtcrime.redphone&hl=zh_TW)

**Kryptos** -
[http://kryptoscommunications.com/](http://kryptoscommunications.com/)


### Mumble

Open source、類似無線電對講機、RC 語音聊天室
中心化伺服器架構，需要確認伺服器本身安全性。
跨平臺 Desktop&Mobile
傳輸的大小可設定品質來控制（Desktop）
可加密、針對使用者發 channel 的憑證
官網每月付 $7 美金可以自動生成一個 Server for 15 users.
據說德國海盜黨有在用
- official site: [http://www.mumble.com/](http://www.mumble.com/)
- 自己架 Server doc: [http://mumble.sourceforge.net/ACL_Tutorial/English](http://mumble.sourceforge.net/ACL_Tutorial/English)
            - [ ] Android: [https://play.google.com/store/apps/details?id=com.lordmarty.mumbleclient](https://play.google.com/store/apps/details?id=com.lordmarty.mumbleclient)
- iOS: [https://itunes.apple.com/us/app/mumble/id443472808?mt=8](https://itunes.apple.com/us/app/mumble/id443472808?mt=8)

little issues:
適合團體內部使用，遊行現場可能需要解決頻寬問題
> 可能架在 g0v 下然後開放 NGO 申請加密頻道，以降低技術門檻？
> [name=Wu H]

iOS & Android Client 端的設定選項不多，~iOS 沒有 Push to talk 可能會變成災難~ iOS 也有 PTT 功能，需要額外設定。


### SMS

TextSecure Beta
[https://play.google.com/store/apps/details?id=org.thoughtcrime.securesms](https://play.google.com/store/apps/details?id=org.thoughtcrime.securesms)
(for iOS)
[https://github.com/WhisperSystems/TextSecure-iOS](https://github.com/WhisperSystems/TextSecure-iOS)

### Instant Message


OTR加密教學：[http://billy3321.blogspot.com/2013/08/otrgtalkfacebook.html](http://billy3321.blogspot.com/2013/08/otrgtalkfacebook.html)

TOX: [https://github.com/irungentoo/ProjectTox-Core](https://github.com/irungentoo/ProjectTox-Core)

safeslinger: [http://www.cylab.cmu.edu/safeslinger/](http://www.cylab.cmu.edu/safeslinger/)
    教學：[http://blog.g0v.tw/post/58513500285](http://blog.g0v.tw/post/58513500285)
    非 Open source、快速上手

BitMessage
    從 bitcoin 衍生出的訊息傳遞系統；匿名、分散式，有類似 mailist 的機制叫做 chan(channel)，可訂閱方便擴散訊息。
    安裝、下載：[https://bitmessage.org/wiki/Main_Page](https://bitmessage.org/wiki/Main_Page)
    網頁版客戶端：[https://bitmessage.ch](https://bitmessage.ch)

Telegram [https://telegram.org/](https://telegram.org/)
    open source 反應速度很快，需要一隻電話號碼去收簡訊，以電話號碼當作帳號 [client 目前提供](https://telegram.org/apps)， windows、iOS、Android、Mac OSX、Web client、CLI、等

- wall command on linux server ( [http://www.webhostingtalk.com/showthread.php?t=39656](http://www.webhostingtalk.com/showthread.php?t=39656) )\- ([irc log](http://logbot.g0v.tw/channel/g0v.tw/2014-05-01/279))
- WireRoom is written in js, powered by node js( [https://github.com/c9s/WireRoom/](https://github.com/c9s/WireRoom/) ) \- ([irc log](http://logbot.g0v.tw/channel/g0v.tw/2014-05-01/306))

Gilgamesh
    Secure Bluetooth peer-to-peer instant messaging and broadcasting.
    [https://f-droid.org/repository/browse/?fdfilter=gilgamesh&fdid=info.guardianproject.gilga](https://f-droid.org/repository/browse/?fdfilter=gilgamesh&fdid=info.guardianproject.gilga)

### What is GPG


[http://tetralet.luna.com.tw/index.php?op=ViewArticle&articleId=58&blogId=1](http://tetralet.luna.com.tw/index.php?op=ViewArticle&articleId=58&blogId=1)

### Email 加密


GPG for gmail
[http://howto.cnet.com/8301-11310_39-10434684-285/want-really-secure-gmail-try-gpg-encryption/](http://howto.cnet.com/8301-11310_39-10434684-285/want-really-secure-gmail-try-gpg-encryption/)

### VoIP

[http://tox.im/](http://tox.im/)
- open source

**Web Browser**
[http://webpg.org/](http://webpg.org/)

### Voting System

- **PyBitmessageVote** is a trustless, private and decentralized peer-to-peer voting scheme. [https://github.com/jesperborgstrup/PyBitmessageVote](https://github.com/jesperborgstrup/PyBitmessageVote)

### 如何得知被監聽

?


### 運動現場已知需求

1\. 記者發稿專用網路
2\. 媒體組即時上傳影像、新聞稿、臉書
3\. 工作人員（e.g. 交通組）無障礙通訊
4\. 核心幹部機密加密通訊：[阿端safeslinger教學文](http://blog.g0v.tw/posts/58513500285/safeslinger-android-iphone-8-18)

匿名os 系統 使用USB或光碟等


[https://www.youtube.com/watch?v=YlmM7b8OdRI](https://www.youtube.com/watch?v=YlmM7b8OdRI)


[https://www.youtube.com/watch?v=BWTaqSyYb6k](https://www.youtube.com/watch?v=BWTaqSyYb6k)


