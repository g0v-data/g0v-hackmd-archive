# JS鍵盤


//鍵盤監聽事件

document.addEventListener("keydown",keydown);

//參數1：表示事件，keydown:鍵盤向下按；參數2：表示要觸發的事件
function keydown(event){
//表示鍵盤監聽所觸發的事件，同時傳遞參數event
switch(event.keyCode){
    case 37:
        alert("左键");
        break;
    case 39:
        alert("右键");
        break;
}
}
