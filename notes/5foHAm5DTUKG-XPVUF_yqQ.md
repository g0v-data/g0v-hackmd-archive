---
name: 如何安裝 Ubuntu 在虛擬機上
tags: 教學, Ubuntu, vmWare, 虛擬機
image: https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_423005858d9673472b97691b9fc3af1f
description: 如何在 Windows 作業系統安裝 vmWare，並建立一個 Ubuntu 作業系統的虛擬機。
---

# 如何安裝 Ubuntu 在虛擬機上

## 下載安裝檔

- [虛擬機 VMware Workstation Player](https://www.vmware.com/tw/products/workstation-player/workstation-player-evaluation.html)（選擇 Windows 適用的 Workstation Player）
- [Ubuntu 16.04](https://www.ubuntu-tw.org/modules/tinyd0/)
    - 「發行版」選擇「Ubuntu 桌面版本」
    - 「版本」選擇「16.04 LTS」
    - 「電腦架構」選擇「64 位元版本」

## 安裝 VMware Workstation Player

安裝這個軟體沒甚麼困難，一直「下一步」即可。

1. 點擊安裝檔，安裝過程中程式會經常提示需要重開機，以下便不贅述，這部分配合指示重開機即可。
2. 勾選同意使用者條款。
3. 選擇虛擬機程式安裝在硬碟的哪個位置，並勾選 Enhanced Keyboard Driver。
4. User Experience Settings 的部分看個人意願勾選即可。
5. Shortcuts 的部分看個人意願勾選要不要新增捷徑。

**恭喜你**，安裝好 VMware Workstation Player 了，以下是開啟程式後的畫面。

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_e8b59bf391a73061a0cad3d983d4e3c4)

## 安裝 Ubuntu 16.04

1. 開啟 VMware Workstation Player
2. 程式右側有圖列幾個選項，點選「Create a New Virtual Machine」
3. 首先要選擇作業系統的安裝檔，也就是稍早下載的 Ubuntu 安裝檔，勾選 Installer disc image file，並提供 Ubuntu 安裝檔的路徑，即可點選下一步。
4. Personalize Linux 的部分是設定開機登入 Ubuntu 時的帳號（Full name）跟密碼（Password），==User name 的部分強烈建議跟 Full name 一樣，不然之後登入虛擬電腦時很容易混淆。==
5. 接下來設定虛擬機的名稱，及安裝位置，到時候安裝完成整台虛擬機就是放在該資料夾下，未來可以複製資料夾到其他有 VMware Workstation Player 去開啟虛擬機，同時也就是代表如果手動刪掉這個資料夾，虛擬機就不見了。
6. Specify Disk Capacity 的部分可以照預設的建議分配 20G 給虛擬機，Ubuntu 16.04 的作業系統需求最少差不多就需要 20~25G 左右。這個配合虛擬機的虛擬硬碟可隨喜好儲存成單一檔案或多個檔案，以下是差別上的比較：

|選項|優點|缺點|
|:-|:-|:-|
|Store virtual disk as a single file|虛擬機搬家時一次搬一個大檔案很容易出錯|讀取虛擬硬碟資訊時比較快|
|Store virtual disk into multiple files|分成幾個小檔案，搬家時不容易出錯|讀取虛擬硬碟資訊時比較慢|

7. 這一步就是幫你的虛擬機設定 CPU、記憶體的配置，就像是去組台桌機時去選擇配備一樣，點選 Customize Hardware 可以調整，建議 Memeory 的部分設定為 4G 以上，使用虛擬機時比較順暢，當然虛擬機要多快也還是要考量本身主機的 CPU 與記憶體有多少，而這些設定也可以在建好虛擬機後再去做調整，跟升級桌機的道理一樣。
8. 點選 Finish 讓 VMware Workstation Player 去建立你設定的 Ubuntu 虛擬機。
9. 接下來 VMware Workstation Player 就會開一個視窗，這個視窗就是虛擬機的螢幕顯示，它啟動了 Ubuntu 安裝檔，所以你在畫面就會看到 Ubuntu install 的畫面，就放著讓安裝精靈去安裝作業系統。

**恭喜你，整個虛擬機的安裝就要完成了，趁 Ubuntu 安裝的時候泡杯咖啡、吃個小點心獎勵自己吧！** :smile: 

10. 安裝好後就會直接到 Ubuntu 的登入畫面，選擇當初設定的 User，輸入密碼，成功登入即完成整個安裝。

## 開機與關機

### 開機
打開 VMware Workstation Player 你會看到一開始建的虛擬機器陳列在左側的清單，點選後再按 Play virtual machine，就會開啟虛擬機的視窗啟動開機程序了，直接在清單上右鍵選擇 Power on 也可以。

### 關機
Ubuntu 的開關機按鈕在右上角，點選電源鍵的圖案，選擇 Shut Down 即可正常關機，偵測到虛擬機關機後 vmWare 就會幫你把整個視窗關掉。