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


