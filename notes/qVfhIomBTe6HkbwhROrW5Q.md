# 55688-研發處-派遣部-預約池API文件

## 一、文件說明
## 二、物件型別定義
### 1.IncomePilot，派遣法則。(列舉型別)
| IntValue | 說明 |
| -------- | -------- |
| ?待訂     | 預約池Pilot     |


## 三、API清單-APP
### 1.訂車API
| 項目         | 說明              |
| ----------  | ----             |
| API Name    | Dispatch/Order   |
| URL         | ?待訂             |
| HttpMethod  | Post             |
| ContentType | application/json |

**Request**


| FieldName | DataType    | Req. | Description                                                                              |
| --------- | ----------- | ---- | ---------------------------------------------------------------------------------------- |
| Income    | IncomePilot | Y    | a.訂車類別跟最終叫到的車輛類型無關。<br>b.實際派遣車輛會依據是否聯派等規則決定承接司機。 |
| OCSType   |          |      |                                                                                          |
|           |          |      |                                                                                          |
|           |          |      |                                                                                          |
|           |          |      |                                                                                          |
|           |          |      |                                                                                          |
|           |          |      |                                                                                          |
|           |          |      |                                                                                          |
|           |          |      |                                                                                          |



### 2.乘客預約任務查詢API

## 四、API清單-車機