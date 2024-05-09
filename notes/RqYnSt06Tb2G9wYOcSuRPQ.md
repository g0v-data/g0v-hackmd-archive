2024 體驗營 - Hexo 從零打造個人品牌網站
工具：VS CODE
進入之後按新增project
開始輸入之後按!並且按enter即可產生HTML的環境：
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4b89b90aea607b3c7a2a3ce92038589e.png)
head跟body都要有
title代表網站分頁的名稱
內容輸入在body內

***插入圖片：***
先把圖片名稱放在同資料夾後輸入img後enter
在irc" "的中間改上圖片檔名.png即可
若放在資料夾內前面需加入路徑：資料夾名稱/圖片檔名.png
<img src="img/123.png" alt="123">
新增外部圖片路徑：先在網頁上找圖片按右鍵>>選擇複製圖片路徑之後輸入到src內即可
<img src="https://ssl.gstatic.com/ui/v1/icons/mail/rfr/logo_gmail_lockup_default_1x_r5.png" alt="">

***新增連結：***
<a href="https://www.youtube.com/">連到youtube</a>

若要點擊連結時**開新分頁**：增加一個**target**屬性，雙引中間加_blank即可
<a target="_blank" href="https://www.youtube.com/">連到youtube</a>

若要游標移到上面有**小文字提示**，輸入**title**雙引號中間輸入顯示文字即可
<a title="油管" target="_blank" href="https://www.youtube.com/">連到youtube</a>

***段落文字加入連結練習：***
<p>
        <a title="段落練習" target="_blank" href="https://www.starbucks.com.tw/home/index.jspx">星巴克</a>行動預點為星禮程會員專屬服務，提供APP線上預點免排隊取餐，可選擇當日預約取餐與即時15分鐘取餐，飲料可依您的喜好調製風味及留下飲料專屬訊息，也可預熱餐點。透過星禮程隨行卡線上兌換優惠及結帳，訂購成功將開立雲端發票，消費可同步累積星星。
    </p>
    






