# 保護吹哨揭密者的軟體工具

# GlobalLeaks & SecureDrop

此份共筆蒐集吹哨人與相關軟體工具的資料。特別感謝以下資料來源：

## 什麼是吹哨人

吹哨人（whistleblower）是指那些冒著法律威脅與生命危險，將違法、腐敗、不道德的資訊暴露給大眾的人。

> 正因為收集貪腐證據的過程並不容易，更需要鼓勵知道組織已出現腐敗情況的內線消息來對外揭露不法的資訊。- (https://blog.jxtsai.info/2017/01/31/globaleaks/)

並不一定要揭發重大醜聞才算是吹哨人，在不成熟的法律環境中，各種檢舉行為都會受到類似的壓力。例如，檢舉公司勞動條件違法時，也可能會因為資料外洩而讓檢舉人受到各種威脅。

> 在法律制度上尚未成熟的環境中，鼓勵揭弊行為最佳的保護作法，不妨透過科技工具的應用，讓揭弊行為的風險最小化來保護吹哨者安全。 -(https://blog.jxtsai.info/2017/01/31/globaleaks/)

## 匿名爆料軟體：GlobalLeaks
> GlobaLeaks是由HERMES Center for Transparency and Digital Human Rights這個ＮＧＯ／新創社創（？）所推動的一個專案。HERMES成立的願景就是要提倡社會整體對於民主透明度與法治問責的意識與關注，因此它除了作相關主題的研究報告外，也推動某些技術性專案的開發。而GlobaLeaks就是其中一個技術性專案，希望讓媒體機構或是ＮＧＯ組織，能夠輕易地架構出一個讓吹哨者可以透過此平台進行內幕不公資訊揭露的通訊工具,讓這些體制內的不公或問題得以為外人所知。 - [GlobaLeaks project 中文化 ~ Return to laughter](https://self.jxtsai.info/2016/04/globaleaks-project.html)

比起使用 PGP 等加密通訊，GlobalLeaks 提供簡化後的流程，爆料者只需下載 Tor Browser 後，即可透過熟悉的 web 介面上傳機密資料，大大省下許多時間與技術門檻。

## GlobalLeaks 安裝方式
以下流程已在 GCP 虛擬主機、Ubuntu 18.04 上測試成功。對於缺乏軟硬體資源的組織而言較為容易。

#### GlobalLeaks 系統需求

* CPU：雙核心 2GHz
* RAM：2GB
* 儲存空間：20GB，根據資料量擴充
* 網路頻寬：10Mb/s 
* email 帳號

#### 安裝步驟

1. 在 linux 主機上執行以下三個指令：
```
wget https://deb.globaleaks.org/install-globaleaks.sh
chmod +x install-globaleaks.sh
sudo ./install-globaleaks.sh
```

如果安裝步驟出現簽證錯誤，參考 Tor 安裝步驟，手動設定 apt repository

1. 安裝 `gnupg`

```
sudo apt install gnupg
```

2. 修改 `/etc/apt/sources.list`，加入以下兩行

```
deb https://deb.torproject.org/torproject.org bionic main
deb-src https://deb.torproject.org/torproject.org bionic main
```

3. 執行以下兩個指令，加入 Tor Project 的金鑰

```
gpg2 --recv A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89
gpg2 --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | apt-key add -
```

之後重新執行第一步驟的三個指令即可。

## GlobalLeaks 使用方式

參考 https://blog.jxtsai.info/2017/01/31/globaleaks/

## 其他的吹哨方式
除了 GlobalLeaks 之外，還有其他的吹哨工具：

#### SECUREDROP
SecureDrop 是另一套類似的軟體，比起 GlobalLeaks 提供了更強大的保密系統。不過，架設門檻也高上許多。比較可參考這篇 [GlobaLeaks and SecureDrop: which is right for you? – Focus Determines Reality](https://yawnbox.com/globaleaks-and-securedrop-which-is-right-for-you/)

其他的軟體可參考 The Intercept 的介紹：[The Intercept Welcomes Whistleblowers](https://theintercept.com/source/)