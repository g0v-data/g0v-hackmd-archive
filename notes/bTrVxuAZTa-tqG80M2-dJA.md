---
title: "法官是否公正？被告黨派對定罪率的影響"
tags: hackpad
---

# 法官是否公正？被告黨派對定罪率的影響

> [點此觀看原始內容](https://g0v.hackpad.tw/8TfZ6xaVj6I)


git-hub:
[https://github.com/as1986/court-ruling-analysis](https://github.com/as1986/court-ruling-analysis)

## 專案目標

我們想透過判決資料來瞭解資法體系到底公正不公正，具體細分為兩個問題：
1.  被告黨派是否影響法官/審判長的分配？
2.  被告黨派是否影響定罪率？



## Data：

立法委員,縣市議員貪污判決書
99~104年 （92~99年判決書姓名被遮蔽，99年修法公布姓名，但不追溯既往）
##  Todo：

- [ ] Literature Review
- [ ] 抓出99~104年的縣市議員名單及所屬黨派（含增補選）
- [ ] 抓出99~104年中，有以上名單姓名的一審（地方法院）判決書
- [ ] 讀取判決書的罪名、法官、有罪/無罪
- [ ] 整理出Clean Data
(完整版一筆資料：判決書編號、日期、被告、罪名、日期、檢察官、法官、審判長）
（初級版不包含罪名）
- [ ] 寫出完整回歸Model
- [ ] 跑出回歸結果
- [ ] 分析、解讀統計結果
- [ ] 視覺化呈現結果
- [ ] 撰寫給大眾看的文案

## Model




## 判決書例子

邱毅無罪 ：[http://jirs.judicial.gov.tw/FJUD/PrintFJUD03\_0.aspx?jrecno=102%2c易%2c18%2c20130926%2c1&v\_court=TPD+臺灣臺北地方法院&v_sys=M&jyear=102&jcase=易&jno=18&jdate=1020926&jcheck=1](http://jirs.judicial.gov.tw/FJUD/PrintFJUD03_0.aspx?jrecno=102%2c易%2c18%2c20130926%2c1&v_court=TPD+臺灣臺北地方法院&v_sys=M&jyear=102&jcase=易&jno=18&jdate=1020926&jcheck=1)



林益世多罪：
[http://jirs.judicial.gov.tw/FJUD/PrintFJUD03\_0.aspx?jrecno=101%2c金訴%2c47%2c20130430%2c3&v\_court=TPD+臺灣臺北地方法院&v_sys=M&jyear=101&jcase=金訴&jno=47&jdate=1020430&jcheck=3](http://jirs.judicial.gov.tw/FJUD/PrintFJUD03_0.aspx?jrecno=101%2c金訴%2c47%2c20130430%2c3&v_court=TPD+臺灣臺北地方法院&v_sys=M&jyear=101&jcase=金訴&jno=47&jdate=1020430&jcheck=3)

賴素如判決10年:
台北地院法官周玉琦、林惠霞、姚念慈組成的合議庭認定，賴素如犯行明確，痛斥她貪圖不法利益，有害公務員廉潔自持的要求、敗壞官箴，且犯後飾詞卸責，難認有悔意，考量她無前科且主動退還賄款，依公務員對於職務上行為收賄罪判刑10年，褫奪公權5年。
[http://www.cna.com.tw/news/firstnews/201410310334-1.aspx](http://www.cna.com.tw/news/firstnews/201410310334-1.aspx)


判決搜尋:[http://www.lawgle.com.tw/](http://www.lawgle.com.tw/)
律評網:[http://www.pingluweb.com/](http://www.pingluweb.com/#mainJudge)[#mainJudge](https://g0v.hackpad.tw/ep/search/?q=%23mainJudge&via=8TfZ6xaVj6I)
裁判家:免費7天試用, 搜尋判決書很快
[http://www.lawplus.com.tw/](http://www.lawplus.com.tw/#reportDetail?id=TPD,103,%E8%81%B2,1782-b37d0db7-cb35-4f60-aedd-4a53717c4513)[#reportDetail](https://g0v.hackpad.tw/ep/search/?q=%23reportDetail&via=8TfZ6xaVj6I)[?id=TPD,103,%E8%81%B2,1782-b37d0db7-cb35-4f60-aedd-4a53717c4513](http://www.lawplus.com.tw/#reportDetail?id=TPD,103,%E8%81%B2,1782-b37d0db7-cb35-4f60-aedd-4a53717c4513)

有罪抓罪名：犯.\[...\]罪
git-hub:
[https://github.com/as1986/court-ruling-analysis](https://github.com/as1986/court-ruling-analysis)


一些已經有的學術期刊
[http://www.tpsr.tw/sites/tpsr/files/papers/16-1-3.pdf](http://www.tpsr.tw/sites/tpsr/files/papers/16-1-3.pdf)
[http://www.airitilibrary.com/Publication/alDetailedMesh?docid=17269350-201203-201206200032-201206200032-1-40](http://www.airitilibrary.com/Publication/alDetailedMesh?docid=17269350-201203-201206200032-201206200032-1-40)
[http://www.tpsr.tw/sites/tpsr/files/papers/12-2-4.pdf](http://www.tpsr.tw/sites/tpsr/files/papers/12-2-4.pdf)


