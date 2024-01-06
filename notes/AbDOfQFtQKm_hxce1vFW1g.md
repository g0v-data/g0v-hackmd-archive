---
title: "20140510支持松-太陽花盒子"
tags: 0media,太陽花盒子,hackpad
---

# 20140510支持松-太陽花盒子

> [點此觀看原始內容](https://g0v.hackpad.tw/QZ7WShK1gPu)

[太陽花盒子](https://g0v.hackpad.tw/Fr9H87GPcUM)  [黑客松](http://ccsp.kktix.cc/events/hackathon) [http://hackfoldr.org/2014ccsp/](http://hackfoldr.org/2014ccsp/)

## User Story

### FourDollars

- [x] FourDollars: 想要完成 Debian/SH4 開發基礎平台
    - [x] 確認 qemu/lxc 建立出來的環境裡面編譯出來的 Hello World 程式可以直接放在網樂通上面執行
    - [x] 使用 [http://download.si-linux.co.jp/debian-sh/wheezy-sh4/](http://download.si-linux.co.jp/debian-sh/wheezy-sh4/) 建立 Debian/wheezy 的 Linux Container
    - [x] 透過 NFS 分享 Linux Container 的 rootfs 給網樂通使用
        - 安裝 nfs-kernel-server 修改 /etc/exports
                - /var/lib/lxc/wheezy-sh4/rootfs 10.42.0.*(rw,sync,no\_subtree\_check,all_squash,anonuid=0,anongid=0)
        - 需要修改 /etc/inittab 以及 /etc/network/interfaces
            - 1:2345:respawn:/sbin/getty 115200 console
            - 將 /etc/network/interfaces 裡面 eth0 的部份注解掉
        - 所使用的 UBoot 啟動參數
            - setenv cm coprossor_mem=16m@0x10000000,16m@0x11000000
            - setenv nwhwconf nwhwconf=device:eth0,hwaddr:24:cf:21:b2:a4:76
            - setenv console console=ttyAS0,115200
            - setenv nfsroot nfsroot=/var/lib/lxc/wheezy-sh4/rootfs
            - setenv bootargs ${console} root=/dev/nfs rw ${nfsroot} ip=dhcp mem=256M ${cm} ${nwhwconf}
            - boot
    - [x] Linux Kernel 意外被刪掉了，所以自己的 Linux Kernel 自己編譯。
        - [http://www.ptt.cc/bbs/Linux/M.1374821355.A.95F.html](http://www.ptt.cc/bbs/Linux/M.1374821355.A.95F.html)
    - [x] 建立 personal Debian archive (以 mplayer 為目標)
        - [https://wiki.debian.org/HowToSetupADebianRepository](https://wiki.debian.org/HowToSetupADebianRepository) \- 最後選擇使用 reprepro
        - 寫了一些輔助的 script 放在 [https://github.com/fourdollars/debian-sh4](https://github.com/fourdollars/debian-sh4) 上面
        - deb [http://people.linux.org.tw/~fourdollars/debian/](http://people.linux.org.tw/~fourdollars/debian/) wheezy main contrib non-free
        - deb-src [http://people.linux.org.tw/~fourdollars/debian/](http://people.linux.org.tw/~fourdollars/debian/) wheezy main contrib non-free

### Rex

- [x] Rex: 確認硬體解碼可以運作
    - [x] 測試 gstreamer 解碼
> 失敗。疑似 xbmc 用的 gst library binding 跟 gst-launch 用的不一致
> [name=Rex T]

- [x] Rex: 確認可以用 USB Pendriver 散布安裝檔案
    - [x] 確認 u-boot 從 USB 開機 的 boot script
> update\_uboot=usb start;fatload usb 0 80000000 u-boot.bin;update\_spi_uboot 
> [name=Rex T]

    - [x] 確認 original u-boot, boot from usb 開機流程
- [x] Rex: 希望完成一個可以展示播放功能的基礎使用者界面
    - [x] 決定使用的開發工具為何 (Android, XBMC, Qt, DirectFB)
> xmbc (directfb) works, 但是有幾個問題
> [name=Rex T]

> 1\. lircd 實在太慢，需要研究為什麼會高度延遲
> [name=Rex T]

> 2\. Youtube 播放失敗、MP4 播放失敗。
> [name=Rex T]

> 3\. XBMC 的 memory footprint 太高。機器共 256M, 需留下一半給 coprocessor 使用 ([bigphysarea](http://lwn.net/Articles/111132/) )
> [name=Rex T]

> 。xbmc 遠遠需要超過 120Mb.
> [name=Rex T]

> 4\. Duckbox 有一套自己的 build system, 
> [name=Rex T]

> 使用 STLinux prebuilt BSP. 
> [name=Rex T]

> 使用 STLinux 是出的 src.rpm (但是這些 src.rpm 的格式有些問題，造成新版的 rpm 讀取 spec 檔案會失敗)
> [name=Rex T]

> STLinux 做了一個 DirectFB-1.0.1/gfxdrivers/stgfx/
> [name=Rex T]

> gstreamere codec 硬幹在 xbmc-nightly/xbmc/cores/gstplayer/GSTPlayer.cpp
> [name=Rex T]

> 目前台灣玩家沒有統一的 code repository. 整合上需要修改 makefile, backport xbmc, integrate firmware binaries.
> [name=Rex T]


> 目前無 Qt port, 需要檢查 EGL 相容性。
> [name=Rex T]

- [x] ~ Rex: live stream API 整合~
    - [x] ~解讀~ [~https://github.com/g0v/live~](https://github.com/g0v/live)
    - [x] ~解讀 ~ [~API Document~](https://g0v.hackpad.tw/668AHTZTehn)
> 沒空整合 API.
> [name=Rex T]

### Miaoski

- [ ] Miaoski: 把 X 開起來...
    - [x] 確定 ST231 co-processors 兩顆都可以 init (FW 大概沒指望了?)
> 用了噁心的方法: 用 Hans Yu 的 XBMC distribution 裡的 kernel + /lib/modules/*.ko 配上派樂靈丹的 rootfs 以及裡面的 fbtest 程式... 總之看得到東西了，但卻沒辦法自己 compile 出來。
> [name=Zhemin L]

> *.elf 和 *.fw 可以在 STLinux-2.4 找到。還沒試過用 Hans Yu 的 .config 能不能做出一樣的東西.
> [name=Zhemin L]

    - [ ] 看有沒有 qwx 或 X 可以用
> 有 xorg 但開不進去，因為它一直想寫 /dev/tty0
> [name=Zhemin L]

> 原廠有 xorg, 不知道改了什麼就是 [ftp://ftp.stlinux.com/pub/stlinux/2.4/updates/SRPMS/](ftp://ftp.stlinux.com/pub/stlinux/2.4/updates/SRPMS/)
> [name=Rex T]

    - [ ] 升級到 Wheezy 7.5
> apt-get dist-upgrade 但有一堆 failed dependency 想想現在還是別升級比較安心。
> [name=Zhemin L]

    - [x] 嘗試派樂靈丹 0.9.2 載入 FB firmware (root 密碼 wb1234)

### Conrad

- [ ] ...

## 需要工具

- USB TTL Debug cable.
- USB Pendriver
- 硬體
    - 網樂通數台
    - Android Settop Box
        - 小米盒子
        - MK802
- 電視一台

### References

- 硬體資訊等 NextVOD [https://gist.github.com/chihchun/753181](https://gist.github.com/chihchun/753181)
- Debian on NextVOD STB [https://gist.github.com/chihchun/754972](https://gist.github.com/chihchun/754972)
- [http://stwp26.cyberhood.net.tw/NextNAS/target.NexNAS-wheezy-sh4twbox092.tgz](http://stwp26.cyberhood.net.tw/NextNAS/target.NexNAS-wheezy-sh4twbox092.tgz) root wb1234
- [https://www.kernel.org/doc/Documentation/filesystems/nfs/nfsroot.txt](https://www.kernel.org/doc/Documentation/filesystems/nfs/nfsroot.txt)

## 工作紀錄

### u-boot

- 派樂靈丹 \- TWPDA: 再探 網樂通 uboot code (UBOOTWPDA) [http://www.twpda.com/2013/08/uboot-code.html](http://www.twpda.com/2013/08/uboot-code.html)
- dlintw/twpda-uboot [https://github.com/dlintw/twpda-uboot](https://github.com/dlintw/twpda-uboot)
- git.stlinux.com Git - stm/u-boot.git/summary [http://git.stlinux.com/?p=stm/u-boot.git;a=summary](http://git.stlinux.com/?p=stm/u-boot.git;a=summary)
- Modifying U-Boot | STLinux [http://stlinux.com/node/126](http://stlinux.com/node/126)
- Porting U-Boot To A New Board | STLinux [http://stlinux.com/node/127](http://stlinux.com/node/127)
```
37895f3b538dcc4c9e19cc8b23c4bd3fc32642ff  www.fulldynamic.com/download/GPL/linux-sh4-2.6.23.17\_stm23\_A18B.tar.gz
aba4734671e975c1a6d3c4436acd8efaa4d80373  www.fulldynamic.com/download/GPL/U-boot_sourcecode.zip
```
- [ ] 檢查 STLinux, 派樂靈丹的 diff

試用 xmbc 的 vmlinux.ub + FourDollars 的 mplayer:
- 軟解，放 320x240 還不錯，更大就糟了
- 可以 mplayer -zoom -x 900 -y 600 -geometry 50%:50% 但速度很慢
- 播放的時候背景底圖 (如果有的話) 會左右亂動.
- ~可能是 display1 / display2 的問題，再檢查一下 insmod 那邊.~不設 display2 一樣會晃
- 必須要 mem=256M 不然 bpa 的 LMI_IO 不能建立 (why? mem=240M 不行喲)
- uboot 參數:
```
tftp 80000000 xbmc.ub
setenv nfsroot nfsroot=192.168.100.1:/srv/nfs/root root=/dev/nfs rw
setenv mem phyaddr:0,watchdog:5000 mem=256M bigphysarea=2048
setenv bootargs ${console} rootdelay=0 ${nfsroot} ${nwhwconf} ${mem} ${ip}
bootm 0x80000000

```
試用 Hans Yu 的 e2
- 必須 mem=240M 才能正常 init 各項模組
- mem=120M 會 kernel panic
- 因為沒有搖控器，就卡在 Video input selection (/usr/local/bin/enigma2) 的畫面了
- gst-launch-0.10 playbin2 uri=[file:///root/somefile.avi](file:///root/somefile.avi) 的 codec 似乎只有 H.264 但仍然放不出畫面
- uboot 參數:
```
tftp 80000000 e2.ub
setenv nfsroot nfsroot=192.168.100.1:/srv/nfs/e2 root=/dev/nfs rw
setenv mem phyaddr:0,watchdog:5000 mem=240M bigphysarea=2048
setenv bootargs ${console} rootdelay=0 ${nfsroot} ${nwhwconf} ${mem} ${ip}
bootm 0x80000000



```
### 活動花絮


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_07d9497c490b71519ad9b4f265536a39)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_1ba2ca7023fc368d21e6b15f6dd361d3)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_71cd885d1c332660f344c834ea09bc5a)


Jack> 請問 如果我可以寄一台mk802 贊助研究 該如何寄給你們
Jack> mk802系列 記的是 友善之臂 當初自立門戶的員工 所copy產出
[Jack>](http://www.arm9.net/) [http://www.arm9.net/](http://www.arm9.net/)
[Jack>](http://www.360doc.com/content/12/0412/14/9413880_203022427.shtml) [http://www.360doc.com/content/12/0412/14/9413880_203022427.shtml](http://www.360doc.com/content/12/0412/14/9413880_203022427.shtml)
[Jack>](http://www.arm9.net/Mini210s.asp) [http://www.arm9.net/Mini210s.asp](http://www.arm9.net/Mini210s.asp)
> Hi Jack, 可以寄到台北郵政35-45信箱林哲民收。謝謝！
> [name=Zhemin L]

> 友善之臂這幾個 mini / tiny 都不便宜呢... 從 1000 RMB 起跳.
> [name=Zhemin L]

> 請問是那一代？我手上還有四台 mk802
> [name=Rex T]

> 台灣的更貴 喔  且沒有編輯程式  但這樣也後有後面 不過也比較知道 他們的後面如何防堵 
> [name=Jack S]

> 最重要的有2個 學會這種東西的朋友 要自己拼3C創意 很有前途 不要再被台灣血汗工廠給騙了
> [name=Jack S]

> 真正的RD也不過就50人不到
> [name=Jack S]

> 友善之臂說穿了就是copy 大廠  很多國外的廠商 恨的牙癢癢 草媒機 他們也有copy 所以不要只看網頁廣告喔 那只是參考
> [name=Jack S]

> 更重要的是 有能力者或會規劃者 可以制定規格 至於量的部份 可採低量單價洽詢 這部份 台灣的工業電腦態度就很硬
> [name=Jack S]

> mk802這2天有空我就寄
> [name=Jack S]

> [https://github.com/omegamoon/rockchip-rk30xx-mk808](https://github.com/omegamoon/rockchip-rk30xx-mk808)
> [name=Jack S]

> [http://www.oschina.net/hardware](http://www.oschina.net/hardware)
> [name=Jack S]

> [http://www.oschina.net/p/cubieboard](http://www.oschina.net/p/cubieboard)
> [name=Jack S]

> [http://www.oliospec.com/item_detail/itemCode,Giada-mpc-wifi-kit/](http://www.oliospec.com/item_detail/itemCode,Giada-mpc-wifi-kit/)
> [name=Jack S]

> [http://www.oschina.net/shop/mixtile/59](http://www.oschina.net/shop/mixtile/59)
> [name=Jack S]

> 不過為什麼 大家不用對講機  木瓜的範圍很大  頻道雖易被攔截 就當是故意被攔截的訊息 
> [name=Jack S]


Michael_LI＞［請問］有人帶去攜帶型的液晶螢幕，知道是哪個廠牌嗎？以及動態畫面延遲會很明顯嗎？／正在找這個東西，比較中／
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_406df406b4febe454b2ae4134f19ff1b)



