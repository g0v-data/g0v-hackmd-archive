---
title: "課綱正反意見表列"
tags: hackpad
---

# 課綱正反意見表列

> [點此觀看原始內容](https://g0v.hackpad.tw/LUXl1KVH4ys)

### 進度

- github 比較版 v1 己出爐：
    [https://github.com/lydian/tw\_curriculum/compare/curriculum\_101...curriculum_104](https://github.com/lydian/tw_curriculum/compare/curriculum_101...curriculum_104)
- json檔 程式轉檔完成，但仍需手工調整:
    - [https://github.com/lydian/tw\_curriculum/blob/master/compare\_history\_101\_104/history\_101\_book\_1history\_104\_book\_1.json](https://github.com/lydian/tw_curriculum/blob/master/compare_history_101_104/history_101_book_1history_104_book_1.json)
    - [https://github.com/lydian/tw\_curriculum/blob/master/compare\_history\_101\_104/history\_101\_book\_2history\_104\_book\_2.json](https://github.com/lydian/tw_curriculum/blob/master/compare_history_101_104/history_101_book_2history_104_book_2.json)
    - [https://github.com/lydian/tw\_curriculum/blob/master/compare\_history\_101\_104/history\_101\_book\_3history\_104\_book\_3.json](https://github.com/lydian/tw_curriculum/blob/master/compare_history_101_104/history_101_book_3history_104_book_3.json)

### 動機

    近日課綱爭議，網路上卻常看到斷章取義要來支持/反對課綱調整的文章，目前看到最完整的比較當屬這篇: [https://alberttzeng.wordpress.com/2014/01/29/history\_curriculum\_dispute/](https://alberttzeng.wordpress.com/2014/01/29/history_curriculum_dispute/) ，然而可惜的是，這只是個人blog，所以大多數分享的人都只會看到這篇blog的想法，可是其實在PTT上或是其他地方，都有不少根據這個比較而做的分析，卻因此而無法輕易讓人看到，希望能有一個統一的地方，列出課綱的差異，並且根據差異讓大家可以自由發表評論。

### 需求

1.  比較不同課綱差異
2.  讓大家可以留下評論，或至少正反兩方的意見。

### 可行作法

- github 的code review功能剛好可以滿足我們的需求，所以我建議可以把課綱轉成文字檔，利用不同的branch 表示不同年份的課綱，例如：[lydian/](https://github.com/lydian/tw_curriculum/pull/2)[tw\_curriculutw\_curriculumm](https://github.com/lydian/tw_curriculum/pull/2/files)[#2](https://github.com/lydian/tw_curriculum/pull/2)
    - 優點：有comment 功能
    - 缺點：一般人可能不會操作（囧）而且diff 太難懂
- 或是利用法條系統　[http://billab.io/tipo/copyright-reform-act-2014](http://billab.io/tipo/copyright-reform-act-2014)
    - 優點：界面清爽易讀
    - 缺點：尚無comment 功能（？）

> 我覺得「列出課綱差異」與「正反意見並陳」兩者不一定要放在同一個界面。
> [name=Johnson L]

> 以課綱爭議來說，主要的爭點除了跟內容真正相關的歷史解讀歧義之外，其他有公文施壓、名單與會議記錄不公開、修改課綱的組織不限於課發會等等與課綱差異本身無關的正反意見。或許比較合適的方式是，課綱差異使用 [billab.io](http://billab.io/tipo/copyright-reform-act-2014) 呈現，而正反意見則用[協作式比較表](http://hacktabl.org/fepz)讓大家更新，兩者分開但可以互相用超連結連在一起這樣。
> [name=Johnson L]


### 注意事項

1.  課綱比較為表格，需轉換成文字
> 建議先轉成簡單的 markdown 有單元跟標題 到時候比較容易切分段，也比較容易轉換成 billab 用的 json
> [name=Liang K]

2.  不同版本間轉換格式需一致，才能方便比較
3.  github 比較如有不同的部份，會加深整個句子，不知道有沒有辦法換成以字元方式顯示

### 原始資料

- [1999 課綱（88課綱）](http://www.hwashing.com.tw/teacher/teacher01_001.asp)
- [2006 暫行綱要（95暫綱）](https://sites.google.com/a/cyhs.tc.edu.tw/whole/95whole)
- [2008 年以後的四版課程綱要](http://edu.law.moe.gov.tw/LawContentHistory.aspx?id=GL000364&KeyWord=)
    - 2012（101課綱）
- [2014 修正](http://edu.law.moe.gov.tw/NewsContent.aspx?id=2722)

### Github

    repo: [https://github.com/lydian/tw_curriculum](https://github.com/lydian/tw_curriculum)

### 補充資料

- 2010 [高中課程99課綱與95暫綱之分析 李坤崇](http://www3.ylsh.chc.edu.tw/%E5%9C%96%E6%9B%B8%E9%A4%A8/%E5%AF%A6%E6%96%BD%E8%A8%88%E7%95%AB%E5%8F%8A%E8%BE%A6%E6%B3%95/99%E8%AA%B2%E7%B6%B1/%E5%BF%85%E4%BF%AE/p0000001.pdf)
- 2015/7/24 聯合報 課綱內容爭議列表
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_cfbe8d18a027544e1d8061818e8cf369)

