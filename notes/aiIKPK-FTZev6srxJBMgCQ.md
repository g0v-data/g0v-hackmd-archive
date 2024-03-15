# 2024-03-15 Recap
###### tags: `School`, `recap`
## Recap

- 
    
    

## Discussion Topics
- lazy property
    - class 建立時還不會建立，等用到它時才會建立。
- computed property 
    - 沒有 = ，所以不會儲存值(相對於 stored property)，每次都會重新計算

        `var a: Int = 10
var b: Int = 10
var num: Int {
    get          
}`
- property observer
  
      `var num2: Int = 10 {
  willSet {
         print(newValue)
  }
  didSet {
          print(oldValue)
  }
  
}`