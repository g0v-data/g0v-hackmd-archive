---
tags: GIS,
---

# umap & OpenStreetmap

## 工具介紹

<iframe width=100% height="490" src="https://www.youtube.com/embed/bHblo2uofcI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<br>
<br>

==umap & OpenStreetMap 操作教學影片：https://youtu.be/bHblo2uofcI==
工具網址：https://umap.openstreetmap.fr/zh-tw/

---
🔻 澎湖縣 OpenStreetMap 飲水點 (自動更新) 套疊 mapbox 衛星底圖
示範地圖：http://u.osmfr.org/m/638568/

<iframe width="100%" height="400px" frameborder="0" allowfullscreen src="//umap.openstreetmap.fr/zh-tw/map/osm-mapbox_638568?scaleControl=false&miniMap=false&scrollWheelZoom=true&zoomControl=true&allowEdit=false&moreControl=true&searchControl=null&tilelayersControl=null&embedControl=null&datalayersControl=true&onLoadPanel=undefined&captionBar=false#12/23.6015/119.6282"></iframe>

資料
- 遠端資料，網址欄位請輸入以下：澎湖縣範圍的飲水點
    - `
https://overpass-api.de/api/interpreter?data=[out:json][timeout:25];(node["amenity"="drinking_water"](23.038033989127,118.98193359375,23.978724193277,120.02563476563););out;>;out skel qt;
`
- 教學文章：umap + data from OpenStreetmap
    - 「製作隨時更新的客製化地圖，透過動態連結 uMap 地圖與開放街圖資料庫」by RL Chen
        - http://supaplex99.blogspot.com/2015/08/using-overpass-turbo-to-extract-data-and-umap-with-dynamic-data-link-visualization.html
    - https://wiki.openstreetmap.org/wiki/UMap/Guide/Import_data_with_Overpass
- 經驗建議：
    - 若資料集 沒有需要持續更新，記得不用勾選「動態」
    - 若資料集 希望採用動態更新，那麼資料範圍比較適合「鄉鎮區」尺度，若地理範圍太大，對於使用者網頁端可能跑不出來

底圖
- umap 提供許多樣式的底圖，例如強調出自行車道路線，或是水彩渲染的底圖樣式..等
- 若希望自行調整底圖樣式，或是需要高解析度衛星底圖，可考慮使用 mapbox studio 自製底圖的服務 https://studio.mapbox.com/

---
特定主題的圖資，是否適合以 OpenStreetMap 資料庫來進行資料標注？
- 您可以查看 Map features 的清單，了解資料庫中目前的資料種類
    - https://wiki.openstreetmap.org/wiki/Map_features
- 評估文章：主題地圖與 OSM：https://osmtw.hackpad.tw/-OpenStreetMap-VnjVOhWBZuO
- 主題型編輯器：使用 MapComplete 建立主題地圖編輯器 https://mapcomplete.osm.be/

🔻 MapComplete 以「公共飲水點」為例
https://mapcomplete.osm.be/drinking_water.html?z=13&lat=22.63386&lon=120.3091&background=Mapbox
<iframe width=100% height="400" src="https://mapcomplete.osm.be/drinking_water.html?z=13&lat=22.63386&lon=120.3091&background=Mapbox" frameBorder="0"></iframe>
