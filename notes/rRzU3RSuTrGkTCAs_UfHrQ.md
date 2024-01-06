ACE - Final Challenge -Group 


**1. Deep Security 發現一筆紀錄異常**
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ab37b40865c77a8b868e50ae3417fe37)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_364983210203fef5cedb3726f7b23a16)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_aebd47a310d1a497428920280c42b460)
**發現外部IP172.16.100.200 於02/19/2019 15:57:34使用Havij SQL injection工具對192.168.203.10的Web Server進行入侵**

**2.查找 DDI上有無從該時間點發現的任何異常**
* High
(1)發現172.16.100.200對Web主機發出Webshell Request痕跡
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_cea29bc444a4fcde304d3a46a3fa4e8f)
(2)發現異常的DNS Query,由DC(亦是 DNS Server)發出
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_89c1656ec75ec2ce3ba760efc53b72fe)
(3)發現從Web向svr-web, Staff-pc1, staff-pc2, staff-pc3, mis-pc傳送駭客工具 PoisonIvy (update.exe)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_2adc4b1f610e5dfc37a8c8ff8b364452)

* Medium
(1)往前溯源 發現client-edit.php存在SQL injection弱點,遭駭客利用
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_93191af86459d6f3eb78dd9274b49045)
(2)駭客置入Good.php Webshell,建立灘頭堡
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_f02c105be089d91fedd58b22b32ce0fb)
(3)發現駭客從Web分別對svr-web, Staff-pc1, staff-pc2, staff-pc3, mis-pc遠端執行cmd
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_a155cc834845972da7cf27b053b4b4f7)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_558e5cd2360c5f747d077ff495e479fb)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_96acc983f3e4dca43e632317c3b9b8d3)
(4)發現駭客從Web分別對svr-web, Staff-pc1, staff-pc2, staff-pc3, mis-pc遠端建立At Job
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_46c274b2d169588b097ca369df5af474)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_dc0e7b507651ceeae588f0527edd10b6)


*Low
(1)發現駭客從Web使用nmap對內網環境偵查
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_e1c9dc383f6520f4a556a33eb29c993a)



3. 使用ES調查主機異常
(1)使用updater.exe hash 查找環境中有相同程式的主機
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_56c752977cd98c7ed42a99c981a4d08b)

Command: cmd/c updater.exe
User: jack_fisher@ATD
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0d4f5c992c0e1e1af96048f1c8ceaafe)
發現僅Staff-PC1

(2)使用updater.exe filename 查找環境中有相同程式的主機
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_257c865222d47dd328a5d4685cc2fdbc)
發現AV-EP, SVR-dc, svr-sql


4. 查找受駭主機 svr-web, Staff-pc1, staff-pc2, staff-pc3, mis-pc異常
(1)svr-web
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0ac86a29e00e5c878e01a557cc0c0c42)
被植入webshell
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_30edfb580a7762e4054de94ae4bdff8a)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_5801e6b869ff30d0c4e2c1c1e349dc43)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d6f49626f702a374b9333d88bd842070)

取得db TABLE

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9c264fbde666a70ca1dc45e3789bd649)

使用內網轉發工具 可從外部以42000 PORT連入Web的3389 (RDP)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_a45060003af7cecc5e3e294c42678dac)


(2) Staff-pc1
查找 At Job

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_8c1f4121f80439c2bb193960b6cab3af)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_923b321793c88b7f141d09596beace10)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_40c5ad5ad8ebe457cfda64f2b0bb5185)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_cf0d6ae201376d5359e90661b0cb6cf0)




MIS-PC上發現
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_f7276dfed112aafa29c2d4980935a1cf)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_5a78e8f948d4afeedef42ac24bb84bec)
![Uploading file..._vlv3923ph]()

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d04c881eca863dfc1cdd3c7dd5bfff44)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_398593d9fa745ab45ff26ea6edb59a9f)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_741ed974a8cce5b5a42febc5e5f097b0)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6c12bf8a406d4629a2cfcb8b99925f17)

使用ES發現以下主機皆有
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_b79c48fd798f3e670934057adeb96857)



DC上發現

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_03858a515f1ad1d60c54af9e747cdc42)
