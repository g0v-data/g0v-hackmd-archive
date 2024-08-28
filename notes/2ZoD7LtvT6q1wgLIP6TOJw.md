Crema 3.- 模板架構說明
[模板官方說明文件](https://docs.cremawork.com/v/v-3)
#### 專案參數設定檔案， :file_folder: next.config.js.js
含:資料庫連線、系統參數、發送email帳密、jwt_secret ... 等。
#### 網站基本設定
* 登入後的預設頁面:  
    * AppConst.js，變數: const initialUrl 
:file_folder:(`src\shared\constants\AppConst.js`)
    Crema v4: `src\@crema\constants\AppConst.js`
* 左側 menu 路由清單 及 存取權限 : 
    * routesConfig.js 
:file_folder:(`src\modules\routesConfig.js`)
Crema v4:  `\src\@crema\core\AppRoutes\routeConfig.js`
* 路由/頁面的權限類別:  
	* routesConfig.js，變數: const RoutePermittedRole 
:file_folder:(`src\shared\constants\AppConst.js`)
		mgmt_: 表示擁有平台權限
	    org_: 表示擁有機構權限
	* ~~const authRole，目前未使用~~
    Crema v4: `\src\@crema\constants\AppEnums.js`

#### 頁面架構
* 主階層: :file_folder:`src\pages\_app.js`
* 模板全域變數( Auth Context / JWTAuthProvider)  user object 設定: 
	1. :file_folder:`src\@crema\services\auth\jwt-auth\JWTAuthProvider.js` 取得 user 登入者的資料、登入及登出 function
	2. :file_folder:`src\@crema\utility\AuthHooks.js` 設定 1.的hook
	3. :file_folder:`src\@crema\utility\helper\AuthHelper.js` 設定 2.hook，user object 傳出的細部資料格式
* 自定義全域變數 context : :file_folder:`context\`
	* 切換後台當下所在的組織階層，eg. 平台 or OOO機構
* 新增自訂頁面:  
	1. 新增頁面網址
		* 路徑: :file_folder:`src\pages\頁面網址名稱\檔名`，頁面網址名稱小寫開頭
		* 檔名: index.js 或 [id].js，
		* eg.  `src\pages\members\training-list\single\[training_program_id].js`
		* eg.  `src\pages\members\list\index.js`
	2. 新增頁面對應module檔案:  :file_folder:`src\modules\頁面模組\index.js` ，頁面模組大寫開頭
	3. 修改 routesConfig.js 設定
	4. 於 module 檔案內呼叫 API : 
		1. 引入，`import { apiGetAction } from "@/pages/api/api.js";`
		2. 使用，`const response = await apiGetAction({training_action_id: training_action_id});`
		3. 範例 :
		   ```JSX
		   async function listActions(org_id, status, training_module_id) {
               try {
                   const response = await apiListActions({org_id: org_id, status: status, training_module_id: training_module_id});
                   const actions = response.data.map(function (item, index) {
                       let array = {
                           training_action_id : item.training_action_id,
                           action_name: item.action_name,
                           left: item.lefthand_position_x+'-'+item.lefthand_position_y,
                           right: item.righthand_position_x+'-'+item.righthand_position_y,
                           stay_times: item.stay_times,
                           action_type : item.action_type
                           }
                           return array
                           });
                           return actions;
                } catch (err) {
                    //console.error(err);
                    return false;
                }
            }
			```
	
#### API
* API For APP 放置路徑規則:　:file_folder:`src\pages\api\app\v版本號\`
* API For Web 放置路徑規則:　:file_folder:`src\pages\api\web\v版本號\模組名稱` 或 :file_folder:`src\pages\web\共用模組名稱\` 
  Crema v4 放置規則:　`src\app\`
* 網站登入認證 API 及 token 內容設定: auth.js 
:file_folder:(`src\pages\api\auth.js`)
* API 路徑管理及存取版本設定: api.js 
:file_folder:(`src\pages\api\api.js`)，該架構參考網路範本
  ``` jsx
	// 設定版本路徑，eg. 後台統計分析的 api，若後續若遇 API 變更版本時，只要更改此路徑即可
	const saRequest = axios.create({
        baseURL: process.env.URL + "api/web/v2/sa/",
	});
	
	// 設定呼叫的 api， eg.後台統計分析的 api
	export const apiGetSaTraining = (data) => saRequest.post("/getTrainingStatistics", data);
	export const apiGetSaMember = (data) => saRequest.get("/getMembersTraining", data);
	```
* API 連接資料庫使用方式:
  ```JSX
	var db = require('../../../../lib/db');
	import moment from 'moment';
	import Moment from 'moment-timezone';
	
	// 新增
	var query = 'INSERT INTO training_actions (action_type, x_grids, y_grids) VALUES (?, ?, ?);';
    var values =  ['customer', customerAction.x_grids, customerAction.y_grids];
    const createActionResults = await db.excuteQuery(query, values);
    var trainingActionId = createActionResults.insertId;
	
    // 取得
    var query = 'SELECT SQL_CALC_FOUND_ROWS p.training_program_id as id FROM training_programs as p  WHERE p.member_id = ? ;
    var values = [user_id];
    const results = await db.excuteQuery(query, values);
	```
* db連線設定: db.js
:page_with_curl:`lib\db.js`