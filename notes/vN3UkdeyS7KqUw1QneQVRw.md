---
tags: digital-resilience, 數位韌性松, DigiResiTh0n
---

# 海纜斷光會怎樣？
## When Submarine Cables Go Dark: Examining the Web Services Resilience Amid Global Internet Disruptions

@g0v hackath67n

2025/5/25

[g0v.hackmd.io/@irvin/cable-dark](https://g0v.hackmd.io/@irvin/cable-dark)

問題收集共筆
https://g0v.hackmd.io/@irvin/cable-questions/edit

---

## Irvin Chen

- Open Culture Foundation (OCF) Tech. Consultant
- MozTW, Mozilla Taiwan Community Liaison

Note:

自我介紹一下，Mozilla 志工、Firefox 的推廣者、摩茲工寮社群場地 hackerspace 顧門的志工、開放文化基金會顧問

---

## Submarine Cables Connecting Taiwan 台灣對外/境內海纜

https://www.submarinecablemap.com/country/taiwan

![](https://hackmd.io/_uploads/S1OpC_NZxx.png)

note: 10 cables (inc. 2 to China)

----

## How it connect us 台日間的連線

![](https://hackmd.io/_uploads/HJ-jTZc-gg.jpg)

note: 7 cables

---

# What if it's all broken? 
# 海纜斷光會怎樣？

----

src: https://github.com/irvin/digital-service-resilience?tab=readme-ov-file#韌性檢測結果

| Services | work without cables | 
| -------- | -------- |
| MoMo 產品頁 | Ｘ |
| Google | Ｏ |
| Gmail | Ｏ  |
| Google Maps | Ｏ  |
| Yahoo Mail | Ｏ |
| Bing | Ｘ |
| 華視新聞網 | ？ |
| 中央社 | Ｘ |
| 公視新聞 | Ｏ |
| 中央廣播電台 | Ｘ |
| 數位發展部 | ？ |
| 國防部 | ？ |
| 總統府 | Ｏ |
| 內政部警政署防空避難專區 | Ｏ |
| g0v | Ｘ |
| OCF | Ｘ |
| SITCON | Ｘ |

----

Think about your daily app and web - 
News, Communication, Office, Company system
Everything rely on internet infra will gone.

---

# Will it ever break?

---

## Curent status (2025/1~)

![](https://g0v.hackmd.io/_uploads/BkMQ3VExfex.png)

note: 扣除直接與對岸相連的 3 條海纜，總共有 8 個海纜系統將台灣連接到全球的網際網路。另外有 6 條海纜連接台灣本島與離島。光在今年，臺馬2號，臺澎3號就兩次被中國權宜船「意外」破壞。其中臺澎3號就發生在 rightscon 期間，也是我國第一次抓到當事船

----

## 2023/1-2025/1: 18 incidents

source: https://www.twreporter.org/a/damaged-undersea-cables-raises-alarm-in-taiwan

![20250212115800-6a695557a077052f75298106c11f527b-desktop](https://hackmd.io/_uploads/B1EgfFNZgl.jpg)

note: 台灣與馬祖之間的兩條海纜為例，2018-2023 六年之間，遭中國底拖網漁船、Sand Dredger 抽砂船破壞 27 次；2019- ，有 36次海纜遭外國船隻破壞的事件

---

## Weapenize “cable incidents” 

Ancient Tradition, Fresh Experience

source: https://www.twreporter.org/a/damaged-undersea-cables-in-europe-baltic-sea

![](https://hackmd.io/_uploads/rkzuVj4-xe.jpg)

- 2022/9 Russia-German Nord Stream gas pipe 北溪管線
- 2023/2 Matsu (50 days) 馬祖兩條海纜一週內損壞，斷網50天
- 2023/10/8 Finland-Estonia gas pipe & cable 芬蘭與愛沙尼亞間的天然氣管線與電纜
- 2024/11/15-19 Swiden-Lithuania-German-Finland cable 瑞典-立陶宛-德國-芬蘭
- 2024/12/25 Finland-Estonia 芬蘭-愛沙尼亞
 
Note: 

2023/10 新新北極熊號 - 從現場離開到聖彼得堡，並在事發地點遺留一個船錨，超過一百公里的拖痕；2024/11 伊鵬三號 180km been monitored by navy around but cannot do investment on International waters without china' consense。

過去170年，作為戰爭與灰色侵擾手段；1989 年美西戰爭，美國海軍中尉卡麥隆．溫斯洛（Lt Cameron Winslow）切斷古巴海域的電報電纜，試圖干擾西班牙的通訊網絡


----

## Route of 2/24 incident 

source  https://www.youtube.com/watch?v=NXroXYzXLX0

![](https://g0v.hackmd.io/_uploads/H1DghIWJxe.png)

note: 破壞臺澎三號的「宏泰輪」航跡, Z字型漂流兩天之後，在海纜「事故」後，才加速要離開

----

## Route of Jan incident

Source: (Finantial Times) https://www.ft.com/content/be994bfb-7299-4334-829d-230dddbc7e25


![](https://g0v.hackmd.io/_uploads/rJltAYLW1lx.png)


note: 一月時的「順興39」航跡,從12/5一路晃到1/3，後來得手後逃到釜山

---

## Natual Disaster

source: https://medium.com/vincent-chen/台灣海纜-submarine-cable-概況及備援機制-3e47ea550fd6

2006/12/26 恆春大地震

震央附近發生大規模海底山崩，影響網路與語音電話  
只剩北向 APCN 2 ＆ 法新歐亞三號（SEA-ME-WE 3）

![](https://g0v.hackmd.io/_uploads/H1gHQbSlGgx.jpg)


---

## Expensive & hard to fix, cheap and easy to break 

![](https://hackmd.io/_uploads/rJh6_o4bge.jpg)

- 台灣參與兩個海纜維護協議 
Taiwan participated in 2 Cable Maintenance Agreements: "South East Asia and Indian Ocean Cable Maintenance Agreement, SEAIOCMA" & "Yokohama Zone Cable Maintenance Agreement" 
- 海纜維修船只有 50 艘，台灣有合作的只有 6 艘 
50 repair vessles globally and 6 in local region from Japan / Korea / Singapore 
- 每次海纜斷掉的維修費用，中華電信自負 1~2 千萬 
Each fixing cost 10-20M TWD (50M-100M JPY) 
- 新建臺馬四號海纜成本 14 億
New Taiwan-Matsu cable #4 cost 1400,000,000 TWD (7000 Million JPY) est 2026

note: 海纜很貴，破壞很便宜, 破壞海纜只需要一艘破船一隻錨, Shadow Fleets
<!-- - agreement6 vessels 海纜維修船只有 50 艘，台灣有合作的只有 6 艘（South East Asia and Indian Ocean Cable Maintenance Agreement, SEAIOCMA）、橫濱區海纜維護協議（Yokohama Zone Cable Maintenance Agreement） -->
<!-- ，前瞻建設預算補助 2 億 -->

---

## Landing stations is also a fragile point

source: https://www.cna.com.tw/news/aipl/202501100035.aspx

![](https://g0v.hackmd.io/_uploads/SyNi6LgGlx.jpg)

Note: 

登陸點位於淡水、八里、頭城、枋山、大武、金門

----

## The only way is backup and backup?!

- Low-earth orbit satallite 低軌衛星：實用化需要數百至數千顆衛星 thousands of sat to be work
- Geo orbit satallite 同步軌道衛星：頻寬低、延遲高 slow and low brandwith 
- New cables 新海纜：十億起跳 cost 10M+USD
- Landing stations 海纜站

<!-- 數發部編列 5.3 億預算，被砍了 3 億
 -->
note:  基礎建設只能備援再備援, OneWeb 650, Telesat 300, starlink 7000
SES 中軌道&同步軌道 70顆，下行90Mbps/上行45Mbps，目前的軍事指揮備援

<!--

## 封鎖的有效手段

- 能源
- 經濟
- 通訊

破壞海纜、海纜站是低成本一兼兩顧的事情

災難情境分級：https://g0v.hackmd.io/@irvin/digital-disaster-level

note: 戰爭來臨前，可以預期海纜絕對會斷光；台海戰爭時世界再也看不到賴給清德的最後影片或共軍上岸的直播
-->

---

## What can we do to growing resillience besides new infra?

除了自己發射衛星、買現有低軌衛星、建設更多海纜與海纜站、建設更多微波系統以外，還有什麼辦法能提升網路韌性，讓大家在海纜斷光時，能繼續維持日常生活？


note: 數量問題、預算問題；網路本應是具有韌性的


---

## Understand the impact of cable broken 

## Keep more website live without cables (without international internet)

只要「海纜斷掉時，重要網站都還會動」，就可以將資訊封鎖的衝擊降到最小

note: 與國際上發生的 internet blackout 的不同；為什麼要確保對外斷線時，國內服務正常？ -如果戰時要用小七作為物資站，結果小七運作完全崩潰 -如果 gmail & google doc / office 365 無法使用

---

## Digital service resillience check

民生數位服務韌性檢測 

an g0v hackathon project 
g0v 韌性松專案
https://github.com/irvin/digital-service-resilience

----

## answer the question

“If the cables are gone, can ______ still work?”

<!-- **海纜斷掉時，______會動嗎？** -->

eg., [海纜斷掉時，MoMo 會動嗎？](https://irvin.github.io/web-resilience-test-result/?url=https://www.momoshop.com.tw/category/LgrpCategory.jsp?l_code=2180000000)

----

## How to ensure the site can work?

-> All requests need to be domestic 

1. collect requests data, [L52](https://github.com/irvin/digital-service-resilience/blob/7d689561185fcbda12ecc217eb5d4aa1ccba8bff/no-global-connection-check.js#L52)
2. clean data (rm known analytics, ads... etc useless requests), [L94](https://github.com/irvin/digital-service-resilience/blob/7d689561185fcbda12ecc217eb5d4aa1ccba8bff/no-global-connection-check.js#L94)
3. check loc of requests via IPinfo API, [L152](https://github.com/irvin/digital-service-resilience/blob/7d689561185fcbda12ecc217eb5d4aa1ccba8bff/no-global-connection-check.js#L152)

----

## Next steps

- 完善檢測的執行邏輯（處理 CDN / multicast... 問題）
deeper logics
- 收集更多更完整的現況數據
collect more field data
- 理解雲端平台對國際斷網的耐受狀態
cloud platform
- 提醒各單位、公司、工程師
raise engineer awareness 
    - 需要強化自己網站的韌性
    strengthern your site
    - 建立國內備援與回復計畫
    domestic backup and recovery plan
- 擬定政府如何著手的政策建議
policy suggestions for government

---

## Q1: Japan?

- country situation - country with many islands
- J Alert

## Q2: Can Japan Help?

- Taiwan-(Yonaguni)-Japan microwave link?
- low-orbit sat. ground station

---

## progress & contact 目前進度

**～努力找預算來做上述的事 finding the resources to do research～**

有相關（社會韌性、民防備戰、國安、網路 infra）的管道，或建議可以接觸交流的單位，還請幫忙引介。我們有詳細的企劃書： suggestion, discussion or refer org/resources: 
- t.me/irvin
- irvin@moztw.org
- OCF: hi@ocf.tw

---

## 延伸閱讀 references (in Trad. Chinese)

- [海底電纜斷裂危機下，台灣維繫「數位生命線」的應變挑戰｜報導者](https://www.twreporter.org/a/damaged-undersea-cables-raises-alarm-in-taiwan)
- [動態模擬「宏泰輪」詭跡：台、歐斷纜危機的中國陰影｜報導者YT ](https://www.youtube.com/watch?v=NXroXYzXLX0)
- [網路韌性的重要性 災害發生時，如何運用數位科技聯繫？｜科學月刊](https://www.scimonth.com.tw/archives/10981)
- [【RightsCon 紀錄】臺灣海底電纜關乎全球網路安全？專家籲增加經濟投資誘因 | READr](https://www.readr.tw/post/3030)
- [簡評SHUNXIN-39海底電纜事件之水下安全意涵｜國防安全研究院](https://indsr.org.tw/focus?typeid=0&uid=11&pid=2758)
- [海纜 (107篇報導)｜中央社](https://www.cna.com.tw/tag/12261/)

