## 代訂
download:https://github.com/NVIDIA-Omniverse/kit-app-template
## Clone the Repository(no)
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
