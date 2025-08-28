# Unity Building APP in iOS

:::info
Building 到 iOS裝置上要透過xcode
所以你會需要一台有xcode的Mac
實驗室剛好有一台粉紅色，密碼去問學長姐
> hint：老樣子
:::

:::warning
伴隨版本迭代我的UI可能跟你不同，除了圖片我會盡量用文字說明
:::

## Step 1：建置Unity iOS

安裝到iPad前 你會需要先有檔案，在Unity中你要先點右下`Switch Platform`到 iOS 中
圖中我目前是用Android
![BuildSettings](https://g0v.hackmd.io/_uploads/Syez0rBpKxl.png)
> 路徑是 File->Build Settings (Unity 6 是 File->Building Files)
> ![Unity頂端](https://g0v.hackmd.io/_uploads/SkgAUIraYxe.png)

切換平台後就可以建置執行檔
![build](https://g0v.hackmd.io/_uploads/r1WVDB6Yge.png)
點擊`Build`，圖片中我還是在android平台但你要在iOS平台
> iOS建置出來的不像是android 單一個檔案(.apk)，而是一整個資料夾，所以你需要新增資料夾

你build出來會類似下圖，我的專案名字叫做`LabFrame_iOS`建置出來的資料夾名稱是`ParameterTest`
![圖片](https://g0v.hackmd.io/_uploads/ryZeOSatge.png)

## Step 2：將檔案搬到Xcode

因為要透過xcode轉譯到iPad或是iOS裝置上，所以我們要將資料搬移到Mac上面
那我是透過Google Drive，用實驗室的帳號即可(用完記得刪除)
用硬體也可以
![drive](https://g0v.hackmd.io/_uploads/r1UvcSTYgl.png)

將檔案下載或是搬到Mac後，解壓縮出來會是這張圖