---
title: "演算法歧視案例"
tags: hackpad
---

# 演算法歧視案例

> [點此觀看原始內容](https://g0v.hackpad.tw/WI4KnMaK2pg)


### 壹些評論蒐集


- 也許演算法沒問題但技術坐實而且合理化了原本就存在的歧視
- data input/output  encoding / decoding issue.
    - 只有当训练数据足够优质的时候，这些预测程序才足够有效；而训练数据则有着很复杂的历史背景。


### 面像歧視


- [http://www.chinatimes.com/newspapers/20170510000758-260309](http://www.chinatimes.com/newspapers/20170510000758-260309)
- 中國上海交通大學研究人員吳曉琳（音譯，以下簡稱吳）和張希（音譯，以下簡稱張）使用了一個有 1856 張面部照片的資料庫訓練機器學習算法，其中 730 人是罪犯，另外 1126 人不是。 在分析了 90％ 的圖片後，AI 能夠正確地識別剩餘 10％ 照片中的罪犯。
- 該算法將具體的面部特徵與罪犯相關聯。例如罪犯的眼角、嘴唇曲率和鼻尖更有可能存在特定的空間關係。吳說，他也認同如果一個人有這些特徵，不能說這個人更可能是罪犯。 吳同時發現罪犯的面孔差異較大，而非罪犯往往具有相似的面部特徵。
- 吳繼續使用以前沒有看過的不同的照片來測試算法，發現它多半情況下可以正確識別罪犯。研究人員試圖通過只使用沒有面部毛髮和疤痕的中國青年或中年男子的面部圖片進行訓練和測試其算法來避免偏差。
- 吳說：「我本來想證明面相學是錯的」，他指的是基於面部特徵評估性格的有數百年歷史的偽科學。 「結果卻令我們大吃一驚。」雖然這項研究似乎可以驗證了面相學的某些方面，但吳承認，使用這種技術來識別罪犯將是「瘋狂的」，沒有計劃在執法機關中應用。
- Wilson 說：「基於偏見在刑事司法系統中的表現，相同的數據和工具可以用來更好地了解（人的）偏見。 而不是教一台電腦來重現這些人類的偏見。」
- 原文網址：[https://read01.com/04PxBE.html](https://read01.com/04PxBE.html)

### 種族歧視


- [Artificial Intelligence’s White Guy Problem](https://www.nytimes.com/2016/06/26/opinion/sunday/artificial-intelligences-white-guy-problem.html?emc=edit_tu_20160628&nl=bits&nlid=74307160&ref=technology&te=1&_r=0)
    - Google’s photo app, which applies automatic labels to pictures in digital photo albums, was [classifying images](http://blogs.wsj.com/digits/2015/07/01/google-mistakenly-tags-black-people-as-gorillas-showing-limits-of-algorithms/) of black people as gorillas.
    - [Hewlett-Packard](http://www.nytimes.com/topic/company/hewlettpackard-company?inline=nyt-org)’s web camera software, which had [difficulty recognizing](http://www.wired.com/2009/12/hp-notebooks-racist/) people with dark skin tones.
    - Nikon’s camera software, which misread images of Asian people [as blinking](http://gizmodo.com/5256650/camera-misses-the-mark-on-racial-sensitivity)
    - [machine-bias-risk-assessments-in-criminal-sentencing](https://www.propublica.org/article/machine-bias-risk-assessments-in-criminal-sentencing)
        - There’s software used across the country to predict future criminals. And it’s biased against blacks.
        - The reason those predictions are so skewed is still unknown, because the company responsible for these algorithms keeps its formulas secret .
        - Northpointe’s core product is a set of scores derived from [137 questions](https://www.documentcloud.org/documents/2702103-Sample-Risk-Assessment-COMPAS-CORE.html) that are either answered by defendants or pulled from criminal records.
- [QUESTIONING THE FAIRNESS OF TARGETING ADS ONLINE](https://www.cmu.edu/news/stories/archives/2015/july/online-ads-research.html)
    - [The study](http://www.degruyter.com/view/j/popets.2015.1.issue-1/popets-2015-0007/popets-2015-0007.xml) of Google ads, using a CMU-developed tool called [AdFisher that runs experiments with simulated user profiles](http://www.cs.cmu.edu/~mtschant/ife/).
    - How would a woman know to apply for a job she never saw advertised? How might a black community learn that it were being overpoliced by software?
    - The male users were shown the high-paying job ads about 1,800 times, compared to female users who saw those ads about 300 times,
- [Amazon Doesn’t Consider the Race of Its Customers. Should It?](https://www.bloomberg.com/graphics/2016-amazon-same-day/)
    - Rasberry pays the same $99 Prime membership fee as people who live in the city’s majority-white neighborhoods, but she doesn’t get the same benefits.
    - Amazon won’t reveal specifics about how it decides its same-day delivery areas.
    - As soon as you try to represent something as complex as a neighborhood with a spreadsheet based on a few variables, you’ve made some generalizations and assumptions that may not be true, and they may not affect all people equally

### 性別歧視

- [How Vector Space Mathematics Reveals the Hidden Sexism in Language](https://www.technologyreview.com/s/602025/how-vector-space-mathematics-reveals-the-hidden-sexism-in-language/)
- [Semantics derived automatically from language corpora contain human-like biases](http://science.sciencemag.org/content/356/6334/183.full)

### 技術性解法相關論文

- [Equality of Opportunity in Supervised Learning](https://arxiv.org/abs/1610.02413)
    - A case study of FICO credit scores
    - A naïve approach might require that the algorithm should ignore all protected attributes such as race, color, religion, gender, disability, or family status. However, this idea of “fairness through unawareness” is ineffective due to the existence of redundant encodings, ways of predicting protected attributes from other features
    - consider non-discrimination from the perspective of supervised learning, where the goal is to predict a true outcome Y from features X based on labeled training data, while ensuring they are “non-discriminatory” with respect to a specified protected attribute A.
    - 新聞: [https://kknews.cc/tech/xogl3r.html](https://kknews.cc/tech/xogl3r.html)
        - 將敏感屬性的集合從數據中移除，讓它無法帶來影響。但是這是一種「通過無知實現公平」的想法，而且往往會因為「冗餘編碼（redundant encodings）」的存在而失敗。
        - 「人口平價（demographic parity）」，該方法是要求預測必須與某特定敏感屬性不相關。直觀上這聽起來是我們想要的，但輸出本身往往是與敏感屬性聯合相關的。比如說，心臟衰竭發病基本上往往在男性中比在女性中更常見。當預測這樣一種醫療狀況時，阻止預測結果和群體成員之間所有的相關性既不現實，也不是我們想要的。
        - 一個有資格得到一個期望結果的個體應該在這一結果上具有同等地被正確分類的機會。在我們的金融貸款的例子中，這意味著真正會償還貸款的人的「低風險」預測率不應該依賴於種族或性別等敏感屬性。我們將這一原理稱為監督學習中的機會均等（equality of opportunity in supervised learning）。

### 非技術性解法相關論文


- 因演算法歧視造成不可復原傷害的賠償
- 歐盟2018 European Union regulations on algorithmic decision-making and a "right to explanation" [https://www.wikiwand.com/en/General\_Data\_Protection_Regulation](https://www.wikiwand.com/en/General_Data_Protection_Regulation)
- [https://blog.acolyer.org/2017/01/31/european-union-regulations-on-algorithmic-decision-making-and-a-right-to-explanation/](https://blog.acolyer.org/2017/01/31/european-union-regulations-on-algorithmic-decision-making-and-a-right-to-explanation/)

### 解決方向


- 公平性
- 苛責性
    - 誰該負責
        - 資料蒐集者?
        - 資料倉儲?
        - Data Scientist?
        - 產品整合者?
        - 使用者?
            - 將產品用在ML演算法者沒考慮到的應用造成 side effect
- 透明性
    - domain expert  檢驗
    - 問題: 商業公司不願意公佈演算法
    - 解法: 共識演算法?

### 相關書籍

- [大數據的傲慢與偏見](https://victranslates.blogspot.tw/2017/06/blog-post.html)
- [The Machine Question](https://mitpress.mit.edu/books/machine-question)



### 檢驗方法

- [https://read01.com/nONz.html](https://read01.com/nONz.html)
- 監督學習是否帶有太強烈的假設
- [https://www.ajlunited.org/](https://www.ajlunited.org/)
- alg watch
### Related Conference

- [http://www.fatml.org/](http://www.fatml.org/)





