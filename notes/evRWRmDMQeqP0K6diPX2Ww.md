# React JSX注意事項

**一、不可喧染**
* 1. boolen值
* 2. null
* 3. undefined

**二、需先律定變數值**
* 1. 物件
* 2. function

**三、自我封閉元素標記，結尾一定要加 /**
* 1. < img src=http.xxx.xxx />
* 2. < hr />
* 3. < br />
* 4. <input /> 

**四、class、label for改名**
* 1. < class>需改名為 < className>
* 2. < labe for> 需改名< label htmlfor>
```
<div className="mb-3">
  <label htmlfor="exampleFormControlInput1" class="form-label">Email address</label>
  <input type="email" className="form-control" id="exampleFormControlInput1" placeholder="name@example.com">
</div>

//htmlfor="exampleFormControlInput1"是對應input的id名稱
```

