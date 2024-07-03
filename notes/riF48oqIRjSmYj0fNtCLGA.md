# JavaScript

### **陣列的批次處理** [不再迷失在 JavaScript 的陣列處理 - 客座投稿 | W3HexSchool](https://w3c.hexschool.com/blog/6ccb7d73)

#### forEach
forEach 是對陣列內的每一個元素執行函式，以陣列 browser 為例。

```js
browser.forEach(function (item, index) {
  item.newSupport = item.support - 5;
});
```

#### map

map 跟 forEach 其實非常地像，都是針對陣列內的每一個元素執行函式，最大的差別在於 map 會將 return 的結果存成一個新陣列，而 forEach 並不會 return 結果。

```js
// map 做法，定義一個變數去接 return 回來的值
let mapBrowser = browser.map(function (item, index) {
  // map 跟 forEach 最大的差別在於 map 會回傳值
  return item.name;
});

// forEach 做法，預先定義一個空陣列，並使用 push 去新增資料
let forEachBrowser = [];
browser.forEach(function (item, index) {
  forEachBrowser.push(item.name);
});
```

#### filter

filter 可以把它想成一個過濾器，會將 "符合條件" 的元素 return 回來，因此很適合用在搜尋特定條件的資料，跟 map 一樣也會產生一個新陣列，可能有些人會把兩者功能搞混，讓我們來看一下差別。

```js
// filter 寫法
let filterBrowser = browser.filter(function (item, index) {
  return item.support > 40;
});

// map 寫法
let mapBrowser = browser.map(function (item, index) {
  return item.support > 40;
});
```

filter 會將符合條件 ( item.support > 40 ) 的這三包資料 ( Google、Safari、Firefox ) return 回 filterBrowser

![images](https://w3c.hexschool.com/img/%E8%A8%BB%E8%A7%A3_2019-11-15_1044081f4v32.jpg)

map 卻只是把 item.support > 40 的值 Boolean ( true / false ) 回傳，跟我們預期想要的不同。

![images](https://w3c.hexschool.com/img/%E8%A8%BB%E8%A7%A3_2019-11-15_1045131f5p0e.jpg)

那假如我們想使用 map 也做到一樣的結果呢? 來看一下下列程式碼

```js
let mapBrowser = browser.map(function (item, index) {
  if(item.support > 40) {
      return item;
  }
});
```

此時我們使用 `console.table(mapBrowser);` 觀察一下結果，會發現不符合條件的元素他一樣會回傳一個值 ( undefined )，不符合我們想要的資料結構，因此 map 並不適合使用在 "過濾" 這種情境下。

![images](https://w3c.hexschool.com/img/%E8%A8%BB%E8%A7%A3_2019-11-14_230325q3plf.jpg)

到這邊可能有人會有一個疑問，那 forEach 有辦法做到嗎? 讓我們來看看。

```js
// 前面有提到 forEach 要產生新陣列必須先定義一個空陣列
let forEachBrowser = [];
browser.forEach(function(item, index) {
  if(item.support > 40) {
      // 將符合條件的 item 推進去
    forEachBrowser.push(item);
  }
});
```

此時得到的結果跟使用 filter 是一樣的，但是會發現程式碼並沒有 filter 直覺、乾淨，因此若是要過濾資料還是建議使用 filter 來操作。

![images](https://w3c.hexschool.com/img/%E8%A8%BB%E8%A7%A3_2019-11-15_1048531famcb.jpg)
#### sort
sort 會對陣列的元素進行排序，此方法會變更原本陣列的內容。
#### 情境 : 將 Browser 的 support 由低至高排列

```js
let browser = [
  {
    name: 'Google',
    support: 98
  },
  {
    name: 'IE',
    support: 11
  },
  {
    name: 'Safari',
    support: 49
  },
  {
    name: 'Firefox',
    support: 86
  },
  {
    name: "Edge",
    support: 11
  }
]

// --------------------------------------------------------------------- //

// 這邊傳入的參數跟上述幾個方法不太一樣，排序時傳入兩個參數 a、b(自定義)。
browser.sort(function(a, b) {
  // 此時會將 a.support 的值跟 b.support 的值做比較
  // 若是 a.support < b.support，則回傳 -1，並且把 a 排在 b 的前面
  // 若是 a.support > b.support，則回傳 1，並且把 b 排在 a 的前面
  // 若是 a.support = b.support，則回傳 0，並且兩者順序不變
  if (a.support < b.support) {
    return -1;
  } else if (a.support > b.support) {
    return 1;
  } else {
    return 0;
  }
});
```

![images](https://w3c.hexschool.com/img/sort315up.jpg)

#### reduce
reduce 比較常用在"累加"，我個人認為它算是 forEach 以及 map 的複合型，能夠傳入的參數比較多也比較複雜，讓我們來看一下以下範例。

#### 情境 : 將所有瀏覽器的 support 相加

```js
let browser = [
  {
    name: 'Google',
    support: 98
  },
  {
    name: 'IE',
    support: 11
  },
  {
    name: 'Safari',
    support: 49
  },
  {
    name: 'Firefox',
    support: 86
  }
]

// --------------------------------------------------------------------- //

// reduce 可以傳入四個參數(初始值, 目前的元素, 目前元素的索引, 陣列內容)，
// 在函數後面可以傳入一個初始值，這邊傳入的是 0，讓我們來拆解一下

let supportTotal = browser.reduce(function(prev, current, index, array) {

  // 第一個傳入 : prev 此時是帶入後方的初始值 0，
  // 跟目前的 current.support ( Google 的 support ) 98 相加 => 98

  // 第二個傳入 : prev 此時是 98，
  // 跟目前的 current.support ( IE 的 support ) 11 相加 => 109 

  // 第三個傳入 : prev 此時是 109，
  // 跟目前的 current.support ( Safari 的 support ) 49 相加 => 158

  // 第四個傳入 : prev 此時是 158，
  // 跟目前的 current.support ( Firefox 的 support ) 86 相加 => 244

  // 最後 prev 得到的結果是 244，並且把它 return 回來

  prev += current.support;
  return prev;
}, 0);
```

接著讓我們使用 reduce 來進行前面做過的 "將 support > 40" 的元素取出來，傳進新陣列。

```js
let reduceBrowser = browser.reduce(function(prev, current, index, array) {

  // 第一個傳入 : prev 此時是空陣列，
  // Google 的 support 符合條件，因此將整包 Google 物件 push 進去

  // 第二個傳入 : prev 此時是 [{Google...}]，
  // IE 的 support 不符合條件，因此不會被 push 進去

  // 第三個傳入 : prev 此時是 [{Google...}]，
  // Safari 的 support 符合條件，因此將整包 Safari 物件 push 進去

  // 第四個傳入 : prev 此時是 [{Google..., Safari...}]，
  // Firefox 的 support 符合條件，因此將整包 Firefox 物件 push 進去

  // 最後 return prev 的結果為 [{Google...},{Safari...},{Firefox...}]

  if (current.support > 40) {
      prev.push(current);
  }
  return prev;
}, []); // 這邊傳入預設值空陣列
```

最後得到的新陣列就跟前面使用 filter 以及 forEach 篩選出來的結果一樣。

![images](https://w3c.hexschool.com/img/%E8%A8%BB%E8%A7%A3_2019-11-17_2350213hcfy.jpg)

![images](https://w3c.hexschool.com/img/reduce31l90.jpg)



### console.log( [Say no to console.log! - DEV Community](https://dev.to/alishgiri/say-no-to-consolelog-556n?ref=dailydev)
* ##### console.dir()
  For hierarchical listing of arrays and objects.  
	
	```
	console.dir(["apples", "oranges", "bananas"]);
	```
	
	[![console.dir example](https://media.dev.to/cdn-cgi/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2F3ksvxyavsmejk1eb73u5.png)

* ##### console.table()
  For rows and columns listing of arrays (might not be suitable for objects).  
	
	```
	console.table(["apples", "oranges", "bananas"]);
	```
	
	[![console.table array example](https://media.dev.to/cdn-cgi/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fzwzq9uf4t643lorq1qbu.png)](https://media.dev.to/cdn-cgi/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fzwzq9uf4t643lorq1qbu.png)  
	
	```
	console.table({"a": 1, "b": 2, "c": 3});
	```
	
	[![console.table object example](https://media.dev.to/cdn-cgi/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fr45pzliuaaxbx4preo4k.png)](https://media.dev.to/cdn-cgi/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fr45pzliuaaxbx4preo4k.png)

* ##### console.group()
	
	```
	console.log('This is the top outer level');
	
	console.group('Task 1');
	console.log('Task activity 1');
	console.log('Task activity 2');
	console.groupEnd();
	
	console.group('Task 2');
	console.log('Task activity 3');
	console.log('Task activity 4');
	console.groupEnd();
	
	console.log('Back to the top outer level');
	
	```
	
	[![console.group example](https://media.dev.to/cdn-cgi/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fqomtbv7ifve72l51hino.png)](https://media.dev.to/cdn-cgi/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fqomtbv7ifve72l51hino.png)
* ##### console.time() & console.timeEnd()
	
	```
	try {
	  console.time("record-1");
	  await someAsyncTask();
	} catch (error) {
	   // handle error
	} finally {
	  console.timeEnd("record-1");
	}
	```
	
	[![console.time log](https://media.dev.to/cdn-cgi/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fd102ywfw05lmnp69lc0l.png)](https://media.dev.to/cdn-cgi/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fd102ywfw05lmnp69lc0l.png)
* ##### console.clear()
  This will clear the console.

### 等待事件Promise (eg. modal彈跳視窗)
在async function內，modal彈跳視窗有可能在動作結束後才打開，這時候在事件結束後要將modal關閉，會因為modal根本尚未打開而無法關閉，變成事件結束後modal視窗是開啟的狀態
```javascript
$('.addMetamaskWallet').click(async function() {
	event.preventDefault();
		
	//顯示模態視窗
	$('#waittingModal').modal('show');

	// Use a promise to ensure the modal is fully shown，等待模態視窗完全顯示: 使用 `Promise` 來等待 `shown.bs.modal` 事件，確保模態視窗完全顯示之後再繼續執行。
	await new Promise((resolve) => {
		$('#waittingModal').on('shown.bs.modal', resolve);
	});

	try {
		const r = await metamask_sign();
		if ( ! r ) {
			if ($('#waittingModal').hasClass('in') || $('#waittingModal').hasClass('show')) {
				// 如果沒有使用`Promise`等待視窗顯示，會造成loading視窗在 await metamask_sign() 執行完才開啟，而無法準確的將loading視窗隱藏
				$('#waittingModal').modal('hide');
			}
			return;
		}
	} catch (error) {
		console.error('metamask_sign 過程中發生錯誤:', error);
	} finally {
		if ($('#wihoutMCModal').hasClass('in') || $('#wihoutMCModal').hasClass('show')) {
			$('#wihoutMCModal').modal('hide');
		}
	}
});

```