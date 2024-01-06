# JavaScript 接值


- [prompt接傳值](#prompt接傳值)
  - [1-1] 範例 - 前端送值
  - [1-2] 範例 - 後端接值
  - [1-3] 範例 - 後端送值
  - [1-4] 範例 - 前端接值

- [FormSubmit接傳值](#ForSubmit接傳值)
  - [2-1] 範例 - 前端送值
  - [2-2] 範例 - 後端接值
  - [2-3] 範例 - 後端送值
  - [2-4] 範例 - 前端接值
  
- [Ajax接傳值](#Ajax接傳值)
  - [3-1] 範例 - 後端接值
  - [3-2] 範例 - 後端送值
  - [3-3] 範例 - 前端送值
  - [3-4] 範例 - 前端接值

接值的觀念
```python
1. 前端會送請求給後端
2. 後端會接值
3. 後端必須要傳值
4. 前端顯示
```

1. 前端會送請求給後端
跟DataSet一樣，有這些步驟，前後端都是用"KEY"值在傳遞，
前端的KEY值 from submit是送全部的form，AJAX是
```javascript
1. Form Submit 是hmtl 內的form的KEY值
<input type="text" size ="20" id='DIV_NO' name='DIV_NO' > 
<input type="text" size ="20" id='EMP_NAME' name='EMP_NAME' > 

2. Ajax的KEY值 
reqMap : Object.toJSON(reqMap)
以上KEY值是reqMap
reqMap2 : Object.toJSON(reqMap)
以上KEY值是reqMap2
```

2. 後端會接值
後端都是用"KEY"值在接String Map VO
```java
1. String id = req.getParameter("EMP_NAME_HELLO");
2. Map reqMap =VOTool.jsonToMap(req.getParameter("reqMap"))
3. DTXXTP01 vo = VOTool.mapToVO(DTXXTP01.class, reqMap);
```
3. 後端必須要傳值
後端都是用"KEY"值放在resp再送回前端
```java
1. resp.addOutputData("DIV_NO2", user.getDivNo()); 
//從userobject拿出DivNo字串回傳，回傳一個KEY是DIV_NO2
2. resp.addOutputData("reqMap", reqMap);
//回傳一個KEY是reqMap，內文是reqMap
3. resp.addOutputData("reqMap", rtnList);
//回傳一個KEY是reqMap，內文是Map List
```

4. 前端顯示
```javascript
1. TABLE UI接值
grid.load(resp.rtnList || []);
2. TABLE UI接值 Fomr submit *須放在initApp
grid.load(<c:out value="${XXZX_0200rtnList}" default="[]"/>);


```
# prompt接傳值
1. 前端會送請求給後端
這邊不用處理，主要是底層會幫忙，即便是導頁的也是LP_JSON幫忙


## 1-1 範例 - 前端送值
```javascript=
通常首頁沒有
導頁由LP_JSON幫忙
```

## 1-2 範例 - 後端接值
```java=
String ACTION_TYPE = req.getParameter("ACTION_TYPE");
```
## 1-3 範例 - 後端送值
```java=
    resp.addOutputData("ACTION_TYPE",ACTION_TYPE );

```
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1538f9174d419413f96fdc76327ea192.png)
你沒看錯就是這樣，大家很常會忘記這個事情，前端送給後端後，他就會忘記所有的事情，你必須要回傳給他，他接值後才會做，否則沒resp.addOutputData他什麼也不會做
## 1-4 範例 - 前端接值
要放在initAPpp 或是下方Html用 JSTL顯示


放在initApp內

http://localhost:8080/XXWeb/servlet/HttpDispatcher/XXZX_0100/prompt?ACTION_TYPE=I
```javascript=
var ACTION_TYPE_GET = '${ACTION_TYPE}';
			alert(ACTION_TYPE_GET);
```
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_979393f93dafeb264f6b8d306eec1895.png)

放在html用JSTL
```javascript=
<td class ="tbYellow">生日</td>
    <td class ="tbYellow2">
	<input class ="textBox2" id='BIRTHDAY' value='${rtnMap.BIRTHDAY}'>
	<c:out value="${ACTION_TYPE}" />
</td>
```
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d1d3037de865a1eb47be973d66d4e77d.png)


# ForSubmit接傳值

## 2-1 範例 - 前端送值
```javascript=
var form = document.getElementById('form1');
form.action = "${dispatcher}/XXZX_0200/queryFromDemo"; 
form.submit(); 
```

## 2-2 範例 - 後端接值 
因為form submit是針對所有的欄位往後送，只能這樣接，
如果要傳入reqMap給其他模組，須自己組Map
```java=
String 生日 = req.getParameter("生日");
String 姓名 = req.getParameter("姓名");
String 職稱 = req.getParameter("職稱");
String 身分證字號 = req.getParameter("身分證字號");

Map.put("HELLO",生日);
Map.put("HELLO_NAME",姓名);
Map.put("HELLO_PPP",職稱);

XX_Z0Z001.query(Map);
.
.
.

```
## 2-3 範例 - 後端送值
傳值無論是什麼方法都是使用addOutputData
複習一下這邊就是傳了三個KEY FRIEND1 FRIEND2 FRIEND3給前端 前端需要用這三個KEY值去接到AUTHER OO DORIS
```java=
    resp.addOutputData("FRIEND1","AUTHER" );
    resp.addOutputData("FRIEND2","OO" );
    resp.addOutputData("FRIEND3","DORIS" );
```


## 2-4 範例 - 前端接值
重要觀念是 他會跟promp一樣，會再重新進去initApp，所以可以跟prompt一樣把東西放在
initApp或是HTML使用JSTL，但這樣會有一個問題，有個回傳參數可能prompt有，做的方法沒有，或是做的方法有，prompt沒有。
意思就是

```java=
doprompt方法有
 		resp.addOutputData("rtnList", rtnList  );
doquery沒有
但是都放在initApp或HTML的JSTL，都會去執行，有時候沒處理好會噴錯

```
所以通常會建議做一些判斷
```javascript=
沒有就空陣列
grid.load(<c:out value="${XXZX_0200rtnList}" default="[]" escapeXml="false" />);

如果有ACTION_TYPE在進去
<c:if test="${not empty ACTION_TYPE}">
	var DIV_NO2 = <c:out value="${ACTION_TYPE}" />;
	alert(DIV_NO2);
	$('EMP_NAME_HELLO').value = DIV_NO2;
</c:if>
```

# Ajax接傳值

## 3-1 範例 - 前端送值
```javascript=
new CSRUtil.AjaxHandler.request('${dispatcher}/XXZX_0200/').post('doQueryForm', {reqMap2: Object.toJSON(reqMap)},

KEY值是reqMap2，傳的東西是一個Object轉乘JSON格式
```

## 3-2 範例 - 後端接值
```java=
就是接你的KEY值，如上面KEY就是reqMap2 很重要的觀念
```
## 3-3 範例 - 後端送值
永遠的addOutputData
```java=
	List<String> friends = new ArrayList();
	friends.add("OO");
	friends.add("DORIS");
	friends.add("AUTHER");
	friends.add("IVY");
	resp.addOutputData("friends_DEMO_ALL", friends) ;
同樣回傳一個KEY值是friends_DEMO_ALL的KEY值
```

## 3-4 範例 - 前端接值


原本prompt有回傳朋友清單
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_983a877a874a5cce250bb069c3646c57.png)

但因為我在3-3重新回傳了一個friends_DEMO_ALL
於是可以接friends_DEMO_ALL回來
```javascript=
new CSRUtil.AjaxHandler.request('${dispatcher}/XXZX_0200/').post('query', {reqMap2: Object.toJSON(reqMap)},	
			function(resp){ //ReturnCode
				grid.load(resp.rtnList); 
				$('EMP_NAME2').value = 'hello';
				$('DIV_NO').value = resp.rtnList;
				var friend_list = resp.friends_DEMO_ALL;
				alert(friend_list);
				var friends_DEMO = $('friends_DEMO');
				if(friend_list&&friend_list.length>0){
				
				for(var i=0; i<friend_list.length; i++) {
						alert(friend_list[i]);
						//friends_DEMO.append(new Option(friend_list[i], friend_list[i]));
					}			
				}
				},
				function(resp){
					//error
				}		
			);
```


會議號碼
25131778278
會議密碼
1234
https://cathay.webex.com/cathay/j.php?MTID=m30cd3bf0ca30ffd3b3332363481b7e22