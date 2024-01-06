**五尺傳統**
fieldname
基本尺 4 倍數 5 軌道售價 38 布價 7 折數 39
窗寬 11 窗高 13 布價進位 15

幅數 41
CEIL( fieldname11 * fieldname5 /5)

才數 25 null

總尺數 42
CEIL( fieldname41 * CEIL( (fieldname13+1),0.1)+1,0.1 )

牌數 96,27
fieldname28+fieldname45+fieldname44

布價 97,28
IF(CEIL((fieldname39*fieldname7),10)<100
,fieldname42*(CEIL((fieldname39*fieldname7),10)+10)
,fieldname42*(CEIL((fieldname39*fieldname7),10)))

車工 98,45 null

軌道 99,44
IF(fieldname11<=fieldname4
,fieldname38*fieldname4
,CEIL(fieldname11)*fieldname38)

鉛條 100,43
CEIL(CEIL((fieldname11*fieldname5+2),0.1)*25,0)


**九尺傳統**
fieldname
基本尺 81,4 折景倍數 79,5 軌道售價 66,38 布價 83,7 折數 82,39
窗寬 11 窗高 4,13 

面寬*折景倍數 67,15
(CEIL( fieldname11 * fieldname5,0.1))

布價*折數 101,46
CEIL( fieldname7* fieldname39,10)

幅數 93,41 null

才數 86,25 null

尺數 95,42
fieldname15+2

牌數 96,27
fieldname28+fieldname45+fieldname44

布價 97,28
IF(fieldname46<=120,fieldname42*(fieldname46+20),IF(fieldname46<=130,fieldname42*(fieldname46+10),fieldname42*fieldname46))

車工 98,45 null

軌道 99,44
IF(fieldname11<=fieldname4
,fieldname38*fieldname4
,CEIL(fieldname11)*fieldname38)

鉛條 100,43
CEIL(CEIL((fieldname11*fieldname5+2),0.1)*25,0)



**五尺蛇簾**
fieldname
基本尺 81,4 折景倍數 79,5 布價 83,7 折數 82,39
蛇簾車工 66,38 蛇簾軌道 101,46
窗寬 11 窗高 4,13 

布價*折數 67,15
(CEIL( fieldname11 * fieldname5,0.1))

寬高*幅數 102,47
CEIL(fieldname41*(fieldname13+1),0.1)

幅數 93,41
CEIL( fieldname11 * fieldname5 /5)

才數 86,25 null

尺數 95,42
fieldname47+1

牌數 96,27
fieldname28+fieldname45+fieldname44

布價 97,28
IF(fieldname15<100,fieldname42*(fieldname15+10),fieldname42*(fieldname15))

車工 98,45
CEIL( fieldname41* fieldname38)

軌道 99,44
IF(fieldname11<=fieldname4
	,fieldname46*fieldname4
	,CEIL(fieldname11)*fieldname46)

鉛條 100,43
CEIL(CEIL((fieldname11*fieldname5+2),0.1)*25,0)



**九尺蛇簾**
fieldname
基本尺 81,4 折景倍數 79,5 布價 83,7 折數 82,39
蛇簾車工 104,38 蛇簾軌道 66,46
窗寬 11 窗高 4,13 

布價*折數 101,15
(CEIL( fieldname7 * fieldname39,0.1))

面寬*折景倍數(0.1) 67,47
CEIL(fieldname11 * fieldname5,0.1)

面寬*折景倍數(0) 105,48
CEIL(fieldname11 * fieldname5)

幅數 93,41 null

才數 86,25 null

尺數 95,42
fieldname47+2

牌數 96,27
IF(fieldname15<=120,fieldname42*(fieldname15+20),IF(fieldname15<=130,fieldname42*(fieldname15+10),fieldname42*fieldname15))+fieldname38*CEIL(((fieldname11*fieldname5+2)/3))+IF(fieldname11<=fieldname4,fieldname46*fieldname4,CEIL(fieldname11)*fieldname46)

布價 97,28
IF(fieldname15<=120,fieldname42*(fieldname15+20),IF(fieldname15<=130,fieldname42*(fieldname15+10),fieldname42*fieldname15))

車工 98,45
fieldname38*fieldname48

軌道 99,44
IF(fieldname11<=fieldname4
	,fieldname46*fieldname4
	,CEIL(fieldname11)*fieldname46)

鉛條 100,43
CEIL(CEIL((fieldname11*fieldname5+2),0.1)*25,0)



**五尺羅馬**
fieldname
基本尺 81,4 基本才 104,49
布價 83,7 折數 82,39
羅馬車工 66,38 羅馬軌道 101,46
窗寬 11 窗高 4,13 

布價*折數 67,15
(CEIL( fieldname7 * fieldname39,10))

窗高*幅數 102,47
fieldname41*CEIL((fieldname13+1),0.1)

幅數 93,41 
CEIL( (fieldname11 -0.5) /5)

才數 94,25
CEIL( fieldname11*fieldname13, 0.1)

尺數 95,42
fieldname47+1

牌數 96,27
fieldname28+fieldname45+fieldname44

布價 97,28
IF(fieldname15<100,fieldname42*(fieldname15+10),CEIL(fieldname42*fieldname15))

車工 98,45
CEIL(IF((fieldname11*fieldname13)>=fieldname49,(fieldname11*fieldname13)*CEIL(fieldname38,-1),fieldname49*CEIL(fieldname3,-1)))

軌道 99,44
IF(fieldname11<=fieldname4
	,fieldname46*fieldname4
	,CEIL(fieldname11)*fieldname46)


**九尺羅馬**
fieldname
基本尺 81,4 基本才 104,49
布價 83,7 折數 82,39
羅馬車工 66,38 羅馬軌道 101,46
窗寬 11 窗高 4,13 

布價*折數 67,15
~~(CEIL( fieldname7 * fieldname39,10))~~

窗高*幅數 102,47
~~fieldname41*CEIL((fieldname13+1),0.1)~~

幅數 93,41 null

才數 94,25
~~CEIL( fieldname11*fieldname13, 0.1)~~

尺數 95,42
CEIL(fieldname11+0.5, 0.1)

牌數 96,27
~~fieldname28+fieldname45+fieldname44~~

布價 97,28
IF(fieldname15<=120,CEIL(fieldname11+2,0.1)*CEIL((fieldname7*fieldname39+20),10),(IF(fieldname15<=130,CEIL(fieldname11+2,0.1)*CEIL((fieldname7*fieldname39+10),10),CEIL(fieldname11+2,0.1)*fieldname15)))	

車工 98,45
~~CEIL(IF((fieldname11*fieldname13)>=fieldname49,(fieldname11*fieldname13)*CEIL(fieldname38,-1),fieldname49*CEIL(fieldname3,-1)))~~

軌道 99,44
~~IF(fieldname11<=fieldname4
	,fieldname46*fieldname4
	,CEIL(fieldname11)*fieldname46)~~