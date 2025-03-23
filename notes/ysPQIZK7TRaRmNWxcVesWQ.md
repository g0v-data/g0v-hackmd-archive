---
tags: 3166, iso3166, iso-3166, iso, country list, 國家
---

# uso-3166 - Website with ISO-3166 alternatives

> 嘘-3166

###### tags: iso3166, iso-3166

## 專案簡介

### 緣由

- 20XX 年中國小粉紅迫使機場修改國家列表事件

### 要解決的問題

ISO-3166 is a go-to option when developers want a list of countries.

Actually, There are much more alternatives that deserves more recognition and adoption.

### 預定使用者

- 做網站時在網路上找「國家列表」的人，應該要得到這些資訊
- For advocates that want to nudge their favourite site to get rid of "province of china" from "Taiwan" in its country list, this site can be used as a backup resource when they demand a change.

### 預定功能

最終成果應為一個網站。

核心功能是「提供 iso3166 的 alternative」。Any criticisms to ISO-3166 should come *after* the suggested alternatives. This should Provides a more pragmatic way to raise adoption of other langage lists

#### 第一階段：Landing page = list of language lists

##### 選項區 

> 「Want a language list? Try: (Dropdown)」

Dropdown items:
- [Unicode CLDR](https://cldr.unicode.org/)
- [歐盟](https://publications.europa.eu/code/en/en-5000500.htm)
- [FIPS 10-4 (GENC)](https://en.wikipedia.org/wiki/List_of_FIPS_country_codes)
- [ICANN ccTLD](https://icannwiki.org/Country_code_top-level_domain)
- ...TBA...
- 其他非地理的列表：語言 locale、幣別 currency

每個選項都整理，附上「好處」：
- Full name list 35B smaller than ISO-3166
- takes 18% less (8 em width) of the precious screen space
- Covers 3 more country than ISO-3166
- Ready-made packages for Node.JS / Python / PHP / ... etc
- Adopted by <有名的 distro / 組織 or 公司>

##### Compatibility table 區

side by side 比較兩個 language list：
一邊預設是 ISO-3166, 另一邊是上面 dropdown 選的東西（可以再換）
比較
- 2 letter shortcode, 3 letter shortcode
- full name of countries
- list of countries

預設折疊相同的部分（但列出相同的項目數量與所佔百分比）

##### Want to stick to ISO-3166?

> 提供 patch ISO-3166 的做法

You should change. (連到第二階段)
But if you cannot, consider:
- 增加某些 items (列舉如科索沃)
- 修改某些 items
    - "Taiwan" only --> 19 Bytes smaller!
    - "Taiwan, Republic of China" --> Only change 6 bytes!
- TBA

#### 第二階段：Evidence-based criticisms and controversies to ISO-3166

> 網站的「說明」頁面可在第一階段完工之後再來進行。

「說明」頁面則表列 ISO-3166 的缺點，但立論應根基於 ISO 開會記錄等。

from user's perspective:
- weird names
- outdated, missing countries

from inclusion's perspective:
- missing countries

from political perspective:
- UN interpretation
- controversy of ISO coining the standard
- ISO 3166 used by Chinese netizens to safeguard "territorial integrity of China" https://www.globaltimes.cn/content/1162205.shtml , https://github.com/peeringdb/peeringdb/issues/552  https://www.theguardian.com/world/2018/jun/19/japanese-airlines-rename-taiwan-as-china-taiwan-on-websites  https://time.com/5348666/airlines-websites-taiwan-china/
- https://clkao.substack.com/p/how-dbt-labs-demonstrates-its-inclusive

##### Optional - Call to action 區塊

:::danger
這可能會對其他開源專案造成困擾，需謹慎規劃。
:::

1. scan open source softwares that uses iso3166 list / scan airline website for country names / scan booking website for country names
2. if you are the user of a software, try submitting pull requests converting iso3166 to one of the alternative / if you are a heavy user of the website, send them the email


### 現有類似專案 / 相關專案


#### github.com/iso3166
- https://iso3166.github.io/
- https://github.com/iso3166/

Sort of like an extension to the site above.


#### 150-Elbb

https://github.com/150/Elbb

Leetspeak of ISO-3166

#### GENC names

ISO 3166-1 country list names considered harmful. use GENC names
https://g0v.hackmd.io/MTJiGC49Qd6uQMKVM-2Zdw?view


### 授權方式

- 文字 CC-BY USO-3166 project
- 程式碼 MIT

### 使用資料

- Language lists
- ISO-3166 維護署 https://www.iso.org/iso-3166-country-codes.html

### 專案目前狀態

構想階段，未有實作或雛形

## 徵求協作者

還沒 XD


## 實作細節

Should be a statically generated site hosted on github pages.

Can use gatsby or next.js SSG or other similar tech.

No repos yet.


## 成果展示

N/A
