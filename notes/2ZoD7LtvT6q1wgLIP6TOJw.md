Crema 3.- 模板架構說明
[模板官方說明文件](https://docs.cremawork.com/v/v-3)

### Installing Template
1. 安裝 : run the following command to run the project in the browser.
``` command
yarn
```
2. 資料庫連線設定，於根目錄 next.config.js
3. 執行 dev 模式 : run the following command to run the project in the browser.
``` command
yarn start
```
3. 打包
``` command
yarn build
```

---

### 專案架構說明
#### 專案環境變數設定檔案， :file_folder: next.config.js.js
含: 資料庫連線、系統參數、發送通知email的帳密、jwt_secret ... 等，可以在全站內使用。
#### 網站基礎變數設定
* 登入後，網站預設的首頁頁面/網址:  
    * AppConst.js，變數: ` const initialUrl` 
:file_folder:(`src\shared\constants\AppConst.js`)
    Crema v4: `src\@crema\constants\AppConst.js`
* 網站左側 menu 路由清單 及 存取權限 : 
    * 設定檔案: routesConfig.js，變數: `const routesConfig`
:file_folder:(`src\modules\routesConfig.js`)
Crema v4:  `\src\@crema\core\AppRoutes\routeConfig.js`
    * 程式碼 components
:file_folder:(`src\@crema\core\AppLayout\components\VerticalNav\`)
* 路由/頁面的權限類別:  
	* routesConfig.js，變數: `const RoutePermittedRole` 
:file_folder:(`src\shared\constants\AppConst.js`)
		mgmt_: 自定義，表示擁有平台權限
	    org_: 自定義，表示擁有機構權限
        * 使用範例
        ```JSX
        import {useAuthMethod, useAuthUser} from '@/@crema/utility/AuthHooks';
        
        const usePermission = (user) => {
          const roles = user.role || [];
          const can_view = roles.some(role => ['mgmt_admin', 'org_admin', 'mgmt_user_view', 'org_user_view', 'mgmt_user_edit', 'org_user_edit'].includes(role));
          const can_edit = roles.some(role => ['mgmt_admin', 'org_admin', 'mgmt_user_edit', 'org_user_edit'].includes(role));

          return { can_view, can_edit };
        };
        
        const Table = () => {
          const router = useRouter()
          const {user, isAuthenticated, isLoading} = useAuthUser();
          const { can_view, can_edit } = usePermission(user);

          // 判断是否具有查看或编辑權限
          if (!can_view && !can_edit) {
            return (
              <div><h4>無人員管理權限</h4></div>
            );
          }}
        ```

	* ~~const authRole，目前未使用~~
    Crema v4: `\src\@crema\constants\AppEnums.js`

#### 頁面架構 及 相關使用說明
* 主階層( 網站 index ): :file_folder:`src\pages\_app.js`
* 模板全域變數 : 
    * Auth Context / JWTAuthProvider， 全域變數 User Object 的設定: 
        1. :file_folder:`src\@crema\services\auth\jwt-auth\JWTAuthProvider.js` 取得 user 登入者的資料、登入及登出 function
        2. :file_folder:`src\@crema\utility\AuthHooks.js` 設定 1.的hook
        3. :file_folder:`src\@crema\utility\helper\AuthHelper.js` 設定 2.hook，user object 傳出的細部資料格式
        4. 詳細說明[參考筆記](https://coda.io/d/_dcVt0nnt0Ca/NextJs-React-Template-Crema-Theme_su0hAYTx)
* 自定義全域變數 context : :file_folder:`context\`
	1. 自定義功能1 `context\HeaderContextProvider.js` : 切換後台當下所在的組織階層，eg. 平台 or OOO機構
( 記得在 _app.js 引入 )
* 新增自訂頁面:  
	1. 新增頁面網址
		* 路徑: :file_folder:`src\pages\頁面網址名稱\檔名`，頁面網址名稱小寫開頭
		* 檔名: index.js 或 [id].js
		* eg.  `src\pages\members\training-list\single\[training_program_id].js`
		* eg.  `src\pages\members\list\index.js`
	2. 新增頁面對應的 module 檔案:  :file_folder:`src\modules\頁面模組\index.js` ，頁面模組資料夾名稱大寫開頭
	3. 修改 routesConfig.js 設定專案 router /  左側 menu，及頁面權限
*  呼叫 API : 
    在 module\ 內 或是 api\ 內用法相同
		1. 引入方式，`import { apiGetAction } from "@/pages/api/api.js";`
		2. 使用方式，`const response = await apiGetAction({training_action_id: training_action_id});`
		3. 範例 :
    * 方式1. 使用 NextJs fetching-data-on-the-client-side
	```JSX
	import { apiGetAction } from "@/pages/api/api.js";
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
    
    React.useEffect(() => {
       const fetchData = async () => {
           try {
               setLoading(true);
               await listActions(org_id, status, training_module_id);
               setLoading(false);
           } catch (err) {
               console.log(err);
           }
       }

       // Call the function
       fetchData();
   }, []);
	```
    
    * 方式2. 使用 React Query
    ```JSX
    const usersQuery = useQuery({
        queryKey: ['users', { state, currentOrgId }],
        queryFn: () => {
            const params = {
                ...(currentOrgId && { org_id: currentOrgId }),
                ...(state.searchColumn && { [state.searchColumn]: state.search }),
                rowsPerPage,
                currentPage: state.page + 1,
            };
            const searchParams = new URLSearchParams(params).toString();  
            switch (state.tabCurrent) {
                case 0:
                    return  apiGetAdmins(searchParams)
                case 1:
                    return  apiGetDoctors(searchParams)
                default:
                    return  apiGetAdmins(searchParams)
            }
        },
        /* enabled: Boolean(currentOrgId && state.page !== null), // 仅在条件满足时启用查询 */
    });
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
    const results = await db.excuteQuery(query, value);
    
    res.statusCode = 200;
    res.json({
        "Errorcode" : 0, 
        "total": total,//總共頁碼數
        "all": totalCount,//總共資料筆數
        "page": currentPage ,//當前頁碼
        "detail": results
    });
	```
* db連線設定: db.js
:page_with_curl:`lib\db.js`

#### 前端 fetchData
1. getStaticProps : 适合静态内容或部分更新的页面
2. getStaticPaths 
3. getServerSideProps : 适合需要实时数据的页面
适用场景: 适合需要在每次请求时都获取最新商品数据的场景，例如商品价格、库存经常变化。
```JSX
export async function getServerSideProps({ params }) {
  const res = await fetch(`https://api.example.com/product/${params.id}`);
  const product = await res.json();

  return {
    props: { product },
  };
}

```
4. Forms and Mutations : 适合处理用户输入的数据操作
5. Incremental Static Regeneration (ISR) : 适合静态内容或部分更新的页面
6. Client-side Fetching : 适合用户交互后获取数据，或者非 SEO 关键的页面。
适用场景: 商品页面数据可以在客户端渲染后再加载，不需要首屏立即显示完整数据。可以用于在页面首次加载时显示基本商品信息，而复杂的库存、价格、评论等通过客户端获取。
```JSX
useEffect(() => {
    const fetchProduct = async () => {
      const res = await fetch('/api/product');
      const data = await res.json();
      setProduct(data);
    };
    
    fetchProduct();
  }, []);
```