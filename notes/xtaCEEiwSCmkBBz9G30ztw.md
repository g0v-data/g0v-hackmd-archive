# React計時器

* **引用react內建{useState}**
於vs code 最上方輸入 import {useState} from "react"
* **創建react簡易code**
於vs code 打入縮寫rfc 將function 後面英文第一個字改大寫
* **命名變數名稱**
const [Total, setTotal] =useState(0)
//設定一個變數Total 並在後續抓取某個區域的質
* **定義變數**
< h1 onClick{()=>{
setTotal(Total+1)
}}>{Total}
< /h1>
//onClick代表點擊觸發事件 setTotal等於Total質+1 預設為0 相對等於total=total+=1 

// {Total} 顯示Total質

**完整code**

```

import { useState } from "react"

export default function Count() {
  const [Total, setTotal] =useState(0)
  return (
    <>
      <h1>React計時器</h1>
      <h1 onClick={()=>{
        setTotal(Total+1)
      }}>{Total}</h1>
    </>
  )
}

```
