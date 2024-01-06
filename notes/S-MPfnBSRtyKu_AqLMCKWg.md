# 20190506

GitHub
  >放code
  
  

What is server?

  > 伺服器有細分網頁/檔案/郵件/資料庫....伺服器
  >
  > 任何一台電腦都可以成為伺服器 -> 在電腦上安裝伺服器軟體即可
  >
  > 伺服器主要提供讓電腦資料交換與存取的服務
  >
  > 網頁伺服器目前有兩大主流： Microsoft IIS / Linux APACHE
  >
  > server/client可以同時存在
  >
  > 可以自己架伺服器/也可以放上網營運

* 遠端連線server

  > 透過網路連進某個具有基本設備的主機進行操控
  >
  > 目前預想 -> 專題教室的電腦架伺服器,透過遠端連線操控

* Web Server?

  > web server是存放網路伺服器軟體、網站檔案的電腦
  >
  > 透過連上網路、http protocol可以獲得網站檔案的存取

  * Static web server -> 提供基本的瀏覽功能
  * Dynamic web server -> 除了靜態功能之外搭載資料庫/應用伺服器等等等的

  * 有些web framework 自帶server的簡易功能 ex:PHP,Django



<span style='color:#5bab44'>**What is putty???**</span>

> 一種ssh(protocol)的連線方式，通常好像是連接到linux伺服器用
>
> telnet, SSH, rlogin 串行接口連接軟體



<span style='color:#5bab44'>**About 架設伺服器**</span>

1. 伺服器軟體

   > 1. Linux -> Apache server -> execute HTML/PHP
   > 2. Windows -> IIS/Apache server -> HTML+ASP+ASP.net / HTML+PHP 
   > 3. 以上的 resource : https://www.appserv.org/en/

   架設簡易教學：->http://163.21.31.9/~liao/computer/web/webhost.pdf

   ​						   ->http://finalfrank.pixnet.net/blog/post/6841252

   Q: 申請domain name 需要付費 -> 有沒有別的替代方案？

   

------

### About NLP

last update

-> Microsoft NLP resources -> Azure Luis 

* OLAMI????

  > https://tw.olami.ai/open/website/home/home_show
  >
  > https://medium.com/@zaoldyeck9970/%E5%88%A9%E7%94%A8-olami-open-api-%E7%82%BA-chatbot-%E5%A2%9E%E5%8A%A0-nlp-%E5%8A%9F%E8%83%BD-e6b37940913d
  >
  > 直接備有中文語意的資料庫,語意不用自己train
  >
  > 詳細做法還在看

* Google Dialog flow????

  > https://dialogflow.com/
  >
  > -> use machine learning to understand what user is saying
  >
  > -> 搭配google search 和周邊服務技術
  >
  > https://ithelp.ithome.com.tw/articles/10202280 -> 教學文
  > 
## 下次要報給老師的內容
1. 模組
2. 製作順序
3. 上禮拜老師的問題：a.wordpress跟heroku的伺服器差異 b.為什麼要用Wordpress c.為什麼要用heroku
    Heroku 
4. 使用github
5. OLA   DIALOG FLOW   LUIS的比較

抓資料     抓下來如何呈現      網站外觀設計
nlp串接    連接linebot       icon設計