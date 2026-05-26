Qualcomm

1_CHK_PN
* get system PN
* PN [S15R100040] found in CFG -> PASS

2_UPD_VAR

* get BMC IP, mac address, system SN, GPU SN (LEFT_GPBBSN_69, RIGHT_GPBBSN_69)
* SN=265654070023
* left GPB SN
* right GPB SN 
* 確認左右兩張GPU board 有裝及SN 正確

3_SET_GPU_SN65

* check left GPU board SN 與 .bom file 一致
* BOM_FILE=/autotest/project/P029_KURT/265654070023_2026-05-25_15-32-25/265654070023.bom

4_ECHO_RESULT_T

* 切tera term 畫面
* Term /dev/tty1 Termsize 50 160 Term_h 50 Term_w 160 Term_h1 17 Term_h3 18 Term_w1 40 Term_w3 40

5_TRY_BMC_USER

* ping BMC IP, try BMC ps, 紀錄BMC info (mc info)
* Try BMC User: root passwd: 0penBmc
* Try BMC User: admin passwd: Pega#1234
* ipmitool -I lanplus -U admin -P Pega#1234 -H 192.168.10.159 mc info > dmp_ipmitool_try_acc_2.raw

6_CHK_SWITCH_LINK
* check bdf, speed, width under OS
* check USP, DSP (dsp can downgraded)
* CAP 理論能力
* STA 實際

7_CHK_FW_VER
connect to UUT(測試機)
從測試機用ssh connet to server
get version, 在跟expected result 比較
* cd /home/user/Downloads/qaic-factory-tools-2.2.1.8/factory_self_test_tool/deb && chmod +x ./P029_KURT.sh && ./P029_KURT.sh --chk-gpu-ver
* 在server上執行/opt/qti-aic/tools/qaic-util -q
* output: 
    * QID 0
	HW Version:0.3.2.0
	FW Version:2.2.1.8
	NSP Version:2.2.1.1
    
8_PRG_FRU
把 GPU 板的「序號 / PN / 製造資訊」寫進硬體（FRU），並確認寫成功
* 拿原始的fru檔, 設定檔來改
    * SrcFruBin=kurt_gpu.bin
        FruCfg=Fru.cfg
* copy required tools
* /fru_cfg_upd.sh
    ./fruuti
    ./fruuti.jar
* 把SN, PN 寫入
    * Board Serial Number="${SN_65}"
        Board Part Number="${PN_65}"
* 產生新的FRU binary
    * Generate binary "New_kurt_gpu.bin"
* copy binary to UUT and run FRU write/check on UUT local OS
![](https://g0v.hackmd.io/_uploads/SyDiBqflMx.png)

```
左邊 = 你寫的資料
右邊 = 從硬體讀回來的資料
== = 一樣
```

9_CHK_QID_BOOTLOG_ALL
10_CHK_QID_BOOTLOG
11_SOC_FW_UPD -> 卡資訊都正常Skip qaic-firmware-updater
把這張 GPU 卡從開機到啟動完成的所有韌體流程列出來
cat /sys/kernel/debug/accel/0000:9a:00.0/bootlog
* 看卡狀態Status: Ready
* 看卡速度
    * Max Link Speed: 32GT/s
        Current Link Speed: 32GT/s
        Current Link Width: x16
* 看卡溫度SoC temperature: 57°C / 58°C
* 看卡dram 容量	
    * Dram Total:31299524 KB
	    Dram Free:30812804 KB
* 看負載
    * Networks Active: 0
        Constants Loaded: 0
* 卡power
    * 	Board power(Watts):0.00
	Board TDP Cap(Watts):2400.00
	SOC power(Watts):20.00
	SOC TDP Cap(Watts):80.00

階段  意義
PBL  晶片上電最初啟動 Primary Boot Loader
SBL1 初始化硬體
XBL  載入系統
FW   Load載入韌體

boot 基本資訊 -> 硬體資訊 -> boot loader 流程 (🔌 上電 → 初始化 → 載入韌體 → 準備運作) -> DDR 初始化 -> 電源(PMIC 初始化) 「電源系統正常啟動」

13_SET_FW_INS
* Command: ./install_fw
* Reset the AIC200 card to load the newly installed Factory FW image...!!!
* echo 1 > /sys/bus/mhi/devices/<mhi device pcie addr>/soc_reset

14_CHK_SOC_RST_TEST
* ./qaic_factory_tool_Zion -o soc_reset_test --retry_count 3
一次把所有 GPU 卡 reset（相當於重新開機）
    
15_CHK_QID_OEM
Check QID FW IMAGE_VARIANT
check FW 韌體版本的「類型」

16_CHK_QID_BOOTLOG_ALL
/opt/qti-aic/tools/qaic-util -q
    

17_CHK_CDT_PRO
./qaic_factory_tool -o cdt_program --skutype ultraplus24SOC

* [INFO] CDT PROGRAM TEST
    [INFO] QID 0: Programming CDT to SKU 'ultraplus24SOC'...
    [INFO] Reading current CDT from device QID 0...
    [INFO] CDT is already programmed with the correct version (NORDAU_DCP_3.2.0.bin) for QID 0
    [INFO] Skipping CDT programming

* 寫sku type成ultraplus24SOC
* Please take a moment to reboot your device which will help reflect the changes made by CDT program
    
18_CHK_SOC_RST_TEST
* reset SOC: ./qaic_factory_tool_Zion -o soc_reset_test --retry_count 3
    
19_CHK_QID_TYPE
* check QID Sku type: /opt/qti-aic/tools/qaic-util -q -d 0~23
![](https://g0v.hackmd.io/_uploads/SJl--hpMxfe.png)

20_CHK_L1_L2_PCIE
check GPU link(總共有四個L1, 一個L2)
./qaic_factory_tool -o read_L1_L2_pcie_sw_pwr
    
![](https://g0v.hackmd.io/_uploads/HJoLnpfefx.png)

![](https://g0v.hackmd.io/_uploads/H17F36fxfe.png)

![](https://g0v.hackmd.io/_uploads/rJaOppGxzg.png)


21_CHK_BOARD_PWR
read board power
./qaic_factory_tool -o read_board_pwr

![](https://g0v.hackmd.io/_uploads/B1x5T66feMl.png)



22_CHK_COMPLEX_PWR
read complex power
./qaic_factory_tool -o read_complex_pwr

這樣是一個complex, 一個cluster裡面有6個complex
![](https://g0v.hackmd.io/_uploads/H1oWCaGxGl.png)

23_CHK_COMPLEX_TEMP
read complex temp: ./qaic_factory_tool -o read_complex_temp
    
24_CHK_SOC_TEMP
read SOC temp: ./qaic_factory_tool -o read_soc_temp
一個complex 裡面有一個SOC
![](https://g0v.hackmd.io/_uploads/B15q06fxfe.png)

    
25_CHK_MQ_TEST
測試BW
./qaic_factory_tool -o mq_test --qid 0  --qid1 1
./qaic_factory_tool -o mq_test --qid 2  --qid1 3
./qaic_factory_tool -o mq_test --qid 4  --qid1 5
./qaic_factory_tool -o mq_test --qid 6  --qid1 7
./qaic_factory_tool -o mq_test --qid 8  --qid1 9
./qaic_factory_tool -o mq_test --qid 10 --qid1 11
./qaic_factory_tool -o mq_test --qid 12 --qid1 13
./qaic_factory_tool -o mq_test --qid 14 --qid1 15
./qaic_factory_tool -o mq_test --qid 16 --qid1 17
./qaic_factory_tool -o mq_test --qid 18 --qid1 19
./qaic_factory_tool -o mq_test --qid 20 --qid1 21
    
![](https://g0v.hackmd.io/_uploads/S1BFb0MxMg.png)


26_CHK_NETWORK_TEST
./qaic_factory_tool -o network_test

![](https://g0v.hackmd.io/_uploads/SJgtXf0feGg.png)


27_CHK_IPMI_TEST
./qaic_factory_tool -o ultraplus_ipmi_test --bmcip 192.168.10.159 --slot 11 --device 1 --userid admin --passwd Pega#1234
* sensor_off_cmd: ipmitool -H 192.168.10.159 -U admin -P Pega#1234 -I lanplus raw 0x2e 0x10 0x0a 0x3c 0 0x04 0x00
* slot11_cmd1: ipmitool -H 192.168.10.159 -U admin -P Pega#1234 -I lanplus raw 0x06 0x52 0x03 0xE6 0 0x00
* slot11_cmd2: ipmitool -H 192.168.10.159 -U admin -P Pega#1234 -I lanplus raw 0x06 0x52 0x03 0xE6 0 0x08
* slot11_cmd3: ipmitool -H 192.168.10.159 -U admin -P Pega#1234 -I lanplus raw 0x06 0x52 0x03 0xE0 0 0x01
    
SOC serial number mapping
* select_cluster: ipmitool -H 192.168.10.159 -U admin -P Pega#1234 -I lanplus raw 0x06 0x52 0x03 0xE2 0x00 0x01/0x02/0x04/0x08
    
* select_soc: ipmitool -H 192.168.10.159 -U admin -P Pega#1234 -I lanplus raw 0x06 0x52 0x03 0xE4 0x00 **0x01**
Successfully selected SOC A0
Cluster 0 -> SOC A0 -> SOC Serial: 0xaaa9034e -> Mapping to QID: 21

* select_soc: ipmitool -H 192.168.10.159 -U admin -P Pega#1234 -I lanplus raw 0x06 0x52 0x03 0xE4 0x00 **0x02**
Successfully selected SOC A1
Cluster 0 -> SOC A1 -> SOC Serial: 0x778bd2cc -> Mapping to QID: 22
    
* select_soc: ipmitool -H 192.168.10.159 -U admin -P Pega#1234 -I lanplus raw 0x06 0x52 0x03 0xE4 0x00 **0x04**
Successfully selected SOC A2
Cluster 0 -> SOC A2 -> SOC Serial: 0xbf9a29b8 -> Mapping to QID: 23
    
* select_soc: ipmitool -H 192.168.10.159 -U admin -P Pega#1234 -I lanplus raw 0x06 0x52 0x03 0xE4 0x00 **0x08**
Successfully selected SOC A3
Cluster 0 -> SOC A3 -> SOC Serial: 0x18ee1ede -> Mapping to QID: 20

* select_soc: ipmitool -H 192.168.10.159 -U admin -P Pega#1234 -I lanplus raw 0x06 0x52 0x03 0xE4 0x00 **0x10**
Successfully selected SOC A4
Cluster 0 -> SOC A4 -> SOC Serial: 0xba82bcb2 -> Mapping to QID: 19

* select_soc: ipmitool -H 192.168.10.159 -U admin -P Pega#1234 -I lanplus raw 0x06 0x52 0x03 0xE4 0x00 **0x20**
Successfully selected SOC A5
Cluster 0 -> SOC A5 -> SOC Serial: 0x0402aee8 -> Mapping to QID: 18
    
![](https://g0v.hackmd.io/_uploads/HJUCXCzeGe.png)


28_CHK_SMBUS_IO_TEST
ultraplus_smbus_io_expander_test
* sensor_off_cmd: ipmitool -H 192.168.10.159 -U admin -P Pega#1234 -I lanplus raw 0x2e 0x10 0x0a 0x3c 0 0x04 0x00
* slot11_cmd1: ipmitool -H 192.168.10.159 -U admin -P Pega#1234 -I lanplus raw 0x06 0x52 0x03 0xE6 0 0x00
* slot11_cmd2: ipmitool -H 192.168.10.159 -U admin -P Pega#1234 -I lanplus raw 0x06 0x52 0x03 0xE6 0 0x08
* slot11_cmd3: ipmitool -H 192.168.10.159 -U admin -P Pega#1234 -I lanplus raw 0x06 0x52 0x03 0xE0 0 0x01

select cluster then test (total 4 clusters)
ipmitool -H 192.168.10.159 -U admin -P Pega#1234 -I lanplus raw 0x06 0x52 0x03 0xE2 0x00 0x01/0x02/0x04/0x08
![](https://g0v.hackmd.io/_uploads/Bkl2vLRMlzx.png)

29_PWR_STR_PCIETX
./PowerStress -w PCIETX -r 120 -l PowerStress_PCIETX.log -k
> check power, temp
![](https://g0v.hackmd.io/_uploads/HkeWAURfeMx.png)

30_PWR_STR_PCIERX
./PowerStress -w PCIERX -r 120 -l PowerStress_PCIERX.log -k

> check power, temp
![](https://g0v.hackmd.io/_uploads/HkxGDRfxGe.png)

    
31_PWR_STR_DDR
./PowerStress -w DDR -r 120 -l PowerStress_DDR.log -k
> check power, temp
![](https://g0v.hackmd.io/_uploads/HkFHDCGezl.png)


32_PWR_STR_HVX
./PowerStress -w HVX -r 120 -l PowerStress_HVX.log -k
> check power, temp
![](https://g0v.hackmd.io/_uploads/rygatDCGgGl.png)

33_CHK_DMESG
grep dmesg

