# iOS plugin in Unity

tag： wifi、bluetooth

people(member)、device(IDFV)、資料型態

::: info
iOS平台有許多關於權限問題要處理，以防開發者們不會用，故寫這份以提供後面的人
:::

:::warning
你若是開發iOS APP必須有開發者帳號，這實驗室有提供，可以去實驗室wiki找
:::

## 安裝

## 註冊

iOS 開發的時候會需要辨認你的APP都是用identifier，啟用 **APP Group** 就需要你去網路上註冊

## 設計流程

設計上會分成三層，分別是 Unity 中的 **C#** 世界以及 iOS 原生 **Objective-C** 世界
最後是連接這兩個世界的 **C++** 介面層(橋接層)，

![操](https://g0v.hackmd.io/_uploads/BkvdrWhXle.png)

![](https://g0v.hackmd.io/_uploads/rJxWsrbhQeg.png)

## url scheme
xrlab-{productname}://
xrlab-{productname}://?{參數1}={值1}&{參數2}={值2}...
你的productname不能有 `_`之類
