https://g0v-tw.slack.com/archives/C022F62TF5X/p1621338529006700

archived at 2021/5/19 6:35am

au:sdgs: Yesterday at 19:48
「1922 簡訊實聯制」系統已經初步完成開發，明天 11:00 會發表，感謝大家這幾天協助討論～
https://www.youtube.com/watch?v=zIvaCCjuboo (edited) 
YouTubeYouTube | udn video
0519行政院簡訊實聯制記者會 

:heart:
26
:pray:
7
:+1:
5
:bulb:
4
:iphone:
5
:selfie:
4
:muscle:
3
:ey:
3
:congratulation:
4

42 replies
acechen  9 hours ago
那…我把 HackMD 的 簡訊實聯 改標題好了，以免混淆
希望有些 feature 可以進行政院版的簡訊實聯，尤其是 [MerchantID] 討論那邊，畢竟是一些現實應用可能會遇到的情況
g0v.hackmd.iog0v.hackmd.io
簡訊實聯 - HackMD (725 B)
https://g0v.hackmd.io/pdlHsfCKTpuf0KL4Cr5W6A

kiang  9 hours ago
https://news.ltn.com.tw/news/politics/breakingnews/3537500
自由時報電子報自由時報電子報
唐鳳再次出手！全國通用的「實聯制」來了 政院明公布 - 政治 - 自由時報電子報
因應武漢肺炎（新型冠狀病毒病，COVID-19）防疫加嚴，各超市、賣場與店家紛紛啟動實聯制卻未經整合，導致民眾一天之內出入各店家或商場買餐飲與民生必需品頻繁填各家實聯制，相當不便。行政院數位政務委員唐鳳出手，結合民間業者完成全國可通用的實聯制新系統「簡訊實聯制」的開發，明天將正式公布，民眾只要透過掃QR Code系統、按下相關指示，幾秒鐘就可完成登錄，不必填寫個人姓名與手機號碼，可省下不少時間。目前有的店家僅提供以原子筆手寫個人資訊，有些店家則是只提供QR code掃碼，讓不擅使用手機與中文輸入的老年人叫苦連天，有的店家則是手寫與掃碼二者都有，不過，也有人擔心店家各自使用的實聯制，恐導致個資外洩問題。
Yesterday at 20:32
pichuchen  9 hours ago
目前政院版應該是完全沒有釋出任何資訊這樣？
所以理論上目前民眾想像應該會是類似一個 APP 要下載然後掃 QRCode 之類的東西？
au:sdgs:  9 hours ago
對。這個會在記者會剛開始就說，沒有 App 要下載，用手機內建的掃碼、內建簡訊程式（手動傳）都可以。LINE 掃碼器目前不支援 SMSTO:，但是可以用疾管家掃。
:open_mouth:
3

Kai:house_with_garden:  9 hours ago
是說這個政院版的簡訊實聯系統未來是否能整合現有的「台灣社交距離app」
au:sdgs:  9 hours ago
政院版的很多 feature，例如店碼中間加空白，以及 MerchantID 各種例外情況處理，完全參採 @acechen 等夥伴的貢獻，非常感謝。 (edited) 
au:sdgs:  8 hours ago
@Kai 未來 AI Labs ENS 開源後歡迎發掃碼 pullreq 來討論 XD 這次因為 i18n 已經用掉了 ENS 的 app store review cycle 所以沒有做整合。 (edited) 
:heart:
7
:beating-heat:
4

pichuchen  8 hours ago
掃碼器的部分，iPhone的相機和Google Pixel 的相機是可以支援smsto的
:iphone:
2

pichuchen  8 hours ago
另外我想知道的是政院版會是自願使用，還是他會以強制使用的方式？像是公家機關的部分他們會是自己決定，還是公家機關也都是強制使用？
au:sdgs:  8 hours ago
「簡訊實聯制」系統是實聯制其中一種方式，與紙筆登記及各店家自行製作表單並不衝突。政府不會強制民間使用這個系統。
公家機關一般來說，即使用這個做掃碼，還是會同時提供紙本實聯表單。 (edited) 
acechen  8 hours ago
接下來要克服的是怎樣讓店家/場館覺得容易申請和查驗，以及民眾理解它背後的隱私保護，以免又落入「政府監控人民」的流言循環
當然，與現行的其他實聯制不衝突，大家可以自由選擇，不營利（包含投放廣吿）的話也沒有競爭關係
au:sdgs:  8 hours ago
店家採自助申請，類似今年綜所稅的多元登入，可採手機驗證等任一種登入方式，不會比 eMask 困難。
隱私部份可能就要請社群協助，把「各電信業者依法不得將簡訊紀錄做目的外利用，也不會收到場所代碼和店家的對照表，不會知道場所代碼分別代表哪些店家，提供疫調人員的僅有場所代碼和時間區塊。這些內容均遵循實聯制指引，於 28 天後刪除紀錄。」轉譯成比較容易看懂的說明...
和其他實聯制不衝突，可以並行，絕無廣告投放。現有掃碼器可以多支援一種 SMSTO，現有表單可以最後多一動到 SMSTO。 (edited) 
acechen  8 hours ago
不知道明天記者會有沒有時間對其他實聯制作宣導（可能會離題就是了，但記者應該會問？）
我比較在意的是個資管理：明確的權限（誰看得到）和刪除（包含備份）規範，以及提醒永遠要有紙本可以 fallback ，尤其最近很常停電⋯ (edited) 
pichuchen  8 hours ago
我在協助導入的現場比較多還是店家會問能不能看到（確認）實際上有輸入的這件事，但是如果今天說是政府會協助搜集的話，那這樣店家其實可以省去確認是否系統正確運作的麻煩
au:sdgs:  8 hours ago
*fallback 到紙本確實很重要，我會記得說。不過，停電通常不影響傳送簡訊，除非照明失效，但那樣紙筆也不容易填。
pichuchen  8 hours ago
不過申請方式聽起來就很麻煩，因為攤販不一定有報稅XDDDDD
au:sdgs:  8 hours ago
攤販只要有收得到簡訊的手機，號碼登記在自己名下就可以了。 (edited) 
pichuchen  8 hours ago
喔喔，所以申請方式也是用簡訊申請嗎？
au:sdgs:  8 hours ago
目前是網頁，不過會用到 TWID 的技術。
pichuchen  8 hours ago
那這樣一個手機可以申請多個店家編號嗎？ 像是分店這樣
au:sdgs:  8 hours ago
可以多個。而且後綴可以自己產製。意思是如果 0123456 是合法的 [MerchantID] 則 0123456001 也是。 (edited) 
pichuchen  8 hours ago
了解，所以 MerchantID 就像是給一個prefix 這樣？
au:sdgs:  8 hours ago
是的，最前面一碼是 QR authority。目前有兩個，分別受理民間和公部門申請。 (edited) 
acechen  8 hours ago
我覺得簡訊實聯店家看不到個資的 tradeoff 是，沒辦法真的知道眼前的這個人是不是已經進資料庫，包含可能的技術問題(exception)和偽造簡訊等，不然就要開發匿名的即時 stat (edited) 
au:sdgs:  8 hours ago
是，目前只能肉眼確認在顧客手機上的店碼有送出到 1922。每次確認花的時間還是比紙本少一點。
顧客如果有動機偽造簡訊，也就有動機在紙本留假資料（後者成本較低）。
Default exception handling 或許就是 fallback 到紙本。 (edited) 
pichuchen  8 hours ago
不過我覺得prefix的想法真的很好，因為我本來是想簡訊實聯的作法會讓實聯發送成本變得很低，變成我可能可以把更細部的場域也做成QR Code做掃描，例如說公園電線咁也可以放這樣
au:sdgs:  8 hours ago
公園電線桿就比較不容易 fallback 到紙本了，變成 opt-in，我覺得也無妨就是了 (edited) 
acechen  8 hours ago
By the way, 真的是 1922 嗎？這樣問會不會爆雷 XD 但是跟防疫專線分開比較好？比如說 1985 (誤XD
pichuchen  8 hours ago
我覺得會不會fallback到紙本是一個信心問題，如果他覺得害怕，怕自己不會用，那就會改選擇比較明確的選項。
可是明明這些人（說不會用的）都用 Line 傳早安圖傳的很勤勞 XD
au:sdgs:  8 hours ago
簡碼必須用 1922，是因為接觸通知的最後一動就是請你回撥，而且初期大量的客服需求也只有 1922 可以彈性吸收。 (edited) 
:+1:
1

pichuchen  8 hours ago
另外是今天有想到的延伸，是QR Code 載具的加強，在人流真的比較多的地方可以用 nfc tag ，印象中他也有 smsto 這樣的東西，所以可以做到類似新加坡 tracetogether 那樣的 UX
:bulb:
1

pichuchen  8 hours ago
https://www.163.com/dy/article/G98RPO0905148HD5.html
技術差別在新加坡的系統需要安裝 SafeEntry Gateway 這有硬體安裝問題
163.com163.com
5月17日起，新加坡全岛将强制使用TraceTogether“合力追踪”器
5月17日起，新加坡全岛将强制使用TraceTogether“合力追踪”器,新加坡,应用程序,tracetogether
May 5th
acechen  7 hours ago
覆議：我知道要初期要串 Line 會比較麻煩，但似乎 Line 在台灣有不可忽視的族群（我不是XD）也許未來可以加到 feature request
pichuchen  7 hours ago
其實我最近這幾天的感想，掃描實聯制 QR Code 是一種驚喜，因為你掃描之前其實不知道他是問卷還是Line ＸＤ
家樂福的系統是用Line
au:sdgs:  7 hours ago
目前對這些族群的說法就是「請用疾管家掃」。以我所知，LINE Taiwan 若要改核心功能，也需要等 app review cycle，更需要合乎某種明確目的（例如只支援 SMSTO:1922:，而不是所有簡訊，畢竟 LINE 是取代簡訊的 XD）。 (edited) 
pichuchen  7 hours ago
這是家樂福的，掃描之前真的不會知道他是一個Line機器人的OAuth頁面，充滿期待與驚喜(?
image.png 
image.png


au:sdgs:  7 hours ago
今天先這樣，晚安，明天中午再來維護新的 hackmd 頁面～ (edited) 
g0v.hackmd.iog0v.hackmd.io
1922 簡訊實聯制 - HackMD (725 B)
https://g0v.hackmd.io/FxudGiM8RSKnpCo4TrMhNg

:heart:
6

acechen  7 hours ago
這也是我傾向 SMSTO 而不是 URL ，電信端應該都處理好例外了，但 URL 很容易被 injection attack  (edited) 
pichuchen  7 hours ago
injection attack? 你是指XSS這類的嗎？
acechen  7 hours ago
比如說掃 QR code，你永遠不知道打開的是哪個網頁，又有沒有被 redirect etc.
pichuchen  6 hours ago
對，所以這個也是我會想要站在店家立場知道使用者有沒有輸入進來的原因，因為交班的時候可以要求做一次測試，有看到東西代表系統運作正常。
pichuchen  6 hours ago
那被偷換QR Code的損失平均會被控制在一個班內