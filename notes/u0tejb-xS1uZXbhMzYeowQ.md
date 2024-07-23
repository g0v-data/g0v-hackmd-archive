# 期中考

- [下拉選單](#下拉選單)
  - [1-1] 範例 - 下拉選單(處理回傳的List)
  - [1-2] 範例 - 下拉選單(連動選單)
   
- [隱藏欄位](#隱藏欄位)
  - [2-1] 範例-隱藏欄位

- [錯誤處理Exception](#錯誤處理)
  - [3-1] 範例 - 錯誤處理Exception
  - [3-2] 範例 - 模組檢核

# 下拉選單


## 1-1 範例 - 下拉選單(處理回傳的List)
一個是放在html 使用forEach

```java=
resp.addOutputData("ORG_ID_List_TEST",ORG_ID_List);
```

```javascript=
<select id="q_SYS_CD" >
	<option value="">全部</option>
	<c:forEach var="data" items="${ORG_ID_List_TEST}">
		<option value="${data.ORG_ID}">${data.ORG_ID} ${data.ORG_SRT_NM}</option>
	</c:forEach>
</select>
```

一個是放在jsp 使用迴圈處理
```java=
resp.addOutputData("ORG_ID_List",  VOTool.toJSON(ORG_ID_List));
```
```javascript=
var ORG_ID_List = <c:out value = "${ORG_ID_List}" default="[]" escapeXml="false" />; 

var select_ORG_ID=$("ORG_ID");
	for(i=0; i<ORG_ID_List.length; i++){
		const option = document.createElement('option');
		option.setAttribute('value', ORG_ID_List[i].ORG_ID);
		option.innerHTML = ""+ORG_ID_List[i].ORG_SRT_NM;
		select_ORG_ID.appendChild(option);
	}
    
    也可以使用new Option
    var newOption = new Option('歐歐','OOOOOOO');
	//添加至選單_
	$('TRD_ACNT_NO').add(newOption);
```

## 1-2 範例 - 下拉選單(連動選單)

首先下拉選單要先在initApp註冊一個事件 網路方法有很多change move 等等
https://www.w3schools.com/jsref/event_onchange.asp


```javascript=
$("ORG_ID").addEventListener('change', actions.doSelect_TRD_ACNT_NO);

```
借用這個把內文改成
https://www.w3schools.com/jsref/tryit.asp?filename=tryjsref_onchange_addeventlistener

```javascript=
<!DOCTYPE html>
<html>
<body>



<select id="ORG_ID" onchange="myFunction()">
  <option value="Audi">Audi</option>
  <option value="BMW">BMW</option>
  <option value="Mercedes">Mercedes</option>
  <option value="Volvo">Volvo</option>
</select>


<select id="ORG_ID_NM">
  <option value="">全部</option>
</select>


<script>

document.getElementById("ORG_ID").addEventListener('change', doSelect_TRD_ACNT_NO);

function myFunction() {
  var x = document.getElementById("fname");
  x.value = x.value.toUpperCase();
}


function doSelect_TRD_ACNT_NO() {
	var ORG_ID_NM = document.getElementById("ORG_ID_NM");
    var x = document.getElementById("ORG_ID").value;
    
	const option = document.createElement('option');
	option.setAttribute('value', x);  //處理選項值
	option.innerHTML = '賓士';  //處理文字
	ORG_ID_NM.appendChild(option);
}

</script>

</body>
</html>

```
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c32c65ef13c02d36a1bb8d5947bf611b.png)


# 隱藏欄位
隱藏欄位沒有特別的，就是找到該物件給一個hidden的屬性，可以自己找一個物件F12自己試試看
常用的方法就是 找到ID後 設定hidden維true或是設定屬性

這題會需要這樣是因為大部分來說，我們查詢資料庫可能有30個欄位，我們想要給使用者看的可能是姓名、ID跟年齡和保額，可能性別不太重要，因為性別可能只是判斷最後輸出的訊息是先生還是小姐，但如果不把查詢的結果保留起來，請求的時候有教過，第二個請求會忘記第一個請求，所以往往會把資訊包在form裡面隱藏起來，在做form submit或ajax時送出去

## 2-1 範例-隱藏欄位

最簡單就是用jqeruy語法找到後設定成hidden
也可以用傳統的找到ID後設定hidden
或是使用setAttribute 設定屬性

以下方法可以隱藏網頁元件
```javascript=
$('ORG_ID').hidden = true;
document.getElementById("btn_approve").hidden = true;
$('btn_query').setAttribute("hidden", "hidden");
```

這邊示範如何把需要的欄位隱藏在form內

首先HTML要有物件
```javascript=
<td class="tbYellow" >指揮官好朋友</td>
<td>
    <input type="hidden" id="MACHI" name="MACHI"></input>
</td>
```
後端要傳
```java=
resp.addOutputData("MACHI", "DORIS");
```

顯示
```javascript=
$('MACHI').setValue('${MACHI}');
```



# 錯誤處理


## 3-1 範例 - 錯誤處理Exception
```java=

```

## 3-2 範例 - 模組檢核
公司會把一些專門用來檢覈的模組放在 四碼_四碼_mod
這些模組只處理參數檢核，不會做計算

通常無論是模組或是檢核模組，SPEC就算沒寫都要針對傳入參數檢核不得為空或是null

EX: 雖然SPEC沒講，但會希望這樣檢核

```java=
if (DTRGD030VO_List == null || DTRGD030VO_List.isEmpty()) {
   throw new ErrorInputException("期貨商子帳戶設定清單不得為空");
}
```
如果有錯除非是ErrorInputException、DataNotFoundException
否則幾乎都是拋出ModuleException
```java=
if (QA_LIST.isEmpty()) {
    throw new ModuleException("指揮官找無QA可用，程式終止");
}

不然就是直接拋出去
throws ModuleException {
XX
XX
XX
}
```