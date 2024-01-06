---
title: "維基文庫吳守禮國台辭典開放"
tags: hackpad
---

# 維基文庫吳守禮國台辭典開放

> [點此觀看原始內容](https://g0v.hackpad.tw/7pyxbmwwYOk)


## 專案整合

1.  第一階段萌典協助：[2015均優台語駭客松](https://wikimedians-tw.hackpad.com/2015Hackathon-OpenWuDict-83yidnJy4bi)、[github](https://github.com/g0v/koktai)
2.  維基社群台語推廣：[維基社群吳阿公台語辭典專案](https://wikimedians-tw.hackpad.com/25luKxNEmqB)
3.  g0v其他相關專案：[iTaigi](https://g0v.hackpad.tw/moed7ct-taigi-neologism#iTaigi)
4.  [2015三月moed9ct萌典松](https://g0v.hackpad.tw/3-moed9ct#3-moed9ct)
5.  [2015九月moed6ct萌典松](https://g0v.hackpad.tw/9-moed6ct#9-moed6ct-)
6.  [2015十一月第⓭次萌典松](https://g0v.hackpad.tw/fC9waMmFmnN)
7.  2016二月[第⒁次萌典松](https://g0v.hackpad.tw/oeBceDBeNA2)
8.  2016四月[第⓯次萌典松](https://g0v.hackpad.tw/--Ksr7HH0T9Pd#:h=吳守禮華台辭典整合進入維基文庫)
9.  2016七月[第〡〦次萌典松 moed16ct](https://g0v.hackpad.tw/5u9QrhicuIy)

## 分頁上傳

1.  [目標排版](https://zh.wikisource.org/wiki/%E5%9C%8B%E8%87%BA%E5%B0%8D%E7%85%A7%E6%B4%BB%E7%94%A8%E8%BE%AD%E5%85%B8/%E3%84%85)
2.  由於紙本排版與網頁排版有不同的需求，不論是在閱讀習慣與辭典格式區分都與紙本不同，因此凡例應有原紙本凡例與電子版凡例。
3.  紙本辭典的排版和印刷有做過校正，但上傳之後還要做紙本校對。
4.  感謝a-tsioh和Alex協助，將python語法轉為Wiki的語法。
5.  缺字部分先整批上傳到wiki，之後再全部改為IDS。無法以IDS處理的字才留下以圖顯示。

## 動態組字解決方案

1.  感謝[意傳線上組字](http://xn--v0qr21b.xn--kpry57d/%E7%B7%9A%E4%B8%8A%E7%B5%84%E5%AD%97)協助組字系統。
2.  因顯示需求，組字不要在周邊留白。
> 這個是今年的新issue嗎？這個好像在上上次的萌典松已克服
> [name=Chou S]

> 不適新issue，只是確認。感謝！
> [name=A-Han L]

> OK那這個已經解決
> [name=Chou S]

1.  組字系統server將設立於[WMFLab](https://wikitech.wikimedia.org/wiki/Main_Page)，MG已申請帳號與金鑰；接下來要將組字系統Engine安裝在Lab上；並且讓維基其他平台皆能使用，因此還需要再安裝IDS extension外掛讓維基其他平台連到Engine使用。
> 我說一下我今天的進度，已安裝上去，不過遇到技術問題（外面看不到wbflabs雲端裡面的server），看了很多官方文件沒清楚指引， 得等週一上班日，我跟總會的技術人員尋求技術解答，將來 組字server試行網址在這裡 [https://tools.wmflabs.org/idsgen/](https://tools.wmflabs.org/idsgen/)
> [name=Chou S]

> 2/22/2016 [WMFLab](https://wikitech.wikimedia.org/wiki/Main_Page)官方用的java servlets容器不同，我要來改用不同的作法
> [name=Chou S]


1.  server設立後除動態組字外，若辭典開發其他線上檢索功能亦能使用。
> 這個意思是？？？
> [name=Chou S]

> 這個部分誤植，我把維基育竹苗討論時提到的另一個方案貼錯到這邊來。 囧rz
> [name=A-Han L]



###  圖文拾遺（期待字典上線推廣時分享守禮仙的故事）

- 2000 年傅月庵向吳守禮致敬[文章](http://www.ylib.com/class/topic/show1.asp?Object=gossip&No=1279)
- 故紙堆中的吳守禮老先生[照片](https://www.facebook.com/photo.php?fbid=1045167655519499&set=a.107173652652242.5310.100000788247231&type=3&theater)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ccb0f252b239bbbab737ea397008c4bf)

