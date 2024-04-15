## Tourmap引入DynamicForm完成CMS功能規劃

共筆筆記網址 : https://g0v.hackmd.io/70u02RdPQSC0djx9gICwZw

DynamicForm github網址 : https://github.com/EasyAbp/DynamicForm

這模組重要的實體有四個，分別是Form、FormItem、FormTemplate、FormItemTemplate。

以該模組的設計**FormTemplate**是用來定義表單的樣式，**FormItemTemplate**是用來定義表單的欄位樣式，**Form**是用來存放表單的資料，**FormItem**是用來存放表單的欄位資料。

按照目前的需求，我們希望能用form表單來支應cms完成下圖的功能

![cmsModal](https://files.furthersoftware.com.tw/assets/Tourmap/產品Cms/cmsModal.png)

舉例來說用題目名稱**簡介**來當作表單的標題，**內容**來當作表單的欄位，每個欄位的內容都是一個**DynamicForm**的**FormItem**。

用這方法能在**FormItemTemplate**定義出符合我們cms需求的表單，並且能夠透過**DynamicForm**的**Form**來存放表單的資料。

目前除了用**DynamicForm**來完成cms的功能規劃外，還考慮有fallback的機制。

順序為 productSku -> project -> product -> productCategory

這樣的設計是為了讓cms的功能規劃能夠有一個fallback的機制，當productSku沒有資料時，會去找project，project沒有資料時，會去找product，product沒有資料時，會去找productCategory。

## 實體規劃

![dataModal](https://files.furthersoftware.com.tw/assets/Tourmap/產品Cms/formsDataModal.png)
