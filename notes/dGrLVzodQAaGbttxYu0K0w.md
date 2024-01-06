---
title: "vTaiwan 小松會議記錄 2017.02.03"
tags: vTaiwan小松, hackpad
---

# vTaiwan 小松會議記錄 2017.02.03

> [點此觀看原始內容](https://g0v.hackpad.tw/39ZFJ5FNcx1)


Bugs / issues: [https://github.com/g0v/vue.vtaiwan.tw/issues](https://github.com/g0v/vue.vtaiwan.tw/issues) \- 可蒐集 issue
Story Board: [https://github.com/g0v/vue.vtaiwan.tw/projects/1](https://github.com/g0v/vue.vtaiwan.tw/projects/1) \- 可放團隊準備做的事情與筆記（對外是 read-only）


關於 [https://www.vtaiwan.org.tw](https://www.vtaiwan.org.tw) 的後續問題



### Hosing server

- 請國發會發函給科技部交接 org，科法所就可轉讓出來

### 內容

- 國外法治觀測區
    - 採顧問制：當議題有需求要研究國外的法制時再予以顧問。
    - 「國外法治觀測專區」則直接移除
- 電子報
    - 每個月一次自制電子報內容 （可宣傳用）
- 影音專區
    - 直接用 youtube 連結

### vue.vtaiwan 版面更新

[https://github.com/g0v/vue.vtaiwan.tw](https://github.com/g0v/vue.vtaiwan.tw)
[https://xd.adobe.com/view/ee22173d-47c1-43ad-8020-cd6c210b84e3/](https://xd.adobe.com/view/ee22173d-47c1-43ad-8020-cd6c210b84e3/)

- [ ] 訂閱電子報
    - 原電子報內容，網誌，以及近期議題更新，預告即將開始的議題等等。
    - 電子報寄送頻率：一個月一次。
    - 寄送對象：
        -   \- 科法所的電子報 (會內的訂閱者)
        -   \- MailChimp 名單
- 影音專區
    - footer

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d2bb708e1777bec1b2e3e5d79283a44c)

- [ ] 影音專區改成 footer 裡的[連結](https://www.youtube.com/channel/UChC85hbUuDAvFpc7Uuj69DA/videos?flow=grid&view=0&sort=dd&live_view=500)

- [ ] 關於我們 (on footer) -> 連絡我們（support）-\> form post on /c/meta
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_904b5d8d7dffa3b45059cf7d176982af)


社群

清點 vTaiwan 的意見徵集宣傳：
- 電子報訂閱
- 臉書追蹤
- 聯絡我們->信箱回信->電子報訂閱
- 針對議題的個人 (專家學者) 邀約


###  實作 Notes

> 舊的 gh-pages 備份到: [https://github.com/g0v/vue.vtaiwan.tw/tree/gh-pages-old](https://github.com/g0v/vue.vtaiwan.tw/tree/gh-pages-old)
> [name=isacl]

> 從 g0v.tw [https://github.com/g0v/g0v.tw/blob/master/deploy](https://github.com/g0v/g0v.tw/blob/master/deploy) 抄了 deploy script 過來
> [name=isacl]

  \- 需要一個測試 domain, ex: dev.vtaiwan.tw => 改成  [**http://vue.vtaiwan.tw**](http://vue.vtaiwan.tw) (DONE)
目前已可從 [**http://vue.vtaiwan.tw**](http://vue.vtaiwan.tw) 連到最近一次 deploy 的內容

#### [vue.vtaiwan.tw](http://vue.vtaiwan.tw/)  遇到 https 連線問題時：

 **chrome**:
在網址列打 [chrome://net-internals/](chrome://net-internals/#hsts)[#hsts](https://g0v.hackpad.tw/ep/search/?q=%23hsts&via=39ZFJ5FNcx1)
於 Delete domain 處輸入 \`vtaiwan.tw\` 並點 Delete
  root cause:
    在 vtaiwan.tw ngnix 內 sub header 拿掉 sub-domain
> 拿掉 includeSubDomains (by au)
> [name=isacl]

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6ee44fe4bbab279eb9363485b69719c9)



--
[版面更新](https://xd.adobe.com/view/ee22173d-47c1-43ad-8020-cd6c210b84e3/screen/62315d45-8d88-496e-9a80-6de9802d117d/footer-demo) (footer)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c534606337e190716f2833bbc559adff)

訂閱電子報版面
（參考）
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_90df62c4aa5920e609eccdd5de6bc36f)

[footer](https://xd.adobe.com/view/ee22173d-47c1-43ad-8020-cd6c210b84e3/screen/62315d45-8d88-496e-9a80-6de9802d117d/footer-demo)
[關於 vTaiwan](https://xd.adobe.com/view/ee22173d-47c1-43ad-8020-cd6c210b84e3/screen/89346e07-fcdd-45b1-98e2-eef16e1602cd/about-vTaiwan)


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_cf8b1c489fbe764f6b96d91c41e17853)


[vTaiwan 電子報 (閱讀與訂閱)](https://xd.adobe.com/view/ee22173d-47c1-43ad-8020-cd6c210b84e3/screen/a0a364eb-4485-4697-bd73-df3246f2d168/subscription)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_b3976aee30b23f0b9dc94b3efa2a84a4)

[ vTaiwan 聯絡我們](https://xd.adobe.com/view/ee22173d-47c1-43ad-8020-cd6c210b84e3/screen/75b961a5-0235-4725-8e07-0db223d7e24e/contact-us)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_abea330a865aad26b0e087051fb47d78)



 some chat about vr...

 au: 軟體運鏡

 360 配人臉辨識 AI 聲音
 stich

social & interaction

直播互動

VR 互動 (後製)

jacqlyn: 我們要如何讓台灣變成一個美麗的地方？


