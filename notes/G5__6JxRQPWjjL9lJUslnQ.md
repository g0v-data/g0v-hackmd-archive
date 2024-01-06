---
title: "全台人口資料計算平台"
tags: hackpad
---

# 全台人口資料計算平台

> [點此觀看原始內容](https://g0v.hackpad.tw/p6mANPV1Bb7)


掌握人口資料常常是參與政治運動不可或缺的一環，有鑑於現在一般網路上可取得資料的來源大多來自行政院主計總處和各地的戶政事務所，中央的資料精細度有限，地方的資料又相當零散。因此，建立一個人口資料計算平台，可以幫助許多社運團體提供快速取得所需人口資料的地方。

## 現有問題

1.  行政院主計總處的資料僅達縣市層級，若需要往下詳細到鄉鎮市區、甚至是村里層級，就需要到各縣市的民政局、甚至是各鄉鎮市區的戶政事務所
2.  許多市的民政局乃至各鄉鎮市區的戶政事務所都未將資料人口上網，若需要資料還需要親自跑戶政事務所輸出文件
3.  在選舉事務部份，由於選舉資料不會包含人口的年齡組成，因此戶政資料就成為一個相當重要的資料來源
4.  檢視立委選民時，需要區分一般民眾與原住民民眾之身分別以確認其是否為一般立委或原住民立委的選民。但是，各戶政事務所的網路資料甚少有精細到以里為單位的人口資料。

## 所需資料類型

1.  全臺灣「各村里」「單一年齡組」「每月」「靜態人口」資料
    1.  一般民眾 (一般資料有包含原住民)
    2.  平地原住民
    3.  山地原住民
2.  動態人口資料
> 尚不確定資料的精細程度
> [name=Chen C]

    1.  遷出
    2.  遷入

## 相關資料來源

1.  全臺灣「各村里」「單一年齡組」「每月」「靜態人口」資料
    1.  一般民眾 (一般資料有包含原住民)
        統計月報表 編號 RCRP0C1B0
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_bd3482b2c8d8fbcdddd232024a8b0f35)
    1.  平地原住民
> 來源待查
> [name=Chen C]

    2.  山地原住民
> _來源待查_
> [name=Chen C]

1.  動態人口資料
> 尚不確定資料的精細程度
> [name=Chen C]

    1.  遷出
    2.  遷入

## 基本模版

- 男性與女性分表
- 一村里一列
- 單一年齡組一行
- 其他格式可靠運算得到
| 男性 |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 行政區 | 里名 | 0歲 | 1歲 | 2歲 | 3歲 | 4歲 | ...... |
| 南港區 | 九如里 |  |  |  |  |  |  |
| 南港區 | 三重里 |  |  |  |  |  |  |
| 南港區 | 中南里 |  |  |  |  |  |  |
| 南港區 | 中研里 |  |  |  |  |  |  |
| 南港區 | 仁福里 |  |  |  |  |  |  |
| 南港區 | 玉成里 |  |  |  |  |  |  |
| 南港區 | 合成里 |  |  |  |  |  |  |
| 南港區 | 成福里 |  |  |  |  |  |  |

## 資料來源現況

- 全國(不定期)
[http://data.moi.gov.tw/MoiOD/Data/DataContent.aspx?oid=16DB45A1-37BD-478E-BEE1-E44088B54CF5](http://data.moi.gov.tw/MoiOD/Data/DataContent.aspx?oid=16DB45A1-37BD-478E-BEE1-E44088B54CF5)
> 有發 email & 打電話去問過，看樣子承辦人員並不是很想 "定時更新"
> [name=Finjon K]

- 新北市(每月)
[http://www.ca.ntpc.gov.tw/Editors/DATA_PageNode/net/upload/2014-07-21/e9e1dc75-f52b-4c07-9318-48c2848e38e2.xls](http://www.ca.ntpc.gov.tw/Editors/DATA_PageNode/net/upload/2014-07-21/e9e1dc75-f52b-4c07-9318-48c2848e38e2.xls)
- 臺中市(不定期)
[http://demographics.taichung.gov.tw/Demographic/Web/Demographic.aspx](http://demographics.taichung.gov.tw/Demographic/Web/Demographic.aspx)
- 嘉義縣(每月)
[http://hro-service.cyhg.gov.tw/population/index.asp?Parser=99,6,37](http://hro-service.cyhg.gov.tw/population/index.asp?Parser=99,6,37)
> 不過原住民資料來源仍然是一個大問題......Orz
> [name=Chen C]

> 資料釋出時間不定期，也是ㄧ個很大的問題，選舉前希望是能夠抓到時間最接近的103/7的資料
> [name=Chen C]



