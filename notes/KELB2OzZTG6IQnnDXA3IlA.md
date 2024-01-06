Flutter Taipei interview
===

#### 可以跟我們分享聊聊這個 APP 的理念嗎？
人才發展是企業永續的重要基礎。 有別於亞洲傳統人才管理模式，AMPOS Solutions（易智能股份有限公司）以「Help People Do Better」的理念，提供模組化的人力資源發展解決方案。企業可以根據其人才發展上的重點，從入職、培訓、激勵、績效甚至是企業文化實踐等階段，透過 AMPOS 提供的解決方案能夠進行更深度的人才溝通及發展管理，企業也能透過應用程式進行互動及宣傳文化精神，凝聚內部員工共識以因應外在環境的快速變化與突發挑戰。

員工入職計畫
階段性的入職流程，讓新人快速有條理地熟悉公司與基本的作業、流程等。

結構化的培訓
整合的線上、線下培訓資源，通過權限控管，讓員工方便聚焦在職務能力的提升並打造符合員工需求的學習旅程。

員工激勵
以遊戲化的方式，達成即時、頻繁的多維度正向回饋，營造企業內部正向循環的氛圍。幫助高階管理者更及時掌握組織行為和團隊表現。 
個人化的發展
Coaching、個人發展計畫為潛力員工量身訂製；可根據追蹤個人指標的弱項，提升相對的能力。

組織溝通
便於追蹤的公告讀取、員工回饋、調研、以及以部門為單位的聊天群，雙向的管道提升組織溝通成效。

實時績效追蹤
即時、量化的指標追蹤，部屬日常表現不漏接；搭配個人化的發展/結構化的培訓，讓評鑒與考核不再只有開始與結束。

企業接班人計劃
通過長期追蹤員工的各項表現進行分類與搜尋，成為企業補齊職位空缺的有效工具。

![alt text](https://i.imgur.com/Cob2qfE.png)


#### 為什麼決定採用 Flutter 技術來開發呢？大約花多久的時間評估決定使用的技術？
AMPOS app 早期是分別在iOS和Android平台上開發的。當我們新增功能時， 我們需要熟悉iOS和Android工程師同時開發， 即耗時又耗力。為了提高產品新功能開發速度，產品團隊決定評估PWA,React Native和Flutter跨平台技術。經過兩個月評估和測試，我們最總決定使用Flutter,因為PWA在現階段不能完全滿足產品需求，而Flutter相比較React Native更適合我們的團隊，無論是從技術轉換難度還是後續開發資源支持都符合我們需求。 


#### 可以跟我們分享團隊 1年半大家一起研究 Flutter 的過程和方式嗎 :) ?
日常Code Review我們會彼此分享一些語法/技巧/風格/模式/函式庫...等等。由於我們的開發團隊分散在台北和曼谷， 我們也經常在Slack上討論一些問題的解法，最佳實作，導入新工具之類的。另外每週例會除了更新彼此的進度，也會討論一些比較工程/架構/流程或框架本身的問題。


#### 有多少人一起投入開發？大家是什麼樣的背景？
前後大約12人左右，熟悉Android的較多。除了個別工程師在加入團隊之前就接觸過Flutter，其它所有人都是決定採用Flutter之後才現學現賣的。因為做Add-to-App的關係，所有人都要試著一起開發Android/iOS/Flutter，偶爾也有人臨時被抓去做Web/Backend，總之大家學習/適應能力都蠻強的。


#### 團隊花了多少時間時間開發？
Flutter部分從早期POC到現在幾乎完成整個原生到Flutter的轉移大概一年半左右，原生的部分之前做了三年。



#### 團隊的 Flutter App使用的後端是第三方服務還是自架後端？並還有用到哪些第三方服務（不方便的話可以不用回答）
我們主要是以Spring Boot(in Kotlin)為框架，搭配Python/Node.js的micro service，架在我們後端大神鬼斧神工般的AWS Infra上，整合諸多服務如ECS, EC2, S3, RDS, DynamoDB, Lambda, Athena, Route 53, API gateway, CloudWatch, CodeBuild, CloudFormation...各種你想得到想不到的服務應有盡有，另外我們也有在考慮提供AWS顧問的服務，有興趣的話也歡迎洽詢。
另外APP端還有用到[MatterMost](https://mattermost.com/)(aka open source Slack)做In-app Messaging。VCS/CI/CD用到Bitbucket, Fastlane, Jenkins。當然也有大家熟悉的Firebase Analytics, Crashlytics, App Distribution, FCM(中國用百度雲推送)等等。



#### 團隊之前有使用非 Flutter 的技術開發 App 的經驗嗎？使用 Flutter 後，在團隊協作或產出方面，有沒有特別想分享的經驗呢？
如前所述，我們有一組開發三年的原生App，透過Add-to-App，花費一年半左右一頁一頁逐步轉換成Flutter。
在我們過去的兩套原生code base中，偶而會看到明明應該是相同的商業邏輯，但因為開發者各自的理解或習慣不同，在Android/iOS上出現很不一樣的實作方式，進而造成在和Backend/QA/PM討論時的一些困難或誤解（例如為什麼同一個需求iOS改很快，Android卻可能要動到整個架構之類的）。這類的問題在Flutter上自然是不會發生，也就是說單一code base不只降低了mobile團隊的開發成本，同時也降低了對外的溝通成本。



#### 在決定使用 Flutter 技術時有什麼擔憂嗎？
擔憂一定是有的， 畢竟Flutter是一個新的技術。雖然看到網路上有些針對Flutter的討論和開發案例，但我們自己團隊畢竟沒有Flutter開發經驗，我們可以想像開發過程中一定會遇到的各種問題。針對於這些問題我們能否找到資源來協助我們解決問題是我們當時最大的擔憂。 



#### 如何評估適合的架構模式，並取得共識並決定採用呢？
以架構來說，因為大部份的團隊成員都蠻熟悉Clean Architecture，而且Clean本來就是以平台/框架無關為核心精神之一，因此就直接沿用了。Presentation layer則是早期大家各自嘗試，scoped_model, redux, BLOC, MVVM都有人試過，大家Code Review互相參考一陣子之後慢慢還是收斂到MVVM。簡單來說scope_model太簡單，redux太複雜，BLOC和MVVM太像感覺也沒什麼好糾結的，最後似乎還是熟悉的MVVM最對味。但也沒有硬性規定，如果你覺得在這個場景更適合用其他模式，甚至值得犧牲一點一致性，只要你能說服足夠多的Reviewer也是會得到approval。



#### 承上題，團隊在 Flutter App 使用的架構模式，以你們的實際經驗來說，有什麼樣的優缺點嗎？
Clean的一大重點在DI，但我們剛開始做Flutter架構的時候，並沒有像Dagger那麼強大的DI Framework，因此我們先用了簡單的simple_flutter_dependency_injection。如名稱所述，它幫你做的事情真的不多，但我們又想要有像Dagger那樣切割乾淨的DI component/module，導致我們寫一個新的service, interactor都需要經過相當繁瑣的boilerplate。
但大費周章的DI對我們在做單元測試mocking和後續的重構上的確是有很大的幫助，因為我們的目標是從Add-to-app轉移到純Flutter，寫一個service的時候就必須考量這點做一個抽象層，再透過DI將不同版本的實作提供給其他模組。
例如一開始我們的authentication寫在原生端，要從Flutter頁面登入/登出就必須透過platform channel去呼叫原生函式。我們會做一個AuthenticationService的介面，注入到Interactor給Flutter頁面使用，接著就會有AuthenticationServiceImpl的實作(by platform channel)，透過DI提供出來。未來當我們要把這部份轉成Flutter，只要改寫Impl就好。


#### 用Flutter開發的時候，什麼樣的事情讓你們覺得最有挑戰性/最困難？
因為早期Add-to-App還在alpha channel，比較容易撞到一些框架本身的bug，這時候Flutter團隊並不會去做hotfix，就必須自己找work around。但做Add-to-App的人又沒有純Flutter App那麼多，偶爾遇到Github issue和Stack overflow都無解的問題，最後可能就必須自己看source code。
另外同樣是Add-to-App，因為頁面會有原生/Flutter交錯的情況，需要去管理不同頁面使用的Flutter Engine，同時為了解決Engine初始化效能的問題，也需要先做Pre-warm。這部份相關的文件很少，API又常常改變，也讓我們費了不少功夫。
總之我們最後是有一個Engine Factory，準備一個Pre-warm Engine Queue，每次有新Flutter頁面就取一個engine，同時warm up一個新的。


#### 你們的 Flutter App之中 有什麼特別想介紹的技術嗎？（例如用到藍芽、IOT、動畫、直播、AdobeXD、Rive, Machine Learning, translation等等...）
老實說我們App本身做的事情相對單純，就是各個頁面呼叫後端API做CRUD，因此也可以說特別適合Flutter。
有一個我個人正在評估的測試工具蠻值得一提的：[Repeato](https://www.repeato.app/)。雖然標語是Android UI測試，但它指的是在Android裝置上，而不只是原生Android App。因為它是直接對鏡射到桌面上的手機畫面做電腦視覺處理，以此來錄製測試用例和操作App，理論上不論是原生, Flutter, hybrid, embedded webview, React Native, 甚至PWA都有可能透過這樣的技術來做UI測試，而且完全不須要寫測試code，任何QA甚至PM都能輕鬆上手。
我目前是只有拿我們的hybrid Flutter來測試，效果還挺不錯的，作者也很快地在後續版本採納了我的幾個小建議，所以我蠻看好它的後續發展的。
另一方面官方的[Flutter Driver](https://api.flutter.dev/flutter/flutter_driver/flutter_driver-library.html)是沒辦法做Hybrid App Testing的，你可以想像若是用Espresso, Flutter Driver這類直接操作UI元素的測試工具，要整合測試Flutter/Native頁面交錯的流程有多困難。
另外[appium-flutter-driver](https://github.com/truongsinh/appium-flutter-driver)的發展也很值得追蹤，同樣支援各種形式的Hybrid App，如WebView-in-Flutter、Flutter-in-Native、Native-in-Flutter，雖然現在還在極為初期的階段，未來若是成熟，就可以佈署Hybrid App到各大支援Appium的Device Farm如[AWS Device Farm](http://awsdevicefarm.info/)等。
說到AWS Device Farm讓我再講一個[Sylph](https://github.com/mmcc007/sylph/)，這是一個cli tool讓你可以把Flutter Driver當作是Appium送到ADF上跑，所以純Flutter App應該用這個就可以了。可惜它實際跑的還是Flutter Driver，所以我們的Hybrid App還是沒辦法用。


#### 你們的 APP 的使用對象看起來有分佈在不同的國家：中國、曼谷和台灣，可以跟我們分享 App 中 internationalize或是 Localization 的處理部分嗎 :) ?
目前的流程是有一個Google Spreadsheet存放所有字串，欄位類似key/en/zh-TW/zh-CN/thai這樣。每次有新字串加入會先放上key和en，通知翻譯人員補上其他翻譯。然後有一個Google App Script把sheet裡面的字串分別轉換成Android/iOS/Flutter適用的資源結構和格式（Flutter這邊是每個語言x每個模組有一個json檔），儲存到個人的雲端硬碟，再手動下載並整包丟進各專案裡面來更新字串。
這段其實蠻麻煩的，因為要spreadsheet, drive, Android/iOS/Flutter到處跑。理論上可以先打spreadsheet API資料全部抓回來，本地處理完直接存到對應的專案就好，可惜我一直沒有時間做。
Flutter端讀取這些資源的方式就蠻土砲的，簡單來說就是App初始化/切語系時根據locale讀json檔(key-value pair)進來，存在一個`AppLocalization` class裡，用DI把這個class注入到ViewModel裡，在ViewModel裡根據key取得localized string，提供給View使用。我們沒有用任何第三方套件，連Flutter Framework的`LocalizationsDelegate`和`Localizations`都沒用到，畢竟我們沒有根據不同`BuildContext`使用不同Localization的需求，自然也就不須要到處使用`Localizations.of()`，給程式多添加不必要的框架相依性。


#### 你們有使用任何CI/CD工具嗎？有的話是否可以跟我們分享使用的工具，以及為什麼選擇該工具
之前是Jenkins, Fabric Beta, Fastlane，但這些在我加入團隊之前的原生時代就全部建好了，所以我也沒辦法提供太多資訊。至於現在Beta已經轉移到Firebase App Distribution，Jenkins也正在轉移到AWS CodeBuild，主要是希望Backend, Web, Mobile用同一套CI/CD工具。


#### 如果可以重新選擇開發技術，你們還是會選擇用Flutter來開發嗎？
絕對會。現在偶爾還是要回原生Android/iOS專案寫些東西，寫到Android UI就覺得天啊我們以前真的要搞這麼多Activity, Fragment, View, XML嗎？到iOS專案修bug就想說天啊每次一編譯就是5~10分鐘，難道iOS開發者都是得道高僧嗎？Flutter的Widget Composition和Hot Reload真的是體驗過就回不去了，即使只開發單平台也很有價值，更不用說現在就能很好的跨雙平台，Web/Desktop也正如火如荼的開發中。雖然早期因為框架成熟度和Add-to-App的關係多付出了一些時間成本，但長遠來看Flutter還是非常好的一項投資。


#### 你們會推薦什麼樣的APP使用Flutter？如果團隊決定使用Flutter來開發，你們有什麼樣的建議想給大家嗎？
針對這個問題，我們換個方式回答可能比較清楚。 我們總結了一些Flutter還不適合的情況：
* 大量用到原生API、套件或硬體的應用(Map/Camera/Bluetooth/AR/VR...)
* 非主流裝置(Watch/TV...)
* 遊戲(也不是不能做但顯然有比Flutter更好的選擇)
* 設計師希望所有UI元件都分別使用原生設計(Cupertino還有一段路要走)

除了上述情況，Flutter發展到這個階段，我們認為80%的APP都會適合用Flutter開發，只要確認過核心功能在Flutter上支援足夠，就算可能有其它細項無法直接透過Flutter實現，還是可以回去寫原生來串接，多寫5% platform code總比100%都分別寫來得好。因此另一個考量的點可以放在你有什麼樣的團隊，或你個人有什麼樣的技能。例如你們本來就有Web產品/團隊，想跨足Mobile，那麼根據產品需求，走PWA可能也是一個強力的選擇（主要就是看有沒有遇到iOS上的限制）。如果是像我們一樣從原生Android/iOS轉跨平台，選擇Flutter就會比PWA理想的多。
如果最終選擇了Flutter，我們會建議在興奮地開始玩新玩具的同時，也多點耐心把防護措施做好。模組化、IOC、Unit Test、SOLID、DDD、TDD，甚至是最基本的clean code，這些不管走到哪個平台/框架，該做的事情還是要做。畢竟軟體開發最大的挑戰之一就是因應變化，這點在Flutter這個既年輕又極為活躍的生態系中更加顯著，API會變，典範/模式會變，套件/服務會變，當然產品本身的需求更會變。良好的軟體工程，架構和程式碼品質能幫助你快速且安全地因應這些變化，這樣你才能放心大膽地去嘗試Flutter各種新玩法，同時不會爆一堆Bug把你們家PM氣死。
當然以上是針對有實際產品要發佈的開發團隊，如果是個人開發者就別想那麼多了先上車再說吧。


#### 額外補充（有什麼沒提到的歡迎在此提補充）

#### 團隊現在或未來打算招募 Flutter工程師嗎？(如果有想要工商歡迎，找Flutter工程師、找開源合作夥伴，可以回答這題)