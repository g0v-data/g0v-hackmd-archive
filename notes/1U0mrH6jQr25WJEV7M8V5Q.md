**Delridge16 build / command**

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