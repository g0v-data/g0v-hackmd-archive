# 2024-02-26 Recap
## Recap

- 想要帶著最新版本的 code 另開 branch 可善用 git stash
- Autolayout
    - view 沒有預設的寬高； button 有
    - 可從畫面左上角開始排版
- kingfisher 的 sandbox error
    - 可裝前一版本的 kingfisher 試試看
    
    

## Discussion Topics

1. 大家來找碴 ([請看附件](https://discord.com/channels/1189112358832984104/1189498607859150930/1210517877766098954)) ，基於良好的 coding style，去找出附件專案內可以調整的地方，請不要花費超過 30 分鐘，重心還是要擺在 STYLiSH
    
3. 什麼是 Version Number、Build Number？
    - Build Number：方便內部團隊區分開發版本，有可能 N 版 Build Number 都在 Version Number 1.0 裡面
    - Version Number：App store 會看到的版本號。
        - major, minor, patch
        - 強制更新，在 viewDidLoad：
            - 使用 API 下載
            - 判斷版號 vs 最低版號需求：通常在前幾版就會先預埋好。
            - 跳出 alert
5. 怎麼用 Xcode 內建的工具 debug？
6. HTTP request & response