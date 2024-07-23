7/17 1st meeting with Kos
===

Weekly Tasks
--

- [ ] 思考要擴充什麼功能
- [ ] 決定Framework、語言
- [ ] 思考哪些要上AWS，要用什麼服務
- [ ] 建立Gitbub project / to-dos


## Notes：如何深化自己的Side project
- 待深入研究名詞：三層次架構、Service Repository Pattern、Data Transfer Object
- 小習慣：
    - Git commit應言之有物
        - 使用what而非how
        - 用biz term取代工程師term，例如place order而非create order
    - 不要有奇怪的註解
    - 建立潔癖、使用formatter
    - 客製化git指令（例：git save），概念測試時可快速回覆
    - PR的原子化
- 所有功能先以簡單為主（先求有，再求好？）：
    - 利用Eslint / 靜態分析工具進行CI
    - 利用github action進行CD 
- 測試自動化的重要性：
    - 最小單位以一個PR做一個測試
    - 很多工程師工作一兩年也尚不具備此能力
- SOLID原則：可擴充、可替換性、建立新class而非改code
    