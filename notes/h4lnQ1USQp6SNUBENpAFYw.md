---
title: "hackpad 延伸功能"
tags: 新手教學,hackpad
---

# hackpad 延伸功能

> [點此觀看原始內容](https://g0v.hackpad.tw/ogVzpCI6IJp)

> 新坑
> [name=Yuan C]


### IRC 即時轉播 To Hackpad (irc2hackpad)


不論大小松或是g0v的成員各自參與gov公開活動時，常常會藉由irc的實況轉播讓其他人遠端共同參與，但是事後需要將irc的紀錄複製到hackpad，除了手動複製貼上還需要人工整理，希望透過bot來減低人工處理的時間。

使用情境:
1.  bot 在g0v channel常駐
2.  使用以下的命令 _textlive start \[title\] 即開始文字轉播
3.  bot會自動將轉播者的文字轉發到hackpad
4.  其他人若要加入文字轉播協作則是 _textlive join
5.  有加入協作者若要結束文字轉播則輸入 _textlive end

> 感覺上也可以從 logbot 的紀錄頁面裡挑「時間範圍、使用者名稱」再產生，這樣可以回溯既有的紀錄，也許可以解決漏打指令的問題？
> [name=Audrey T]


### hackpad 共筆 To Blog (hackpad2blog)

> 本來是想直出logdown 但是目前logdown沒有api, 所以要自己hack
> [name=Yuan C]

> 這個超需要，這樣公報也可以匯出到Logdown 不然現在都是半自動。
> [name=Lee]

每個blog共同協作的環境差異很大，希望透過chrome extension來完成，hackpad共筆協作即可發佈道到blog平台。

使用情境:
1.  裝chrome extension
2.  hackpad協作
3.  使用chrome extension登入該blog
4.  將hackpad的內容一鍵發布至blog

技術討論
hackpad這邊使用markdown輸出，透過chrome extension呼叫伺服器端服務，把markdown輸出到該blog。
> 融合以上兩者就可以使用irc寫blog了 XDD 
> [name=Yuan C]


### hackpad To 公報

- [公報自動化](https://g0v.hackpad.com/CULVn9DDzEU)

### hackpad To SayIt

- [Sayit](http://sayit.mysociety.org/)
- Hackpad to SayIt importer [http://pad.archive.tw:8080/](http://pad.archive.tw:8080/)
    - Create a new instance at [mySociety SayIt](http://sayit.mysociety.org/instances/add), or use an existing instance.
    - Click **Import Speeches** to show the **/import/akomantoso** screen.
    - Enter the URL [**http://pad.archive.tw/**](http://pad.archive.tw/) followed by Hackpad source URL (with no spaces in-between) to import the section.
- case: ?

## 其他構想

- hackpad2csv
- hackpad2csv2GeoJson（地址？）
- hackpad2spreadsheet
- hackpad2spreadsheet2[Timemapper](http://timemapper.okfnlabs.org/)
- hackpad2[Excel2Earth](http://excel2earth.blogspot.tw/)


