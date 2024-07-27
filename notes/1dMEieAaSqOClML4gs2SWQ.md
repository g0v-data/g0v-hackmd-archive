# 能源轉型模擬器討論共筆

# 想做的事情
- 建立模型
    - en-roads 是 prototype
        - vensim
            - for system dynamics model
        - 透過模型，觀察每個變量之間的關係
    - 第一個模型：知道台灣的碳排對全球氣候有什麼正面貢獻；如果台灣淨零對全球氣候會有幫助嗎
    - 第二個模型：把 en-roads 模型變小（降階），拿來作為台灣的供電分析模型
        - 各種不同行業的用電
        - 把人口等變量納入
        - 可能是五年之內的模型
        - 或許也能從 2025 非核家園 - 2050 淨零碳排之間如何達到碳中和目標
    - 第三個模型：V to G
        - EV to grid 從電車的儲能回送到電網
        - 反之亦然，綠電產生多餘電力的時候就可以把能源送到電車上儲存
- 報名 2024 總統盃黑客松
    - 可以取得經濟部能源署、環境部、台電公司等對於上述的原始資料
- 能源署資料 API: https://www.esist.org.tw/database/api
- 台電長期用電規劃: https://www.taipower.com.tw/tc/page.aspx?mid=212&cid=122&cchk=260a432c-fc0e-47e0-a90e-2bc0cc52cb61

## en-roads
- https://github.com/climateinteractive/SDEverywhere
- https://www.climateinteractive.org/en-roads/

## 2050 calculators
- 相關連結
    - [程式碼](https://github.com/ImperialCollegeLondon/Template2050Calculator)
    - [介紹網站](https://www.imperial.ac.uk/2050-calculator/news/)
- 過去研究資料
    - [2014工研院投影片 - 2050 calculators](https://www.digitimes.com.tw/seminar/itri_20150210/pdf/0211_final/0211-Q.pdf)
    - [中研院永續科學發展中心有在使用 2050 calculatos 2020-10-07](https://ddpp.ntu.edu.tw/in-depth-coverage/113-2017-04-14-02-50-37/2018-03-16-03-33-25/1511-2021-sub-2b.html)
    - [臺灣2050淨零排放路徑及策略總說明 2022-03-30](https://ws.ndc.gov.tw/Download.ashx?u=LzAwMS9hZG1pbmlzdHJhdG9yLzEwL3JlbGZpbGUvMC8xNTA0MC82Yzg4MWJlZC04ZDBlLTRhZmEtOGY4ZC02NTI5ZTE1MjViMTQucGRm&n=6Ie654GjMjA1MOa3qOmbtuaOkuaUvui3r%2bW%2bkeWPiuetlueVpee4veiqquaYjl%2fnsKHloLEucGRm&icon=..pdf)
- 後續情況
    - [評估淨零路徑的模型及其背後所需的社會科學](https://www.taiwansustainabilityhub.org/post/%E8%A9%95%E4%BC%B0%E6%B7%A8%E9%9B%B6%E8%B7%AF%E5%BE%91%E7%9A%84%E6%A8%A1%E5%9E%8B%E5%8F%8A%E5%85%B6%E8%83%8C%E5%BE%8C%E6%89%80%E9%9C%80%E7%9A%84%E7%A4%BE%E6%9C%83%E7%A7%91%E5%AD%B8#viewer-9q2mu
    
- > [name=ronnywang] 當初工研院和中研院都有搜集過類似的資料
- > [name=]