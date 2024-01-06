#    專題進度
##    公佈欄
7/04前：達成5um半高寬、-1dB內的loss、類高斯場型
       (取決於間距與角度搭配)
7/11前：角度deadline且加入助教給予的grating coupler開始做layout
7/18~7/20：下線文件繳交日期
##    問題
(1)

(2)

(3)

(4)357要多注意到後面高階模是否有被激發到，可以用EME計算


(6)承1，
##    code
<font color="#f00"> 請用編輯模式複製!!! </font>

position=0;
percent=70;//70%開始
z0span=0;
z1span=0;
half_z=0;
addstructuregroup;
set("name","test_group");
set("x",0);
set("y",0);
set("z",0);
for(i=1:857)//300um
{ 
z0span=percent*0.35e-8;
half_z=z0span/2;
position=(0.35e-6*(i-1))+half_z;
select("s1"); #Si
copy(position,0,0);
set("name",i);
set("x span",z0span);
addtogroup("::model::test_group");

z1span=0.35e-6-z0span;
half_z=z1span/2;
position=(0.35e-6*i)-half_z;
select("s2"); #Sio2
copy(position,0,0);
set("name",i);
set("x span",z1span);
addtogroup("::model::test_group");
percent=percent-0.0467; //70% to 30%
}
//=================================================
<font color="#f00">New code</font>
position=0;
percent=60;
y0=0;
y0span=0.5e-6;
z0span=0;
z1span=0;
half_z=0;
addstructuregroup;
set("name","test_group");
set("x",0);
set("y",0);
set("z",0);
for(i=1:858)
{ 

z0span=percent*0.35e-8;
half_z=z0span/2;
position=(-300e-6)+(0.35e-6*(i-1))+half_z;
select("s2"); #Si
copy(position,0,0);
set("name",i);
set("x span",z0span);
set("y span",y0span);
addtogroup("::model::test_group");
y0span=y0span-0.42007e-9;   #0.5 to 0.14
percent=percent-0.0233;
}
addstructuregroup;
set("name","extend_group");
set("x",0);
set("y",0);
set("z",0);
for(j=1:571) #total 571 extend part
{ 

z0span=40*0.35e-8;
half_z=z0span/2;
position=(0.35e-6)+(0.35e-6*(j-1))+half_z;
select("s2"); #Si
copy(position,0,0);
set("name",j);
set("x span",z0span);
set("y span",y0span);
addtogroup("::model::extend_group");
}
 #<font color="#f00">以下為三良建議結構的code</font>
addstructuregroup;
set("name","extend_group+um+angle");
set("x",0);
set("y",0);
set("z",0);
for(k=1:571) #total 571 extend part
{ 
z0span=40*0.35e-8;
half_z=z0span/2;
position=(0.35e-6)+(0.35e-6*(k-1))+half_z;
y0=(2.452e-9)*(k-1); #degree 0.4 
select("s2"); #Si
copy(position,0,0);
set("name",k);
set("x span",z0span);
set("y span",y0span);
set("y",y0);
addtogroup("::model::extend_group+um+angle");
}
addstructuregroup;
set("name","extend_group-um-angle");
set("x",0);
set("y",0);
set("z",0);
for(l=1:571) #total 571 extend part
{ 
z0span=40*0.35e-8;
half_z=z0span/2;
position=(0.35e-6)+(0.35e-6*(l-1))+half_z;
y0=-(2.452e-9)*(l-1);
select("s2"); #Si
copy(position,0,0);
set("name",l);
set("x span",z0span);
set("y span",y0span);
set("y",y0);
addtogroup("::model::extend_group-um-angle");
}
//==================================================


##    結果

####    Taper 100um
在50um WGm與Taper接縫中的monitor E
光源為120um
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b1cd4ae6b2aeb9b3abff8ba695c9aa03.png)


><font color="#f00">猜測(開頭%數變小)：末端中心點能量更集中，擴散範圍收斂，
>起點端的穿透率變低(90%時穿透率最好)</font>

##    統整

>穿透率
>https://docs.google.com/spreadsheets/d/1Bj7tlHdhUPU57PoqMUBojWnsY4izMNqG3lYBPAK7Q7U/edit#gid=0

>峰值&擴散範圍
>https://docs.google.com/spreadsheets/d/1xoDref7zIlueSt3tVEltP3mq8Uo8BZOa80A4lm07icM/edit#gid=0

>穿透率統整
>https://docs.google.com/spreadsheets/d/1X_U5VHcNLDjJGCBT_aSDUp9OtHgtKmm_pNp4LFkGr-Q/edit#gid=0

###     延長200um(以半高寬視之擴散度由起點0.66um~終點2um)
####     overall
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_49601c6d0a31bc83ee286c9a2b9a99a0.png)

####     T
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4b80e13ad3cc9a4c72e92c8d1d65e8b4.png)


####    前段50umWG E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4b69bdf6316332e4bb5b3f8acac89082.png)


####    tapper中段 E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0e691ff5fa3ba110eafe2d8ff6435aab.png)


####    tapper to swg  E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_780b3dd0d220b2746b75d16447b71ad5.png)


####    mid of swg  E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fb470bbbb9f944cd969c3c93c5f7463e.png)


####    end of swg  E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0110c37a03ab9ad9d12d4f7e7990da3c.png)


####    half of extend  E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_be19bc5b6f2e9000b29bdefdf442488f.png)


####    end of extend  E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_48a529a81ac9203456acd701ee512ed8.png)

###     延長間隔0.5um三叉(以半高寬視之擴散度由起點0.66um~終點2um)
####     overall
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c4f6dc129c9bbe7155a7a06c47fdd73c.png)


####     T
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_083f382a7b30de077ee9153c3afb77e5.png)



####    前段50umWG E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_65d66170f04abae337e949d0f049930f.png)


####    tapper中段 E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6eeda9f4feb5f394a073e157722831e1.png)


####    tapper to swg  E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_982023911d739ac96246c186d2315a33.png)


####    mid of swg  E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2f56d372a75c183316dd1c6bd70bdac5.png)


####    end of swg  E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8815089662ae181193d42c106070f9bd.png)


####    half of extend  E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_83e306f49b70b0e1b6e16e6397080fc8.png)


####    end of extend  E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2b777738e4ade0125c0fbf5c0c3f48fd.png)

###     延長間隔0.75um三叉(以半高寬視之擴散度由起點0.66um~終點2.7um)
####     overall
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4179e26d8b1c301d750407c613b584c7.png)


####     T
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9a79ad03d072a8093165181bcb8aebec.png)


####    前段50umWG E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ff1c5b801939648880eb5538af0da892.png)


####    tapper中段 E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2e701224f0b4ab29bddb99ab826fb977.png)


####    tapper to swg  E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1e0ed177013eedb00c10a0b16c6fb901.png)


####    mid of swg  E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4fbaba61802b47c48099e2832fa98019.png)


####    end of swg  E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f2aaf88f5ee7ae971e76d0b62dad8849.png)


####    half of extend  E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e3cf62f0698ff416010f7e5b7934b6bc.png)


####    end of extend  E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a48a2646d822c1fdf9860ef400a99551.png)


###     延長間隔1um三叉(以半高寬視之擴散度由起點0.66um~終點3.2um)
####     overall
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_685a65662ead69bf2bbc4ab87c525671.png)


####     T
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6816502cf33f28c990f763061f3be9e6.png)


####    前段50umWG E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_da4d21231b73460b460cd97151f10977.png)


####    tapper中段 E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_bfa0bb51e4b67f764e575c88d1742bed.png)


####    tapper to swg  E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_630d7645869ddd08baeaf1ce678b06e0.png)


####    mid of swg  E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b4938c907b4ac4fdbf2a7348f6128ff1.png)


####    end of swg  E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_900498fe4b8dde62db2088dfe873224c.png)


####    half of extend  E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5083c64cb91405108f337a076bc0cdd8.png)


####    end of extend  E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2f7090f4c3cd3829081358296ec85e5c.png)

###     延長間隔1.25um三叉(以半高寬視之擴散度由起點0.66um~終點3.8um)
####     overall
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_808c7ca6074b3d55c64976ef20048bb3.png)


####     T
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_730ee1ff4e3a1ebbccd4f62846903a26.png)


####    前段50umWG E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b3b123a49f2925a5f9d91672a2b457a7.png)


####    tapper中段 E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_19de501df271b97e0cf0acb2f629c828.png)



####    tapper to swg  E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1cca080ac4dbc6878c05f5fe75da9955.png)


####    mid of swg  E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_214513a76a31343ba3ad01733bc0db79.png)


####    end of swg  E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8448f966f94dd86d1ead249c3d8df938.png)


####    half of extend  E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3b29344a52c21ee1f2316baba0a404bf.png)


####    end of extend  E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d2e64a478a39dcee1b48a79db3b6d208.png)


###     延長間隔1.5um三叉(以半高寬視之擴散度由起點0.66um~終點4.1um)
####     overall
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1c302aaf6480aa39e1eaf532dc036ba9.png)


####     T
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_963f28dde7973f0164419aa18fbc73ff.png)


####    前段50umWG E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c3931aff5dacb6db794beab68181757d.png)


####    tapper中段 E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_675ce196af9e57dae8e3d29c0edfb0db.png)


####    tapper to swg  E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_52448d4fcf7f426b80abbf6fd44d03e9.png)


####    mid of swg  E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2be88274195750182864848c268d7c82.png)


####    end of swg  E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c09e92175b4e36a4f3f4aea92b41ce82.png)


####    half of extend  E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_299ff977373d31409658a8668cf046b7.png)


####    end of extend  E
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c9c8f7a1ffbacb08d0400091d833ad01.png)
## sweep result
### 50um WG T
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4a827e02c0266997766e6ecae09b0765.png)

### end of extend  T
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d56c1c7b247b30243af3111c9cdca85f.png)

### 以0.85um做模擬、觀測優化與相關紀錄(sweep17)
####  overall
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_79abe0e70cb373a06d3172ae88c4134b.png)

####  穿透率
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d546c5dcbfee330d0cd5cb73b6ba1a21.png)

####  輸出場型 擴散度由0.66um~3.34um
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e6da5b7f4fff01073accdfb852cfef96.png)

