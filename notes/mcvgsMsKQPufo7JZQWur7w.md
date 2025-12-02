# rROK5520

### 11/10
- [x] 1.CPU(Q659 221E BTL)的HDMI畫面出不來->應是BIOS GOP CHILD DEVICE問題，MR52T002已解決
- [x] 2.進OS出現I219裝置(ROK5520無I219)，MR52T001已解決
=>11/10發MR52T001#

### 11/11
- [x] 1.MR52T001上傳src，寫readme
- [x] 2.改HDMI順序
  HDMI1(DDIB)+HDMI2(DDIC)
  HDMI1(DDIB)+VGA(DDIA)
  HDMI2(DDIC)+VGA(DDIA)
  HDMI1(DDIB)
  HDMI2(DDIC)
  VGA(DDIA)
- [x] 3.SATA資訊標記tray2(對應右邊sata 0-3), tray1(對應左邊sata4-7)
- [x] 4.修改SMBIOS: PN, BN
=>11/11發MR52T002#

### 11/12
ATC8120
- [x] 1.MA82T032轉MA82-003，發PLM

ROK5520
- [x] 1.新增PXE功能
- [x] 2.更正MCU版號
- [x] 3.移除跟MCU的FAN溝通
=>11/12發MR52T003

### 11/13
- [x] 1.根據protocol V0.2調整與MCU溝通 
- [ ] 2.COM1-4 RS232 可跑但有少數err，RS422/485還沒測
- [x] 3.參考5510設計SYSFAN(for POE FAN) 檢查溫度來源暫存器選擇，有SMF功能
- [x] 4.參考5510顯示主板之外如POE等資訊
=>11/13發MR52T004

### 11/14
- [x] 1.新增Graphic Fan SMT 在HWM

### 11/17
- [x] 1.完成Graphic Fan SMT 在HWM
=>11/17 發MR52T005

### 11/19
- [x] 1.確認RS485半雙工功能失敗原因

### 11/20
- [x] 1.修RS485功能問題
=>11/20 發MR52T006


### 11/24

### 11/25

### 11/26
nROK6231-ICO MV23W033
- [x] BIOS: Secure boot RSA 8192 keys (2025/3/7 已提供客戶, 客戶無回應)
- [ ] 改成CN5 slot to M.2 Key B, 支援5G FN990A28-HP
- [ ] 改成CN7 slot to mPCIe, 支援Wi-Fi WLE7002 x 1, disable pin 改1.8V (是否要上Wi-Fi,待客戶確認)
- [ ] 移除不需要的IO
- [ ] RTC battery 改成super cap, 供電時間3天,需做新小板 (供電時間待客戶確認


### 12/02
- [ ] Possibility to upgrade Boot FW from within host Linux OS (without using external programmer). 

- [x] TPM 2.0 support  

- [x] Shall have 8192-bits encryption keys for Secure Boot

- [ ] Support for booting only signed OS bootloader 

- [x] Boot console on UART (115200 baud) 

- [ ] All USB, PCIe and SATA interfaces shall be enumerated the same even if some modules/hardware are not inserted/detected. 

- [ ] If a device module connected to USB is powered off and the same or another one is inserted and powered on, then the OS needs to be able to detect it (on the same interface as previous) 

- [ ] Boot order prioritization:  USB, mSATA, 2.5" SATA

- [ ] Virtualization support VT-x should be enabled

- [ ] Virtualization support VT-d should be enabled

- [x] BIOS menu using UART only, booth for console output and as a keyboard input.

- [x] It shall be possible to read the FRU/DMI information from within the OS, e.g., by using ‘dmidecode’  

- [ ] Saving settings to BIOS shall not rely on RTC Battery 

- [ ] Pre-BIOS WDT shall issue a system reset if the unit does not reach BIOS stage (not a hard requirement)

- [ ] Pre-OS boot WDT shall  issue a system reset if the unit is not able find a bootable device or if for any other reason it can not boot an OS

- [ ] The Pre-OS boot WDT time shall be configurable, and the setting shall be persistant and saved between power cycles.

- [ ] Active WDTs shall be disabled when entering BIOS menu.

- [ ] In OS Intel WDT shall be able to pinged/petted using standard Intel iTCO_WDT driver in Linux kernel

- [ ] In OS WDT time shall be configurable, and the setting shall be persistant and saved between power cycles.

- [ ] BIOS default values shall be agreed between supplier and client before production





