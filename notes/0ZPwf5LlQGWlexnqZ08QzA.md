# Omniverse install
[toc]

download:https://github.com/NVIDIA-Omniverse/kit-app-template
## 限制

==驅動程式需求==
[安裝驅動程式](https://www.nvidia.com/zh-tw/drivers/details/258684/)
![](https://g0v.hackmd.io/_uploads/B1g5M6wfE-l.png)

* Driver Branch:最低R535，570.00–573.39會有問題不能用
* Driver 類型:Studio
* CUDA:12.x

==開啟「初始畫面」會吃多少資源？==(使用顯卡為RTX A2000)
![](https://g0v.hackmd.io/_uploads/ryhfOiMNbe.png)


## 各系統適合的driver
![](https://g0v.hackmd.io/_uploads/HJPnzIm8-e.png)
[nvidia driver 580.88 連結](https://www.nvidia.com/zh-tw/geforce/drivers/results/251260/)
```
選自訂
```
![](https://g0v.hackmd.io/_uploads/Byev1NIQ8-l.png)
```
勾選執行全新安裝
```
![](https://g0v.hackmd.io/_uploads/HyeNVVUm8bx.png)


```
安裝完後，按win+r，輸入regedit
```

![](https://g0v.hackmd.io/_uploads/rJIEUIX8Zx.png)


```
找到電腦\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\FileSystem
```
![](https://g0v.hackmd.io/_uploads/ByxMXDU7LZx.png)

```
點開longpathenable，輸入1
```
![](https://g0v.hackmd.io/_uploads/HyDKw87LZx.png)


- [安裝miniconda(powershell)](https://www.anaconda.com/docs/getting-started/miniconda/install#powershell)

```
Invoke-WebRequest -Uri "https://repo.anaconda.com/miniconda/Miniconda3-latest-Windows-x86_64.exe" -OutFile ".\Miniconda3-latest-Windows-x86_64.exe"
```

## Clone the Repository
```
git clone https://github.com/NVIDIA-Omniverse/kit-app-template.git
```
![](https://g0v.hackmd.io/_uploads/r1QtVvfEbg.png)

```
cd kit-app-template
```
## Create and Configure New Application From Template

Windows:
```
.\repo.bat template new
```
Linux:
```
./repo.sh template new
```
![](https://g0v.hackmd.io/_uploads/ryBMIPzN-x.png)

## Build
Windows:
```
.\repo.bat build
```


Linux:
```
./repo.sh build
```



## Launch(每次要開啟Omniverse時，下這個指令，會開啟初始畫面)
Windows:
```
.\repo.bat launch
```
雙顯卡用這個:
```
.\repo.bat launch  --/renderer/multiGpu/enabled=false
```

Linux:
```
./repo.sh launch
```


## 初始畫面
![](https://g0v.hackmd.io/_uploads/HkxnH9Oz4-g.png)


