# 建立普惠測試環境 新UIUX 
## GCP
* 到**網路端點群組** 新增網路端點群組與網路端點*test-webserver-newui*
* 到load balancing(Network services)編輯puhui-client-lb
* 在**轉送規則**新增:
    * 主機 - puhui.pasha.tw
    * 路徑 - /newUIUX/*
    * 後端 - test-webserver-newui
* 到防火牆開port 
* 如果要過load balancer 要到health check那邊也開port