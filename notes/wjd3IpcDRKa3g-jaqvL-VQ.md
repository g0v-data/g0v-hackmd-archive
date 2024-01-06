---
title: "社區資料規格討論"
tags: hackpad
---

# 社區資料規格討論

> [點此觀看原始內容](https://g0v.hackpad.tw/ZqJ6xeehvKw)


\# 2017-03-29 會議筆記

### 兩處平台簡介

- 防災地方誌
    - [https://lowiki.tw/main/](https://lowiki.tw/main/)
    - 目前採用行政區劃方式來界定「社區」，最小單元為村或里
- 社區通部落格
    - [http://sixstar.moc.gov.tw/blog/localfarm/communityAction.do?method=doCommunityView](http://sixstar.moc.gov.tw/blog/localfarm/communityAction.do?method=doCommunityView)
    - 目前以社區組織為內容主要撰寫者，至少包含「組織基本資料」與「社區基本資料」

### 討論「如何認定社區」

- 社區的認定
    - 公寓大廈 or 里辦公室 or 社區發展協會
    - 社區活動中心一般是里辦公室負責管理
    - 以社區為主體來看，發展協會只是一個其中的組織型態，所以可能是一種社區概念對應到多種實質型態的情形。
    - 對文化部而言，要有一個人民團體組織才能認定為社區，不一定有地理上的邊界，有的社區可能跨兩個里，或是行政區重劃了被規到另一個行政區，但是當地居民認為自己屬於原本的地區
    - LocalWiki 的概念比較著重在地理上的界定，反而不涉及人或組織。
    - 東波：我們所認知的社區到底是什麼！！！！？？？
    - 維志：我認為還是跟地域有關係，**但這個地域劃和行政區域的劃分沒有必然的關係**。所以我們在村里的行政區層級的上一層會怎麼處理？或是要把社區做為另一個層級來討論？我認為這邊討論的社區就是一個組織了，**所以對我來講的最小單位就是一個法人組織，只是這個組織有它的地域**。
    - 社區營造上，是一群人有了社區感，才凝聚起來去申請一個法人組織。
    - 所以這樣的社區概念，要怎麼跟 LocalWiki 的地區概念整合在一起？
    - 哲瑋：假如文化部的社區通網站，請社區把自己認為自己的社區範圍畫出來？
    - 至今沒有單位去把它做起來！！！可能大家自己都還在形成那個認定中。
    - 國際推動開放資料的單位，是否已提出「社區資料規格」必要欄位？
        - 暫列可能相關的網路素材
            - [http://linkedgeodata.org/About](http://linkedgeodata.org/About)
            - Nextdoor is the private social network for your neighborhood. [https://nextdoor.com/](https://nextdoor.com/)
            - Neighborland [https://neighborland.com/](https://neighborland.com/)
    - 其他討論頁面：[https://g0v.hackpad.com/ork4P0hC7jF](https://g0v.hackpad.com/ork4P0hC7jF)
- 文化部的立場
    - 社區，若是沒有跟文化部或公部門有互動關係的法人組織的話，我們要考慮嗎？
    - 東波：我沒有要給一個界線，但需要給一個概念。

### 社區基本資料

- 地域範圍
    - 通常是 polygon 而非點或線
    - 組織特性影響了 polygon 的構成方式，例如：
        - 里辦公處 polygon 即該里範圍
        - 社區發展協會 polygon 有時候不一定與行政區劃方式完全一致，由該團體自己認定
        - 公寓大廈管理委員會 polygon 多數就是該集合式住宅的建築線範圍內為主
        - 部落 polygon 多將傳統領域納入，海域、海岸、山林、溪流等情境多元
- 組織型態
    - 若從行政區劃最小單元的角度出發，單元內可能有一個、或多個、或沒有法人組織、或不是法人組織資格的團體，例如：
        - 里辦公處（例如：臺北市北投區奇岩里）
        - 社區發展協會（例如：臺北市北投區奇岩社區發展協會）
        - 巡守隊
        - 公寓大廈管理委員會（例如：）
        - 文史工作室（例如：）
        - 獨立書店（例如：淡水有河Book）
        - 部落（例如：）
    - 該組織與公務體系的關係
        - 例如：文化部有沒有補助這個組織？有沒有什麼樣的政策措施輔導關係？
- 地區內的人口特性
    - 人口總數
    - 年齡分佈
    - 族群：客家、閩南、外省、原住民族、外籍
        - 哲瑋：可能可以從  [最小統計資料](http://moisagis.moi.gov.tw/moiap/match/system_common.cfm)  那邊配合地域範圍算出來
        - 客委會有客家聚落人口普查，最小單位到鄉鎮。但數據上可能不能直接套用到我們的情況，像有的閩南聚落中有小的客家聚落會特別強調自己的特殊性，但在統計上不會認定他們客家聚落。也有可能他們人口外移了，人口數變少，但他們很強調自己的族群。這件事情對社區來說是情感性大於客觀性的。
        - 概念可以描述為「這個社區是以什麼族群所形成的社區」
        - 這部分也與「此地所使用的語言」相關聯
        - 這部分也與「ＯＯ街」相關聯，例如永和韓國街(中興街)、中和緬甸街(華新街)
    - 信仰與宗教
        - 相關概念：場所、信仰中心、祭祀圈
        - 很多社區跟這個是綁在一起的
        - 一些社區內的社會服務、教育等生活機能，也經常與宗教信仰場所相關
        - 廟宇也可能就是社區大學的所在，例如台南社區大學運用大廟興學的推動方式
        - 維志：宗教的資料有 4 星喔！
        - 歸納出幾種情境：
            - 祭祀圈 \> 社區：祭祀圈的範圍內有多個相異的社區自我認定屬於該祭祀圈
            - 祭祀圈 < 社區：社區裡的信仰設施，像是社區內的一個土地公廟，祭拜範圍小於社區範圍
            - 社群網絡式：社區裡的信仰設施，這個信仰設施是比較社群網絡式的特性，例如臺北市大安區的清真寺，並不是清真寺旁邊成為回教信眾社區，而是都市中各處信眾會來此的一個節點
- 自然環境，地理設施
    - 山
    - 河
    - 基礎設施
    - 水利
        - 農田水利會。現在社區通裡有些社區會有這樣的自我描述，但比例不高。
        - 多半水利會或灌溉範圍，會比社區的地理範圍還大。
    - 涉及的特色環境法規，以下舉例：
        - 花蓮縣富里鄉豐南村由縣府依《文化資產保存法》登錄為吉哈拉艾文化景觀 [https://www.facebook.com/ciharaay/](https://www.facebook.com/ciharaay/)
        - 臺北市大安區蟾蜍山地區登錄為文化景觀 [http://www.bp.ntu.edu.tw/?p=3155](http://www.bp.ntu.edu.tw/?p=3155)
        - 臺北市大安區青田街保存區聚落風貌保存專用區 [http://www.geo76.tw/2011/08/blog-post_09.html](http://www.geo76.tw/2011/08/blog-post_09.html)
        - 臺北市大同區大稻埕歷史風貌特定專用區 [http://uro.gov.taipei/ct.asp?xItem=210939&CtNode=19998&mp=118011](http://uro.gov.taipei/ct.asp?xItem=210939&CtNode=19998&mp=118011)
- 商圈
    - 可能一個商圈在一個社區，也可能一個商圈跨好幾個社區，也可能一個社區有兩三個商圈。
- 產業
    - 例如農村再生補助計畫，會要求社區提出這個社區的特色產業是什麼
- 易犯罪地圖
    - 例如一些警政單位的開放資料
- 可以列舉更多種類的描述
    - 「ＯＯＯ」，並且描述「社區」與「ＯＯＯ」的相互關係。
    - 更多項目可以參考「社會經濟地理資料服務平台」內有建立的資料項目
        - [https://segis.moi.gov.tw/STAT/Web/Portal/STAT_PortalHome.aspx](https://segis.moi.gov.tw/STAT/Web/Portal/STAT_PortalHome.aspx)

### 延續發想


#### 「描述社區的流程」[https://goo.gl/vPqUMi](https://goo.gl/vPqUMi)

![](https://hackpad-attachments.imgix.net/osmtw.hackpad.com_Crl1cQWKBb7_p.208757_1490896589747_%E7%A4%BE%E5%8D%80%E8%B3%87%E6%96%99%E8%A6%8F%E6%A0%BC%20(2).jpg?fit=max&w=882)
- 描述組織
    - 填寫組織名稱
        - 鏈結法定組織資料
        - 帶入所需法定組織資料
    - 填寫組織特性
- 描述社區
    - 畫出社區範圍
        - 依據範圍與判釋原則，抓取相關地理資料
        - 呈現相關地理資料
    - 標註社區地理資料
    - 填寫社區特性

![](https://hackpad-attachments.imgix.net/osmtw.hackpad.com_Crl1cQWKBb7_p.208757_1490910464504_%E7%A4%BE%E5%8D%80%E8%B3%87%E6%96%99%E8%A6%8F%E6%A0%BC%20(3).jpg?fit=max&w=882)

### 關於部落，列舉請益對象

- 花蓮吉哈拉艾文化景觀
    - Website：[http://cilamitay.wixsite.com/cilamitay/blank](http://cilamitay.wixsite.com/cilamitay/blank)
    - FB：[https://www.facebook.com/ciharaay/](https://www.facebook.com/ciharaay/)
    - 台大地理博士生 Lameru Kacaw(阿美族)：[https://www.facebook.com/lameru.kacaw](https://www.facebook.com/lameru.kacaw)
    - 蔡博文老師指導學生
- 台東蘭嶼
    - 地球公民基會研究員 ChiaNan Lin：[https://www.facebook.com/cnlin81](https://www.facebook.com/cnlin81)
- 來義社區
    - [https://www.facebook.com/Giyav/posts/1213214112117323](https://www.facebook.com/Giyav/posts/1213214112117323)
- 基隆海濱社區
    - [https://www.facebook.com/chanupstairs/posts/10213887141241836](https://www.facebook.com/chanupstairs/posts/10213887141241836)
- 邵族傳統領域劃設課題
    - [https://www.facebook.com/titv.ipcf/videos/1504151282987942/](https://www.facebook.com/titv.ipcf/videos/1504151282987942/)
- [http://iknowledge.tw/](http://iknowledge.tw/)


