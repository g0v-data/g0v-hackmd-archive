# 活動報表後台API Spec
##### <font color="red">ps. 因後台權限架構導致API無法使用restful風格設計 </font>

<br> 


### 活動列表
* 請參考舊有API撈取上架中活動
* Http Method: **POST**
* 請求Path: **/api/gl/activity/manage/list**
* 請求參數:status=1, size=1000

<hr>

### 活動參與名單列表
* 請求Path: **/api/gl/participant/list**
* Http Method: **POST**
* Req格式: **JSON**
* Resp格式: **JSON**
* Request 參數詳情

| 編號 | 參數 | 名稱 | 型態 | 是否必須 | 範例 | 備註 |
| :----: | :----: | :----: | :----:| :----: | :----: | :----: |
| 1 | activityId | 參與活動名單編號 | Integer| N | 1 ||
| 2 | startTime | 參與開始時間 | String| Y | 2021-03-24 00:00:00 ||
| 3 | endTime | 參與結束時間 | String| Y | 2021-03-24 23:59:59 ||
| 4 | userName | 用戶名 | String| N | stan666 ||
| 5 | page | 頁數 | Integer| N | 1 ||
| 6 | size | 每頁大小 | Integer| N | 10 ||
* Response Data 參數詳情

| 編號 | 參數 | 名稱 | 類型 | 備註 |
| :----: | :----: | :----: | :----: | :----: |
|1|userId|用戶ID|Integer||
|2|userName|用戶名|String||
|3|activityId|參與活動編號|Integer||
|4|activityName|參與活動名稱|String||
|5|joinTime|參與時間|String||


* 範例
```json
{
   "code": 1,
   "message": "SUCCESS",
   "data":{
	   "total":10,
	   "list":[
		   {... 上述內容 ...}
	   ]
   }
}
```
<hr>

### 活動參與名單報表導出
* 請求Path: **/api/gl/activity/participant/report/generate**
* Http Method: **POST**
* Req格式: **JSON**
* Resp格式: **JSON**
* Request 參數詳情

| 編號 | 參數 | 名稱 | 型態 | 是否必須 | 範例 | 備註 |
| :----: | :----: | :----: | :----:| :----: | :----: | :----: |
| 1 | activityId | 參與活動名單編號 | Integer| N | 1 ||
| 2 | startTime | 參與開始時間 | String| Y | 2021-03-24 00:00:00 ||
| 3 | endTime | 參與結束時間 | String| Y | 2021-03-24 23:59:59 ||
| 4 | userName | 用戶名 | String| N | stan666 ||

* Response Data 參數詳情

| 編號 | 參數 | 名稱 | 類型 | 備註 |
| :----: | :----: | :----: | :----: | :----: |
|1|id|ID|Integer||
|2|source|報表來源|String|活动参与名单下载|
|3|type|文件類型|Integer|ACTIVE_PARTICIPANT_LIST|
|4|objectId|文件上傳的id|String||
|5|url|文件位置|String||
|6|createTime|創建時間|String||
|7|updateTime|更新時間|String||
|8|status|狀態|String|0待生成 1成功，2失败|


* 範例
```json
{
   "code": 1,
   "message": "SUCCESS",
   "data":{
	   "total":10,
	   "list":[
		   {... 上述內容 ...}
	   ]
   }
}
```




