KQL 語法
```
# 更改 retention time
.alter-merge table TABLE policy retention softdelete = 30d
.show table sdltelemetry policy retention


# 刪除 table data
.drop extents from TABLE
# Top 5 data
T | top 5 by Name desc nulls last

# debug
.show operations 
| where Operation == "DataIngestPull"
| where Database=="database"

.show capacity 


table
| count

.show ingestion failures 
| where Database == 'database'

# delete raw in table 
.drop extents from Table


# Azure Function debug 
requests
| project timestamp, id, operation_Name, success, resultCode, duration, operation_Id, cloud_RoleName, invocationId=customDimensions['InvocationId']
| where timestamp > ago(30d)
| where cloud_RoleName =~ 'sdleuprodqueue2' and operation_Name =~ 'sdldataingest' and success == "False"
| order by timestamp desc
| take 20

union traces
| union exceptions
| where timestamp > ago(30d)
| where operation_Id == '8260a13aab4ca443a521c30a1f6efa55'
| where customDimensions['InvocationId'] == 'ce278521-5d2e-4b8b-8244-58150b1e8524'
| order by timestamp asc
| project timestamp, message = iff(message != '', message, iff(innermostMessage != '', innermostMessage, customDimensions.['prop__{OriginalFormat}'])), logLevel = customDimensions.['LogLevel']


let trace_id = 'a062865e7a7cff4185c0f8680059b537';
traces
| project timestamp, message, operation_Id, logLevel = customDimensions.['LogLevel']
| where operation_Id  == trace_id
| union (exceptions 
| project timestamp, message = iff(message != '', message, iff(innermostMessage != '', innermostMessage, customDimensions.['prop__{OriginalFormat}'])), operation_Id, logLevel = customDimensions.['LogLevel']
| where operation_Id  == trace_id)
| order by timestamp asc;
```