# Day 23 - 準備好要上線了嗎？(一)

歐齁齁，終於來到這一步了，~~金流寫了半天終究是要上線才能賺錢啊~~

但！上線前還是得先來個好名字！

## 域名

蝦米名字呢！就是域名啦！ 畢竟之前串金流的時候都還是用 `Ngrok` 處理，但上線可不能繼續這樣用

所以我這裡先採用 `Godaddy` 的服務，買起來買起來！

基本的就是挑個喜歡的名字掏出魔法卡啦，剛好正打算架自己的部落格就順便一起處理

流程上也沒有什麼太難的地方，剛好他有提供架站神器，就拿來試一下一鍵生成網頁跟 DNS 設定，來確認是不是真的買下來（可以連接看到畫面）了

只是買完等設定生效要好一陣子（氣

生效之後，還得把應用推上去啊，同時搞 DNS 跟部署，兩邊的問題混在一起，當初在學的時候可是搞得天崩地裂 XD

所以今天還是按部就班，將問題分離開來確認比較輕鬆（茶

## 輕鬆部署

沒錯，懶人部署，感謝 Heroku 但今天不是要用他 XD

Heroku 很好用，隨手估狗也能找到很多介紹與實作解說

但是... 他要收錢了啊～

公告原因大概是免費的期間被拿來做很多壞事，像是詐騙網站之類的，所以就收回了

基於一篇~~沒有人看的~~鐵人賽就不打算在這邊去支出多餘的費用

那就得找到替代方案！

就是 [Render](https://render.com/) !!

操作也非常容易，實際部署一個專案大概只需要滑鼠點點就行了，想當然，比當初的免費 Heroku 功能上還是差了好幾截

但今天的用途只是做一版最簡單的部署來幫助確認 域名 以及 App 到底有沒有正常運作，所以也是綽綽有餘了

### 三步部署
#### Create web service
![https://ithelp.ithome.com.tw/upload/images/20231008/20142040nApggC2SHK.png](https://ithelp.ithome.com.tw/upload/images/20231008/20142040nApggC2SHK.png)

#### Connect GitHub / GitLab and Selet Repo
![https://ithelp.ithome.com.tw/upload/images/20231008/20142040tmji6tDua9.png](https://ithelp.ithome.com.tw/upload/images/20231008/20142040tmji6tDua9.png)

#### Custom setting and Deploy

![https://ithelp.ithome.com.tw/upload/images/20231008/20142040Jr3p5ogccn.png](https://ithelp.ithome.com.tw/upload/images/20231008/20142040Jr3p5ogccn.png)

記得選免費 XD
![https://ithelp.ithome.com.tw/upload/images/20231008/20142040jfPUpaf2Dm.png](https://ithelp.ithome.com.tw/upload/images/20231008/20142040jfPUpaf2Dm.png)

接下來就是等待部署完成了

完成後會會在介面上看到幫你設定好的 URL，先點進去確認網站各功能都有正常運作，看起來是沒捨問題啦 （吧

## Domain 置換！
既然買了域名，當然是要來用一下的

這時候切到面板的設定，諸多設定中找到一項 `Custom Domains`

很貼心的還提醒你怎麼設定 DNS，設定完之後也還是ㄧ樣貼心的會告訴你設定有沒有生效

先按照操作，回頭到 `Godaddy` 在 DNS Management 將 A Record `ironman2023` 直接設定 `Render` 告訴你的 IP

下一步則是 C Name，將 `www.ironman2023` 設定到 `Render` 幫你部署完成的 domain 上

因為我買的主 domain 是 `dantecheng.me`

所以這樣設定完成之後會獲得兩組可以導到剛剛部署的網站的 domain

`ironman2023.dantecheng.me`
`www.ironman2023.dantecheng.me`

當然，生效也需要一點點時間，可以隨時確認 `Render` 的介面，通過驗證的話會有圖示告訴你

![https://ithelp.ithome.com.tw/upload/images/20231008/20142040AQs9mCDtuV.png](https://ithelp.ithome.com.tw/upload/images/20231008/20142040AQs9mCDtuV.png)

再來輸入剛剛生效的 domain ，就可以看到網站內容啦！（跟 Heroku 一樣太久沒用要等待被喚醒）

測試帳號：'ironman2023@gmail.com'
測試密碼：'123123'
(玩壞很正常 XD

可喜可賀 猜猜明天要幹嘛ㄋ ：Ｄ