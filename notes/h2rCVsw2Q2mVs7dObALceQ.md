# 會員權限 
###### 第2次開始時間(1/13號~)
1. 新增 **navigationConfig.json**
2. 在utils中的helper.js新增 `export function checkPermission(userRole, tag, action, navigationConfig)`
3. Navigation.js 中 `import { checkPermission } from '../utils/helper';`
`import navigationConfig from '../config/navigationConfig.json';`
4. 在App.js 中宣告`const [userRole, setUserRole] = useState(null); //會員權限`，在`useEffect(() => {` 裡面加上 `const role = localStorage.getItem('userRole') || 'corporate_user'; // 默認角色為 guest`
        `setUserRole(role);`，`<Navigation />`新增參數變成`<Navigation  userRole={userRole}/>`
5. "執行實績"不做。
6. 在Product.js宣告`const userRole='maintainer';`或`const userRole='PMO';`進行測試，傳入ProductList.js中`<ProductList userRole={userRole}></ProductList>`
7. ProductList新增userRole參數`const ProductList = ({ member_uuid,userRole }) => {`，使用 `const canView = checkPermission(userRole, 'company', 'view', navigationConfig);`
   ` const canEdit = checkPermission(userRole, 'company', 'edit', navigationConfig);`
    `console.log("product  "+userRole+",mem   "+member_uuid);`，在SwitchStatus加上canEdit參數並傳入`<SwitchStatus data={list} handleStatusChange={handleStatusChange} canEdit={canEdit} ></SwitchStatus>`
8. 在SwitchStatus.js利用canEdit參數 在Return修改
```
{canEdit && (
<input className="form-check-input" type="checkbox" role="switch" id={`switch${data.uuid}`} checked={data.status === 1} onChange={handleChange} onClick={handleClick} />
)}
```
9. 使用Context紀錄userRole，在context資料夾下的PermissionContext.js。
10. 將context 用在 app.js 的 return 利用children的性質應包裹整個應用，以確保所有組件（包括 Navigation 和路由中的 element）都能使用 usePermission()。
11. 移除6. 中的操作 ~~const userRole='maintainer'~~，<ProductList ~~userRole={userRole}~~></ProductList>；移除4. 中的部分操作，<Navigation  ~~userRole={userRole}~~/>
12. 新增與調整canView，canEdit和其相應的import(之前的刪除)
```
import { usePermission } from '../../context/PermissionContext';

const { hasPermission } = usePermission();
const canView = hasPermission('product', 'view');
const canEdit = hasPermission('product', 'edit');
```
13. 修改spring PerfessionalService的verifiedMaintainSuper與verifiedMaintainSuperToken<br>將GeneralCode.Professional改成ProfessionalCode.Maintainer並新增對應的名稱與專人ID
14. 後端從回傳成功響應，改成回傳專人身分。
15. 宣告 `const tokenReturn = await verifiedToken();` 然後使用tokenReturn.data.result.idName取出後端API回傳值
16. 開始修改原始專案(上面的react 在個人部分測試)
17. Company.js新增 key={member.id}處理 `Company.js:172  Warning: Each child in a list should have a unique "key" prop.`問題。
18. 新增PermissionContext.js
19. 將context 用在 app.js 的 return 
20. 修改 Navigation.js
21. 修改 Navigation.js中的visibleSubItems成
```
// 檢查該分類是否有至少一個可見的小分類
const visibleSubItems = item.subItems.filter(subItem =>{
 // checkPermission(userRole, item.tag, 'view', navigationConfig)
const { hasPermission } = usePermission();
return hasPermission(item.tag, 'view');
}
```

22. SwitchStatus.js 利用canEdit參數 在Return修改
23. Company.js新增"canView"與"canEdit"，
```
if (!canView) {
    return <div>您無權查看此頁面</div>;
}
```
SwitchStatus新增canEdit
`<SwitchStatus data={company} handleStatusChange={handleStatusChange} canEdit={canEdit}>`
24. 調整MemberList.js 同步驟23.
25. 商品頁面分為Product.js與ProductList.js，先在Product.js加上"canView"與相關ProductList.js加上canEdit相關
26. 需求單頁面分為Pr.js與PrList.js，同25
27. ~~將前面的canEdit相關移到SwitchStatus.js 這樣只要這邊有就好同時改回<SwitchStatus data={company} handleStatusChange={handleStatusChange} canEdit={canEdit}>~~ 還是需要知道哪裡來的，company product之類的，所以改回有canEdit={canEdit}
28. Company.js 的 SwitchStatus 改名為SwitchCompanyStatus，他與另外五個SwitchStatus的來源不同，修改完即完成主功能(所有頁面上會完全處理)



### 問題
    (已處理)廠商列表 Company.js:172  Warning: Each child in a list should have a unique "key" prop.
    


## VSCode 關閉但未輸入ctrl+C 關閉server
* 停止Server方法:
1. 開啟windows powershell
2. 輸入`tasklist | findstr node` 查找 node 相關進程
node.exe                     32672 Console                    1      9,136 K
node.exe                     34592 Console                    1     41,032 K  
在Console前的為PID 如32672與34592。
3. 或是輸入 `netstat -ano | findstr :3000` 輸出為
 TCP    0.0.0.0:3000           0.0.0.0:0              LISTENING       34592
  TCP    127.0.0.1:3000         127.0.0.1:55707        ESTABLISHED     34592
  TCP    127.0.0.1:3000         127.0.0.1:62844        ESTABLISHED     34592
  TCP    127.0.0.1:55707        127.0.0.1:3000         ESTABLISHED     43944
  TCP    127.0.0.1:62844        127.0.0.1:3000         ESTABLISHED     43944
  最後面的是PID。
4. 輸入`taskkill /PID <PID> /F` 刪除進程即可關閉server,如:`taskkill /PID 34592 /F`

