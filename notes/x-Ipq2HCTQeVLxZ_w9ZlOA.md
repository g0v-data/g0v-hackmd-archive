# 2024-03-12 Recap
###### tags: `School`, `recap`
## Recap

- core data 出現重複錯誤，注意是否重複呼叫 persistant container
    
    

## Discussion Topics
1. How to remove cells on the screen
    1. deleteRows(at:with:) 
    2. remove(at:)
3. beginUpdates / endUpdates
    - 跟 reload data 二擇一使用即可，並且官方建議用 performBatchUpdates(_:completion:) 代替此方法。
