# 容器監控與觀測 - 提升您的應用可用性


監控不用使用者回覆就發現問題 - CloudWatch Synthetics 
撰寫Canaries，定期發出Request檢查是否問題

發現問題後如何調查 - CloudWatch ServiceLens

主動問題追蹤分析、尋找問題、原因 - X-Ray Insights
Group建立後回到Insights查問題


上面是新版本，後者是原本的手動方式
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9e6ca4209ec8fb40c31d4c0ac0bf7090.png)

結論
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9b74d57cd2faddce984c4cf4980729fe.png)

[WorkShop Link](https://catalog.us-east-1.prod.workshops.aws/v2/workshops/31676d37-bbe9-4992-9cd1-ceae13c5116c/en-US)



---


# 【實際案例分享】TVBS - 以資料湖為核心的資料驅動敏捷產品開發

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_92eceb60f9edb00697902dd2922e1d87.png)

情境一 App推播


DB : RDS+EFS
透過SNS推撥
一小包log (stream - JSON格式) 進入至Amaazon Kinesis Sata Stramas 再轉進firehose
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_317d5de53e7e1089a542d3059b59946f.png)


情境二 電商會原壽星優惠EDM

AWS Glue - 建議script掛上 (搞不太懂)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f23422b296f32af4b7250dc451675ff8.png)


情境三 觀看數據系統優化


Data Lake

AWS Lake Formation - 權限控管

Athena - SQL 操作介面，

透過數據來排序後定優先順序

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5dcaee9c743971fffd3715b8b643f47a.png)

未來
收集數據、未來可做克制化推薦、並讓ML學習的資料
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5c96f0efe78c9ed1e280fca74658c9a2.png)


---

# Serverless 安全架構最佳實務

用戶的安全性

把單一EC2上的多個API改成多個Lambda service，可對每個Lambda分別設定權限
Lambda負責計算，可由Trigger觸發

Amazon Cognito - 管理帳號註冊登入認證管理
Function Poliy - 誰可以來使用function
Execution Role - 

建議：對每一個function建立一個role，避免日後修改權限影響到其他的function
權限不要開太寬容易有風險問題

SAM會自動建立「最小」權限
ENI= Elastic network interface

安全性控制
1. 機密資訊不要直接寫在Lambda，
2. 不要放在Lambda env內
3. 使用『AWS Secrets Manager』透過IAM授權，去存取資料。

Lambda function isolation:
可以想像對每一個小function建立一個小VM


Api gateway
- 可以針對每個path每個method驗證，不用進入到核心程式，不用coding達成
- 阻擋沒有權限的人進來，不耗用後端資源
- 後續才轉為後端資源處理
- 也可以用lambada authorizer來驗證
- api gateway cache 5分鐘，不用浪費後端資源
- 目的:後端資源對外接觸面積越小越安全

Limiting and throtting
- 流量控管
- 非常好用

AWS WAF - 可以防止DDOS攻擊


Lambda Authorizer: 用來作認證的function，通過後再呼叫其他function
Resource policy可以控制能存取的endpoint
Code 429: too many request
可以設定API Gateway只吃已通過CloudFront來的流量

QA : 去拿SM拿資料會不會造成流量
- 在run time前先處理 (沒聽清楚)


QA : Lambda env不是可以加密嗎
- api key 、password、會更重視lifecycle，如果放在env不容易維護與更換

QA : Lambda authorizer流量問題
- 還是要適度壓測，lambda auth有caching方法，讓同個user reuse cache



---


# 透過機器學習的個人化推薦贏得您的客戶


個人化
- 提昇用戶感知，點擊率
- 提升效率收入
- 找到新的產品線

對使用者進行個人話推薦
- 使用規則來推薦→不容易維護，容易衝突
- 使用ML來推薦→不夠即時，對新資料沒有經驗來學習，使用一個演算法可能不夠，需要專家來訓練模型

Amazon Personalize 個人化推薦
提供用戶互動資料→事件
提供metadata: 產品說明
User metadata : 年齡、地點
-> 可以用在智慧選字? (http://jira.arphic.com.tw/browse/RC-595)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_357b05da6b948e2c807224ccbbcb7ae5.png)


User Personalization 
Similar items: 尋找用戶有興趣的相關商品
Personalized ranking:個人化排序

註:完全可以用在字體上.

如何使用Amazon Personalize
- 把資料上傳到S3，就可以開始訓練模型
- 使用JS即時取得最新操作資料
- 

新用戶→預設推薦→看了幾個產品後→透過事件將用戶喜好輸入→取得新的推薦

impression : 有在用戶畫面上但用戶沒點的其他產品，可能也有用處，也放進來。

Filter
加入：想讓用戶再買的商品、期間限定商品、好評商品
排除：下架商品、分級商品(年齡、價格...)


QA:Null空值沒有關係，還是可以送出，就讓系統自行學習。



---


# 【實際案例分享】AWS EKS 搭配 S3 + CloudFront 打造萬人響應零延遲的現代化線上尾牙

k8s = Kubernetes
管理各container的工具

AWS EKS=k8s的託管服務
用Pod來取代VM
調整deployment replica可快速擴充一模一樣的pod


# 以 AWS Step Functions 實作無伺服器的工作流

Standard workflow:時間較長的workflow
Express workflow:event-deiven的workflow

Step function的用途:
自動化流程
檔案或影像處理
傳統功能現代化，改成微服務/雲服務


Codepipeline : git 管理觸發


用平行的方式來處理檔案清單:
- Type: Map
- MaxConcurrency
- 都執行完才會往下走

單體式架構VS微服務架構

事件分散式設計架構：
所有的動作都要提供一個反向的動作，錯誤發生後依序回溯

綠色：執行完成的步驟
藍色：正在執行的步驟


# 【實際案例分享】無伺服器模組快速交付創造現代化雲原生應用程式價值

無伺服器
API Gateway + Lambda + dynamoDB

案例分享




