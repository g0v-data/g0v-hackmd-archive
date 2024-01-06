<font color=red>primary key 紅色</font>
<font color=blue>foreign key 藍色</font>

`bank`
><font color=red>bank_id:銀行編號</font>
>bank_name:銀行名稱

`rate`
><font color=red>rate_id:利率id(insert後自動產生)</font>
><font color=blue>bank_id:銀行編號</font>
>rate_name:利率種類(定存.活存...)
>rate_time:期數(一個月.二個月.一年...)
>rate_status:固定利率或機動利率
>amount:用來判斷是不是大額存款
>(ex.30萬大額存款,這格就存30萬,只要確認使用者輸入的是不是超過這個值就好)
>rate_value:利率值(小數)

`card`
><font color=red>card_id:信用卡id(insert後自動產生)</font>
><font color=blue>bank_id:銀行編號</font>
>card_name:信用卡名稱

`bonus`
><font color=red>bonus_id:優惠id(insert後自動產生)</font>
><font color=blue>card_id:信用卡id</font>
>bonus_type:優惠大類別(ex.交通)
>detail:優惠小類別(ex.飛機)
>bonus_title:優惠標題(linebot顯示內容)
>bonus_content:優惠詳細內容(網頁顯示內容)