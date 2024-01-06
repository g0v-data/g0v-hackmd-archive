Outpost : AWS 為了合規性可解決這樣問題

台灣有節點，可以拿來做CDN (https://zh.wikipedia.org/wiki/%E5%85%A7%E5%AE%B9%E5%82%B3%E9%81%9E%E7%B6%B2%E8%B7%AF)
用來接觸遠端客戶，緩存CACHE 如影片、音樂等
若要額外佈署節點，需要額外的費用

region > AZ > 節點

IAM (Identity and Access Management) : 認證(IAM user、Group)與授權(透過IMA Policy (用JSON 格式)定義角色)
預設的user，唯一的policy只有change password (需要定義policy 才能做事)

進入IAM > 左側點選policy > Filter Policy 填寫想要的service > 便可找出可套用的 policy


什麼時候用IAM role?
因為預設AWS 內部服務不能自己溝通，必須有 policy 定義role 才能溝通
使用角色取得臨時安全登入資料
透過 IAM 賦予的Role，可拿到一組臨時性的 cridential (預設維持一小時)
不用把cridential 寫在程式上 (避免被駭客駭)


Amazon S3 (simple storage service)
存放非結構性的資料 
上傳到一個照片到S3，會預設存在一個region內的3個AZ上 (算是一個REGION內跨AZ的SERVICE，並一職偵測自動修復，才能達成耐久性高，達11個9)

EC2 > subnet > AZ > VPC > Region (EC2 有單點故障問題，IASS)

(elastic load balancing，不會有單點故障的問題，PASS):自動將流量分散到多個目標

#AWS five Pillars
1. Security
2. Reliability
3. Cost Optimization
4. Performance Efficeicncy
5. Operation Excellence

#Edge Location (Cloudfront)
CDN概念

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6c011afb2e570b04866c70c922709970.jpg)

#Avalible Zone
跨AZ間差不多5毫秒
每個Account的AZ ID可能指到不同實體機房
Latency考量大於容錯時，可不跨AZ

#AWS Wavekength(去年推出的infra的一種)
cloudping.info (去看Latency)

#AWS Local Zone (小型的AZ，但沒有像Region這麼全面，目前只有洛杉磯有)

#AWS Outposts rack
https://aws.amazon.com/tw/outposts/
1. 不能上雲的，會有頻寬問題的，就直接搬一台到自己公司機房裡面
    1. Native AWS (裸機)
    2. VMWare xxxxxxx (裝好der)
2. Outposts 其實就是一個延伸，延遲性低，視為一個local region 走內網的溝通方式


#The Simplest Architecture

#S3
放EC2 Image
適合放靜態網頁，high avalible、low cost
*S3 耐久性有11個9*，因為資料放在3個 AZ，檔案會自動偵測和自動修復 (可能會考)
非結構化資料儲存 (圖片影片等)

P41、bucket name 的url 呈現方式(可能會考)
Bucket Policies 使用JASON格式

ARN : Amzon Resource Name (每個 bucket、服務等，會有一個ARN，類似身分證字號)

VPC = Virtul Privaty Cloud 必考
AZ 與 AZ 之間可以溝通 > 透過網路設定 (VPC = Virtul Privaty Cloud)
**VPC 考試會考**

#臨時性的使用 Access Point Policy去設定

AWS近兩年推出新服務
AWS Wavelength => 降低延遲
https://aws.amazon.com/tw/wavelength/

AWS Local Zone (更小型規模的region，更靠近你的城市，目前僅在LA實施)
https://aws.amazon.com/tw/about-aws/global-infrastructure/localzones/

*任何有衝突的規則AWS Deny always wins.

Transfer Acceleration 功能開啟需要費用，預設不開
https://docs.aws.amazon.com/zh_tw/AmazonS3/latest/dev/transfer-acceleration.html

#AWS S3 Glacier (磁帶)

實驗 :Architecting on AWS - Lab 1 - Hosting a Static Website
補充常用 policy :
https://docs.aws.amazon.com/AmazonS3/latest/dev/WebsiteAccessPermissionsReqd.html


EC2的資源為disposable resource 隨時隨地可拋棄的資源 (EC2的基礎就是AMI-設定檔)

AMI 可以從東京 region 複製到新加玻 region
AMI 可以開放特定人士存取或Public

#Three ways to get your AMI (p.92)
1. Pre-Built
2. AWS Marketplace
3. Create your own
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AMIs.html

#EC2資料放在EBS (p.103)

#Instance Store is ephemeral(暫時性的)

#Instance store vs. EBS
1. Instanse store 便宜、效能好，但資料是暫時性的
3. EBS 資料永久，但速度比較慢?

Instances Optimized for Amzon EBS (p.106)
一個EC2可以搭很多個EBS
但一個EBS只能配一個EC2 (EBS only attaches to one instance)
當發生讀寫很慢，可能原因是 EBS 選太爛或者沒選 EBS Optimized (水管較粗)

EFS : elastic file system

有多個EC2要mapping到多個Storage (就可以讀到同一個storage的檔案)

#類比
EFS (NAS)
EC2+Instance store (DAS)
EBS (SAN)
S3 (儲存snaptshot+AMI)->IA->Glacier (lifecycle manager)

What is Amzon EBS? (p.154)
Block storage device that connects to one instance at a time. Can be backed up to Amazon S3.


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0d3321d9c60baadeadc42b7be49ac649.jpg)


#如果不想要Stopping後開起來IP不一樣，一定要配一個EIP(Allocate Elastic IP address (配置彈性IP 位址)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d2b6720a126a128507bc26667e839ee0.jpg)


如何知道專案是否符合所選之 EC2?
1.Cloud Watch (監控CPU Loading)
https://aws.amazon.com/tw/cloudwatch/
2.Trusted Advisor (有一個dashboard 監控EC2)
https://aws.amazon.com/tw/premiumsupport/technology/trusted-advisor/
3.Compute Optimizer
https://aws.amazon.com/tw/compute-optimizer/


(p.129)EC2的購買方式:
ON-DEMAND INSTANCES (需要的時候開，最貴)
RESERVED-INSTANCES (RI；購買一年以上，七八折)
SAVING PLANS
SPOT-INSTANCES (競標，一~三折，淡季多出來的資源拍賣，劣勢:當AWS需要的時候，會要收回，2分鐘就會關起來)
Standard:不能改instance type
Convertible:可改instance type

Saving Plans 比 RI 更彈性，只要承諾會用幾個小時，就會提供優惠，分兩種
Compute Saving Plans (最彈性，不限region與OA，只管使用期限) 
EC2 Instance Saving Plans 


(p.137)Dedicated Options:
 =>法規與Lincense ，需要有獨享資源 

Dedicated Instance (同時間不會跟別人共享，不一定會是同一台機器)
Dedicated Host (多提供一個Host Id，都不會跟別人共享，控制性更高，更貴)

#(p.141)若有300台EC2，要將其中20台更新，如何知道哪20台?
使用 tags : 可 manage、search 與 filter

#Placement Group(讓EC2群組化，可以擺在一起，降低Lantency) :Cluster、Spread、Partition 
=>預先劃一個池子，強制放在一個框框，降低延遲

Cluster Placement Groups:
全放在一起，lantancy 最低，效能最好，但犧牲HA(備援)

Spread Placement Group:
每個都放不同地方高lantancy、且兼顧HA(但最高檔)

Partition Placement Group:
綜合體，一個機櫃放兩三個

Database Typess
1. Relational
2. Nonrelarional

地端 vs AWS
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9490f7396b438463ff35b375cbd23c33.png)


#AWS RDS (Relational Database Service)
https://en.wikipedia.org/wiki/Amazon_Relational_Database_Service
https://aws.amazon.com/tw/rds/

RDS 提供之服務:
 *選 multi-AZ (容錯，會在兩個AZ建立)*
加密、同步資料與容錯，省去後續管理的時間(節省維運成本)

DynamoDB (Non Relational Database Service)
比 RDS 少了 server (是一個serverless的DB服務，全託管server服務，比RDS更省事)
Primary Key 包含 :Partition Key(必填)，sort key(可填可不填)
 =>DynamoDB 只 query Partition Key 和 Sort key，故定義這兩個很重要，會影響到 query DB (RDS 則可 query 較多面向的條件)

DynamoDB 由多個Item組成；Item由 Primary Key + 多個Attributes；Primary Key由 Partition Key(必填)，sort key(可填可不填)組成


**考試必考**
如何打造自己的VPC?
Create VPC > Create Interne Gateway > 將 IGW attach 到落單的VPC (VPC&IGW為一對一的關係)
>Create (Public/Privaty)Subnet>選擇剛建立的VPC>選擇哪個AZ >定義(Public/Privaty)subnet網段
>因尚未建立routing table，外部連不到 > Create (Public/Privaty)routes >於subnet associations選擇和哪一個(Public/Privaty)subnet做連接

**不放IGW，預設為Privaty Routes** (VPC 沒有 IGW 就是私有雲，無法對外溝通)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3a9209c654829530046f30c2d56eeb5b.png)

Public Routes & Privaty Routes 的共同點都會有 VPC 的default routes (10.10.10.0/16)
=> 即使在不同AZ，只要在同一個VPC，也可以溝通
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_30af2c0cd9e8f50df5b90246508c7542.png)

AWS也有NACL(Network Access Control List)，套用在subnet上面 (可做黑白名單功能)
  *Rule# 代表順序，數字越小，Priority 越高*
Subnet 裡又細分EC2 Level的防火牆，則套用Security Groups 
  *與NACL不同點為沒有Rule#，因為Security Groups沒有Deny的功能，皆為Allow；Security Group 若inbound 80 port 開了，outbound 80 port 亦會同步開(一邊通另一邊自動通，stateful)反之，NACL不會同步開，需兩邊設定(stateless)

內網的資源和外網溝通，要透過NAT，在Private/Public Routes 加入NAT

若IT從外網要更方便連內網，可透過跳板機 : Bastion Server(跳板/堡壘機) (放在public subnet)
Bastion Server可通全部內網 (故要加一個security groups，限制source)

 NAT (Way-Out)/Bastion Server (Way-In)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b493968dbd0501b04fa0a88830d7e8f0.png)


2020/9/18 
Module 5 (p.211)
NAT Gateway : 轉址，以對外溝通

預設VPC與VPC間不能互通，故可做 isolation
每個region都會有預設的VPC，且VPC是跨AZ (故AZ間可溝通是靠VPC)

Using one VPC : 使用的人很少(P.219)
大部分公司多使用Multi-VPC Pattern & Multi-Account Pattern

一個region 可有多個VPC，預設最多開5個 (有超出需求再另外開)
創多個VPC和創一個VPC價格相同，charge的是VPC裡建置的資源 (一個VPC可建大概200個subnetS)

(P.228)每個routing table 有defule rout，不可刪除修改

(P.229)
Public Subnet : 有路由可通internet gateway 
Private Subnet : 沒有路由可通internet gateway, 使用nat gateway連外網

(P.231)VPC 和 IGW 是一對一的關係

NAT Gateway 是託管服務 (有多台EC2在維運，降低故障率)
NAT Instance 不是託管服務

(P.235)能畫/16 就畫/16 (最大開下去)，以便之後切割網段
(P.238)預留多一點IP address 給Privaty，少留一點給 Public
(p.239)ENI (Elastic Network Interface)=網卡，EC2 預設帶一張網卡，至少支援2張 
(但每個EC2可支援的網卡數量不同，要先確認好)

(P.242) *Everything will be fail* 不鼓勵特定IP綁特定的EC2 (EC2這種非託管，易壞)

(P.246)Rules are **stateful (防火牆在EC2上面，只開一邊通，另一邊就同步通。必考)

(P.249)三層式網站架構，可使用 Security Groups : Chaining Diagram

(P.250)
NACLs 套用在subnet上，為stateless 
Security Groups 套用在EC2上，為statefule

**必考 (P.255)如果創建了一個EC2，想從筆電連但連不上，如何troubleshooting
1. 確認 IGW
2. 確認Routing Table
3. 確認NACLs & Security Groups
4. 確認是否有 Public IP Address

Moudle 6 假設要搭建混和雲的話如何搭
VGW (Virtula Privaty Gateway) 為託管服務，不會有單點故障問題，attach 在VPC上 (P.270)
IGW 和 internet 溝通
VGW 和 VPN 溝通
=>使用私有網路連aws，如在地機房的延伸

(P.272)專線 (DX-AWS Direct Connect)費用高

(P.280) VPC 間預設不通，若要互通 => 使用 VPC Peering

VPC Peering :可和不同 AWS account、AWS region peer，皆走私有網路
設定 : VPC > Peering Connection > Route Table (兩邊的VPC route table皆要設定)
Peering 設定完為兩邊都通，若只想要單邊通，要去NACLs 設定黑名單


(P.297)VPC Endpoint
VPC 打一個洞，讓VPC內和外的服務(eg:S3)，可以走內網溝通

RISC 看AWS上網路架構資訊(第三方)

何時會需要ELB (Elastic Load Balance):
同一個region 跨 AZ 時，於使用者與服務之間建立ELB，ELB會將使用者的請求，平均分散到底下多個EC2
使用者和ELB溝通，是透過 DNS URL
ELB (elastic load balancing，託管服務，不會有單點故障的問題，PASS):自動將流量分散到多個目標
假設底下其中一個EC2壞掉，ELB會知道 (ELB會做Health Check，定期ping他)，會將使用者請求導入好的 EC2
=>延續使用者服務品質

(P.302)有分內外ELB
(P.306)ELB分三種
CLB是第一代，較少人用，目前提供給舊客戶建置舊版EC2使用 (2011年11月前建置)
ALB :走Layer 7(HTTP、HTTPS)，ALP可創建不同的 target groups，依據不同的 request，分配給不同顏色的target groups，如根據request，使用不同的Microsoft Office (P.310)
NLA :走Layer 4(TCP、TLS、UDP), 每秒可處理百萬request, 效能最好

ELB 只處理inbound，若outbound看位置，走NAT

Route 53 放置AZ 上
(P.320)除了做DNS服務，還可以做不同 Routine Policy (跨region)
=> (P.321)provides DNS health checks 
可處理跨Regaion HA

(P.338)
Policy 分三種
1. AWS-managed :AWS 先寫好
2. Customer-managed : 客戶客製
   (AWS-managed 與 Customer-managed 可互通)
3.Inline : 專屬專用，不能與上面互通

(P.342)
為何已寫allow，要另外再寫deny => 因為以防其他人的 policy 加入影響不小心allow其他resource，故先寫 deny

(P.350)若想要給臨時性的權限=>透過 IAM role 賦予，permission is assumed by the user or service
(讓使用者戴上一頂安全帽，就會賦予安全帽所附加的policy，為臨時性的permission，預設一小時)

STS : Simple Token Service

(P.361)Amazon Cognito
開發網頁或app，Cognito會出現 portal 讓使用者輸入帳密，寄驗證信，增加安全性

(P.372)AWS Organizaations 管理 multiple account
透過最上層的 policy SCP (Service Control Policies) 控管，也可幫大家付錢
https://aws.amazon.com/tw/organizations/

Module 8 

Three types of Elasticity
- Time-Based
- Volume-Based
- Predictive-Based

CloudTrail = 幫你記錄日誌

Cloudwatch = 以日誌、指標和事件的形式來收集監控和運作資料，為AWS 與現場部署伺服器上執行的AWS 資源、應用程式和服務提供一個整合的檢視。

Auto Scaling = 監控應用程式並自動調整容量，盡可能以最低成本維持穩定、可預測的效能

CloudFormation = 使用編程語言或簡單的文字檔以自動且安全的方式，在所有區域和帳戶為應用程式所需的資源建立模型並進行佈建。
支援YMAL & JSON
Change Set = 可以先預覽CloudFormaion的更動結果

AWS quick start = 快速自動化佈署Template (建議)；透過JSON、yaml方式搭建環境。
https://aws.amazon.com/tw/quickstart/

AWS OpsWorks = 快速自動化佈署Template

AWS beanstalk = 快速自動化佈署Template；透過程式語言方式搭建環境。

AWS system manager = 集中化管理平台(EC2)、快速佈署更新

CloudFront (Edge Location,CDN的概念) / 可防DDos

Elastic Cache = 緩存RDS Data
Sticky Session = 緩存 Web session

Module 11

Amazon Simple Queue Service (SQS) = 託管服務 :　讓洩洪不要掉棒

(必考) queue 的設定值

Module 12 : 微服務與無服務差別  (Microservice vs Serverless)
Monolithic forum application v.s. Microservice forum application
Microservice 將 service 細分組合在一起 (example:樂高)
達到 Microservice 的途徑:
Container :可達到更快佈署 Microservice架構 (example:Docker)
AWS 使用 Docker:
可用 EC2 佈署 Docker (但需要額外設定其他功能，如CloudWatch，不建議)
(p.584)建議用 Elastic Container Service (ECS):託管 Continers 服務
也可用 Farget 跟ECS 幾乎是一模一樣的東西，幫助Dockers 快速佈署的服務
Farget(託管程度較高，不用選instance type，但貴) v.s. ECS

AWS Serless : 在AWS上就是用Lambda這服務 (可將 server 控管的較精準，依照使用時間計算費用，如用水用電，相較於EC2 較省)
https://aws.amazon.com/tw/lambda/

Lambda 無法取代 EC2
使用 AWS Lambda 執行程式碼，不必佈建或管理伺服器。您只需為使用的運算時間支付費用。
區別 : 
時間:Lambda 只能執行15分鐘以內的事 (偶發性)
次數:若執行次數頻繁，使用 EC2 會比 Lambda 便宜 

AWS 之間的服務都是需要授權，才能溝通




AWS Step Funtion: 可把多個Lambda 串起來

RPO 需要多久時間恢復
RTO 承受多久時間的資料遺失 (遺失多久時間的資料)

***************
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c18134783b9f819f2fce54d63b74b431.png)
***************

AWS Compute Optimizer / CloudWatch / AWS Trusted Advisor = 設計架構/Resource/Security 時自動化檢查及提供建議

