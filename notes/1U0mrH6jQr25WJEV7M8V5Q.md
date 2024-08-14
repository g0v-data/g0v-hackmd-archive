**Delridge16**

# Build prerequisite:
## /* OS */
Ubuntu 18.04 LTS

## /* update / upgrade */
    sudo apt update
    sudo apt upgrade

## /* python 3.7.5 */
    sudo add-apt-repository ppa:deadsnakes/ppa
    sudo apt update
    sudo apt install python3.7

## /* set alternatives */
    sudo update-alternatives --install /usr/bin/python python /usr/bin/python3.7 1
    sudo update-alternatives --config python

## /* Missing lib / tool */
    python -m pip install gitpython
    python -m pip install Cython
    python -m pip install numpy==1.18.5
    python -m pip install sentry-sdk
    python -m pip install boto
    python -m pip install hashlib
    python -m pip install argparse
    sudo apt install pkg-config
    sudo apt install libssl-dev
    sudo apt insall autoconf-archive
    

## Follow README_build.md to the end

    sudo apt install software-properties-common gcc-multilib mtd-utils:i386 subversion patch patchutils bison
    sudo apt install libc6-dev rand bc openssh-client libxml-dom-perl zlib1g zlib1g-dev libz-dev libcurl4-openssl-dev libncurses5
    sudo apt install libncurses5:i386 python-numpy doxygen cppcheck libpcre3-dev  wget curl make autoconf automake libtool
    sudo apt install m4 flex rsync python3-dev python-dev python-pip ruby util-linux fakeroot unzip lcov

## START BUILD
    cd {yourfolder}/delridge-bmc/BonitoBase
    sudo ./configure.sh
    sudo ./build.sh -c full -p Delridge16


---

# IPMI COMMAND

    ipmitool raw 0x34 0x50 0x01   [GET JOBD1] 
    ipmitool raw 0x34 0x51 0x01 0x01 ( SET off:0 on:1 cycle:2)

    ipmitool sdr elist
    ipmitool mc reset cold
    ipmitool fru edit 0 field p 8 MCHP  /* FRU EDIT */


---

# CODE READ
## AC cycle
**ipmi oem cmd 0x6c**
1. check power status 
2. Check virtual Power Drain Event
3. issue command and return complete code

## MAIN
**init**
PDB, JBOD, ODM_INFO, WDT, FSC, POST_TASK
**start compmanager**
system("cd /usr/local/bin/;./compmanager start&");

**OEMPostTask**
1. GPIO_BIOS_POST_CMPLT_FCOUT_N(GPIO_AA7) (Platform_CheckPOSTEnd read GPIO)
2. GET TJMAX :temperature where the CPU will start to throttle (reduce performance to cool down)

## PIC
在伺服器中，**PIC（Platform Interface Controller）**芯片通常指的是一種用於管理系統電源、監控硬件健康狀況以及提供底層硬件接口的微控制器。這種芯片在伺服器內部的主要功能包括：

1. 硬件監控
電壓監控：監控伺服器內部的各種電壓軌道，確保它們在安全範圍內運行。
溫度監控：監控伺服器內的溫度感測器，包括CPU、GPU、內存、電源等，以防止過熱。
風扇控制：根據溫度監控結果調整伺服器內的風扇速度，以優化散熱效果。
2. 電源管理
電源序列控制：在伺服器啟動或關閉時，控制不同電源軌道的開啟或關閉順序，確保系統穩定性。
待機管理：在低功耗模式下管理電源供應，確保伺服器在休眠狀態下仍能保持基本功能（如網絡喚醒）。
3. 故障診斷與報警
事件記錄：記錄硬件故障事件，如電壓異常、過熱等，並在必要時觸發報警。
指示燈和蜂鳴器控制：控制伺服器上的LED指示燈和蜂鳴器，提示運維人員注意硬件狀態。
4. 系統初始化
初始化外設：在伺服器啟動時，初始化各種外設和接口，如PCIe、SATA、USB等，以便操作系統接管控制。
自檢（POST）協助：在伺服器開機自檢過程中協助處理硬件檢查和初始化任務。
5. 通信與接口管理
I2C/SMBus 管理：負責處理與伺服器內部其他硬件的低速通信，這通常包括與電源管理單元（PMU）、溫度感測器等設備的通信。
串行接口控制：管理與外部管理系統（如BMC，Baseboard Management Controller）的串行通信接口。
6. 固件管理
更新固件：負責管理和更新伺服器內的低層固件，這些固件通常控制著伺服器硬件的基本功能。
保護固件安全：提供加密和驗證機制，確保固件更新過程的安全性，防止惡意攻擊。
總結
在伺服器中，PIC芯片是一個關鍵的底層控制單元，負責監控、管理和保護伺服器的硬件，確保伺服器穩定高效地運行。它通常扮演著“系統管理者”的角色，處理各種低層次的硬件操作，並為伺服器的其他組件提供支持。

**LEARN FROM CODE/FW_SPEC**
FAN is controlled by BMC default, if BMC timeout/offline, PIC will take FAN control and pull to full speed.
0x1A: Before BMC ready, PIC will refer to this duty as default AC ON fan duty.
0x1B: When BMC is timeout/offline, PIC will refer to this duty as MAX fan duty.
If PIC meet I2C lock issue.
1. set I2C SDA/SCL to high.
2. PIC tries to pull nine clocks to release other dev.
3. PIC reset itself.
**補充:在I2C通訊中，每個字節由8位數據加上一位確認位（ACK或NACK）組成。因此，在傳輸一個字節後，從設備會在第9個時鐘脈衝時拉低SDA線以發送ACK信號。如果通訊過程中發生錯誤或從設備在等待下一個指令時出現問題，SDA可能會被從設備拉低，並保持在低電平，導致總線卡住。
送9個SCL時鐘脈衝的目的是模擬完整的字節傳輸過程，幫助從設備完成其內部狀態轉換，並釋放SDA線**

get JBOD/SLED present info
set JBOD/SLED on/off
set LED for storage nodes
get current state of LED for storage nodes
reset JBOD/SLED controller
fan control
cable prsent
pcie mode