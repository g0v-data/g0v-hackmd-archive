# JavaScript 接值


- [prompt接值](#prompt接值)
  - [1-1] 範例 - 後端接值
  - [1-2] 範例 - 後端送值
  - [1-3] 範例 - 前端送值
  - [1-4] 範例 - 前端接值

- [Form Submit](#Form Submit接值)
  - [2-1] 範例 - 後端接值
  - [2-2] 範例 - 後端送值
  - [2-3] 範例 - 前端送值
  - [2-4] 範例 - 前端接值
  
- [Ajax接值](#Ajax接值)
  - [3-1] 範例 - 後端接值
  - [3-2] 範例 - 後端送值
  - [3-3] 範例 - 前端送值
  - [3-4] 範例 - 前端接值

接值的觀念
```python
1. 前端第一次會送請求給後端
2. 後端會接值
3. 後端必須要傳值
4. 前端顯示
```

跟DataSet一樣，有這些步驟，前後端都是用"KEY"值在傳遞，
前端的KEY值
```python
1. Form Submit 是hmtl 內的form的KEY值
<input type="text" size ="20" id='DIV_NO' name='DIV_NO' > 
<input type="text" size ="20" id='EMP_NAME' name='EMP_NAME' > 

2. Ajax的KEY值 
reqMap : Object.toJSON(reqMap)
以上KEY值是reqMap
reqMap2 : Object.toJSON(reqMap)
以上KEY值是reqMap2
```

後端都是用"KEY"值在接String Map VO
```java
1. String id = req.getParameter("EMP_NAME_HELLO");
2. Map reqMap =VOTool.jsonToMap(req.getParameter("reqMap"))
3. DTXXTP01 vo = VOTool.mapToVO(DTXXTP01.class, reqMap);
```

後端都是用"KEY"值放在resp再送回前端
```java
1. resp.addOutputData("DIV_NO2", user.getDivNo()); 
//從userobject拿出DivNo，回傳一個KEY是DIV_NO2
2. resp.addOutputData("reqMap", reqMap);
//回傳一個KEY是reqMap，內文是reqMap
3. resp.addOutputData("reqMap", rtnList);
//回傳一個KEY是reqMap，內文是reqMap
```

# prompt接值
我們依序覆寫<td class ="tbYellow2"></td>的物件部分


## 1-1 範例 - 後端接值

```javascript=
		<!-- 先試試看寫死姓名-->
		<td class ="tbYellow">員工姓名</td> <!---- -->
		<td class ="tbYellow2">WEI-CHANG</td> 
        
        改成用JSTL拿值 userNAME是後端傳給的KEY值
		<!-- 新增 DEMO JSTL區域-->
		<td class ="tbYellow">員工姓名</td> <!---- -->
		<td class ="tbYellow2">
			<c:out value="${userNAME}" />
		</td> 
```

## 1-2 範例 - c:if 判斷如果沒傳會為空
```javascript=
<c:if test="${not empty userDIVNM}">
    <!--  userDIVNM 有值 -->
    <c:out value="${userDIVNM}" />
</c:if>
```

## 1-3 範例 - c:forEach 下拉選單
```javascript=
		<td class ="tbYellow">朋友清單</td>
		<td class ="tbYellow2">
		<select id="friends_list" class="input">
			<option value="">全部</option>
			<c:forEach var="data" items="${friends}">
				<option value="${data}">${data}</option>
			</c:forEach>
		</select>
		</td>
```

# FormSubmit
發送請求會有兩種方式一種是FormSubmit一種是Ajax，兩者最大的不同是FormSubmit會整個reload一次畫面，所以可以利用這時候重新刷新畫面的資訊，將請求的資訊呈現在畫面上，最代表性的畫面就是主約資訊查詢，

## 2-1 範例 - 打包前端值
```javascript=
不用 script內form.submit()
已經自行幫忙 會將整個form的所有值往後端送
```

## 2-2 範例 - script寫法
```javascript=
doQueryForm : function(){		
 		var form = document.getElementById('form1');
 		form.action = "${dispatcher}/XXZX_0200/queryForm"; 
 		form.submit();
	}
```
好像看起來很方便耶 他也不用自己組reqMap


## 2-3 範例 - HTML物件寫法
需要像前面的練習一樣在html內接值

```javascript=
<td class ="tbYellow">員工編號_FORM</td> 
	<td class ="tbYellow2">
		input id="EMP_NAME2" name="EMP_NAME2" type="text" class="textBox2"  value="${EMP_NAME2_NAME} ${EMP_NAME2_ID}" /> 
	</td> 
```
或是因為他會重Load畫面，可以寫在initApp的地方
```javascript=
var DIV_NO2 = <c:out value="${DIV_NO2}" />;
$('DIV_NO2').value = DIV_NO2;

但這樣要考慮 prompt有可能不會有DIV_NO2 雖然這個範例不會錯 但通常希望加上一些檢核
在進入c:out

<c:if test="${not empty DIV_NO2}">
	<!--  DIV_NO2 有值 -->
	var DIV_NO2 = <c:out value="${DIV_NO2}" />;
	$('DIV_NO2').value = DIV_NO2;
</c:if>
```


## 2-4 範例 - XML寫法
```xml=

 <property name="url">/CM/js/ajax/dummy.jsp</property>
 改成
 <property name="url">/XX/XX/XXZX_0200/XXZX0200.jsp</property>
            
```
## 2-5 範例 - 我還是想用TABLE UI能怎麼做
只有這個可以不用學，因為2-1和2-2在導頁的時候會用到，2-3和2-4都是常見的接值方法。
此方法會被grid.load取代

用這個方法需要結合上面的想法，那我在initApp做grid.load不就可以了嗎?
```javascript=
grid.load(<c:out value="${XXZX_0200rtnList}" default="[]"/>);
```
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_29b9005b476eb5de4e3be6b4a4acf36c.png)

```javascript=
結果出錯了，這個會很難DEBUG，我也是問到
grid.load(<c:out value="${XXZX_0200rtnList}" default="[]" escapeXml="false" />);
```

# Ajax

## 3-1 範例 - 
一樣之前的作法
```javascript=
 var buttons = {
    	doQuery : function(){		
            var EMP_NAME = $F('EMP_NAME');
            alert(EMP_NAME);
        }
	};	
```

## 3-2 範例 - script寫法
```javascript=
new CSRUtil.AjaxHandler.request(XXXXXXXXXXXXXXXX)


function(resp){ //ReturnCode
	grid.load(resp.rtnList);  //TABLE UI
	$('EMP_NAME2').value = 'hello'; //自己給值
	$('DIV_NO').value = resp.INV_NO; //從後端拿值

```
## 3-3 範例 - HTML物件寫法
```javascript=
可以不用動 因為resp已經處理了 BY上面第5和6的寫法
```
## 3-4 範例 - XML寫法
```xml=
<property name="url">/CM/js/ajax/dummy.jsp</property>
```

# 共用方法
已經學過button可以\.多個方法，想像未來查詢新增修改刪除，都是要將form內的資料往後面送，
如果寫成Java

```java=
Map reqMap = new HashMap();
reqMap.put("EMP_NAME", "IVY");
reqMap.put("DIV_NO", "9100000");
mod.query(reqMap);

Map reqMap = new HashMap();
reqMap.put("EMP_NAME", "IVY");
reqMap.put("DIV_NO", "9100000");
mod.update(reqMap);  
        .
        .     
```
希望可以改成
```java=
Map reqMap = this.getMap();
mod.query(reqMap);

Map reqMap = this.getMap();
mod.update(reqMap);  
        .
        .        
```
更簡潔
```java=
mod.query(this.getMap());

mod.update(this.getMap());  
        .
        .        
```
同理Jsp也是一樣，可以把reqMap的方法抽出來，我們習慣使用action這個變數名稱

## 4-1 範例 - 範例-共用打包
```javascript=
	var actions = {
		getReqMap : function(){				
			var EMP_NAME = $F('EMP_NAME');
			var DIV_NO = $F('DIV_NO');
			var reqMap = {
				'EMP_NAME' : EMP_NAME,
				'DIV_NO' : DIV_NO
			}		
			alert(reqMap);
			return reqMap;
		}
	};
	
    
    
    呼叫請求的時候把它放進去
    {reqMap: Object.toJSON(actions.getReqMap())}
    //仿造前面的JAVA呼叫方式
```

## 4-2 範例 - 共用檢核
首先先學習怎麼自己檢核，同樣在action新增一個方法doCheck


```javascript=
doCheck : function(){				
			var EMP_NAME = document.getElementById("EMP_NAME").value;  	
			if(!EMP_NAME){
				alert('EMP_NAME不可為空');
				return false;
			} else {
				return true;
			}
		}
```
在doQuery呼叫的時候先判斷

```javascript=

			if(!actions.doCheck()){
				return;
			}
```

如果我想檢核單位代號只能是數字...
```javascript=
			var DIV_NO = document.getElementById("DIV_NO").value;  	
			
			<c:if test="判斷DIV_NO是否為數字....">
    			
			</c:if>
            
            這邊是不WORK的 因為這段要寫一個正則表示判斷 很難
```
想想這樣好像有點麻煩，所以底層幫你做了一些檢核方法!! 下面是三個常用的
```javascript=
function initValidation(){
    valid = new Validation('form1');
    valid.define( 'required', [{ id : 'EMP_ID', errMsg : '身份證字號不得為空' }] );
    valid.define('validate-date', [{ id : 'EMP_ID', errMsg : '身份證字號須為日期格式' }])
    valid.define('validate-number', [{ id : 'DIV_NO', errMsg : 'DIV_NO需為數字' }] );
}
```

在你呼叫的do方法要去使用vaild
```javascript=
function initValidation(){
    valid = new Validation('form1');
    valid.define( 'required', [{ id : 'EMP_ID', errMsg : '身份證字號不得為空' }] );
    valid.define('validate-date', [{ id : 'EMP_ID', errMsg : '身份證字號須為日期格式' }])
    valid.define('validate-number', [{ id : 'DIV_NO', errMsg : 'DIV_NO需為數字' }] );
}
```

$('OP_STATUS_NM').innerHTML = resp.rtnList[0]['OP_STATUS_NM'];

			<td class ="tbYellow">審批狀態</td>
			<td class ="tbYellow2" id='OP_STATUS_NM'>