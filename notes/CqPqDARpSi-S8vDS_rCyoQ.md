手機信令(cellular probe data)相關資訊
===

參考說明：
https://www.hindawi.com/journals/jat/2019/9401630/

> 手機開機的時候，其實基地台時不時會有一個 protocol (RRC) 和一個 timer (T3410) 確認手機還在不在這區，因為 MMC 要知道 paging 的時候要往哪裡送，所以有以下幾種情況
> 1. timer 到了手機主動做 RRC reconnect 更新 timer 且回報自己還活著 --> 手機在原來那區
> 2. 手機移動中，然後從基地台提供的 neighbor list 和手機自己掃的基地台，發現別台訊號比較好 —> 進行 hand over，做 TAU
> 3. 手機移動中，然後跨區了 (小區，不是中國那個「小區」的意思) ，仍然是進行 TAU
> 4. 手機正常關機，關機前發 RRC disconnect 告訴 MMC 它要下線
> 5. 手機沒電了，而且來不及發 RRC disconnect --> 在 T3410 timeout 的時候，基地台發現手機不理它，只好 deregister
> 6. 手機移動中，然後移到沒訊號的地方… 和 5. 差不多的做法，除非剛好遇上基地台要求手機做 signal strength measurement report 於是知道這隻手機快沒訊號了。
> 7. Verint 是另一個問題，他們似乎有一套系統可以不走 LI 介面，就透過 MSISDN (門號) 或是 IMSI (SIM卡上的號碼) 追蹤人在哪裡。我不知道他們用什麼技術去做。在很多國家 SS7 網路沒有鎖，所以有機會走這個路徑。但是因為那套系統只有執法單位買得到，敝國警方為什麼要買 Verint 我想才是需要追的事情。
> 
> 警察應該是和電信公司簽了約，要求他們在手機下線的時候發 alert
> 即使是這樣，這和 Verint, Pegasus 都完全沒有關係。這是標準的手機通訊協定，3GPP 標準實作。[name=miaoski]

> 許多電信商都有在銷售 OD(origin-destination) 資料，目前比較常看到的應用是用來分析交通運輸，下面提供其中一個類型的範例欄位
> '平假日', '旅次發生小時', '年齡級距', '性別', '家網格縣市', '家網格鄉鎮市區',
'家網格村里', '家網格', '家網格經度', '家網格緯度', '旅次目的', '旅次類型', 'OD是否經過居住縣市', '移動Duration組別', '起停留縣市', '起停留鄉鎮市區', '起停留村里', '起停留網格ID', '起停留經度', '起停留緯度', '迄停留縣市', '迄停留鄉鎮市區', '迄停留村里', '迄停留網格ID', '迄停留經度', '迄停留緯度'[name=kiang]

在 Covid-19 防疫工作，台灣跟南韓應該都有運用這樣的資料去追蹤確診病患的旅遊史，並不清楚原始資料現在能夠到達如何的精準度，但集合各主要電信商的資料後可以勾勒出大部分人民的活動記錄；目前比較大的疑慮大概是電信商在轉做其他用途時，並不是每個用途都像防疫工作那樣師出有名，也許在防疫工作有機會告一個段落後，該去思考其中該有的 opt-in/opt-out 規則，同時也該明確限制政府或各種單位運用這些資料的條件

基於電信需求蒐集沒有太大問題，問題只是被用在其他地方，像是各種交通研究，還有更多我們不知道的用途吧

## 染疫敦睦艦隊官兵足跡作法問題

> * 我想這已經是非常尊重隱私的做法了，合不合法我不確定，畢竟我不是律師，我的法學素養又一直很差。但是以技術觀點來看，一來這不涉及定位，二來對這些註冊過的人發送簡訊，它「可以不要 map 回電話號碼」(使用 IMSI paging 發送即可，也就是說，行政權可以選擇無視註冊到基地台的手機的持有人是誰 — 他們無視比較好，不然就有違法之虞)[name=miaoski]
> * 手機門號絕對是個資 , NCC "粉絲頁" 講錯了 :  "聯絡方式" --[個人資料保護法#2](https://law.moj.gov.tw/LawClass/LawSingle.aspx?pcode=I0050021&flno=2)[name=pofeng]
> * 匿名跟個資, 層次上有點不同,  單看 "職業" 一欄, 是匿名的, 但仍然是個資, 受個資法保障 --[個人資料保護法#3](https://law.moj.gov.tw/LawClass/LawSingle.aspx?pcode=I0050021&flno=3)[name=pofeng]
> * IMSI 是個資，手機門號也是個資 (門號是個資有高院判例)。保存的話，我不懂法律，但二年以上好像是必須的。IP 看國家，在荷蘭 IP 是個資，受 GDPR 保護，但是在美國 IP 就不是個資。[name=miaoski]
> * 「蒐集目的跟使用目的不同」這個你確定嗎？我沒看過法令，我不敢講。說不久蒐集目的當初在立法的時候就訂得很寬。[name=miaoski]
> * [個人資料保護法#5](https://law.moj.gov.tw/LawClass/LawSingle.aspx?pcode=I0050021&flno=5) & [個人資料保護法#8](https://law.moj.gov.tw/LawClass/LawSingle.aspx?pcode=I0050021&flno=8) & [個人資料類別清單](https://mojlaw.moj.gov.tw/LawContent.aspx?LSID=FL010631)[name=pofeng]
> * 美國很複雜, 沒有聯邦層級的個資法, 但加州有個資法, 聯邦層級有 HIPPA 規範(醫療)個資, 所以 :"以歐盟（EU）而言，IP位址是被視為可識別至特定個人的個資，美國聯邦貿易委員會（Federal Trade Commission，FTC）也認為，若IP位址與醫療健康資訊有關，就會被認定為個資之一。但是，在愛爾蘭的法庭卻認為，IP位址並不構成所謂個人資料的要件，因此不被視為是需要保護的個資。" [ref](https://www.netadmin.com.tw/netadmin/zh-tw/technology/5642043D99EB4F1D91C43AF268331617) [name=pofeng]
> * 和本題題旨有關的，應該要去查[《電信事業用戶查詢通信紀錄作業辦法》 #4](https://law.moj.gov.tw/LawClass/LawSingle.aspx?pcode=K0060075&flno=4)，但是該法沒有寫除了本人申請調閱以外的情況。我法學素養很差，看有沒有懂法律的人來補充一下。[name=miaoski]
> 

相關新聞：
* [提醒民眾避開人潮 政院研發警示APP](https://www.cna.com.tw/news/ait/202004110141.aspx)
* [染疫敦睦艦隊官兵足跡公布 20萬人陸續收提醒簡訊](https://www-cna-com-tw.cdn.ampproject.org/c/s/www.cna.com.tw/amp/news/firstnews/202004200035.aspx)

謠言：
* [台灣用衛星監控被隔離者](https://twitter.com/MiloHsieh/status/1241540231595044864)
* [以色列總理承認幫台灣侵害隱私追蹤每支手機](https://www.facebook.com/photo.php?fbid=10219885157615321)