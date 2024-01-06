# 磁碟100 解決方法

>## https://www.reneelab.net/how-to-defrag-windows-10.html
>![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4e643ab0b34e7362947c889cbfdde340.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b5243e97e3786a570143ff3b06584b14.png)
>針對機械硬碟，使用Windows 10的“最佳化磁碟機”程式
注意：此方法建議僅用於機械硬碟。
① 在搜索內容框搜索“重組並最佳化磁碟機”，按“Enter”鍵。
② 選擇需要優化的驅動器，然後按一下“分析”。
提示：建議先分析驅動器以確定是否需要進行優化（碎片大於10%則需優化）。

>③ 選擇目標磁碟機，按一下“最佳化”即可。
磁碟重組完成後，當前狀態會顯示“正常”。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_752975ccd6cd3a7844f813fad76db054.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2da094aeefb57cedb97f5543563809de.png)
① 在搜索內容框搜索“cmd”，然後按右鍵“命令提示字元”，選擇“以系統管理員身份執行”
② 在命令提示字元中輸入：fsutil behavior query DisableDeleteNotify，按“Enter”鍵。
執行此命令後，如果顯示DisableDeleteNotify = 0，則表示TRIM已成功啟動。
Tips:若想要關閉TRIM功能，則在命令提示字元中輸入fsutil behavior set DisableDeleteNotify 1，再按“Enter”鍵即可。

>## https://news.sina.com.tw/article/20190614/31625590.html
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_172f9a902cbf8afc78420acd3642b053.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_df40755d0965fa9f0cffc97c2241e684.png)

>## *https://forum.gamer.com.tw/C.php?bsn=60030&snA=552610
>WIN + R 
下一步輸入services.msc*
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8ed2ef6d665e946e53ccb26d49cbaab5.png)

>## https://dahufoodtravel.pixnet.net/blog/post/221625435-%E8%A7%A3%E6%B1%BA%E7%A3%81%E7%A2%9F100%25%E5%B0%8E%E8%87%B4%E9%9B%BB%E8%85%A6%E7%B7%A9%E6%85%A2%E9%81%8B%E8%A1%8C%E7%9A%84%E6%96%B9%E6%B3%95-%E4%B8%8D%E7%9C%8B%E4%BD%A0
>![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5c15d43f2621e251b5f95302cd12443e.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6d6ac7c291f9030cbf14cfef4c9b6330.png)

>## https://kknews.cc/n/3qpbxb3.html
>### 方法1：禁用SuperFetch

>## https://beebom.com/disable-compattelrunner-exe-windows-10/
>### 方法工作排程器 (Windows Task Scheduler) 

>Cleaner One
>https://news.trendmicro.com/2019/12/18/how-to-speed-up-a-slow-pc-running-windows-os/
>登入