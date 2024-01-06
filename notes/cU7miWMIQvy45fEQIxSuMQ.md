---
title: "NVDA 無障礙數學報讀"
tags: hackpad
---

# NVDA 無障礙數學報讀

> [點此觀看原始內容](https://g0v.hackpad.tw/lJMlFXtAcBt)


坑主：曾奕勳（[雲端千眼平台](http://www.edocumentservice.org/) 開發者，本身為視障朋友）
協力：au

[NVDA](https://www.nvaccess.org/)（NonVisual Desktop Access）是一套開源的螢幕閱讀器。目前中文數學網頁報讀，是採取非開源的 MathPlayer 軟體，但它有不少問題，例如：

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_baeb0e9878ac04e5e792f0b104d52b1a)
會報讀成：
    「x 等於 分數 2 a 分子 減 b 加減 的平方根 b 平方 減 4  a c 結束根號 結束分數 」

其中「的平方根」的讀法難以理解，甚至有些符號（微分、積分）沒中文直接會唸英文。

理想狀況下，應報讀成：
      「x 等號 開始分數
                 2 a
             分之
                  負數 b 加減號 開始平方根
                       b 的平方 減號 4 a c
                  結束平方根
           結束分數」

但目前沒有開源的 MathML 轉中文引擎，僅英文有 [ChromeVox](https://github.com/cynthia/chromevox/blob/master/speech_rules/mathml_store_rules.js) 。

徵求跳坑（意者請[連絡坑主](http://www.edocumentservice.org/genericUser/contact_us/)）：
- [ ] 將 ChromeVox 規則（JavaScript）中文化，或
- [ ] 寫一套 MathML 轉 NVDA speech command 的 plugin（Python）

補充說明：
- NVDA有定義MathML處理的物件介面規格，可自行寫轉換程式進行處理，且NVDA有附加元件擴充供能，即使PR官方無納入，也可透過附加元件發佈。
- 坑主之前幫wiris翻譯時看到不錯的做法概念，讓順序也可以自訂。主要做法是去研究MathML的規範並整理成一條一條的rule與文字化內容，當看到式子內有對應的rule就找對應的文字化內容。
- 像分數的例子中，就會類似「開始分數->(分母)->分之->(分子)->結束分數」除了括號內的部份是用遞迴往下一層外，其他三項是可自訂的且五項的順序也可調整，會較有彈性。

參考文件：
- [https://www.nvaccess.org/files/nvda/documentation/developerGuide.html](https://www.nvaccess.org/files/nvda/documentation/developerGuide.html)
- [https://addons.nvda-project.org/devDocs/devDocs.en.html](https://addons.nvda-project.org/devDocs/devDocs.en.html)

範列 MathML 源碼：

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_57cdf87e7e284cbf9cd32695e7fb5f1a)

```
<math>
 <mrow>
  <mi>x</mi>
  <mo>=</mo>
  <mfrac>
   <mrow>
    <mo form="prefix">−</mo>
    <mi>b</mi>
    <mo>&PlusMinus;</mo>
    <msqrt>
     <msup>
      <mi>b</mi>
      <mn>2</mn>
     </msup>
     <mo>−</mo>
     <mn>4</mn>
     <mo>&InvisibleTimes;</mo>
     <mi>a</mi>
     <mo>&InvisibleTimes;</mo>
     <mi>c</mi>
    </msqrt>
   </mrow>
   <mrow>
    <mn>2</mn>
    <mo>&InvisibleTimes;</mo>
    <mi>a</mi>
   </mrow>
  </mfrac>
 </mrow>
</math>


