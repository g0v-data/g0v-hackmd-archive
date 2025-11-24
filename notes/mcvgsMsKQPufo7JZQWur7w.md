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
