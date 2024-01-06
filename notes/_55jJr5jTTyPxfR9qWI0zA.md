---
title: "Public Money, Public Code: 為什麼用人民納稅錢所建立的軟體與資訊系統，卻沒有以自由軟體授權公開釋出呢？"
tags: hackpad
---

# Public Money, Public Code: 為什麼用人民納稅錢所建立的軟體與資訊系統，卻沒有以自由軟體授權公開釋出呢？

> [點此觀看原始內容](https://g0v.hackpad.tw/MDDEWRPg0uX)


[https://publiccode.asia/zh_tw/](https://publiccode.asia/zh_tw/)

我參與的社群：FOSSASIA ([http://](http://fossasia.org)[f](http://fossasia.org)[o](http://fossasia.org)[s](http://fossasia.org)[s](http://fossasia.org)[a](http://fossasia.org)[s](http://fossasia.org)[i](http://fossasia.org)[a](http://fossasia.org)[.](http://fossasia.org)[o](http://fossasia.org)[r](http://fossasia.org)[g](http://fossasia.org))  除了積極貢獻並推廣open source project ([FOSSASIA · GitHub](https://github.com/fossasia))之外，目前也希望更多social tech領域的群眾一同貢獻並分享，其中一項為響應歐洲自由軟體基金會(FSFE)發起的Public Code([http://publiccode.eu](http://publiccode.eu)) 的專案，並希望推廣至亞洲各國: [Public Money, Public Code](https://publiccode.asia/).。

推廣影片：目前有英文、中文及諸多歐洲語言，
Public Money? Public Code!
by [Free Software Foundation Europe](https://vimeo.com/fsfe)
[https://vimeo.com/232524527](https://vimeo.com/232524527)

[https://www.youtube.com/watch?v=iuVUzg6x2yo](https://www.youtube.com/watch?v=iuVUzg6x2yo)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d694ff8dfa86b468a33f7c590c680a80)

台灣法律系統為大陸法系，相較於英國等海洋法系的差異為：大陸法系法條必須非常詳細，海洋法系先提出原則，再用眾多的判例或例外來補全法條中所缺少的部分。

R: 國發會目前有類似的規範，
小方：唐鳳推廣OpenAPI，其內容並非是(特定的)API，反而是一種(針對API的)文件編寫準則，[https://www.slideshare.net/autang/ss-77881578](https://www.slideshare.net/autang/ss-77881578)
Lisa：目前推廣open source最大的難處在各級政府長官，工程師或基層執行單位沒壓力
caasi:  開源軟體所製作的內容是否需要開放？像是wordpress製作的網站，但本身有修改一些部分，該修改的部分是否需回饋回wordpress的mainstream?或是用framework統一製作的網站，是否需開放framework即可？另外，NASA（美國太空總署，每年有來自聯邦政府的諸多預算）也有許多開源專案 ( [https://code.nasa.gov](https://code.nasa.gov) )，
> 嗨～ XD
> [name=caasi H]

> 我該我剛想到的問題是，如果只規定「一定要開放」，那若 patch 了 wordpress ，那最省事（但無用的）開放方法是直接放出 patch 過的 wordpress 而不是按本來的開源精神 merge 回 upstream 。
> [name=caasi H]

> 再來如果一個公司用自家的 framework 做了 n 個站，該放出那 n 的站的 source ？還是他們家 framework 的 source ？
> [name=caasi H]

> 還有怎麼確定跑的版本和開源的版本相同？（FSF 和 au 都提過的 freedom 0）
> [name=caasi H]


1.  著作權人？政府的角色？
    a. 政府協助的專案（例如贊助學校發展高科技，產出為政府還是研究單位？）
    b. 國防單位是否需要開源？

1.  開源對政府有什麼好處？
> DIGI⁺ 的論述:
> [name=Audrey T]

> Open Source 部份 [https://www.digi.ey.gov.tw/WaterFall.aspx?n=920FAE6D6C20B1A5&sms=36A0BB334ECB4011](https://www.digi.ey.gov.tw/WaterFall.aspx?n=920FAE6D6C20B1A5&sms=36A0BB334ECB4011)
> [name=Audrey T]

> Open API 部份 [https://www.digi.ey.gov.tw/WaterFall.aspx?n=4345D662AD61BF79&sms=36A0BB334ECB4011](https://www.digi.ey.gov.tw/WaterFall.aspx?n=4345D662AD61BF79&sms=36A0BB334ECB4011)
> [name=Audrey T]


    a. 經濟價值是對政府單位推廣最有利的方法，像當初推廣OpenData時就用opendata有xx元的產值，但open source能否量化？
    ＝＝\> Lisa：政府委託的網站或軟體，其維護也是由同一公司或再外包給其他公司維護，若開源後，除了原有協力廠商之外，可多一個管道：由社群維護，發揮其更大的剩餘價值。
    b. 經2017/18跨年松的討論，很多人覺得政府對於開源態度是拒絕，很大的理由是因為開源會導致駭客攻擊，或是開源會增加官方業務，其中以駭客攻擊為最大考慮點。我方的說法為開源不能避免攻擊，但原有或現有封閉方案也無法避免，開源專案可以讓社群或愛好者可以在第一時間更新，可以減少受攻擊的時間。
    AU: 開源有機會參與制定國際標準，OpenData在台灣主要增加既有服務的價值，有創新，但主要為增加公民參與政策的便利，並銜接國際標準，有機會還能參與制定國際標準。

1.  開源對人民有什麼好處？
    a. 以軟體工程師來說，開源能夠讓大家更容易監督政府網站及軟體的品質，
    b. 對剛接觸電腦科學或想學習程式寫作的初學者來說，政府開源可以變成學生或初學者學習的範本，相較於民間眾多學習工具，政府網站或行動工具的軟體（mobile app）開源絕對是值得學習的方法之一。
    c. 對其他非電腦專長領域的人：除了有多一項學習管道之外，另外可以清楚知道政府對於資訊安全的把握度

1.  主要說服對象：政府：數位政委（唐鳳）？還是各政府及法人機關（工研院、資策會）？

1.  目前方向：A.修法（[政府採購法施行細則](http://lawweb.pcc.gov.tw/LawContent.aspx?id=FL000660) ） ？B.以行政命令要求在採購條約中增列？
> [https://talk.pdis.nat.gov.tw/t/openapi/17/6](https://talk.pdis.nat.gov.tw/t/openapi/17/6)
> [name=Audrey T]

> 有1060713版的資訊服務採購契約範本，參考了 [OAS3](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/3.0.0.md) 和 [SPDX](https://spdx.org/licenses/) 兩個主要的精神。source:
> [name=Audrey T]

> [http://www1.pcc.gov.tw/pccap2/BIZSfront/MenuContent.do?site=002&bid=BIZS_C09804055](http://www1.pcc.gov.tw/pccap2/BIZSfront/MenuContent.do?site=002&bid=BIZS_C09804055)
> [name=Audrey T]

> 推廣機制: [https://issuu.com/pdis.tw/docs/digi___________________v4.8/24](https://issuu.com/pdis.tw/docs/digi___________________v4.8/24)
> [name=Audrey T]

> 討論逐字稿: [https://sayit.pdis.nat.gov.tw/2017-08-09-digi%E6%95%B8%E4%BD%8D%E5%9C%8B%E5%AE%B6%E5%88%86%E7%B5%84%E6%8E%A8%E5%8B%95%E6%9C%83%E8%AD%B0](https://sayit.pdis.nat.gov.tw/2017-08-09-digi%E6%95%B8%E4%BD%8D%E5%9C%8B%E5%AE%B6%E5%88%86%E7%B5%84%E6%8E%A8%E5%8B%95%E6%9C%83%E8%AD%B0)
> [name=Audrey T]


**無紙化政府**，也許可以考慮也 open source 。參考這一篇---_將政府的表格搬到網上_ ([https://wanqu.co/a/6252/2018-02-26-what-i-learned-in-two-years-of-moving-government-forms-online.html](https://wanqu.co/a/6252/2018-02-26-what-i-learned-in-two-years-of-moving-government-forms-online.html))。



    a. 修法：在社群及大眾推廣，凝聚足夠的認同後，再向個立委遊說（[遊說法簡介簡報](https://www.moi.gov.tw/files/download7_file/%E9%81%8A%E8%AA%AA%E6%B3%95%E7%B0%A1%E4%BB%8B-%E7%B0%A1%E5%A0%B19707_1.pdf)）修改法條
        i.   目前現有法規是否有類似法條？
            a. 經口頭詢問：沒有。建議再多方查詢並查明
        ii.  法律是否需要更改？
            a. 我並非法律專業，是否需要修改無法建議。
        iii. 時間。
            a. 凝聚共識需要時間，修法需要更多時間，以目前來說，採購法並非各方關注焦點，
        ix. 適用性。
            a. 初步想法是：排除機密採購及高科技具有國家競爭力的軟體技術，需另外討論其開放範圍，除此之外政府機關所有軟體或網站一律開源。
            b. 由於是法律，故需考慮到目前修改後的版本適用對象，
            c. 若要全部政府機關一律適用，則很可能因為思考不周而碰到各種狀況，最終恐怕會導致失去原本開源理念或開源的好處，進而失去人們對於開源的信任感。


OpenAPI:
民間案例：KKBOX,

