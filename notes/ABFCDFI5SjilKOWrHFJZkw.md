---
title: "如何在Mac上分流直播"
tags: hackpad
---

# 如何在Mac上分流直播

> [點此觀看原始內容](https://g0v.hackpad.tw/OvlqGpv6NfL)


有時候，我們會想要分流政府的直播到Facebook、Youtube或Livehouse.in等平台，這個指南說明該如何操作。

首先，可以先參考Livehouse.in的[這份指南](https://event.livehouse.in/zh-TW/tutorial/obs-mac.html)下載OBS。也請[在此下載Soundflower](https://github.com/mattingalls/Soundflower/releases/tag/2.0b2 )。

接著，在安裝完畢Soundflower之後，把mac的音效輸出改到Soundflower(2ch)，輸入不用改變：

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_78a67aef5c9e9530316ec9c0c6d6e8e8)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_93033be6f97fb1186dddeb52f54bdf3d)

在OBS中，先新增視窗擷取，選取要的視窗：

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_8c94affd80e313325f01ec987621e695)

打開設定->音效，把輸入改為Soundflower(2ch)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0ac0f66e27db28c9ec6dcca96393d13c)

最終OBS設定應該像這個樣子：

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_699579096c5e5a574bc76367811104ca)

以上，就完成了設定。







