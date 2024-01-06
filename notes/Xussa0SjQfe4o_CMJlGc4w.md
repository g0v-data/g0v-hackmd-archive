# JavaScript 導頁和傳遞資料

- [導頁](#導頁)
  - [1-1] 範例-AJAX導頁!?
  - [1-2] 範例-form submit導頁
  - [1-3] 範例-LP_JSON導頁
  - [1-4] 範例-另開視窗

- [TABLE UI超連結](#TABLEUI_LINK)
  - [2-1] 範例-產生超連結(href)
  - [2-2] 範例-在超連結放置LP_JSON
  - 

- [TABLE UI選資料](#TABLEUI_GETDATA)
  - [3-1] 範例-確認資料(checkBox)
  - [3-2] 範例-選取資料(radio)

# 導頁


導頁其實是發一個GET請求(先不考慮另開視窗)

是打GET請求
/XXWeb/servlet/HttpDispatcher/XXZX_0101/prompt
所以我們可以送一個大家最熟悉的Ajax請求!?
## 1-1 範例-AJAX導頁!?
```javascript=
doInsertBtnAjax : function(){						
    var reqMap = {
		EMP_ID : $F('EMP_ID'),  
		DIV_NO : $F('DIV_NO')
	}
	new CSRUtil.AjaxHandler.request('${dispatcher}/XXZX_0101/').post('prompt', {reqMap2:Object.toJSON(reqMap)},
				function(resp){ 
				},
				function(resp){
				}		
			);	
		 },
```
......畫面閃一下 什麼都不幹
原因是Ajax是原地重新整理，目前的機制無法，網路有一些教學先不考慮

## 1-2 範例-form submit導頁
```javascript=
		 doInsertBtnFORM : function(){						
			var form=document.getElementById('form1');
			form.action= "${dispatcher}/XXZX_0101/prompt";
			form.submit();
		 }
```

```java=
Map reqMap = VOTool.jsonToMap(req.getParameter("reqMap")); // 會噴錯
```

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8a0b0dd99ae3cdf44754acc8053d1002.png)
錯了!!!
因為後端也要處理，接值那邊有說如form submit要用KEY值來接


```java=

String DIV_NO = req.getParameter("EMP_ID");
String DIV_NO = req.getParameter("DIV_NO");

2023-09-02 12:37:24,613 [FATAL] [XXZX_0101.doPrompt()(82)] - CCCC

```

發現可以拿到，統理可以在回傳給上一頁

```java=

resp.addOutputData("EMP_ID", EMP_ID);
resp.addOutputData("DIV_NO", DIV_NO);

如此0100前端的initApp可以再接值顯示原資料

```

"0101"的JSP一樣的方法回傳!!!
```javascript=
 doBackForm : function(){			
    var form=document.getElementById('form1');
	form.action= "${dispatcher}/XXZX_0100/prompt";
	form.submit();
}
```        
其實到這邊就知道導頁要怎麼做了，原理就是用form submit搭配前作業一(HW1)提到的街傳值
不過這邊還是有個麻煩，如果我想跨多個頁面，且想彈性一點都保留個個頁面資訊怎麼辦，底層有方法可以幫你保留就不用自己寫。




## 1-3 範例-LP_JSON導頁

使用的套件是CSRUtil的linkTo，回上一頁會搭配linkBack
```javascript=
		doInsertBtn : function(){					
			var LP_JSON = {
     			action : '${dispatcher}/XXZX_0101/prompt' //必要選項
     		};
     		CSRUtil.linkTo(LP_JSON, 'form1'); //將Form的資料打包
		 },
```
所以同樣後端去接值.........
```java=

String EMP_ID = req.getParameter("EMP_ID");
String DIV_NO = req.getParameter("DIV_NO");

2023-09-02 12:45:34,292 [FATAL] [XXZX_0101.doPrompt()(82)] - null
```
結果是空的發現底層的教學文件寫說要放一行
VOTool.setParamsFromLP_JSON(req); 

```java=
VOTool.setParamsFromLP_JSON(req); //務必在取值前執行
String EMP_ID = req.getParameter("EMP_ID");
String DIV_NO = req.getParameter("DIV_NO");

2023-09-02 12:45:34,293 [FATAL] [XXZX_0101.doPrompt()(87)] - LP_JSON之後:null
```
被騙了!? 答案是不是，底層會希望你把要給的變數自己在前端包起來，雖然她會幫你幫整個form但那是他記錄用的這樣才可以再四處傳遞的時候顯示

先講怎麼紀錄，需要自己給KEY值 :　後面帶自己
```javascript=
doInsertBtn : function(){					
    var LP_JSON = {
        action : '${dispatcher}/XXZX_0101/prompt', //必要選項
        EMP_ID: $F('EMP_ID')   // <-要注意最後一個不要有逗號
    };
    CSRUtil.linkTo(LP_JSON, 'form1'); //將Form的資料打包
},
```
這樣就可以了!
```java=
VOTool.setParamsFromLP_JSON(req); //務必在取值前執行
String DIV_NO = req.getParameter("EMP_ID");
```
這邊跟HW1的提醒一樣，如果發現都沒接/傳到
```java=
1.檢查0100的傳值JSP方法，可用alert,console 看看到底傳了什麼或是有噴錯
2.檢查0101的接值方法(trx),直接印出來看參數是什麼
3.檢查0101的送值方法(trx),注意addOutputData
4.檢查0100的接值JSP方法，可用alert,console 通常看initApp
```
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_630fcf174929e629624032cdc903d55a.png)

可學著使用DEBUG MODE追變數 

同樣跟前面fromsubmit一樣 0101的JSP把你要傳的東西回給他
```javascript=
doBack : function(){			
	CSRUtil.linkBack();
},
```


題外練習!!!

就只有這樣底層會幫你把第一個網頁的LP_JSON做打包回傳的動作。
以上就完成了導頁跟回上一頁，但是...

如果我在0101的主程式新增
		resp.addOutputData("EMP_ID", "HELLO");
會發現0101的主程式畫面會顯示HELLO，
或者你在畫面把HELLO改成HI，
但回上一頁還是你輸入的ID，不會是HELLO或是HI
原因是底層再透過BQ_ARG的LP_JSON在送的

如果想要更新能怎麼辦呢

想法1 我去動底層的LP_SON
```java=
Map reqMapBQ_ARG = VOTool.jsonToMap(req.getParameter("BQ_ARG")); 
主程式可以透過這樣拿出來
之後對MAP操作後丟回去...
reqMapBQ_ARG.put("EMP_ID", "HELLO");
resp.addOutputData("BQ_ARG", VOTool.toJSON(reqMapBQ_ARG)); //要再轉回JSON丟回去
```
但是以上暫時不知道為什麼會丟錯...
不過這個方法不是解方，一般不會這樣寫死在後端處理
因為USER是有可能修改網頁而非主程式
所以應該是要把在USER按出回上一頁的時候 取得當下頁面的狀態

想法2 包前端的參數往前傳 
需要再被傳的地方放一個欄位紀錄原本的值
請在WIKI找 回上頁重新查詢功能作法及相關說明

請在0101的HTML欄位放置一個隱藏的物件 這樣USER看不到
可放在最後面，因為前端傳的是EMP_ID要用 EMP_ID接但存在ORI_EMP_ID裡面
```javascript=
</table>
<input type="hidden" id="ORI_EMP_ID" name="ORI_EMP_ID" value="${EMP_ID}" />
```
JSP的部分參考 RYG00201的概念
如果不一樣的重抓值後重新送出，一樣直接用linkBack
```javascript=
doBack : function(){	
    if(!$F('ORI_EMP_ID') === $F('EMP_ID')){
        alert('畫面有改 重抓物件重新送');
        var LP_JSON = {
            action: '${dispatcher}/XXZX_0100/prompt',
            EMP_ID  : $F('EMP_ID'),
            DIV_NO  : $F('DIV_NO')
		};	
        CSRUtil.linkTo(LP_JSON , 'form1');
    }else{
        CSRUtil.linkBack();
    }	
},
```

# TABLE UI超連結

## 2-1 範例-產生超連結(href)
首先先長出超連結的樣子
https://www.w3schools.com/tags/tryit.asp?filename=tryhtml_a_href
```javascript=
<a href="https://www.w3schools.com">Visit W3Schools</a>
```
這樣會是一個超聯結的HTML寫法，同理我們也類似
```javascript=
<a href=".......XXXXX../XXZX_0100/prompt">員工編號</a>
```
使用底層的方法 new Element 先NEW出一個空的超連結
```javascript=
{
header: "員工編號",
key: "EMP_ID",
render: function (recored, value) {
	alert(value);
	var link = new Element( 'a' , { href : "#" } );
	return link;
	}
},
```
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7ab37702bdfe2e9cf75c6078cfc47c21.png)
雖然發現是空的，但其實F12已經看的到一個物件
複習這邊的render跟序號一樣是底層的方法之一，第一個參數是Map ，第二個是String,
第二個是當下的值就把它拿來用
```javascript=
{
header: "員工編號",
key: "EMP_ID",
render: function (recored, value) {
	alert(value);
	var link = new Element( 'a' , { href : "#" } );
    link.update(value);
	return link;
	}
},
```
這時候就產出了一個有URL連結的物件在TABLE UI上
不過點了沒反應正常 下面會教怎麼在裡面塞一個LP_JSON的導頁

## 2-2 範例-在超連結放置LP_JSON
我們在使用按鈕的時候會能夠有反應是因為有綁定一個OnClick事件，同理我們也希望超連結的物件能觸發一個click事件。
公定的寫法是用 observe + function click
這邊還沒找到教學文件 先當公式使用
```javascript=
{
header: "員工編號",
key: "EMP_ID",
render: function (recored, value) {
	alert(value);
	var link = new Element( 'a' , { href : "#" } ); //產生空HREF
    link.update(value); //將文字塞給他
    link.observe('click', function () {
        alert(1234);
    });
	return link;
	}
},
```
會發現點了超連結已經有出現ALERT 表示onClick事件觸發成功
無腦將新增的LP_JSON直接取代

```javascript=
{
header: "員工編號",
key: "EMP_ID",
render: function (recored, value) {
	alert(value);
	var link = new Element( 'a' , { href : "#" } ); //產生空HREF
    link.update(value); //將文字塞給他
    link.observe('click', function () {
        var LP_JSON = {
            action: '${dispatcher}/XXZX_0101/prompt'
        }
        CSRUtil.linkTo(LP_JSON, 'form1');
    });
	return link;
	}
},
```
這時候會發現已經有做到導頁過去
只是因為沒帶值 0101什麼都不做
```javascript=
{
header: "員工編號",
key: "EMP_ID",
render: function (recored, value) {
	alert(value);
	var link = new Element( 'a' , { href : "#" } ); //產生空HREF
    link.update(value); //將文字塞給他
    link.observe('click', function () {
        var LP_JSON = {
            action: '${dispatcher}/XXZX_0101/prompt',
		    ACTION_TYPE : 'U'
        }
        CSRUtil.linkTo(LP_JSON, 'form1');
    });
	return link;
	}
},
```
塞個U給他就可以看見按鈕被控制了! (0101的主程式+JSP需做處理)



至於怎麼塞當筆資料就是把vaule傳給他，可以參考WIKI上的WORD
這邊讓大家思考(請先做到U可以接傳跟按鈕控制成功再來想EMP_ID怎麼傳過去)


# TABLE UI選資料
主要參考TableUI_API_003

## 3-1 範例-確認資料(checkBox)
checkBox比較簡單，其實也是最常用的，需要整個打勾多筆資料往後送
只要加一行即可autoCheckBox
```javascript=
grid = new TableUI({
    table: $("grid"),
    autoCheckBox:{isSelectAll:true },
        column:[
            {header: "部門名稱", key:'DEP_NM' },
            {header: "部門代號", key:'DEP_CODE' }
        ]
});
```
這邊練習一下看WIKI的文件，雖然不是很清楚，但可以看網頁的第b項目，可以修正預設文字
```javascript=
grid = new TableUI({
    table: $("grid"),
    autoCheckBox:{
            isSelectAll:true,
            text:'我是選項'
            },
        column:[
            {header: "部門名稱", key:'DEP_NM' },
            {header: "部門代號", key:'DEP_CODE' }
        ]
});
```
如上方可以修正文字

## 3-2 範例-選取資料(radio)
會用上方的文件後，其實radio也是類似，我們直接貼範例的CODE到自己的CODE
```javascript=
grid = new TableUI({
    table: $("grid"),
	autoCheckBox:{
        type:'radio' ,//文件有寫 預設是checkBox 我們這次要radio
        valueKey:'DEP_CODE' //文件有寫 radio的綁定key值
	},
        column:[
            {header: "部門名稱", key:'DEP_NM' },
            {header: "部門代號", key:'DEP_CODE' }
        ]
});
```
這邊可以看到radio長出來了，強調不要不會走就想要飛，都是先產出物件後，在寫function要做什麼。
```javascript=
grid = new TableUI({
    table: $("grid"),
	autoCheckBox:{
        type:'radio' ,//文件有寫 預設是checkBox 我們這次要radio
        valueKey:'DEP_CODE', //文件有寫 radio的綁定key值
        action:function( node , boxStatus , records ){ 
             alert(node);
             alert(node.value );
    }
	},
        column:[
            {header: "部門名稱", key:'DEP_NM' },
            {header: "部門代號", key:'DEP_CODE' }
        ]
});
```
至少點了選項有回你了 action其實也是API文件有寫的
再來要拿出records的資料
老實說一開始也不確定怎麼拿 文件是
```javascript=
Object.toJSON(records))
```
沒關係一樣的方法，F12清空打開後看看有什麼
```javascript=

console.log(records);
DEP_CODE = records[0]['DEP_CODE'];
DEP_NM = records[0]['DEP_NM'];
alert(DEP_CODE);
alert(DEP_NM);
```
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_41d4cb25de97872b57575c87c012b3db.png)

似乎是個map就用.拿出來了

