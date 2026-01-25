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

- 點開miniconda
![](https://g0v.hackmd.io/_uploads/SkpknLQ8-e.png)

![](https://g0v.hackmd.io/_uploads/ByWfh8X8bg.png)
- 打開系統內容，點擊環境變數
![](https://g0v.hackmd.io/_uploads/rk-B72IXUZg.png)
- 點path，按編輯
![](https://g0v.hackmd.io/_uploads/H1MPhUQUZx.png)
- 新增下面三條路徑
![](https://g0v.hackmd.io/_uploads/B1gd53ImI-g.png)
- 打開powershell，輸入`conda --version`，檢查版本
![](https://g0v.hackmd.io/_uploads/B1elk6U7L-e.png)
## [安裝](https://isaac-sim.github.io/IsaacLab/main/source/setup/installation/pip_installation.html)
```
conda create -n env_isaaclab python=3.11
```
```
conda init
```
- 執行完後關掉powershell，重開一個輸入
```
conda activate env_isaaclab
```
![](https://g0v.hackmd.io/_uploads/Skg1LCL7LWx.png)

- Install a CUDA-enabled PyTorch build that matches your system architecture:
```
pip install -U torch==2.7.0 torchvision==0.22.0 --index-url https://download.pytorch.org/whl/cu128
```
- Install Isaac Sim pip packages:
```
pip install "isaacsim[all,extscache]==5.1.0" --extra-index-url https://pypi.nvidia.com
```
## [Verifying the Isaac Sim installation](https://isaac-sim.github.io/IsaacLab/main/source/setup/installation/pip_installation.html#verifying-the-isaac-sim-installation)
- Make sure that your virtual environment is activated (if applicable)

- Check that the simulator runs as expected:
```
isaacsim
```
- 打開後，點選隨機一個內建的範例場景，點選Open With New Edit Layer，嘗試儲存

![](https://g0v.hackmd.io/_uploads/ryEgTDQLbg.png)


## [安裝Isaac Lab](https://isaac-sim.github.io/IsaacLab/main/source/setup/installation/pip_installation.html#installing-isaac-lab)
- Cloning Isaac Lab:Clone the Isaac Lab repository into your project’s workspace
```
git clone https://github.com/isaac-sim/IsaacLab.git
```
- install
```
cd IsaacLab
```
```
isaaclab.bat --install
```
- Verifying the Isaac Lab installation
```
isaaclab.bat -p scripts\tutorials\00_sim\create_empty.py
```
## [workstation install](https://docs.isaacsim.omniverse.nvidia.com/latest/installation/install_workstation.html)

- [Download Isaac Sim](https://docs.isaacsim.omniverse.nvidia.com/latest/installation/download.html)，下載windows版本的
![](https://g0v.hackmd.io/_uploads/Hkg70RFm8-g.png)

- 離開conda環境
```
conda deactivate
```
![](https://g0v.hackmd.io/_uploads/Skf1TFQI-l.png)

```
mkdir C:\isaacsim
cd ./Downloads/
tar -xvzf "isaac-sim-standalone-5.1.0-windows-x86_64.zip" -C C:\isaacsim
cd C:\isaacsim
post_install.bat
isaac-sim.selector.bat
```
![](https://g0v.hackmd.io/_uploads/Sk58W5QI-e.png)

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


