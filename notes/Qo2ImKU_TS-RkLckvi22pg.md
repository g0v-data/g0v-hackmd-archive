# 區塊元素 行內元素差異
CSS規範規定，每个元素都有display屬性，每個元素都有默認的display值，如div的display默認值為“block”，則為“區塊”元素；span默認display屬性值為“inline”，是“行内”元素。

區塊（block）元素特點
1.區塊(block)元素都會另起一行
2.高度，行高以及頂和底邊距都可控制；
3.默認情况下，其寬度自動填满其父元素寬度，即寬度100%
4.可以設置寬高 width hight
區塊元素常見包括
div、p、h1~h6、ul、ol、li、
dl、dt、dd、form、table、hr、
blockquote 、address、menu、pre.....等等

行內（inline）元素特點
1.和其他元素都在一行上，相臨的行内元素會排列在同一行，
  直到一行排不下，才會換行，其寬度隨元素的内容而變化。
2.設置寬高無效，只能由内容撑起来，即行内元素設置width，height屬性無效。
3.設置上下margin、padding無效，左右padding 、margin有效
4.水平方向的padding-left 、padding-right、margin-left、margin-right都
  會產生效果，但上下方向的padding-top、padding-bottom、margin-top   、margin-bottom不會產生邊距效果。
 行內元素常見包括
 span、em、i、b、strong、a、img、input、br、select、textarea、   q、bdo、sub、sup...等等
 
 空元素特點
1.没有内容的 HTML 元素被稱為空元素。空元素是在開始標籤中關閉的。
2.由於HTML元素的内容是開始標籤与结束標籤之间的内容。
  而某些HTML元素具有空内容。那些含有空内容的HTML元素，就是空元素。
3.單標籤，只有開始標籤，没有结束標籤
空元素常見包括
<br> <hr> <img> <input> <link> <meta>
 
<area> <base> <col> <command> <embed> <keygen> <param> <source> <track> <wbr>
...等等

行内元素與區塊元素的包含規則？
大多數 HTML 元素 可以包含其他 HTML 元素。

-區塊元素可以包含行内元素或者某些區塊元素
-行内元素只能包含行內元素，不能包含區塊元素

比較典型的特例
-a無所不能，但a不能包含它本身
-p標籤不能包含區塊元素
-h1~h6、p、dt標籤：只能包含行內元素，不能再包含區塊元素
-li很强大，它可以包含div，甚至可以包含它的父元素ul或者ol