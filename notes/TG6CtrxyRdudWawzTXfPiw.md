---
tags: edu, 
---

# 學校就學人口變化趨勢推測 / 廢校預警

:::info 方便分享共筆網址
廢校預警 🚨 學校就學人口變化趨勢推測
https://g0v.hackmd.io/TG6CtrxyRdudWawzTXfPiw?view
:::

:::warning
文件目錄
[toc]
:::

跳坑：明錡, chewei, yellowsoar, Tiff
討論請至：
- g0v Slack #edu
- FB 社團「零時小學校」

專案介紹影片：https://youtu.be/Int0d9_eLiA
<iframe width=100% height="450" src="https://www.youtube.com/embed/Int0d9_eLiA?si=kWoXyKq5Y36YBiqp" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## 今日任務 (g0v Hackath66n)

使用學校基本統計資訊資料集，來看各學校的就學人口趨勢

找出有可能被廢校的學校
- 小學、中學廢校的母法
    - 全國法規資料庫：公立國民小學及國民中學變更或停辦準則
        https://law.moj.gov.tw/LawClass/LawAll.aspx?pcode=H0070070
    - 教育部主管法規查詢系統：公立國民小學及國民中學變更或停辦準則
        https://edu.law.moe.gov.tw/LawContent.aspx?id=GL001597
- 各縣市政府教育部門依據母法所制定的作業辦法/施行細則
- 偏遠地區學校教育發展條例 https://edu.law.moe.gov.tw/LawContent.aspx?id=GL001698
    

將已經廢校的名單，整理成資料集
- 用途？
    - 了解過往廢校的地點位置
- 資料集欄位：
    - 廢校年份、經度、緯度



## Data 需要的資料集

:::info
共用資料集
https://drive.google.com/drive/folders/1vccBs56aJ1RTBsA5NHZh-ESwwJYKq_01?usp=sharing
:::

全國學校地點資料
- https://g0v.hackmd.io/kb9Sn5u0TZuvWwFbfgt3Hg

歷年各學校就學人口資料
- 學校基本統計資訊1998~2024 https://depart.moe.edu.tw/ed4500/News.aspx?n=5A930C32CC6C3818&page=1&PageSize=40&fbclid=IwY2xjawJKFblleHRuA2FlbQIxMAABHVxw1Je5gUogRsOQl30yL2tXD4xF_lKVfteRKMTqMccMQx6wvBTayeqZXQ_aem_fP4cQl1tMf0siIiACHBClg
- https://depart.moe.edu.tw/ed4500/News_Content.aspx?n=5A930C32CC6C3818&sms=91B3AAE8C6388B96&s=33128143574210DF&fbclid=IwY2xjawJKEohleHRuA2FlbQIxMAABHVxw1Je5gUogRsOQl30yL2tXD4xF_lKVfteRKMTqMccMQx6wvBTayeqZXQ_aem_fP4cQl1tMf0siIiACHBClg

關於「學校代碼」
- https://depart.moe.edu.tw/ed4500/News.aspx?n=63F5AB3D02A8BBAC&sms=1FF9979D10DBF9F3
- 這個頁面裡面也有解釋學校代碼的含義
- 合併的學校會取得新的學校代碼，例如：「原澎湖縣立虎井國小(164612)→澎湖縣立馬公國小虎井分班(164601)」
- 所以看起來學校代碼應該是可以當作 UID 的


原住民族地區
- 盤點原住民族重點小學 csv https://airtable.com/appEy0jH7wgeFfcMY/shrjmzerb0sobb2oY/tblXkKfDdxXyZF61O/viw5fJFBCcmoPcCCu/recXkz9axQ5SY0TdY?blocks=hide
- 台灣原住民族部落基礎資料庫(2021年6月) https://airtable.com/appEy0jH7wgeFfcMY/shrjmzerb0sobb2oY/tblXkKfDdxXyZF61O/viw5fJFBCcmoPcCCu/rec9WT7YbVpcnLlBh?blocks=hide
- 教育部公布有關於原住民族學生資料地圖集 https://airtable.com/appEy0jH7wgeFfcMY/shrjmzerb0sobb2oY/tblXkKfDdxXyZF61O/viw5fJFBCcmoPcCCu/recyOUIQrPIHdqgp3?blocks=hide
- 個別學校素材蒐集
    - 花蓮縣萬榮國小，設立超過百年，目前雖然學生只有47名，老師加校長不到10人，但仍持續辦學 https://www.facebook.com/permalink.php?story_fbid=pfbid02e7xjC8o7fvkVZ6tg4hhrcaieeFcLw12JRaPU1pCRrrXFRpoxykor2vZW6F7bT1w8l&id=100051170178681

學區範圍
- 臺北市可以看到的地理圖框 https://schooldistrict.tp.edu.tw/gis/index.jsp?school=%25E9%25BE%258D%25E5%25AE%2589%25E5%259C%258B%25E5%25B0%258F@undefined@undefined
- 臺南市學區
    - http://std.tn.edu.tw/sis/anonyquery/SchoolDistrict.aspx
    - kiang 做的視覺化 - https://tainan.olc.tw/p/school/

戶籍人口資料
- 社會經濟資料服務平台 https://segis.moi.gov.tw/STATCloud/Index 

已廢校的地點
- 已經停辦的學校清單在教育部統計處的學校名錄頁面裡面可以找到資料
    https://depart.moe.edu.tw/ed4500/News.aspx?n=63F5AB3D02A8BBAC&sms=1FF9979D10DBF9F3
- 教育部國民中小學 整併後校園空間 活化再生案例，但是主題網站關閉了@_@ http://ssdelt.nhps.tp.edu.tw/
    - 教育部廢校活化網站 撤站之前的樣貌 https://web.archive.org/web/20221206201303/http://ssdelt.nhps.tp.edu.tw/
    - 國教署新聞稿頁面 https://www.edu.tw/News_Content.aspx?n=9E7AC85F1954DDA8&s=7E9E989F1DEFD729
- 民間文件：台灣廢校盤點與再生、餘裕空間活化機制 https://g0v.hackmd.io/sTanR4YKQNq45GjWinU_yg?view





