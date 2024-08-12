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
sudo apt install pkg-config
sudo apt install libssl-dev
sudo apt insall autoconf-archive

## Follow README_build.md to the end



---

# IPMI COMMAND

get: ipmitool raw 0x34 0x50 0x01 [JOBD1]
set: ipmitool raw 0x34 0x51 0x01 0x01 (off:0 on:1 cycle:2)

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
