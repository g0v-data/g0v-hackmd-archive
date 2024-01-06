---
tags: 0archive, disinfo
---
# 0archive news websites crawling analysis

## 105 聯合
### discover
- 2020/3/17
    - no more discoveries since 2020-2-6
    - observed that `https://udn.com` redirects to `https://udn.com/news/index`. After changing the website url to `https://udn.com/news/index`, we started to see new articles
    - I think some of the raw_data does not have the body rendered.
- 2020/3/18 抓到 2091 則
- 2020/03/22 網頁上應該有 ~430 則左右，spider抓了 849 則
- [x] remove older duplicates

### raw_data

## 101 東森
### discover
- 2020/3/17
    - update articles and following rules
- 2020/3/18 抓到 748 則
- :star: 2020/3/19 變157則！！
    - 實際數了一下即時新聞中3/19的真的只有~150則左右

### raw_data:
ok

## 107 中央社
### discover
- 2020/3/18 總共524則
- Observations:
    - url 的後面數字是日期+序號，序號是照順序排的
        - 2020/3/19 第一則 是002 好，不確定之前是否有新聞被刪除`https://www.cna.com.tw/news/firstnews/202003190002.aspx`
        - 2020/3/18 最後一則 `https://www.cna.com.tw/news/aopl/202003180503.aspx`
    - 推估一天有~500則
    - 同一篇新聞會有不同url，但序號相同。(序號是文章的unique identifier?)
        - e.g. 土耳其武漢肺炎疫情三級跳 他們超愛洗手就是不戴口罩:
            - `https://www.cna.com.tw/news/firstnews/202003180267.aspx`
            - `https://www.cna.com.tw/news/aopl/202003180267.aspx`
        - so 會重複抓
            - 那有沒有少抓啊？？？總數看起來和每新文章數差不多
- 2020/3/22
    - 網頁上有247則，看來每日新聞數變動大（可能因為是週日的關係）？
    - spider抓到253則新文章

### raw_data:
ok

## 104 蘋果即時
### discover
- 2020/3/18 總共抓647則
- 2020/3/18 網站上總共有564則
- [x] 蘋果即時在list上面的url點進去都會302到另外一個url，applications.py 的 url搜尋應該要同時搜尋redirect_to的欄位
- [ ] 同樣有像udn news & chinatimes url後面會加inconsequential parameters的狀況, e.g. `https://tw.appledaily.com/international/realtime/20191213/1676663?itm_source=twad_web&itm_medium=internal&itm_campaign=twad_marquee&itm_content=marquee`，已經把appledaily加入StandardizePipeline，目前正在清db中的duplicate article & snapshot entries。

### raw_data:
- 若是公開文章有完整內容
- 大部分只有Meta中的部分內容
- [x] 需要登入壹會員

## 102 ETtoday
- 2020/3/18 總共抓924則
- 算不太出來一天有幾則新聞...

### raw_data:
ok

## 106 自由時報

### discover
- 2020/3/18 總共抓942則
- 一天breakingnews預估有500左右，paper不太確定
    - paper e.g.
        -  `https://news.ltn.com.tw/news/Taitung/paper/1359500`
        - `https://news.ltn.com.tw/news/society/paper/1359507`

### raw_data:
ok

## 100 中國時報
### discover
- 2020/3/18 總共抓 991 則
- tracking code inside url `?ctrack`, generating many duplicates article entries. 
    - 在最新discovered的`1200`則articles中大約有`470`則為重複的article entries (`40%`)
- [x] remove older duplicates
### raw_data:
有抓到完整html，而且內文完整的在meta的 `<meta property="og:description" itemprop="description" >`中

## 108 芋傳媒
### discover
- [ ] 每天spider抓到的新文章數在350 - 500 之間，但會有duplication，例如以下這兩個在db中為不同article 
    - https://living.taronews.tw/2020/03/22/642737/
    - https://taronews.tw/2020/03/22/642737/

### raw_data:
ok~ 
文章中多有新聞來源 （都是中央社...)

---
## 789 雪花新聞