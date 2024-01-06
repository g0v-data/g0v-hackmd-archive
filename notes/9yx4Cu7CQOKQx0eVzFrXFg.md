## 問題列表

|問題描述|處理情形|備註|
|-|-|-|
|* 權限群組管理>成員設定<br>UNIT1下拉選單出不來|是URL的問題，之後統一處理||
||||

## 待辦事項

|描述|處理情形|備註|
|-|-|-|
|資料表設計管理的備註欄比例調大一點|之後會用Kendo Grid做(欄寬可以手動拖拉調整)||
||||


---
# 重構作業

## WFAdmin

**測試還是丟到最底下好了**


### Filters

| 名稱 | 睿涵 |
| -------- | -------- |
| AuthorizationFilter   | 完成     |


### API Controller

| 名稱              | Kadice      | 睿涵             |
| ----------------- | ----------- | ---------------- |
| iColumnController | <別動>      | 完成      |
| iFileController   |             | 不用改(尚無功能) |
| iFormController   | 完成/測過了   |                  |
| iModuleController | 完成/測過了   |                  |
| iSampleController | 完成/測過了 |                  |
| iTableController  | <別動>      | 完成 |


### Controller

| 名稱               | Kadice      | 睿涵               |
| ------------------ | ----------- | ------------------ |
| AccessController   | 完成/測過了 |                    |
| AnnController      |             | 完成(功能尚有缺漏) |
| FormController     | 不用改      |                    |
| HomeController     |             | 不用改             |
| LoginController    |             | 完成               |
| MenuController     | 完成/測過了 |                    |
| ModuleController   | 完成/測過了 |                    |
| RoleController     | 完成/測過了 |                    |
| SiteController     | 完成/測過了 |                    |
| SwitchVCController | 不用改      |                    |
| TableController    | 不用改      |                    |
| UnitController     | 完成/測過了 |                    |
| UserController     | 完成/測過了 |                    |
|                    |             |                    |


### ViewComponent
| 名稱                  | Kadice    | 睿涵 |
| --------------------- | --------- | ---- |
| AccessViewComponent   | 完成/測過了 |      |
| AnnViewComponent      |           | 完成 |
| ColumnViewComponent   | <別動>    | 完成 |
| FormViewComponent     | 完成/測過了 |      |
| MenuListViewComponent | 完成/測過了 |      |
| MenuViewComponent     | 完成/測過了 |      |
| ModuleViewComponent   | 完成/測過了 |      |
| RoleViewComponent     | 完成/測過了 |      |
| SiteViewComponent     | 完成/測過了 |      |
| TableViewComponent    | <別動>    | 完成 |
| UnitViewComponent     | 完成/測過了 |      |
| UserViewComponent     | 完成/測過了 |      |


## WFClient

### Filters

| 名稱 | 睿涵 |
| -------- | -------- |
| AuthorizationFilter   | 完成     |


### API Controller

| 名稱              | 睿涵     |
| ----------------- | ------  |
| iAccessController    |      | 
| iAnnouncementController |  Jenny寫的Vue+Api Sample(先不用改)    |
| iUnitController   |      |
| iUserController   |      |


### Controller
| 名稱   | 睿涵 |
| -------- | -------- |
| LoginController   | 完成   |
| ApplyController |太複雜先不改|


### ViewComponent
| 名稱                   | 睿涵 |
| --------------------- | ---- |
| MenuListViewComponent | 完成   |
| PageListComponent     | 暫時不改(之後應該用不到) |


## BALogin
### Filters

| 名稱 | 睿涵 |
| -------- | -------- |
| AuthorizationFilter   | 完成     |


### Controller
| 名稱 | 睿涵 |
| -------- | -------- |
| LoginController   | 完成     |


### API Controller
| 名稱 | 睿涵 |
| -------- | -------- |
| SSOLoginController   | 完成     |
| TokenCheckController   | 完成     |


---

## 功能測試
最後測試時間 2021/05/21 05:18pm

| 測試內容                | 結果(要重測可以刪整欄)     |
| ----------------------- | -------------------------- |
| 模組管理-新增       | V                          |
| 模組管理-修改       | V                          |
| 模組管理-刪除       | V                          |
| 表單設計管理-新增       | V                          |
| 表單設計管理-修改       | V                          |
| 表單設計管理-刪除       | V                          |
| 選單管理-新增(父層)     | V                          |
| 選單管理-修改(父層)     | V                          |
| 選單管理-刪除(父層)     | V                          |
| 選單管理-新增(子層)     | V                          |
| 選單管理-修改(子層)     | V                          |
| 選單管理-刪除(子層)     | V                          |
| 權限群組設定-新增       | V                          |
| 權限群組設定-修改       | V                          |
| 權限群組設定-刪除       | V                          |
| 權限群組設定-選單設定   | V                          |
| 權限群組設定-成員設定   | 下拉選單未正常顯示以外正常 |
| 組織管理-新增機關(父層) | 下拉選單未正常顯示以外正常 |
| 組織管理-修改機關(父層) | 下拉選單未正常顯示以外正常 |
| 組織管理-新增機關(子層) | 下拉選單未正常顯示以外正常 |
| 組織管理-修改機關(父層) | 下拉選單未正常顯示以外正常 |
| 帳號管理-查詢           | V                          |
| 帳號管理-新增           | 下拉選單問題導致無法測試   |
| 帳號管理-修改           | 下拉選單問題導致無法測試   |
| 帳號管理-詳細           | V                          |
| 帳號管理-權限設定       | V                          |
| 帳號管理-刪除           | V                          |
| 帳號管理-LOG寫入        | V                          |
| 分組角色管理-新增       | V                          |
| 分組角色管理-修改       | V                          |
| 分組角色管理-人員設定   | V                          |
| 分組角色管理-刪除       | V                          |
| 特殊角色管理-新增       | V                          |
| 特殊角色管理-修改(名稱) | V                          |
| 特殊角色管理-修改(人員) | V                          |
| 特殊角色管理-刪除       | V                          |
| 公告-                   | 117上面沒得對照功能先沒測  |
| 平台管理-新增           | V                          |
| 平台管理-詳細           | V                          |
| 平台管理-權限設定       | V                          |
| 平台管理-修改           | V                          |




