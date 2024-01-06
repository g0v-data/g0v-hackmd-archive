---
title: "第零次百姓松 civicth0n"
tags: hackpad
---

# 第零次百姓松 civicth0n

> [點此觀看原始內容](https://g0v.hackpad.tw/S5TC0hvy8r3)

> 這個 pad 裡的課程規劃、文字、參考資料均採 CC0 拋棄著作權。
> [name=Audrey T]


## 前言

==如何將原始數據轉換為社會議題，讓每個人都能進行有意義的對話與貢獻？==

今年一月，au 在巴黎的〈思想之夜〉[與 blaise 對談](https://sayit.archive.tw/world-after-tomorrow#s4000)，深入討論如何在虛擬世界中設計審議程序、加入建築師的視野，並即時與其互動。目標在於讓參與審議程序成為一種享受——就像收看、演出 3D IMAX 電影。

今天，HTC Vive 與 Oculus 的虛擬桌面共用工具已經面世，行動裝置的「白日夢」機型也將在九月登場。在九月時 au 會再次造訪巴黎，將自己的 3D 模型傳送到杭州中國美術學院（CAA）——並且用虛擬實境遙現，與網絡社會研究所（caa-ins）的朋友錄下互動，未來任何人都可以重新進入虛擬空間參與。

如果成功，我們會將這項實驗[擴展至全球](https://www.facebook.com/notes/%E5%94%90%E9%B3%B3/%E9%87%8D%E6%96%B0%E5%89%B5%E9%80%A0%E6%B0%91%E4%B8%BB/1275887265773824)。


[https://www.youtube.com/watch?v=LccR-9a\_Y20&list=PLoe9GsfO1mjmWHwzo\_1JPIzUllL4C6yTN&index=2](https://www.youtube.com/watch?v=LccR-9a_Y20&list=PLoe9GsfO1mjmWHwzo_1JPIzUllL4C6yTN&index=2)

## 初步時程

> 基本想法是：把兩天十六小時的黑客松，拆成六周（每周同步兩小時、異步兩小時）進行。
> [name=Audrey T]

> VR 為異步（au 周一錄製 2hr，參與者在周一到周四之間用 2hr+ 時間互動），CAA 為同步。
> [name=Audrey T]


2015-12 落地松《新作一個杭州人》
- [x] 建築、天氣、空間聽覺化：[:emoji_1f3a7:](https://github.com/hACKbUSTER/Renaissance) [〈潛望鏡〉](https://github.com/hACKbUSTER/Renaissance)

### 2016-06 籌備

- [x] 6/10 teleconference kickoff: au, sunquan, zangcheng, luruiyang, littlered

### 2016-07 器材

- [ ] caa-ins: PixPro 4K (photogrammetry room modeling of CAA)
- [ ] caa-ins: Vive #1
- [ ] au: Intel RealSense F200 (avatar modeling)

### 2016-08  空間

- [ ] 異步空間（虛擬: VR）開放預覽
- [ ] 同步空間（實體: CAA）開放報名（現場參與者 ~30 人）

### 2016-09 挖坑

- [ ] 9/19 VR: 解說 g0v 年會及大小松材料
- [ ] 9/22 CAA: 自我介紹、專案發想

### 2016-10 跳坑

- [ ] 10/17 VR: 組隊完成
- [ ] 10/20 CAA: 分組討論互動空間、協作架構
- [ ] 10/24 VR: 遠端協作者提供技術、設計資源
- [ ] 10/27 CAA: 坑形整併
- [ ] 10/31 VR: 草圖展示及回饋

### 2016-11  填坑

- [ ] 11/3 CAA: 實體作品實作
- [ ] 11/7 VR: 作品數位化、建模上傳
- [ ] 11/10 CAA: 錄製、編輯展示影片
- [ ] 11/14 VR: 線上參與網絡社會年會
- [ ] 11/16 CAA+VR: Demo Day
- [ ] 11/17 CAA: 成果交接給第壹次百姓松（@ [Medialab Prado](http://medialab-prado.es/article/herramientas-para-una-democracia-real-2016)，au 同樣以遙現方式參加）

## 硬體元件

caa-ins:
- [ ] 2 * HTC Vive
- [x] 2 * Kodak PixPro 4K

au:
- [x] 1 * HTC Vive
- [x] 3 * Kodak PixPro 4K
- [ ] 1 * Intel RealSense F200
- [ ] 1 * Leap Motion (Universal VR Mount)

## 軟體元件

開放源碼
- [x] [High Fidelity](https://highfidelity.io/) (domain: hifi://caa-ins)
- [x] [Sandstorm](https://sandstorm.io/)
- [x] [Hackpad](https://pad.g0v.link)
- [x] [MakeHuman](http://www.makehuman.org/)
- [ ] [Python Photogrammetry Toolbox](http://arc-team-open-research.blogspot.tw/2012/12/how-to-make-3d-scan-with-pictures-and.html)
- [ ] [VizCities](http://vizicities.com/)

非開放源碼 （但支援開放格式匯出、匯入）
- [ ] Google [Tilt Brush](https://www.tiltbrush.com/)
- [ ] Adobe [Fuse](http://www.adobe.com/products/fuse.html)
- [ ] Valve [Destinations Workshop Tools](http://store.steampowered.com/app/453170)
- [ ] [ReconstructMe](http://reconstructme.net/)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_8fe1dab2f30bbc342f62fedab5f50cf5)

## 疑難排除

### High Fidelity

- 在開啟瀏覽器時按下滑鼠右鍵，會讓自己暫停（出現按任意鍵繼續的圈圈），但是因為輸入被瀏覽器（或其他視窗）吃掉，無法繼續。此時勿將顯示模式切回 Desktop ，可能會讓滑鼠在 HMD 模式下無法作用。按 Ctrl 鍵解除暫停才是正解。
- 在 Edit 模式下加入 web view 時，如果錯誤地將它放太大，會讓 High Fidelity Interface 無法回應，甚至讓 Windows 無法正確認識你的 HMD ，這時請小心地利用還能操作的空檔，把調壞的東西刪除即可。
- 目前 Script Editor 無法在 VR 下使用，就算在 VR 模式開了它，也只能在 Desktop 模式看到，適合先想好再動手，而不是在 VR 世界中邊做邊改。
- 雖然沒有右鍵菜單，但一樣可以用 \`Ctrl-C\` 等 hotkey 。
- 如果想將 Marketplace 裡的內容搬到 caa-ins 內，可以用 browser 登入 [Marketplace](https://highfidelity.io/marketplace) ，找到想要的內容，點擊「Get Item」，會得到一個 JSON 檔，以 TeaHouse 為例：
```
{
  "Entities": [
    {
      "clientOnly": 0,
   "compoundShapeURL": "https://hifi-content.s3.amazonaws.com/DomainContent/Home/JJAssets/teahouse/teahouse_Hull4.obj",
      "created": "2016-06-20T21:42:43Z",
      "dimensions": {
        "x": 11.2451810836792,
        "y": 6.7597455978393555,
        "z": 10.591434478759766
      },
      "id": "{6a5ec39d-3c52-4fae-a601-1c2b43cf8786}",
      "marketplaceID": "26b76914-6662-469a-a070-a8a601f212ac",
   "modelURL": "https://hifi-content.s3.amazonaws.com/DomainContent/Home/JJAssets/teahouse/teahouseHiFi_RoofV2.fbx",
      "owningAvatarID": "{00000000-0000-0000-0000-000000000000}",
      "queryAACube": {
        "scale": 33.72397994995117,
        "x": -16.861989974975586,
        "y": -16.861989974975586,
        "z": -16.861989974975586
      },
      "registrationPoint": {
        "x": 0,
        "y": 0,
        "z": 0
      },
      "shapeType": "compound",
      "type": "Model"
    }
  ],
  "Version": 60
}
```
    將其中 \`compoundShapeURL\` 與 \`modelURL\` 指向的檔案抓下來，接著按 [The Sandbox Asset Server](http://blog.highfidelity.com/blog/2016/5/3/the-sandbox-asset-server) 的說明，上傳到 Asset Server ，再取得 \`atp:/\` 開頭的 URL ，就能替換掉 Entity 本來的 model 。

