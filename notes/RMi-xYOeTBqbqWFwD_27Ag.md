---
title: "超農域--栽培管理資訊"
tags: hackpad
---

# 超農域--栽培管理資訊

> [點此觀看原始內容](https://g0v.hackpad.tw/dz2qc0E8i0T)


## 栽培管理資訊系統  說明

影響市面以及貿易上作物的價格以及品質的事物非常多，其中疫情以及栽培管理訊息也是一個非常重要的關鍵，華爾街也有設置專門分析重大作物疫情的職位(針對期貨)，歷史上也有許多因為作物疫情導致的大饑荒，若可以讓主管單位以及栽培者更快速掌握疫情變化，是一個非常重要的關鍵，目前國內的植物疫情系統還有很大的強化空間:
提供一點想法：
- 如果這個可以監控疫情及栽培資訊，也許可以協助生產者在農藥與資材使用的控制，進一步達到食品安全與生產順利。
- 使用者對象有哪些？如果是栽培者，可能需要知道病蟲害的相關FAQ；如果是農產品進出口業者如何從這個系統得到資訊
> Yes 使用者對象就是針對栽培者和政府農業單位的農業行政和研究單位。
> [name=曼 奧]

```
進出口業者也同樣會需要藥劑和疫情變化，所以也可以從這個系統得到資訊
```
> FAQ部分我想整合到還沒列出來的第三系統裡面(栽培/觀察者系統)，同時包含教育訓練和福利資訊
> [name=曼 奧]

下面是幾個目前與疫情相關性最大的網頁
1.  [植物疫情](http://data.g0v.ronny.tw/index/data/7273) ~傳說中的官網~
2.  目前出現了這個新東西 [「稻熱病疫情現況」網頁專區](http://phis.baphiq.gov.tw/Plant/GoogleMap.nsf)
3.  惡意軟體可能竊取個人資訊、造成財務損失及永久刪除檔案。
4.  [蔬果重要病蟲害疫情旬報](http://data.g0v.ronny.tw/index/data/7295)
5.  [氣象局](http://www.cwb.gov.tw/V7/index.htm)
6.  [台灣有害生物天敵資料庫](http://210.69.150.201/insectsite/Default.aspx) (內有大量資料 [神秘的介紹和使用方法\[PDF\]](http://agbio.coa.gov.tw/image_doc/06%E8%87%BA%E7%81%A3%E8%BE%B2%E4%BD%9C%E7%89%A9%E6%9C%89%E5%AE%B3%E7%94%9F%E7%89%A9%E8%B3%87%E6%96%99%E5%BA%AB%E7%B0%A1%E4%BB%8B.pdf))
7.  [Google Flu](http://www.google.org/flutrends/) (這是部分呈現方式的參考用)
8.  [防檢局植物疫情管理資訊網（主動監測區）](http://phis.baphiq.gov.tw/WebEvery.nsf/searchViewTs?OpenForm)：病蟲害監測及相關資料下載。
9.  [農藥使用資訊系統](http://pesticide.tactri.gov.tw/index.php?option=com_content&view=article&id=47&Itemid=53)
10.  [不同國家（區域）農產品中農藥殘留安全標準查詢網站](http://www.tactri.gov.tw/wSite/ct?xItem=5637&ctNode=286&mp=11)
11.  可參考以色列開發的：[AgriTask](http://www.pest-scout.com/m/main/)，號稱是[農業版的waze](http://bit.ly/1kxDtXb)。如何做出不同且適用於台灣的東西出來。
12.[Google 地圖參考](https://developers.google.com/maps/documentation/javascript/examples/?hl=zh-tw)
13.[圖表呈現參考](https://github.com/mbostock/d3/wiki/Gallery)
## MOCKUPS


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_3f3de6b28d7972027be2047f204c4077)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_5cf112c85bfb79270f1e77de63138974)
### 地圖以Google Map顯示，並且可以轉成Earth，如顯示為行政區地圖，可以色塊表示嚴重性，若有持續填報累積資料，可以earth跑出色塊變化的嚴重性



![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_49913e557edbb690790c696676496f6e)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_59c9a20ea20e328dfa98be17e41e0f15)


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_97f2efd1593d9747fb4c8dfa264efa55)

**疫情概況在點擊後可以亦可以選擇一次出現整篇的全國報告(組合)，相關的內容都可以匯出成DOC或PDF等格式，亦或是產生QR-Code後，系統產生的報告圖片(類似**[Bokete](http://bokete.jp/boke/hot)**的方法)，疫情資料(確定是什麼疫情後)可連接到藥物系統和管理(診斷)系統進行**

## UI補充

- 地圖至少要以鄉鎮為基礎，但各地鄉鎮比例非常大，所以如果能有村，甚至是可帶入以座標畫出疫情/事件邊界的輸入介面會更好(鄉鎮向量圖需求)
- 可以具備時間歷史紀錄變化的視覺介面
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_4cc3d133c95e7b8ec734daf8acb15a80)
### 子龍設計，V1.0

## 系統連動想法

1.  發生疫情或栽培環境狀況(如天災)後，需要防治的地方會有農藥或其他災情復原方法的需求，連動農藥系統進行藥劑的建議與提供。
2.  和**栽培管理與資訊系統連動，提供栽培者關注的疫情變化**
3.  連接氣象局，記錄大面積農業區域的氣像變化，以供推估疫情與事件出現的可能性
> 有辦法和地理資訊結合嗎？
> [name=YingChu C]

4.  與檢疫系統互通( [對外貿易植物檢疫資料庫查詢系統](http://192.192.148.121/coa/hotnews_idx.php)  )，可以更快速比對作物出入口要注意的疫情檢疫事項(也轉譯成英日文方便國際使用?)

## 延伸系統構想


參考用(日本)
[http://ymmfarm.com/agribiz/3311.html](http://ymmfarm.com/agribiz/3311.html)

## 其他疫情整合參考(結合檢疫)

-
1.  [IPPC](https://www.ippc.int/)（國際植物保護公約，FAO\[國際農糧組織\]單位之一）[WIKI介紹](http://zh.wikipedia.org/wiki/IPPC)
2.  [ISPM](http://www.baphiq.gov.tw/news_list.php?menu=29&typeid=960&typeid2=1525) (**國際植物防疫檢疫措施標準**IPPC主管，這個是防檢局翻譯的中文內容)
3.  [CABI](http://www.cabi.org/cpc/) (CABI Plant protection compendium 最權威的全球有害生物資料庫，包含線上鑑定的功能)

