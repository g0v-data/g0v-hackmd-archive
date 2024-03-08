# 2024-03-08 Recap
###### tags: `School`, `recap`
## Recap

- git merge 後打不開 xcode，可能是專案目錄出現衝突 conflicts，要用文字編輯器打開專案
    
    

## Discussion Topics
1. UITableViewCell 的 Reuse 機制產生什麼問題，解決了什麼問題
    1. 解決的問題：
        - 佔用大量記憶體
    3. 產生的問題：
       
        - 會出現重複的內容（沒有清掉前一個 cell 的內容）
        - 可以在 cell 內寫一個 reset func 來還原cellForRow 設定資料
        - 用內建 function： prepareForReuse () 
        - [Solving duplicated / repeating cells in Table view](https://fluffy.es/solve-duplicated-cells/)
3. IQKeyboardManager 所解決的問題

    - 打字時鍵盤會遮住 field

    - 如果要自己寫，而不依賴 IQKeyboardManager 推鍵盤，可以用「通知中心」偵測鍵盤位置