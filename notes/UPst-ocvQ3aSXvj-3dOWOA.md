> DD技術讀書會 
> # 策略模式 
> Reference[name=Ada] [time=Fri, Mar 29, 2019] [color=#907bf7]

---

**範例：『 年終獎金計算 』（ javascript ）**

*    Bad:
```javascript=
    var calculateBonus = function( performanceLevel, salary ){
        
        if ( performanceLevel === 'S' ){
            return salary * 4;
        }
        if ( performanceLevel === 'A' ){
            return salary * 3;
        }
        if ( performanceLevel === 'B' ){
            return salary * 2;
        }

    };
    
    calculateBonus( 'B', 20000 );    //輸出：40000
    calculateBonus( 'S', 6000 );    //輸出：24000
    
```
*    Good:
```javascript=
    var S = function( salary ){
        return salary * 4;
    };
    var A = function( salary ){
        return salary * 3;
    };
    var B = function( salary ){
        return salary * 2;
    };    
    
    
    var calculateBonus = function( func, salary ){
        return func( salary );
    }
    
    
    calculateBonus( 'S', 10000 );    //輸出：40000
    
```
----
