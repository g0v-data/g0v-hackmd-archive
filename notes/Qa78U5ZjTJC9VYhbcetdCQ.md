# C# Data to MongoDB Insert Update Delete

```
#region 取出資料表內最後一筆data
var cdc = myDB.GetCollection<BsonDocument>("CDC_increment_lsn")
.Find("{}")
.Sort("{UpdateTime:-1}")
.Limit(1)
.ToList();
#endregion
```
```
var coll = IMongoDatabasemdb.GetCollection<BsonDocument>(table_name);//指定要操作的MongoDB資料表
```
### Delete
```
string sad = "{ TRANSFER_ID: { $in: [ " + "\"2021-05-10 09:07:52.0447793\",\"2021-05-07 15:02:21.1762718\"" + "] } }";
string st1 = "{ TRANSFER_ID: { $in: [ ";
string st2 = "\"" + "2021-05-10 09:07:52.0447793" + "\",";
string st3 = "\"" + "2021-05-07 15:02:21.1762718" + "\",";
string st4 = "] } }";
delete_str = st1 + st2 + st3 +st4 ;
coll.DeleteMany(delete_str);
```

### Insert
```
public static Dictionary<string, object> add_data = new Dictionary<string, object>();
public static List<BsonDocument> all_data = new List<BsonDocument>();
Dictionary<string, object> onedata = config.add_data;
List<BsonDocument> insert_list = config.all_data;
nowTime = "";
nowtime = DateTime.Now;
nowTime = nowtime.ToString("yyyy-MM-dd HH:mm:ss.fffffff");
onedata.Add("UpdateTime", nowTime);
insert_list.Add(new BsonDocument(onedata));
onedata.Clear();
coll.InsertMany(insert_list);
insert_list.Clear(); 
```
### Update
```
static class config{
public static List<Update> update = new List<Update>();
}

public class Update{
public string filter { get; set; }
public string update { get; set; }
}

var filter = "{\"" + "TRANSFER_ID" + "\":\"" + row["TRANSFER_ID"].ToString().Replace(" ","") + "\"}";
var update = "{$set:" + "{\"" + "CMD_START_TIME" + "\":\"" + "2021-04-01 06:10:12.1111111"+"," + "CMD_STATUS" + "\":\"" + "3" + "\"}" + "}";

foreach (Update item in config.update) { //執行Update
coll.UpdateOne(item.filter, item.update);
}
```
### Find
```
var a = coll.Find("{ }").Sort("{_id:-1}").Limit(1).ToList();
Console.WriteLine(a[0]["TRANSFER_ID"].ToString());
```