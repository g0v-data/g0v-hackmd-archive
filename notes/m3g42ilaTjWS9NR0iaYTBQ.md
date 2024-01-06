這個檔案記錄如何將現有元件轉換為 ES6 module 方式載入

# 預期目標 
- 模組化 js 
- Iframe app 也可以開啟
- 提供 webcomponet 元件 


## 模組化 js
以下將介紹如何在 QTS Desktop 環境中引入模式化JS 架構。
包含：
- 模組化方式
- 載入方式
- 模組化 App 主畫面元件

### 模組化方式
- 基礎知識 
    - [JavaScript modules
](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules)
    - 原子設計 [#Link 1](https://bradfrost.com/blog/post/atomic-web-design/)[#Link 2](https://medium.com/uxeastmeetswest/%E7%B6%B2%E9%A0%81%E8%A8%AD%E8%A8%88-atomic-design%E7%B0%A1%E4%BB%8B%E5%8F%8A%E5%B7%A5%E4%BD%9C%E5%AF%A6%E4%BE%8B-42e666358d52)
- 打碎畫面元件及 API，達成解耦，才能有效重用。
  **減低元件之間的相依**
- 保持 function 單純，不要把取資料跟把資料給呈現在畫面上混在一個功能中，盡量分割。



首先，一個元件一個檔案，可以採用原子設計，依不同的角色來切分元件。
有切分元件，才能理解功能要怎麼分配給不同階段的元件。

**例如**：新舊密碼的比對，不是密碼欄位的功能，而是密碼設定畫面的功能。
  因此不會把比對的功能放在密碼欄位中，而是放在密碼設定畫面。

好的元件分割，不會再有
 - **複制貼上程式碼** 
 - **一個 function 多用**
 - **直接操作特定元件**

> 參考案例：[QTSDL000-1825](https://qnap-jira.qnap.com.tw/browse/QTSDL000-1845)

```bash
login_security/
└── components/
    │   # 基礎元件，給予樣式或基本行為
    ├── atoms/
    │   ├── textFields.js
    │   ├── passwordFields.js
    │   ├── button.js
    │   ├── ...
    │   └── comboBox.js
    │
    │   # 有特定功能的基礎元件
    ├── molecules/
    │   ├── accountList.js
    │   ├── ...
    │   └── accountWithBtn.js
    │
    │   # 組合元件，給予元件的互動規則
    ├── organisms/
    │   ├── changePasswordFieldSet.js
    │   └── createNewAccountFieldSet.js
    │
    │   # 組合更多元件及規則，產出 spec 需要的畫面
    ├── templates/
    │   ├── changePasswordView.js
    │   └── CreateNewAdminView.js
    │
    │   # 依不同環境或設定顯示特定畫面
    └── pages/
        └── adminChangePwd.js
```
**atoms**: 就算 Extjs 已經有基本元件了，我還是會在 App 的 atoms 中重新包裝一次，因為可以定義元件在 App 中的標準樣式及行為。
```javascript=
// atoms/passwordField.js
const PASSWORD_EL = {
  tag: 'input',
  type: 'checkbox',
  autocomplete: 'new-password',
  'data-flag': 'true',
};
export class PasswordField extends QNAP.QOS.component.form.TextFieldV3 {
  constructor(options) {
    super({
      maxLength: 64, // QTS 4.2 upgrade to 64
      labelWidth: 150,
      width: 200,
      inputType: 'password',
      defaultAutoCreate: { ...PASSWORD_EL },
      qInternational: true,
      enableKeyEvents: true,
      labelSeparator: '',
      ...options,
    });
  }

  qInternationalFn() {}

  afterRender() {
    super.afterRender();
    this.qInternationalFn();
  }
}

```
**molecules**: 有特定功能的基本元件，可以在不同畫面重用，範例為新密碼欄位，密欄欄位再加上密碼驗證規則
```javascript=
// molecules/newPassworldField.js
import { PasswordField } from '../atoms/PasswordField.js';

export class NewPasswordField extends PasswordField {
  initEvents() {
    super.initEvents();

    this.on({
      buffer: 500,
      keyup(cmp) {
        if (QNAP.QOS.quickWizard.countStrLen(cmp.getValue()) > cmp.maxLength) {
          cmp.setValue(QNAP.QOS.quickWizard.getCusLenStr(cmp.getValue(), cmp.maxLength));
        }

        cmp.validator(cmp.getValue());
      },
      specialkey(cmp) {
        cmp.validator(cmp.getValue());
      },
    });
  }

  qInternationalFn() {
    this.fieldLabel = _S.IEI_PASSWORD_NEW + _S.QUICK09_STR01;
    if (this.rendered) {
      this.label.update(this.fieldLabel);
    }

    this.validator(this.getValue());
  }
}
```
**organisms**: 一組特定功能的元件集
 - 大量元件都來自 import 
 - 在這層才決定元件之間的互動，像是 `NewPasswordField`, `OldPasswordField` 之間的比對，及密碼強度的提示，都這層的 `genPasswordValidator()` 執行。

在 `changePasswordFieldSet` 跟 `createNewAccountFieldSet` 都會引用 `NewPasswordField` 但是驗證規則是在個自的 FieldSet 中決定。
```javascript=
// Path: organisms/changePasswordFieldSet/js
import { DisplayField } from '../atoms/DisplayField.js';
import { AccountList } from '../molecules/AccountList.js';
import { NewPasswordField } from '../molecules/NewPasswordField.js';
import { OldPasswordField } from '../molecules/OldPasswordField.js';
import { ConfirmPasswordField } from '../molecules/ConfirmPasswordField.js';
import { DenyPasswordMsg } from '../molecules/DenyPasswordMsg.js';
import { PasswordStrengthIndicator } from '../molecules/PasswordStrengthIndicator.js';
import ...

// 由上層決定密碼驗證規則
function genPasswordValidator({ oldPwdField, denyPwdMsg, passwordStrengthIndicator, triggerLayout }) {
  return function (newPassword) {
      // verify password rule
  }}
  
export class ChangePasswordFieldSet extends Ext.form.FieldSet {
  initComponent() {
    const denyPwdMsg = new DenyPasswordMsg();
    const passwordStrengthIndicator = new PasswordStrengthIndicator();
    const oldPwdField = new OldPasswordField({ ref: 'oldPwdField' });
    const newPwdField = new NewPasswordField({
          validator: genPasswordValidator({ oldPwdField, denyPwdMsg, passwordStrengthIndicator, triggerLayout: this.triggerLayout }),

    });
    this.items = [oldPwdField, newPwdField, denyPwdMsg, passwordStrengthIndicator, ...];
    super.initComponent();
  }
  ...
}
.....
```


### App load module
桌面載入 App js 是直接用 `<script>` tag 來載入 App 在 system-items.json 或是 config.json(QPKG) 指定的 js 檔案。
屬傳統型的js 載入方式所以無法直接使 `import xxx from "path/to/module.js"` 方式來載入 module 類型的js.

所以暫時必須透過一些小手段來繞過這個限制。
桌面之後會應該在 config 中可以聲明要用 module 型態載入。

#### 解法：
透過在 app 初始化階段呼叫 `await import ("path/to/module.js")` 方式載入 module。   
如果 module 是會影響主視窗(app main window) 中呈現的內容，可以透過主視窗在 `beforeshow` 事件回傳 `false`，來等待 module 載入完成。  

範例碼的流程：
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_bdb3d241e2119d6f00e6b65e2540a8a2.png)

```javascript
// 範例：module.js
// 直接採用 ES6 class 模式
export default class extends Ext.form.FormPanel {
 constructor(config) {
    this.title = _S.IEI_NAS_SHARE2;
    this.qInternational = true;
    this.items = [/*...*/];
 }
}
```
```javascript
// 範例：App 主要 js
// 在 getMainWinParams 中觸發 module 截入
// 在載入完成前在 main window 的 beforeshow 回傳 false
// 載入完成後再次觸發 main window show
QNAP.QOS.LoginSecurity = Ext.extend(QNAP.QOS.BaseApp, {
  // ...
  moduleIsReady: false,
  async loadModule() {
    const app = this;
    const win = app._getMainWindow();
    const module = await import('path/to/module.js');

    app.moduleIsReady = true;
    // 按實際需求執行
    win.add(new module.default);

    // 重新觸發窗顯示
    if (win.isVisible() === false) {
      win.show();
    }
  },
  getMainWinParams (cfg) {
    const app = this;
    app.loadModule();

    return {
      // ...
      listeners: {
        beforeshow: () {
          // module 未載入完成就不顯示視窗
          return app.moduleIsReady;
        }
      }
  },
  // ...
});
```

### 共用 module
先做好模式化設計才能在不同 App 之間重用。
以下範例程式碼以 `_createModalWindow()` 為例。
在呼叫 export 的功能時，必須用 apply/bind/call 來改變 function scope，讓`openSharedFolderViewerPanel` 在執行`_createModalWindow()` 可以開在正確的 app 上。

```javascript=
// module app
export function openSharedFolderViewerPanel(config) {
  const app = this;
  const windowConfig = new SharedFolderViewerConfig({ ...config });
  const panel = app._createModalWindow(windowConfig);

  panel.show();
  
  return panel;
}
```
```javascript=
// app A
async openViewSharedFolderHandler() {
    const { openSharedFolderViewerPanel } = await import(`../sharedFolderViewer/index.js`);
    const { sharedFolderList } = this;
    const app = this._getApp();
    const panel = openSharedFolderViewerPanel.apply(app, [{ sharedFolderName }]);
  }
  
// app B
async openViewSharedFolderHandler() {
    const { openSharedFolderViewerPanel } = await import(`../sharedFolderViewer/index.js`);
    const { sharedFolderList } = this;
    const app = this._getApp();
    const panel = openSharedFolderViewerPanel.apply(app, [{ sharedFolderName }]);
  }
```
## QNAP.QOS.modalWindow 新功能

為了 iframe app 在開啟 modalWindow 時，方便取得 modalWindow 的套用或設定結果，因此新增 `retrieveResult()`。
建議實作方式：
1. 在初始化階段，先建立一個 Promise 物件，將 Promise 的 resolve 保留下來。
2. 實作 `retrieveResult()` 回傳在步驟1建立的 promise。 
3. 在視窗關閉時，執行步驟1保留的 resolve 結束 promise。

```javascript=
// example
this.retrieveResultPromise = new window.Promise((resolve) => {
  this.resolveFn = resolve;
});

this.retrieveResult = () => this.retrieveResultPromise;
this.on('close', ()=> this.resolveFn('hello world'));
```

## iframe (QMessage) 新增 createModalWindow()/getWindowRetrieveResult()
為了 iframe app 也可以重用 Extjs 的模組化元件且取得設定值，所以在 QTSDL000-1857 開始新增 `createModalWindow()` / `getWindowRetrieveResult()` 功能，並且增加 async/await 的模式。讓閱讀程式碼更直覺。

### js module 規範

### 呼叫方式
#### createModalWindow:
createModalWindow(option)
*option:object*
*option.module: string - js module path*
*option.config: any - 桌面會傳入 module default function*

*return: string - windowId*

#### getWindowRetrieveResult:
getWindowRetrieveResult(option)
*option: string - 在 getWindowRetrieveResult() 回傳的 windowId*

*return: any*

```javascript
// exmaple
const qc = new QMessageClient();
const windowId = await qc.fn.createModalWindow({
  module: `/path/to/modalWindowConfig.js?v=${version}`,
  config: { sharedFolderName: 'Public' },
});
const result = await qc.fn.getWindowRetrieveResult(windowId);
console.log('result', result);
```

Q&A： 
1. Moudle 的載入方式差異 
- 標準載入：開發階段會有 cache 問題
- 動態載入(推薦)：可依需求觸發載入，開發階段也比較方便

 
2. WebComponet 化遇到的問題 
CSS 可以透過 shadow dom 封裝，但 js 不行!
就算在 WebComponet shadow dom 區塊載入 Extjs，Extjs 仍會成為全域變數。 
先不管全域變數問題，要 WebComponet 化，仍需要花時間更多處理。
像是額外的 window 或是 menu 類型元件等基礎元件，都需先完成 WebComponet 化。
才能在其他非 Extjs framewrok 中順利使用。

