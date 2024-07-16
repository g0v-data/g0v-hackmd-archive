AIX 舊機器新增LPM流程

### LPAR做開機image / 設定開機磁區 ###

lspv

bosboot -ad hdisk0

bootlist -m normal hdisk0

bootlist -m normal -o
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1f89c11c0e2d666868f5a444f78e7b6a.png)

### 關機修改profile ###

注意：是修改!!! 不是刪除，刪除的話 需要重新Zoning

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_54406338a0298898e66da42d3fb99bf5.png)

### 針對虛擬光纖通道 修改配接卡、虛擬配接卡ID

Before
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_99b131071387a7fdb763c952d004c298.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7edb6825d17ecb9cd6cddda1e9dd4aac.png)

After

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0a07afdefcb1458dbfa2a330683ddab6.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1166d9fe6b1e2a4f110f6082133c1faf.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c10fe45f93989e2f5dd8f64cda643326.png)

★VIOS操作

##### 移除舊的vfchost資訊

### 登入VIO 列出所有vfchost

lsmap -all -npiv

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c6630caf1cad95ba36295ca7002758ee.png)

### 移除 vfchost fcs對應關係

vfcmap -vadapter vfchost? -fcp

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_16573b2c0cf9bcf129ab3de434eeca6e.png)

###移除vfchost

rmdev -dev vfchost?

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_71fdea51a26a51a7b5b86c0e77a15ee1.png)

★HMC操作

### 從HMC Session做刪除VIO對應

chhwres -m C105-DR2-S922-SN78691C0 -r virtualio --rsubtype fc -o r -p DR2-VIO1 -s 13

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_82111c1680ff0978838c31e33f026076.png)

##### 新增新的vfchosts

###從HMC Session做新增VIO對應

chhwres -m C105-DR2-S922-SN78691C0 -r virtualio --rsubtype fc -o a -p DR2-VIO1 -s 301 -a "adapter_type=server,remote_lpar_name=AIX_TEST,remote_slot_num=301"

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_29cb9477d4b20d3d2f423c7def477262.png)

★VIOS操作

###登入VIO 列出所有vfchost

lsmap -all -npiv

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3b2f3e001deab14ede7af776df4d9896.png)

### VIO1固定綁fcs0，VIO2固定綁fcs1

VIO1

vfcmap -vadapter vfchost17 -fcp fcs0

VIO2

vfcmap -vadapter vfchost17 -fcp fcs1

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_484120a0a339b56910de8f6f5d5b04eb.png)

### 上述都完成後 就可以開機測試

由於硬體有變動，第一次登入時有可能找不到開機磁區，可手動選擇。

★LPAR操作

### LPAR做開機image / 設定開機磁區 ###

lspv

bosboot -ad hdisk0

bootlist -m normal hdisk0

bootlist -m normal -o

### 更換VIO的HBA ###

lsdev

rmdev -dl fcs? -R

### 啟用PowerHA服務 ###

smit clstart(啟動)

clRGinfo