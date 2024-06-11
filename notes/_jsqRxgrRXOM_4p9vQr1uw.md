# React map應用
map屬於React陣列迴圈，運用於重複喧染陣列元素例如
陣列number=[1,3,5,7,9] 要一次喧染,可以將number加入map

{number.map((v, i)=>{
return < h1 key= i> {v}< /h1>
})}

上述v代表value陣列元素每個質 i代表index代表陣列第幾個元素

**注意事項**
* 使用map一定要使用key通常key都會與index值一致

code如下    

```
import React from 'react'



export default function Map() {

    const numbers=[1,3,5,7,9]
  return (
    <>
        {numbers.map((v, i)=>{
            return <div key={i}> <h1>{v}</h1> </div> 
        })}
           </>
  )
}

```