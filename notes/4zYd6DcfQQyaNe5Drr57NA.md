# 判斷MongoDB內Table是否存在
```
public bool CollectionExists(IMongoDatabase database, string collectionName)
        {
            var filter = new BsonDocument("name", collectionName);
            var options = new ListCollectionNamesOptions { Filter = filter };
            return database.ListCollectionNames(options).Any();
        }

# 依照TableName取最後一筆的RecordTime
```
### h3region 依照TableName取最後一筆的RecordTime  
```
var collection = myDB.GetCollection<BsonDocument>(table_name);
var sort = Builders<BsonDocument>.Sort.Descending("_id");
List<BsonDocument> doc = collection.Find(new BsonDocument()).Sort(sort).Limit(1).ToList();
DateTime recordtime = DateTime.Parse(doc[0]["UpdateTime"].ToString());
string recordTime = recordtime.ToString("yyyy-MM-dd HH:mm:ss.fffffff");
Console.WriteLine(recordTime);
                        
```