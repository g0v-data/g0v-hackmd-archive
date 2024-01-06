# Trigger(補)
###### tags: `TSQL`
---

inserted/deleted table
---
DML Trigger 是有insert/delete/update

在觸發dml trigger後，如果你的動作是要insert新的資料進去table，sql server會把同時創造一個table叫inserted，我們的table會從這個table抓出來insert;而deleted table就有點不一樣，假設你今天要刪除某個值為value時你會這樣打
```sql=
delete * from Table_Name where Column_Name = value
```
如果table裡沒有這個值的話，你的deleted table會沒有顯示任何東西，但有這個值的話你的deleted table就會存你要刪除的資料，在那個table你已經刪掉了

update則是兩個table都會參與到，所以inserted table會留你要更新後的那筆資料，而deleted table 則會留你更新前的那筆資料


Disabled Trigger
---
trigger簡單來講就是當你遇到某些狀況時你所採取的動作觸發器，而有些情況會讓你開後門給他，也就是所謂的例外，在這種情況我們會停用trigger來達到我們的目的。
```sql=
disable trigger TriggerName on TableName
```
如果你要把在那個table裡的trigger全部關閉
```sql=
disable trigger all on TableName
```
如果要重啟就把disable 換成 enable就好了

instead of
---


