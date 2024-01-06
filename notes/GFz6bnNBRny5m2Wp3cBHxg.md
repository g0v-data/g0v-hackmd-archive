# Appium 第二章

adb command refer
https://developer.android.com/studio/command-line/adb

## 獲取app入口
 - adb logcat|grep Displayed
     - log example
     ```
     11-05 12:25:05.853   438   518 I ActivityManager: Displayed com.game.wt.poc.t01.rel/com.iv.phoneclient.ui.SplashActivity: +631ms
     ```

## 開啟app
 - adb shell am start -n ${packageName}
     - example
     ```
     adb shell am start -n com.ag888.ams.staging/com.ag888.ams.ui.SplashActivity
     ```
## 清除緩衝
 - adb shell pm clear ${packageName}
     - example
     ```
     adb shell pm clear com.iv.phoneclient.staging
    ```

## Monkey Testing
- adb shell monkey -p ${packageName} -s 2  -v 100
    - example
    ```
    adb shell monkey -p com.iv.phoneclient.staging -s 2  -v 100
    ```
 
## Android 常用指令 
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f3f8be521d34937956dd79647e500ca5.png)


## adb shell command

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b75cef246ba2566158ce0fc6af65f001.png)

## Android 性能統計 dumpsys


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b9a7ce7761d663814f991c32b923bd19.png)

## Android Input Command

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f3e49c60e01c2b7a2481f28b8d52a411.png)

## 獲取App訊息

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0a59657ee0bba5db4f55b5d178620020.png)
