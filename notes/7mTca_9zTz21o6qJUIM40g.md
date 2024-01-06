Spring

1. IOC底層原理 ( IOC容器 = 工廠 )
    https://www.youtube.com/watch?v=3HyHcIfzFvc&list=PLmOn9nNkQxJFsh3ikY1bN86FjJgbQ9Plq&index=4
   演進:     直接在類中new(高耦合度) 
      ->    工廠模式。建立工廠類，透過工廠類get(降低耦合)
      ->    xml解析+反射(降低耦合，只需更改xml文件。不寫死在類中)

2. IOC接口
    (1)    BeanFactory
    (2)    ApplicationContext
