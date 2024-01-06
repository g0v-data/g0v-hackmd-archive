# Visual Studio2019 C# MongoDB連線與Insert(BsonDocument)
加入參考
using MongoDB.Bson;
using MongoDB.Driver;
```
MongoClient _client = new MongoClient("mongodb://sa:password@IP:Port");
MongoServer server = _client.GetServer();
MongoDatabase myDB = server.GetDatabase("DataBaseName");
MongoCollection<OPC> _data = myDB.GetCollection<OPC>("TableName");

BsonDocument dcc = new BsonDocument();
dcc.Add("ID", 123);
dcc.Add("VH_ID", 456);
dcc.Add("CARRIER_ID", 789);

BsonDocument doc = new BsonDocument {
    { "DBName_Device_TableName","AS400_AGVC_ACMD"},{"value",new BsonArray{dcc} }
};
BsonDocument doc2 = new BsonDocument {
    { "DBName_Device_TableName","AS400_AGVC_ACMD"},{"value",new BsonArray{dcc,dcc} }
};
BsonDocument doc3 = new BsonDocument {
    { "DBName_Device_TableName","AS400_AGVC_ACMD"},{"value",dcc}
};

_data.Insert(doc);
_data.Insert(doc2);
_data.Insert(doc3);

```
### doc
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_11884832bc9015362522fd2ccc2d1875.png)
### doc2
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d81ae3182621feeffb63fa7c48be40ea.png)
### doc3
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2f69d8a9b73743e9780e96a3170b9d6d.png)
