# JavaScript 練習


項目
- [HTML-CATHAY](#HTML-CATHAY)
  - [1-1] 範例 - 產出標頭
  - [1-2] 範例 - 輸入輸入框
  - [1-3] 範例 - 產出按鈕
  - [1-4] 範例 - 產出form (資料框)
  - [1-5] 範例 - 產出公司的黃綠底框
  - [1-6] 範例 - 使用TABLE排版
  
- [Js](#Js)
  - [2-1] 範例 - 打包前端值
  - [2-2] 範例 - doButton
  - [2-3] 範例 - 打包多個前端值
  - [2-4] 範例 - 打包成Map
  - 
- [TRX](#TRX)
  - [3-1] 範例-接值
  - [3-2] 範例-回傳-alert顯示
  - [3-3] 範例-回傳-console顯示
  - [3-4] 範例-接值+資料處理(String)
  - [3-5] 範例-接值+資料處理(Map)
  - [3-6] 範例-接值+呼叫模組(LIST < Map >)

- [TablueUI](#TablueUI)
  - [4-1] 範例 - TableUI columm
  - [4-2] 範例 - gridLoad
  - [4-3] 範例 - 格式調整


# HTML-CATHAY
這邊先不要想一步登天，先能產出基礎的物件
之後再整成公司的樣子
1.先產物件
2.組成Form
3.印用公司的class

## 1-1 範例 - 產出標頭
```javascript=
	<label >姓名</label>
```

## 1-2 範例 - 輸入輸入框

```javascript=
<input type="text" size ="20" id='EMP_NAME' name='EMP_NAME'> 

```

結果發現 跑版了...!!!
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ed90d03aa22d637a87c4a2276f3c40b8.png)

這邊就是常常說的前端畫面不好刻，有時候會歪掉醜醜的，通常會找類似的畫面參考人家怎麼做的
這時候很多方法，只要能達標即可
```javascript=
解法1 用label框起來
    <label >姓名
	<input type="text" size ="20" id='EMP_NAME' name='EMP_NAME'> 
    </label>
    
解法2
    <div>
		<label>姓名NAME</label>
		<input type="text" size ="20" id='EMP_NAME2' name='EMP_NAME2'> 
	</div>

```

## 1-3 範例 - 產出按鈕
```javascript=
	<button type='button' id='queryBtn'>查詢</button>
```

## 1-4 範例 - 產出form (資料框)
我們一個頁面很可能有很多區塊，當然可以把全部的資訊往後面送，但這樣很浪費效能，加上資料傳越多越容易混淆，通常我們會使用一個form把頁面框起來，常聽到的form submit就是把某個form的資料打包起來往後送。
```javascript=
<form name='form1' id='form1' style='PADDING-RIGHT: 0px; PADDING-LEFT: 0px; PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-TOP: 0px'>

你剛剛打的東西

</form>

```

```javascript=
<form name='form1' id='form1' > 後面的stype是一些字型或設定

```


比較
```javascript= 
<form name='form1' id='form1' >
	<label >姓名
	    <input type="text" size ="20" id='EMP_NAME' name='EMP_NAME'> 
    </label>
	<button type='button' id='queryBtn'>查詢</button>

    <div>
	    <label>姓名NAME</label>
	    <input type="text" size ="20" id='EMP_NAME2' name='EMP_NAME2'> 
    </div>
</form>

```
```javascript= 
<form name='form1' id='form1' >
	<label >姓名
	    <input type="text" size ="20" id='EMP_NAME' name='EMP_NAME'> 
    </label>
	<button type='button' id='queryBtn'>查詢</button>
</form>
<div>
	<label>姓名NAME</label>
	<input type="text" size ="20" id='EMP_NAME2' name='EMP_NAME2'> 
</div>

```

的差別

第二個因為form把第一個區塊姓名包起來了 等等按下查詢並不會把姓名NAME的資料往後送

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4983c91e66e444d375ab03fd76073b22.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7510d49639a11b6e36db73abaa485093.png)



## 1-5 範例 - 產出公司的黃綠底框
需使用class tbYellow 和 tbYellow2 變色
```javascript=
<form name='form1' id='form1' >
	<label class ="tbYellow" >姓名
	    <input type="text" size ="20" id='EMP_NAME' name='EMP_NAME'> 
    </label>
	<button type='button' id='queryBtn' class ="tbYello2">查詢</button>
</form>
```
可以看見好像有輕微的黃底出現在區塊後面，另外按鈕公司也長的不一樣，需使用button


```javascript=
<button type='button' id='queryBtn' class ="tbYellow2 button">查詢</button>

```


## 1-6 範例 - 使用TABLE排版
table　常用的class是tbbox2
```javascript= 
<table width="100%" border="0" cellpadding="0" cellspacing="1" class="tbBox2">


你的東西  
//要注意 form要在 table外面(form要包整個框)
</table>
```
這時候用了發現他怎麼還是擠在一起沒有效果，回去看JSP1的TABLE
TABLE這個TAG，要靠td和tr做分隔


```javascript= 
    <tr>
	<td>
        <label class ="tbYellow">姓名 
	</td>

	<td>
         <input type="text" size ="20" id='EMP_NAME' name='EMP_NAME'> 
        </label>
    </td>
	<td>
        <button type='button' id='queryBtn' class ="tbYellow2 button">查詢</button>
    </td>
    </tr>

	<tr>
        <td>
            <label class ="tbYellow">我是第二列 
        </td>
	</tr>
```


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4b33bb4628ff849edd6e46e2d6f6b122.png)
雖然還很醜，但有點樣子了

現在有td tr幫忙，不需要label了!

```javascript= 
    <tr>
	<td class ="tbYellow">姓名 
	</td>

	<td>
         <input type="text" size ="20" id='EMP_NAME' name='EMP_NAME'> 

    </td>
	
```
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8d5d2a6102626ed02e4a3cd8015d4e96.png)


發現漂亮多了!!!

原因是剛剛有說，table要靠td和tr，所以變顏色的class要用在td，才會對整個欄位起作用，
可以想像class放在td很像把excel的某個欄位都設定成紅色，而放在裡面的button只有button吃的到
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c3ec1542aa1a69f9d950c65486b7f3b3.png)

將原本的程式碼改成下面區塊

```javascript= 
	<td >
        <button type='button' id='queryBtn' class ="tbYellow2 button">查詢</button>
    </td>
    
    
    //改成這樣!

	<td class ="tbYellow2" align="center">
        <button type='button' id='queryBtn' class ="button">查詢</button>
    </td>
	
```
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_966e6b3487b298f0fb0b654cdcc8e636.png)



差一步了!

同理輸入欄位也需要修正

```javascript= 
	<td>
         <input type="text" size ="20" id='EMP_NAME' name='EMP_NAME'>    
    </td>
    //改成這樣!
	<td class ="tbYellow2">
         <input type="text" size ="20" id='EMP_NAME' name='EMP_NAME'> 
    </td>
```
    
成功了
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_27e19d67628142ab7f99cd80a00258cb.png)

以上至少會刻畫面了，之後都是類似的概念，組成SPEC要的樣子，到這邊為止都不用管後端跟JavaScript。
    
    

# Js
## 2-1 範例 - 打包前端值
首先要先定義點了query會觸發onclick事件

```javascript= 
$('queryBtn').observe('click', buttons.doQuery);
//這句請放在initApp後面，也有人會放在html 註冊一個onclick事件
```
            
請在buttons內新增方法doQuery
```javascript= 
	var buttons = {
	
	};	
```
```javascript= 
    var buttons = {
    	doQuery : function(){		
            var EMP_NAME = $F('EMP_NAME');
            alert(EMP_NAME);
        }
	};	
```

## 2-2 範例 - doSomeAction
請先用主程式開發工具產一個doQuery方法，一定要(不要只貼下面的CODE過去)
```java= 
	public ResponseContext doQuery(RequestContext req){
		//System.out.println(req.getParameter("EMP_NAME"));
		return resp;
	}
```

定義請求
```javascript= 
  有公司的程式 請參考FOR IVY的 button.query
  
```

可以試試看 改在主程式用貼的 把TRX改成query2
JSP把方法改成query2 看為什麼錯 ?

## 2-3 範例 - 打包多個前端值
有時候需要多個傳入參數怎麼辦，可以繼續放值，且在發請求的時候用逗號區隔
    
```javascript=
var EMP_NAME = $F('EMP_NAME');
var DIV_NO = $F('DIV_NO');
XXXXXXXXXXXXXXXXXX('query', {EMP_NAME: EMP_NAME,DIV_NO: DIV_NO,HEELO:'123'},
        
        
```

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9bc3868d9292ce10618877eee8cb4962.png)

## 2-4 範例 - 打包成Map
同上如果如果參數眾多，可以將其打包成一個Map

```javascript=
			var reqMap = {
				EMP_NAME : $F('EMP_NAME'),  
				DIV_NO : $F('DIV_NO')
			}
```
發送的時候轉成json字串送出
```javascript=
XXXXXXXXXXXXXXXXXX('query', {reqMap2 : Object.toJSON(reqMap)},
```
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b65549077f51c538cb45c8c950c7602d.png)


# TRX
## 3-1 範例-接值
```java= 
//接字串
String EMP_NAME = req.getParameter("EMP_NAME");
```
## 3-2 範例-回傳-alert顯示
要回傳的話，主程式需要給一個回傳值，這邊故意換個KEY的名稱EMP_NAME_RTN，表示這是可以自己任意取名子的
```java= 
resp.addOutputData("EMP_NAME_RTN", EMP_NAME);
```

```javascript= 
alert(resp.EMP_NAME_RTN);
```
## 3-3 範例-回傳-console顯示
```javascript= 
console.log(resp.EMP_NAME_RTN); //要開F12看LOG
```
## 3-4 範例-接值+資料處理(String)
```java= 
		String EMP_NAME = req.getParameter("EMP_NAME");
		EMP_NAME = EMP_NAME + " 87";
		resp.addOutputData("EMP_NAME_RTN", EMP_NAME  );
```
## 3-5 範例-接值+資料處理(Map)
```java= 
Map reqMap =  VOTool.jsonToMap(req.getParameter("reqMap"));
```
## 3-6 範例-呼叫模組(LIST < Map >)
```java= 
		List<Map> rtnList = 呼叫模組;
		resp.addOutputData("rtnList", rtnList  );
```

```javascript= 
alert(resp.rtnList);
```
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5969ba66905073d5a2a5db0a26bde9b9.png)

直接印是印不出來的，js的map要使用Array.prototype.map()幫忙印出
```javascript= 
//使愈filter的item 印出來 依序印出map和裡面的值
function(resp){ //ReturnCode
    resp.rtnList.filter(function(item, index, array){
        alert(item);
		alert(item.EMP_NAME);
		alert(item.DIV_NO);
		})
	},
```


# TablueUI

## 4-1 範例 - TableUI columm

Body部分引用class grid
```javascript= 
<table id="grid" class="grid"></table>
```
會發現重整葉面後什麼都沒有，是因為沒有宣告TableUI在script，請先這樣放在initApp內
```javascript= 
var grid = 
 	new TableUI({
    table: $("grid"),
     column:[
            {header: "貨號" , key:'INV_NO' },
            {header: "品名" , key:'INV_NAME' }
        ]
    });
```
這邊要注意你的table: 要對應自己html的table id

```javascript= 
var grid = 
 	new TableUI({
    table: $("grid2"), <---
     column:[
            {header: "貨號" , key:'INV_NO' },
            {header: "品名" , key:'INV_NAME' }
        ]
    });
```

如果iD對不起來會跳錯

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_380958d21c91033ada05ee02ea61d612.png)

但這樣寫繪有個問題，就是var grid，這個變數宣告只在initApp這個function內，前面的action或是button會認不得，所以通常會宣告在一開始，讓以下所有的方法都譨認識var grid
```javascript= 

一開始


var grid



後面改成拿掉var
grid = 
 	new TableUI({
    table: $("grid2"), <---
     column:[
            {header: "貨號" , key:'INV_NO' },
            {header: "品名" , key:'INV_NAME' }
        ]
    });
```



如果你想要自己刻其實也可以就是要運用前面的教學自己慢慢弄
```javascript=
		<table  width='100%' border='0' cellpadding='0' cellspacing='3'  style="background-color:#ABFFFF;"> 
			<TR><TH>序號<TH>員工編號<TH>員工姓名<TH>單位代號<TH>生日<TH>職位</TR>
		<tbody id="tablelsw">  
			<TR ALIGN=CENTER>
			<c:forEach items="${rtnList}" var="current" varStatus="status">
				<TR ALIGN=CENTER>
				<th><c:out value="${status.count}"/>
				<th><c:out value="${current.EMP_ID}" />
				<th><c:out value="${current.EMP_NAME}" />
				<th><c:out value="${current.DIV_NO}" />
				<th><c:out value="${current.BIRTHDAY}" />
				<th><c:out value="${current.POSITION}" />
				</tr>
			</c:forEach>
		</tbody> 
		</table> 
```
但本質很花時間，還要處理之後怎麼load資料到Table，這邊也是我們拿掉的原生HTML這段的原因，但只是強調會看到很多人用非傳統的tableUI的方法，其實都是可行的。


## 4-2 範例 - gridLoad

***可參考 wiki  IM_TableUI_API_004**
以上的範例有兩個KEY值 INV_NO貨號和品名INV_NAME，這邊需要讓後端有回傳這個值
且為List< Map >


```java=
		List<Map> rtnList = new ArrayList();
		Map data1 = new HashMap();
		data1.put("EMP_NAME", "IVY");
		data1.put("DIV_NO", "9100000");
		rtnList.add(data1);
		Map data2 = new HashMap();
		data2.put("EMP_NAME", "OO");
		data2.put("DIV_NO", "9100100");
		rtnList.add(data2);
		Map data3 = new HashMap();
		data3.put("EMP_NAME", "DORIS");
		data3.put("DIV_NO", "9100100");
		rtnList.add(data3);
		Map data4 = new HashMap();
		data4.put("INV_NO", "1234567");
		data4.put("INV_NAME", "香蕉");
		rtnList.add(data4);		
		Map data5 = new HashMap();
		data5.put("INV_NO", "3345678");
		data5.put("INV_NAME", "蘋果");
		rtnList.add(data5);
		resp.addOutputData("rtnList", rtnList  );  <---- 傳給前端什麼key前端要接什麼
        
```


```javascript=
	function(resp){ //ReturnCode
		grid.load(resp.rtnList || []); //將resp的rtnList拿出來 底層會去load
	},
	function(resp){ //如果錯的時候要處理什麼 目前先都為空沒關係
		//error
		}		
	);
    
```
## 4-3 範例 - 格式調整
通常會在後端處理好資料再來，但有時候為了方便並不會全部處理完，這邊舉例一個當範例，譬如時間欄位都是 YYYY-MM-DD hh:mm:ss 通常會去掉尾數的三位毫秒，但如果是從DB拿出來直接顯示會包含完整的timestemp，所以要把他不顯示
```javascript= 
	{header:'更新日期', key:'UPD_DT', sortRule:'datetime'},

```
