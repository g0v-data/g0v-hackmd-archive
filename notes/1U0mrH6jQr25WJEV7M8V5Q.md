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
    sudo apt-get install libssl-dev

## Follow README_build.md to the end

    sudo apt install software-properties-common gcc-multilib mtd-utils:i386 subversion patch patchutils bison
    sudo apt install libc6-dev rand bc openssh-client libxml-dom-perl zlib1g zlib1g-dev libz-dev libcurl4-openssl-dev libncurses5
    sudo apt install libncurses5:i386 python-numpy doxygen cppcheck libpcre3-dev  wget curl make autoconf automake libtool
    sudo apt install m4 flex rsync python3-dev python-dev python-pip ruby util-linux fakeroot unzip lcov

## START BUILD
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
ipmi oem cmd 0x6c
1. check power status 
2. Check virtual Power Drain Event
3. issue command and return complete code

## MAIN
INIT pdb, jbod, odminfo, wdt, fsc, posttask
system("cd /usr/local/bin/;./compmanager start&");

OEMPostTask
1. check GPIO_BIOS_POST_CMPLT_FCOUT_N(GPIO_AA7)
2. GET TJMAX :temperature where the CPU will start to throttle (reduce performance to cool down)