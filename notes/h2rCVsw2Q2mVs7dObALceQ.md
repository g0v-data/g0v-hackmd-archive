# 會員權限
1. 新增 **navigationConfig.json**
2. 在utils中的helper.js新增 `export function checkPermission(userRole, tag, action, navigationConfig)`
3. Navigation.js 中 