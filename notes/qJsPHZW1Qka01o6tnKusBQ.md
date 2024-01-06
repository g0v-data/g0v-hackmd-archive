# K8s 學習心得

> Borg k8s 的前身
> k8s 繼承高CPU memory的應用與低延遲性

k8s 最初目標
. 部屬多副本應用程式
. 提供服務探索與附載平衡
. 健康機制，自我檢查與修復能力
. 機器調度功能
> CNCF (Cloud Native Computing foundtion )雲原生計算基金會
 
CNCF 內產品有三大階段
. sabdbox
. incubating
. Graduated 到此階段代表專案很成熟了，多家大型公司已經在用了

## 架構概念
### 控制平面(control plane)
. API Server: control plane 的前端，讓外部服務有能力去操作k8s，可以有多台
        與這台溝通都是要透過憑證。
. etcd: key/value 的高可用性資料庫，存放k8s 內的各種運算資料
        備份與還原非常重要，需要多加練習
        基於Raft的演算法，要注意etcd的數量
. Scheduler: 透過各種分數計算，找尋欲創立之容器最適合之節點
. controller: 內部是無窮迴圈，監聽各種事件變化進行後續處理

個節點與API Server的溝通，一率都是用憑證

### 工作節點(worker node)
. Kubelet:
    API Server 溝通
    確保所有容器都如預期般執行
. Kube-proxy
    透過iptables/ipvs 等方式搞定網路附載平衡與服務探索
. Container 引擎
    Docker、Containerd等....
    
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5bab4072eacef4e6fb1bcbdeab9575b0.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_142ccca76a98a77147d1b7c25e53a103.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9822bf7f18aca015aa357050c86813ce.png)

> k8s 是支援容器，不是支援docker
> 使用CRI(container runtime interface)進行溝通。

Kubelet 執行container flow
* 1.24 版之前，中間會透過DockerShim轉換CRI的協定
* 1.24 之後移除DockerShim ，所以1.24之後就再也不支援Docker了，改使用containerd
* ContainerD已經支援CRI了
* 移除docker 效能上也能有效提升

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_86dc76e7dfe74562a4b180cdf2e0055e.png)


## 網路
節點內部的網路管理方式(Container Network Interface)
* 容器與容器
    * 同節點
    * 跨節點
* 容器到外部網路
* 外部網路到容器
* IP地址分配
    * 隨機分配
    * 靜態管理
* 容器被移除，回收資源
每個k8s 一定都要安裝一個CNI，例如Calico

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0381ec61336247f8643aee75260e4ade.png)

## 儲存設備
存取硬體的管理方式(Container Storage Interface)
k8s 內有兩種主要實作邏輯
* in-tree 程式碼實作
* CSI 標準銜接

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_68b6db3252cc7feabe9dfb3823365e79.png)


## 各服務架構圖
kubelet 是代理agent，每個節點都要有
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3c45ac7f4a63a458cbb8ac236cc63a5e.png)

## Kubeconfig
為kubenetes很重要的設定檔，紀錄了cluster與與User name，如果要在一台機器上管理多個clouster或是user，就需要在此檔案內進行修改。
語法
```
kube config
```

## namespace
輕量級虛擬化，將k8s方便管理，概念拆分出來不同的大樓名稱，對於未來的管理與除錯會更容易
kube開頭的namespace 盡量不要使用。
```
kubectl get ns
#加入參數可以輸出更多資訊
kubectl get ns -o wide
#輸出成Json 或yaml
kubectl get ns -o json

#查詢kubectl 的API-resource，例如get xxxx，xxxx就是api-resource
kubectl api-resources
```

Examples
---
- [Book example](/s/book-example)
- [Slide example](/s/slide-example)
- [YAML metadata](/s/yaml-metadata)
- [Features](/s/features)

Themes
---
- [Dark theme](/theme-dark?both)
- [Vertical alignment](/theme-vertical-writing?both)

###### tags: `Templates` `Book`
