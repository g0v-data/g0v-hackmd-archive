---
title: "貧富差距數據透明化"
tags: 財稅,hackpad
---

# 貧富差距數據透明化

> [點此觀看原始內容](https://g0v.hackpad.tw/Ko9q8O2Y1rr)

:accept:  [**20等分位所得差距 又要公布了**](http://news.ltn.com.tw/news/business/paper/776603)
> 可能之後就轉成視覺化的實作坑吧！
> [name=nchild]


## 直指問題

請先看[這篇報導](http://news.housefun.com.tw/news/article/17321463236.html)，『自今年起，財政部將不再公布依560餘萬綜所稅申報戶算得的10等分位、20等分位所得分配統計，這項廣為各界引用的數據將吹熄燈號，停止發布的理由是「為符合國際慣例，並與國際接軌」』。
缺乏貧富差距分佈，最大的直接影響就是無法（或難以）判斷貧富差距是否惡化，往後將只有總體經濟數據，無法衡量經濟政策的所得重分配效果。
> 請財政專業夥伴協力補完問題的重要性，論述缺乏此數據的後果。
> [name=nchild]

> 就統計學家的觀點，貧富差距逐年增加是顯著的事實，參考
> [name=Johnson H]

> 應該是會缺乏最高5%的所得資料喔，還是可以用5等分位資料算貧富差距，只是凸顯不出極端的情形，當貧富差距不嚴重時，也許影響不大，但重點是當貧富差距逐年擴大的時候，這個資料有某種程度的警示性。
> [name=Peggy C]

> 上次黑客松 @choupi 有做一些現有資料的分析
> [name=Chia-liang K]

> 事實上稅收資料並不是貧富差距（貧富差距會補上社會福利的所得），但是稅收結構資料仍然非常重要
> [name=Chia-liang K]

> 10分位、20分位跟5分位的差別就是5分位根本畫不出薪水分佈圖啊！只有五個點哪知道曲線會長怎樣？到底社會是M型、L型還是正常的鐘狀，只有5個點什麼都畫不出來。這也是為何我下面附上的CIA、OECD都至少是10分位，這樣才有知道我國薪資結構差距的意義在。
> [name=Austin W]


## 資料在哪裡

- [主計總處統計專區](http://www.stat.gov.tw/np.asp?ctNode=452)[家庭收支調查](http://www.stat.gov.tw/np.asp?ctNode=509)
    - 10等分位、20等分位所得分配統計到今（2014）年為止
- [中研院學術調查研究資料庫](https://srda.sinica.edu.tw)
> 不確定不公佈所得分配統計之後，還有沒有資料可以自行生出貧富差距。
> [name=nchild]

> 還是可以用5等分位資料算貧富差距，若想要10等分位、20等分位的貧富差距資料，除非花錢去主計總處申請row data，自己計算，申請費不算很貴，但也不覺得便宜QQ。
> [name=Peggy C]

> 如果是這樣問題還不算太大，[Peggy](https://g0v.hackpad.tw/ep/profile/mWOtyynXjZ0) 可以貼一下申請方式嗎？
> [name=nchild]

> 行政院主計處 [統計資訊提供](http://www.dgbas.gov.tw/lp.asp?ctNode=2361&CtUnit=456&BaseDSD=7)，第一類資料其實上[中研院學術調查研究資料庫](https://srda.sinica.edu.tw/)，會員就可以免費申請，第二類資料比較麻煩。
> [name=Peggy C]

- 網路上找得到的歷年資料
    - [http://readata.org/datasci/lie-and-statistics/](http://readata.org/datasci/lie-and-statistics/)
| 年度(萬元) | 94年 | 95年 | 96年 | 97年 | 98年 | 99年 | 100年 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 最低5% | 7.2 | 6.9 | 7.2 | 6.9 | 5.1 | 4.6 | 4.8 |
| 最低20% | 29.8 | 30.4 | 31.2 | 30.4 | 28.2 | 28.9 | 29.6 |
| 最高20% | 180 | 183 | 187 | 184 | 179 | 187 | 183 |
| 最高5% | 397 | 402 | 435 | 451 | 383 | 432 | 464 |

## 開發資源

> 請寫上 source code 存放的位置（version control repository location），以及 Issue Tracking System 的位置。
> [name=isacl]

> 如有團隊專屬聊天頻道，請寫上頻道在哪裡，如何加入。
> [name=isacl]


## 可以做的事

> 是否有簡單的畫面雛型或是流程代表你想做的事情？
> [name=isacl]

先從法律面與國際趨勢開始研究，目前想到以下工作項目：
- 國際慣例蒐集、整理（資料可先放下方 Reference）
    - 就各國做法與台灣比較，以視覺化呈現
> 確認各國做法、國際慣例為何，何謂「與國際接軌」
> [name=nchild]

> 日本厚生勞動省，採用Gini coefficient 以及十分位比較，每10%統計一個數據，共10個，平成28年相關[文件在此](http://www.mhlw.go.jp/file/04-Houdouhappyou-12605000-Seisakutoukatsukan-Seisakuhyoukakanshitsu/h23hou_1.pdf)。
> [name=Hsieh P]

    - 政府資訊公開法
        - 依照政府資訊公開法9條1項：「具有中華民國國籍並在中華民國設籍之國民及其所設立之本國法人、團體，得依本法規定申請政府機關提供政府資訊。」，向稅務機關要求提供無姓名及可資識別申報者個人資料的所得總額統計。理論上來說，政府資訊只要不違反第18條政府資訊公開限制，比如個人隱私，政府就應該公開。
    - 其他法律（請補充）
> 看看有無以現有法規要求財政部繼續提供數據的空間。
> [name=nchild]

- 民間自幹版貧富差距分配統計（若公開資料足以呈現）
    - 互動視覺化圖表
> 就公開資料來硬幹是困難的，不過若是用統計方法以歷年資料來「預測」當年度的20等分、10等分、5等分是有可能的。
> [name=Johnson H]

> 有必要進行預測我可以做
> [name=Johnson H]

- 發函財政部要求提出進一步說明（可能的話先做完前面幾項）
    - 要求政府依法公開資訊（若法律研究支持）
- 發起各界連署要求恢復提供
> 新聞中有提到胡正勝院士也會撰文籲請政府恢復原來發布的內容，不知道有沒有辦法一起配合？
> [name=Peggy C]

> 好的，加入工作項目。
> [name=nchild]

> 已聯繫胡教授，此刻他在國外開會，回來會聯繫。
> [name=nchild]


上次hackath8n的時候做了一下小研究
資料是從財政部財政資訊中心抓的99年度綜合所得稅申報核定統計專冊
[http://www.fia.gov.tw/ct.asp?xItem=2532&ctNode=730&mp=4](http://www.fia.gov.tw/ct.asp?xItem=2532&ctNode=730&mp=4)
因為原始資料是HTML格式 orz 把一些已經整理過的表格轉成csv格式放在github上
[https://github.com/choupi/isa99](https://github.com/choupi/isa99)
並試著畫了幾個圖, 想從這些資料看看貧富差距
各縣市平均所得分佈 [https://choupi.github.io/isa99/county.html](https://choupi.github.io/isa99/county.html)
二十分位平均所得分佈 [https://choupi.github.io/isa99/q20.html](https://choupi.github.io/isa99/q20.html)
所得總額分佈 與 戶數比率 [https://choupi.github.io/isa99/in.html](https://choupi.github.io/isa99/in.html)
希望有些幫助

## 授權

> 如果這是一個新專案而非既有專案，想要用什麼授權方式釋出你們的成果？
> [name=isacl]

CC0
> 若本專案執行過程與成果產生任何有著作權之著作。程式著作（若有）則請技術夥伴填寫。
> [name=nchild]


## 目前開發進度、狀況、遇到的問題

- 4-30 中研院胡教授在國外，回國才會聯繫
- 4-29 協力挖坑填坑 @hackpad
- 4-28 概念發想

## Reference

> [http://ipa.logdown.com/posts/143277-g0v-proposal-tips](http://ipa.logdown.com/posts/143277-g0v-proposal-tips)
> [name=isacl]

- [**World Development Indicators | The World Bank**](http://wdi.worldbank.org/table/2.9)
    - 美國
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_94bac8d9e5b7b6aee3293d8739d78799)
 [http://inequality.org/income-inequality/](http://inequality.org/income-inequality/)
  計算到top 1%
 [http://zh.scribd.com/doc/208218671/Appendix](http://zh.scribd.com/doc/208218671/Appendix)
  提供top 5% income data
  美國稅收統計資料網站[http://www.irs.gov/uac/SOI-Tax-Stats-Individual-Income-Tax-Returns-Publication-1304-(Complete-Report](http://www.irs.gov/uac/SOI-Tax-Stats-Individual-Income-Tax-Returns-Publication-1304-(Complete-Report))
  2011年Selected Income and Tax Items的excel檔，級距非常的細：[http://www.irs.gov/file_source/pub/irs-soi/11in11si.xls](http://www.irs.gov/file_source/pub/irs-soi/11in11si.xls)

    - [英國](http://tutor2u.net/blog/index.php/economics/comments/life-in-the-middle-income-distribution-in-the-uk/)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_8b9a410c9c03836f48d70a064ac8c470)



- 美國Current Population Survey (CPS)
    - [http://www.census.gov/hhes/www/cpstables/032013/hhinc/toc.htm](http://www.census.gov/hhes/www/cpstables/032013/hhinc/toc.htm)
        - HINC-05 五分位還有Top5%，HINC-06按金額分
    - Household income in the United States
    - [http://en.wikipedia.org/wiki/Household\_income\_in\_the\_United_States](http://en.wikipedia.org/wiki/Household_income_in_the_United_States)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_261bef3885813e27a0611fa77e21dde4)

- 澳洲Australian Bureau of Statistics
    - [http://www.abs.gov.au/AUSSTATS/abs@.nsf/DetailsPage/6523.02011-12?OpenDocument](http://www.abs.gov.au/AUSSTATS/abs@.nsf/DetailsPage/6523.02011-12?OpenDocument)
        - Household Income and Income Distribution, Australia 2011-12 - Detailed tables 裡面的Table5C有P10, P20, P50, P80, P90，然後P90/P10, P80/P20, ... Gini等都有
- OECD網站公佈的是前後10% [http://goo.gl/L47Od6](http://goo.gl/L47Od6)
- CIA世界統計資料庫 前後10%[http://goo.gl/](http://goo.gl/rYCxbj)[rYCxbj](http://goo.gl/rYCxbj)
- 歐盟部份國家統計  精確到前後0.01%[http://goo.gl/cZOUcM](http://goo.gl/cZOUcM)
- [Two Monkeys Were Paid Unequally](http://youtu.be/meiU6TxysCg) （貧富不均的猴子實驗）
補充貧富差距相關新聞報導、理論與論述。
- 歷年相關新聞報導
    - 自由時報-貧富差距飆至93倍 歷史新高 [http://www.libertytimes.com.tw/2012/new/mar/27/today-t3.htm](http://www.libertytimes.com.tw/2012/new/mar/27/today-t3.htm)
    - 尹啟銘-讓國人正確瞭解當前貧富差距, [http://www.ndc.gov.tw/m1.aspx?sNo=0016735](http://www.ndc.gov.tw/m1.aspx?sNo=0016735)
> 所謂的「無法與國際接軌」與時任經建會主委的尹啟銘先生一致
> [name=Johnson H]

    - 自由時報-最富5％VS.最窮5％ 所得差距逾96倍 [http://www.libertytimes.com.tw/2013/new/jun/10/today-t2.htm](http://www.libertytimes.com.tw/2013/new/jun/10/today-t2.htm)
    - TVBS-貧富差距擴大？ 逾9成民眾：嚴重！[http://news.tvbs.com.tw/entry/517145](http://news.tvbs.com.tw/entry/517145)
    - 爺們在台大的演講，對使用貧富差距數據的資料分析有精闢的見解。請從28min開始看 [https://speech.ntu.edu.tw/sng/ci/index.php?c=User&m=vod\_search&srh\_PID=1&film\_sn=1595&show=1&key\_no=81](https://speech.ntu.edu.tw/sng/ci/index.php?c=User&m=vod_search&srh_PID=1&film_sn=1595&show=1&key_no=81)
> 這個talk不賴! 在32min的時候，管爺有秀出台灣1980, 1990, 2000, 2005, 2008每戶所得的「分布」，也就是說除了5等分, 10等分, 20等分之外，相關統計單位根本就有記錄所得整體分布 (類似reference裡面美國 annual household income 那張圖) !!!
> [name=Johnson H]

- 論述
    - [統計指標與謊言](http://readata.org/datasci/lie-and-statistics/)

