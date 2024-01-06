# Embedded system design

### 1.發現不尋常
DEVCORE 的情資中心監控到全台灣有大量的網路地址開著 3097 連接埠，只能接受從外部連入，而無法從內部網路存取
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_e907312bbdd5b511b4373c69da7043d7)
### 2.大膽假設與求證
  Q.是否能利用3097port登入路由器並該改內部設定呢?
  A.嘗試驗證，以3097port進入目標後透過 HELP 指令列出其他功能(圖二)，其中MISC SCRIPT指令可執行權限較高，藉由該指令來查看root帳號與密碼，得到一組密碼雜湊(圖三)，經破解後用該密碼成功登入測試用路由器。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_dcf7f79ee4f989cb63d5a0ac7c941e04)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_e7a3fefe9ecf796cd588a4720d5d14d4)
  Q.如何從3097port進入後獲得較高的權限呢?
  A. 推測，中華電信的數據機是一個跑在 MIPS 處理器架構上的嵌入式 Linux 系統，而 3097 服務則是由一個在 /usr/bin/omcimain 的二進位檔案(圖四)來處理，逆向該檔案來找出可用功能。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6fa1664326874950df1e1bb0b0057d76)  
### 3.有哪些指令可用?
3097 服務的處理核心其實就是一個多層的 IF-ELSE 選項，每一個小框框對應的一個功能的實作，但所有指命都匹配失敗時，會進入到了一個 with_fallback 的函數，而這個函數是把匹配失敗的指令接到 /usr/bin/diag 後繼續執行。


# ***/usr/bin/omcimain***

```c=

  //而 BLACKLISTS 定義如下:
  char *BLACKLISTS = "|<>(){}`;";
  char *input = util_trim(s1);
  if (input[0] == '\0' || input[0] == '#')
      return 0;

  while (SUB_COMMAND_LIST[i] != 0) {
      sub_cmd = SUB_COMMAND_LIST[i++];
      if (strncmp(input, sub_cmd, strlen(sub_cmd)) == 0)
          break;
  }
  
  if (SUB_COMMAND_LIST[i] == 0 && strchr(input, '?') == 0)
      return -10;
      
  // ...
  
  while (BLACKLISTS[i] != 0) {
      if (strchr(input, BLACKLISTS[i]) != 0) {
          util_fdprintf(fd, "invalid char '%c' in command\n", BLACKLISTS[i]);
          return -1;
      }
      i++;
  }
  
  snprintf(file_buf,  64, "/tmp/tmpfile.%d.%06ld", getpid(), random() % 1000000);
  snprintf(cmd_buf, 1024, "/usr/bin/diag %s > %s 2>/dev/null", input, file_buf);
  system(cmd_buf);
```



![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ca983ca4ef822515ed135dd4ec9dd294)

 
## 利用漏洞
CVE-2019-15066    在 6998 埠開放的服務存在字串處理問題，可導致攻擊者執行任意指令
CVE-2019-15065    允許攻擊者執行特定指令讀取任意檔案。(與CVE-2019-15066 不相關)
CVE-2019-15064    允許攻擊者不經驗證就登入設備。
CVE-2019-13412    攻擊者可接受託管在3097端口上的服務利用該漏洞執行命令，讀取任意文件
CVE-2019-13411    攻擊者可通過3097端口利用該擴展執行任意命令


## Teacher will Q&A
 #### - How to find port 3097 and ELF file?
     參照3圖   
    
 #### - What is your perceptions for this project
     以常見設備安全為例，且案例中因漏洞使用MIPS指令，與本課程呼應
 
 #### - What is MIPS ?
     
 
 #### - What is RISC ?
     RISC精簡指令集，原設計理念是為了解決常執行的瑣碎動作(例如：把兩數值分別讀取到記憶體相加後，在存入記憶體中)，改為由處理器處理(例如：讀取兩數值相加後再放入記憶體)，以減少記憶體的存取次數。
 
 #### -  Why you want to do this project?
 
 
 #### -  What is actioning for "/usr/bin/diag" ?
 
 
 ## 來源:
 https://zh.wikipedia.org/wiki/%E7%B2%BE%E7%AE%80%E6%8C%87%E4%BB%A4%E9%9B%86
 https://www.ithome.com.tw/news/133322
 https://devco.re/blog/2019/11/11/HiNet-GPON-Modem-RCE/
 https://www.jianshu.com/p/42030f8d1f38
 https://medium.com/@pipi9baby/%E4%BD%BF%E7%94%A8-buildroot-%E5%BB%BA%E7%AB%8B-mips-cross-compiler-%E7%9A%84%E7%92%B0%E5%A2%83-e63a665b87f2
 https://github.com/GundamBox/DIY_OpenMIPS
 https://www.itread01.com/content/1546287866.html
 https://chi_gitbook.gitbooks.io/personal-note/content/cpu_time.html
 
 
 
## 影片：

https://www.youtube.com/watch?v=Pq00YUoBOsQ
<video src="https://blog.niostack.com/rewu.mp4" controls="controls" width="640" height="320" autoplay="autoplay">
Your browser does not support the video tag.
</video>