# 熔爐計畫《Code:Cauldron》與臺灣協定《Protocol of TAIWAN》

所有內容皆以GPLv3授權，且作者保有修改授權的權利。

## 楔子(有關動機與人工智慧)

當前開啟專案的原因很多，但簡單的說，是我經歷總和的思考。

為何要創造並開源這個系統？詳盡的解釋在下方的論文中，這裡則簡易的引出主旨。

熔爐是一個作業系統的核心，這個核心的功能是輸出個人的身分作為社會連結的基礎，以取代當前全球互聯網中的IP協議。

當前的人工智慧建立在主從架構上，也就是client與server的結構，這樣的結構與人類社會目前政府、企業與組織的結構有著相同的拓樸。

3200年來，人類社會運行的主流模式一直是統治者與被統治者、征服者與被征服者的關係，這種模式在過去一直是人類社會的主流，科技如同金錢，並不改變人性，而是來源於人性，並放大了人性。

設想一個人若擁有了3200年來所有人類的經驗，世上的一切都將被他改變，他將成為超人，而人工智慧將有能力做到。

也因為人工智慧能夠成就的巨大能力，使人類社會應該將主要的精力投入主從架構的變革，而不是人工智慧的技術變革。

在人工智慧伺服器成為私人的全球核武器以前，這種變革是必須的。

沒有了這種變革，人類會在舊有的主從結構中嚐到巨大貧富差距的苦果，偏狹的權力與財富，將使人類社會面臨災難、環境惡化、戰爭或滅絕的風險。

價值衡量、建設社會的貢獻、人類自尊與地位的認可應全面擯棄金錢、資本與銀行的特權模式，轉換成人人平權皆得以計算機網路協議實現的全新模式。

只有在沒有任何人被拋下，建立在對等架構，以計算機語言統一實現全體人類高度的協議，武裝每個個人的權益，才能有效的對抗這些風險。

下面的論文詳述了計畫如何一步步形成以及實施改變的根據。

2024/06/23

[name=Benjaminpeng]

## 理論基礎

### 社會哲學的計算機原理
BenjaminPeng
TomoBenjaminPeng@icloud.com

主題定義：
「社會」的根基在協作，沒有協作，就沒有社會可言。
「哲學」是抽取社會「本質」與「原理」的工作。
「計算機」提供「原理」實踐的工具。
「原理」提供「計算機」運行的程序。

#### 零、緣起:

讓我們承認：人類社會要達成美好與和諧的願景需要倚靠的是最高級的真理以及最基本的共同原則，這種既最高級又最基本的真理與原則，正如牛頓從星體的運動中提煉出的數學原理一樣，並不以個人或是集體的力量或意志所變，儘管後世的科學家能將其修正的更接近終極的知識，也並不妨礙自17世紀以來，人類依託其原理所鑄成的科學、科技、工業等文明成就。

讓我們承認：人類即使擁有了這些知識的結晶與文明的成就，亦未能塑造一個理想的人類社會：飢荒、戰爭、貧窮……數不勝數的人類與自然的浩劫，無不代表著我們的體制有問題，它們依託於過時或退化的原則與局部的利益所設，它們並不尊重宇宙存在先於我們的真理並謙遜地承認人類並非主宰。

所以，讓我們再次投向宇宙本存的原則，如牛頓一樣，淬鍊我們應該依託的宇宙法則，尊重真理、遵循自然規律，並依此建立與運行更好的人類社會。

我們將處理現行社會的首要問題：金錢問題，即價值衡量問題，也即人類的利益問題。

讓我為您闡述並回顧美國第一任財政部長漢彌爾頓的措施，因其塑造了近代美國資本主義經濟的實踐基礎，可以說沒有此人，就沒有近代的華爾街與當今的金融體系。

這套體系的起源，來自於美國建國遇到的第一個巨大問題：因獨立戰爭花費大量人力物力的戰爭債務問題，然而漢彌爾頓以他出身於貧民底層卻逐步走向權力巔峰的深刻人性洞察與經驗，實施了一套被後世稱為旋轉門的計畫，具體的步驟為：

1. 美國十三州政府放棄並上交地方財政權及鑄幣權給中央，美國聯邦政府承擔所有地方債務。
2. 美國聯邦政府統一發行新美元，以1:1匯率向民間回收舊美元，所有新美元發向民間，舊幣退出市場。
3. 美國以統一身分發行新美元債券，當時的承銷債券者即為今日華爾街從業者的起源，以此回收民間的新美元(債信來源於政府有新美元徵稅權)。
4. 以新美元償還所有戰爭債務。
5. 至此，因為避免採用了貨幣濫發等將使信用喪失或造成通貨膨脹的隨意方法，美國建立起了強大的聯邦信用，保有尊嚴的新生，旋轉門完成。

若我們細究這些步驟，總結美國之所以能夠說服債主接受新美元的償還：

1.	來自華盛頓將軍的威信、紐約的運河與勤勞的美國人民(漢彌爾頓親口銷售債券的說辭)……
2.	來自統一的美國聯邦政府能夠依靠稅收回收新美元的實際權力
3.  來自美國政權延續的假設。

若我們再萃取這些總結的精華，使我們得到唯一精簡的要素，這項要素，即是美國對於未來的承諾。

然而，美國不是一個人，它是一群人，漢彌爾頓及美國國父們憑藉其意志匡列的一群人。

我們在內心深處與我們的經歷中知道，我們都來自某個家庭，我們也都並非孤島，在我們的經驗中：一個完美運作的組織，幾乎不可能存在，只要涉及一群人，無論大小，組織皆無可避免的持續內生出問題，會有人貢獻的多，會有人貢獻的少，會有不令所有人滿意的處理，也會有令人不快的反對，而組織之所以能持續的生存與發展下去，有賴於這些問題的解決。

也就是說，美國集體的承諾，到了當今，他們是否依然決意踐行到底？而哪個美國人，儘管是美國總統，他的個人或團體所能採取的行為，能夠代表每一個美國人所採取的行為？而美國人的利益，又豈是全人類的利益？

我要表達的是，當今流通金錢的本質，來自於對未來的承諾，只要這個承諾被背棄了或因為任何的因素不被實現，過往的承諾與金錢本身，並無任何價值，而這套體系並不憑空設計，它基於我們的人性，但卻不夠基本，因為它的基礎來自於國家這一基於一大群人的組織，而不是基於每個個人，所以它終將失敗。簡單試問：美國如何在不使外部付出代價的前提下，處理國內千萬的遊民問題？

我們必須承認，在歷史進程中不斷出現的無數改革，幾乎從未成功，真正成功的，大多為新生的東西，而那些舊有的，衰老的東西，它們終將自然的凋零。

在這裡，您應該意識到，正因為您在使用這個體系，所以您就是這些承諾的買單者，我完全了解社會近乎沒有其他選擇的現況，但您要知道，當這個體系出問題時，沒有人能夠為我們負責，除了我們自己。

所以我需要提出更好的方法與做法，而我也需要人們能夠共同參與建立新的東西。

所以，讓我們回到鑄幣的源頭，什麼東西有價值？什麼價值能夠使整個人類公眾得以採信並使用？

讓我們承認：真正的價值，來自於我們每個人的承諾，我們將從這些承諾中，創造真正的價值，我們不需要一個模稜且超過我們能力所能夠處理的「國家」或「政府」來發行實際無力掌握運行的東西。我們將不再以華盛頓將軍的威信、新生美國的軍事力量、漢彌爾頓的才幹、紐約的運河或美國的天然資源……來當作貨幣的支持基礎，我們的基礎將來自於普世的原則、來自於我們每一個人。

我們也將不再需要繳稅，不再需要將軍或英雄來拯救人類的社會，讓我們直接承認：我們需要的：是我們自己，也只有依靠我們自己，我們每個人才能重新得到我們原本就有的自由，從現存的體制中解放。

我所提出的鑄幣基礎，是所有人皆平等的資源：*時間。

時間，如何成為鑄幣基礎？

再敘述至此前，請讓我為您闡述歷史的證據與現實的需要，以支持我們將賴以建立的原則與程序。

*BAT(Basic Attention Token)是一套曾經發起的類似的區塊鏈專案，但與我們的模式將有差異。

#### 壹、	歷史的證據與現實的需要

大多人以為，人類文明的開始，最初是以以物易物作為價值交換的基礎，構成了協作，形成了部落，鑄成了文明。

然而這並非事實，以物易物天然存在，然而因其天生缺乏效率的做法，並不足以形成有效率的協作組織和部落。

真正能讓文明形成的關鍵：是來自驗證、保證每一筆交易進行的第三方。

我這麼說，完全是基於自然的常理。

交易之中，買方擔憂對方供給商品或服務的品質是否符合其宣稱？而賣方亦擔憂買方的償付能力，或是買方欲以清償的代價，是否有其真實價值？

任何一筆涉及微小利益的交易，或許是一顆饅頭、一碗羊奶、一把米……這些交易之所以不需要通過驗證而能迅速達成的原因，單純是因為交易的雙方因為交易利益的微小，自認能承擔交易出錯的風險。

然而當交易本身，涉及到個人會對交易風險感到擔憂的規模時，這時第三方驗證的出現，完全基於自然而形成的需要。

簡單的說，買賣雙方誰先交錢，誰先交貨的問題，在沒有第三方提供保全或驗證的情況下，交易的信任問題就無法被解決。
 
在現代大額交易的代表：不動產買賣上，這種擔憂，以一套程序被簡單解決。

0.	賣方擁有由政府權力擔保在其轄下的產權。
1.	買方準備購買產權，將價金轉至第三方信託帳戶(通常為賣方指派銀行，買方同意後行之，因賣方關注買方之償付能力及代幣價值)。
2.	賣方已見價金至第三方帳戶，將產權移轉至買方。
3.	買方驗證過產權後，第三方帳戶將價金轉至賣方。

但這套方法在現代社會的成形並非一蹴而就，在歷史的進程中，為了形成這套穩固的體系，人類付出了巨大的代價，書寫了時代的興亡。

從古至今，這個提供第三方驗證的實體，真正鑄寫了人類的歷史。

這個提供驗證的實體，在古代：是祭司、是教皇、是酋長、是帝王，然而演進到現代，這個驗證方的主體，已經轉變為銀行、資本或財閥。

我們究其本質，誰能夠不讓一筆交換出錯？更甚者：誰能夠提供擔保？

在古代，教皇或祭司，因其律法上的解釋權形成權威(古時教皇擔任法官)，能以巨大的群眾號召力形塑秩序，這種權威迫使交易的雙方有因其不誠信所必須付出的代價而形成威攝。(由教皇權威提供的懲罰、下獄……或是死亡。)

酋長與帝王更為直接，透過暴力的優勢與實施，提供秩序的保證。

也正因如此，自古皇權與教權因其提供的功能屬相不同(一文一武)，有協同、亦有競爭的形勢。

但人類歷史向前的洪流中，總有人們不願意為權威和力量所屈服，他們不願在這樣的統治下生活，不願與其接觸。

但人只要活著：合作就無所不在，必要的交易必須完成，實際的問題也需要被實際的解決，於是：實物抵押，成了一種能夠不倚賴強制力而形成的驗證機制–由雙方都認為有價的東西，作為公信，以完成交易。

這種方法，由貴金屬商人開始，形成了最初的銀行。

然而，正如皇權與教權的競合般，財權為了維繫本身的存有，亦需與其他兩者合作，也必與競爭對手產生競爭。(只有財產的，遇到戰爭會失去；只有暴力的，失去群眾支持會失勢；而只有法律的，亦無法只依其本身保證其發展。)

所以我們得到簡單的結論，一個完整的社會秩序，需要法律、權威、文化上的話語權；需要科技、軍隊、競爭力的領導地位；亦需要財富與金融的擔保力……失去任何一份擔保協議的脊柱，秩序都有崩潰的風險。

然而如今的人類社會，已經有數十億人，我們要怎能決定–哪個群體擁有怎麼樣的財富？擁有怎麼樣的權力？又擁有怎麼樣的名譽和擔保力呢？……無論我們如何決定，沒有個體或區域這麼偉大，在能力極限以外，永遠都有力有未逮的問題。

所以，要解決這個問題，只有一個方法 — 基於共同的原則，而不是基於哪些人，或是哪個群體。

具有一套能實踐運行普世原則的程序與計算機，而不僅僅只是如獨立宣言般的宣示，即是人類的新世界得以形成的基礎。

而得以連接所有人的技術，我們也已有了，就是互聯網。

當今的人類社會，真正統一的語言，是計算機的二進制語言，而人類現在的社會，完全可以基於互聯網，建立一個基於人類全體的社會體制。

互聯網能夠把世界任何一個角落的任何人連接在一起，只要人們知道怎麼連接，備有設備，互聯網就應帶給任何人以平等與無盡的機遇，而不致孤立。

#### 貳、從複式簿記到時間帳本(從資本主義的實踐基礎到基於共同原則的實踐)

為了實現現代經濟社會運作的秩序，資本主義並非僅是理論，它具體實現在每一張債券、每一檔股票、每一份有價證券、每一份地契……與每一分錢中。

您應該能夠認知到：沒有您手上的任何一分錢，是不存在源頭的。

而您應該也能夠想像：這世界上的每一分錢，都來源於世界上某一處帳本的紀錄。

所以當我們真正細究這一切的現實是基於什麼時，我們會發現這一切的物理基礎就是帳本，如此簡單而已。

但您在這裡，不應該沒有合理的疑惑：「我手上的這份錢，究竟源自哪個帳本記錄？這個源頭是基於什麼能成為源頭？為什麼這個源頭不是我？究竟憑什麼，別人能是源頭，而我卻要玩別人設定好的遊戲？」

這種基於部分人的權力，而不是所有人皆有的權力，即是當下不平等現況的根源。

然而如我上節所述，金錢最初由承諾的形式鑄成，直到轉移到您手上成為真正可以使用的數字：是由政權、金權、教權等擔保力量集體運作後的結果。這些概念並不是虛幻的，它們必依託於某人或某集體(通常為集體)的長期作為才得以實現，也有其過去發展的必然需求與原因。

所以我無意基於這種不平等的現況，去挑起任何一種情緒，因為人要能超越自己的立場為超過自己的一切考慮，絕非能隨意律人的限制，而更應為自發的覺察，試問：「如果您已因過去的經歷，成就了財富、權力、名聲與地位，您又怎會因他人不是中心就放棄已經成為這一切中心的自己呢？您又怎會確信已是中心的自己，能夠張開雙眼去看見一切中心以外的人們、那些感受到不平或正在受苦的人們是否需要關注和關懷呢？而我是否能將他們視為一體，成為我的一部分、成為我的責任、成為我需要去幫助的人？您是否會謙遜地看待一切的擁有，去堅定地相信、追尋與實踐：這世上存在的偉大力量和讓星體運轉的真理？」

所以我也無意以「推翻」的方式去打倒這些人或破壞資本主義的遊戲，因為若是拉遠至超越己身的廣闊格局與歷史的長河中來看，這一切現況，也不過是人之常情。

正如法國大革命所示，我們應當真正注意的最大問題是：革命後要建立什麼？眾人應該重塑、遵循何種秩序而活？我們從歷史中知道，一旦採用「推翻」的方法，就會陷入不面對這些真正重要問題的情緒，而一旦陷入混亂與激情，必誕生出人們對秩序的急迫需要，出現解決問題的將是拿破崙或希特勒那樣「有能力」重整秩序的強人。

所以我的立場是：真正能夠改變世界的行動，並非打倒或是推翻現存的中心，而是基於平等的原則，打造一個人人皆可為中心的基礎，並以此基礎做連結的新世界。

正如一切看似抽象的資本主義或經濟理論絕非脫離現實的倡議，它們存在著您看的到、摸的著、用的了的金錢物理現實，亦存在著得以將這一切落實的實體根本工具，即–複式簿記，所以亦如我們將在這裡倡議與建設的，也絕非沒有實踐的方法與建設的工具。

我們將打造的，是吸收了前人篳路藍縷走過的歷史經驗後，一套嶄新的，包含了所有資本主義優點，但卻改善了弊病的新東西。

我們要建立什麼？什麼樣的秩序與程序，能夠讓眾人信任與採用？

我們計畫打造類似WordPress般兼有非營利組織org(得創造廣大自由貢獻的社群、擁有大量外部插件……)與營利組織com(創造私有的實作典範)並存的生態系。

我們將首先打造的是：一套自由、開源、基於尊重個體所設計、能部屬至所有裝置，使人人得以使用的自動化時間紀錄程序，亦使人人得以自建個性化的時間報表應用、繼承了複式簿記的精神與經驗再創新的*時間帳本。

為什麼我們需要這個帳本？

還有緣起的提問：時間，如何成為鑄幣基礎？

因為我們每天每個人擁有的皆是24小時，這24小時完全由自己所支配，而您如何花費時間，這個帳本就會如何記錄。

基於實證紀錄，我們將基於時間這個珍貴且人人平等卻最常被忽視其價值的資源，建立新制度，以革新退化的社會現實，帶來新的現實。

而鑄幣基礎，來自於您為他人所花費的時間，即投入的關注，成為受關注者的時間代幣。(EX:假使有人在網路中創造了一些內容，並使自己共得到了20000小時的他人關注，這20000個小時的時間代幣即為鑄幣基礎。)

要注意的是，這些鑄幣基礎並非金錢，它們是代幣。真正讓這些代幣轉換成流通貨幣需要一套所有人認可的協議與程序，而這套程序與協議的基本要求是：近似牛頓的數學原理，即它並不因個人或集體的意志所變，也即：某種程度上來說，它並不需要公眾的認可 — 所以它能得到所有人的認可，它應該是不證自明的源於真理與常識，我將在述及這些協議與程序時再闡明。

這一套協定，我簡稱為：臺灣協定TAIWAN Protocol，展開為：分時人工智慧廣域網路協定Time-Sharing Artificial Intelligence Wide Area Networks Protocol。

*一套自動化的時間紀錄程序，可輸出多樣的時間報表，完全保存於私人的裝置，同時解決現存社會中的隱私權問題，不會由中央的伺服器保存，不會有後門，系統以自由、開源的方法，供人人檢視。
記憶於獨立的記憶體空間，因需基於整體記憶資料統一輸出一個動態的身分識別，作為與他人連結的基礎，彼此只有在發生造訪、鑄幣、交易、契約、銷毀、聯合……等一切關聯時，依一套新的網路協定，進入公眾的公開運作體系。

#### 參、從國家為管理發給的靜態身分到個人為連結而總結的動態身分

名字、身份證字號、生日、護照號碼……這些基本的靜態資訊構成了人在當前社會中的身分，這些簡化的識別訊息存在的原因是為了滿足第三方權力對於社會管理的需要而並非代表人真正的「身分」。

如果一個人的墓誌銘要回答「你是誰？」這個問題，同一個人可能有千百種敘述方式，然而若我們總結來看，人就是他這一輩子經歷的所有時間紀錄。人的身分可以非常複雜，來自多重經驗的總和，他可以同時是經理、飛機駕駛員、運動員、企業主、地主、租戶、歌唱明星、父母親、孩子、兄弟姊妹、祖父母、發明家……等所有字符的疊加，而人若尚未蓋棺論定，身分甚至是隨著時間動態變化的，我們知道僅僅只是簡易的靜態資訊不能夠代表他。

雖然為了社會連結的需要，這些簡化的識別訊息，大幅增進了效率，然而付出的代價是有著足夠權力得以忽略個體權益的強大第三方。

所以需要重塑身分系統對於社會變革來說至關重要，若我們不將自古上下的主從關係，改變成由協議主導的對等關係，人類將不能再解決既有的如貧富差距、戰爭、不平等的世界等種種重要問題。

我們完全可以建立一個為人人打造，完全保護個人隱私，基於服務每個個人的時間紀錄應用，並可輸出唯獨身分的個人身分系統，並以此作為連結的新基礎，形成新的社會運作模式。

我們主張建立的新社會，並不是無政府、缺乏管理的混亂狀態，而是改變主從架構的管理模式，使之轉向為人人皆被協議賦權、人人皆得成為第三方、人人皆得隨時退出不為第三方、人人關係由計算機執行協議、社會地位因貢獻而有差別的新模式。

#### 肆、價值鑄造、流通、銷毀的協議

連載中……

歡迎您加入這個計畫共同建設，我們目標讓人人從現有的資本世界中解放、重新調焦，使人人能與社會有平等的關係，亦讓人人更好的享受本自擁有的自由。

[name=Benjaminpeng]

## 現況與問題

1. 互聯網資訊的碎片化：互聯網實現全球資訊互通，但上傳的文件、圖片、影音......等一切資訊都來源於「人」的碎片，也就是說，所有的資訊，都來自於某創始來源的割裂，而呈零碎、混亂的狀態。
    > 也就是說，要整理整個互聯網，使其不再零碎，而有秩序，需要一套全新的模式，根植於每個創始來源，也即每個人，因為人本身就是資訊的創始者。
2. 攸關經濟的一切問題：要成就大事，需要解決資源的困難，也即面對當前的金錢系統，解決攸關每個人的資源問題。
    > 基於全球標準時間作為資源衡量與價值鑄造的基礎，最終完全取代現有的金融體系。
3. 攸關政治的一切問題：當價值衡量的標準從金錢過渡到標準時間並重塑整個社會，現代的政治系統就會全部重塑。 
4. 世界的政府統治下的人類與大企業承載了數十億人的"授權與信任"
5. 世界的政府是區域性的、部分性的，封閉的，大企業的本質是商業、閉源的
6. 政府本質是割裂的、區分的、鬥爭的，大企業的社群媒體是分眾的，容易創造同溫層
7. 世界政府靠人類的汗水與勞作生存，媒體曲解現況，大企業的社群媒體靠廣告與商業維生，資訊的破碎使演算法不會使人們關注真正重要的問題。

## 目標

1. 重塑全球互聯網：以一套基於個人身分互聯的協定，取代當前基於地址連結(IP address)與內容連結(HTTP協定)等資訊碎片化的協定，先在區域實現，最後擴展到整個人類社會。
2. 重塑全球經濟系統：以全球標準時間作為資源標準衡量系統，以此標準資源衡量系統建立價值衡量系統，最終完全取代現有的金融體系。
3. 重塑全球人類社會管理系統

[name=Benjaminpeng]

## 解決方案

(-1).建立如RescueTime, ManicTime等自動追蹤時間記錄程序作為當前應用，依未來依然可用的UX設計，形成初始UI。

0. 熔爐計畫《Cauldron》
    > 將個人資訊形成單一身分，並以此唯一的身分證作為新的IP。

1. 區域實現到展望全球：臺灣協定《Taiwan Protocol》
    > 分時人工智慧廣域網路協定 Time-Sharing Artificial Intelligence Wide Area Networks Protocol。

> 請問樓主想實做的項目，是否能用Feature by Feature的方式列點, 比較好懂?[name=Bestian]

## (-1). functions set[name=Benjaminpeng]
1. Automatic Time Tracking : Tracks time spent on applications, websites, and documents without manual entry.
2. FocusTime Sessions and Real-time Alerts: Allows users to block distracting websites and set focus goals to stay on task and notifies users when they are off track or exceed set focus limits.
3. Goals and Alerts: Users can set goals for productivity, receive real-time alerts, and monitor progress towards these goals.
4. Detailed Reports: Provides daily, weekly, and monthly reports with detailed insights into how time is spent, helping identify productivity trends.
5. Weekly Summaries: Summarizes weekly activities and productivity scores, offering insights to plan the upcoming week more effectively.
6. Distraction Management: Identifies and blocks distracting websites, aiding in maintaining focus during work hours.
7. Customizable Work Hours: Allows setting specific work hours and tracking offline time to ensure work-life balance.
8. Offline Tracking: offline time tracking capabilities, tracks breaks and non-work activities, giving a complete picture of time allocation 
9. Integrations and Plugins: Supports integration with calendars and other productivity tools to provide a holistic view of time usage and offers plugins for web browsers
10. Activity Dashboard: A comprehensive dashboard that visualizes time usage data with graphs and charts.
11. Tagging and Automatic Categorization: Automatically categorizes activities based on the user’s work type for more relevant insights and  Users can add custom tags to activities
12. Smart Coaching: Provides personalized advice and tips to improve focus and productivity based on usage patterns.
13. Timesheet Management: Features for tracking billable hours, generating invoices, and managing client billing 
14. Reporting and Exporting: Generates detailed reports in various formats (PDF, Excel) and allows data export for further analysis or sharing 
15. [non-fucntonal requirements]Data Security and Privacy: Offers encryption, password protection, and control over data access 
16. [non-fucntonal requirements]Cross-Platform Compatibility: Available on Windows, macOS, and Linux, allowing seamless time tracking across different devices
17. [non-fucntonal requirements]Mobile App: Allows time tracking on the go, with synchronization to the desktop version for comprehensive tracking and reporting
18. Advanced Features for Pro Version:
    - [non-fucntonal requirements]Time Server topology
    - Auto tagging
    - [non-fucntonal requirements]Advanced search topology
    - Tag shortcuts
    - Scheduled backup
    - [non-fucntonal requirements]Privacy protection
    - Shift day start 

[name=Benjaminpeng]

## 可能的限制

1. 開發者人力
2. 測試者人力
3. 使用者習慣不容易一夕改變


# 目前攸關的APP、開源專案、網路媒體或NPO專案：

## 英文與國際(共筆收集中)

1. [RESCUETIME](https://www.rescuetime.com/)
2. [MANICTIME](https://www.manictime.com/)
3. [BAT(Basic Attention Token)](https://basicattentiontoken.org/zh/) and [Brave(Browser)](https://brave.com/)
4. [KaiOS](https://www.kaiostech.com/)
5. [OpenID](https://openid.net/)
6. PassKey
> 請問PassKey的url?[name=Bestian]
7. [Meta Group](https://www.meta-group.com/)
8. [Fediverse](https://fediverse.party/)
9. [Mastodon](https://joinmastodon.org/)
10. [GentooGroup](https://www.gentoogroup.com/)
11. Pop! 
> 請問Pop!的url?[name=Bestian]

## 中文與在地(共筆收集中)

1. [自學2.0](https://we.alearn.org.tw)- NPO專案, 公開部份個資的互認平台, 地圖介面.
    > [簡報檔](https://docs.google.com/presentation/d/1mok1-N8zmTUKukIdtetemBejXgJdBcCL_U6iXBFWJyQ/edit#slide=id.g19637ce7b_0205)
    > [專案Github Repo](https://www.github.com/3dw/auto20-next)

> 可以抓裡面的部件來用，就不必重頭造車輪[name=Bestian Tang 小巴]


# 坑

> 請問樓主想實做的項目，是否能用Feature by Feature的方式列點, 比較好懂?[name=Bestian]

## (-1). functions set[name=Benjaminpeng]
1. Automatic Time Tracking : Tracks time spent on applications, websites, and documents without manual entry.
2. FocusTime Sessions and Real-time Alerts: Allows users to block distracting websites and set focus goals to stay on task and notifies users when they are off track or exceed set focus limits.
3. Goals and Alerts: Users can set goals for productivity, receive real-time alerts, and monitor progress towards these goals.
4. Detailed Reports: Provides daily, weekly, and monthly reports with detailed insights into how time is spent, helping identify productivity trends.
5. Weekly Summaries: Summarizes weekly activities and productivity scores, offering insights to plan the upcoming week more effectively.
6. Distraction Management: Identifies and blocks distracting websites, aiding in maintaining focus during work hours.
7. Customizable Work Hours: Allows setting specific work hours and tracking offline time to ensure work-life balance.
8. Offline Tracking: offline time tracking capabilities, tracks breaks and non-work activities, giving a complete picture of time allocation 
9. Integrations and Plugins: Supports integration with calendars and other productivity tools to provide a holistic view of time usage and offers plugins for web browsers
10. Activity Dashboard: A comprehensive dashboard that visualizes time usage data with graphs and charts.
11. Tagging and Automatic Categorization: Automatically categorizes activities based on the user’s work type for more relevant insights and  Users can add custom tags to activities
12. Smart Coaching: Provides personalized advice and tips to improve focus and productivity based on usage patterns.
13. Timesheet Management: Features for tracking billable hours, generating invoices, and managing client billing 
14. Reporting and Exporting: Generates detailed reports in various formats (PDF, Excel) and allows data export for further analysis or sharing 
15. [non-fucntonal requirements]Data Security and Privacy: Offers encryption, password protection, and control over data access 
16. [non-fucntonal requirements]Cross-Platform Compatibility: Available on Windows, macOS, and Linux, allowing seamless time tracking across different devices
17. [non-fucntonal requirements]Mobile App: Allows time tracking on the go, with synchronization to the desktop version for comprehensive tracking and reporting
18. Advanced Features for Pro Version:
    - [non-fucntonal requirements]Time Server topology
    - Auto tagging
    - [non-fucntonal requirements]Advanced search topology
    - Tag shortcuts
    - Scheduled backup
    - [non-fucntonal requirements]Privacy protection
    - Shift day start 

[name=Benjaminpeng]


# MVP(Minimum Viable Product)

> 試想：如果只有三個核心功能，你們想要什麼？[name=Bestian]

> 如果只有三個核心功能模組, 應該只會是單機功能，只支持個人使用，無法支援團隊。[name=Benjaminpeng]
> 試想：如果只有三個核心功能，你們想要什麼？
 1. 使用者追蹤與數據收集
 2. 數據分析與圖像化報告生成
 3. 使用者介面




## 技術層面


前端：
* Framwork
> 推 Quasar + Vue3 但不排斥其他
> 

後端：
* Framwork  or Service
> 推 Firebase 但不排斥其他
> 
UI/UX設計：
* Framwork  or Service
> 推 Figma + chatGPT4 但不排斥其他 
> 