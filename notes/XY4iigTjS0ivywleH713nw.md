# [鳥哥-基礎學習篇目錄 - for CentOS 7](https://linux.vbird.org/linux_basic/centos7/)

**顏色定義**
---
依重要程度分為五個階段
<font color="#0A0">1. 掌握 (有辦法類比解釋給不懂的人聽)</font>
<font color="#F00">2. 熟悉 (了解輪廓以及這東西扮演的角色及用途並可實際應用)</font>
<font color="#00F">3. 有印象 (模糊、粗略的瞭解這東西的輪廓或大致在做什麼用途) </font>
<font color="#8D6FD1">4. 當故事即可 (看過這東西，但可能不太清楚他在做什麼用)</font>
<font color="#000">5. 可忽略 </font>
---
時期

<font color="#0A0">綠色 #0A0 : 3 個月內</font>

<font color="#F00">紅色 #F00 : 3 個月 - 6 個月</font>

<font color="#00F">藍色 #00F : 長期需提升至熟悉 </font>

<font color="#8D6FD1">紫色 #8D6FD1 : 看過，有印象即可</font>

**第零章、計算機概論** (done)
---
<font color="#8D6FD1">0.1 電腦：輔助人腦的好工具</font>
<font color="#F00">0.1.1 電腦硬體的五大單元</font>
*#電腦的五大單元*
<font color="#8D6FD1">0.1.2 一切設計的起點：CPU 的架構, RISC與ARM, CISC與x86</font>
<font color="#8D6FD1">0.1.3 其他單元的設備</font>
0.1.4 運作流程
<font color="#8D6FD1">0.1.5 電腦用途的分類</font>
*#電腦的分類*
<font color="#0A0">0.1.6 電腦上面常用的計算單位 (容量、速度等)</font>
*#容量/速度的單位*

<font color="#00F">0.2 個人電腦架構與相關設備元件</font>
*#南僑/北橋 #主機板*
<font color="#8D6FD1">0.2.1 執行腦袋運算與判斷的 CPU： CPU的工作時脈, 32位元與64位元, CPU等級, 超執行緒</font>
*#時脈 #匯流排寬度*
<font color="#F00">0.2.2 記憶體： 多通道, DRAM與SRAM, ROM</font>
*#RAM #ROM #CMOS #BIOS #flash #EEPROM*
<font color="#F00">0.2.3 顯示卡： PCIe 規格</font>
*#PCIe Speed*
<font color="#F00">0.2.4 硬碟與儲存設備： 物理組成, 磁碟盤與磁區, 傳輸界面(SATA,SAS,USB..), SSD, 購買與運轉</font>
*#HDD #SATA Speed #SAS Speed #USB Speed #SSD*
<font color="#F00">0.2.5 擴充卡與界面</font>
<font color="#00F">0.2.6 主機板</font>
*#Bottleneck #I/O Address #IRQ #BIOS #CMOS*
0.2.7 電源供應器
0.2.8 選購須知

<font color="#0A0">0.3 資料表示方式</font>
<font color="#0A0">0.3.1 數字系統</font>
*#進制轉換*
<font color="#0A0">0.3.2 文字編碼系統</font>
*#ASCII*
0.4 軟體程式運作
<font color="#0A0">0.4.1 機器程式與編譯程式</font>
*#為何需要編譯 #高階程式語言 #機器碼*
<font color="#F00">0.4.2 作業系統</font>
*#kernel #system call #OS #Application #Kernel功能概覽 #驅動程式*
<font color="#00F">0.4.3 應用程式</font>

0.5 重點回顧
0.6 本章習題
0.7 參考資料與延伸閱讀

**第一章、Linux是什麼與如何學習(done)**
---
1.1 Linux是什麼
<font color="#00F">1.1.1 Linux是什麼？作業系統/應用程式？</font>
*#Linux作業系統*
1.1.2 Linux之前，Unix的歷史
*#GNU歷史 #GCC歷史*
1.1.3 關於GNU計畫、自由軟體與開放原始碼
*#GNU歷史 #GCC歷史*
1.2 Torvalds的Linux發展
1.2.1 與Minix之間
1.2.2 對386硬體的多工測試
1.2.3 初次釋出Linux 0.02
<font color="#8D6FD1">1.2.4 Linux的發展：虛擬團隊的產生</font>
<font color="#F00">1.2.5 Linux 的核心版本</font>
*#uname*
<font color="#F00">1.2.6 Linux distributions</font>
*#Kernel&Distribution*
1.3 Linux當前應用的角色
1.3.1 企業環境的利用
<font color="#8D6FD1">1.3.2 個人環境的使用</font>
*#Linux在哪裡使用*
<font color="#8D6FD1">1.3.3 雲端運用</font>
<font color="#0A0">1.4 Linux 該如何學習</font>
<font color="#0A0">1.4.1 從頭學習Linux基礎</font>
1.4.2 選擇一本易讀的工具書
1.4.3 實作再實作
<font color="#0A0">1.4.4 發生問題怎麼處理啊？建議流程是這樣...</font>
<font color="#0A0">1.4.5 鳥哥的建議(重點在solution的學習)</font>
<font color="#8D6FD1">補充#1: [寫程式不再崩潰！介紹 5 個 Google 工程師都在用的好習慣](https://buzzorange.com/techorange/2019/04/22/google-engineer-career/)</font>
<font color="#8D6FD1">補充#2: [黑客世界的提問](https://github.com/ryanhanwu/How-To-Ask-Questions-The-Smart-Way/blob/main/README.md)</font>

1.5 重點回顧
1.6 本章習題
1.7 參考資料與延伸閱讀

**第二章、主機規劃與磁碟分割(done)**
---
2.1 Linux與硬體的搭配
2.1.1 認識電腦的硬體配備
2.1.2 選擇與Linux搭配的主機配備： 硬體支援相關網站
<font color="#F00">2.1.3 各硬體裝置在Linux中的檔名</font>
*# /dev #*
2.1.4 使用虛擬機器學習
<font color="#00F">2.2 磁碟分割</font>
<font color="#00F">2.2.1 磁碟連接的方式與裝置檔名的關係</font>
<font color="#F00">2.2.2 MSDOS(MBR) 與 GPT 磁碟分割表(partition table)</font>
*#MBR #GPT*
<font color="#00F">2.2.3 開機流程中的 BIOS 與 UEFI 開機檢測程式</font>
*#BIOS #UEFI #Bootloader in MBR*
<font color="#F00">2.2.4 Linux安裝模式下，磁碟分割的選擇</font>
*#掛載*
2.3 安裝Linux前的規劃
<font color="#8D6FD1">2.3.1 選擇適當的distribution</font>
*#下載CentOS*
2.3.2 主機的服務規劃與硬體的關係
2.3.3 主機硬碟的主要規劃(partition)
2.3.4 鳥哥的兩個實際案例
2.4 重點回顧
2.5 本章習題
2.6 參考資料與延伸閱讀

**第三章、安裝 CentOS7.x**
---
自行在 Google 搜尋 "windows虛擬機 Linux CentOS" 或 "windows虛擬機 Linux Ubuntu"來架設環境
鳥哥的教學幾乎都是圖形化介面來進行設定，與我們的使用情境不符合
但可以瀏覽一下教學以學習在建立時需要著重哪些方面的設定

註: VsCode 可直接以 WSL 來架設虛擬機會比較容易一些。這章節主要著重在會進行合理的磁碟分割以及套裝軟體的安裝即可，先將環境架設起來後才有辦法練習後續的章節

~~3.1 本練習機的規劃--尤其是分割參數
3.2 開始安裝CentOS 7
3.2.1 調整開機媒體(BIOS)與虛擬機建置流程
3.2.2 選擇安裝模式與開機： inst.gpt 參數
3.2.3 在地設定之時區、語系與鍵盤配置
3.2.4 安裝來源設定與軟體選擇
3.2.5 磁碟分割與檔案系統設定
3.2.6 核心管理與網路設定
3.2.7 開始安裝、設定 root 密碼與新增可切換身份之一般用戶
3.2.8 準備使用系統前的授權同意
3.2.9 其他功能：RAM testing, 安裝筆記型電腦的核心參數(Option)
3.3 多重開機安裝流程與管理(Option)
3.3.1 安裝 CentOS 7.x + windows 7 的規劃
3.3.2 進階安裝 CentOS 7.x 與 Windows 7
3.3.3 救援 MBR 內的開機管理程式與設定多重開機選單
3.4 重點回顧
3.5 本章習題
3.6 參考資料與延伸閱讀~~

**第四章、首次登入與線上求助**
---
4.1 首次登入系統
4.1.1 首次登入CentOS 7.x圖形介面
4.1.2 GNOME的操作與登出, 應用程式, 檔案總管, 中文輸入法, 登出視窗, 快速重啟 X
4.1.3 X Window與文字模式的切換, startx
<font color="#0A0">4.1.4 在終端介面登入linux</font>
<font color="#0A0"> 4.2 文字模式下指令的下達
4.2.1 開始下達指令, 語系的支援</font>
*#指令與參數描述方法 #語系*
4.2.2 基礎指令的操作, date, cal, bc
<font color="#0A0"> 4.2.3 重要的幾個熱鍵[Tab], [ctrl]-c, [ctrl]-d, [shift]+[UP/DOWN]</font>
<font color="#0A0">4.2.4 錯誤訊息的查看</font>
*#錯誤訊息*
<font color="#0A0"> 4.3 Linux系統的線上求助man page與info page </font>
<font color="#0A0"> 4.3.1 指令的 --help 求助說明</font>
<font color="#02f">  4.3.2 man page, mandb/makewhatis </font>
*man page*
4.3.3 info page
4.3.4 其他有用的文件(documents)
4.4 超簡單文書編輯器： nano
<font color="#0A0">4.5 正確的關機方法: sync, shutdown, reboot, halt, poweroff, systemctl</font>
4.6 重點回顧
4.7 本章習題
4.8 參考資料與延伸閱讀

**第五章、Linux 的檔案權限與目錄配置**
---
5.1 使用者與群組
<font color="#0A0">5.2 Linux檔案權限概念
5.2.1 Linux檔案屬性, 改變語系的 locale</font>
5.2.2 如何改變檔案屬性與權限： chgrp, chown,<font color="#0A0">chmod</font>
<font color="#02f">5.2.3 目錄與檔案之權限意義：, 資料夾與抽屜, 各項動作所需最小權限
5.2.4 Linux檔案種類與副檔名</font>
<font color="#8D6FD1">5.3 Linux目錄配置</font>
<font color="#8D6FD1">5.3.1 Linux目錄配置的依據--FHS：/, /usr, /var</font>
<font color="#0A0">5.3.2 目錄樹(directory tree)</font>
<font color="#0A0">5.3.3 絕對路徑與相對路徑</font>
<font color="#02f">5.3.4 CentOS 的觀察： lsb_release</font>
5.4 重點回顧
5.5 本章練習
5.6 參考資料與延伸閱讀

**第六章、Linux 檔案與目錄管理**
---
<font color="#0A0">6.1 目錄與路徑
6.1.1 相對路徑與絕對路徑
6.1.2 目錄的相關操作： cd, pwd, mkdir, rmdir
6.1.3 關於執行檔路徑的變數： $PATH
6.2 檔案與目錄管理
6.2.1 檔案與目錄的檢視： ls
6.2.2 複製、刪除與移動： cp, rm, mv
6.2.3 取得路徑的檔案名稱與目錄名稱</font>
6.3 檔案內容查閱
6.3.1 直接檢視檔案內容： <font color="#0A0">cat</font>, tac, nl
<font color="#0A0">6.3.2 可翻頁檢視： more, less
6.3.3 資料擷取： head, tail</font>
6.3.4 非純文字檔： od
<font color="#02f">6.3.5 修改檔案時間與建置新檔： touch</font>
6.4 檔案與目錄的預設權限與隱藏權限
6.4.1 檔案預設權限：umask
6.4.2 檔案隱藏屬性： chattr, lsattr
6.4.3 檔案特殊權限：SUID, SGID, SBIT, 權限設定
6.4.4 觀察檔案類型：file
<font color="#02f">6.5 指令與檔案的搜尋
指令檔名的搜尋：which
檔案檔名的搜尋：whereis, locate / updatedb, find</font>
6.6 極重要的複習！權限與指令間的關係
6.7 重點回顧
6.8 本章習題
6.9 參考資料與延伸閱讀

**第七章、Linux 磁碟與檔案系統管理**
---
7.1 認識 Linux 檔案系統
7.1.1 磁碟組成與分割的複習
7.1.2 檔案系統特性： 索引式檔案系統
7.1.3 Linux 的 EXT2 檔案系統(inode): data block, inode table, superblock, dumpe2fs
7.1.4 與目錄樹的關係
7.1.5 EXT2/EXT3 檔案的存取與日誌式檔案系統的功能
7.1.6 Linux 檔案系統的運作
<font color="#02f">7.1.7 掛載點的意義 (mount point)</font>
7.1.8 其他 Linux 支援的檔案系統與 VFS
7.1.9 XFS 檔案系統簡介： xfs_info
7.2 檔案系統的簡單操作
7.2.1 磁碟與目錄的容量： df, du
<font color="#02f">7.2.2 實體連結與符號連結： ln</font>
7.3 磁碟的分割、格式化、檢驗與掛載
7.3.1 觀察磁碟分割狀態：, lsblk, blkid, parted
7.3.2 磁碟分割 gdisk/fdisk： gdisk, partprobe, fdisk
7.3.3 磁碟格式化(建置檔案系統)： mkfs.xfs, mkfs.xfs for raid, mkfs.ext4, mkfs
7.3.4 檔案系統檢驗： xfs_repair, fsck.ext4
<font color="#0A0">7.3.5 檔案系統掛載與卸載： mount, umount</font>
7.3.6 磁碟/檔案系統參數修訂： mknod, xfs_admin, uuidgen, tune2fs
7.4 設定開機掛載
7.4.1 開機掛載 /etc/fstab 及 /etc/mtab
7.4.2 特殊裝置 loop 掛載(映象檔不燒錄就掛載使用)： 掛載DVD, 大型檔案, dd
7.5 記憶體置換空間(swap)之建置
7.5.1 使用實體分割槽建置swap： mkswap, free, swapon, swapoff
7.5.2 使用檔案建置swap
7.6 檔案系統的特殊觀察與操作
7.6.1 磁碟空間之浪費問題
7.6.2 利用 GNU 的 parted 進行分割行為 (Optional)
7.7 重點回顧
7.8 本章習題 - 第一題一定要做
7.9 參考資料與延伸閱讀

**第八章、檔案與檔案系統的壓縮,打包與備份**
---
8.1 壓縮檔案的用途與技術
8.2 Linux 系統常見的壓縮指令
8.2.1 gzip, zcat/zmore/zless/zgrep
8.2.2 bzip2, bzcat/bzmore/bzless/bzgrep
8.2.3 xz, xzcat/xzmore/xzless/xzgrep
<font color="#0A0">8.3 打包指令: tar, 解壓後的 SELinux 課題</font>
8.4 XFS 檔案系統的備份與還原
8.4.1 XFS 檔案系統備份 xfsdump
8.4.2 XFS 檔案系統還原 xfsrestore
8.5 光碟寫入工具
8.5.1 mkisofs：建立映像檔： isoinfo
8.5.2 cdrecord：光碟燒錄工具
8.6 其他常見的壓縮與備份工具
8.6.1 dd
8.6.2 cpio
8.7 重點回顧
8.8 本章習題
8.9 參考資料與延伸閱讀

**第九章、vim 程式編輯器**
---
<font color="#0A0">9.1 vi 與 vim
9.1.1 為何要學 vim
9.2 vi 的使用
9.2.1 簡易執行範例
9.2.2 按鍵說明
9.2.3 一個案例的練習
9.2.4 vim 的暫存檔、救援回復與開啟時的警告訊息
9.3 vim 的額外功能</font>
9.3.1 區塊選擇(Visual Block)
9.3.2 多檔案編輯
9.3.3 多視窗功能
9.3.4 vim 的挑字補全功能
9.3.5 vim 環境設定與記錄： ~/.vimrc, ~/.viminfo
<font color="#02f">9.3.6 vim 常用指令示意圖</font>
9.4 其他 vim 使用注意事項
9.4.1 中文編碼的問題
9.4.2 DOS 與 Linux 的斷行字元： dos2unix, unix2dos
9.4.3 語系編碼轉換： iconv
9.5 重點回顧
9.6 本章習題
9.7 參考資料與延伸閱讀

**第十章、認識與學習BASH**
---
<font color="#0A0">10.1 認識 BASH 這個 Shell
10.1.1 硬體、核心與 Shell
10.1.2 為何要學文字介面的 shell
10.1.3 系統的合法 shell 與 /etc/shells 功能
10.1.4 Bash shell 的功能
10.1.5 查詢指令是否為 Bash shell 的內建命令： type
10.1.6 指令的下達與快速編輯按鈕
10.2 Shell 的變數功能
10.2.1 什麼是變數？</font>
10.2.2 變數的取用與設定：<font color="#0A0">echo</font>, 變數設定規則, unset
<font color="#02f">10.2.3 環境變數的功能： env 與常見環境變數說明, set, export</font>
10.2.4 影響顯示結果的語系變數 (locale)
10.2.5 變數的有效範圍
10.2.6 變數鍵盤讀取、陣列與宣告： read, declare, <font color="#0A0">array</font>
10.2.7 與檔案系統及程序的限制關係： ulimit
10.2.8 變數內容的刪除、取代與替換 (Optional)：, 刪除與取代, 測試與替換
<font color="#02f">10.3 命令別名與歷史命令
10.3.1 命令別名設定： alias, unalias</font>
10.3.2 歷史命令： <font color="#0A0">history</font>, HISTSIZE
10.4 Bash shell 的操作環境
10.4.1 路徑與指令搜尋順序
10.4.2 bash 的進站與歡迎訊息： /etc/issue, /etc/motd
10.4.3 環境設定檔: login, non-login shell, /etc/profile, ~/.bash_profile, <font color="#02f">source, ~/.bashrc</font>
10.4.4 終端機的環境設定： stty, set
<font color="#0A0">10.4.5 萬用字元與特殊符號
10.5 資料流重導向 (Redirection)
10.5.1 何謂資料流重導向？
10.5.2 命令執行的判斷依據： ; , &&, ||
10.6 管線命令 (pipe)
10.6.1 擷取命令： cut, grep</font>
10.6.2 排序命令： sort, uniq, wc
10.6.3 雙向重導向： <font color="#00F">tee</font>
10.6.4 字元轉換命令： tr, col, join, paste, expand
10.6.5 分割命令： split
10.6.6 參數代換： xargs
<font color="#00F"> 10.6.7 關於減號 - 的用途</font>
10.7 重點回顧
10.8 本章習題
10.9 參考資料與延伸閱讀

**第十一章、正規表示法與文件格式化處理**
---
<font color="#02f">11.1 開始之前：什麼是正規表示法</font>
11.2 基礎正規表示法
11.2.1 語系對正規表示法的影響
<font color="#0A0">11.2.2 grep 的一些進階選項</font>
<font color="#8D6FD1">11.2.3 基礎正規表示法練習</font>
<font color="#8D6FD1">11.2.4 基礎正規表示法字符彙整(characters)</font>
<font color="#8D6FD1">11.2.5 sed 工具： 行的新增/刪除, 行的取代/顯示, 搜尋並取代, 直接改檔</font>
11.3 延伸正規表示法
11.4 文件的格式化與相關處理
11.4.1 printf： 格式化列印
<font color="#F00">11.4.2 awk：好用的資料處理工具</font>
11.4.3 檔案比對工具：, diff, cmp, patch
11.4.4 檔案列印準備工具： pr
11.5 重點回顧
11.6 本章習題
11.7 參考資料與延伸閱讀

**第十二章、學習 Shell Scripts**
---
<font color="#0A0">12.1 什麼是 Shell Script</font>
12.1.1 幹嘛學習 shell scripts
12.1.2 第一支 script 的撰寫與執行
12.1.3 撰寫 shell script 的良好習慣建立
12.2 簡單的 shell script 練習
<font color="#0A0">12.2.1 簡單範例： 對談式腳本, 隨日期變化, 數值運算, 計算 pi</font>
<font color="#0A0">12.2.2 script 的執行方式差異 (source, sh script, ./script)</font>
12.3 善用判斷式
12.3.1 利用 test 指令的測試功能
<font color="#0A0">12.3.2 利用判斷符號 [ ]</font>
12.3.3 Shell script 的預設變數($0, $1...)： shift
12.4 條件判斷式
<font color="#0A0">12.4.1 利用 if .... then： 單層簡單條件, 多重複雜條件, 檢驗$1內容, 網路狀態, 退伍</font>
<font color="#0A0">12.4.2 利用 case ..... esac 判斷</font>
12.4.3 利用 function 功能
<font color="#0A0">12.5 迴圈 (loop)</font>
<font color="#0A0">12.5.1 while...do...done, until...do...done (不定迴圈)</font>
<font color="#0A0">12.5.2 for...do...done (固定迴圈)： 帳號檢查, 網路狀態 $(seq )</font>
<font color="#0A0">12.5.3 for...do...done 的數值處理</font>
12.5.4 搭配亂數與陣列的實驗
<font color="#00F">12.6 shell script 的追蹤與 debug</font>
12.7 重點回顧
12.8 本章習題

**第十三章、Linux 帳號管理與 ACL 權限設定**
---
13.1 Linux 的帳號與群組
13.1.1 使用者識別碼： UID 與 GID
13.1.2 使用者帳號：/etc/passwd 檔案結構, /etc/shadow 檔案結構
13.1.3 關於群組： /etc/group 檔案結構, 有效與初始群組, groups, newgrp, /etc/gshadow
13.2 帳號管理
13.2.1 新增與移除使用者： useradd, useradd 參考檔, passwd, chage, usermod, userdel
13.2.2 使用者功能：id, finger, chfn, chsh
13.2.3 新增與移除群組：groupadd, groupmod, groupdel, gpasswd 群組管理員
13.2.4 帳號管理實例
13.2.5 使用外部身份認證系統
13.3 主機的細部權限規劃：ACL 的使用
13.3.1 什麼是 ACL 與如何支援啟動 ACL
13.3.2 ACL 的設定技巧： setfacl, getfacl, ACL 的設定(user, group mask, default)
13.4 使用者身份切換
13.4.1 su
13.4.2 sudo： sudo 指令, visudo (/etc/sudoers) ( 帳號, 群組, 限制指令, 別名, 時間間隔, 配合 su)
13.5 使用者的特殊 shell 與 PAM 模組
13.5.1 特殊的 shell :/sbin/nologin, nologin.txt
13.5.2 PAM 模組簡介
13.5.3 PAM 模組設定語法：驗證類別(type)、控制標準(flag)、模組與參數
13.5.4 常用模組簡介： securetty, nologin, pam_pwquality, login流程
13.5.5 其他相關檔案： limits.conf
13.6 Linux 主機上的使用者訊息傳遞
13.6.1 查詢使用者： w, who, last, lastlog
13.6.2 使用者對談： write, mesg, wall
13.6.3 使用者郵件信箱： mail
13.7 CentOS 7 環境下大量建置帳號的方法
13.7.1 一些帳號相關的檢查工具：pwck, pwconv, pwunconv, chpasswd
13.7.2 大量建置帳號範本(適用 passwd --stdin 選項)
13.8 重點回顧
13.9 本章習題
13.10 參考資料與延伸閱讀

**第十四章、磁碟配額(Quota)與進階檔案系統管理**
---
14.1 磁碟配額 (Quota) 的應用與實作
14.1.1 什麼是 Quota： 一般用途, 限制, 規範 (inode/block, soft/hard, grace time)
14.1.2 一個 XFS 檔案系統的 Quota 的實作範例
14.1.3 實作 Quota 流程-1：檔案系統的支援與觀察 (/etc/fstab, /etc/mtab)
14.1.4 實作 Quota 流程-2：觀察 Quota 報告資料 (xfs_quota, print, df, report, state)
14.1.5 實作 Quota 流程-3：限制值設定方式 (limit, grace_time)
14.1.6 實作 Quota 流程-4：project 的限制 (針對目錄限制) (Optional)
14.1.7 XFS quota 的管理與額外指令對照表
14.1.8 不更動既有系統的 Quota 實例
14.2 軟體磁碟陣列 (Software RAID)
14.2.1 什麼是 RAID： RAID-0, RAID-1, RAID1+0, RAID-5, Spare disk
14.2.2 software, hardware RAID
14.2.3 軟體磁碟陣列的設定： mdadm --create
14.2.4 模擬 RAID 錯誤的救援模式： mdadm --manage
14.2.5 開機自動啟動 RAID 並自動掛載
14.2.6 關閉軟體 RAID(重要！)
14.3 邏輯捲軸管理員 (Logical Volume Manager)
14.3.1 什麼是 LVM： PV, PE, VG, LV 的意義
14.3.2 LVM 實作流程： PV 階段, VG 階段, LV 階段, 檔案系統階段
14.3.3 放大 LV 容量： xfs_growfs
14.3.4 使用 LVM thin Volume 讓 LVM 動態自動調整磁碟使用率
14.3.5 LVM 的磁碟快照： 建立傳統快照, 以快照還原, 用於測試環境
14.3.6 LVM 相關指令彙整與 LVM 的關閉
14.4 重點回顧
14.5 本章習題
14.6 參考資料與延伸閱讀

**第十五章、例行性工作排程(crontab)**
---
15.1 什麼是例行性工作排程
15.1.1 Linux 工作排程的種類： at, crontab
15.1.2 CentOS Linux 系統上常見的例行性工作
15.2 僅執行一次的工作排程
15.2.1 atd 的啟動與 at 運作的方式： /etc/at.deny
15.2.2 實際運作單一工作排程： at, atq & atrm, batch
15.3 循環執行的例行性工作排程
15.3.1 使用者的設定： /etc/cron.deny, crontab
15.3.2 系統的設定檔： /etc/crontab, /etc/cron.d/*
15.3.3 一些注意事項
15.4 可喚醒停機期間的工作任務
15.4.1 什麼是 anacron
15.4.2 anacron 與 /etc/anacrontab
15.5 重點回顧
15.6 本章習題

**第十六章、程序管理與 SELinux 初探**
---
<font color="#0A0">16.1 什麼是程序 (Process)</font>
<font color="#0A0">16.1.1 程序與程式 (process & program)： 子程序與父程序, fork-and-exec, 系統服務</font>
<font color="#F00">16.1.2 Linux 的多人多工環境</font>
<font color="#F00">16.2 工作管理 (job control)</font>
<font color="#F00">16.2.1 什麼是工作管理</font>
<font color="#F00">16.2.2 job control 的管理：&, [ctrl]-z, jobs, fg, bg, kill</font>
16.2.3 離線管理問題： nohup
16.3 程序管理
<font color="#F00">16.3.1 程序的觀察： ps (ps -l, ps aux, zombie), top, pstree</font>
16.3.2 程序的管理： signal, <font color="#F00">kill, killall</font>
16.3.3 關於程序的執行順序： priority, nice, renice
<font color="#F00">16.3.4 系統資源的觀察： free, uname, uptime, netstat, dmesg, vmstat</font>
16.4 特殊檔案與程序
16.4.1 具有 SUID/SGID 權限的指令執行狀態
16.4.2 /proc/* 代表的意義
16.4.3 查詢已開啟檔案或已執行程序開啟之檔案： fuser, lsof, pidof
16.5 SELinux 初探
16.5.1 什麼是 SELinux： 目標, DAC, MAC
16.5.2 SELinux 的運作模式： 元件, 安全性本文, domain/type
16.5.3 SELinux 三種模式的啟動、關閉與觀察： getenforce, sestatus, 啟動與關閉, setenforce
16.5.4 SELinux 政策內的規則管理： getsebool, seinfo, sesearch, setsebool
16.5.5 SELinux 安全本文的修改： chcon, restorecon, semanage
16.5.6 一個網路服務案例及登錄檔協助： 所需服務, FTP 實例, 匿名者範例, 一般用戶家目錄, 非正規目錄, 非正規 port
16.6 重點回顧
16.7 本章習題
16.8 參考資料與延伸閱讀

**第十七章、認識系統服務 (daemons)**
---
<font color="#00F">17.1 什麼是 daemon 與服務 (service)</font>
17.1.1 早期 Systemp V 的 init 管理行為中 daemon 的主要分類
17.1.2 systemd 使用的 unit 分類
<font color="#00F">17.2 透過 systemctl 管理服務</font>
<font color="#00F">17.2.1 透過 systemctl 管理單一服務 (service unit) 的啟動/開機啟動與觀察狀態</font>
17.2.2 透過 systemctl 觀察系統上所有的服務
17.2.3 透過 systemctl 管理不同的操作環境 (target unit)
17.2.4 透過 systemctl 分析各服務之間的相依性
17.2.5 與 systemd 的 daemon 運作過程相關的目錄簡介： /etc/services
17.2.6 關閉網路服務
17.3 systemctl 針對 service 類型的設定檔
17.3.1 systemctl 設定檔相關目錄簡介
17.3.2 systemctl 設定檔的設定項目簡介
17.3.3 兩個 vsftpd 運作的實例
17.3.4 多重的重複設定方式：以 getty 為例
<font color="#00F">17.3.5 自己的服務自己作</font>
17.4 systemctl 針對 timer 的設定檔
17.5 CentOS 7.x 預設啟動的服務簡易說明
17.6 重點回顧
17.7 本章習題
17.8 參考資料與延伸閱讀

**第十八章、認識與分析登錄檔**
---
<font color="#F00">18.1 什麼是登錄檔：</font>
<font color="#F00">18.1.1 CentOS 7 登錄檔簡易說明： 重要性, 常見檔名, 服務與程式, systemd-journald</font>
18.1.2 登錄檔內容的一般格式
18.2 rsyslog.service ：記錄登錄檔的服務
18.2.1 rsyslog.service 的設定檔： /etc/rsyslog.conf, 預設的 rsyslog.conf 內容
18.2.2 登錄檔的安全性設置
18.2.3 登錄檔伺服器的設定
18.3 登錄檔的輪替 (logrotate)
18.3.1 logrotate 的設定檔
18.3.2 實際測試 logrotate 的動作
18.3.3 自訂登錄檔的輪替功能
<font color="#F00">18.4 systemd-journald.service 簡介：</font>
<font color="#F00">18.4.1 使用 journalctl 觀察登錄資訊</font>
18.4.2 logger 指令的應用
18.4.3 保存 journal 的方式
18.5 分析登錄檔
18.5.1 CentOS 預設提供的 logwatch
18.5.2 鳥哥自己寫的登錄檔分析工具：
18.6 重點回顧
18.7 本章習題練習
18.8 參考資料與延伸閱讀

**第十九章、開機流程、模組管理與 Loader**
---
<font color="#F00">19.1 Linux 的開機流程分析</font>
<font color="#F00">19.1.1 開機流程一覽</font>
<font color="#F00">19.1.2 BIOS, boot loader 與 kernel 載入：lsinitrd</font>
<font color="#8D6FD1">19.1.3 第一支程式 systemd 及使用 default.target 進入開機程序分析</font>
19.1.4 systemd 執行 sysinit.target 初始化系統、basic.target 準備系統
19.1.5 systemd 啟動 multi-user.target 下的服務： 相容的 rc.local, getty.target 啟動
19.1.6 systemd 啟動 graphical.target 底下的服務
19.1.7 開機過程會用到的主要設定檔
<font color="#F00">19.2 核心與核心模組
19.2.1 核心模組與相依性： depmod
19.2.2 核心模組的觀察： lsmod, modinfo
19.2.3 核心模組的載入與移除：insmod, modprobe, rmmod
19.2.4 核心模組的額外參數設定：/etc/modprobe.d/*conf</font>
<font color="#F00">19.3 Boot loader: Grub2</font>
<font color="#00F">19.3.1 boot loader 的兩個 stage</font>
<font color="#00F">19.3.2 grub2 的設定檔 /boot/grub2/grub.cfg 初探： 磁碟代號, grub.cfg</font>
<font color="#00F">19.3.3 grub2 設定檔維護 /etc/default/grub 與 /etc/grub.d： grub, 40_custom</font>
<font color="#00F">19.3.4 initramfs 的重要性與建立新 initramfs 檔案： dracut/mkinitrd</font>
<font color="#00F">19.3.5 測試與安裝 grub2： grub2-install</font>
<font color="#00F">19.3.6 開機前的額外功能修改</font>
<font color="#00F">19.3.7 關於開機畫面與終端機畫面的圖形顯示方式</font>
19.3.8 為個別選單加上密碼： grub2-mkpasswd-pbkdf2
19.4 開機過程的問題解決
19.4.1 忘記 root 密碼的解決之道
19.4.2 直接開機就以 root 執行 bash 的方法
19.4.3 因檔案系統錯誤而無法開機
19.5 重點回顧
19.6 本章習題
19.7 參考資料與延伸閱讀

**第二十章、基礎系統設定與備份策略**
---
20.1 系統基本設定
20.1.1 網路設定 (手動設定與DHCP自動取得)： 手動, 自動, 改主機名稱
20.1.2 日期與時間設定
20.1.3 語系設定
20.1.4 防火牆簡易設定
20.2 伺服器硬體資料的收集
20.2.1 以系統內建 dmidecode 解析硬體配備
20.2.2 硬體資源的收集與分析： lspci, lsusb, iostat...
20.2.3 瞭解磁碟的健康狀態
20.3 備份要點
20.3.1 備份資料的考量
20.3.2 哪些 Linux 資料具有備份的意義
20.3.3 備份用儲存媒體的選擇
20.4 備份的種類、頻率與工具的選擇
20.4.1 完整備份之累積備份 (Incremental backup), 使用軟體
20.4.2 完整備份之差異備份 (Differential backup)
20.4.3 關鍵資料備份
20.5 VBird 的備份策略與 scripts
20.5.1 每週系統備份的 script
20.5.2 每日備份資料的 script
20.5.3 遠端備援的 script
20.6 災難復原的考量
20.7 重點回顧
20.8 本章習題
20.9 參考資料與延伸閱讀

**第二十一章、軟體安裝：原始碼與 Tarball**
---
<font color="#F00">21.1 開放源碼的軟體安裝與升級簡介
21.1.1 什麼是開放源碼、編譯器與可執行檔
21.1.2 什麼是函式庫
21.1.3 什麼是 make 與 configure
21.1.4 什麼是 Tarball 的軟體
21.1.5 如何安裝與升級軟體</font>
<font color="#0A0">21.2 使用傳統程式語言進行編譯的簡單範例
21.2.1 單一程式：印出 Hello World
21.2.2 主、副程式連結：副程式的編譯
21.2.3 呼叫外部函式庫：加入連結的函式庫
21.2.4 gcc 的簡易用法 (編譯、參數與鏈結)
21.3 用 make 進行巨集編譯
21.3.1 為什麼要用 make
21.3.2 makefile 的基本語法與變數</font>
<font color="#F00">21.4 Tarball 的管理與建議
21.4.1 使用原始碼管理軟體所需要的基礎軟體
21.4.2 Tarball 安裝的基本步驟
21.4.3 一般 Tarball 軟體安裝的建議事項 (如何移除？升級？)
21.4.4 一個簡單的範例、利用 ntp 來示範</font>
21.4.5 利用 patch 更新原始碼
21.5 函式庫管理
21.5.1 動態與靜態函式庫
21.5.2 ldconfig 與 /etc/ld.so.conf
<font color="#00F">21.5.3 程式的動態函式庫解析： ldd</font>
<font color="#00F">21.6 檢驗軟體的正確性</font>
21.6.1 <font color="#00F">md5sum</font> / sha1sum / sha256sum
21.7 重點回顧
21.8 課後練習
21.9 參考資料與延伸閱讀

**第二十二章、軟體安裝 RPM, SRPM 與 YUM**
---
22.1 軟體管理員簡介
22.1.1 Linux 界的兩大主流: RPM 與 DPKG
22.1.2 什麼是 RPM 與 SRPM
22.1.3 什麼是 i386, i586, i686, noarch, x86_64
22.1.4 RPM 的優點
22.1.5 RPM 屬性相依的克服方式： YUM 線上升級
<font color="#F00">22.2 RPM 軟體管理程式： rpm
22.2.1 RPM 預設安裝的路徑
22.2.2 RPM 安裝 (install)
22.2.3 RPM 升級與更新 (upgrade/freshen)
22.2.4 RPM 查詢 (query)</font>
22.2.5 RPM 驗證與數位簽章 (Verify/signature)
<font color="#F00">22.2.6 RPM 反安裝與重建資料庫 (erase/rebuilddb)</font>
<font color="#F00">22.3 YUM 線上升級機制</font>
<font color="#F00">22.3.1 利用 yum 進行查詢、安裝、升級與移除功能</font>
<font color="#F00">22.3.2 yum 的設定檔</font>
22.3.3 yum 的軟體群組功能
22.3.4 EPEL/ELRepo 外掛軟體以及自訂設定檔
22.3.5 全系統自動升級
22.3.6 管理的抉擇：RPM 還是 Tarball
22.3.7 基礎服務管理：以 Apache 為例
22.4 SRPM 的使用： rpmbuild (Optional)
22.4.1 利用預設值安裝 SRPM 檔案 (--rebuid/--recompile)
22.4.2 SRPM 使用的路徑與需要的軟體
22.4.3 設定檔的主要內容 (*.spec)
22.4.4 SRPM 的編譯指令 (-ba/-bb)
22.4.5 一個打包自己軟體的範例
22.5 重點回顧
22.6 本章習題
22.7 參考資料與延伸閱讀

**第二十三章、X Window 設定介紹X Window 的簡易設定與相關知識介紹**
---
23.1 什麼是 X Window System
23.1.1 X Window 的發展簡史
23.1.2 主要元件： X Server/X Client/Window Manager/Display Manager
23.1.3 X Window 的啟動流程：startx, xinit
23.1.4 X 啟動流程測試
23.1.5 我是否需要啟用 X Window System
23.2 X Server 設定檔解析與設定
23.2.1 解析 xorg.conf 設定
23.2.2 字型管理
23.2.3 顯示器參數微調
23.3 顯示卡驅動程式安裝範例
23.3.1 NVidia
23.3.2 AMD (ATI)
23.3.3 Intel
23.4 重點回顧
23.5 本章習題
23.6 參考資料與延伸閱讀

**第二十四章、Linux 核心編譯與管理**
---


<font color="#00F">24.1 編譯前的任務：認識核心與取得核心原始碼
24.1.1 什麼是核心 (Kernel)
24.1.2 更新核心的目的
24.1.3 核心的版本
24.1.4 核心原始碼的取得方式：distributions 預設、最新、patch
21.1.5 核心原始碼的解壓縮/安裝/觀察
24.2 核心編譯的前處理與核心功能選擇
24.2.1 硬體環境檢視與核心功能要求
24.2.2 保持乾淨原始碼： make mrproper
24.2.3 開始挑選核心功能： make XXconfig
24.2.4 核心功能細項選擇
一般設定(General setup)：附加版本名稱、IPC 通訊、程序相關等
核心模組與 block layer 支援
CPU 的類型與功能選擇(含虛擬化技術)
電源管理功能
核心的網路功能
各項裝置的驅動程式
檔案系統的支援
虛擬化與函式庫
24.3 核心的編譯與安裝
24.3.1 編譯核心與核心模組
24.3.2 實際安裝模組
24.3.3 開始安裝新核心與多重核心選單 (grub)
24.4 額外(單一)核心模組編譯
24.4.1 編譯前注意事項
24.4.2 單一模組編譯
24.4.3 核心模組管理</font>
24.5 以最新核心版本編譯 CentOS 7.x 的核心
24.6 重點回顧
24.7 本章習題
24.8 參考資料與延伸閱讀
