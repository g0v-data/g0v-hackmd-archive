# 網路急難時的重要民生網站

###### tags: digital-resilience


```
在天災人禍導致「台灣對外斷網」時，希望能盡量維持正常運作的重要網路服務。
```

**情境：** 2023年初，馬祖的對外海纜被中國的拖網漁船/挖沙船「意外」挖斷，因而斷網長達一週。 假設此一情境發生在台灣，台灣對外網路骨幹的海纜斷了八九成（甚至完全中斷），推估需要一個月以上才能恢復的話，有哪些服務，是維持*基本生活品質*必要的服務，應在「只有島內網路」的狀態下維持正常運作？

**範疇：** 國民第一線會使用的「網路服務」、「手機 APP」。

> 不納入實體離線服務如 7-11 店面與捷運⋯⋯等。也不列入各消費端服務的上游相關設施（如 EC 網站的物流，我們期待該網站能與其供應鏈上下游協作，推行進一步的韌性計畫）

**倡議：** 民生必需的服務應備有網路嚴重障礙的緊急應變計劃，並且定期進行相關的演練。


---

## 重要民生網站與數位服務

### 搜尋引擎

|||
|---|---|
| Google | google.com |
| Yahoo奇摩 | yahoo.com |


### 新聞

|||
|---|---|
| 中央社 | cna.com.tw |
| 公視 | pts.org.tw |
| 警廣（線上直播） | https://www.pbs.npa.gov.tw/ch/app/programList/list?module=programlist&id=18112 |

<!-- 
|Youtube|youtube.com| 
在災難狀態下，我認為大量耗費流量的線上影音，不太適合列入必要服務 [name=Irvin]
-->

### 流通

|||
|---|---|
| MoMo | www.momoshop.com.tw |
| 蝦皮 | shopee.tw |
| PChome 24 | 24h.pchome.com.tw |

### 生活

|||
|---|---|
| Google Maps (app / web) | |

### 通訊與社群

| Service | Link | Notes |
|-|-|-|
| Line | | （需想辦法檢測其啟動、訊息收發時會運用到的 API）|
| Telegram | tg.me | (同上) |
| Gmail      | mail.google.com | |
| Yahoo Mail | mail.yahoo.com | |
| Ptt | ptt.cc | ssh, web access, api | 


<!-- 本專案納入的範圍為「平常就被大量使用，而災難時希望能維持運作的民生服務」，以下適合災難環境下使用的服務移到:
https://g0v.hackmd.io/oyNRfe4lTuaZ5RbcPSS7TQ?both#peer-to-peer-服務測試

| Briar      | briarproject.org | 不需要網際網路，僅靠藍芽即可傳送文字訊息的通訊軟體。初次設定仍需網際網路。 |
| Bridgefy   | bridgefy.me | （同上，但沒開源。） |
-->



### 官方與避難資訊

||| 備註 |
|-|-|-|
| 總統府 | www.president.gov.tw ||
| 國防部 | www.mnd.gov.tw ||
| 內政部 警政署 防空避難專區 | https://adr.npa.gov.tw |  (Website, Google Map) |

### 政府 APP / 金流 / 發票

> 烏克蘭曾經用一些健保APP來推播戰爭資訊，所以可能也能盤點台灣很普及的政府APP  [name=Ronny]

| APP | 主管機關 / link | 備註 |
|-|-|-|
| 健保快易通 | 衛服部 | |
| 集保e手掌握 | 臺灣集中保管結算所 |
| 統一發票兌獎 | 財政部 |
| 發票存摺 | https://apps.apple.com/tw/app/id1276986959 |
| 雲端發票 | https://apps.apple.com/tw/app/id512920023 |


<!-- 
我覺得這個屬於「日常不會用到的東西」，其覆蓋率應該會隨時間越來越低，且功能已停止也難以檢測，可先跳過
| 台灣社交距離 | 衛服部 | 疫情期間實裝的 | 
-->

### 銀行

|||
|---|---|
|||

### 對外溝通與宣傳

|||
|-|-|
| X | x.com |
| Facebook | facebook.com |



---

## 數位服務的基礎建設

> 列入基準：大量民生服務運用的資訊基礎建設與服務。
> 先行調查這些服務是否有落地節點，構成檢測上方民生服務的韌性所需的重要資訊


### 作業系統相關基礎服務

|| notes |
|-|-|
| iCloud | |
| Ubuntu apt mirrors ||
| Firebase | 手機上的 push notification |
|||

> iPhone / mac 運作時會存取（depend）超多 icloud 下的服務（與 api），android / windows 有什麼相對的服務?[name=irvin]



### 雲端平台 / IaaS / SaaS

| 供應商 | 台灣有節點  | 資料來源 | 備註 |
| --- | --- | --- | --- |
| AWS | Y | [ref](https://aws.amazon.com/tw/about-aws/global-infrastructure/localzones/locations/) | |
| Azure | Coming soon | [ref](https://azure.microsoft.com/zh-tw/explore/global-infrastructure/geographies/#geographies) | |
| Azure CDN | Y | [ref](https://learn.microsoft.com/zh-tw/azure/cdn/microsoft-pop-abbreviations) | |
| Google Cloud   | Y | | |
| Cloudflare | Y | | |
| Akamai | | | |
| Digicert |  | | 憑證驗證商<br> 在檢視 DNS log 時，發現 iPhone / Mac 都對這個憑證商有大量存取，如果無法使用，是否會造成 https 連鎖信任問題？ [name=Irvin] |
| GitHub | | | 許多軟體資源都在上面，少了它可能有很多緊急建置需求無法達成 |
| Google Workspace | | | 許多企業運作必須 |
| Microsoft 365 | | | 同上 |


### 被許多廣泛使用的 framework / service

| framework | 服務提供的預設網址 | 是否有國內節點 | 備註 |
|---|---|---|---|
| jQuery | code.jquery.com | Fastly / 香港 | |
| Google Tag Manager | www.googletagmanager.com | ? (Google) | |
| fontawesome | kit.fontawesome.com | Y (Cloudflare) | |
| Adobe (Typekit) | use.typekit.net | | 死掉可能沒差 |
| Google Font | | | 死掉可能沒差 |



<!-- 需離線可得或整理與分流的防災資訊移到：https://g0v.hackmd.io/oyNRfe4lTuaZ5RbcPSS7TQ?both#防災知識庫
### 生存

| Service | Line |
| -------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Survival Manual (Offline App)                      | [F-Droid](https://f-droid.org/packages/org.ligi.survivalmanual/), <br />[Google Play Store](https://play.google.com/store/apps/details?id=org.ligi.survivalmanual), <br />[Amazon appstore](https://www.amazon.com/ligi-Survival-Manual/dp/B06WW43R3T). |
-->


---

## 服務韌性檢測方式（wip）

- 檢查網站 hosting 所在地 & API 所在地
    - 位置：國內 / 國外
    - 是否是 anycast，且提供國內節點
- 網站 / API hosting 是否通過 CDN
    - CDN 是否是已知有落地的單位
        - cloudflare (TPE)
        - Akamai
- 有無使用外部 library (jquery, anguler, vue... etc)
    - 是否位於已知有落地的 CDN
        - cdnjs (over cloudflare)
        - jsdelivr?




