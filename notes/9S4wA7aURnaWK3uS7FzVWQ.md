# React &&判斷
&& 為falsy判斷 若值為0 或nan還是會讓數值顯現出來
例如
若total變數預設為0 將我+1會顯示出"現在total為{total}"
故按下+1會喧染結果為 "現在total為1"
但當我total為0時 則只會喧染0
code如下
<button onClick={() =>
{
setTotal(total+1)
}
</button>}>
