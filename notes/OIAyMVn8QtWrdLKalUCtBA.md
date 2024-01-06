---
title: "#{急診及時等床資訊}"
tags: hackpad
---

# #{急診及時等床資訊}

> [點此觀看原始內容](https://g0v.hackpad.tw/7Oz2YpnNjzM)

專案介紹 | Project Readme / Meta
因為台灣轉診制度不完全, 民眾習慣至較大醫院就醫, 導致急診雍塞
為方便民眾及基層轉診者瞭解並評估是否將會在急診等很久, 可以設計一網站, 讓使用者可以上傳最新帶床資訊, 供欲轉診者決定是否前往就診



## 來龍去脈（想解決什麼問題）


靈感來源:
1.  不時有人把照片放到FB, 但無整合
2.  醫院並沒有義務把資訊公開到醫院網站
3.  政府並沒有提供公開資訊讓民眾方便查詢

![](https://g0v.hackpad.tw/static/img/pixel.gif)
[https://www.facebook.com/photo.php?fbid=372888479509233&set=a.118547204943363.20053.118446058286811&type=1&theater](https://www.facebook.com/photo.php?fbid=372888479509233&set=a.118547204943363.20053.118446058286811&type=1&theater)

主旨
建立一個網站或 App 可供上傳輸入以下資訊:
[#醫院](https://g0v.hackpad.tw/ep/search/?q=%23%E9%86%AB%E9%99%A2&via=7Oz2YpnNjzM)  (可用GPS定位) [#日期](https://g0v.hackpad.tw/ep/search/?q=%23%E6%97%A5%E6%9C%9F&via=7Oz2YpnNjzM)  [#時間](https://g0v.hackpad.tw/ep/search/?q=%23%E6%99%82%E9%96%93&via=7Oz2YpnNjzM) (可抓手機系統資訊)
[#等候掛號人數](https://g0v.hackpad.tw/ep/search/?q=%23%E7%AD%89%E5%80%99%E6%8E%9B%E8%99%9F%E4%BA%BA%E6%95%B8&via=7Oz2YpnNjzM)  [#等後看診人數](https://g0v.hackpad.tw/ep/search/?q=%23%E7%AD%89%E5%BE%8C%E7%9C%8B%E8%A8%BA%E4%BA%BA%E6%95%B8&via=7Oz2YpnNjzM)  [#目前急診人數](https://g0v.hackpad.tw/ep/search/?q=%23%E7%9B%AE%E5%89%8D%E6%80%A5%E8%A8%BA%E4%BA%BA%E6%95%B8&via=7Oz2YpnNjzM) [#等候住院人數](https://g0v.hackpad.tw/ep/search/?q=%23%E7%AD%89%E5%80%99%E4%BD%8F%E9%99%A2%E4%BA%BA%E6%95%B8&via=7Oz2YpnNjzM) (手動輸入? 照片?)

牽涉領域
[#g0v](https://g0v.hackpad.tw/ep/search/?q=%23g0v%E9%86%AB%E7%99%82&via=7Oz2YpnNjzM)[醫療](https://g0v.hackpad.tw/ep/search/?q=%23g0v%E9%86%AB%E7%99%82&via=7Oz2YpnNjzM)

界面 : 類似於此專案, 在地圖顯示待床數, 點到醫院可以知道細目
雨量記錄表 , 但此資料是由中央氣象局提供
[http://g0v.github.io/twgeojson/interpolation.html](http://g0v.github.io/twgeojson/interpolation.html)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9a29fbb09e1d62a829ea716b14ebe688)
而本專案需要 "志工" 提供 (照片 or 資料 update app)

相關組織單位
建議 : [#醫勞盟](https://g0v.hackpad.tw/ep/search/?q=%23%E9%86%AB%E5%8B%9E%E7%9B%9F&via=7Oz2YpnNjzM)

相關專案
> 衍生自某專案/衍生出某專案/API串接自某專案...etc.
> [name=ET B]


授權方式
> 程式碼部分（如 MIT/BSD）
> [name=ET B]

> 文件部分（如 CC-BY）
> [name=ET B]


使用資料

專案目前狀態
> 構想 / 規劃 / 雛形 / 實作
> [name=ET B]



## 目標與功能（要如何解決）


預定使用者
1.  一般民眾
2.  轉診醫療單位

預定功能
1.  查詢急診雍塞程度

使用方式
 INPUT: 上傳 照片 或 App 輸入
 OUTPUT: 網頁呈現

## 實做細節（非技術背景可跳填）


使用技術
- 使用的 vagrant box 版本 / 網址：

協作工具
- github repo：
- hackfoldr 工作資料夾網址：
- google drive 共用資料夾網址：
- google groups 討論群組：
- irc channel：

產出檔案格式

進度與 to-do
> 僅供參考
> [name=ET B]

- [ ] product planning（recommanded procedure from justin lee / 李易修）
    - [ ] strategy
    - [ ] scope
    - [ ] structure
    - [ ] wireframe
    - [ ] visual
- [ ] web front-end
- [ ] web back-end
- [ ] ui / visual design


## 成果展示（規劃文件、雛形/草稿、原型/初稿、正式發佈/完稿）




## 開發者


技術指導

分工與成員
- [ ] NeedsWriter: 需要文案幫手（撰寫基本資訊、報導專案etc）
- [ ] NeedsDesigner: 需要介面設計
- [ ] NeedsData: 需要資料（擷取、清理）
- [ ] NeedsTech: 需要技術支援（程式、架站 etc)
- [ ] NeedsProcess: 需要幫忙設計作業流程
- [ ] NeedsTalkingToRealPerson: 需要有人幫忙和其他機關聯絡
> 設定成 project registry 中的 tags，需要幫忙的會自動 promote 到 g0v project hub
> [name=ET B]



