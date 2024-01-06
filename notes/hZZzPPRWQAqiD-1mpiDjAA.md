---
title: "⭐ Country-Language-Selectors國家/語言選擇器：有一致排序的實現方案"
tags: hackpad
---

> [點此觀看原始內容](https://g0v.hackpad.tw/557poKLD3EG)

廖漢騰    聯合國大學計算與社會研究所 研究員 ( UNU-CS )

### 問題

上網時有沒有找要選取的國家，但上上下下找了很久還找不到的經驗？要用台灣、中華民國、Taiwan、還是China, Republic of找？排序到底是哪一種：筆劃、注音、拼音？國家/語言選擇器（**Country  Language Selectors**）是許多網站[國際化與在地化](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=3&ved=0ahUKEwj2u4_nsLDNAhWBVZQKHZgmA7gQFgguMAI&url=http%3A%2F%2Fwiki.ubuntu-tw.org%2Findex.php%3Ftitle%3D%25E5%259C%258B%25E9%259A%259B%25E5%258C%2596%25E8%2588%2587%25E5%259C%25A8%25E5%259C%25B0%25E5%258C%2596&usg=AFQjCNGYA4Qnh2OrhnfxVXyyfyd58oMiJQ&sig2=sJHD5VvOIweygCeGBg9PEA)的一環，然而用戶經驗和使用者介面設計需要有一致排序的實現方案。

### 背景

- OKFN [country code](https://github.com/datasets/country-codes/blob/master/data/country-codes.csv)
- [Riga W3C workshop slide](https:// https://www.w3.org/International/multilingualweb/2015-riga/slides/liao.pdf)

### 實作

- 利用 Unicode CLDR (資料) IBM ICU (排序) HTML5 (datalist 元素：[支援瀏覽器](http://caniuse.com/#feat=datalist) )
- Github: [Country-Selector](https://github.com/hanteng/country-selector) [All Demo](https://github.com/hanteng/country-selector/tree/master/demo)
- Rawgit demo: [zh-Hant Demo (台灣正體)](https://rawgit.com/hanteng/country-selector/master/demo/zh-Hant/index.htm) [my Demo (緬甸語)](https://cdn.rawgit.com/hanteng/country-selector/master/demo/my/index.htm) [ja Demo](https://cdn.rawgit.com/hanteng/country-selector/master/demo/ja/index.htm)  [(日本語)](https://cdn.rawgit.com/hanteng/country-selector/master/demo/my/index.htm)

### 待填

- 給UI及Web desinger 的全球說明：為什麼要用常用名（zh\_tw:南韓）而非官方名（zh\_tw:大韓民國）？為什麼要使用國家代碼或語言代碼？如何能鼓勵使用者使用國家及語言代碼？
- 給政府及企業網站的說帖：如何以最不冒犯/親合的方式處理國家及語言選擇器？
- 給HTML5開發者：Datalist如何能實現 國家/語言選擇器 實作的需要？

### 來源

- Liao, H.-T. (2015, April). _Country/Language Selectors Matter: A Call to Build and Implement a Common Translation and Country-Language Selector Repository_. Presented at the W3C Workshop Program:  Data, content and services for the Multilingual Web, part of the Riga Summit 2015 on the Multilingual Digital Single Market, Riga. Retrieved from [http://www.w3.org/International/multilingualweb/2015-riga/slides/liao.pdf](http://www.w3.org/International/multilingualweb/2015-riga/slides/liao.pdf)
- 廖漢騰 ； 陳舜伶 ； 鄧東坡 (2015). 國家代碼、分類及名稱的國際標準：比較聯合國M.49和萬國碼聯盟通用區域資料庫CLDR. _國土及公共治理_, _3_(4), 61–71. [PDF](http://ws.ndc.gov.tw/Download.ashx?u=LzAwMS9hZG1pbmlzdHJhdG9yLzEwL3JlbGZpbGUvNTU2Ni84MTcyL2NmYTZjMWFlLTBiZjMtNDVmMy1hYWNkLWRjZTM5NGNkODMxYS5wZGY%3D&n=5pys5pyf5bCI6aGMMDYt5ZyL5a625Luj56K844CB5YiG6aGe5Y%2BK5ZCN56ix55qE5ZyL6Zqb5qiZ5rqW77ya5q%2BU6LyD6IGv5ZCI5ZyL772NLjQ55ZKM6JCs5ZyL6IGv55uf6YCa55So5Y2A5Z%2Bf6LOH5paZ5bqrY2xkci5wZGY%3D&icon=..pdf)
- Liao, Han-Teng. (2016). Country / Language Selectors: a prototype implementation with consistent collating sequence (p. Poster Sessions). To be presented at the META-FORUM 2016 Beyond Multilingual Europe, Lisbon, Portugal. Retrieved from [http://www.meta-net.eu/events/meta-forum-2016/p](http://www.meta-net.eu/events/meta-forum-2016/postersessions)[ostersessions](http://www.meta-net.eu/events/meta-forum-2016/postersessions)


