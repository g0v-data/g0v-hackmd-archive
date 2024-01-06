---
title: "尋找完美的共筆平台"
tags: hackpad
---

# 尋找完美的共筆平台

> [點此觀看原始內容](https://g0v.hackpad.tw/Mh1LjzkizQf)

> 以 g0v.hackpad.com 的使用者數量來說, 搬到 paper.dropbox 應該還是會炸掉...
> [name=lanfon]

> (btw, g0v domain 下是獨立主機而且確定不會向 g0v 社群收費)
> [name=lanfon]

> uh... 應該說找共筆平台的訴求對象反而也會影響平台的完美程度(?)
> [name=lanfon]

> 什麼意思？是說每個人心目中的完美共筆平台都不一樣嗎？XD
> [name=chihao y]

> [https://quip.com/](https://quip.com/) 還有quip啊
> [name=Ymow W]

> 這是必然的吧?!(?) 主需求不同，對於提供的功能的要求度、是否收費等其他項目自然也會有不同的評斷點...
> [name=lanfon]

> [lanfon](https://g0v.hackpad.tw/ep/profile/FhF2TCnIycW): 同意，似乎應該把需求列一下
> [name=chihao y]

> [Ymow Wu](https://g0v.hackpad.tw/ep/profile/uoWnheSbrRw): 對耶！Quip好用嗎？
> [name=chihao y]



## 想要⋯

- 在文件中就能清楚、簡單看到是誰寫了那些內容
- 能夠同時打中文，並且及時看到對方的input
- 能夠插入圖片
- 還有表格功能


## pad.riseup.net (etherpad-lite)

- 作者標示：有，以文字底色表示
- 同時打中文：沒問題
- 插入圖片：不行
- 其他
    - Etherpad hosted on riseup.net (an activist-supported info-infrastructure)==【勝】==
    - 30天不編輯會刪除


## Hackpad

- 作者標示：有，以底線表示，並在文件左側直接顯示作者名，還有「對話」功能==【勝】==
- 同時打中文：會爆炸
- 插入圖片：可以
- 其他
    - 首頁以時間排序顯示「最近有更新的 Pad」，而且只著重於有變更的部份，是個獨特的優點。
> 同意！
> [name=chihao y]

    - 被Dropbox買下來之後好像開發就停滯了
> 我猜不會開發了，不過有開源 [https://github.com/dropbox/hackpad](https://github.com/dropbox/hackpad)
> [name=ChengHan W]

> app 壞惹
> [name=che l]

> app整個崩毀
> [name=chihao y]

    - Dropbox的隱私保護？
    - 萬年Chrome bug...
    - 謠言指出快收攤了？
    - API不支援delete pad
    - 轉移到 Dropbox Paper 之後不能轉回來（泣


## Dropbox Paper

- 作者標示：有，以底線表示，並在文件左側直接顯示作者名
- 同時打中文：會爆炸
> 喔耶？
> [name=chihao y]

> 幾個朋友今天實測，發現不行耶，問題跟Hackpad一樣⋯
> [name=chihao y]

- 插入圖片：可以
- 其他
    - Dropbox 推出 類似「hackpad」 的功能 ( hackpad 停滯的原因 !? )
    - 幾乎包含 hackpad 的功能
> 這個對話的功能也有嗎？
> [name=chihao y]

> 自問自答：沒有，對話的功能變成在文件右側的註解框了（類似Google Doc）
> [name=chihao y]

    - 支援 各種程式碼 highlight ==【勝】==
    - 有像 Google Doc 註解的功能
    - 目前還在 測試 階段，申請制
> feedback 問了是否可以 import/export hackpad....
> [name=lanfon]

> 申請了！好想試用喔～
> [name=chihao y]

> 拿到試用邀請了！還蠻快的嘛⋯
> [name=chihao y]

    - 可從  hackpad  匯入
> ^^^確定會有這個功能 but not implement yet.
> [name=lanfon]

> 可以匯入整個workspace嗎？
> [name=AceChen]

> 注意：匯入之後不能匯出喔>.O
> [name=Vdragon, Ｖ]

> 好魔法少女不簽嗎？
> [name=Vdragon, Ｖ]

> 追加：官方支援 import workspace from Hackpad
> [name=chihao y]



## Google Doc

- 作者標示：無，僅在revision history裡可以大概看出誰寫了什麼
- 同時打中文：沒問題
- 插入圖片：可以
- 其他
    - 介面功能蠻完整的
    - 是Google，所以會有潛在隱私以及censorship的問題


## hackmd.io

- 作者標示：僅在blockquote中可以用\[\]-tag
    - [https://hackmd.io/MYRgTARuYgtMAzAHGWAWMCDssCcBWAUwVi1wiUKwBNqAGAQwYiA=](https://hackmd.io/MYRgTARuYgtMAzAHGWAWMCDssCcBWAUwVi1wiUKwBNqAGAQwYiA=)
- 同時打中文：應該沒問題吧？
> 沒問題
> [name=ChengHan W]

- 插入圖片：可以
- 其他
    - Open Source ==【大勝】==
    - 台灣團隊開發中，即將大改版？==【勝】==
        - 支援 graphviz
        - 支援 Sequence diagrams
        - 支援 Flow charts
        - 支援 MathJax
        - 範例請看 [https://hackmd.io/GwEw7AhgplBGDGBaAjAMwCwGZHogBlkQgCYo9ERhYBWPYzdEVCCIA===#](https://hackmd.io/GwEw7AhgplBGDGBaAjAMwCwGZHogBlkQgCYo9ERhYBWPYzdEVCCIA===#)
    - 資料安全？
> 持續加強中，但是目前沒什麼疑慮
> [name=ChengHan W]

> 嗨！作者在這裡XD，歡迎聯絡 [https://github.com/jackycute](https://github.com/jackycute)
> [name=ChengHan W]

> jacky++
> [name=chihao y]

> 如果有WYSIWYG編輯器的話對一般人比較友善 e.g. [stackedit.io](https://stackedit.io/)
> [name=AceChen]

> 另外期待組織功能快推出，這樣就可以搬家了 \\o/
> [name=AceChen]

> Update: [stackedit](https://github.com/benweet/stackedit) 看起來有點開發停滯了，原作者轉去開發 [Classeur](https://github.com/classeur/classeur)
> [name=AceChen]


## Quip

- 作者標示：沒有或不明顯
- 同時打中文：應該沒問題
- 插入圖片：可以
- 其他：
    - 可插入試算表
    - markdown語法
    - 有檔案管理介面 (分資料夾 資料夾可設顏色)
    - 可設定管控分享權限 view / view&edit / disable
    - share link
    - export to PDF
    - 有註解功能 不過是用泡泡呈現，不是像hackpad的小字
    - 可從hackpad匯入
    - 有syntax highlight： [https://quip.com/blog/code-blocks](https://quip.com/blog/code-blocks)
    - 似乎沒辦法公開文件清單，一定要登入及加入團隊
    - 客服會來主動搔擾(X)關心(O)你
> 若單純文字工作，大推Quip 
> [name=Yang-Hsiang C]

> 作者標示只能滑歷史編輯記錄找，試算表中文輸入有一點便利性BUG，話說我沒遇過客服
> [name=a0000778]



## Notion

[http](https://www.notion.so/)[s://www](https://www.notion.so/)[.notion.so/](https://www.notion.so/)



## outreach dashboard

（維基媒體基金會出的協作平台，很多大學院校採用）
> PS.我不清楚，我只是在「維基醫學」票選中看到選項，問「[上官良治](https://www.facebook.com/shangkuanlc) 」可能會比較清楚。
> [name=Michael_Li]


請參考這個連結
[https://meta.m.wikimedia.org/wiki/Programs_%26\_Events\_Dashboard/zh](https://meta.m.wikimedia.org/wiki/Programs_%26_Events_Dashboard/zh)




