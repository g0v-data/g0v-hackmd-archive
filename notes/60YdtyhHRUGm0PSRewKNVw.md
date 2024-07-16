---
tags: energy
---

# 核電翻譯機  (Nuclear Data)

> [點此觀看原始內容](https://g0v.hackpad.tw/8sYMW30othK)

- 發起人/拋磚人：蔡雅瀅
- 狀態：  概念發想
- 授權方式：[CC:BY-SA](http://creativecommons.org/licenses/by-sa/3.0/tw/)
- Repository: [https://github.com/g0v/nuclear-data](https://github.com/g0v/nuclear-data)
- 專案簡介：將原能會  [運轉中電廠每日](http://www.aec.gov.tw/controlreport/historydata.html)[管制](http://www.aec.gov.tw/controlreport/historydataview.html?searchdate=2014-02-01)[資](http://www.aec.gov.tw/controlreport/historydata.html)[料（直接改searchdate）](http://www.aec.gov.tw/controlreport/historydata.html)  轉譯成容易理解的圖表  [簡報](http://goo.gl/cxXji2)
    台電機組發電量 , 每10分鐘更新 [http://g0v-data.github.io/mirror/](http://g0v-data.github.io/mirror/)
> gugod++
> [name=nchild]

- 使用資料：原能會網站的公開資訊

## 工作目標

1.  目的:
    1.  讓大家了解一年中有多少日期是有反應爐運轉異常。
    2.  了解說有多少核電廠停機時，_台灣仍能正常供電_。
> 台灣仍能正常供電要再找其他資料。
> [name=Chang S]

> 比較台灣發電量, 和 耗電量, 就能證明這一點!
> [name=Ginger C]

        1.  重要資訊:
            1.  熱功率: 百分比
            2.  異常停機、檢修停機、異常降載、檢修降載、颱風等狀況，內容詳細說明。
                1.  電廠、機組
                2.  處理: 降載、停機
                3.  原因: 異常、檢修、颱風
> 穩定運轉是可忽略的。
> [name=Chang S]

            3.  呈現的方式 : 用年曆表示一整年的時間資訊。
2.  頁面上的功能 :
    - [x] 行事曆+折線圖，要畫Wireframe 看下方網站界面項目
    1.  檢索 : 以幾號廠為區分、以事件為區分，如最長停機時間 ( 事件 )
    2.  連結 : 連到原能會頁面。
        - [ ]  找資料來源跟整理格式。
3.  條列反應爐「連續停機日數」/ 排序
4.  條列多部反應爐「同時停機、降載日數」/ 排序
5.  圖像化停機、降載事由（如：大修、故障、颱風、魚群）
- [ ] 提取所有文字內容，成為容易使用的文字或excel檔
> 有人可以先幫忙完成這部分嗎？會涉及相關關鍵字選擇或其他架構性的問題(大致讀完歷年資料後，找出有意義的脈絡)
> [name=蔡雅瀅]

> 如果是畫mockup可以嗎？就是我上次畫的那些圖, 在精細些
> [name=Ginger C]

> 不是很懂mockup，是折線圖或是行事曆式的圖?我覺得兩種應該都有幫助
> [name=蔡雅瀅]

> 對, 但沒辦法操作, 因為沒有寫code進去, 
> [name=Ginger C]

> 我覺得可以先試看看，大量看資料後，再挑選適合的關建字，比較能做出好的網頁
> [name=蔡雅瀅]

> 原能會的網站似乎很多應該是同樣的事，用不同的用語表達(如跳機和急停)
> [name=蔡雅瀅]

> 好, 我先丟一版給大家討論好了
> [name=Ginger C]

> 感謝  ^  ^
> [name=蔡雅瀅]


6.  側錄並比對與[核能電廠運轉即時資訊](http://gamma.aec.gov.tw/spds/) ([data](http://gamma.aec.gov.tw/spds/bottom.asp))有無差異（如：運轉即時資訊有停機或降載，事後公布的每日管制資訊卻未揭露）
7.  視覺化使用介面（參考下方 comment）
    1.  一年份的俯瞰圖
    2.  意外停機與維修停機區別開來
    3.  呈現(特殊)降載發電
    4.  可點進去看細節\- 可以看到意外的狀況
    5.  檢索排序
    6.  最長停機多久？
        答：97天(101.03.16 -- 101.06.20) \[推測的答案，不確定是否有更長的\]
        最多幾部機組同時停機？
        答：6部(88.07.30)

```
 最多幾部機組停機

 _\- 目前有六部（颱風）, 目前停機機組？ 曾經停幾最多組_
```
    1.  我們有沒有被騙？(原能會資料正確？)
    2.  不同資料來源比對
    3.  側錄網站內容，避免修改（要不要做網站截圖？）
    4.  名詞解釋
1.  核電廠有在做「南電北送」嗎？
2.  倘若發生核災，須撤離之法定範圍，與他國之撤離範圍之比較，撤離之人口數，以及安置成本，社會成本計算




## 夥伴列表

- 徵求夥伴（有興趣直接簽名）：
    NeedsWriter (撰寫基本資訊、報導專案 etc)：蔡雅瀅
    NeedsDesigner (介面設計)：Ginger
    NeedsData (擷取整理資料、資料視覺化)：junsuwhy, Ginger(資料視覺化)
    NeedsTech (程式、架站 etc)： jeffhung (後端, 打雜), MarkWu(前端)
    NeedsProcess (設計作業流程)：
    NeedsTalkingToRealPerson (需要真人溝通協調)：蔡雅瀅

## 工作分類


### 專案管理

- Git on [github](https://github.com/g0v/nuclear-data)
    - [x] Create source repository
    - Join team members
> 建議文案組也申請進來 github 玩玩，一來看看 commit history 了解技術組在做什麼，二來發現 bug (程式裡有問題與預期表現不符的地方) 可以發 issue request。
> [name=Jeff H]

> 感覺非技術人員要發現Bug是十分困難的事，只要發現一個就能解開最高成就了吧~不過也許有類似「名詞解釋錯誤」的Bug。
> [name=Chang S]

        - [x] Shihta
        - [x] psdmac-Mark
        - [x] [tomchentw](https://github.com/tomchentw)
        - [x] junsuwhy
> 還有需要存取 source code 的請在上面加上 checkbox 並標上你的 github id。
> [name=Jeff H]

    - [x] 登記在 [http://hack.g0v.tw/project](http://hack.g0v.tw/project)
### 系統架構

主機架設
    - [ ] VPS環境申裝
    - [ ] DNS申請
    - [ ] Python與Bottle環境設定
    - [ ] 前端web相關需求仍不明確，需要人補充
#### 前端

- 使用技術：AngularJS + NodeJS
#### 後端

- 使用技術：Python + Virtualenv + [Bottle](http://bottlepy.org/)  \+ SQLite3
- API Spec:
```
/api/tai-vs-aec/<start:int>/<end:int>
```
    - start: epoch, include
    - end: epoch, exclude
    - Sample Output
```
{ 'data': [ {'t': 1393082562, 'powersets': [{'planet': u'\\u6838\\u4e00', 'aec': 656.0, 'capacity': 636.0, 'powerset': u'1', 'tai': 627.5}, {'planet': u'\\u6838\\u4e00', 'aec': 636.0, 'capacity': 636.0, 'powerset': u'2', 'tai': 597.7}, {'planet': u'\\u6838\\u4e8c', 'aec': 1028.0, 'capacity': 985.0, 'powerset': u'1', 'tai': 993.3}, {'planet': u'\\u6838\\u4e8c', 'aec': 693.0, 'capacity': 985.0, 'powerset': u'2', 'tai': 664.9}, {'planet': u'\\u6838\\u4e09', 'aec': 980.0, 'capacity': 951.0, 'powerset': u'1', 'tai': 941.5}, {'planet': u'\\u6838\\u4e09', 'aec': 976.0, 'capacity': 951.0, 'powerset': u'2', 'tai': 938.1}]}, ... ] }
```
    - API Real Output:
```
{"data": [{"t": 1393083159, "powersets": [{"planet": "\\u6838\\u4e00", "aec": 657.0, "capacity": 636.0, "powerset": "1", "tai": 628.4}, {"planet": "\\u6838\\u4e00", "aec": 641.0, "capacity": 636.0, "powerset": "2", "tai": 602.4}, {"planet": "\\u6838\\u4e8c", "aec": 1026.0, "capacity": 985.0, "powerset": "1", "tai": 992.0}, {"planet": "\\u6838\\u4e8c", "aec": 693.0, "capacity": 985.0, "powerset": "2", "tai": 666.3}, {"planet": "\\u6838\\u4e09", "aec": 982.0, "capacity": 951.0, "powerset": "1", "tai": 939.2}, {"planet": "\\u6838\\u4e09", "aec": 975.0, "capacity": 951.0, "powerset": "2", "tai": 935.8}]}, {"t": 1393083219, "powersets": [{"planet": "\\u6838\\u4e00", "aec": 658.0, "capacity": 636.0, "powerset": "1", "tai": 628.4}, {"planet": "\\u6838\\u4e00", "aec": 643.0, "capacity": 636.0, "powerset": "2", "tai": 602.4}, {"planet": "\\u6838\\u4e8c", "aec": 1023.0, "capacity": 985.0, "powerset": "1", "tai": 992.0}, {"planet": "\\u6838\\u4e8c", "aec": 698.0, "capacity": 985.0, "powerset": "2", "tai": 666.3}, {"planet": "\\u6838\\u4e09", "aec": 980.0, "capacity": 951.0, "powerset": "1", "tai": 939.2}, {"planet": "\\u6838\\u4e09", "aec": 976.0, "capacity": 951.0, "powerset": "2", "tai": 935.8}]}, {"t": 1393083280, "powersets": [{"planet": "\\u6838\\u4e00", "aec": 655.0, "capacity": 636.0, "powerset": "1", "tai": 628.4}, {"planet": "\\u6838\\u4e00", "aec": 643.0, "capacity": 636.0, "powerset": "2", "tai": 602.4}, {"planet": "\\u6838\\u4e8c", "aec": 1028.0, "capacity": 985.0, "powerset": "1", "tai": 992.0}, {"planet": "\\u6838\\u4e8c", "aec": 700.0, "capacity": 985.0, "powerset": "2", "tai": 666.3}, {"planet": "\\u6838\\u4e09", "aec": 982.0, "capacity": 951.0, "powerset": "1", "tai": 939.2}, {"planet": "\\u6838\\u4e09", "aec": 978.0, "capacity": 951.0, "powerset": "2", "tai": 935.8}]}]}
```
> 想請教 \\u6838\\u4e09 這個怎麼轉中文啊??
> [name=Chang S]

> 還有，取到的就會像上面這個 json 只有三個時間點的資料嗎??
> [name=Chang S]

> See: [JSON and escaping characters](http://stackoverflow.com/questions/4901133/json-and-escaping-characters)
> [name=Jeff H]


### 網站界面

- 設計方向：公正,不帶情緒, 清楚, 明白
- [Desgin for fontend 資料夾 @ Google Drive](https://drive.google.com/?usp=chrome_app#folders/0B7mNkeigw1U1VGUxUmlUVDN2aDQ)
- [折線圖 標注 範例](https://docs.google.com/file/d/0B7mNkeigw1U1VzNkMC1mRE1UYjQ/edit?usp=drive_web)
- [Design Mockup](https://drive.google.com/folderview?id=0B7mNkeigw1U1Rm9aMHA5YzBUelk&usp=sharing)
- 簡單wireframe+功能 [http://g6qeun.axshare.com/](http://g6qeun.axshare.com/#p=page_1)[#p](https://g0v.hackpad.tw/ep/search/?q=%23p&via=8sYMW30othK)[=page_1](http://g6qeun.axshare.com/#p=page_1)
- 篩選器：大修、檢修、跳脫、降載、急停、過熱
- **資料截取**

### 待解釋名詞

- [ ] 負載率：
- [ ] 電量Mew：
- [ ] 大修：
- [ ] 檢修：
- [ ] 跳脫：
- [ ] 降載：
- [ ] 急停：
- [ ] 過熱：
- [ ] 熱功率 :
- [ ] 發電功率 :
- [ ] 意外降載 : 如魚群湧入降載
- [ ] 計劃降載 : 檢修、
> 可能有參考價值的維基頁面 : [核電站](https://zh.wikipedia.org/wiki/%E6%A0%B8%E7%94%B5%E7%AB%99)、[核動力](https://zh.wikipedia.org/wiki/%E6%A0%B8%E5%8B%95%E5%8A%9B#.E7.9B.B8.E5.85.B3.E9.A3.8E.E9.99.A9)，或是我們寫出來之後拿去更新維基
> [name=Chang S]


### 熱門QA


- 最長停機多久？
    答：97天(101.03.16 -- 101.06.20) \[推測的答案，不確定是否有更長的\]
- 最多幾部機組同時停機？
    答：6部(88.07.30)

### 資料來源

官方來源
- [運轉中每日管制資料](http://www.aec.gov.tw/controlreport/historydata.html?searchyear=2012&searchmonth=3&button=%E9%80%81%E5%87%BA)
- [原能會即時資訊](http://gamma.aec.gov.tw/spds/)
- [台電即時資訊(同上內容)](http://www.taipower.com.tw/content/new_info/new_info-b24.aspx?LinkID=7%E5%97%8E?)
- [台電各機組資料，包含非核電廠](http://www.taipower.com.tw/content/new_info/new_info_in.aspx?LinkID=11)
- [核能電廠自動急停次數](http://www.aec.gov.tw/%E8%B3%87%E8%A8%8A%E5%85%AC%E9%96%8B/%E9%96%8B%E6%94%BE%E8%B3%87%E6%96%99-Open-Data/14.%E6%A0%B8%E8%83%BD%E9%9B%BB%E5%BB%A0%E8%87%AA%E5%8B%95%E6%80%A5%E5%81%9C%E6%AC%A1%E6%95%B8--219_2015_2217.html)
- [核安管制紅綠燈績效指標燈號](http://www.aec.gov.tw/%E8%B3%87%E8%A8%8A%E5%85%AC%E9%96%8B/%E9%96%8B%E6%94%BE%E8%B3%87%E6%96%99-Open-Data/12.%E6%A0%B8%E5%AE%89%E7%AE%A1%E5%88%B6%E7%B4%85%E7%B6%A0%E7%87%88%E7%B8%BE%E6%95%88%E6%8C%87%E6%A8%99%E7%87%88%E8%99%9F--219_2015_2215.html)
- [核能電廠異常事件次數](http://www.aec.gov.tw/%E8%B3%87%E8%A8%8A%E5%85%AC%E9%96%8B/%E9%96%8B%E6%94%BE%E8%B3%87%E6%96%99-Open-Data/15.%E6%A0%B8%E8%83%BD%E9%9B%BB%E5%BB%A0%E7%95%B0%E5%B8%B8%E4%BA%8B%E4%BB%B6%E6%AC%A1%E6%95%B8--219_2015_2218.html)
- [核能電廠違規件數](http://www.aec.gov.tw/%E8%B3%87%E8%A8%8A%E5%85%AC%E9%96%8B/%E9%96%8B%E6%94%BE%E8%B3%87%E6%96%99-Open-Data/16.%E6%A0%B8%E8%83%BD%E9%9B%BB%E5%BB%A0%E9%81%95%E8%A6%8F%E4%BB%B6%E6%95%B8--219_2015_2219.html)
非官方來源
- [台電發電記錄](http://taipower.g0v.ronny.tw/)  [@ronnywang](http://ronnywang.pixnet.net/blog)

## 其他討論

（討論主題若在上方已經有適合擺放的地方，請直接就在上方適當處附加 comment 討論，這樣可以省去事後從下方討論搬到上方的整理工夫。）

> 腦海裡一直浮現 heroku status 的樣子 XD  --> [https://status.heroku.com/](https://status.heroku.com/)
> [name=Johnson L]


> 如果要凸顯台灣發電過剩 / 全部停機也不會缺電這件事情，可以的話建議在 visualization 裡加上目前全台灣的發電量 / 蓄電量；若可以用電池充電的意象做視覺化，用折線圖表示總蓄電量與核電發電量隨時間的變動，應該滿清楚的 :)
> [name=Johnson L]

> [電池充電意象參考](http://blog.baagic.com/post/50496003427/powerbank)
> [name=nchild]


> [https://github.com/g0v/aec-process](https://github.com/g0v/aec-process)
> [name=Jeff H]

> [https://github.com/g0v/g0vre](https://github.com/g0v/g0vre)
> [name=Jeff H]


> IRC 2014/2/22 10:36:27
> [name=Johnson L]

> ronnywang: [http://taipower.g0v.ronny.tw/place/177](http://taipower.g0v.ronny.tw/place/177) # 關於核電廠停機資訊我已經收集一年了 _xD_
> [name=Johnson L]

> _好讚_
> [name=蔡雅瀅]


> 一直很想知道原能會對於2/22(六)核電廠的狀況如何說明?但已經2/24(一)下午還沒有上傳周末的資料，打電話去問何時上傳？總機轉接的第一位女士說：有時候會【沒有資料】喔。第二位說：早上他們在開會。2:53終於上傳了
> [name=蔡雅瀅]



- [ ] 若有「停機」或「異常降載」能否**拍攝網頁畫面截圖**？
說明：2/22(六)凌晨有地震，同日下午黑客松時，看到核一二廠各有一部機組降載(印象中是熱功率降到50%和60%左右，不確定)，但台電在媒體上說反應爐一切正常，如果有保存未經轉換的台電網頁畫面，未來要提出質疑，請台電或原能會說明降載原因?會比較容易



![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_2a3aa81382b1fc79e0574655da471527)


> 有點好奇這張圖Data 從拿裡拿來的?  縱軸沒有單位...
> [name=Ginger C]

1.點進[ronnywang做的台電發電紀錄](http://taipower.g0v.ronny.tw/)，再點選核一#2，作者應該是提取[台電系統各機組發電量資料](http://www.taipower.com.tw/content/new_info/new_info_in.aspx?LinkID=11)
2.單位應該是 百萬瓦 (MW)


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_4a5e292f6c1304554f253fa24ad85562)

原能會103.02.22[運轉中電廠每日管制資料](http://www.aec.gov.tw/controlreport/historydata.html?searchyear=2014&searchmonth=2&button=%E9%80%81%E5%87%BA)，僅記載核二2號機降載，未公布核一2號機也有降載

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_456f16e64c973282a54cf8d50c397c88)


原能會發布的2/23資料，有記載核一2號機和核二2號機降載事宜
![](https://g0v.hackpad.tw/static/img/pixel.gif)
[https://www.facebook.com/photo.php?fbid=10201282136045973&set=p.10201282136045973&type=1&theater](https://www.facebook.com/photo.php?fbid=10201282136045973&set=p.10201282136045973&type=1&theater)

> 台電的頁面是[這個](http://www.taipower.com.tw/content/new_info/new_info-b24.aspx?LinkID=7)嗎?
> [name=Chang S]

> 所以我們要重新爬資料嗎？
> [name=Tom C]


### 文案討論

- 網站英文名字
    - 英文名字提案：Nuclear Truth
    - 英文名字提案：Nuclear Watch (看守核電)
    - 英文名字提案：Nuclear .TW (雙關語：台灣核電、翻譯與看守核電：Nuclear translate & Watch，將原能會、台電等官方公布的核電資訊轉譯成容易理解的圖表，並且紀錄、比對、分析相關資訊，監督核安   )
> 投 nuclear.tw 一票，這樣網站名稱也有了。
> [name=Jeff H]

> 假設「translate」是名稱的一部分，那這個網站可能也應負有「將核能名稱以簡易的方式解說予大眾」的責任。
> [name=Jeff H]

> 投nuclear.tw，且這網址似乎還沒有人用~
> [name=Chang S]

        - [ ] 文案中若出現核能專有名詞，當滑鼠 mouse over 時，可以像 Dr. Eye 一樣，跳出名詞解說。
> 專有名詞的解說，不一定要通通由這個網站提供，也可以連結與截取自 wikipedia。
> [name=Jeff H]

> 可能有參考價值的維基頁面 : [核電站](https://zh.wikipedia.org/wiki/%E6%A0%B8%E7%94%B5%E7%AB%99)、[核動力](https://zh.wikipedia.org/wiki/%E6%A0%B8%E5%8B%95%E5%8A%9B#.E7.9B.B8.E5.85.B3.E9.A3.8E.E9.99.A9)，或是我們寫出來之後拿去更新維基
> [name=Chang S]

> 看起來會需要核工背景的知識人才
> [name=Chang S]


- Slogan 提案 (好比蔡雅瀅在上文舉例的「台灣核電、翻譯與看守核電」)，請提案：
    -

2/22（六）下午大家在參加黑客松時，看到網頁上有兩部反應爐降載，當時很好奇發生何事？（正常狀況反應爐熱功率100％或99％）；回家看新聞[2/22凌晨接連發生芮氏規模5.4、4.2地震，台電指出，經調查後發現，各轄區供電系統，都沒有問題，核一、二、三廠共6部機，皆正常發電、運轉，未受地震影響，請民眾不用擔心](http://www.ettoday.net/news/20140222/327783.htm)。想問當時有人截圖嗎？或者可用其他方式驗證台電是否說謊（皆正常發電、運轉）？
- [ ] 系統可以有（先人工手動輸入的）新聞列表，並與圖表連結，就好像下面舉例的 Google Finance 一樣：
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c24de26dbc1b27280ad71e102df71adf)
> 取的是東電的圖表，可惜 2011 年那時股價大跌，已經沒有新聞資料與之對應連結了。
> [name=Jeff H]

    - [ ] 需要有人繪製 mock up：新聞與圖表並陳的樣式
> 跟 [Google finance 的圖表](http://goo.gl/oJyH0Q)形式真的蠻像的，可以讓每個核電場用一條線呈現，且可以選擇顯示或是隱藏。
> [name=Chang S]

> 我找找 Google chart 或有沒有其他 Libraries 可以方便做這個功能的，不然可能要自己刻看看。
> [name=Chang S]

- [ ] 可以仿照 Facebook Like，在新聞上面加上「我相信」、「我懷疑」的按鈕，幫忙自動發佈到 Facebook 上。但是分享的頁面不是新聞，而是新聞與同時段對應的圖表並陳。
    - 點下按鈕，會跳出 dialog 並附上預先準備好的分享「說詞」的 template，允許使用者修改，按「確定」後才真的分享到 Facebook
        - [ ] 需要有人設計「說詞」的文案
- [ ] 新聞也可以與「新聞小幫手」連結，供人檢舉_質疑_並以我們準備的圖表作為佐證。
> 這裡無法確定是新聞有誤，還是我們抓到的資料有誤。為了避免爭議，也許真的需要有留下 screenshot 的功能。
> [name=Jeff H]

從台電發電記錄可看出：
1.比對台電（[台電發電記錄＠ ronnywang](http://taipower.g0v.ronny.tw/place/355)）和[原能會的核電記錄](http://www.aec.gov.tw/controlreport/historydata.html?searchyear=2013&searchmonth=5&button=%E9%80%81%E5%87%BA)，以2013.05.20為例，台電曾出現6部機組發電量僅6百萬瓦（註：[全國核電總裝置容量5144百萬瓦](http://www.taipower.com.tw/content/new_info/new_info-b22.aspx?LinkID=7)）的低點，但同日原能會每日一筆的記錄，卻顯示核一1號機大修，其他機組穩定運轉。其它低點（如：2013.04.11、2013.08.10）也有類似狀況。

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_014129e952043759538c84f917e4c8cf)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_8a1001b062df66a298425bea6e2bba01)
2.全國核電裝置容量5144百萬瓦（即514.4萬千瓦），實際發電量大多在5000百萬瓦以下。
> 安全issue ?
> [name=Ginger C]

> 1.提實際發電量低於裝置容量，是在思考核電實際的發電量，比裝置容量低，找核電的替代方案時，不一定要取代核電的裝置容量，能取代實際發電量就夠了
> [name=蔡雅瀅]

> 2.安全issu則是:
> [name=蔡雅瀅]

> a.折線圖中，有很多突然降低的點，有些是計畫性檢修停機、降載，有些是意外狀況，故障停機、降載
> [name=蔡雅瀅]

> b.若能比對各機組折線圖中的低點，與原能會選擇公布的每日運轉狀況表做比較，中間若有差異，有可能原能會隱匿一些資訊。因折線圖是根據短時間自動紀錄的資訊，較不易竄改，而每日運轉狀況表則是經過挑選後的結果。而核能管制單位若不當隱匿資訊，是核安問題     
> [name=蔡雅瀅]


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_20e972d971e242e1e04cca10146397ee)

3.燃氣電廠（燒天然氣）的，發電量落差很大，台電的燃氣電廠有高到接近7000百萬瓦，也有低到1000多百萬瓦。而民營的有高到3685百萬瓦，也有低到0百萬瓦。（若將各電廠閒置情形（裝置容量 - 實際發電量）彙整，扣除核電在該時點實際發電量，再比對當時的用電量，應可得出，廢核是否會缺電？）

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_25628ebacc3a36118b394bf7bb375ca3)


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_cd5fbbc8bc1c4ac941f88ff837c19863)

今天反核遊行有碰到雅瀅，提到說其實那天沒有留到大家的連絡方式，專案進度很難持續，還有之後也可以再找時間辦個小鬆 (可以在蠻野心足，也可以來我們公司喔~[Netivism.com.tw](http://Netivism.com.tw))，把這個專案完成出來。
話說我也沒有大家的連絡方式XD....我的 FB 和 G+ 是  junsuwhy@gmail.com 歡迎來加我~
非常感謝CHANG S 的提議，蠻野可以當活動場地（而且我好像只會用桌機，不太會用自己的筆電），先列幾個時間，懇請可以參加的朋友，在後面簽名：
3/25（二）7：00 書懷
3/27（四）7：00 書懷
3/28（五）7：00 書懷
3/29（六）9：00 書懷
3/29（六）1：30
> 最後一個是指 3/29 ?
> [name=Chang S]

> 對，我打錯了 ：）
> [name=蔡雅瀅]

> 請問「蠻野」是哪裡？
> [name=Jeff H]

> 台北市懷寧街106號6樓之1（捷運台大醫院站1號出口，穿過228公園，左轉種福園樓上）
> [name=蔡雅瀅]


Jeff Hung: jeff.cc.hung -at- gmail.com
Ginger: chenyijyun@gmail.com
剛剛看到這個
[你家能不能倖免於難？](http://mapstalk.blogspot.tw/2014/03/blog-post.html) [http://mapstalk.blogspot.tw/](http://mapstalk.blogspot.tw/)



