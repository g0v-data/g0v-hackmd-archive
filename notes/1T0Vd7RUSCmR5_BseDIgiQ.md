---
title: "社區醫療群地圖"
tags: event,醫療,hackpad
---

# 社區醫療群地圖

> [點此觀看原始內容](https://g0v.hackpad.tw/y7hpeEVwePc)

### 動機與目的

家醫科制度的精神是，民眾選擇一個長期配合的家醫科診所或是家庭醫師。家庭醫師會給予各種健康的照護與諮詢，並憑著專業知識判斷在患者需要更高層次的醫療時轉介到合適的醫院，在疾病穩定控制之後協助追蹤。
一來可以實踐三段五級預防醫學；二來節省醫療經費。畢竟醫院的掛號費比較貴，重新收集臨床資料的資源耗損也很可觀，地區醫院、醫學中心等機構也應該專注於比較困難的疾病。
配合國情與歷史因素，政府大約在 2003 年推行「全民健康保險家庭醫師整合性照護計畫」設計一個折衷的家醫科制度，由若干個基層診所 (可能是家醫科診所或是內外婦兒等其他專科) 加上至少一所綜合醫院組成一個「社區醫療群」，醫療群內部會視患者的病況互相轉診。
然而一般民眾大部分沒有這方面的訊息，即便有這樣的概念也不知道如何選擇。政府提供的查詢系統有很多限制，大部分的社區醫療群在網路上曝光的管道僅限於合作醫院的官方網站。我2013年九月想要開始以民眾的身分參與這個制度發覺這個過程並不容易，所以想要設計一個地圖呈現這些資訊。

### 目前成果

code：[https://github.com/mcdlee/communitymedcare](https://github.com/mcdlee/communitymedcare)
影片： [https://www.youtube.com/watch?v=8tml6g3lFAs](https://www.youtube.com/watch?v=8tml6g3lFAs) (COSCUP)
主機： [http://community.kmu.edu.tw/](http://community.kmu.edu.tw/) 感謝高雄醫學大學協助
> domain name 有人要幫忙想嗎？
> [name=昕迪 李]

> community general practioners (衛生署) [http://libir.tmu.edu.tw/bitstream/987654321/34471/6/%E8%A8%88%E7%95%AB.pdf](http://libir.tmu.edu.tw/bitstream/987654321/34471/6/%E8%A8%88%E7%95%AB.pdf)
> [name=昕迪 李]

> family doctor integrated delivery system (國家教育研究院) [http://terms.naer.edu.tw/detail/2010727/](http://terms.naer.edu.tw/detail/2010727/)
> [name=昕迪 李]

> (我本身在高醫，可以問一下線怎麼拉的嗎？)
> [name=淑華]

> 然後有沒有需要幫忙？
> [name=淑華]

> 陳以德老師和謝志昌組長幫我準備了一台 Ubuntu 的虛擬機器
> [name=昕迪 李]

> Domain name 目前取 community.kmu.edu.tw
> [name=昕迪 李]

### 未來發展方向

- 正本清源，請衛福部釋出此資料。
- 因為原生的 shiny 沒有提供每個選項的 permalink ，考慮以別的 framework 取代。
    - django
> 可以考慮以 [http://drugs.olc.tw/points](http://drugs.olc.tw/points) 為基礎，基本上原始碼都是公開的 [https://github.com/kiang/drugs](https://github.com/kiang/drugs) ，只是得學 PHP XD
> [name=Finjon K]

- 從地址得到 GPS 是透過 Google geocode，一來有授權爭議，二來對Google資料比較不完整的地區一定沒有 TGOS正確。
> TGOS API( [http://api.tgos.nat.gov.tw/TGOS\_MAP\_API/Web/Default.aspx](http://api.tgos.nat.gov.tw/TGOS_MAP_API/Web/Default.aspx) ) 也可以做，只是模糊比對能力比較差
> [name=Finjon K]

- 評價功能？

