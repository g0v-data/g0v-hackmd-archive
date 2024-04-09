---
tags: planning,獎勵容積,hackpad
---

# 獎勵容積在臺灣

> [點此觀看原始內容](https://g0v.hackpad.tw/1ceZB2gCkqf)


挖一個關於「容積獎勵現形」的坑(開放空間、停車空間、台北好好看系列二、空地維護管理辦法、都市計畫本身既有的獎勵項目與法條、綠建築中涉及容獎的法條、都市更新各式獎勵、都市設計審議..)
> 一直希望這種容積獎勵產生的開放空間能夠有完整資訊，畢竟很多都被二次施工藏起來了
> [name=Finjon K]

> 二工作為正常！
> [name=che l]

> 二次施工（二工）為什麼是正常的？
> [name=Gerrard Y]

> 偉哉業界
> [name=che l]


#### 專案目的

1.  獎勵容積，在哪裡？
2.  獎勵容積，如何給？
3.  獎勵容積，後來怎麼了？
4.  獎勵容積，值得嗎？

### Data

- 依照不同縣市
- 法規資料：自治條例...
- 審議資料：會議紀錄
- 核定資料：建築執照內的相關資料、獎勵容積表達的數值方法
    - 台北市建照記錄中有「獎勵」的紀錄
        - [https://github.com/cades/taipei-building-has-reward](https://github.com/cades/taipei-building-has-reward)
        - check\_and\_push.sikuli 這隻 crawler script 以 ronny 爬下來的[台北建管處建照記錄](http://tpebuilding.g0v.ronny.tw/)為資料來源，撈出有「獎勵」關鍵字的執照之url, 存在 record.txt 內。因為開發時用的瀏覽器是Safari, 故目前只能在Mac OS X 上執行. （若改成用Google Chrome / Firefox 就能跨平台了）
        - [https://gist.github.com/ronnywang/688caae73a3fc096966af600d7502994](https://gist.github.com/ronnywang/688caae73a3fc096966af600d7502994)
- 現況資料：照片、歷年使用現況、管理單位

### Visual (idea pool)

1.  呈現方式、位置、樓地板面積
2.  呈現所有大台北的獎勵容積分佈？讓市民善加利用。


## TODO

- [ ] 寫信詢問台北市與新北市的『獎勵容積之評定與核計』資料集
> 這個是要問容獎核定的量，還是問決定核給容獎的「決策過程」？
> [name=Gerrard Y]

> 都蠻想知道的
> [name=che l]

- 資料集欄位需求：?
- [ ] 整理獎勵項目清單，含法規依據

## 資料詢問與回覆紀錄區

(20141121) 詢問內政部的回覆
關於您所提出的敬請開放**獎勵容積之評定與核計等相關資料集**建議，有最新的回覆如下: 您好, 有關於您提到開放『獎勵容積之評定與核計』資料集，相關主管機關回復如下：獎勵容積之評定與核計結果、會議紀錄等事涉地方自治事項，目前本署並無此獎勵容積之資料集。建議您逕向直轄市、縣市主管機關洽詢提供。謝謝您！（[http://data.gov.tw/node/9395](http://data.gov.tw/node/9395)）

(20150720) 詢問台北市政府
敬請開放獎勵容積之評定與核計等相關資料集
建議資料集名稱：獎勵容積之核計資料集
建議開放的欄位：獎勵容積之評定與核計結果、會議紀錄
建議原因：獎勵容積之評定與核計，事關整體都市發展，相關政策的形成，長期以委員會與行政機關意向為主導，此議題應受民眾公評，已核定的獎勵容積之資料集，應盡速匯整公佈，才有助於民眾參與此政策之討論與關注。

(20150804) 台北市政府的回覆 104.08.04北市都規字第10436499300號
回復內容 (Content) 親愛的民眾：您好！ 有關您反映建議開放容積獎勵之評定與核計相關資料一案，已交由本局彙整，並分別說明如下：
- 有關都市更新各項獎勵容積之核給事宜，經洽本局都市更新處了解，係以本市都市更新及爭議處理審議會審定為準，其獎勵值及核給額度並載明於歷次都市更新及爭議處理審議會會議紀錄中。倘欲瞭解會議紀錄內容，其電子檔案可於本市都市更新處網站/便民服務（[http://www.uro.taipei.gov.tw/](http://www.uro.taipei.gov.tw/)）下載。若您對都市更新各項獎勵容積之核給事宜有任何疑問，請逕洽逕洽本市都市更新處（地址：臺北市中正區羅斯福路1段8號9樓；法令諮詢專線：2321-5696分機3030）
- 至有關綜合設計放寬及停車獎勵等容積獎勵，經洽本局建築管理工程處，查該處業務係辦理建築執照審查，**涉該處權管容積獎勵(如:開放空間、停車獎勵……等)均載記於建築執照注意事項附表**，且執照存根均於核准後公開上網，您可逕至該處網站查詢(網址:[http://dba.gov.taipei](http://dba.gov.taipei))。 若對綜合設計放寬及停車獎勵等容積獎勵有任何疑問，請逕洽本市建築管理工程處建照科，服務專線1999(外縣市02-27208889)轉分機8372；對都市計畫有任何疑問，請洽本局承辦人：張懿萱，電話：1999(外縣市02-27208889)轉分機8266。 謝謝您來信與指教，並祝您 健康愉快 臺北市政府都市發展局 局長林洲民 敬上




## 議題探討

- 都市更新獎勵的公共賬 https://www.facebook.com/share/p/QFgm7eyesnjivWMY/
- 重探都市金融化：大台北都市空權經濟化過程作為取徑 https://www.ios.sinica.edu.tw/events/seminar/agenda20240508.pdf
- 獎勵容積與停車位
    - 蒐集
        - [https://photos.app.goo.gl/6FPlyhpc3RXGUExq1](https://photos.app.goo.gl/6FPlyhpc3RXGUExq1)
    - 議題探討
        - [https://www.facebook.com/saul.peng/posts/10211394740053986](https://www.facebook.com/saul.peng/posts/10211394740053986)

臺北市
- 「臺北好好看」系列計畫系列二 北市環境更新、減少廢棄建物
    - 相關記錄：[https://abcd.hackpad.com/PChgBWzszlo](https://abcd.hackpad.com/PChgBWzszlo)
    - 監察院糾正 [「臺北好好看系列二計畫」有適法性問題](https://www.facebook.com/notes/%E5%8F%B0%E5%8C%97%E5%A5%BD%E5%A5%BD%E7%9C%8B%E4%B8%80%E7%9C%BC-%E5%8D%81%E5%85%AB%E5%80%8B%E6%9C%88%E5%81%87%E5%85%AC%E5%9C%92/101-%EF%A6%8E-06-%E6%9C%88-07-%E6%97%A5-%E7%9B%A3%E5%A7%94%E6%8C%87%E5%87%BA%E8%87%BA%EF%A5%A3%E5%A5%BD%E5%A5%BD%E7%9C%8B%E7%B3%BB%EF%A6%9C%E4%BA%8C%E8%A8%88%E7%95%AB%E6%9C%89%E9%81%A9%E6%B3%95%E6%80%A7%E5%95%8F%E9%A1%8C/767544389957917)
- 實施容積獎勵建案之開放空間人行流動與公共性探討—以臺北市信義區、中山區為例
    - [http://www.airitilibrary.com/Publication/alDetailedMesh1?DocID=U0026-1008201702164100](http://www.airitilibrary.com/Publication/alDetailedMesh1?DocID=U0026-1008201702164100)
- 「臺北市新建建築物綠化實施規則」草案，內容中有提及獎勵容積
    - [http://twinfo.ncl.edu.tw/tiqry/hypage.cgi?HYPAGE=search%2Fshow_gaztext.hpg&sysid=E1507292](http://twinfo.ncl.edu.tw/tiqry/hypage.cgi?HYPAGE=search%2Fshow_gaztext.hpg&sysid=E1507292)
-  https://www.facebook.com/100000649848605/posts/4822711521093795/

新北市
- 「新北市都市更新建築容積獎勵核算基準」最新修正案
    - [https://www.facebook.com/ur.org.tw/photos/a.121064764639595.29170.120977447981660/842892842456780/?type=1](https://www.facebook.com/ur.org.tw/photos/a.121064764639595.29170.120977447981660/842892842456780/?type=1)

高雄市
- 高雄登革熱疫情，與容積獎勵政策落日建商搶照現象，似乎相關聯
    - [20141112](https://g0v.hackpad.tw/6ykubjy7sit)

### 其他


容積移轉
- [https://www.facebook.com/dbyin/posts/2145333758874944](https://www.facebook.com/dbyin/posts/2145333758874944)

