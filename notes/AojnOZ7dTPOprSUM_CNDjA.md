flash Switch FW (L1, L2)

due to SI issue, flash to Gen4
one GPU tray has 1*L2+4*L1
![](https://g0v.hackmd.io/_uploads/B1em7CQEgGx.png)

https://qualcomm-confluence.atlassian.net/wiki/spaces/AI200/pages/1197212976/Switchclid+tool

1. Use ‘show -hw’ command to identify the switch (e.g. for inband command: sudo ./switchclid.x86_64 -pci 6e:00.0 show -hw)
2. sudo ./switchclid.x86_64 -pci 0002:50:00.0 sbr -d -type main -b A0-DCSG-169146-FF.5.2.7_Gen4_all_UM_SBRs_signed.bin -r 0 -quad
3. Use port to check flash to Gen4: sudo ./switchclid.x86_64 -pci 0002:44:00.0 port 
0001:
L1
07, 11, 1b, 25, 35, 3f, 49, 53
 
 
L2
05, 33
 
 
0002:
L1
46, 50 , 5a, 64, 74, 7e, 88, 92
 
L2
44, 72


![](https://g0v.hackmd.io/_uploads/Hy3DKmreMg.png)
