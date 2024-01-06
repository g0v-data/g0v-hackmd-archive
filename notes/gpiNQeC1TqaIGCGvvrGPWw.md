# Code Review 2019 / 06 / 26 - sql


==1.== 
- 使用哪個join要注意

---

==2.==
- 若有遇到排名問題，要注意到排名的依據會不會有相同名次的問題
- 可以使用RANK()
- 可以使用WITH TIES，把所有排名依據相同的都輸出出來
以TOP(6)為例子較為明顯，若加上WITH TIES會將相同數量視為共同排名第六並列出所有內容
```sql=
SELECT TOP(6) WITH TIES L.BOOK_ID AS BookId, 
		d.BOOK_NAME AS BookName, 
		COUNT(L.BOOK_ID) AS QTY
FROM BOOK_LEND_RECORD L
 INNER JOIN BOOK_DATA d
  ON L.BOOK_ID = d.BOOK_ID
GROUP BY L.BOOK_ID, d.BOOK_NAME
ORDER BY QTY DESC; 
```
結果如下：

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_3ea13569016c73c2e6f45e08b9f4548a)

而在沒有WITH TIES的情況，結果如下：

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_23e3f99a89875ef8f85110a924332e20)



---
==3.== 
- 可以使用join級距表，來劃分界線

---
==4.==
- 與第二題類似
- 注意**ROW_NUMBER()**與**RANK()**
```sql=
/*ROW_NUMBER()在查詢的結果加上編號*/
SELECT Result.Seq, Result.BookClass, Result.BookId, Result.BookName, Result.Cnt
FROM(
	SELECT	ROW_NUMBER() OVER (PARTITION BY bc.BOOK_CLASS_NAME ORDER BY COUNT(bd.BOOK_ID)DESC) AS Seq, 
			bc.BOOK_CLASS_NAME AS BookClass,
			bd.BOOK_ID AS BookId,
			bd.BOOK_NAME AS BookName,
			COUNT(bd.BOOK_ID) AS Cnt
	FROM BOOK_LEND_RECORD AS blr
	LEFT JOIN BOOK_DATA AS bd
		ON blr.BOOK_ID = bd.BOOK_ID
	LEFT JOIN BOOK_CLASS AS bc
		ON bd.BOOK_CLASS_ID = bc.BOOK_CLASS_ID
	GROUP BY	bc.BOOK_CLASS_NAME, 
				bd.BOOK_ID,
				bd.BOOK_NAME
)Result
WHERE Seq <= 3
ORDER BY	Result.BookClass,
			Result.Cnt DESC, 
			Result.BookId
```
```sql=
/*使用RANK()，相比的資料數據相同，給予同樣的排名*/
SELECT Result.Seq, Result.BookClass, Result.BookId, Result.BookName, Result.Cnt
FROM(
	SELECT	RANK() OVER (PARTITION BY bc.BOOK_CLASS_NAME ORDER BY COUNT(bd.BOOK_ID)DESC) AS Seq, 
			bc.BOOK_CLASS_NAME AS BookClass,
			bd.BOOK_ID AS BookId,
			bd.BOOK_NAME AS BookName,
			COUNT(bd.BOOK_ID) AS Cnt
	FROM BOOK_LEND_RECORD AS blr
	LEFT JOIN BOOK_DATA AS bd
		ON blr.BOOK_ID = bd.BOOK_ID
	LEFT JOIN BOOK_CLASS AS bc
		ON bd.BOOK_CLASS_ID = bc.BOOK_CLASS_ID
	GROUP BY	bc.BOOK_CLASS_NAME, 
				bd.BOOK_ID,
				bd.BOOK_NAME
)Result
WHERE Seq <= 3
ORDER BY	Result.BookClass,
			Result.Cnt DESC, 
			Result.BookId
```


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_5fe49750cc21970e014de235082c918c)





---
==5.==
- JOIN要注意，各種JOIN的使用時機

---
==6.== 
- 單引號使用注意!先確認型別，INT就不用使用了
- AS後面的命名盡量不要使用到保留字

**動態PIVOT**

---
==7.== 
- 注意CODE TYPE
- 日期格式：通常的格式是2019/06/26(有補0的狀況)，而不會是2019/6/26
- 組合字串IS NULL 防止該格為空
- char中的 varchar，若遇到中文難字時可以利用N，不然結果會是0
```sql=
SELECT N'峯'
```
- NVARCHAR、CHAR、
- CONVERT可以轉換輸出形式 https://dotblogs.com.tw/spark/2009/08/05/9868

---
==8.==
- Transation處理來確保資料能夠正確執行UPDATE、INSTERION、DELETE等等動作。
- 可以先檢查update資料數量，再update

```sql=

/*先檢查*/
SELECT *
--UPDATE A SET LEND_DATE = '2019-01-02 00:00:00.000'
FROM BOOK_LEND_RECORD AS A 
WHERE A.KEEPER_ID = 0002

/*再執行更改資料的指令*/
INSERT INTO BOOK_LEND_RECORD(BOOK_ID, KEEPER_ID, LEND_DATE) 
	VALUES (2004, '0002', '2019-01-02 00:00:00.000');

SELECT bd.BOOK_ID AS 書本ID,
	FORMAT(bd.BOOK_BOUGHT_DATE, 'd', 'zh-TW') AS 購書日期,
	REPLACE(FORMAT(blr.LEND_DATE, 'd', 'KO-KR'), '-','/') AS 借閱日期,
	bcla.BOOK_CLASS_ID + '-' + bcla.BOOK_CLASS_NAME AS 書籍類別
	,blr.KEEPER_ID+'-'+mm.USER_CNAME+'('+mm.USER_ENAME+')' AS 借閱人,
	bd.BOOK_STATUS + '-' + bcod.CODE_NAME AS 狀態,
	REPLACE(CONVERT(NVARCHAR(20),CAST(bd.BOOK_AMOUNT AS Money) ,1),'.00','') + '元' AS 購買金額
FROM BOOK_LEND_RECORD AS blr
LEFT JOIN BOOK_DATA AS bd
	ON blr.BOOK_ID = bd.BOOK_ID
LEFT JOIN MEMBER_M AS mm
	ON blr.KEEPER_ID = mm.[USER_ID]
LEFT JOIN BOOK_CLASS AS bcla
	ON bd.BOOK_CLASS_ID = bcla.BOOK_CLASS_ID
LEFT JOIN BOOK_CODE AS bcod
	ON bd.BOOK_STATUS =  bcod.CODE_ID
WHERE blr.KEEPER_ID = 0002
ORDER BY bd.BOOK_AMOUNT DESC
```
---
==9.==
- 為了避免只選取到一行程式碼執行，所以把WHERE拿到第一行來做，若後方條件太長，那就只留WHERE，其餘的丟到下一行
```sql=
DELETE FROM BOOK_LEND_RECORD
WHERE BOOK_LEND_RECORD.BOOK_ID = 2004
```


- 如果沒有提供編碼類型，可以直接在SSMS裡面查看
    - 反白要查詢的，按Alt + F1
    - 安裝SQL Complete
    - 左側物件總管的資料苦資料行