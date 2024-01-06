---
title: "歐噴。豆知識 (待訂)"
tags: hackpad
---

# 歐噴。豆知識 (待訂)

> [點此觀看原始內容](https://g0v.hackpad.tw/1Y83e0mcK76)


### 緣由

- 原為 Pixnet Hackathon 2015 的參賽作品
    - 「歐噴豆知識」是把廣告轉換成 open data 豆知識的擴充套件，使用者能訂閱感興趣的 open data，它會很厲害的把你不想看的廣告遮掉，讓您輕鬆獲得豆知識，無負擔。另外，我們也提供熱門豆知識排行榜！
- Repo: [https://github.com/conradhuang/PixnetHackday2015](https://github.com/conradhuang/PixnetHackday2015)
- Deck: [https://speakerdeck.com/bryanyuan2/ou-pen-dou-zhi-shi-pixnet-hackathon-2015](https://speakerdeck.com/bryanyuan2/ou-pen-dou-zhi-shi-pixnet-hackathon-2015)
- Extension: [https://chrome.google.com/webstore/detail/%E6%AD%90%E5%99%B4%E8%B1%86%E7%9F%A5%E8%AD%98/jgkidmplccofmhbdmogcncnlogaliidp](https://chrome.google.com/webstore/detail/%E6%AD%90%E5%99%B4%E8%B1%86%E7%9F%A5%E8%AD%98/jgkidmplccofmhbdmogcncnlogaliidp)

### 要解決的問題


- 網頁上的廣告很煩人，通常使用者會安裝 adblocker/adblocker plus 阻擋廣告。但其實我們可以在廣告上面，直接疊加呈現整理過的 open data 資訊，讓使用者能隨時獲得有用/實用的訊息 ?!

### 預定使用者

- end users / adblocker/adblocker plus users / 關心 Open Data 資訊的使用者 / 想看到像廣告又不要太花俏太多餘的使用者 / 想移除 adblocker 的使用者

### 預定功能

- **_直接 apply adblock plus easy list rules_** [**_https://easylist.adblockplus.org/en/_**](https://easylist.adblockplus.org/en/)
- 有更系統化的資訊能直接吐給  FE
- (已實作雛形) 訂閱主題：讓使用者選擇想要訂閱的主題，置換廣告欄位上的豆知識
- (已實作雛形) 豆知識排行榜：顯示最多人關心的豆知識


### 現有類似專案

- 尚無尋獲

### 相關專案

- Catblocker: [http://catblock.getadblock.com/](http://catblock.getadblock.com/)
    - Adblocker 的延伸專案，把廣告內容換成貓

### 授權方式

（程式碼部分如 MIT/BSD /文件部分，如 CC-BY）

### 使用資料

(也許會打掉重練也不一定，目前沒有一個有系統/人工整理的「問答資料」集)

- 臺北市立動物園動物 tpe-animal
- 臺北市各級學校 tpe-school
- 臺北市公園 tpe-park **location img**
- 臺北市公園內景點 tpe-parkSp  **img**
- 臺北市 wifi 熱點 tpe-wifi **location**
- 臺北市停車場 tpe-parking
- 臺北市景點 tpe-spot **location img url**
- 臺北市住宿 tpe-hotel **location img url**
- 臺北市104年度颱風期間開放停車學校 tpe-typhoon
- 臺北市公私立醫療院所 tpe-hospital
- 臺北市垃圾資源回收、廚餘回收限時收受點 tpe-garbage **location**
- 臺北捷運系統票價資料 tpe-mrt

### 專案目前狀態

（雛形 / 實作）

已實作類別 (8)
- 觀光 travel
- 自然 natural
- 生活 lifestyle
- 醫療 care
- 理財 finance
- 交通 trans
- 政治 politic
- 其他 other

### 利益揭露

- 網站業者會非常不爽，no revenue，但 adblcoker 也幹了同樣的事


## API

#### 取得一個知識

[http://test.wjhuang.net/api.php?a=getkg&n=](http://test.wjhuang.net/api.php?a=getkg&n=##number##&cat=##category##&manual=##manual##)[**#**](http://test.wjhuang.net/api.php?a=getkg&n=##number##&cat=##category##&manual=##manual##)[**#number**](https://g0v.hackpad.tw/ep/search/?q=%23number&via=1Y83e0mcK76)[**##**](http://test.wjhuang.net/api.php?a=getkg&n=##number##&cat=##category##&manual=##manual##)[&cat=](http://test.wjhuang.net/api.php?a=getkg&n=##number##&cat=##category##&manual=##manual##)[**#**](http://test.wjhuang.net/api.php?a=getkg&n=##number##&cat=##category##&manual=##manual##)[**#category**](https://g0v.hackpad.tw/ep/search/?q=%23category&via=1Y83e0mcK76)[**##**](http://test.wjhuang.net/api.php?a=getkg&n=##number##&cat=##category##&manual=##manual##)[&manual=](http://test.wjhuang.net/api.php?a=getkg&n=##number##&cat=##category##&manual=##manual##)[**#**](http://test.wjhuang.net/api.php?a=getkg&n=##number##&cat=##category##&manual=##manual##)[**#manual**](https://g0v.hackpad.tw/ep/search/?q=%23manual&via=1Y83e0mcK76)[**##**](http://test.wjhuang.net/api.php?a=getkg&n=##number##&cat=##category##&manual=##manual##)
for example: [http://test.wjhuang.net/api.php?a=getkg&n=1&cat=natural](http://test.wjhuang.net/api.php?a=getkg&n=1&cat=natural)
for example: [http://test.wjhuang.net/api.php?a=getkg&n=10&manual=1&cat=politic](http://test.wjhuang.net/api.php?a=getkg&n=10&manual=1&cat=politic)
cat is optional
manual is optional (1= 要手工資料, 0=defailt)

#### 知識+1

[http://test.wjhuang.net/api.php?a=logkg&id=](http://test.wjhuang.net/api.php?a=logkg&id=##id##)[**#**](http://test.wjhuang.net/api.php?a=logkg&id=##id##)[**#id**](https://g0v.hackpad.tw/ep/search/?q=%23id&via=1Y83e0mcK76)[**##**](http://test.wjhuang.net/api.php?a=logkg&id=##id##)

#### 排行榜 過去24hr

[http://test.wjhuang.net/api.php?a=stat](http://test.wjhuang.net/api.php?a=stat&cat=##category##)[&cat=](http://test.wjhuang.net/api.php?a=stat&cat=##category##)[**#**](http://test.wjhuang.net/api.php?a=stat&cat=##category##)[**#category**](https://g0v.hackpad.tw/ep/search/?q=%23category&via=1Y83e0mcK76)[**##**](http://test.wjhuang.net/api.php?a=stat&cat=##category##)
for example: [http://test.wjhuang.net/api.php?a=stat&cat=trans](http://test.wjhuang.net/api.php?a=stat&cat=trans)
cat is optional

#### 取得類別清單

[http://test.wjhuang.net/api.php?a=getCats](http://test.wjhuang.net/api.php?a=getCats)

#### 單一知識 landing page

[http://test.wjhuang.net/a/](http://test.wjhuang.net/a/##id##)[**#**](http://test.wjhuang.net/a/##id##)[**#id**](https://g0v.hackpad.tw/ep/search/?q=%23id&via=1Y83e0mcK76)[**##**](http://test.wjhuang.net/a/##id##)
example: [http://test.wjhuang.net/a/tpe-parking-q01-868](http://test.wjhuang.net/a/tpe-parking-q01-868)


##


