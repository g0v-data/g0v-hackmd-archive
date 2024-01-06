# SQL
SELECT DISTINCT "欄位名"
FROM "表格名";

---
SELECT "欄位名"
FROM "表格名"
WHERE "簡單條件"
[AND|OR] "簡單條件";

---
SELECT "欄位名"
FROM "表格名"
WHERE "欄位名" IN ('值一', '值二', ...);

---
SELECT "欄位名"
FROM "表格名"
WHERE "欄位名" BETWEEN '值一' AND '值二';

---
% (百分比符號)：代表零個、一個、或數個字母。

_ (底線)：代表剛好一個字母。

萬用字元是與 LIKE 關鍵字一起使用的。

'A_Z'
'ABC%'

---
SELECT "欄位名"
FROM "表格名"
WHERE "欄位名" LIKE {模式};

---
## 排序
SELECT "欄位名"
FROM "表格名"
[WHERE "條件"]
ORDER BY "欄位名" [ASC, DESC];

---
AVG (平均)
COUNT (計數)
MAX (最大值)
MIN (最小值)
SUM (總合)

---
SELECT "函數名"("欄位名")
FROM "表格名";

---
SELECT "欄位1", SUM("欄位2")
FROM "表格名"
GROUP BY "欄位1";

---
SELECT "欄位1", SUM("欄位2")
FROM "表格名"
GROUP BY "欄位1"
HAVING (函數條件);

---
## 別名
SELECT "表格別名"."欄位1" "欄位別名"
FROM "表格名" "表格別名";

---
SELECT "表格別名"."欄位1" AS "欄位別名"
FROM "表格名" AS "表格別名";

---
## 連接
SELECT A1.Region_Name REGION, SUM(A2.Sales) SALES
FROM Geography A1, Store_Information A2
WHERE A1.Store_Name = A2.Store_Name
GROUP BY A1.Region_Name;

---
SELECT A1.Store_Name, SUM(A2.Sales) SALES
FROM Georgraphy A1, Store_Information A2
WHERE A1.Store_Name = A2.Store_Name (+)
GROUP BY A1.Store_Name;

---
CONCAT(字串1, 字串2, 字串3, ...)

SELECT CONCAT(Region_Name, Store_Name) FROM Geography
WHERE Store_Name = 'Boston';

---
SUBSTR (str, pos, len)

由 <str> 中的第 <pos> 位置開始，選出接下去的 <len> 個字元。

SELECT SUBSTR(Store_Name, 3)
FROM Geography
WHERE Store_Name = 'Los Angeles';

---
TRIM ( [ [位置] [要移除的字串] FROM ] 字串): [位置] 的可能值為 LEADING (起頭), TRAILING (結尾), or BOTH (起頭及結尾)。 這個函數將把 [要移除的字串] 從字串的起頭、結尾，或是起頭及結尾移除。如果我們沒有列出 [要移除的字串] 是什麼的話，那空白就會被移除。

LTRIM (字串): 將所有字串起頭的空白移除。

RTRIM (字串): 將所有字串結尾的空白移除。

SELECT TRIM ('   Sample   ');

---
Length (str)

---
Replace (str1, str2, str3)

在字串 str1 中，當 str2 出現時，將其以 str3 替代