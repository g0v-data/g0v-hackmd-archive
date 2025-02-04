### public_develop

---

OCMS 2.0 是 OCMS 後臺網頁的 web 介面，主要其包含帳管、告警、排程、日誌、點位編輯等，並依照不同專案進行功能擴充。

**Figma 設計稿**：https://www.figma.com/design/T1FNfcuKW6wg35gUBFtCdu/DELTA_Shanghai_BMS

**Framework / Library**

- Framework: [Next.js](https://nextjs.org/)
- Style: [Tailwindcss](https://tailwindcss.com/)
- State Management: [Recoil](https://recoiljs.org/)
- Form Library: [React Hook Form](https://www.react-hook-form.com/)
- Unit test: [Jest](https://jestjs.io/), [React Testing Library](https://testing-library.com/docs/react-testing-library/intro/)
- API Mock: [Mock Service Worker](https://mswjs.io/)
- Code Style & Git Hooks: [eslint](https://eslint.org/), [prettier](https://prettier.io/), [husky](https://github.com/typicode/husky), [commitlint](https://commitlint.js.org/)

### 環境建置

---

```bash
git clone https://gitlab.nadisystem.com/backend/web/web-gui/project/public_develop.git
git submodule update --init --recursive 
npm i
npm run dev
```

### 資料夾結構

---

```bash
public_develop
├── build.sh
├── change_log.MD
├── commitlint.config.js
├── components
├── config
|  ├── colorCategory.json  # 告警類型 - 依照不同案子設定不同告警名稱以及顏色
|  ├── countries.json  # 國家清單
|  ├── display.json  # 各個頁面表格是否顯示資料
|  ├── layout.json  # 最外層 layout 設定是否顯示
|  ├── liveStatus.json
|  ├── menuList.json  # 右側菜單列階層是否顯示以及相對應的權限
|  ├── subsysurl.json  # 設定 subsysurl 點擊子連結後方 url 是否自動帶入 token 
|  └── _colorCategory1_9_backup.json  # 1.9 - P220202 的告警類型
├── Daily.MD  # 已經沒有更新了
├── docker-compose.yaml
├── Dockerfile
├── jest.config.js
├── library  # [submodule] 元件庫 - 全部案子共用此資料夾內元件 & 狀態
|  ├── components
|  ├── hooks
|  ├── README.md
|  ├── state
|  ├── styles
|  ├── types
|  └── utils
├── middleware.ts  # 自動在網址後帶入 en | zh 的 i18n 
├── mocks  # mock api
|  ├── browser.ts
|  ├── handlers.ts  # 引入不同 submodule 的 mock api
|  ├── index.ts
|  ├── server.ts
|  └── setupTests.ts
├── module
|  ├── account  # [submodule] 帳管
|  ├── alarm  # [submodule] 告警
|  ├── nodeObject  # [submodule] 點位編輯
|  ├── notification  # [submodule] 通知Log
|  ├── schedule  # [submodule] 排程
|  └── systemRelated  # [submodule] 系統設定
├── next-env.d.ts
├── next-i18next.config.js
├── next.config.js
├── package-lock.json
├── package.json
├── pages  # 引用 submodule page
|  ├── 404.tsx
|  ├── account
|  |  ├── group
|  |  |  └── index.tsx
|  |  ├── plugins
|  |  |  ├── add
|  |  |  |  └── index.tsx
|  |  |  ├── index.tsx
|  |  |  └── update
|  |  |     └── index.tsx
|  |  └── userList
|  |     ├── add
|  |     |  └── index.tsx
|  |     ├── index.tsx
|  |     └── update
|  |        └── index.tsx
|  ├── alarm
|  |  ├── alarmHistory
|  |  |  └── index.tsx
|  |  ├── categorySetting
|  |  |  └── index.tsx
|  |  ├── currentAlarms
|  |  |  └── index.tsx
|  |  └── ruleSetting
|  |     ├── add
|  |     |  └── index.tsx
|  |     ├── index.tsx
|  |     └── update
|  |        └── index.tsx
|  ├── api
|  |  └── hello.ts
|  ├── error.tsx
|  ├── index.tsx
|  ├── login
|  |  └── index.tsx
|  ├── nodeObject
|  |  ├── controlHrefGroup.tsx
|  |  ├── node
|  |  |  └── index.tsx
|  |  ├── nodeObjectTable.tsx
|  |  └── object
|  |     └── index.tsx
|  ├── reset.tsx
|  ├── schedule
|  |  ├── commandHistory
|  |  |  └── index.tsx
|  |  ├── commandTemplate
|  |  |  ├── add
|  |  |  |  └── index.tsx
|  |  |  ├── index.tsx
|  |  |  └── update
|  |  |     └── index.tsx
|  |  ├── currentTaskList
|  |  |  └── index.tsx
|  |  ├── schedule
|  |  |  ├── add
|  |  |  |  └── index.tsx
|  |  |  ├── index.tsx
|  |  |  └── update
|  |  |     └── index.tsx
|  |  ├── taskHistory
|  |  |  └── index.tsx
|  |  ├── taskTemplate
|  |  |  ├── add
|  |  |  |  └── index.tsx
|  |  |  ├── index.tsx
|  |  |  └── update
|  |  |     └── index.tsx
|  |  └── timeTemplate
|  |     ├── add
|  |     |  └── index.tsx
|  |     ├── index.tsx
|  |     └── update
|  |        └── index.tsx
|  ├── signup.tsx
|  ├── sso
|  |  ├── login
|  |  |  └── index.tsx
|  |  └── logout
|  |     └── index.tsx
|  ├── systemRelated
|  |  ├── accessLogs
|  |  |  └── index.tsx
|  |  ├── commonRule
|  |  |  └── index.tsx
|  |  ├── loginLogs
|  |  |  └── index.tsx
|  |  ├── notification
|  |  |  └── index.tsx
|  |  ├── notificationLogs
|  |  |  └── index.tsx
|  |  └── subsysUrlSetting
|  |     └── index.tsx
|  ├── _app.tsx
|  └── _document.tsx
├── pageTest  # 舊的檔案單元測試可以無視
|  ├── alarm
|  ├── login.test.tsx
|  ├── reset.test.tsx
|  ├── schedule
|  ├── signup.test.tsx
|  └── systemRelated
├── postcss.config.js
├── public
|  ├── error.png
|  ├── flags.png
|  ├── flags@2x.png
|  ├── icon.ico
|  ├── indexLogo.svg
|  ├── locales
|  ├── loginBg.png
|  ├── logo.svg
|  ├── logo_header.svg
|  └── mockServiceWorker.js
├── README.md
├── tailwind.config.js
├── tsconfig.json
├── type
|  └── i18next.d.ts  # i18n 的 type
├── utils
|  ├── i18n.ts  # 已經沒有再使用了
|  └── url.ts  # Fetch API Response 整理成想要的回傳 json 格式
├── .env.development  # API URL 路徑設定 - 開發
├── .env.production  # API URL 路徑設定 - 編譯
└── version.ts  # 顯示版本
```