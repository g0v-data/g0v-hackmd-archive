# 2024-03-15 Recap
###### tags: `School`, `recap`
## Recap

- 
    
    

## Discussion Topics
- lazy property
    - class 建立時還不會建立，等用到它時才會建立。
- computed property 
    - 沒有 = ，所以不會儲存值(相對於 stored property)，每次都會重新計算
        ```swift
        var a: Int = 10
        
        var b: Int = 10
        
        var num: Int {
        
        get {
        return a + b  // 計算 a 和 b 的和
            }      
        }
        ```
- property observer
  屬性觀察器
    ```swift
    var num2: Int = 10 {
  willSet {
         print(newValue)
  }
  didSet {
          print(oldValue)
  }
    }
    ```