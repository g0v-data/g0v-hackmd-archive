# S3 Storage

S3 (Simple Storage Service) for Internet

存放靜態檔案(網頁, 影片, 軟體安裝檔)
備份,版本控制與Amazon Machine Images(AMI) template

Data Consistency Model
    Read-after-write for PUTS of "new" object
    Eventual Consistency Delete/Update file have to half second delay
    
S3 bucket創建時, 需要指定Region
    Object stored in a region never leave the region unless transfer to another region
    
Every object is contained in a bucket, bucket and object are one-to-many relationship

Object consist of Object data and metadata(KV)

更新檔案會讓權限重置

S3 可以開啟Static website hosting直接當成網站 in bucket property

Storage Class
    1. General purpose
    2. Infrequent Access(IA)
        Standard-IA (Cold with DR)
        One Zone-IA (Cold without DR)
    3. Intelligent-Tiering Class (自己判斷)
    4. Archive
        Glacier (Expedited(1-5Min), Standard(3-5Hours), Bulk(5-12Hours))
        Glacier Deep Archive (Standard(12Hours), Bulk(48Hours))
    5. S3 on OutPosts (建在地端)
    
Server-Side (at rest) & Client-Side (in transit via SSL/TLS)

AWS S3-managed keys(SSE-S3)把key放在bucket裡面,  or AWS KMS-managed key(SSE-KMS)
在開啟預設加密之前的資料, 並不會被加密(要重新上傳才能加密)
跨區複製預設就會開啟預設加密
request header要求加密, 最優先, 再來是預設加密, 可用bucket policy拒絕沒有加密的需求

Consistency (一致性) - 從 client 的讀寫角度來描述資料一致性
Availability (可用性) - 不能超時、不能出錯，結果是合理的
Partition Tolerance (分區容忍性) - 網路封包遺失等，只要網路分區就是

ACL for **object**&bucket level and bucket policy for **bucket** level only
IAM Policy & Bucket Policy & Bucket ACL & Permission 取交集, deny優先allow

CloudTrail for Audit account activity, monitor and log actions
    create "trail" S3 bucket to record activity
Athena for analyze logs using SQL
CloudWatch for metrics and event or alarms

S3 transfer acceleration 用cloudfront去加速上傳, 或用Direct Connect上傳

S3 Glacier 只能用CLI上傳下載或寫程式發request(Rest API or SDK)
    最小單位是vault

S3 Versioning
overwrite會創出一個新版本, 每個版本都有唯一的版本ID, 刪除物件會有DeleteMarker, 可以透過移除DeleteMarker來復原

Life-Cycle management
    Transition actions & Expiration actions rule
    