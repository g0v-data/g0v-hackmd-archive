---
title: "[PPT] 國內外類似專案 / Related Work"
tags: Promise Tracker,hackpad
---

> [點此觀看原始內容](https://g0v.hackpad.tw/PCvj3oj9myK)


#### ＊專案上層 Hackfoldr：[http://beta.hackfoldr.org/ppt](http://beta.hackfoldr.org/ppt) ＊


## 動民主 \- 真度計 / 長鼻尺

> 嗯，基本上就是同一個專案（紺） 嗚嗚現在才看到
> [name=Johnson L]

> 以名字來說 UI 好像滿多可以調整，之前 tisa 的 progress bar 還不錯看
> [name=Shelling F]

- [Hackpad](https://g0v.hackpad.com/--lzGKZQAwe7e) / [討論](https://g0v.hackpad.com/--lzGKZQAwe7e) / [Prototype](http://johnlin.tw/nose-meter/candidate.html#朱立倫)
- Prototype 階段
> 是個 Python 專案，不是 Flux/React 喔
> [name=Shelling F]


## 蘋果日報 [柯文哲百日監督條](http://www.appledaily.com.tw/realtimenews/article/new/20150212/559084/)

- 開發與維護：蘋果日報
- 資料來源與更新：蘋果日報負責，不開放編輯。
- 追蹤對象：僅有柯文哲、上任後 100 天（雖然好像只更新到第 51 天⋯⋯）
- 使用者互動：最下面的 Facebook comment
- 分成「改變」與「堅持」，下附新聞鏈結


## 對智利總統的 Promise Tracker


[http://deldichoalhecho.cl/](http://deldichoalhecho.cl/) by lfalvarez @ Chile
- 開發與維護：[Ciudadano Inteligente 基金會](http://ciudadanointeligente.org/)
- 資料來源與更新：不開放眾人編輯，網頁背後是 view only 的 [google spreadsheet](https://docs.google.com/spreadsheets/d/1XN3GxGzK0YRLvcTf9I0dSI1cPsYShu4MHw0EvZqfhm8/edit#gid=196760107)。
- 追蹤對象：僅有總統
- 使用者互動：僅有一個留言板，最後提供 email 讓人聯繫
- 個別政見與整體執行率計算百分比，以 progress bar 呈現
- Source code: [https://github.com/ciudadanointeligente/check-it](https://github.com/ciudadanointeligente/check-it) (django app,)

智利的這個專案相當成熟，他們的公開報告（[西班牙原文](https://docs.google.com/document/d/1nQuNV0y0eyZRRStK-B744OHkM12ixrof7EZWiOOXAkY/edit) / [Google 翻譯成英文](https://docs.google.com/document/d/1-w6h4p3FQzCtDwK239UdhJ71FctvrW1MRfssllgYud4/edit) \[建議閱讀此版\] / [Google 翻譯成中文](https://docs.google.com/document/d/1Yf9RHNeYZiRZ069VymUIwYX1S-FdbeuJoiRqdHKSftk/edit) \[x_x\]）將這個專案交代得非常完整。

他們計算完成度的公式是： (C\*0.5 + V\*0.5) * 100
其中 C 是 consistency variable，V 是 verification variable
> 求助 QQ 我看不懂 3.1 Consistency 與 3.2 Verification 的意思是什麼 QQ
> [name=Johnson L]

> 3.1ㄧ致性：政見與履行政策手段的ㄧ致性  如果ㄧ個工作可以達成政見就評分為1, 如果只能達成其中ㄧ部份就0.5, 如果政見只有在方法裡看到ㄧ點邊就給0.1, 如果不能驗證的就不給分。每個政見會有一個評分方法，給分方式經討論修正。
> [name=May K]

> 我發現他們的分數算法，好像無法處理「政見跳票」這回事，例如說當我們看了[這則新聞](https://tw.news.yahoo.com/%E8%AA%AA%E5%88%B0%E5%81%9A%E4%B8%8D%E5%88%B0-%E8%83%A1%E8%87%AA%E8%A1%8C%E8%BB%8A%E9%81%93%E6%94%BF%E8%A6%8B%E8%B7%B3%E7%A5%A8-202900033.html)，好像沒辦法幫胡市長打這個一致性分數 XD"
> [name=Johnson L]

> 應該可以喔, 大台中交通一六八」計畫是政策, 完成這個政策的方法, 建構五百公里通勤型及休閒型自行車道, 光這兩個就夠嗎? 那就要回頭去看這個計畫的實質內涵是什麼, 只要腳踏車就夠嗎? 有包含公車, 捷運, 機車等等嗎? 如果只有一個面向, 而這個面向是有完成部分政策, 那應該就是0.5分吧, 所以才會說, 評分標準也是需要修正的
> [name=May K]


> 3.2 可驗證：政見能否有標準可勾稽，如果檢查的欄位完整就給1分，不完整0.5,沒有檢查給0分。(這邊的標準就是3.1所說的評分方法)
> [name=May K]

> 「可以勾稽」這裡，好像是看是否有證明文件 (supporting document) 這樣嗎？ 如果未釋出政見實現的證明就 0 分；若有釋出文件但文件僅能證成部分的政見實現，就是 0.5 分；若釋出的文件們可以完整驗證此政見已經完全兌現，就是1分。
> [name=Johnson L]

> 你是對的, 可驗證是以提交出來文件是否可以證明實現政策的方法是否有完成, 3.2有提到, 但看到政策文件是不可能的, 所以只能從宣傳或新聞中來驗證
> [name=May K]

> 文件([這則新聞](https://tw.news.yahoo.com/%E8%AA%AA%E5%88%B0%E5%81%9A%E4%B8%8D%E5%88%B0-%E8%83%A1%E8%87%AA%E8%A1%8C%E8%BB%8A%E9%81%93%E6%94%BF%E8%A6%8B%E8%B7%B3%E7%A5%A8-202900033.html))-->施行方法(建構五百公里通勤型及休閒型自行車道)-->政策(「大台中交通一六八」計畫 )
> [name=May K]

> 只有一致性跟可驗證是不是不太夠啊，為了讓這分數衝高，我都挑簡單的政策來實行就好啦。我在想要不要加個重要性或是影響性之類的評估。
> [name=Wei-Zhi L]

> 所以每個政策應該要有權重之分嗎？
> [name=Johnson L]

> 我自己是覺得還好耶，有達成就是有達成，而且我相信不會有執政者會為了衝高在我們網站的數字， 而專門提出簡單的政見或只挑簡單的做。尤其平台會列出他在各項政見的個別完成度，是衝數字還是真的在做事，大家應該看得出來。
> [name=Johnson L]



## 歐巴馬 ＆ 共和黨 Promise Tracker


[http://www.politifact.com/truth-o-meter/promises/obameter/](http://www.politifact.com/truth-o-meter/promises/obameter/)
- 資料來源與更新：不開放眾人編輯，由媒體 Tampa Bay Times 更新
- 追蹤對象：[歐巴馬](http://www.politifact.com/truth-o-meter/promises/obameter/)，[共和黨](http://www.politifact.com/truth-o-meter/promises/gop-pledge-o-meter/)
- 使用者互動：無
- 分成 Not Yet Rated / In the Works / Stalled / Promise Kept / Compromise / Promise Broken.

## 澳洲 The Abbott Government


[http://www.abc.net.au/news/factcheck/promisetracker/](http://www.abc.net.au/news/factcheck/promisetracker/)
- 資料來源與更新：由媒體 ABC 更新
- 追蹤對象：Tony Abbott
- 分成 Broken, stalled, in-progress, delivered
- 呈現上以時間進行為主要經緯，用線把單一承諾的進度連起來。


## Facebook 監督型粉絲頁


[柯p新政進度條](https://www.facebook.com/kpmeter)  [http://www.facebook.com/kpmeter](http://www.facebook.com/kpmeter)
市民監督林智堅 [https://www.facebook.com/HsinChuMayorSupervision](https://www.facebook.com/HsinChuMayorSupervision)
林佳龍施政進度條 [http://on.fb.me/1rWbjdW](http://on.fb.me/1rWbjdW)
新北市施政監督專區 [https://www.facebook.com/NewTaipeiCitySupervise](https://www.facebook.com/NewTaipeiCitySupervise)

- 資料來源與更新：粉專管理人。柯Ｐ進度條的管理人，似乎是做民調的 NGO 開的專頁？
> 「[利益揭露：本粉絲頁接受政府與人民團體委託進行民意調查](https://www.facebook.com/kpmeter/info)」
> [name=柔慕 余]

> sorry，不小心消除連結，已補上。
> [name=柔慕 余]

- 追蹤對象：柯文哲、林智堅、林佳龍、朱立倫。
- 使用者互動：Facebook page 上留言討論、私訊管理人
- 管理人負責匯整項目。柯Ｐ進度條管理人還有訂定重要突破點
- 柯Ｐ進度條除了一般的進度條外，「數量」相關政見也有視覺化（如 1400 名社區輔警），非「數量」相關者則加入民調數字（如文化咨議委員會的支持度）。
- 可以用 "市政監督聯盟" 當作關鍵字去找，還蠻多相關群組的，只是這些群組政治鬥爭性質比較高，所以不見得需要參考 XD, ex. [https://www.facebook.com/groups/tainangogo/](https://www.facebook.com/groups/tainangogo/)


## [政誌](http://fact.g0v.tw/)


## [成為市政府的影子，如影隨行地監督](https://g0v.hackpad.com/39pf0Milpkz)


## [大台中市政監督網](https://www.facebook.com/taichungcivicwatch)


## [各地類似組織](http://www.coolloud.org.tw/node/80571)

> via  \_slack\_bot1 on IRC
> [name=nchild]



