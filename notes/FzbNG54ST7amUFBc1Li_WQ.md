# OS_project1
### 組員 : 
F74066349 周奕君
F74061103 林郁喬
F74061161 蔡旻恩
F74062191 洪鉦壹
### 安裝和編譯過程 :

1. 從網路上下載Linux Kernel的原始碼（我們使用Linux 5.5.18）![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3f7e40fbcd25a7d98762a5b497fa1a62.PNG)

2. 解壓縮![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_74a58fed20f0d534d6724a5884e70944.PNG)

3. 進入Kernel資料夾，建立新的System Call資料夾及程式碼（hello、hello.c）![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a69c04e5186801f43e8b57d8991a7094.PNG)

4. 加入System Call程式碼![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b548cd8dacc0a32e7ab8ca48e65e59f9.PNG)

5. 新增Makefile![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fab6f493fab05086a96979b0749b48c5.PNG)

6. 回到Linux資料夾，修改Makefile![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a386b90db3cbfa468d98822c717e159e.PNG)

7. 接著到arch/x86/syscalls/syscall_32.tbl下，新增System Call![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f0f6b3308ddd3fe3b3c6cc7ed8bb2e6b.PNG)

8. 再到include/linux/syscalls.h下，新增System Call的定義![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d93a5dd27fd998b871233194bc4653e2.png)

9. 之後再用指令安裝需要的套件：
    $ sudo apt-get install libncurses5-dev
    
    $ sudo apt-get install python-pip python-dev libffi-dev libssl-dev 
    libxml2-     dev libxslt1-dev libjpeg8-dev zlib1g-dev
    
    $ sudo apt-get install bison
    
    $ sudo apt-get update
    
    $ sudo apt-get upgrade
    
10. 安裝後執行
    $ sudo make menuconfig
    
    $ sudo make oldconfig
    
11. 都完成之後開始編譯並等待
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8ca44580c842b60364028f1f43c91e10.PNG)

    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_62b940c8b4ebda5f6cd749eb6298c603.PNG)

12. 編譯完成之後安裝，繼續等待
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8db16d818ffec02685c207bd3f927d7e.PNG)

    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_857e88c4a5ac72f5e39e358cd5d3ac3f.PNG)

13. 安裝完後，修改Grub的檔案，讓下次開機時可以顯示Grub介面
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_00101638497e231209d497c918d0d916.PNG)

    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_07391721fdbb2a89036827842c63c347.PNG)

    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b35de4eedd7517e16d2c05e4145f6c8a.PNG)
    
14. 重開機，選新裝好的Linux![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1e588ecc424e138264edfd8e452b157c.PNG)

15. 驗證版本
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fc44d7cce719bd74ef926be3d98a901b.png)
    
16. 新增測試用程式![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_666219e295d5a62320e4639e0b6ecafd.PNG)

17. 用戶端測試結果（回傳0代表執行成功）![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7274a348bb8aba54d7d53aa0e616e0ff.PNG)

18. Kernel端測試結果（使用dmesg指令查看Kernel訊息）
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_18d87b0fbd73b6614309d4a43adad2a6.png)



### 進階問題
* 修改了哪一些檔案，與修改之目的？

    1. 新增hello資料夾以及資料夾下的自訂System Call（hello.c）

    2. 新增Makefile（obj-y := hello.o）

    3. 修改Linux資料夾中的Makefile，讓Compiler知道新增的System Call在哪裡
    （core-y     +=kernel/ certs/ mm/ fs/ ipc/ security/ crypto/ block/         hello/）

    4. 在arch/x86/syscalls/syscall_32.tbl（因使用的系統為32位元）之下，新增System Call，要新增在32位元的位置，並紀錄編號如此才可以使用此自訂的System Call（syscall(編號））

    5. 在include/linux/syscalls.h下，新增System Call的定義


* 概述一下，為了這項Project學到了什麼額外知識以及遇到的困難？

    1. 遇到的困難：
         1. 需要在系統中額外安裝許多套件（如libcurses5，etc.)，不然在過程中會發生編譯錯誤。
         
         2. 超出預期的Compile時間。
         3. 在Linux Kernel原始碼加入新System call步驟較繁瑣，需修改與增加許多檔案。許多指令需仔細操作，不可遺漏，否則可能造成不可預期的錯誤。
         4. 在編譯時，需要等待較長時間，在過程中不可以中斷，若中斷必須重新安裝。
         5. 使用指令進行編譯的時候出現Conflicting Type的相關錯誤訊息，使編譯無法成功，導致無法安裝執行。
         
         
    2. 學到的東西：
        1. 如何利用指令(dmesg)，來查看Kernel內的訊息（printk所印出的東西）。
       
        2. 如何修改Kernel，並自定義新的System call。
        3. 當出現不可預期的錯誤時，能夠善用網路資源，找到解決問題的辦法，培養查找資料的能力。
        4. 了解當前進行的指令所代表的意義，若不小心遺漏，能夠迅速找到問題所在。
        5. 在完成作業要求的同時，清楚明白其中所新增與修改的檔案所發揮的作用與功能。


### 參考資料
* https://blog.kaibro.tw/2016/11/07/Linux-Kernel%E7%B7%A8%E8%AD%AF-Ubuntu/
* http://chriswenyuan.blogspot.com/2017/05/system-call-linux-kernel-v4x.html
* 


















