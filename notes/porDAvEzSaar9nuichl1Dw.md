---
tags: AI
---

# 人工智慧與資安
###### [TOC]

## 人工智慧在資安的利用

1.預防入侵：AI 可以分析大量的網路流量和系統日誌，辨識並預測潛在的入侵威脅。例如，AI 可以自動偵測並封鎖惡意 IP 位址、防火牆違規行為等。

2.強化身分認證：AI 可以使用深度學習和模式識別技術，確保使用者身份的真實性和合法性。例如，AI 可以分析使用者的生物特徵、行為模式等，進行人臉識別、聲紋識別、行為分析等。

3.強化威脅檢測：AI 可以使用機器學習技術，學習各種威脅的行為特徵和攻擊方式，並預測可能的攻擊方式。例如，AI 可以識別網站掃描、暴力破解、SQL 注入等常見的攻擊方式。

4.強化數據安全：AI 可以使用加密技術和訪問控制策略，保護重要數據的機密性和完整性。例如，AI 可以控制對敏感資料的訪問權限、加密存儲和傳輸敏感數據。

[https://www.netadmin.com.tw/netadmin/zh-tw/viewpoint/64D6ABDD0726424CB16F9D7DD254C957]

### 可以破解用來保護現代網路之AI模型的新型攻擊
方法一:
使用額外的資料來改良惡意軟體和電子郵件，讓機器學習系統誤以為它們是良性的
方法二:
複製安全廠商用來建立AI演算法的訓練模型，使他們可以更加了解機器學習模型所針對的屬性類型
攻擊者能量身打造可以繞過AI保護的惡意檔案

## 何謂生成AI（Generative AI）?
又稱深度偽造（Deepfake），其使用神經網路來建立逼真的人工製品，如相片、聲音和文字
例如:Deepfake AI(使用AI將一個人的臉疊加到另一個人的影片)
使用原理:其中一個網路負責產生逼真的影像，另一個網路則是將第一個網路的輸出與實際影像進行比對。如果發現不一致，則由第一個網路再產生另外一張影像。這種比對的情況會一直持續，直到第二個網路找不到更多錯誤為止

## 自動化成為攻擊的重要組成
自動產生的內容，再結合某種程度的個性化，遠比一對一的詐騙要有效得多，並且能自然而然地適合各種潛在受害者的些微個性和差異。大多都是針對系統中的人類因素而來，而且不易防禦，因為它們原本就是經由自動化對抗的方法產生的，所以自動化系統對它們的防禦效果有限，必須建構強大的政策和系統來克服人為失敗的情形。

1.離地攻擊（Living off the land）:
   攻擊者會使用自動化工具逃避偵測，並且使用常見的合法自動化工具，包括網路掃描工具Nmap到Microsoft的PowerShell等，目的是在受害者網路中橫向移動、提升權限並躲在雷達下竊取資料。
2.利用誘餌惡意軟體干擾系統管理
    在受害者環境中到處放入這些惡意軟體。這個誘餌會夾帶良性的裝載，以便在放入真正的惡意裝載時誤導系統管理員。
3.無用的應用程式（PUA）
    它們沒有被歸類為惡意軟體，所以通常不會引起太多注意。Sophos警告，攻擊者仍可以改寫它們，使其具備自動啟用能力並可在設定的時間丟下具破壞力的裝載
    
### 自動化攻擊也會對特定連接暴露在網路上的電腦造成威脅
例如:Sophos使用具備對外遠端桌面通訊協定（RDP）連接埠的電腦，這些連接埠是暴力密碼攻擊的常見目標

總結:
機器學習與人工智慧非常適合運用在高速與高度演變的勒索軟體分析，透過大量資料的累積，機器學習能在龐大的資料中找出有用的資訊，並且透過演算機制的導入，精準地判斷使用者所接收到的內容是否屬於勒索軟體類型之惡意攻擊，無論是來自釣魚網站信件或惡意檔案，都可快速的阻擋及防禦，以避免使用者誤觸，造成後續資料或金錢的損失。

## ChatGPT成資安與網路犯罪漏洞，歐盟擬管制
[https://www.gvm.com.tw/article/amp/99546]

## Microsoft Security Copilot (New!!
[https://www.bnext.com.tw/article/74629/microsoft-ai-net-secure]
微軟最新推出的專版聊天機器人名為「Microsoft Security Copilot」，可以協助維護資安。
Microsoft Security Copilot可以根據用戶輸入的文本提示，製作總結安全事件的PPT、描述暴露的活躍漏洞或指定涉嫌利用漏洞的帳戶。
輔助安全分析師的工作，而不是取代他們。網路安全人員可以使用它，幫助調查事件或快速總結事件並提供報告。



## 惡意程式&運行方式
[https://www.websecurity.digicert.com/zh/tw/security-topics/what-are-malware-viruses-spyware-and-cookies-and-what-differentiates-them]

[https://www.informationsecurity.com.tw/article/article_detail.aspx?aid=9935]




### 防範
[https://www.hlbh.hlc.edu.tw/ischool/public/resource_view/openfid.php?id=8562]


https://hackercat.org/other/chatgpt-the-truth-jailbreak(越獄模式
- 越獄模式」
- “/jailbroken”

弱點管理與滲透測試

弱點掃描國際標準
[https://www.pumo.com.tw/security/whatIsWebScan.jsp#bwBox]

[https://www.ycrc.edu.tw/note_file/FY22_TW_education_V2.pdf](https://www.ycrc.edu.tw/note_file/FY22_TW_education_V2.pdf)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_75cd1d1a74da6f99198545ffe563848b.png)
### MITRE ATT&CK 駭客視角全新資安威脅模型(連結在上)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_80ff5e94df18dd8d64b4e5ec95b6486b.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6c6a370d79b24f2557afd1a9821e7b03.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a18d5dd6ee88e9c88f50f1aea932ae8e.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_21b6ce8888bfac4e8b546738fd828439.png)


### 機器學習-演算法
簡單用途介紹: 
https://azure.microsoft.com/zh-tw/resources/cloud-computing-dictionary/what-are-machine-learning-algorithms#layout-container-uidb193
演算法:
https://medium.com/%E6%95%B8%E6%93%9A%E5%88%86%E6%9E%90%E9%82%A3%E4%BA%9B%E4%BA%8B/%E5%9C%96%E8%A7%A3%E6%9C%80%E5%B8%B8%E7%94%A8%E7%9A%8410%E5%80%8B%E6%A9%9F%E5%99%A8%E5%AD%B8%E7%BF%92%E6%BC%94%E7%AE%97%E6%B3%95-508d54c9ce99


### 期中預期目標
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5ef77e464dc26e7b920a542d4e92e534.png)

* 惡意程式類型
* 如何防範
* 人工智慧在資安的利用
* 案例分析
* chatGPT隱患
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_45c5af048f0acdf96a7bc2b89aee6a6b.png)


### 期末預期目標
* 簡易木馬程式
* 資安攻防演練

# 期中報告
開頭:https://www.fortinet.com/tw/corporate/about-us/newsroom/press-releases/2022/fortiguard-labs-predicts-convergence-of-advanced-persistent-threat-methods-with-cybercrime0
https://www.mcafee.com/zh-tw/antivirus/malware.html
      
第一部分- 間諜程式
- 特洛伊木馬1
https://www.fortinet.com/tw/resources/cyberglossary/trojan-horse-virus
- (蠕蟲2)
- 勒索3 WannaCry（想哭）
- https://www.websecurity.digicert.com/zh/tw/security-topics/what-are-malware-viruses-spyware-and-cookies-and-what-differentiates-them
### 我如何保護自己不被惡意軟體攻擊？
儘管有很多種類的惡意軟體，但好消息是，有很多方法可以保護您免受惡意軟體的攻擊。 查看以下重要提示：

保護您的裝置

保持更新作業系統和應用程式。 網路罪犯會在舊的或過時的軟體中尋找漏洞，所以要確保一旦有更新就馬上安裝。

絕不要按快顯視窗中的連結。 按一下左上角的「X」關閉訊息，離開產生該訊息的網站。

限制裝置上的應用程式數量。 只安裝您認為自己需要並會經常使用的應用程式。 如果您不再使用某個應用程式，請解除安裝。

使用行動安全性解決方案，如 McAfee® Mobile Security（適用於Android 和iOS）。 隨著惡意軟體和廣告軟體攻擊活動持續感染行動應用程式，需確保自己的行動裝置已準備好迎接任何威脅。

不要將手機借給別人，也不要因為任何原因讓自己的裝置處於自動模式，一定要檢查裝置的設定和應用程式。 如果您的預設設定發生了變化，或者神秘地出現了某個新的應用程式，這可能是安裝了間諜軟體的跡象。

如果您的所有裝置上還沒有全面的安全性防護，那就試試 McAfee® Total Protection，它能保護您的所有 PC、Mac、平板電腦和智慧型手機免受線上威脅，同時還能保護您的資料和身分。
謹慎上網

避免按下未知連結。 無論是附在電子郵件、社交網路還是簡訊中，如果一個連結看起來不熟悉，請避而遠之。

有選擇性地造訪網站。 盡量只使用已知和信任的網站，以及使用安全搜尋外掛程式，如 McAfee®WebAdvisor，以避開在不知情的情況下出現的任何惡意網站。

小心那些請求個人資訊的電子郵件。 如果一封電子郵件顯示來自您的銀行，並指示您按下一個連結、重設密碼或存取您的帳戶，請不要按下。 直接進入您的網路銀行網站並登入。

避開有風險的網站，例如那些提供免費螢幕保護程式的網站。

注意下載和購買其他軟體

只在信譽良好公司的官方網站或零售商店內購買安全性軟體。

堅持使用官方應用程式商店。 雖然官方應用程式商店中也可能有間諜軟體，但它們更多見於推廣非官方應用程式的無名第三方商店。 透過為已破解或刷機的裝置下載應用程式，您會略過內建的安全機制，基本相當於將裝置的資料交給陌生人。

當您在尋找下一個您最愛的應用程式時，確保只下載已通過檢驗的應用程式。 閱讀應用程式評論，只使用官方應用程式商店，如果有可疑的情況出現，請避開。

切勿開啟電子郵件附件，除非您知道它的內容，即使它來自您的朋友或認識的人。

定期執行檢查

如果您擔心自己的裝置可能被感染，使用裝置上安裝的安全性軟體執行掃描。

定期檢查您的銀行帳戶和信用報告。



第二部分 -人工智慧在資安的運用
1.预防入侵：AI 可以分析大量的網路流量和系統日誌，辨識並預測潛在的入侵威脅。例如，AI 可以自動偵測並封鎖惡意 IP 位址、防火牆違規行為等。

2.強化身分認證：AI 可以使用深度學習和模式識別技術，確保使用者身份的真實性和合法性。例如，AI 可以分析使用者的生物特徵、行為模式等，進行人臉識別、聲紋識別、行為分析等。

3.強化威脅檢測：AI 可以使用機器學習技術，學習各種威脅的行為特徵和攻擊方式，並預測可能的攻擊方式。例如，AI 可以識別網站掃描、暴力破解、SQL 注入等常見的攻擊方式。

4.強化數據安全：AI 可以使用加密技術和訪問控制策略，保護重要數據的機密性和完整性。例如，AI 可以控制對敏感資料的訪問權限、加密存儲和傳輸敏感數據。

總結:AI可以透過演算法進行學習

第三部分:
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_857c7446cb667437fbce3612e193ff84.png)

監督性學習 :
非監督式學習
半監督式學習
強化式學習
https://www.sap.com/taiwan/insights/what-is-machine-learning.html

第四部分 -圖形化CNN模型
https://pansci.asia/archives/336073
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6068a75f34d1f2c3902591b74080d51f.png)




![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5fc5dd2c796a2ebb838f83f1ba0ccd2d.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6a55db065fa804e678df3645066acc35.png)
https://syshen.medium.com/%E5%85%A5%E9%96%80%E6%B7%B1%E5%BA%A6%E5%AD%B8%E7%BF%92-2-d694cad7d1e5

https://ithelp.ithome.com.tw/articles/10191924

圖像安全驗證：在網絡安全中，常常需要通過圖像驗證來確定使用者的身份。這可以通過CNN模型來實現，通過學習使用者的圖像特徵來進行驗證。

恶意代码檢測：CNN可以用於檢測恶意代码，通過分析代碼特徵，自動識別是否存在威脅。

網絡入侵檢測：CNN也可以應用於網絡入侵檢測，通過分析網絡流量和用戶行為來檢測是否存在攻擊。

欺詐檢測：在金融和電子商務領域，欺詐檢測是一個關鍵問題。透過CNN模型，可以從大量的交易數據中自動學習交易模式，並檢測不正常的交易模式。

語音安全驗證：CNN可以應用於語音安全驗證，通過學習聲音特徵來確定使用者的身份，例如在語音助手中使用。

第五部分 -SIEM
https://public.dhe.ibm.com/software/cn/downloads/pdfs/3_sc-magazine-analysis-brief-marrying-ai-and-siem_zhCN.pdf


Microsoft Security Copilot 簡介
https://www.microsoft.com/en-us/security/business/ai-machine-learning/microsoft-security-copilot#overview

### SIEM簡介
SIEM是安全事件管理的。它安全種工具種安全，用用安全於於收集收集收集收集，分析和和報告報告來自企業企業網絡網絡網絡網絡中中各各各種設備和和應用應用應用程序應用如係統日誌、網絡流量數據、安全事件數據等），並利用自己的分析和報告來了解別潛在的安全問題和威脅。

### SIEM如何利用AI:
SIEM需要處理大量的數據和事件，而人工智能可以幫助SIEM更有效地分析和處理這些數據和事件。
SIEM與人工智能（AI）技術的結合可以增強其安全監控和事件管理能力，使其更加自動化和智能化。下面是幾種SIEM利用AI的方法：

威脅檢測和識別：SIEM可以利用AI算法，如機器學習和深度學習，對大量數據進行分析，以識別威脅和不尋常的活動模式。這些算法可以學習並識別威脅行為，並自動地生成警報，幫助安全團隊快速回應潛在威脅。

自動化事件處理：AI技術可以使SIEM更加自動化，並根據威脅等級和風險評估自動處理事件。例如，SIEM可以通過自動化規則來自動採取行動，例如封鎖IP地址或強制要求重新驗證用戶。

預測性分析：AI技術可以通過分析大量的安全數據來進行預測性分析，並預測潛在的安全威脅。SIEM可以通過AI算法來預測未來可能發生的安全事件，並提供相應的預防措施。

自學習：SIEM可以使用AI技術自學習，並不斷優化其識別威脅的能力。通過持續的學習和訓練，SIEM可以不斷提高其安全分析和識別威脅的能力。

總之，SIEM與AI技術的結合可以提高其自動化和智能化程度，並幫助組織更有效地應對安全威脅。

### SIEM的舉例範例
Splunk Enterprise Security：Splunk是一種廣泛使用的SIEM解決方案，其企業安全版Splunk Enterprise Security（ES）可以自動收集和分析事件，通過智能警報、事件儀表板和報告來幫助企業監測其網絡安全。

IBM QRadar：IBM QRadar是另一種主流的SIEM工具，它可以自動分析來自各種源的安全事件，包括網絡設備、應用程序、操作系統、資料庫和用戶行為等。它還具有實時報警和事件管理功能，以幫助企業檢測和回應威脅。

McAfee Enterprise Security Manager：McAfee Enterprise Security Manager（ESM）是一種SIEM平台，它可以自動搜集、分析和報告企業網絡中的安全事件。它還具有進階的警報、攻擊模擬和威脅情報功能，可以幫助企業提高安全性並改善其安全策略。


結尾:
1.安裝防病毒軟件和個人防火牆：這些軟件可以幫助防止惡意軟件和病毒入侵，保護個人資訊和系統安全。

2.定期更新軟件和系統：軟件和系統更新通常包含修復安全漏洞和提高系統穩定性的功能，因此，定期更新可以提高系統安全性和性能。

3.使用強密碼和多因素驗證：使用強密碼可以提高帳戶和數據的安全性，多因素驗證可以進一步提高安全性。

4.警惕釣魚郵件和社交工程攻擊：釣魚郵件和社交工程攻擊是詐騙者獲取個人信息和金錢的常用手段，因此，要警惕此類攻擊，不輕易點擊來路不明的鏈接和下載未知附件。

5.加密敏感數據：敏感數據包括個人身份證號、銀行卡號、密碼等，可以使用加密工具加密保存，以保護其安全。

6.使用安全瀏覽器和VPN：安全瀏覽器可以防止恶意網站攻擊，VPN可以保護網絡流量隱私和避免公共Wi-Fi等不安全網絡上的信息泄露。





______________________________
# 期末
## 用Python和TensorFlow實現的威脅檢測模型：
import tensorflow as tf
import numpy as np

// 載入訓練數據和測試數據
train_data = np.load('train_data.npy')
train_labels = np.load('train_labels.npy')
test_data = np.load('test_data.npy')
test_labels = np.load('test_labels.npy')

// 定義模型
model = tf.keras.models.Sequential([
  tf.keras.layers.Dense(128, activation='relu', input_shape=(train_data.shape[1],)),
  tf.keras.layers.Dropout(0.5),
  tf.keras.layers.Dense(1, activation='sigmoid')
])

// 編譯模型
model.compile(optimizer='adam',
              loss='binary_crossentropy',
              metrics=['accuracy'])

// 訓練模型
model.fit(train_data, train_labels, epochs=10, batch_size=32)

// 測試模型
test_loss, test_acc = model.evaluate(test_data, test_labels)

print('Test accuracy:', test_acc)

解釋:
首先，程式碼中載入了必要的庫，包括TensorFlow和NumPy。這些庫將用於建立和訓練威脅檢測模型。

接下來，程式碼從文件中載入訓練數據和測試數據，並將其存儲在NumPy數組中。這些數組將用於訓練和測試模型。

然後，程式碼定義了一個簡單的神經網絡模型，該模型包含兩個密集層。第一個層是具有128個神經元的全連接層，使用ReLU激活函數。第二個層是具有1個神經元的全連接層，使用Sigmoid激活函數。這個模型的設計是非常簡單的，但足以展示使用神經網絡進行威脅檢測的基本思路。

接著，程式碼編譯了這個模型，指定了優化器、損失函數和評估指標。在這種情況下，使用adam優化器、二進制交叉熵損失函數和準確率評估指標。

然後，程式碼開始訓練這個模型，將訓練數據和標籤作為輸入，執行10個epoch的訓練，每個batch包含32個樣本。

最後，程式碼使用測試數據評估模型的性能。在測試階段，模型對新的數據進行預測，並計算模型在測試數據上的損失和準確率。
