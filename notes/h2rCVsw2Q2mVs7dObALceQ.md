# 會員權限
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
9.使用Context紀錄userRole，在context資料夾下的PermissionContext.js。