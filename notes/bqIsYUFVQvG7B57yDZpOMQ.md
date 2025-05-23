---
title: "2014選舉資料改進"
tags: hackpad
---

# 2014選舉資料改進

> [點此觀看原始內容](https://g0v.hackpad.tw/DjHEyHcmR9o)


### 可改進的點

- 姓名重複的情況常見，應該有比姓名更具識別性的代碼才是
> 這個最重要，移到第一條XD
> [name=johnny]

- 釋出候選人登記資料時包含[更完整的資料](https://github.com/ronnywang/vote2014/blob/master/webdata/data/T1.csv) <= 例如，目前候選人登記只有名字、推薦黨籍、選區、登記日
- 行政區應該直接使用[主計處行政區域及村里代碼](http://www.dgbas.gov.tw/ct.asp?xItem=951&ctNode=5485)
- 名字中非中文字的標準化，例如原住民名字中常見。˙・•．等字元，可統一；原住民名字中常見的英文要以括號呈現或另外一欄以示尊重也可再討論
- 資料釋出格式應該更開放些，不要都停留在[一顆星](http://5stardata.info/tw/)，更別說那些放滿圖片的 PDF 文件了
- 縣市升格，例如此次桃園縣升格為桃園市並未在[選區變更文件](http://web.cec.gov.tw/ezfiles/0/1000/img/149/3.pdf)中
- 第幾選區統一格式，目前有臺北市第1選區、臺北市第一選區、臺北市第01選區等
- 選區號次內的詳細區里資訊，例如議員臺北市第1選區：北投區、士林區；另外可否附上經緯度等有利數位呈現的資料
- 應該要有一個統一的位置去發布各種候選人的異動資訊，包括放棄參選、死亡、資格不符等等，目前是交給各地選委會獨立發布，發布時間也沒有清楚規定
- 續上，報名參選後的政黨異動，例如2014-09-01~2014-09-05報名時為X黨，報名過後選舉前退黨或更改黨籍，目前似乎無法如實即時顯示
- 選舉公報相關資訊發布時間太慢了，而且太多人工作業，應該要將選舉公報的工作流程自動化才是
- 各種發布的資料應該有基本的版本紀錄，像是登記概況的 pdf 就在不知不覺間有多次更動，如果不是程式去比對很難知道改了些什麼
- 選舉公報應該集中發布，而不是交給地方選委會選擇性在中央與地方的網站間任意放置，以屏東為例，在[中央提供的公報網站](http://103bulletin.cec.gov.tw/103/%E5%B1%8F%E6%9D%B1%E7%B8%A3/)就看不到選舉公報資料，必須回到[地方選委會網站](http://www.ptec.gov.tw/files/11-1014-5260.php)找


