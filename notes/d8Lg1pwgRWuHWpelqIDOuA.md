---
title: "全球空難事件視覺化"
tags: hackpad
---

# 全球空難事件視覺化

> [點此觀看原始內容](https://g0v.hackpad.tw/4o8ADZLQJfx)


目的
新聞模版的實驗

授權
協作文件以 CC-BY 授權

工具
地理事件規模模版: [http://0media.tw/t/geoevent/](http://0media.tw/t/geoevent/)

空難列表協作文件
[https://docs.google.com/spreadsheets/d/1weTyy3X52QginfNbrSmxjR8WpsAEgJSRjzzqBJ8RaXk/edit#gid=615981805](https://docs.google.com/spreadsheets/d/1weTyy3X52QginfNbrSmxjR8WpsAEgJSRjzzqBJ8RaXk/edit#gid=615981805)

產生結果
[http://0media.tw/t/geoevent/widget/?src=1weTyy3X52QginfNbrSmxjR8WpsAEgJSRjzzqBJ8RaXk&color=green&ratio=20&clat=22&clng=0&initz=3](http://0media.tw/t/geoevent/widget/?src=1weTyy3X52QginfNbrSmxjR8WpsAEgJSRjzzqBJ8RaXk&color=green&ratio=20&clat=22&clng=0&initz=3)
> 修正了
> [name=Kirby W]

[~http://0media.tw/t/geoevent/widget/?src=17u9luNKn77I4Tyz3pPADnr6sw3yiob0Z6Dy4_FFpbl4&color=default&ratio=5&clat=8.420997&clng=-6.036083&initz=2~](http://0media.tw/t/geoevent/widget/?src=17u9luNKn77I4Tyz3pPADnr6sw3yiob0Z6Dy4_FFpbl4&color=default&ratio=5&clat=8.420997&clng=-6.036083&initz=2)
> 上面是地震結果，空難事件圖無法正常載入
> [name=積木陳]



加碼: 全球地震
[http://0media.tw/t/geoevent/widget/?src=17u9luNKn77I4Tyz3pPADnr6sw3yiob0Z6Dy4_FFpbl4&color=default&ratio=5&clat=8.420997&clng=-6.036083&initz=2](http://0media.tw/t/geoevent/widget/?src=17u9luNKn77I4Tyz3pPADnr6sw3yiob0Z6Dy4_FFpbl4&color=default&ratio=5&clat=8.420997&clng=-6.036083&initz=2)

資料來源
[http://en.wikipedia.org/wiki/List\_of\_accidents\_and\_incidents\_involving\_commercial_aircraft](http://en.wikipedia.org/wiki/List_of_accidents_and_incidents_involving_commercial_aircraft)

空難事件資料庫：
[http://aviation-safety.net/database/](http://aviation-safety.net/database/)
列出各年的全球空難事件資料 有列出大約失事地點地圖

製作方式
1.  在協作文件中最上面右方填入你的名字 (列入 contributor)
2.  找個協作文件中想幫填的欄位
3.  找到他對應在資料來源中的位置
4.  工人智慧找出座標，死傷人數
5.  填進協作文件中
6.  回到 2.

欄位說明
- shortname: 為了友善的顯示在樣版中，一個夠短又可理解的名稱
    - 若省略的話, 會改用 name 欄位
- death: 死亡人數
- wounded: 受傷人數

注意:  死傷人數在 listing 裡面有時會忽略, 需要點到詳細資料頁面去看比較準確

### 有建議直接開 issue

[http://github.com/zbryikt/geoevent/issues](http://github.com/zbryikt/geoevent/issues)


## 討論

目前我針對death & wounded爬了wiki的資料，但會有一些值像是30 (including 7 on the ground)，這樣的情況是只需取int即可？（以下連結為爬完結果）
> 這樣的話就是取 30 
> [name=Kirby W]

> ok
> [name=JackHou]

> 順道一提, 失蹤的寫法是先算在死亡人數中, 然後在備註裡寫含多少人失蹤
> [name=Kirby W]

然後shortname的話現在看起來是用「名字@地點」的命名方式，還是說有其他規則呢？
> 目前是航空公司 航班@地點, 但有些比較著名的可以直接寫名字, 比方說 911
> [name=Kirby W]

＊　ＨＩ！外面的˙人發個問，就是關於空難的部分，如果是戰爭時期，例如[：駝峰航線](http://zh.wikipedia.org/wiki/%E9%A9%BC%E5%B3%B0%E8%88%AA%E7%BA%BF) 有沒有可能也算在內呢？
　　最近有個[紀錄片上映](http://www.pts.org.tw/theflyingtigers/ep3.htm)（[飛虎傳奇The Flying Tigers](http://www.google.com.tw/url?sa=t&rct=j&q=&esrc=s&source=web&cd=7&cad=rja&uact=8&ved=0CDsQFjAG&url=http%3A%2F%2Fwww.pts.org.tw%2Ftheflyingtigers%2Fep3.htm&ei=TELgVITcOIPV8gXn3oD4Dw&usg=AFQjCNHGlg-tKVP17Ip1iW98PoCiYC2KBA&sig2=QlsOE_qzoI84aHqfJimPyQ)） 　讓我聯想到這件事情。
　　［節錄］據統計，至二戰結束，_駝峰航線_沿途共埋葬了六百多架飛機，奪走一千多名機組人員的生命。
＊　我幾個月前收集到一些數據視覺化的影片　這裡順便分享給各位（尤其是Kirby）
 　　（從這個ＵＲＬ以下共５個）[世界の戦争1000年の歴史(西洋から見た)](https://www.youtube.com/watch?v=bYy2W_5F27M&list=PLn7CPpVp9BT2fjZ9g14xpQIEQiZMH0MW_&index=102) 　到了２戰時期會很強烈歐

