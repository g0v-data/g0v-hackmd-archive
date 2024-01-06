---
title: "工時紀錄 app"
tags: hackpad
---

# 工時紀錄 app

> [點此觀看原始內容](https://g0v.hackpad.tw/HmVaQeCbwzD)


這是一個還在發想階段的 g0v 的專案，用來記錄工時，並且可以選擇將匿名的工時紀錄存到雲端供勞動主管單位知道要先稽核哪些公司。同時提供計算加班費與各式勞工相關資訊如產假、退休、資遣等資訊。

背景：Yuren Ju 曾做過一些跟勞工議題相關的專案如[一例一休修法計算機](https://g0v.github.io/workweek/#!/)與[勞動權益](https://yurenju.github.io/laborrights)網站，正在構思要寫一個工時紀錄的 app 一來讓勞工可以自主記錄與分析工時狀況，二來這些資訊也可以匿名的提供給勞工局，提升勞檢效率。

在 2017/09/16 的黑客松有一些[深入技術的討論](https://g0v.hackpad.tw/hqQGdzE8KJn)，有興趣也可以參考。下面盤點一下勞動權益網站目前的功能，並且介紹工時紀錄 app 想要的功能。

## 勞動權益網站


用手機打開此網站：[https://yurenju.github.io/laborrights/](https://yurenju.github.io/laborrights/)

1.  輸入基本資訊如年齡、到職日、性別以及月薪，根據這些資訊可以提供更多資訊給勞工
2.  最低特休天數
3.  是否可申請退休
4.  產假與小產的休假資訊
5.  計算加班費
6.  資遣與離職資訊如最少資遣費用以及公司應於哪天告知你

勞動權益可以再做更多的：
1.  退休倒數計時
2.  退休金

勞動權益網站的問題：
1.  到底名字應該要是**勞動權益**，還是**勞工權益**
2.  使用者不會想每天使用，需要一個可以每天使用的誘因
3.  目前每日使用量幾乎沒有，原因也很容易理解，不是每個人都需要使用這個網站

## 紀錄工時 app


因為已經有勞動權益網站的基礎，紀錄工時 app 應該要包含勞動權益網站上面的功能，同時額外再提供更多功能，目前覺得要提供的功能有：

1.  即時記錄上下班打卡時間，可以的話允許設定打卡提醒
2.  事後記錄上下班打卡時間（要跟上面的即時紀錄有區別，在手機沒有被 JB 或 root 的狀況，即時記錄上下班時間應該是要相對可以信任的）
3.  依據上下班打卡資訊，紀錄該月公司最低應該付出的加班費
4.  可以看每月紀錄以及每週紀錄，包含自己的工時資訊以及至少應該得到的加班費，以及計算明細
5.  將紀錄提供上網的機制（選用），紀錄資訊時應該要確保資料某種程度的匿蹤性，確保隱私安全，並且清楚的告訴使用者為什麼要記錄這些資訊，主要是提供給政府稽查公司的先後順序
6.  另外應該要提供「勞動權益」網站所有功能

另外要思考的點：
1.  怎麼吸引使用者每天都會想使用，可以增加每天都打卡的機率。
> 想到我同事有的人會被要求寫週報，什麼事情做了多久，也許可以用工作紀錄的方式去紀錄工時？
> [name=Chuck L]

> 其實搭配蕃茄鐘就可以了啊 XDD 每半個小時會記錄一次自己做什麼
> [name=Yuren J]

> 這樣做一做最後就很像外國的那些打卡程式了 XD
> [name=Chuck L]

2.  怎麼確定使用者打卡的正確性？可以要求打卡時拍一張照片，比如說打卡鐘或是時鐘、日曆。這張照片不用上傳雲端，但是可以把照片 \+ 紀錄的 hash 上傳雲端，之後如果真的要確認真實性，可以用這個 hash 驗證這張照片。
> 上傳到FB/Plurk/Instgram，然後設定權限是只有本人看得到，會不會比較好？
> [name=Chuck L]

3.  諮詢律師如何最大化紀錄在法律上的證據能力
4.  資料儲存／備份／回復方案（修手機或換手機的狀況）

## UI 草稿


沒有 UI Designer，我就只好自己先畫一下，等到有設計師受不了再來想這個 UI。

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d6605e3c8eceb675ca941cab27671ce1)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_3ab3adf9040f079d07038f3be0c850ea)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_1aae5628811aa28d68b79d2dd1a8148e)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_5d9f45b072b359cf1cb07002b024e528)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_14519fe7fec974b3b18eb4a8a8b2a59f)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0a71537e682fc2eff02eeeb10ba9f6b9)

## 相關 app

這邊記錄了類似的 app 已經做了工時紀錄。

### 工時記錄 \- 考勤 \- 打卡


**介紹**：工時紀錄的功能做得非常完備，也可以計算加班費，但是猜想應該不能計算一例一休。跟「勞動權益」相比對於沒有資遣、產假、退休等等資訊，不過也不是 app 主要聚焦的功能。這邊有篇文章介紹 [工時記錄 \- 打工族必備，時數、薪資、加班費計算，還可直接打卡計時](https://steachs.com/archives/28621)。
**平台**：[Android](https://play.google.com/store/apps/details?id=com.aadhk.time&hl=zh_TW)

### 鹹魚打卡王 My Punch


**介紹**：單純的打卡記錄
**平台**：[iOS](https://itunes.apple.com/tw/app/%E9%B9%B9%E9%AD%9A%E6%89%93%E5%8D%A1%E7%8E%8B-my-punch-%E5%B7%A5%E6%99%82%E7%B4%80%E9%8C%84-%E4%B8%8A%E4%B8%8B%E7%8F%AD%E6%89%93%E5%8D%A1-%E8%80%83%E5%8B%A4-%E8%BE%A6%E5%85%AC%E5%AE%A4%E7%B0%BD%E5%88%B0%E7%B3%BB%E7%B5%B1/id996812959?l=zh&mt=8)

### 班表小幫手


**介紹**：可以排班，雖然跟工時紀錄比較沒有關係，不過也是個很不錯的參考 app。
**平台**：[iOS](https://itunes.apple.com/tw/app/%E7%8F%AD%E8%A1%A8%E5%B0%8F%E5%B9%AB%E6%89%8B/id994771057?l=zh), [Android](https://play.google.com/store/apps/details?id=lincyu.shifttable&hl=zh_TW)
**其他跟班表相關的 app**：
- [PayDay](https://itunes.apple.com/tw/app/%E5%B7%A5%E8%B3%87%E8%A8%88%E7%AE%97%E6%A9%9F-%E8%A8%88%E7%AE%97%E5%99%A8-%E8%96%AA%E7%AE%97-%E6%8E%92%E7%8F%AD%E8%A1%A8-%E6%99%82%E9%96%93%E8%A1%A8-payday/id1137032845?l=zh&mt=8) (iOS)
- [工作時間管理器 \+ 輪班日曆,工作安排和工作管理器](https://itunes.apple.com/tw/app/%E5%B7%A5%E4%BD%9C%E6%99%82%E9%96%93%E7%AE%A1%E7%90%86%E5%99%A8-%E8%BC%AA%E7%8F%AD%E6%97%A5%E6%9B%86-%E5%B7%A5%E4%BD%9C%E5%AE%89%E6%8E%92%E5%92%8C%E5%B7%A5%E4%BD%9C%E7%AE%A1%E7%90%86%E5%99%A8/id1003684086?l=zh&mt=8) (iOS)

一些值得再研究的 apps / services
- [Hours Keeper Pro](https://itunes.apple.com/us/app/hours-keeper-pro-timesheet-tracking-billing/id559701364?mt=8): UI 做得很好看

發現有蠻多線上打卡服務的（不確定是不是會跟公司的IT系統整合）
[https://www.google.com.tw/search?q=employee+clock](https://www.google.com.tw/search?q=employee+clock)

