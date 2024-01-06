---
title: "CC.tw x g0v文化部"
tags: g0v 文化部,hackpad
---

# CC.tw x g0v文化部

> [點此觀看原始內容](https://g0v.hackpad.tw/Y35BFwIsz1D)


2014/1/16 初次討論 / 文茵、nchild、ETBlue
> 很多問題其實可看 CC FAQ，先附上連結，日後整理 [http://wiki.creativecommons.org/Frequently\_Asked\_Questions](http://wiki.creativecommons.org/Frequently_Asked_Questions)
> [name=nchild]

### 相關網址

- g0v 文化部授權中心，雛形： [http://g0v.github.io/moc-license-center](http://g0v.github.io/moc-license-center) 、[共筆](https://g0v.hackpad.com/g0v--LoscL87LD2a)
- CC.tw 授權精靈 [http://creativecommons.tw/choose-license](http://creativecommons.tw/choose-license)
    - 雖有簡單的問卷，但並沒有解答到選擇授權時的盲腸，像是「選了這個以後會不會發生什麼無法預測的災難」「通常這種作品大家都選什麼」之類的問題
- CC.tw 素材搜尋 [http://creativecommons.tw/search](http://creativecommons.tw/search)
    - 原理是用 google 去搜幾個常見的有內建CC授權的平台，CC.tw 本身不做資料庫。之後 g0v 授權中心做好以後，可以加入被搜尋對象
    - 據說有內嵌CC授權標章的網頁語法，可以讓素材搜尋容易抓到你的作品，但是，看語法發現內嵌的標章圖片本身的alt屬性並沒有註明是哪一種CC，只有文字說明那一行才有寫，但許多情況是大家只會內嵌標章，因為比較好看…所以揪竟內嵌這個標章能不能幫助作品增加被搜尋到的機率呢？文茵說她要回去問問
> 標章圖片本身不是重點，metadata 讓搜尋引擎認得出的關鍵是 <a href="授權網址" **rel="license"**>   <\- 代表這個作品的授權是 href 所指名的授權條款網址。那網址本來就是唯一值，不同的網址就是不同的授權。如果是在網頁上，不寫文字而只有授權標章是無妨，只是一定要加連結不然認不出。
> [name=Po-chiang C]

- [校園著作權百寶箱](http://www.tipo.gov.tw/ct.asp?xItem=219540&ctNode=7561&mp=1)（著作權基本觀念）
- github 開發的 open source licencse selector [http://choosealicense.com/](http://choosealicense.com/)
- moon_c , jimmy: cc helper [http://g0v.github.io/cchelper/](http://g0v.github.io/cchelper/)

### 結論

- [ ] g0v文化部授權（素材）中心的CC標示要能連到說明頁面 - ETBlue
> 據說「授權中心」感覺像是有很多授權的地方，目前比較像是「素材中心」或「下載中心」
> [name=ET B]

- [ ] 釐清CC.tw素材搜尋功能是怎麼去抓取授權方式？只有內嵌圖片的話，會從授權說明頁網址抓取嗎？ - 文茵
> 就是看 meta data 而已，這邊要實作時可以找我討論一下想法（或者告訴我實作上的討論區在哪裡），因為實際上的問題應該是「我要怎麼把素材列出來，搜尋引擎才抓得到」，對吧？素材的 list 本身不要提供 matadata，只有素材 detail (每個素材自己獨立一頁）的地方提供，這樣搜尋引擎就不會混亂。
> [name=Po-chiang C]

- [ ] 列出插畫、音樂類的CC常見問題，供懶人包使用 - ETBlue

## 作品採用 CC 授權時的疑問


### 插畫創作者選擇CC授權時的疑問

- 好不容易畫完了，還要選這個東西，選完還要加浮水印，很煩耶 =3=
    - [ ] 解法：系統要有授權標章浮水印功能，在上傳時自動加上，不用每個人每張圖手動貼
    - [ ] 要讓選授權流程變得很順暢，提高意願
- 即使選了授權，會盜圖的人還是會盜圖，選授權也阻止不了他們啊，防君子不防小人 =3=
    - 解釋一：因為君子會一個一個作品都和原作者敲授權，例：nchild，所以，如果不使用CC授權釋出作品，對盜圖的人來說沒有差別，但對君子來說卻是一種懲罰，讓他們很難做事。所以為了獎勵好人，我們要認真選擇授權（握拳）
    - 解釋二：像是服貿rap的影片裡面就用到了服貿小人插圖，因為有事先選好授權，所以製作服貿rap的大德就不用大老遠跑來問我能不能用，直接拿去用就可以了，先選好授權可以讓別人容易拿去混搭，這樣子我的作品就產生了更多影響力。
- 我看到西西有六種，但不知道我的作品適合哪一種？選了以後會發生什麼事情？各有什麼好處壞處？最常用的是哪一種？有沒有誰用了什麼授權結果導致什麼悲劇的故事？
    - 搭配開源碼軟體專案的圖，最常採用的授權是 CC-By、CC-By-SA。
        - 因為其他四種授權（限制營利、限制衍生作品）不符合開放源碼的定義。
    - 為公民團體或社運活動畫的圖，最常採用的授權是____，因為____
    -
    - 平常自己接案子畫的圖…通常跟CC無關，會去找商業設計合約書、授權書範本來用
- CC0沒有在六種CC裡面耶，那是什麼可以吃嗎
    -
- 各種CC的縮寫正確來說到底怎麼寫…要加上版本嗎？
- CC跟WTFPL有什麼差別？為什麼一定要用CC這一套？
    - 因為CC有免責聲明比較安全……嗯，然後咧 ?_?
- 標章的圖樣和我的作品風格不合，搭起來很醜 =3=
    - 解法：官方答覆是可以改作CC標章，但並不建議大家這樣做。所以最好的解法就是……文字註明就好，不要放標章圖樣？！
- 糟糕，我選錯CC了，可以釋出之後說我要改用另一種CC嗎？
    - 可以，只要是著作權人，隨時可以改用另一種CC。
    - 但是已經用原本的CC授權取得作品的使用者，可以繼續用原授權使用。
    - [http://wiki.creativecommons.org/Frequently\_Asked\_Questions#Can\_I\_change\_the\_license\_terms\_or_conditions.3F](http://wiki.creativecommons.org/Frequently_Asked_Questions#Can_I_change_the_license_terms_or_conditions.3F)

### 音樂創作者選擇CC授權時的疑問

- 我的作品是音樂，裡面沒有地方可以放授權標章的浮水印耶 @.@
    - 解法：就…內嵌在作品頁面上，或者用各家音樂平台內建的授權選項
- 我的作品放在soundcloud.com，音樂工作檔放在blend.io，這樣也會被CC.tw的素材搜尋找到嗎？
    - Soundcloud 已經結合 CC 機制，上傳時可以選擇，所以理論上會被搜尋到。
- 我用garageband做音樂，不只想要CC還想要更激進的open source，可以嗎？
    - open source通常指的是程式碼，而且要能夠不限定載體，.band工作檔因為只能使用特定軟體打開，所以沒辦法所謂的open source，不過還是可以用CC的方式釋出。
- 如果用了買來的素材在自己 CC 授權的創作這樣可以嗎？/nchild
    - 如果只有使用權的話就會侵權，除非財產權讓與了。如果用到買來的素材，那我的作品就只能「部分CC」…用別人的東西要獲得權利人的允許，才可以加以變動/改作其作品，所以按照法律是不能無權利用（這邊是討論要利用/改作別人的著作）然後，如果要採用創用CC授權，是你有權利才能進一步思考的問題.../文茵
    - [http://wiki.creativecommons.org/Frequently\_Asked\_Questions#What\_things\_should\_I\_think\_about\_before\_I\_apply\_a\_Creative\_Commons\_license.3F](http://wiki.creativecommons.org/Frequently_Asked_Questions#What_things_should_I_think_about_before_I_apply_a_Creative_Commons_license.3F)

### 音像紀錄(?) (影片) 創作者選擇CC授權時的疑問

- 可以改作會不會扭曲影片原意？
- 可以營利就代表作品可以無償在商業電視台播出？而且商業電視台可以不用告知？
- 通常影片都會請受訪者簽同意書，受訪者會知道是哪個單位拍攝製作，但是如果cc出去，他可能會發現自己原本的訪問放在他不知道的地方，或是被改成自己不想要的樣子（通常拍攝結束我都會讓受訪者看一下拍攝內容，尤其是牽涉到個人隱私的部份），那導演或創作者應該如何對受訪者交代？
> 這些問題真是太重要了，cc 推廣的阻礙完全就在這些技術細節啊，要想辦法解決才行囧
> [name=ET B]

> 我可以再繼續列一些細節，待我想想
> [name=Angel S]


### Reference:

出自[【資訊人權貴專欄】Facebook 訊息用丟即棄，社運打網路戰要注意](http://techorange.com/2014/04/14/tools-for-social-movement/)
    就法律面來說， 想要提高你的論述 / 漫畫 / 影片的曝光率， 最好採用創用 CC 的方式授權分享你的作品。 [分享創意， 換取注意力](http://user.frdm.info/ckhung/s/cc.php)才符合注意力經濟的思維。 也要提醒大家別 [誤解非商業條款](http://ckhung0.blogspot.tw/2011/05/cc-non-commercial.html)。 採用 （與維基百科相容的） cc-by 或 cc-by-sa 才有利於擴散。

## 使用 CC 授權作品的疑問


### ND 授權的 D 定義

問題
1.  有個聲音檔，使用 CC 授權的 NCND3.0 釋出，其中的 ND，代表不能將這個聲音檔配上圖片後製作成影片，對嗎？
2.  如果這個聲音檔，配上全黑畫面，或者配上列出原作者授權資訊的畫面，目的只是為了將聲音格式轉成影片格式，也是不行的，對嗎？
回答
- 改作看法是加入別的元素，達到一定的創意程度，有可能到新的作品，1 侵權機會相當高
- 改作不是改變格式，而是改變創意成分，所以 2 應該是可以的

