---
tags: 0archive, disinfo
---
# 0archive 資料分析發想

## 了解內容農場
- 內容農場的經營分析
    - 有些內容農場專門抄/引用別家媒體的文章，有觀察到一些內容農場，例如[怒吼](https://www.nooho.net/)，抄得速度很快。想要了解他們是怎麼做到的、如何決定要抄哪一些文章？
        - 「內容農場最喜歡轉哪種文章？」
        - 「內容農場的文章都是哪裡來的？」
        - 「內容農場成份分析」

- 內容農場的內容分析
    - 文風分析：有一些內容農場幾乎都是自製文章（例如琦琦、[每日頭條](https://kknews.cc/)），是否可以比較這些內容農場的文章與一般新聞網站的文章，找出內容農場文章的特點
        - Maybe a ML model，加速未來判斷內容農場文章
        - 或是 Exploratory Data Analysis，可以用來教育大眾覺察內容農場文章。
    - 找尋一些已知的假訊息主題，從0archive資料集中看trend，例如針對「武漢肺炎病毒發源自美國」這個主題，找尋「武漢肺炎發源」的資料，看「美國」什麼時候開始多起來

## 針對武漢肺炎的輿情分析（時間區間：2019/12/29-2020/5/16）
- 每週前三大報導主題
    - 建立「歷史上的今天」資料庫
    - 參考資料
        - https://pudding.cool/2018/12/brief-history/
        - https://pudding.cool/2018/12/countries/
- 口罩政策報導演變
- 選定幾個主詞（例如：口罩、藥局、藥師、WHO、紐時廣告等），分析各家媒體、平台針對其主詞的報導傾向/情感分析
    - [snownlp](https://github.com/isnowfy/snownlp)
    - 找主題方法：
        - 利用斷詞後&詞性tagged完後的名詞自己篩選
        - topic modeling
    - 情感分析方法：
        - 利用斷詞後&詞性tagged完後的形容詞
        - 把標題放到人家做好的model跑跑看，看有沒有合用的model
            - https://github.com/Tony607/Chinese_sentiment_analysis
            - ...
- 敦睦艦隊 
    - 時間點在4月下旬，目前資料庫較完整
    - 議題：
        - 國防部、海軍黑箱(?)
        - 公布人數有兩波
- 文章內容比較
    - 選一個有重大事件的一天＋後三四天的文章
    - 大概10個source
    - 比較內文 (edit distance)

## 針對 qiqi 的研究
- 專門分享密訊文章 https://www.facebook.com/%E8%97%8D%E8%89%B2%E6%AD%A3%E7%BE%A9%E5%8A%9B%E9%87%8F-1100522356652838/
## 基礎建設
`tokenized-datasets/publications/<producer_id>-<producer_name>/YYYY-MM-DD.jsonl`
- process
    - remove punctuations & numbers
    - tokenization:
    `jieba`: 
        - speed: very fast: 3 minutes for 3500 ppt titles & texts
        - can use self determined dictionary. Now include [`民國104年常用語詞調查語料統計分析詞頻表-附錄19_多音節詞頻統計`](https://github.com/irvin/moe-common-phrases-of-zhtw/blob/master/2011-2015/csv/%E6%B0%91%E5%9C%8B104%E5%B9%B4%E5%B8%B8%E7%94%A8%E8%AA%9E%E8%A9%9E%E8%AA%BF%E6%9F%A5%E8%AA%9E%E6%96%99%E7%B5%B1%E8%A8%88%E5%88%86%E6%9E%90%E8%A9%9E%E9%A0%BB%E8%A1%A8-%E9%99%84%E9%8C%8419_%E5%A4%9A%E9%9F%B3%E7%AF%80%E8%A9%9E%E9%A0%BB%E7%B5%B1%E8%A8%88.csv)
    - pos tagging
    `ckipnlp`: tagged very well however is slow. 
        - 10 sec for 1 ptt titles+texts
        > [name=wenyi] looking to maybe speed up by multiprocessing??
        
        `jieba` also has pos tagging but the tag comes from a predetermined set of dictionary. It does not have the function of "guessing" the pos itself. 

- 斷詞
    - ckip
    - jieba
    - [分身伐樹](https://g0v.hackmd.io/MdNJToWwTIStjg23Xtl10A?both#%E5%88%86%E8%BA%AB%E4%BC%90%E6%A8%B9)
- 詞性 tagging
    - https://www.moedict.tw/raw/%E8%90%8C
    - [分身伐樹](https://g0v.hackmd.io/MdNJToWwTIStjg23Xtl10A?both#%E5%88%86%E8%BA%AB%E4%BC%90%E6%A8%B9)

## Favorite sources

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_26f9a1e116a93811533ed160f9e20d4c.png)

## Title lengths

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4d49326cfd90facb53452a4bb48481df.jpg)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_60cb54e70039cc44936b817cc207769c.png)

## Trace news upstreams

A few examples:

```json
[{'canonical_url': 'https://www.xuehua.tw/2020/04/02/%e6%96%b0%e5%86%a0%e7%a2%ba%e8%a8%ba%e3%80%8c%e7%99%bc%e7%97%85%e5%89%8d1%e8%87%b33%e5%a4%a9%e3%80%8d%e5%8d%b3%e5%8f%af%e5%82%b3%e6%9f%93%e4%bb%96%e4%ba%ba%ef%bc%81%e3%80%80%e7%be%8e%e5%9c%8b%e7%96%be/',
  'id': '682ae6f7-8257-11ea-8627-f23c92e71bad',
  'urls': ['https://www.ettoday.net/news/20200402/1682465.htm',
   'https://www.ettoday.net/news/20200402/1682455.htm',
   'https://www.ettoday.net/news/20200402/1682452.htm'],
  'published_at': Timestamp('2020-04-02 15:40:13'),
  'title': '新冠確診「發病前1至3天」即可傳染他人！ 美國疾管局最新研究出爐 - 雪花台灣'},
 {'canonical_url': 'https://www.ettoday.net/news/20200402/1682465.htm',
  'id': '58e9f8a6-8257-11ea-8627-f23c92e71bad',
  'urls': [],
  'published_at': Timestamp('2020-04-02 11:30:00'),
  'title': '美單日激增917死創新高 洛杉磯市長「超前部署」：全民外出請戴口罩！ | ETtoday國際 | ETtoday新聞雲'},
 {'canonical_url': 'https://www.ettoday.net/news/20200402/1682455.htm',
  'id': '57ef05dd-8257-11ea-8627-f23c92e71bad',
  'urls': [],
  'published_at': Timestamp('2020-04-02 11:32:00'),
  'title': '身體勇不怕死？東京40%感染者不到40歲...年輕人愛玩成隱藏高風險群 | ETtoday國際 | ETtoday新聞雲'},
 {'canonical_url': 'https://www.ettoday.net/news/20200402/1682452.htm',
  'id': 'c519085a-512f-4c1a-acec-8ba1f3949991',
  'urls': ['https://edition.cnn.com/2020/04/01/asia/coronavirus-mask-messaging-intl-hnk/index.html?fbclid=IwAR27oY1ntDS3A6UKMGjHWBrZQ8D39eDaBJWy86QJgMAf4a-8gY6cEZfxDtk',
   'https://ppt.cc/fl3ONx'],
  'published_at': Timestamp('2020-04-02 11:09:00'),
  'title': '以台灣為例！ CNN：亞洲「戴口罩」防疫也許才是對的 | ETtoday國際 | ETtoday新聞雲'}]
```

```json
[{'canonical_url': 'https://www.storm.mg/article/2551600',
  'id': '418a28fb-c8fc-4afa-97f7-d06e96368391',
  'urls': ['http://www.rfi.fr/tw/%E7%A4%BE%E6%9C%83/20200409-%E4%B8%AD%E5%9C%8B%E6%95%99%E8%82%B2%E9%83%A8-%E6%9A%AB%E5%81%9C%E4%BB%8A%E5%B9%B4%E9%99%B8%E7%94%9F%E8%B5%B4%E5%8F%B0%E5%B0%B1%E8%AE%80%E8%A9%A6%E9%BB%9E%E5%B7%A5%E4%BD%9C',
   'https://www.setn.com/News.aspx?NewsID=725104',
   'https://money.udn.com/money/story/7307/4441503',
   'https://news.tvbs.com.tw/politics/1311256',
   'https://www.bbc.com/zhongwen/trad/chinese-news-52061844',
   'https://www.chinatimes.com/realtimenews/20200417005337-260408?chdtv',
   'https://newtalk.tw/news/view/2020-04-21/395061',
   'https://www.ettoday.net/news/20200411/1689353.htm',
   'https://www.chinatimes.com/realtimenews/20200405003683-260408?chdtv'],
  'published_at': Timestamp('2020-04-23 14:20:01'),
  'title': '蕭旭岑觀點：粉塵瀰漫的兩岸關係-風傳媒'},
 {'canonical_url': 'https://www.setn.com/News.aspx?NewsID=725104',
  'id': '235e93c3-8259-11ea-8627-f23c92e71bad',
  'urls': ['https://bit.ly/37gsay1'],
  'published_at': Timestamp('2020-04-14 15:56:00'),
  'title': '「武漢肺炎」歧視？林書豪3千字喊話：讓我們對抗種族歧視 | 娛樂星聞 | 三立新聞網 SETN.COM'},
 {'canonical_url': 'https://newtalk.tw/news/view/2020-04-21/395061',
  'id': 'd3226961-ac08-4e74-80ea-dbfa97b81d8e',
  'urls': [],
  'published_at': Timestamp('2020-04-21 20:23:17'),
  'title': '追究中國疫情責任 美國保守派智庫挺台美建交 | 國際 | 新頭殼 Newtalk'},
 {'canonical_url': 'https://www.ettoday.net/news/20200411/1689353.htm',
  'id': 'd517adc3-8258-11ea-8627-f23c92e71bad',
  'urls': [],
  'published_at': Timestamp('2020-04-11 20:24:00'),
  'title': '陸官媒罕見措辭「勿謂言之不預」 專家：置之不理恐逼其動武 | ETtoday軍武 | ETtoday新聞雲'}]
```

```json
[{'canonical_url': 'https://www.storm.mg/article/2555911',
  'id': '35777b24-b718-438e-a1ec-e2c6b889877c',
  'urls': ['https://www.chinatimes.com/realtimenews/20200422001427-260407?chdtv',
   'https://www.ptt.cc/bbs/Gossiping/M.1587535692.A.931.html',
   'https://www.upmedia.mg/news_info.php?SerialNo=85923',
   'https://newtalk.tw/news/view/2020-04-22/395362',
   'https://udn.com/news/story/121072/4511486'],
  'published_at': Timestamp('2020-04-24 14:40:01'),
  'title': '汪葛雷觀點：國防部長保蔡英文不保國軍，良心何在？-風傳媒'},
 {'canonical_url': 'https://www.ptt.cc/bbs/Gossiping/M.1587535692.A.931.html',
  'id': '293a8425-de3f-4cb2-8494-51118123f78f',
  'urls': [],
  'published_at': Timestamp('2020-04-22 22:08:10'),
  'title': '[問卦] 敦睦艦支隊長與委員對話逐字稿'},
 {'canonical_url': 'https://newtalk.tw/news/view/2020-04-22/395362',
  'id': '33937f60-1276-4a8d-899b-40653ec37d1c',
  'urls': [],
  'published_at': Timestamp('2020-04-22 12:06:21'),
  'title': '敦睦艦隊出航 蔡英文：國防部已做了決定 總統就該尊重 | 政治 | 新頭殼 Newtalk'},
 {'canonical_url': 'https://udn.com/news/story/121072/4511486',
  'id': '3c22dc63-14f2-4403-a567-08803d0c4991',
  'urls': [],
  'published_at': Timestamp('2020-04-22 19:05:09'),
  'title': '吳斯懷批「總統尊重」是外行話 調閱逐字稿就知蔡英文拍板 | 海軍艦隊爆疫情 | 要聞 | 聯合新聞網'}]
```

## 肺炎名稱使用

### by site across time
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b8bb7000c8d4fc2d0f4db7f21140b395.jpg)
>[name=wenyi]
>這其實滿有趣的，中時在二月的時候仍有1/4文章是使用武漢肺炎，直到三月才變成新冠肺炎，直得深入看一下二月的報導是不是吻合世界衛生組織宣布正名的時程。(其他的新聞媒體的文章比較完整後也可以做個比較)
>"一個多月前，世衛2月12日將新冠肺炎命名為「COVID-19」，並強調命名時不會特定指向某個地理位置、任何動物、人類個體或群體。台灣政府同一天稱，因法定傳染病名稱「嚴重特殊傳染性肺炎」不好記，故可簡稱「武漢肺炎」。
3月19日，蔡英文在官方臉書發文時也稱「武漢肺炎」。她寫道，將針對「武漢肺炎」疫情情勢發表談話。
因此，至今仍有許多台灣媒體以「武漢肺炎」稱呼新冠病毒引發的肺炎。至於中國媒體，在疫情剛爆發時也都稱「武漢肺炎」，但在世衛正式命名後，已改稱「新冠肺炎」。" (from [bbc](https://www.bbc.com/zhongwen/trad/chinese-news-51958854))

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_56e58e6bac86e9626724d0a8cdc6949d.jpg)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e7eee5510f76c7355a53bfe347eea1e9.jpg)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9b10fa7587a3ccdcce2ed508e38a0479.jpg)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f1281782e4c92add053b036be59a4b06.jpg)


### in 2020-04 across site
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fe481d5137b2fde356b8b5b429ba4ce5.jpg)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3edffe455ba9ac745cbbd8a1fc3694eb.jpg)
>[name=wenyi] 聯合報也太愛報導肺炎......
>[name=pm5] XD
### 聯合報轉發中央社文章，再改肺炎名字歷程
>[name=wenyi] 因為發現udn四月的文章標題中仍有~40篇是使用武漢肺炎，所以好奇去看了一下是哪些文章，發現都是轉發中央社的，然後大部分都在幾天後將標題改成新冠肺炎。下面列兩個當參考

中央社新聞連結：https://www.cna.com.tw/news/aopl/202004010462.aspx
聯合新聞連結：https://udn.com/news/story/6809/4462687
> [name=wenyi] Note: 中央社的published_at 應該是 04-01 (from website)，不知為何published_at parsed出來是 04/02。但是由聯合新聞的文章可以看出本篇文章是聯合取自中央社。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_aaf8ec43e0321e13f21b3c29209aa941.png)


中央社連結：https://www.cna.com.tw/news/aopl/202004090011.aspx
聯合新聞連結：https://udn.com/news/story/120944/4478478
>[name=wenyi] 這篇文章很有趣:聯合新聞改了標題但內文沒改XD p.s. 這篇中央社有在scraper db裡面但目前還沒出現在公開資料的jsonl中，所以下面的表格沒有列出來。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ef59df0bf1cbff09d2548d0a171f1b94.png)

## 媒體對於「口罩」的報導sentiment
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_616a54b561c7a39878ee05c8a8fb8515.jpg)
這是用`snownlp`做的，他非常不準所以這就當示意圖看看（分數越高越正面）...`snownlp`是用商品review train出來的，但是可以自己提供training set 去重新訓練模型，如果有比較適合我們使用case的dataset值得來試試看 （或是開新的分身伐樹來做）。![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_bbde2e09550a10c64d1754aaf53ae8a4.png)

## 敦睦艦隊內容互相引用
https://observablehq.com/@andrea-w-wang/arc-diagram

## keywords

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_295e89ca752a41cd0b9c226b0fad1e29.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7986083991311ef92d59c9f660ac36f0.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a363ea2df3895d0d9bf42f92c07d8aa7.png)

## PTT 使用者

### 針對政黑版 2019/11-2020/2 使用者發文的來源 IP 分析

進行中 ->> https://gist.github.com/pm5/05b990c02e15a1adf89d4c3a6bfd57db

用社交網絡分析：

1. $G$ 為包含所有發文過的使用者為 node 的 graph。
    - Number of nodes: 4986
2. 每位使用者 $i$ 在這段期間使用過的來源 IP 為 $S_i$。 
3. 如果 $S_i \cap S_j\ne\emptyset$ 則 $(i, j)\in G$。
    - Number of edges: 542
4. Degree distribution 表示使用者之間共用來源 IP 的現象有多少，其平均值可以做為分析的 baseline。
    - Average degree:   0.2174
    - degree == 0 的使用者（從未與人共用 IP）有 4275 位
5. Clustering coefficient 表示使用者之間的群聚現象；使用者 $i$ 的 clustering coefficient 高，表示 $i$ 鄰居之間彼此相連的比例較高。換句話說，與 $i$ 共用過來源 IP 的使用者，彼此之間也共用過 IP 的比例較高。這樣可以找出一小群彼此之間頻繁共用來源 IP 的使用者帳號。

用使用頻率分析：

1. 找出被很多使用者用過的 IP。
2. 列出所有透過這個 IP 發文的記錄。
3. 找出多位使用者交錯使用這個 IP 發文的情形。
4. 對照一下 IP 資料庫；有時候這是因為 IP 屬於單位共用，例如大學無線網路的 IP。