# 會員權限
1. 新增 **navigationConfig.json**
2. 在utils中的helper.js新增 `export function checkPermission(userRole, tag, action, navigationConfig)`
3. Navigation.js 中 `import { checkPermission } from '../utils/helper';`
`import navigationConfig from '../config/navigationConfig.json';`
4.在App.js 中宣告`const [userRole, setUserRole] = useState(null); //會員權限`，在`useEffect(() => {` 裡面加上 `const role = localStorage.getItem('userRole') || 'corporate_user'; // 默認角色為 guest`
        `setUserRole(role);`，`<Navigation />`新增參數變成`<Navigation  userRole={userRole}/>`