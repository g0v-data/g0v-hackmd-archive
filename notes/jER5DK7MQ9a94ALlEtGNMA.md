# 2019 / 07 / 01 CodeReview FrontSide

1. 刪除的時候最好再做一次詢問
2. 當臨場有問題，不應該直接說沒有滿足功能需求，而是應該有臨場說服客戶的能力
3. jQuery物件和Kendo物件語法要辨識清楚，不要混用
4. 變數名稱命名規則一致
5. 講解自身code的時候，如果中間call了某function，應該先跳去function講解，再回來剛剛跳走的點繼續講
6. 按下刪除出現#，在使用者的角度是刪除了該筆資料且呈現，但對瀏覽器來說是超連結的方式。利用event.preventdefault解決，即「非我寫的程式碼都不要跑」。
```javascript=
event.preventdefault();
//在function參數不需要加入event，瀏覽器本身支援
```
---
7. code review時，不需要的程式碼就刪掉無需註解。會希望要在code review時討論才註解，要測驗的時候再把註解刪除。
---
8. Book_ID應該是要找grid中的最大值，而非grid長度再加。且為了避免在每一次要create的時候都還在跑迴圈去找
---
9. JSON的字串，中間要包含,，而[]表示array，{}表示物件
```javascript=
$("#book_grid").data("kendoGrid").dataSource.filter({
    logic: "or",
    filters: [
        {
            field: "BookName",
            operator: "contains",
            value: target
        },
        {
            field: "BookAuthor",
            operator: "contains",
            value: target
        },
    ]
});
```
---
10. pageable
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_34b44ae8ed6f5d934f5adc0e82fdf03f)
```javascript=
pageable: {
    refresh: true,
    input: false,//手key頁數
    numeric: false
}
```

- refresh是grid右下角的刷新圖示的出現與否!
- input是決定grid是否能夠手動key頁數

---

11. 避免自己手key到不允許的日期（例如：7/32），故可用kendo的dateInput來檢查並避免。

```javascript=
$("#bought_datepicker").kendoDatePicker({
    value: new Date(),
    format: "yyyy-MM-dd",
    dateInput: true
});
    
```

---
12. 變數命名，註解要注意，能打就打。
---
13. document.ready是為了確保整份html的DOM Tree都跑完後才會執行。其方式類似於$(function)
```javascript=
$(function(){
}

$(document).ready()
//兩者相同
```
---
14. 註解要寫中文
---

15. 跟瀏覽器講我的程式碼呈現出來的東西是中文的，所以瀏覽器認為中文。但若使用en，瀏覽器會覺得是英文需要翻譯，所以差別在於會跳出翻譯這個網頁的按鈕。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_65fde68899ea181923ad30ebc3c04296)
---
15. 針對瀏覽器能夠持續不間段的監聽，所使用的function，可以只使用input，不用多加上propertychange來限定哪種輸入。
```javascript=
$(".book-grid-search").bind('input propertychange',function(){
    var target = $(".book-grid-search").val();
    $("#book_grid").data("kendoGrid").dataSource.filter({
        logic: "or",
        filters: [
            {
                field: "BookName",
                operator: "contains",
                value: target
            },
            {
                field: "BookAuthor",
                operator: "contains",
                value: target
            },
        ]
    });
});
```


