# How to implement Processor Temperature Sensor

    busctl  introspect  SERVICE OBJECT [INTERFACE]
           
顯示SERVICE服務上OBJECT對象(以路徑表示)的 interface, method, property, signal 值。
如果指定了 INTERFACE 參數， 那麼僅輸出指定接口上的成員。

常見方法是透過D-bus

    busctl | grep -i entity

可以得到        xyz.openbmc_project.EntityManager.service
所以SERVICE= xyz.openbmc_project.EntityManager

    busctl tree xyz.openbmc_project.EntityManager
    
可以看到

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_01863fd771dac574137b2e2f4a64c7a5.png)


###### tags:`entity-manager` ` Processor Temperature Sensor`