---
title: "有地點的通報功能專案：路平、違章工廠、拍照上傳"
tags: GIS
---

# 有地點的通報功能專案：<br>路平、違章工廠、拍照上傳

[KIANG](https://g0v.hackpad.com/ep/profile/G4yGGowBe3x)
> 就熊熊想要找資料發現都找不到，所以怒開一個 hackpad 做雜記
> [name=kiang]

## 專案類型歸納

- 已知地點與題目，邀請民眾協助拍照上傳，例如：
    - 先給公園位置邀請民眾拍照上傳公園遊具的照片
    - 已知 5 萬間違章工廠，邀請民眾拍照上傳
    - 路殺社提供認養樣區，針對樣區邀請參與者投入樣區調查
- 從零開始通報，民眾可以通報新的資料地點：
    - 揪地霸
    - 督視人
    - 路殺社
- 通報資料內容：
    - 經緯度取得方式：
        - 從行動裝置取得經緯度
        - 先給定需要通報的目標
    - 資料內容
        - 文字
        - 拍照
- 技術層面：
    - ？

## 台灣案例

- g0v 路見不平專案
    - github repo: [https://github.com/g0v/roadpin](https://github.com/g0v/roadpin)
    - demo site: [http://106.187.101.193](http://106.187.101.193)
    - forum: [https://groups.google.com/forum/#!forum/roadpin](https://groups.google.com/forum/#!forum/roadpin)
- 平安走路許願帳戶-行人庇護空間
    - https://commutag.agawork.tw/dataset?id=63528cc34f042e88cc951433
- Line
    - [LINE BOT 市容幫手 & 相關案例](https://g0v.hackmd.io/PzbDfow8QZ-FWLQeefMbaQ)
- 揪地霸
    - https://g0v.hackmd.io/L_v7mAAyT8GT-c_ukR9IYQ?view
- 台南也要特色公園
    - https://parks.olc.tw/
    - https://www.facebook.com/groups/playgrounds.tainan
- 農地違章工廠
    - https://disfactory.tw/
    - https://g0v.hackmd.io/@yukaii/Disfactory/
- 蒐集道路標線已改造、待改造路段地點的地圖
    - https://g0v.hackmd.io/X8mWlCWIRkOfCIhTjp1oLA
- 高雄市潛力植樹地點盤點
    - https://www.facebook.com/groups/573697330058183/permalink/951609918933587/
- 公民科學的專案，其中採用地點通報的專案
    - https://www.facebook.com/groups/437659989769965
- 路殺社模式
    - [https://roadkill.tw/](https://roadkill.tw/)
    - 「路殺社」鼓勵民眾回報道路上死亡的動物
- [Open Geo Data for Government - Cases of OSM and Gov collaboration mode](http://hackfoldr.org/OpenGeoData/FH8Jcnpt052) \- 政府與OSM的合作應該可以為二種模式，一是政府匯入OSM，經由Mappers修改、更新後，再被政府取回，另一種是OSM資料被政府資料庫吸收後，再釋出於社群，後者所收集到的案例，資訊都不是相當明確。
- 小編模式
    - 交通事件 [https://www.facebook.com/safe.traffic/](https://www.facebook.com/safe.traffic/)
    - 淹水 [https://www.facebook.com/crazyck101/posts/1306884369431587](https://www.facebook.com/crazyck101/posts/1306884369431587)
- 歷史影像平台
    - https://photo.swcb.gov.tw/
    - 台灣水土保持局鼓勵民眾上傳無版權爭議之歷年災害照片及重要地景，並且協助將照片定位，釐清拍攝角度
- 督視人
    - [http://spectatordo.herokuapp.com/](http://spectatordo.herokuapp.com/)
    - 讓居民回報公共空間中較不具急迫性的議題，例如人行道設計不良。
- 紅不讓
    - [https://www.facebook.com/redred.tw/about](https://www.facebook.com/redred.tw/about)
    - 套疊都市紅黃線地圖與路霸通報
- 共享路平
    - [https://g0v.hackpad.tw/Iz4ydeSxlGH](https://g0v.hackpad.tw/Iz4ydeSxlGH)
- 「市民探針」app
    - Android [https://goo.gl/YzE1A2](https://goo.gl/YzE1A2)
    - ios [https://goo.gl/Q08ez6](https://goo.gl/Q08ez6)
    - 積水通報，介紹文章 [http://communitytaiwan.moc.gov.tw/Item/Detail/%E9%97%9C%E6%96%BC%E9%98%B2%E7%81%BD%EF%BC%8C%E7%A4%BE%E5%8D%80%E7%87%9F%E9%80%A0%E5%8F%AF%E4%BB%A5%E5%81%9A%E4%BB%80%E9%BA%BC%EF%BC%9F](http://communitytaiwan.moc.gov.tw/Item/Detail/%E9%97%9C%E6%96%BC%E9%98%B2%E7%81%BD%EF%BC%8C%E7%A4%BE%E5%8D%80%E7%87%9F%E9%80%A0%E5%8F%AF%E4%BB%A5%E5%81%9A%E4%BB%80%E9%BA%BC%EF%BC%9F)
- City Probe 都市探針
    - [https://apkpure.com/city-probe-%E9%83%BD%E5%B8%82%E6%8E%A2%E9%87%9D/tw.edu.fcu.cityprobe](https://apkpure.com/city-probe-%E9%83%BD%E5%B8%82%E6%8E%A2%E9%87%9D/tw.edu.fcu.cityprobe)
    - [https://www.grb.gov.tw/search/planDetail?id=11588969&docId=0](https://www.grb.gov.tw/search/planDetail?id=11588969&docId=0)
- [全民監督公共工程資訊系統](https://cmdweb.pcc.gov.tw/pccms/pwreport/ducon2_geoeng.pasin)
- 地圖協作平台
    - [http://tgos.nat.gov.tw/MapSites/Web/MS_Home.aspx](http://tgos.nat.gov.tw/MapSites/Web/MS_Home.aspx)
- 台北市資訊局
    - [https://hackpad.com/Input-Beta-G2rD0vAMzx3](https://hackpad.com/Input-Beta-G2rD0vAMzx3)
- fixmystreet
    - 中文版： [https://github.com/misgod/fixmystreet](https://github.com/misgod/fixmystreet)
    - 開發者記錄：[http://35around.blogspot.tw/2014/06/311.html](http://35around.blogspot.tw/2014/06/311.html)


## 國際案例

- iNaturalist：https://www.inaturalist.org/observations
    - 全球公民科學家進行生物調查拍照上傳的成果地圖
    - 可以設置一個生物觀察的樣區，例如「臺北市內湖區舊宗路匝道綠地生態觀察」：https://www.inaturalist.org/projects/aeae4fa7-0c32-4238-806a-52db3bebae24
- Bristol Bugbears
    - [https://bristolbugbears.commonplace.is/](https://bristolbugbears.commonplace.is/)
    - Bristol City Council has been awarded funding to make small improvements to cycling and walking facilities around the city.
- Cyclescape crowdsources desired changes to street infrastructure. Although this particular system focusses on transport, the use-case is generic: a means for citizens to crowdsource proposals containing both geodata and metadata.
    - https://www.cyclescape.org/
- Pothole Tracker
    - [https://www.cityofchicago.org/city/en/depts/cdot/dataset/potholetracker.html](https://www.cityofchicago.org/city/en/depts/cdot/dataset/potholetracker.html)
    - When crews respond to a 311 pothole request, they fill all additional potholes on that block. Click a dot on the map to see potholes filled by address, the date the service request was completed, and the total number of potholes filled on a particular block. Duplicate requests have been removed.
- MapIt
    - [http://mapit.mysociety.org/](http://mapit.mysociety.org/)
    - MapIt was written back in 2003 as a postcode lookup to power the original [mySociety](http://www.mysociety.org/) sites such as[WriteToThem](http://www.writetothem.com/). Over time it gained features such as point lookup (for [FixMyStreet](http://www.fixmystreet.com/)), and when Ordnance Survey data became freely available in 2010, it was rewritten and made public for the whole UK. Versions have appeared in other countries, such as [Norway](http://mapit.nuug.no/), and in 2012 we released a [global version](http://global.mapit.mysociety.org/) based on OpenStreetMap data.
- City Savior
    - [https://www.facebook.com/groups/opengovgroup/permalink/2001119393452980/](https://www.facebook.com/groups/opengovgroup/permalink/2001119393452980/)
- Open311
    - [http://www.open311.org/](http://www.open311.org/)
    - A collaborative model and open standard for civic issue tracking
- ichangemycity
    - [http://www.ichangemycity.com/](http://www.ichangemycity.com/)
    - comment and complains, backend links to civil agency.
- uReport
    - [https://github.com/City-of-Bloomington/uReport](https://github.com/City-of-Bloomington/uReport)
    - Issue tracking and constituent relations management for municipalities with an Open311 (GeoReport v2) endpoint
- Citizens Connect: Making Boston Beautiful.
    - [http://www.cityofboston.gov/doit/apps/citizensconnect.asp](http://www.cityofboston.gov/doit/apps/citizensconnect.asp)
    - Citizens Connect is the City of Boston's award-winning effort to empower residents to be the City's "eyes and ears." Now you can alert the City of Boston to neighborhood issues such as potholes, damaged signs, and graffiti.
- Adopt-a-Hydrant (認養消防栓)
    - [http://www.adoptahydrant.org/](http://www.adoptahydrant.org/)
- Boston StreetBump
    - [http://www.streetbump.org/](http://www.streetbump.org/)
- iCitizen: Mapping Service Delivery in a South African Municipality
    - [https://crowdgov.wordpress.com/case-studies/icitizen-mapping-service-delivery-in-a-south-african-municipality/](https://crowdgov.wordpress.com/case-studies/icitizen-mapping-service-delivery-in-a-south-african-municipality/)
- 邁阿密
    - https://www.miamigov.com/Services/Solve-a-Problem/Report-Flooding
- StreetCred
    - 波士頓市政府與 Engagement Game Lab 合作，推出了StreetCred（街頭威望）的API [https://www.bnext.com.tw/article/32563/bn-article-32563](https://www.bnext.com.tw/article/32563/bn-article-32563)
- Shareabouts - Shareabouts is a simple web app for crowdsourced mapping.
    - [http://demo.shareabouts.org](http://demo.shareabouts.org)
    - 應用案例：[http://blog.openplans.org/category/shareabouts/](http://blog.openplans.org/category/shareabouts/)
- 「TrailWatch 徑．香港」手機應用程式
    - [https://www.facebook.com/trailwatch/posts/1376132082426369](https://www.facebook.com/trailwatch/posts/1376132082426369)
- 馬來西亞 MyCleanCity
    - [http://www.mycleancity.my/](http://www.mycleancity.my/)
- 馬來西亞 BetterPanang
    - [http://www.betterpg.com/](http://www.betterpg.com/)
    - [http://cat.betterpg.com/v2/](http://cat.betterpg.com/v2/)
- 馬來西亞 AduanKu(Report, view, or discuss local problems)
    - [https://aduanku.my/](https://aduanku.my/)
    - [https://www.facebook.com/sinarproject/posts/673529212813278:0](https://www.facebook.com/sinarproject/posts/673529212813278:0)
- 馬來西亞 Issue Tracker
    - [https://sinarproject.hackpad.com/Issue-Tracker-Concept-Draft-ZoBEiHHAWhM](https://sinarproject.hackpad.com/Issue-Tracker-Concept-Draft-ZoBEiHHAWhM)
- MINING CITIZEN FEEDBACK DATA FOR ENHANCED LOCAL GOVERNMENT DECISION-MAKING
    - [http://www.unglobalpulse.org/projects/citizen-feedback-data-local-government-decision-making](http://www.unglobalpulse.org/projects/citizen-feedback-data-local-government-decision-making)
- Maptionnaire
    - [http://maptionnaire.com/?lang=en](http://maptionnaire.com/?lang=en)
- 衛報的群眾貢獻影像平台
    - 主題舉例「不再被喜愛的都市河流 Unloved city rivers: share your stories and photos」：[https://witness.theguardian.com/assignment/56261b84e4b00378ab588bbf](https://witness.theguardian.com/assignment/56261b84e4b00378ab588bbf)
- [瑞典的于默奧市(Umeå)想要打造維基百科城，舉辦競公開編寫條目競賽，號招全球一起幫他們寫當地文史條目，（有些條目甚至連英文版的都沒有，真是超local的）未來會在各地標上放QRcode，方便民眾查閱。](https://meta.wikimedia.org/wiki/Umepedia_challenge/zh-hant)
- 蒐集相關案例的文章: [http://googlemapsmania.blogspot.tw/2016/05/map-reporting-in-local-government.html](http://googlemapsmania.blogspot.tw/2016/05/map-reporting-in-local-government.html)
- [https://crowdgov.wordpress.com/case-studies/](https://crowdgov.wordpress.com/case-studies/) \- about governmental projects that incorporate crowdsourced data.
- [https://www.facebook.com/googhostmap/posts/147326995674563](https://www.facebook.com/googhostmap/posts/147326995674563)
- 海嘯通報器材檢查
    - [http://sirens.honolulu.gov/](http://sirens.honolulu.gov/)

