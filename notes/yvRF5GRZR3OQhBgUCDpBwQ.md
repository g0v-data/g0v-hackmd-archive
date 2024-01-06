---
title: "OpenEvSys 中文化"
tags: hackpad
---

# OpenEvSys 中文化

> [點此觀看原始內容](https://g0v.hackpad.tw/mouFan2X4Nd)


提案: TonyQ
[https://www.facebook.com/groups/g0v.general/permalink/647760865300323/](https://www.facebook.com/groups/g0v.general/permalink/647760865300323/)

feature branch: [https://github.com/swem/OpenEvSys/tree/zhtw_feature](https://github.com/swem/OpenEvSys/tree/zhtw_feature)
demo 網站 [http://162.222.176.96/demo](http://162.222.176.96/demo)
初步成果截圖：[http://gyazo.com/ec5e43ca15f2d63c00cce68c9979ca0a](http://gyazo.com/ec5e43ca15f2d63c00cce68c9979ca0a)
> 注意，此網站僅供測試用， 測試過程視需要可能reset 資料庫，請勿放置重要資料
> [name=Chen-Han H]

> 測試帳號密碼：
> [name=Chen-Han H]

> admin/admin
> [name=Chen-Han H]

> dataentry/dataentry
> [name=Chen-Han H]

> analyst/analyst
> [name=Chen-Han H]


(2014-07-15) 這幾天寫信給 huridocs, 跟他們表示我們會翻譯中文，他們提供了一個 excel 檔，表示我們只要把對應的 key 翻譯完畢再交給他們就可以。
~現有各國語系文字檔，目前計~~畫~~參考 en.json 英文語系~
[~https://github.com/huridocs/OpenEvSys/tree/master/translate/translated/js~](https://github.com/huridocs/OpenEvSys/tree/master/translate/translated/js)
請在 Google Spreadsheet 上進行翻譯
[https://docs.google.com/spreadsheets/d/1ZE-t87UT9QB50fqGedOyc6Se1GU2l1Njo_9v43Kwgcg/edit?usp=sharing](https://docs.google.com/spreadsheets/d/1ZE-t87UT9QB50fqGedOyc6Se1GU2l1Njo_9v43Kwgcg/edit?usp=sharing)
> ethercalc 反應很慢而且難以用 control +f  直接search key ，我覺得直接用個 google spreadsheet 或許比較快。
> [name=Tonyq W]

> ok, 我把目前結果放到 Google Spreadsheet上了。Google Spreadsheet可同步輸出[tsv](https://docs.google.com/spreadsheets/d/1ZE-t87UT9QB50fqGedOyc6Se1GU2l1Njo_9v43Kwgcg/export?format=tsv&id=1ZE-t87UT9QB50fqGedOyc6Se1GU2l1Njo_9v43Kwgcg&gid=43848623)
> [name=Chen-Han H]

> 2014-07-16：現在每一分鐘，demo site 都會更新來自 google doc 的翻譯字串，大家可以即時的在網頁上比對並進行翻譯。
> [name=Chen-Han H]


目前著手進行：
> 架設 demo 網站
> [name=Chen-Han H]

> 原本的 translation.txt機制太難用，來做出從 json 翻譯出需要的字典檔的 fork
> [name=Tonyq W]

> Done
> [name=Tonyq W]

> 應急可以先 merge 我的 commit 
> [name=Tonyq W]

> [https://github.com/tony1223/OpenEvSys/commit/bb87ef6c11bd43277f6a8bcf11b590748f3c6eb4](https://github.com/tony1223/OpenEvSys/commit/bb87ef6c11bd43277f6a8bcf11b590748f3c6eb4)
> [name=Tonyq W]


> 我把翻譯的原始檔放在這 [https://github.com/tony1223/OpenEvSys/blob/master/translate/translation\_zh\_tw.json](https://github.com/tony1223/OpenEvSys/blob/master/translate/translation_zh_tw.json)
> [name=Tonyq W]

> 然後跑 [http://localhost/OpenEvSys/translate/generate_zhtw.php](http://localhost/OpenEvSys/translate/generate_zhtw.php) 就能自動建立對應的語系檔了。
> [name=Tonyq W]

> 了解。我已經把你的 patch 放上測試網站，可以看初步成果截圖。
> [name=Chen-Han H]

> 我的想法是可以把目前翻譯好的放回 translations.txt ，然後用 ethercalc 來編輯。
> [name=Chen-Han H]

> 在ethercalc 上翻譯好以後，可以輸出 csv，到時候再轉成 translations.txt，然後發 pull request 給 huridocs/OpenEvSys
> [name=Chen-Han H]

> OK ;)
> [name=Tonyq W]

> 好像有些字沒上去，是因為那是後來翻的嗎？ ex. EVENT_TITLE
> [name=Tonyq W]


目前遇到的困難：
> 這個 project 裡面還有個 translations.txt，裡面的詞都是一樣的。目前我看 php 的 code 的猜測是，其實我們要翻譯 translations.txt，然後再去 generate 這些 en.json 檔。有熟悉php 的朋友可以幫忙確定一下嗎?
> [name=Chen-Han H]

> Confirmed , 你說的沒錯. 
> [name=Tonyq W]

> 根據 [https://github.com/huridocs/OpenEvSys/blob/master/translate/generate.php](https://github.com/huridocs/OpenEvSys/blob/master/translate/generate.php) 的邏輯的確是這樣
> [name=Tonyq W]

> 不過我 translation.txt 看起來是 tab 分隔的 csv ，多語系擠一起不好編輯，我覺得我們還是先照原本計畫先翻完 .json，然後再來想辦法塞回 translation.txt，照理說是會 1:1 對應的。
> [name=Tonyq W]

> 或是簡單點，直接 hack 他，把 json 讀回來變成 translation array 後面流程照舊，
> [name=Tonyq W]

> 語系檔的部份我應該已經先做出條應急的路了，請參考「目前著手進行」裡面我的留言。
> [name=Tonyq W]




### 討論區

> 699 "ervention information"不知如何翻譯。
> [name=glll4678]

> 705 "Erase" 跟 707 "Clear" 都翻成「清除」？
> [name=glll4678]

> 推測一個是指定範圍的清除另一個是全部清除
> [name=艾俠]

> user: 使用者, person是翻成「人」嘛XD?
> [name=宏昱 林]

> person應該是翻成人 
> [name=Davidou O]

> 這裡面的 person 在這裡應該是用來指資料庫裡存放的人的資料，可能用「個人」或「對象」之類的。確切說法應該還是要看介面裡怎麼用。
> [name=艾俠]

> PERPETRATOR"應翻作"加害人"
> [name=glll4678]

> 侵犯者？
> [name=艾俠]


備註：開發完成後，統一將語系名稱改為 zh_TW

