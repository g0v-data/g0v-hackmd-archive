# 耘想 JS 修改

### 導覽列 hover 下滑殘影
*khaki.js - 958* 
```javascript=
var $autohide_nav = $navbarTop.filter('.nk-navbar-autohide');
self.throttleScroll(function (type, scroll) {
    var start = 400;
    var hideClass = 'nk-onscroll-hide';
    var showClass = 'nk-onscroll-show';
    var isDropDown = $('.nk-navbar-autohide').find('.nk-drop-item.open').length;

    // hide / show
    if (type === 'down' && scroll > start && isDropDown === 0) {
        $autohide_nav.removeClass(showClass).addClass(hideClass);
    } else if (type === 'up' || type === 'end' || type === 'start') {
        $autohide_nav.removeClass(hideClass).addClass(showClass);
    }

    // add solid color
    if ($navbarTop.hasClass('nk-navbar-transparent')) {
        $navbarTop[(scroll > 70 ? 'add' : 'remove') + 'Class']('nk-navbar-solid');
    }
});
```

### 移除左欄 icon
```javascript=
$(".nk-widget-categories > li > a > span[class^=ion]").hide();
```

### 麵包屑首頁 icon 移除換 "首頁"
```javascript=
$('.breadcrumbs a[title=Home]').html('首頁');
```

### 首字變色
```javascript=
function FirstWordColorChange(){
    var HavePageTitle = $('.pageTitle').length > 0 ? true : false;
    if(HavePageTitle){
        let words = $('.pageTitle').text().split('');
        $('.pageTitle').empty();
        words.forEach(function(item) {
            $('.pageTitle').append('<span>' + item + '</span>');
        })
    }
}
```
```css=
.pageTitle span:nth-child(1){
    color:#000
}
```