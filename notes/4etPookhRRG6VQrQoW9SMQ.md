# OCE survey 
## Salesforce

1. 點 **surveys > New** 打開 **survey builder** 以建立survey
    * 每頁只能建立一個問題
    * 建立survey的 **Page** 請按照問題的題號編號為 **Q__** 
(e.g. 第一題的page為Q1, 第二題為Q2...)

2. **Send > Get Link** 以產生共用連結

3. **Survey Name > Related > Survey Invitations Name** 以編輯Territory

4. 建立完成後，需要 **generate metadata cache** 一次
（Admin Console > Mobile > Create New Cache）

## CLM
1. 選擇attendee，make a call
2. 選取Details > PLOMAX-DETAIL
3. Submit

## Report
**以CLM傳回資料，Survey頁面不會更新數據，需要到Report查詢資料庫**
1. 點Reports > New Report
2. 建立“Survey Question Responses Report”
