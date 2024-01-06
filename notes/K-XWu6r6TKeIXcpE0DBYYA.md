---
title: "g0village - 勇者傳說"
tags: hackpad
---

# g0village - 勇者傳說

> [點此觀看原始內容](https://g0v.hackpad.tw/UbRMyR1GliV)

發起人
hlb, tkirby, au, kcwu, racklin

github 網址：[https://github.com/g0v/g0village](https://github.com/g0v/g0village)
專案窗口 hlb 聯絡方式：
- irc 暱稱： hlb
- 推特帳號： [https://twitter.com/hlb](https://twitter.com/hlb)

在文化部的討論串（含進度更新）：[https://groups.google.com/forum/#!topic/g0v-moc/HHNvvbhBFfY](https://groups.google.com/forum/#!topic/g0v-moc/HHNvvbhBFfY)
8bit 版 (RPG+LV/HP) 雛形: [http://g0v.github.io/g0village-8bit/](http://g0v.github.io/g0village-8bit/)

### 任務項目清單


新手村
> Email/Github/Facebook OAuth 登入
> [name=Angus H]

> 閱讀 g0v 簡介 (零時條款)
> [name=Angus H]

> 到處走走認識村民 (hub)
> [name=Angus H]

> 到各部會選職/轉職 (tagging)
> [name=Angus H]

> 進入酒吧聊天 (irc)
> [name=Angus H]

> 觀看議事佈告 (hackathon news, hack folder, group)
> [name=Angus H]

> 打倒村長，自己成為村長 <\- 最後一步 according to clkao
> [name=Angus H]

> 出村打怪（職業特定任務/成就分支)
> [name=Angus H]


### Lv/HP系統相關想法


- 目的是增進對 g0v 的理解和鼓勵玩家自己 tag 分工/技能
- 新手村裡的每個行動，從最小像看某個 slogan 看板（觸發時可以選擇「我感覺...」來做民調?），都可以昇級(「等級」約等於理解程度)。
- 各職業（分工）及技能（坑相關...）在 identify 時都可以加 HP。
- 任何職業/技能的玩家，走完全線就一定可以昇到 3000+ HP 300+ Lv，獨立打倒村長成為村長。
- GitHub（或其他 OAuth )帳號只用來登入，無關初始數值 (不然就變成技術宅限定遊戲了...)
- 除了專案列表具象化之外，還有萬能的 NPC 名叫「沒有人」... # j/k
- 也許 [http://hack.g0v.tw/people](http://hack.g0v.tw/people) 可以提供一個量化值？
- 可以連結 [hack.g0v.tw](http://hack.g0v.tw) ，如果參與討論的次數多就會升級，新增專案且該專案達到一定人數也會升級

### 概念提案


剛進入時讓玩家選職業(可複選), 用來決定後面是否跳過某些任務
    職業例如:   程式員? 畫家? 寫手? 講者? 鄉民?

可以把 idea pool 裡面每一個專案構想都變成一個 NPC。
當有登入的玩家的職業是該 NPC 需要的職業時，NPC 會跳出對話框，對話框的內容是專案名稱，還有一至兩行的簡介。跟該 NPC 對話就可以得到更詳細的專案內容。

Q: "橫在你面前的是一個古舊的專案@@@，現在它需要一副主題為畫&&&，來重獲新生！你要："
">\> 馬上畫圖上載 / 不管它 / 晚點再畫"

Q: 在原野上移動 --\> 進入戰鬥 (旋渦音樂) -->
"野生的立法院網站出現了!"
">\> 砍站 / 插畫 / 寄信 / 無視"
- "你使用了砍站!"
    "對立法院造成了 50 點的傷害!"
    (勝利音樂)
    "立法院網站倒了!"git@github.com:arch-jslin/nm2008proj.git
    "ly.g0v.tw 獲得 120 個粉絲"
Q: "立法院網站掉落了會期影音檔, 你的 github 空間已滿, 請問要轉移到夥伴身上嗎?"
">\> 轉移 / 捨棄"
- "轉移到 >\> ETBlue / IamBlue / BlueT"
> 這題目好難 XDDDDDDDDDDD
> [name=ET B]

    "ETBlue 被推坑了."
回到原野, 前方出現一個坑

打倒村長就可以離開新手村去打怪了！-clkao

難解的 angularJS bug走了過來!
\[出口: 北 / 南\]
<120/137HP 42/52MP> summon blue
你召換了 angularJS.tw 管理員!
angularJS.tw 管理員用力的揍了難解的 angularJS bug 一拳!
angularJS bug 血流如注!
angularJS bug 正在哀嚎!
angularJS bug 被解決了. 你獲得了 5 點的前端經驗值.
angularJS.tw 管理員: 最近的坑有夠多的, 下次請先開 issue.

### 參考資料

售票亭老闆說暫時出出嘴也好，所以我來貼幾個臨時想到的 reference XD：
- 跟社會議題大略有關的遊戲作者，可參考看看： [http://dukope.com/](http://dukope.com/)
- and this: [http://www.riotgame.org/](http://www.riotgame.org/)
- 這個報紙治國也很有趣：[http://www.nationstates.net/](http://www.nationstates.net/)

### 技術需求

- 新手村遊戲過程中的閱讀其他網址任務，應該讓遊戲中能展開新的視窗分頁
> 然後例如說要求讀過專案列表，專案列表最下面有「新手村 code」，回到遊戲輸入完之後才算解開任務 etc..
> [name=Wu H]

> 其實整個計畫讓我想到 kk mud 的任務編輯系統，或是早期 cgi 網頁遊戲 lol 
> [name=Wu H]

> 不過使用技術已經確定了嗎？Demo link？（爬了 github 那邊跟這邊，都看不出來）
> [name=Wu H]

> racklin 發起的 8bit demo link 在 [http://g0v.github.io/g0village-8bit/](http://g0v.github.io/g0village-8bit/)
> [name=Audrey T]


### 暫存區

（以下剪貼自 irc）
- hlb - clkao: 我完全沒辦法抗拒這個誘惑... [https://dl.dropboxusercontent.com/u/132028/Screenshots/g0v-game.001.png](https://dl.dropboxusercontent.com/u/132028/Screenshots/g0v-game.001.png)
- au - hlb: prehackath4n 專門來生這個吧
- au「打倒村長！現在你就是村長了」「閱讀村長手冊」
- hlb剛剛想到勇者選擇回應的話
- hlb可以拿 [http://more.handlino.com/?corpus=twly](http://more.handlino.com/?corpus=twly) 語料
- ttcat「你得到一個鏟子」
- hlb「這是合法的單位，非常謝謝您。」
- au「我感覺你的眼光都已經發紅了」
- 15:32:21chuiyi"你想當村長嗎" "想" "不想"
- 15:32:29chuiyi"不想也由不得你 你現在就是村長了"
- 15:32:52superbil「你得到使用 Portal 的能力」
- 15:33:58hlb evenwu: 「你遇到了史萊姆」「使用必殺技」「對不起你的必殺技用完了，請先 commit」
- 15:36:18 yhsiang寫遊戲嗎 unity!!
- 15:37:38chuiyi unreal engine for web...
- 15:38:27au Unreal ASM.js
- 15:48:47hlb [http://rpgjs.com/](http://rpgjs.com/)
- 15:48:48kcwu hlb's url: \[RPG JS: Your online RPG on your browser\]
- 15:48:49hlb好像夠用
- 15:50:05au rpgjs 不賴
- 15:52:01ipa[https://www.facebook.com/iamhlb/posts/10151806399091789](https://www.facebook.com/iamhlb/posts/10151806399091789)
- 15:52:02kcwuipa's url: \[Liang-Bin Hsueh - 剛剛在 g0v IRC 講到設計遊戲來帶大家走完新手村任務......... | Facebook\]
- 15:52:15jimyhuang[http://www.chuto.tw/record](http://www.chuto.tw/record) 會有布丁跳出
- 18:34:46caasiHuang講到遊戲，繼續偷偷推廣 Papers, Please ：[http://dukope.com/](http://dukope.com/)
- 18:40:46au記得 mozilla 有推兩個遊戲... 很搞笑的 browserquest.mozilla.org 和很華麗的 [http://www.unrealengine.com/html5/](http://www.unrealengine.com/html5/)
- 18:43:50aucaasiHuang: 非商業用 UDK 好像是免費（但不是自由）授權
- 18:43:53au(UDK3)
- 20:35:33hlbcaasiHuang: 跟成就系統相比，我覺得比較需要對話選擇支
- 20:35:57hlbcaasiHuang: 因為想要順便讓路人在 3mins 內就很怒，跑來作 g0v
- 20:36:15hlbcaasiHuang: 例如一開始就可以選打大魔王，然後馬囧就出現，立刻死
- 20:36:41hlbcaasiHuang: 選擇跟村民唬爛，就出現白賊... 之類的
- 20:37:01caasiHuanghlb: XDDDD 上次朋友才跟我說有遊戲一開始就打最終決戰可以看到製作小組XD
- 20:37:12caasiHuangRen'Py: [http://www.renpy.org/](http://www.renpy.org/)
- 20:37:13kcwucaasiHuang's url: \[The Ren'Py Visual Novel Engine\]
- 20:42:44hlb「獲得成就：分身伐樹（跟 15 個人一起砍木頭」
- 20:44:51auhychen++ # [https://badges.webmaker.org/](https://badges.webmaker.org/) 真不賴
- 20:44:52kcwuau's url: \[Mozilla Webmaker Badges\]
- 20:44:58hychen"第一次糾團上凱到成就達成"
- 20:45:27hychen"第一次在凱道寫code成就達成"
- 20:45:37ronnywang還有給非碼農的「解除將10個PDF轉成CSV」
- 20:52:57hlb選了奇怪的選擇枝
- 20:53:03hlb會進到 完全沒有畫面 T_T
- 21:22:12aucaasiHuang: vn-canvas 有用過嗎? [https://googledrive.com/host/0ByTPdb3Faj\_XSWtkMUpxWjh0SDg/demo\_vn.html](https://googledrive.com/host/0ByTPdb3Faj_XSWtkMUpxWjh0SDg/demo_vn.html)
- 21:22:15kcwuau's url: \[VN-Canvas Demo\]
- AVG 只要圖的意思是不用做成 sprite？
==22:22 <====[**hlb**](https://www.irccloud.com/#!/ircs://irc.freenode.net:6697/hlb)====\> ETBlue: 請見== ==[http://langintro.com/js-vine/docs/exampleNovel.html](http://langintro.com/js-vine/docs/exampleNovel.html)==
22:22 <[**kcwu**](https://www.irccloud.com/#!/ircs://irc.freenode.net:6697/kcwu)\> hlb's url: \[Visual Novel Example\]
- 22:18:15hlb[https://github.com/g0v/g0village](https://github.com/g0v/g0village)
- 22:18:18kcwuhlb's url: \[g0v/g0village · GitHub\]
-  我需要一個高村長 sprite
- 勇者 sprite
- 布丁 sprite
- 大魔王馬囧
- 不過如果是 AVG 那只要圖就可以了 XD
- 22:24:50hlbcaasiHuang: 你要選擇載入哪裡的自我介紹呢 1. Facebook 2. GitHub 3. Twitter
- 22:25:08hlbcaasiHuang: 4. 健保局資料
- 22:25:30hlbcaasiHuang: 「你選了 4 嗎？太好了，我們有請 allenown」

- 20:34:03 clkao: 據說 g0v 的 g 是炸g的意思
- 20:34:23 clkao: 0 是苦主，忙著寫 code 沒吃到炸g
- 20:34:35 clkao: (掰不下去了)
- 20:34:39 Fumi: 我不知道該信任誰 T__T
- 20:34:47 miaout17: 信任村長就對了
- 20:34:53 ipa: v就是沒寫code吃到炸雞比出勝利手勢的人～
- 20:35:41 opop: v
- 20:35:45 ipa: v
- 20:35:58 ttcat: v
- 20:36:56 clkao: 少年 去吃炸雞吧


